---
title: Mirada con los ojos y confirmación
description: Obtenga información sobre el modelo de entrada de mirada con los ojos y confirmación.
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Eye Tracking, Mixed Reality, Input, Eye Gaze, Eye Targeting, HoloLens 2, Eye-based Selection, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit, gaze
ms.openlocfilehash: 1dff0ded282678a695070feca2b578004610d2c7
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196470"
---
# <a name="eye-gaze-and-commit"></a>Mirada con los ojos y confirmación

La _mirada con los ojos y confirmación_ es un caso especial del modelo de entrada de [mirada y confirmación](gaze-and-commit.md) que implica establecer como destino un objeto mirándolo. Se puede actuar sobre el destino con una entrada de _confirmación_ secundaria, como un gesto de la mano, un comando de voz o una entrada de periférico (por ejemplo, un controlador de juego). 

Con HoloLens 2 se nos presenta la gran oportunidad de _mirar y confirmar_ de manera más rápida y cómoda mediante el cómodo control con los ojos en lugar del control con la cabeza. Para ampliar el modelo de interacción habitual de [mirada con la cabeza y confirmación](gaze-and-commit.md): 
1. Mire un destino 
2. Para confirmar su intención de seleccionar el destino, use una entrada explícita secundaria, por ejemplo:  
   - Realice un gesto con la mano (por ejemplo, pulsar en el aire)
   - Presione un botón (por ejemplo, en un teclado Bluetooth o un dispositivo de clic)
   - Emita un comando de voz (por ejemplo, "Select")
   - Mantenga la mirada (es decir, siga mirando el destino para seleccionarlo)

Aun así, la mirada con los ojos se comporta de manera diferente a la mirada con la cabeza en determinados aspectos y presenta numerosos desafíos específicos. 

En las [Directrices para el diseño de mirada con los ojos](eye-tracking.md), se resumen las ventajas generales y los desafíos al usar el seguimiento de los ojos como modelo de entrada en la aplicación holográfica. En esta sección, vamos a centrarnos en las consideraciones de diseño específicas de la función de _control con los ojos y confirmación_.
En primer lugar, los ojos se mueven a una velocidad increíblemente rápida y son estupendos para fijar rápidamente un destino en la vista. La mirada con los ojos resulta idónea para realizar acciones rápidas de mirada y confirmación, sobre todo cuando se combina con confirmaciones rápidas, como pulsar en el aire o presionar un botón.

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demostración de los conceptos de diseño de seguimiento de la cabeza y los ojos

Si quiere ver en acción los conceptos de diseño de seguimiento de cabeza y manos, consulte nuestra demostración de vídeo **Diseño de hologramas: Seguimiento de cabeza y seguimiento de manos** a continuación. Cuando haya terminado, continúe para profundizar más en detalle en temas específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo se tomó de la aplicación "Designing Holograms" para HoloLens 2. Descargue y disfrute de la experiencia completa [aquí](https://aka.ms/dhapp).*
   
## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Directrices de diseño para la mirada con los ojos y la confirmación

**No muestre ningún cursor**: aunque es casi imposible interactuar sin un cursor cuando se usa la mirada con la cabeza, este resulta molesto cuando se usa la mirada con los ojos. En lugar de confiar en un cursor para avisar al usuario de si el seguimiento con la mirada funciona y ha detectado correctamente el destino al que se está mirando actualmente, use otros resaltes visuales más sutiles.

**Busca señales más sutiles de la información sobre el gesto de mantener pulsado**: La información visual que puede parecer estupenda para la mirada con la cabeza puede resultar en experiencias muy negativas en la mirada con los ojos. Recuerde que los ojos son extremadamente rápidos y capaces de fijar la mirada rápidamente en muchos puntos del campo de visión. Los cambios súbitos y rápidos de resaltado (activación o desactivación) pueden provocar un parpadeo al mirar alrededor. Por lo tanto, para proporcionar información sobre el gesto de mantener pulsado, es recomendable utilizar un resaltado con fundido de entrada suave (o fundido de salida al dejar de mirar). Esto significa que al principio apenas se daría cuenta de la información al mirar a un destino. En el transcurso de 500-1000 ms el resaltado aumentaría en intensidad. Aunque puede que los usuarios inexpertos mantengan la mirada en el destino para asegurarse de que el sistema ha determinado correctamente el destino enfocado, los usuarios expertos miran y confirman rápidamente sin necesidad de esperar a que la información alcance su mayor intensidad. También se recomienda usar un fundido de salida que atenúe la información al mantener el puntero. La investigación ha demostrado que los movimientos rápidos y los cambios de contraste son notorios en la visión periférica (el área del campo visual a la que no está mirando directamente).
El fundido de salida no tiene que ser tan lento como el de entrada. Esto solo es importante si dispones de cambios rápidos de contraste o color en el resaltado. Si la información sobre el gesto de mantener pulsado era sutil al comenzar, posiblemente no observará ninguna diferencia.

**Busca señales de sincronización de la mirada y confirmación**: La sincronización de las señales de entrada es un desafío menor para las pulsaciones en el aire y las presiones de botón. Es algo que debe tener en cuenta en caso de que quiera usar acciones de confirmación más complicadas que pueden implicar comandos de voz largos o complicados gestos con las manos. Imagina que miras un objetivo y dices un comando de voz largo. Piense en el tiempo que necesita para pronunciar el comando y el tiempo que tarda el sistema en detectar lo que ha dicho; la mirada con los ojos se habrá dirigido a un nuevo objetivo del escenario. Debe explicar a los usuarios que tienen que fijar la mirada en un destino hasta que se haya reconocido el comando, o bien controlar la entrada de forma que se determine el comienzo del comando y lo que el usuario había estado mirando en ese momento.

## <a name="see-also"></a>Consulta también

* [Interacción basada en ojos] (eye-gaze-interaction.md)
* [Seguimiento de los ojos en HoloLens 2] (eye-tracking.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
