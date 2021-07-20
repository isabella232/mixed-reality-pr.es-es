---
title: Introducción a Azure Spatial Anchors
description: Siga este curso para aprender a usar Azure Spatial Anchors dentro para anclar objetos en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656646"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="d444a-104">2. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d444a-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="d444a-105">En este tutorial, explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors, y para crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d444a-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="d444a-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d444a-106">Objectives</span></span>

* <span data-ttu-id="d444a-107">Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d444a-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="d444a-108">Aprender a crear anclajes espaciales y a capturarlos desde Azure</span><span class="sxs-lookup"><span data-stu-id="d444a-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="d444a-109">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="d444a-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="d444a-110">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="d444a-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="d444a-111">Primero, debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="d444a-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="d444a-112">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="d444a-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="d444a-113">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="d444a-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="d444a-114">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="d444a-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="d444a-115">Importación de Mixed Reality Toolkit y configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="d444a-115">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="d444a-116">[Crear y configurar la escena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) y asignarle un nombre adecuado; por ejemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="d444a-116">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="d444a-117">A continuación, siga las instrucciones de [Cambio de la opción de visualización del reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para asegurarse de que el perfil de configuración de MRTK de la escena sea **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="d444a-117">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="d444a-118">Instalación de paquetes de Unity integrados e importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="d444a-118">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a><span data-ttu-id="d444a-119">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="d444a-119">Preparing the scene</span></span>

<span data-ttu-id="d444a-120">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="d444a-120">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="d444a-121">En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** y, a continuación, haga clic y arrastre los siguientes objetos prefabricados a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="d444a-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="d444a-122">Objeto prefabricado **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="d444a-122">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="d444a-123">Objeto prefabricado **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="d444a-123">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="d444a-124">Objeto prefabricado **Instructions**</span><span class="sxs-lookup"><span data-stu-id="d444a-124">**Instructions** prefabs</span></span>
* <span data-ttu-id="d444a-125">Objeto prefabricado **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="d444a-125">**ParentAnchor** prefabs</span></span>

![Unity con los objetos prefabricados recién agregados seleccionados](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="d444a-127">Si le molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puede ocultarlos. Para hacerlo, desactive los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>, como se muestra en la imagen anterior.</span><span class="sxs-lookup"><span data-stu-id="d444a-127">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

<span data-ttu-id="d444a-128">Seleccione el objeto **MixedRealityToolkit** en la ventana Hierarchy (Jerarquía) y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar los componentes siguientes:</span><span class="sxs-lookup"><span data-stu-id="d444a-128">Select **MixedRealityToolkit** object in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="d444a-129">AR Anchor Manager (Script) (Administrador de delimitadores de AR [script])</span><span class="sxs-lookup"><span data-stu-id="d444a-129">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="d444a-130">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="d444a-130">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="d444a-131">Objeto MixedRealityToolkit de Unity con los componentes AR Anchor Manager y DisableDiagnosticsSystem agregados</span><span class="sxs-lookup"><span data-stu-id="d444a-131">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> <span data-ttu-id="d444a-132">Hay un problema conocido con ASA v2.9.0 y v2.10.0-preview.1 que requiere que se sitúen en la escena dos objetos adicionales.</span><span class="sxs-lookup"><span data-stu-id="d444a-132">There is a known issue with ASA v2.9.0 and v2.10.0-preview.1 that requires two additional objects to be placed in the scene.</span></span> <span data-ttu-id="d444a-133">Use el botón **Add Component** (Agregar componente) de la ventana Inspector para agregar AR Camera Manager (Script) (Administrador de la cámara de AR [script]) y AR Session (Script) (Sesión de AR [script]) al objeto **MixedRealityToolkit.**</span><span class="sxs-lookup"><span data-stu-id="d444a-133">Please use the **Add Component** button in the inspector window to add an AR Camera Manager (Script) and an AR Session (Script) to the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="d444a-134">Asegúrese de deshabilitar la cámara que se crea automáticamente al agregar AR Camera Manager (Script) (Administrador de la cámara de AR [script]); para ello, desactive la casilla situada junto al objeto Camera en la ventana Inspector.</span><span class="sxs-lookup"><span data-stu-id="d444a-134">Be sure to disable the Camera that is created automatically while adding the AR Camera Manager (Script) by unchecking the checkbox next to the Camera object in the inspector window.</span></span> <span data-ttu-id="d444a-135">Este problema se solucionará en la versión completa de ASA v2.10.0.</span><span class="sxs-lookup"><span data-stu-id="d444a-135">This issue will be addressed in the full release of ASA v2.10.0.</span></span>
>

> [!NOTE]
> <span data-ttu-id="d444a-136">Cuando se agregue el componente AR Anchor Manager (Script) (Administrador de anclaje de AR [script]), se agregará automáticamente el componente AR Session Origin (Script) (Origen de la sesión de AR [script]) según lo requiere el componente AR Anchor Manager (Script).</span><span class="sxs-lookup"><span data-stu-id="d444a-136">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="d444a-137">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="d444a-137">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="d444a-138">En esta sección, agregará scripts a la escena para crear una serie de eventos de botón que muestren los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d444a-138">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="d444a-139">En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d444a-139">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d444a-140">Asigne el objeto **ParentAnchor** como cliente de escucha para el evento On Click () arrastrándolo desde la ventana Hierarchy (Jerarquía) hasta el campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d444a-140">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="d444a-141">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d444a-141">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón StartAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="d444a-143">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **StopAzureSession**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d444a-143">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d444a-144">Asigne el objeto **ParentAnchor** como cliente de escucha para el evento On Click () arrastrándolo desde la ventana Hierarchy (Jerarquía) hasta el campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d444a-144">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="d444a-145">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StopAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d444a-145">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón StopAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="d444a-147">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **CreateAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d444a-147">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d444a-148">Asigne el objeto **ParentAnchor** como cliente de escucha para el evento On Click () arrastrándolo desde la ventana Hierarchy (Jerarquía) hasta el campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d444a-148">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="d444a-149">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **CreateAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d444a-149">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="d444a-150">Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="d444a-150">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity con el evento OnClick del botón CreateAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="d444a-152">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **RemoveLocalAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d444a-152">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d444a-153">Asigne el objeto **ParentAnchor** como cliente de escucha para el evento On Click () arrastrándolo desde la ventana Hierarchy (Jerarquía) hasta el campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d444a-153">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="d444a-154">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **RemoveLocalAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d444a-154">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="d444a-155">Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="d444a-155">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity con el evento OnClick del botón RemoveLocalAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="d444a-157">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **FindAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d444a-157">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d444a-158">Asigne el objeto **ParentAnchor** como cliente de escucha para el evento On Click () arrastrándolo desde la ventana Hierarchy (Jerarquía) hasta el campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d444a-158">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="d444a-159">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **FindAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d444a-159">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón FindAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="d444a-161">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **DeleteAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d444a-161">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="d444a-162">Asigne el objeto **ParentAnchor** como cliente de escucha para el evento On Click () arrastrándolo desde la ventana Hierarchy (Jerarquía) hasta el campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="d444a-162">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="d444a-163">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **DeleteAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="d444a-163">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con el evento OnClick del botón DeleteAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="d444a-165">Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="d444a-165">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="d444a-166">En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, busque el componente **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="d444a-166">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="d444a-167">Configure la sección **Credentials** (Credenciales) con las credenciales de la cuenta de Azure Spatial Anchors creada como parte de los [requisitos previos](mr-learning-asa-01.md#prerequisites) de esta serie de tutoriales:</span><span class="sxs-lookup"><span data-stu-id="d444a-167">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="d444a-168">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d444a-168">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="d444a-169">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d444a-169">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="d444a-170">En el campo **Spatial Anchors Account Domain** (Dominio de la cuenta de Spatial Anchors), pegue el valor de **Account Domain** (Dominio de cuenta) de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d444a-170">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Unity con Spatial Anchor Manager (Administrador de anclaje espacial) configurado](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="d444a-172">Prueba de los comportamientos básicos de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d444a-172">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="d444a-173">Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad de Azure Spatial Anchors, debe compilar el proyecto e implementar la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d444a-173">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="d444a-174">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d444a-174">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="d444a-175">Cuando la aplicación se ejecute en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="d444a-175">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="d444a-176">Mueva el cubo a una ubicación diferente.</span><span class="sxs-lookup"><span data-stu-id="d444a-176">Move the cube to a different location</span></span>
2. <span data-ttu-id="d444a-177">Inicie una sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d444a-177">Start Azure Session</span></span>
3. <span data-ttu-id="d444a-178">Cree un anclaje de Azure (se crea un anclaje en la ubicación del cubo).</span><span class="sxs-lookup"><span data-stu-id="d444a-178">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
4. <span data-ttu-id="d444a-179">Detenga la sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d444a-179">Stop Azure Session</span></span>
5. <span data-ttu-id="d444a-180">Quite el anclaje local (permite que el usuario mueva el cubo).</span><span class="sxs-lookup"><span data-stu-id="d444a-180">Remove Local Anchor (allows the user to move the cube)</span></span>
6. <span data-ttu-id="d444a-181">Mueva el cubo a otro lugar.</span><span class="sxs-lookup"><span data-stu-id="d444a-181">Move the cube somewhere else</span></span>
7. <span data-ttu-id="d444a-182">Inicie una sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d444a-182">Start Azure Session</span></span>
8. <span data-ttu-id="d444a-183">Busque el anclaje de Azure (posiciona el cubo en la ubicación del paso 3).</span><span class="sxs-lookup"><span data-stu-id="d444a-183">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
9. <span data-ttu-id="d444a-184">Elimine el anclaje de Azure.</span><span class="sxs-lookup"><span data-stu-id="d444a-184">Delete Azure Anchor</span></span>
10. <span data-ttu-id="d444a-185">Detenga la sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="d444a-185">Stop Azure session</span></span>

![Unity con el objeto Instructions (Instrucciones) seleccionado](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="d444a-187">Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debe asegurarse de que el dispositivo esté conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="d444a-187">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="d444a-188">Anclaje de una experiencia</span><span class="sxs-lookup"><span data-stu-id="d444a-188">Anchoring an experience</span></span>

<span data-ttu-id="d444a-189">En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d444a-189">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d444a-190">Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto.</span><span class="sxs-lookup"><span data-stu-id="d444a-190">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="d444a-191">En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="d444a-191">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="d444a-192">En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, configure los componentes **Transform** de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="d444a-192">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="d444a-193">Cambie **Scale X** (Escala X) a 1.1.</span><span class="sxs-lookup"><span data-stu-id="d444a-193">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="d444a-194">Cambie **Scale Z** (Escala Z) a 1.1.</span><span class="sxs-lookup"><span data-stu-id="d444a-194">Change **Scale Z** to 1.1</span></span>

![Unity con el objeto ParentAnchor seleccionado, colocado y escalado](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="d444a-196">En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** > **Rover** y haga clic y arrastre el objeto prefabricado **RoverExplorer_Complete** a la ventana Hierarchy (Jerarquía) para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="d444a-196">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity con el objeto prefabricado RoverExplorer_Complete recién agregado seleccionado](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="d444a-198">Con el objeto RoverModule_Complete recién agregado todavía seleccionado en la ventana Hierarchy (Jerarquía), arrástralo sobre el objeto **ParentAnchor** para convertirlo en un elemento secundario del objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="d444a-198">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity con el objeto RoverExplorer_Complete establecido como elemento secundario de ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="d444a-200">Si vuelve a compilar el proyecto e implementar la aplicación en el dispositivo, ahora podrá cambiar la posición de toda la experiencia del explorador de róver moviendo el cubo cuyo tamaño se ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="d444a-200">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="d444a-201">Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el control de límites alrededor de la experiencia, el uso de gizmos de posición y rotación, etc.</span><span class="sxs-lookup"><span data-stu-id="d444a-201">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d444a-202">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="d444a-202">Congratulations</span></span>

<span data-ttu-id="d444a-203">En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d444a-203">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="d444a-204">El tutorial le ha proporcionado varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="d444a-204">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="d444a-205">Además de crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d444a-205">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="d444a-206">En el siguiente tutorial, aprenderá a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="d444a-206">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d444a-207">Tutorial siguiente: 3. Guardado, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d444a-207">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
