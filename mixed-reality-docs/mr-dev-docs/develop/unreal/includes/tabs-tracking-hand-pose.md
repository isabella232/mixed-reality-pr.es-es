---
ms.openlocfilehash: 9fdcbdfe115fa859081c28b768f9c213ac241d13
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002723"
---
# <a name="425"></a>[<span data-ttu-id="963e4-101">4.25</span><span class="sxs-lookup"><span data-stu-id="963e4-101">4.25</span></span>](#tab/425)

<span data-ttu-id="963e4-102">La `EWMRHandKeypoint` enumeración describe la jerarquía del hueso de la mano.</span><span class="sxs-lookup"><span data-stu-id="963e4-102">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="963e4-103">Puede encontrar cada keypoint de mano enumerado en los planos:</span><span class="sxs-lookup"><span data-stu-id="963e4-103">You can find each hand keypoint listed in your Blueprints:</span></span>

![Mano keypoint BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="963e4-105">La enumeración completa de C++ se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="963e4-105">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="963e4-106">Puede encontrar los valores numéricos de cada caso de enumeración en la tabla [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="963e4-106">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="963e4-107">Compatibilidad con el seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="963e4-107">Supporting Hand Tracking</span></span>

<span data-ttu-id="963e4-108">Puede usar el seguimiento de manos en Blueprints agregando **compatibilidad con** el seguimiento de la mano **> Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="963e4-108">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Seguimiento de mano BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="963e4-110">Esta función devuelve `true` si se admite el seguimiento manual en el dispositivo y `false` si el seguimiento de mano no está disponible.</span><span class="sxs-lookup"><span data-stu-id="963e4-110">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Admite el seguimiento de manos BP](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="963e4-112">C++:</span><span class="sxs-lookup"><span data-stu-id="963e4-112">C++:</span></span>

<span data-ttu-id="963e4-113">Incluya `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="963e4-113">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="963e4-114">Obtención del seguimiento manual</span><span class="sxs-lookup"><span data-stu-id="963e4-114">Getting Hand Tracking</span></span>

<span data-ttu-id="963e4-115">Puede usar **GetHandJointTransform** para devolver datos espaciales desde la mano.</span><span class="sxs-lookup"><span data-stu-id="963e4-115">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="963e4-116">Los datos se actualizan cada fotograma, pero si se encuentra dentro de un marco, los valores devueltos se almacenan en caché.</span><span class="sxs-lookup"><span data-stu-id="963e4-116">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="963e4-117">No se recomienda tener una lógica pesada en esta función por motivos de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="963e4-117">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![Obtener transformación Unión a mano](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="963e4-119">C++:</span><span class="sxs-lookup"><span data-stu-id="963e4-119">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="963e4-120">Este es un desglose de los parámetros de función de GetHandJointTransform:</span><span class="sxs-lookup"><span data-stu-id="963e4-120">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="963e4-121">**Mano** : puede ser la mano izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="963e4-121">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="963e4-122">**Keypoint** : el hueso de la mano.</span><span class="sxs-lookup"><span data-stu-id="963e4-122">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="963e4-123">**Transformación** : coordenadas y orientación de la base del hueso.</span><span class="sxs-lookup"><span data-stu-id="963e4-123">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="963e4-124">Puede solicitar la base del siguiente hueso para obtener los datos de transformación para el final de un hueso.</span><span class="sxs-lookup"><span data-stu-id="963e4-124">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="963e4-125">Un hueso de la sugerencia especial proporciona el final de distal.</span><span class="sxs-lookup"><span data-stu-id="963e4-125">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="963e4-126">\* \* Radio: radio de la base del hueso.</span><span class="sxs-lookup"><span data-stu-id="963e4-126">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="963e4-127">\* \* Valor devuelto: true si se realiza un seguimiento del hueso de este fotograma, false si no se realiza el seguimiento del hueso.</span><span class="sxs-lookup"><span data-stu-id="963e4-127">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>


# <a name="426"></a>[<span data-ttu-id="963e4-128">4.26</span><span class="sxs-lookup"><span data-stu-id="963e4-128">4.26</span></span>](#tab/426)

<span data-ttu-id="963e4-129">La jerarquía se describe mediante `EHandKeypoint` enum:</span><span class="sxs-lookup"><span data-stu-id="963e4-129">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Imagen de las opciones de keypoint bluprint](../images/hand-keypoint-bp.png)

<span data-ttu-id="963e4-131">Puede obtener todos estos datos de las manos de un usuario mediante la función **Get Motion Controller Data** .</span><span class="sxs-lookup"><span data-stu-id="963e4-131">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="963e4-132">Esa función devuelve una estructura **XRMotionControllerData** .</span><span class="sxs-lookup"><span data-stu-id="963e4-132">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="963e4-133">A continuación se muestra un script de plano de ejemplo que analiza la estructura XRMotionControllerData para obtener las ubicaciones de unión a mano y dibuja un sistema de coordenadas de depuración en cada ubicación de la Unión.</span><span class="sxs-lookup"><span data-stu-id="963e4-133">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![Plano de la función de datos de mirada conectada a la función de seguimiento de línea por canal](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="963e4-135">Es importante comprobar si la estructura es válida y es una mano.</span><span class="sxs-lookup"><span data-stu-id="963e4-135">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="963e4-136">De lo contrario, puede obtener un comportamiento indefinido en el acceso a las posiciones, las rotaciones y las matrices de radios.</span><span class="sxs-lookup"><span data-stu-id="963e4-136">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>
