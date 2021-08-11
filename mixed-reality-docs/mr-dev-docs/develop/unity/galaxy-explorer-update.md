---
title: Making of Galaxy Explorer for HoloLens 2
description: Obtenga información sobre cómo nuestro equipo está actualizando el proyecto de código abierto de Galaxy Explorer para HoloLens 2 en GitHub.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer, case study, project, sample, MRTK, Mixed Reality Toolkit, Unity, sample apps, example apps, open source, Microsoft Store, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: c3d9c6da13446816f3fd75f83e5a9088661c9604ef4d86ea805202f538d395b5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200509"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>La realización de Galaxy Explorer para HoloLens 2

![Nuevo logotipo de Galaxy Explorer](../images/GalaxyExplorer2.jpg)


Le damos la bienvenida a la aplicación Galaxy Explorer para HoloLens 2 aplicación. [Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Explorador de la galaxia") se desarrolló originalmente como una aplicación de código abierto para HoloLens (primera generación) a través del programa Share Your Idea y es una de las primeras experiencias de realidad mixta que muchas personas han tenido. Ahora lo estamos actualizando para las nuevas [y emocionantes funcionalidades de HoloLens 2](https://www.microsoft.com/hololens/hardware).

Como uno de los estudios [de Microsoft Mixed Reality,](galaxy-explorer-update.md#mixed-reality-studios)normalmente desarrollamos soluciones de nivel comercial y desarrollamos pruebas de & en plataformas de destino a lo largo del proceso creativo y de desarrollo. Nos estamos lanzando a este proyecto con los marcos y herramientas (como [MRTK)](mrtk-getting-started.md)a medida que están disponibles para nosotros y la comunidad, y queremos llevarle a la carrera.

Al igual que el Explorador de Galaxy [original,](galaxy-explorer-update.md#meet-the-team) nuestro equipo estará abierto para obtener el proyecto en [GitHub](https://github.com/Microsoft/GalaxyExplorer) asegurarse de que la comunidad tiene acceso completo. También vamos a documentar nuestro recorrido aquí con total transparencia sobre cómo se ha portado de MRTK v1 a MRTK v2, se ha mejorado la experiencia con nuevas características disponibles en HoloLens 2 y se ha asegurado de que Galaxy Explorer sigue siendo una experiencia multiplataforma. Tanto si está viendo Galaxy Explorer en HoloLens (primera generación), HoloLens 2, un casco de Windows Mixed Reality o en el escritorio de Windows 10, queremos asegurarnos de que está disfrutando del viaje tanto como estamos.

Esta página se expandirá a medida que avancemos por el proyecto con vínculos a artículos más detallados, código, artefactos de diseño y documentación adicional de MRTK para proporcionarle una vista interna del proyecto.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Descarga de la aplicación Microsoft Store en HoloLens 2
Si tiene un HoloLens 2, puede descargar e instalar directamente la aplicación en el dispositivo.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>Pensar en interacciones

Como estudio creativo, estamos extáticos sobre el privilegio de portabilidad de Galaxy Explorer a HoloLens 2. Sabíamos desde el principio que queríamos que la experiencia fuera una demostración del nuevo dispositivo y demostrar que Mixed Reality capacitación solo está limitada por la imaginación.

HoloLens 2 permite a los usuarios tocar, comprender y mover hologramas de maneras que se sientan naturales: responden mucho como objetos reales. Los modelos de mano totalmente articulados son increíbles, ya que permiten a los usuarios hacer lo que parece natural. Por ejemplo, todos los usuarios recogen una taza de forma ligeramente diferente y, en lugar de aplicar una manera determinada de hacerlo, HoloLens 2 le permite hacerlo a su manera.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Se trata de un cambio significativo de las interfaces basadas en Air Tap en dispositivos de primera HoloLens generación. En lugar de interactuar con hologramas desde una distancia, los usuarios ahora pueden estar "de cerca y personal". Al portear experiencias existentes a HoloLens 2 o planear otras nuevas, es importante familiarizarse con la manipulación directa de hologramas.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Manipulación directa frente a las grandes distancias en el espacio

Es una experiencia mágica para llegar a un planeta, agarrarlo y contenerlo en la mano. El desafío con este enfoque es el tamaño del sistema solar, es enorme. El usuario tendría que recorrer su habitación para acercarse a cada planeta para interactuar con él.

Para permitir que los usuarios interactúen con objetos que están más lejos, MRTK ofrece rayos de mano que se lanzan desde el centro de la mano del usuario, actuando como una extensión de la mano. Se adjunta un cursor en forma de anillo al final del rayo para indicar dónde forma intersección el rayo con un objeto de destino. El objeto en que se posa el cursor puede recibir comandos gestuales de la mano. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

En la versión original de Galaxy Explorer, el usuario apuntaba a un planeta con el cursor de mirada y, a continuación, pulsaba en el aire para llamarlo más cerca. La manera más fácil de portabilidad de la experiencia HoloLens 2 es tomar este comportamiento y usar rayos de mano para seleccionar planetas. Aunque esto era funcional, nos dejó deseando más.

### <a name="back-to-the-drawing-board"></a>Volver a empezar desde cero

Nos unimos para idear lo que se podría crear sobre las interacciones existentes. El pensamiento era: aunque HoloLens 2 permite a los usuarios interactuar con hologramas de manera natural y realista, los hologramas no son reales por definición. Por lo tanto, siempre que una interacción sea plausible para el usuario, no importa si esa interacción sería posible con un objeto real o no, podemos hacerlo posible.

Un concepto que exploramos se basaba en la telekinesis: la capacidad de manipular objetos con la mente. A menudo se ve en películas de super hero, una persona se acercaría con su mente y llamaría a un objeto a mano abierta. Hemos tocado con la idea de algo más y hemos ideado un breve boceto de cómo podría funcionar el concepto.

![Concepto de la interacción de force grab](images/ge-update-interactions-concept-force-grab.png)

El usuario apuntaría el rayo de la mano a un planeta, lo que proporcionaría comentarios de destino. A medida que el usuario extiende su mano abierta, el planeta sería arrastrado hacia el usuario por una fuerza mágica hasta que esté lo suficientemente cerca como para agarrarlo. Por lo tanto, nuestro nombre para la interacción: force grab. Como el usuario se alejaba del planeta con la mano abierta, regresaba de nuevo a su gira.

### <a name="force-grab-prototyping"></a>Forzar la creación de prototipos de toma

A continuación, creamos varios prototipos para probar el concepto: ¿Cómo se siente la interacción en general? ¿Debe detenerse el objeto llamado delante del usuario o ponerse en sus manos hasta que se coloque? ¿Debe cambiar el tamaño o la escala del objeto al llamar a ?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementación de force grab en la aplicación

Cuando intentamos la toma de fuerza en los planetas, nos dimos cuenta de que teníamos que cambiar la escala del sistema solar. Resulta que una representación precisa y de tamaño medio del sistema solar es difícil de entender y navegar para los usuarios; no saben dónde buscar. Sin embargo, una representación de tamaño pequeño hizo que algunos planetas sean demasiado pequeños para poder seleccionarse fácilmente. Como resultado, el tamaño de los planetas y el espaciado entre los objetos solares se diseñaron para sentirse cómodos dentro de una sala de tamaño medio, al tiempo que se mantiene la precisión relativa.

Durante las fases posteriores del sprint de desarrollo, tuvimos la suerte de tener expertos de MSFT Mixed Reality locales, por lo que tenemos que trabajar para obtener sus entradas como evaluadores expertos y realizar iteraciones rápidas en la interacción de la toma de fuerza.

![Realización de pruebas en Una compilación en versión preliminar de Galaxy Explorer](images/ge-update-user-testing.png)

En la imagen: Senior Design Lead, tests a work-in-progress of Galaxy Explorer.In picture: Senior Design Lead, testing a work-in-progress of Galaxy Explorer( In picture: Senior Design Lead, testing a work-in-progress of Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Adición de las asequibilidades para la orientación

A medida que experimentamos en HoloLens 2, descubrimos que, aunque las nuevas interacciones son naturales e intuitivas, los hologramas siguen siendo los mismos: sin peso ni sensibilidades táctiles. Dado que los hologramas no proporcionan comentarios naturales que los seres humanos están acostumbrados a recibir cuando interactúan con objetos, es necesario crearlos.

Hemos pensado en los comentarios visuales y de audio que se proporcionarían a los usuarios para las distintas fases de sus interacciones y, puesto que el mecanismo de toma de fuerza es fundamental para interactuar con Galaxy Explorer, hemos realizado muchas iteraciones. El objetivo era encontrar el equilibrio adecuado de comentarios visuales y de audio para cada fase de la interacción: centrarse en el objeto deseado, llamarlo al usuario y, a continuación, liberarlo. Lo que hemos aprendido es que se necesitaron más comentarios visuales y de audio para reforzar la interacción de la que solíamos HoloLens (primera generación).

![Asequibilidades visuales en planetas](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Adición de las asequiciones para forzar la toma
 
Una vez que hemos tenido el mecanismo básico de toma de fuerza con las asequibilidades visuales y de audio, hemos visto cómo hacer que la selección de planetas sea más fácil de usar. Había dos aspectos principales que abordar: dado que el sistema solar es una interfaz móvil 3D, hay una complejidad adicional para que los usuarios aprendan a dirigirse a objetos de forma coherente. Esto se com compuesto por el hecho de que el rayo de la mano es rápido para seleccionar un objeto, lo que hace que los planetas se muevan hacia el usuario increíblemente rápidamente.

Hemos abordado esto con una solución de tres puntos. La primera fue bastante intuitiva: ralentizar el proceso de selección para que los planetas se acerquen al usuario a un ritmo más natural. Una vez que se ha ajustado la velocidad, hemos tenido que volver a visitar las asequibilidades visuales y de audio, agregando comentarios de audio a medida que se realizaba el seguimiento del planeta hacia el usuario.

La segunda parte de la solución era hacer que la visualización de toda la interacción force grab fuera tangible. Hemos visualizado una línea gruesa que se mueve hacia el objeto de destino una vez que el rayo de mano se conecta con él y, a continuación, devuelve el objeto al usuario, como un lasso. 

![Asequibilidades de "lasso" visuales para la toma de fuerza](images/ge-update-lasso-affordances.png)

Por último, hemos optimizado la escala del sistema solar para que los planetas fueran lo suficientemente grandes como para que la mirada y el rayo de la mano del usuario se dirigiran a ellos. 

Estas tres mejoras permiten a los usuarios realizar selecciones precisas, llamando a los planetas de una manera intuitiva. En general, el efecto de la toma de fuerza final es una experiencia más envolvente e interactiva en el sistema solar.

## <a name="spotlight-on-jupiter"></a>Spotlight on Jupiter

La creación de los cuerpos solares de la vía de la leche fue una experiencia desalmada. En concreto, las características únicas de La Ándalo hacen que sea una visión a la vista. Es el mayor y más vistoso de los gigantes gaseosos y contiene más masa que todos los demás planetas combinados. Su gran tamaño y su mesmerizadora banda de lenbulencia y dinámica de nube son una atención especial.

### <a name="geometry-and-meshes"></a>Geometría y mallas

Como gas gigante, las conchas exteriores de Al asco están formadas por capas gaseosas. La combinación de su velocidad de rotación rápida, el intercambio térmico interno y Coriolis fuerza la creación de capas y flujos de colores que se forman en bandas y vórtices en la nube. La captura de esta intrincada dicha fue clave para crear nuestro sistema solar.

Estaba claro inmediatamente que el uso de técnicas de visualización como simulaciones de fluidos y texturas animadas con secuencias precalutadas no estaba en cuestión. La potencia informática necesaria para simular esto en combinación con todo lo demás que sucede simultáneamente habría tenido un impacto perjudicial significativo en el rendimiento. 

![Información general sobre el objeto Desándalo](images/ge-update-jupiter-shells-complete.jpg)

El siguiente enfoque era una solución de "humo y reflejo", que consistía en superponer capas de textura transparentes, cada una de las cuales abordaba un aspecto específico del movimiento ambiental, compilado en una composición de mallas rotatorias.

En la imagen siguiente, puede ver el shell interno a la izquierda. Esta capa de capas proporcionaba un fondo a la composición para protegerse frente a pequeñas brechas entre las varias capas que formaron las nubes. Debido a la rotación lenta de la capa, también sirve como búfer visual entre las bandas móviles más rápidas para ayudar a crear unidad visual en todas las capas.

Después de establecer este delimitador en el modelo, las capas de nube en movimiento se proyectaron a continuación en las mallas central y derecha que se ven a continuación.

![Información general sobre el objeto Desuso con shells separados](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturizado

La textura existente se separó en un atlas de textura de tres partes: el tercero superior hospeda una capa sin movimiento de nubes con espacios para proporcionar un efecto paralaje, la sección central contiene los flujos externos de movimiento rápido y el tercero inferior contiene una capa base interna de rotación lenta.

La característica Great Red Spot también se separó en sus distintas partes móviles y, a continuación, se insertó en un área invisible de la textura. Estos componentes se pueden ver como las especificaciones de color rojo en la sección central de la imagen siguiente.

Dado que cada banda tiene una dirección y velocidad específicas, la textura se aplicó individualmente a cada malla. A continuación, las mallas tenían un centro común y un punto de pivote, lo que hacía posible animar de forma concéntrica toda la superficie.

![Introducción a las texturas de Textura](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Comportamiento de rotación y textura

Una vez que se estableció la composición visual de La luna, era necesario asegurarse de que las velocidades de rotación y rotación se calcularon y aplicaron correctamente en consecuencia. La rotación completa tarda aproximadamente 9 horas en completarse. Esto es una cuestión de definición debido a su rotación diferencial. Por lo tanto, la secuencia ecuatorial se ha establecido como una "secuencia maestra", con una rotación completa de 3600 fotogramas. Todas las demás capas necesitaban tener una velocidad de rotación como factor de 3600 para que coincida con su posición inicial, lo que permite, por ejemplo, 600, 900, 1200, 1800, etc.

![Texturas shell de Shell de Shell de Shell](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>La gran zona roja

Las secuencias rotativas individualmente proporcionan una buena impresión visual, pero carecen de detalle cuando se observan a un intervalo cercano.

La parte más llamativa fue great red spot (Gran spot rojo) de Al aserción, por lo que creamos un conjunto de mallas y texturas específicamente para presentarlo.
 
Se usó un mecanismo similar al de las bandas de Quesada: se componía un conjunto de partes rotativas unas encima de otras, mientras que también se agrupaban bajo su "capa maestra" para garantizar que permanecen en su posición independientemente de la rapidez con la que se mueva el resto.

Cuando las mallas se configuraron y se aplicaron, se aplicaron distintas capas del vórtex stormy y, a continuación, cada disco se animaba individualmente, las piezas centrales se movían más rápido y el resto se ralentizaba progresivamente a medida que se desplazaba hacia el exterior.

![Malla de Great Red Spot de Great Red Spot](images/ge-update-great-red-spot-mesh.jpg)

La composición también tenía el mismo pivote que todas las demás mallas, a la vez que mantiene su inclinación desde su eje Y original (!) para permitir la libertad de animar la rotación. 3600 fotogramas es la velocidad base, y cada capa tiene un factor de esto como un período de rotación.

![Textura great red spot](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Obtención correcta en Unity

Hay un par de aspectos clave que debe tener en cuenta al implementar esto en Unity.

Unity se confundía fácilmente cuando se trabaja con grandes conjuntos de capas transparentes. La solución era duplicar el material de textura para cada malla y aplicar valores ascendentes de cola de representación progresivamente desde el interior al exterior en 5 a cada material.

El resultado era que el shell interno tenía un valor de cola de representación de 3000 (valor predeterminado), el exterior estático de color rojo más adelante tenía un valor de 3005 y las nubes externas blancas rápidas tenían 3010. La gran zona roja (que progresa de la capa interna a la externa) finalizó con un valor de 3025 en este modelo.

![Objeto final Desaprobación](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Toques finales

Al principio, las capas de capa de textura se configuraron, lo que resultaba insuficiente para la implementación.

El sombreador Planet Standard original, y todas sus variaciones, reciben su información de iluminación a través de un script, SunLightReceiver, que no es compatible con el sombreador MRTK Standard.

El simple intercambio de los sombreadores no era una solución porque el sombreador Planet Standard no admite mapas de textura con transparencias. Se ha editado este sombreador para que la compilación de Asíns funcione según lo previsto.

Por último, las mezclas alfa deben configurarse estableciendo la mezcla de origen en 10 y la mezcla de destino en 5.

![Propiedades de Unity unity de Unity de Unity](images/ge-update-jupiter-unity-render-queue.jpg)

Puede ver la representación final de Asíns en Galaxy Explorer.

## <a name="meet-the-team"></a>Conozca al equipo 

Nuestro Mixed Reality studio está configurado por diseñadores, creadores en 3D, especialistas en experiencias de usuario, desarrolladores, un administrador de programas y un jefe de estudio. Procedemos de todo el mundo: Países Bajos, Canadá, Alemania, Israel, Japón, Reino Unido y el Estados Unidos. Somos un equipo de arquitectura que procede de una amplia experiencia: juegos, tanto tradicionales como independientes, marketing digital, atención sanitaria y ciencia.

Nos complace crear Galaxy Explorer para HoloLens 2 y actualizar las versiones HoloLens (primera generación), VR y escritorio. 

![El equipo de Galaxy Explorer](images/ge-update-team-image.png)

De arriba a derecha: ArtemisA Tsouflidou (desarrollador), Angie Teickner (Diseñador visual), David Janer (diseñador de UX), Janés Julia (director de producción de Delivery &), Yasfli Zonno (director creativo), Eline Ledent (desarrollador) y BenRta (desarrollador sr. ).
Abajo de izquierda a derecha: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist) y Dirk Sonbina (Studio Head).
No destacados: Tim Jailken (director técnico) y Sale Salandin (Visual Designer).

## <a name="additional-information"></a>Información adicional

### <a name="mixed-reality-studios"></a>Mixed Reality Studios

Los equipos de Microsoft Mixed Reality Studio, ubicados en Las Américas, Europa y Asia-Pacific, son expertos en diseño de experiencia del usuario, computación holográfica, tecnologías de AR/VR y desarrollo 3D. incluida la creación de recursos 3D, DirectX, Unity y Unreal. Le ayudaremos a imaginar los futuros deseados, diseñar, crear y entregar soluciones, al tiempo que permitimos a los clientes crear un impacto medible en toda su organización. Los estudios trabajan estrechamente con más de 22 000 profesionales de servicios de Microsoft para la integración, adopción, operaciones y soporte técnico de aplicaciones empresariales.