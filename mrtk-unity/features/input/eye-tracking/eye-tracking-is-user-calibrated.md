---
title: Calibración de los ojos
description: Configuración de la calibración de los ojos del usuario en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking, Calibración,
ms.openlocfilehash: a2023a2d7f6a0254e8fef32f4faf09def956e94f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177205"
---
# <a name="eye-calibration"></a><span data-ttu-id="c0a6d-104">Calibración de los ojos</span><span class="sxs-lookup"><span data-stu-id="c0a6d-104">Eye calibration</span></span>

![Captura de pantalla de la notificación de calibración de los ojos](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="c0a6d-106">Información general</span><span class="sxs-lookup"><span data-stu-id="c0a6d-106">Overview</span></span>

<span data-ttu-id="c0a6d-107">Si el seguimiento de los ojos es una parte fundamental de la experiencia de la aplicación, es posible que desee asegurarse de que la calibración de los ojos del usuario es válida.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="c0a6d-108">La razón principal para que no sea válida es que el usuario ha decidido omitir la calibración del seguimiento de los ojos al colocar en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="c0a6d-109">En esta página se trata lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c0a6d-109">This page covers the following:</span></span>

- <span data-ttu-id="c0a6d-110">Describe cómo detectar que un usuario está calibrado con los ojos</span><span class="sxs-lookup"><span data-stu-id="c0a6d-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="c0a6d-111">Proporciona un ejemplo de cómo desencadenar una notificación de usuario para indicar al usuario que pase por la calibración de los ojos.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="c0a6d-112">Descartar automáticamente la notificación si la calibración de los ojos pasa a ser válida</span><span class="sxs-lookup"><span data-stu-id="c0a6d-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="c0a6d-113">Descartar manualmente la notificación si el usuario decide continuar sin calibración</span><span class="sxs-lookup"><span data-stu-id="c0a6d-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="c0a6d-114">Detección del estado de calibración de los ojos</span><span class="sxs-lookup"><span data-stu-id="c0a6d-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="c0a6d-115">La configuración de seguimiento de los ojos en MRTK se configura a través de la [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaz .</span><span class="sxs-lookup"><span data-stu-id="c0a6d-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="c0a6d-116">El [uso de CoreServices.InputSystem.EyeGazeProvider proporciona](eye-tracking-eye-gaze-provider.md) la implementación predeterminada del proveedor de mirada registrada en el kit de herramientas en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="c0a6d-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` devuelve un valor null si aún no hay información disponible del seguimiento `bool?` de los ojos.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="c0a6d-118">Una vez recibidos los datos, devolverá true o false para indicar que la calibración del seguimiento de los ojos del usuario es válida o no válida.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="c0a6d-119">Notificación de calibración de los ojos de ejemplo: paso a paso</span><span class="sxs-lookup"><span data-stu-id="c0a6d-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="c0a6d-120">Abra el paquete de ejemplo de seguimiento ocular de MRTK (Assets/MRTK/Examples/Demos/EyeTracking)</span><span class="sxs-lookup"><span data-stu-id="c0a6d-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="c0a6d-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span><span class="sxs-lookup"><span data-stu-id="c0a6d-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="c0a6d-122">Eche un _vistazo a EyeCheckbrationChecker:_</span><span class="sxs-lookup"><span data-stu-id="c0a6d-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="c0a6d-123">En esta escena, ya tenemos un ejemplo para detectar si el usuario actual está calibrado en el objeto de juego *_EyeObjectbrationChecker_*.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="c0a6d-124">Simplemente incluye algunas mallas de texto y tiene algunos desencadenadores adicionales para combinar la notificación de entrada y salida. Esto incluye aumentar lentamente su tamaño y opacidad en la activación.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="c0a6d-125">Una vez descartada la notificación, disminuirá lentamente su tamaño y se atenuará.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="c0a6d-126">Asociado al *_objeto de juego EyeCheckbrationChecker_* se encuentra el script [EyeCheckbrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) que expone dos eventos de Unity:</span><span class="sxs-lookup"><span data-stu-id="c0a6d-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="c0a6d-127">Estos eventos solo se desencadenarán si cambia el estado de calibración.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="c0a6d-128">Por lo tanto, si un usuario decide descartar la notificación, la notificación no se mostrará de nuevo hasta que</span><span class="sxs-lookup"><span data-stu-id="c0a6d-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="c0a6d-129">La aplicación se reinicia</span><span class="sxs-lookup"><span data-stu-id="c0a6d-129">The app gets restarted</span></span>
      - <span data-ttu-id="c0a6d-130">Se ha detectado un usuario válido y, a continuación, un nuevo usuario sin problemas ha puesto el dispositivo en</span><span class="sxs-lookup"><span data-stu-id="c0a6d-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="c0a6d-131">Para probar si las animaciones y los eventos se desencadenan correctamente, el script EyeCheckbrationChecker posee una `bool editorTestUserIsCalibrated` marca.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="c0a6d-132">Por ejemplo, cuando se ejecuta en el editor de Unity, se puede probar:</span><span class="sxs-lookup"><span data-stu-id="c0a6d-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="c0a6d-133">Si la notificación aparece automáticamente una vez que el estado de calibración cambia de true a false</span><span class="sxs-lookup"><span data-stu-id="c0a6d-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="c0a6d-134">Si descarta automáticamente la notificación de nuevo una vez que el estado cambia de false a true.</span><span class="sxs-lookup"><span data-stu-id="c0a6d-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="c0a6d-135">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c0a6d-135">See also</span></span>

- [<span data-ttu-id="c0a6d-136">Introducción al seguimiento de los ojos de MRTK</span><span class="sxs-lookup"><span data-stu-id="c0a6d-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="c0a6d-137">Configuración del seguimiento de los ojos de MRTK</span><span class="sxs-lookup"><span data-stu-id="c0a6d-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="c0a6d-138">Seguimiento de los ojos de MRTK mediante código</span><span class="sxs-lookup"><span data-stu-id="c0a6d-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="c0a6d-139">HoloLens 2 Documentación sobre el seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="c0a6d-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)
