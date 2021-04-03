---
title: Usar la compatibilidad integrada de XR heredada
description: Aprenda a configurar los proyectos de Unity con y sin MRTK con la compatibilidad integrada de XR heredada.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, MRTK
ms.openlocfilehash: 09989b3b2b7fa1d351235a2cc9b885d4795dc2b6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088534"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="40dfc-104">Usar la compatibilidad integrada de XR heredada</span><span class="sxs-lookup"><span data-stu-id="40dfc-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="40dfc-105">Configurar el proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="40dfc-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="40dfc-106">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="40dfc-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="40dfc-107">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="40dfc-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="40dfc-108">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="40dfc-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40dfc-109">Pruebe nuestros tutoriales de MRTK</span><span class="sxs-lookup"><span data-stu-id="40dfc-109">Try out our MRTK tutorials</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=wsa)

<span data-ttu-id="40dfc-110">Eche un vistazo a [la documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="40dfc-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="40dfc-111">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="40dfc-111">Manual setup without MRTK</span></span>

<span data-ttu-id="40dfc-112">Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="40dfc-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana de configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltada](images/wmr-config-img-3.png)

<span data-ttu-id="40dfc-114">Si tiene como destino HoloLens 2, debe cambiar a la Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="40dfc-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="40dfc-115">Seleccionar **archivo > configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="40dfc-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="40dfc-116">Seleccione **plataforma universal de Windows** en la lista plataforma y seleccione **Switch Platform (cambiar plataforma** ).</span><span class="sxs-lookup"><span data-stu-id="40dfc-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="40dfc-117">Establecimiento de la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="40dfc-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="40dfc-118">Establecimiento del **dispositivo de destino** en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="40dfc-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="40dfc-119">Establecer el **tipo de compilación** en **D3D**</span><span class="sxs-lookup"><span data-stu-id="40dfc-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="40dfc-120">Establecimiento del **SDK de UWP** en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="40dfc-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="40dfc-121">Establezca la **configuración de compilación** en **Release** porque hay problemas de rendimiento conocidos con debug</span><span class="sxs-lookup"><span data-stu-id="40dfc-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

<span data-ttu-id="40dfc-123">Después de establecer la plataforma, debe dejar que Unity sepa crear una [vista envolvente](../../design/app-views.md) en lugar de una vista 2D cuando se exporte.</span><span class="sxs-lookup"><span data-stu-id="40dfc-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="40dfc-124">El XR heredado está en desuso en Unity 2019 y se quitó en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="40dfc-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="40dfc-125">Abra **configuración del reproductor...** en la **configuración de compilación... y** expanda el grupo de **configuración XR**</span><span class="sxs-lookup"><span data-stu-id="40dfc-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="40dfc-126">En la sección **configuración de XR** , seleccione **realidad virtual compatible** para agregar la lista de dispositivos de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="40dfc-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="40dfc-127">Establecer el **formato de profundidad** en profundidad de **16 bits** y habilitar el **uso compartido del búfer de profundidad**</span><span class="sxs-lookup"><span data-stu-id="40dfc-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="40dfc-128">Establecer el **modo de representación estéreo** en **una instancia de paso único**</span><span class="sxs-lookup"><span data-stu-id="40dfc-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="40dfc-129">Seleccione **WSA Holographic Remoting compatible** si desea usar Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="40dfc-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración del reproductor resaltada](images/wmr-config-img-9.png)