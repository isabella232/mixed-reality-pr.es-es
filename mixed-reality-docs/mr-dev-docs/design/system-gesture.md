---
title: Movimiento de inicio
description: Obtenga información acerca de cómo usar el gesto de inicio para llamar al menú Inicio en HoloLens y en los auriculares con forma de Windows Mixed Reality.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, floración
ms.openlocfilehash: 9e29d483375db103cebc30be9117e40899a9f81f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009435"
---
# <a name="start-gesture"></a><span data-ttu-id="79a9a-104">Movimiento de inicio</span><span class="sxs-lookup"><span data-stu-id="79a9a-104">Start gesture</span></span>

<span data-ttu-id="79a9a-105">El gesto de inicio es un gesto de mano que se usa para invocar el menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="79a9a-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="79a9a-106">Es el equivalente de presionar la tecla Windows en los teclados, el botón Xbox en los controladores Xbox o el botón Windows en los controladores de movimiento de auriculares inmersivo.</span><span class="sxs-lookup"><span data-stu-id="79a9a-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="79a9a-107">Preste especial atención a los gestos del sistema reservados en cada dispositivo de realidad mixta para evitar conflictos al diseñar interacciones.</span><span class="sxs-lookup"><span data-stu-id="79a9a-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="79a9a-108">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="79a9a-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="79a9a-109"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="79a9a-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="79a9a-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="79a9a-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="79a9a-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="79a9a-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="79a9a-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="79a9a-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="79a9a-113">Eclosión</span><span class="sxs-lookup"><span data-stu-id="79a9a-113">Bloom</span></span></td>
        <td><span data-ttu-id="79a9a-114">✔️</span><span class="sxs-lookup"><span data-stu-id="79a9a-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="79a9a-115">Botón de muñeca</span><span class="sxs-lookup"><span data-stu-id="79a9a-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="79a9a-116">✔️</span><span class="sxs-lookup"><span data-stu-id="79a9a-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="79a9a-117">Mira fijamente y contacto con Palm up</span><span class="sxs-lookup"><span data-stu-id="79a9a-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="79a9a-118">✔️</span><span class="sxs-lookup"><span data-stu-id="79a9a-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="79a9a-119">Eclosión</span><span class="sxs-lookup"><span data-stu-id="79a9a-119">Bloom</span></span>

<span data-ttu-id="79a9a-120">Hemos diseñado "floración" para que aparezca el menú Inicio en HoloLens (1ª generación), que es un gesto simbólico que imita un Blossom de flores.</span><span class="sxs-lookup"><span data-stu-id="79a9a-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="79a9a-121">Es distintivo para asegurar la interacción, es fácil de usar y rápida para la recuperación.</span><span class="sxs-lookup"><span data-stu-id="79a9a-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="79a9a-122">Para usar el gesto, mantenga su mano con su bolsillo hacia arriba y a la mano y, a continuación, abra la mano mediante la distribución de los dedos.</span><span class="sxs-lookup"><span data-stu-id="79a9a-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="79a9a-123">![Cierre del floración](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="79a9a-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="79a9a-124">**Paso 1: Palm con las manos**</span><span class="sxs-lookup"><span data-stu-id="79a9a-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="79a9a-125">![Floración abierto](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="79a9a-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="79a9a-126">**Paso 2: Palm up con la mano**</span><span class="sxs-lookup"><span data-stu-id="79a9a-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="79a9a-127">Movimiento de inicio</span><span class="sxs-lookup"><span data-stu-id="79a9a-127">Start gesture</span></span>

<span data-ttu-id="79a9a-128">En HoloLens 2, reemplazamos el gesto de floración por un botón de muñeca virtual, que es más instinctual para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="79a9a-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="79a9a-129">Al mostrar a los usuarios el botón de la muñeca, pueden ponerse en contacto de forma intuitiva y presionarlo con la mano.</span><span class="sxs-lookup"><span data-stu-id="79a9a-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="79a9a-130">![Botón de pulsera listo](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="79a9a-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="79a9a-131">**Paso 1: Palm para mostrar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="79a9a-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="79a9a-132">![Presionar el botón de muñeca](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="79a9a-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="79a9a-133">**Paso 2: presionar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="79a9a-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="79a9a-134">Gesto de inicio con una sola mano</span><span class="sxs-lookup"><span data-stu-id="79a9a-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79a9a-135">Para que funcione el gesto de inicio con una sola mano:</span><span class="sxs-lookup"><span data-stu-id="79a9a-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="79a9a-136">Debe actualizar a la actualización de noviembre de 2019 (compilación 18363,1039) o posterior.</span><span class="sxs-lookup"><span data-stu-id="79a9a-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="79a9a-137">Los ojos deben calibrarse en el dispositivo para que el seguimiento ocular funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="79a9a-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="79a9a-138">Si no ve puntos en órbita alrededor del icono de inicio al mirarlo, los ojos no se calibrarán en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="79a9a-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="79a9a-139">También puede usar el gesto de inicio con solo una mano.</span><span class="sxs-lookup"><span data-stu-id="79a9a-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="79a9a-140">Manténgase al alcance de su mano con la mano y mire el **icono de inicio** en su muñeca interna.</span><span class="sxs-lookup"><span data-stu-id="79a9a-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="79a9a-141">**Mientras mantiene el ojo del icono**, acerque el dedo y el dedo del índice.</span><span class="sxs-lookup"><span data-stu-id="79a9a-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="79a9a-142">![Botón de pulsera listo](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="79a9a-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="79a9a-143">**Paso 1: Palm para mostrar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="79a9a-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="79a9a-144">![Botón de muñeca](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="79a9a-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="79a9a-145">**Paso 2: mira fijamente en el botón y luego en Pinch**</span><span class="sxs-lookup"><span data-stu-id="79a9a-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="79a9a-146">Consulte también</span><span class="sxs-lookup"><span data-stu-id="79a9a-146">See also</span></span>

* [<span data-ttu-id="79a9a-147">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="79a9a-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="79a9a-148">Miras hacia abajo</span><span class="sxs-lookup"><span data-stu-id="79a9a-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="79a9a-149">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="79a9a-149">Voice input</span></span>](voice-input.md)
