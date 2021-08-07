---
title: Gesto Inicio
description: Obtenga información sobre cómo usar el gesto de inicio para llamar al menú Inicio HoloLens y Windows Mixed Reality cascos envolventes.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed Reality, gestos, interacción, diseño, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, bloom
ms.openlocfilehash: f3ad9309c7232f20a25060b1d98d7374272ceea00f24be18d7263b8ec7002fb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213745"
---
# <a name="start-gesture"></a>Gesto Inicio

El gesto De inicio es un gesto de mano que se usa para invocar el menú Inicio. Equivale a presionar la tecla Windows teclados, el botón Xbox en los controladores de Xbox o el botón Windows en los controladores de movimiento envolventes del casco. Preste especial atención a los gestos reservados del sistema en Mixed Reality dispositivo para evitar conflictos al diseñar interacciones.

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
        <td>Botón de botón Dedo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Mirada con los ojos y desenlazador</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Eclosión

Hemos diseñado "Bloom" para mostrar el menú inicio en HoloLens (1ª generación), que es un gesto simbólico que imita una flor. Es distintivo para la interacción segura, fácil de usar y rápida de recuperar. Para usar el gesto, mantenga la mano con la mano arriba y los dedos juntos y, a continuación, abra la mano repartiendo los dedos.

:::row:::
    :::column:::
        ![Cierre de Bloom](images/bloom-close.png)<br>
        **Paso 1: Manos arriba con los dedos juntos**<br>
    :::column-end:::
    :::column:::
        ![Apertura de Bloom](images/bloom-open.png)<br>
        **Paso 2: Resalte con los dedos extendidos**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Gesto Inicio

En HoloLens 2, reemplazamos el gesto de Bloom por un botón de botones de botones virtuales, que es más instintivo para los usuarios. Al mostrar a los usuarios el botón de la mano, pueden comunicarse intuitivamente y presionarlo con la otra mano.

:::row:::
    :::column:::
        ![Botón de botón Desa punto](images/wrist-button-ready.png)<br>
        **Paso 1: Pie arriba para mostrar el botón de botones de botones**<br>
    :::column-end:::
    :::column:::
        ![Botón de botones de presión](images/wrist-button-press.png)<br>
        **Paso 2: Presionar el botón de presión**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Gesto Inicio con una mano

> [!IMPORTANT]
> Para que el gesto Inicio funcione con una mano:
>
> 1. Debe aplicar la actualización de noviembre de 2019 (compilación 18363.1039) o posterior.
> 1. Los ojos deben estar calibrados en el dispositivo para que el seguimiento de ojos funcione correctamente. Si no ve puntos alrededor del icono Inicio al mirarlo, los ojos no están calibrados en el dispositivo.

También puede usar el gesto Iniciar con una sola mano. Mantenga la mano con la mano orientada a usted y mire el icono **De inicio** en la mano interna. **Mientras mantiene el ojo sobre el icono**, acerque el dedo pulgar y el dedo índice.<br>
:::row:::
    :::column:::
        ![Botón de botón Desa punto](images/wrist-button-ready.png)<br>
        **Paso 1: Pie arriba para mostrar el botón de botones de botones**<br>
    :::column-end:::
    :::column:::
        ![Botones de botones de botones de botones](images/wrist-button-pinch.png)<br>
        **Paso 2: mirada con los ojos en el botón y, después, acercar**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Consulte también

* [Interacciones instintivas](interaction-fundamentals.md)
* [Mirada con los ojos](eye-tracking.md)
* [Entrada de voz](voice-input.md)