---
title: Mirada y permanencia
description: Obtenga información general sobre el modelo de entrada de mirada y permanencia con los ojos y la cabeza para las aplicaciones de realidad mixta.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality, mirada, permanencia, interacción, diseño, seguimiento de los ojos, seguimiento de la cabeza, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c65c13b06df70ed5471b283ad349dd72e1575018a98913177983d7a13571d666
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213679"
---
# <a name="gaze-and-dwell"></a>Mirada y permanencia

Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible.
Los comandos de voz también pueden ser poco confiables en determinados contextos, por ejemplo, en condiciones excesivamente ruidosas.
La mirada y permanencia ofrece un mecanismo familiar y fácil de dominar para trabajar de forma rápida y sin manos en HoloLens.
Además, la mirada y permanencia es una gran reserva, que es independiente de las restricciones de interferencia de ruido o silencio en el entorno operativo.
Se distinguen dos variantes de _mirada y permanencia:_ mirada con la cabeza y [permanencia](gaze-and-dwell-head.md) y mirada con los ojos [y permanencia.](gaze-and-dwell-eyes.md)

## <a name="scenarios"></a>Escenarios

La mirada y permanencia se destacan en escenarios en los que las manos de una persona están ocupadas con otras tareas y la voz no es 100 % confiable o disponible debido a restricciones ambientales o sociales.
Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil.
Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor.
En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz.
La mirada y permanencia permite a la persona que usa HoloLens navegar con confianza por su material de referencia sin interrumpir su flujo de trabajo.

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