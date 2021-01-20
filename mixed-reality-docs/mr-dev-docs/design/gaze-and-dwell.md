---
title: Mirada y permanencia
description: Obtenga información general sobre el modelo de entrada de ojo y punta de la mirada para aplicaciones de realidad mixta.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidad mixta, miradas, viviendas, interacción, diseño, seguimiento ocular, seguimiento de cabezales, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: aa4fceeb8875da89fd7f84c3709ff6db07fd96f4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582137"
---
# <a name="gaze-and-dwell"></a>Mirada y permanencia

Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible.
Los comandos de voz también pueden ser poco confiables en determinados contextos, por ejemplo, en condiciones excesivamente altas.
La mirada y la vivienda ofrecen un mecanismo familiar y fácil de usar para los directivos de trabajo y las manos libres de HoloLens.
Además, la mirada y la permanencia son una gran reserva, que es independiente de las interferencias de ruido o las restricciones de silencio en el entorno operativo.
Se distinguen dos variantes de _miradas y_ de la vivienda: [miran hacia la cabeza y la vivienda](gaze-and-dwell-head.md) , y [miran](gaze-and-dwell-eyes.md)y se superponen.

## <a name="scenarios"></a>Escenarios

Miran y colaboran en escenarios en los que las manos de una persona están ocupados con otras tareas y la voz no es 100% confiable o disponible debido a restricciones ambientales o sociales.
Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil.
Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor.
En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz.
La mirada y la vivienda permiten a la persona que usa HoloLens navegar por confianza su material de referencia sin interrumpir su flujo de trabajo.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mirada con la cabeza y permanencia</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
     <tr>
        <td>Control con los ojos y permanencia</td>
        <td>❌ No disponible</td>
        <td>✔️ Recomendado</td>
        <td>❌ No disponible</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>Consulte también

* [Interacción basada en los ojos](eye-gaze-interaction.md)
* [Seguimiento de los ojos en HoloLens 2](eye-tracking.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)