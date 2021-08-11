---
title: Proveedor de ojo de seguimiento ocular
description: Documentación del proveedor eye gaze en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: 9a62bdba0bc4bb2985e6c2ffc4e8e66a8f867681a5e51c9e5f235b29f3baaf50
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193197"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Acceso a los datos de seguimiento ocular en el script de Unity

En este artículo se da por supuesto que tiene conocimientos para configurar el seguimiento ocular en una escena de MRTK (consulte Configuración básica de [MRTK para usar el seguimiento ocular).](eye-tracking-basic-setup.md)
Acceder a los datos de seguimiento ocular en un script MonoBehaviour es fácil. Simplemente use *CoreServices.InputSystem.EyeGazeProvider*.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

La configuración del seguimiento ocular en MRTK se configura a través de la [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaz . El [uso de CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) proporciona la implementación predeterminada del proveedor de mirada registrada en el kit de herramientas en tiempo de ejecución.
A continuación se `EyeGazeProvider` describen las propiedades útiles de .

- **IsEyeTrackingEnabled:** true si el usuario ha seleccionado usar el seguimiento ocular para la mirada.

- **IsEyeEyebrationValid:** indica si la calibración del seguimiento ocular del usuario es válida o no.
Devuelve "null", si el valor aún no ha recibido datos del sistema de seguimiento ocular.
Puede no ser válido porque el usuario omitió la calibración del seguimiento ocular.

- **IsEyeTrackingEnabledAndValid:** indica si los datos de seguimiento ocular actuales se usan actualmente para la mirada.

- **IsEyeTrackingDataValid:** true si hay datos de seguimiento ocular disponibles.
Es posible que no esté disponible debido a que se ha superado el tiempo de espera (debe ser sólido para que el usuario parpadee) o a la falta de hardware o permisos de seguimiento.
Consulte nuestro ejemplo [de notificación falta de calibración de](eye-tracking-is-user-calibrated.md) los ojos que explica cómo detectar si un usuario está calibrado con los ojos y mostrar una notificación adecuada.

- **GazeOrigin:** origen del rayo de mirada.
Tenga en cuenta que esto devolverá el origen *de* la mirada con la cabeza si "IsEyeGazeValid" es false.

- **GazeDirection:** dirección del rayo de mirada.
Esto devolverá la dirección *de la* mirada con la cabeza si "IsEyeGazeValid" es false.

- **HitInfo,** **HitPosition,** **HitNormal,** etc.: información sobre el destino que se mira actualmente.
De nuevo, `IsEyeGazeValid` si es false, esto se basará en la mirada con *la cabeza del* usuario.

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>Ejemplos de uso de CoreServices.InputSystem.EyeGazeProvider

Este es un ejemplo de [FollowEyeGaze.cs:](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)

- Obtenga el punto de un holograma que el usuario está viendo:

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- Mostrar un recurso visual a una distancia fija desde donde el usuario está buscando actualmente:

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>Consulte también

- [Información general sobre el seguimiento ocular de MRTK](eye-tracking-main.md)
- [Configuración del seguimiento ocular de MRTK](eye-tracking-basic-setup.md)
- [Calibración del seguimiento ocular de MRTK](eye-tracking-is-user-calibrated.md)
- [HoloLens 2 Documentación de seguimiento de los ojos](/windows/mixed-reality/eye-tracking)