---
title: 'Caso práctico: diseño de sonido espacial para HoloTour'
description: Para crear un paseo virtual en 3D realmente envolvente para Microsoft HoloLens, los vídeos envolventes y el ambiente holográfico solo forman parte de la fórmula.
author: jsyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, sonido espacial, caso práctico, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, audio
ms.openlocfilehash: b398ea7b3ddd85db85018da1852ed0c5ae410f625ff88bdda286e750a517d260
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196469"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Caso práctico: Diseño de sonido espacial para HoloTour

Los vídeos envolventes y el ambiente holográfico solo forman parte de la fórmula para un paseo Microsoft HoloLens envolvente. En este artículo se describe cómo se usó el sonido para hacer que parezca que realmente está en cada ubicación de HoloTour.

## <a name="the-tech"></a>La tecnología

Las imágenes y escenas holográficas que se ven en HoloTour son solo una parte de una experiencia de realidad mixta reconocible. Aunque los hologramas solo aparecen delante de un [](spatial-sound.md) usuario, HoloLens proporcionar sonido espacial desde todas las direcciones, lo que proporciona una experiencia sensoral más completa.

El sonido espacial proporciona indicaciones para indicar una dirección a la que el usuario debe girar o para indicar al usuario que hay más hologramas para ver dentro de su espacio. También podemos adjuntar un sonido directamente a un holograma y actualizar continuamente la dirección y la distancia que el holograma tiene del usuario. Esta técnica hace que parezca que el sonido viene directamente de ese objeto.

Para HoloTour, queríamos aprovechar las funcionalidades de sonido espacial de HoloLens, por lo que creamos un entorno ambiente de 360 grados que se sincroniza con el vídeo para mostrar los resaltados sónicos de ubicaciones específicas.

## <a name="behind-the-scenes"></a>Entre bambalinas

Creamos experiencias de Holo Tour de dos ubicaciones diferentes: Rome y Rome Holo. Para que estos paseos parezcan auténticos y atractivos, queríamos capturar audio de las ubicaciones donde grabamos en lugar de usar sonidos genéricos.

### <a name="capturing-the-audio"></a>Captura del audio

En nuestro [caso práctico sobre la captura del contenido visual para HoloTour,](../out-of-scope/case-study-capturing-and-creating-content-for-holotour.md)hablaremos sobre el diseño de nuestro equipo de cámara. Constaba de 14 cámaras GoPro en una caja impresa en 3D diseñada para ajustarse al tripode. Para capturar audio, agregamos una matriz de cuatro micrófonos debajo de las cámaras. El sonido se alimenta en una unidad de grabación compacta de cuatro canales en la base del tripode. Elegimos micrófonos que estaban bien, pero que eran lo suficientemente pequeños como para evitar interferir con las cámaras.

![Cámara y micrófono personalizados](images/camera-rig-microphones-300px.png)<br>
*Cámara personalizada y plataforma de micrófono*

Esta configuración captura el sonido en cuatro direcciones. Grabamos suficiente información para volver a crear un panorama de sonido espacial en 3D que más adelante podríamos sincronizar con el vídeo de 360 grados.

Un desafío del audio de la matriz de cámaras es que está a la altura de los sonidos fuera de la cámara, como las sirenes, los aviones o los vientos elevados. Para asegurarnos de que teníamos todos los elementos de sonido que necesitamos, hemos usado grabadoras móviles estéreo y mono para capturar el sonido ambiental asincrónico en puntos de interés específicos de cada ubicación. Estas grabaciones dan al diseñador de sonido contenido limpio para agregar interés y mejorar la direccionalidad en la postproducción.

Cada día de captura genera muchos archivos. Por lo tanto, era importante desarrollar un sistema para realizar un seguimiento de los archivos que se corresponden con una ubicación determinada o una toma de cámara. Nuestra unidad de grabación se ha configurado para dar nombre automáticamente a los archivos por fecha y número "take". Hemos creado una copia de seguridad de los archivos en unidades externas al final de cada día. También hemos descubierto que es importante parar verbalmente el principio de las grabaciones de audio. Esta precaución permite una identificación contextual sencilla del contenido en caso de que se produzcan problemas de nombre de archivo. También era importante realizar una pizarra visual de la captura del equipo de cámara, ya que el vídeo y el audio se grababan como medios independientes y tenían que sincronizarse durante la fase de postproducción.

### <a name="editing-the-audio"></a>Edición del audio

De vuelta en el estudio después del viaje de captura, el primer paso para ensamblar una experiencia de sonido direccional y envolvente es revisar todo el audio capturado para una ubicación. Seleccionamos las mejores toma e identificamos los aspectos destacados que se pueden aplicar durante la integración. A continuación, se edita y limpia el audio. Por ejemplo, un sonido de radio de coche que dura un segundo y se repite varias veces podría reemplazarse por audio ambiental más silencioso de la misma sesión de captura.

Una vez establecida la edición de vídeo para una ubicación, el diseñador de sonido puede sincronizar el audio correspondiente. En este punto, se evalúan las capturas de sonido móvil y de cámara para decidir qué elementos crearían la mejor escena de audio inmersiva. Nos ha resultado útil colocar todos los elementos de sonido en un editor de audio y crear simulaciones lineales rápidas para experimentar con diferentes ideas de mezcla. Este paso nos proporcionó ideas mejor formadas para cuando llegó el momento de crear las escenas reales de HoloTour.

### <a name="assembling-the-scene"></a>Ensamblar la escena

El primer paso para crear una escena ambiental en 3D es crear un fondo con sonidos de bucle ambiente generales que admitirán otras características y elementos de sonido interactivos en una escena. Tomamos un enfoque holístico para la implementación según lo determinado por los criterios de diseño de cualquier escena determinada. Algunas escenas pueden indexar hacia el uso de la captura de cámara sincronizada. Los momentos más "méticos" pueden requerir un enfoque seleccionado que se base en sonidos colocados discretamente, elementos interactivos y música.

Al indexar en el audio de captura de cámara, colocamos emisores de audio ambiente habilitados para sonido espacial que se correspondían con la orientación direccional de las cámaras. La vista de la cámara norte reproduce audio del micrófono norte y del mismo modo para las otras direcciones cardinales. Estos emisores están bloqueados por el mundo, lo que significa que el sonido cambia cuando los usuarios se voltan la cabeza. Esta técnica modela de forma eficaz el sonido de estar en esa ubicación. Escuche a Telón Ángulo o The Pantheon para ver ejemplos de escenas que usan una buena combinación de audio capturado por la cámara.

En un enfoque diferente, a veces se reproducen sonidos estéreo en bucle con emisores de sonido espaciales que se colocan alrededor de la escena. Estos emisores reproducen sonidos únicos de volumen aleatorio, tono y frecuencia de desencadenador. Esta técnica crea ambiente que tiene una sensación mejorada de direccionalidad. Por ejemplo, en TemasAtes, puede escuchar cómo cada cuadrante del panorama tiene emisores específicos que resaltan áreas específicas de la geografía, pero trabajan juntos para crear un ambiente envolvente general.

## <a name="tips-and-tricks"></a>Sugerencias y trucos

Hay otras maneras de resaltar la direccionalidad y mejorar la inmersión para hacer un uso completo de las funcionalidades de sonido espacial de HoloLens. Aquí se proporciona una lista. Escuche estos efectos la próxima vez que pruebe HoloTour.
* **Buscar destinos:** Estos sonidos se desencadenan cuando se observa un objeto o área específicos del marco holográfico. Por ejemplo, mire hacia el café del lado de la calle en la ciudad de Rome para desencadenar sutilmente sonidos de restaurantes ocupados.
* **Visión local:** El recorrido, aunque HoloTour contiene ciertos "latidos", donde la guía de paseo, con ayuda de hologramas, explora un tema en profundidad. Por ejemplo, a medida que la fachada del Pantheon se disuelve para revelar el oculus, el audio reverberante que se colocó como emisor 3D desde dentro del Pantheon anima al usuario a explorar el interior.
* **Direccionalidad mejorada:** En muchas escenas, colocamos sonidos de varias maneras de agregar a la direccionalidad. En la escena de Pantheon, por ejemplo, el sonido del sonido del sonido se colocaba como un emisor independiente lo suficientemente cerca del usuario para que pudiera obtener una sensación de "paralax sónica" al recorrer el espacio de juego. En la escena salinas de Maras, los sonidos de pequeñas secuencias individuales se colocaron como emisores independientes para crear un entorno ambiental más envolvente, rodeando al usuario con los sonidos auténticos de esa ubicación.
* **Emisor spline:** Estos emisores se mueven en espacio 3D en función de la posición visual del objeto al que están asociados. Un ejemplo es el entrenamiento en Sentido Nico, donde se usa un emisor de spline para dar un sentido distintivo de direccionalidad y movimiento.
* **Música y SFX:** Ciertos aspectos de HoloTour que representan un enfoque más estilizado o sonético usan la música y los efectos de sonido para aumentar el impacto emocional. Por ejemplo, el animador se enfrentará al final del paseo de Rome y usa efectos especiales como whooshes y stingers para reforzar el efecto de las etiquetas que aparecen en las escenas.

## <a name="see-also"></a>Consulte también

* [Sonido espacial](spatial-sound.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Sonido espacial en Unity](../develop/unity/spatial-sound-in-unity.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
