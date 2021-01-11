---
title: Tutoriales de MRTK - 2. Inicialización de su proyecto e implementación de su primera aplicación
description: En este curso se muestra cómo configurar un proyecto de Unity para Mixed Reality Toolkit (MRTK) y cómo implementarlo en HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859534"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="088d6-105">2. Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="088d6-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="088d6-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="088d6-106">Overview</span></span>

<span data-ttu-id="088d6-107">En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e importar MRTK.</span><span class="sxs-lookup"><span data-stu-id="088d6-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="088d6-108">También le guiará a través de la configuración, la compilación y la implementación de una escena básica de Unity desde Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="088d6-108">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="088d6-109">Una vez que la haya implementado en HoloLens 2, debería ver una malla de asignación espacial que cubre las superficies que HoloLens percibe.</span><span class="sxs-lookup"><span data-stu-id="088d6-109">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="088d6-110">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="088d6-110">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="088d6-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="088d6-111">Objectives</span></span>

* <span data-ttu-id="088d6-112">Aprender a configurar Unity para el desarrollo de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="088d6-112">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="088d6-113">Aprender a compilar e implementar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="088d6-113">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="088d6-114">Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas en un dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="088d6-114">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="088d6-115">Creación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="088d6-115">Creating the Unity project</span></span>

1. <span data-ttu-id="088d6-116">Inicie **Unity Hub**, seleccione la pestaña **Proyectos** y haga clic en la **flecha hacia abajo** situada junto al botón **Nuevo**:</span><span class="sxs-lookup"><span data-stu-id="088d6-116">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![Unity Hub con la flecha hacia abajo del botón "Nuevo" resaltada.](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="088d6-118">En el menú desplegable, seleccione la versión de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="088d6-118">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Selección de la versión de Unity.](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="088d6-120">Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="088d6-120">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="088d6-121">En la ventana **Crear un proyecto nuevo**, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="088d6-121">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="088d6-122">Asegúrese de que la opción **Plantillas** está establecida como **3D**.</span><span class="sxs-lookup"><span data-stu-id="088d6-122">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="088d6-123">En el cuadro **Nombre del proyecto**, escriba un nombre adecuado para el proyecto (por ejemplo, "Tutoriales MRTK").</span><span class="sxs-lookup"><span data-stu-id="088d6-123">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="088d6-124">Haga clic en el botón de tres puntos situado junto a **Ubicación** y, a continuación, vaya a la carpeta en la que quiera guardar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="088d6-124">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="088d6-125">Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="088d6-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="088d6-126">Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.</span><span class="sxs-lookup"><span data-stu-id="088d6-126">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="088d6-127">Haga clic en el botón **Crear**.</span><span class="sxs-lookup"><span data-stu-id="088d6-127">Click the **Create** button.</span></span> <span data-ttu-id="088d6-128">Esta opción crea e inicia el nuevo proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="088d6-128">This creates and launches your new Unity project.</span></span>

![Unity Hub con la ventana para crear un nuevo proyecto rellena.](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="088d6-130">La barra de estado le mantiene al tanto del progreso realizado.</span><span class="sxs-lookup"><span data-stu-id="088d6-130">The status bar keeps you updated on your progress.</span></span>

![La barra de progreso de Unity le mantiene al tanto del estado de "creación del proyecto".](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="088d6-132">Cambio de la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="088d6-132">Switching the build platform</span></span>

1. <span data-ttu-id="088d6-133">En la barra del menú, seleccione **Archivo** > **Configuración de compilación...** .</span><span class="sxs-lookup"><span data-stu-id="088d6-133">On the menu bar, select **File** > **Build Settings...**</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="088d6-135">En la ventana de **Configuración de compilación**, seleccione **Plataforma universal de Windows** y haga clic en el botón **Cambiar plataforma**:</span><span class="sxs-lookup"><span data-stu-id="088d6-135">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="088d6-137">Espere a que Unity termine de cambiar la plataforma y, a continuación, cierre la ventana **Configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="088d6-137">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="088d6-138">Importación de los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="088d6-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="088d6-139">Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="088d6-139">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="088d6-140">Si no va a usar los elementos de la interfaz de usuario de MRTK en el proyecto, puede omitir este paso.</span><span class="sxs-lookup"><span data-stu-id="088d6-140">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="088d6-141">En la barra del menú, seleccione **Ventana**  > **TextMeshPro** > **Import TMP Essential Resources** (Importar recursos esenciales de TMP).</span><span class="sxs-lookup"><span data-stu-id="088d6-141">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Ruta de menú Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="088d6-143">En la ventana **Import Unity Package** (Importar paquete de Unity), haga clic en el botón **Todos** para asegurarse de que todos los recursos están seleccionados y, a continuación, haga clic en el botón **Importar** para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="088d6-143">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Ventana Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="088d6-145">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="088d6-145">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="088d6-146">Descarga el paquete personalizado de Unity:</span><span class="sxs-lookup"><span data-stu-id="088d6-146">Download the Unity custom package:</span></span>

    [<span data-ttu-id="088d6-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="088d6-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="088d6-148">En la barra del menú, seleccione **Recursos** > **Paquete de importación** > **Paquete personalizado...** .</span><span class="sxs-lookup"><span data-stu-id="088d6-148">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="088d6-149">En el cuadro de diálogo **Importar paquete...** , vaya a la ubicación del paquete que acaba de descargar, selecciónelo y, a continuación, haga clic en el botón **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="088d6-149">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="088d6-150">En la ventana **Import Unity Package** (Importar paquete de Unity), haga clic en el botón **Todos** para asegurarse de que todos los recursos están seleccionados y, a continuación, haga clic en el botón **Importar** para importar los recursos.</span><span class="sxs-lookup"><span data-stu-id="088d6-150">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="088d6-151">Selección de la configuración de MRTK y del proyecto</span><span class="sxs-lookup"><span data-stu-id="088d6-151">Selecting MRTK and project settings</span></span>

<span data-ttu-id="088d6-152">Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="088d6-152">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="088d6-153">Si no aparece, puede abrirlo de forma manual seleccionando la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity):</span><span class="sxs-lookup"><span data-stu-id="088d6-153">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Ruta del menú Configure Unity Project (Configurar proyecto de Unity) de Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="088d6-155">En la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK), expanda la sección **Modificar configuraciones** si fuera necesario, y asegúrese de que todas las demás opciones están seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="088d6-155">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![Ventana de Configurador del proyecto de MRTK con la opción Modificar configuraciones a la vista.](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="088d6-157">Para aplicar la configuración, haga clic en el botón **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="088d6-157">To apply the settings, click the **Apply** button.</span></span>

![Botón "Aplicar" en MRTK.](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="088d6-159">Está usando la versión de XR heredada integrada de Unity en lugar del nuevo sistema de complementos de XR, ya que el nuevo sistema no es totalmente compatible con las [versiones recomendadas de Unity y MRTK](mr-learning-base-01.md#prerequisites) para esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="088d6-159">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="088d6-160">Si ve alguna advertencia acerca de que la versión de XR integrada está en desuso, puede omitirla.</span><span class="sxs-lookup"><span data-stu-id="088d6-160">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="088d6-161">La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:</span><span class="sxs-lookup"><span data-stu-id="088d6-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="088d6-162">Enable legacy XR (Habilitar la versión de XR heredada): Habilita VR para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="088d6-162">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="088d6-163">Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw.</span><span class="sxs-lookup"><span data-stu-id="088d6-163">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="088d6-164">Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="088d6-164">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="088d6-165">Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="088d6-165">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="088d6-166">Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.</span><span class="sxs-lookup"><span data-stu-id="088d6-166">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="088d6-167">En la barra del menú, seleccione **Editar** > **Configuración del proyecto...** .</span><span class="sxs-lookup"><span data-stu-id="088d6-167">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="088d6-168">En la ventana **Configuración del proyecto**, seleccione **Reproductor**, haga clic en la lista desplegable **Configuración de XR** y, a continuación, active la casilla situada junto a **Virtual Reality Supported** (Compatibilidad con realidad virtual):</span><span class="sxs-lookup"><span data-stu-id="088d6-168">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![Se muestra la Configuración de XR de Unity con la opción de compatibilidad con realidad virtual.](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="088d6-170">Esta opción importa el SDK de Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="088d6-170">This imports the Windows Mixed Reality SDK:</span></span>

![Se muestra la Configuración de XR de Unity con los SDK de realidad virtual.](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="088d6-172">Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="088d6-172">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="088d6-173">Si no aparece, puede abrirla mediante la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Kit de herramientas de Mixed Reality > Utilidades > Configurar proyecto de Unity).</span><span class="sxs-lookup"><span data-stu-id="088d6-173">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="088d6-174">En la ventana **MRTK Project Configurator** (Configurador del proyecto de MRTK), haga clic en la lista desplegable **Audio spatializer** (Espacializador de audio) y, a continuación, seleccione **MS HRTF Spatializer** (Espacializador MS HRTF).</span><span class="sxs-lookup"><span data-stu-id="088d6-174">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![Configuración del proyecto con las opciones del Espacializador de audio a la vista.](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="088d6-176">Haga clic en el botón **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="088d6-176">Click the **Apply** button.</span></span> <span data-ttu-id="088d6-177">Esta opción cierra la ventana de **MRTK Project Configurator** (Configurador del proyecto MRTK).</span><span class="sxs-lookup"><span data-stu-id="088d6-177">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="088d6-178">La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="088d6-178">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="088d6-179">Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="088d6-179">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="088d6-180">Para obtener más información sobre este tema, puede consultar los tutoriales de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="088d6-180">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="088d6-181">En la ventana **Configuración del proyecto**, haga clic en la lista desplegable **Depth Format** (Formato de profundidad) y, a continuación, seleccione **Profundidad de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="088d6-181">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Configuración de XR de Unity con profundidad de 16 bits seleccionada.":::

    > [!TIP]
    > <span data-ttu-id="088d6-183">Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudarle a mejorar el rendimiento de los gráficos en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="088d6-183">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="088d6-184">Para obtener más información sobre este tema, puede consultar la sección [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) (Uso compartido del búfer de profundidad [HoloLens]) de la documentación [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="088d6-184">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="088d6-185">Haga clic en la lista desplegable **Publishing Settings** (Configuración de publicación) y, a continuación, en el cuadro **Nombre del paquete**, escriba un nombre adecuado (por ejemplo, "MRTK-Tutorials-Getting-Started").</span><span class="sxs-lookup"><span data-stu-id="088d6-185">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Configuración de publicación de Unity con el nombre del paquete configurado.":::

    <span data-ttu-id="088d6-187">**Nombre del paquete y nombre del producto**</span><span class="sxs-lookup"><span data-stu-id="088d6-187">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="088d6-188">"Package name" es el identificador único para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="088d6-188">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="088d6-189">Debe crear este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="088d6-189">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="088d6-190">"Product Name" es el nombre que se muestra en el menú Inicio de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="088d6-190">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="088d6-191">Para que la búsqueda de la aplicación sea más fácil durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo en la parte superior.</span><span class="sxs-lookup"><span data-stu-id="088d6-191">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Configuración del proyecto de Unity con el nombre de producto configurado.":::

9. <span data-ttu-id="088d6-193">Cierre la ventana **Configuración del proyecto**.</span><span class="sxs-lookup"><span data-stu-id="088d6-193">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="088d6-194">Creación y configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="088d6-194">Creating and configuring the scene</span></span>

1. <span data-ttu-id="088d6-195">En la barra del menú, haga clic en **Archivo** > **Importar**.</span><span class="sxs-lookup"><span data-stu-id="088d6-195">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="088d6-196">Para agregar MRTK a la escena, vaya a la barra del menú y seleccione **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Kit de herramientas de Mixed Reality > Agregar a la escena y configurar...).</span><span class="sxs-lookup"><span data-stu-id="088d6-196">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Ruta del menú &quot;Agregar a la escena y configurar…&quot; de Unity.":::

3. <span data-ttu-id="088d6-198">En la ventana **Jerarquía**, asegúrese de que el objeto **MixedRealityToolkit** esté seleccionado.</span><span class="sxs-lookup"><span data-stu-id="088d6-198">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Asegúrese de que MixedRealityTookit está seleccionado.":::

4. <span data-ttu-id="088d6-200">En la sección **MixedRealityToolkit** de la ventana **Inspector**, compruebe que el perfil de configuración está establecido en **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="088d6-200">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Componente MixedRealityToolkit de Unity con DefaultMixedRealityTookitConfigurationProfile seleccionado.":::

    > [!IMPORTANT]
    > <span data-ttu-id="088d6-202">Normalmente, se usa el perfil DefaultHoloLens2ConfigurationProfile para desarrollar para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="088d6-202">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="088d6-203">Sin embargo, en este tutorial usará DefaultMixedRealityToolkitConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="088d6-203">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="088d6-204">En el siguiente tutorial, [Configuración de los perfiles de MRTK](mr-learning-base-03.md), cambiará al perfil DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="088d6-204">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="088d6-205">En la barra del menú, haga clic en **Archivo** > **Guardar como...** .</span><span class="sxs-lookup"><span data-stu-id="088d6-205">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="088d6-206">En el cuadro de diálogo **Guardar escena**, vaya a la carpeta **Escenas** del proyecto.</span><span class="sxs-lookup"><span data-stu-id="088d6-206">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="088d6-207">En el cuadro **Nombre de archivo**, escriba un nombre adecuado para la escena (por ejemplo, "\_GettingStarted\_") y, a continuación, haga clic en el botón **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="088d6-207">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Ventana de solicitud para Guardar la escena de Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="088d6-209">Creación e implementación en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="088d6-209">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="088d6-210">Antes de compilar contenido en el dispositivo, confirme lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="088d6-210">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="088d6-211">El dispositivo está en modo de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="088d6-211">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="088d6-212">El dispositivo está emparejado con el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="088d6-212">Your device is paired with your development computer.</span></span> <span data-ttu-id="088d6-213">Si no es así, verá el cuadro de diálogo siguiente en Visual Studio durante el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="088d6-213">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![Entrada de PIN para el emparejamiento de dispositivos](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="088d6-215">Para obtener más información sobre estos dos pasos, consulte [Uso de Visual Studio para implementar y depurar](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="088d6-215">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="088d6-216">En la barra del menú, seleccione **Archivo** > **Configuración de compilación...** .</span><span class="sxs-lookup"><span data-stu-id="088d6-216">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="088d6-217">En la ventana **Configuración de compilación**, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación).</span><span class="sxs-lookup"><span data-stu-id="088d6-217">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![Agregar la escena actual a la lista "Escenas en la compilación".](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="088d6-219">Haga clic en el botón **Build** (Compilación).</span><span class="sxs-lookup"><span data-stu-id="088d6-219">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Haga clic en el botón Build (Compilación).":::

4. <span data-ttu-id="088d6-221">En el cuadro de diálogo **Build Universal Windows Platform** (Compilar Plataforma universal de Windows), elija una ubicación adecuada para guardar la compilación (por ejemplo, puede crear una carpeta denominada "Compilaciones" en la carpeta "Tutoriales de MRTK").</span><span class="sxs-lookup"><span data-stu-id="088d6-221">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="088d6-222">Cree una nueva carpeta y asígnele un nombre adecuado (por ejemplo, "GettingStarted"), seleccione la carpeta y, a continuación, haga clic en el botón **Seleccionar carpeta** para iniciar el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="088d6-222">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Ventana de compilación de Unity con la carpeta de compilación a la vista.":::

    <span data-ttu-id="088d6-224">Aparecerá una barra de estado que le indicará el progreso de la compilación.</span><span class="sxs-lookup"><span data-stu-id="088d6-224">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Proceso de compilación de Unity en curso.":::

    > [!TIP]
    > <span data-ttu-id="088d6-226">También puede realizar la implementación en el [emulador de HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o crear un [paquete de aplicación](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.</span><span class="sxs-lookup"><span data-stu-id="088d6-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="088d6-227">Cuando se haya completado el proceso de compilación, use el Explorador de archivos para obtener la ubicación donde almacenó la compilación y, a continuación, haga doble clic en el archivo de solución para abrirlo en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="088d6-227">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Explorador de Windows con la solución de Visual Studio recién creada seleccionada.":::

    > [!NOTE]
    > <span data-ttu-id="088d6-229">Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="088d6-229">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="088d6-230">Para configurar Visual Studio para HoloLens, seleccione la configuración **Master** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino.</span><span class="sxs-lookup"><span data-stu-id="088d6-230">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="088d6-231">Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.</span><span class="sxs-lookup"><span data-stu-id="088d6-231">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configurado para implementar en HoloLens 2.":::

    > [!NOTE]
    > <span data-ttu-id="088d6-233">En el caso de HoloLens, normalmente se compilará para la arquitectura ARM.</span><span class="sxs-lookup"><span data-stu-id="088d6-233">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="088d6-234">Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="088d6-234">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="088d6-235">La solución recomendada es compilar para ARM64.</span><span class="sxs-lookup"><span data-stu-id="088d6-235">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="088d6-236">Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).</span><span class="sxs-lookup"><span data-stu-id="088d6-236">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="088d6-237">Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="088d6-237">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="088d6-238">Para ello, en el Explorador de soluciones, haga clic con el botón derecho en el nombre del proyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.</span><span class="sxs-lookup"><span data-stu-id="088d6-238">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="088d6-239">Conecte el dispositivo HoloLens al equipo y, a continuación, realice una de las acciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="088d6-239">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="088d6-240">Para compilar la aplicación, impleméntela en HoloLens e iníciela automáticamente sin adjuntar el depurador de Visual Studio; en la barra del menú, seleccione **Depurar** > **Iniciar sin depurar**.</span><span class="sxs-lookup"><span data-stu-id="088d6-240">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Ruta del menú Iniciar sin depurar de Visual Studio.":::

- <span data-ttu-id="088d6-242">Si quiere compilar e implementar la aplicación en HoloLens, pero no que se inicie automáticamente, en la barra del menú, seleccione **Compilar > Implementar la solución**.</span><span class="sxs-lookup"><span data-stu-id="088d6-242">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="088d6-243">Es posible que veas el generador de perfiles de diagnóstico en la aplicación, que puedes activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="088d6-243">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="088d6-244">Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="088d6-244">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="088d6-245">Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="088d6-245">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="088d6-246">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="088d6-246">Congratulations</span></span>

<span data-ttu-id="088d6-247">Ya ha implementado su primera aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="088d6-247">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="088d6-248">A medida que avance, debería ver una malla de asignación espacial que cubre todas las superficies que HoloLens ha percibido.</span><span class="sxs-lookup"><span data-stu-id="088d6-248">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="088d6-249">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="088d6-249">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="088d6-250">Estas características son solo algunas partes fundamentales incluidas en MRTK.</span><span class="sxs-lookup"><span data-stu-id="088d6-250">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="088d6-251">En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.</span><span class="sxs-lookup"><span data-stu-id="088d6-251">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="088d6-252">Tutorial siguiente: 3. Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="088d6-252">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
