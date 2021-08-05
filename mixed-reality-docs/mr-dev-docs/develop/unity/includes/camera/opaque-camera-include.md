---
ms.openlocfilehash: 73aba70497323d406b5138eca9c7d2054b8d8b3cea6e82ef67e962a21876c280
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212335"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK controlará automáticamente la configuración específica de la cámara, en función de [la configuración del perfil del sistema de la cámara.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)

**Espacio de nombres:** *Microsoft.MixedReality.Toolkit. CameraSystem*<br>
**Tipo:** *MixedRealityCameraSystem*

Para comprobar la opacidad de la cámara, el sistema MixedRealityCamera tiene [una `IsOpaque` propiedad](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Espacio de nombres:** *UnityEngine.XR*<br>
**Tipo:** *XRDisplaySubsystem*

Puede usar código de script para determinar en tiempo de ejecución si el casco es envolvente o holográfico comprobando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) en el [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)que se ejecuta activamente.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Espacio de nombres:** *UnityEngine.XR.WSA*<br>
**Tipo:** *HolographicSettings*

Puede usar código de script para determinar en tiempo de ejecución si el casco es envolvente o holográfico comprobando [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).