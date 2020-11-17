---
title: Introducción al desarrollo con Native
description: Cree un motor de realidad mixta basado en DirectX mediante las API de realidad mixta de Windows directamente.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, representación holográfica, nativa, aplicación nativa, WinRT, aplicación de WinRT, API de plataforma, motor personalizado, middleware, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 0d5e364fdb4faac73f28649f5c009823a74ac595
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679654"
---
# <a name="native-development-overview"></a><span data-ttu-id="af46e-104">Introducción al desarrollo con Native</span><span class="sxs-lookup"><span data-stu-id="af46e-104">Native development overview</span></span>

![Logotipo de banner nativo](../images/native_logo_banner.png)

<span data-ttu-id="af46e-106">los motores 3D como [Unity](../unity/unity-development-overview.md) o las no [reales](../unreal/unreal-development-overview.md) no son las únicas rutas de desarrollo de realidad mixta que se abren.</span><span class="sxs-lookup"><span data-stu-id="af46e-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="af46e-107">También puede crear aplicaciones de realidad mixta mediante la codificación directa en las API de Windows Mixed Reality con DirectX 11 o DirectX 12.</span><span class="sxs-lookup"><span data-stu-id="af46e-107">You can also create Mixed Reality apps by directly coding to the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="af46e-108">Al aprovechar la plataforma directamente, básicamente está creando su propio middleware o marco.</span><span class="sxs-lookup"><span data-stu-id="af46e-108">By leveraging the platform directly, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="af46e-109">Si tiene un proyecto de WinRT existente que le gustaría mantener, diríjase a nuestra documentación principal de [winrt](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="af46e-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="af46e-110">Puntos de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="af46e-110">Development checkpoints</span></span>

<span data-ttu-id="af46e-111">Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unity en el mundo de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="af46e-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="af46e-112">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="af46e-112">1. Getting started</span></span>

<span data-ttu-id="af46e-113">Windows Mixed Reality admite [dos tipos de aplicaciones](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="af46e-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="af46e-114">**Aplicaciones de realidad mixta** (UWP o Win32) que usan la [API de HOLOGRAPHICSPACE](getting-a-holographicspace.md) o la [API de OpenXR](openxr.md) para presentar una [vista envolvente](../../design/app-views.md) al usuario que rellena la pantalla del casco</span><span class="sxs-lookup"><span data-stu-id="af46e-114">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="af46e-115">**aplicaciones 2D** (UWP) que usan DirectX, XAML u otro marco de trabajo para representar [vistas 2D](../../design/app-views.md#2d-views) en pizarras en la Página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="af46e-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="af46e-116">Las diferencias entre el desarrollo de DirectX para [vistas 2D y vistas envolventes](../../design/app-views.md) se refieren principalmente a la representación holográfica y la entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="af46e-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="af46e-117">El HWND de la aplicación de [UWP o el](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) HWND de la aplicación de Win32 son necesarios y permanecen en gran medida.</span><span class="sxs-lookup"><span data-stu-id="af46e-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="af46e-118">Lo mismo se aplica a las API de WinRT que están disponibles para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="af46e-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="af46e-119">Sin embargo, debe usar un subconjunto diferente de estas API para aprovechar las características holográficas.</span><span class="sxs-lookup"><span data-stu-id="af46e-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="af46e-120">Por ejemplo, el sistema intercambio y el marco actual se administran mediante el sistema para aplicaciones holográficas con el fin de habilitar un bucle de trama de predicción de supuestos.</span><span class="sxs-lookup"><span data-stu-id="af46e-120">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="af46e-121">2. Bloques de creación principales</span><span class="sxs-lookup"><span data-stu-id="af46e-121">2. Core building blocks</span></span>

<span data-ttu-id="af46e-122">Las aplicaciones de Windows Mixed Reality usan las siguientes API para compilar experiencias de [realidad mixta](../../discover/mixed-reality.md) para HoloLens y otros auriculares envolventes:</span><span class="sxs-lookup"><span data-stu-id="af46e-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="af46e-123">Característica</span><span class="sxs-lookup"><span data-stu-id="af46e-123">Feature</span></span>  |  <span data-ttu-id="af46e-124">Funcionalidad</span><span class="sxs-lookup"><span data-stu-id="af46e-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="af46e-125">Gaze</span><span class="sxs-lookup"><span data-stu-id="af46e-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="af46e-126">Permite que los usuarios se dirijan a los hologramas mediante su mirada.</span><span class="sxs-lookup"><span data-stu-id="af46e-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="af46e-127">Gesto</span><span class="sxs-lookup"><span data-stu-id="af46e-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="af46e-128">Agregar acciones espaciales a las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="af46e-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="af46e-129">Representación de holografías</span><span class="sxs-lookup"><span data-stu-id="af46e-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="af46e-130">Dibuje un holograma en una ubicación precisa del mundo en torno a los usuarios</span><span class="sxs-lookup"><span data-stu-id="af46e-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="af46e-131">Controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="af46e-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="af46e-132">Permita que los usuarios tomen medidas en sus entornos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="af46e-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="af46e-133">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="af46e-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="af46e-134">Permite asignar su espacio físico con una superposición de malla virtual para marcar los límites de su entorno.</span><span class="sxs-lookup"><span data-stu-id="af46e-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="af46e-135">Voz</span><span class="sxs-lookup"><span data-stu-id="af46e-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="af46e-136">Permite capturar palabras clave, frases y dictado en voz alta de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="af46e-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="af46e-137">Puede encontrar características principales futuras y en desarrollo en la documentación del [plan](openxr.md#roadmap) de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="af46e-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="af46e-138">3. implementación y prueba</span><span class="sxs-lookup"><span data-stu-id="af46e-138">3. Deploying and testing</span></span>

<span data-ttu-id="af46e-139">Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="af46e-139">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="af46e-140">Si no tiene acceso a un casco, puede usar el [emulador de HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) o el [simulador de realidad mixta de Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="af46e-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="af46e-141">¿Qué sigue?</span><span class="sxs-lookup"><span data-stu-id="af46e-141">What's next?</span></span>

<span data-ttu-id="af46e-142">Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK.</span><span class="sxs-lookup"><span data-stu-id="af46e-142">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="af46e-143">En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado.</span><span class="sxs-lookup"><span data-stu-id="af46e-143">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="af46e-144">Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.</span><span class="sxs-lookup"><span data-stu-id="af46e-144">Note that these topics and resources are not in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="af46e-145">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="af46e-145">Additional resources</span></span>

<span data-ttu-id="af46e-146">Si desea realizar un seguimiento del juego de OpenXR, consulte los vínculos siguientes:</span><span class="sxs-lookup"><span data-stu-id="af46e-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="af46e-147">Procedimientos recomendados de OpenXR</span><span class="sxs-lookup"><span data-stu-id="af46e-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="af46e-148">Rendimiento de OpenXR</span><span class="sxs-lookup"><span data-stu-id="af46e-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="af46e-149">Solución de problemas de OpenXR</span><span class="sxs-lookup"><span data-stu-id="af46e-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="af46e-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="af46e-150">See also</span></span>
* [<span data-ttu-id="af46e-151">Modelo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="af46e-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="af46e-152">Vistas de aplicación</span><span class="sxs-lookup"><span data-stu-id="af46e-152">App views</span></span>](../../design/app-views.md)
