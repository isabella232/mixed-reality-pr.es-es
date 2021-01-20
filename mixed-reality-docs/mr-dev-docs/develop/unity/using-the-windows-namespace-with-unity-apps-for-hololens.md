---
title: API de WinRT con Unity para HoloLens
description: Más eficiente cómo hacer uso de las API de WinRT y el espacio de nombres de Windows en los proyectos de la realidad mixta de Unity para HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, tutorial, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, API de realidad mixta
ms.openlocfilehash: 2116f0025449fdf127998e605f87de456e9bdaf9
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583557"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="25b9c-104">API de WinRT con Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="25b9c-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="25b9c-105">En esta página se describe cómo hacer uso de las API de WinRT en el proyecto de Unity para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="25b9c-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="25b9c-106">API de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="25b9c-106">Mixed Reality APIs</span></span>

<span data-ttu-id="25b9c-107">Un subconjunto centrado en la realidad mixta del Windows SDK se ha puesto a disposición en una proyección compatible con .NET Standard 2,0, que puede usar en el proyecto sin las directivas de preprocesador.</span><span class="sxs-lookup"><span data-stu-id="25b9c-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="25b9c-108">La mayoría de las API de Windows.</span><span class="sxs-lookup"><span data-stu-id="25b9c-108">Most APIs in the Windows.</span></span> <span data-ttu-id="25b9c-109">Los espacios de nombres imception y Windows. UI. Input. Spatial se incluyen y se pueden expandir para incluir API adicionales en el futuro.</span><span class="sxs-lookup"><span data-stu-id="25b9c-109">Perception and Windows.UI.Input.Spatial namespaces are included and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="25b9c-110">Las API proyectadas se pueden usar mientras se ejecutan en el editor, lo que permite el uso del [modo de reproducción](//windows/mixed-reality/unity-play-mode).</span><span class="sxs-lookup"><span data-stu-id="25b9c-110">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="25b9c-111">Para usar esta proyección, realice las siguientes modificaciones en el proyecto:</span><span class="sxs-lookup"><span data-stu-id="25b9c-111">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="25b9c-112">Agregue una referencia al paquete de Nuget [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) mediante [Nuget para Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="25b9c-112">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="25b9c-113">Referencias de prefijo al `Windows` espacio de nombres con `Microsoft.` :</span><span class="sxs-lookup"><span data-stu-id="25b9c-113">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="25b9c-114">Reemplace las conversiones de puntero nativas por `FromNativePtr` :</span><span class="sxs-lookup"><span data-stu-id="25b9c-114">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="25b9c-115">Inclusión condicional de llamadas API de WinRT</span><span class="sxs-lookup"><span data-stu-id="25b9c-115">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="25b9c-116">También puede usar las API de WinRT en proyectos de Unity creados para el Plataforma universal de Windows y la plataforma Xbox One mediante directivas de preprocesador.</span><span class="sxs-lookup"><span data-stu-id="25b9c-116">You can also use the WinRT APIs in Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives.</span></span> <span data-ttu-id="25b9c-117">Cualquier código que escriba en scripts de Unity que tengan como destino las API de WinRT debe incluirse condicionalmente solo para esas compilaciones.</span><span class="sxs-lookup"><span data-stu-id="25b9c-117">Any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="25b9c-118">Esto puede hacerse a través de dos pasos en Unity:</span><span class="sxs-lookup"><span data-stu-id="25b9c-118">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="25b9c-119">El nivel de compatibilidad de API debe establecerse en **.net 4,6** o **.net Standard 2,0** en la configuración del reproductor.</span><span class="sxs-lookup"><span data-stu-id="25b9c-119">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="25b9c-120">**Editar**  >  **Configuración**  >  del proyecto **Reproductor**  >  de **Configuración**  >  de **Nivel de compatibilidad de API** a **.net 4,6** o **.net Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="25b9c-120">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="25b9c-121">La Directiva de preprocesador **ENABLE_WINMD_SUPPORT** debe ajustarse alrededor de cualquier código aprovechado por WinRT</span><span class="sxs-lookup"><span data-stu-id="25b9c-121">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="25b9c-122">El siguiente fragmento de código procede de la página manual de Unity para [plataforma universal de Windows: API de WinRT en scripts de C#](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="25b9c-122">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="25b9c-123">En este ejemplo, se devuelve un identificador de anuncio, pero solo en las compilaciones de UWP y Xbox One:</span><span class="sxs-lookup"><span data-stu-id="25b9c-123">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="25b9c-124">Editar los scripts en un proyecto de C# de Unity</span><span class="sxs-lookup"><span data-stu-id="25b9c-124">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="25b9c-125">Al hacer doble clic en un script en el editor de Unity, se iniciará el script de forma predeterminada en un proyecto de editor.</span><span class="sxs-lookup"><span data-stu-id="25b9c-125">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="25b9c-126">Parece que las API de WinRT son desconocidas porque el proyecto de Visual Studio no hace referencia al Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="25b9c-126">The WinRT APIs will appear to be unknown because the Visual Studio project doesn't reference the Windows Runtime.</span></span> <span data-ttu-id="25b9c-127">La directiva **ENABLE_WINMD_SUPPORT** no está definida y cualquier código ajustado *#if* se omite hasta que compile el proyecto en una solución de Visual Studio para UWP.</span><span class="sxs-lookup"><span data-stu-id="25b9c-127">The **ENABLE_WINMD_SUPPORT** directive is undefined and any *#if* wrapped code is ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="25b9c-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="25b9c-128">See also</span></span>
* [<span data-ttu-id="25b9c-129">Exportación y creación de una solución de Visual Studio para Unity</span><span class="sxs-lookup"><span data-stu-id="25b9c-129">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="25b9c-130">Windows Runtime admite Unity</span><span class="sxs-lookup"><span data-stu-id="25b9c-130">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)