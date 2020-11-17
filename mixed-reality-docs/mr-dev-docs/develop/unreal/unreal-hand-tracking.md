---
title: Seguimiento de las manos en Unreal
description: Explica cómo usar el seguimiento de manos en inreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, seguimiento de mano, inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 0a16a0291261277cb09e736e60b25f8ba71382e3
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679214"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="b7f88-104">Seguimiento de las manos en Unreal</span><span class="sxs-lookup"><span data-stu-id="b7f88-104">Hand tracking in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="b7f88-105">Información general</span><span class="sxs-lookup"><span data-stu-id="b7f88-105">Overview</span></span>

<span data-ttu-id="b7f88-106">El sistema de seguimiento de mano usa las palmeras y los dedos de una persona como entrada.</span><span class="sxs-lookup"><span data-stu-id="b7f88-106">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="b7f88-107">Puede obtener la posición y la rotación de cada dedo, toda la palma e incluso los gestos de mano que se usarán en el código.</span><span class="sxs-lookup"><span data-stu-id="b7f88-107">You can get the position and rotation of every finger, the entire palm, and even hand gestures to use in your code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="b7f88-108">Postura de mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-108">Hand Pose</span></span>

<span data-ttu-id="b7f88-109">La postura de mano le permite realizar un seguimiento de las manos y los dedos del usuario activo y usarlo como entrada, a la que puede acceder a través de Blueprints y C++.</span><span class="sxs-lookup"><span data-stu-id="b7f88-109">Hand pose lets you track the hands and fingers of the active user and use it as input, which you can access through Blueprints and C++.</span></span> <span data-ttu-id="b7f88-110">Puede encontrar más detalles técnicos en la API de [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) de la que no es real.</span><span class="sxs-lookup"><span data-stu-id="b7f88-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="b7f88-111">La API no real envía los datos como un sistema de coordenadas, con tics sincronizados con el motor inreal.</span><span class="sxs-lookup"><span data-stu-id="b7f88-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="b7f88-112">Descripción de la jerarquía del hueso</span><span class="sxs-lookup"><span data-stu-id="b7f88-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="b7f88-113">La `EWMRHandKeypoint` enumeración describe la jerarquía del hueso de la mano.</span><span class="sxs-lookup"><span data-stu-id="b7f88-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="b7f88-114">Puede encontrar cada keypoint de mano enumerado en los planos:</span><span class="sxs-lookup"><span data-stu-id="b7f88-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![Mano keypoint BP](images/hand-keypoint-bp.png)

<span data-ttu-id="b7f88-116">La enumeración completa de C++ se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="b7f88-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="b7f88-117">Puede encontrar los valores numéricos de cada caso de enumeración en la tabla [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="b7f88-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="b7f88-118">En la imagen siguiente se muestra el diseño de pose de mano completo con casos de enumeración coincidentes:</span><span class="sxs-lookup"><span data-stu-id="b7f88-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![Esqueleto manual](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="b7f88-120">Compatibilidad con el seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="b7f88-121">Puede usar el seguimiento de manos en Blueprints agregando **compatibilidad con** el seguimiento de la mano **> Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="b7f88-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Seguimiento de mano BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="b7f88-123">Esta función devuelve `true` si se admite el seguimiento manual en el dispositivo y `false` si el seguimiento de manos no está disponible.</span><span class="sxs-lookup"><span data-stu-id="b7f88-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking is not available.</span></span>

![Admite el seguimiento de manos BP](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="b7f88-125">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-125">C++:</span></span> 

<span data-ttu-id="b7f88-126">Incluya `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="b7f88-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="b7f88-127">Obtención del seguimiento manual</span><span class="sxs-lookup"><span data-stu-id="b7f88-127">Getting Hand Tracking</span></span>
<span data-ttu-id="b7f88-128">Puede usar **GetHandJointTransform** para devolver datos espaciales desde la mano.</span><span class="sxs-lookup"><span data-stu-id="b7f88-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="b7f88-129">Los datos se actualizan cada fotograma, pero si se encuentra dentro de un marco, los valores devueltos se almacenan en caché.</span><span class="sxs-lookup"><span data-stu-id="b7f88-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="b7f88-130">No se recomienda tener una lógica pesada en esta función por motivos de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="b7f88-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![Obtener transformación Unión a mano](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="b7f88-132">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="b7f88-133">Desglose de parámetros de función:</span><span class="sxs-lookup"><span data-stu-id="b7f88-133">Function parameter breakdown:</span></span>

* <span data-ttu-id="b7f88-134">**Mano** : es la mano izquierda o derecha del usuario</span><span class="sxs-lookup"><span data-stu-id="b7f88-134">**Hand** – an be the left or right hand of the user</span></span>
* <span data-ttu-id="b7f88-135">**Keypoint** : el hueso de la mano.</span><span class="sxs-lookup"><span data-stu-id="b7f88-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="b7f88-136">**Transformación** : coordenadas y orientación de la base del hueso.</span><span class="sxs-lookup"><span data-stu-id="b7f88-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="b7f88-137">Puede solicitar la base del siguiente hueso para obtener los datos de transformación para el final de un hueso.</span><span class="sxs-lookup"><span data-stu-id="b7f88-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="b7f88-138">Un hueso de la sugerencia especial proporciona el final de distal.</span><span class="sxs-lookup"><span data-stu-id="b7f88-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="b7f88-139">**Radio** : radio de la base del hueso.</span><span class="sxs-lookup"><span data-stu-id="b7f88-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="b7f88-140">**Valor devuelto** : true si se realiza un seguimiento del hueso de este fotograma, false si no se realiza el seguimiento del hueso.</span><span class="sxs-lookup"><span data-stu-id="b7f88-140">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="b7f88-141">Animación de vínculo activo a mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-141">Hand Live Link Animation</span></span>
<span data-ttu-id="b7f88-142">Los planteamientos de mano se exponen a la animación mediante el [complemento de vínculo dinámico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="b7f88-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="b7f88-143">Si los complementos de Windows Mixed Reality y Live Link están habilitados:</span><span class="sxs-lookup"><span data-stu-id="b7f88-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="b7f88-144">Seleccione **window > Live Link** para abrir la ventana del editor de vínculos activos.</span><span class="sxs-lookup"><span data-stu-id="b7f88-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="b7f88-145">Haga clic en **origen** y habilite el origen de seguimiento de la **mano mixta de Windows**</span><span class="sxs-lookup"><span data-stu-id="b7f88-145">Click **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Origen de vínculo activo](images/unreal/live-link-source.png)
 
<span data-ttu-id="b7f88-147">Después de habilitar el origen y abrir un recurso de animación, expanda la sección **animación** en la pestaña **vista previa** de la escena, también puede ver opciones adicionales (los detalles se encuentran en la documentación de Live Link real), ya que el complemento está en versión beta, el proceso puede cambiar más adelante.</span><span class="sxs-lookup"><span data-stu-id="b7f88-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options (the details are in Unreal’s Live Link documentation - as the plugin is in beta, the process may change later).</span></span>

![Animación de vínculos dinámicos](images/unreal/live-link-animation.png)
 
<span data-ttu-id="b7f88-149">La jerarquía de animaciones a mano es la misma que en `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="b7f88-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="b7f88-150">La animación se puede redestinar mediante **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span><span class="sxs-lookup"><span data-stu-id="b7f88-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Animación de vínculos en directo 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="b7f88-152">También se puede crear una subclase en el editor:</span><span class="sxs-lookup"><span data-stu-id="b7f88-152">It can also be subclassed in the editor:</span></span>

![Reasignación de vínculos en directo](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="b7f88-154">Acceso a los datos de malla manual</span><span class="sxs-lookup"><span data-stu-id="b7f88-154">Accessing Hand Mesh Data</span></span>

![Malla de mano](images/unreal/hand-mesh.png)

<span data-ttu-id="b7f88-156">Para poder acceder a los datos de malla a mano, deberá:</span><span class="sxs-lookup"><span data-stu-id="b7f88-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="b7f88-157">Seleccione el recurso **ARSessionConfig** , expanda **configuración de ar-> configuración de asignación de mundo** y active la opción **generar datos de malla a partir de la geometría sometida a seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="b7f88-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span> 

<span data-ttu-id="b7f88-158">A continuación se muestran los parámetros de malla predeterminados:</span><span class="sxs-lookup"><span data-stu-id="b7f88-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="b7f88-159">Usar datos de malla para la oclusión</span><span class="sxs-lookup"><span data-stu-id="b7f88-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="b7f88-160">Generar colisión para datos de malla</span><span class="sxs-lookup"><span data-stu-id="b7f88-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="b7f88-161">Generar malla de navegación para datos de malla</span><span class="sxs-lookup"><span data-stu-id="b7f88-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="b7f88-162">Representar datos de malla en el parámetro de trama: Debug que muestra la malla generada</span><span class="sxs-lookup"><span data-stu-id="b7f88-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="b7f88-163">Estos valores de parámetro se usan como la malla de asignación espacial y los valores predeterminados de la malla de mano.</span><span class="sxs-lookup"><span data-stu-id="b7f88-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="b7f88-164">Puede cambiarlos en cualquier momento en Blueprints o en el código de cualquier malla.</span><span class="sxs-lookup"><span data-stu-id="b7f88-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="b7f88-165">Referencia de la API de C++</span><span class="sxs-lookup"><span data-stu-id="b7f88-165">C++ API Reference</span></span> 
<span data-ttu-id="b7f88-166">Use `EEARObjectClassification` para buscar valores de malla de mano en todos los objetos de los que se pueda realizar un seguimiento.</span><span class="sxs-lookup"><span data-stu-id="b7f88-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="b7f88-167">Se llama a los siguientes delegados cuando el sistema detecta cualquier objeto del que se pueden realizar acciones de seguimiento, incluida una malla de mano.</span><span class="sxs-lookup"><span data-stu-id="b7f88-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="b7f88-168">Asegúrese de que los controladores de delegado siguen la firma de la función siguiente:</span><span class="sxs-lookup"><span data-stu-id="b7f88-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="b7f88-169">Puede tener acceso a los datos de malla a través del  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="b7f88-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="b7f88-170">Referencia de la API de Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-170">Blueprint API Reference</span></span>

<span data-ttu-id="b7f88-171">Para trabajar con mallas manuales en Blueprints:</span><span class="sxs-lookup"><span data-stu-id="b7f88-171">In order to work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="b7f88-172">Agregar un componente **ARTrackableNotify** a un actor Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Notificación de ARTrackable](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="b7f88-174">Vaya al panel de **detalles** y expanda la sección **eventos** .</span><span class="sxs-lookup"><span data-stu-id="b7f88-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![ARTrackable notificar 2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="b7f88-176">Sobrescriba al agregar, actualizar o quitar la geometría sometida a seguimiento con los siguientes nodos en el gráfico de eventos:</span><span class="sxs-lookup"><span data-stu-id="b7f88-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![On ARTrackable Notify](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="b7f88-178">Rayos de mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-178">Hand Rays</span></span>

<span data-ttu-id="b7f88-179">Puede usar un rayo de mano como dispositivo señalador en C++ y blueprints, que expone la API [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .</span><span class="sxs-lookup"><span data-stu-id="b7f88-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

<span data-ttu-id="b7f88-180">Es importante mencionar que, dado que los resultados de todas las funciones cambian cada fotograma, todos ellos se pueden llamar.</span><span class="sxs-lookup"><span data-stu-id="b7f88-180">It’s important to mention that since the results of all the functions change every frame, they're all made callable.</span></span> <span data-ttu-id="b7f88-181">Para obtener más información sobre las funciones puras e inpuras o que se puede llamar, consulte el GUID de usuario de Blueprint en [Functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure) .</span><span class="sxs-lookup"><span data-stu-id="b7f88-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="b7f88-182">Para usar rayos de mano en blueprints, busque cualquiera de las acciones en **Windows Mixed Reality HMD**:</span><span class="sxs-lookup"><span data-stu-id="b7f88-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Rayos de mano BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="b7f88-184">Para tener acceso a ellos en C++, incluya `WindowsMixedRealityFunctionLibrary.h` en la parte superior del archivo de código que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="b7f88-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="b7f88-185">Enumeración</span><span class="sxs-lookup"><span data-stu-id="b7f88-185">Enum</span></span>
<span data-ttu-id="b7f88-186">También tiene acceso a los casos de entrada en **EHMDInputControllerButtons**, que se pueden usar en Blueprints:</span><span class="sxs-lookup"><span data-stu-id="b7f88-186">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Botones del controlador de entrada](images/unreal/input-controller-buttons.png)

<span data-ttu-id="b7f88-188">Para el acceso en C++, utilice la `EHMDInputControllerButtons` clase enum:</span><span class="sxs-lookup"><span data-stu-id="b7f88-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="b7f88-189">A continuación se muestra un desglose de los dos casos de enumeración aplicables:</span><span class="sxs-lookup"><span data-stu-id="b7f88-189">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="b7f88-190">**Select** : evento de selección desencadenada por el usuario.</span><span class="sxs-lookup"><span data-stu-id="b7f88-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="b7f88-191">El evento se puede desencadenar en HoloLens 2 con la pulsación aérea, la función de pulsar y confirmar, o bien decir "seleccionar" con [entrada de voz](unreal-voice-input.md) habilitada.</span><span class="sxs-lookup"><span data-stu-id="b7f88-191">The event can be triggered in HoloLens 2 by air-tap, gaze and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="b7f88-192">**Agarre** : evento de agarre desencadenado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="b7f88-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="b7f88-193">Este evento se puede desencadenar en HoloLens 2 cerrando los dedos del usuario en un holograma.</span><span class="sxs-lookup"><span data-stu-id="b7f88-193">This event can be triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="b7f88-194">Puede tener acceso al estado de seguimiento de la malla de mano en C++ a través de la `EHMDTrackingStatus` enumeración que se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="b7f88-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="b7f88-195">A continuación se muestra un desglose de los dos casos de enumeración aplicables:</span><span class="sxs-lookup"><span data-stu-id="b7f88-195">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="b7f88-196">**NotTracked** : la mano no es visible</span><span class="sxs-lookup"><span data-stu-id="b7f88-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="b7f88-197">**Seguimiento** : se realiza un seguimiento completo de la mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="b7f88-198">Estructura</span><span class="sxs-lookup"><span data-stu-id="b7f88-198">Struct</span></span>
<span data-ttu-id="b7f88-199">El struct PointerPoseInfo puede proporcionarle información sobre los siguientes datos de la mano:</span><span class="sxs-lookup"><span data-stu-id="b7f88-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>
* <span data-ttu-id="b7f88-200">**Origin** : origen de la mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="b7f88-201">**Dirección** : dirección de la mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="b7f88-202">**Vertical** : Vector de la mano</span><span class="sxs-lookup"><span data-stu-id="b7f88-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="b7f88-203">**Orientación** : cuaternión de orientación</span><span class="sxs-lookup"><span data-stu-id="b7f88-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="b7f88-204">**Estado de seguimiento** : estado de seguimiento actual</span><span class="sxs-lookup"><span data-stu-id="b7f88-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="b7f88-205">Puede tener acceso a esto a través de blueprints, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="b7f88-205">You can access this through Blueprints, as shown below:</span></span>

![El puntero representa la información BP](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="b7f88-207">O con C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="b7f88-208">Funciones</span><span class="sxs-lookup"><span data-stu-id="b7f88-208">Functions</span></span>

<span data-ttu-id="b7f88-209">Todas las funciones que se enumeran a continuación se pueden llamar en cada fotograma, lo que permite la supervisión continua.</span><span class="sxs-lookup"><span data-stu-id="b7f88-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="b7f88-210">**Obtener** información de la pose de puntero devuelve información completa sobre la dirección del rayo en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="b7f88-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="b7f88-211">Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-211">Blueprint:</span></span>

![Obtener información de la repostura de puntero](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="b7f88-213">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="b7f88-214">**Se ha captado** devuelve true si la mano se ha captado en el fotograma actual.</span><span class="sxs-lookup"><span data-stu-id="b7f88-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="b7f88-215">Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-215">Blueprint:</span></span>

![Se ha captado BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="b7f88-217">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="b7f88-218">Si **se selecciona, se** devuelve true si el usuario desencadenó SELECT en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="b7f88-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="b7f88-219">Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-219">Blueprint:</span></span>

![Seleccione BP presionado](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="b7f88-221">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="b7f88-222">Si se **hace clic** en el botón, devuelve true si el evento o el botón se desencadena en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="b7f88-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="b7f88-223">Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-223">Blueprint:</span></span>

![Clic en el botón BP](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="b7f88-225">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="b7f88-226">**Obtener estado de seguimiento del controlador** devuelve el estado de seguimiento en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="b7f88-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="b7f88-227">Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-227">Blueprint:</span></span>

![Obtiene el estado de seguimiento del controlador BP](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="b7f88-229">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="b7f88-230">Gestos</span><span class="sxs-lookup"><span data-stu-id="b7f88-230">Gestures</span></span>

<span data-ttu-id="b7f88-231">Hololens 2 puede realizar el seguimiento de gestos espaciales, lo que significa que puede capturar esos gestos como entrada.</span><span class="sxs-lookup"><span data-stu-id="b7f88-231">The Hololens 2 can track spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="b7f88-232">Puede encontrar más detalles sobre los movimientos en el documento de [uso básico de HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="b7f88-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="b7f88-233">Puede encontrar la función Blueprint en en **entrada espacial de Windows Mixed Reality** y la función de C++ agregando `WindowsMixedRealitySpatialInputFunctionLibrary.h` en el archivo de código que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="b7f88-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Capturar movimientos](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="b7f88-235">Enumeración</span><span class="sxs-lookup"><span data-stu-id="b7f88-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="b7f88-236">Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-236">Blueprint:</span></span> 

![Tipo de gesto](images/unreal/gesture-type.png)

<span data-ttu-id="b7f88-238">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="b7f88-239">Función</span><span class="sxs-lookup"><span data-stu-id="b7f88-239">Function</span></span>
<span data-ttu-id="b7f88-240">Puede habilitar y deshabilitar la captura de gestos con la `CaptureGestures` función.</span><span class="sxs-lookup"><span data-stu-id="b7f88-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="b7f88-241">Cuando un gesto habilitado activa eventos de entrada, la función devuelve `true` si la captura de gestos se realizó correctamente y se `false` produce un error.</span><span class="sxs-lookup"><span data-stu-id="b7f88-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="b7f88-242">Blueprint</span><span class="sxs-lookup"><span data-stu-id="b7f88-242">Blueprint:</span></span>

![Movimientos de captura BP](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="b7f88-244">C++:</span><span class="sxs-lookup"><span data-stu-id="b7f88-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="b7f88-245">Los siguientes son eventos clave, que puede encontrar en Blueprints y C++: ![ eventos de clave.](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="b7f88-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![Eventos clave 2](images/unreal/key-events2.png)
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

## <a name="next-development-checkpoint"></a><span data-ttu-id="b7f88-247">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="b7f88-247">Next Development Checkpoint</span></span>

<span data-ttu-id="b7f88-248">Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="b7f88-248">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b7f88-249">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="b7f88-249">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7f88-250">Anclajes espaciales locales</span><span class="sxs-lookup"><span data-stu-id="b7f88-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="b7f88-251">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="b7f88-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7f88-252">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="b7f88-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="b7f88-253">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="b7f88-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>