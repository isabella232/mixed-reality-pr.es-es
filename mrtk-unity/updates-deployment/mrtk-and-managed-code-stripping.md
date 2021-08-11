---
title: MRTK y eliminación de código administrado
description: Quitar código en MRTK y Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 4348adf1d9cb2e7fc74cf5258e3272baaac96a5fc34565873cf35ae93225bdbe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221875"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK y eliminación de código administrado

Cuando se usa el back-end de scripting IL2CPP de Unity (opcional en Unity 2018.4, obligatorio en 2019 y versiones [posteriores),](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) se produce la extracción de código administrado.
El vinculador de Unity realiza este proceso para reducir el tamaño binario, así como para reducir los tiempos de compilación.

El Mixed Reality Toolkit usa un archivo, , para influir en cómo el vinculador de `link.xml` Unity procesa ensamblados MRTK. Este archivo, descrito en su totalidad en la documentación de [Unity,](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)proporciona al vinculador instrucciones sobre cómo conservar el código cuando no se puede inferir su uso (por ejemplo, se usa a través de la reflexión).

Como plataforma flexible y personalizable, MRTK crea el archivo en durante la importación, si se encuentra `link.xml` `Assets/MixedRealityToolkit.Generated` que no existe. Los archivos de link.xml existentes no se sobrescriben. Se recomienda que y `link.xml` `link.xml.meta` se agregó al control de versiones. Los desarrolladores no duden en `Assets/MixedRealityToolkit.Generated/link.xml` personalizarlo para satisfacer las necesidades del proyecto.

De forma predeterminada, link.xml archivo creado por MRTK conserva la totalidad de los ensamblados que se muestran en los datos siguientes.

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

Para obtener más información sobre el link.xml de archivos, consulte la documentación de Unity.

## <a name="see-also"></a>Consulte también

- [Unity: desmontado de código administrado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: vincular archivo XML](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
