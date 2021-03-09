---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475084"
---
# <a name="mrtk"></a>[<span data-ttu-id="6a4af-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="6a4af-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="6a4af-102">WindowsMixedRealityUtilities</span><span class="sxs-lookup"><span data-stu-id="6a4af-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="6a4af-103">**Espacio de nombres:** *Microsoft. MixedReality. Toolkit. WindowsMixedReality*</span><span class="sxs-lookup"><span data-stu-id="6a4af-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="6a4af-104">**Tipo:** *WindowsMixedRealityUtilities*</span><span class="sxs-lookup"><span data-stu-id="6a4af-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="6a4af-105">MRTK proporciona tipos ya basados en el SDK de WSA y XR heredado a través de la clase **WindowsMixedRealityUtilities** .</span><span class="sxs-lookup"><span data-stu-id="6a4af-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="6a4af-106">SDK DE XR</span><span class="sxs-lookup"><span data-stu-id="6a4af-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="6a4af-107">WindowsMREnvironment</span><span class="sxs-lookup"><span data-stu-id="6a4af-107">WindowsMREnvironment</span></span>

<span data-ttu-id="6a4af-108">**Espacio de nombres:** *UnityEngine. XR. WindowsMR*</span><span class="sxs-lookup"><span data-stu-id="6a4af-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="6a4af-109">**Tipo:** *WindowsMREnvironment*</span><span class="sxs-lookup"><span data-stu-id="6a4af-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="6a4af-110">La clase estática **WindowsMREnvironment** proporciona acceso a varios punteros nativos.</span><span class="sxs-lookup"><span data-stu-id="6a4af-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="6a4af-111">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="6a4af-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="6a4af-112">XRDevice</span><span class="sxs-lookup"><span data-stu-id="6a4af-112">XRDevice</span></span>

<span data-ttu-id="6a4af-113">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="6a4af-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="6a4af-114">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="6a4af-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="6a4af-115">El tipo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> permite obtener acceso a los objetos nativos subyacentes mediante el método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="6a4af-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="6a4af-116">Lo que GetNativePtr devuelve varía entre distintas plataformas.</span><span class="sxs-lookup"><span data-stu-id="6a4af-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="6a4af-117">En el Plataforma universal de Windows cuando el destino es Windows Mixed Reality, XRDevice. GetNativePtr devuelve un puntero (IntPtr) a la estructura siguiente:</span><span class="sxs-lookup"><span data-stu-id="6a4af-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

<span data-ttu-id="6a4af-118">Puede convertirlo en HolographicFrameNativeData mediante el método Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="6a4af-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="6a4af-119">***IHolographicCameraPtr** es una matriz de referencias de IntPtr calculadas como UnmanagedType. ByValArray con una longitud igual a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="6a4af-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
