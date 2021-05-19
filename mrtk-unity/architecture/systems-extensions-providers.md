---
title: Proveedor de extensiones del sistema
description: Extensiones y proveedores de datos de MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, extensiones del sistema,
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143508"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="f0d86-104">Sistemas, servicios de extensión y proveedores de datos</span><span class="sxs-lookup"><span data-stu-id="f0d86-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="f0d86-105">En Mixed Reality Toolkit, muchas de las características se entregan en forma de servicios.</span><span class="sxs-lookup"><span data-stu-id="f0d86-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="f0d86-106">Los servicios se agrupan en tres categorías principales: sistemas, servicios de extensión y proveedores de datos.</span><span class="sxs-lookup"><span data-stu-id="f0d86-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="f0d86-107">Sistemas</span><span class="sxs-lookup"><span data-stu-id="f0d86-107">Systems</span></span>

<span data-ttu-id="f0d86-108">Los sistemas son servicios que proporcionan la funcionalidad principal de Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f0d86-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f0d86-109">Todos los sistemas son implementaciones de la [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interfaz .</span><span class="sxs-lookup"><span data-stu-id="f0d86-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="f0d86-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="f0d86-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="f0d86-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="f0d86-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="f0d86-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="f0d86-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="f0d86-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="f0d86-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="f0d86-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="f0d86-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="f0d86-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="f0d86-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="f0d86-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="f0d86-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="f0d86-117">Cada uno de los sistemas enumerados aparece en el [](../features/profiles/profiles.md)perfil de configuración del componente MixedRealityToolkit .</span><span class="sxs-lookup"><span data-stu-id="f0d86-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="f0d86-118">Extensiones</span><span class="sxs-lookup"><span data-stu-id="f0d86-118">Extensions</span></span>

<span data-ttu-id="f0d86-119">Los servicios de extensión son componentes que amplían la funcionalidad de Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f0d86-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f0d86-120">Todos los servicios de extensión deben especificar que implementen la [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interfaz .</span><span class="sxs-lookup"><span data-stu-id="f0d86-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="f0d86-121">Para obtener información sobre cómo crear servicios de extensión, consulte el [artículo Servicios de](../features/extensions/extension-services.md) extensión.</span><span class="sxs-lookup"><span data-stu-id="f0d86-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="f0d86-122">Para poder acceder a MRTK, los servicios de extensión se registran y configuran mediante la sección Extensiones del perfil de configuración del componente MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="f0d86-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Configuración de un servicio de extensión](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="f0d86-124">Proveedores de datos</span><span class="sxs-lookup"><span data-stu-id="f0d86-124">Data providers</span></span>

<span data-ttu-id="f0d86-125">Los proveedores de datos son componentes que, por su nombre, proporcionan datos a un servicio Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f0d86-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="f0d86-126">Todos los proveedores de datos deben especificar que implementan la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .</span><span class="sxs-lookup"><span data-stu-id="f0d86-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="f0d86-127">No todos los servicios requerirán proveedores de datos.</span><span class="sxs-lookup"><span data-stu-id="f0d86-127">Not all services will require data providers.</span></span> <span data-ttu-id="f0d86-128">De los sistemas Mixed Reality Toolkit, los sistemas de entrada y de reconocimiento espacial son los únicos servicios que usan proveedores de datos.</span><span class="sxs-lookup"><span data-stu-id="f0d86-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="f0d86-129">Para que el servicio MRTK específico sea accesible, los proveedores de datos se registran en el perfil de configuración del servicio.</span><span class="sxs-lookup"><span data-stu-id="f0d86-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="f0d86-130">El código de la aplicación accede a los proveedores de datos a través de la [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interfaz .</span><span class="sxs-lookup"><span data-stu-id="f0d86-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="f0d86-131">Para simplificar el acceso, los proveedores de datos también se pueden recuperar a través de la `CoreServices` clase auxiliar.</span><span class="sxs-lookup"><span data-stu-id="f0d86-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="f0d86-132">Aunque `IMixedRealityDataProvider` hereda de `IMixedRealityService` , los proveedores de datos no se registran con `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="f0d86-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="f0d86-133">Para acceder a los proveedores de datos, el código de la aplicación debe consultar la instancia de servicio para la que se registraron (por ejemplo, el sistema de entrada).</span><span class="sxs-lookup"><span data-stu-id="f0d86-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="f0d86-134">Entrada</span><span class="sxs-lookup"><span data-stu-id="f0d86-134">Input</span></span>

<span data-ttu-id="f0d86-135">El sistema de entrada de MRTK solo usa proveedores de datos que implementan [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="f0d86-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Proveedores de datos del sistema de entrada](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="f0d86-137">En el ejemplo siguiente se muestra cómo obtener acceso al proveedor de simulación de entrada y alternar la propiedad SmoothEyeTracking.</span><span class="sxs-lookup"><span data-stu-id="f0d86-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

<span data-ttu-id="f0d86-138">El acceso a un proveedor de datos para el sistema de entrada principal también se puede simplificar mediante el uso de la `CoreServices` clase auxiliar.</span><span class="sxs-lookup"><span data-stu-id="f0d86-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="f0d86-139">El sistema de entrada devuelve solo los proveedores de datos que se admiten para la plataforma en la que se ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f0d86-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="f0d86-140">Para obtener información sobre cómo escribir un proveedor de datos para el sistema de entrada de MRTK, consulte Creación de un [proveedor de datos del sistema de entrada](../features/input/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f0d86-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="f0d86-141">Reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="f0d86-141">Spatial awareness</span></span>

<span data-ttu-id="f0d86-142">El sistema de reconocimiento espacial de MRTK solo usa proveedores de datos que implementan la [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interfaz .</span><span class="sxs-lookup"><span data-stu-id="f0d86-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Proveedores de datos del sistema de reconocimiento espacial](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="f0d86-144">En el ejemplo siguiente se muestra cómo acceder a los proveedores de datos de malla espacial registrados y cambiar la visibilidad de las mallas.</span><span class="sxs-lookup"><span data-stu-id="f0d86-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

<span data-ttu-id="f0d86-145">El acceso a un proveedor de datos para el sistema de reconocimiento espacial básico también se puede simplificar mediante el uso de la `CoreServices` clase auxiliar.</span><span class="sxs-lookup"><span data-stu-id="f0d86-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="f0d86-146">El sistema de reconocimiento espacial devuelve solo los proveedores de datos que se admiten para la plataforma en la que se ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f0d86-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="f0d86-147">Para obtener información sobre cómo escribir un proveedor de datos para el sistema de reconocimiento espacial DE MRTK, consulte Creación de un [proveedor de datos](../features/spatial-awareness/create-data-provider.md)del sistema de reconocimiento espacial .</span><span class="sxs-lookup"><span data-stu-id="f0d86-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0d86-148">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f0d86-148">See also</span></span>

- [<span data-ttu-id="f0d86-149">Servicios de extensión</span><span class="sxs-lookup"><span data-stu-id="f0d86-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="f0d86-150">Creación de un proveedor de datos del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="f0d86-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="f0d86-151">Creación de un proveedor de datos del sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="f0d86-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="f0d86-152">Interfaz IMixedRealityService</span><span class="sxs-lookup"><span data-stu-id="f0d86-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="f0d86-153">Interfaz IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="f0d86-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="f0d86-154">Interfaz IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="f0d86-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
