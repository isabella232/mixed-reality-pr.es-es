---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717646"
---
# <a name="426"></a>[<span data-ttu-id="acd96-101">4.26</span><span class="sxs-lookup"><span data-stu-id="acd96-101">4.26</span></span>](#tab/426)

<span data-ttu-id="acd96-102">Para obtener los datos de los rayos de mano, debe usar la función get Motion Controller data de la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="acd96-102">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="acd96-103">La estructura devuelta contiene dos parámetros que se pueden usar para crear un rayo de mano: **posición de objetivo** y **rotación de objetivos**.</span><span class="sxs-lookup"><span data-stu-id="acd96-103">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="acd96-104">Estos parámetros forman un rayo dirigido por el codo.</span><span class="sxs-lookup"><span data-stu-id="acd96-104">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="acd96-105">Debe tomarlos y encontrar un holograma al que apunta.</span><span class="sxs-lookup"><span data-stu-id="acd96-105">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="acd96-106">A continuación se muestra un ejemplo de cómo determinar si un rayo de mano alcanza un widget y establece un resultado personalizado de aciertos:</span><span class="sxs-lookup"><span data-stu-id="acd96-106">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Plano de la función get Motion Controller Data](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[<span data-ttu-id="acd96-108">4.25</span><span class="sxs-lookup"><span data-stu-id="acd96-108">4.25</span></span>](#tab/425)

<span data-ttu-id="acd96-109">Para usar rayos de mano en blueprints, busque cualquiera de las acciones en **Windows Mixed Reality HMD**:</span><span class="sxs-lookup"><span data-stu-id="acd96-109">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Rayos de mano BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="acd96-111">Para tener acceso a ellos en C++, incluya `WindowsMixedRealityFunctionLibrary.h` en la parte superior del archivo de código que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="acd96-111">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="acd96-112">Enumeración</span><span class="sxs-lookup"><span data-stu-id="acd96-112">Enum</span></span>

<span data-ttu-id="acd96-113">También tiene acceso a los casos de entrada en **EHMDInputControllerButtons**, que se pueden usar en Blueprints:</span><span class="sxs-lookup"><span data-stu-id="acd96-113">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Botones del controlador de entrada](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="acd96-115">Para el acceso en C++, utilice la `EHMDInputControllerButtons` clase enum:</span><span class="sxs-lookup"><span data-stu-id="acd96-115">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="acd96-116">A continuación se muestra un desglose de los dos casos de enumeración aplicables:</span><span class="sxs-lookup"><span data-stu-id="acd96-116">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="acd96-117">**Select** : evento de selección desencadenada por el usuario.</span><span class="sxs-lookup"><span data-stu-id="acd96-117">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="acd96-118">Se desencadena en HoloLens 2 con la pulsación aérea, miran y confirman, o bien diciendo "Select" con [entrada de voz](../unreal-voice-input.md) habilitada.</span><span class="sxs-lookup"><span data-stu-id="acd96-118">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="acd96-119">**Agarre** : evento de agarre desencadenado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="acd96-119">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="acd96-120">Se desencadena en HoloLens 2 cerrando los dedos del usuario en un holograma.</span><span class="sxs-lookup"><span data-stu-id="acd96-120">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="acd96-121">Puede tener acceso al estado de seguimiento de la malla de mano en C++ a través de la `EHMDTrackingStatus` enumeración que se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="acd96-121">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="acd96-122">A continuación se muestra un desglose de los dos casos de enumeración aplicables:</span><span class="sxs-lookup"><span data-stu-id="acd96-122">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="acd96-123">**NotTracked** : la mano no es visible</span><span class="sxs-lookup"><span data-stu-id="acd96-123">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="acd96-124">**Seguimiento** : se realiza un seguimiento completo de la mano</span><span class="sxs-lookup"><span data-stu-id="acd96-124">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="acd96-125">Estructura</span><span class="sxs-lookup"><span data-stu-id="acd96-125">Struct</span></span>

<span data-ttu-id="acd96-126">El struct PointerPoseInfo puede proporcionarle información sobre los siguientes datos de la mano:</span><span class="sxs-lookup"><span data-stu-id="acd96-126">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="acd96-127">**Origin** : origen de la mano</span><span class="sxs-lookup"><span data-stu-id="acd96-127">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="acd96-128">**Dirección** : dirección de la mano</span><span class="sxs-lookup"><span data-stu-id="acd96-128">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="acd96-129">**Vertical** : Vector de la mano</span><span class="sxs-lookup"><span data-stu-id="acd96-129">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="acd96-130">**Orientación** : cuaternión de orientación</span><span class="sxs-lookup"><span data-stu-id="acd96-130">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="acd96-131">**Estado de seguimiento** : estado de seguimiento actual</span><span class="sxs-lookup"><span data-stu-id="acd96-131">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="acd96-132">Puede acceder a la estructura PointerPoseInfo a través de blueprints, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="acd96-132">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![El puntero representa la información BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="acd96-134">O con C++:</span><span class="sxs-lookup"><span data-stu-id="acd96-134">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="acd96-135">Functions</span><span class="sxs-lookup"><span data-stu-id="acd96-135">Functions</span></span>

<span data-ttu-id="acd96-136">Todas las funciones que se enumeran a continuación se pueden llamar en cada fotograma, lo que permite la supervisión continua.</span><span class="sxs-lookup"><span data-stu-id="acd96-136">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="acd96-137">**Obtener** información de la pose de puntero devuelve información completa sobre la dirección del rayo en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="acd96-137">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="acd96-138">Blueprint</span><span class="sxs-lookup"><span data-stu-id="acd96-138">Blueprint:</span></span>

![Obtener información de la repostura de puntero](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="acd96-140">C++:</span><span class="sxs-lookup"><span data-stu-id="acd96-140">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="acd96-141">**Se ha captado** devuelve true si la mano se ha captado en el fotograma actual.</span><span class="sxs-lookup"><span data-stu-id="acd96-141">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="acd96-142">Blueprint</span><span class="sxs-lookup"><span data-stu-id="acd96-142">Blueprint:</span></span>

![Se ha captado BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="acd96-144">C++:</span><span class="sxs-lookup"><span data-stu-id="acd96-144">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="acd96-145">Si **se selecciona, se** devuelve true si el usuario desencadenó SELECT en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="acd96-145">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="acd96-146">Blueprint</span><span class="sxs-lookup"><span data-stu-id="acd96-146">Blueprint:</span></span>

![Seleccione BP presionado](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="acd96-148">C++:</span><span class="sxs-lookup"><span data-stu-id="acd96-148">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="acd96-149">Si se **hace clic** en el botón, devuelve true si el evento o el botón se desencadena en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="acd96-149">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="acd96-150">Blueprint</span><span class="sxs-lookup"><span data-stu-id="acd96-150">Blueprint:</span></span>

![Clic en el botón BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="acd96-152">C++:</span><span class="sxs-lookup"><span data-stu-id="acd96-152">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="acd96-153">**Obtener estado de seguimiento del controlador** devuelve el estado de seguimiento en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="acd96-153">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="acd96-154">Blueprint</span><span class="sxs-lookup"><span data-stu-id="acd96-154">Blueprint:</span></span>

![Obtiene el estado de seguimiento del controlador BP](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="acd96-156">C++:</span><span class="sxs-lookup"><span data-stu-id="acd96-156">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```