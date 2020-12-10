---
title: Depuración administrada con Unity IL2CPP
description: En este artículo se explica cómo ejecutar un depurador administrado en el proyecto de IL2CPP para UWP de Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, depuración, il2cpp, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010246"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="9e7d7-104">Depuración administrada con Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="9e7d7-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="9e7d7-105">Siga estos pasos para asociar un depurador administrado a la compilación de UWP IL2CPP para HoloLens y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="9e7d7-106">Deberá estar en una red que admita la [multidifusión](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="9e7d7-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="9e7d7-107">Vaya a la **configuración de publicación de UWP funcionalidades** y compruebe **InternetClientServer** y **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="9e7d7-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funcionalidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="9e7d7-109">Configurar las opciones de compilación de UWP para Unity:</span><span class="sxs-lookup"><span data-stu-id="9e7d7-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="9e7d7-110">Compilación de desarrollo</span><span class="sxs-lookup"><span data-stu-id="9e7d7-110">Development Build</span></span>
    - <span data-ttu-id="9e7d7-111">Depuración de script</span><span class="sxs-lookup"><span data-stu-id="9e7d7-111">Script Debugging</span></span>
    - <span data-ttu-id="9e7d7-112">Esperar al depurador administrado (opcional)</span><span class="sxs-lookup"><span data-stu-id="9e7d7-112">Wait for Managed Debugger (optional)</span></span>

    ![Configuración de compilación de UWP](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="9e7d7-114">Compilar en Unity.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-114">Build in Unity.</span></span>
5. <span data-ttu-id="9e7d7-115">Compile e implemente desde la solución de Visual Studio en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="9e7d7-116">Debe compilar con las configuraciones de **depuración** o de **lanzamiento** .</span><span class="sxs-lookup"><span data-stu-id="9e7d7-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="9e7d7-117">La configuración **maestra** deshabilita el generador de perfiles de Unity y puede impedir la depuración óptima.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="9e7d7-118">Opcionalmente, compruebe **Internet (cliente & servidor)** y **redes privadas (servidor de & de cliente)** en la lista de capacidades de Package. appxmanifest en la solución.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="9e7d7-119">Asegúrese de que el dispositivo está conectado a la misma red que el equipo e inicie la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="9e7d7-120">Asegúrese de que el dispositivo **no está** conectado al equipo a través de USB.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="9e7d7-121">Haga doble clic en uno de los scripts en Unity y vaya a la solución de Visual Studio que se abre para ver y editar.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="9e7d7-122">Debug: > adjuntar el depurador de Unity.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-122">Debug -> Attach Unity Debugger.</span></span>

    ![Adjuntar depurador de Unity](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="9e7d7-124">Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntarlo.</span><span class="sxs-lookup"><span data-stu-id="9e7d7-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
