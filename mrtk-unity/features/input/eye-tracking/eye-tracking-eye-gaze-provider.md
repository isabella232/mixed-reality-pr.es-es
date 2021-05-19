---
title: Proveedor de ojo de seguimiento ocular
description: Documentación del proveedor de Mirada con los ojos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144028"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Acceso a los datos de seguimiento de los ojos en el script de Unity

En este artículo se da por supuesto que uno tiene conocimientos para configurar el seguimiento de los ojos en una escena de MRTK (consulte Configuración básica de [MRTK para usar el seguimiento de los ojos).](eye-tracking-basic-setup.md)
El acceso a los datos de seguimiento de los ojos en un script MonoBehaviour es fácil. Simplemente use *CoreServices.InputSystem.EyeGazeProvider.*

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

La configuración de seguimiento de los ojos en MRTK se configura a través de la [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaz . El [uso de CoreServices.InputSystem.EyeGazeProvider proporciona](eye-tracking-eye-gaze-provider.md) la implementación predeterminada del proveedor de mirada registrada en el kit de herramientas en tiempo de ejecución.
A continuación se `EyeGazeProvider` describen las propiedades útiles de .

- **IsEyeTrackingEnabled:** true si el usuario ha seleccionado usar el seguimiento de los ojos para la mirada.

- **IsEyeEyebrationValid:** indica si la calibración del seguimiento de los ojos del usuario es válida o no.
Devuelve "null", si el valor aún no ha recibido datos del sistema de seguimiento de los ojos.
Puede no ser válido, porque el usuario omitió la calibración del seguimiento de los ojos.

- **IsEyeTrackingEnabledAndValid:** indica si los datos de seguimiento de los ojos actuales se usan actualmente para la mirada.

- **IsEyeTrackingDataValid:** true si hay datos de seguimiento de los ojos disponibles.
Puede que no esté disponible debido a que se ha superado el tiempo de espera (debe ser sólido para que el usuario parpadee) o a la falta de hardware o permisos de seguimiento.
Consulte nuestro ejemplo [de notificación falta de](eye-tracking-is-user-calibrated.md) calibración de los ojos que explica cómo detectar si un usuario está calibrado con los ojos y mostrar una notificación adecuada.

- **GazeOrigin:** origen del rayo de mirada.
Tenga en cuenta que esto devolverá el origen *de* la mirada con la cabeza si "IsEyeGazeValid" es false.

- **GazeDirection:** dirección del rayo de mirada.
Esto devolverá la dirección *de la* mirada con la cabeza si "IsEyeGazeValid" es false.

- **HitInfo,** **HitPosition,** **HitNormal,** etc.: información sobre el objetivo que se mira actualmente.
De nuevo, si es false, esto se basará en la mirada con la `IsEyeGazeValid` *cabeza del* usuario.

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>Ejemplos de uso de CoreServices.InputSystem.EyeGazeProvider

Este es un ejemplo de [FollowEyeGaze.cs:](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)

- Obtenga el punto de un holograma que el usuario está observando:

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

- [Información general sobre el seguimiento de los ojos de MRTK](eye-tracking-main.md)
- [Configuración del seguimiento de los ojos de MRTK](eye-tracking-basic-setup.md)
- [Calibración del seguimiento ocular de MRTK](eye-tracking-is-user-calibrated.md)
- [HoloLens 2 de seguimiento de los ojos](/windows/mixed-reality/eye-tracking)