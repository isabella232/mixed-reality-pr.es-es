---
title: Mantener el puntero sobre la luz
description: Documentación sobre HoverLight con ejemplos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Hover Light,
ms.openlocfilehash: ed45d3345931376283cfca2372ac57459c777f6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176737"
---
# <a name="hover-light"></a>Mantener el puntero sobre la luz

Un es un paradigma Sistema Fluent Design que imita una luz de punto que se mantiene cerca [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) de la superficie de un objeto. [](https://www.microsoft.com/design/fluent/) [](https://docs.unity3d.com/Manual/Lighting.html) A menudo se usa para interacciones lejanas, la aplicación puede controlar las propiedades de un elemento Hover Light a través del [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente .

Para que un material se influye en un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *sombreador Mixed Reality Toolkit/Estándar* se debe usar y la propiedad *Hover Light* debe estar habilitada.

> [!Note]
> El sombreador MRTK/Standard admite hasta dos de forma predeterminada, pero se escalará para admitir cuatro y diez a medida que se agregan más luces a [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) la escena.

## <a name="examples"></a>Ejemplos

La mayoría de las escenas dentro de MRTK usan [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) un . El caso de uso más común se puede encontrar en MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab

La **escena HoverLightExamples** también muestra el uso de comportamientos y se puede encontrar [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) en: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Uso avanzado

Solo diez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) pueden iluminación de un [material](https://docs.unity3d.com/ScriptReference/Material.html) a la vez. Si el proyecto requiere más de diez para influir en un material, el código de [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) ejemplo siguiente muestra cómo lograr esto. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!Note]
> Tener muchos [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) iluminación de un material aumentará las instrucciones del [sombreador](https://docs.unity3d.com/ScriptReference/Material.html) de píxeles y afectará al rendimiento. **Desenlaza estos cambios dentro del proyecto.**

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
