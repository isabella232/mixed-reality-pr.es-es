---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636363"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK actualmente no tiene ayudantes para el modo de Reproyección. Para obtener más información, consulte una de las otras pestañas.

# <a name="xr-sdk"></a>[SDK DE XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

El modo de Reproyección se puede configurar estableciendo [XRDisplaySubsystem. reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) en el valor adecuado.

Por ejemplo, si va a compilar una [experiencia solo de orientación](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenido rígidomente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de Reproyección en orientación solo si se establece en [ReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

El modo de Reproyección se puede configurar estableciendo [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) en el valor adecuado.

Por ejemplo, si va a compilar una [experiencia solo de orientación](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenido rígidomente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de Reproyección en orientación solo si se establece en [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).