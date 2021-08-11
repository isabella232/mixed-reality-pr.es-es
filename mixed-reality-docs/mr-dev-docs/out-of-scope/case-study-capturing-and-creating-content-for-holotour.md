---
title: 'Caso práctico: HoloTour'
description: Explore el caso práctico de la aplicación HoloTour y explore el proceso de captura y creación de su contenido.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: 7e9bc2078e90b0f0cd98cf0612b583c06b2d51b400d682d3aff71e59eed620a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202248"
---
# <a name="case-study---holotour"></a>Caso práctico: HoloTour

HoloTour para Microsoft HoloLens proporciona paseos personales 3D inmersivos de ubicaciones icono de todo el mundo. Como averiguaron los diseñadores, creadores, productores, diseñadores de audio y desarrolladores que trabajan en este proyecto, la creación de una representación en 3D realmente real de una ubicación conocida toma una combinación única de asistentes creativos y tecnológicos. Este caso práctico le ayudará a capturar y crear el contenido usado para HoloTour.

## <a name="the-tech"></a>La tecnología

Con HoloTour, queríamos hacer posible que los usuarios visitaran algunos de los destinos más sorprendentes del mundo, como los lugares donde se encuentra la familia Den Visit o la moderna [Ciudad DeÓn en](https://en.wikipedia.org/wiki/Piazza_Navona) Italia, directamente desde sus [propias](https://en.wikipedia.org/wiki/Machu_Picchu) salas de estar. Nuestro equipo se ha hecho el objetivo de HoloTour para "hacer que se sienta como si realmente está allí". La experiencia tenía que ser algo más que imágenes o vídeos. Al aprovechar la pantalla, el seguimiento y la tecnología de audio únicas de HoloLens creemos que podríamos transportarlo virtualmente a otro lugar. Tendríamos que capturar el ambiente, los sonidos y la geometría tridimensional de cada ubicación que visitamos y, a continuación, volver a crearlo dentro de nuestra aplicación.

Para ello, necesitamos un equipo de cámara de 360° con captura de audio direccional. Era necesario capturar a una resolución extremadamente alta, de modo que la secuencia se mostrase precisa cuando se reproduce en un HoloLens y las cámaras deban colocarse juntas para minimizar los artefactos de unión. Queríamos una cobertura esférica completa, no solo a lo largo del horizonte, sino también por encima y debajo de usted. El equipo también tenía que ser portátil para poder llevarlo a todo el mundo. Hemos evaluado las opciones disponibles y nos dimos cuenta de que simplemente no eran lo suficientemente buenas como para realizar nuestra visión, ya sea debido a la resolución, el costo o el tamaño. Si no encontramos un equipo de cámara que satisface nuestras necesidades, tendríamos que crear uno nosotros mismos.

### <a name="building-the-rig"></a>Creación de la plataforma

La primera versión,realizada a partir de la televisión, Velcro, cinta de cinta y 14 cámaras GoPro, era algo de lo que MacGyver habría sido muy bueno. Después de revisar todo, desde soluciones de gama baja hasta equipos fabricados a medida, las cámaras GoPro eran en última instancia la mejor opción para nosotros porque eran pequeñas, asequibles y tenían almacenamiento de memoria fácil de usar. El factor de forma pequeño era especialmente importante porque nos permitía colocar cámaras bastante cerca juntas: cuanto menor sea la distancia entre las cámaras, más pequeños serán los artefactos de unión. Nuestra disposición de cámara única nos  permitió obtener cobertura de esfera completa más suficiente superposición para alinear las cámaras de forma inteligente y suavizar algunos artefactos durante el proceso de unión.

Aprovechar las funcionalidades de [sonido espacial](../design/spatial-sound.md) en HoloLens es fundamental para crear una experiencia inmersiva realmente real. Hemos usado una matriz de cuatro micrófonos situada debajo de las cámaras del tripode, que capturaría el sonido de la ubicación de la cámara en cuatro direcciones, lo que nos proporciona suficiente información para crear sonidos espaciales en nuestras escenas.

![Nuestra plataforma de cámara de 360° configurada para la película fuera del Pantheon.](images/camera-pantheon-200px.png)

Nuestra plataforma de cámara de 360° configurada para la película fuera del Pantheon. 


Hemos probado nuestro equipo de fabricación propia, para lo que lo llevamos a Rattlesnake Ridge, cerca de Seattle, capturando el ambiente en la parte superior de la montaña. El resultado, aunque significativamente menos brillante que las ubicaciones que se ven en HoloTour hoy en día, nos dio la confianza de que nuestro diseño de plataforma era lo suficientemente bueno como para que se sienta realmente allí.

Hemos actualizado nuestro equipo de Velcro y de una caja de cámara impresa en 3D y hemos comprado paquetes de batería externos para las cámaras GoPro con el fin de simplificar la administración de la batería. A continuación, hemos hecho una prueba más exhaustiva y viajamos a San Francisco para crear un paseo por la costa de la ciudad y el icono puente de Golden Gate. Este equipo de cámara es lo que hemos usado para la mayoría de nuestras capturas de las ubicaciones que visita en HoloTour.

![La cinta de cámara de 360° que se rodó en Radar Booking.](images/camera-machu-pichu-500px.png)

La cinta de cámara de 360° que se rodó en Radar Booking. 

## <a name="behind-the-scenes"></a>Entre bambalinas

Antes de la película, era necesario averiguar qué ubicaciones queríamos incluir en nuestro paseo virtual. Rome fue la primera ubicación que queríamos enviar y queríamos hacerlo bien, por lo que decidimos realizar un recorrido de exploración de antemano. Hemos enviado un equipo de seis personas(incluidos los creadores, diseñadores y productores) para una visita en persona a los sitios que se estaban considerando. El viaje tardó aproximadamente de 9 días a 2,5 para el viaje y el resto para la película. (En el caso de Noé, optamos por no realizar un viaje de explorador, investigar de antemano y reservar unos días de búfer para la película).

Mientras se encuentra en Rome, el equipo tomó fotos de cada área y anotó hechos interesantes, así como consideraciones prácticas, como lo difícil que sería viajar a cada lugar y lo difícil que sería viajar debido a las aficiones o restricciones. Esto puede parecer unas vacaciones, pero es mucho trabajo. Los días se iniciaron a primera hora de la mañana y no se detendría hasta la noche. Cada noche, se cargaba material para que el equipo lo revisara en Seattle. 

![Nuestro equipo de captura en Rome.](images/holotour-filming-crew-rome-500px.jpg) 

Nuestro equipo de captura en Rome. 


Una vez completado el recorrido de exploración, se realizó un plan final para la película real. Esto requería una lista detallada de dónde ir al cine, en qué día y a qué hora. Cada día, los gastos son caros, por lo que estos viajes deben ser eficaces. Hemos reservado guías y controladores en Rome para ayudarnos y usarnos por completo todos los días desde antes del sol hasta después de la puesta de sol. Necesitamos obtener la mejor secuencia posible para que se sienta como si realmente está allí.

### <a name="capturing-the-video"></a>Captura del vídeo

Hacer algunas cosas sencillas durante la captura puede facilitar mucho el procesamiento posterior. Por ejemplo, cada vez que une imágenes de varias cámaras, terminará con artefactos visuales porque cada cámara tiene una vista ligeramente diferente. Cuanto más cercanos estén los objetos a la cámara, mayor será la diferencia entre las vistas y más grandes serán los artefactos de unión. Esta es una manera fácil de visualizar el problema: mantener el dedo en la parte delantera de la cara y mirarlo con un solo ojo. Ahora, cambie los ojos. Verá que el control de posición parece moverse en relación con el fondo. Si mantiene el dedo más lejos de la cara y repite el experimento, parecerá que se mueve menos. Ese movimiento aparente es similar al problema de unión al que nos enfrentamos: los ojos, como nuestras cámaras, no ven exactamente la misma imagen porque están separados por una distancia pequeña.

Dado que es mucho más fácil evitar los peores artefactos durante la película que corregirlos en el procesamiento posterior, intentamos mantener a las personas y las cosas lejos de la cámara con la esperanza de que podamos eliminar la necesidad de unir los objetos de primer nivel. El mantenimiento de una gran limpieza alrededor de la cámara probablemente fue uno de los mayores desafíos que teníamos durante el vídeo y tuvimos que ser creativos para que funcionara. Trabajar con guías locales fue una gran ayuda para administrar las aglomeraciones, pero también encontramos que el uso de signos (y, a veces, pequeños conos o bolsas de haba) para marcar nuestro espacio de grabación fue razonablemente eficaz, especialmente porque solo necesitamos obtener una breve cantidad de material en cada ubicación. A menudo, la mejor manera de obtener una buena captura era llegar solo a primera hora de la mañana, antes de que se presentara la mayoría de las personas.

Otras técnicas de captura útiles proceden directamente de las prácticas tradicionales del cine. Por ejemplo, hemos usado una tarjeta de corrección de color en todas nuestras cámaras y hemos capturado fotos de referencia de texturas y objetos que podríamos necesitar más adelante. 

![Un corte aproximado de La Dula que muestra la tarjeta de corrección de color.](images/rough-cut-machu-picchu-500px.png)

Un corte aproximado de material de Pantheon antes de la unión.

### <a name="processing-the-video"></a>Procesamiento del vídeo

La captura de contenido de 360° es solo el primer paso: se necesita mucho procesamiento para convertir la secuencia de la cámara sin procesar que capturamos en los recursos finales que se ven en HoloTour. Una vez que regresamos a casa, necesitamos tomar el vídeo de 14 fuentes de cámara diferentes y convertirlo en un único vídeo continuo con artefactos mínimos. Nuestro equipo de arte usó una serie de herramientas para combinar y pulir la secuencia capturada y desarrollamos una canalización para optimizar el procesamiento tanto como sea posible. La secuencia se tenía que unir, corregir el color y, a continuación, componer para quitar elementos y artefactos que distraían, o para agregar unos bolsas complementarios de vida y movimiento, todo ello con el objetivo de mejorar esa sensación de estar allí.

![Un corte aproximado de material de Pantheon antes de la unión.](images/rough-cut-pantheon-500px.png)

Un corte aproximado de material de Pantheon antes de la unión. 


Para unir los vídeos, hemos usado una herramienta denominada [PTGui](https://www.ptgui.com/) y la hemos integrado en nuestra canalización de procesamiento. Como parte del procesamiento posterior, extrajemos fotogramas de nuestros vídeos y encontramos un patrón de unión que era bueno para uno de esos fotogramas. A continuación, aplicamos ese patrón a un complemento personalizado que escribimos que permitía a nuestros intérpretes de vídeo ajustar y ajustar el patrón de unión directamente mientras componía en After Effects. 

![Captura de pantalla de PTGui que muestra la secuencia de Pantheon unida.](images/stitching-tool-pantheon-500px.png)

Captura de pantalla de PTGui que muestra la secuencia de Pantheon unida. 


### <a name="video-playback"></a>Reproducción de vídeo

Una vez completado el procesamiento de la secuencia, tenemos un vídeo sin problemas, pero es muy grande, alrededor de 8 000 de resolución. La decodificación de vídeo es costosa y hay muy pocos equipos que puedan controlar un vídeo de 8 K, por lo que el siguiente desafío era encontrar una manera de reproducir este vídeo en HoloLens. Hemos desarrollado una serie de estrategias para evitar el costo de la descodización y, al mismo tiempo, hacer que el usuario se sienta como si estuviera viendo todo el vídeo.

La optimización más sencilla es evitar la decodificación de partes del vídeo que no cambian mucho. Hemos escrito una herramienta para identificar las áreas de cada escena que tienen poco o ningún movimiento. Para esas regiones, mostramos una imagen estática en lugar de decodificar un vídeo en cada fotograma. Para que esto sea posible, dividimos el vídeo masivo en fragmentos mucho más pequeños.

También nos aseguramos de que cada píxel que descodificamos se usara de la manera más eficaz. Hemos experimentado con técnicas de compresión para reducir el tamaño del vídeo. dividimos las regiones de vídeo según los polígonos de la geometría en la que se proyectaría. hemos ajustado los UV y hemos reempaquetado los vídeos en función de la cantidad de detalle que incluyen los distintos polígonos. El resultado de este trabajo es que lo que empezó como un solo vídeo de 8 k se convirtió en muchos fragmentos que parecen casi ininteligibles hasta que se proyectan correctamente en la escena. Para un desarrollador de juegos que comprende la asignación de texturas y el empaquetado uv, probablemente le será familiar. 

![Una vista completa del Pantheon antes de las optimizaciones.](images/pantheon-before-optimization-500px.png) 

Una vista completa del Pantheon antes de las optimizaciones. 


![La mitad derecha del Pantheon, procesada para la reproducción de vídeo.](images/pantheon-process-video-playback-500px.png) 

La mitad derecha del Pantheon, procesada para la reproducción de vídeo. 


![Ejemplo de una sola región de vídeo después de la optimización y el empaquetado.](images/single-video-region-after-optimization-500px.png) 

Ejemplo de una sola región de vídeo después de la optimización y el empaquetado. 


Otro truco que hemos usado fue evitar la decodificación de vídeo que no está viendo activamente. Mientras se encuentra en HoloTour, solo puede ver parte de la escena completa en un momento dado. Solo descodificamos vídeos dentro o poco fuera de su campo de vista (FOV). A medida que gira la cabeza, comenzamos a reproducir las regiones del vídeo que ahora están en la fov y dejaremos de reproducir las que ya no están dentro de ella. La mayoría de las personas ni siquiera se darán cuenta de que esto sucede, pero si se da la vuelta rápidamente, verá que el vídeo tarda un segundo en iniciarse; mientras tanto, verá una imagen estática que, a continuación, se atenua al vídeo una vez que esté listo.

Para que esta estrategia funcione, hemos desarrollado un amplio sistema de reproducción de vídeo. Hemos optimizado el código de reproducción de bajo nivel para que el cambio de vídeo sea muy eficaz. Además, hemos tenido que codificar nuestros vídeos de una manera especial para que sea posible cambiar rápidamente a cualquier vídeo en cualquier momento. Esta canalización de reproducción tardó una cantidad significativa de tiempo de desarrollo, por lo que la implementamos en fases. Comenzamos con un sistema más sencillo que era menos eficaz, pero que permitía a diseñadores y creadores trabajar en la experiencia, y lo mejoramos lentamente a un sistema de reproducción más sólido que nos permitía enviar en la barra de calidad final. Este sistema final tenía herramientas personalizadas que creamos en Unity para configurar el vídeo dentro de la escena y supervisar el motor de reproducción.

### <a name="recreating-near-space-objects-in-3d"></a>Volver a crear objetos de espacio próximo en 3D

Los vídeos son la mayor parte de lo que se ve en HoloTour, pero hay una serie de objetos 3D que aparecen cerca de usted, como el cuadro de La Familia, el frío fuera del Panteón o el globo de aire caliente en el que se encuentran las escenas aéreas. Estos objetos 3D son importantes porque la percepción de profundidad humana es muy buena de cerca, pero no muy buena lejos. Podemos salir con el vídeo a distancia, pero para permitir a los usuarios recorrer su espacio y sentir que realmente están allí, los objetos cercanos necesitan profundidad. Esta técnica es similar al tipo de cosas que puede ver en un patrimonio de historia natural: imagine un dioramóma que tiene plantas físicas, plantas y animales en primer plano, pero retrocede en un dibujo de flores enmascarada inteligentemente en segundo plano.

Algunos objetos son simplemente recursos 3D que creamos y agregamos a la escena para mejorar la experiencia. El cuadro y el globo de aire caliente se incluyen en esta categoría porque no estaban presentes cuando se rodó. De forma similar a los recursos del juego, los creó un intérprete en 3D de nuestro equipo y se texturaron correctamente. Los colocamos en nuestras escenas cerca de donde se encuentra, y el motor de juego puede representarlos en las dos pantallas HoloLens para que aparezcan como un objeto 3D.

Otros recursos, como el lugar fuera del Panteón, son objetos reales que existen en las ubicaciones donde estamos grabando vídeo, pero para sacar estos objetos del vídeo y en 3D, tenemos que hacer una serie de cosas.

En primer lugar, necesitamos información adicional sobre cada objeto. Mientras estaba en la ubicación para la grabación, nuestro equipo capturó una gran cantidad de secuencias de referencia de estos objetos para que íamos suficientes imágenes detalladas para volver a crear con precisión las texturas. El equipo también [](https://en.wikipedia.org/wiki/Photogrammetry) realizó un examen de fotogrametría, que construye un modelo 3D a partir de decenas de imágenes 2D, lo que nos proporciona un modelo aproximado del objeto a escala perfecta.

A medida que procesamos la secuencia, los objetos que más adelante se reemplazarán por una representación 3D se quitan del vídeo. El recurso 3D se basa en el modelo de fotogrametría, pero lo limpian y simplifican nuestros intérpretes. Para algunos objetos, se pueden usar partes del vídeo, como la textura de agua en la zona, pero la mayor parte del cuerpo es ahora un objeto 3D, lo que permite a los usuarios percibir la profundidad y recorrerla en un espacio limitado de la experiencia. Tener objetos casi espaciales como este agrega en gran parte a la sensación de realismo y ayuda a abate a los usuarios en la ubicación virtual. 

![Material de panteón con el desenlazón quitado. Se reemplazará por un recurso 3D.](images/object-removal-pantheon-500px.png)

Material de panteón con el desenlazón quitado. Se reemplazará por un recurso 3D.


## <a name="final-thoughts"></a>Consideraciones finales

Obviamente, había más cosas para crear este contenido que lo que se ha analizado aquí. Hay algunas escenas, que nos gusta llamarlas "perspectivas imposibles", como el paseo en globo de aire caliente y el paseo por el desenfreno en el coloso, que tuvo un enfoque más creativo. Los abordaremos en un caso práctico futuro.

Esperamos que compartir soluciones a algunos de los desafíos más grandes que hemos tenido durante la producción sea útil para otros desarrolladores y que esté inspirado en usar algunas de estas técnicas para crear sus propias experiencias inmersivas para HoloLens. (Y si lo hace, asegúrese de compartirlo con nosotros en el foro HoloLens [Desarrollo de aplicaciones).](https://forums.hololens.com/)

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> es un desarrollador sénior que aprendió más sobre las plataformas de cámara y la reproducción de vídeo de lo que se le ía posible al trabajar en HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Por su parte, El</b> intérprete de vídeo Que se aseguró de que el recorrido por Rome fuera lo más difícil posible.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> es un diseñador de audio que se aseguró de que podría experimentar el sonido de cada destino que visite, incluso cuando vuelva atrás en el tiempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Antes de dirigir la</b> película en el sitio, Se trata de un director de diseño que ha investigado y explorado ubicaciones, ha creado planes de viaje y dirigido películas.</td>
</tr>
</table>



## <a name="see-also"></a>Consulte también
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
