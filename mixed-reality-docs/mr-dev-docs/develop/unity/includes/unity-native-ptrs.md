---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2021
ms.locfileid: "122264169"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**Espacio de nombres:** *Microsoft.MixedReality.Toolkit. WindowsMixedReality*<br>
**Tipo:** *WindowsMixedRealityUtilities*

MRTK proporciona tipos ya clasificados en el SDK de WSA y XR heredados a través de **la clase WindowsMixedRealityUtilities.**

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="windows-xr-plugin"></a>[Windows Complemento XR](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Espacio de nombres:** *UnityEngine.XR.WindowsMR*<br>
**Tipo:** *WindowsMREnvironment*

La clase **estática WindowsMREnvironment** proporciona acceso a varios punteros nativos.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Espacio de nombres:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

El <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**tipo XRDevice**</a> permite obtener acceso a objetos nativos subyacentes mediante el <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">método GetNativePtr.</a> Lo que devuelve GetNativePtr varía entre distintas plataformas. En la plataforma Windows universal al tener como destino Windows Mixed Reality, XRDevice.GetNativePtr devuelve un puntero (IntPtr) a la estructura siguiente:

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

Puede convertirlo a HolographicFrameNativeData mediante el método Marshal.PtrToStructure:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr es** una matriz de IntPtr serializada como UnmanagedType.ByValArray con una longitud igual a MaxNumberOfCammatriz*
