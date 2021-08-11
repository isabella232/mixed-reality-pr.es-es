---
title: UsingGuide
description: describe los mecanismos clave y las API para configurar mediante programación el sistema de reconocimiento espacial
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204127"
---
# <a name="configuring-mesh-observers-via-code"></a>Configuración de observadores de malla mediante código

En este artículo se analizarán algunos de los mecanismos clave y las API para configurar mediante programación el sistema [de](spatial-awareness-getting-started.md) reconocimiento espacial y los proveedores de datos *de Mesh Observer* relacionados.

## <a name="accessing-mesh-observers"></a>Acceso a observadores de malla

Las clases mesh observer que implementan la interfaz proporcionan datos de malla específicos de la [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) plataforma al sistema de reconocimiento espacial. Se pueden configurar varios observadores en el perfil de reconocimiento espacial.

El acceso a los proveedores de datos del sistema de reconocimiento espacial es principalmente el mismo que para cualquier otro Mixed Reality Toolkit servicio. El servicio de reconocimiento espacial se debe convertir a la interfaz para acceder a través de las API, que luego se puede usar para acceder a los objetos de Mesh Observer directamente en [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) `GetDataProvider<T>` tiempo de ejecución.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

El `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` asistente simplifica este patrón de acceso, como se muestra a continuación.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>Inicio y detención de la observación de malla

Una de las tareas más comunes al tratar con el sistema de reconocimiento espacial es desactivar o activar dinámicamente la característica en tiempo de ejecución. Esto se realiza por observador a través de [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) las [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) API y .

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

Esta funcionalidad de código también se puede simplificar mediante el acceso directamente a través del sistema de reconocimiento espacial.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>Iniciar y detener toda la observación de malla

Por lo general, es conveniente iniciar o detener toda la observación de malla en la aplicación. Esto se puede lograr a través de las útiles API del sistema de reconocimiento espacial, [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) y [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) .

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>Enumeración y acceso a las mallas

El acceso a las mallas se puede realizar por observador y, a continuación, enumerarse a través de las mallas conocidas para ese observador de malla a través de la [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.

Si se ejecuta en el editor, se puede usar [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) para guardar el objeto en un archivo de `Mesh` recursos.

Si se ejecuta en el dispositivo, hay muchos complementos de comunidad y almacenamiento disponibles para serializar los datos en un tipo de archivo de `MeshFilter` modelo([ejemplo OBJ](http://wiki.unity3d.com/index.php/ObjExporter)).

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>Mostrar y ocultar la malla espacial

Es posible ocultar o mostrar mallas mediante programación con el código de ejemplo siguiente:

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>Registro para eventos de observación de malla

Los componentes pueden implementar `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` y, a continuación, registrarse con el sistema de reconocimiento espacial para recibir eventos de observación de malla.

El script (Assets/MRTK/Examples/Demos/SpatialAwareness/Scripts) es un ejemplo útil y un punto de partida para escuchar eventos `DemoSpatialMeshHandler` de Mesh Observer.

Este es un ejemplo simplificado del script *DemoSpatialMeshHandler* y la escucha de eventos de observación de malla.

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>Consulte también

- [Reconocimiento espacial Tareas iniciales](spatial-awareness-getting-started.md)
- [Configuración del observador de la malla de reconocimiento espacial](configuring-spatial-awareness-mesh-observer.md)
- [Documentación de Spatial Awareness API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
