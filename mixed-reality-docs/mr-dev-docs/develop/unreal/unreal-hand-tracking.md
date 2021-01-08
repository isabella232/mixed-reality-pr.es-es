---
title: Seguimiento de las manos en Unreal
description: Obtenga información sobre cómo usar la entrada, la postura, las mallas de mano y las animaciones de vínculos activos en aplicaciones de realidad mixta.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, seguimiento de mano, inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: e482c93233348325736d2c224788e9174c1f3b67
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010165"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="43972-104">Seguimiento de las manos en Unreal</span><span class="sxs-lookup"><span data-stu-id="43972-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="43972-105">El sistema de seguimiento de mano usa las palmeras y los dedos de una persona como entrada.</span><span class="sxs-lookup"><span data-stu-id="43972-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="43972-106">Están disponibles los datos sobre la posición y la rotación de cada dedo, la Palma completa y los gestos de mano.</span><span class="sxs-lookup"><span data-stu-id="43972-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="43972-107">A partir de 4,26 inreal, el seguimiento de mano se basa en el complemento HeadMountedDisplay inreal y usa una API común en todas las plataformas y dispositivos de XR.</span><span class="sxs-lookup"><span data-stu-id="43972-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="43972-108">La funcionalidad es la misma para los sistemas OpenXR y de realidad mixta de Windows.</span><span class="sxs-lookup"><span data-stu-id="43972-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="43972-109">Postura de mano</span><span class="sxs-lookup"><span data-stu-id="43972-109">Hand pose</span></span>

<span data-ttu-id="43972-110">La postura de mano permite realizar el seguimiento y el uso de las manos y los dedos de los usuarios como entrada, a los que se puede tener acceso tanto en Blueprints como en C++.</span><span class="sxs-lookup"><span data-stu-id="43972-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="43972-111">La API no real envía los datos como un sistema de coordenadas, con tics sincronizados con el motor inreal.</span><span class="sxs-lookup"><span data-stu-id="43972-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![Esqueleto manual](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="43972-113">Animación de vínculo activo a mano</span><span class="sxs-lookup"><span data-stu-id="43972-113">Hand Live Link Animation</span></span>

<span data-ttu-id="43972-114">Los planteamientos de mano se exponen a la animación mediante el [complemento de vínculo dinámico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="43972-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="43972-115">Si los complementos de Windows Mixed Reality y Live Link están habilitados:</span><span class="sxs-lookup"><span data-stu-id="43972-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="43972-116">Seleccione **window > Live Link** para abrir la ventana del editor de vínculos activos.</span><span class="sxs-lookup"><span data-stu-id="43972-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="43972-117">Seleccionar **origen** y habilitar el origen de seguimiento de la **mano mixta de Windows**</span><span class="sxs-lookup"><span data-stu-id="43972-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Origen de vínculo activo](images/unreal/live-link-source.png)

<span data-ttu-id="43972-119">Después de habilitar el origen y abrir un recurso de animación, expanda la sección **animación** en la pestaña **vista previa** de la escena, también puede ver opciones adicionales.</span><span class="sxs-lookup"><span data-stu-id="43972-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Animación de vínculos dinámicos](images/unreal/live-link-animation.png)

<span data-ttu-id="43972-121">La jerarquía de animaciones a mano es la misma que en `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="43972-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="43972-122">La animación se puede redestinar mediante **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span><span class="sxs-lookup"><span data-stu-id="43972-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Animación de vínculos en directo 2](images/unreal/live-link-animation2.png)

<span data-ttu-id="43972-124">También se puede crear una subclase en el editor:</span><span class="sxs-lookup"><span data-stu-id="43972-124">It can also be subclassed in the editor:</span></span>

![Reasignación de vínculos en directo](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="43972-126">Malla de mano</span><span class="sxs-lookup"><span data-stu-id="43972-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="43972-127">Malla de mano como geometría sometida a seguimiento</span><span class="sxs-lookup"><span data-stu-id="43972-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43972-128">La obtención de mallas manuales como geometría sometida a seguimiento en OpenXR requiere que se llame a **set usar malla de mano** con **geometría de seguimiento habilitada**.</span><span class="sxs-lookup"><span data-stu-id="43972-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="43972-129">Para habilitar ese modo, debe llamar a **set Use Hand Mesh** with **Enabled Tracking Geometry**:</span><span class="sxs-lookup"><span data-stu-id="43972-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![Plano del evento de inicio de reproducción de eventos conectado para establecer la función usar la malla de mano con el modo de geometría de seguimiento habilitado](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="43972-131">No es posible habilitar ambos modos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="43972-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="43972-132">Si habilita uno, el otro se deshabilitará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="43972-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="43972-133">Acceso a los datos de malla manual</span><span class="sxs-lookup"><span data-stu-id="43972-133">Accessing Hand Mesh Data</span></span>

![Malla de mano](images/unreal/hand-mesh.png)

<span data-ttu-id="43972-135">Para poder acceder a los datos de malla a mano, deberá:</span><span class="sxs-lookup"><span data-stu-id="43972-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="43972-136">Seleccione el recurso **ARSessionConfig** , expanda **configuración de ar-> configuración de asignación de mundo** y active la opción **generar datos de malla a partir de la geometría sometida a seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="43972-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="43972-137">A continuación se muestran los parámetros de malla predeterminados:</span><span class="sxs-lookup"><span data-stu-id="43972-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="43972-138">Usar datos de malla para la oclusión</span><span class="sxs-lookup"><span data-stu-id="43972-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="43972-139">Generar colisión para datos de malla</span><span class="sxs-lookup"><span data-stu-id="43972-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="43972-140">Generar malla de navegación para datos de malla</span><span class="sxs-lookup"><span data-stu-id="43972-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="43972-141">Representar datos de malla en el parámetro de trama: Debug que muestra la malla generada</span><span class="sxs-lookup"><span data-stu-id="43972-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="43972-142">Estos valores de parámetro se usan como la malla de asignación espacial y los valores predeterminados de la malla de mano.</span><span class="sxs-lookup"><span data-stu-id="43972-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="43972-143">Puede cambiarlos en cualquier momento en Blueprints o en el código de cualquier malla.</span><span class="sxs-lookup"><span data-stu-id="43972-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="43972-144">Referencia de la API de C++</span><span class="sxs-lookup"><span data-stu-id="43972-144">C++ API Reference</span></span>
<span data-ttu-id="43972-145">Use `EEARObjectClassification` para buscar valores de malla de mano en todos los objetos de los que se pueda realizar un seguimiento.</span><span class="sxs-lookup"><span data-stu-id="43972-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="43972-146">Se llama a los siguientes delegados cuando el sistema detecta cualquier objeto del que se pueden realizar acciones de seguimiento, incluida una malla de mano.</span><span class="sxs-lookup"><span data-stu-id="43972-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

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

<span data-ttu-id="43972-147">Asegúrese de que los controladores de delegado siguen la firma de la función siguiente:</span><span class="sxs-lookup"><span data-stu-id="43972-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="43972-148">Puede tener acceso a los datos de malla a través del  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="43972-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="43972-149">Referencia de la API de Blueprint</span><span class="sxs-lookup"><span data-stu-id="43972-149">Blueprint API Reference</span></span>

<span data-ttu-id="43972-150">Para trabajar con mallas manuales en Blueprints:</span><span class="sxs-lookup"><span data-stu-id="43972-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="43972-151">Agregar un componente **ARTrackableNotify** a un actor Blueprint</span><span class="sxs-lookup"><span data-stu-id="43972-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Notificación de ARTrackable](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="43972-153">Vaya al panel de **detalles** y expanda la sección **eventos** .</span><span class="sxs-lookup"><span data-stu-id="43972-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![ARTrackable notificar 2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="43972-155">Sobrescriba al agregar, actualizar o quitar la geometría sometida a seguimiento con los siguientes nodos en el gráfico de eventos:</span><span class="sxs-lookup"><span data-stu-id="43972-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![On ARTrackable Notify](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="43972-157">Visualización de la malla de mano en OpenXR</span><span class="sxs-lookup"><span data-stu-id="43972-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="43972-158">La forma recomendada de visualizar la malla de mano es usar el complemento XRVisualization de Epic junto con el [complemento de OpenXR de Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="43972-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="43972-159">Después, en el editor de Blueprint, debe usar la función de **configuración usar la malla de mano** del [complemento de Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) con **XRVisualization habilitado** como parámetro:</span><span class="sxs-lookup"><span data-stu-id="43972-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![Plano del evento Begin Play Connected para establecer la función usar la malla de mano con el modo xrvisualization habilitado](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="43972-161">Para administrar el proceso de representación, debe usar el **controlador de movimiento de representación** de XRVisualization:</span><span class="sxs-lookup"><span data-stu-id="43972-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![Plano de la función de datos de Get Motion Controller conectada a la función de controlador de movimiento de representación](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="43972-163">El resultado es:</span><span class="sxs-lookup"><span data-stu-id="43972-163">The result:</span></span>

![Imagen de la mano digital de una mano humana](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="43972-165">Si necesita algo más complicado, como dibujar una malla de mano con un sombreador personalizado, debe obtener las mallas como geometría sometida a seguimiento.</span><span class="sxs-lookup"><span data-stu-id="43972-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="43972-166">Rayos de las manos</span><span class="sxs-lookup"><span data-stu-id="43972-166">Hand rays</span></span>

<span data-ttu-id="43972-167">La obtención de la mano funciona para las interacciones de cierre, como la captura de objetos o la pulsación de botones.</span><span class="sxs-lookup"><span data-stu-id="43972-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="43972-168">Sin embargo, a veces es necesario trabajar con hologramas alejados de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="43972-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="43972-169">Esto puede hacerse con los rayos de mano, que se pueden usar como dispositivos señaladores en C++ y Blueprints.</span><span class="sxs-lookup"><span data-stu-id="43972-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="43972-170">Puede dibujar un rayo desde su mano hasta un punto lejano y, con algo de ayuda de un seguimiento de rayos no real, seleccione un holograma que, de otro modo, no estará disponible.</span><span class="sxs-lookup"><span data-stu-id="43972-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="43972-171">Dado que todos los resultados de la función cambian cada fotograma, todos ellos se pueden llamar.</span><span class="sxs-lookup"><span data-stu-id="43972-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="43972-172">Para obtener más información sobre las funciones puras e inpuras o que se puede llamar, vea el GUID de usuario de Blueprint en [Functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="43972-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="43972-173">Gestos</span><span class="sxs-lookup"><span data-stu-id="43972-173">Gestures</span></span>

<span data-ttu-id="43972-174">HoloLens 2 realiza el seguimiento de gestos espaciales, lo que significa que puede capturar esos gestos como entrada.</span><span class="sxs-lookup"><span data-stu-id="43972-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="43972-175">El seguimiento de gestos se basa en un modelo de suscripción.</span><span class="sxs-lookup"><span data-stu-id="43972-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="43972-176">Debe usar la función "configurar gestos" para indicar al dispositivo qué gestos desea seguir.  Puede encontrar más detalles sobre los movimientos en el documento de [uso básico de HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="43972-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="43972-177">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="43972-177">Next Development Checkpoint</span></span>

<span data-ttu-id="43972-178">Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="43972-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="43972-179">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="43972-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43972-180">Anclajes espaciales locales</span><span class="sxs-lookup"><span data-stu-id="43972-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="43972-181">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="43972-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43972-182">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="43972-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="43972-183">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="43972-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
