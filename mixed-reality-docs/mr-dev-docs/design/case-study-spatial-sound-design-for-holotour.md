---
title: 'Caso práctico: diseño de sonido espacial para HoloTour'
description: Para crear un paseo virtual 3D realmente envolvente para Microsoft HoloLens, los vídeos panorámicos y los escenarios holográficas solo forman parte de la fórmula.
author: jsyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, sonido espacial, caso práctico, auricular de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, audio
ms.openlocfilehash: 7f2474ba6edbdd54c31b24d38bb60e170b65b25a
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848015"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Caso práctico: diseño de sonido espacial para HoloTour

Los vídeos panorámicos y los escenarios holográficas solo forman parte de la fórmula de un paseo por Microsoft HoloLens. En este artículo se describe cómo se usó el sonido para que se parezca que realmente está en cada ubicación de HoloTour.

## <a name="the-tech"></a>La tecnología

Las atractivas imágenes y escenas holográficas que se ven en HoloTour son solo una parte de una experiencia de realidad mixta increíble. Aunque los hologramas solo aparecen delante de un usuario, HoloLens puede proporcionar [sonido espacial](spatial-sound.md) desde todas las direcciones, lo que proporciona una experiencia organoléptica más completa.

El sonido espacial proporciona indicaciones para indicar una dirección que el usuario debe activar o permitir que el usuario sepa que hay más hologramas para ver dentro de su espacio. También se puede adjuntar un sonido directamente a un holograma y actualizar continuamente la dirección y la distancia que el holograma proviene del usuario. Esta técnica hace que parezca que el sonido proviene directamente de ese objeto.

En el caso de HoloTour, queríamos aprovechar las capacidades de sonido espacial de HoloLens, por lo que creamos un entorno ambiente de 360 grados que se sincroniza con el vídeo para mostrar los resaltados de Sonic de ubicaciones específicas.

## <a name="behind-the-scenes"></a>Entre bambalinas

Creamos experiencias de HoloTour de dos ubicaciones diferentes: Roma y Machu Picchu. Para que estos paseos se sientan auténticos y atractivos, queríamos capturar audio de las ubicaciones donde se filmó en lugar de usar sonidos genéricos.

### <a name="capturing-the-audio"></a>Captura del audio

En nuestro [caso práctico sobre la captura del contenido visual para HoloTour](../out-of-scope/case-study-capturing-and-creating-content-for-holotour.md), hablamos del diseño de la plataforma de la cámara. Constaba de 14 cámaras GoPro en una carcasa impresa en 3D diseñada para adaptarse al trípode. Para capturar audio, agregamos una matriz de micrófono cuádruple debajo de las cámaras. El sonido se alimenta en una unidad de grabación de cuatro canales compacta en la base del trípode. Hemos elegido los micrófonos que han sido correctos, pero que eran lo suficientemente pequeños como para evitar interferir con las cámaras.

![Plataforma de micrófono y videocámara personalizada](images/camera-rig-microphones-300px.png)<br>
*Plataforma de micrófono y de cámara personalizada*

Esta configuración captura sonido en cuatro direcciones. Hemos grabado suficiente información para volver a crear una panorámica 3D aural de sonido espacial, que posteriormente podría sincronizar con el vídeo de 360 grados.

Uno de los desafíos del audio de la matriz de cámara es que está a la velocidad de los sonidos fuera de la cámara, como Sirens, aviones o altas vueltas. Para asegurarse de que teníamos todos los elementos de sonido necesarios, usamos grabadores móviles estéreo y mono para capturar el sonido ambiente asincrónico en puntos de interés específicos de cada ubicación. Estas grabaciones proporcionan al diseñador de sonido el contenido limpio para agregar interés y mejorar la direccionalidad en la producción posterior.

Cada día de captura genera muchos archivos. Por lo tanto, era importante desarrollar un sistema para realizar un seguimiento de qué archivos corresponden a una determinada ubicación o cámara. La unidad de grabación se configuró para asignar nombres automáticamente a los archivos por fecha y "Take". Hemos realizado copias de seguridad de los archivos en unidades externas al final de cada día. También encontramos que es importante empezar de cero a las grabaciones de audio. Esta precaución permite una sencilla identificación contextual del contenido en caso de que se produzcan problemas con el nombre de archivo. También era importante ver la captura de la plataforma de la cámara, ya que el vídeo y el audio se grabaron como medios independientes y debían sincronizarse durante el postproducción.

### <a name="editing-the-audio"></a>Edición del audio

En el estudio después del viaje de captura, el primer paso para ensamblar una experiencia de aural direccional y envolvente es revisar todo el audio capturado para una ubicación. Seleccionamos las mejores tomas e identificamos los resaltados que se pueden aplicar durante la integración. Después, el audio se edita y se limpia. Por ejemplo, una bocina de coche que dura un segundo, o lo que se repite varias veces, se puede reemplazar por un audio ambiente más silencioso de la misma sesión de captura.

Una vez establecida la edición de vídeo de una ubicación, el diseñador de sonido puede sincronizar el audio correspondiente. En este punto, evaluaremos las capturas de sonido móvil y de la plataforma de cámara para decidir qué elementos compilarían la mejor escena de audio envolvente. Encontramos útil colocar todos los elementos de sonido en un editor de audio y crear simuladores lineales rápidos para experimentar con distintas ideas de combinación. Este paso nos ha proporcionado mejores ideas sobre Cuándo llegó el momento de crear las escenas HoloTours reales.

### <a name="assembling-the-scene"></a>Montaje de la escena

El primer paso para crear una escena ambiente 3D es crear una cama de sonidos de bucle de ambiente de fondo generales que admitan otras características y elementos de sonido interactivos en una escena. Tomamos un enfoque holístico de la implementación según lo determinen los criterios de diseño de cualquier escena determinada. Algunas escenas pueden indexar hacia el uso de la captura de cámara sincronizada. Un momento más "cinematográfico" podría requerir un enfoque seleccionada que se basa en sonidos, elementos interactivos y música colocados discretamente.

Cuando se indexa en el audio de captura de cámara, colocamos emisores de audio ambiente de ambiente habilitados para sonido espacial que se corresponden con la orientación direccional de las cámaras. La vista de cámara norte Reproduce audio desde el micrófono norte y, de forma similar, para las otras direcciones cardinales. Estos emisores están bloqueados mundialmente, lo que significa que el sonido cambia cuando los usuarios cambian de cabeza. Esta técnica modela de forma eficaz el sonido de la posición en esa ubicación. Escuche Piazza Navona o Pantheon para ver ejemplos de escenas que usan una buena combinación de audio capturado por cámara.

En un enfoque diferente, a veces se reproduce ambiente estéreo en bucle con los emisores de sonido espacial que se colocan alrededor de la escena. Estos emisores juegan un sonido único de volumen aleatorio, tono y frecuencia del desencadenador. Esta técnica crea ambiente que tiene un sentido mejorado de direccionalidad. En aguas Alienates, por ejemplo, puede oír cómo cada cuadrante de la panorámica tiene emisores específicos que resaltan áreas específicas de la geografía pero colaboran para crear un ambiente envolvente general.

## <a name="tips-and-tricks"></a>Sugerencias y trucos

Hay otras maneras de resaltar la direccionalización y mejorar la inmersión para hacer un uso completo de las capacidades de sonido espacial de HoloLens. Hemos proporcionado una lista aquí. Escuche estos efectos la próxima vez que intente HoloTour.
* **Buscar destinos:** Estos sonidos se desencadenan cuando se observa un objeto o área específica del marco holográfica. Por ejemplo, mire hacia el café de la calle del Navona de Piazza de Roma para desencadenar sutilmente los sonidos de los restaurantes ocupados.
* **Visión local:** El viaje a través de HoloTour contiene ciertas "pulsaciones" en las que la guía del paseo, asistida por hologramas, explora un tema en profundidad. Por ejemplo, a medida que la fachada del Pantheon se resuelve para mostrar el Oculus, la reverberación de audio que se colocó como un emisor 3D desde dentro de la Pantheon anima al usuario a explorar el interior.
* **Direccionalidad mejorada:** En muchas escenas, colocamos sonidos de varias maneras para agregarlos a la direccionalidad. En la escena de Pantheon, por ejemplo, el sonido de la fuente se colocó como una emisora independiente lo suficientemente cerca del usuario que podía tener una idea de "Sonic Parallax" a medida que recorren el espacio de juego. En la escena de Salinas de Maras de Perú, los sonidos de los pocos flujos individuales se colocaban como emisores independientes para compilar un entorno ambiente más envolvente, lo que rodea al usuario con los sonidos auténticos de esa ubicación.
* **Emisor de Spline:** Estos emisores se mueven en el espacio 3D en función de la posición visual del objeto al que están asociados. Un ejemplo es el tren en Machu Picchu, donde usamos un emisor de spline para dar una sensación distintiva de direccionalidad y movimiento.
* **Música y SFX:** Algunos aspectos de HoloTour que representan un enfoque más estilizado o cinematográfico usan música y efectos sonoros para aumentar el impacto emocional. Por ejemplo, la batalla de Gladiator al final del paseo de Roma usa efectos especiales como whooshes y los separadores para reforzar el efecto de las etiquetas que aparecen en segundo plano.

## <a name="see-also"></a>Consulte también

* [Sonido espacial](spatial-sound.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Sonido espacial en Unity](../develop/unity/spatial-sound-in-unity.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
