---
title: Uso del complemento XR de Windows
description: Obtenga información sobre cómo configurar los proyectos de Unity con y sin MRTK mediante la compatibilidad con Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, mrtk, windows
ms.openlocfilehash: c9733d58236d97db370ce4f58dc1760bdf4eda86
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110232"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="0b8b8-104">Uso del complemento XR de Windows</span><span class="sxs-lookup"><span data-stu-id="0b8b8-104">Using Windows XR plugin</span></span>

<span data-ttu-id="0b8b8-105">Para los desarrolladores que tienen como destino Unity 2020, el complemento XR de Windows permite el acceso a características de realidad mixta en HoloLens 2 y Windows Mixed Reality cascos.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="0b8b8-106">Este complemento también se admite en Unity 2019, aunque hay algunas incompatibilidades conocidas con Azure Spatial Anchors al usar este complemento en esa versión.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="0b8b8-107">Aunque Microsoft y la comunidad han creado herramientas de código abierto como [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) que configurarán automáticamente el entorno WMR, muchos desarrolladores desean crear sus experiencias desde el primer momento.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="0b8b8-108">En la siguiente documentación se muestra cómo configurar correctamente un proyecto para Mixed Reality desarrollo independientemente de si usa MRTK o no.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="0b8b8-109">La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="0b8b8-110">Configuración del proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="0b8b8-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="0b8b8-111">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="0b8b8-112">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="0b8b8-113">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b8b8-114">Pruebe nuestros tutoriales de MRTK</span><span class="sxs-lookup"><span data-stu-id="0b8b8-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="0b8b8-115">Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="0b8b8-116">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="0b8b8-116">Manual setup without MRTK</span></span>

<span data-ttu-id="0b8b8-117">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="0b8b8-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](images/wmr-config-img-3.png)

<span data-ttu-id="0b8b8-119">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="0b8b8-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="0b8b8-120">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="0b8b8-121">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="0b8b8-122">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="0b8b8-123">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="0b8b8-124">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="0b8b8-125">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="0b8b8-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="0b8b8-126">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="0b8b8-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

<span data-ttu-id="0b8b8-128">Después de configurar la plataforma, debe dejar [](../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte:</span><span class="sxs-lookup"><span data-stu-id="0b8b8-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="0b8b8-129">En el Editor de Unity, vaya **a Editar > configuración del** proyecto y seleccione Administración de complementos **XR.**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="0b8b8-130">Seleccione **Install XR Plugin Management (Instalar administración de complementos XR).**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-130">Select **Install XR Plugin Management**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](images/wmr-config-img-5.png)

3. <span data-ttu-id="0b8b8-132">Seleccione **Initialize XR on Startup (Inicializar XR)** **al iniciar Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](images/wmr-config-img-7.png)

4. <span data-ttu-id="0b8b8-134">Expanda la **sección XR Plug-in Management (Administración** de complementos XR) y seleccione la pestaña **Univeral Windows Platform Settings (Configuración de plataforma de Windows univeral).**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="0b8b8-135">Si usa Unity 2020 o posterior, verá las opciones para comprobar **OpenXR** o **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="0b8b8-136">Puede elegir cualquiera de los entornos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-136">You can choose either runtime.</span></span>  <span data-ttu-id="0b8b8-137">Si va a desarrollar específicamente para HoloLens 2 o HP Reverb G2 y decide probar **OpenXR,** active la casilla OpenXR y revise nuestra guía Uso del complemento [de OpenXR](openxr-getting-started.md) de Mixed Reality para Unity para configurarse correctamente para estos dispositivos antes de volver a este tutorial.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="0b8b8-138">A partir de Unity 2020 LTS, Microsoft está adoptando el desarrollo con OpenXR.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="0b8b8-139">A medida que migramos a esta ruta de acceso, en Unity 2021.1 el complemento XR de Windows estará en desuso y se quitará en 2021.2, lo que hace que OpenXR sea la única ruta de acceso admitida.</span><span class="sxs-lookup"><span data-stu-id="0b8b8-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="0b8b8-140">Puede encontrar más información en [Uso del complemento Mixed Reality OpenXR.](openxr-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="0b8b8-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="0b8b8-141">Si decide elegir  el complemento de Windows Mixed Reality, active todas las casillas y establezca **Modo de envío de** profundidad en Profundidad **de 16 bits.**</span><span class="sxs-lookup"><span data-stu-id="0b8b8-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)