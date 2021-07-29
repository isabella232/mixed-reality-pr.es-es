---
title: Experiencia Ford GT40
description: Siga a medida que exploramos la realización de la aplicación de realidad mixta Ford GT40 con MRTK para HoloLens 2 en Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, deploy to device, PC, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
appliesto:
- HoloLens 2
ms.openlocfilehash: e634d75af92509372209d8e7c0cde2833127c128
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757206"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>La realización de la experiencia de Ford GT40
![Imagen principal de Ford GT40](images/ford-gt40-hero_1920.jpg)

*"Antes de MRTK, desarrollar para HoloLens 2 con Unreal era un poco tedioso porque todas las interacciones espaciales tenían que codificarse a mano, en C++. MrTK para Unreal hizo que muchas de esas mismas tareas fuera trivial. Calculo que se ha recortado el tiempo necesario para el prototipo inicial a la mitad".* - Jose Chan, desarrollador de software

*"La experiencia de Ford GT40 es una prueba de que una aplicación de HoloLens 2 de alta fidelidad se puede completar en tan solo unos meses, con un presupuesto moderado, pero todavía ofrece resultados muy impactantes".*  - Daniel Cháetham, director de innovación, Happy Finish

Con el Mixed Reality Toolkit (MRTK) para Unreal, la empresa de producción creadora Happy Finish ha ofrecido una experiencia de HoloLens 2 que proporciona una perspectiva nueva sobre ford GT40, el coche de carreras ineficiible que superó a Verd en las 24 horas de Le Mans.

Mediante una variedad de interacciones espaciales naturales e intuitivas, los usuarios pueden explorar la naturaleza, el rendimiento y la ingeniería de gt40, todo ello de una manera que aproveche la alta fidelidad visual proporcionada por Unreal Engine. El desarrollo de software para todo el proyecto lo completó un solo desarrollador en menos de tres meses, lo que mrtk ha hecho posible para el entorno de diseño y scripting visual de Unreal.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Descarga de la aplicación Microsoft Store en HoloLens 2
Si tiene HoloLens 2 dispositivo, puede descargar e instalar directamente la aplicación en el dispositivo.

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>La pregunta

Happy Finish es una de las empresas de producción creadoras más importantes del mundo, con una base de clientes que incluye, Ford, Microsoft, Wcf, Netflix, Vodafone y otros nombres de hogar. La empresa llegó a empezar como una agencia de foto-retouch de gama alta, bifurcando en el cine y CGI antes de extender su compromiso a la excelencia en la narración envolvente con el diseño espacial 3D y la interacción.

A mediados de 2020, Microsoft se abordó en Happy Finish para generar una aplicación de demostración que podría ayudar a mostrar las posibilidades habilitadas por el nuevo Mixed Reality Toolkit (MRTK) para Unreal, que se basa en la compatibilidad con HoloLens 2 en Unreal Engine. En este momento, la empresa ya tenía dos proyectos de Unreal on-HoloLens 2 correctos en su haber. Ambos eran para una marca de consumidor reconocida globalmente, que eligió Unreal en HoloLens 2 para una herramienta de ventas interna de R&D/B2B por su alta fidelidad visual, según sea necesario para presentar mejor los propios productos de gama alta de ese cliente.

Aunque la propia solución se dejara en Happy Finish, tenía que cumplir algunas directrices clave. En primer lugar, tuvo que centrarse en un escenario empresarial para ilustrar la utilidad de Unreal HoloLens 2 fuera del sector de los juegos. En segundo lugar, tenía que ser solo dispositivo, lo que significa que podía servir como demostración independiente, sin necesidad de una conexión de red y una potencia de procesamiento externa para obtener las velocidades de fotogramas de destino y la calidad visual. En tercer lugar, debe combinar la gama de interacciones intuitivas admitidas por MRTK en una experiencia sin problemas y natural. Por último, la solución propuesta debe mostrar la fidelidad visual inherente y otras ventajas del propio motor de Unreal, como las eficiencias del sombreador. 

Dadas estas directrices, Happy Finish comenzó a pensar en las posibilidades, con la idea de una experiencia de realidad mixta que usaba la interacción espacial para comunicar el valor de un producto de alto valor y nombre de marca. Después de considerar una variedad de objetos que incluían relojes, cámaras, automóviles y jets privados, Happy Finish decidió en última instancia ford GT40, una leyenda de automoción que alcanzó la notoriedad en 1966 cuando Ford superó a Led en las 24 horas de Le Mans, como se muestra en la película de bloques de 2019 Ford frente a Rand. 

Tras obtener la compra de Ford, un cliente de Happy Finish existente, la empresa se estableció para ofrecer una perspectiva nueva sobre el icono clásico de automoción.

## <a name="the-solution"></a>La solución

El trabajo comenzó el 7 de mayo de 2020. Después de obtener los archivos de modelo GT40, un intérprete en 3D pasó tres semanas optimizando modelos de polígono, asignación de UV, repintado de mapas de textura y condensando esos mapas en el menor número posible de texturas. Un intérprete técnico ha trabajado en paralelo para realizar pruebas comparativas de la salida del intérprete en 3D, determinar los tamaños óptimos de textura según las velocidades de fotograma objetivo y averiguar la mejor manera de aplicar sombreadores personalizados en Unreal. Todo este trabajo de preproducción se ha realizado para optimizar la experiencia en el dispositivo.

El director creativo Alex Lambert escribió la imagen una vez finalizado el trabajo de preproducción. Comenzó viendo Ford frente aAndo, pensando en cómo tejer una narrativa en torno a los escenarios y las interacciones. También recopiló referencias visuales para el intérprete de la interfaz de usuario, como imágenes del panel GT40 y objetos visuales del circuito de Le Mans, y recopilaba grabaciones de audio del GT40 en acción para el diseñador de sonidos.

Con los recursos de preproducción definidos y optimizados en la mano, el desarrollador de software de software de software Desconocedió a Jose Conexión para reunirlo todo. Había sido el desarrollador en los dos proyectos anteriores de Unreal-on-HoloLens 2 que Happy Finish había realizado, antes de que se publicara MRTK para Unreal.

El valor proporcionado por MRTK para Unreal se hizo evidente al principio, lo que ayuda a Proto a entregar un prototipo inicial en una semana. Implementó tres escenarios únicos, uno para cada uno de los aspectos clave del GT40 que Lambert había identificado: su iluminación, su rendimiento y su ingeniería. Para cada escenario, Matriz usó MRTK para integrar los recursos 3D optimizados de la fase de preproducción en una variedad de interacciones espaciales. 

Con MRTK para Unreal, Having ha creado cada escenario mediante el Diseñador de interfaz de usuario de gráficos de movimiento de Unreal (UMG) visual en lugar de tener que implementar todo en C++. Herramientas de UX para [Unreal,](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)el complemento que contiene componentes y bloques de creación de UX dentro de MRTK, le ha dado planos planos de [Unreal](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) para la simulación de entrada, interacciones de la mano de scripting visual, botones presionables, manipulación de imágenes 3D, magnetismo de superficie, etc., todo ello dentro de un entorno de diseño sin código, arrastrar y colocar.

"Antes de MRTK, desarrollar para HoloLens 2 con Unreal era un poco tedioso porque todas las interacciones espaciales tenían que codificarse a mano, en C++", afirma Matriz. "MrTK para Unreal hizo que muchas de esas mismas tareas fuera trivial. Calculo que se ha recortado el tiempo necesario para el prototipo inicial a la mitad".

Con un prototipo en la mano, el equipo comenzó iteraciones semanales para refinar la experiencia. "Aquí es cuando la característica Captura de realidad mixta y la Windows Portal de dispositivos resultaron realmente útiles", recuerda Lambert. "Las usé para capturar mis revisiones de diseño, difundir mis comentarios a otros usuarios y colaborar en los cambios. Trabajar de forma aislada de este modo habría sido imposible de hacer sin estas herramientas".

![Aplicación Ford GT40 del editor de Unreal que se ejecuta con componentes de rueda dispuestos en secuencia](images/ford-gt40-img-04.JPG)

A medida que Lambert solicitaba cambios, como cambiar la posición de los elementos de la interfaz de usuario o cambiar el comportamiento de un botón, Composición los implementaba. Aunque algunos de los cambios requerían pequeños ajustes de código, la mayoría de ellos se controló en el diseñador visual de Unreal. "Me he quedón con la rapidez con la que podía iterar", afirma How. "No se ha desperdiciado tiempo; Realizaría un cambio en el diseñador y, a continuación, presionaría Reproducir para verlo inmediatamente en el dispositivo. MrTK realmente ha simplificado mi trabajo".

También recuerda que se ha quedado impactado por la forma en que todas las herramientas de desarrollo estaban listas para producción. "Progresamos sin problemas desde el prototipo inicial hasta la producción final, sin tener que volver atrás y volver a implementar u optimizar las cosas en el código", afirma.  

## <a name="the-final-build"></a>La compilación final

Happy Finish completó la producción de ford GT40 Experience for HoloLens 2 el 28 de julio de 2020, proporcionando una perspectiva nueva sobre el coche de carreras más famoso. La experiencia comienza con una pantalla de bienvenida y, a continuación, guía al usuario para que configure un anclaje; para ello, toma el logotipo de Ford y lo coloca en una superficie plana como una tabla o un escritorio. 

### <a name="beauty"></a>Belleza

El **segmento de** la comodidad lleva al usuario a un configurador GT40, que muestra el GT40 en un automóvil de rotación, de forma similar a cómo se podría mostrar un automóvil físico en un automóvil. El usuario puede aplicar diferentes opciones de rueda, elegir entre diferentes esquemas de color y abrir y cerrar las puertas y el tronco (o el arranque, como lo llaman en el Reino Unido). A lo largo de la experiencia de la naturaleza, el usuario puede recoger el automóvil y manipularlo libremente para un aspecto más cercano.

![GIF animado del configurador GT40 que se ejecuta en un dispositivo](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Rendimiento

El **segmento de** rendimiento muestra la velocidad y durabilidad de gt40. El control de voz comienza por describir cómo se desarrolló el automóvil y cómo se presentó a lo largo de sus pasos en la pista de prueba de Ford's Kingman, Arizona, con objetos visuales 3D que muestran el GT40 en movimiento en la pista de prueba. A medida que finaliza la introducción al segmento de rendimiento, la voz en off pide al usuario que "presione el botón Le Mans para alcanzar el circuito".

![GIF animado de la aplicación de durabilidad y velocidad GT40 que se ejecuta en un dispositivo](images/ford-gt40-img-06.gif)

La segunda parte del segmento de rendimiento muestra el GT40 bajo el intervalo de condiciones que los controladores pueden experimentar en las 24 horas de Le Mans, que se realiza anualmente en el Circuito de la Sarthe cerca de Le Mans, Francia. Una vista 3D muestra el automóvil en movimiento en la pista de Le Mans, con botones proporcionados para que el automóvil sea más rápido o más lento. Las imágenes del velocómetro análogo y el tachómetro del GT40 flotan sobre la vista del circuito, con más telemetría de carreras en segundo plano. El usuario puede alternar entre las vistas de día y de noche y entre condiciones de conducción sin efectos y con efectos, lo que proporciona una perspectiva realista y realista de lo que Ken Miles y los otros conductores GT40 experimentaron en la carrera real.

### <a name="engineering"></a>Engineering

El  segmento de ingeniería de la experiencia de Ford GT40 muestra una de las innovaciones de ingeniería que ayudaron a Ford a ganar la carrera: la capacidad de cambiar las ruedas y las almohadillas en menos de un minuto, en comparación con los 20-30 minutos necesarios para los demás equipos. Mediante gestos intuitivos, el usuario puede manipular un modelo 3D detallado de la rueda GT40 y el ensamblado de ruedas. Para expandir el ensamblado, el usuario toma una llave inglesa, la alinea con el bloqueo central de la rueda, lo gira en sentido contrario a las agujas del reloj y, a continuación, lo extrae de la rueda. Otros gestos se usan para quitar las ruedas y las almohadillas de los resaltes, reemplazarlas por otras nuevas, contraer el ensamblado y volver a asegurar el bloqueo central. En segundo plano, un temporizador muestra el tiempo transcurrido, lo que permite al usuario ver si puede completar el proceso tan rápidamente como la cuadrilla de boxes de Le Mans.

![GIF animado de la experiencia de ingeniería GT40 que se ejecuta en un dispositivo](images/ford-gt40-img-07.gif)

La experiencia de Ford GT40 se puede descargar de [Microsoft Store,](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)lo que permite a cualquier persona con un HoloLens 2 explorar cómo Happy Finish presentó una perspectiva nueva para el coche de carreras.

### <a name="getting-impressive-visual-fidelity"></a>Obtención de una fidelidad visual impresionante

Aunque la gama de interacciones espaciales admitidas por la experiencia ford GT40 es impresionante por sí sola, la creatividad y la fidelidad visual que ofrece la experiencia es lo que realmente hace que resalte. A través de su optimización de modelos 3D y el uso de sombreadores personalizados de Unreal, Happy Finish alcanzó su objetivo de 60 fotogramas por segundo, incluso con el segmento de rendimiento de la aplicación que se aproxima a 315 000 polígonos de tamaño. 

"Estoy muy satisfecho con cómo pudimos reunir un conjunto de interacciones fluidas e intuitivas en una narración coherente y atractiva", afirma Lambert. "Claramente, la potencia de Unreal Engine en HoloLens 2 abre un nuevo mundo de oportunidades para experiencias de realidad mixta más sorprendentes y emocionantes. La fidelidad visual sin compromiso no siempre es el objetivo final de las aplicaciones empresariales en HoloLens 2, pero cuando es así, la compatibilidad con Unreal en HoloLens 2 resulta muy valiosa".

### <a name="rapid-solution-delivery"></a>Entrega rápida de soluciones

Tan impresionante como la experiencia de Ford GT40 del usuario final es la rapidez con la que happy finish la entregó, con todo el proyecto (desde la preproducción hasta la entrega final) completado en poco menos de 12 semanas. En resumen, el proyecto consumió 1088 horas de esfuerzo, desglosadas de la siguiente manera: director creativo (80 horas), diseñador de UX (56 horas), diseñador de IU (40 horas), diseñador de sonido (40 horas), 3D/intérprete técnico (328 horas), desarrollador de software (408 horas), director técnico (40 horas), productor (56 horas) y control de calidad (40 horas).

"En general, nos acercamos bastante a nuestras estimaciones originales del proyecto", afirma Daniel Cháetham, director de innovación de Happy Finish, que dirige la división interactiva de la empresa. "La experiencia de Ford GT40 es una prueba de que una aplicación de HoloLens 2 de alta fidelidad se puede completar en tan solo unos meses, con un presupuesto moderado, pero todavía ofrece resultados muy impactantes". 

Desde una perspectiva de desarrollo, en función de su experiencia anterior con Unreal en HoloLens 2, Mill calcula que MRTK para Unreal ha recortado a la mitad el tiempo total y el esfuerzo necesario por su parte. También observa cómo MRTK puede ayudar a los desarrolladores que nunca han trabajado con HoloLens 2 empezar a trabajar. "Cuando otros desarrolladores digan que están interesados en la realidad mixta, les animo a que se den un salto, instalen la pila de desarrollo de HoloLens 2 y MRTK y vayan por ella. MRTK hace que la creación de una aplicación sea rápida y sencilla, y el editor visual de Unreal funciona tan bien que ni siquiera necesita un dispositivo HoloLens 2 para empezar. No es complicado en absoluto, todo funciona".

### <a name="potential-azure-service-enhancements"></a>Posibles mejoras del servicio de Azure

Lambert ve varias maneras en que los servicios de realidad mixta de Azure podrían usarse para mejorar la experiencia de Ford GT40, como el uso de Azure Spatial Anchors para ofrecer una experiencia de varios usuarios anclada en el mundo real. "Desde una perspectiva creadora, Azure Spatial Anchors abre una gama completamente nueva de posibilidades a través de la capacidad que proporcionan para asignar, conservar y restaurar contenido 3D o puntos de interés dentro de nuestro mundo físico", afirma.

Lambert también prevé cómo se puede usar Azure Remote Rendering o streaming de la aplicación desde Azure para lograr las velocidades de fotogramas deseadas mientras se trabaja con modelos 3D más detallados y complejos. "Hemos tenido que implementar algunos sombreadores personalizados altamente optimizados en Unreal para alcanzar nuestro objetivo en el dispositivo de 60 fotogramas por segundo", explica. "Con Azure Remote Rendering, podríamos hacer muchas más cosas, y hacerlo mucho más fácilmente, sin tanto trabajo necesario para optimizar modelos de polígono, volver a dibujar mapas de textura, etc.".

### <a name="endless-new-possibilities"></a>Nuevas posibilidades infinitas

¿Qué sigue para Happy Finish? Los comentarios de Ford sobre la experiencia de Ford GT40 han sido abrumadoramente positivos, lo que ha dado lugar a más discusiones entre Happy Finish y Ford sobre futuros proyectos HoloLens 2 desarrollo. Fuera de su relación con Ford, Happy Finish ya está iniciando un nuevo proyecto en HoloLens 2, donde MRTK para Unreal será un bloque de creación fundamental para la mayor parte de la experiencia del usuario. 

"Siempre hemos mantenido un enfoque independiente de la tecnología para cada nuevo proyecto, proponiendo el conjunto de herramientas más adecuado para ayudar al cliente a lograr los resultados deseados", afirma Cheetham. "Dicho esto, HoloLens 2 ha surgido como el estándar de oro de facto para la realidad mixta, especialmente en la empresa, con la cabeza y la altura sobre todas las demás opciones en términos de funcionalidades de dispositivo y la generalización del ecosistema de apoyo".

Según Cheetham, la pandemia global ha impulsado un gran interés en la realidad mixta inmersiva entre los clientes potenciales. "Estamos más ocupados que nunca, con aproximadamente el 50 por ciento de los clientes potenciales abiertos a analizar una opción de realidad mixta", afirma. "La clave es que los usuarios lo prueben. Puede contarles sobre la realidad mixta todo el día, pero cuando les entrega un HoloLens 2 para experimentar por sí mismos, obtienen inmediatamente cómo puede ser un cambio de juego. La compatibilidad con Unreal Engine en HoloLens 2 solo aumenta el valor que podemos ofrecer, lo que nos permite ofrecer experiencias visualmente sorprendentes que están seguras de satisfacer incluso a los clientes más exigentes".

## <a name="try-it-out"></a>Haga la prueba

> [!div class="nextstepaction"]
> [Descarga de la aplicación Ford GT40](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Consulte nuestra introducción [al desarrollo Mixed Reality en HoloLens 2](../development.md) [o MRTK para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) en GitHub.

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->