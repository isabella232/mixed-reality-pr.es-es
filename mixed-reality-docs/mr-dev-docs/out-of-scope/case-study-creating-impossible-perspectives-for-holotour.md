---
title: 'Caso práctico: Creación de perspectivas imposibles para HoloTour'
description: Queríamos que sus experiencias en HoloTour Microsoft HoloLens sean más agradables. Además de las paradas tradicionales, hemos planeado algunas "perspectivas imposibles".
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: bf1f2b3c9c82e4b649a75efc0275a063ea5a2363dfa15b818c0159b947f6b515
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199954"
---
# <a name="case-study---creating-impossible-perspectives-for-holotour"></a>Caso práctico: Creación de perspectivas imposibles para HoloTour

Queríamos que sus experiencias en HoloTour Microsoft HoloLens sean más agradables. Además de las tradicionales paradas, hemos planeado algunas "perspectivas imposibles", momentos que serían imposibles de experimentar en cualquier paseo, pero que, a través de la tecnología de HoloLens, podríamos traer directamente a su sala. La creación del contenido para estas experiencias requería algunas técnicas diferentes a nuestro proceso de captura estándar.

## <a name="the-content-challenge"></a>El desafío de contenido

Hay ciertas escenas en la experiencia HoloTour, como el paseo en globo de aire caliente sobre la Moderna Ciudad de La Rome y la noche de la noche en el Coloso de la Antigua Rome, que proporcionan vistas únicas que no verá en ningún otro lugar. Estos momentos están pensados para que le enoja y le enoja, lo que hace que su viaje a través de HoloTour sea algo más que una experiencia educativa. Son los momentos que queremos que recuerde y nos complace contarle a otras personas. Dado que no hemos podido subir la plataforma de la cámara al cielo y no hemos (todavía) maestro el viaje en el tiempo, cada una de estas "perspectivas imposibles" ha llamado a un enfoque especial para crear contenido.

## <a name="behind-the-scenes"></a>Entre bambalinas

La creación de estos momentos y perspectivas únicos requiere algo más que simplemente grabar y editar. Se tardó una gran cantidad de tiempo, personas con muchas aptitudes diferentes y un poco de Magia mágica.

### <a name="viewing-rome-from-a-hot-air-balloon"></a>Visualización de Rome desde un globo de aire caliente

Desde nuestros primeros días de planeamiento, sabíamos que queríamos hacer vistas aéreas en HoloTour. Ver Rome desde el cielo ofrece una perspectiva que la mayoría de las personas nunca pueden ver y una idea de cómo se ubican espacialmente los puntos de referencia populares. Intentar capturar esto con la cámara y la plataforma de micrófono existentes habría sido enormemente difícil, pero afortunadamente no tuvimos que hacerlo.

En primer lugar, es importante explicar que todas las ubicaciones que visita en HoloTour tienen movimiento en ellas. Nuestro objetivo era hacer que "se sienta realmente allí" y, dado que está rodeado por el movimiento en cualquier lugar de la vida real, nuestros destinos virtuales también necesitaban transmitir el movimiento ambiente. Por ejemplo, cuando visite pantheon en su viaje, verá a personas paseando por la calles y recorriendo los pasos. El movimiento en segundo plano le ayuda a sentir que realmente se encuentra en la ubicación, en lugar de en un entorno estático y con almacenamiento por fases.

Para crear las vistas aéreas para la carrera en globo, trabajamos con otros equipos de Microsoft para obtener acceso a imágenes aéreas de La Rome. La calidad de estas imágenes era excelente y la vista era impresionante, pero cuando se usaban en escenas sin modificaciones, se sincronían sin vida en comparación con las otras partes del paseo y la falta de movimiento distraía. 


![La cesta de globos de aire caliente, flotante sobre Rome.](images/hotairballoon1-300px.png)<br>
*La cesta de globos de aire caliente, flotante sobre Rome*

Para asegurarse de que las ubicaciones aéreas cumplen la misma barra de calidad que otros destinos, decidimos transformar las fotografías estáticas en escenas en vivo y en movimiento. El primer paso fue editar la imagen y el movimiento compuesto en ella. Contratamos a un intérprete de efectos visuales para ayudarnos con esto. La edición se ha realizado para mostrar nubes que se desván lentamente, vuelos de los animales y un plano ocasional o un vuelo que atraviesa el árbol. En el suelo, se han realizado varios automóviles para conducir por las calles. Si ha estado de paseo por Rome en Holo Tour, es poco probable que conozca explícitamente cualquiera de estos movimientos. Eso es realmente excelente. El movimiento sutil no está pensado para ponerse de acuerdo, pero sin estos pequeños toques, los usuarios observaron inmediatamente que se trataba de una imagen estática en la escena.

Lo segundo que hicimos fue darle un punto de vista desde el que ver la escena. No tendrá la sensación de que realmente está allí si parece que simplemente está flotando en el aire, por lo que creamos un modelo 3D de un globo y te colocamos dentro de él. Esto le permite recorrer el globo y mirar sobre el borde para obtener un mejor punto de vista. Hemos descubierto que se trata de una manera natural y divertida de experimentar las imágenes aéreas.

La experiencia de globo de aire caliente presentaba desafíos únicos para nuestro equipo de audio, ya que la logística nos impedía tener micrófonos que se desplazaban miles de pies sobre Rome. Afortunadamente, tuvimos una gran cantidad de captura de audio ambiente de toda la ciudad que pudimos usar durante la postproducción. Colocamos emisores de audio en sus ubicaciones relativas desde donde se capturaron desde el suelo. A continuación, el audio se filtró para parecer lejano, como si lo escuchara desde la perspectiva de alguien paseando por el globo de aire caliente, proporcionando un sonido auténtico y direccional para la escena.

### <a name="time-traveling-to-ancient-rome"></a>Hora de viaje a La Rome

Los restos de edificios y edificios de La Rome son impresionantes incluso dos mil años después de su construcción, pero sabíamos que teníamos una oportunidad única de mostrarle lo que sería volver atrás en el tiempo y ver estas estructuras tal y como aparecían en la antigua Rome.

Por supuesto, no hay ninguna secuencia de vídeo ni imágenes estáticas) del coloso tal y como aparecía cuando se creó, por lo que es necesario crear las nuestras. Hemos tenido que realizar muchas investigaciones para aprender tanto sobre la estructura como podríamos. comprender los materiales de los que se hizo, revisar diagramas arquitectónicos y leer descripciones históricas para obtener información suficiente para poder realizar una recreación virtual. 

![Las modernas lotas del coloso con una superposición que muestra el suelo de la pista tal y como se habría visto en la Antigua Rome.](images/rome-colosseum-overlay-500px.png)<br>
*Las lotas modernas del coloso con una superposición que muestra el suelo de la pista tal y como se habría visto en la Antigua Rome.*

Lo primero que queríamos hacer era mejorar las giras tradicionales con superposiciones educativas. En HoloTour, cuando visita los terrenos del Coloso tal y como están hoy, el suelo del campo se transforma para mostrar cómo se habría visto durante el uso, incluidas las complejas áreas de ensayo de los campos. En un paseo normal, es posible que se le describa esta información e intentar imaginarla, pero en Holo Tour puede verla realmente.

Para una superposición como esta, nuestros intérpretes coinciden con el punto de vista de la secuencia de captura y crean la imagen de superposición a mano. La perspectiva debe coincidir para que, cuando reemplacemos el vídeo por nuestra imagen, ambos se alineen correctamente.

### <a name="staging-the-gladiator-fight"></a>Ensayo de la conmoción del mesón

Aunque las superposiciones son una manera atractiva de enseñar a los usuarios sobre la historia, lo que más nos emocionó fue transportarlo en el tiempo. La superposición era simplemente una imagen fija desde un punto de vista determinado, pero el tiempo de desplazamiento requeriría que se modelase todo el coloso y, como se ha descrito anteriormente, era necesario tener movimiento en la escena para que se sinuosase. Lograr eso tardó una cantidad considerable de esfuerzo.

Esta empresa era demasiado grande para que nuestro equipo lo realizara por sí solo, por lo que nuestro equipo de arte colaboró conTree, una empresa de efectos externos que normalmente trabaja en efectos visuales para películas de Varía. Tree nos ha ayudado a volver a crear el coloso en su día, lo que nos ha permitido enseñarnos sobre la estructura mientras nos encontrabamos en el suelo del campo y crear una vista de un desenfrenado desenfrenado desde la caja del hombre. Las aglomeraciones y las pancartas ondeando agregan el movimiento sutil necesario para que se sienta como si se tratase de lugares reales y no solo imágenes.

![El coloso recreado tal y como se ve desde el suelo del campo. Cuando se ven en HoloTour, los banners oneran a simple vista, lo que da una sensación de movimiento.](images/recreated-colosseum-holotour-500px.png)<br>
*El coloso recreado tal y como se ve desde el suelo del campo. Cuando se ven en HoloTour, los banners oneran a simple vista, lo que da una sensación de movimiento.*

El paseo por Rome se reentornó con el desenlazador. Tree nos proporcionó las simulaciones de audiencia y de público en 3D que se representan como vídeo, pero era necesario agregar los meses en el suelo del campo. Esta parte de nuestro proceso se parece más a una producción de vídeo de Verón que a un proyecto de un estudio de juegos de cocina. Los miembros de nuestro equipo asignaron una secuencia de acción aproximada y, a continuación, la refinaron con un coreógrafo. Contratamos actores para que esceniesemos nuestra guerra simulada y adquirimos la protección para que se buscara el papel. Por último, hemos proyectado toda la escena en una pantalla verde.

![Nuestros meladores, obtención de instrucciones entre toma.](images/green-screen-gladiators-holotour-500px.jpg)<br>
*Nuestros meladores, obtener instrucciones entre toma*

Esta escena le coloca en el cuadro del indiósco, lo que significaba que todas las imágenes de vídeo deban estar desde esa perspectiva. Si se grabara desde donde los animadores estaban en la pista, no habríamos podido componer correctamente la secuencia de la marcha más adelante, por lo que colocamos nuestro operador de cámara en una elevación de altura muy alta, mirando hacia abajo la secuencia de la secuencia de la película.

![Obtención de la perspectiva correcta: la película desde un lift-lift de la loda.](images/scissor-lift-holotour-500px.jpg)<br>
*Obtención de la perspectiva correcta: la película desde un lift-lift de las manos*

En la posproducción, los meladores se componían en el suelo de la pista y la perspectiva era correcta, pero hubo un problema: las sombras de los meladores en la pantalla verde se quitaron como parte del proceso de composición. Sin sombras, era como si los meladores estuvieran flotando en el aire. Afortunadamente,Certtree es excelente para resolver solo este tipo de problema y han usado un poco de asistente técnico para agregar sombras de nuevo a nuestra escena. El resultado es lo que se ve hoy en el paseo.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley es</b> un desarrollador sénior que ha aprendido más sobre los equipos de cámara y la reproducción de vídeo de lo que consideró posible al trabajar en HoloTour.</td>

<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> es un diseñador de audio que se aseguró de que podría experimentar el sonido de cada destino que visite, incluso cuando vuelva en el tiempo.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Daniel Askew es</b> un actor de vídeo que se aseguró de que el recorrido por Rome fuera lo más difícil posible.</td>

<td style="border:0" width="60px"></td>
<td style="border:0" width="408"></td>
</tr>
</table>


## <a name="see-also"></a>Consulte también
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
