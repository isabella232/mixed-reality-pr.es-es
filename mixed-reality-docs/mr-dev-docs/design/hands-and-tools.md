---
title: Controladores de manos y movimiento
description: Obtenga información sobre los modelos de interacción de manos y controladores de movimiento, que pueden quitar el límite entre lo virtual y lo físico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality, manos, controladores de movimiento, interacción, diseño, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 3a54d707260a3e5aebd83a53b62098504c86c9fea7b2ecbb49d3dbd8b72400dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213704"
---
# <a name="hands-and-motion-controllers"></a>Controladores de manos y movimiento

## <a name="scenarios"></a>Escenarios

Después de leer la [introducción a la](interaction-fundamentals.md)interacción, elija el modelo de interacción de mano y controlador de movimiento. Esto significa que está desarrollando una aplicación que requiere que los usuarios usen dos manos para interactuar con el mundo holográfico. La aplicación va a lograr el objetivo de quitar el límite entre virtual y físico.

Algunos escenarios específicos pueden ser:
* Proporcionar a los trabajadores de la información pantallas virtuales 2D con prestaciones de la interfaz de usuario para mostrar y controlar el contenido.
* Proporcionar tutoriales y guías de trabajadores de primera línea para las líneas de ensamblado de fábrica
* Desarrollo de herramientas profesionales para ayudar y formar a los profesionales médicos.  
* Uso de objetos virtuales 3D para decorar el mundo real o crear un segundo mundo. 
* Crear servicios y juegos basados en la ubicación que usan el mundo real como fondo.

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Modalidades de controladores de manos y movimiento

:::row:::
    :::column:::
       [![Manipulación directa con las manos](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[Manipulación directa con las manos](direct-manipulation.md)<br>
       Modalidad que aplica el poder de las manos que los usuarios pueden usar para tocar y manipular hologramas. Mediante el uso de experiencias de la vida diaria y la prestación visual adecuada, los usuarios pueden usar la misma manera de manipular objetos del mundo real para interactuar con los virtuales.
    :::column-end:::
    :::column:::
       [![Apuntar y confirmar con las manos](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[Apuntar y confirmar con las manos](point-and-commit.md)<br>
        Esta modalidad permite a los usuarios interactuar con hologramas a distancia. Permite a los usuarios hacer el mejor uso del entorno. Los usuarios pueden colocar hologramas en cualquier lugar y seguir teniendo acceso a ellos desde cualquier distancia. Los modelos y gestos mentales para controlar y manipular hologramas 2D y 3D están muy sincronizados con los de manipulación directa.
    :::column-end:::
    :::column:::
       [![Controladores de movimiento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[Controladores de movimiento](motion-controllers.md)<br>
       Los controladores de movimiento amplían las funcionalidades físicas del usuario con interacciones precisas a lo largo de un intervalo de distancias mientras se usan una o ambas manos. Estos accesorios de hardware proporcionan accesos directos a muchas interacciones que se usan con frecuencia y proporcionan comentarios táctiles seguros para diversas acciones. Actualmente, los controladores de movimiento solo están disponibles para Windows Mixed Reality escenarios (WMR). 
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
