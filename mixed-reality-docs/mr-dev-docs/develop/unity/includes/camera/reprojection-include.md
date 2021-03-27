---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636363"
---
# <a name="mrtk"></a>[<span data-ttu-id="b2ba7-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="b2ba7-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b2ba7-102">MRTK actualmente no tiene ayudantes para el modo de Reproyección.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="b2ba7-103">Para obtener más información, consulte una de las otras pestañas.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="b2ba7-104">SDK DE XR</span><span class="sxs-lookup"><span data-stu-id="b2ba7-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b2ba7-105">El modo de Reproyección se puede configurar estableciendo [XRDisplaySubsystem. reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) en el valor adecuado.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="b2ba7-106">Por ejemplo, si va a compilar una [experiencia solo de orientación](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenido rígidomente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de Reproyección en orientación solo si se establece en [ReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="b2ba7-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="b2ba7-107">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="b2ba7-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b2ba7-108">El modo de Reproyección se puede configurar estableciendo [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) en el valor adecuado.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="b2ba7-109">Por ejemplo, si va a compilar una [experiencia solo de orientación](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenido rígidomente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de Reproyección en orientación solo si se establece en [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="b2ba7-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>