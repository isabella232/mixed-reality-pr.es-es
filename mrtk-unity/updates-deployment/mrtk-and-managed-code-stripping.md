---
title: MRTK y la extracción de código administrado
description: Quitar código en MRTK y Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 8b8e0f4488a6e955e599084c0b59d8c80f553a78
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176297"
---
# <a name="mrtk-and-managed-code-stripping"></a><span data-ttu-id="49c19-104">MRTK y la extracción de código administrado</span><span class="sxs-lookup"><span data-stu-id="49c19-104">MRTK and managed code stripping</span></span>

<span data-ttu-id="49c19-105">Cuando se usa el back-end de scripting IL2CPP de Unity (opcional en Unity 2018.4, obligatorio en 2019 y versiones [posteriores),](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) se produce la extracción de código administrado.</span><span class="sxs-lookup"><span data-stu-id="49c19-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="49c19-106">El vinculador de Unity realiza este proceso para reducir el tamaño binario, así como para reducir los tiempos de compilación.</span><span class="sxs-lookup"><span data-stu-id="49c19-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="49c19-107">El Mixed Reality Toolkit usa un archivo, , para influir en cómo el vinculador de `link.xml` Unity procesa ensamblados MRTK.</span><span class="sxs-lookup"><span data-stu-id="49c19-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="49c19-108">Este archivo, descrito en su totalidad en la documentación de [Unity,](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)proporciona al vinculador instrucciones sobre cómo conservar el código cuando no se puede inferir su uso (por ejemplo, se usa a través de la reflexión).</span><span class="sxs-lookup"><span data-stu-id="49c19-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="49c19-109">Como plataforma flexible y personalizable, MRTK crea el archivo en durante la importación, si se encuentra `link.xml` `Assets/MixedRealityToolkit.Generated` que no existe.</span><span class="sxs-lookup"><span data-stu-id="49c19-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="49c19-110">Los archivos de link.xml existentes no se sobrescriben.</span><span class="sxs-lookup"><span data-stu-id="49c19-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="49c19-111">Se recomienda que y `link.xml` se agregan al control de `link.xml.meta` versiones.</span><span class="sxs-lookup"><span data-stu-id="49c19-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="49c19-112">Los desarrolladores deben tener la libertad de `Assets/MixedRealityToolkit.Generated/link.xml` personalizar para satisfacer las necesidades del proyecto.</span><span class="sxs-lookup"><span data-stu-id="49c19-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="49c19-113">De forma predeterminada, link.xml archivo creado por MRTK conserva la totalidad de los ensamblados que se muestran en los datos siguientes.</span><span class="sxs-lookup"><span data-stu-id="49c19-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

<span data-ttu-id="49c19-114">Para obtener más información sobre el link.xml de archivos, consulte la documentación de Unity.</span><span class="sxs-lookup"><span data-stu-id="49c19-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="49c19-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="49c19-115">See also</span></span>

- [<span data-ttu-id="49c19-116">Unity: desmontado de código administrado</span><span class="sxs-lookup"><span data-stu-id="49c19-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="49c19-117">Unity: vincular archivo XML</span><span class="sxs-lookup"><span data-stu-id="49c19-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
