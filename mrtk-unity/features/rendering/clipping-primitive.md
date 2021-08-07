---
title: Primitivo de recorte
description: Documentación sobre primitivos de recorte con ejemplos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, primitivo de recorte,
ms.openlocfilehash: 1feecbbd51eb80ff6113e66d053f032acb3005b9c7d1debbd5dfd46da0925798
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214422"
---
# <a name="clipping-primitive"></a>Primitivo de recorte

Los comportamientos permiten el recorte de formas , y con la capacidad de especificar en qué lado de la primitiva se va a recortar (dentro o fuera) cuando se usa con sombreadores [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK.

![gizmos de recorte primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) use [instrucciones de recorte y descarte](https://developer.download.nvidia.com/cg/clip.html) en sombreadores y deshabilite la capacidad de Unity para procesar por lotes representadores recortados. Al usar primitivas de recorte, debe tener en cuenta estas implicaciones de rendimiento.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) y se pueden usar para controlar fácilmente las propiedades [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) primitivas de recorte. Use estos componentes con los siguientes sombreadores para aprovechar los escenarios de recorte.

- *Mixed Reality Toolkit/Estándar*
- *Mixed Reality Toolkit/TextMeshPro*
- *Mixed Reality Toolkit/Text3DShader*

## <a name="examples"></a>Ejemplos

Las **escenas ClippingExamples** y **MaterialGallery** muestran el uso de los comportamientos y se pueden encontrar [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) en: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Uso avanzado

De forma predeterminada, [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) solo uno puede recortar un [representador](https://docs.unity3d.com/ScriptReference/Renderer.html) a la vez. Si el proyecto requiere más de uno para influir en un representador, el código de ejemplo [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) siguiente muestra cómo lograr esto. [](https://docs.unity3d.com/ScriptReference/Renderer.html)

> [!NOTE]
> Tener varios [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clips un [representador aumentará](https://docs.unity3d.com/ScriptReference/Renderer.html) las instrucciones del sombreador de píxeles y afectará al rendimiento. Desenlaza estos cambios dentro del proyecto.

*Cómo hacer que dos clips [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) diferentes se represente. Por ejemplo, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) y [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) al mismo tiempo:*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> El cambio anterior incurrirá en tiempo de compilación de sombreador adicional.

*Cómo hacer que dos de los mismos [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) recorten una representación. Por ejemplo, dos [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) al mismo tiempo:*

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

Por último, agregue un componente y SecondClippingBox a la escena y [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) especifique el mismo representador para ambos cuadros. Ahora ambos cuadros deben recortar el representador simultáneamente.

## <a name="see-also"></a>Consulte también

- [Sombreador estándar de MRTK](mrtk-standard-shader.md)
