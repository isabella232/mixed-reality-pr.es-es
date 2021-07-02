---
title: Seguimiento de las manos
description: Documentación sobre cómo usar HandTracking en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, seguimiento de manos,
ms.openlocfilehash: 68e936cb4121027008f37aae72496fe59445b636
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176897"
---
# <a name="hand-tracking"></a><span data-ttu-id="a6799-104">Seguimiento de las manos</span><span class="sxs-lookup"><span data-stu-id="a6799-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="a6799-105">Perfil de seguimiento de manos</span><span class="sxs-lookup"><span data-stu-id="a6799-105">Hand tracking profile</span></span>

<span data-ttu-id="a6799-106">El _perfil de seguimiento de mano_ se encuentra en el perfil del sistema de _entrada_.</span><span class="sxs-lookup"><span data-stu-id="a6799-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="a6799-107">Contiene la configuración para personalizar la representación de la mano.</span><span class="sxs-lookup"><span data-stu-id="a6799-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="a6799-108">Prefabs conjuntos</span><span class="sxs-lookup"><span data-stu-id="a6799-108">Joint prefabs</span></span>

<span data-ttu-id="a6799-109">Los prefabs conjuntos se visualizan mediante prefabs simples.</span><span class="sxs-lookup"><span data-stu-id="a6799-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="a6799-110">Las _uniones de la_ mano y el dedo índice son de especial importancia y tienen su propio prefab, mientras que el resto de las uniones comparten el mismo prefab. </span><span class="sxs-lookup"><span data-stu-id="a6799-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="a6799-111">De forma predeterminada, los elementos prefabs de las uniones de mano son primitivos geométricos simples.</span><span class="sxs-lookup"><span data-stu-id="a6799-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="a6799-112">Se pueden reemplazar si se desea.</span><span class="sxs-lookup"><span data-stu-id="a6799-112">These can be replaced if desired.</span></span> <span data-ttu-id="a6799-113">Si no se especifica ningún elemento prefab, se crean [objetos GameObject vacíos](https://docs.unity3d.com/ScriptReference/GameObject.html) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="a6799-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="a6799-114">Evite el uso de scripts complejos o una representación costosa en prefabs conjuntos, ya que los objetos de unión se transforman en cada fotograma y pueden tener un costo de rendimiento considerable.</span><span class="sxs-lookup"><span data-stu-id="a6799-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="a6799-115">Representación de conjunto de manos predeterminada</span><span class="sxs-lookup"><span data-stu-id="a6799-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="a6799-116">Etiquetas de unión</span><span class="sxs-lookup"><span data-stu-id="a6799-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="a6799-117">Prefab de malla de mano</span><span class="sxs-lookup"><span data-stu-id="a6799-117">Hand mesh prefab</span></span>

<span data-ttu-id="a6799-118">La malla manual se usa si el dispositivo de seguimiento de manos proporciona datos de malla totalmente definidos.</span><span class="sxs-lookup"><span data-stu-id="a6799-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="a6799-119">La malla que se puede representar en el objeto prefab se reemplaza por los datos del dispositivo, por lo que una malla ficticia como un cubo es suficiente.</span><span class="sxs-lookup"><span data-stu-id="a6799-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="a6799-120">El material del prefab se usa para la malla de mano.</span><span class="sxs-lookup"><span data-stu-id="a6799-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="a6799-121">La pantalla de malla de mano puede tener un impacto notable en el rendimiento; por esta razón, se puede deshabilitar completamente desactivando **la opción Habilitar** visualización de malla de mano.</span><span class="sxs-lookup"><span data-stu-id="a6799-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="a6799-122">Configuración de visualización manual</span><span class="sxs-lookup"><span data-stu-id="a6799-122">Hand visualization settings</span></span>

<span data-ttu-id="a6799-123">Las visualizaciones de la malla de mano y  las uniones de manos se pueden desactivar o activados a través de la opción Modos de visualización de malla de mano y modos de visualización conjunta *de* mano, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a6799-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="a6799-124">Esta configuración es específica del modo de aplicación, lo que significa que es posible activar algunas características en el editor (para ver las uniones con la simulación en el editor, por ejemplo) mientras se desactivan las mismas características cuando se implementa en el dispositivo (en las compilaciones del reproductor).</span><span class="sxs-lookup"><span data-stu-id="a6799-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="a6799-125">Tenga en cuenta que, por lo general, se recomienda que la visualización de la unión de manos esté activada en el editor (para que la simulación en el editor muestre dónde están las uniones de mano) y que la visualización de la malla de mano y la de la mano estén desactivadas en el reproductor (porque suponen un impacto en el rendimiento).</span><span class="sxs-lookup"><span data-stu-id="a6799-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="a6799-126">Scripting</span><span class="sxs-lookup"><span data-stu-id="a6799-126">Scripting</span></span>

<span data-ttu-id="a6799-127">La posición y la rotación se pueden solicitar desde el sistema de entrada para cada una de las uniones de mano individuales como [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="a6799-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="a6799-128">Como alternativa, el sistema permite el acceso [a GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) que siguen a las uniones.</span><span class="sxs-lookup"><span data-stu-id="a6799-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="a6799-129">Esto puede ser útil si otro GameObject debe realizar un seguimiento continuo de una unión.</span><span class="sxs-lookup"><span data-stu-id="a6799-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="a6799-130">Las uniones disponibles se enumeran en [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) la enumeración.</span><span class="sxs-lookup"><span data-stu-id="a6799-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="a6799-131">El objeto conjunto se destruye cuando se pierde el seguimiento de las manos.</span><span class="sxs-lookup"><span data-stu-id="a6799-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="a6799-132">Asegúrese de que los scripts que usan el objeto conjunto controle el `null` caso correctamente para evitar errores.</span><span class="sxs-lookup"><span data-stu-id="a6799-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="a6799-133">Acceso a un controlador de mano determinado</span><span class="sxs-lookup"><span data-stu-id="a6799-133">Accessing a given hand controller</span></span>

<span data-ttu-id="a6799-134">A menudo hay un controlador de mano específico disponible, por ejemplo, al controlar eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="a6799-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="a6799-135">En este caso, los datos conjuntos se pueden solicitar directamente desde el dispositivo, mediante la [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interfaz .</span><span class="sxs-lookup"><span data-stu-id="a6799-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="a6799-136">Sondeo de la posición conjunta del controlador</span><span class="sxs-lookup"><span data-stu-id="a6799-136">Polling joint pose from controller</span></span>

<span data-ttu-id="a6799-137">La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) función devuelve si la unión solicitada no está disponible por algún `false` motivo.</span><span class="sxs-lookup"><span data-stu-id="a6799-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="a6799-138">En ese caso, la posición resultante será [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .</span><span class="sxs-lookup"><span data-stu-id="a6799-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="a6799-139">Transformación conjunta del visualizador de manos</span><span class="sxs-lookup"><span data-stu-id="a6799-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="a6799-140">Los objetos conjuntos se pueden solicitar desde el [visualizador del controlador](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span><span class="sxs-lookup"><span data-stu-id="a6799-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a><span data-ttu-id="a6799-141">Acceso a datos conjunto simplificado</span><span class="sxs-lookup"><span data-stu-id="a6799-141">Simplified joint data access</span></span>

<span data-ttu-id="a6799-142">Si no se proporciona ningún controlador específico, se proporcionan clases de utilidad para un acceso cómodo a los datos conjuntos de mano.</span><span class="sxs-lookup"><span data-stu-id="a6799-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="a6799-143">Estas funciones solicitan datos conjuntos del primer dispositivo de mano disponible actualmente.</span><span class="sxs-lookup"><span data-stu-id="a6799-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="a6799-144">Sondeo de la posición conjunta de HandJointUtils</span><span class="sxs-lookup"><span data-stu-id="a6799-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="a6799-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) es una clase estática que consulta el primer dispositivo de mano activo.</span><span class="sxs-lookup"><span data-stu-id="a6799-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="a6799-146">Transformación conjunta del servicio de mano conjunta</span><span class="sxs-lookup"><span data-stu-id="a6799-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="a6799-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantiene un conjunto persistente de [GameObjects para](https://docs.unity3d.com/ScriptReference/GameObject.html) realizar el seguimiento de las uniones.</span><span class="sxs-lookup"><span data-stu-id="a6799-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="a6799-148">Eventos de seguimiento de manos</span><span class="sxs-lookup"><span data-stu-id="a6799-148">Hand tracking events</span></span>

<span data-ttu-id="a6799-149">El sistema de entrada también proporciona eventos, si no es conveniente sondear datos de controladores directamente.</span><span class="sxs-lookup"><span data-stu-id="a6799-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="a6799-150">Eventos conjuntos</span><span class="sxs-lookup"><span data-stu-id="a6799-150">Joint events</span></span>

<span data-ttu-id="a6799-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) controla las actualizaciones de posiciones conjuntas.</span><span class="sxs-lookup"><span data-stu-id="a6799-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a><span data-ttu-id="a6799-152">Eventos de malla</span><span class="sxs-lookup"><span data-stu-id="a6799-152">Mesh events</span></span>

<span data-ttu-id="a6799-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) controla los cambios de la malla de mano articulada.</span><span class="sxs-lookup"><span data-stu-id="a6799-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="a6799-154">Tenga en cuenta que las mallas de mano no están habilitadas de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a6799-154">Note that hand meshes are not enabled by default.</span></span>

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a><span data-ttu-id="a6799-155">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="a6799-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="a6799-156">.NET Native</span><span class="sxs-lookup"><span data-stu-id="a6799-156">.NET Native</span></span>

<span data-ttu-id="a6799-157">Actualmente hay un problema conocido con las compilaciones maestras mediante el back-end de .NET.</span><span class="sxs-lookup"><span data-stu-id="a6799-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="a6799-158">En .NET Native, los punteros no se pueden `IInspectable` serializar de código nativo a administrado mediante `Marshal.GetObjectForIUnknown` .</span><span class="sxs-lookup"><span data-stu-id="a6799-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="a6799-159">MrTK lo usa para obtener el objeto con el fin de recibir datos de manos `SpatialCoordinateSystem` y ojos de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="a6799-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="a6799-160">Hemos proporcionado el origen dll como solución alternativa para este problema, en [el repositorio Mixed Reality Toolkit nativo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span><span class="sxs-lookup"><span data-stu-id="a6799-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="a6799-161">Siga las instrucciones del archivo LÉAME y copie los archivos binarios resultantes en una carpeta Plugins en los recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6799-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="a6799-162">Después de eso, el script WindowsMixedRealityUtilities proporcionado en MRTK resolverá la solución alternativa.</span><span class="sxs-lookup"><span data-stu-id="a6799-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="a6799-163">Si desea crear su propio archivo DLL o incluir esta solución alternativa en una existente, el núcleo de la solución es:</span><span class="sxs-lookup"><span data-stu-id="a6799-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="a6799-164">Y su uso en el código de Unity de C#:</span><span class="sxs-lookup"><span data-stu-id="a6799-164">And its use in your C# Unity code:</span></span>

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
