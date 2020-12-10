---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002706"
---
# <a name="425"></a>[<span data-ttu-id="8cb08-101">4.25</span><span class="sxs-lookup"><span data-stu-id="8cb08-101">4.25</span></span>](#tab/425)

<span data-ttu-id="8cb08-102">Puede encontrar la función Blueprint en en **entrada espacial de Windows Mixed Reality** y la función de C++ agregando `WindowsMixedRealitySpatialInputFunctionLibrary.h` en el archivo de código que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="8cb08-102">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Capturar movimientos](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="8cb08-104">Enumeración</span><span class="sxs-lookup"><span data-stu-id="8cb08-104">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="8cb08-105">Blueprint</span><span class="sxs-lookup"><span data-stu-id="8cb08-105">Blueprint:</span></span>

![Tipo de gesto](../images/unreal/gesture-type.png)

<span data-ttu-id="8cb08-107">C++:</span><span class="sxs-lookup"><span data-stu-id="8cb08-107">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="8cb08-108">Función</span><span class="sxs-lookup"><span data-stu-id="8cb08-108">Function</span></span>
<span data-ttu-id="8cb08-109">Puede habilitar y deshabilitar la captura de gestos con la `CaptureGestures` función.</span><span class="sxs-lookup"><span data-stu-id="8cb08-109">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="8cb08-110">Cuando un gesto habilitado activa eventos de entrada, la función devuelve `true` si la captura de gestos se realizó correctamente y se `false` produce un error.</span><span class="sxs-lookup"><span data-stu-id="8cb08-110">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="8cb08-111">Blueprint</span><span class="sxs-lookup"><span data-stu-id="8cb08-111">Blueprint:</span></span>

![Movimientos de captura BP](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="8cb08-113">C++:</span><span class="sxs-lookup"><span data-stu-id="8cb08-113">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="8cb08-114">Los siguientes son eventos clave, que puede encontrar en Blueprints y C++: ![ eventos de clave.](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="8cb08-114">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

![Eventos clave 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

# <a name="426"></a>[<span data-ttu-id="8cb08-116">4.26</span><span class="sxs-lookup"><span data-stu-id="8cb08-116">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="8cb08-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8cb08-117">Windows Mixed Reality</span></span>

![Plano del evento Begin Play Connected para configurar la función gestos](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="8cb08-119">Después, debe agregar código para suscribirse a los siguientes eventos:</span><span class="sxs-lookup"><span data-stu-id="8cb08-119">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="8cb08-120">![Plano de gestos de la retención de entrada espacial de Windows, TAP y izquierda gestos ](../images/unreal/key-events.png)
 ![ de manipulación de entradas espaciales de Windows en el panel detalles](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="8cb08-120">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="8cb08-121">OpenXR</span><span class="sxs-lookup"><span data-stu-id="8cb08-121">OpenXR</span></span>

<span data-ttu-id="8cb08-122">En OpenXR, se realiza un seguimiento de los eventos de gesto a través de la canalización de entrada.</span><span class="sxs-lookup"><span data-stu-id="8cb08-122">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="8cb08-123">Mediante la interacción con la mano, el dispositivo puede reconocer automáticamente los gestos de pulsar y mantener, pero no los demás.</span><span class="sxs-lookup"><span data-stu-id="8cb08-123">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="8cb08-124">Se denominan asignaciones de selección y control de OpenXRMsftHandInteraction.</span><span class="sxs-lookup"><span data-stu-id="8cb08-124">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="8cb08-125">No es necesario habilitar la suscripción. debe declarar los eventos en configuración del proyecto/motor/entrada, de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="8cb08-125">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![Captura de pantalla de las asignaciones de acción de OpenXR](../images/unreal-hand-tracking-img-12.png)
