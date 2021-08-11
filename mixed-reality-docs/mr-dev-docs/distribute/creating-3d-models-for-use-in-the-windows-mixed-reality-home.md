---
title: Creación de modelos 3D para su uso en el hogar
description: Requisitos de recursos e instrucciones de creación para los modelos 3D que se usarán en la Windows Mixed Reality en cascos envolventes (VR) HoloLens y envolventes.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, modelado, guía de modelado, requisitos de recursos, directrices de creación, iniciador, iniciador 3D, textura, materiales, complejidad, triángulos, malla, polígonos, polycount, límites, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 9fdd485c67a757d40b049c08f114ce9982aafc27e9103c4b31c21fd8af08d186
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207685"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Creación de modelos 3D para su uso en el hogar

La [Windows Mixed Reality principal es](../discover/navigating-the-windows-mixed-reality-home.md) el punto de partida en el que los usuarios se desatensan antes de iniciar aplicaciones. Al diseñar la aplicación para cascos Windows Mixed Reality, use un modelo [3D](implementing-3d-app-launchers.md) como iniciador de aplicaciones y coloque vínculos [profundos 3D](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)en el Windows Mixed Reality principal. En este artículo se describen las directrices para crear modelos 3D compatibles con Windows Mixed Reality inicio.

## <a name="asset-requirements-overview"></a>Información general sobre los requisitos de recursos

Al crear modelos 3D para Windows Mixed Reality, hay algunos requisitos que todos los recursos deben cumplir: 
1. [Exportación: los](#exporting-models) recursos deben entregarse en el formato de archivo .glb (glTF binario)
2. [Modelado:](#modeling-guidelines) los recursos deben tener menos de 10 000 triángulos, no tener más de 64 nodos y 32 submeshes por LOD
3. [Materiales:](#material-guidelines) las texturas no pueden ser mayores que 4096 x 4096 y el mapa mip más pequeño no debe ser mayor que 4 en ninguna de las dimensiones.
4. [Animación:](#animation-guidelines) las animaciones no pueden tener más de 20 minutos a 30 FPS (36 000 fotogramas clave) y deben contener <= 8192 vértices de destino morph
5. [Optimización:](#optimizations) los recursos deben optimizarse mediante [WindowsMRAssetConverter.](https://github.com/Microsoft/glTF-Toolkit/releases) Obligatorio en Windows versiones del sistema operativo *<= 1709** y recomendado en Windows versiones del sistema operativo >= 1803

En el resto de este artículo se incluye información general detallada de estos requisitos y directrices adicionales para asegurarse de que los modelos funcionan bien con el Windows Mixed Reality inicio. 

## <a name="detailed-guidance"></a>Instrucciones detalladas

### <a name="exporting-models"></a>Exportación de modelos

El Windows Mixed Reality principal espera que los recursos 3D se entreguen con el formato de archivo .glb con imágenes incrustadas y datos binarios. Glb es la versión binaria del formato glTF, que es un estándar abierto gratuito de regalías para la entrega de recursos 3D que mantiene el grupo Degronos. A medida que glTF evoluciona como estándar del sector para contenido 3D interoperable, también lo hará la compatibilidad de Microsoft con el formato en Windows aplicaciones y experiencias. Si no ha creado un recurso glTF antes de encontrar una lista de exportadores y convertidores [admitidos](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) en la página de github del grupo de trabajo glTF.  

### <a name="modeling-guidelines"></a>Directrices de modelado

Windows espera que los recursos se generen mediante las siguientes directrices de modelado para garantizar la compatibilidad con la experiencia Mixed Reality inicio. Al modelar en el programa que prefiera, tenga en cuenta las siguientes recomendaciones y limitaciones:
1. El eje Up debe establecerse en "Y".
2. El recurso debe dar la cara "hacia delante" hacia el eje Z positivo.
3. Todos los recursos deben basarse en el plano del suelo en el origen de la escena (0,0,0).
4. Las unidades de trabajo deben establecerse en medidores y recursos para que los recursos se puedan crear a escala mundial.
5. No es necesario combinar todas las mallas, pero se recomienda si el destino son los dispositivos con recursos restringidos.
6. Todas las mallas deben compartir un material, y solo se usa un conjunto de texturas para todo el recurso.
7. Los UV se deben colocar en una disposición cuadrada en el espacio 0-1. Evite las texturas de tiling aunque están permitidas.
8. No se admiten varias UVS
9. No se admiten materiales de doble cara

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Recuentos de triángulos y niveles de detalle (LOD)

El Windows Mixed Reality inicio no admite modelos con más de 10 000 triángulos. Se recomienda trianfiar las mallas antes de exportar para asegurarse de que no superan este recuento. Windows MR también admite niveles opcionales de geometría de detalle (LOD) para garantizar una experiencia de alto rendimiento y alta calidad. [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) le ayudará a combinar tres versiones del modelo en un único modelo .glb. Windows determina qué LOD se va a mostrar en función de la cantidad de patrimonio de pantalla que está tomando el modelo. Solo se admiten 3 niveles de LOD con los siguientes recuentos de triángulos recomendados:
<br>

|  Nivel de LOD  |  Recuento de triángulos recomendado  |  Número máximo de triángulos | 
|------|------|------|
|  LOD 0 |  10 000 |  10 000 | 
|  LOD 1 |  5\.000  |  10 000 | 
|  LOD 2 |  2,500  |  10 000 | 

### <a name="node-counts-and-submesh-limits"></a>Recuentos de nodos y límites de submesh

El Windows Mixed Reality inicio no admite modelos con más de 64 nodos o 32 submeshes por LOD. Los nodos son un concepto de la [especificación glTF](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) que define los objetos de la escena. Las submeshes se definen en la matriz de [primitivas](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) en la malla del objeto . 

|  Característica |  Descripción  |  Máximo admitido | Documentación |
|------|------|------|------|
|  Nodos |  Objetos de la escena glTF |  64 por LOD | [Aquí](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  Suma de primitivas en todas las mallas |  32 por LOD | [Aquí](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Directrices de material

Las texturas deben prepararse mediante un flujo de trabajo de aspersividad de metal PBR. Empiece por crear un conjunto completo de texturas, como Albedo, Normal, Oclusión, Aserción y Aspersión. Windows Mixed Reality admite texturas con resoluciones de hasta 4096 x 4096, pero se recomienda crear a 512 x 512. Las texturas deben crearse con resoluciones en múltiplo de 4. Este es un requisito para el formato de compresión aplicado a las texturas en los pasos de exportación que se describen a continuación. Al generar mapas mip o una textura, el mip más bajo debe ser un máximo de 4x4.
<br>

|  Tamaño de textura recomendado  |  Tamaño máximo de textura | Mip más bajo
|----|----|----|
|  512x512  |  4096x4096 | max 4x4|

### <a name="albedo-base-color-map"></a>Mapa de Albedo (color base)

Color sin procesar sin información de iluminación. Este mapa también contiene la información de reflectancia y difuso para superficies de metal (blanco en el mapa plano) y de aislador (negro en el mapa plano) respectivamente.

### <a name="normal"></a>Normal

Mapa normal de espacio tangente

### <a name="roughness-map"></a>Mapa de aspersividad

Describe la microsuperficie del objeto. Blanco 1.0 es negro 0.0 aproximado es suave. Este mapa proporciona al recurso el mayor carácter, ya que realmente describe la superficie. Por ejemplo, scratches, fingerprints, smudges, scratche, and así sucesivamente.

### <a name="ambient-occlusion-map"></a>Mapa de oclusión ambiental

Mapa de escala de valores que muestra áreas de luz ocluida, que bloquea las reflexión

### <a name="metallic-map"></a>Mapa de mapa plano

Indica al sombreador si algo es metal o no. Raw Metal = 1,0 blanco no metal = 0,0 negro. Puede haber valores grises transitorios que indiquen algo que cubre el metal sin procesar, como la envoltura, pero en general este mapa solo debe ser blanco y negro.

## <a name="optimizations"></a>Optimizaciones

Windows Mixed Reality home ofrece una serie de optimizaciones sobre la especificación glTF principal definida mediante extensiones personalizadas. Estas optimizaciones son necesarias en Windows versiones <= 1709 y se recomiendan en las versiones más recientes de Windows. Puede optimizar fácilmente cualquier modelo glTF 2.0 mediante el convertidor Windows Mixed Reality [Asset Converter disponible en GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Esta herramienta realizará el empaquetado y las optimizaciones de textura correctos, tal y como se especifica a continuación. Para uso general, se recomienda usar WindowsMRAssetConverter, pero si necesita más control sobre la experiencia y desea crear su propia canalización de optimización, puede consultar la especificación detallada siguiente.  

> [!NOTE]
> Para obtener una lista definitiva de cuáles son las posibilidades de los límites exactos del modelo, consulte el artículo optimización de modelos [3D](/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) para su uso en aplicaciones de Dynamics 365.

### <a name="materials"></a>Materiales

Para mejorar el tiempo de carga de recursos en entornos Mixed Reality Windows MR admite la representación de texturas DDS comprimidas empaquetadas según el esquema de empaquetado de textura definido en esta sección. Se hace referencia a las texturas de DDS mediante MSFT_texture_dds [extensión](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). Se recomienda encarecidamente comprimir texturas. 

#### <a name="hololens"></a>HoloLens

HoloLens basadas en realidad mixta esperan que las texturas se empaqueten mediante una configuración de 2 texturas mediante la siguiente especificación de empaquetado:
<br>

|  GlTF (propiedad)  |  Textura  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRness  |  baseColorTexture  |  Rojo (R), verde (G), azul (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), Aspersividad (B), Metalosa (A) | 


Al comprimir las texturas de DDS, se espera la compresión siguiente en cada mapa:
<br>

|  Textura  |  Compresión esperada | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Cascos envolventes (VR)

Las experiencias de Windows Mixed Reality basadas en PC para cascos envolventes (VR) esperan que las texturas se empaqueten mediante una configuración de 3 texturas mediante la siguiente especificación de empaquetado:

##### <a name="windows-os--1803"></a>Windows Sistema operativo >= 1803

<br>

|  GlTF (propiedad)  |  Textura  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRness  |  baseColorTexture  |  Rojo (R), verde (G), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRnessMetallicTexture  |  Oclusión (R), Aspersión (G), Metal metalórnica (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Al comprimir las texturas de DDS, se espera la compresión siguiente en cada mapa:
<br>

|  Textura  |  Compresión esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows Sistema operativo <= 1709
<br>

|  GlTF (propiedad)  |  Textura  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRness  |  baseColorTexture  |  Rojo (R), verde (G), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Aspersión (R), metal metal (G), oclusión (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Al comprimir las texturas de DDS, se espera la compresión siguiente en cada mapa:
<br>

|  Textura  |  Compresión esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Adición de LOD de malla

Windows Mr usa los LOD de nodo de geometría para representar modelos 3D en diferentes niveles de detalle en función de la cobertura en pantalla. Aunque técnicamente esta característica no es necesaria, se recomienda para todos los recursos. Actualmente Windows admite 3 niveles de detalle. El LOD predeterminado es 0, que representa la calidad más alta. Otros LOD se numeran secuencialmente, por ejemplo, 1, 2 y se reducen progresivamente en calidad. El [Windows Mixed Reality Asset Converter](https://github.com/Microsoft/glTF-Toolkit/releases) admite la generación de recursos que cumplen esta especificación de LOD mediante la aceptación de varios modelos glTF y su combinación en un único recurso con niveles de LOD válidos. En la tabla siguiente se describen las ordenaciones de LOD y los destinos de triángulo esperados:
<br>

|  Nivel de LOD  |  Recuento de triángulos recomendado  |  Número máximo de triángulos | 
|-------|-------|-------|
|  LOD 0 |  10 000 |  10 000 | 
|  LOD 1 |  5\.000  |  10 000 | 
|  LOD 2 |  2,500  |  10 000 | 

Al usar los LOD, especifique siempre 3 niveles de LOD. Los LOD que faltan harán que el modelo no se represente de forma inesperada a medida que el sistema de LOD cambia al nivel de LOD que falta. glTF 2.0 no admite actualmente los LOD como parte de la especificación principal. Los LOD deben definirse mediante la [extensión MSFT_LOD .](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)

### <a name="screen-coverage"></a>Cobertura de pantalla

Los LOD se muestran en Windows Mixed Reality en función de un sistema controlado por el valor de cobertura de pantalla establecido en cada LOD. Los objetos que consumen actualmente una parte mayor del espacio de pantalla se muestran en un nivel de LOD superior. La cobertura de pantalla no forma parte de la especificación glTF 2.0 principal y debe especificarse mediante MSFT_ScreenCoverage en la sección "extras" de la extensión [MSFT_lod .](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)
<br>

|  Nivel de LOD  |  Intervalo recomendado  |  Intervalo predeterminado | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  0,5 | 
|  LOD 1 |  Menos del 50 % al 20 %  |  0,2 | 
|  LOD 2 |  Menos del 20 % al 1 %  |  0,01 | 
|  LOD 4  |  Por debajo del 1 %  |  - | 

## <a name="animation-guidelines"></a>Directrices de animación

> [!NOTE]
> Esta característica se agregó como parte de la actualización [de Windows 10 de abril de 2018.](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) En versiones anteriores de Windows estas animaciones no se reproducirán, pero se seguirán cargando si se crearon según las instrucciones de este artículo.  

La ambiente principal admite objetos glTF animados HoloLens cascos envolventes (VR). Si desea desencadenar animaciones en el modelo, deberá usar la extensión Mapa de animación en el formato glTF. Esta extensión le permite desencadenar animaciones en el modelo glTF en función de la presencia del usuario en el mundo; por ejemplo, desencadenar una animación cuando el usuario está cerca del objeto o mientras lo mira. Si el objeto glTF tiene animaciones, pero no define desencadenadores, las animaciones no se reproducirán. En la sección siguiente se describe un flujo de trabajo para agregar estos desencadenadores a cualquier objeto glTF animado.

### <a name="tools"></a>Herramientas

En primer lugar, descargue las siguientes herramientas si aún no las tiene. Estas herramientas le permitirán abrir fácilmente cualquier modelo glTF, obtener una vista previa de él, realizar cambios y volver a guardarlo como glTF o .glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Herramientas glTF para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Apertura y vista previa del modelo

Para empezar, abra el modelo glTF en VSCode arrastrando el archivo .glTF a la ventana del editor. Si tiene un archivo .glb en lugar de un archivo .glTF, puede importarlo en VSCode mediante el complemento glTF Tools que descargó. Vaya a "Ver -> Paleta de comandos" y, a continuación, comience a escribir "glTF" en la paleta de comandos y seleccione "glTF: Import from glb", que mostrará un selector de archivos con el que importar un .glb. 

Una vez que haya abierto el modelo glTF, debería ver el json en la ventana del editor. También puede obtener una vista previa del modelo en un visor 3D en directo haciendo clic con el botón derecho en el nombre de archivo y seleccionando el acceso directo del comando "glTF: Preview 3D Model" (glTF: Preview 3D Model) en el menú contextual. 

### <a name="adding-the-triggers"></a>Adición de los desencadenadores

Los desencadenadores de animación se agregan a glTF model JSON mediante la extensión Animation Map. La extensión de mapa de animación se documenta públicamente aquí [en GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (NOTA: ESTA ES UNA EXTENSIÓN DRAFT). Para agregar la extensión al modelo, desplácese hasta el final del archivo glTF en el editor y agregue el bloque "extensionsUsed" y "extensions" al archivo si aún no existen. En la sección "extensionsUsed", agregará una referencia a la extensión "EXT_animation_map" y, en el bloque "extensions", agregará las asignaciones a las animaciones del modelo.

Como se [indica en la](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) especificación, se define lo que desencadena la animación mediante la cadena "semántica" en una lista de "animaciones", que es una matriz de índices de animación. En el ejemplo siguiente, hemos especificado la animación que se va a reproducir mientras el usuario mira el objeto:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
La semántica de desencadenadores de animación siguiente es compatible con Windows Mixed Reality inicio.  
* "ALWAYS": bucle constante de una animación
* "HELD": se recorre en bucle durante todo el tiempo que se captura un objeto.
* "GAZE": bucle mientras se está observando un objeto
* "PROXIMITY": bucle mientras un visor está cerca de un objeto
* "POINTING": bucle mientras un usuario apunta a un objeto

### <a name="saving-and-exporting"></a>Guardar y exportar

Una vez que haya realizado los cambios en el modelo glTF, puede guardarlo directamente como glTF. También puede hacer clic con el botón derecho en el nombre del archivo en el editor y seleccionar "glTF: Exportar a GLB (archivo binario)" para exportar un .glb. 

### <a name="restrictions"></a>Restricciones

Las animaciones no pueden tener más de 20 minutos y no pueden contener más de 36 000 fotogramas clave (20 minutos a 30 FPS). Además, cuando se usan animaciones basadas en destinos de transformación, no superan los vértices de destino de morph 8192 o menos. Si se superan estos recuentos, el recurso animado no se admite en la Windows Mixed Reality principal. 

|Característica|Máxima|
|-----|-----|
|Duration|20 minutos|
|Fotogramas clave|36 000| 
|Morph Target Vertices|8192|

## <a name="gltf-implementation-notes"></a>Notas de implementación de glTF

Windows Mr no admite el volteo de geometría mediante escalas negativas. La geometría con escalas negativas probablemente dará como resultado artefactos visuales.

El recurso glTF DEBE apuntar a la escena predeterminada mediante el atributo de escena que va a representar Windows MR. Además, el cargador Windows mr glTF antes [de la actualización Windows 10 abril de 2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) requiere **los** accessors:
* Debe tener valores mínimos y máximos.
* El tipo SCALAR debe ser componentType UNSIGNED_SHORT (5123) o UNSIGNED_INT (5125).
* El tipo VEC2 y VEC3 deben ser componentType FLOAT (5126).

Las siguientes propiedades de material se usan desde la especificación glTF 2.0 principal, pero no son necesarias:
* baseColorFactor,factorfactor de metal, roughnessFactor
* baseColorTexture: debe apuntar a una textura almacenada en dds.
* emissiveTexture: debe apuntar a una textura almacenada en dds.
* emissiveFactor
* alphaMode

Las siguientes propiedades de material se omiten de la especificación principal:
* Todas las multi-UVs
* metalRoughnessTexture: en su lugar, debe usar el empaquetado de textura optimizado para Microsoft definido a continuación.
* normalTexture: en su lugar, debe usar el empaquetado de textura optimizado para Microsoft definido a continuación.
* normalScale
* occlusionTexture: en su lugar, debe usar el empaquetado de textura optimizado para Microsoft definido a continuación.
* occlusionStrength

Windows MR no admite líneas y puntos en modo primitivo. 

Solo se admite un único atributo de vértice UV.

## <a name="more-resources"></a>Más recursos

* [glTF Exporters and Converters](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [Especificación glTF 2.0](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Especificación de la extensión LOD de GlTF de Microsoft](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Especificación de extensiones Mixed Reality empaquetado de textura de PC](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Mixed Reality especificación de extensiones de empaquetado de textura](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Especificación de extensiones glTF de texturas DDS de Microsoft](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Consulte también

* [Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)](implementing-3d-app-launchers.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)