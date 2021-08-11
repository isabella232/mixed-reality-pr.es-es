---
title: 'Caso práctico: Escalado de Datascape entre dispositivos con un rendimiento diferente'
description: Este caso práctico ofrece información sobre cómo los desarrolladores de Microsoft han optimizado la aplicación Datascape para ofrecer una experiencia atractiva en todos los dispositivos con una variedad de funcionalidades de rendimiento.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: casco envolvente, optimización del rendimiento, REALIDAD virtual, caso práctico
ms.openlocfilehash: d1c54f5fbe6843f9bf61af20b611c6aeb22b0704c209bfdb555fe57b95805cf9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195800"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Caso práctico: Escalado de Datascape entre dispositivos con un rendimiento diferente

Datascape es una aplicación Windows Mixed Reality desarrollada internamente en Microsoft, donde nos centramos en mostrar datos meteorológicos sobre los datos del terreno. La aplicación explora la información única que los usuarios obtienen al detectar datos en realidad mixta rodeando al usuario con la visualización de datos holográficos.

Para Datascape, queríamos tener como destino una variedad de plataformas con diferentes funcionalidades de hardware, desde Microsoft HoloLens hasta cascos envolventes de Windows Mixed Reality, y desde equipos con menos tecnología hasta los equipos más recientes con GPU de gama alta. El desafío principal era representar nuestra escena en una materia visualmente atractiva en dispositivos con capacidades gráficas muy diferentes mientras se ejecutaba a una velocidad de fotogramas alta.

Este caso práctico le ayudará a analizar el proceso y las técnicas que se usan para crear algunos de nuestros sistemas con un uso intensivo de GPU, donde se describen los problemas que se han encontrado y cómo los superamos.

## <a name="transparency-and-overdraw"></a>Transparencia y sobredibuja

Nuestras principales dificultades de representación se tratan con la transparencia, ya que la transparencia puede ser costosa en una GPU.

La geometría sólida se puede representar de frente a atrás mientras se escribe en el búfer de profundidad, lo que impide que se descarten los píxeles futuros ubicados detrás de ese píxel. Esto evita que los píxeles ocultos ejecuten el sombreador de píxeles, lo que acelera significativamente el proceso. Si la geometría está ordenada de forma óptima, cada píxel de la pantalla se dibujará solo una vez.

La geometría transparente debe ordenarse hacia delante y se basa en combinar la salida del sombreador de píxeles con el píxel actual de la pantalla. Esto puede dar lugar a que cada píxel de la pantalla se dibuja varias veces por fotograma, lo que se conoce como sobred dibujo.

En HoloLens equipos estándar y estándar, la pantalla solo se puede rellenar varias veces, lo que hace que la representación transparente sea problemática.

## <a name="introduction-to-datascape-scene-components"></a>Introducción a los componentes de la escena de Datascape

Hemos tenido tres componentes principales en nuestra escena. **la interfaz de usuario, el mapa** y **el tiempo**. Sabíamos al principio que los efectos meteorológicos requerirían todo el tiempo de GPU que podía obtener, por lo que diseñamos a propósito la interfaz de usuario y el terreno de una manera que reduciría cualquier sobredesdibujado.

Hemos rediseñado la interfaz de usuario varias veces para minimizar la cantidad de sobredestrabajo que produciría. Hemos errado en el lado de una geometría más compleja en lugar de superponer el arte transparente entre sí para componentes como botones brillantes e información general del mapa.

Para el mapa, se usa un sombreador personalizado que elimina las características estándar de Unity, como sombras e iluminación compleja, y las reemplaza por un modelo de iluminación solar simple y un cálculo personalizado de la solería. Esto produjo un sombreador de píxeles simple y libera ciclos de GPU.

Hemos conseguido que tanto la interfaz de usuario como el mapa se representaran en el presupuesto, donde no se necesitaban cambios en ellos en función del hardware. sin embargo, la visualización meteorológica, en particular la representación en la nube, ha demostrado ser más un desafío.

## <a name="background-on-cloud-data"></a>Información general sobre los datos en la nube

Nuestros datos en la nube se descargaron de los servidores NOAA ( y llegaron a nosotros en tres capas 2D distintas, cada una con la altura superior e inferior de la nube, así como la densidad de la nube para cada celda de la https://nomads.ncep.noaa.gov/) cuadrícula. Los datos se procesaron en una textura de información de nube donde cada componente se almacenaba en el componente rojo, verde y azul de la textura para facilitar el acceso en la GPU.

## <a name="geometry-clouds"></a>Nubes de geometría

Para asegurarnos de que nuestras máquinas de menor potencia pudieran representar nuestras nubes, decidimos comenzar con un enfoque que usaría geometría sólida para minimizar el sobredesbo.

Primero intentamos generar nubes mediante la generación de una malla de mapa de altura sólida para cada capa mediante el radio de la textura de información de la nube por vértice para generar la forma. Hemos usado un sombreador de geometría para generar los vértices tanto en la parte superior como en la parte inferior de la nube, generando formas de nube sólidas. Hemos usado el valor de densidad de la textura para colorear la nube con colores más oscuros para nubes más densas.

**Sombreador para crear los vértices:**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

Hemos introducido un pequeño patrón de ruido para obtener más detalles sobre los datos reales. Para generar bordes de nube redondeados, recortamos los píxeles del sombreador de píxeles cuando el valor de radio interpolado alcanza un umbral para descartar valores cercanos a cero.

![Nubes de geometría](images/datascape-geometry-clouds-700px.jpg)

Dado que las nubes son de geometría sólida, se pueden representar antes que el terreno para ocultar los píxeles de mapa costosos debajo para mejorar aún más la velocidad de fotogramas. Esta solución se ejecutó correctamente en todas las tarjetas gráficas, desde la especificación mínima hasta las tarjetas gráficas de gama alta, así como en HoloLens, debido al enfoque sólido de representación de geometría.

## <a name="solid-particle-clouds"></a>Nubes de partículas sólidas

Ahora teníamos una solución de copia de seguridad que producía una representación aceptable de los datos en la nube, pero estaba un poco desconfiada en el factor "wow" y no transmitía la sensación volumétrica que queríamos para nuestras máquinas de gama alta.

El siguiente paso fue crear las nubes al representarlas con aproximadamente 100 000 partículas para generar una apariencia más orgánica y volumétrica.

Si las partículas permanecen sólidas y se ordenan de frente a atrás, todavía podemos beneficiarnos de la selección del búfer de profundidad de los píxeles detrás de las partículas que se representaron previamente, lo que reduce el sobredibujado. Además, con una solución basada en partículas, podemos modificar la cantidad de partículas que se usan para dirigirse a hardware diferente. Sin embargo, todavía es necesario probar la profundidad de todos los píxeles, lo que da lugar a una sobrecarga adicional.

En primer lugar, creamos posiciones de partícula alrededor del punto central de la experiencia en el inicio. Distribuymos las partículas de forma más densa alrededor del centro y menos en la distancia. Hemos ordenado previamente todas las partículas del centro a la parte posterior para que las partículas más cercanas se represente primero.

Un sombreador de proceso muestrearía la textura de información de la nube para colocar cada partícula en una altura correcta y colore según la densidad.

Hemos usado *DrawProcedural para* representar un cuadrándular por partícula, lo que permite que los datos de partícula permanezcan en la GPU en todo momento.

Cada partícula contenía una altura y un radio. El alto se basaba en los datos en la nube muestreados de la textura de información de la nube y el radio se basaba en la distribución inicial donde se calcularía para almacenar la distancia horizontal a su vecino más cercano. Los cuadrángulos usarían estos datos para orientarse en ángulo según la altura, de modo que cuando los usuarios los vean horizontalmente, se mostraría la altura y, cuando los usuarios los mirasan de arriba abajo, se cubriría el área entre sus vecinos.

![Forma de partícula](images/particle-shape-700px.png)

**Código de sombreador que muestra la distribución:**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

Dado que ordenamos las partículas de frente a atrás y seguimos utilizando un sombreador de estilo sólido para recortar (no mezclar) píxeles transparentes, esta técnica controla una cantidad sorprendente de partículas, lo que evita un costoso exceso de dibujo incluso en las máquinas de menor potencia.

## <a name="transparent-particle-clouds"></a>Nubes de partículas transparentes

Las partículas sólidas proporcionaron una buena sensación orgánica a la forma de las nubes, pero todavía necesitaban algo para vender la fluffiness de las nubes. Hemos decidido probar una solución personalizada para las tarjetas gráficas de gama alta, donde podemos introducir transparencia.

Para ello, simplemente cambiamos el criterio de ordenación inicial de las partículas y cambiamos el sombreador para usar las texturas alfa.

![Nubes esponjosas](images/fluffy-clouds-700px.jpg)

Tenía un aspecto excelente, pero resultaba demasiado pesado incluso para las máquinas más difíciles, ya que daría lugar a la representación de cada píxel en la pantalla cientos de veces.

## <a name="render-off-screen-with-lower-resolution"></a>Representación fuera de pantalla con una resolución inferior

Para reducir el número de píxeles representados por las nubes, empezamos a representarlos en un búfer de resolución trimestral (en comparación con la pantalla) y a extender el resultado final de nuevo a la pantalla después de que se hubieran dibujado todas las partículas. Esto nos dio aproximadamente una aceleración de cuatro veces, pero llegó con un par de advertencias.

**Código para la representación fuera de pantalla:**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

En primer lugar, cuando se representa en un búfer fuera de la pantalla, se pierde toda la información de profundidad de la escena principal, lo que da lugar a la representación de partículas detrás de las montañas en la parte superior de la montaña.

En segundo lugar, al extender el búfer también se introdujeron artefactos en los bordes de nuestras nubes donde se apreciaba el cambio de resolución. En las dos secciones siguientes se explica cómo se resuelven estos problemas.

## <a name="particle-depth-buffer"></a>Búfer de profundidad de partícula

Para que las partículas coexistieran con la geometría mundial donde una montaña u objeto podría cubrir las partículas que hay detrás, rellenamos el búfer fuera de pantalla con un búfer de profundidad que contiene la geometría de la escena principal. Para generar este búfer de profundidad, creamos una segunda cámara, que representa solo la geometría sólida y la profundidad de la escena.

A continuación, se usa la nueva textura en el sombreador de píxeles de las nubes para occluir píxeles. Hemos usado la misma textura para calcular la distancia a la geometría detrás de un píxel de nube. Al usar esa distancia y aplicarla al alfa del píxel, ahora hemos tenido el efecto de que las nubes se desvanecien a medida que se acercan al terreno, lo que elimina los cortes duros donde se encuentran las partículas y el terreno.

![Nubes mezcladas en terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Afilar los bordes

Las nubes con extensión eran casi idénticas a las nubes de tamaño normal en el centro de las partículas o donde se superponen, pero mostraban algunos artefactos en los bordes de la nube. De lo contrario, los bordes nítidos aparecerán desenfocados y los efectos de alias se introdujeron cuando se movió la cámara.

Hemos resuelto esto mediante la ejecución de un sombreador simple en el búfer fuera de pantalla para determinar dónde se produjeron grandes cambios en contraste (1). Colocamos los píxeles con grandes cambios en un nuevo búfer de galería de símbolos (2). A continuación, se usa el búfer de galería de símbolos para enmascarar estas áreas de contraste alto al volver a aplicar el búfer fuera de la pantalla a la pantalla, lo que produce huecos en las nubes (3).

A continuación, se representan todas las partículas de nuevo en modo de pantalla completa, pero esta vez se usa el búfer de galería de símbolos para enmascarar todo menos los bordes, lo que da lugar a un conjunto mínimo de píxeles tocados (4). Puesto que el búfer de comandos ya se creó para las partículas, simplemente tuvimos que representarlo de nuevo en la nueva cámara.

![Progresión de los bordes de la nube de representación](images/cloud-steps-1-4-700px.jpg)

El resultado final fueron bordes nítidos con secciones centrales baratas de las nubes.

Aunque esto era mucho más rápido que representar todas las partículas en pantalla completa, todavía hay un costo asociado a la prueba de un píxel en el búfer de galería de símbolos, por lo que una gran cantidad de sobredesdeñamiento sigue teniendo un costo.

## <a name="culling-particles"></a>Culling particles

Para nuestro efecto de viento, generamos franjas de triángulos largos en un sombreador de proceso, lo que creaba muchas wisps de viento en el mundo. Aunque el efecto del viento no fue pesado en la tasa de relleno debido a las franjas de rellenado generadas, generó muchos cientos de miles de vértices, lo que provocó una carga pesada para el sombreador de vértices.

Hemos introducido búferes de anexo en el sombreador de proceso para alimentar un subconjunto de las franjas de viento que se dibujarán. Con alguna lógica de selección de frustum de vista simple en el sombreador de proceso, podríamos determinar si una franja estaba fuera de la vista de la cámara e impedir que se agregara al búfer de inserción. Esto redujo significativamente la cantidad de franjas, liberando algunos ciclos necesarios en la GPU.

**Código que muestra un búfer de anexos:**

*Sombreador de proceso:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*Código de C#:*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

Hemos intentado usar la misma técnica en las partículas de la nube, donde las crearíamos en el sombreador de proceso y solo insertaríamos las partículas visibles que se representarán. En realidad, esta técnica no nos ahorraba mucho en la GPU, ya que el cuello de botella más grande era la cantidad de píxeles representados en la pantalla y no el costo de calcular los vértices.

El otro problema con esta técnica era que el búfer de anexos se rellenaba en orden aleatorio debido a su naturaleza paralelizada de calcular las partículas, lo que provocaba que las partículas ordenadas no se ordenaran, lo que provocaba el parpadeo de las partículas de la nube.

Existen técnicas para ordenar el búfer de inserción, pero es probable que la cantidad limitada de ganancia de rendimiento que se obtiene de las partículas de la selección se desplazaría con una ordenación adicional, por lo que decidimos no llevar a cabo esta optimización.

## <a name="adaptive-rendering"></a>Representación adaptable

Para garantizar una velocidad de fotogramas estable en una aplicación con distintas condiciones de representación, como una vista en la nube frente a una vista clara, hemos introducido la representación adaptable en nuestra aplicación.

El primer paso de la representación adaptable es medir la GPU. Para ello, insertamos código personalizado en el búfer de comandos de GPU al principio y al final de un fotograma representado, capturando el tiempo de la pantalla del ojo izquierdo y derecho.

Al medir el tiempo dedicado a la representación y compararlo con la frecuencia de actualización deseada, hemos conseguido una idea de lo cerca que estabamos de quitar fotogramas.

Cuando estamos cerca de quitar fotogramas, adaptamos nuestra representación para que sea más rápida. Una manera sencilla de adaptarse es cambiar el tamaño de la ventanilla de la pantalla, lo que requiere que se represente menos píxeles.

Mediante *UnityEngine.XR.XRSettings.renderViewportScale,* el sistema reduce la ventanilla de destino y ajusta automáticamente el resultado para ajustarlo a la pantalla. Un pequeño cambio en la escala es apenas perceptible en la geometría mundial y un factor de escala de 0,7 requiere la mitad de la cantidad de píxeles que se representará.

![Escala del 70 %, la mitad de los píxeles](images/datascape-scaling-700px.jpg)

Cuando detectamos que estamos a punto de quitar fotogramas, se reduce la escala en un número fijo y se vuelve a aumentar cuando se vuelve a ejecutar lo suficientemente rápido.

Aunque hemos decidido qué técnica de nube usar en función de las funcionalidades gráficas del hardware en el inicio, es posible basarse en los datos de la medida de GPU para evitar que el sistema se quede en una resolución baja durante mucho tiempo, pero esto es algo que no hemos tenido tiempo de explorar en Datascape.

## <a name="final-thoughts"></a>Consideraciones finales

Dirigirse a una variedad de hardware es complicado y requiere cierta planeación.

Se recomienda empezar a dirigirse a máquinas de menor potencia para familiarizarse con el espacio de problemas y desarrollar una solución de copia de seguridad que se ejecutará en todas las máquinas. Diseñe la solución con la tasa de relleno en mente, ya que los píxeles serán el recurso más valioso. Geometría sólida de destino sobre transparencia.

Con una solución de copia de seguridad, puede empezar a crear capas en mayor complejidad para máquinas de gama alta o quizás simplemente mejorar la resolución de la solución de copia de seguridad.

Diseñe para los peores escenarios y considere la posibilidad de usar la representación adaptable para situaciones intensas.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Querese</b><br>Ingeniero de software @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Ingeniero de software @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Consulte también
* [Descripción del rendimiento de Mixed Reality](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Rendimiento Recomendaciones para Unity](../develop/unity/performance-recommendations-for-unity.md)

 
