---
title: Ojos y manos
description: Uso de la orientación con los ojos como puntero principal en combinación con los movimientos de la mano en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: ff464c6f2381a9df020a9ccf807672d4463d662c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175116"
---
# <a name="eyes-and-hands"></a><span data-ttu-id="dcac3-104">Ojos y manos</span><span class="sxs-lookup"><span data-stu-id="dcac3-104">Eyes and hands</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="dcac3-105">Compatibilidad con los _movimientos de_ la mano y la apariencia (mirada con los & gestos de mano)</span><span class="sxs-lookup"><span data-stu-id="dcac3-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="dcac3-106">En esta página se explica cómo usar la orientación con los ojos como puntero principal en combinación con los movimientos de las manos.</span><span class="sxs-lookup"><span data-stu-id="dcac3-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="dcac3-107">En nuestras demostraciones de seguimiento de los ojos de [MRTK,](../../example-scenes/eye-tracking-examples-overview.md)se describen varios ejemplos para usar los ojos y las manos, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="dcac3-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="dcac3-108">[Selección:](eye-tracking-target-selection.md)examinar el botón holográfico lejana y simplemente realizar un gesto de acercamiento para seleccionarlo rápidamente.</span><span class="sxs-lookup"><span data-stu-id="dcac3-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="dcac3-109">**Posicionamiento (este artículo):** mueva fluidamente un holograma por la escena con solo mirarlo, aprete el dedo índice y el dedo para agarrarlo y moverlo con la mano.</span><span class="sxs-lookup"><span data-stu-id="dcac3-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="dcac3-110">[Navegación:](eye-tracking-navigation.md)basta con mirar la ubicación en la que desea  acercar, reducir el dedo índice y el dedo índice juntos y extraer la mano hacia usted para acercarse.</span><span class="sxs-lookup"><span data-stu-id="dcac3-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="dcac3-111">Tenga en cuenta que MRTK está diseñado actualmente de forma que, a distancia, los rayos de mano actúan como punteros de foco priorizado.</span><span class="sxs-lookup"><span data-stu-id="dcac3-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="dcac3-112">Esto significa que los punteros de mirada con la cabeza y los ojos se suprimirán automáticamente una vez que se detecte una mano y se volverán a ver después de decir "Seleccionar".</span><span class="sxs-lookup"><span data-stu-id="dcac3-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="dcac3-113">Sin embargo, puede que esta no sea la manera en que desea interactuar a distancia y prefiere una interacción simple de "mirada y _confirmación"_ independientemente de la presencia de las manos en la vista.</span><span class="sxs-lookup"><span data-stu-id="dcac3-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="dcac3-114">Cómo deshabilitar el rayo de mano</span><span class="sxs-lookup"><span data-stu-id="dcac3-114">How to disable the hand ray</span></span>

<span data-ttu-id="dcac3-115">Para deshabilitar el puntero de rayo de mano, simplemente quite _"DefaultControllerPointer"_ en la configuración de MRTK input _-> Pointer._</span><span class="sxs-lookup"><span data-stu-id="dcac3-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="dcac3-116">Para usar los ojos y las manos como se ha descrito anteriormente en la aplicación, asegúrese también de cumplir todos los requisitos para usar el [seguimiento de los ojos.](eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="dcac3-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Cómo quitar el rayo de mano](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="dcac3-118">También puede consultar cómo se configura el perfil de entrada _EyeTrackingDemoPointerProfile_ del paquete de ejemplo de seguimiento de los ojos como referencia.</span><span class="sxs-lookup"><span data-stu-id="dcac3-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="dcac3-119">Cómo mantener el puntero de mirada siempre on</span><span class="sxs-lookup"><span data-stu-id="dcac3-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="dcac3-120">Para evitar que los punteros de mirada con la cabeza o los ojos se suprima automáticamente una vez que se detecta una mano, se puede especificar la mirada para controlar si debe estar activa [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) o desactivada.</span><span class="sxs-lookup"><span data-stu-id="dcac3-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="dcac3-121">Consulte [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).</span><span class="sxs-lookup"><span data-stu-id="dcac3-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="dcac3-122">Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit)</span><span class="sxs-lookup"><span data-stu-id="dcac3-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
