---
title: Manos libres
description: Obtenga información sobre las dificultades a las que pueden enfrentarse los usuarios con una interfaz de manos y controladores y sobre diversas alternativas de manos libres.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, manos libres, mirada, mirada dirigida, interacción, diseño, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, entrada de voz, facilidad de uso
ms.openlocfilehash: 725d8886d21b42ee4643680c0dc91c1d29c25f8409b0ed0828256564dde7545c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213539"
---
# <a name="hands-free"></a>Manos libres

## <a name="scenarios"></a>Escenarios

Como se describe en la introducción al modelo de [interacción,](interaction-fundamentals.md)una vez que haya identificado a los usuarios y sus objetivos, pregúntese a qué desafíos ambientales o situacionales podrían enfrentarse a medida que trabajan para realizar sus tareas. Por ejemplo, muchos usuarios necesitan usar sus manos para lograr sus objetivos reales y tendrán dificultades para interactuar con una interfaz basada en manos y controladores.

Algunos escenarios específicos incluyen: 
* Guiar al usuario por una tarea mientras tiene las manos ocupadas.
* Consultar materiales mientras el usuario tiene las manos ocupadas.
* Fatiga manual.
* Guantes en los que no se puede realizar un seguimiento.
* Llevar algo en las manos.
* Incomodidad social al usar gestos de mano grandes
* Espacios estrechos.

## <a name="hands-free-modalities"></a>Modalidades de manos libres

### <a name="voice-input"></a>[Entrada de voz](voice-input.md)

El uso de la voz para controlar y controlar una interfaz ofrece una manera cómoda de trabajar con manos libres y usar accesos directos para omitir varios pasos si lo desea. Con la entrada de voz, el usuario puede leer el nombre de cualquier botón en voz alta para activarlo _("verlo, decirlo")_ y dialogar con un agente digital que pueda realizar tareas automáticamente.

### <a name="gaze-and-dwell"></a>[Mirada y permanencia](gaze-and-dwell.md)

En algunas situaciones de manos libres, el uso de la voz no es ideal ni siquiera posible. Los entornos de fábrica, la privacidad o las normas sociales pueden ser restricciones. El modelo de mirada y permanencia permite al usuario navegar por una aplicación sin ninguna entrada adicional aparte de la mirada con los ojos o la cabeza: el usuario simplemente sigue mirando (con la cabeza o los ojos) al destino y permanece allí durante un momento para activarla. Para más información sobre las consideraciones de diseño individuales de mirada y permanencia, consulte mirada con los ojos [y](gaze-and-dwell-eyes.md) permanencia y mirada con la cabeza [y permanencia.](gaze-and-dwell-head.md)

## <a name="transitioning-in-and-out-of-hands-free"></a>Transición dentro y fuera de las manos libres

En estos escenarios, liberar las manos de la interacción con hologramas para comandos y navegación puede abarcar desde un requisito absoluto hasta el funcionamiento de la aplicación, de un extremo a otro, hasta una mayor comodidad de que el usuario pueda realizar la transición dentro y fuera en cualquier momento. 

Si la aplicación requiere que siempre se use sin manos, ya sea mediante permanencia, comandos de voz personalizados o el comando de una sola voz, "select", asegúrese de crear el espacio adecuado en la interfaz de usuario. 

Si el usuario de destino necesita cambiar de manos a manos libres a su discreción, es importante tener en cuenta los siguientes principios.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Suponga que el usuario ya está en el modo al que desea cambiar.
Por ejemplo, si el usuario está en la fábrica, viendo una referencia de vídeo en su HoloLens y decide recoger una llave inglesa para empezar a trabajar, lo más probable es que empiece a trabajar en manos libres sin tener que bajar la llave inglesa para presionar un botón. Puede invocar una sesión de voz con un comando de voz, permanencia en una interfaz de usuario ya visible para comenzar la permanencia o decir la palabra "seleccionar".

El usuario puede: 
* Cambiar a manos libres mientras se hace uso de las manos libres
* Cambiar a las manos con las manos
* Cambiar al controlador mediante un controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Creación de formas redundantes de cambiar de modo

Aunque el primer principio es sobre el acceso, el segundo trata sobre la disponibilidad. No debe haber una única manera de realizar la transición dentro y fuera de un modo. 

Algunos ejemplos serían: 
* Un botón para comenzar las interacciones de voz
* Un comando de voz al que realizar la transición, mediante la mirada con la cabeza y la permanencia

### <a name="add-a-dash-of-drama"></a>Adición de un guión de guion

Un cambio de modo es muy importante. Es importante que cuando se sucedan estas transiciones, sean un cambio explícito, incluso drástico, para que el usuario sepa lo que ha ocurrido. 

## <a name="usability-checklist"></a>Lista de comprobación de facilidad de uso

**¿Puede el usuario hacer todo y todo lo que sea manos libres, de un extremo a otro?**
* Cada interactuable debe ser accesible con manos libres
* Asegúrese de que hay un reemplazo para todos los gestos personalizados, como el cambio de tamaño, la colocación, los deslizamientos, las pulsaciones, y así sucesivamente.
* Asegúrese de que el usuario tiene un control seguro de la presencia de la interfaz de usuario, la selección de ubicación y el nivel de detalle siempre.
    * Sacar la interfaz de usuario del camino
    * Direccionamiento de la interfaz de usuario que está fuera del campo de vista (FOV)
    * Cuánto veo, dónde, cuándo

**¿Se enseña y se refuerza la mecánica de la interacción con las asequibilidades correctas?**

¿Entiende el usuario...
* ... ¿En qué modo están?
* ... ¿Qué pueden hacer en este modo?
* ... ¿Cuál es el estado actual?
* ... ¿Cómo pueden realizar la transición?
    
**¿La interfaz de usuario está optimizada para manos libres?**   

* Ejemplo: Las asequibilidades de permanencia no están integradas en patrones 2D típicos
* Ejemplo: El destino de voz es mejor con el resaltado de objetos
* Ejemplo: Las interacciones de voz son mejores con subtítulos que deben estar activados

## <a name="see-also"></a>Consulte también

* [Seguimiento de los ojos en HoloLens 2](eye-tracking.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
