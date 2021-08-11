---
title: Estado de entrada
description: Documentación sobre los estados de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, InputState,
ms.openlocfilehash: 7d5e008ae3e43d227b90a563dd74e65a89527bd7ddf1720e26577042ce0d545f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228365"
---
# <a name="accessing-input-state-in-mrtk"></a>Acceso al estado de entrada en MRTK

Es posible consultar directamente el estado de todas las entradas en MRTK mediante la iteración de los controladores asociados a los orígenes de entrada. MRTK también proporciona métodos prácticos para acceder a la posición y rotación de los ojos, las manos, la cabeza y el controlador de movimiento.

Consulte la escena InputDataExample para obtener un ejemplo de consulta de entrada a través de la iteración sobre controladores y mediante la [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) clase .

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Ejemplo: Posición de acceso, rotación de la cabeza, las manos y los ojos en MRTK

La clase de MRTK proporciona métodos prácticos para acceder al rayo de la mano, al rayo de la cabeza, al rayo de la mirada con los ojos y a los rayos [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) del controlador de movimiento.

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Ejemplo: Posición de acceso, rotación de todos los controladores 6DOF activos en la escena

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
