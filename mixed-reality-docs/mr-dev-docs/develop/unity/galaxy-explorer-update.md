---
title: La creación del explorador de Galaxy para HoloLens 2
description: Obtenga información sobre cómo el equipo está actualizando el proyecto de código abierto de Galaxy Explorer para HoloLens 2 en GitHub.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: Explorador de Galaxy, caso práctico, proyecto, ejemplo, MRTK, kit de herramientas de realidad mixta, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 2d72e005bd955bbf2611f0724ba63b80c70f7dc1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759821"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>La creación del explorador de Galaxy para HoloLens 2

Este es el explorador de Galaxy actualizado para la aplicación HoloLens 2. El [Explorador de Galaxy](/windows/mixed-reality/galaxy-explorer "Explorador de la galaxia") se desarrolló originalmente como una aplicación de código abierto para HoloLens (First gen) a través del programa de compartir ideas, y es una de las primeras experiencias de realidad mixta que muchos usuarios tenían. Ahora lo estamos actualizando para las [nuevas y emocionantes funcionalidades de HoloLens 2](https://www.microsoft.com/hololens/hardware).

Como uno de los [estudios de realidad mixta de Microsoft](galaxy-explorer-update.md#mixed-reality-studios), normalmente desarrollamos soluciones de calidad comercial y desarrollamos & pruebas en las plataformas de destino a lo largo del proceso de desarrollo y creativo. Estamos embarcados en este proyecto con los marcos y las herramientas (como [MRTK](mrtk-getting-started.md)) a medida que están disponibles para nosotros y la comunidad, y queremos que le llevemos el paso.

Al igual que el explorador de Galaxy original, [nuestro equipo](galaxy-explorer-update.md#meet-the-team) [abrirá el proyecto en github](https://github.com/Microsoft/GalaxyExplorer) para asegurarse de que la comunidad tiene acceso completo. También documentaremos nuestro viaje aquí con una transparencia completa sobre cómo migramos de MRTK v1 a MRTK V2, hemos mejorado la experiencia con las nuevas características disponibles en HoloLens 2 y hemos asegurado de que el explorador de Galaxy seguía siendo una experiencia multiplataforma. Si está viendo el explorador de Galaxy en HoloLens (primera generación), HoloLens 2, un casco de realidad mixta de Windows o en el escritorio de Windows 10, queremos asegurarnos de que está disfrutando del viaje tan bien como estamos.

Esta página se expandirá a medida que progresamos en el proyecto con vínculos a artículos más detallados, código, artefactos de diseño y documentación adicional de MRTK para proporcionarle una mirada al proyecto.

## <a name="unveiling-the-new-logo"></a>Desvelando el nuevo logotipo

Nos complace comenzar con una vista previa del nuevo logotipo de Galaxy Explorer. Mientras paga Homage al logotipo original con la forma de la leche, hemos diseñado una visualización realista y actualizado la tipografía para ofrecer una sensación más moderna. En el logotipo se incluye un vistazo a uno de los nuevos iconos.

![Nuevo logotipo de Galaxy Explorer](images/ge-update-app-icon.png)

El diseño y la tipografía del logotipo establecerán el tono de la apariencia general de los elementos de la interfaz de usuario a lo largo de la experiencia. 

## <a name="thinking-about-interactions"></a>Pensar en las interacciones

Como Creative Studio, estábamos ECSTATIC acerca del privilegio para migrar el explorador de Galaxy a HoloLens 2. Sabíamos que, al principio, deseamos que la experiencia sea una celebración del nuevo dispositivo y demostrar que el uso de la realidad mixta solo está limitado por la imaginación.

HoloLens 2 permite a los usuarios tocar, captar y trasladar hologramas de formas que parezcan naturales: responden a un gran número de objetos reales. Los modelos de mano totalmente articulados son increíbles, ya que permite a los usuarios hacer lo que le parece natural. Por ejemplo, todo el mundo recoge un taza ligeramente diferente y, en lugar de aplicar una manera determinada de hacerlo, HoloLens 2 le permite hacerlo.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Se trata de un cambio significativo de las interfaces basadas en Air TAP en dispositivos HoloLens de primera generación. En lugar de interactuar con los hologramas a partir de una distancia, ahora los usuarios pueden obtener el "cierre y personal". Al migrar experiencias existentes a HoloLens 2 o planear otras nuevas, es importante familiarizarse con la manipulación directa de los hologramas.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Manipulación directa frente a las grandes distancias en el espacio

Es una experiencia mágica para ponerse en contacto con usted, tomar un planeta y mantenerlo a mano. El reto de este enfoque es el tamaño del sistema solar, lo que es enorme. El usuario tendría que desplazarse por su habitación para ponerse a cerca de cada planeta para interactuar con él.

Para permitir que los usuarios interactúen con objetos que están más lejos, MRTK ofrece rayos de mano que salen del centro de la palma del usuario, actuando como una extensión de la mano. Se adjunta un cursor en forma de anillo al final del rayo para indicar dónde se corta el rayo con un objeto de destino. El objeto en que se posa el cursor puede recibir comandos gestuales de la mano. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

En la versión original del explorador de Galaxy, el usuario destinaría un planeta con el cursor de mirar y, a continuación, puntee en Air para llamarlo. La forma más fácil de migrar la experiencia a HoloLens 2 es tomar este comportamiento y usar los rayos de mano para seleccionar los planetas. Aunque esto era funcional, nos dejó más.

### <a name="back-to-the-drawing-board"></a>Volver al panel de dibujo

Nos hemos incorporado a ideate lo que podría basarse en las interacciones existentes. El pensamiento era: aunque HoloLens 2 permite a los usuarios interactuar con hologramas de maneras naturales y realistas, los hologramas no son reales por definición. Por tanto, siempre que se plausible una interacción para el usuario, no importa si esa interacción sería posible con un objeto real o no, podemos hacer que sea posible.

Un concepto que se ha explorado se basó en Telekinesis: la capacidad de manipular objetos con una mente. A menudo, en las películas con súper héroe, una persona se encontraba con su mente y llama a un objeto en su mano abierta. Jugamos con la idea algo más y apareció con un boceto rápido de cómo podría funcionar el concepto.

![Concepto de la interacción forzar toma](images/ge-update-interactions-concept-force-grab.png)

El usuario apuntaría al rayo de la mano en un planeta, lo que proporcionaría comentarios de destino. A medida que el usuario amplía su mano abierta, el planeta se extraerá hacia el usuario mediante una fuerza mágica hasta que esté lo suficientemente cerca para captarla. Por lo tanto, el nombre de la interacción: Force tomar. Como el usuario descartaría el planeta con su mano abierta, volvería a su órbita.

### <a name="force-grab-prototyping"></a>Forzar el prototipo de agarre

Después creamos varios prototipos para probar el concepto: ¿cómo se siente la interacción en general? ¿El objeto al que se ha llamado se detiene delante del usuario o se pega a sus manos hasta que se coloca? ¿Se debe cambiar el tamaño o la escala del objeto al que se llama?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementar Force tomar en la aplicación

Cuando intentamos realizar la toma forzada en los planetas, nos dimos cuenta de que teníamos que cambiar la escala del sistema solar. Resultó que una representación precisa y mediana del sistema solar es difícil para los usuarios entender y navegar, por lo que no sabía dónde mirar. Sin embargo, una representación de pequeño tamaño hizo que algunos planetas sean demasiado pequeños para que se puedan seleccionar fácilmente. Como resultado, el tamaño de los planetas y el espaciado entre los objetos solares se diseñó para sentirse cómodos en una habitación de tamaño medio manteniendo una precisión relativa.

En las fases posteriores de nuestro Sprint de desarrollo, estábamos lo suficientemente afortunado como para tener expertos en la realidad mixta de MSFT en la empresa, por lo que tenemos que trabajar como evaluadores expertos y realizar iteraciones rápidas en la interacción forzada.

![Jesus Kam probar una versión preliminar de Galaxy Explorer](images/ge-update-user-testing.png)

En la imagen: Jesus Kam, responsable de diseño Senior, prueba de trabajo en curso del explorador de Galaxy.

### <a name="adding-affordances-for-targeting"></a>Agregar prestaciones para el destino

Como hemos experimentado en HoloLens 2, encontramos que, aunque las nuevas interacciones son naturales e intuitivas, los hologramas siguen siendo los mismos: sin peso ni sensationss táctiles. Dado que los hologramas no proporcionan comentarios naturales que se usan para recibir cuando interactúan con objetos, es necesario crearlos.

Pensamos en los comentarios visuales y de audio que se proporcionaron los usuarios para las distintas fases de sus interacciones, y como el mecanismo de toma forzada es fundamental para interactuar con el explorador de Galaxy, hicimos muchas iteraciones. El objetivo era encontrar el equilibrio adecuado entre audio y comentarios visuales para cada fase de la interacción: centrarnos en el objeto deseado, llamarlo al usuario y, a continuación, soltarlo. Lo que hemos aprendido es que se requirieron más comentarios visuales y de audio para reforzar la interacción de lo que se solía usar para HoloLens (First gen).

![Prestaciones visuales en planetas](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Agregar prestaciones para forzar la toma
 
Una vez que teníamos el mecanismo básico de captación de fuerza con prestaciones visuales y de audio, analizamos cómo hacer que la selección de planetas sea más fácil de usar. Había dos cosas principales que abordar: dado que el sistema solar es una interfaz en movimiento 3D, se ha agregado una complejidad a los usuarios para aprender a dirigirse a los objetos de forma coherente. Esto se ha compuesto por el hecho de que el rayo de mano es más rápido al seleccionar un objeto, lo que hace que los planetas se muevan hacia el usuario increíblemente rápidamente.

Lo hemos aproximado con una solución de tres clavijas. La primera era bastante intuitiva: ralentiza el proceso de selección para que los planetas se acerquen al usuario a un ritmo más natural. Una vez ajustada la velocidad, tuvimos que revisar las prestaciones de audio y visuales, agregando comentarios de audio a medida que se realiza un seguimiento del planeta hacia el usuario.

La segunda parte de la solución era hacer que la visualización de toda la interacción de captación de fuerza sea tangible. Hemos visualizado una línea gruesa que se desplaza hacia el objeto de destino una vez que el rayo de mano se conecta con él y, a continuación, devuelve el objeto al usuario como un lazo. 

![Prestaciones de "lazo" visual para la toma de fuerza](images/ge-update-lasso-affordances.png)

Por último, optimizamos la escala del sistema solar para que los planetas fueran lo suficientemente grandes como para que el rayo y el rayo del usuario se dirijan a ellos. 

Estas tres mejoras permitían a los usuarios realizar selecciones precisas, llamando a los planetas de manera intuitiva. En general, el efecto de la toma de fuerza final es una experiencia más envolvente e interactiva en el sistema solar.

## <a name="spotlight-on-jupiter"></a>Spotlight en Júpiter

La creación de los cuerpos solares de la forma láctea era una experiencia Humbling. En concreto, las características únicas de Júpiter lo convierten en una visión de BEHOLD. Es el mayor y más colorido de los Giants de gas, y contiene más masa que todos los demás planetas combinados. Su gran tamaño y las bandas de mesmerizing de las turbulencias y la dinámica de la nube se Prefect para una atención artística especial.

### <a name="geometry-and-meshes"></a>Geometría y mallas

Como gigante del gas, los shells exteriores de Júpiter están compuestos de capas gaseosas. La combinación de la velocidad de rotación rápida, el intercambio de calor interno y las fuerzas de Coriolis crea capas y flujos vistosos que forman el Vortices de los cinturones de la nube y los. La captación de esta compleja belleza era clave al crear nuestro sistema solar.

Antes estaba claro que el uso de técnicas de visualización como las simulaciones fluidas y las texturas animadas con flujos precalculados no me cuestionaba. La potencia informática necesaria para simular esto en combinación con todo lo demás que se produce de forma simultánea habría tenido efectos perjudiciales en el rendimiento. 

![Información general sobre el objeto Júpiter](images/ge-update-jupiter-shells-complete.jpg)

El siguiente enfoque era una solución de "humo y reflejo", que consiste en la superposición de capas de textura transparentes, cada una de las cuales dirigió un aspecto específico del movimiento atmosférico, compilada en una composición de mallas de rotación.

En la imagen siguiente, puede ver el shell interno a la izquierda. Este nivel de paspartú proporcionó un fondo para la composición con el fin de protegerse frente a huecos pequeños entre las distintas capas que componen las nubes. Debido a la rotación lenta de la capa, también se sirve como un búfer visual entre las bandas de movimiento más rápido para ayudar a crear Unity visual a lo largo de las capas.

Después de establecer este delimitador en el modelo, las capas de la nube en movimiento se proyectan en las mallas central y derecha que se muestran a continuación.

![Información general sobre el objeto Júpiter con shells separados](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturización

La textura existente se separó en un Atlas de texturas de tres partes: el tercio superior hospeda una capa motionless de nubes con huecos para proporcionar un efecto parallax, la sección central contiene las secuencias exteriores de movimiento rápido y la tercera parte inferior contiene una capa base interna que gira lentamente.

La excelente zona roja también se separó en las distintas partes móviles y, a continuación, se insertan en un área invisible de la textura. Estos componentes pueden verse como motas de toned en la sección central de la imagen siguiente.

Dado que cada banda tiene una dirección y una velocidad específicas, la textura se aplicó individualmente a cada malla. A continuación, las mallas tenían un centro común y un punto de pivote, lo que hace posible animar de forma interactiva toda la superficie.

![Información general de las texturas de Júpiter](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Comportamiento de giro y textura

Una vez que se ha establecido la composición visual de Júpiter, es necesario asegurarse de que las velocidades de rotación y órbita se calcularon correctamente y se aplicaron en consecuencia. Tarda aproximadamente 9 horas en Júpiter en completar una rotación completa. Se trata de una cuestión de definición debido a su rotación diferencial. Por lo tanto, el flujo de Guinea se ha establecido como una "secuencia maestra", que toma 3600 fotogramas para una rotación completa. Cada otra capa necesitaba tener una velocidad de rotación como factor de 3600 para que coincida con su posición inicial, lo que permite, por ejemplo, 600, 900, 1200, 1800, etc.

![Las texturas de Shell de Júpiter](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>La gran zona roja

Los flujos que giran individualmente proporcionan una buena impresión visual, pero que faltan en detalle cuando se observan en el intervalo de cierre.

La parte más atractiva es la excelente zona roja, por lo que creamos un conjunto de mallas y texturas específicamente para exhibirlas.
 
Usamos un mecanismo similar al de las bandas de Júpiter: un conjunto de piezas giratorias se creó entre sí, a la vez que se agrupaba bajo su ' capa maestra ' para asegurarse de que permanecen en la posición independientemente de la rapidez con que se mueva el resto.

Una vez configuradas y colocadas las mallas, se aplicaron diferentes capas del Vortex de Storm y cada disco se animaría individualmente, las piezas centrales se mueven con más rapidez, con lo que el resto se ralentiza gradualmente a medida que se mueve hacia afuera.

![Malla de gran zona roja de Júpiter](images/ge-update-great-red-spot-mesh.jpg)

La composición también tenía la misma dinamización que las demás mallas, a la vez que mantiene su inclinación de su eje y original (!) para permitir la libertad de animación de la rotación. 3600 fotogramas es la tasa base, donde cada capa tiene un factor de esto como un período de rotación.

![Textura de la zona roja de Júpiter grande](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Obtenerlo directamente en Unity

Hay un par de aspectos clave que hay que tener en cuenta al implementar esto en Unity.

Unity se confunde fácilmente cuando se trabaja con grandes conjuntos de capas transparentes. La solución era duplicar el material de textura de cada malla y aplicar los valores de cola de representación ascendentes progresivamente desde el interior al exterior en 5 a cada material.

El resultado era que el shell interno tenía un valor de cola de representación de 3000 (valor predeterminado), el externo rojo-toned externo tenía un valor de 3005, mientras que las nubes externas de blanco rápido tenían 3010. La gran zona roja (que progresa de la capa interna a la externa) ha finalizado con un valor de 3025 en este modelo.

![Júpiter final (objeto)](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Toques finales

En primer lugar, se configuraron las capas de Júpiter con textura, lo que demostró ser insuficientes para la implementación.

El sombreador estándar del planeta original y todas sus variaciones, reciben la información de iluminación a través de un script, el SunLightReceiver, que no es compatible con el sombreador estándar de MRTK.

Simplemente el intercambio de los sombreadores no era una solución porque el sombreador estándar del planeta no admite mapas de texturas con transparencias. Hemos editado este sombreador para que la compilación de Júpiter funcione según lo previsto.

Por último, las mezclas alfa deben configurarse estableciendo la mezcla de origen en 10 y la mezcla de destino en 5.

![Propiedades de Unity de Júpiter](images/ge-update-jupiter-unity-render-queue.jpg)

Puede ver la representación final de Júpiter en el explorador de Galaxy.

## <a name="meet-the-team"></a>Conozca al equipo 

Nuestro equipo de estudio de realidad mixta se compone de diseñadores, artistas en 3D, especialistas de experiencia del usuario, desarrolladores, un administrador de programas y un director de estudio. Nos sentimos del mundo: Bélgica, Canadá, Alemania, Israel, Japón, Reino Unido y el Estados Unidos. Somos un equipo multidisciplinar que proviene de un fondo diverso: juegos, tanto tradicionales como indie, marketing digital, sanidad y ciencia.

Nos complace crear el explorador de Galaxy para HoloLens 2 y para actualizar las versiones de HoloLens (primera generación), VR y Desktop. 

![El equipo del explorador de Galaxy](images/ge-update-team-image.png)

En la parte superior de izquierda a derecha: Artemis Tsouflidou (desarrollador), Angie Teickner (diseñador visual), David Janer (diseñador de la experiencia de usuario), Laura Garrett (entrega & responsable de producción), Yasushi Zonno (responsable creativo), Eline Ledent (desarrollador) y Ben Turner (Sr. Developer).
Inferior de izquierda a derecha: Amit Rojtblat (intérprete técnico), Martin Wettig (artista 3D) y Dirk Songuer (Director de estudio).
No destacado: Tim Gerken (responsable técnico) e Oscar Salandin (diseñador visual).

## <a name="additional-information"></a>Información adicional

### <a name="mixed-reality-studios"></a>Estudios de realidad mixta

Los equipos de Microsoft Mixed Reality Studio (ubicados en América, Europa y Asia-Pacific) son expertos en el diseño de la experiencia del usuario, la informática Holographic, las tecnologías de AR/VR y el desarrollo en 3D. incluye la creación de activos en 3D, DirectX, Unity y no real. Ayudamos a imaginar futuros, diseñar, compilar y ofrecer soluciones, a la vez que permite a los clientes crear un impacto medible en su organización. Los estudios trabajan en estrecha colaboración con más de 22.000 profesionales de servicios de Microsoft para la integración, adopción, operaciones y soporte técnico de aplicaciones empresariales.