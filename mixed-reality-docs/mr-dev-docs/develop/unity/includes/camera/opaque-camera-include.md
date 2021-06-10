---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748535"
---
# <a name="mrtk"></a>[<span data-ttu-id="77fe6-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="77fe6-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="77fe6-102">MRTK controlará automáticamente la configuración específica de la cámara, en función de [la configuración del perfil del sistema de la cámara.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)</span><span class="sxs-lookup"><span data-stu-id="77fe6-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="77fe6-103">**Espacio de nombres:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="77fe6-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="77fe6-104">**Tipo:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="77fe6-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="77fe6-105">Para comprobar la opacidad de la cámara, el sistema MixedRealityCamera tiene [una `IsOpaque` propiedad](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="77fe6-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="77fe6-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="77fe6-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="77fe6-107">**Espacio de nombres:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="77fe6-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="77fe6-108">**Tipo:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="77fe6-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="77fe6-109">Puede usar código de script para determinar en tiempo de ejecución si el casco es envolvente o holográfico comprobando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) en el [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)que se ejecuta activamente.</span><span class="sxs-lookup"><span data-stu-id="77fe6-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="77fe6-110">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="77fe6-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="77fe6-111">**Espacio de nombres:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="77fe6-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="77fe6-112">**Tipo:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="77fe6-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="77fe6-113">Puede usar código de script para determinar en tiempo de ejecución si el casco es envolvente o holográfico si comprueba [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span><span class="sxs-lookup"><span data-stu-id="77fe6-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>