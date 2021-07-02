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
# <a name="gestures"></a>Gestos

Los gestos son eventos de entrada basados en manos humanas. Hay dos tipos de dispositivos que genera eventos de entrada de gestos en MRTK:

- Windows Mixed Reality dispositivos como HoloLens. Aquí se describen los movimientos de acercamiento ("Pulsación en el aire") y los gestos de pulsar y mantener presionados.

  Para obtener más información sobre los HoloLens, consulte la [documentación Windows Mixed Reality Gestures](/windows/mixed-reality/gestures).

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)ajusta el [XR de Unity. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) para consumir eventos de gesto de Unity desde HoloLens dispositivos.

- Dispositivos de pantalla táctil.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) ajusta la clase [Unity Touch que](https://docs.unity3d.com/ScriptReference/Touch.html) admite pantallas táctiles físicas.

Ambos orígenes de entrada usan el perfil _gesture Configuración_ para traducir los eventos Touch y Gesture de Unity respectivamente en acciones de entrada [de](input-actions.md)MRTK. Este perfil se puede encontrar en el perfil _de Configuración_ entrada.

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Eventos de gestos

Los eventos de gesto se reciben mediante la implementación de una de las interfaces del controlador de gestos: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vea la tabla de [controladores de eventos](input-events.md)).

Vea [Escena de ejemplo para](#example-scene) obtener una implementación de ejemplo de un controlador de eventos de gestos.

Al implementar la versión genérica, los eventos *OnGestureCompleted* y *OnGestureUpdated* pueden recibir datos con tipo de los siguientes tipos:

- `Vector2` - Gesto de posición 2D. Producido por pantallas táctiles para informar de su [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` - Gesto de posición 3D. Producido por HoloLens para informar de:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) de un evento de manipulación
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) de un evento de navegación
- `Quaternion` - Gesto de rotación 3D. Disponible para orígenes de entrada personalizados, pero no producidos actualmente por ninguno de los existentes.
- `MixedRealityPose` - Gesto combinado de posición y rotación 3D. Disponible para orígenes de entrada personalizados, pero no producidos actualmente por ninguno de los existentes.

## <a name="order-of-events"></a>Orden de los eventos

Hay dos cadenas principales de eventos, en función de la entrada del usuario:

- "Hold":
    1. Mantenga pulsado:
        - iniciar _manipulación_
    1. Mantenga pulsado más [allá de HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _Hold_
    1. Pulsación de versión:
        - complete _Hold_
        - Manipulación _completa_

- "Mover":
    1. Mantenga pulsado:
        - iniciar _manipulación_
    1. Mantenga pulsado más [allá de HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _Hold_
    1. Ir más allá [de NavigationStartThreshold:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)
        - cancelar _retención_
        - iniciar _navegación_
    1. Pulsación de versión:
        - Manipulación _completa_
        - navegación _completa_

## <a name="example-scene"></a>Escena de ejemplo

En la **escena HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) se muestra cómo usar el puntero Result para generar un objeto en la ubicación de acceso.

El script (Assets/MRTK/Examples/Demos/HandTracking/Script) es una implementación de ejemplo para visualizar eventos de gestos a `GestureTester` través de GameObjects. Las funciones de controlador cambian el color de los objetos de indicador y muestran el último evento registrado en objetos de texto de la escena.
