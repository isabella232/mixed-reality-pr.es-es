---
title: Luz de proximidad
description: Documentación sobre la luz de proximidad con ejemplos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 1adf4d1d70313c917d63224b91a14d995d1888c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145002"
---
# <a name="proximity-light"></a>Luz de proximidad

Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) es un paradigma [Sistema Fluent Design](https://www.microsoft.com/design/fluent/) que imita una "luz de punto inverso de degradado" que se mantiene cerca de la superficie de un objeto. A menudo se usa para interacciones cercanas, la aplicación puede controlar las propiedades de una luz de proximidad a través del [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente .

Para que un material se ve afectado por un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *sombreador Mixed Reality Toolkit/Standard* se debe usar y la propiedad *Luz* de proximidad debe estar habilitada.

> [!NOTE]
> Se admiten [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) hasta dos de forma predeterminada.

## <a name="examples"></a>Ejemplos

La mayoría de las escenas dentro de MRTK usan [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) un . El caso de uso más común se puede encontrar en MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab

## <a name="advanced-usage"></a>Uso avanzado

De forma predeterminada, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) solo dos pueden iluminación de un [material](https://docs.unity3d.com/ScriptReference/Material.html) a la vez. Si el proyecto requiere más de dos para influir en un material, el código de [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) ejemplo siguiente muestra cómo lograr esto. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!NOTE]
> Tener muchos [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) iluminación de un [material](https://docs.unity3d.com/ScriptReference/Material.html) aumentará las instrucciones del sombreador de píxeles y afectará al rendimiento. Desenlaza estos cambios dentro del proyecto.

*Cómo aumentar el número de disponibles [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) de dos a cuatro.*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> Si Unity registra una advertencia similar a la siguiente, debe reiniciar Unity antes de que los cambios sumen efecto.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>Consulte también

* [Sombreador estándar de MRTK](mrtk-standard-shader.md)
