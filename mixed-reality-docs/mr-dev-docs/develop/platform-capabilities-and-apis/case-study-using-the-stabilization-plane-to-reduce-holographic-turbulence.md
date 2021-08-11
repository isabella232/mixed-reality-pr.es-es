---
title: 'Caso práctico: uso del plano de estabilización'
description: Explore cómo nuestro equipo de desarrollo usó el plano de estabilización para reducir la rebulencia holográfica en una aplicación de realidad mixta.
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, estabilización, caso práctico, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 4227be39c18e43ad712a14dd61217994a8fc761f41f9416b95b511be5396712a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202368"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Caso práctico: uso del plano de estabilización para reducir la lebulencia holográfica

Trabajar con hologramas suele ser complicado. Moverse alrededor de un espacio y mirar hologramas desde todos los ángulos proporciona un nivel de inmersión que no está disponible en una pantalla normal del equipo. Mantener estos hologramas en su lugar y tener un aspecto realista es una hazaña técnica lograda por el hardware de Microsoft HoloLens y el diseño inteligente de aplicaciones holográficas.

## <a name="the-tech"></a>La tecnología

Para que los hologramas aparezcan como si realmente compartan el espacio con usted, deben representarse correctamente sin separación de colores. Esto se logra, en parte, mediante la tecnología integrada en el hardware HoloLens, que mantiene los hologramas anclados en lo que llamamos un plano [de estabilización](hologram-stability.md#reprojection).

Un plano se define mediante un punto y un normal. Puesto que siempre queremos que el plano se apunte a la cámara, nos preocupa establecer el punto del plano. Podemos decir a HoloLens punto en el que centrar su procesamiento para mantener todo anclado y estable. Sin embargo, establecer este punto de enfoque es específico de la aplicación y puede hacer o interrumpir la aplicación en función del contenido.

Hologramas mejor cuando el plano de estabilización se aplica correctamente, pero lo que eso significa realmente depende del tipo de aplicación que está creando. Echemos un vistazo a cómo algunas de las aplicaciones disponibles actualmente para HoloLens abordar este problema.

## <a name="behind-the-scenes"></a>Entre bambalinas

Al desarrollar las siguientes aplicaciones, hemos observado que, cuando no usamos el plano, los objetos se movían cuando se movía la cabeza. También veríamos la separación de color con movimientos rápidos de la cabeza o hologramas. Terminamos aprendiendo a través de la prueba y el error cómo usar mejor el plano de estabilización y diseñar nuestras aplicaciones en torno a los problemas que no se pueden corregir.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: contenido estacionado, interactividad 3D

[Galaxy Explorer tiene](../unity/galaxy-explorer.md) dos elementos principales en la escena: la vista principal del contenido y la pequeña barra de herramientas de la interfaz de usuario que sigue la mirada. En el caso de la lógica de estabilización, observamos con qué se interseca el vector de mirada actual en cada fotograma para determinar si alcanza algo en una capa de colisión especificada. En este caso, las capas que nos interesan son los planetas, por lo que si la mirada cae sobre un planeta, el plano de estabilización se coloca allí. Si no se encuentra ninguno de los objetos de la capa de colisión de destino, la aplicación usa una capa secundaria de "plan B". Si no se mira nada, el plano de estabilización se mantiene a la misma distancia que al mirar el contenido. Las herramientas de interfaz de usuario se quedan como un destino de plano, ya que hemos encontrado que el salto entre cerca y lejos redujo la estabilidad de la escena general.

El diseño de Galaxy Explorer se presta bien para mantener las cosas estables y reducir el efecto de la separación de colores. Se recomienda al usuario que pasee por el contenido y lo mueva de lado a lado, y los planetas se remueven lo suficientemente lentamente como para que la separación de colores no sea perceptible. Además, se mantiene una constante de 60 FPS, lo que hace un largo camino para evitar que se haga la separación de colores.

Para comprobarlo usted mismo, busque un archivo denominado LSRPlaneModifier.cs en el código [de Galaxy Explorer en GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: contenido fijo con un foco de interfaz de usuario

En HoloStudio, dedica la mayor parte del tiempo a mirar el mismo modelo en el que está trabajando. La mirada no mueve una cantidad significativa, excepto cuando se selecciona una nueva herramienta o se desea navegar por la interfaz de usuario, por lo que podemos mantener la lógica de configuración del plano simple. Al mirar la interfaz de usuario, el plano se establece en cualquier elemento de la interfaz de usuario al que se ajuste la mirada. Al mirar el modelo, el plano está a una distancia establecida, correspondiente a la distancia predeterminada entre usted y el modelo.

![Plano de estabilización visualizado en HoloStudio mientras el usuario mira el botón Inicio](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour y Visor 3D: contenido stationary con animaciones y películas

En HoloTour y Visor 3D, está viendo un objeto animado o una película con efectos 3D agregados encima. La estabilización de estas aplicaciones se establece en lo que esté viendo actualmente.

HoloTour también evita que se aleje demasiado de su mundo virtual haciendo que se mueva con usted en lugar de permanecer en una ubicación fija. Esto garantiza que no se alejará lo suficiente de otros hologramas para que los problemas de estabilidad se alejen.

![En este ejemplo de HoloTour, el plano de estabilización se establecería en esta película de Pantheon de Hadrian.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: interacciones dinámicas de contenido e entorno

Establecer el plano de estabilización en RoboRaid es sorprendentemente sencillo, a pesar de ser la aplicación que requiere el movimiento más repentino. El plano está orientado a pegarse a las paredes o a los objetos circundantes y flotará a una distancia fija delante de usted cuando esté lo suficientemente lejos.

RoboRaid se diseñó pensando en el plano de estabilización. El reticle, que se mueve más porque está bloqueado con la cabeza, evita esto usando solo rojo y azul, lo que minimiza cualquier daño de color. También contiene un pequeño poco de profundidad entre las piezas, lo que reduce al mínimo los efectos de color que se producirían al enmascararse con un efecto de paralaje ya esperado. Los robots no se mueven rápidamente y solo recorren distancias cortas en intervalos regulares. Tienden a permanecer unos 2 metros delante de usted, donde la estabilización está establecida de forma predeterminada.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragmentos y Young Conker: contenido dinámico con interacción con el entorno

Escrito por Asobo Studio en C++, Fragments y Young Conker toman un enfoque diferente para establecer el plano de estabilización. Los puntos de interés (POI) se definen en el código y se ordenan por prioridad. Los objetos de interés son contenido en el juego, como el modelo de Conker en Young Conker, los menús, la retícula de objetivo y los logotipos. La mirada del usuario interseca los PUNTOS de referencia y el plano se establece en el centro del objeto con la prioridad más alta. Si no se produce ninguna intersección, el plano se establece en la distancia predeterminada.

Los fragmentos y Young Conker también diseñan a su alrededor desviando demasiado lejos de los hologramas mediante la pausa de la aplicación si se mueve fuera de lo que se ha examinado previamente como espacio de juego. Por lo tanto, le mantienen dentro de los límites que se encuentran para proporcionar la experiencia más estable.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Si tiene una HoloLens y quiere trabajar con los conceptos de este artículo, puede descargar una escena de prueba para probar los ejercicios siguientes. La escena de prueba usa la API gizmo integrada de Unity para ayudarle a visualizar dónde se establece el plano. El código también se usó para capturar las capturas de pantalla en este caso práctico.
1. Sincronice la versión más [reciente de MixedRealityToolkit-Unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity)
2. Abra la [escena HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)
3. Compile y configure el proyecto generado.
4. Ejecute en el dispositivo.

### <a name="exercise-1"></a>Ejercicio 1

Verá varios puntos en blanco a su alrededor en distintas orientaciones. Delante de usted, verá tres puntos en profundidades diferentes. Pulse en el aire para cambiar el punto en el que está establecido el plano. Para este ejercicio, y para los otros dos, moverse por el espacio mientras mira los puntos. Girar la cabeza hacia la izquierda, la derecha, hacia arriba y hacia abajo. Moverse más cerca y más lejos de los puntos. Vea cómo reaccionan cuando el plano de estabilización está establecido en destinos diferentes.

### <a name="exercise-2"></a>Ejercicio 2

Ahora, gire a la derecha hasta que vea dos puntos móviles, uno oscilando en un trazado horizontal y otro en un trazado vertical. Una vez más, pulse en el aire para cambiar el punto en el que está establecido el plano. Observe cómo se reducirá la separación de colores y aparecerá en el punto que está conectado al plano. Pulse de nuevo para usar la velocidad del punto en la función de configuración del plano. Este parámetro proporciona una sugerencia para HoloLens sobre el movimiento previsto del objeto. Es importante saber cuándo usar esto, ya que observará cuándo se usa la velocidad en un punto, el otro punto móvil mostrará una mayor separación de color. Tenga esto en cuenta al diseñar las aplicaciones: tener un flujo cohesivo al movimiento de los objetos puede ayudar a evitar que aparezcan artefactos.

### <a name="exercise-3"></a>Ejercicio 3

Vuelva a la derecha una vez más hasta que vea una nueva configuración de puntos. En este caso, hay puntos en la distancia y un punto delante de ellos. Pulsación en el aire para cambiar el punto en el que está establecido el plano, alternando entre los puntos de la parte posterior y el punto en movimiento. Observe cómo establecer la posición del plano y la velocidad en la del punto de conexión hace que los artefactos aparezcan en todas partes.

**Sugerencias**
* Mantenga la lógica de configuración del plano simple. Como ha visto, no necesita algoritmos de configuración de plano complejos para crear una experiencia envolvente. El plano de estabilización es solo una parte del rompecabezas.
* Siempre que sea posible, mueva siempre el plano entre los destinos sin problemas. Cambiar al instante los destinos lejanos puede interrumpir visualmente la escena.
* Considere la posibilidad de tener una opción en la lógica de configuración del plano para bloquear un destino específico. De este modo, puede bloquear el plano en un objeto, como un logotipo o una pantalla de título, si es necesario.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Str strs</b><br>Ingeniero de software @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también
* [MR Basics 100: introducción a Unity](../unity/tutorials/holograms-100.md)
* [Punto de enfoque en Unity](../unity/focus-point-in-unity.md)
* [Estabilidad de hologramas](hologram-stability.md)
