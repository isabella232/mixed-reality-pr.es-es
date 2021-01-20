---
title: Movimiento de inicio
description: Obtenga información acerca de cómo usar el gesto de inicio para llamar al menú Inicio en HoloLens y en los auriculares con forma de Windows Mixed Reality.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, floración
ms.openlocfilehash: d0f3bd81cab945a01a523806ebaf4546752d74c1
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583236"
---
# <a name="start-gesture"></a>Movimiento de inicio

El gesto de inicio es un gesto de mano que se usa para invocar el menú Inicio. Es el equivalente de presionar la tecla Windows en los teclados, el botón Xbox en los controladores Xbox o el botón Windows en los controladores de movimiento de auriculares inmersivo. Preste especial atención a los gestos del sistema reservados en cada dispositivo de realidad mixta para evitar conflictos al diseñar interacciones.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Eclosión</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Botón de muñeca</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Mira fijamente y contacto con Palm up</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Eclosión

Hemos diseñado "floración" para que aparezca el menú Inicio en HoloLens (1ª generación), que es un gesto simbólico que imita un Blossom de flores. Es distintivo para asegurar la interacción, es fácil de usar y rápida para la recuperación. Para usar el gesto, mantenga su mano con su bolsillo hacia arriba y a la mano y, a continuación, abra la mano mediante la distribución de los dedos.

:::row:::
    :::column:::
        ![Cierre del floración](images/bloom-close.png)<br>
        **Paso 1: Palm con las manos**<br>
    :::column-end:::
    :::column:::
        ![Floración abierto](images/bloom-open.png)<br>
        **Paso 2: Palm up con la mano**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Movimiento de inicio

En HoloLens 2, reemplazamos el gesto de floración por un botón de muñeca virtual, que es más instinctual para los usuarios. Al mostrar a los usuarios el botón de la muñeca, pueden ponerse en contacto de forma intuitiva y presionarlo con la mano.

:::row:::
    :::column:::
        ![Botón de pulsera listo](images/wrist-button-ready.png)<br>
        **Paso 1: Palm para mostrar el botón de muñeca**<br>
    :::column-end:::
    :::column:::
        ![Presionar el botón de muñeca](images/wrist-button-press.png)<br>
        **Paso 2: presionar el botón de muñeca**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Gesto de inicio con una sola mano

> [!IMPORTANT]
> Para que funcione el gesto de inicio con una sola mano:
>
> 1. Debe actualizar a la actualización de noviembre de 2019 (compilación 18363,1039) o posterior.
> 1. Los ojos deben calibrarse en el dispositivo para que el seguimiento ocular funcione correctamente. Si no ve puntos en órbita alrededor del icono de inicio al mirarlo, los ojos no se calibrarán en el dispositivo.

También puede usar el gesto de inicio con solo una mano. Manténgase al alcance de su mano con la mano y mire el **icono de inicio** en su muñeca interna. **Mientras mantiene el ojo del icono**, acerque el dedo y el dedo del índice.<br>
:::row:::
    :::column:::
        ![Botón de pulsera listo](images/wrist-button-ready.png)<br>
        **Paso 1: Palm para mostrar el botón de muñeca**<br>
    :::column-end:::
    :::column:::
        ![Botón de muñeca](images/wrist-button-pinch.png)<br>
        **Paso 2: mira fijamente en el botón y luego en Pinch**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Consulte también

* [Interacciones instintivas](interaction-fundamentals.md)
* [Miras hacia abajo](eye-tracking.md)
* [Entrada de voz](voice-input.md)