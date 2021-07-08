---
title: Inicialización de su proyecto e implementación de su primera aplicación
description: En este curso se muestra cómo configurar un proyecto de Unity para Mixed Reality Toolkit (MRTK) y cómo implementarlo en HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175840"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="ace24-104">2. Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="ace24-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="ace24-105">En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con Mixed Reality Toolkit (MRTK) e importar MRTK.</span><span class="sxs-lookup"><span data-stu-id="ace24-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="ace24-106">También le guiará a través de la configuración, la compilación y la implementación de una escena básica de Unity desde Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ace24-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="ace24-107">Una vez que la haya implementado en HoloLens 2, debería ver una malla de asignación espacial que cubre las superficies que HoloLens percibe.</span><span class="sxs-lookup"><span data-stu-id="ace24-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="ace24-108">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ace24-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="ace24-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ace24-109">Objectives</span></span>

* <span data-ttu-id="ace24-110">Aprender a configurar Unity para el desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="ace24-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="ace24-111">Aprender a compilar e implementar la aplicación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="ace24-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="ace24-112">Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas en un dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ace24-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="ace24-113">Descripción general de los pasos</span><span class="sxs-lookup"><span data-stu-id="ace24-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="ace24-114">![Descripción general del paso 1](images/mr-learning-base/base-02-overview-step1.png) **1. Crear un proyecto de Unity**</span><span class="sxs-lookup"><span data-stu-id="ace24-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ace24-115">![Descripción general del paso 2](images/mr-learning-base/base-02-overview-step2.png) **2. Importar MRTK en el proyecto**</span><span class="sxs-lookup"><span data-stu-id="ace24-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ace24-116">![Descripción general del paso 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configurar una nueva escena con MRTK**</span><span class="sxs-lookup"><span data-stu-id="ace24-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="ace24-117">![Descripción general del paso 4](images/mr-learning-base/base-02-overview-step4.png) **4. Compilar el proyecto de Unity**</span><span class="sxs-lookup"><span data-stu-id="ace24-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ace24-118">![Descripción general del paso 5](images/mr-learning-base/base-02-overview-step5.png) **5. Compilar el proyecto para UWP**</span><span class="sxs-lookup"><span data-stu-id="ace24-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ace24-119">![Descripción general del paso 6](images/mr-learning-base/base-02-overview-step6.png) **6. Ejecutar el proyecto en el dispositivo**</span><span class="sxs-lookup"><span data-stu-id="ace24-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="ace24-120">Creación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ace24-120">Creating the Unity project</span></span>

<span data-ttu-id="ace24-121">Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):</span><span class="sxs-lookup"><span data-stu-id="ace24-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="ace24-122">En el desplegable, seleccione la **versión** de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="ace24-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="ace24-123">Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="ace24-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="ace24-124">En la ventana Create a new project (Crear un proyecto nuevo):</span><span class="sxs-lookup"><span data-stu-id="ace24-124">In the Create a new project window:</span></span>

* <span data-ttu-id="ace24-125">Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.</span><span class="sxs-lookup"><span data-stu-id="ace24-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="ace24-126">Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_</span><span class="sxs-lookup"><span data-stu-id="ace24-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="ace24-127">Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="ace24-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="ace24-128">Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ace24-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="ace24-129">Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="ace24-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="ace24-130">Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.</span><span class="sxs-lookup"><span data-stu-id="ace24-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="ace24-131">Espera a que Unity cree el proyecto:</span><span class="sxs-lookup"><span data-stu-id="ace24-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="ace24-132">Cambio de la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="ace24-132">Switching the build platform</span></span>

<span data-ttu-id="ace24-133">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="ace24-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="ace24-135">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y:</span><span class="sxs-lookup"><span data-stu-id="ace24-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="ace24-136">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="ace24-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="ace24-137">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="ace24-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="ace24-138">Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).</span><span class="sxs-lookup"><span data-stu-id="ace24-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="ace24-139">Establezca la **versión del SDK de destino** en **Instalada la más reciente**.</span><span class="sxs-lookup"><span data-stu-id="ace24-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="ace24-140">Establezca **Minimum Platform Version** (Versión mínima de la plataforma) en **10.0.1024.0**.</span><span class="sxs-lookup"><span data-stu-id="ace24-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="ace24-141">Establezca la **versión de Visual Studio**  en **Instalada la más reciente**.</span><span class="sxs-lookup"><span data-stu-id="ace24-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="ace24-142">Establezca **Compilar y ejecutar en** en **Dispositivo USB**.</span><span class="sxs-lookup"><span data-stu-id="ace24-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="ace24-143">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="ace24-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="ace24-144">Haga clic en el botón Switch Platform (Cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="ace24-144">Click the Switch Platform button</span></span>

![Configuración de compilación de Unity con la configuración establecida para Plataforma universal de Windows](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="ace24-146">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="ace24-146">Wait for Unity to finish switching the platform:</span></span>

![Cambio de plataforma de Unity en curso](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="ace24-148">Cuando Unity haya terminado de cambiar la plataforma, haga clic en el icono con la **x** para cerrar la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ace24-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="ace24-149">Importación de Mixed Reality Toolkit y configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ace24-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="ace24-150">Para importar Mixed Reality Toolkit en el proyecto de Unity, habrá que usar la herramienta [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md), que permite a los desarrolladores detectar, actualizar y agregar paquetes de características de Mixed Reality a proyectos de Unity.</span><span class="sxs-lookup"><span data-stu-id="ace24-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="ace24-151">Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación.</span><span class="sxs-lookup"><span data-stu-id="ace24-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="ace24-152">Descargue la versión más reciente de la herramienta Mixed Reality Feature Tool del [Centro de descarga de Microsoft](https://aka.ms/MRFeatureTool). Cuando finalice la descarga, descomprima el archivo y guárdelo en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="ace24-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="ace24-153">Para que pueda ejecutar la herramienta, instale el [entorno de ejecución de .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="ace24-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="ace24-154">Abra el archivo ejecutable, **MixedRealityFeatureTool**, que se encuentra en la carpeta descargada, para iniciar la herramienta Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ace24-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="ace24-155">Creación de la escena y configuración de MRTK</span><span class="sxs-lookup"><span data-stu-id="ace24-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="ace24-156">En el menú de Unity, seleccione **File** > **New Scene** (Nuevo > Nueva escena):</span><span class="sxs-lookup"><span data-stu-id="ace24-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Ruta del menú New Scene (Nueva escena) de Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="ace24-158">En la ventana **New Scene** (Nueva escena), seleccione **Basic (Built-in)** (Básico [integrado]) y haga clic en **Create** (Crear) para crear una escena:</span><span class="sxs-lookup"><span data-stu-id="ace24-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Ventana New Scene de Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="ace24-160">La captura de pantalla anterior corresponde a Unity 2020, si usa Unity 2019, al hacer clic en **Create** (Crear), se creará una nueva escena vacía.</span><span class="sxs-lookup"><span data-stu-id="ace24-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="ace24-161">En el menú de Unity, seleccione **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** (Realidad mixta > Kit de herramientas > Agregar a escena y configurar...) para agregar MRTK a la escena actual:</span><span class="sxs-lookup"><span data-stu-id="ace24-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Ruta del menú Add to Scene and Configure… (Agregar a escena y configurar…) de Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="ace24-163">Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, compruebe que el perfil de configuración **MixedRealityToolkit** se haya definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="ace24-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit de Unity con DefaultMixedRealityTookitConfigurationProfile seleccionado](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="ace24-165">En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):</span><span class="sxs-lookup"><span data-stu-id="ace24-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Ruta del menú Save As… (Guardar como…) de Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="ace24-167">Guarde la escena en el proyecto en **Asset** > **Scenes** (Recurso > Escenas).</span><span class="sxs-lookup"><span data-stu-id="ace24-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Ventana de solicitud Save Scene (Guardar escena) de Unity](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="ace24-169">Adición de la interacción de la mano a un objeto</span><span class="sxs-lookup"><span data-stu-id="ace24-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="ace24-170">En el menú de Unity, seleccione **GameObject** > **3D Object** > **Cube** (GameObject > Objeto 3D > Cubo) para agregar un objeto de cubo a la escena.</span><span class="sxs-lookup"><span data-stu-id="ace24-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![Adición de un objeto Cube a la escena](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="ace24-172">Haga clic en el objeto **Cube** (Cubo) en la ventana Hierarchy (Jerarquía) y, en la ventana Inspector, configure su componente **Transform** (Transformación) como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="ace24-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="ace24-173">**Posición**: X = 0, Y = 0.1, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="ace24-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="ace24-174">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="ace24-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="ace24-175">**Escala**: X = 0.1, Y = 0.1, Z = 0.1</span><span class="sxs-lookup"><span data-stu-id="ace24-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="ace24-176">1 unidad de Unity es 1 metro.</span><span class="sxs-lookup"><span data-stu-id="ace24-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="ace24-177">Hemos actualizado el tamaño del cubo a 10×10×10 cm, situado a 50 cm de la posición del casco (0,0,0),</span><span class="sxs-lookup"><span data-stu-id="ace24-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="ace24-178">10 cm por debajo del nivel de los ojos para una interacción cómoda.</span><span class="sxs-lookup"><span data-stu-id="ace24-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="ace24-179">Si usa la escala predeterminada (1,1,1), el cubo será demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="ace24-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="ace24-180">Si usa la posición predeterminada (0,0,0), el cubo se colocará en la misma posición que el casco, y no podrá verlo hasta que no retroceda.</span><span class="sxs-lookup"><span data-stu-id="ace24-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![Ajuste de la información de transformación](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="ace24-182">Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **Cube** (Cubo) y, a continuación, volver a acercarse ligeramente.</span><span class="sxs-lookup"><span data-stu-id="ace24-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="ace24-183">O bien, puede usar la tecla F para acercar y centrar el objeto.</span><span class="sxs-lookup"><span data-stu-id="ace24-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="ace24-184">Para interactuar y agarrar un objeto con seguimiento de manos, el objeto debe tener:</span><span class="sxs-lookup"><span data-stu-id="ace24-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="ace24-185">Componente de colisionador, como **Box Collider** (Colisionador de cuadro) (el cubo de Unity ya tiene un colisionador de cuadro de manera predeterminada)</span><span class="sxs-lookup"><span data-stu-id="ace24-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="ace24-186">Componente **Object Manipulator (Script)** (Manipulador de objetos [script])</span><span class="sxs-lookup"><span data-stu-id="ace24-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="ace24-187">Componente **NearInteractionGrabbable(Script)**</span><span class="sxs-lookup"><span data-stu-id="ace24-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="ace24-188">El script **ObjectManipulator** de MRTK hace que un objeto se pueda mover, escalar y girar con una mano o las dos.</span><span class="sxs-lookup"><span data-stu-id="ace24-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="ace24-189">Este script es compatible con el modelo de entrada de manipulación directa, porque permite al usuario tocar los hologramas directamente con las manos.</span><span class="sxs-lookup"><span data-stu-id="ace24-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="ace24-190">Con el objeto **Cube** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione el script **Object Manipulator** (Manipulador de objetos) para agregar el script correspondiente al objeto Cube.</span><span class="sxs-lookup"><span data-stu-id="ace24-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Adición de Object Manipulator (Manipulador de objetos) al objeto Cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="ace24-192">Repita el mismo procedimiento para agregar un **script Near Interaction Grabbable** (Interacción próxima de agarre) al objeto Cube</span><span class="sxs-lookup"><span data-stu-id="ace24-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Adición de Near Interaction Grabbable (Interacción próxima de agarre) al objeto Cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="ace24-194">Cuando se agrega un manipulador de objetos (script), en este caso, se agrega automáticamente el administrador de restricciones (script) porque el manipulador de objetos (script) depende de él.</span><span class="sxs-lookup"><span data-stu-id="ace24-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="ace24-195">Prueba de la aplicación en el editor de Unity con la simulación de entrada de MRTK</span><span class="sxs-lookup"><span data-stu-id="ace24-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="ace24-196">Con la simulación de entrada de MRTK, puede probar varios tipos de interacción en el editor de Unity sin necesidad de compilar ni implementar en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ace24-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="ace24-197">Esto le permite iterar rápidamente las ideas en el proceso de diseño y desarrollo.</span><span class="sxs-lookup"><span data-stu-id="ace24-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="ace24-198">Use combinaciones de teclado y mouse para controlar las entradas simuladas.</span><span class="sxs-lookup"><span data-stu-id="ace24-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="ace24-199">Haga clic en el botón de reproducción e ingrese al modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="ace24-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="ace24-200">Mantenga presionada la tecla **Mayús izquierda** o la **barra espaciadora** para abrir el controlador (manos simuladas), el mouse moverá el controlador, que también se puede alejar o acercar de la cámara mediante la rueda del mouse.</span><span class="sxs-lookup"><span data-stu-id="ace24-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="ace24-201">Una vez que el puntero esté en el objeto Cube (Cubo), mantenga presionado el **botón izquierdo del mouse** para agarrar el objeto Cube.</span><span class="sxs-lookup"><span data-stu-id="ace24-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="ace24-202">Presiona las teclas **W, A, S, D, Q, E** para mover la cámara.</span><span class="sxs-lookup"><span data-stu-id="ace24-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="ace24-203">Mantenga presionado el **botón derecho del mouse** y muévalo para mirar alrededor.</span><span class="sxs-lookup"><span data-stu-id="ace24-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="ace24-204">Para abrir las manos simuladas, presione la **barra espaciadora (mano derecha)** o la **tecla Mayús izquierda (mano izquierda)** .</span><span class="sxs-lookup"><span data-stu-id="ace24-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="ace24-205">Para mantener las manos simuladas en la vista, presione las teclas **T** o **Y**.</span><span class="sxs-lookup"><span data-stu-id="ace24-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="ace24-206">Para girar las manos simuladas, mantenga presionada la tecla **CTRL** y mueva el mouse.</span><span class="sxs-lookup"><span data-stu-id="ace24-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![Modo Juego](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="ace24-208">Compilación de la aplicación a HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ace24-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="ace24-209">1. Compilar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ace24-209">1. Build the Unity project</span></span>

<span data-ttu-id="ace24-210">En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ace24-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="ace24-211">En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):</span><span class="sxs-lookup"><span data-stu-id="ace24-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="ace24-213">En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="ace24-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="ace24-215">Espera a que Unity finalice el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="ace24-215">Wait for Unity to finish the build process:</span></span>

![Proceso de compilación de Unity en curso](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="ace24-217">2. Compilar e implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="ace24-217">2. Build and deploy the application</span></span>

<span data-ttu-id="ace24-218">Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación.</span><span class="sxs-lookup"><span data-stu-id="ace24-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="ace24-219">Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="ace24-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Explorador de Windows con la solución de Visual Studio recién creada seleccionada](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ace24-221">Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="ace24-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="ace24-222">Configure Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="ace24-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurado para implementar en HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="ace24-224">Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.</span><span class="sxs-lookup"><span data-stu-id="ace24-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="ace24-225">En el caso de HoloLens, normalmente se compilará para la arquitectura ARM.</span><span class="sxs-lookup"><span data-stu-id="ace24-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="ace24-226">Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ace24-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="ace24-227">La solución recomendada es compilar para ARM64.</span><span class="sxs-lookup"><span data-stu-id="ace24-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="ace24-228">Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).</span><span class="sxs-lookup"><span data-stu-id="ace24-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="ace24-229">Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="ace24-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="ace24-230">Para ello, en el Explorador de soluciones, haga clic con el botón derecho en NombreDelProyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.</span><span class="sxs-lookup"><span data-stu-id="ace24-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="ace24-231">Conecte su HoloLens al equipo y, a continuación, seleccione **Depurar** > **Iniciar sin depurar** para compilar e realizar la implementación en el dispositivo:</span><span class="sxs-lookup"><span data-stu-id="ace24-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Ruta del menú Iniciar sin depuración en Visual Studio](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="ace24-233">Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="ace24-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="ace24-234">Ambos pasos pueden completarse siguiendo [estas instrucciones](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ace24-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="ace24-235">También puede realizar la implementación en el [emulador de HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o crear un [paquete de aplicación](/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.</span><span class="sxs-lookup"><span data-stu-id="ace24-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="ace24-236">Al usar Iniciar sin depurar, la aplicación se inicia automáticamente en el dispositivo sin el depurador de Visual Studio adjunto.</span><span class="sxs-lookup"><span data-stu-id="ace24-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="ace24-237">Seleccione **Compilar > Implementar solución** para realizar una implementación en el dispositivo sin que se inicie automáticamente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ace24-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="ace24-238">Es posible que vea el generador de perfiles de diagnóstico en la aplicación, que puede activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="ace24-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="ace24-239">Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="ace24-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="ace24-240">Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="ace24-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="ace24-241">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="ace24-241">Congratulations</span></span>

<span data-ttu-id="ace24-242">Ya ha implementado su primera aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ace24-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="ace24-243">Una vez que se abra la aplicación, el usuario debería ver un objeto Cube delante suyo e interactuar con él moviéndolo y, además, a medida que avance, aparecerá una malla de asignación espacial que cubre las superficies que percibe HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ace24-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="ace24-244">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ace24-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="ace24-245">Estas características son solo algunas partes fundamentales incluidas en MRTK.</span><span class="sxs-lookup"><span data-stu-id="ace24-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="ace24-246">En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.</span><span class="sxs-lookup"><span data-stu-id="ace24-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ace24-247">Tutorial siguiente: 3. Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="ace24-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
