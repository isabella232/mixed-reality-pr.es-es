---
title: Documentación para desarrolladores de MRTK-Unity
description: Obtenga información sobre Mixed Reality Toolkit para Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: a774a5c08cb2d8bbaeebeca19cec366504efba58
ms.sourcegitcommit: 5c81c19905b26818882e49679bd71f5dd7bc6d3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2021
ms.locfileid: "103202824"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="2297f-104">¿Qué es Mixed Reality Toolkit?</span><span class="sxs-lookup"><span data-stu-id="2297f-104">What is the Mixed Reality Toolkit</span></span>

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="2297f-106">MRTK Unity es un proyecto controlado por Microsoft que proporciona un conjunto de componentes y características para acelerar el desarrollo de aplicaciones de MR multiplataforma en Unity.</span><span class="sxs-lookup"><span data-stu-id="2297f-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="2297f-107">Estas son algunas de sus funciones:</span><span class="sxs-lookup"><span data-stu-id="2297f-107">Here are some of its functions:</span></span>

* <span data-ttu-id="2297f-108">Proporciona el **sistema de entrada multiplataforma y los bloques de creación para las interacciones espaciales y la interfaz de usuario**.</span><span class="sxs-lookup"><span data-stu-id="2297f-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="2297f-109">Permite la **creación rápida de prototipos** gracias a la simulación en el editor, que permite ver los cambios inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="2297f-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="2297f-110">Funciona como **plataforma extensible** que permite a los desarrolladores intercambiar los componentes principales.</span><span class="sxs-lookup"><span data-stu-id="2297f-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="2297f-111">**Es compatible con una amplia gama de plataformas**, entre las que se incluyen:</span><span class="sxs-lookup"><span data-stu-id="2297f-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="2297f-112">OpenXR (Unity 2020.2 o posterior)</span><span class="sxs-lookup"><span data-stu-id="2297f-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="2297f-113">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2297f-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="2297f-114">Cascos de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2297f-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="2297f-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2297f-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="2297f-116">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="2297f-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="2297f-117">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2297f-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="2297f-118">Cascos de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2297f-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="2297f-119">Oculus (Unity 2019.3 o posterior)</span><span class="sxs-lookup"><span data-stu-id="2297f-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="2297f-120">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="2297f-120">Oculus Quest</span></span>
  * <span data-ttu-id="2297f-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="2297f-121">OpenVR</span></span>
    * <span data-ttu-id="2297f-122">Cascos de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2297f-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="2297f-123">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="2297f-123">HTC Vive</span></span>
    * <span data-ttu-id="2297f-124">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="2297f-124">Oculus Rift</span></span>
  * <span data-ttu-id="2297f-125">Seguimiento de manos de Ultraleap</span><span class="sxs-lookup"><span data-stu-id="2297f-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="2297f-126">Dispositivos móviles, como iOS y Android</span><span class="sxs-lookup"><span data-stu-id="2297f-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="2297f-127">Introducción a MRTK</span><span class="sxs-lookup"><span data-stu-id="2297f-127">Getting started with MRTK</span></span>

<span data-ttu-id="2297f-128">Si no está familiarizado con MRTK ni el desarrollo para realidad mixta en Unity, se recomienda instalar las herramientas necesarias y seguir la serie de tutoriales de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2297f-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2297f-129">Instalar las herramientas</span><span class="sxs-lookup"><span data-stu-id="2297f-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="2297f-130">Serie de tutoriales de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2297f-130">HoloLens 2 Tutorial Series</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="2297f-131">¿Quiere conocer lo que se esconde bajo la superficie?</span><span class="sxs-lookup"><span data-stu-id="2297f-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2297f-132">Explorar MRTK en GitHub</span><span class="sxs-lookup"><span data-stu-id="2297f-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="2297f-133">Documentación</span><span class="sxs-lookup"><span data-stu-id="2297f-133">Documentation</span></span>

| <span data-ttu-id="2297f-134">[![Notas de la versión](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="2297f-135">Notas de la versión</span><span class="sxs-lookup"><span data-stu-id="2297f-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="2297f-136">[![Información general de MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="2297f-137">Información general de MRTK</span><span class="sxs-lookup"><span data-stu-id="2297f-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="2297f-138">[![Referencia de API](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="2297f-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="2297f-139">Referencia de API</span><span class="sxs-lookup"><span data-stu-id="2297f-139">API Reference</span></span>](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="2297f-140">Estado de la compilación</span><span class="sxs-lookup"><span data-stu-id="2297f-140">Build status</span></span>

| <span data-ttu-id="2297f-141">Rama</span><span class="sxs-lookup"><span data-stu-id="2297f-141">Branch</span></span> | <span data-ttu-id="2297f-142">Estado de CI</span><span class="sxs-lookup"><span data-stu-id="2297f-142">CI Status</span></span> | <span data-ttu-id="2297f-143">Estado del documento</span><span class="sxs-lookup"><span data-stu-id="2297f-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="2297f-144">[![Estado de CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="2297f-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="2297f-145">[![Estado del documento](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="2297f-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="2297f-146">Áreas de características</span><span class="sxs-lookup"><span data-stu-id="2297f-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="2297f-147">[![Sistema de entrada](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="2297f-148">**[Sistema de entrada](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-148">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-149">[![Seguimiento de manos (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-149">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="2297f-150">**[Seguimiento de manos <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-150">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-151">[![Seguimiento de los ojos (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-151">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="2297f-152">**[Seguimiento de los ojos <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-152">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-153">[![Perfiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-153">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="2297f-154">**[Perfiles](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-154">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-155">[![Seguimiento de manos (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-155">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="2297f-156">**[Seguimiento de manos <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-156">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-157">[![Controles de la interfaz de usuario](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="2297f-157">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="2297f-158">**[Controles de la interfaz de usuario](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="2297f-158">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-159">[![Solucionadores](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-159">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="2297f-160">**[Solucionadores](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-160">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-161">[![Administrador de varias escenas](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-161">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2297f-162">**[Administrador de<br/> varias escenas](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-162">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-163">[![Reconocimiento espacial](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-163">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="2297f-164">**[Reconocimiento <br/> espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-164">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-165">[![Herramienta de diagnóstico](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-165">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2297f-166">**[Herramienta de <br/> diagnóstico](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-166">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-167">[![Vista del sombreador estándar de MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="2297f-167">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="2297f-168">**[Vista de ejemplo del sombreador estándar de MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="2297f-168">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-169">[![Voz y dictado](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-169">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2297f-170">**[Voz de](features/input/speech.md)<br/> & [Dictado](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-170">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-171">[![Sistema de límites](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-171">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2297f-172">**[Sistema <br/> de límites](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-172">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-173">[![Simulación en editor](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-173">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2297f-174">**[Simulación <br/> en editor](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-174">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-175">[![Características experimentales](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-175">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="2297f-176">**[Características <br/> experimentales](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-176">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="2297f-177">Bloques de creación de la experiencia de usuario</span><span class="sxs-lookup"><span data-stu-id="2297f-177">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="2297f-178">[![Botón](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Botón](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-178">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="2297f-179">Control de botón que admite varios métodos de entrada, incluida la mano articulada de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2297f-179">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-180">[![Control de límites](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Control de límites](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-180">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="2297f-181">Interfaz de usuario estándar para manipular objetos en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="2297f-181">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-182">[![Manipulador de objetos](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Manipulador de objetos](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-182">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="2297f-183">Script para manipular objetos con una o dos manos.</span><span class="sxs-lookup"><span data-stu-id="2297f-183">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-184">[![Claqueta](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Claqueta](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-184">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="2297f-185">Plano de estilo 2D que admite el desplazamiento con la entrada de mano articulada.</span><span class="sxs-lookup"><span data-stu-id="2297f-185">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-186">[![Teclado del sistema](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Teclado del sistema](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-186">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="2297f-187">Ejemplo de script de uso del teclado del sistema en Unity.</span><span class="sxs-lookup"><span data-stu-id="2297f-187">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-188">[![Interactuable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactuable](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-188">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="2297f-189">Un script para que los objetos interactúen con los estados visuales y la compatibilidad con temas.</span><span class="sxs-lookup"><span data-stu-id="2297f-189">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-190">[![Solucionador](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solucionador](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-190">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="2297f-191">Varios comportamientos de posicionamiento de objetos, como etiquetado, bloqueo del cuerpo, tamaño de vista constante y magnetismo de la superficie.</span><span class="sxs-lookup"><span data-stu-id="2297f-191">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-192">[![Colección de objetos](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Colección de objetos](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-192">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="2297f-193">Script para diseñar una matriz de objetos en una forma tridimensional.</span><span class="sxs-lookup"><span data-stu-id="2297f-193">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-194">[![Información sobre herramientas](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Información sobre herramientas](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-194">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="2297f-195">Interfaz de usuario de anotación con un sistema flexible de anclaje/dinamización que se puede usar para etiquetar controladores de movimiento y objetos.</span><span class="sxs-lookup"><span data-stu-id="2297f-195">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-196">[![Control deslizante](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Control deslizante](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-196">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="2297f-197">Interfaz de usuario del control deslizante para ajustar los valores que admiten la interacción directa de seguimiento de manos.</span><span class="sxs-lookup"><span data-stu-id="2297f-197">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-198">[![Sombreador MRTK Standard](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Sombreador MRTK Standard](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-198">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="2297f-199">El sombreador MRTK Standard admite varios elementos de diseño de Fluent con rendimiento.</span><span class="sxs-lookup"><span data-stu-id="2297f-199">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-200">[![Menú Mano](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Menú Mano](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-200">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="2297f-201">Interfaz de usuario bloqueada manualmente para un acceso rápido mediante el solucionador de restricciones de la mano.</span><span class="sxs-lookup"><span data-stu-id="2297f-201">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-202">[![Barra de aplicaciones](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Barra de aplicaciones](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-202">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="2297f-203">Interfaz de usuario para la activación manual del control de límites.</span><span class="sxs-lookup"><span data-stu-id="2297f-203">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-204">[![Punteros](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Punteros](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-204">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="2297f-205">Información sobre los distintos tipos de punteros.</span><span class="sxs-lookup"><span data-stu-id="2297f-205">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-206">[![Visualización de la punta del dedo](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualización de la punta del dedo](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-206">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="2297f-207">Prestación visual de la punta del dedo, lo que mejora la confianza para la interacción directa.</span><span class="sxs-lookup"><span data-stu-id="2297f-207">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-208">[![Menú Cerca](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Menú Cerca](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-208">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="2297f-209">Interfaz de usuario de menú flotante para las interacciones cercanas.</span><span class="sxs-lookup"><span data-stu-id="2297f-209">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-210">[![Introducción al reconocimiento espacial](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Vista de reconocimiento espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-210">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="2297f-211">Haga que los objetos holográficos interactúen con los entornos físicos.</span><span class="sxs-lookup"><span data-stu-id="2297f-211">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-212">[![Comando de voz](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Comando de voz](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-212">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="2297f-213">Scripts y ejemplos para integrar la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="2297f-213">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-214">[![Indicador de progreso](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Indicador de progreso](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-214">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="2297f-215">Indicador visual para comunicar el proceso o la operación de datos.</span><span class="sxs-lookup"><span data-stu-id="2297f-215">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-216">[![Cuadro de diálogo](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Cuadro de diálogo](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-216">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="2297f-217">Interfaz de usuario para solicitar confirmación o reconocimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="2297f-217">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-218">[![Asesor manual](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Asesor manual](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-218">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="2297f-219">Componente que ayuda a guiar al usuario cuando no se ha enseñado el gesto.</span><span class="sxs-lookup"><span data-stu-id="2297f-219">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-220">[![Servicio de la física de la mano](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Servicio de la física de la mano [experimental]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-220">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="2297f-221">El servicio de la física de la mano permite eventos e interacciones de colisión de cuerpos rígidos con manos articuladas.</span><span class="sxs-lookup"><span data-stu-id="2297f-221">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-222">[![Desplazamiento por la colección](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Desplazamiento por la colección](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-222">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="2297f-223">Colección de objetos que desplaza objetos 3D de forma nativa.</span><span class="sxs-lookup"><span data-stu-id="2297f-223">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [experimental]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="2297f-225">Dock permite que los objetos entren y salgan de las posiciones predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="2297f-225">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2297f-226">[![Seguimiento ocular: selección de destino](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Seguimiento ocular: selección de destino](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-226">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="2297f-227">Combine la entrada ocular, de voz y de manos para seleccionar los hologramas de forma rápida y sencilla a lo largo de la escena.</span><span class="sxs-lookup"><span data-stu-id="2297f-227">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-228">[![Seguimiento ocular: navegación](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Seguimiento ocular: navegación](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="2297f-228">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="2297f-229">Aprenda sobre cómo desplazarse por texto automáticamente o acercar de forma fluida el contenido donde está el foco en función de lo que está examinando.</span><span class="sxs-lookup"><span data-stu-id="2297f-229">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2297f-230">[![Seguimiento ocular: mapa térmico](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Seguimiento ocular: mapa térmico](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="2297f-230">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="2297f-231">Ejemplos para registrar, cargar y visualizar lo que los usuarios han estado examinando en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2297f-231">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="2297f-232">Herramientas</span><span class="sxs-lookup"><span data-stu-id="2297f-232">Tools</span></span>

|  <span data-ttu-id="2297f-233">[![Optimizar ventana](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimizar ventana](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-233">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="2297f-234">[![Ventana de dependencia](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Ventana de dependencia](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-234">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![Ventana de compilación](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="2297f-236">Ventana de compilación</span><span class="sxs-lookup"><span data-stu-id="2297f-236">Build Window</span></span> | <span data-ttu-id="2297f-237">[![Grabación de entrada](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Grabación de entrada](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-237">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="2297f-238">Automatice la configuración de proyectos de Mixed Reality para optimizar el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="2297f-238">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="2297f-239">Analice las dependencias entre recursos e identifique los recursos sin usar.</span><span class="sxs-lookup"><span data-stu-id="2297f-239">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="2297f-240">Configure y ejecute un proceso de compilación de un extremo a otro para aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2297f-240">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="2297f-241">Grabe y reproduzca los datos de movimiento y seguimiento de manos en el editor.</span><span class="sxs-lookup"><span data-stu-id="2297f-241">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="2297f-242">Escenas de ejemplo</span><span class="sxs-lookup"><span data-stu-id="2297f-242">Example scenes</span></span>

<span data-ttu-id="2297f-243">Explore los distintos tipos de interacciones y controles de interfaz de usuario de MRTK en [esta escena de ejemplo](features/example-scenes/hand-interaction-examples.md).</span><span class="sxs-lookup"><span data-stu-id="2297f-243">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="2297f-244">[![Escenas de ejemplo 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-244">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="2297f-245">MRTK Examples Hub</span><span class="sxs-lookup"><span data-stu-id="2297f-245">MRTK examples hub</span></span>

<span data-ttu-id="2297f-246">Con MRTK Examples Hub, puede probar varias escenas de ejemplo en MRTK.</span><span class="sxs-lookup"><span data-stu-id="2297f-246">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="2297f-247">Puede descargar paquetes de aplicaciones pregenerados para HoloLens (x86), HoloLens 2 (ARM) y cascos envolventes de Windows Mixed Reality (x64); para ello, seleccione el paquete "Ejemplos de Mixed Reality Toolkit" en [MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="2297f-247">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="2297f-248">Asegúrese de [usar el Portal de dispositivos Windows para instalar aplicaciones en HoloLens (1.ª generación)](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span><span class="sxs-lookup"><span data-stu-id="2297f-248">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="2297f-249">En HoloLens 2, puede descargar e instalar [MRTK Examples Hub a través de Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span><span class="sxs-lookup"><span data-stu-id="2297f-249">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="2297f-250">Consulte la [página Léame de Examples Hub](features/example-scenes/example-hub.md) para obtener información sobre cómo crear un centro de varias escenas con el sistema de escenas y el servicio de transición de escenas de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2297f-250">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="2297f-251">[![Centro de escenas de ejemplo](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="2297f-251">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="2297f-252">Aplicaciones de ejemplo hechas con MRTK</span><span class="sxs-lookup"><span data-stu-id="2297f-252">Sample apps made with MRTK</span></span>

| <span data-ttu-id="2297f-253">[![Tabla periódica de los elementos](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="2297f-253">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="2297f-254">[![Explorador de la galaxia](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="2297f-254">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="2297f-255">[![Aplicación de ejemplo Surfaces](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="2297f-255">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="2297f-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto que muestra cómo usar el sistema de entrada de MRTK y los bloques de creación para crear una experiencia de aplicación para HoloLens y cascos envolventes.</span><span class="sxs-lookup"><span data-stu-id="2297f-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="2297f-257">Lea la historia de la migración: [Incorporación de la aplicación Periodic Table of the Elements a HoloLens 2 con MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158).</span><span class="sxs-lookup"><span data-stu-id="2297f-257">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="2297f-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) es una aplicación de ejemplo de código abierto que se desarrolló originalmente en marzo de 2016 como parte de la campaña "Share Your Idea" de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2297f-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="2297f-259">Galaxy Explorer se ha actualizado con las nuevas características de HoloLens 2, mediante MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="2297f-259">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="2297f-260">Lea la historia: [La creación de Galaxy Explorer para HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update).</span><span class="sxs-lookup"><span data-stu-id="2297f-260">Read the story: [The Making of Galaxy Explorer for HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="2297f-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) es una aplicación de ejemplo de código abierto para HoloLens 2, que explora cómo podemos crear una sensación táctil con entrada visual, de audio y seguimiento de manos totalmente articuladas.</span><span class="sxs-lookup"><span data-stu-id="2297f-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="2297f-262">Consulte [Aprendizajes de la aplicación Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) de la sesión Microsoft MR Dev Days para obtener información sobre el diseño y la historia de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="2297f-262">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="2297f-263">Vídeos de sesión de Mixed Reality Dev Days 2020</span><span class="sxs-lookup"><span data-stu-id="2297f-263">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="2297f-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="2297f-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="2297f-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="2297f-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="2297f-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="2297f-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="2297f-267">Tutorial sobre cómo crear una sencilla aplicación de MRTK de principio a fin.</span><span class="sxs-lookup"><span data-stu-id="2297f-267">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="2297f-268">Obtenga información sobre los conceptos de interacción y las funcionalidades multiplataforma de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2297f-268">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="2297f-269">Profundice en los bloques de creación de la experiencia de usuario de MRTK que le ayudarán a crear fantásticas experiencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2297f-269">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="2297f-270">Introducción a las herramientas de rendimiento, tanto de MRTK como externas, e información general sobre el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2297f-270">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="2297f-271">Consulte [Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) para explorar más vídeos de sesiones.</span><span class="sxs-lookup"><span data-stu-id="2297f-271">See [Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="2297f-272">Interacción con la comunidad</span><span class="sxs-lookup"><span data-stu-id="2297f-272">Engage with the community</span></span>

* <span data-ttu-id="2297f-273">Únase a la conversación en torno a MRTK en [Slack](https://holodevelopers.slack.com/).</span><span class="sxs-lookup"><span data-stu-id="2297f-273">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="2297f-274">Puede unirse a la comunidad de Slack a través del [remitente de invitación automática](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="2297f-274">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="2297f-275">Formule preguntas sobre el uso de MRTK en [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) con la etiqueta **MRTK**.</span><span class="sxs-lookup"><span data-stu-id="2297f-275">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="2297f-276">Busque [problemas conocidos](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) o presente un [nuevo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) si encuentra algo mal en el código de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2297f-276">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="2297f-277">Si tiene preguntas sobre cómo contribuir con MRTK, vaya al canal [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) en Slack.</span><span class="sxs-lookup"><span data-stu-id="2297f-277">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="2297f-278">El proyecto ha adoptado el [Código de conducta de código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="2297f-278">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="2297f-279">Para obtener más información, vea las [Preguntas más frecuentes sobre el código de conducta](https://opensource.microsoft.com/codeofconduct/faq/), o póngase en contacto con [opencode@microsoft.com](mailto:opencode@microsoft.com) si tiene preguntas o comentarios.</span><span class="sxs-lookup"><span data-stu-id="2297f-279">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="2297f-280">Recursos útiles en el Centro de desarrollo de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="2297f-280">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="2297f-281">![Descubrir](features/images/mrdevcenter/icon-discover.png) [Descubrir](https://docs.microsoft.com/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="2297f-281">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](https://docs.microsoft.com/windows/mixed-reality/)</span></span>| <span data-ttu-id="2297f-282">![Diseñar](features/images/mrdevcenter/icon-design.png) [Diseñar](https://docs.microsoft.com/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="2297f-282">![Design](features/images/mrdevcenter/icon-design.png) [Design](https://docs.microsoft.com/windows/mixed-reality/design)</span></span>| <span data-ttu-id="2297f-283">![Desarrollar](features/images/mrdevcenter/icon-develop.png) [Desarrollar](https://docs.microsoft.com/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="2297f-283">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](https://docs.microsoft.com/windows/mixed-reality/development)</span></span>| <span data-ttu-id="2297f-284">![Distribuir](features/images/mrdevcenter/icon-distribute.png) [Distribuir](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="2297f-284">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="2297f-285">Aprende a crear experiencias de realidad mixta para HoloLens y cascos envolventes (VR).</span><span class="sxs-lookup"><span data-stu-id="2297f-285">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="2297f-286">Obtenga guías de diseño.</span><span class="sxs-lookup"><span data-stu-id="2297f-286">Get design guides.</span></span> <span data-ttu-id="2297f-287">Cree interfaces de usuario.</span><span class="sxs-lookup"><span data-stu-id="2297f-287">Build user interface.</span></span> <span data-ttu-id="2297f-288">Aprenda sobre interacciones y entradas.</span><span class="sxs-lookup"><span data-stu-id="2297f-288">Learn interactions and input.</span></span>     | <span data-ttu-id="2297f-289">Obtenga guías de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="2297f-289">Get development guides.</span></span> <span data-ttu-id="2297f-290">Aprenda sobre la tecnología.</span><span class="sxs-lookup"><span data-stu-id="2297f-290">Learn the technology.</span></span> <span data-ttu-id="2297f-291">Aprenda sobre la ciencia.</span><span class="sxs-lookup"><span data-stu-id="2297f-291">Understand the science.</span></span>       | <span data-ttu-id="2297f-292">Haga que la aplicación esté disponible para otros usuarios y considere la posibilidad de crear un iniciador 3D.</span><span class="sxs-lookup"><span data-stu-id="2297f-292">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="2297f-293">Recursos útiles en Azure</span><span class="sxs-lookup"><span data-stu-id="2297f-293">Useful resources on Azure</span></span>

| <span data-ttu-id="2297f-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="2297f-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="2297f-295">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2297f-295">Spatial Anchors</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)| <span data-ttu-id="2297f-296">![Servicios de Voz](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="2297f-296">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="2297f-297">![Servicios de visión](features/images/mrdevcenter/icon-azurevisionservices.png) [Servicios de visión](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="2297f-297">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="2297f-298">Spatial Anchors es un servicio multiplataforma que le permite crear experiencias de realidad mixta mediante objetos que conservan su ubicación en los dispositivos y a lo largo del tiempo.</span><span class="sxs-lookup"><span data-stu-id="2297f-298">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="2297f-299">Conozca e integre en su aplicación las funcionalidades de voz con tecnología de Azure como, por ejemplo, conversión de voz a texto, reconocimiento del hablante o traducción de voz.</span><span class="sxs-lookup"><span data-stu-id="2297f-299">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="2297f-300">Identifique y analice el contenido de sus imágenes o vídeos mediante servicios de visión como Computer Vision, detección de caras, reconocimiento de emociones o indexador de vídeo.</span><span class="sxs-lookup"><span data-stu-id="2297f-300">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="2297f-301">Cómo contribuir</span><span class="sxs-lookup"><span data-stu-id="2297f-301">How to contribute</span></span>

<span data-ttu-id="2297f-302">Obtenga información sobre cómo contribuir a MRTK en [Colaboración](contributing/contributing.md).</span><span class="sxs-lookup"><span data-stu-id="2297f-302">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="2297f-303">Ayuda</span><span class="sxs-lookup"><span data-stu-id="2297f-303">Getting help</span></span>

<span data-ttu-id="2297f-304">Si surgen problemas debido a MRTK o tiene dudas sobre cómo hacer algo, hay algunos recursos que pueden resultar útiles:</span><span class="sxs-lookup"><span data-stu-id="2297f-304">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="2297f-305">Para notificar errores, [registre un problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) en el repositorio de GitHub.</span><span class="sxs-lookup"><span data-stu-id="2297f-305">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="2297f-306">Si tiene alguna pregunta, póngase en contacto con [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) o con el [canal mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) en Slack.</span><span class="sxs-lookup"><span data-stu-id="2297f-306">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="2297f-307">Puede unirse a la comunidad de Slack a través del [remitente de invitación automática](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="2297f-307">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>
