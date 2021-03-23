---
title: Creación de una aplicación para equipos de comunicación remota holográfica
description: Siga este curso para aprender cómo crear una aplicación de PC para la comunicación remota de una experiencia de realidad mixta remota del equipo a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, PC holographic remoting, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 916a9396c0b29637d5619bac203718e05112b598
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590307"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="5c2ec-104">2. Creación de una aplicación para PC de comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="5c2ec-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="5c2ec-105">En este tutorial, aprenderá cómo crear una aplicación de PC para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="5c2ec-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5c2ec-106">Objectives</span></span>

* <span data-ttu-id="5c2ec-107">Configurar Unity para la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="5c2ec-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="5c2ec-108">Aprender a compilar e implementar la aplicación con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5c2ec-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="5c2ec-109">Desarrollar una aplicación de comunicación remota holográfica y conectarla a HoloLens</span><span class="sxs-lookup"><span data-stu-id="5c2ec-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="5c2ec-110">Configurar la escena para la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="5c2ec-110">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="5c2ec-111">En esta sección, configurará el proyecto para que transmita la experiencia de realidad mixta a su dispositivo HoloLens 2 desde su PC en tiempo real a través de una conexión Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-111">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="5c2ec-112">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** y haga clic y arrastre el elemento prefabricado **HolographicRemoting** a la escena.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![Unity con el objeto prefabricado HolographicRemoting recién agregado aún seleccionado](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="5c2ec-114">Compilación de la aplicación para PC</span><span class="sxs-lookup"><span data-stu-id="5c2ec-114">Build your application to PC</span></span>

<span data-ttu-id="5c2ec-115">La aplicación de comunicación remota holográfica ya está lista para compilarse en su PC.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-115">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="5c2ec-116">Siga los pasos que se indican a continuación y realice estos cambios para compilar esta aplicación en su PC.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-116">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="5c2ec-117">1. Configuración del reproductor</span><span class="sxs-lookup"><span data-stu-id="5c2ec-117">1. Set the player settings</span></span>

<span data-ttu-id="5c2ec-118">En el menú de Unity, seleccione Edit > Project Settings (Editar > Configuración del proyecto) para abrir la ventana Player Settings (Configuración del reproductor):</span><span class="sxs-lookup"><span data-stu-id="5c2ec-118">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="5c2ec-119">En la ventana Project Settings (Configuración del proyecto), expanda **Publishing Settings** (Configuración de la publicación), desplácese hacia abajo a la sección **Funcionalidades** y seleccione la casilla de funcionalidad que aparece a continuación además de las funcionalidades ya existentes.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-119">In the Project Settings window, expand the **Publishing Settings**, scroll down to the **Capabilities** section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="5c2ec-120">Servidor cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="5c2ec-120">Internet Clint server</span></span>
* <span data-ttu-id="5c2ec-121">Servidor cliente de red privada</span><span class="sxs-lookup"><span data-stu-id="5c2ec-121">Private Network Client Server</span></span>

<span data-ttu-id="5c2ec-122">En la sección **XR Settings** (Configuración de XR), seleccione la casilla **WSA Holographic Remoting Supported** (Admitir la comunicación remota holográfica de WSA) y habilite la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-122">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Ventana XR Settings (Configuración de XR) de Unity con WSA Holographic Remoting Supported (Admitir la comunicación remota holográfica de WSA) habilitado](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="5c2ec-124">2. Compilación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="5c2ec-124">2. Build the Unity Project</span></span>

<span data-ttu-id="5c2ec-125">En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="5c2ec-125">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="5c2ec-126">En la ventana Build Settings (Configuración de compilación), haga clic en el botón \***Add Open Scenes** _ (Agregar escenas abiertas) para agregar la escena actual a las escenas.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-126">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="5c2ec-127">En la lista Build (Compilación), haga clic en el *_botón Build_* (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows):</span><span class="sxs-lookup"><span data-stu-id="5c2ec-127">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la escena agregada](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="5c2ec-129">En la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows), elija una ubicación adecuada para almacenar la compilación, como por ejemplo, Mis Documentos\AprendizajeRealidadMixta.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-129">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="5c2ec-130">Cree una nueva carpeta y asígnele un nombre adecuado, por ejemplo, ComunicaciónRemotaHolográficaPC.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-130">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="5c2ec-131">A continuación, haga clic en el botón ***Select Folder*** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="5c2ec-131">Then click the ***Select Folder*** button to start the build process:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="5c2ec-133">Espere a que Unity finalice el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-133">Wait for Unity to finish the build process.</span></span>

![Proceso de compilación de Unity en curso](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="5c2ec-135">3. Compilar e implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="5c2ec-135">3. Build and deploy the application</span></span>

<span data-ttu-id="5c2ec-136">Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-136">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="5c2ec-137">Navegue dentro de la carpeta y haga doble clic en el archivo .sln para abrirlo en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="5c2ec-137">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Explorador de Windows con la solución de Visual Studio recién creada seleccionada](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="5c2ec-139">Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que todos los componentes de los requisitos previos estén instalados, tal como se especifica en la documentación Instalación de herramientas.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-139">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="5c2ec-140">Configure Visual Studio para PC. Para ello, selecciona la configuración Publicación, la arquitectura x64 y la opción Equipo local como destino:</span><span class="sxs-lookup"><span data-stu-id="5c2ec-140">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Visual Studio configurado para el equipo local](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="5c2ec-142">Haga clic en el botón que indica ***Equipo local***.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-142">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="5c2ec-143">Comienza la compilación e implementación de la aplicación en el PC.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-143">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="5c2ec-144">La aplicación se instalará de forma predeterminada en su PC.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-144">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="5c2ec-145">Prueba de la aplicación remota de comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="5c2ec-145">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="5c2ec-146">Para conectar la aplicación de PC a HoloLens 2, siga el proceso siguiente:</span><span class="sxs-lookup"><span data-stu-id="5c2ec-146">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="5c2ec-147">1. Instalación de la aplicación Remoting Player en el dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5c2ec-147">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="5c2ec-148">En HoloLens 2, visite la aplicación Store y busque "**Remoting Player**".</span><span class="sxs-lookup"><span data-stu-id="5c2ec-148">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="5c2ec-149">Seleccione la aplicación **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-149">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="5c2ec-150">Pulse **Instalar** una vez para descargar e instalar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-150">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="5c2ec-151">2. Conexión de la aplicación de comunicación remota holográfica para PC a Remoting Player</span><span class="sxs-lookup"><span data-stu-id="5c2ec-151">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="5c2ec-152">Inicie **Remoting Player** en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-152">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="5c2ec-153">Tome nota de la **dirección IP** de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-153">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="5c2ec-154">**Remoting Player** la mostrará como un holograma en cuanto se inicie.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-154">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="5c2ec-155">Abra la aplicación de comunicación remota holográfica para PC en su PC.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-155">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="5c2ec-156">Una vez iniciada la aplicación, escriba la **dirección IP** y haga clic en el botón **Conectar** para conectarse.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-156">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5c2ec-157">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="5c2ec-157">Congratulations</span></span>

<span data-ttu-id="5c2ec-158">En este tutorial, aprendió cómo crear una aplicación para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-158">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="5c2ec-159">Una vez que HoloLens esté conectado a la aplicación de comunicación remota holográfica para PC, debería ver la experiencia de realidad mixta transmitida en el dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-159">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
