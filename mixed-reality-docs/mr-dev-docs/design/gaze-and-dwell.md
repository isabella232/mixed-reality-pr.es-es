---
title: Mirada y permanencia
description: Obtenga información general sobre el modelo de entrada de ojo y punta de la mirada para aplicaciones de realidad mixta.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidad mixta, miradas, viviendas, interacción, diseño, seguimiento ocular, seguimiento de cabezales, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 2daeea996251b1220ee4753567b42117fbb2126c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007645"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="23ff8-104">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="23ff8-104">Gaze and dwell</span></span>

<span data-ttu-id="23ff8-105">Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible.</span><span class="sxs-lookup"><span data-stu-id="23ff8-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="23ff8-106">Los comandos de voz también pueden ser poco confiables en determinados contextos, por ejemplo, en condiciones excesivamente altas.</span><span class="sxs-lookup"><span data-stu-id="23ff8-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="23ff8-107">La mirada y la vivienda ofrecen un mecanismo familiar y fácil de usar para los directivos de trabajo y las manos libres de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="23ff8-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="23ff8-108">Además, la mirada y la permanencia son una gran reserva, que es independiente de las interferencias de ruido o las restricciones de silencio en el entorno operativo.</span><span class="sxs-lookup"><span data-stu-id="23ff8-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="23ff8-109">Se distinguen dos variantes de _miradas y_ de la vivienda: [miran hacia la cabeza y la vivienda](gaze-and-dwell-head.md) , y [miran](gaze-and-dwell-eyes.md)y se superponen.</span><span class="sxs-lookup"><span data-stu-id="23ff8-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="23ff8-110">Escenarios</span><span class="sxs-lookup"><span data-stu-id="23ff8-110">Scenarios</span></span>

<span data-ttu-id="23ff8-111">Miran y colaboran en escenarios en los que las manos de una persona están ocupados con otras tareas y la voz no es 100% confiable o disponible debido a restricciones ambientales o sociales.</span><span class="sxs-lookup"><span data-stu-id="23ff8-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="23ff8-112">Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil.</span><span class="sxs-lookup"><span data-stu-id="23ff8-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="23ff8-113">Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor.</span><span class="sxs-lookup"><span data-stu-id="23ff8-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="23ff8-114">En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="23ff8-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="23ff8-115">La mirada y la vivienda permiten a la persona que usa HoloLens navegar por confianza su material de referencia sin interrumpir su flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="23ff8-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="23ff8-116">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="23ff8-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="23ff8-117"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="23ff8-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="23ff8-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="23ff8-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="23ff8-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="23ff8-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="23ff8-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="23ff8-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="23ff8-121">Mirada con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="23ff8-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="23ff8-122">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="23ff8-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="23ff8-123">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="23ff8-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="23ff8-124">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="23ff8-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="23ff8-125">Control con los ojos y permanencia</span><span class="sxs-lookup"><span data-stu-id="23ff8-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="23ff8-126">❌ No disponible</span><span class="sxs-lookup"><span data-stu-id="23ff8-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="23ff8-127">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="23ff8-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="23ff8-128">❌ No disponible</span><span class="sxs-lookup"><span data-stu-id="23ff8-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="23ff8-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="23ff8-129">See also</span></span>

* [<span data-ttu-id="23ff8-130">Interacción basada en los ojos</span><span class="sxs-lookup"><span data-stu-id="23ff8-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="23ff8-131">Seguimiento de los ojos en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="23ff8-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="23ff8-132">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="23ff8-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="23ff8-133">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="23ff8-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="23ff8-134">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="23ff8-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="23ff8-135">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="23ff8-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="23ff8-136">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="23ff8-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="23ff8-137">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="23ff8-137">Voice input</span></span>](voice-input.md)
