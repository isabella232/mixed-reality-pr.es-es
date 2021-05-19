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
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a>¿Qué son MixedRealityServiceRegistry e IMixedRealityServiceRegistrar?

El Mixed Reality toolkit tiene dos componentes con nombre muy similares que realizan tareas relacionadas: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry es](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) el componente que contiene instancias de cada servicio registrado (sistemas principales y servicios de extensión).

> [!NOTE]
> MixedRealityServiceRegistry contiene instancias de objetos que implementan la interfaz [IMixedRealityService,](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) incluido [IMixedRealityExtensionService.](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
>
>Los objetos que implementan [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (una subclase de IMixedRealityService) no se registran explícitamente en MixedRealityServiceRegistry. Estos objetos se administran mediante los servicios individuales (por ejemplo, reconocimiento espacial).

MixedRealityServiceRegistry se implementa como una clase estática de C# y es el patrón recomendado para adquirir instancias de servicio en el código de la aplicación.

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

Puede encontrar otros registradores en la carpeta MRTK/SDK/Experimental/Features. Estos componentes se pueden usar para agregar compatibilidad con un único servicio (por ejemplo, reconocimiento espacial) a una aplicación. Estos administradores de servicios únicos se enumeran a continuación.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Cada uno de los componentes anteriores, a excepción de InputSystemManager, es responsable de administrar el registro y el estado de un único tipo de servicio. InputSystem requiere algunos servicios de soporte técnico adicionales (por ejemplo, FocusProvider) que también administra InputSystemManager.

En general, los componentes de administración de servicios llaman internamente a los métodos definidos por IMixedRealityServiceRegistrar o a los servicios que requieren componentes de servicio adicionales para funcionar correctamente. Por lo general, el código de la aplicación no debe llamar a estos métodos, ya que puede provocar que la aplicación se comporte de forma impredecible (por ejemplo, una instancia de servicio almacenada en caché puede dejar de ser válida).

## <a name="see-also"></a>Consulte también

- [Documentación de la API IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Documentación de la API MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
