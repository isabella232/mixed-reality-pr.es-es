---
title: Objetos nativos de realidad mixta en Unity
description: Obtenga información sobre cómo obtener acceso a objetos nativos holográficas subyacentes en Unity con el espacio de nombres XR.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: Unity, Mixed Reality, Native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475083"
---
# <a name="mixed-reality-native-interop-in-unity"></a><span data-ttu-id="51042-104">Interoperabilidad nativa de realidad mixta en Unity</span><span class="sxs-lookup"><span data-stu-id="51042-104">Mixed Reality native interop in Unity</span></span>

<span data-ttu-id="51042-105">Cada aplicación de realidad mixta [obtiene un HolographicSpace antes de](../native/getting-a-holographicspace.md) empezar a recibir los datos de la cámara y los fotogramas de representación.</span><span class="sxs-lookup"><span data-stu-id="51042-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="51042-106">En Unity, el motor se encarga de estos pasos, el control de los objetos holográficas y la actualización interna como parte de su bucle de representación.</span><span class="sxs-lookup"><span data-stu-id="51042-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="51042-107">Sin embargo, en escenarios avanzados, puede que necesite obtener acceso a los objetos nativos subyacentes, como <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> y <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>actuales.</span><span class="sxs-lookup"><span data-stu-id="51042-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="51042-108">Anular serialización de punteros nativos</span><span class="sxs-lookup"><span data-stu-id="51042-108">Unmarshaling native pointers</span></span>

<span data-ttu-id="51042-109">Después de obtener el `IntPtr` de uno de los métodos anteriores (no es necesario para MRTK), use los siguientes fragmentos de código para serializarlos en objetos administrados.</span><span class="sxs-lookup"><span data-stu-id="51042-109">After obtaining the `IntPtr` from one of the methods above (not needed for MRTK), use the following code snippets to marshal them to managed objects.</span></span>

<span data-ttu-id="51042-110">Si usa [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), puede construir un objeto administrado a partir de un puntero nativo mediante el `FromNativePtr()` método:</span><span class="sxs-lookup"><span data-stu-id="51042-110">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

<span data-ttu-id="51042-111">De lo contrario, use `Marshal.GetObjectForIUnknown()` y convierta al tipo que desee:</span><span class="sxs-lookup"><span data-stu-id="51042-111">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="51042-112">Convertir entre sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="51042-112">Converting between coordinate systems</span></span>

<span data-ttu-id="51042-113">Unity usa un sistema de coordenadas de la mano izquierda, mientras que las API de percepción de Windows usan sistemas de coordenadas a la derecha.</span><span class="sxs-lookup"><span data-stu-id="51042-113">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="51042-114">Para realizar la conversión entre estas dos convenciones, puede usar las siguientes aplicaciones auxiliares:</span><span class="sxs-lookup"><span data-stu-id="51042-114">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="51042-115">Uso de datos nativos de HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="51042-115">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="51042-116">Cambiar el estado de los objetos nativos recibidos a través de HolographicFrameNativeData puede producir artefactos de representación y comportamientos imprevisibles, especialmente si Unity también tiene por objeto el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="51042-116">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behavior and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="51042-117">Por ejemplo, no debe llamar a HolographicFrame. UpdateCurrentPrediction o, de lo contrario, la predicción de supuestos que Unity representa con ese marco no estará sincronizada con la que espera Windows, lo que reducirá la [estabilidad del holograma](../platform-capabilities-and-apis/hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="51042-117">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="51042-118">Si necesita tener acceso a interfaces nativas para la representación o la depuración, use los datos de HolographicFrameNativeData en los complementos nativos o en el código de C#.</span><span class="sxs-lookup"><span data-stu-id="51042-118">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span>

<span data-ttu-id="51042-119">A continuación se muestra un ejemplo de cómo se puede usar HolographicFrameNativeData para obtener la predicción del fotograma actual para la hora de Photon con las extensiones del SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="51042-119">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time using the XR SDK extensions.</span></span>

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a><span data-ttu-id="51042-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="51042-120">See Also</span></span>

* [<span data-ttu-id="51042-121">Uso del espacio de nombres de Windows con las aplicaciones de Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="51042-121">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="51042-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="51042-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="51042-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="51042-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="51042-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="51042-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="51042-125">Representación en DirectX</span><span class="sxs-lookup"><span data-stu-id="51042-125">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)
