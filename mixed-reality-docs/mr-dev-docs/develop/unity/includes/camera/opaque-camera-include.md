---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748535"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK controlará automáticamente la configuración específica de la cámara, en función de [la configuración del perfil del sistema de la cámara.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)

**Espacio de nombres:** *Microsoft.MixedReality.Toolkit.CameraSystem*<br>
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

Puede usar código de script para determinar en tiempo de ejecución si el casco es envolvente o holográfico si comprueba [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).