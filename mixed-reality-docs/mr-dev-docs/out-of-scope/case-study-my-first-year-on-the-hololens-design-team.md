---
title: 'Caso práctico: mi primer año en el equipo HoloLens diseño'
description: Mi recorrido desde una zona plana 2D al mundo 3D comenzó cuando me uní al equipo de diseño de HoloLens en enero de 2016.
author: designnomad
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, diseño, editorial, personal
ms.openlocfilehash: 2defa24b8e53b28f90a8eb613afcbae7d1b9b1f2d12caaf885e405593df01ffe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192915"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Caso práctico: mi primer año en el equipo HoloLens diseño

Mi recorrido desde una zona plana 2D al mundo 3D comenzó cuando me uní al equipo de diseño de HoloLens en enero de 2016. Antes de unirse al equipo, tenía muy poca experiencia en el diseño 3D. Era como el proverbios chino sobre un recorrido de miles de kilómetros a partir de un solo paso, salvo que en mi caso ese primer paso fue un salto.

![Dar el salto de 2D a 3D](../develop/platform-capabilities-and-apis/images/2D_to_3D-800px.gif)<br>
*Dar el salto de 2D a 3D*

> *"Me he sentido como si hubiera saltado al puesto del conductor sin saber cómo conducir el coche. Estaba desbordado y abrumado, pero muy centrado".*<br>
> — Hae Jin Lee

Durante el año pasado, recogí aptitudes y conocimientos lo más rápido posible, pero todavía tengo mucho que aprender. En este caso, he escrito cuatro observaciones con un tutorial en vídeo que documenta mi transición de un diseñador de interacciones 2D a 3D. I hope my experience will inspire other designers to take the leap to 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Marco de adiós. Hello spatial/diegetic UI

Siempre que diseñé pósteres, revistas, sitios web o pantallas de aplicaciones, un marco definido (normalmente un rectángulo) era una constante para cada problema. A menos que esté leyendo esta publicación en un HoloLens  u otro dispositivo vr, lo está viendo desde fuera hasta la pantalla 2D que se protege de forma segura dentro de un fotograma. El contenido es externo a usted. Sin embargo, Mixed Reality *casco* elimina el marco, por lo que está dentro del espacio de contenido, buscando y recorrindo el contenido desde dentro hacia fuera.

He comprendido esto conceptualmente, pero al principio cometí el error de simplemente transferir el pensamiento 2D al espacio 3D. Obviamente, esto no funcionaba bien porque el espacio 3D tiene sus propias propiedades únicas, como un cambio de vista (en función del movimiento de la cabeza del usuario) y un requisito diferente para la comodidad del usuario [(en](https://www.youtube.com/watch?v=-606oZKLa_s/) función de las propiedades de los dispositivos y los seres humanos que los usan). Por ejemplo, en un espacio de diseño de interfaz de usuario 2D, el bloqueo de elementos de la interfaz de usuario en la esquina de una pantalla es un patrón muy común, pero esta interfaz de usuario de estilo HUD (head up display) no parece natural en las experiencias de REALIDAD virtual o realidad virtual. dificulta la inmersidad del usuario en el espacio y provoca molestias en el usuario. Es como tener una partícula de tierra pesada en las gafas de la que está deseando deshacerse. Con el tiempo, he aprendido que resulta más natural colocar el contenido en un espacio 3D y agregar un comportamiento bloqueado por el cuerpo que hace que el contenido siga al usuario a una distancia fija relativa.

![Cuerpo bloqueado](../develop/platform-capabilities-and-apis/images/bodylockedtagalong.gif)<br>
*Cuerpo bloqueado*

<br>

![Bloqueado por el mundo](../develop/platform-capabilities-and-apis/images/worldlocked.gif)<br>
*Bloqueado por el mundo*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmentos: un ejemplo de excelente interfaz de usuario de Diegetic

[Fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8), un grupo delictivo en primera persona desarrollado por [Asobo Studio](https://www.asobostudio.com/) para HoloLens muestra una excelente interfaz de usuario de Diegetic. En este juego, el usuario se convierte en un carácter principal, un escritor que intenta resolver un problema. Las pistas dinámicas para resolver este problema se asperen en la sala física del usuario y a menudo se incrustan dentro de un objeto ficticio en lugar de existir por sí mismos. Esta interfaz de usuario diegetic tiende a ser menos reconocible que la interfaz de usuario bloqueada por el cuerpo, por lo que el equipo de Asobo usó inteligentemente muchas indicaciones, como la dirección de la mirada, el sonido, la luz y las guías de los caracteres virtuales (por ejemplo, la flecha que señala la ubicación de la pista) para llamar la atención del usuario.

![Fragmentos: ejemplos de interfaz de usuario de Diegetic](../develop/platform-capabilities-and-apis/images/fragments-game-example-1.jpg)<br>
*Fragmentos: ejemplos de interfaz de usuario de Diegetic*

### <a name="observations-about-diegetic-ui"></a>Observaciones sobre la interfaz de usuario de diegetic

La interfaz de usuario espacial (tanto con el cuerpo bloqueado como con el mundo bloqueado) y la interfaz de usuario matriz tienen sus propios puntos fuertes y débiles. Animo a los diseñadores a probar tantas aplicaciones de realidad virtual o realidad virtual como sea posible y a desarrollar su propia comprensión y sensibilidad para varios métodos de posicionamiento de la interfaz de usuario.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>El retorno del skeuomorphism y la interacción mágica

Skeuomorphism, una interfaz digital que imita la forma de los objetos del mundo real ha estado "desfasada" durante los últimos 5 o 7 años en el sector del diseño. Cuando Apple por fin dio paso al diseño plano en iOS 7, parece que el skeuomorfismo finalmente ha quedo como una metodología de diseño de interfaz. Pero luego, un nuevo casco de realidad virtual/realidad virtual mediano llegó al mercado y parece que el Skeuomorphism ha vuelto a devolverse. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulador de trabajos: un ejemplo de diseño de VR skeuomorphic

[Simulador de trabajos,](https://jobsimulatorgame.com/)un juego esquiloférico desarrollado por [Labs Demásquico es](https://owlchemylabs.com/) uno de los ejemplos más populares para el diseño de VR esqueuomórfico. Dentro de este juego, los jugadores se transportan al futuro, donde los robots reemplazan a los humanos y los humanos visitan un lugar para experimentar lo que se siente al realizar tareas rutinarias en uno de los cuatro trabajos diferentes: Mecánica automática, Chef chef, vendedor de tiendas o Office Worker.

La ventaja del Skeuomorphism es clara. Los entornos y objetos conocidos de este juego ayudan a los nuevos usuarios de realidad virtual a sentirse más cómodos y presentes en el espacio virtual. También les hace sentir que están en control mediante la asociación de conocimientos y comportamientos conocidos con objetos y sus correspondientes reacción físicas. Por ejemplo, para tomar un café, los usuarios simplemente necesitan ir a la cafetera, presionar un botón, agarrar el asa de la cafetera y inclinarlo hacia su cocina como lo harían en el mundo real.

![Simulador de trabajos](../develop/platform-capabilities-and-apis/images/job-simulator.gif)<br>
*Simulador de trabajos*

Dado que MR/VR sigue siendo un medio en desarrollo, es necesario usar un cierto grado de skeuomorphism para desmitificar la tecnología mr/vr y presentarla a públicos más grandes de todo el mundo. Además, el uso de skeuomorphism o una representación realista podría ser beneficioso para tipos específicos de aplicaciones, como la simulación de vuelos o la salud. Dado que el objetivo de estas aplicaciones es desarrollar y refinar aptitudes específicas que se pueden aplicar directamente en el mundo real, cuanto más cercana sea la simulación al mundo real, más transferible será el conocimiento.

Recuerde que skeuomorphism es solo un enfoque. El potencial del mundo de realidad virtual y realidad virtual es mucho mayor que eso, y los diseñadores deben procurar crear interacciones hiper naturales mágicas, nuevas soluciones que son únicas posibles en el mundo de realidad virtual y realidad virtual. Como principio, considere la posibilidad de agregar potencias mágicas a objetos normales para permitir que los usuarios cumplan sus necesidades fundamentales, incluida la teleportación y la omniscience.

![Puerta mágica de Doraemon (izquierda) y rubyí (derecha)](../develop/platform-capabilities-and-apis/images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Puerta mágica de Doraemon (izquierda) y rubyí (derecha)*

### <a name="observations-about-skeuomorphism-in-vr"></a>Observaciones sobre el skeuomorphism en VR

Desde "Puerta de cualquier lugar" en Doraemon, "Ruby Desacertados" en El asistente deIma a "Mapa de Maurader" en Asínes, ejemplos de objetos normales con potencia mágica abundan en la popularidad. Estos objetos mágicos nos ayudan a visualizar una conexión entre el mundo real y el fantástico, entre lo que es y lo que podría ser. Tenga en cuenta que al diseñar el objeto mágico o mágico, es necesario encontrar un equilibrio entre la funcionalidad y el entretenimiento. Tenga cuidado con la tentación de crear algo puramente mágico solo por el bien de la novedad.

## <a name="understanding-different-input-methods"></a>Descripción de los distintos métodos de entrada

Cuando diseñé para el medio 2D, tenía que centrarme en las interacciones táctiles, del mouse y del teclado para las entradas. En el espacio de diseño mr/vr, nuestro cuerpo se convierte en la interfaz y los usuarios pueden usar una selección más amplia de métodos de entrada: como voz, mirada, gesto, controladores [de 6 dof](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)y gafas que permiten una conexión más intuitiva y directa con objetos virtuales.

![Entradas disponibles en HoloLens](../develop/platform-capabilities-and-apis/images/inputs.jpg)<br>
*Entradas disponibles en HoloLens*

> *"Todo es mejor para algo y peor para otra cosa".*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

Por ejemplo, la entrada de gestos mediante sensores de cámara y de manos sin sistema en un dispositivo HMD libera a los usuarios de la mano de los controladores o de llevar unas gafas de esfuerzo, pero el uso frecuente puede provocar una agotamiento físico (también es decir, un brazo de un gorilla). Además, los usuarios tienen que mantener las manos dentro de la línea de visión; si la cámara no puede ver las manos, no se pueden usar.

La entrada de voz es buena para recorrer tareas complejas porque permite a los usuarios cortar los menús anidados con un comando (por ejemplo, "Mostrarme las películas realizadas por Lamelo Studio") y también muy económica cuando se combina con otras modalidades (por ejemplo, el comando "Orientar hacia mí" orienta el holograma que un usuario está mirando hacia el usuario). Sin embargo, es posible que la entrada de voz no funcione bien en un entorno ruidoso o que no sea adecuada en un espacio muy silencioso.

Además de gesto y voz, los controladores con seguimiento manual (por ejemplo, Oculus Touch, Vive, etc.) son métodos [](https://en.wikipedia.org/wiki/Proprioception)de entrada muy populares porque son fáciles de usar, precisos, aprovechan la propiedad de las personas y proporcionan indicaciones hapticas pasivas. Sin embargo, estas ventajas tienen el costo de no poder estar sin manos y usar el seguimiento de dedo completo.

![Senso (izquierda) y Manus VR (derecha)](../develop/platform-capabilities-and-apis/images/senso-and-manus-vr.jpg)<br>
*Senso (izquierda) y Manus VR (derecha)*

Aunque no es tan popular como los controladores, los cascos están afirándose de nuevo gracias a la ola de realidad virtual o de realidad virtual. Más recientemente, la entrada del cerebro y la mente ha empezado a ganar peso como interfaz para entornos virtuales mediante la integración de sensores EEG o EMG en el casco (por ejemplo, [MindMaze VR).](https://www.mindmaze.com/)

### <a name="observations-about-input-methods"></a>Observaciones sobre los métodos de entrada

Estos son solo un ejemplo de dispositivos de entrada disponibles en el mercado para MR/VR. Seguirán proliferando hasta que el sector madure y acepte los procedimientos recomendados. Hasta entonces, los diseñadores deben mantenerse al tanto de los nuevos dispositivos de entrada y estar bien al tanto de los métodos de entrada específicos para su proyecto concreto. Los diseñadores deben buscar soluciones creadoras dentro de las limitaciones, a la vez que se aplican a los puntos fuertes de un dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Esbozar la escena y probar en el casco

Cuando he trabajado en 2D, esbozé principalmente solo el contenido. Sin embargo, en el espacio de realidad mixta no era suficiente. Tenía que esbozar toda la escena para imaginar mejor las relaciones entre el usuario y los objetos virtuales. Para ayudar a mi pensamiento espacial, comé a esbozar escenas en [Cine 4D](https://www.maxon.net/en/products/cinema-4d/overview/) y, a veces, crear recursos sencillos para la creación de prototipos en [Maya](https://www.autodesk.com/products/maya/overview/). Nunca había usado ninguno de los programas antes de unirse al equipo de HoloLens y todavía soy un principiante, pero trabajar [](https://en.wikipedia.org/wiki/Shader) con estos programas 3D me ayudó definitivamente a sentirme cómodo con la nueva terminología, como el sombreador y la [IK (cinemática inversa).](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)

**"Independientemente de la proximidad con la que esbozé la escena en 3D, la experiencia real en el casco casi nunca fue la misma que el boceto. Por eso es importante probar la escena en los cascos de destino". Hae Jin Lee**

Para HoloLens creación de prototipos, he probado todos los tutoriales en Mixed Reality [tutoriales para](../develop/unity/tutorials.md) empezar. Después, comé a jugar con [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) que Microsoft proporciona a los desarrolladores para acelerar el desarrollo de aplicaciones holográficas. Cuando me quedé atascado con algo, he publicado mi pregunta en HoloLens [question & Answer Forum](https://forums.hololens.com/categories/questions-and-answers/).

Después de adquirir conocimientos básicos HoloLens creación de prototipos, quería capacitar a otros no programadores para crear prototipos por sí mismos. Por lo tanto, he realizado un tutorial en vídeo que enseña a desarrollar un proyecto simple mediante HoloLens. Explico brevemente los conceptos básicos, por lo que incluso si no tiene ninguna experiencia en HoloLens desarrollo, debería poder seguir los pasos.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*He realizado este tutorial sencillo para no programadores como yo.*

Para la creación de prototipos de realidad virtual, he tomado cursos en [VR Dev School](https://learn.vrdev.school/) y también he tomado [contenido 3D Para](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) la creación de realidad virtual en Lynda.com. Vr Dev School me proporcionó conocimientos más profundos sobre la codificación y el curso de Lynda me ofrecía una breve introducción a la creación de recursos para VR.

## <a name="take-the-leap"></a>Dar el salto

Hace un año, me ha parecido que todo esto era un poco abrumador. Ahora puedo decir que merece la pena el esfuerzo al 100 %. Mr/VR sigue siendo un medio muy pequeño y hay muchas posibilidades interesantes a la espera de ser realizadas. Me inspira y soy capaz de desempeñar un papel pequeño en el diseño del futuro. ¡Esperamos que se una a mí en el viaje al espacio 3D!

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="../develop/platform-capabilities-and-apis/images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>

 
