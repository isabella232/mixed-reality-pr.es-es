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
# <a name="hover-light"></a><span data-ttu-id="f4e12-104">Mantener el puntero sobre la luz</span><span class="sxs-lookup"><span data-stu-id="f4e12-104">Hover light</span></span>

<span data-ttu-id="f4e12-105">Un es un paradigma Sistema Fluent Design que imita una luz de punto que se mantiene cerca [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) de la superficie de un objeto. [](https://www.microsoft.com/design/fluent/) [](https://docs.unity3d.com/Manual/Lighting.html)</span><span class="sxs-lookup"><span data-stu-id="f4e12-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="f4e12-106">A menudo se usa para interacciones lejanas, la aplicación puede controlar las propiedades de un elemento Hover Light a través del [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente .</span><span class="sxs-lookup"><span data-stu-id="f4e12-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="f4e12-107">Para que un material se influye en un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *sombreador Mixed Reality Toolkit/Estándar* se debe usar y la propiedad *Hover Light* debe estar habilitada.</span><span class="sxs-lookup"><span data-stu-id="f4e12-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="f4e12-108">El sombreador MRTK/Standard admite hasta dos de forma predeterminada, pero se escalará para admitir cuatro y diez a medida que se agregan más luces a [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) la escena.</span><span class="sxs-lookup"><span data-stu-id="f4e12-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="f4e12-109">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="f4e12-109">Examples</span></span>

<span data-ttu-id="f4e12-110">La mayoría de las escenas dentro de MRTK usan [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) un .</span><span class="sxs-lookup"><span data-stu-id="f4e12-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="f4e12-111">El caso de uso más común se puede encontrar en MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span><span class="sxs-lookup"><span data-stu-id="f4e12-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="f4e12-112">La **escena HoverLightExamples** también muestra el uso de comportamientos y se puede encontrar [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) en: MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="f4e12-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="f4e12-113">Uso avanzado</span><span class="sxs-lookup"><span data-stu-id="f4e12-113">Advanced Usage</span></span>

<span data-ttu-id="f4e12-114">Solo diez [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) pueden iluminación de un [material](https://docs.unity3d.com/ScriptReference/Material.html) a la vez.</span><span class="sxs-lookup"><span data-stu-id="f4e12-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="f4e12-115">Si el proyecto requiere más de diez para influir en un material, el código de [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) ejemplo siguiente muestra cómo lograr esto. [](https://docs.unity3d.com/ScriptReference/Material.html)</span><span class="sxs-lookup"><span data-stu-id="f4e12-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="f4e12-116">Tener muchos [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) iluminación de un material aumentará las instrucciones del [sombreador](https://docs.unity3d.com/ScriptReference/Material.html) de píxeles y afectará al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="f4e12-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="f4e12-117">**Desenlaza estos cambios dentro del proyecto.**</span><span class="sxs-lookup"><span data-stu-id="f4e12-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="f4e12-118">*Cómo aumentar el número de disponibles de [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) diez a doce.*</span><span class="sxs-lookup"><span data-stu-id="f4e12-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

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
> <span data-ttu-id="f4e12-119">Si Unity registra una advertencia similar a la siguiente, debe reiniciar Unity antes de que los cambios sumen efecto.</span><span class="sxs-lookup"><span data-stu-id="f4e12-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="f4e12-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f4e12-120">See also</span></span>

* [<span data-ttu-id="f4e12-121">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="f4e12-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
