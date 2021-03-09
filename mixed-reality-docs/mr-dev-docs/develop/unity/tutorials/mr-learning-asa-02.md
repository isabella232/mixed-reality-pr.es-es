---
title: Introducción a Azure Spatial Anchors
description: Siga este curso para aprender a usar Azure Spatial Anchors dentro para anclar objetos en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: a44e79d656875d7730ee155e10260bd5ebb6265f
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237126"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="d7fb8-104">2. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d7fb8-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="d7fb8-105">En este tutorial, explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors, y para crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="d7fb8-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d7fb8-106">Objectives</span></span>

* <span data-ttu-id="d7fb8-107">Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d7fb8-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="d7fb8-108">Aprender a crear anclajes espaciales y a capturarlos desde Azure</span><span class="sxs-lookup"><span data-stu-id="d7fb8-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="d7fb8-109">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="d7fb8-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="d7fb8-110">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="d7fb8-111">Primero, debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="d7fb8-112">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="d7fb8-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="d7fb8-113">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="d7fb8-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="d7fb8-114">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="d7fb8-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="d7fb8-115">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="d7fb8-115">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="d7fb8-116">Configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="d7fb8-116">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="d7fb8-117">[Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignarle un nombre adecuado; por ejemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="d7fb8-117">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="d7fb8-118">A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-118">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="d7fb8-119">Cambiar el **perfil de configuración de MRTK** por **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-119">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="d7fb8-120">Cambiar las **opciones de visualización de la malla de reconocimiento espacial** a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-120">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="d7fb8-121">Instalación de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="d7fb8-121">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="d7fb8-122">En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation** y haga clic en el botón **Install** (Instalar) para instalar el paquete:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-122">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Unity Package Manager con AR Foundation seleccionado](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d7fb8-124">Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-124">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d7fb8-125">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="d7fb8-125">Importing the tutorial assets</span></span>

<span data-ttu-id="d7fb8-126">Agregue el SDK de Azure Spatial Anchors V2.7.1 al proyecto de Unity. Para agregar los paquetes, siga este [tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-126">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="d7fb8-127">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-127">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>


* [<span data-ttu-id="d7fb8-128">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d7fb8-128">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="d7fb8-129">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d7fb8-129">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage)

<span data-ttu-id="d7fb8-130">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-130">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d7fb8-132">Si ve que las advertencias de CS0618 con respecto a "WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)" están en desuso, puede omitir estas advertencias.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-132">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="d7fb8-133">Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-133">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d7fb8-134">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="d7fb8-134">Preparing the scene</span></span>

<span data-ttu-id="d7fb8-135">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="d7fb8-136">En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** y, a continuación, haga clic y arrastre los siguientes objetos prefabricados a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-136">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="d7fb8-137">Objeto prefabricado **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="d7fb8-137">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="d7fb8-138">Objeto prefabricado **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="d7fb8-138">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="d7fb8-139">Objeto prefabricado **Instructions**</span><span class="sxs-lookup"><span data-stu-id="d7fb8-139">**Instructions** prefabs</span></span>
* <span data-ttu-id="d7fb8-140">Objeto prefabricado **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="d7fb8-140">**ParentAnchor** prefabs</span></span>

![Unity con los objetos prefabricados recién agregados seleccionados](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="d7fb8-142">Si le molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puede ocultarlos. Para hacerlo, desactive los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>, como se muestra en la imagen anterior.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-142">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="d7fb8-143">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="d7fb8-143">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="d7fb8-144">En esta sección, agregará scripts a la escena para crear una serie de eventos de botón que muestren los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-144">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="d7fb8-145">En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-145">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d7fb8-146">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-146">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7fb8-147">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-147">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón StartAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="d7fb8-149">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **StopAzureSession**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-149">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d7fb8-150">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-150">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7fb8-151">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StopAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-151">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón StopAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="d7fb8-153">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **CreateAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-153">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d7fb8-154">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-154">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7fb8-155">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **CreateAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-155">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="d7fb8-156">Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="d7fb8-156">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity con el evento OnClick del botón CreateAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="d7fb8-158">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **RemoveLocalAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-158">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d7fb8-159">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-159">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7fb8-160">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **RemoveLocalAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-160">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="d7fb8-161">Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="d7fb8-161">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity con el evento OnClick del botón RemoveLocalAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="d7fb8-163">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **FindAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-163">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d7fb8-164">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-164">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7fb8-165">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **FindAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-165">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón FindAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="d7fb8-167">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **DeleteAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-167">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d7fb8-168">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-168">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7fb8-169">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **DeleteAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-169">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón DeleteAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="d7fb8-171">Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="d7fb8-171">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="d7fb8-172">En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, busque el componente **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="d7fb8-172">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="d7fb8-173">Configure la sección **Credentials** (Credenciales) con las credenciales de la cuenta de Azure Spatial Anchors creada como parte de los [requisitos previos](mr-learning-asa-01.md#prerequisites) de esta serie de tutoriales:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-173">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="d7fb8-174">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-174">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="d7fb8-175">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-175">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="d7fb8-176">En el campo **Spatial Anchors Account Domain** (Dominio de la cuenta de Spatial Anchors), pegue el valor de **Account Domain** (Dominio de cuenta) de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-176">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Unity con Spatial Anchor Manager (Administrador de anclaje espacial) configurado](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="d7fb8-178">Prueba de los comportamientos básicos de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d7fb8-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="d7fb8-179">Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad de Azure Spatial Anchors, debe compilar el proyecto e implementar la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="d7fb8-180">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="d7fb8-181">Cuando la aplicación se ejecute en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="d7fb8-182">Mueva el cubo a una ubicación diferente.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="d7fb8-183">Inicie una sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-183">Start Azure Session</span></span>
1. <span data-ttu-id="d7fb8-184">Cree un anclaje de Azure (se crea un anclaje en la ubicación del cubo).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="d7fb8-185">Detenga la sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-185">Stop Azure Session</span></span>
1. <span data-ttu-id="d7fb8-186">Quite el anclaje local (permite que el usuario mueva el cubo).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="d7fb8-187">Mueva el cubo a otro lugar.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="d7fb8-188">Inicie una sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-188">Start Azure Session</span></span>
1. <span data-ttu-id="d7fb8-189">Busque el anclaje de Azure (posiciona el cubo en la ubicación del paso 3).</span><span class="sxs-lookup"><span data-stu-id="d7fb8-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="d7fb8-190">Elimine el anclaje de Azure.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="d7fb8-191">Detenga la sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-191">Stop Azure session</span></span>

![Unity con el objeto Instructions (Instrucciones) seleccionado](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="d7fb8-193">Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debe asegurarse de que el dispositivo esté conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="d7fb8-194">Anclaje de una experiencia</span><span class="sxs-lookup"><span data-stu-id="d7fb8-194">Anchoring an experience</span></span>

<span data-ttu-id="d7fb8-195">En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d7fb8-196">Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="d7fb8-197">En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="d7fb8-198">En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, configure los componentes **Transform** de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="d7fb8-199">Cambie **Scale X** (Escala X) a 1.1.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="d7fb8-200">Cambie **Scale Z** (Escala Z) a 1.1.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-200">Change **Scale Z** to 1.1</span></span>

![Unity con el objeto ParentAnchor seleccionado, colocado y escalado](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="d7fb8-202">En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** > **Rover** y haga clic y arrastre el objeto prefabricado **RoverExplorer_Complete** a la ventana Hierarchy (Jerarquía) para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity con el objeto prefabricado RoverExplorer_Complete recién agregado seleccionado](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="d7fb8-204">Con el objeto RoverModule_Complete recién agregado todavía seleccionado en la ventana Hierarchy (Jerarquía), arrástralo sobre el objeto **ParentAnchor** para convertirlo en un elemento secundario del objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="d7fb8-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity con el objeto RoverExplorer_Complete establecido como elemento secundario de ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="d7fb8-206">Si vuelve a compilar el proyecto e implementar la aplicación en el dispositivo, ahora podrá cambiar la posición de toda la experiencia del explorador de róver moviendo el cubo cuyo tamaño se ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="d7fb8-207">Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el control de límites alrededor de la experiencia, el uso de gizmos de posición y rotación, etc.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d7fb8-208">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="d7fb8-208">Congratulations</span></span>

<span data-ttu-id="d7fb8-209">En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d7fb8-210">El tutorial le ha proporcionado varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="d7fb8-211">Además de crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="d7fb8-212">En el siguiente tutorial, aprenderá a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="d7fb8-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d7fb8-213">Tutorial siguiente: 3. Guardado, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d7fb8-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
