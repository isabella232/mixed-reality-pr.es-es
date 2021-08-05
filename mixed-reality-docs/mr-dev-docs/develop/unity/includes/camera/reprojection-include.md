---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212336"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK no tiene actualmente asistentes para el modo de reproducción. Consulte una de las otras pestañas para obtener más información.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

El modo de reproducción se puede configurar estableciendo [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) en el valor adecuado.

Por ejemplo, si va [a](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) crear una experiencia de solo orientación con contenido rígidamente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de reproducción en orientación si lo establece en [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

El modo de reproducción se puede configurar estableciendo [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) en el valor adecuado.

Por ejemplo, si va [a](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) crear una experiencia de solo orientación con contenido rígidamente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de reproducción en orientación si solo lo establece en [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).