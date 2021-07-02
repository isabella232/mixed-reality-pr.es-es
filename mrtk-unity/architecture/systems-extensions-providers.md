---
title: Sistemas, servicios de extensión y proveedores de datos
description: Proveedores de datos y extensiones de MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, extensiones del sistema,
ms.openlocfilehash: 668df40cec9b9443b37f63d80fcf8a1ca2e0bcbc
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177424"
---
# <a name="systems-extension-services-and-data-providers"></a>Sistemas, servicios de extensión y proveedores de datos

En el Mixed Reality Toolkit, muchas de las características se entregan en forma de servicios. Los servicios se agrupan en tres categorías principales: sistemas, servicios de extensión y proveedores de datos.

## <a name="systems"></a>Sistemas

Los sistemas son servicios que proporcionan la funcionalidad básica del Mixed Reality Toolkit. Todos los sistemas son implementaciones de la [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interfaz .

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

Cada uno de los sistemas enumerados aparece en el [](../features/profiles/profiles.md)perfil de configuración del componente MixedRealityToolkit .

## <a name="extensions"></a>Extensiones

Los servicios de extensión son componentes que amplían la funcionalidad del Mixed Reality Toolkit. Todos los servicios de extensión deben especificar que implementen la [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interfaz .

Para obtener información sobre la creación de servicios de extensión, consulte el [artículo Servicios de](../features/extensions/extension-services.md) extensión.

Para ser accesibles para MRTK, los servicios de extensión se registran y configuran mediante la sección Extensiones del perfil de configuración del componente MixedRealityToolkit.

![Configuración de un servicio de extensión](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>Proveedores de datos

Los proveedores de datos son componentes que, por su nombre, proporcionan datos a un Mixed Reality Toolkit servicio. Todos los proveedores de datos deben especificar que implementen la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .

> [!NOTE]
> No todos los servicios requerirán proveedores de datos. De los Mixed Reality Toolkit, los sistemas de entrada y reconocimiento espacial son los únicos servicios que usan proveedores de datos.

Para que el servicio MRTK específico pueda acceder a ellos, los proveedores de datos se registran en el perfil de configuración del servicio.

El código de aplicación tiene acceso a los proveedores de datos a través de la [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interfaz . Para simplificar el acceso, los proveedores de datos también se pueden recuperar a través de la `CoreServices` clase auxiliar.

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> Aunque `IMixedRealityDataProvider` hereda de `IMixedRealityService` , los proveedores de datos no están registrados con `MixedRealityServiceRegistry` . Para acceder a los proveedores de datos, el código de la aplicación debe consultar la instancia de servicio para la que se registraron (por ejemplo, el sistema de entrada).

### <a name="input"></a>Entrada

El sistema de entrada de MRTK solo usa proveedores de datos que implementan [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .

![Proveedores de datos del sistema de entrada](../features/images/input/RegisteredServiceProviders.PNG)

En el ejemplo siguiente se muestra cómo acceder al proveedor de simulación de entrada y alternar la propiedad SmoothEyeTracking.

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

El acceso a un proveedor de datos para el sistema de entrada principal también se puede simplificar mediante el uso de la `CoreServices` clase auxiliar.

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> El sistema de entrada devuelve solo los proveedores de datos que se admiten para la plataforma en la que se ejecuta la aplicación.

Para obtener información sobre cómo escribir un proveedor de datos para el sistema de entrada de MRTK, consulte Creación [de un proveedor de datos del sistema de entrada](../features/input/create-data-provider.md).

### <a name="spatial-awareness"></a>Reconocimiento espacial

El sistema de reconocimiento espacial de MRTK solo usa proveedores de datos que implementan la [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interfaz .

![Proveedores de datos del sistema de reconocimiento espacial](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

En el ejemplo siguiente se muestra cómo acceder a los proveedores de datos de malla espacial registrados y cambiar la visibilidad de las mallas.

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

El acceso a un proveedor de datos para el sistema de reconocimiento espacial básico también se puede simplificar mediante el uso de la `CoreServices` clase auxiliar.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> El sistema de reconocimiento espacial devuelve solo los proveedores de datos que se admiten para la plataforma en la que se ejecuta la aplicación.

Para obtener información sobre cómo escribir un proveedor de datos para el sistema de reconocimiento espacial de MRTK, consulte Creación de un proveedor de datos del sistema de reconocimiento [espacial](../features/spatial-awareness/create-data-provider.md).

## <a name="see-also"></a>Consulte también

- [Servicios de extensión](../features/extensions/extension-services.md)
- [Creación de un proveedor de datos del sistema de entrada](../features/input/create-data-provider.md)
- [Creación de un proveedor de datos del sistema de reconocimiento espacial](../features/spatial-awareness/create-data-provider.md)
- [Interfaz IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [Interfaz IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [IMixedRealityExtensionService (interfaz)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
