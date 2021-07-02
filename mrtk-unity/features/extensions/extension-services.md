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
# <a name="extension-services"></a>Servicios de extensión

Los servicios de extensión son componentes que amplían la funcionalidad del Mixed Reality Toolkit. Estos servicios pueden ser proporcionados por MRTK o por otras partes.

## <a name="creating-an-extension-service"></a>Creación de un servicio de extensión

La manera más eficaz de crear un servicio de extensión es usar el Asistente para la creación [de servicios de extensión](../tools/extension-service-creation-wizard.md).
Para iniciar el Asistente para la creación del servicio de extensión, **seleccione Mixed Reality Toolkit > Utilidades > Crear servicio de extensión**.

![Asistente para la creación de servicios de extensión](../images/extension-wizard/ExtensionServiceCreationWizard.png)

El asistente automatiza la creación de los componentes del servicio y garantiza la herencia de interfaz adecuada.

![Componentes creados por el Asistente para creación de servicios de extensión](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> En la versión 2.0.0 de MRTK, hay un problema en el asistente del servicio de extensión en el que es necesario generar el inspector de servicio y el perfil de servicio. Consulte el problema [5654 para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) obtener más información.

Cuando se completa el asistente, se puede implementar la funcionalidad del servicio.

## <a name="registering-an-extension-service"></a>Registro de un servicio de extensión

Para que una aplicación pueda acceder a él, el nuevo servicio de extensión debe registrarse con el Mixed Reality Toolkit.

El Asistente para la creación de servicios de extensión se puede usar para registrar el servicio.

![Registro del Asistente para creación de servicios de extensión](../images/extension-wizard/ExtensionServiceWizardRegister.png)

El servicio también se puede registrar manualmente mediante el inspector Mixed Reality Toolkit configuración.

![Registro manual del servicio de extensión](../images/profiles/RegisterExtensionService.png)

Si el servicio de extensión usa un perfil, asegúrese de que se especifica en el inspector.

![Servicio de extensión configurado](../images/profiles/ConfiguredExtensionService.png)

También se pueden ajustar el nombre y la prioridad del componente.

## <a name="accessing-an-extension-service"></a>Acceso a un servicio de extensión

Se accede a los servicios de extensión, en el código, mediante , [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) como se muestra en el ejemplo siguiente.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>Consulte también

- [Sistemas, servicios de extensión y proveedores de datos](../../architecture/systems-extensions-providers.md)
- [Asistente para la creación de servicios de extensión](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
