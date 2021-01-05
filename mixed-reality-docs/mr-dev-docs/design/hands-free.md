---
title: Manos libres
description: Obtenga información acerca de las dificultades a las que pueden encontrarse los usuarios con una interfaz de manos y controladores y sobre diversas alternativas gratuitas.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realidad mixta, manos libres, miradas a la mano, la interacción, el diseño, el casco de realidad mixta, el casco de la realidad mixta de Windows, el casco de realidad virtual, HoloLens, MRTK, el kit de herramientas de realidad mixta, la entrada de voz, la facilidad de uso
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847678"
---
# <a name="hands-free"></a>Manos libres

## <a name="scenarios"></a>Escenarios

Tal como se describe en [información general sobre el modelo de interacción](interaction-fundamentals.md), una vez que haya identificado los usuarios y sus objetivos, pregúntese qué desafíos ambientales o en situaciones pueden enfrentarse a medida que trabajan para realizar sus tareas. Por ejemplo, muchos usuarios necesitan usar sus manos para lograr sus objetivos del mundo real y tienen dificultades para interactuar con una interfaz basada en manos y controladores.

Algunos escenarios específicos incluyen: 
* Guiar al usuario por una tarea mientras tiene las manos ocupadas.
* Consultar materiales mientras el usuario tiene las manos ocupadas.
* Fatiga manual.
* Guantes en los que no se puede realizar un seguimiento.
* Llevar algo en las manos.
* Awkwardness social al usar gestos de gran tamaño
* Espacios estrechos.

## <a name="hands-free-modalities"></a>Modalidades de manos libres

### <a name="voice-input"></a>[Entrada de voz](voice-input.md)

El uso de la voz para el comando y el control de una interfaz ofrece una manera cómoda de trabajar de forma gratuita y usar accesos directos para omitir varios pasos si lo desea. Con la entrada de voz, el usuario puede leer el nombre de cualquier botón en voz alta para activarlo _("verlo, decirlo")_ y conversar con un agente digital que puede realizar tareas por usted.

### <a name="gaze-and-dwell"></a>[Mirada y permanencia](gaze-and-dwell.md)

En algunas situaciones sin experiencia, el uso de la voz no es lo ideal o incluso posible. Los entornos de fábrica, la privacidad o las normas sociales de alta carga pueden ser restricciones. El modelo de vista y la vivienda permite al usuario navegar por una aplicación sin ninguna información adicional aparte de su ojo o mirarnos: el usuario simplemente mantiene Gazing (con sus cabezales o ojos) en el destino y permanece en él durante un momento para activarlo. Para obtener más información acerca de las consideraciones de diseño individuales para mirarlas y la vivienda, eche [un vistazo a la vista de miras + la vivienda](gaze-and-dwell-eyes.md) y [el cabezal y la vivienda](gaze-and-dwell-head.md).

## <a name="transitioning-in-and-out-of-hands-free"></a>Transición dentro y fuera de manos libres

En estos casos, la liberación de las manos de la interacción con los hologramas para la navegación y los comandos puede abarcar de ser un requisito absoluto para el funcionamiento de la aplicación, de un extremo a otro, a una mayor comodidad en la que el usuario puede realizar la transición en cualquier momento. 

Si la aplicación requiere que siempre se use de forma gratuita, ya sea mediante la permanencia, comandos de voz personalizados o el único comando de voz, "seleccionar", asegúrese de tomar las adaptaciones adecuadas en la interfaz de usuario. 

Si el usuario de destino tiene que cambiar de manos libres a su discreción, es importante tener en cuenta los siguientes principios.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Supongamos que el usuario ya está en el modo al que desea cambiar
Por ejemplo, si el usuario está en la fábrica, viendo una referencia de vídeo en su HoloLens y decide tomar una llave para empezar a trabajar, lo más probable es que comience a trabajar en manos libres sin tener que dejar la llave inglesa para presionar un botón. Puede invocar una sesión de voz con un comando de voz, hospedar en una interfaz de usuario ya visible para comenzar la permanencia o decir la palabra "seleccionar".

El usuario puede: 
* Cambiar a manos libres sin manos libres
* Cambiar a manos con las manos
* Cambiar al controlador mediante un controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Crear formas redundantes de cambiar de modo

Aunque el primer principio es acerca del acceso, el segundo es acerca de la disponibilidad. No debe haber una única manera de pasar de un modo a otro. 

Algunos ejemplos serían: 
* Un botón para iniciar las interacciones de voz
* Un comando de voz para realizar la transición a, con el encabezado de la mirada y la vivienda

### <a name="add-a-dash-of-drama"></a>Agregar un guion de series

Un cambio de modo es un gran negocio. Es importante que cuando estas transiciones sucedan que se trata de un modificador explícito, incluso un cambio drástico, para que el usuario sepa lo que ha sucedido. 

## <a name="usability-checklist"></a>Lista de comprobación de usabilidad

**¿Puede el usuario hacer todo lo posible y todo lo que sea gratuito?**
* Cada interactúable debe ser accesible sin complicaciones
* Asegúrese de que haya un reemplazo para todos los gestos personalizados, como el cambio de tamaño, la colocación, los deslizamientos, los grifos, etc.
* Asegúrese de que el usuario tiene el control seguro de la presencia de la interfaz de usuario, la ubicación y el nivel de detalle siempre
    * Sacar la interfaz de usuario del camino
    * Interfaz de usuario de direccionamiento fuera del campo de vista (campo de campo)
    * ¿Cuánto veo, dónde?

**¿La mecánica de la interacción se enseña y se refuerza con las prestaciones adecuadas?**

¿Entiende el usuario...
* ... ¿En qué modo se encuentran?
* ... ¿Qué pueden hacer en este modo?
* ... ¿Cuál es el estado actual?
* ... ¿Cómo pueden realizar la transición?
    
**¿La interfaz de usuario está optimizada para manos libres?**   

* Ejemplo: las prestaciones de permanencia no están integradas en patrones 2D típicos
* Ejemplo: el destinatario de la voz es mejor con el resaltado de objetos
* Ejemplo: las interacciones de voz son mejores con títulos que se deben activar

## <a name="see-also"></a>Consulte también

* [Seguimiento de los ojos en HoloLens 2](eye-tracking.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
