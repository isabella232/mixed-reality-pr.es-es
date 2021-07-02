---
title: Primitiva de recorte
description: Documentación sobre primitivos de recorte con ejemplos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, primitivo de recorte,
ms.openlocfilehash: c3331084f87ccc57208426910d84ed7bef457bc1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176747"
---
# <a name="clipping-primitive"></a><span data-ttu-id="accac-104">Primitiva de recorte</span><span class="sxs-lookup"><span data-stu-id="accac-104">Clipping primitive</span></span>

<span data-ttu-id="accac-105">Los comportamientos permiten el recorte de formas , y con la capacidad de especificar en qué lado de la primitiva se va a recortar (dentro o fuera) cuando se usa con sombreadores [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK.</span><span class="sxs-lookup"><span data-stu-id="accac-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![gizmos de recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="accac-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) use [instrucciones de recorte y descarte](https://developer.download.nvidia.com/cg/clip.html) dentro de los sombreadores y deshabilite la capacidad de Unity para procesar por lotes representadores recortados.</span><span class="sxs-lookup"><span data-stu-id="accac-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="accac-108">Al usar primitivas de recorte, debe tener en cuenta estas implicaciones de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="accac-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="accac-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) y se pueden usar para controlar fácilmente las propiedades [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) primitivas de recorte.</span><span class="sxs-lookup"><span data-stu-id="accac-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="accac-110">Use estos componentes con los siguientes sombreadores para aprovechar los escenarios de recorte.</span><span class="sxs-lookup"><span data-stu-id="accac-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="accac-111">*Mixed Reality Toolkit/Estándar*</span><span class="sxs-lookup"><span data-stu-id="accac-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="accac-112">*Mixed Reality Toolkit/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="accac-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="accac-113">*Mixed Reality Toolkit/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="accac-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="accac-114">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="accac-114">Examples</span></span>

<span data-ttu-id="accac-115">Las **escenas ClippingExamples** y **MaterialGallery** muestran el uso de los comportamientos y se pueden encontrar [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) en: MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="accac-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="accac-116">Uso avanzado</span><span class="sxs-lookup"><span data-stu-id="accac-116">Advanced Usage</span></span>

<span data-ttu-id="accac-117">De forma predeterminada, [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) solo uno puede recortar un [representador](https://docs.unity3d.com/ScriptReference/Renderer.html) a la vez.</span><span class="sxs-lookup"><span data-stu-id="accac-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="accac-118">Si el proyecto requiere más de uno para influir en un representador, el código de ejemplo [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) siguiente muestra cómo lograr esto. [](https://docs.unity3d.com/ScriptReference/Renderer.html)</span><span class="sxs-lookup"><span data-stu-id="accac-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="accac-119">Tener varios [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clips un [representador aumentará](https://docs.unity3d.com/ScriptReference/Renderer.html) las instrucciones del sombreador de píxeles y afectará al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="accac-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="accac-120">Desenlaza estos cambios dentro del proyecto.</span><span class="sxs-lookup"><span data-stu-id="accac-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="accac-121">*Cómo hacer que dos clips [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) diferentes se represente. Por ejemplo, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) y [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) al mismo tiempo:*</span><span class="sxs-lookup"><span data-stu-id="accac-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="accac-122">El cambio anterior incurrirá en tiempo de compilación de sombreador adicional.</span><span class="sxs-lookup"><span data-stu-id="accac-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="accac-123">*Cómo hacer que dos de los mismos [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) recorten una representación. Por ejemplo, dos [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) al mismo tiempo:*</span><span class="sxs-lookup"><span data-stu-id="accac-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

<span data-ttu-id="accac-124">Por último, agregue un componente y SecondClippingBox a la escena y [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) especifique el mismo representador para ambos cuadros.</span><span class="sxs-lookup"><span data-stu-id="accac-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="accac-125">Ahora ambos cuadros deben recortar el representador simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="accac-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="accac-126">Consulte también</span><span class="sxs-lookup"><span data-stu-id="accac-126">See also</span></span>

- [<span data-ttu-id="accac-127">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="accac-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
