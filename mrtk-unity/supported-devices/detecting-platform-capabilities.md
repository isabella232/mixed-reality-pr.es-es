---
title: DetectingPlatformCapabilities
description: Detalles de las distintas funcionalidades que admite MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, funcionalidades,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852559"
---
# <a name="detecting-platform-capabilities"></a>Detección de funcionalidades de plataforma

Una pregunta común que se hace de MRTK implica saber qué dispositivo específico (por ejemplo, Microsoft HoloLens 2) se usa para ejecutar una aplicación. Identificar el hardware exacto puede ser complicado en distintas plataformas. En su lugar, MRTK proporciona una manera de identificar funcionalidades específicas en tiempo de ejecución (por ejemplo, si el punto de conexión del dispositivo actual admite manos articuladas).

## <a name="capabilities"></a>Funciones

El Mixed Reality kit de herramientas proporciona la enumeración , que define un conjunto de funcionalidades para las que una [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) aplicación puede consultar en tiempo de ejecución.

### <a name="input-system-capabilities"></a>Funcionalidades del sistema de entrada

El sistema de entrada DE MRTK predeterminado admite la consulta de las siguientes funcionalidades:

| Capacidad | Descripción |
|---|---|
| ArticulatedHand | Entrada de mano articulada |
| EyeTracking | Objetivo de la mirada con los ojos |
| GGVHand | Entrada de la mano Mirada-Gesto-Voz |
| MotionController | Entrada del controlador de movimiento |
| VoiceCommand | Comandos de voz mediante palabras clave definidas por la aplicación |
| VoiceDictation | Dictado de voz a texto |

El código de ejemplo siguiente comprueba si el sistema de entrada ha cargado un proveedor de datos con compatibilidad con las manos articuladas.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Funcionalidades de reconocimiento espacial

El sistema de reconocimiento espacial de MRTK predeterminado admite la consulta de las siguientes funcionalidades:

| Capacidad | Descripción |
|---|---|
| SpatialAwarenessMesh | Mallas espaciales |
| SpatialAwarenessPlane | Planos espaciales |
| SpatialAwarenessPoint | Puntos espaciales |

En este ejemplo se comprueba si el sistema de reconocimiento espacial ha cargado un proveedor de datos compatible con mallas espaciales.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>Consulte también

- [Documentación de la API IMixedRealityCapabilityCheck](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Documentación de la enumeración MixedRealityCapability](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
