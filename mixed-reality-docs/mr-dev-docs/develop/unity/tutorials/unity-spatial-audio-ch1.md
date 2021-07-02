---
title: 'Tutoriales de audio espacial: 1. Adición de audio espacial al proyecto'
description: Agregue el complemento Microsoft Spatializer al proyecto de Unity para acceder a HoloLens 2 descarga de hardware HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer
ms.openlocfilehash: a61e709f24c2162bc6e6e1248de658128674d49e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175377"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="69218-105">1. Adición de audio espacial al proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="69218-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="69218-106">Información general</span><span class="sxs-lookup"><span data-stu-id="69218-106">Overview</span></span>

<span data-ttu-id="69218-107">Le damos la bienvenida al tutorial de audio espacial para Unity en HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="69218-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="69218-108">A través de esta serie de tutoriales, aprenderá a usar la descarga de la función de transferencia relacionada con la cabeza (HRTF) en HoloLens 2 y a habilitar la reverberación al usar la descarga de HRTF.</span><span class="sxs-lookup"><span data-stu-id="69218-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="69218-109">El repositorio de GitHub Microsoft [Spatializer tiene](https://github.com/microsoft/spatialaudio-unity) un proyecto de Unity completado de esta secuencia de tutorial.</span><span class="sxs-lookup"><span data-stu-id="69218-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="69218-110">Para comprender lo que significa espacializar sonidos mediante tecnologías de espacialización basadas en HRTF y recomendaciones para cuándo puede ser útil, consulte [diseño de sonido espacial](/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="69218-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="69218-111">¿Qué es la descarga de HRTF?</span><span class="sxs-lookup"><span data-stu-id="69218-111">What is HRTF offload?</span></span>

<span data-ttu-id="69218-112">El procesamiento de audio mediante algoritmos basados en HRTF requiere una gran cantidad de cálculo especializado.</span><span class="sxs-lookup"><span data-stu-id="69218-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="69218-113">HoloLens 2 incluye hardware dedicado que se puede usar para evitar sobrecargar el procesador de aplicaciones, lo que "descarga" el procesamiento de algoritmos basados en HRTF.</span><span class="sxs-lookup"><span data-stu-id="69218-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="69218-114">El complemento espacializador de Microsoft proporciona una manera sencilla de que la aplicación aproveche el hardware HRTF dedicado para que la aplicación pueda usar más del procesador de aplicaciones para operaciones que no son el audio espacial.</span><span class="sxs-lookup"><span data-stu-id="69218-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="69218-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="69218-115">Objectives</span></span>

* <span data-ttu-id="69218-116">Importación y habilitación del complemento espacializador de Microsoft</span><span class="sxs-lookup"><span data-stu-id="69218-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="69218-117">Habilitación del audio espacial en la estación de trabajo para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="69218-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="69218-118">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="69218-118">Prerequisites</span></span>

* <span data-ttu-id="69218-119">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="69218-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="69218-120">Conocimientos básicos de programación de C#</span><span class="sxs-lookup"><span data-stu-id="69218-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="69218-121">Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="69218-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="69218-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS montado y el módulo compatibilidad con la compilación de plataforma universal Windows agregado</span><span class="sxs-lookup"><span data-stu-id="69218-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="69218-123">Se **recomienda encarecidamente completar** la serie [de](mr-learning-base-01.md) tutoriales de introducción o tener alguna experiencia previa básica con Unity y MRTK antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="69218-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!Important]
> <span data-ttu-id="69218-124">Esta serie de tutoriales admite Unity 2020 LTS (actualmente 2020.3.x) si usa Open XR o el complemento XR de Windows y también Unity 2019 LTS (actualmente 2019.4.x) si usa un complemento WSA o XR heredado Windows.</span><span class="sxs-lookup"><span data-stu-id="69218-124">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="69218-125">Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="69218-125">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="69218-126">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="69218-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="69218-127">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="69218-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="69218-128">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="69218-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="69218-129">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="69218-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="69218-130">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="69218-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="69218-131">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="69218-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="69218-132">Importación de la Mixed Reality Toolkit y configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="69218-132">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="69218-133">[Crear y configurar la escena y](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) dar a la escena un nombre adecuado, por ejemplo, *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="69218-133">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="69218-134">A continuación, siga las instrucciones de Cambio de la opción [de](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) visualización de reconocimiento espacial para asegurarse de que el perfil de configuración de MRTK de la escena es **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de visualización de la malla de reconocimiento espacial a **Oclusion**.</span><span class="sxs-lookup"><span data-stu-id="69218-134">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="69218-135">Agregar Microsoft Spatializer al Project</span><span class="sxs-lookup"><span data-stu-id="69218-135">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="69218-136">Descargue e importe Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="69218-136">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="69218-137">Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="69218-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="69218-138">Habilitación del complemento Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="69218-138">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="69218-139">Una vez que importe Microsoft Spatializer en el proyecto de Unity, aparecerá la ventana **MRTK Project Configurator,** use la lista desplegable **Espacializador** de audio para seleccionar **Microsoft Spatializer** y, a continuación, haga clic en el botón Aplicar para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="69218-139">Once you import the Microsoft Spatializer into your unity project, **MRTK Project Configurator** window will appear, use the **Audio spatializer** dropdown to select the **Microsoft Spatializer**, then click the Apply button to apply the setting:</span></span>

![Configurador de Project MRTK](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

<span data-ttu-id="69218-141">También puede habilitar manualmente Microsoft Spatializer: abra **Editar -> Project Configuración -> Audio** y cambie El complemento **Spatializer** a "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="69218-141">you can also manually enable the Microsoft Spatializer: Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Project Configuración complemento espacializador](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="69218-143">Habilitación del audio espacial en la estación de trabajo</span><span class="sxs-lookup"><span data-stu-id="69218-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="69218-144">En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="69218-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="69218-145">Para habilitarlo, haga clic con el botón derecho en el icono de volumen de la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="69218-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="69218-146">Para obtener la mejor representación de lo que oirá en HoloLens 2, elija **Spatial sound -> Windows Sonic para auriculares**.</span><span class="sxs-lookup"><span data-stu-id="69218-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Configuración de audio espacial de escritorio](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="69218-148">Esta configuración solo es necesaria si planea probar el proyecto en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="69218-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="69218-149">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="69218-149">Congratulations</span></span>

<span data-ttu-id="69218-150">En este tutorial ha aprendido a importar y habilitar el complemento De Microsoft Spatializer y también a habilitar el audio espacial en la estación de trabajo.</span><span class="sxs-lookup"><span data-stu-id="69218-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="69218-151">En el siguiente tutorial, aprenderá a agregar audio espacial en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="69218-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="69218-152">Tutorial siguiente: 2. Espacialización de los sonidos de interacción del botón</span><span class="sxs-lookup"><span data-stu-id="69218-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
