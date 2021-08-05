---
title: Seguimiento de las manos
description: Documentación sobre cómo usar HandTracking en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, seguimiento de manos,
ms.openlocfilehash: f9d3b6b0f83a513b849aa27d464595ec8543bc30b64314c9a6e341cd6cb3a519
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189501"
---
# <a name="hand-tracking"></a>Seguimiento de las manos

## <a name="hand-tracking-profile"></a>Perfil de seguimiento de manos

El _perfil de seguimiento de mano_ se encuentra en el perfil del sistema de _entrada_. Contiene la configuración para personalizar la representación de la mano.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>Prefabs conjuntos

Los prefabs conjuntos se visualizan mediante prefabs simples. Las _uniones de la_ mano y el dedo índice son de especial importancia y tienen su propio prefab, mientras que el resto de las uniones comparten el mismo prefab. 

De forma predeterminada, los prefabs de las uniones de mano son primitivos geométricos simples. Estos se pueden reemplazar si se desea. Si no se especifica ningún elemento prefab, se crean [objetos GameObject vacíos](https://docs.unity3d.com/ScriptReference/GameObject.html) en su lugar.

> [!WARNING]
> Evite el uso de scripts complejos o una representación costosa en prefabs conjuntos, ya que los objetos de unión se transforman en cada fotograma y pueden tener un costo de rendimiento considerable.

Representación de conjunto de manos predeterminada |  Etiquetas de unión
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>Prefab de malla de mano

La malla manual se usa si el dispositivo de seguimiento de manos proporciona datos de malla totalmente definidos. La malla que se puede representar en el objeto prefab se reemplaza por los datos del dispositivo, por lo que una malla ficticia como un cubo es suficiente. El material del prefab se usa para la malla de mano.

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

La pantalla de malla de mano puede tener un impacto notable en el rendimiento; por este motivo, se puede deshabilitar completamente desactivando **la opción** Habilitar visualización de malla de mano.

## <a name="hand-visualization-settings"></a>Configuración de visualización manual

Las visualizaciones de la malla de mano y  las uniones de manos se pueden desactivar o activados a través de la opción Modos de visualización de malla de mano y modos de visualización conjunta *de* mano, respectivamente. Esta configuración es específica del modo de aplicación, lo que significa que es posible activar algunas características en el editor (para ver las uniones con la simulación en el editor, por ejemplo) mientras se desactivan las mismas características cuando se implementa en el dispositivo (en las compilaciones del reproductor).

Tenga en cuenta que, por lo general, se recomienda que la visualización de la unión de manos esté activada en el editor (para que la simulación en el editor muestre dónde están las uniones de mano) y que la visualización de la malla de mano y la de la mano estén desactivadas en el reproductor (porque suponen un impacto en el rendimiento).

## <a name="scripting"></a>Scripting

La posición y la rotación se pueden solicitar desde el sistema de entrada para cada una de las uniones de mano individuales como [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Como alternativa, el sistema permite el acceso [a GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) que siguen a las uniones. Esto puede ser útil si otro GameObject debe realizar un seguimiento continuo de una unión.

Las uniones disponibles se enumeran en [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) la enumeración.

> [!NOTE]
> El objeto conjunto se destruye cuando se pierde el seguimiento de las manos. Asegúrese de que los scripts que usan el objeto conjunto controle el `null` caso correctamente para evitar errores.

### <a name="accessing-a-given-hand-controller"></a>Acceso a un controlador de mano determinado

A menudo hay un controlador de mano específico disponible, por ejemplo, al controlar eventos de entrada. En este caso, los datos conjuntos se pueden solicitar directamente desde el dispositivo, mediante la [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interfaz .

#### <a name="polling-joint-pose-from-controller"></a>Sondeo de la posición conjunta del controlador

La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) función devuelve si la unión solicitada no está disponible por algún `false` motivo. En ese caso, la posición resultante será [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

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

#### <a name="joint-transform-from-hand-visualizer"></a>Transformación conjunta del visualizador de manos

Los objetos conjuntos se pueden solicitar desde el [visualizador del controlador](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).

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

### <a name="simplified-joint-data-access"></a>Acceso a datos conjunto simplificado

Si no se proporciona ningún controlador específico, se proporcionan clases de utilidad para un acceso cómodo a los datos conjuntos de mano. Estas funciones solicitan datos conjuntos del primer dispositivo de mano disponible actualmente.

#### <a name="polling-joint-pose-from-handjointutils"></a>Posición conjunta de sondeo de HandJointUtils

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) es una clase estática que consulta el primer dispositivo de mano activo.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>Transformación conjunta del servicio de mano conjunta

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantiene un conjunto persistente de [GameObjects para](https://docs.unity3d.com/ScriptReference/GameObject.html) realizar el seguimiento de las uniones.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>Eventos de seguimiento de manos

El sistema de entrada también proporciona eventos, si no es conveniente sondear datos de controladores directamente.

#### <a name="joint-events"></a>Eventos conjuntos

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) controla las actualizaciones de posiciones conjuntas.

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

#### <a name="mesh-events"></a>Eventos de malla

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) controla los cambios de la malla de mano articulada.

Tenga en cuenta que las mallas de mano no están habilitadas de forma predeterminada.

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

## <a name="known-issues"></a>Problemas conocidos

### <a name="net-native"></a>.NET Native

Actualmente hay un problema conocido con las compilaciones maestras mediante el back-end de .NET. En .NET Native, los punteros no se pueden `IInspectable` serializar de código nativo a administrado mediante `Marshal.GetObjectForIUnknown` . MrTK lo usa para obtener el objeto con el fin de recibir datos de manos `SpatialCoordinateSystem` y ojos de la plataforma.

Hemos proporcionado el origen dll como solución alternativa para este problema, en [el repositorio Mixed Reality Toolkit nativo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround). Siga las instrucciones del archivo LÉAME y copie los archivos binarios resultantes en una carpeta Plugins en los recursos de Unity. Después de eso, el script WindowsMixedRealityUtilities proporcionado en MRTK resolverá la solución alternativa.

Si desea crear su propio archivo DLL o incluir esta solución alternativa en una existente, el núcleo de la solución es:

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

Y su uso en el código de Unity de C#:

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
