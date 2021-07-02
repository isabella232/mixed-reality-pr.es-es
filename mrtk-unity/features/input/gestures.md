---
title: Gestos
description: Docummentation on Gestures and its events in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, gestos,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176886"
---
# <a name="gestures"></a><span data-ttu-id="89d86-104">Gestos</span><span class="sxs-lookup"><span data-stu-id="89d86-104">Gestures</span></span>

<span data-ttu-id="89d86-105">Los gestos son eventos de entrada basados en manos humanas.</span><span class="sxs-lookup"><span data-stu-id="89d86-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="89d86-106">Hay dos tipos de dispositivos que genera eventos de entrada de gestos en MRTK:</span><span class="sxs-lookup"><span data-stu-id="89d86-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="89d86-107">Windows Mixed Reality dispositivos como HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89d86-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="89d86-108">Aquí se describen los movimientos de acercamiento ("Pulsación en el aire") y los gestos de pulsar y mantener presionados.</span><span class="sxs-lookup"><span data-stu-id="89d86-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="89d86-109">Para obtener más información sobre los HoloLens, consulte la [documentación Windows Mixed Reality Gestures](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="89d86-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="89d86-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)ajusta el [XR de Unity. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) para consumir eventos de gesto de Unity desde HoloLens dispositivos.</span><span class="sxs-lookup"><span data-stu-id="89d86-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="89d86-111">Dispositivos de pantalla táctil.</span><span class="sxs-lookup"><span data-stu-id="89d86-111">Touch screen devices.</span></span>

  <span data-ttu-id="89d86-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) ajusta la clase [Unity Touch que](https://docs.unity3d.com/ScriptReference/Touch.html) admite pantallas táctiles físicas.</span><span class="sxs-lookup"><span data-stu-id="89d86-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="89d86-113">Ambos orígenes de entrada usan el perfil _gesture Configuración_ para traducir los eventos Touch y Gesture de Unity respectivamente en acciones de entrada [de](input-actions.md)MRTK.</span><span class="sxs-lookup"><span data-stu-id="89d86-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="89d86-114">Este perfil se puede encontrar en el perfil _de Configuración_ entrada.</span><span class="sxs-lookup"><span data-stu-id="89d86-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="89d86-115">Eventos de gestos</span><span class="sxs-lookup"><span data-stu-id="89d86-115">Gesture events</span></span>

<span data-ttu-id="89d86-116">Los eventos de gesto se reciben mediante la implementación de una de las interfaces del controlador de gestos: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vea la tabla de [controladores de eventos](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="89d86-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="89d86-117">Vea [Escena de ejemplo para](#example-scene) obtener una implementación de ejemplo de un controlador de eventos de gestos.</span><span class="sxs-lookup"><span data-stu-id="89d86-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="89d86-118">Al implementar la versión genérica, los eventos *OnGestureCompleted* y *OnGestureUpdated* pueden recibir datos con tipo de los siguientes tipos:</span><span class="sxs-lookup"><span data-stu-id="89d86-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="89d86-119">`Vector2` - Gesto de posición 2D.</span><span class="sxs-lookup"><span data-stu-id="89d86-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="89d86-120">Producido por pantallas táctiles para informar de su [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .</span><span class="sxs-lookup"><span data-stu-id="89d86-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="89d86-121">`Vector3` - Gesto de posición 3D.</span><span class="sxs-lookup"><span data-stu-id="89d86-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="89d86-122">Producido por HoloLens para informar de:</span><span class="sxs-lookup"><span data-stu-id="89d86-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="89d86-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) de un evento de manipulación</span><span class="sxs-lookup"><span data-stu-id="89d86-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="89d86-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) de un evento de navegación</span><span class="sxs-lookup"><span data-stu-id="89d86-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="89d86-125">`Quaternion` - Gesto de rotación 3D.</span><span class="sxs-lookup"><span data-stu-id="89d86-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="89d86-126">Disponible para orígenes de entrada personalizados, pero no producidos actualmente por ninguno de los existentes.</span><span class="sxs-lookup"><span data-stu-id="89d86-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="89d86-127">`MixedRealityPose` - Gesto combinado de posición y rotación 3D.</span><span class="sxs-lookup"><span data-stu-id="89d86-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="89d86-128">Disponible para orígenes de entrada personalizados, pero no producidos actualmente por ninguno de los existentes.</span><span class="sxs-lookup"><span data-stu-id="89d86-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="89d86-129">Orden de los eventos</span><span class="sxs-lookup"><span data-stu-id="89d86-129">Order of events</span></span>

<span data-ttu-id="89d86-130">Hay dos cadenas principales de eventos, en función de la entrada del usuario:</span><span class="sxs-lookup"><span data-stu-id="89d86-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="89d86-131">"Hold":</span><span class="sxs-lookup"><span data-stu-id="89d86-131">"Hold":</span></span>
    1. <span data-ttu-id="89d86-132">Mantenga pulsado:</span><span class="sxs-lookup"><span data-stu-id="89d86-132">Hold tap:</span></span>
        - <span data-ttu-id="89d86-133">iniciar _manipulación_</span><span class="sxs-lookup"><span data-stu-id="89d86-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="89d86-134">Mantenga pulsado más [allá de HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="89d86-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="89d86-135">start _Hold_</span><span class="sxs-lookup"><span data-stu-id="89d86-135">start _Hold_</span></span>
    1. <span data-ttu-id="89d86-136">Pulsación de versión:</span><span class="sxs-lookup"><span data-stu-id="89d86-136">Release tap:</span></span>
        - <span data-ttu-id="89d86-137">complete _Hold_</span><span class="sxs-lookup"><span data-stu-id="89d86-137">complete _Hold_</span></span>
        - <span data-ttu-id="89d86-138">Manipulación _completa_</span><span class="sxs-lookup"><span data-stu-id="89d86-138">complete _Manipulation_</span></span>

- <span data-ttu-id="89d86-139">"Mover":</span><span class="sxs-lookup"><span data-stu-id="89d86-139">"Move":</span></span>
    1. <span data-ttu-id="89d86-140">Mantenga pulsado:</span><span class="sxs-lookup"><span data-stu-id="89d86-140">Hold tap:</span></span>
        - <span data-ttu-id="89d86-141">iniciar _manipulación_</span><span class="sxs-lookup"><span data-stu-id="89d86-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="89d86-142">Mantenga pulsado más [allá de HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="89d86-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="89d86-143">start _Hold_</span><span class="sxs-lookup"><span data-stu-id="89d86-143">start _Hold_</span></span>
    1. <span data-ttu-id="89d86-144">Ir más allá [de NavigationStartThreshold:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)</span><span class="sxs-lookup"><span data-stu-id="89d86-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="89d86-145">cancelar _retención_</span><span class="sxs-lookup"><span data-stu-id="89d86-145">cancel _Hold_</span></span>
        - <span data-ttu-id="89d86-146">iniciar _navegación_</span><span class="sxs-lookup"><span data-stu-id="89d86-146">start _Navigation_</span></span>
    1. <span data-ttu-id="89d86-147">Pulsación de versión:</span><span class="sxs-lookup"><span data-stu-id="89d86-147">Release tap:</span></span>
        - <span data-ttu-id="89d86-148">Manipulación _completa_</span><span class="sxs-lookup"><span data-stu-id="89d86-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="89d86-149">navegación _completa_</span><span class="sxs-lookup"><span data-stu-id="89d86-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="89d86-150">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="89d86-150">Example scene</span></span>

<span data-ttu-id="89d86-151">En la **escena HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) se muestra cómo usar el puntero Result para generar un objeto en la ubicación de acceso.</span><span class="sxs-lookup"><span data-stu-id="89d86-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="89d86-152">El script (Assets/MRTK/Examples/Demos/HandTracking/Script) es una implementación de ejemplo para visualizar eventos de gestos a `GestureTester` través de GameObjects.</span><span class="sxs-lookup"><span data-stu-id="89d86-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="89d86-153">Las funciones de controlador cambian el color de los objetos de indicador y muestran el último evento registrado en objetos de texto de la escena.</span><span class="sxs-lookup"><span data-stu-id="89d86-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
