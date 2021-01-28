---
title: Inicialización de su proyecto e implementación de su primera aplicación
description: En este curso se muestra cómo configurar un proyecto de Unity para Mixed Reality Toolkit (MRTK) y cómo implementarlo en HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 4d82d0974a0a797e7f8d2de2d4943666f7d32a4f
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635534"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="72fdb-104">2. Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="72fdb-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="72fdb-105">En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e importar MRTK.</span><span class="sxs-lookup"><span data-stu-id="72fdb-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="72fdb-106">También le guiará a través de la configuración, la compilación y la implementación de una escena básica de Unity desde Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="72fdb-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="72fdb-107">Una vez que la haya implementado en HoloLens 2, debería ver una malla de asignación espacial que cubre las superficies que HoloLens percibe.</span><span class="sxs-lookup"><span data-stu-id="72fdb-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="72fdb-108">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="72fdb-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="72fdb-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="72fdb-109">Objectives</span></span>

* <span data-ttu-id="72fdb-110">Aprender a configurar Unity para el desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="72fdb-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="72fdb-111">Aprender a compilar e implementar la aplicación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="72fdb-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="72fdb-112">Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas en un dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="72fdb-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="72fdb-113">Creación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="72fdb-113">Creating the Unity project</span></span>

<span data-ttu-id="72fdb-114">Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):</span><span class="sxs-lookup"><span data-stu-id="72fdb-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub con el botón New (Nuevo) resaltado](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="72fdb-116">En el desplegable, seleccione la **versión** de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="72fdb-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub con lista desplegable del selector de la nueva versión](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="72fdb-118">Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="72fdb-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="72fdb-119">En la ventana Create a new project (Crear un proyecto nuevo):</span><span class="sxs-lookup"><span data-stu-id="72fdb-119">In the Create a new project window:</span></span>

* <span data-ttu-id="72fdb-120">Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.</span><span class="sxs-lookup"><span data-stu-id="72fdb-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="72fdb-121">Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_</span><span class="sxs-lookup"><span data-stu-id="72fdb-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="72fdb-122">Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="72fdb-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="72fdb-123">Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="72fdb-123">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub con la ventana para crear un nuevo proyecto rellena](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="72fdb-125">Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="72fdb-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="72fdb-126">Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.</span><span class="sxs-lookup"><span data-stu-id="72fdb-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="72fdb-127">Espera a que Unity cree el proyecto:</span><span class="sxs-lookup"><span data-stu-id="72fdb-127">Wait for Unity to create the project:</span></span>

![Creación de nuevo proyecto de Unity en curso](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="72fdb-129">Cambio de la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="72fdb-129">Switching the build platform</span></span>

<span data-ttu-id="72fdb-130">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="72fdb-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="72fdb-132">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):</span><span class="sxs-lookup"><span data-stu-id="72fdb-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="72fdb-134">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="72fdb-134">Wait for Unity to finish switching the platform:</span></span>

![Cambio de plataforma de Unity en curso](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="72fdb-136">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="72fdb-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Ventana Build (Compilación) de Unity con el icono de cerrar resaltado](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="72fdb-138">Importación de los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="72fdb-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="72fdb-139">En el menú de Unity, seleccione **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Ventana > TextMeshPro > Importar recursos esenciales de TMP) para abrir la ventana Import Unity Package (Importar paquete de Unity):</span><span class="sxs-lookup"><span data-stu-id="72fdb-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Ruta de menú Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="72fdb-141">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="72fdb-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Ventana Import TMP Essential Resources (Importar recursos esenciales de TMP) de Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="72fdb-143">Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="72fdb-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="72fdb-144">Puede omitir este paso si no va a usar los elementos de la interfaz de usuario de MRTK en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="72fdb-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="72fdb-145">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="72fdb-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="72fdb-146">Descarga el paquete personalizado de Unity:</span><span class="sxs-lookup"><span data-stu-id="72fdb-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="72fdb-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="72fdb-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

<span data-ttu-id="72fdb-148">En el menú de Unity, selecciona **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):</span><span class="sxs-lookup"><span data-stu-id="72fdb-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Ruta de menú Import Custom Package… (Importar paquete personalizado…) de Unity](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="72fdb-150">En la ventana Import package... (Importar paquete...), seleccione el paquete **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** que descargó y haga clic en el botón **Open** (Abrir):</span><span class="sxs-lookup"><span data-stu-id="72fdb-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** you downloaded and click the **Open** button:</span></span>

![Import Custom Package (Importar paquete personalizado) de Unity con la ventana de mensajes Open (Abrir)](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="72fdb-152">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="72fdb-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Ventana de importación de Unity MRTK Foundation](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="72fdb-154">Configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="72fdb-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="72fdb-155">1. Aplicación de la configuración del configurador del proyecto de MRTK</span><span class="sxs-lookup"><span data-stu-id="72fdb-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="72fdb-156">Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="72fdb-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="72fdb-157">Si no aparece, puede abrirlo de forma manual seleccionando la opción **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity):</span><span class="sxs-lookup"><span data-stu-id="72fdb-157">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Ruta del menú Configure Unity Project (Configurar proyecto de Unity) de Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="72fdb-159">En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), expanda la sección **Modify Configurations (Modificar configuraciones)** , asegúrese de que todas las demás opciones están seleccionadas y haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="72fdb-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="72fdb-161">La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:</span><span class="sxs-lookup"><span data-stu-id="72fdb-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="72fdb-162">Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw.</span><span class="sxs-lookup"><span data-stu-id="72fdb-162">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="72fdb-163">Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="72fdb-163">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="72fdb-164">Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="72fdb-164">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="72fdb-165">Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.</span><span class="sxs-lookup"><span data-stu-id="72fdb-165">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="72fdb-166">2. Configuración de valores adicionales del proyecto</span><span class="sxs-lookup"><span data-stu-id="72fdb-166">2. Configure additional project settings</span></span>

<span data-ttu-id="72fdb-167">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="72fdb-167">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Ruta del menú Project Settings… (Configuración del proyecto…) de Unity](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="72fdb-169">En la ventana Configuración del proyecto, seleccione **XR Plug-in Management** > **Instalar XR Plug-in Management** para instalar XR Plug-in Management:</span><span class="sxs-lookup"><span data-stu-id="72fdb-169">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Publishing Settings (Configuración de publicación) de Unity con Package name (Nombre del paquete) configurado](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="72fdb-171">después de que Unity haya terminado de instalar XR Plug-in Management.</span><span class="sxs-lookup"><span data-stu-id="72fdb-171">after Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="72fdb-172">Asegúrese de estar en la configuración de la Plataforma universal de Windows y active Initialize XR on Startup (Inicializar XR al inicio).</span><span class="sxs-lookup"><span data-stu-id="72fdb-172">Ensure that you are in Universal Windows Platform settings and Check the Initialize XR on Startup.</span></span>

![Configuración de XR Plug-in Management en Unity](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="72fdb-174">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR), haga clic en el icono **+** y seleccione Windows Mixed Reality para agregar el SDK de Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="72fdb-174">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![XR Settings (Configuración de XR) de Unity con la opción para agregar el SDK de Windows Mixed Reality seleccionada](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="72fdb-176">Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="72fdb-176">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="72fdb-177">Si no es así, use el menú de Unity para abrirla.</span><span class="sxs-lookup"><span data-stu-id="72fdb-177">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="72fdb-178">En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="72fdb-178">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![XR Settings (Configuración de XR) de Unity con la opción para agregar el SDK de Windows Mixed Reality seleccionada](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="72fdb-180">La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="72fdb-180">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="72fdb-181">Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="72fdb-181">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="72fdb-182">Para obtener más información sobre este tema, puede consultar los <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="72fdb-182">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="72fdb-183">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y, a continuación, use la lista desplegable **Depth Format** (Formato de profundidad) para seleccionar **16-bit depth** (Profundidad de 16 bits):</span><span class="sxs-lookup"><span data-stu-id="72fdb-183">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Habilitar la profundidad 16 en Unity](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="72fdb-185">Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="72fdb-185">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="72fdb-186">Para obtener más información sobre este tema, puede consultar la sección <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">Performance</a> (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="72fdb-186">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="72fdb-187">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:</span><span class="sxs-lookup"><span data-stu-id="72fdb-187">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Publishing Settings (Configuración de publicación) de Unity con Package name (Nombre del paquete) configurado](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="72fdb-189">"Package name" es el identificador único para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="72fdb-189">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="72fdb-190">Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="72fdb-190">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="72fdb-191">"Product Name" es el nombre que se muestra en el menú Inicio de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="72fdb-191">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="72fdb-192">Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.</span><span class="sxs-lookup"><span data-stu-id="72fdb-192">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="72fdb-193">Creación y configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="72fdb-193">Creating and configuring the scene</span></span>

<span data-ttu-id="72fdb-194">En el menú de Unity, seleccione **File** > **New Scene** (Archivo > Nueva escena) para crear una nueva escena:</span><span class="sxs-lookup"><span data-stu-id="72fdb-194">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Ruta del menú New Scene (Nueva escena) de Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="72fdb-196">En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a escena y configurar...) para agregar MRTK a la escena actual:</span><span class="sxs-lookup"><span data-stu-id="72fdb-196">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Ruta del menú Add to Scene and Configure… (Agregar a escena y configurar…) de Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="72fdb-198">Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, compruebe que el perfil de configuración **MixedRealityToolkit** se haya definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="72fdb-198">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit de Unity con DefaultMixedRealityTookitConfigurationProfile seleccionado](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="72fdb-200">En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):</span><span class="sxs-lookup"><span data-stu-id="72fdb-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Ruta del menú Save As… (Guardar como…) de Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="72fdb-202">En la ventana Save Scene (Guardar escena), desplázate hasta la carpeta **Scenes** (Escenas) del proyecto, asígnale un nombre adecuado (por ejemplo, _GettingStarted_), y haz clic en el botón **Save** (Guardar) para guardar la escena:</span><span class="sxs-lookup"><span data-stu-id="72fdb-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Ventana de solicitud Save Scene (Guardar escena) de Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="72fdb-204">Compilación de la aplicación a HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="72fdb-204">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="72fdb-205">1. Compilar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="72fdb-205">1. Build the Unity project</span></span>

<span data-ttu-id="72fdb-206">En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="72fdb-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="72fdb-207">En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):</span><span class="sxs-lookup"><span data-stu-id="72fdb-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="72fdb-209">En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="72fdb-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="72fdb-211">Espera a que Unity finalice el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="72fdb-211">Wait for Unity to finish the build process:</span></span>

![Proceso de compilación de Unity en curso](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="72fdb-213">2. Compilar e implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="72fdb-213">2. Build and deploy the application</span></span>

<span data-ttu-id="72fdb-214">Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación.</span><span class="sxs-lookup"><span data-stu-id="72fdb-214">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="72fdb-215">Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="72fdb-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Explorador de Windows con la solución de Visual Studio recién creada seleccionada](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="72fdb-217">Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="72fdb-217">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="72fdb-218">Configure Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="72fdb-218">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurado para implementar en HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="72fdb-220">Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.</span><span class="sxs-lookup"><span data-stu-id="72fdb-220">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="72fdb-221">En el caso de HoloLens, normalmente se compilará para la arquitectura ARM.</span><span class="sxs-lookup"><span data-stu-id="72fdb-221">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="72fdb-222">Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72fdb-222">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="72fdb-223">La solución recomendada es compilar para ARM64.</span><span class="sxs-lookup"><span data-stu-id="72fdb-223">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="72fdb-224">Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).</span><span class="sxs-lookup"><span data-stu-id="72fdb-224">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="72fdb-225">Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="72fdb-225">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="72fdb-226">Para ello, en el Explorador de soluciones, haga clic con el botón derecho en NombreDelProyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.</span><span class="sxs-lookup"><span data-stu-id="72fdb-226">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="72fdb-227">Conecte su HoloLens al equipo y, a continuación, seleccione **Depurar** > **Iniciar sin depurar** para compilar e realizar la implementación en el dispositivo:</span><span class="sxs-lookup"><span data-stu-id="72fdb-227">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Ruta del menú Iniciar sin depuración en Visual Studio](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="72fdb-229">Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="72fdb-229">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="72fdb-230">Ambos pasos pueden completarse siguiendo [estas instrucciones](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="72fdb-230">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="72fdb-231">También puede realizar la implementación en el [emulador de HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o crear un [paquete de aplicación](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.</span><span class="sxs-lookup"><span data-stu-id="72fdb-231">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="72fdb-232">Al usar Iniciar sin depurar, la aplicación se inicia automáticamente en el dispositivo sin el depurador de Visual Studio adjunto.</span><span class="sxs-lookup"><span data-stu-id="72fdb-232">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="72fdb-233">Seleccione **Compilar > Implementar solución** para realizar una implementación en el dispositivo sin que se inicie automáticamente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="72fdb-233">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="72fdb-234">Es posible que veas el generador de perfiles de diagnóstico en la aplicación, que puedes activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="72fdb-234">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="72fdb-235">Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="72fdb-235">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="72fdb-236">Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="72fdb-236">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="72fdb-237">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="72fdb-237">Congratulations</span></span>

<span data-ttu-id="72fdb-238">Ya ha implementado su primera aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="72fdb-238">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="72fdb-239">A medida que avance, debería ver una malla de asignación espacial que cubre todas las superficies que HoloLens ha percibido.</span><span class="sxs-lookup"><span data-stu-id="72fdb-239">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="72fdb-240">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="72fdb-240">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="72fdb-241">Estas características son solo algunas partes fundamentales incluidas en MRTK.</span><span class="sxs-lookup"><span data-stu-id="72fdb-241">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="72fdb-242">En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.</span><span class="sxs-lookup"><span data-stu-id="72fdb-242">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72fdb-243">Tutorial siguiente: 3. Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="72fdb-243">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)