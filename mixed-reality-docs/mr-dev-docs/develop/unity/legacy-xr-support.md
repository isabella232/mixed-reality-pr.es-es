---
title: Uso de la compatibilidad con XR integrada heredada
description: Aprenda a configurar los proyectos de Unity con y sin MRTK mediante la compatibilidad con XR integrada heredada.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743507"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="c1ef2-104">Uso de la compatibilidad con XR integrada heredada</span><span class="sxs-lookup"><span data-stu-id="c1ef2-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="c1ef2-105">Configuración del proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="c1ef2-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="c1ef2-106">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="c1ef2-107">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="c1ef2-108">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1ef2-109">Pruebe nuestros tutoriales de MRTK</span><span class="sxs-lookup"><span data-stu-id="c1ef2-109">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=wsa)

<span data-ttu-id="c1ef2-110">Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="c1ef2-111">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="c1ef2-111">Manual setup without MRTK</span></span>

<span data-ttu-id="c1ef2-112">Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="c1ef2-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & independiente resaltado](images/wmr-config-img-3.png)

<span data-ttu-id="c1ef2-114">Si tiene como destino HoloLens 2, debe cambiar a la Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="c1ef2-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="c1ef2-115">Seleccione File > Build Settings... (Configuración **de > compilación de archivos...**</span><span class="sxs-lookup"><span data-stu-id="c1ef2-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="c1ef2-116">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="c1ef2-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="c1ef2-117">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="c1ef2-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="c1ef2-118">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="c1ef2-119">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="c1ef2-120">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="c1ef2-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="c1ef2-121">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="c1ef2-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

<span data-ttu-id="c1ef2-123">Después de configurar la plataforma, debe hacer [](../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="c1ef2-124">La XR heredada está en desuso en Unity 2019 y se ha quitado en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="c1ef2-125">Abra **Configuración del reproductor...** desde la **configuración de compilación... ventana** y expanda el grupo **Configuración de XR.**</span><span class="sxs-lookup"><span data-stu-id="c1ef2-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="c1ef2-126">En la **sección Configuración de XR,** seleccione **Virtual Reality Supported (Virtual Reality compatible)** para agregar la lista Dispositivos de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="c1ef2-127">Establezca **Formato de profundidad en** Profundidad de **16 bits y** habilite El uso compartido del búfer de **profundidad**</span><span class="sxs-lookup"><span data-stu-id="c1ef2-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="c1ef2-128">Establecer **el modo de representación estéreo en** Instancia de paso **único**</span><span class="sxs-lookup"><span data-stu-id="c1ef2-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="c1ef2-129">Seleccione **WSA Holographic Remoting Supported (Comunicación** remota holográfica de WSA compatible) si desea usar la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="c1ef2-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la sección Configuración del reproductor resaltada](images/wmr-config-img-9.png)