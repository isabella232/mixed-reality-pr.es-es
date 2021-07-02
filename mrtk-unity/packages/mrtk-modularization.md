---
title: Modularización de MRTK
description: Describe la componenteización en MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: eac96e309afc21f9a2b6efe9c3aef5975e4f0dff
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177013"
---
# <a name="mrtk-modularization"></a><span data-ttu-id="c16d8-104">Modularización de MRTK</span><span class="sxs-lookup"><span data-stu-id="c16d8-104">MRTK modularization</span></span>

<span data-ttu-id="c16d8-105">Una de las nuevas características excelentes de Mixed Reality Toolkit v2 es la mejora de la componenteización.</span><span class="sxs-lookup"><span data-stu-id="c16d8-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="c16d8-106">Siempre que sea posible, los componentes individuales están aislados de todos, menos de la capa principal de la base.</span><span class="sxs-lookup"><span data-stu-id="c16d8-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="c16d8-107">Dependencias minimizadas</span><span class="sxs-lookup"><span data-stu-id="c16d8-107">Minimized dependencies</span></span>

<span data-ttu-id="c16d8-108">MRTK v2 se desarrolló intencionadamente para ser modular y minimizar las dependencias entre los servicios del sistema (por ejemplo, el reconocimiento espacial).</span><span class="sxs-lookup"><span data-stu-id="c16d8-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="c16d8-109">Debido a la naturaleza de algunos servicios del sistema (por ejemplo, entrada y teleportación), existe un número pequeño de dependencias.</span><span class="sxs-lookup"><span data-stu-id="c16d8-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="c16d8-110">Aunque se espera que los servicios necesiten uno o varios componentes del proveedor de datos, no hay vínculos directos entre ellos.</span><span class="sxs-lookup"><span data-stu-id="c16d8-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="c16d8-111">Lo mismo sucede con las características del SDK (por ejemplo, Interfaz de usuario componentes).</span><span class="sxs-lookup"><span data-stu-id="c16d8-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="c16d8-112">Comunicación de componentes</span><span class="sxs-lookup"><span data-stu-id="c16d8-112">Component communication</span></span>

<span data-ttu-id="c16d8-113">Para asegurarse de que no hay vínculos directos entre componentes, MRTK v2 usa interfaces para comunicarse entre servicios, proveedores de datos y código de aplicación.</span><span class="sxs-lookup"><span data-stu-id="c16d8-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="c16d8-114">Estas interfaces se definen en y toda la comunicación se enruta a través del Mixed Reality Toolkit principal.</span><span class="sxs-lookup"><span data-stu-id="c16d8-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![Uso del sistema de reconocimiento espacial a través de interfaces](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="c16d8-116">Minimizar la superficie de importación de MRTK</span><span class="sxs-lookup"><span data-stu-id="c16d8-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="c16d8-117">En este momento, mrtk se importa como un único paquete básico (omitiendo por un momento la existencia del paquete de ejemplos, que es un paquete completamente opcional).</span><span class="sxs-lookup"><span data-stu-id="c16d8-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="c16d8-118">Es posible reducir esta superficie si se recortan manualmente los archivos importados, aunque se trata de un proceso muy manual que no tiene una guía bien definida.</span><span class="sxs-lookup"><span data-stu-id="c16d8-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="c16d8-119">Es posible desactivar los elementos arbitrarios durante la importación del paquete foundation.</span><span class="sxs-lookup"><span data-stu-id="c16d8-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="c16d8-120">Sin embargo, no se recomienda hacerlo en una fase temprana del desarrollo, ya que podría interrumpir la funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="c16d8-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="c16d8-121">Después de haber descubierto el conjunto de características final de una aplicación, los proveedores y servicios innecesarios se pueden realizar en las carpetas siguientes:</span><span class="sxs-lookup"><span data-stu-id="c16d8-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="c16d8-122">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="c16d8-122">MRTK/Services</span></span>
- <span data-ttu-id="c16d8-123">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="c16d8-123">MRTK/Providers</span></span>
- <span data-ttu-id="c16d8-124">MRTK/SDK/Features</span><span class="sxs-lookup"><span data-stu-id="c16d8-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="c16d8-125">MRTK v2.x **_requiere el_** contenido de la carpeta Assets/MRTK/Core.</span><span class="sxs-lookup"><span data-stu-id="c16d8-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="c16d8-126">Próximas características</span><span class="sxs-lookup"><span data-stu-id="c16d8-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="c16d8-127">Arquitectura de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c16d8-127">Application architecture</span></span>

<span data-ttu-id="c16d8-128">MrTK tendrá compatibilidad para permitir que las aplicaciones se puedan crear con una variedad de arquitecturas, entre las que se incluyen:</span><span class="sxs-lookup"><span data-stu-id="c16d8-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="c16d8-129">Localizador de servicios MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="c16d8-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="c16d8-130">Servicios individuales</span><span class="sxs-lookup"><span data-stu-id="c16d8-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="c16d8-131">Localizador de servicios personalizados</span><span class="sxs-lookup"><span data-stu-id="c16d8-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="c16d8-132">Arquitectura híbrida</span><span class="sxs-lookup"><span data-stu-id="c16d8-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="c16d8-133">Al seleccionar una arquitectura de aplicación, es importante tener en cuenta la flexibilidad de diseño y el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c16d8-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="c16d8-134">No se espera que las arquitecturas descritas aquí sean adecuadas para todas las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c16d8-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="c16d8-135">Localizador de servicios MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="c16d8-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="c16d8-136">MRTK permite (y configura automáticamente) las escenas de aplicación para usar el componente de [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizador de servicios predeterminado.</span><span class="sxs-lookup"><span data-stu-id="c16d8-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="c16d8-137">Este componente incluye compatibilidad para configurar sistemas MRTK y proveedores de datos a través de inspectores de configuración y administra la duración de los componentes y los comportamientos principales (por ejemplo, cuándo actualizar).</span><span class="sxs-lookup"><span data-stu-id="c16d8-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="c16d8-138">Todos los sistemas se representan en el inspector de configuración principal, independientemente de si están presentes o no en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c16d8-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="c16d8-139">Consulte la Guía [Mixed Reality configuración de datos](../configuration/mixed-reality-configuration-guide.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="c16d8-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="c16d8-140">Componentes de servicio individuales</span><span class="sxs-lookup"><span data-stu-id="c16d8-140">Individual service components</span></span>

<span data-ttu-id="c16d8-141">Algunos desarrolladores han expresado su deseo de incluir componentes de servicio individuales en la jerarquía de la escena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c16d8-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="c16d8-142">Para habilitar este uso, los servicios tendrán que encapsularse en un registrador personalizado o se registrarán por sí solos o se administrarán por sí solos.</span><span class="sxs-lookup"><span data-stu-id="c16d8-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="c16d8-143">Un servicio de registro propio implementaría y se registraría a sí mismo para que el código de la aplicación pudiera detectar la instancia [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) de servicio a través de un registro.</span><span class="sxs-lookup"><span data-stu-id="c16d8-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="c16d8-144">Un servicio de auto-administración podría implementarse como un objeto singleton en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="c16d8-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="c16d8-145">Este objeto proporcionaría y la propiedad de instancia que el código de aplicación podría usar para acceder directamente a la funcionalidad del servicio.</span><span class="sxs-lookup"><span data-stu-id="c16d8-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="c16d8-146">Localizador de servicios personalizados</span><span class="sxs-lookup"><span data-stu-id="c16d8-146">Custom service locator</span></span>

<span data-ttu-id="c16d8-147">Algunos desarrolladores han solicitado la capacidad de crear un componente de localizador de servicios personalizado.</span><span class="sxs-lookup"><span data-stu-id="c16d8-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="c16d8-148">Los localizadores de servicios personalizados implementarían la interfaz y administrarían el ciclo de vida [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) y los comportamientos principales de los servicios activos.</span><span class="sxs-lookup"><span data-stu-id="c16d8-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="c16d8-149">Arquitectura híbrida</span><span class="sxs-lookup"><span data-stu-id="c16d8-149">Hybrid architecture</span></span>

<span data-ttu-id="c16d8-150">MRTK admitirá una arquitectura híbrida en la que los desarrolladores pueden combinar los enfoques anteriores según sea necesario o deseado.</span><span class="sxs-lookup"><span data-stu-id="c16d8-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="c16d8-151">Por ejemplo, un desarrollador podría empezar con el localizador [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) de servicios y agregar un servicio de registro propio.</span><span class="sxs-lookup"><span data-stu-id="c16d8-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="c16d8-152">Al optar por una arquitectura híbrida, es importante tener en cuenta cualquier duplicación de trabajo (por ejemplo, adquirir datos de controlador de varios componentes).</span><span class="sxs-lookup"><span data-stu-id="c16d8-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
