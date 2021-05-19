---
title: Mixed Reality Service Registry e IMixedRealityServiceRegistrar
description: Documentación sobre MixedRealityServiceRegistry e IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 09b20537824af42d241b6c33496cedcb4f530bc7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145229"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a><span data-ttu-id="7f17a-104">¿Qué son MixedRealityServiceRegistry e IMixedRealityServiceRegistrar?</span><span class="sxs-lookup"><span data-stu-id="7f17a-104">What are the MixedRealityServiceRegistry and IMixedRealityServiceRegistrar?</span></span>

<span data-ttu-id="7f17a-105">El Mixed Reality toolkit tiene dos componentes con nombre muy similares que realizan tareas relacionadas: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.</span><span class="sxs-lookup"><span data-stu-id="7f17a-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="7f17a-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="7f17a-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="7f17a-107">[MixedRealityServiceRegistry es](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) el componente que contiene instancias de cada servicio registrado (sistemas principales y servicios de extensión).</span><span class="sxs-lookup"><span data-stu-id="7f17a-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="7f17a-108">MixedRealityServiceRegistry contiene instancias de objetos que implementan la interfaz [IMixedRealityService,](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) incluido [IMixedRealityExtensionService.](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)</span><span class="sxs-lookup"><span data-stu-id="7f17a-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="7f17a-109">Los objetos que implementan [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (una subclase de IMixedRealityService) no se registran explícitamente en MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="7f17a-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="7f17a-110">Estos objetos se administran mediante los servicios individuales (por ejemplo, reconocimiento espacial).</span><span class="sxs-lookup"><span data-stu-id="7f17a-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="7f17a-111">MixedRealityServiceRegistry se implementa como una clase estática de C# y es el patrón recomendado para adquirir instancias de servicio en el código de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7f17a-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="7f17a-112">En el fragmento de código siguiente se muestra cómo adquirir una instancia de IMixedRealityInputSystem.</span><span class="sxs-lookup"><span data-stu-id="7f17a-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="7f17a-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="7f17a-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="7f17a-114">[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) es la interfaz que define la funcionalidad implementada por los componentes que administran el registro de uno o varios servicios.</span><span class="sxs-lookup"><span data-stu-id="7f17a-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="7f17a-115">Los componentes que implementan IMixedRealityServiceRegistrar son responsables de agregar y quitar los datos dentro de MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="7f17a-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="7f17a-116">El [objeto MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) es uno de estos componentes.</span><span class="sxs-lookup"><span data-stu-id="7f17a-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="7f17a-117">Puede encontrar otros registradores en la carpeta MRTK/SDK/Experimental/Features.</span><span class="sxs-lookup"><span data-stu-id="7f17a-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="7f17a-118">Estos componentes se pueden usar para agregar compatibilidad con un único servicio (por ejemplo, reconocimiento espacial) a una aplicación.</span><span class="sxs-lookup"><span data-stu-id="7f17a-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="7f17a-119">Estos administradores de servicios únicos se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="7f17a-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="7f17a-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="7f17a-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="7f17a-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="7f17a-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="7f17a-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="7f17a-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="7f17a-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="7f17a-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="7f17a-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="7f17a-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="7f17a-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="7f17a-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="7f17a-126">Cada uno de los componentes anteriores, a excepción de InputSystemManager, es responsable de administrar el registro y el estado de un único tipo de servicio.</span><span class="sxs-lookup"><span data-stu-id="7f17a-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="7f17a-127">InputSystem requiere algunos servicios de soporte técnico adicionales (por ejemplo, FocusProvider) que también administra InputSystemManager.</span><span class="sxs-lookup"><span data-stu-id="7f17a-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="7f17a-128">En general, los componentes de administración de servicios llaman internamente a los métodos definidos por IMixedRealityServiceRegistrar o a los servicios que requieren componentes de servicio adicionales para funcionar correctamente.</span><span class="sxs-lookup"><span data-stu-id="7f17a-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="7f17a-129">Por lo general, el código de la aplicación no debe llamar a estos métodos, ya que puede provocar que la aplicación se comporte de forma impredecible (por ejemplo, una instancia de servicio almacenada en caché puede dejar de ser válida).</span><span class="sxs-lookup"><span data-stu-id="7f17a-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f17a-130">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7f17a-130">See also</span></span>

- [<span data-ttu-id="7f17a-131">Documentación de la API IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="7f17a-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="7f17a-132">Documentación de la API MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="7f17a-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
