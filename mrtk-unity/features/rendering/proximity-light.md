---
title: Luz de proximidad
description: Documentación sobre la luz de proximidad con ejemplos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 6e57a76d54d0f3f63ce8dcb80582e178effa39d9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176379"
---
# <a name="proximity-light"></a><span data-ttu-id="1a71e-104">Luz de proximidad</span><span class="sxs-lookup"><span data-stu-id="1a71e-104">Proximity light</span></span>

<span data-ttu-id="1a71e-105">Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) es un paradigma [Sistema Fluent Design](https://www.microsoft.com/design/fluent/) que imita una "luz de punto inverso de degradado" que se mantiene cerca de la superficie de un objeto.</span><span class="sxs-lookup"><span data-stu-id="1a71e-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="1a71e-106">A menudo se usa para interacciones cercanas, la aplicación puede controlar las propiedades de una luz de proximidad a través del [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente .</span><span class="sxs-lookup"><span data-stu-id="1a71e-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="1a71e-107">Para que un material se influye en un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *sombreador Mixed Reality Toolkit/Estándar* se debe usar y la propiedad *Luz* de proximidad debe estar habilitada.</span><span class="sxs-lookup"><span data-stu-id="1a71e-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="1a71e-108">De forma [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) predeterminada, se admiten hasta dos.</span><span class="sxs-lookup"><span data-stu-id="1a71e-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="1a71e-109">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="1a71e-109">Examples</span></span>

<span data-ttu-id="1a71e-110">La mayoría de las escenas dentro de MRTK usan [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) un .</span><span class="sxs-lookup"><span data-stu-id="1a71e-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="1a71e-111">El caso de uso más común se puede encontrar en MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span><span class="sxs-lookup"><span data-stu-id="1a71e-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="1a71e-112">Uso avanzado</span><span class="sxs-lookup"><span data-stu-id="1a71e-112">Advanced Usage</span></span>

<span data-ttu-id="1a71e-113">De forma predeterminada, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) solo dos pueden ilustrar un [material](https://docs.unity3d.com/ScriptReference/Material.html) a la vez.</span><span class="sxs-lookup"><span data-stu-id="1a71e-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="1a71e-114">Si el proyecto requiere más de dos [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) para influir en un [material,](https://docs.unity3d.com/ScriptReference/Material.html) el código de ejemplo siguiente muestra cómo lograrlo.</span><span class="sxs-lookup"><span data-stu-id="1a71e-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="1a71e-115">Tener muchas [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) luces de un [material](https://docs.unity3d.com/ScriptReference/Material.html) aumentará las instrucciones del sombreador de píxeles y afectará al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="1a71e-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="1a71e-116">Desenlaza estos cambios en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a71e-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="1a71e-117">*Cómo aumentar el número de disponibles [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) de dos a cuatro.*</span><span class="sxs-lookup"><span data-stu-id="1a71e-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

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
> <span data-ttu-id="1a71e-118">Si Unity registra una advertencia similar a la siguiente, debe reiniciar Unity antes de que los cambios sumen efecto.</span><span class="sxs-lookup"><span data-stu-id="1a71e-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="1a71e-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1a71e-119">See also</span></span>

* [<span data-ttu-id="1a71e-120">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="1a71e-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
