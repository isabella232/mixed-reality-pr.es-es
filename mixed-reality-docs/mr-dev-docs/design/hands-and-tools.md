---
title: Controladores de manos y movimiento
description: Obtenga información acerca de los modelos de interacción de los controladores de manos y de movimiento, que pueden quitar el límite entre el virtual y el físico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realidad mixta, manos, controladores de movimiento, interacción, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847317"
---
# <a name="hands-and-motion-controllers"></a>Controladores de manos y movimiento

## <a name="scenarios"></a>Escenarios

Después de leer la [información general](interaction-fundamentals.md)de la interacción, elija el modelo de interacción del controlador de movimiento y la mano. Esto significa que está desarrollando una aplicación que requiere que los usuarios usen dos manos para interactuar con el mundo holográfica. La aplicación va a lograr el objetivo de quitar el límite entre virtual y física.

Algunos escenarios específicos pueden ser:
* Proporcionar a los trabajadores de la información pantallas virtuales 2D con prestaciones de la interfaz de usuario para mostrar y controlar el contenido.
* Proporcionar tutoriales y guías de primera línea para las líneas de montaje de fábrica
* Desarrollo de herramientas profesionales para ayudar y formar a los profesionales médicos.  
* Uso de objetos virtuales 3D para decorar el mundo real o crear un segundo mundo. 
* Crear servicios y juegos basados en la ubicación que usan el mundo real como fondo.

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Modalidades de los controladores de manos y de movimiento

:::row:::
    :::column:::
       [![Manipulación directa con las manos](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[Manipulación directa con las manos](direct-manipulation.md)<br>
       Modalidad que aplica la potencia de las manos que los usuarios pueden usar para tocar y manipular los hologramas. Mediante el uso de experiencias de vida diaria y la prestación de prestaciones visuales adecuadas, los usuarios pueden usar la misma manera de manipular objetos del mundo real para interactuar con los virtuales.
    :::column-end:::
    :::column:::
       [![Apuntar y confirmar con las manos](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[Apuntar y confirmar con las manos](point-and-commit.md)<br>
        Esta modalidad permite a los usuarios interactuar con los hologramas en una distancia. Permite a los usuarios hacer el mejor uso de los entornos. Los usuarios pueden colocar hologramas en cualquier lugar y seguir accediendo a ellos desde cualquier distancia. Los modelos y gestos mentales para controlar y manipular los hologramas 2D y 3D están muy sincronizados con los de manipulación directa.
    :::column-end:::
    :::column:::
       [![Controladores de movimiento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[Controladores de movimiento](motion-controllers.md)<br>
       Los controladores de movimiento amplían las capacidades físicas del usuario con interacciones precisas en un intervalo de distancias al usar una o ambas manos. Estos accesorios de hardware proporcionan accesos directos a muchas de las interacciones usadas comúnmente y proporcionan comentarios de seguridad en el pie de página para realizar diversas acciones. Actualmente, los controladores de movimiento solo están disponibles para escenarios de Windows Mixed Reality (WMR). 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Consulta también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Manos libres](hands-free.md)
