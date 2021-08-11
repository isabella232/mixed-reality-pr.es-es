---
title: Representación de volúmenes
description: Obtenga información sobre cómo representar eficazmente imágenes volumétricas enriquecciones con opacidad y color en Windows Mixed Reality.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: imagen volumétrica, representación de volúmenes, rendimiento, realidad mixta
ms.openlocfilehash: 3843f0f4e49a0564b41d834231630d281aa9e874df8d35c4feaa4fe5bba0ed68
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220940"
---
# <a name="volume-rendering"></a>Representación de volúmenes

Para obtener una MRI médica o volúmenes de ingeniería, vea [Representación de volúmenes en Wikipedia.](https://en.wikipedia.org/wiki/Volume_rendering) Estas "imágenes volumétricas" contienen información enriquez con opacidad y color en todo el volumen que no se puede expresar fácilmente como superficies como mallas [poligonales.](https://en.wikipedia.org/wiki/Polygon_mesh)

Soluciones clave para mejorar el rendimiento
1. BAD: Naïve Approach: Show Whole Volume(Bad: enfoque naïve: Mostrar volumen entero) generalmente se ejecuta demasiado lentamente
2. BUENO: Plano de corte: mostrar solo un solo segmento del volumen
3. BUENO: Cortar sub volúmenes: mostrar solo algunas capas del volumen
4. GOOD: Reduzca la resolución de la representación del volumen (vea "Mixed Resolution Scene Rendering")

Solo hay una cierta cantidad de información que se puede transferir desde la aplicación a la pantalla en un fotograma determinado, que es el ancho de banda total de memoria. Además, cualquier procesamiento (o "sombreado") necesario para transformar los datos para la presentación requiere tiempo. Las consideraciones principales al realizar la representación del volumen son las siguientes:
* Screen-Width * Screen-Height * Screen-Count * Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame
* 1028 * 720 * 2 * 256 = 378961920 (100 %) (volumen res completo: demasiadas muestras)
* 1028 * 720 * 2 * 1 = 1480320 (0,3 % de completo) (segmento fino: 1 muestra por píxel, se ejecuta sin problemas)
* 1028 * 720 * 2 * 10 = 14803200 (3,9 % de completo) (segmento de subvolume: 10 muestras por píxel, se ejecuta de forma bastante fluida, parece 3d)
* 200 * 200 * 2 * 256 = 20480000 (5 % de volumen completo) (volumen res inferior: menos píxeles, volumen completo, parece 3d pero un poco desenfoque)

## <a name="representing-3d-textures"></a>Representación de texturas 3D

En la CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

En la GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Sombreado y degradados

Cómo sombrear un volumen, como MRI, para una visualización útil. El método principal consiste en tener una "ventana de intensidad" (un mínimo y un máximo) en la que quiera ver las intensidades y simplemente escalar a ese espacio para ver la intensidad en blanco y negro. A continuación, se puede aplicar una "rampa de color" a los valores dentro de ese intervalo y almacenarse como una textura, de modo que se puedan sombrear diferentes partes del espectro de intensidad de diferentes colores:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

En muchas de nuestras aplicaciones, almacenamos en nuestro volumen un valor de intensidad sin procesar y un "índice de segmentación" (para segmentar diferentes partes, como la máscara y el tejido; estos segmentos los crean expertos en herramientas dedicadas). Esto se puede combinar con el enfoque anterior para colocar un color diferente o incluso una rampa de color diferente para cada índice de segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Licación de volumen en un sombreador

Un primer paso excelente consiste en crear un "plano de corte" que pueda moverse por el volumen, "cortarlo" y cómo se analizan los valores en cada punto. Esto supone que hay un cubo "VolumeSpace", que representa dónde se encuentra el volumen en el espacio mundial, que se puede usar como referencia para colocar los puntos:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Seguimiento de volúmenes en sombreadores

Cómo usar la GPU para realizar el seguimiento de subvolúmenes (recorre algunos vóxeles en profundidad y, a continuación, capas en los datos de atrás a delante):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Representación de volúmenes completos

Al modificar el código de subvolume anterior, se obtiene lo siguiente:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Representación de escena de resolución mixta

Cómo representar una parte de la escena con una resolución baja y volver a colocarla en su lugar:
1. Configuración de dos cámaras fuera de pantalla, una para seguir cada ojo que actualiza cada fotograma
2. Configuración de dos destinos de representación de baja resolución (es decir, 200 x 200 cada uno) en los que se representan las cámaras
3. Configuración de un quad que se mueve delante del usuario

Cada fotograma:
1. Dibuje los destinos de representación de cada ojo a baja resolución (datos de volumen, sombreadores caros, entre otros)
2. Dibuje la escena normalmente como resolución completa (mallas, interfaz de usuario, entre otras)
3. Dibuje un cuatro delante del usuario, sobre la escena y proyecte las representaciones de baja velocidad en esa
4. Resultado: combinación visual de elementos de resolución completa con datos de volumen de baja resolución pero alta densidad
