---
title: Making of Galaxy Explorer for HoloLens 2
description: Obtenga información sobre cómo nuestro equipo está actualizando el proyecto de código abierto Galaxy Explorer para HoloLens 2 en GitHub.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer, case study, project, sample, MRTK, Mixed Reality Toolkit, Unity, sample apps, example apps, open source, Microsoft Store, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 1e19f63f493eba2559cf60ef7c1224b7323ec825
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757082"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>La realización de Galaxy Explorer para HoloLens 2

![Nuevo logotipo de Galaxy Explorer](../images/GalaxyExplorer2.jpg)


Le damos la bienvenida a la aplicación Galaxy Explorer HoloLens 2 actualización. [Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Explorador de la galaxia") se desarrolló originalmente como una aplicación de código abierto para HoloLens (primera generación) a través del programa Compartir tu idea, y es una de las primeras experiencias de realidad mixta que muchas personas han tenido. Ahora lo estamos actualizando para las [nuevas y emocionantes funcionalidades de HoloLens 2](https://www.microsoft.com/hololens/hardware).

Como uno de los microsoft [Mixed Reality Studios,](galaxy-explorer-update.md#mixed-reality-studios)normalmente desarrollamos soluciones de nivel comercial y desarrollamos pruebas de & en plataformas de destino a lo largo del proceso de desarrollo y creación. Nos estamos lanzando a este proyecto con los marcos y herramientas (como [MRTK)](mrtk-getting-started.md)a medida que están disponibles para nosotros y la comunidad, y queremos llevarle a la carrera.

Al igual que la versión original [](https://github.com/Microsoft/GalaxyExplorer) de Galaxy [Explorer,](galaxy-explorer-update.md#meet-the-team) nuestro equipo abrirá el proyecto en GitHub para asegurarse de que la comunidad tiene acceso completo. También vamos a documentar nuestro recorrido aquí con total transparencia sobre cómo se ha pasado de MRTK v1 a MRTK v2, se ha mejorado la experiencia con nuevas características disponibles en HoloLens 2 y se ha asegurado de que Galaxy Explorer sigue siendo una experiencia multiplataforma. Ya sea que vea Galaxy Explorer en HoloLens (primera generación), HoloLens 2, un casco de Windows Mixed Reality o en el escritorio de Windows 10, queremos asegurarnos de que está disfrutando del viaje tanto como estamos.

Esta página se expandirá a medida que avancemos por el proyecto con vínculos a artículos más detallados, código, artefactos de diseño y documentación adicional de MRTK para proporcionarle una vista interna del proyecto.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Descarga de la aplicación Microsoft Store en HoloLens 2
Si tiene HoloLens 2 dispositivo, puede descargar e instalar directamente la aplicación en el dispositivo.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>Pensar en las interacciones

Como estudio creativo, nos hemos quedó extáticos sobre el privilegio de portabilidad de Galaxy Explorer a HoloLens 2. Sabíamos desde el principio que queríamos que la experiencia fuera una demostración del nuevo dispositivo y que demostrara que Mixed Reality capacitación solo está limitada por la imaginación.

HoloLens 2 permite a los usuarios tocar, comprender y mover hologramas de maneras que se sientan naturales: responden mucho como objetos reales. Los modelos de mano totalmente articulados son increíbles, ya que permiten a los usuarios hacer lo que parece natural. Por ejemplo, todos los usuarios recogen un café de forma ligeramente diferente y, en lugar de aplicar una manera determinada de hacerlo, HoloLens 2 le permite hacerlo a su manera.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Se trata de un cambio significativo de las interfaces basadas en Air Tap en dispositivos de primera generación HoloLens dispositivos. En lugar de interactuar con hologramas desde una distancia, los usuarios ahora pueden estar "cerca y personalmente". Al portear experiencias existentes a HoloLens 2 o planear otras nuevas, es importante familiarizarse con la manipulación directa de hologramas.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Manipulación directa frente a las grandes distancias en el espacio

Es una experiencia mágica para alcanzar, agarrar un planeta y agarrarlo en la mano. El desafío con este enfoque es el tamaño del sistema solar, es enorme. El usuario tendría que recorrer su habitación para acercarse a cada planeta para interactuar con ella.

Para permitir que los usuarios interactúen con objetos que están más lejos, MRTK ofrece rayos de mano que sale del centro de la mano del usuario, actuando como una extensión de la mano. Se adjunta un cursor con forma de anillo al final del rayo para indicar dónde forma una intersección con un objeto de destino. El objeto en que se posa el cursor puede recibir comandos gestuales de la mano. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

En la versión original de Galaxy Explorer, el usuario apuntaba a un planeta con el cursor de mirada y, a continuación, pulsaba en el aire para llamarlo más cerca. La manera más fácil de portabilidad de la experiencia HoloLens 2 es tomar este comportamiento y usar rayos de mano para seleccionar planetas. Aunque esto era funcional, nos dejó deseando más.

### <a name="back-to-the-drawing-board"></a>Volver a empezar desde cero

Nos unimos para idear lo que se podría crear sobre las interacciones existentes. La idea era: aunque HoloLens 2 permite a los usuarios interactuar con hologramas de manera natural y realista, los hologramas no son reales por definición. Por lo tanto, siempre que una interacción sea plausible para el usuario, no importa si esa interacción sería posible con un objeto real o no, podemos hacerlo posible.

Un concepto que exploramos se basaba en la telekinesis: la capacidad para manipular objetos con la mente de uno. A menudo, en las películas de super hero, una persona se acercaba con su mente y llamaba a un objeto a mano abierta. Hemos tocado con la idea algo más y se ha ideado un breve boceto de cómo podría funcionar el concepto.

![Concepto de la interacción force grab](images/ge-update-interactions-concept-force-grab.png)

El usuario apuntaría el rayo de la mano a un planeta, lo que proporcionaría comentarios de destino. A medida que el usuario extiende su mano abierta, el planeta se acercaría al usuario mediante una fuerza mágica hasta que esté lo suficientemente cerca como para agarrarlo. Por lo tanto, nuestro nombre para la interacción: force grab. Como el usuario alejaba el planeta con la mano abierta, se devolvía de nuevo a su gira.

### <a name="force-grab-prototyping"></a>Creación de prototipos de toma de fuerza

A continuación, creamos varios prototipos para probar el concepto: ¿Cómo se ve la interacción en general? ¿Debe detenerse el objeto llamado delante del usuario o detenerse a las manos hasta que se coloque? ¿El objeto al que se llama debe cambiar de tamaño o escala mientras se llama?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementación de force grab en la aplicación

Cuando intentamos la toma de fuerza en los planetas, nos dimos cuenta de que había que cambiar la escala del sistema solar. Resulta que una representación precisa y de tamaño medio del sistema solar es difícil de entender y navegar para los usuarios; no saben dónde buscar. Sin embargo, una representación de tamaño pequeño hizo que algunos planetas sean demasiado pequeños para que se puedan seleccionar fácilmente. Como resultado, el tamaño de los planetas y el espaciado entre los objetos solares se diseñaron para que se sintase cómodos dentro de una sala de tamaño medio mientras se mantiene la precisión relativa.

Durante las fases posteriores del sprint de desarrollo, hemos tenido la suerte de tener expertos de MSFT Mixed Reality dentro, por lo que tenemos que trabajar para obtener sus entradas como evaluadores expertos y realizar iteraciones rápidas en la interacción de la toma de fuerza.

![Pruebas de una compilación en versión preliminar de Galaxy Explorer](images/ge-update-user-testing.png)

En la imagen: Senior Design Lead, tests a work-in-progress of Galaxy Explorer ./In picture: Senior Design Lead, testing a work-in-progress of Galaxy Explorer( In picture: Senior Design Lead, testing a work-in-progress of Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Adición de asequiciones para la orientación

A medida que experimentamos en HoloLens 2, hemos descubierto que, aunque las nuevas interacciones son naturales e intuitivas, los hologramas siguen siendo los mismos: sin peso ni sensibilidades táctiles. Puesto que los hologramas no proporcionan comentarios naturales que los seres humanos están acostumbrados a recibir cuando interactúan con objetos, es necesario crearlos.

Hemos pensado en los comentarios visuales y de audio que se proporcionarían a los usuarios para las distintas fases de sus interacciones y, dado que el mecanismo de toma de fuerza es fundamental para interactuar con Galaxy Explorer, hemos realizado muchas iteraciones. El objetivo era encontrar el equilibrio correcto de comentarios visuales y de audio para cada fase de la interacción: centrarse en el objeto deseado, llamarlo al usuario y, a continuación, liberarlo. Lo que aprendimos es que se necesitaron más comentarios visuales y de audio para reforzar la interacción de lo que solíamos hacer HoloLens (primera generación).

![Asequibilidades visuales en planetas](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Adición de asequiciones para forzar la toma
 
Una vez que teníamos el mecanismo básico de toma de fuerza con las asequibilidades visuales y de audio, hemos visto cómo hacer que la selección de planetas sea más fácil de usar. Había dos aspectos principales que abordar: dado que el sistema solar es una interfaz móvil 3D, los usuarios pueden aprender a dirigirse a los objetos de forma coherente. Esto se com compuesto por el hecho de que el rayo de la mano es rápido para seleccionar un objeto, lo que hace que los planetas se muevan hacia el usuario increíblemente rápidamente.

Hemos abordado este problema con una solución de tres puntos. La primera fue bastante intuitiva: ralentizar el proceso de selección para que los planetas se acerquen al usuario a un ritmo más natural. Una vez que se ha ajustado la velocidad, hemos tenido que volver a revisar las asequibilidades visuales y de audio, agregando comentarios de audio a medida que se realizaba el seguimiento del planeta hacia el usuario.

La segunda parte de la solución era hacer que la visualización de la interacción de toma de fuerza completa fuera tangible. Hemos visualizado una línea gruesa que se desplaza hacia el objeto de destino una vez que el rayo de mano se conecta con él y, a continuación, devuelve el objeto al usuario, como un lasso. 

![Asequiciones de "lasso" visuales para la toma de fuerza](images/ge-update-lasso-affordances.png)

Por último, hemos optimizado la escala del sistema solar para que los planetas fueran lo suficientemente grandes como para que la mirada y el rayo de la mano del usuario se dirigiran a ellos. 

Estas tres mejoras permitieron a los usuarios realizar selecciones precisas, llamando a los planetas de una manera intuitiva. En general, el efecto de la toma de fuerza final es una experiencia más inmersiva e interactiva en el sistema solar.

## <a name="spotlight-on-jupiter"></a>Spotlight on Jupiter

La creación de los cuerpos solares de la manera de la leche fue una experiencia de desmoronado. En concreto, las características únicas de La Loba hacen que sea una visión a la vista. Es el más grande y más vistoso de los gigantes gaseosos y contiene más masa que todos los demás planetas combinados. Su gran tamaño y sus mesmerizadoras bandas de revoluciones y dinámicas en la nube son especialmente llama la atención.

### <a name="geometry-and-meshes"></a>Geometría y mallas

Como gaseoso, las conchas exteriores de La Concha están formadas por capas gaseosas. La combinación de su velocidad de rotación rápida, el intercambio térmico interno y Coriolis fuerza la creación de capas y flujos de colores que se forman en cintas de nube y vórtices. La captura de esta intrincada dicha fue clave para crear nuestro sistema solar.

Estaba claro inmediatamente que el uso de técnicas de visualización como simulaciones fluidas y texturas animadas con secuencias precalutadas no estaba en cuestión. La capacidad informática necesaria para simular esto en combinación con todo lo demás que sucede simultáneamente habría tenido importantes efectos perjudiciales en el rendimiento. 

![Información general sobre el objeto Desándalo](images/ge-update-jupiter-shells-complete.jpg)

El siguiente enfoque era una solución de "humo y reflejo", que constaba de capas de textura transparente superpuestas, cada una de las cuales abordaba un aspecto específico del movimiento ambiental, compilado en una composición de mallas rotativas.

En la imagen siguiente, puede ver el shell interno a la izquierda. Esta capa de capas proporcionaba un fondo a la composición para protegerse frente a las pequeñas brechas entre las varias capas que formaron las nubes. Debido a la rotación lenta de la capa, también sirve como búfer visual entre las bandas móviles más rápidas para ayudar a crear unidad visual en todas las capas.

Después de establecer este delimitador en el modelo, las capas de nube móviles se proyectaron en las mallas central y derecha que se ven a continuación.

![Información general sobre el objeto Desuso con shells separados](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturizado

La textura existente se separó en un atlas de textura de tres partes: el tercero superior hospeda una capa de nubes sin movimiento con espacios para proporcionar un efecto paralaje, la sección central contiene los flujos exteriores de movimiento rápido y el tercero inferior contiene una capa base interna de rotación lenta.

La característica Great Red Spot también se separó en sus distintas partes móviles y, a continuación, se insertó en un área invisible de la textura. Estos componentes se pueden ver como las especificaciones de color rojo en la sección central de la imagen siguiente.

Dado que cada banda tiene una dirección y velocidad específicas, la textura se aplicó individualmente a cada malla. A continuación, las mallas tenían un centro común y un punto de pivote, lo que hacía posible animar de forma concéntrica toda la superficie.

![Introducción a las texturas de Texture](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Comportamiento de rotación y textura

Una vez que se estableció la composición visual de La luna, era necesario asegurarse de que las velocidades de rotación y rotación se calcularon y aplicaron correctamente en consecuencia. La rotación completa tarda aproximadamente 9 horas en completarse. Esto es una cuestión de definición debido a su rotación diferencial. Por lo tanto, la secuencia ecuatorial se ha establecido como una "secuencia maestra", con una rotación completa de 3600 fotogramas. Todas las demás capas necesitaban tener una velocidad de rotación como un factor de 3600 para que coincida con su posición inicial, lo que permite, por ejemplo, 600, 900, 1200, 1800, etc.

![Texturas shell de Shell de Shell de Shell](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>La gran zona roja

Las secuencias rotativas individualmente proporcionan una buena impresión visual, pero carecen de detalle cuando se observan a un intervalo cercano.

La parte más llamativa fue great red spot (Gran spot rojo) de Al aserción, por lo que creamos un conjunto de mallas y texturas específicamente para presentarlo.
 
Se usó un mecanismo similar al de las bandas de Quesada: se componía un conjunto de partes rotativas unas encima de otras, mientras que también se agrupaban bajo su "capa maestra" para garantizar que permanecen en su posición independientemente de la rapidez con la que se mueva el resto.

Cuando las mallas se configuraron y se aplicaron, se aplicaron distintas capas del vórtex stormy y, a continuación, cada disco se animaba individualmente, las piezas centrales se movían más rápido y el resto se ralentizaba progresivamente a medida que se desplazaba hacia el exterior.

![Malla de Great Red Spot de Great Red Spot](images/ge-update-great-red-spot-mesh.jpg)

La composición también tenía el mismo pivote que todas las demás mallas, a la vez que mantiene su inclinación desde su eje y original (!) para permitir la libertad a la hora de animar la rotación. 3600 fotogramas es la velocidad base, y cada capa tiene un factor de esto como un período de rotación.

![Textura great red spot](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Obtención correcta en Unity

Hay un par de aspectos clave que debe tener en cuenta al implementar esto en Unity.

Unity se confundía fácilmente cuando se trabaja con grandes conjuntos de capas transparentes. La solución era duplicar el material de textura para cada malla y aplicar valores ascendentes de cola de representación progresivamente desde el interior al exterior en 5 a cada material.

El resultado era que el shell interno tenía un valor de cola de representación de 3000 (valor predeterminado), el exterior estático de color rojo más adelante tenía un valor de 3005 y las nubes externas blancas rápidas tenían 3010. La gran zona roja (que progresa de la capa interna a la externa) finalizó con un valor de 3025 en este modelo.

![Objeto final Desaprobación](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Toques finales

Al principio, se configuraron las capas de Capa de capa con textura, lo que resultaba insuficiente para la implementación.

El sombreador Planet Standard original, y todas sus variaciones, reciben su información de iluminación a través de un script, SunLightReceiver, que no es compatible con el sombreador MRTK Standard.

El simple intercambio de los sombreadores no era una solución porque el sombreador Planet Standard no admite mapas de textura con transparencias. Se ha editado este sombreador para que la compilación de Almente funcione según lo previsto.

Por último, las mezclas alfa deben configurarse estableciendo la mezcla de origen en 10 y la mezcla de destino en 5.

![Propiedades de Unity unity de Unity de Unity](images/ge-update-jupiter-unity-render-queue.jpg)

Puede ver la representación final de Asíns en Galaxy Explorer.

## <a name="meet-the-team"></a>Conozca al equipo 

Nuestro Mixed Reality studio está configurado por diseñadores, creadores en 3D, especialistas en experiencias de usuario, desarrolladores, un administrador de programas y un jefe de estudio. Procedemos de todo el mundo: Países Bajos, Canadá, Alemania, Israel, Japón, Reino Unido y el Estados Unidos. Somos un equipo de arquitectura que procede de una amplia experiencia: juegos, tanto tradicionales como independientes, marketing digital, atención sanitaria y ciencia.

Nos complace crear Galaxy Explorer para HoloLens 2 y actualizar las versiones de HoloLens (primera generación), VR y escritorio. 

![El equipo de Galaxy Explorer](images/ge-update-team-image.png)

De arriba a derecha: ArtemisA Tsouflidou (desarrollador), Angie Teickner (Diseñador visual), David Janer (diseñador de UX),Dado Senior (director de producción de Delivery &), Yasfli Zonno (director de creación), Eline Ledent (desarrollador) y BenRta (desarrollador sr. ).
Abajo de izquierda a derecha: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist) y Dirk Sonhan (Studio Head).
No destacados: Tim Jailken (director técnico) y Sale Salandin (Visual Designer).

## <a name="additional-information"></a>Información adicional

### <a name="mixed-reality-studios"></a>Mixed Reality Studios

Los equipos de Microsoft Mixed Reality Studio, ubicados en Las Américas, Europa y Asia-Pacific, son expertos en diseño de experiencia del usuario, computación holográfica, tecnologías de AR/VR y desarrollo 3D. incluida la creación de recursos 3D, DirectX, Unity y Unreal. Le ayudaremos a imaginar los futuros deseados, diseñar, crear y entregar soluciones, al tiempo que permitimos a los clientes crear un impacto medible en toda su organización. Los estudios trabajan estrechamente con más de 22 000 profesionales de servicios de Microsoft para la integración, adopción, operaciones y soporte técnico de aplicaciones empresariales.