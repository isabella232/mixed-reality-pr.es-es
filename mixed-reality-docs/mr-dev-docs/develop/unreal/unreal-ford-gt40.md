---
title: La experiencia de Ford GT40
description: Siga el tutorial de la aplicación de la realidad de Ford GT40 Mixed Reality con MRTK para HoloLens 2 en el caso de que no sea real.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, implementación en dispositivo, PC, documentación, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: ca577bdc5bc30aebf80c9888345eb0e2d5c3ce6d
ms.sourcegitcommit: cc9d90b046a9fce792058fea25ae13a9186e43e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2021
ms.locfileid: "105008930"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>La realización de la experiencia de Ford GT40

*"MRTK, el desarrollo de HoloLens 2 mediante el uso de la implementación no real era un poco tedioso, ya que todas las interacciones espaciales debían codificarse a mano en C++. La MRTK de forma no real hizo una gran cantidad de esas mismas tareas triviales. Lo calculo y redujo el tiempo necesario para el prototipo inicial en la mitad. "* -José Rodriguez, desarrollador de software

*"La experiencia de Ford GT40 es una prueba de que una aplicación de HoloLens 2 de alta fidelidad puede completarse en unos pocos meses, con un presupuesto modesto, pero aún así ofrecer resultados muy impactantes".*  -Daniel Cheetham, Director de innovación, feliz acabado

El uso del kit de herramientas de la realidad mixta (MRTK) para una empresa de producción creativa no real, con un feliz acabado, proporcionó una experiencia de HoloLens 2 que proporciona una nueva perspectiva sobre el GT40 de Ford, el coche de carreras legendarias que se ha expulsado Ferrari en las 24 horas de la Mans.

Mediante el uso de una variedad de interacciones espaciales naturales e intuitivas, los usuarios pueden explorar la belleza, el rendimiento y la ingeniería de GT40's, todo ello distribuido de una manera que aprovecha la alta fidelidad visual que proporciona el motor inreal. El desarrollo de software para todo el proyecto lo ha realizado un solo Desarrollador en menos de tres meses, lo que MRTK para el entorno de diseño y scripting visual de la realidad.

> [!div class="nextstepaction"]
> [Descarga de la aplicación Ford GT40](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

![Imagen de Ford GT40 Hero](images/ford-gt40-hero.jpg)

## <a name="the-ask"></a>El Ask

Feliz acabado es una de las principales compañías de producción creativa del mundo, con una base de cliente que incluye, Ford, Microsoft, Nike, Netflix, Vodafone y otros nombres de familia. La compañía ha dado su inicio como una agencia de retoques fotográficas de alto nivel, que se ramifica en película y CGI antes de ampliar su dedicación a la excelencia en contar historiass envolventes con diseño e interacción espaciales 3D.

En mediados de 2020, Microsoft se ha aproximado a la finalización de la creación de una aplicación de demostración que podría ayudar a exhibir las posibilidades que ofrece el nuevo kit de herramientas de realidad mixta (MRTK), que se basa en la compatibilidad con HoloLens 2 en el motor inreal. Llegados a este punto, la compañía ya tenía dos proyectos inrealmente de HoloLens 2 que se ejecutaban correctamente en su cinturón. Ambos eran para una marca de consumidor reconocida globalmente, que escogió de forma no real en HoloLens 2 para una herramienta interna de ventas R&D/B2B para su alta fidelidad visual, tal y como se requiere para mostrar mejor los productos de alto nivel de cliente.

A pesar de que la propia solución se quedaba para un acabado feliz, tenía que cumplir algunas directrices clave. En primer lugar, tenía que centrarse en un escenario empresarial para ilustrar la utilidad de no real en HoloLens 2 fuera de la industria de juegos. En segundo lugar, debía ser solo de dispositivo, lo que significa que podría servir como una demostración independiente, sin necesidad de una conexión de red y una capacidad de procesamiento externo para obtener las tarifas de fotogramas de destino y la calidad visual. En tercer lugar, debe combinar el abanico de interacciones intuitivas admitidas por el MRTK en una experiencia perfecta y natural. Por último, la solución propuesta debe presentar la fidelidad visual inherente y otras ventajas del propio motor, como las eficiencias del sombreador. 

Dadas estas directrices, un acabado feliz empezó a pensar en las posibilidades, con la idea de una experiencia de realidad mixta que usaba la interacción espacial para comunicar el patrimonio de un producto de nombre de marca y alto valor. Después de tener en cuenta una variedad de objetos que incluían relojes, cámaras, automóviles y chorros de radio privados, hemos acabado de terminar en última instancia de Ford GT40, una leyenda de automóviles que consiguieron notoriety en 1966 al derrotar Ferrari en las 24 horas de la Mans, como se muestra en 2019 Blockbuster film Ford vs. Ferrari. 

En cuanto a la obtención de la compra de Ford, un cliente de fin feliz existente, la empresa establece para ofrecer una nueva perspectiva en el icono de automoción clásico.

## <a name="the-solution"></a>La solución

El trabajo comenzó el 7 de mayo de 2020. Después de obtener los archivos de modelo de GT40, un artista en 3D dedicó tres semanas a optimizar los modelos de polígono, la asignación de UV, la repintado de mapas de textura y la condensación de los mapas en el menor número de texturas posible. Un artista técnico trabajó en paralelo para realizar pruebas comparativas de la salida del artista 3D, determinar tamaños de textura óptimos dadas las tarifas de fotogramas de destino y averiguar la mejor manera de aplicar sombreadores personalizados en estado inreal. Todo este trabajo de preproducción se realizó para optimizar la experiencia en el dispositivo.

Creative Director Alex Lambert entró en la imagen una vez finalizada la tarea de preproducción. Comenzó por ver Ford frente a Ferrari, pensando en cómo agrupar una descripción en torno a los escenarios y las interacciones. También recopiló referencias visuales para el intérprete de la interfaz de usuario, como imágenes del panel de GT40 y objetos visuales de Le Mans Racetrack, y grabaciones de audio recopiladas de GT40 en acción para el diseñador de sonido.

Con la narración definida y optimizada en los activos de preproducción, el desarrollador de software freelance José Rodriguez se ha dado de alta. Rodriguez había sido el desarrollador en los dos proyectos anteriores de HoloLens 2 no reales que se habían terminado de finalizar, antes de que se hubiera lanzado MRTK for nonreal.

El valor proporcionado por MRTK for nonreal se hizo evidente de manera temprana y ayuda a Rodriguez a ofrecer un prototipo inicial en una semana. Implementó tres escenarios únicos, uno para cada uno de los aspectos clave de la GT40 que Lambert ha identificado: su belleza, su rendimiento y su ingeniería. En cada escenario, Rodriguez usó MRTK para integrar los activos optimizados en 3D desde la fase de preproducción en un intervalo de interacciones espaciales. 

Con MRTK para no real, Rodriguez compiló cada escenario con el diseñador de la interfaz de usuario de gráficos de movimiento no real (UMG) de visual en lugar de tener que implementar todo en C++. [Herramientas de la experiencia del usuario](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)en un entorno inreal, el complemento que contiene los componentes y los bloques de creación de la experiencia del usuario en el MRTK, le dio a los [Blueprints no reales](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) para la simulación de entrada, interacciones manuales de scripts, botones que se admiten, manipulación de imágenes 3D, magnetismo de superficie, etc

"MRTK, el desarrollo de HoloLens 2 con un poco real era un poco tedioso porque todas las interacciones espaciales debían codificarse a mano, en C++", indica Rodriguez. "El MRTK para no real realizaba una gran cantidad de esas mismas tareas triviales. Lo calculo y redujo el tiempo necesario para el prototipo inicial en la mitad. "

Con un prototipo a mano, el equipo comenzó las iteraciones semanales para mejorar la experiencia. "Esto es así cuando la característica de captura de realidad mixta y el portal de dispositivos de Windows resultaron realmente útiles", recupera Lambert. "Los he usado para capturar mis opiniones de diseño, difundir mis comentarios a otras personas y colaborar en los cambios. El uso de un aislamiento como este habría sido imposible de hacer sin tales herramientas ".

![Un editor inreal de la aplicación Ford GT40 que se ejecuta con componentes de rueda dispuestos en secuencia](images/ford-gt40-img-04.JPG)

Como los cambios solicitados por Lambert, como el cambio de posición de los elementos de la interfaz de usuario o la modificación del comportamiento de un botón, Rodriguez los implementa. Aunque algunos de los cambios requieren pequeños ajustes de código, la mayoría de ellos se administraban en el diseñador visual real. "Me sorprendió la rapidez con la que puedo iterar," dice Rodriguez. "No se ha desperdiciado tiempo; Realizaría un cambio en el diseñador y, a continuación, presionaré reproducir para verlo inmediatamente en el dispositivo. El MRTK ha simplificado mi trabajo ".

Rodriguez también recupera el grado de inimpresionado por el modo en que está listo para la producción todas las herramientas de desarrollo. "Progresamos sin problemas desde el prototipo inicial hasta la producción final, sin tener que volver a implementar u optimizar cosas en el código".  

## <a name="the-final-build"></a>La compilación final

Feliz finalizó la producción de la experiencia de Ford GT40 para HoloLens 2 el 28 de julio de 2020, que ofrece una nueva perspectiva en el coche de carreras de legendarias. La experiencia comienza con una pantalla de inicio de sesión y, a continuación, guía al usuario para configurar un anclaje al captar el logotipo de Ford y colocarlo en una superficie plana como una tabla o un escritorio. 

### <a name="beauty"></a>Atractivo

El segmento de **belleza** pone al usuario en un configurador de GT40, que muestra el GT40 en un pedestal rotando, de forma similar a como se podría mostrar un coche físico en un programa de automóviles. El usuario puede aplicar distintas opciones de rueda, elegir entre diferentes combinaciones de colores y abrir y cerrar las puertas y el tronco (o arranque, ya que lo llaman en el Reino Unido). A lo largo de la experiencia de belleza, el usuario puede recoger el coche y manipularlo libremente para obtener una visión más detallada.

![GIF animado del configurador de GT40 que se ejecuta en un dispositivo](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Rendimiento

El segmento **rendimiento** muestra la velocidad y la durabilidad de GT40's. La VoiceOver comienza por la descripción de cómo se desarrolló el automóvil y se ha reunido a sus ritmos en el arrecife de Ford, Arizona demostrando los motivos, con objetos visuales 3D que muestran el GT40 en movimiento en la pista de pruebas. A medida que finaliza la introducción al segmento de rendimiento, VoiceOver solicita al usuario que "Presione el botón le Mans para golpear el Racetrack".

![GIF animado de la aplicación de velocidad y durabilidad de GT40 que se ejecuta en un dispositivo](images/ford-gt40-img-06.gif)

La segunda parte del segmento de rendimiento muestra el GT40 bajo el intervalo de condiciones que los controladores pueden experimentar en las 24 horas de Le Mans, que se mantiene anualmente en el circuito de la Sarthe cerca de Le Mans, Francia. Una vista 3D muestra el coche en movimiento en la pista le Mans, con los botones que se proporcionan para hacer que el automóvil se vuelva más rápido o más lento. Imágenes del velocímetro analógico y del tacómetro de GT40's sobre la vista de Racetrack, con más telemetría de carreras mostrada en segundo plano. El usuario puede alternar entre las vistas de día y de noche, y entre las condiciones de conducción destinadas y húmedas, lo que proporciona una perspectiva realista y realista de qué Ken millas y otros controladores de GT40 experimentaron en la carrera real.

### <a name="engineering"></a>Engineering

El segmento de **ingeniería** de la experiencia de Ford GT40 muestra una de las innovaciones de ingeniería que ayudaron a Ford ganar la carrera: la capacidad de cambiar los Rotors y los zapatas de freno en menos de un minuto, en comparación con los 20-30 minutos que necesitan todos los demás equipos. Con gestos intuitivos, el usuario puede manipular un modelo 3D detallado de la rueda de GT40 y el conjunto de frenos. Para expandir el ensamblado, el usuario selecciona una llave de Lug, la alinea con el bloqueo central de la rueda, lo convierte en sentido contrario a las agujas del reloj y, a continuación, lo extrae de la rueda. Se usan otros gestos para quitar los Rotors y zapatas de freno desgastados, reemplazarlos por otros nuevos, contraer el ensamblado y volver a proteger el bloqueo del centro. En segundo plano, un temporizador muestra el tiempo transcurrido, lo que permite al usuario ver si puede completar el proceso tan pronto como la tripulación de Pit en Le Mans.

![GIF animado de la experiencia de ingeniería de GT40 que se ejecuta en un dispositivo](images/ford-gt40-img-07.gif)

La experiencia de Ford GT40 se puede [Descargar en Microsoft Store](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab), lo que permite a cualquier persona con HoloLens 2 explorar cómo se ha acabado con una perspectiva nueva en legendarias Race Car.

### <a name="getting-impressive-visual-fidelity"></a>Obtención de una fidelidad visual impresionante

Aunque el intervalo de interacciones espaciales admitido por la experiencia de Ford GT40 es impresionante por sí mismo, la creatividad y la fidelidad visual que ofrece la experiencia es lo que lo convierte en lo realmente destacado. A través de la optimización de los modelos 3D y el uso de sombreadores personalizados no reales, el fin de alcanzar su objetivo de 60 fotogramas por segundo, incluso con el segmento de rendimiento de la aplicación que se aproxima a 315.000 polígonos de tamaño. 

"Me encantaría el modo de reunir un conjunto de interacciones intuitivas fluidas en una narrativa coherente y atractiva", comenta Lambert. "Claramente, el potencial de un motor sin real en HoloLens 2 abre un nuevo mundo de la oportunidad para experiencias de realidad mixta más sorprendentes y emocionantes. La fidelidad visual no comprometida no siempre es el objetivo final de las aplicaciones empresariales en HoloLens 2, pero cuando es, la compatibilidad con la no real en HoloLens 2 es inestimable ".

### <a name="rapid-solution-delivery"></a>Entrega rápida de soluciones

Tan impresionante como la experiencia del usuario final de Ford GT40 es la rapidez con la que se ha entregado con todo el proyecto, desde la preproducción hasta la entrega final, que se completa en menos de 12 semanas. En Resumen, el proyecto consumió 1088 horas de trabajo. se desglosa como se indica a continuación: Creative Director (80 horas), UX Designer (56 horas), diseñador de la interfaz de usuario (40 horas), Sound Designer (40 horas), el artista 3D/técnico (328 horas), desarrollador de software (408 horas), director técnico (40 horas), productor (56 horas) y control de calidad (40 horas).

"En general, nos encontramos muy cerca de las estimaciones del proyecto original", comenta Daniel Cheetham, Chief Innovation Director a feliz Finish, que pone en marcha la división interactiva de la empresa. "La experiencia de Ford GT40 es una prueba de que una aplicación de HoloLens 2 de alta fidelidad puede completarse en unos pocos meses, con un presupuesto modesto, pero aún así ofrecer resultados muy impactantes". 

Desde el punto de vista del desarrollo, en función de su experiencia anterior con la implementación de HoloLens 2, Rodriguez estima que el MRTK de forma no real reduce el tiempo total y el esfuerzo necesario en su parte a la mitad. También se indica cómo MRTK puede ayudar a los desarrolladores que nunca han trabajado con HoloLens 2 Introducción. "Cuando otros desarrolladores dicen que están interesados en la realidad mixta, les animamos a que solo salten, instalen la pila de desarrollo de HoloLens 2 y MRTK, y vaya a ella. El MRTK hace que la creación de una aplicación sea rápida y sencilla, y que el editor visual no real funcione tan bien que no sea necesario un dispositivo HoloLens 2 para comenzar. No es complicado: todo funciona.

### <a name="potential-azure-service-enhancements"></a>Posibles mejoras en el servicio de Azure

Lambert ve varias formas de usar los servicios de Azure Mixed Reality para mejorar la experiencia de Ford GT40, como el uso de delimitadores espaciales de Azure para ofrecer una experiencia multiusuario anclada en el mundo real. "Desde una perspectiva creativa, los anclajes espaciales de Azure abren una gama completamente nueva de posibilidades a través de la capacidad que proporcionan para asignar, conservar y restaurar contenido en 3D o puntos de interés en nuestro mundo físico", dice.

Lambert también explica cómo se puede usar la representación remota de Azure o el streaming de la aplicación de Azure para lograr las tasas de fotogramas deseadas mientras se trabaja con modelos 3D más detallados y complejos. "Teníamos que implementar algunos sombreadores personalizados muy optimizados en un lugar real para alcanzar nuestro destino en el dispositivo de 60 fotogramas por segundo", explicamos. "Con la representación remota de Azure, podríamos hacer mucho más y hacerlo mucho más fácilmente, sin tanto trabajo necesario para optimizar los modelos de polígono, volver a pintar los mapas de textura, etc.".

### <a name="endless-new-possibilities"></a>Nuevas posibilidades infinitas

¿Cuál es la próxima vez para feliz acabado? Los comentarios de Ford sobre la experiencia de Ford GT40 se han realizado de forma abrumadora, lo que conduce a debates adicionales entre el placer de finalizar y Ford en futuros proyectos de HoloLens 2. Fuera de su relación con Ford, un acabado feliz ya está iniciando un nuevo proyecto en HoloLens 2, donde MRTK es un bloque de creación fundamental para la mayoría de la experiencia del usuario. 

"Siempre hemos mantenido un enfoque independiente de la tecnología para cada proyecto nuevo, lo que propone la mejor opción para ayudar al cliente a obtener los resultados deseados," dice Cheetham. "Dicho esto, HoloLens 2 ha surgido como el estándar oro de facto para la realidad mixta, especialmente en la empresa, y los hombros por encima de todas las demás opciones en cuanto a las capacidades del dispositivo y la presencia del ecosistema de soporte técnico".

Según Cheetham, el Pandemic global ha impulsado enormemente un nuevo interés en la realidad mixta en combinación entre los posibles clientes. "Estamos más ocupados que nunca, con un 50 por ciento de clientes potenciales que están abiertos para analizar una opción de realidad mixta", dice. "La clave es conseguir que los usuarios la prueben. Puede indicarles la realidad mixta todo el día, pero cuando se entregan a HoloLens 2 para su experiencia, se obtiene inmediatamente cómo puede ser un jugador. La compatibilidad con el motor inreal de HoloLens 2 solo aumenta el valor que podemos ofrecer, lo que nos permite ofrecer experiencias visualmente sorprendentes que están seguros de satisfacer incluso a los clientes más exigentes ".

## <a name="try-it-out"></a>Haga la prueba

> [!div class="nextstepaction"]
> [Descarga de la aplicación Ford GT40](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Eche un vistazo [a nuestra introducción al desarrollo de realidad mixta en HoloLens 2](../development.md) o [MRTK para](https://github.com/microsoft/MixedRealityToolkit-Unreal) no ser real en github.

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