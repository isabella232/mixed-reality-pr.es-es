---
title: Registro del servicio de Mixed Reality
description: Documentación sobre MixedRealityServiceRegistry e IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 16aea46890297dab209c13b6776a0a571b1e05bf5021a5795a33dc88366ee9b1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217441"
---
# <a name="mixed-reality-service-registry"></a>Registro del servicio de Mixed Reality

El Mixed Reality Toolkit tiene dos componentes con nombre muy similares que realizan tareas relacionadas: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) es el componente que contiene instancias de cada servicio registrado (sistemas principales y servicios de extensión).

> [!NOTE]
> MixedRealityServiceRegistry contiene instancias de objetos que implementan la interfaz [IMixedRealityService,](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) incluido [IMixedRealityExtensionService.](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
>
>Los objetos que implementan [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (una subclase de IMixedRealityService) no se registran explícitamente en MixedRealityServiceRegistry. Estos objetos se administran mediante los servicios individuales (por ejemplo, reconocimiento espacial).

MixedRealityServiceRegistry se implementa como una clase estática de C# y es el patrón recomendado que se usa para adquirir instancias de servicio en el código de la aplicación.

En el fragmento de código siguiente se muestra cómo adquirir una instancia de IMixedRealityInputSystem.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) es la interfaz que define la funcionalidad implementada por los componentes que administran el registro de uno o varios servicios. Los componentes que implementan IMixedRealityServiceRegistrar son responsables de agregar y quitar los datos dentro de MixedRealityServiceRegistry. El [objeto MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) es uno de estos componentes.

Puede encontrar otros registradores en la carpeta MRTK/SDK/Experimental/Features. Estos componentes se pueden usar para agregar compatibilidad con un solo servicio (por ejemplo, reconocimiento espacial) a una aplicación. Estos administradores de servicios únicos se enumeran a continuación.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Cada uno de los componentes anteriores, a excepción de InputSystemManager, es responsable de administrar el registro y el estado de un único tipo de servicio. InputSystem requiere algunos servicios de soporte técnico adicionales (por ejemplo, FocusProvider) que también administra InputSystemManager.

En general, los componentes de administración de servicios llaman internamente a los métodos definidos por IMixedRealityServiceRegistrar o a los servicios que requieren componentes de servicio adicionales para funcionar correctamente. Por lo general, el código de la aplicación no debe llamar a estos métodos, ya que puede provocar que la aplicación se comporte de forma imprevisible (por ejemplo, una instancia de servicio almacenada en caché puede dejar de ser válida).

## <a name="see-also"></a>Consulte también

- [Documentación de la API IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Documentación de la API MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
