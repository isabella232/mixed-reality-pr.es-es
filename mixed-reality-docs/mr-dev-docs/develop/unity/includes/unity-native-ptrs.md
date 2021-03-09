---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475084"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**Espacio de nombres:** *Microsoft. MixedReality. Toolkit. WindowsMixedReality*<br>
**Tipo:** *WindowsMixedRealityUtilities*

MRTK proporciona tipos ya basados en el SDK de WSA y XR heredado a través de la clase **WindowsMixedRealityUtilities** .

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[SDK DE XR](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Espacio de nombres:** *UnityEngine. XR. WindowsMR*<br>
**Tipo:** *WindowsMREnvironment*

La clase estática **WindowsMREnvironment** proporciona acceso a varios punteros nativos.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Espacio de nombres:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

El tipo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> permite obtener acceso a los objetos nativos subyacentes mediante el método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . Lo que GetNativePtr devuelve varía entre distintas plataformas. En el Plataforma universal de Windows cuando el destino es Windows Mixed Reality, XRDevice. GetNativePtr devuelve un puntero (IntPtr) a la estructura siguiente:

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

Puede convertirlo en HolographicFrameNativeData mediante el método Marshal. PtrToStructure:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** es una matriz de referencias de IntPtr calculadas como UnmanagedType. ByValArray con una longitud igual a MaxNumberOfCameras*
