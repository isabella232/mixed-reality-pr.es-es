---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636364"
---
# <a name="mrtk"></a>[<span data-ttu-id="19307-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="19307-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="19307-102">MRTK controlará automáticamente la configuración de cámara específica, en función de la [configuración del perfil de sistema de la cámara](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span><span class="sxs-lookup"><span data-stu-id="19307-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="19307-103">**Espacio de nombres:** *Microsoft. MixedReality. Toolkit. CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="19307-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="19307-104">**Tipo:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="19307-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="19307-105">Para comprobar la opacidad de la cámara, el sistema MixedRealityCamera tiene [una `IsOpaque` propiedad](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="19307-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="19307-106">SDK DE XR</span><span class="sxs-lookup"><span data-stu-id="19307-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="19307-107">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="19307-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="19307-108">**Tipo:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="19307-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="19307-109">Puede usar el código de script para determinar en tiempo de ejecución si el casco es inmersivo o Holographic comprobando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) en el [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)que se ejecuta activamente.</span><span class="sxs-lookup"><span data-stu-id="19307-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="19307-110">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="19307-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="19307-111">**Espacio de nombres:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="19307-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="19307-112">**Tipo:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="19307-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="19307-113">Puede usar el código de script para determinar en tiempo de ejecución si el casco es inmersivo o Holographic comprobando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span><span class="sxs-lookup"><span data-stu-id="19307-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>