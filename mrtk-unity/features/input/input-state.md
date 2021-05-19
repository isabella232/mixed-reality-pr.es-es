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
# <a name="accessing-input-state-in-mrtk"></a><span data-ttu-id="54664-104">Acceso al estado de entrada en MRTK</span><span class="sxs-lookup"><span data-stu-id="54664-104">Accessing input state in MRTK</span></span>

<span data-ttu-id="54664-105">Es posible consultar directamente el estado de todas las entradas en MRTK mediante la iteración sobre los controladores asociados a los orígenes de entrada.</span><span class="sxs-lookup"><span data-stu-id="54664-105">It's possible to directly query the state of all inputs in MRTK by iterating over the controllers attached to the input sources.</span></span> <span data-ttu-id="54664-106">MRTK también proporciona métodos prácticos para acceder a la posición y rotación de los ojos, las manos, la cabeza y el controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="54664-106">MRTK also provides convenience methods for accessing the position and rotation of the eyes, hands, head, and motion controller.</span></span>

<span data-ttu-id="54664-107">Consulte la escena InputDataExample para obtener un ejemplo de consulta de entrada tanto a través de la iteración sobre los controladores como mediante la [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) clase .</span><span class="sxs-lookup"><span data-stu-id="54664-107">See the InputDataExample scene for an example of querying input both via iterating over controllers, and by using the [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class.</span></span>

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a><span data-ttu-id="54664-108">Ejemplo: Posición de acceso, rotación de la cabeza, las manos y los ojos en MRTK</span><span class="sxs-lookup"><span data-stu-id="54664-108">Example: Access position, rotation of head, hands, eyes in MRTK</span></span>

<span data-ttu-id="54664-109">La clase de MRTK proporciona métodos prácticos para acceder a los rayos de la mano, los rayos de la cabeza, los rayos de mirada de los ojos y los rayos [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="54664-109">MRTK's [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class provides convenience methods for accessing the hand ray, head ray, eye gaze ray, and motion controller rays.</span></span>

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a><span data-ttu-id="54664-110">Ejemplo: Posición de acceso, rotación de los controladores 6DOF activos en la escena</span><span class="sxs-lookup"><span data-stu-id="54664-110">Example: Access position, rotation of all 6DOF controllers active in scene</span></span>

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

## <a name="see-also"></a><span data-ttu-id="54664-111">Consulte también</span><span class="sxs-lookup"><span data-stu-id="54664-111">See also</span></span>

- [<span data-ttu-id="54664-112">InputEvents</span><span class="sxs-lookup"><span data-stu-id="54664-112">InputEvents</span></span>](input-events.md)
- [<span data-ttu-id="54664-113">Punteros</span><span class="sxs-lookup"><span data-stu-id="54664-113">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="54664-114">HandTracking</span><span class="sxs-lookup"><span data-stu-id="54664-114">HandTracking</span></span>](hand-tracking.md)
