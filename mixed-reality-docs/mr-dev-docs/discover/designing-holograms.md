---
title: Diseñar hologramas
description: Obtenga información sobre la realidad mixta a través de la nueva aplicación de hologramas de diseño de Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, kit de herramientas de realidad mixta, hologramas, diseño de hologramas, aprendizaje, aplicación de ejemplo, auriculares de realidad mixta, auriculares de realidad virtual, qué es realidad virtual
ms.openlocfilehash: 243b6f28da7b074b3ff6d48794d525ac08281fa7
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355500"
---
# <a name="the-making-of-designing-holograms"></a>La realización del diseño de hologramas

> [!NOTE]
> Permita que una pequeña ventana de carga tenga en cuenta todos los archivos GIF y los vídeos insertados en esta página.

Aprender a diseñar una realidad mixta puede ser difícil, especialmente con la apariencia del medio, que no siempre se convierte en procesos de diseño 2D. Aquí, en Microsoft, hemos creado una aplicación gratuita que puede descargar para HoloLens 2, que le ayuda a conocer los aspectos básicos del diseño de la experiencia de usuario de realidad mixta al experimentarlo de primera mano. El enfoque único de la aplicación de diseño de hologramas se adentra en comportamientos de realidad mixta, sugerencias y recomendaciones para ayudarle a crear aplicaciones de HoloLens atractivas y increíbles propias. Descargue la aplicación de forma gratuita desde el Microsoft Store y aprenda del equipo de diseño de la realidad mixta de Microsoft.

> [!div class="nextstepaction"]
> [Descarga de la aplicación de diseño de hologramas](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animado de la escena de seguimiento de cabeza en el salón de demostración del holograma de diseño](images/designing-holograms/demo-room.gif)

*Diseñar el salón de demostración del holograma (también conocido como la casa de muñecas)*

## <a name="designing-for-mixed-reality"></a>Diseño para la realidad mixta

Al igual que muchos de los demás, se usa para diseñar aplicaciones móviles. Desde un mundo de diseño 2D, pasar a todo en informática espacial, donde todo está ahora en todo el mundo, era un cambio significativo. En realidad mixta, las aplicaciones ya no se limitan a una pantalla 2D; de hecho, son casi gratis, se colocan en el mundo real e interactúan con objetos reales.

Para mí, la conexión de experiencias 3D a procesos de diseño 2D convencionales es el aspecto más desafiante del desarrollo de realidad mixta. En conversaciones con los clientes, oigo cosas como "sé qué características incluir y cómo ponerlas en funcionamiento. Código, puedo seguir los documentos y tutoriales, pero la experiencia del usuario. Muchas características, distintas opciones de entrada, diferentes escenarios y entornos físicos, son abrumadoras ".

![Imagen de la imagen de HoloLens 2 Design Workshop en San Francisco ](images/designing-holograms/workshop.jpeg)
 *del taller de diseño de hololens 2 en San Francisco*

## <a name="an-opportunity-to-teach"></a>Una oportunidad para enseñar

No resultó obvio al principio, pero se presentó una excelente oportunidad para usar la realidad mixta como medio para enseñarla.

El diseño de hologramas es una experiencia visual que explica los conceptos y las recomendaciones del diseño de realidad mixta. Simplemente usted y un profesor virtual muestran conceptos de diseño de realidad mixta. Todo está desde una perspectiva de tercera persona con la experiencia firmemente en su propio espacio.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Vídeo de diseño de hologramas*

## <a name="exploring-the-doll-house"></a>Exploración de la casa de muñecas

La casa de muñecas es el entorno virtual que usamos en toda la aplicación, una sala en miniatura de 80 x 60 x 40 cm que contiene los elementos básicos que la mayoría de los salones tienen en común, como las paredes, las lámparas, el mobiliario, una tabla y un televisor. La casa de muñecas es el protagonist principal de la experiencia de la aplicación, por lo que es necesario asegurarse de que funcionaría bien en cualquier entorno. Piense en ello como un pequeño salón de demostración para visualizar todo tipo de conceptos de realidad mixta.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Vídeo del comportamiento de ajuste de dollhouse*

### <a name="11-vs-110-prototypes"></a>1:1 prototipos de vs 1:10

Nuestra suposición inicial era que las demostraciones de 1:1 serían increíbles, casi como mirar a un profesor real. El usuario verá todo lo que ve el profesor en una escala de vida real. Sin embargo, inmediatamente se ha dado cuenta de que hay algunos problemas:

- La mayoría de los desarrolladores ejecutarán sus aplicaciones en oficinas o salas más pequeñas que el salón de demostración, por lo que no cabe.
- Las pantallas son aditivas, lo que significa que todo el entorno virtual se superpone a la habitación de un usuario. Esto puede resultar confuso con dos tablas, por lo que es posible que haya doble sofá y paredes que no se alineen.
- Y el peor de los entornos virtuales están muy restringidos por un campo de vista.

Cuando se intentó una escala de 1:10, el resultado era una fantástica vista de pájaro de una sala realista donde podía ver todo lo que estaba pasando desde cualquier ángulo y todo al mismo tiempo. Lo más sorprendente es que la mayoría de los evaluadores lo encontraron mucho más envolventes para ver una versión pequeña y, después, nunca se han vuelto a la escala 1:1. Por lo tanto, hemos decidido rechazar la versión 1:1 y evitar el trabajo adicional necesario para adaptar la interfaz de usuario y otros aspectos de la aplicación.

![Campo de vista con el ](images/designing-holograms/1-1-scale.png)
 *campo de escala 1:1 de la vista con la escala 1:1*

![Campo de vista con el ](images/designing-holograms/1-10-scale.png)
 *campo de escala 1:10 de la vista con la escala 1:10*

## <a name="using-mixed-reality-capture"></a>Uso de la captura de realidad mixta

Una de las características más característicos de esta aplicación es el uso de la captura de realidad mixta para enseñar y demostrar conceptos de diseño de realidad mixta.

Microsoft tiene un estudio de captura de realidad mixta en San Francisco. Microsoft también concede licencias para esta tecnología a otros estudios, que incluyen la dimensión de Avatar en Washington D.C., metastage en los Ángeles, estudios de Dimension en Londres, SK Telecom en Seúl y Volucap en Berlín. Puede encontrar más información sobre nuestros [estudios de captura de realidad mixta aquí](https://www.microsoft.com/mixed-reality/capture-studios).

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Material de estudio de Daniel escudero de una de las cámaras 106 en el estudio de captura de realidad mixta en San Francisco.*

El proceso de captura genera una malla, normales y texturas fotogramas clave, que se pueden entregar como archivos OBJ/PNG para posteriores a la producción o listas para su reproducción como un archivo MP4 comprimido H. 264. Estos archivos se pueden importar en Unity, nonreal, Native y WebXR, y se ejecutan en Windows, iOS, Mac, Android, Magic Leap y PlayStation VR.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*El reproductor de captura proporcionado para analizar MP4 que contienen vídeo con audio y mallas incrustadas.*

## <a name="manipulating-captures-and-virtual-objects"></a>Manipular capturas y objetos virtuales

Las capturas de realidad mixta producen representaciones virtuales de personas o animales, pero en ocasiones puede que necesite esos caracteres para interactuar con otros objetos virtuales. En los dos ejemplos siguientes se muestran distintas formas de manipular las escenas para lograr este efecto.

### <a name="head-gaze-adjustment"></a>Ajuste de mira hacia abajo

El ajuste Headgaze permite trasladar el encabezado de una persona capturada en tiempo de ejecución, lo que significa que podría tener una superficie de captura hacia un usuario. En nuestro caso, se usa para mostrar el campo de vista y el campo de interés. Lo que se ve a continuación es un GameObject en movimiento que actúa como un destino para que la mirada mire. A medida que se mueve el destino de lado a lado, se sigue el encabezado de la captura.

Usamos este truco para asegurarnos de que la captura inactiva siempre se encontraba en los hologramas colocados en distintas partes de la casa de muñecas. 

![El encabezado de la captura se mueve en el tiempo de ejecución después de un GameObject de destino en Unity.](images/designing-holograms/head-adjustment.gif)

*El encabezado de la captura se mueve en el tiempo de ejecución después de un GameObject de destino en Unity.*

### <a name="syncing-animated-objects"></a>Sincronizar objetos animados

El segundo, estaba animando objetos para sincronizar con el movimiento de una captura. En diferentes partes de la aplicación, se han importado obj secuenciales de una captura específica cada cinco fotogramas. Después, los obj se animaron en la escena para asegurarse de que coincidirían con el fotograma correspondiente de la captura. Es un proceso tedioso de animación y fotogramas clave, pero el resultado es excelente. ahora puede ver una captura de realidad mixta que interactúa con objetos no capturados.

![Animación sincronizada entre una captura de realidad mixta y un panel de interfaz de usuario](images/designing-holograms/synced-objects.gif)

*Animación sincronizada entre una captura de realidad mixta y un panel de interfaz de usuario*

### <a name="ui-creative-process"></a>Proceso de creación de interfaz de usuario

Cuando comenzamos ideating el diseño de la interfaz de usuario, además de la información de transporte, también queríamos mostrar algunos de los datos mágicos y las posibilidades que ofrecen los hologramas. Simplemente mostrar ventanas 2D estáticas y cuadros de texto no se siente bien en el mundo 3D y no muestra muchas de las posibilidades a mano, así que desde el principio decidimos apartarse de eso y hacer uso completo del espacio 3D holográfica.

En primer lugar, empezamos por agregar cierto grosor a los paneles e iconos, además de la información de texto. Aún así, como usuario, lo que veo es un cuadro de texto. Cuadros de texto con imágenes, pero no estamos ahí. Hemos ido más lejos mediante el uso de los sombreadores de kit de herramientas de realidad mixta (MRTK). Los sombreadores de MRTK se convierten en una herramienta eficaz y se utilizaban sus características de estarcido, algunas pueden conocerlo como el efecto del portal, para agregar profundidad negativa a los paneles. Esto significa que, en lugar de agregar elementos delante de un cuadro de texto, los iconos aparecen ahora detrás de un panel transparente. Lo que veo ahora como usuario es algo que simplemente no puedo replicar en el mundo real, y aquí es donde se empezó a producir holográfica mágica. Además, como usuario realmente no me gustaría leer, hago mucho en el mundo físico.

Obviamente, los iconos funcionan mucho mejor que el texto simple, por lo que, para proporcionar una guía aún más eficaz, se inició la creación de un conjunto de objetos y avatares animados, cada uno de ellos con una pequeña historia sobre lo que se hace en el escenario respectivo y cómo se usa.

![GIF animado de un sistema de menús de Holographic interactivo](images/designing-holograms/creative-process.gif)

## <a name="try-it-out-moments"></a>Momentos "pruébelo"

El diseño de hologramas enseña conceptos de realidad mixta, pero también le permite probarlos en su habitación. Después de algunas de esas explicaciones, se pone en pausa y sacamos de la casa de muñecas y en un momento interactivo. Estos son algunos ejemplos de esos momentos interactivos:

![GIF animado del marco de seguimiento de mano que se muestra cuando se detectan manos y cuando entran en el campo de la vista](images/designing-holograms/try-out-1.gif)

*El marco de seguimiento de mano que se muestra cuando se detectan manos y cuando entran en el campo de la vista.*

![GIF animado de interactuar con cristales en conflicto a través de la interacción Far](images/designing-holograms/try-out-2.gif)

*Interactuar con los cristales en conflicto a través de la interacción lejana*

![GIF animado de explorar prestaciones de casi interacción](images/designing-holograms/try-out-3.gif)

*Exploración de las prestaciones de casi interacción*

## <a name="about-the-team"></a>Acerca del equipo

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>Diseñador técnico líder</i><br>Dan es el director creativo sobre el diseño de hologramas y actualmente funciona como responsable de diseño de la Academia de la realidad mixta de Microsoft en San Francisco y antes era un diseñador en uno de los estudios de realidad mixta de Microsoft en Londres.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>Artista Senior en 3D</i><br>Martin lidera el diseño de la interfaz de usuario y la imagen en 3D al diseñar hologramas y antes era un artista Senior en 3D en uno de los estudios de realidad mixta de Microsoft en Berlín.</td>
</tr>
</table>

Le agradecemos enormemente el equipo de diseño de la realidad mixta para compartir todo el conocimiento y, por supuesto, con las increíbles personas en [teoría de objetos](https://objecttheory.com/) que se han convertido en compañeros de equipo esenciales en cada paso único de este proyecto. Gracias por su gran talento, por su pasión y una mirada excepcional para el diseño.

> [!div class="nextstepaction"]
> [Descarga de la aplicación de diseño de hologramas](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)