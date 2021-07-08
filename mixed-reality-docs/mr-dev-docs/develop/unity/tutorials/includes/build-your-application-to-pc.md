---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392657"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="17f78-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="17f78-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="17f78-102">1. Cambio de la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="17f78-102">1. Switching Build Platform</span></span>

<span data-ttu-id="17f78-103">En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="17f78-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="17f78-104">En la ventana Build Settings (Configuración de compilación), seleccione la plataforma **PC, Mac & Linux Standalone** (PC, Mac y Linux independiente) y haga clic en el botón **Switch Platform** (Cambiar plataforma) para cambiar la plataforma de compilación:</span><span class="sxs-lookup"><span data-stu-id="17f78-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![Cambio de la plataforma de compilación](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="17f78-106">Cuando Unity haya terminado de cambiar la plataforma, haga clic en el icono con la x para cerrar la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="17f78-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="17f78-107">2. Configuración del proyecto</span><span class="sxs-lookup"><span data-stu-id="17f78-107">2. Set the project settings</span></span>

<span data-ttu-id="17f78-108">En el menú de Unity, seleccione **Edit** > **Project Configuración** > **XR Plug-in Management** (Editar > Configuración del proyecto > Administración de complementos de XR), asegúrese de estar en la pestaña Windows Standalone (Windows independiente) y active las casillas **OpenXR** y **Windows Mixed Reality feature set** (Conjunto de características de Windows Mixed Reality).</span><span class="sxs-lookup"><span data-stu-id="17f78-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![Habilitación de OpenXR y Windows Mixed Reality feature set](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="17f78-110">En la ventana Project Settings (Configuración del proyecto), seleccione **OpenXR** y asegúrese de estar en la pestaña Windows Standalone (Windows independiente) y cambie **Depth submission mode** (Modo de envío de profundidad) de None (Ninguno) a **Depth 16 Bit** (Profundidad de 16 bits).</span><span class="sxs-lookup"><span data-stu-id="17f78-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="17f78-111">En la pestaña Interaction profiles (Perfiles de interacción), haga clic en el símbolo + para agregar **Eye Gaze Interaction Profile** (Perfil de interacción de mirada) y **Microsoft Hand Interaction Profile** (Perfil de interacción con la mano de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="17f78-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![Adición de Eye Gaze Interaction Profile y Microsoft Hand Interaction Profile](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="17f78-113">En **Open XR feature groups** > **All features** (Grupos de características de OpenXR > Todas las características), marque la casilla **Holographic App Remoting** (Comunicación remota de aplicación holográfica).</span><span class="sxs-lookup"><span data-stu-id="17f78-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![Habilitación de Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="17f78-115">A continuación, active la casilla **Windows Mixed Reality** y, en el grupo Windows Mixed Reality, marque la casilla **Holographic App Remoting** (Comunicación remota de aplicación holográfica).</span><span class="sxs-lookup"><span data-stu-id="17f78-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![Habilitación de Holographic App Remoting en Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="17f78-117">3. Compilación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="17f78-117">3. Build the Unity Project</span></span>

<span data-ttu-id="17f78-118">En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="17f78-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="17f78-119">En la ventana Build Settings (Configuración de compilación), haga clic en el botón \***Add Open Scenes** _ (Agregar escenas abiertas) para agregar la escena actual a las escenas.</span><span class="sxs-lookup"><span data-stu-id="17f78-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="17f78-120">En la lista Build (Compilación), haga clic en el botón _ \*Build\*\*:</span><span class="sxs-lookup"><span data-stu-id="17f78-120">In the Build list, then click the _ *Build*\* button:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la escena agregada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="17f78-122">Elija una ubicación adecuada para almacenar la compilación, por ejemplo, Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="17f78-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="17f78-123">Cree una nueva carpeta y asígnele un nombre adecuado, por ejemplo, ComunicaciónRemotaHolográficaPC.</span><span class="sxs-lookup"><span data-stu-id="17f78-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="17f78-124">A continuación, haga clic en el botón ***Select Folder*** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="17f78-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="17f78-126">Espere a que Unity finalice el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="17f78-126">Wait for Unity to finish the build process.</span></span>

![Proceso de compilación de Unity en curso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="17f78-128">Haga doble clic en el archivo ejecutable para abrir la aplicación para PC de comunicación remota holográfica en el equipo.</span><span class="sxs-lookup"><span data-stu-id="17f78-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="17f78-129">Debido a algunos problemas conocidos de la aplicación para PC de comunicación remota holográfica compilada como UWP, estamos compilando la aplicación para PC como Windows Standalone (Windows independiente) para OpenXR.</span><span class="sxs-lookup"><span data-stu-id="17f78-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="17f78-130">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="17f78-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="17f78-131">1. Configuración del reproductor</span><span class="sxs-lookup"><span data-stu-id="17f78-131">1. Set the player settings</span></span>

<span data-ttu-id="17f78-132">En la sección **XR Settings** (Configuración de XR), seleccione la casilla **WSA Holographic Remoting Supported** (Admitir la comunicación remota holográfica de WSA) y habilite la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="17f78-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Ventana XR Settings (Configuración de XR) de Unity con WSA Holographic Remoting Supported (Admitir la comunicación remota holográfica de WSA) habilitado](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="17f78-134">2. Compilación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="17f78-134">2. Build the Unity Project</span></span>

<span data-ttu-id="17f78-135">En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="17f78-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="17f78-136">En la ventana Build Settings (Configuración de compilación), haga clic en el botón \***Add Open Scenes** _ (Agregar escenas abiertas) para agregar la escena actual a las escenas.</span><span class="sxs-lookup"><span data-stu-id="17f78-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="17f78-137">En la lista Build (Compilación), haga clic en el *_botón Build_* (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows):</span><span class="sxs-lookup"><span data-stu-id="17f78-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la escena agregada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="17f78-139">En la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows), elija una ubicación adecuada para almacenar la compilación, como por ejemplo, Mis Documentos\AprendizajeRealidadMixta.</span><span class="sxs-lookup"><span data-stu-id="17f78-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="17f78-140">Cree una nueva carpeta y asígnele un nombre adecuado, por ejemplo, ComunicaciónRemotaHolográficaPC.</span><span class="sxs-lookup"><span data-stu-id="17f78-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="17f78-141">A continuación, haga clic en el botón ***Select Folder*** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="17f78-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Select Folder (Seleccionar carpeta)](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="17f78-143">Espere a que Unity finalice el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="17f78-143">Wait for Unity to finish the build process.</span></span>

![Proceso de compilación de Unity en curso](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="17f78-145">3. Compilar e implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="17f78-145">3. Build and deploy the application</span></span>

<span data-ttu-id="17f78-146">Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación.</span><span class="sxs-lookup"><span data-stu-id="17f78-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="17f78-147">Navegue dentro de la carpeta y haga doble clic en el archivo .sln para abrirlo en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="17f78-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Explorador de Windows con la solución de Visual Studio recién creada seleccionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="17f78-149">Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que todos los componentes de los requisitos previos estén instalados, tal como se especifica en la documentación Instalación de herramientas.</span><span class="sxs-lookup"><span data-stu-id="17f78-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="17f78-150">Configure Visual Studio para PC. Para ello, selecciona la configuración Publicación, la arquitectura x64 y la opción Equipo local como destino:</span><span class="sxs-lookup"><span data-stu-id="17f78-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Visual Studio configurado para el equipo local](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="17f78-152">Haga clic en el botón que indica ***Equipo local***.</span><span class="sxs-lookup"><span data-stu-id="17f78-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="17f78-153">Comienza la compilación e implementación de la aplicación en el PC.</span><span class="sxs-lookup"><span data-stu-id="17f78-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="17f78-154">La aplicación se instalará de forma predeterminada en su PC.</span><span class="sxs-lookup"><span data-stu-id="17f78-154">The application will be installed in your PC by default.</span></span>
