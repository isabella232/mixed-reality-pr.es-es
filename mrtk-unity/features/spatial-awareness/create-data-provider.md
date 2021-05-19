---
title: Creación de un proveedor de datos de reconocimiento espacial
description: describe cómo crear proveedores de datos personalizados en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145154"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="e03d6-104">Creación de un proveedor de datos del sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="e03d6-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="e03d6-105">El sistema de reconocimiento espacial es un sistema extensible para proporcionar a las aplicaciones datos sobre entornos reales.</span><span class="sxs-lookup"><span data-stu-id="e03d6-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="e03d6-106">Para agregar compatibilidad con una nueva plataforma de hardware o una nueva forma de datos de reconocimiento espacial, es posible que se requiera un proveedor de datos personalizado.</span><span class="sxs-lookup"><span data-stu-id="e03d6-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="e03d6-107">En este artículo se describe cómo crear proveedores de [datos](../../architecture/systems-extensions-providers.md)personalizados, también denominados observadores espaciales, para el sistema de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="e03d6-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="e03d6-108">El código de ejemplo que se muestra aquí es de la implementación de clase , que es útil para cargar datos [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [de malla 3D en el editor](spatial-object-mesh-observer.md).</span><span class="sxs-lookup"><span data-stu-id="e03d6-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e03d6-109">El código fuente completo usado en este ejemplo se puede encontrar en la `Assets/MRTK/Providers/ObjectMeshObserver` carpeta .</span><span class="sxs-lookup"><span data-stu-id="e03d6-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="e03d6-110">Espacio de nombres y estructura de carpetas</span><span class="sxs-lookup"><span data-stu-id="e03d6-110">Namespace and folder structure</span></span>

<span data-ttu-id="e03d6-111">Los proveedores de datos se pueden distribuir de una de estas dos maneras:</span><span class="sxs-lookup"><span data-stu-id="e03d6-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="e03d6-112">Complementos de terceros</span><span class="sxs-lookup"><span data-stu-id="e03d6-112">Third party add-ons</span></span>
1. <span data-ttu-id="e03d6-113">Parte de Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="e03d6-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="e03d6-114">El proceso de aprobación de envíos de nuevos proveedores de datos a MRTK variará caso por caso y se comunicará en el momento de la propuesta inicial.</span><span class="sxs-lookup"><span data-stu-id="e03d6-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="e03d6-115">Las propuestas se pueden enviar mediante la creación de un nuevo problema [ *de tipo de solicitud* de características](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="e03d6-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="e03d6-116">Complemento de terceros</span><span class="sxs-lookup"><span data-stu-id="e03d6-116">Third party add-on</span></span>

<span data-ttu-id="e03d6-117">**Espacio de nombres**</span><span class="sxs-lookup"><span data-stu-id="e03d6-117">**Namespace**</span></span>

<span data-ttu-id="e03d6-118">Los proveedores de datos deben tener un espacio de nombres para mitigar posibles conflictos de nombres.</span><span class="sxs-lookup"><span data-stu-id="e03d6-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="e03d6-119">Se recomienda que el espacio de nombres incluya los siguientes componentes.</span><span class="sxs-lookup"><span data-stu-id="e03d6-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="e03d6-120">Nombre de la empresa que genera el complemento</span><span class="sxs-lookup"><span data-stu-id="e03d6-120">Company name producing the add-on</span></span>
- <span data-ttu-id="e03d6-121">Área de función</span><span class="sxs-lookup"><span data-stu-id="e03d6-121">Feature area</span></span>

<span data-ttu-id="e03d6-122">Por ejemplo, un proveedor de datos de reconocimiento espacial creado y enviado por la empresa Contoso puede ser *"Contoso.MixedReality.Toolkit.SpatialAwareness".*</span><span class="sxs-lookup"><span data-stu-id="e03d6-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="e03d6-123">**Estructura de carpetas**</span><span class="sxs-lookup"><span data-stu-id="e03d6-123">**Folder structure**</span></span>

<span data-ttu-id="e03d6-124">Se recomienda retrasar el código fuente de los proveedores de datos en una jerarquía de carpetas, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="e03d6-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Ejemplo de estructura de carpetas](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="e03d6-126">Cuando la *carpeta ContosoSpatialAwareness* contiene la implementación del proveedor de datos, la carpeta *Editor* contiene el inspector (y cualquier otro código específico del editor de Unity) y la carpeta *Perfiles* contiene uno o varios objetos pre-creados que pueden incluirse en scripts de perfil.</span><span class="sxs-lookup"><span data-stu-id="e03d6-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="e03d6-127">Envío de MRTK</span><span class="sxs-lookup"><span data-stu-id="e03d6-127">MRTK submission</span></span>

<span data-ttu-id="e03d6-128">**Espacio de nombres**</span><span class="sxs-lookup"><span data-stu-id="e03d6-128">**Namespace**</span></span>

<span data-ttu-id="e03d6-129">Si se envía un proveedor de datos del sistema de reconocimiento espacial  al repositorio [de Mixed Reality Toolkit,](https://github.com/Microsoft/MixedRealityToolkit-Unity)el espacio de nombres debe comenzar por Microsoft.MixedReality.Toolkit (por ejemplo: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span><span class="sxs-lookup"><span data-stu-id="e03d6-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="e03d6-130">y el código debe estar ubicado en una carpeta debajo de MRTK/Providers (por ejemplo: *MRTK/Providers/ObjectMeshObserver*).</span><span class="sxs-lookup"><span data-stu-id="e03d6-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="e03d6-131">**Estructura de carpetas**</span><span class="sxs-lookup"><span data-stu-id="e03d6-131">**Folder structure**</span></span>

<span data-ttu-id="e03d6-132">Todo el código debe estar ubicado en una carpeta debajo de MRTK/Providers (por ejemplo: MRTK/Providers/ObjectMeshObserver).</span><span class="sxs-lookup"><span data-stu-id="e03d6-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="e03d6-133">Definición del objeto de datos espaciales</span><span class="sxs-lookup"><span data-stu-id="e03d6-133">Define the spatial data object</span></span>

<span data-ttu-id="e03d6-134">El primer paso para crear un proveedor de datos de reconocimiento espacial es determinar el tipo de datos (por ejemplo, mallas o planos) que proporcionará a las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="e03d6-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="e03d6-135">Todos los objetos de datos espaciales deben implementar la [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interfaz .</span><span class="sxs-lookup"><span data-stu-id="e03d6-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="e03d6-136">La Mixed Reality Toolkit proporciona los siguientes objetos espaciales que se pueden usar o ampliar en nuevos proveedores de datos.</span><span class="sxs-lookup"><span data-stu-id="e03d6-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="e03d6-137">Implementación del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="e03d6-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="e03d6-138">Especificación de la herencia de interfaz o clase base</span><span class="sxs-lookup"><span data-stu-id="e03d6-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="e03d6-139">Todos los proveedores de datos de reconocimiento espacial deben implementar la interfaz , que especifica [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) la funcionalidad mínima requerida por el sistema de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="e03d6-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="e03d6-140">La base de MRTK incluye la [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) clase que proporciona una implementación predeterminada de esta funcionalidad necesaria.</span><span class="sxs-lookup"><span data-stu-id="e03d6-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="e03d6-141">La clase usa la interfaz para indicar que proporciona [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) compatibilidad con la funcionalidad [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) SpatialAwarenessMesh.</span><span class="sxs-lookup"><span data-stu-id="e03d6-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="e03d6-142">Aplicación del atributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="e03d6-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="e03d6-143">Un paso clave para crear un proveedor de datos de reconocimiento espacial es aplicar el [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo a la clase .</span><span class="sxs-lookup"><span data-stu-id="e03d6-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="e03d6-144">Este paso permite establecer los perfiles y plataformas predeterminados para el proveedor de datos, cuando se seleccionan en el perfil de reconocimiento espacial, así como el nombre, la ruta de acceso de la carpeta, etc.</span><span class="sxs-lookup"><span data-stu-id="e03d6-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="e03d6-145">Implementación de los métodos IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="e03d6-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="e03d6-146">Una vez definida la clase , el siguiente paso es proporcionar la implementación de la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .</span><span class="sxs-lookup"><span data-stu-id="e03d6-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="e03d6-147">La [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) clase, a través de [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) la clase , proporciona solo implementaciones vacías para los [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos.</span><span class="sxs-lookup"><span data-stu-id="e03d6-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="e03d6-148">Los detalles de estos métodos suelen ser específicos del proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="e03d6-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="e03d6-149">Los métodos que debe implementar el proveedor de datos son:</span><span class="sxs-lookup"><span data-stu-id="e03d6-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="e03d6-150">Implementación de la lógica del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="e03d6-150">Implement the data provider logic</span></span>

<span data-ttu-id="e03d6-151">El siguiente paso consiste en agregar la lógica del proveedor de datos mediante la implementación de la interfaz del proveedor de datos específica, por ejemplo [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="e03d6-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="e03d6-152">Esta parte del proveedor de datos normalmente será específica de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="e03d6-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="e03d6-153">Notificaciones de cambio de observación</span><span class="sxs-lookup"><span data-stu-id="e03d6-153">Observation change notifications</span></span>

<span data-ttu-id="e03d6-154">Para permitir que las aplicaciones respondan a los cambios en la comprensión del entorno del dispositivo, el proveedor de datos genera eventos de notificación como se define en la [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interfaz .</span><span class="sxs-lookup"><span data-stu-id="e03d6-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="e03d6-155">El código siguiente de los [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) ejemplos muestra la generación y el evento cuando se agregan datos de malla.</span><span class="sxs-lookup"><span data-stu-id="e03d6-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="e03d6-156">La [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) clase no genera eventos porque el modelo `OnObservationUpdated` 3D solo se carga una vez.</span><span class="sxs-lookup"><span data-stu-id="e03d6-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="e03d6-157">La implementación de la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) clase proporciona un ejemplo de cómo generar un evento para una malla `OnObservationUpdated` observada.</span><span class="sxs-lookup"><span data-stu-id="e03d6-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="e03d6-158">Adición de instrumentación de Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="e03d6-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="e03d6-159">El rendimiento es fundamental en las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="e03d6-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="e03d6-160">Cada componente agrega cierta sobrecarga para la que las aplicaciones deben tener en cuenta.</span><span class="sxs-lookup"><span data-stu-id="e03d6-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="e03d6-161">Para ello, es importante que todos los proveedores de datos de reconocimiento espacial contengan instrumentación de Unity Profiler en bucle interno y rutas de acceso de código que se usan con frecuencia.</span><span class="sxs-lookup"><span data-stu-id="e03d6-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="e03d6-162">Se recomienda implementar el patrón utilizado por MRTK al instrumentar proveedores personalizados.</span><span class="sxs-lookup"><span data-stu-id="e03d6-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="e03d6-163">El nombre utilizado para identificar el marcador del profiler es arbitrario.</span><span class="sxs-lookup"><span data-stu-id="e03d6-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="e03d6-164">MrTK usa el siguiente patrón.</span><span class="sxs-lookup"><span data-stu-id="e03d6-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="e03d6-165">"[product] className.methodName - optional note"</span><span class="sxs-lookup"><span data-stu-id="e03d6-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="e03d6-166">Se recomienda que los proveedores de datos personalizados sigan un patrón similar para ayudar a simplificar la identificación de componentes y métodos específicos al analizar seguimientos.</span><span class="sxs-lookup"><span data-stu-id="e03d6-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="e03d6-167">Creación del perfil y el inspector</span><span class="sxs-lookup"><span data-stu-id="e03d6-167">Create the profile and inspector</span></span>

<span data-ttu-id="e03d6-168">En Mixed Reality Toolkit, los proveedores de datos se configuran mediante [perfiles](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e03d6-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="e03d6-169">Definición del perfil</span><span class="sxs-lookup"><span data-stu-id="e03d6-169">Define the profile</span></span>

<span data-ttu-id="e03d6-170">El contenido del perfil debe reflejar las propiedades accesibles del proveedor de datos (por ejemplo, intervalo de actualización).</span><span class="sxs-lookup"><span data-stu-id="e03d6-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="e03d6-171">Todas las propiedades configurables por el usuario definidas en cada interfaz deben incluirse con el perfil.</span><span class="sxs-lookup"><span data-stu-id="e03d6-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="e03d6-172">Se recomiendan las clases base si un nuevo proveedor de datos extiende un proveedor existente.</span><span class="sxs-lookup"><span data-stu-id="e03d6-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="e03d6-173">Por ejemplo, extiende para permitir que los clientes proporcionen un modelo 3D que se [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) usará como datos del [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) entorno.</span><span class="sxs-lookup"><span data-stu-id="e03d6-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="e03d6-174">El atributo se puede aplicar a la clase de perfil para permitir que los clientes creen una instancia de perfil mediante el menú `CreateAssetMenu`   >    >  **Crear recursos Mixed Reality**  >  **Toolkit Profiles** .</span><span class="sxs-lookup"><span data-stu-id="e03d6-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="e03d6-175">Implementación del inspector</span><span class="sxs-lookup"><span data-stu-id="e03d6-175">Implement the inspector</span></span>

<span data-ttu-id="e03d6-176">Los inspectores de perfil son la interfaz de usuario para configurar y ver el contenido del perfil.</span><span class="sxs-lookup"><span data-stu-id="e03d6-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="e03d6-177">Cada inspector de perfil debe extender la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) clase .</span><span class="sxs-lookup"><span data-stu-id="e03d6-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="e03d6-178">El `CustomEditor` atributo informa a Unity del tipo de recurso al que se aplica el inspector.</span><span class="sxs-lookup"><span data-stu-id="e03d6-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="e03d6-179">Creación de definiciones de ensamblado</span><span class="sxs-lookup"><span data-stu-id="e03d6-179">Create assembly definition(s)</span></span>

<span data-ttu-id="e03d6-180">El Mixed Reality Toolkit usa archivos de definición de ensamblado[(.asmdef)](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)para especificar dependencias entre componentes, así como para ayudar a Unity a reducir el tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="e03d6-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="e03d6-181">Se recomienda crear archivos de definición de ensamblado para todos los proveedores de datos y sus componentes del editor.</span><span class="sxs-lookup"><span data-stu-id="e03d6-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="e03d6-182">Con la [estructura de carpetas](#namespace-and-folder-structure) del ejemplo anterior, habría dos archivos .asmdef para el proveedor de datos ContosoSpatialAwareness.</span><span class="sxs-lookup"><span data-stu-id="e03d6-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="e03d6-183">La primera definición de ensamblado es para el proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="e03d6-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="e03d6-184">En este ejemplo, se denominará ContosoSpatialAwareness y se ubicará en la carpeta *ContosoSpatialAwareness del* ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e03d6-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="e03d6-185">Esta definición de ensamblado debe especificar una dependencia en Microsoft.MixedReality.Toolkit y en cualquier otro ensamblado del que dependa.</span><span class="sxs-lookup"><span data-stu-id="e03d6-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="e03d6-186">La definición del ensamblado ContosoInputEditor especificará el inspector de perfil y cualquier código específico del editor.</span><span class="sxs-lookup"><span data-stu-id="e03d6-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="e03d6-187">Este archivo debe encontrarse en la carpeta raíz del código del editor.</span><span class="sxs-lookup"><span data-stu-id="e03d6-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="e03d6-188">En este ejemplo, el archivo se ubicará en la *carpeta ContosoSpatialAwareness\Editor.*</span><span class="sxs-lookup"><span data-stu-id="e03d6-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="e03d6-189">Esta definición de ensamblado contendrá una referencia al ensamblado ContosoSpatialAwareness, así como:</span><span class="sxs-lookup"><span data-stu-id="e03d6-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="e03d6-190">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="e03d6-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="e03d6-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="e03d6-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="e03d6-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="e03d6-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="e03d6-193">Registro del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="e03d6-193">Register the data provider</span></span>

<span data-ttu-id="e03d6-194">Una vez creado, el proveedor de datos se puede registrar con el sistema de reconocimiento espacial que se usará en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e03d6-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![Selección del observador de malla de objetos espaciales](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="e03d6-196">Empaquetado y distribución</span><span class="sxs-lookup"><span data-stu-id="e03d6-196">Packaging and distribution</span></span>

<span data-ttu-id="e03d6-197">Los proveedores de datos que se distribuyen como componentes de terceros tienen los detalles específicos del empaquetado y la distribución de acuerdo con las preferencias del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="e03d6-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="e03d6-198">Probablemente, la solución más común será generar un .unitypackage y distribuirlo a través del Almacén de recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="e03d6-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="e03d6-199">Si se envía y acepta un proveedor de datos como parte del paquete microsoft Mixed Reality Toolkit, el equipo de Microsoft MRTK lo empaquetará y distribuirá como parte de las ofertas de MRTK.</span><span class="sxs-lookup"><span data-stu-id="e03d6-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="e03d6-200">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e03d6-200">See also</span></span>

- [<span data-ttu-id="e03d6-201">Sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="e03d6-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="e03d6-202">`IMixedRealitySpatialAwarenessObject` Interfaz</span><span class="sxs-lookup"><span data-stu-id="e03d6-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="e03d6-203">Clase `BaseSpatialAwarenessObject`</span><span class="sxs-lookup"><span data-stu-id="e03d6-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="e03d6-204">Clase `SpatialAwarenessMeshObject`</span><span class="sxs-lookup"><span data-stu-id="e03d6-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="e03d6-205">Clase `SpatialAwarenessPlanarObject`</span><span class="sxs-lookup"><span data-stu-id="e03d6-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="e03d6-206">`IMixedRealitySpatialAwarenessObserver` Interfaz</span><span class="sxs-lookup"><span data-stu-id="e03d6-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="e03d6-207">Clase `BaseSpatialObserver`</span><span class="sxs-lookup"><span data-stu-id="e03d6-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="e03d6-208">`IMixedRealitySpatialAwarenessMeshObserver` Interfaz</span><span class="sxs-lookup"><span data-stu-id="e03d6-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="e03d6-209">`IMixedRealityDataProvider` Interfaz</span><span class="sxs-lookup"><span data-stu-id="e03d6-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="e03d6-210">`IMixedRealityCapabilityCheck` Interfaz</span><span class="sxs-lookup"><span data-stu-id="e03d6-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
