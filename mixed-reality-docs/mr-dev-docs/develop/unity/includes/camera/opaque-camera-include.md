---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636364"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK controlará automáticamente la configuración de cámara específica, en función de la [configuración del perfil de sistema de la cámara](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Espacio de nombres:** *Microsoft. MixedReality. Toolkit. CameraSystem*<br>
**Tipo:** *MixedRealityCameraSystem*

Para comprobar la opacidad de la cámara, el sistema MixedRealityCamera tiene [una `IsOpaque` propiedad](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[SDK DE XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Espacio de nombres:** *UnityEngine. XR*<br>
**Tipo:** *XRDisplaySubsystem*

Puede usar el código de script para determinar en tiempo de ejecución si el casco es inmersivo o Holographic comprobando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) en el [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)que se ejecuta activamente.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Espacio de nombres:** *UnityEngine. XR. WSA*<br>
**Tipo:** *HolographicSettings*

Puede usar el código de script para determinar en tiempo de ejecución si el casco es inmersivo o Holographic comprobando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).