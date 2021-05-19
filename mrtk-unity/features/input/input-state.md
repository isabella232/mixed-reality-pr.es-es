---
title: Estado de entrada
description: Documentación sobre los estados de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, InputState,
ms.openlocfilehash: 4c1bd115c63e25decf73c082546e75b0f276a7ef
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145257"
---
# <a name="accessing-input-state-in-mrtk"></a>Acceso al estado de entrada en MRTK

Es posible consultar directamente el estado de todas las entradas en MRTK mediante la iteración sobre los controladores asociados a los orígenes de entrada. MRTK también proporciona métodos prácticos para acceder a la posición y rotación de los ojos, las manos, la cabeza y el controlador de movimiento.

Consulte la escena InputDataExample para obtener un ejemplo de consulta de entrada tanto a través de la iteración sobre los controladores como mediante la [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) clase .

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Ejemplo: Posición de acceso, rotación de la cabeza, las manos y los ojos en MRTK

La clase de MRTK proporciona métodos prácticos para acceder a los rayos de la mano, los rayos de la cabeza, los rayos de mirada de los ojos y los rayos [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) del controlador de movimiento.

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Ejemplo: Posición de acceso, rotación de los controladores 6DOF activos en la escena

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>Consulte también

- [InputEvents](input-events.md)
- [Punteros](pointers.md)
- [HandTracking](hand-tracking.md)
