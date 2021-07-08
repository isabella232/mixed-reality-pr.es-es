---
title: Azure Spatial Anchors para iOS y Android
description: Complete este curso para aprender a implementar un proyecto de Unity con Mixed Reality Toolkit (MRTK) y Azure Spatial Anchors en Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, android, ios, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403434"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="ce217-104">5. Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="ce217-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="ce217-105">En este tutorial, aprenderás a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="ce217-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="ce217-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ce217-106">Objectives</span></span>

* <span data-ttu-id="ce217-107">Aprender a compilar el proyecto en el dispositivo Android mediante AR Foundation y el complemento ARCore XR de Unity</span><span class="sxs-lookup"><span data-stu-id="ce217-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="ce217-108">Aprender a compilar el proyecto en su dispositivo iOS mediante AR Foundation y el complemento ARKit XR de Unity</span><span class="sxs-lookup"><span data-stu-id="ce217-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="ce217-109">Instalación de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="ce217-109">Installing inbuilt Unity packages</span></span>

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="ce217-110">Configuración de MRTK para la cámara de AR Foundation</span><span class="sxs-lookup"><span data-stu-id="ce217-110">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="ce217-111">En esta sección, obtendrá información sobre cómo configurar MRTK para realizar la implementación en un dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="ce217-111">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="ce217-112">En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="ce217-112">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="ce217-113">A continuación, en la ventana Inspector, seleccione la pestaña **Camera** (Cámara), clone el perfil de la cámara y asígnele un nombre adecuado, por ejemplo, **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="ce217-113">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![Unity con ARCameraProfile recién creado seleccionado](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="ce217-115">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones del artículo [Configuración de los perfiles de Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="ce217-115">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="ce217-116">Con la pestaña **Camera** (Cámara) aún seleccionada en la ventana Inspector, expanda **Camera Setting Providers** (Proveedores de configuración de la cámara) y haga clic en "-" para quitar **Windows Mixed Reality Camera Setting** (Configuración de la cámara de Windows Mixed Reality) o **XR SDK Windows Mixed Reality Camera Setting** (Configuración de la cámara de Windows Mixed Reality para el SDK de XR):</span><span class="sxs-lookup"><span data-stu-id="ce217-116">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and by clicking the "-" remove the **Windows Mixed Reality Camera Setting** or **XR SDK Windows Mixed Reality Camera Setting**:</span></span>

![<span data-ttu-id="ce217-117">ARCameraProfile de Unity con un nuevo proveedor de datos agregado</span><span class="sxs-lookup"><span data-stu-id="ce217-117">Unity ARCameraProfile with new data provider added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="ce217-118">y haga clic en el botón **+ Add Camera Setting Provider** (+ Agregar proveedor de configuración de la cámara) y, a continuación, expanda **New data provider** (Nuevo proveedor de datos):</span><span class="sxs-lookup"><span data-stu-id="ce217-118">and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider**:</span></span>

![Cámara de AR agregada para Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="ce217-120">Con la lista desplegable **Typo** (Tipo), cambie el tipo a **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="ce217-120">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![ARCameraProfile de Unity con la ruta de acceso a la selección del tipo de proveedor de datos](images/mr-learning-asa/asa-05-section2-step1-4.png)

<span data-ttu-id="ce217-122">Invoque el siguiente elemento de menú para actualizar las definiciones del scripting de MRTK UnityAR: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR > Update Scripting Defines** (Realidad mixta > Kit de herramientas > Utilidades > UnityAR > Actualizar definiciones del scripting).</span><span class="sxs-lookup"><span data-stu-id="ce217-122">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="ce217-123">Compilación de la aplicación en el dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="ce217-123">Building your application to your Android device</span></span>

<span data-ttu-id="ce217-124">En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="ce217-124">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="ce217-125">En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a Android.</span><span class="sxs-lookup"><span data-stu-id="ce217-125">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la plataforma Android seleccionada](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="ce217-127">Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="ce217-127">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="ce217-128">Cierre la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ce217-128">Close the Build Settings window.</span></span>

<span data-ttu-id="ce217-129">En el menú de Unity, seleccione **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar el proyecto para MRTK) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="ce217-129">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Configurador del proyecto MRTK de Unity 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="ce217-131">En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración), seleccione **Vulkan** y quítelo haciendo clic en el símbolo **"-"** .</span><span class="sxs-lookup"><span data-stu-id="ce217-131">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![Other Settings (Otra configuración) de Unity con Vulkan seleccionado](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

<span data-ttu-id="ce217-133">En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación).</span><span class="sxs-lookup"><span data-stu-id="ce217-133">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="ce217-134">A continuación, use un cable USB, conecte el dispositivo Android al equipo y selecciónelo en la lista desplegable **Run Device** (Ejecutar dispositivo):</span><span class="sxs-lookup"><span data-stu-id="ce217-134">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con escena agregada y Run Device (Ejecutar dispositivo) seleccionado](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="ce217-136">Si el dispositivo no aparece en la lista desplegable Run Device (Ejecutar dispositivo), puede que tenga que presionar el botón Refresh (Actualizar) situado junto a dicha lista.</span><span class="sxs-lookup"><span data-stu-id="ce217-136">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="ce217-137">En la ventana Configuración de compilación, haga clic en el botón **Build and Run** (Compilar y ejecutar) para abrir la ventana Build Android (Compilar Android).</span><span class="sxs-lookup"><span data-stu-id="ce217-137">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="ce217-138">Elija una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, asigne a apk un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y haga clic en el botón **Save** (Guardar) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="ce217-138">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Save (Guardar) para Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> <span data-ttu-id="ce217-140">Si se produce algún error en la ventana Console (Consola) de Unity relacionado con los módulos SDK, NDK o JDK de Android, tienes que abrir Unity Hub e instalar los módulos asociados de compatibilidad con la compilación de Android.</span><span class="sxs-lookup"><span data-stu-id="ce217-140">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="ce217-141">Una vez que se complete el proceso de compilación, las aplicaciones deberían cargarse automáticamente en el dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="ce217-141">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="ce217-142">Compilación de la aplicación en el dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="ce217-142">Building your application to your iOS device</span></span>

<span data-ttu-id="ce217-143">En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en su dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="ce217-143">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="ce217-144">En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a iOS.</span><span class="sxs-lookup"><span data-stu-id="ce217-144">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con iOS seleccionado](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="ce217-146">Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="ce217-146">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="ce217-147">Cierre la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ce217-147">Close the Build Settings window.</span></span>

<span data-ttu-id="ce217-148">En el menú de Unity, seleccione **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar el proyecto para MRTK) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="ce217-148">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity para iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

<span data-ttu-id="ce217-150">En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración) y desactive la casilla **Strip Engine Code** (Código del motor de franja).</span><span class="sxs-lookup"><span data-stu-id="ce217-150">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![Other Settings (Otra configuración) de Unity con Strip Engine Code (Código del motor de franja) deshabilitado](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="ce217-152">Cierre la ventana Player Settings (Configuración del reproductor) y vuelva a abrir la ventana **Build Settings** (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ce217-152">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="ce217-153">En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación):</span><span class="sxs-lookup"><span data-stu-id="ce217-153">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la escena agregada](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="ce217-155">En la ventana Configuración de compilación, haga clic en el botón **Build** (Compilar) para abrir la ventana Build iOS (Compilar iOS).</span><span class="sxs-lookup"><span data-stu-id="ce217-155">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="ce217-156">Elija una ubicación adecuada para almacenar el proyecto Xcode, por ejemplo, _D:\MixedRealityLearning\Builds_, cree una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y, luego, haga clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="ce217-156">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Save (Guardar) para iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="ce217-158">Una vez completado el proceso de compilación, siga las instrucciones del artículo [Exportación del proyecto de Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implementar el proyecto de Xcode en el dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="ce217-158">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ce217-159">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="ce217-159">Congratulations</span></span>

<span data-ttu-id="ce217-160">En este tutorial, ha aprendido a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="ce217-160">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
