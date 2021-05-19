---
title: Luz de desplazamiento
description: Documentación sobre HoverLight con ejemplos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Hover Light,
ms.openlocfilehash: b98dff0dd3ff0312f6ce607a5fb8a26f94959ff2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145173"
---
# <a name="hover-light"></a>Luz de desplazamiento

Un es un paradigma Sistema Fluent Design que imita una luz de punto que se mantiene cerca [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) de la superficie de un objeto. [](https://www.microsoft.com/design/fluent/) [](https://docs.unity3d.com/Manual/Lighting.html) A menudo se usa para interacciones lejanas, la aplicación puede controlar las propiedades de un elemento Hover Light a través del [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente .

Para que un material se influa en un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *sombreador Mixed Reality Toolkit/Standard* se debe usar y la propiedad *Hover Light* debe estar habilitada.

> [!Note]
> El sombreador MRTK/Standard admite hasta dos de forma predeterminada, pero se escalará para admitir cuatro y, a continuación, diez a medida que se agregan más luces a [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) la escena.

## <a name="examples"></a>Ejemplos

La mayoría de las escenas dentro de MRTK usan [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) un . El caso de uso más común se puede encontrar en MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab

La **escena HoverLightExamples** también muestra el uso de comportamientos y se puede encontrar [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) en: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Uso avanzado

Solo diez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) pueden ilustrar un [material](https://docs.unity3d.com/ScriptReference/Material.html) a la vez. Si el proyecto requiere más de diez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) para influir en un [material,](https://docs.unity3d.com/ScriptReference/Material.html) el código de ejemplo siguiente muestra cómo lograrlo.

> [!Note]
> Tener muchas [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) luces de un material aumentará [las](https://docs.unity3d.com/ScriptReference/Material.html) instrucciones del sombreador de píxeles y afectará al rendimiento. **Desenlaza estos cambios en el proyecto.**

*Cómo aumentar el número de disponibles de [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) diez a doce.*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> Si Unity registra una advertencia similar a la siguiente, debe reiniciar Unity antes de que los cambios sumen efecto.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>Consulte también

* [Sombreador estándar de MRTK](mrtk-standard-shader.md)
