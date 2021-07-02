---
title: Servicios de extensión
description: documentación para la funcionalidad extendida en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176272"
---
# <a name="extension-services"></a><span data-ttu-id="b7f81-104">Servicios de extensión</span><span class="sxs-lookup"><span data-stu-id="b7f81-104">Extension services</span></span>

<span data-ttu-id="b7f81-105">Los servicios de extensión son componentes que amplían la funcionalidad del Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="b7f81-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="b7f81-106">Estos servicios pueden ser proporcionados por MRTK o por otras partes.</span><span class="sxs-lookup"><span data-stu-id="b7f81-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="b7f81-107">Creación de un servicio de extensión</span><span class="sxs-lookup"><span data-stu-id="b7f81-107">Creating an extension service</span></span>

<span data-ttu-id="b7f81-108">La manera más eficaz de crear un servicio de extensión es usar el Asistente para la creación [de servicios de extensión](../tools/extension-service-creation-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="b7f81-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="b7f81-109">Para iniciar el Asistente para la creación del servicio de extensión, **seleccione Mixed Reality Toolkit > Utilidades > Crear servicio de extensión**.</span><span class="sxs-lookup"><span data-stu-id="b7f81-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Asistente para la creación de servicios de extensión](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="b7f81-111">El asistente automatiza la creación de los componentes del servicio y garantiza la herencia de interfaz adecuada.</span><span class="sxs-lookup"><span data-stu-id="b7f81-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Componentes creados por el Asistente para creación de servicios de extensión](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="b7f81-113">En la versión 2.0.0 de MRTK, hay un problema en el asistente del servicio de extensión en el que es necesario generar el inspector de servicio y el perfil de servicio.</span><span class="sxs-lookup"><span data-stu-id="b7f81-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="b7f81-114">Consulte el problema [5654 para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) obtener más información.</span><span class="sxs-lookup"><span data-stu-id="b7f81-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="b7f81-115">Cuando se completa el asistente, se puede implementar la funcionalidad del servicio.</span><span class="sxs-lookup"><span data-stu-id="b7f81-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="b7f81-116">Registro de un servicio de extensión</span><span class="sxs-lookup"><span data-stu-id="b7f81-116">Registering an extension service</span></span>

<span data-ttu-id="b7f81-117">Para que una aplicación pueda acceder a él, el nuevo servicio de extensión debe registrarse con el Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="b7f81-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="b7f81-118">El Asistente para la creación de servicios de extensión se puede usar para registrar el servicio.</span><span class="sxs-lookup"><span data-stu-id="b7f81-118">The extension service creation wizard can be used to register the service.</span></span>

![Registro del Asistente para creación de servicios de extensión](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="b7f81-120">El servicio también se puede registrar manualmente mediante el inspector Mixed Reality Toolkit configuración.</span><span class="sxs-lookup"><span data-stu-id="b7f81-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Registro manual del servicio de extensión](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="b7f81-122">Si el servicio de extensión usa un perfil, asegúrese de que se especifica en el inspector.</span><span class="sxs-lookup"><span data-stu-id="b7f81-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Servicio de extensión configurado](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="b7f81-124">También se pueden ajustar el nombre y la prioridad del componente.</span><span class="sxs-lookup"><span data-stu-id="b7f81-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="b7f81-125">Acceso a un servicio de extensión</span><span class="sxs-lookup"><span data-stu-id="b7f81-125">Accessing an extension service</span></span>

<span data-ttu-id="b7f81-126">Se accede a los servicios de extensión, en el código, mediante , [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="b7f81-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="b7f81-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b7f81-127">See also</span></span>

- [<span data-ttu-id="b7f81-128">Sistemas, servicios de extensión y proveedores de datos</span><span class="sxs-lookup"><span data-stu-id="b7f81-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="b7f81-129">Asistente para la creación de servicios de extensión</span><span class="sxs-lookup"><span data-stu-id="b7f81-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="b7f81-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="b7f81-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="b7f81-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="b7f81-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
