---
title: Depuración administrada con Unity
description: En este artículo se explica cómo ejecutar un depurador administrado en el proyecto de Unity IL2CPP para UWP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, Visual Studio, depuración, il2cpp, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547084"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="cf0eb-104">Depuración administrada con Unity</span><span class="sxs-lookup"><span data-stu-id="cf0eb-104">Managed debugging with Unity</span></span>

<span data-ttu-id="cf0eb-105">Siga estos pasos para asociar un depurador administrado a la compilación de Unity IL2CPP para UWP para HoloLens y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="cf0eb-106">Deberá estar en una red que admita [multidifusión.](https://en.wikipedia.org/wiki/Multicast)</span><span class="sxs-lookup"><span data-stu-id="cf0eb-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="cf0eb-107">Vaya a **Funcionalidades de configuración de publicación de UWP** y compruebe **InternetClientServer** y **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="cf0eb-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funcionalidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="cf0eb-109">Configure las opciones de compilación de Unity para UWP:</span><span class="sxs-lookup"><span data-stu-id="cf0eb-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="cf0eb-110">Compilación de desarrollo</span><span class="sxs-lookup"><span data-stu-id="cf0eb-110">Development Build</span></span>
    - <span data-ttu-id="cf0eb-111">Depuración de script</span><span class="sxs-lookup"><span data-stu-id="cf0eb-111">Script Debugging</span></span>
    - <span data-ttu-id="cf0eb-112">Esperar a Managed Debugger (opcional)</span><span class="sxs-lookup"><span data-stu-id="cf0eb-112">Wait for Managed Debugger (optional)</span></span>

    ![Configuración de compilación de UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="cf0eb-114">Compilación en Unity.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-114">Build in Unity.</span></span>
5. <span data-ttu-id="cf0eb-115">Compile e implemente desde la Visual Studio en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="cf0eb-116">Debe compilar con las **configuraciones Debug** **o Release.**</span><span class="sxs-lookup"><span data-stu-id="cf0eb-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="cf0eb-117">La **configuración** maestra deshabilita el profiler de Unity y puede impedir una depuración óptima.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="cf0eb-118">Opcionalmente, compruebe **Internet (servidor** cliente &) y redes privadas **(servidor cliente &)** en la lista de funcionalidades de Package.appxmanifest en la solución.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="cf0eb-119">Asegúrese de que el dispositivo está conectado a la misma red que el equipo e inicie la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="cf0eb-120">Asegúrese de que el **dispositivo no está** conectado al equipo a través de USB.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="cf0eb-121">Haga doble clic en uno de los scripts de Unity y vaya a la Visual Studio que se abre para ver y editar.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="cf0eb-122">Depurar -> Adjuntar depurador de Unity.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-122">Debug -> Attach Unity Debugger.</span></span>

    ![Adjuntar depurador de Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="cf0eb-124">Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntarlo.</span><span class="sxs-lookup"><span data-stu-id="cf0eb-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
