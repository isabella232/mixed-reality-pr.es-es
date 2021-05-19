---
title: Designing Holograms
description: Obtenga información Mixed Reality a través de la nueva aplicación Diseño de hologramas de Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, hologramas, diseño de hologramas, aprendizaje, aplicación de ejemplo, casco de realidad mixta, casco de realidad virtual, ¿qué es la realidad virtual?
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143634"
---
# <a name="the-making-of-designing-holograms"></a>La realización de diseño de hologramas

> [!NOTE]
> Permita que una pequeña ventana de carga tenga en cuenta todos los GIF es cool y los vídeos insertados en esta página.

Aprender a diseñar para la realidad mixta puede ser difícil porque el medio no siempre se traduce bien en procesos de diseño 2D. Aquí, en Microsoft, hemos creado una aplicación gratuita para el HoloLens 2 que le ayudará a conocer de primera mano los aspectos básicos del diseño de la experiencia de usuario de realidad mixta. El enfoque único de la aplicación Diseño de hologramas se a profundizar en comportamientos de realidad mixta, sugerencias y recomendaciones para ayudarle a crear aplicaciones holoLens atractivas y sorprendentes propias. Descargue la aplicación de forma gratuita desde el Microsoft Store y aprenda del equipo de diseño de Mixed Reality Microsoft.

> [!div class="nextstepaction"]
> [Descarga de la aplicación Diseño de hologramas](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado de la escena de seguimiento de la cabeza en la sala de demostración del holograma de diseño](images/designing-holograms/demo-room.gif)

*Diseño de la sala de demostración del holograma (también conocida como casa de las cámaras)*

## <a name="designing-for-mixed-reality"></a>Diseño para la realidad mixta

Al igual que muchos de los usuarios, solía diseñar aplicaciones móviles. Procedente de un mundo de diseño 2D, saltar a la informática espacial, donde todo está ahora en el mundo, fue un cambio significativo. En realidad mixta, las aplicaciones ya no se limitan a una pantalla 2D; de hecho, son casi gratis, se colocan en el mundo real e interactúan con objetos reales.

Para mí, la conexión de experiencias 3D a procesos de diseño 2D convencionales es el aspecto más complicado del desarrollo de realidad mixta. En las conversaciones con los clientes, oiría cosas como "Sé qué características incluir y cómo hacer que se ejecuten. Es código, puedo seguir los documentos y tutoriales, pero ¿la experiencia del usuario? Tantas características, distintas opciones de entrada, diferentes escenarios y entornos físicos, es abrumador".

![Imagen de HoloLens 2 Design Workshop en San Francisco Image from the HoloLens 2 Design Workshop in San Francisco (Imagen del taller de diseño de HoloLens 2 ](images/designing-holograms/workshop.jpeg)
 *en San Francisco)*

## <a name="an-opportunity-to-teach"></a>Una oportunidad para enseñar

Al principio no era obvio, pero se presentaba una excelente oportunidad para usar la realidad mixta como medio para enseñarla.

El diseño de hologramas es una experiencia visual que explica los conceptos y recomendaciones de diseño de realidad mixta. Solo usted y un profesor virtual muestran los conceptos de diseño de realidad mixta. Todo es desde una perspectiva de tercera persona con la experiencia en firme en su propio espacio.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Vídeo del finalizador de diseño de hologramas*

## <a name="exploring-the-doll-house"></a>Exploración de la casa del hogar

La casa del hogar es el entorno virtual que usamos en toda la aplicación. El entorno es una sala de 80 x 60 x 40 cm que contiene los elementos básicos que la mayoría de las salas tienen en común, como las paredes, las luces, los suelos, una mesa y un televisor. La casa de cámaras es la principal fuente de la experiencia de la aplicación, por lo que es necesario asegurarnos de que funcionaría bien en cualquier entorno. Conséndalo como una pequeña sala de demostración para visualizar todo tipo de conceptos de realidad mixta.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Vídeo del comportamiento de ajuste deHouse Desajuste*

### <a name="11-vs-110-prototypes"></a>Prototipos de 1:1 frente a 1:10

Nuestra suposición inicial era que las demostraciones de 1:1 serían increíbles, casi como mirar a un profesor de la vida real. El usuario vería todo lo que el profesor ve a escala real. Sin embargo, inmediatamente nos dimos cuenta de que habría algunos problemas:

- La mayoría de los desarrolladores ejecutarán sus aplicaciones en oficinas o en salas más pequeñas que la sala de demostración, por lo que no cabría.
- Las pantallas son aditivas, lo que significa que todo el entorno virtual se superará sobre la sala de un usuario. Esto puede resultar confuso con dos tablas, quizás dobles y paredes que no se alinean.
- Y lo peor de todo es que un entorno virtual está muy restringido por un campo de vista.

Cuando hemos probado una escala mini 1:10, el resultado fue una vista fantástica de una sala realista. Podía ver todo lo que estaba pasando desde cualquier ángulo al mismo tiempo. Lo más sorprendente es que a la mayoría de los evaluadores les hizo mucho más envolvente ver una versión pequeña y, después, nunca cambiaron a la escala 1:1. Por lo tanto, decidimos realmente desechar la versión 1:1 y evitar el trabajo adicional necesario para adaptar la interfaz de usuario y otros aspectos de la aplicación.

![Campo de vista con escala 1:1 ](images/designing-holograms/1-1-scale.png)
 *Campo de vista con escala 1:1*

![Campo de vista con escala 1:10 ](images/designing-holograms/1-10-scale.png)
 *Campo de vista con escala 1:10*

## <a name="using-mixed-reality-capture"></a>Uso de Captura de realidad mixta

Una de las características más características de esta aplicación es el uso de Captura de realidad mixta para enseñar y demostrar conceptos de diseño de realidad mixta.

Microsoft tiene un Captura de realidad mixta studio en San Francisco. Microsoft también licencia esta tecnología a otros estudios, como Avatar Dimension en Washington D.C., Metastage en Los Ángeles, Dimension Studios en Londres, SK Telecom in London y Volucap en París. Puede encontrar más información sobre nuestros [estudios de Captura de realidad mixta aquí.](https://www.microsoft.com/mixed-reality/capture-studios)

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Secuencia sin procesar de Daniel Escudero de una de las 106 cámaras del Captura de realidad mixta Studio en San Francisco.*

El proceso de captura genera una malla con fotogramas clave, normales y texturas, que se pueden entregar como archivos OBJ/PNG para su posterior postproducción o listas para la reproducción como un archivo MP4 comprimido H.264. Estos archivos se pueden importar en proyectos de Unity, Unreal, Native y WebXR. Los archivos se pueden ejecutar en Windows, iOS, Mac, Android, Magic Leap y Playstation VR.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*Capture Player proporciona para analizar archivos MP4 que contienen vídeo con audio y mallas insertadas.*

## <a name="manipulating-captures-and-virtual-objects"></a>Manipulación de capturas y objetos virtuales

Mixed Reality captures generan representaciones virtuales de personas o animales, pero en ocasiones es posible que necesite esos caracteres para interactuar con otros objetos virtuales. En los dos ejemplos siguientes se muestran distintas formas de manipular las escenas para lograr este efecto.

### <a name="head-gaze-adjustment"></a>Ajuste de la mirada con la cabeza

El ajuste de headgaze le permite mover la cabeza de una persona capturada en tiempo de ejecución, lo que significa que podría tener una cara de captura hacia un usuario. En nuestro caso, lo hemos usado para mostrar el campo de vista y el campo de interés. Lo que se ve a continuación es un objeto de juego en movimiento que actúa como destino para que la mirada con la cabeza la mire. A medida que movemos el destino de lado a lado, el jefe de la captura sigue.

Hemos usado este truco para asegurarnos de que la captura inactiva siempre se enfrentaría a hologramas colocados en distintas partes de la casa de la cámara. 

![La cabeza de la captura se mueve en tiempo de ejecución después de un gameobject de destino en Unity](images/designing-holograms/head-adjustment.gif)

*La cabeza de la captura se mueve en tiempo de ejecución después de un gameobject de destino en Unity.*

### <a name="syncing-animated-objects"></a>Sincronizar objetos animados

La segunda, animaba objetos para sincronizar con el movimiento de una captura. En diferentes partes de la aplicación, importamos OBJ secuenciales de una captura específica cada cinco fotogramas. A continuación, los OBJETOSJ se animaron en la escena para asegurarse de que coincidirían con el fotograma correspondiente de la captura. Se trata de un proceso tedioso de animar y defraudar claves, pero el resultado es excelente. Ahora puede ver un Captura de realidad mixta interactuar con objetos no capturados.

![Animación sincronizada entre un panel Captura de realidad mixta interfaz de usuario](images/designing-holograms/synced-objects.gif)

*Animación sincronizada entre un panel Captura de realidad mixta interfaz de usuario*

### <a name="ui-creative-process"></a>Proceso creativo de la interfaz de usuario

Cuando iniciamos el diseño de la interfaz de usuario, queríamos mostrar parte de la magia y la posibilidad de que los hologramas tengan que ofrecer. Mostrar ventanas 2D estáticas y cuadros de texto no es adecuado en el mundo 3D. Muchas de las posibilidades disponibles no se muestran, por lo que, desde el principio, decidimos dejar de hacerlo y hacer un uso completo del espacio holográfico en 3D.

Al principio, empezamos con la adición de cierto grosor a los paneles, iconos e información de texto. Aun así, como usuario, lo que veo es un cuadro de texto. Cuadros de texto con imágenes, pero no estamos allí. Hemos ido más allá haciendo uso de los sombreadores Mixed Reality Toolkit (MRTK). Los sombreadores MRTK se han convertido en una herramienta eficaz y hemos hecho uso de sus características de galería de símbolos para agregar profundidad negativa a los paneles. Esto significa que, en lugar de agregar elementos delante de un cuadro de texto, los iconos ahora aparecen detrás de un panel transparente. Lo que veo ahora como usuario es algo que ya no puedo replicar en el mundo real y aquí es donde comenzó a producirse la magia holográfica. Además, como usuario no me gusta leer, ya hago muchas cosas en el mundo físico.

Obviamente, los iconos funcionan mucho mejor que el texto simple. Para proporcionar una guía aún más eficaz, he empezado a crear un conjunto de objetos animados y avatares, y cada uno de ellos cuenta una pequeña historia sobre lo que se hace en el escenario respectivo y cómo se usa.

![GIF animado de un sistema interactivo de menús holográficos](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>Conceptos principales

**Seguimiento de la cabeza y seguimiento de los ojos**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**Seguimiento de manos**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**Reconocimiento espacial**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**Marco holográfico**

![GIF animado de un usuario que mira alrededor de la casa de fotos con el marco holográfico resaltado](images/designing-holograms/FOVandFOI.gif)

**Sistemas de coordenadas**

![GIF animado de un usuario que mira alrededor de la coordenada con los sistemas de coordenadas resaltados](images/designing-holograms/CoordinateSystems.gif)

**Seguimiento de los ojos**

![GIF animado de un usuario que mira hologramas estacionados con el rayo de mirada con los ojos resaltado](images/designing-holograms/EyeTracking.gif)

**Visualización del examen de sala y asignación espacial**

![GIF animado de todas las superficies dentro de la casa de seguridad que se está asignando](images/designing-holograms/SpatialMapping.gif)

**Descripción de escenas**

![GIF animado de objetos en el centro de reuniones que se reconoce](images/designing-holograms/SceneUnderstanding.gif)

**Apuntar y confirmar con rayos de mano**

![GIF animado de un usuario que eleva la mano con un rayo de mano resaltado](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>Momentos de "Pruébalo"

El diseño de hologramas enseña conceptos de realidad mixta, pero también permite probarlos en su habitación. Después de algunas de esas explicaciones, se pone en pausa y se sale de la casa de la cocina y se entra en un momento interactivo. Estos son algunos ejemplos de esos momentos interactivos:

![GIF animado del marco de seguimiento de manos que muestra cuándo se detectan las manos y cuándo entran en el campo de vista](images/designing-holograms/try-out-1.gif)

*El marco de seguimiento de manos que muestra cuándo se detectan las manos y cuándo entran en el campo de vista.*

![GIF animado de interacción con cristales en colisión a través de la interacción lejana](images/designing-holograms/try-out-2.gif)

*Interacción con cristales en colisión a través de la interacción lejana*

![GIF animado de exploración de las asequibilidades de interacción cercana](images/designing-holograms/try-out-3.gif)

*Exploración de las asequibilidades de interacción cercanas*

## <a name="about-the-team"></a>Acerca del equipo

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>Diseñador técnico de cliente potencial</i><br>Dan es el director creativo de Diseño de hologramas y actualmente trabaja como responsable de diseño de la Academia Mixed Reality de Microsoft en San Francisco y anteriormente fue diseñador en uno de los estudios de Mixed Reality de Microsoft en Londres.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>Senior 3D Artist</i><br>Martin dirige 3D Art and UI Design on Designing Holograms (Diseño de hologramas en 3D Art y UI Designing Holograms) y anteriormente fue un autor sénior en 3D en uno de los estudios Mixed Reality De Microsoft en Alemania.</td>
</tr>
</table>

Un enorme gracias al equipo de diseño de Mixed Reality por compartir tantos conocimientos y a la increíble gente de Teoría de objetos por ser compañeros de equipo esenciales en cada paso del proyecto. [](https://objecttheory.com/) Gracias a todos por su increíble actor, por su pasión y un ojo excepcional por el diseño.

> [!div class="nextstepaction"]
> [Descarga de la aplicación Diseño de hologramas](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)