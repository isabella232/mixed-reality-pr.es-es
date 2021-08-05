---
title: Criterios de calidad de aplicaciones
description: En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criterios de calidad de la aplicación, realidad mixta, aplicación de realidad mixta, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual
ms.openlocfilehash: 858b0782c4e6754ee6753d463d5fe498e3a893f6c21b3f1c86ac14f8c0e6c8cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189392"
---
# <a name="app-quality-criteria"></a>Criterios de calidad de aplicaciones

En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta. Para cada factor, se proporciona la siguiente información
* Información general: una breve descripción del factor de calidad y por qué es importante.
* Impacto en el dispositivo: qué tipo de ventana Mixed Reality dispositivo se ve afectado.
* Criterios de calidad: cómo evaluar el factor de calidad.
* Cómo medir: métodos para medir (o experimentar) el problema.
* Recomendaciones: resumen de los enfoques para proporcionar una mejor experiencia de usuario.
* Recursos: recursos pertinentes para desarrolladores y diseño que son útiles para crear mejores experiencias de aplicación.

## <a name="frame-rate"></a>Velocidad de fotogramas

La velocidad de fotogramas es el primer pilar de la estabilidad del holograma y la comodidad del usuario. La velocidad de fotogramas por debajo de los destinos recomendados puede hacer que los hologramas parezcan vibración, lo que afecta negativamente a la facilidad de proceso de la experiencia y puede provocar la agotamiento de los ojos. La velocidad de fotogramas objetivo para su experiencia en cascos envolventes de Windows Mixed Reality es de 60 Hz o 90 Hz, dependiendo de Windows Mixed Reality equipos compatibles que admita. Por HoloLens, la velocidad de fotogramas objetivo es de 60 Hz.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
| La aplicación cumple constantemente el objetivo de fotogramas por segundo (FPS) para el dispositivo de destino: 60 fps en HoloLens; 90 fps en equipos Ultra; y 60 fps en equipos estándar. | La aplicación tiene caídas intermitentes de fotogramas que no impiden la experiencia principal o FPS es constantemente menor que el objetivo deseado, pero no impide la experiencia de la aplicación. | La aplicación experimenta una caída en la velocidad de fotogramas de media cada 10 segundos o menos. |

### <a name="how-to-measure"></a>Cómo medir

* El gráfico de velocidad de fotogramas en tiempo real se proporciona a través [Windows Portal de dispositivos](using-the-windows-device-portal.md#system-performance) en "Rendimiento del sistema".
* Para la depuración de desarrollo, agregue un contador de diagnóstico de velocidad de fotogramas a la aplicación. Consulte Recursos para obtener un contador de ejemplo.
* Las caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras se ejecuta la aplicación moviendo la cabeza de lado a lado. Si el holograma muestra un movimiento de vibración inesperado, es probable que la causa sea una velocidad de fotogramas baja o el plano de estabilidad.

### <a name="recommendations"></a>Recomendaciones

* Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.
* Los cambios que incurren en una caída en la velocidad de fotogramas deben evaluarse y resolverse correctamente como un error de rendimiento.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Descripción del rendimiento de Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Estabilidad del holograma y velocidad de fotogramas](hologram-stability.md#frame-rate)
* [Presupuesto de rendimiento de recursos](../../design/asset-creation-process.md)
* [Recomendaciones de rendimiento para Unity](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Mixed Reality Toolkit, pantalla del contador fps](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [Mixed Reality Toolkit, Sombreadores](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Referencias externas

* [Unity, optimización de aplicaciones móviles](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Estabilidad de hologramas

Los hologramas estables aumentarán la facilidad de uso y facilidad de uso de la aplicación y crearán una experiencia de visualización más cómoda para el usuario. La calidad de la estabilidad del holograma es el resultado de un buen desarrollo de aplicaciones y la capacidad del dispositivo para comprender (realizar un seguimiento) de su entorno. Aunque la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar a la estabilidad, entre los que se incluyen:

* Uso del plano de estabilización
* Distancia a los delimitadores espaciales
* Seguimiento

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  Hologramas parecen estables de forma coherente. | El contenido secundario muestra un movimiento inesperado; o un movimiento inesperado no impide la experiencia general de la aplicación. | El contenido principal en el marco muestra un movimiento inesperado. |

### <a name="how-to-measure"></a>Cómo medir

Mientras se lleva el dispositivo y se ve la experiencia:

* Mueva la cabeza de lado a lado. Si los hologramas muestran un movimiento inesperado, la causa probable es una baja velocidad de fotogramas o una alineación incorrecta del plano de estabilidad con el plano focal.
* Moverse por los hologramas y el entorno, busque comportamientos como el bañador y el salto. Es probable que este tipo de movimiento se deba a que el dispositivo no hace el seguimiento del entorno o a la distancia al delimitador espacial.
* Si hay hologramas grandes o varios en el marco, observe el comportamiento del holograma en varias profundidades mientras mueve la posición de la cabeza de lado a lado, si aparece la inestabilidad, es probable que se deba al plano de estabilización.

### <a name="recommendations"></a>Recomendaciones

* Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.
* Use el plano de estabilización.
* Represente siempre hologramas delimitados en un radio de 3 metros de su anclaje.
* Asegúrese de que el entorno está configurado para el seguimiento adecuado.
* Diseñe su experiencia para evitar hologramas en varios niveles de profundidad focal dentro del marco.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Estabilidad del holograma y velocidad de fotogramas](hologram-stability.md#frame-rate)
* [Caso práctico, Uso del plano de estabilización](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Descripción del rendimiento de Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](../unity/performance-recommendations-for-unity.md)
* [Delimitadores espaciales](../../design/spatial-anchors.md)
* [Control de errores de seguimiento](../../design/coordinate-systems.md#handling-tracking-errors)
* [Marco de referencia estacionario](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Kit complementario de MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Hologramas posición en superficies reales

Las desalineaciones de hologramas con objetos físicos (si se pretende colocar en relación entre sí) son una indicación clara de la no unión de hologramas y del mundo real. La precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; Por ejemplo, la colocación de la superficie general puede usar el mapa espacial, pero una colocación más precisa requerirá cierto uso de marcadores y calibración.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
| Hologramas alinean con la superficie normalmente en el intervalo de pulgadas a pulgadas. Si necesita más precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación. | N/D | Los hologramas parecen no alineados con el objeto de destino físico al dividir el plano de la superficie o parece que flotan fuera de la superficie. Si se requiere precisión, Hologramas debe cumplir la especificación de proximidad del escenario. | 

### <a name="how-to-measure"></a>Cómo medir

* Hologramas que se colocan en el mapa espacial no deberían parecer flotantes drásticamente por encima o por debajo de la superficie.
* Hologramas que requieren una colocación precisa debe tener algún tipo de sistema de marcador y calibración que sea preciso para el requisito del escenario.

### <a name="recommendations"></a>Recomendaciones

* El mapa espacial es útil para colocar objetos en superficies cuando no se requiere precisión.
* Para obtener la mejor precisión, use marcadores o pósteres para establecer los hologramas y un controlador de Xbox (o algún mecanismo de alineación manual) para la calibración final.
* Considere la posibilidad de dividir hologramas extra grandes en partes lógicas y alinear cada parte con la superficie.
* Establecer incorrectamente la distancia interpupillaria (IPD) también puede tener efecto en la alineación del holograma. Configure siempre HoloLens en el IPD del usuario.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Colocación de asignación espacial](../../design/spatial-mapping.md#placement)
* [Proceso de examen de sala](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Procedimientos recomendados de anclajes espaciales](../../design/spatial-anchors.md#best-practices)
* [Control de errores de seguimiento](../../design/coordinate-systems.md#handling-tracking-errors)
* [Asignación espacial en Unity](../unity/spatial-mapping-in-unity.md)
* [Introducción al desarrollo de Vuforia](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Bibliotecas Toolkit, asignaciones espaciales](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Kit complementario de MR, ejemplo de calibración de póster](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Kit complementario de MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Referencias externas

* [Caso práctico de lowes, alineación de precisión](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Ver zona de confort

Los desarrolladores de aplicaciones controlan dónde convergen los ojos de los usuarios colocando contenido y hologramas en varias profundidades. Los usuarios que usan HoloLens siempre se alojarán a 2,0 m para mantener una imagen clara porque las pantallas HoloLens se fijan a una distancia óptica aproximada de 2,0 m del usuario. Una profundidad de contenido incorrecta puede provocar molestias visuales o agotamiento.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

<table>
<tr>
<td> Óptima </td><td><ul>
<li>Coloque el contenido a 2 m.</li><li>Cuando no se pueden colocar hologramas a 2 m y no se pueden evitar conflictos entre la convergencia y el alojamiento, la zona óptima para la colocación del holograma está entre 1,25 m y 5 m.</li><li>En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar a más de 1 m de distancia (por ejemplo, ajustar el tamaño del contenido y los parámetros de selección de ubicación predeterminados).</li><li>A menos que no lo requiera el escenario, se debe implementar un plano de recorte con atenuación a partir de 1 m.</li><li>En los casos en los que se requiere una observación más cercana de un holograma sin movimiento, el contenido no debe estar más cerca de 50 cm.</li>
</ul></td>
</tr><tr>
<td> Cumple</td><td> El contenido está dentro de la guía de visualización y movimiento, pero el uso no es incorrecto o no se usa el plano de recorte.</td>
</tr><tr>
<td> Suspenso </td><td> El contenido se presenta demasiado cerca (normalmente &lt; 1,25 m o 50 cm para hologramas estacionados que requieren &lt; una observación más cercana).</td>
</tr>
</table>

### <a name="how-to-measure"></a>Cómo medir

* Normalmente, el contenido debe estar a 2 m de distancia, pero no más cerca de 1,25 o más de 5 m.
* Con algunas excepciones, la distancia de representación HoloLens recorte debe establecerse en 85 CM con atenuación de contenido a partir de 1 m. Aproximarse al contenido y observe el efecto del plano de recorte.
* El contenido stationary no debe estar más cerca de 50 cm de distancia.

### <a name="recommendations"></a>Recomendaciones

* Diseño de contenido para una distancia de visualización óptima de 2 m.
* Establezca la distancia de representación del recorte en 85 cm con atenuación del contenido a partir de 1 m.
* En el caso de los hologramas estacionados que necesitan una visualización más cercana, el plano de recorte no debe estar más cerca de 30 cm y el atenuado debe comenzar al menos a 10 cm de distancia del plano de recorte.

### <a name="resources"></a>Recursos

* [Distancia de representación](hologram-stability.md#hologram-render-distances)
* [Punto de enfoque en Unity](../unity/focus-point-in-unity.md)
* [Experimentación con la escala](../../design/scale.md#experimenting-with-scale)
* [Texto, tamaño de fuente recomendado](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a>Cambio de profundidad

Independientemente de la zona de visualización de problemas de confort, la demanda de que el usuario cambie con frecuencia o rápidamente entre objetos focales cercanos y lejanos (incluidos los hologramas y el contenido real) puede provocar una agotamiento oculotricio y una incomodidad general.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  Cambio de profundidad limitado o natural que no hace que el usuario vuelva a centrarse de forma natural. | Cambio de profundidad brusco que es básico y está diseñado en la experiencia de la aplicación, o cambio de profundidad brusco causado por contenido inesperado del mundo real. | Cambio de profundidad coherente o cambio de profundidad brusco que no es necesario o básico para la experiencia de la aplicación. | 

### <a name="how-to-measure"></a>Cómo medir

* Si la aplicación requiere que el usuario cambie de forma coherente o repentina el foco de profundidad, hay un problema de cambio de profundidad.

### <a name="recommendations"></a>Recomendaciones

* Mantenga el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal. Esto mitigará la agotamiento oculotricio y el movimiento inesperado del holograma.

### <a name="resources"></a>Recursos

* [Distancia de representación](hologram-stability.md#hologram-render-distances)
* [Punto de enfoque en Unity](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso de sonido espacial

En Windows Mixed Reality, el motor de audio proporciona el componente de sonido de la experiencia de realidad mixta mediante la simulación de sonido 3D mediante simulaciones de dirección, distancia y entorno. El uso de sonido espacial en una aplicación permite a los desarrolladores colocar sonidos en un espacio tridimensional (esfera) alrededor del usuario. Después, esos sonidos parecerán procedentes de objetos físicos reales o hologramas de realidad mixta en el entorno del usuario. El sonido espacial es una herramienta eficaz para la accesibilidad, la accesibilidad y el diseño de la experiencia de usuario en aplicaciones de realidad mixta.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  El sonido está espacializado lógicamente y la experiencia de usuario usa adecuadamente el sonido para ayudar con la detección de objetos y los comentarios de los usuarios. El sonido es natural y relevante para los objetos y se normaliza en todo el escenario. | El audio espacial se usa adecuadamente para la capacidad de intabilidad, pero falta como medio para ayudar con los comentarios y la detectabilidad del usuario. | El sonido no se espacializa según lo previsto o falta de sonido para ayudar al usuario dentro de la experiencia de usuario. O bien, el audio espacial no se consideró ni se usó en el diseño del escenario. | 

### <a name="how-to-measure"></a>Cómo medir

* En general, los sonidos pertinentes deben emitirse desde hologramas de destino (por ejemplo, sonido de sonido procedente de perro holográfico).
* Las indicaciones de sonido se deben usar en toda la experiencia de usuario para ayudar al usuario a recibir comentarios o conocer las acciones fuera del marco holográfico.

### <a name="recommendations"></a>Recomendaciones

* Use audio espacial para ayudar con la detección de objetos y las interfaces de usuario.
* Los sonidos reales funcionan mejor que el sonido sintetizado o no natural.
* La mayoría de los sonidos deben espacializarse.
* Evite emisores invisibles.
* Evite el enmascaramiento espacial.
* Normalizar todos los sonidos.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Sonido espacial](../../design/spatial-sound.md)
* [Diseño de sonido espacial](../../design/spatial-sound-design.md)
* [Sonido espacial en Unity](../unity/spatial-sound-in-unity.md)
* [Caso práctico, sonido espacial para HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Caso práctico, Uso de sonido espacial en RoboRaid](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Mixed Reality Toolkit: audio espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Centrarse en los límites del marco holográfico (FOV)

Las experiencias de usuario bien diseñadas pueden crear y mantener un contexto útil del entorno virtual que se extiende alrededor de los usuarios. La mitigación del efecto de los límites de FOV implica un diseño cuidadoso de la escala de contenido y el contexto, el uso de audio espacial, sistemas de guía y la posición del usuario. Si se hace correctamente, el usuario se verá menos afectado por los límites de FOV mientras tiene una experiencia de aplicación cómoda.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  El usuario nunca pierde el contexto y la visualización es cómoda. Se proporciona asistencia de contexto para objetos grandes. Se proporcionan instrucciones de detectabilidad y visualización para objetos fuera del marco. En general, el diseño de movimiento y la escala de los hologramas son adecuados para una experiencia de visualización cómoda. | El usuario nunca pierde el contexto, pero es posible que se requiera movimiento adicional en situaciones limitadas. En situaciones limitadas, la escala hace que los hologramas quiebren el marco vertical u horizontal, lo que provoca cierto movimiento de cuello para ver los hologramas. | Es probable que el usuario pierda el contexto o que se requiera un movimiento de cuello coherente para ver los hologramas. No hay instrucciones de contexto para objetos holográficos grandes, mover objetos fáciles de perder fuera del marco sin instrucciones de detectabilidad o hologramas altos requiere movimiento regular de cuello para ver. | 

### <a name="how-to-measure"></a>Cómo medir

* El contexto de un holograma (grande) se pierde o no se entiende debido a que se recorta en los límites.
* Las ubicaciones de hologramas son difíciles de encontrar debido a la falta de atención de directores o contenido que entra y sale rápidamente del marco holográfico.
* El escenario requiere un movimiento de la cabeza regular y repetitivo hacia arriba y hacia abajo para ver completamente un holograma, lo que da lugar a la agotamiento del cuello.

### <a name="recommendations"></a>Recomendaciones

* Comience la experiencia con objetos pequeños que se ajusten a la FOV y, a continuación, haga la transición con indicaciones visuales a versiones más grandes.
* Use audio espacial y directores de atención para ayudar al usuario a encontrar contenido que está fuera de la FOV.
* En la medida de lo posible, evite hologramas que recorten verticalmente la FOV.
* Proporcione al usuario instrucciones en la aplicación para obtener la mejor ubicación de visualización.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Marco holográfico](../../design/holographic-frame.md)
* [Caso práctico, aprendizajes HoloStudio diseño de interfaz de usuario e interacción](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Escala de objetos y entornos](../../design/scale.md)
* [Cursores, indicaciones visuales](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a>Referencias externas

* [Mucho trabajo sobre la FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>El contenido reacciona a la posición del usuario

Hologramas debe reaccionar a la posición del usuario aproximadamente de la misma manera que lo hacen los objetos "reales". Una consideración de diseño importante son los elementos de la interfaz de usuario que no pueden suponer necesariamente que la posición de un usuario es inmóvil y se adapta al movimiento del usuario. El diseño de una aplicación que se adapte correctamente a la posición del usuario creará una experiencia más fácil de usar.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

<table>
<tr>
<td> Óptima </td><td> El contenido y la interfaz de usuario se adaptan a las posiciones del usuario, lo que permite al usuario interactuar de forma natural con el contenido dentro del ámbito del movimiento esperado del usuario.</td>
</tr><tr>
<td> Cumple </td><td> La interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista del contenido clave que requiere que el usuario ajuste su posición.</td>
</tr><tr>
<td> Suspenso </td><td><ol>
<li>Los elementos de la interfaz de usuario se pierden o bloquean durante el movimiento, lo que hace que el usuario vuelva (o busque) de forma no natural a los controles.</li><li>Los elementos de la interfaz de usuario limitan la vista del contenido principal.</li><li>El movimiento de la interfaz de usuario no está optimizado para ver la distancia y el impulso, especialmente con los elementos de la interfaz <a href="../../design/billboarding-and-tag-along.md">de usuario de</a> etiqueta.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Cómo medir

* Todas las medidas deben realizarse dentro de un ámbito razonable del escenario. Aunque el movimiento del usuario variará, no intentes engañar la aplicación con un movimiento extremo del usuario.
* Para los elementos de la interfaz de usuario, los controles pertinentes deben estar disponibles independientemente del movimiento del usuario. Por ejemplo, si el usuario está viendo y recorrindo un mapa 3D con zoom, el control de zoom debe estar disponible para el usuario independientemente de la ubicación.

### <a name="recommendations"></a>Recomendaciones

* El usuario es la cámara y controla el movimiento. Déjelos conducir.
* Considere la posibilidad de usar sistemas de texto y menús que, de lo contrario, estarían bloqueados por el mundo o se ocultarían si un usuario se desplazara.
* Use la etiqueta junto para el contenido que necesita seguir al usuario, a la vez que permite al usuario ver lo que hay delante de él.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Diseño de la interacción](../../discover/hologram.md)
* [Color, luz y material](../../design/color-light-and-materials.md)
* [Etiquetado y vista frontal continua](../../design/billboarding-and-tag-along.md)
* [Interacciones instintivas](../../design/interaction-fundamentals.md)
* [Automovimiento y locomoción del usuario](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a>Claridad de interacción de entrada

La claridad de la interacción de entrada es fundamental para la facilidad de uso de una aplicación e incluye coherencia de entrada, capacidad de enfoque y detectabilidad de los métodos de interacción. El usuario puede usar interacciones comunes para toda la plataforma sin volver a aprender. Si la aplicación tiene una entrada personalizada, debe comunicarse y demostrarse claramente.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  Los métodos de interacción de entrada son coherentes con Windows Mixed Reality [instrucciones proporcionadas.](../../design/interaction-fundamentals.md) Cualquier entrada personalizada no debe ser redundante con la entrada estándar (en su lugar, usar la interacción estándar) y debe comunicarse claramente y demostrarse al usuario. | De forma similar a la mejor, pero las entradas personalizadas son redundantes con los métodos de entrada estándar. El usuario todavía puede lograr el objetivo y el progreso a través de la experiencia de la aplicación. | Difícil de entender el método de entrada o la asignación de botones. La entrada está muy personalizada, no admite la entrada estándar, no tiene instrucciones o es probable que cause problemas de agotamiento y confort. | 

### <a name="how-to-measure"></a>Cómo medir

* La aplicación usa métodos [de entrada estándar coherentes.](../../design/interaction-fundamentals.md)
* Si la aplicación tiene una entrada personalizada, se comunica claramente a través de:
* Experiencia de primera ejecución
* Pantallas de introducción
* Información sobre herramientas
* Asesor manual
* Sección ayuda
* Voice over

### <a name="recommendations"></a>Recomendaciones

* Use métodos de entrada estándar siempre que sea posible.
* Proporcione demostraciones, tutoriales e información sobre herramientas para métodos de entrada no estándar.
* Use un modelo de interacción coherente en toda la aplicación.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Interacciones instintivas](../../design/interaction-fundamentals.md)
* [Objetos interactuables](../../design/interactable-object.md)
* [Control con la cabeza y permanencia](../../design/gaze-and-dwell.md)
* [Cursores](../../design/cursors.md)
* [Confort y mirada](../../design/comfort.md#gaze-direction)
* [Entrada de voz](../../design/voice-input.md)
* [Controladores de movimiento](../../design/motion-controllers.md)
* [Guía de portabilidad de entrada para Unity](../porting-apps/input-porting-guide-for-unity.md)
* [Entrada desde teclado en Unity](../unity/keyboard-input-in-unity.md)
* [Mirada en Unity](../unity/gaze-in-unity.md)
* [Controladores de movimiento en Unity](../unity/motion-controllers-in-unity.md)
* [Gestos en Unity](../unity/gestures-in-unity.md)
* [Entrada de voz en Unity](../unity/voice-input-in-unity.md)
* [Entrada desde teclado, ratón y controlador en DirectX](./keyboard-mouse-and-controller-input-in-directx.md)
* [Control con la cabeza y los ojos de DirectX](../native/gaze-in-directx.md)
* [Manos y controladores de movimiento en DirectX](../native/hands-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Caso práctico: el objetivo de una computación más personal](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Estudio de conversión: aprendizajes de diseño HoloStudio interfaz de usuario e interacción](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Aplicación de ejemplo: tabla periódica de los elementos](../unity/periodic-table-of-the-elements.md)
* [Aplicación de ejemplo: Módulo lunar](../unity/lunar-module.md)

## <a name="interactable-objects"></a>Objetos interactuables

Un botón ha sido durante mucho tiempo una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta tridimensional, ya no tenemos que limitarnos a este mundo de abstracción. Todo puede ser un objeto interactuable que desencadena un evento. Un objeto interactuable se puede representar como cualquier cosa, desde una cafetera de la tabla hasta un globo flotante en el aire. Independientemente del formato, el usuario debe reconocer claramente los objetos que pueden interactuar a través de indicaciones visuales y de audio.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  Independientemente del formato, los objetos que se pueden interactuar se pueden reconocer a través de indicaciones visuales y de audio en tres estados: inactivos, dirigidos y seleccionados. "Véalo, digalo" es claro y se usa de forma coherente a lo largo de la experiencia. Los objetos se escalan y distribuyen para permitir el destino sin errores. | El usuario puede reconocer el objeto como interactuable a través de comentarios visuales o de audio, y puede dirigirse al objeto y activarlo. | Dado que no hay indicaciones visuales o de audio, el usuario no puede reconocer un objeto interactuable. Las interacciones son propensas a errores debido a la escala de objetos o a la distancia entre los objetos. | 

### <a name="how-to-measure"></a>Cómo medir

* Los objetos interactuables se reconocen como "interactables". incluidos botones, menús y contenido específico de la aplicación. Como regla general, debe haber una indicación visual y de audio al dirigirse a objetos interactuables.

### <a name="recommendations"></a>Recomendaciones

* Use comentarios visuales y de audio para las interacciones.
* Los comentarios visuales deben diferenciarse para cada estado de entrada (inactivo, dirigido, seleccionado)
* Los objetos interactuables deben escalarse y colocarse para el destino sin errores.
* Los objetos interactuables agrupados (como una barra de menús o una lista) deben tener el espaciado adecuado para la selección de destino.
* Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto para la palabra clave command ("See it, say it")

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Objeto con el que se puede interactuar](../../design/interactable-object.md)
* [Texto en Unity](../unity/text-in-unity.md)
* [Cuadro de límite y barra de la aplicación](../../design/app-bar-and-bounding-box.md)
* [Entrada de voz](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Mixed Reality Toolkit- UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Examen de la sala

Las aplicaciones que requieren datos de asignación espacial dependen del dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo. La integridad y calidad de estos datos depende de una serie de factores, como la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si se han movido objetos como los alimentos y las puertas desde que el dispositivo ha examinado el área. Muchas aplicaciones analizarán los datos de asignación espacial al principio de la experiencia para decidir si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad del mapa espacial. Si el usuario tiene que examinar el entorno, debe proporcionar instrucciones claras durante la experiencia de examen.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  La visualización de la malla espacial le dice a los usuarios que el examen está en curso. El usuario sabe claramente qué hacer y cuándo se inicia y se detiene el examen. | Se proporciona la visualización de la malla espacial, pero es posible que el usuario no sepa claramente qué hacer y no se proporciona información de progreso. | Ninguna visualización de la malla. No se proporciona información de orientación al usuario sobre dónde buscar o cuándo se inicia o se detiene el examen. |

### <a name="how-to-measure"></a>Cómo medir

* Durante un examen de sala necesario, se proporcionan instrucciones visuales y de audio que indican dónde buscar y cuándo iniciar y detener el examen.

### <a name="recommendations"></a>Recomendaciones

* Indique cuánto del volumen total de las proximidades de los usuarios debe formar parte de la experiencia.
* Comunicarse cuando se inicia el examen y se detiene, como un indicador de progreso.
* Use una visualización de la malla durante el examen.
* Proporcione indicaciones visuales y de audio para animar al usuario a mirar y moverse por la sala.
* Informe al usuario dónde debe ir para mejorar los datos. En muchos casos, puede ser mejor decir al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás de los gatos) para obtener la calidad de examen necesaria.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Visualización de la exploración de la sala](../../design/room-scan-visualization.md)
* [Caso práctico: Expansión de las funcionalidades de asignación espacial de HoloLens](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Caso práctico: Diseño de sonido espacial para HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Caso práctico: Creación de una experiencia inmersiva en fragmentos](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Mixed Reality Toolkit UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicadores direccionales

En una aplicación de realidad mixta, el contenido puede estar fuera del campo de vista u ocluido por objetos del mundo real. Una aplicación bien diseñada facilitará al usuario la búsqueda de contenido no visible. Los indicadores direccionales alertan a un usuario sobre contenido importante y proporcionan instrucciones sobre el contenido en relación con la posición del usuario. Las instrucciones para el contenido no visible pueden tener la forma de emisores de sonido, flechas direccionales o indicaciones visuales directas.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  Las indicaciones visuales y de audio guían directamente al usuario a contenido relevante fuera del campo de vista. | Una flecha o algún indicador que señala al usuario en la dirección general del contenido. | El contenido pertinente está fuera del campo de vista y se proporciona una guía de ubicación deficiente o ninguna al usuario. | 

### <a name="how-to-measure"></a>Cómo medir

* El contenido relevante fuera del campo de vista del usuario se puede detectar a través de indicaciones visuales o de audio.

### <a name="recommendations"></a>Recomendaciones

* Cuando el contenido pertinente esté fuera del campo de vista del usuario, use indicadores direccionales e indicaciones de audio para guiar al usuario al contenido. En muchos casos, se prefiere una guía visual directa sobre las flechas direccionales.
* Los indicadores direccionales no deben estar integrados en el cursor.

### <a name="resources"></a>Recursos

* [Marco holográfico](../../design/holographic-frame.md)

## <a name="data-loading"></a>Carga de datos

Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga. Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto tiempo de espera podría ser.

### <a name="device-impact"></a>Impacto en el dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Óptima  |  Cumple |  Suspenso |
--- | --- | ---
|  Indicador visual animado, en forma de barra de progreso o anillo, que muestra el progreso durante cualquier carga o procesamiento de datos. El indicador visual proporciona instrucciones sobre cuánto tiempo podría ser la espera. | Se informa al usuario de que la carga de datos está en curso, pero no hay ninguna indicación de cuánto tiempo podría ser la espera. | No hay indicadores de carga o proceso de datos para tareas que tarden más de 5 segundos. |

### <a name="how-to-measure"></a>Cómo medir

* Durante la carga de datos, compruebe que no hay ningún estado en blanco durante más de 5 segundos.

### <a name="recommendations"></a>Recomendaciones

* Proporcione un animador de carga de datos que muestre el progreso en cualquier situación en la que el usuario pueda percibir que esta aplicación se ha detenido o se ha detenido. Una regla general razonable es cualquier actividad de "carga" que podría tardar más de 5 segundos.

### <a name="resources"></a>Recursos

* [Indicación del progreso](../../design/progress.md)