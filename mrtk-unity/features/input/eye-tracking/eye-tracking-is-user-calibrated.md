---
title: Calibración de los ojos
description: Configuración de la calibración de los ojos del usuario en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking, Calibración,
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144004"
---
# <a name="eye-calibration"></a>Calibración de los ojos

![Captura de pantalla de la notificación de calibración de los ojos](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Información general

Si el seguimiento de los ojos es una parte fundamental de la experiencia de la aplicación, es posible que desee asegurarse de que la calibración de los ojos del usuario es válida.
La razón principal para que no sea válida es que el usuario ha decidido omitir la calibración del seguimiento de los ojos al colocar en el dispositivo.

En esta página se trata lo siguiente:

- Describe cómo detectar que un usuario está calibrado con los ojos
- Proporciona un ejemplo de cómo desencadenar una notificación de usuario para indicar al usuario que pase por la calibración de los ojos.
  - Descartar automáticamente la notificación si la calibración de los ojos es válida
  - Descartar manualmente la notificación si el usuario decide continuar sin calibración

### <a name="how-to-detect-the-eye-calibration-state"></a>Detección del estado de calibración de los ojos

La configuración del seguimiento de los ojos en MRTK se configura a través de la [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaz .

El [uso de CoreServices.InputSystem.EyeGazeProvider proporciona](eye-tracking-eye-gaze-provider.md) la implementación predeterminada del proveedor de mirada registrada en el kit de herramientas en tiempo de ejecución. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` devuelve un valor null si aún no hay información disponible del seguimiento `bool?` de los ojos.
Una vez recibidos los datos, devolverá true o false para indicar que la calibración del seguimiento de los ojos del usuario es válida o no válida.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Notificación de calibración de los ojos de ejemplo: paso a paso

1. Abra el paquete de ejemplo de seguimiento ocular de MRTK (Assets/MRTK/Examples/Demos/EyeTracking)

2. Load _EyeTrackingDemo-00-RootScene.unity_ scene

3. Eche un _vistazo a EyeCheckbrationChecker:_
   - En esta escena, ya tenemos un ejemplo para detectar si el usuario actual está calibrado en el objeto de juego *_EyeObjectBrationChecker_*.
Simplemente genera unas pocas mallas de texto y tiene algunos desencadenadores adicionales para combinar la notificación de entrada y salida. Esto incluye aumentar lentamente su tamaño y opacidad en la activación.
Una vez descartada la notificación, disminuirá lentamente su tamaño y se atenuará.

   - Asociado al *_objeto de juego EyeCheckbrationChecker_* se encuentra el script [EyeCheckbrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) que expone dos eventos de Unity:
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Estos eventos solo se desencadenarán si cambia el estado de calibración. Por lo tanto, si un usuario decide descartar la notificación, la notificación no se mostrará de nuevo hasta que
      - Se reinicia la aplicación
      - Se ha detectado un usuario válido y, a continuación, un nuevo usuario sin problemas ha puesto el dispositivo en

   - Para probar si las animaciones y los eventos se desencadenan correctamente, el script EyeCheckbrationChecker posee una `bool editorTestUserIsCalibrated` marca. Por ejemplo, cuando se ejecuta en el Editor de Unity, se puede probar:
      1. Si la notificación aparece automáticamente una vez que el estado de calibración cambia de true a false
      1. Si descarta automáticamente la notificación de nuevo una vez que el estado cambia de false a true.

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

## <a name="see-also"></a>Consulte también

- [Información general sobre el seguimiento ocular de MRTK](eye-tracking-main.md)
- [Configuración del seguimiento ocular de MRTK](eye-tracking-basic-setup.md)
- [Seguimiento de los ojos de MRTK mediante código](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2 de seguimiento ocular](/windows/mixed-reality/eye-tracking)