---
title: Usar el complemento de Windows XR
description: Aprenda a configurar los proyectos de Unity con y sin MRTK con la compatibilidad de Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, MRTK, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938153"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="4fac7-104">Uso del complemento de Windows XR</span><span class="sxs-lookup"><span data-stu-id="4fac7-104">Using Windows XR plugin</span></span>

<span data-ttu-id="4fac7-105">Para los desarrolladores que tienen como destino Unity 2020, el complemento de Windows XR permite el acceso a características de realidad mixta en auriculares de la realidad de HoloLens 2 y Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4fac7-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="4fac7-106">Este complemento también se admite en Unity 2019, aunque hay algunas incompatibilidades conocidas con los delimitadores espaciales de Azure al usar este complemento en esa versión.</span><span class="sxs-lookup"><span data-stu-id="4fac7-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="4fac7-107">Aunque Microsoft y la comunidad han creado herramientas de código abierto, como el kit de herramientas de la [realidad mixta (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , que configurará automáticamente el entorno de WMR, muchos desarrolladores quieren crear sus experiencias desde cero.</span><span class="sxs-lookup"><span data-stu-id="4fac7-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="4fac7-108">En la siguiente documentación se muestra cómo configurar correctamente un proyecto para el desarrollo de realidad mixta, tanto si usa MRTK como si no.</span><span class="sxs-lookup"><span data-stu-id="4fac7-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="4fac7-109">La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.</span><span class="sxs-lookup"><span data-stu-id="4fac7-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="4fac7-110">Configurar el proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="4fac7-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="4fac7-111">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="4fac7-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="4fac7-112">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="4fac7-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="4fac7-113">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="4fac7-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fac7-114">Pruebe nuestros tutoriales de MRTK</span><span class="sxs-lookup"><span data-stu-id="4fac7-114">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="4fac7-115">Eche un vistazo a [la documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="4fac7-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="4fac7-116">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="4fac7-116">Manual setup without MRTK</span></span>

<span data-ttu-id="4fac7-117">Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="4fac7-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana de configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltada](images/wmr-config-img-3.png)

<span data-ttu-id="4fac7-119">Si tiene como destino HoloLens 2, debe cambiar a la Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="4fac7-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="4fac7-120">Seleccionar **archivo > configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="4fac7-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="4fac7-121">Seleccione **plataforma universal de Windows** en la lista plataforma y seleccione **Switch Platform (cambiar plataforma** ).</span><span class="sxs-lookup"><span data-stu-id="4fac7-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="4fac7-122">Establecimiento de la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="4fac7-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="4fac7-123">Establecimiento del **dispositivo de destino** en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="4fac7-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="4fac7-124">Establecer el **tipo de compilación** en **D3D**</span><span class="sxs-lookup"><span data-stu-id="4fac7-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="4fac7-125">Establecimiento del **SDK de UWP** en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="4fac7-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="4fac7-126">Establezca la **configuración de compilación** en **Release** porque hay problemas de rendimiento conocidos con debug</span><span class="sxs-lookup"><span data-stu-id="4fac7-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

<span data-ttu-id="4fac7-128">Después de establecer la plataforma, debe dejar que Unity sepa crear una [vista envolvente](../../design/app-views.md) en lugar de una vista 2D cuando se exporte:</span><span class="sxs-lookup"><span data-stu-id="4fac7-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="4fac7-129">En el editor de Unity, navegue a **editar > configuración del proyecto** y seleccione **Administración de complementos de XR** .</span><span class="sxs-lookup"><span data-stu-id="4fac7-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="4fac7-130">Seleccione **instalar administración de complementos de XR**</span><span class="sxs-lookup"><span data-stu-id="4fac7-130">Select **Install XR Plugin Management**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-5.png)

3. <span data-ttu-id="4fac7-132">Seleccione **inicializar XR en el inicio** y **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="4fac7-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-7.png)

4. <span data-ttu-id="4fac7-134">Expanda la sección **Administración de complementos de XR** y seleccione la pestaña Configuración de la **plataforma de Windows universal** .</span><span class="sxs-lookup"><span data-stu-id="4fac7-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="4fac7-135">Si usa Unity 2020 o una versión posterior, verá las opciones para comprobar **OpenXR** o **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="4fac7-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="4fac7-136">Puede elegir en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="4fac7-136">You can choose either runtime.</span></span>  <span data-ttu-id="4fac7-137">Si está desarrollando específicamente para HoloLens 2 o la reverberación de HP G2 y decide probar el **OpenXR**, seleccione el cuadro OpenXR y revise nuestra guía para [usar el complemento Mixed Reality OpenXR para Unity](openxr-getting-started.md) con el fin de configurarlo correctamente para estos dispositivos antes de volver a este tutorial.</span><span class="sxs-lookup"><span data-stu-id="4fac7-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="4fac7-138">A partir de Unity 2020 LTS, Microsoft adopta el desarrollo con OpenXR.</span><span class="sxs-lookup"><span data-stu-id="4fac7-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="4fac7-139">Al migrar a esta ruta de acceso, en Unity 2021,1 el complemento de Windows XR dejará de usarse y se quitará en 2021,2, de modo que OpenXR la única ruta de acceso admitida.</span><span class="sxs-lookup"><span data-stu-id="4fac7-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="4fac7-140">Puede encontrar más información en [uso del complemento OpenXR de realidad mixta](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="4fac7-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="4fac7-141">Si decide elegir el complemento de **Windows Mixed Reality** , active todas las casillas y establezca el **modo de envío de profundidad** en profundidad de **16 bits** .</span><span class="sxs-lookup"><span data-stu-id="4fac7-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)
