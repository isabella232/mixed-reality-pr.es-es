---
title: 'Tutoriales de audio espacial: 1. Agregar audio espacial al proyecto'
description: Agregue el complemento de Microsoft Spatializer a su proyecto de Unity para acceder a la descarga de hardware de HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer
ms.openlocfilehash: cc7a4db5a3b4d853f2912a5e8e022fddd372e105
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635393"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="fa9c2-105">1. agregar audio espacial a su proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="fa9c2-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="fa9c2-106">Información general</span><span class="sxs-lookup"><span data-stu-id="fa9c2-106">Overview</span></span>

<span data-ttu-id="fa9c2-107">Este es el tutorial de audio espacial para Unity en HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="fa9c2-108">A través de esta serie de tutoriales, aprenderá a usar la descarga de la función de transferencia relacionada con el encabezado (HRTF) en HoloLens 2 y cómo habilitar reverberación al usar la descarga de HRTF.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="fa9c2-109">El [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tiene un proyecto de Unity completado de esta secuencia de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="fa9c2-110">Para obtener una descripción de lo que significa para espaciales con las tecnologías de espacialización basadas en HRTF y las recomendaciones para cuando pueda ser útil, consulte [diseño de sonido espacial](/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="fa9c2-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="fa9c2-111">¿Qué es la descarga de HRTF?</span><span class="sxs-lookup"><span data-stu-id="fa9c2-111">What is HRTF offload?</span></span>

<span data-ttu-id="fa9c2-112">El procesamiento de audio mediante algoritmos basados en HRTF requiere una gran cantidad de cálculos especializados.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="fa9c2-113">HoloLens 2 incluye hardware dedicado que se puede usar para evitar sobrecargar el procesador de aplicaciones, por lo que "descarga" el procesamiento de algoritmos basados en HRTF.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="fa9c2-114">El complemento Microsoft spatializer proporciona una manera sencilla para que la aplicación aproveche el hardware de HRTF dedicado para que la aplicación pueda usar más del procesador de aplicaciones para operaciones que no sean de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="fa9c2-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fa9c2-115">Objectives</span></span>

* <span data-ttu-id="fa9c2-116">Importación y habilitación del complemento de Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="fa9c2-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="fa9c2-117">Habilitación del audio espacial en la estación de trabajo de desarrollador</span><span class="sxs-lookup"><span data-stu-id="fa9c2-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa9c2-118">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="fa9c2-118">Prerequisites</span></span>

* <span data-ttu-id="fa9c2-119">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="fa9c2-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="fa9c2-120">Conocimientos básicos de programación de C#</span><span class="sxs-lookup"><span data-stu-id="fa9c2-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="fa9c2-121">Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="fa9c2-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="fa9c2-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS montado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="fa9c2-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="fa9c2-123">Se **recomienda** completar la serie de tutoriales de [Introducción](mr-learning-base-01.md) o tener una experiencia previa básica con Unity y MRTK antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="fa9c2-124">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="fa9c2-125">Sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="fa9c2-126">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="fa9c2-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="fa9c2-127">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="fa9c2-128">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="fa9c2-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="fa9c2-129">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="fa9c2-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="fa9c2-130">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="fa9c2-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="fa9c2-131">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="fa9c2-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="fa9c2-132">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="fa9c2-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="fa9c2-133">Configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="fa9c2-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="fa9c2-134">[Crear y establecer la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignar a la escena un nombre adecuado, por ejemplo, *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="fa9c2-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="fa9c2-135">Después, siga las instrucciones de la [opción de visualización cambiar el reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para asegurarse de que el perfil de configuración de MRTK para la escena sea **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de presentación de la malla de reconocimiento espacial a **oclusión**.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="fa9c2-136">Agregando Microsoft Spatializer al proyecto</span><span class="sxs-lookup"><span data-stu-id="fa9c2-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="fa9c2-137">Descargue e importe Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. unitypackage Tools </a></span><span class="sxs-lookup"><span data-stu-id="fa9c2-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="fa9c2-138">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="fa9c2-138">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="fa9c2-139">Habilitación del complemento Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="fa9c2-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="fa9c2-140">Después de importar la **Spatializer de Microsoft** , debe habilitarla.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="fa9c2-141">Abra **editar > configuración del proyecto-> audio** y cambie el **complemento Spatializer** a "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="fa9c2-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Configuración del proyecto que muestra el complemento spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="fa9c2-143">Habilitación del audio espacial en la estación de trabajo</span><span class="sxs-lookup"><span data-stu-id="fa9c2-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="fa9c2-144">En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="fa9c2-145">Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="fa9c2-146">Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **sonido espacial > Windows Sonic para auriculares**.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Configuración de audio espacial de escritorio](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fa9c2-148">Esta configuración solo es necesaria si tiene previsto probar el proyecto en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fa9c2-149">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="fa9c2-149">Congratulations</span></span>

<span data-ttu-id="fa9c2-150">En este tutorial, aprenderá a importar y habilitar el complemento Microsoft Spatializer y también a habilitar el audio espacial en la estación de trabajo.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="fa9c2-151">En el siguiente tutorial, aprenderá a agregar audio espacial en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fa9c2-152">Siguiente tutorial: 2. Spatial los sonidos de interacción del botón</span><span class="sxs-lookup"><span data-stu-id="fa9c2-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
