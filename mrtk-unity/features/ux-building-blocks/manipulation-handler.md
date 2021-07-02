---
title: Controlador de manipulación
description: Documentación sobre el controlador de manipulación en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, manipulación,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176630"
---
# <a name="manipulation-handler"></a>Controlador de manipulación

![Controlador de manipulación](../images/manipulation-handler/MRTK_Manipulation_Main.png)

El script *ManipulationHandler* permite que un objeto se pueda mover, escalable y girar con una o dos manos. La manipulación se puede restringir para que solo permita determinados tipos de transformación. El script funciona con varios tipos de entradas, como una entrada de mano articulada, rayo HoloLens 2 s de mano, entrada de gesto de HoloLens (1.ª generación) y entrada de controlador de movimiento de casco envolvente.

## <a name="how-to-use-the-manipulation-handler"></a>Uso del controlador de manipulación

Agregue el `ManipulationHandler` componente de script a un Objeto GameObject. Asegúrese de agregar también un colisionador al objeto, que coincida con sus límites que se pueden agarrar.

Para que el objeto responda a una entrada de mano casi articulada, agregue también `NearInteractionGrabbable` el script.

![Uso del controlador de manipulación en el editor de Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>Propiedades del inspector

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**Transformación de host** Transformación que se arrastrará. El valor predeterminado es el objeto del componente.

**Tipo de manipulación** Especifica si el objeto se puede manipular con una mano, dos manos o ambas.

* *Solo una mano*
* *Solo dos manos*
* *Una y dos manos*

**Tipo de manipulación con dos manos**

* *Escala:* solo se permite el escalado.
* *Girar:* solo se permite la rotación.
* *Mover escala:* se permite el movimiento y el escalado.
* *Mover rotación:* se permite mover y girar.
* *Girar escala:* se permite la rotación y el escalado.
* *Mover escala de rotación:* se permite mover, girar y escalar.

![Controlador de manipulación](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**Permitir manipulación lejana** Especifica si se puede realizar la manipulación mediante la interacción lejana con punteros.

**Modo de rotación de una mano cerca** Especifica cómo se comportará el objeto cuando se esté capturando con una mano o un controlador cerca.

**Modo de rotación de una mano lejos** Especifica cómo se comportará el objeto cuando se esté capturando con una mano o un controlador a distancia.

**Opciones del modo de rotación de una mano** Especifica cómo girará el objeto cuando se le agarró con una mano.

* *Mantener la rotación original:* no gira el objeto mientras se mueve.
* *Mantener la rotación al usuario:* mantiene al usuario la rotación original del objeto para el eje X/Y.
* *La gravedad alineada mantiene la rotación al* usuario: mantiene la rotación original del objeto al usuario, pero hace que el objeto sea vertical. Útil para objetos con un control de límites.
* *Usuario de face:* garantiza que el objeto siempre se enfrenta al usuario. Útil para paneles o pizarras.
* *Cara lejos del usuario:* garantiza que el objeto siempre se aleje del usuario. Resulta útil para las pizarras o paneles configurados con versiones anteriores.
* *Girar sobre el centro de objetos:* solo funciona para manos o controladores articulados. Girar el objeto mediante la rotación de la mano o el controlador, pero sobre el punto central del objeto. Útil para inspeccionar a distancia.
* *Girar sobre el punto de agarre:* solo funciona para manos o controladores articulados. Gira el objeto como si lo hubiera mantenido la mano o el controlador. Útil para la inspección.

**Comportamiento de la versión** Cuando se libera un objeto, especifique su comportamiento de movimiento físico. Requiere que un componente de rigidbody esté en ese objeto.

* *Nothing*
* *Everything (Todo)*
* *Mantener velocidad*
* *Mantener Angular velocidad*

**Restricciones de rotación** Especifica en qué eje girará el objeto cuando se interactúe con él.

* *None*
* *Solo eje X*
* *Solo eje Y*
* *Solo eje Z*

**Usar espacio local para la restricción** Un botón de alternancia para cambiar entre aplicar restricciones con respecto al eje del espacio mundial o al eje de espacio local.

**Restricciones en el movimiento**

* *None*
* *Corrección de la distancia desde la cabeza*

**Suavizado activo** Especifica si el suavizado está activo.

**Smoothing Amount One Hand** Cantidad de suavizado que se aplicará al movimiento, la escala y la rotación. Suavizado de 0 significa que no hay suavizado. El valor máximo significa que no hay ningún cambio en el valor.

## <a name="events"></a>Events

El controlador de manipulación proporciona los siguientes eventos:

* *OnManipulationStarted:* se desencadena cuando se inicia la manipulación.
* *OnManipulationEnded:* se ejecuta cuando finaliza la manipulación.
* *OnHoverStarted:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.
* *OnHoverEnded:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.
