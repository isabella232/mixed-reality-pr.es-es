---
title: 'Tutoriales de los servicios de voz de Azure: 1. Integración y uso de reconocimiento de voz y la transcripción'
description: Haz este curso para aprender a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, speech recognition, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 39eaa8a17d4616dc9c044f9bff7522dde41cffb7
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656629"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="b2e5a-105">1. Integración y uso del reconocimiento de voz y la transcripción</span><span class="sxs-lookup"><span data-stu-id="b2e5a-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="b2e5a-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="b2e5a-106">Overview</span></span>

<span data-ttu-id="b2e5a-107">En esta serie de tutoriales, crearás una aplicación de Mixed Reality que explore el uso de los servicios de voz de Azure con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="b2e5a-108">Cuando completes esta serie de tutoriales, podrás usar el micrófono del dispositivo para transcribir la voz a texto en tiempo real, traducir la voz a otros idiomas y aprovechar la característica Reconocimiento de la intención para comprender los comandos de voz mediante inteligencia artificial.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="b2e5a-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b2e5a-109">Objectives</span></span>

* <span data-ttu-id="b2e5a-110">Aprender a integrar los servicios de voz de Azure con una aplicación de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b2e5a-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="b2e5a-111">Aprender a usar el reconocimiento de voz para transcribir texto</span><span class="sxs-lookup"><span data-stu-id="b2e5a-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2e5a-112">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b2e5a-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="b2e5a-113">Si aún no has completado la serie de [tutoriales de introducción](mr-learning-base-01.md), es recomendable que lo hagas en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="b2e5a-114">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="b2e5a-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="b2e5a-115">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="b2e5a-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b2e5a-116">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="b2e5a-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="b2e5a-117">Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="b2e5a-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="b2e5a-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="b2e5a-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="b2e5a-119">Esta serie de tutoriales admite Unity 2020 LTS (actualmente 2020.3.x) si usa Open XR o el complemento de XR de Windows y también Unity 2019 LTS (actualmente 2019.4.x) si usa WSA heredado o el complemento de XR de Windows.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-119">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="b2e5a-120">Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-120">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="b2e5a-121">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="b2e5a-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="b2e5a-122">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="b2e5a-123">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="b2e5a-124">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="b2e5a-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="b2e5a-125">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="b2e5a-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="b2e5a-126">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="b2e5a-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="b2e5a-127">Importación de Mixed Reality Toolkit y configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="b2e5a-127">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="b2e5a-128">[Crear y configurar la escena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) y asignarle un nombre adecuado; por ejemplo, *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="b2e5a-128">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="b2e5a-129">A continuación, siga las instrucciones de [Cambio de la opción de visualización del reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para asegurarse de que el perfil de configuración de MRTK de la escena sea **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="b2e5a-129">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="b2e5a-130">Configurar el comportamiento inicial de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="b2e5a-130">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="b2e5a-131">Dado que usarás el SDK de voz para el reconocimiento de voz y la transcripción, debes configurar los comandos de voz de MRTK para que no interfieran con la funcionalidad del SDK de voz.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-131">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="b2e5a-132">Para ello, puedes cambiar el comportamiento inicial de los comandos de voz de Auto Start (Inicio automático) a Manual Start (Inicio manual).</span><span class="sxs-lookup"><span data-stu-id="b2e5a-132">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="b2e5a-133">Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, selecciona la pestaña **Input** (Entrada), clona **DefaultHoloLens2InputSystemProfile** y **DefaultMixedRealitySpeechCommandsProfile** y, a continuación, cambia el valor de **Start Behavior** (Comportamiento inicial) de los comandos de voz a **Manual Start** (Inicio manual):</span><span class="sxs-lookup"><span data-stu-id="b2e5a-133">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a><span data-ttu-id="b2e5a-135">Configuración de las funcionalidades</span><span class="sxs-lookup"><span data-stu-id="b2e5a-135">Configuring the capabilities</span></span>

<span data-ttu-id="b2e5a-136">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="b2e5a-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="b2e5a-138">En **Publishing Settings** (Configuración de publicación), desplácese hasta la sección **Capabilities** (Funcionalidades) y compruebe nuevamente que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception**, que se habilitaron al crear el proyecto al principio del tutorial, estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which was enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="b2e5a-139">A continuación, habilita las funcionalidades **InternetClientServer** y **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-139">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b2e5a-141">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="b2e5a-141">Importing the tutorial assets</span></span>

<span data-ttu-id="b2e5a-142">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-142">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="b2e5a-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versión más reciente)</span><span class="sxs-lookup"><span data-stu-id="b2e5a-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="b2e5a-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2e5a-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="b2e5a-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b2e5a-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span></span>](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> <span data-ttu-id="b2e5a-146">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo [Importación de Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="b2e5a-146">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="b2e5a-147">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-147">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

<span data-ttu-id="b2e5a-149">Tiene que configurar el proyecto de Unity para publicar los complementos de Voz de Azure para ARM64; para ello, en la ventana de Project (Proyecto), vaya a **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** (Recursos > SpeechSDK > Complementos > WSA > ARM64) y seleccione el complemento **Microsoft.CognitiveServices.Speech.core**.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-149">You need to setup the Unity project to publish the Azure Speech plugins for ARM64,to do this in the Project window, navigate to **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** and select **Microsoft.CognitiveServices.Speech.core** plugin.</span></span>

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

<span data-ttu-id="b2e5a-151">Con el complemento **Microsoft.CognitiveServices.Speech.core** aún seleccionado, en la ventana Inspector, habilite **WSA Player** (Reproductor de WSA) en **Platform settings** (Configuración de la plataforma), seleccione **UWP** para SDK, **ARM64** para CPU, y haga clic en Apply (Aplicar) para aplicar esta configuración al complemento.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-151">with **Microsoft.CognitiveServices.Speech.core** plugin still selected, in the inspector window Enable **WSA Player** then under **Platform settings** select **UWP** for SDK, **ARM64** for CPU and click on Apply to apply these settings to the plugin.</span></span>

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

<span data-ttu-id="b2e5a-153">Repita estos pasos para cada uno de los complementos restantes:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-153">Repeat this steps for each of the remaining plugins:</span></span>

* <span data-ttu-id="b2e5a-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span><span class="sxs-lookup"><span data-stu-id="b2e5a-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span></span>
* <span data-ttu-id="b2e5a-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span><span class="sxs-lookup"><span data-stu-id="b2e5a-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span></span>
* <span data-ttu-id="b2e5a-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span><span class="sxs-lookup"><span data-stu-id="b2e5a-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span></span>
* <span data-ttu-id="b2e5a-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span><span class="sxs-lookup"><span data-stu-id="b2e5a-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="b2e5a-158">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="b2e5a-158">Preparing the scene</span></span>

<span data-ttu-id="b2e5a-159">En esta sección, prepararás la escena agregando el objeto prefabricado del tutorial y configurarás el componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) para controlar la escena.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-159">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="b2e5a-160">En la ventana Project (Proyecto), desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpeechServices** > carpeta **Prefabs** y arrastra y coloca el objeto prefabricado **Lunarcom** en la ventana Hierarchy (Jerarquía) para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-160">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="b2e5a-162">Con el objeto **Lunarcom** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) al objeto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-162">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="b2e5a-164">El componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-164">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="b2e5a-165">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-165">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="b2e5a-166">Con el objeto **Lunarcom** todavía seleccionado, expándelo para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **Terminal** al campo **Terminal** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]):</span><span class="sxs-lookup"><span data-stu-id="b2e5a-166">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="b2e5a-168">Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Terminal para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **ConnectionLight** al campo **Connection Light** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) y el objeto **OutputText** al campo **Output Text** (Texto de salida):</span><span class="sxs-lookup"><span data-stu-id="b2e5a-168">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="b2e5a-170">Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Buttons para mostrar sus objetos secundarios y, a continuación, en la ventana Inspector, expande la lista **Buttons** (Botones), establece su valor de **Size** (Tamaño) en 3 y arrastra los objetos **MicButton**, **SatelliteButton** y **RocketButton** a los campos de **Element** (Elemento) 0, 1 y 2, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-170">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="b2e5a-172">Conexión del proyecto de Unity con el recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="b2e5a-172">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="b2e5a-173">Para usar los servicios de voz de Azure, debes crear un recurso de Azure y obtener una clave de API para el servicio de voz.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-173">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="b2e5a-174">Sigue las instrucciones de [Prueba gratuita del servicio Voz](/azure/cognitive-services/speech-service/get-started) y toma nota de la región de servicio (también conocida como ubicación) y la clave de API (también conocida como Key1 o Key2).</span><span class="sxs-lookup"><span data-stu-id="b2e5a-174">Follow the [Try the Speech service for free](/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="b2e5a-175">En la ventana Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, busca la sección **Speech SDK Credentials** (Credenciales del SDK de voz) de **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) y configúrala como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-175">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="b2e5a-176">En el campo **Speech Service API Key** (Clave de API del servicio Voz), escribe la clave de API (Key1 o Key2)</span><span class="sxs-lookup"><span data-stu-id="b2e5a-176">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="b2e5a-177">En el campo **Speech Service Region** (Región del servicio Voz), escribe tu región de servicio (ubicación) con letras minúsculas y sin espacios.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-177">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="b2e5a-179">Uso del reconocimiento de voz para transcribir la voz</span><span class="sxs-lookup"><span data-stu-id="b2e5a-179">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="b2e5a-180">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Speech Recognizer (Script)** (Reconocimiento de voz de Lunarcom [script]):</span><span class="sxs-lookup"><span data-stu-id="b2e5a-180">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b2e5a-182">El componente Lunarcom Speech Recognizer (Script) (Reconocimiento de voz de Lunarcom [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-182">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="b2e5a-183">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-183">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="b2e5a-184">Si ahora entras en el modo de juego, puedes probar el reconocimiento de voz presionando primero el botón del micrófono:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-184">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="b2e5a-186">A continuación, suponiendo que el equipo tiene un micrófono, cuando digas algo, la voz se transcribirá en el panel del terminal:</span><span class="sxs-lookup"><span data-stu-id="b2e5a-186">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="b2e5a-188">La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-188">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b2e5a-189">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="b2e5a-189">Congratulations</span></span>

<span data-ttu-id="b2e5a-190">Has implementado el reconocimiento de voz con tecnología de Azure.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-190">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="b2e5a-191">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-191">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="b2e5a-192">En el próximo tutorial, obtendrás información sobre cómo ejecutar comandos con el reconocimiento de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="b2e5a-192">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2e5a-193">Siguiente tutorial: 2. Ejecución de comandos mediante el reconocimiento de voz de Azure</span><span class="sxs-lookup"><span data-stu-id="b2e5a-193">Next tutorial: 2. Execute commands using Azure speech recognition</span></span>](mrlearning-speechSDK-ch2.md)
