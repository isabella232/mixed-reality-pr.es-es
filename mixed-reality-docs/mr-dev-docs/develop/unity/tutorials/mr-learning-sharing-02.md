---
title: Configuración de Photon Unity Networking
description: Siga este curso para aprender a implementar Photon Unity Networking en una aplicación de realidad mixta de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, multi-user capabilities, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, PUN
ms.localizationpriority: high
ms.openlocfilehash: 4b81ed3a78cc47f4ad0463cab085621102060dc8
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982768"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="90d25-104">2. Configuración de Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="90d25-104">2. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="90d25-105">En este tutorial, se preparará para la creación de una experiencia compartida con Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="90d25-105">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="90d25-106">Obtendrá información sobre cómo crear una aplicación de PUN, importar recursos de PUN en el proyecto de Unity y conectar el proyecto de Unity a la aplicación de PUN.</span><span class="sxs-lookup"><span data-stu-id="90d25-106">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="90d25-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="90d25-107">Objectives</span></span>

* <span data-ttu-id="90d25-108">Aprender cómo crear una aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="90d25-108">Learn how to create a PUN app</span></span>
* <span data-ttu-id="90d25-109">Aprender cómo buscar e importar los recursos de PUN</span><span class="sxs-lookup"><span data-stu-id="90d25-109">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="90d25-110">Aprender a conectar el proyecto de Unity a la aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="90d25-110">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="90d25-111">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="90d25-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="90d25-112">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="90d25-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="90d25-113">Primero, debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="90d25-113">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="90d25-114">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="90d25-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="90d25-115">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="90d25-115">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="90d25-116">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="90d25-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="90d25-117">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="90d25-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="90d25-118">Configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="90d25-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="90d25-119">[Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignar un nombre adecuado a la escena; por ejemplo, *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="90d25-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="90d25-120">A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:</span><span class="sxs-lookup"><span data-stu-id="90d25-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="90d25-121">Cambiar el **perfil de configuración de MRTK** por **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="90d25-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="90d25-122">Cambiar las **opciones de visualización de la malla de reconocimiento espacial** a **Oclusión**.</span><span class="sxs-lookup"><span data-stu-id="90d25-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="90d25-123">Habilitación de funcionalidades adicionales</span><span class="sxs-lookup"><span data-stu-id="90d25-123">Enabling additional capabilities</span></span>

<span data-ttu-id="90d25-124">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="90d25-124">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![Player Settings (Configuración del reproductor) de Unity](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="90d25-126">En **Configuración de publicación**, desplácese hasta la sección **Funcionalidades** y compruebe que las funcionalidades **InternetClient**, **Microphone**, **SpatialPerception** y **GazeInput** que habilitó durante el paso anterior titulado [Configuración del proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project), estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="90d25-126">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="90d25-127">A continuación, habilite las siguientes funcionalidades adicionales:</span><span class="sxs-lookup"><span data-stu-id="90d25-127">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="90d25-128">Funcionalidad **InternetClientServer**</span><span class="sxs-lookup"><span data-stu-id="90d25-128">**InternetClientServer** capability</span></span>
* <span data-ttu-id="90d25-129">Funcionalidad **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="90d25-129">**PrivateNetworkClientServer** capability</span></span>

![Capabilities Settings (Configuración de funcionalidades) de Unity](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="90d25-131">Instalación de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="90d25-131">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="90d25-132">En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation** y haga clic en el botón **Install** (Instalar) para instalar el paquete:</span><span class="sxs-lookup"><span data-stu-id="90d25-132">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Unity Package Manager con AR Foundation seleccionado](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="90d25-134">Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="90d25-134">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="90d25-135">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="90d25-135">Importing the tutorial assets</span></span>

<span data-ttu-id="90d25-136">Agregue el SDK de Azure Spatial Anchors V2.7.1 al proyecto de Unity. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="90d25-136">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>


<span data-ttu-id="90d25-137">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="90d25-137">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>
 
* [<span data-ttu-id="90d25-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="90d25-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="90d25-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="90d25-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="90d25-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="90d25-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="90d25-141">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="90d25-141">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="90d25-143">Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](mr-learning-base-02.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="90d25-143">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="90d25-144">Después de importar el paquete de recursos del tutorial de MultiUserCapabilities, verás varios errores con el código [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) en la ventana de la consola en los que se indicará que falta el tipo o el espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="90d25-144">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="90d25-145">Este comportamiento es el esperado y se resolverá en la sección siguiente cuando importes los recursos de PUN.</span><span class="sxs-lookup"><span data-stu-id="90d25-145">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="90d25-146">Importación de recursos de PUN</span><span class="sxs-lookup"><span data-stu-id="90d25-146">Importing the PUN assets</span></span>

<span data-ttu-id="90d25-147">En el menú de Unity, seleccione **Ventana** > **Asset Store** (Almacén de recursos) para abrir la ventana del almacén de recursos, busque y seleccione **PUN 2 - FREE** de Exit Games y haga clic en el botón **Descargar** para descargar el paquete de recursos en su cuenta de Unity.</span><span class="sxs-lookup"><span data-stu-id="90d25-147">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="90d25-148">Una vez completada la descarga, haz clic en el botón **Importar** para abrir la ventana Import Unity Package (Importar paquete de Unity):</span><span class="sxs-lookup"><span data-stu-id="90d25-148">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![Asset Store (Almacén de recursos) de Unity con PUN 2 - Free](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="90d25-150">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="90d25-150">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Ventana de importación de Unity con PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="90d25-152">Una vez que Unity haya completado el proceso de importación, se mostrará la ventana Pun Wizard (Asistente para PUN) con el menú de configuración de PUN cargado. Por ahora, puedes omitir o cerrar esta ventana:</span><span class="sxs-lookup"><span data-stu-id="90d25-152">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![Ventana de importación de Unity con PUN Setup (Instalación de PUN)](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="90d25-154">Creación de la aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="90d25-154">Creating the PUN application</span></span>

<span data-ttu-id="90d25-155">En esta sección, creará una cuenta de Photon, si aún no tiene ninguna, y creará una nueva aplicación de PUN.</span><span class="sxs-lookup"><span data-stu-id="90d25-155">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="90d25-156">Ve al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">panel</a> de Photon e inicia sesión si ya tienes una cuenta que quieras usar. De lo contrario, haz clic en el vínculo **Crear una** y sigue las instrucciones para registrar una cuenta nueva:</span><span class="sxs-lookup"><span data-stu-id="90d25-156">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![Página de inicio de sesión de Photon](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="90d25-158">Una vez que hayas iniciado sesión, haz clic en el botón **Crear una nueva aplicación**:</span><span class="sxs-lookup"><span data-stu-id="90d25-158">Once signed in, click the **Create a New App** button:</span></span>

![Página de bienvenida del panel de Photon](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="90d25-160">En la página Crear una nueva aplicación, escribe los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="90d25-160">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="90d25-161">En Photon Type (Tipo de Photon), seleccione PUN.</span><span class="sxs-lookup"><span data-stu-id="90d25-161">For Photon Type, select PUN</span></span>
* <span data-ttu-id="90d25-162">En Nombre, escribe un nombre adecuado, por ejemplo, _Tutoriales de MRTK_.</span><span class="sxs-lookup"><span data-stu-id="90d25-162">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="90d25-163">En Descripción, puedes escribir una descripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="90d25-163">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="90d25-164">En URL, deja el campo vacío.</span><span class="sxs-lookup"><span data-stu-id="90d25-164">For Url, leave the field empty</span></span>

<span data-ttu-id="90d25-165">A continuación, haga clic en el botón **Crear** para crear la nueva aplicación:</span><span class="sxs-lookup"><span data-stu-id="90d25-165">Then click the **Create** button to create the new app:</span></span>

![Página de creación de aplicaciones de Photon](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="90d25-167">Una vez que Photon haya finalizado el proceso de creación, la nueva aplicación de PUN se mostrará en el panel:</span><span class="sxs-lookup"><span data-stu-id="90d25-167">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![Página de la aplicación de Photon](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="90d25-169">Conexión del proyecto de Unity con la aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="90d25-169">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="90d25-170">En esta sección, conectará el proyecto de Unity a la aplicación de PUN que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="90d25-170">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="90d25-171">En el panel de Photon, haz clic en el campo **Id. de la aplicación** para mostrar el identificador de la aplicación y, a continuación, cópialo en el portapapeles:</span><span class="sxs-lookup"><span data-stu-id="90d25-171">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![Página de la aplicación de Photon con el identificador de aplicación seleccionado](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="90d25-173">En el menú de Unity, selecciona **Ventana** > **Photon Unity Networking** > **Pun Wizard** (Asistente para PUN) para abrir la ventana del asistente para PUN, haz clic en el botón **Proyecto de instalación** para abrir el menú de configuración de PUN y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="90d25-173">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="90d25-174">En el campo **AppId or Email** (Id. de la aplicación o correo electrónico), pega el identificador de la aplicación de PUN que copiaste en el paso anterior</span><span class="sxs-lookup"><span data-stu-id="90d25-174">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="90d25-175">A continuación, haz clic en el botón **Proyecto de instalación** para aplicar el id. de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="90d25-175">Then click the **Setup Project** button to apply the app ID:</span></span>

![Ventana PUN Setup (Instalación de PUN) de Unity con AppId rellenado](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="90d25-177">Una vez que Unity termine el proceso de configuración de PUN, se mostrará el mensaje **Listo** en el menú de configuración de PUN.</span><span class="sxs-lookup"><span data-stu-id="90d25-177">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="90d25-178">Asimismo, se seleccionará automáticamente el recurso **PhotonServerSettings** en la ventana Proyecto para que sus propiedades se muestren en la ventana Inspector:</span><span class="sxs-lookup"><span data-stu-id="90d25-178">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![Ventana PUN Setup (Instalación de PUN) de Unity con el proyecto de instalación aplicado](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="90d25-180">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="90d25-180">Congratulations</span></span>

<span data-ttu-id="90d25-181">Creó correctamente una aplicación de PUN y la conectó al proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="90d25-181">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="90d25-182">El siguiente paso consiste en permitir las conexiones con otros usuarios para que varios usuarios puedan verse entre sí.</span><span class="sxs-lookup"><span data-stu-id="90d25-182">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90d25-183">Tutorial siguiente: 3. Conexión de varios usuarios</span><span class="sxs-lookup"><span data-stu-id="90d25-183">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)