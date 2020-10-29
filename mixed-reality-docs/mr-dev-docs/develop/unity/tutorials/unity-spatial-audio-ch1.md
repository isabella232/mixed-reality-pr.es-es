---
title: 'Tutoriales de audio espacial: 1. Agregar audio espacial al proyecto'
description: Agregue el complemento de Microsoft Spatializer a su proyecto de Unity para acceder a la descarga de hardware de HoloLens 2 HRTF.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: 9ddfd1644a20ac063551b8140f9f8950ae172196
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91694491"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="3abf6-105">Incorporación de audio espacial al proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="3abf6-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="3abf6-106">Este es el tutorial de audio espacial para Unity en HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="3abf6-106">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="3abf6-107">Esta secuencia de tutorial muestra:</span><span class="sxs-lookup"><span data-stu-id="3abf6-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="3abf6-108">Cómo usar la descarga relacionada con la función de transferencia (HRTF) en HoloLens 2 en Unity</span><span class="sxs-lookup"><span data-stu-id="3abf6-108">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="3abf6-109">Cómo habilitar la reverberación al usar la descarga de HRTF</span><span class="sxs-lookup"><span data-stu-id="3abf6-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="3abf6-110">El [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tiene un proyecto de Unity completado de esta secuencia de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="3abf6-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="3abf6-111">Para obtener una descripción sobre lo que significa espaciale los sonidos mediante tecnologías de espacialización basadas en HRTF y recomendaciones para cuando pueda ser útil, consulte [diseño de sonido espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="3abf6-111">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="3abf6-112">¿Qué es la descarga de HRTF?</span><span class="sxs-lookup"><span data-stu-id="3abf6-112">What is HRTF offload?</span></span>
<span data-ttu-id="3abf6-113">El procesamiento de audio mediante algoritmos basados en HRTF requiere una gran cantidad de cálculos especializados.</span><span class="sxs-lookup"><span data-stu-id="3abf6-113">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="3abf6-114">HoloLens 2 incluye hardware dedicado que se puede usar para evitar sobrecargar el procesador de aplicaciones, por lo que "descarga" el procesamiento de algoritmos basados en HRTF.</span><span class="sxs-lookup"><span data-stu-id="3abf6-114">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="3abf6-115">El complemento Microsoft spatializer proporciona una manera sencilla para que la aplicación aproveche el hardware de HRTF dedicado para que la aplicación pueda usar más del procesador de aplicaciones para operaciones que no sean de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="3abf6-115">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="3abf6-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3abf6-116">Objectives</span></span>
<span data-ttu-id="3abf6-117">En este primer capítulo, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3abf6-117">In this first chapter, you'll:</span></span>
* <span data-ttu-id="3abf6-118">Creación de un proyecto de Unity e importación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3abf6-118">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="3abf6-119">Importar el complemento de Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="3abf6-119">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="3abf6-120">Habilitación del complemento Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="3abf6-120">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="3abf6-121">Habilitación del audio espacial en la estación de trabajo de desarrollador</span><span class="sxs-lookup"><span data-stu-id="3abf6-121">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="3abf6-122">Creación de un proyecto y adición de NuGet para Unity</span><span class="sxs-lookup"><span data-stu-id="3abf6-122">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="3abf6-123">Comience con un proyecto de Unity vacío y, después, agregue y configure NuGet para Unity:</span><span class="sxs-lookup"><span data-stu-id="3abf6-123">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="3abf6-124">Descargue la versión más reciente de [NuGetForUnity. unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="3abf6-124">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="3abf6-125">En la barra de menús de Unity, haga clic en **activos > importar paquete > paquete personalizado...** e instalar el paquete NuGetForUnity:</span><span class="sxs-lookup"><span data-stu-id="3abf6-125">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importar paquete personalizado](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="3abf6-127">Agregar el paquete de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3abf6-127">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="3abf6-128">La compatibilidad con Windows Mixed Reality en Unity 2019 y versiones posteriores se incluye en un paquete opcional.</span><span class="sxs-lookup"><span data-stu-id="3abf6-128">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="3abf6-129">Para agregarlo al proyecto, abra el **Administrador de paquetes de > de ventana** desde la barra de menús de Unity:</span><span class="sxs-lookup"><span data-stu-id="3abf6-129">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menú del administrador de paquetes](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="3abf6-131">A continuación, busque e instale el paquete de **Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="3abf6-131">Then find and install the **Windows Mixed Reality** package:</span></span>

![Ventana del administrador de paquetes](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="3abf6-133">Instalación de MRTK y Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="3abf6-133">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="3abf6-134">Con NuGet para Unity, instale los complementos de MRTK y Microsoft Spatializer:</span><span class="sxs-lookup"><span data-stu-id="3abf6-134">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="3abf6-135">En la barra de menús de Unity, haga clic en **Nuget-> administrar paquetes NuGet** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-135">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages** .</span></span>

![Administrar paquetes NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="3abf6-137">En el cuadro de **búsqueda** , escriba "Microsoft. MixedReality. Toolkit" e instale el paquete de MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-137">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Paquete NuGet de MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="3abf6-139">El [paquete NuGet de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) tiene contexto y detalles adicionales.</span><span class="sxs-lookup"><span data-stu-id="3abf6-139">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="3abf6-140">En el cuadro de **búsqueda** , escriba "Microsoft. SpatialAudio" e instale el paquete de Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-140">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Complemento NuGet de Spatializer](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="3abf6-142">Configuración de MRTK en el proyecto</span><span class="sxs-lookup"><span data-stu-id="3abf6-142">Set up MRTK in your project</span></span>

1. <span data-ttu-id="3abf6-143">Para abrir la ventana Configuración de compilación, vaya a **archivo-> configuración de compilación** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-143">Open the Build Settings window by going to **File -> Build Settings** .</span></span>

2. <span data-ttu-id="3abf6-144">Seleccione la _plataforma universal de Windows_ y haga clic en **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-144">Select the _Universal Windows Platform_ and click **Switch Platform** .</span></span>

3. <span data-ttu-id="3abf6-145">Haga clic en **configuración del reproductor** en la **ventana compilar** para abrir las propiedades de **configuración del reproductor** en el panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-145">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="3abf6-146">En **configuración de XR** , active la casilla **compatible con realidad virtual**</span><span class="sxs-lookup"><span data-stu-id="3abf6-146">Under **XR Settings** , check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="3abf6-147">En **configuración de XR** , cambie el **modo de representación de estéreo** a instancia de **paso único** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-147">Under **XR Settings** , change the **Stereo Rendering Mode** to **Single Pass Instanced** .</span></span>
    * <span data-ttu-id="3abf6-148">En **configuración de publicación** , active la casilla **percepción espacial** en la sección **capacidades** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-148">Under **Publishing Settings** , check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="3abf6-149">En la barra de menús, haga clic en **Kit de herramientas de realidad mixta: > agregar a la escena y configurar.**</span><span class="sxs-lookup"><span data-stu-id="3abf6-149">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="3abf6-150">para agregar MRTK a la escena.</span><span class="sxs-lookup"><span data-stu-id="3abf6-150">to add MRTK to your scene.</span></span>

<span data-ttu-id="3abf6-151">Para obtener instrucciones adicionales, incluida la forma de compilar la aplicación e implementarla en HoloLens 2, consulte [el capítulo 1 del módulo de base de aprendizaje Mr](../../../mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="3abf6-151">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="3abf6-152">Habilitación del complemento Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="3abf6-152">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="3abf6-153">Habilite el complemento de **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-153">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="3abf6-154">Abra **editar > configuración del proyecto-> audio** y cambie el **complemento Spatializer** a "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="3abf6-154">Open **Edit -> Project Settings -> Audio** , and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="3abf6-155">La sección **audio** de la **configuración del proyecto** tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="3abf6-155">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Configuración del proyecto que muestra el complemento spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="3abf6-157">Habilitación del audio espacial en la estación de trabajo</span><span class="sxs-lookup"><span data-stu-id="3abf6-157">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="3abf6-158">En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="3abf6-158">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="3abf6-159">Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="3abf6-159">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="3abf6-160">Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **sonido espacial > Windows Sonic para auriculares** .</span><span class="sxs-lookup"><span data-stu-id="3abf6-160">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones** .</span></span>

![Configuración de audio espacial de escritorio](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="3abf6-162">Esta configuración solo es necesaria si tiene previsto probar el proyecto en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="3abf6-162">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3abf6-163">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="3abf6-163">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3abf6-164">Audio espacial de Unity capítulo 2</span><span class="sxs-lookup"><span data-stu-id="3abf6-164">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

