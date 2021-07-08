---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175833"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="ed417-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="ed417-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ed417-102">Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en **Start** (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ed417-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="ed417-103">El primer paso es apuntar Mixed Reality Feature Tool a **Project path** (Ruta de acceso del proyecto) mediante el botón de **puntos suspensivos**. Haga clic en el botón de puntos suspensivos junto a la ruta de acceso del proyecto y examine la carpeta del proyecto en el explorador, por ejemplo, _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="ed417-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="ed417-104">Cuando haya ubicado la carpeta del proyecto, haga clic en el botón Open (Abrir) para volver a Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ed417-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="ed417-105">A continuación, haga clic en **Discover Features** (Detectar características).</span><span class="sxs-lookup"><span data-stu-id="ed417-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="ed417-106">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="ed417-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="ed417-107">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="ed417-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="ed417-108">Mixed Reality Feature Tool realiza la validación para asegurarse de que se ha dirigido a una carpeta de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ed417-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="ed417-109">La carpeta debe contener las carpetas Assets, Packages y Project Settings.</span><span class="sxs-lookup"><span data-stu-id="ed417-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="ed417-110">Las características se agrupan por categoría para facilitar la búsqueda, haga clic en una lista desplegable **Mixed Reality Toolkit** para buscar paquetes relacionados con Mixed Reality Toolkit, y haga clic en la lista desplegable **Platform Support** (Soporte técnico de la plataforma) para buscar paquetes relacionados con varias plataformas de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="ed417-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="ed417-111">Compruebe **Mixed Reality Toolkit Foundation** y haga clic en la lista desplegable situada a un lado para seleccionar **MRTK 2.7.2**, también compruebe **Mixed Reality OpenXR Plugin 1.0.0** y haga clic en la lista desplegable situada a un lado para seleccionar la versión más reciente disponible y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.</span><span class="sxs-lookup"><span data-stu-id="ed417-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="ed417-112">A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).</span><span class="sxs-lookup"><span data-stu-id="ed417-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="ed417-113">Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="ed417-114">Configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ed417-114">Configuring the Unity project</span></span>

<span data-ttu-id="ed417-115">Una vez que Unity haya terminado de importar el paquete de la sección anterior, aparece un mensaje de advertencia para reiniciar el editor de Unity para habilitar los back-end para el nuevo sistema de complementos, haga clic en **Yes** (Sí).</span><span class="sxs-lookup"><span data-stu-id="ed417-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="ed417-116">Una vez que Unity se reinicie, debería aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK).</span><span class="sxs-lookup"><span data-stu-id="ed417-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ed417-117">Si no aparece, puede abrirlo de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK):</span><span class="sxs-lookup"><span data-stu-id="ed417-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Apertura de la ventana MRTK Project Configurator](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="ed417-119">Haga clic **Unity OpenXR Plugin** para habilitar la administración de complementos de XR y agregue al proyecto los paquetes necesarios.</span><span class="sxs-lookup"><span data-stu-id="ed417-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="ed417-120">Adición de Unity OpenXR Plugin</span><span class="sxs-lookup"><span data-stu-id="ed417-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="ed417-121">Con esto se importarán los paquetes de Unity necesarios para la administración de complementos de XR. Una vez hecho esto, haga clic en **Show XR Plug-In Management Settings** (Mostrar configuración de administración de complementos de XR) en MRTK Project Configurator (Configurador del proyecto MRTK).</span><span class="sxs-lookup"><span data-stu-id="ed417-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="ed417-122">Show XR Plug-In Management Settings</span><span class="sxs-lookup"><span data-stu-id="ed417-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="ed417-123">Se abrirá la ventana **Project Settings** (Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="ed417-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="ed417-124">En la ventana Project Settings (Configuración del proyecto), en **XR Plug-in Management** (Administración de complementos de XR), asegúrese de que se encuentra en la configuración de la Plataforma universal de Windows (pestaña con el logotipo de Windows).</span><span class="sxs-lookup"><span data-stu-id="ed417-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="ed417-125">Asegúrese también de que **Initialize XR on Startup** (Inicializar XR al iniciar) esté marcada, y luego haga clic en las casillas **OpenXR** y **Microsoft HoloLens feature set** (Conjunto de características de Microsoft HoloLens) para habilitarlos.</span><span class="sxs-lookup"><span data-stu-id="ed417-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Habilitación de OpenXR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="ed417-127">Una vez que marque la casilla OpenXR, la ventana de MRTK Project Configurator (Configurador del proyecto MRTK) mostrará el mensaje actualizado con el botón **Apply Settings** (Aplicar configuración).</span><span class="sxs-lookup"><span data-stu-id="ed417-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="ed417-128">Haga clic en el botón **Apply Settings** (Aplicar configuración).</span><span class="sxs-lookup"><span data-stu-id="ed417-128">Click **Apply Settings** button.</span></span> 

![Ventana 1 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="ed417-130">Al hacer clic en Apply Settings (Aplicar configuración), es posible que vea este mensaje de error en la consola.</span><span class="sxs-lookup"><span data-stu-id="ed417-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="ed417-131">Puede continuar si este es el único error o si no hay ningún error.</span><span class="sxs-lookup"><span data-stu-id="ed417-131">You can proceed if this is the only error or there is no error.</span></span>

![Mensaje de error de comunicación remota de OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="ed417-133">Para validar la configuración de OpenXR, haga clic en **OpenXR** en **XR Plug-in Management** (Administración de complementos de XR) y compruebe estos elementos:</span><span class="sxs-lookup"><span data-stu-id="ed417-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="ed417-134">Depth Submission Mode: **Depth 16 Bit** (Modo de envío de profundidad: profundidad de 16 bits)</span><span class="sxs-lookup"><span data-stu-id="ed417-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="ed417-135">Interaction Profiles: **Microsoft Hand Interaction Profile** (Perfiles de interacción: Perfil de interacción con la mano de Microsoft)</span><span class="sxs-lookup"><span data-stu-id="ed417-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![Ventana 2 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="ed417-137">Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudarle a mejorar el rendimiento de los gráficos en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="ed417-138">Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación Performance (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ed417-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="ed417-139">En la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK), haga clic en **Next** (Siguiente) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="ed417-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="ed417-140">(Si la cerró, puede abrirla de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** [Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK]).</span><span class="sxs-lookup"><span data-stu-id="ed417-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![Ventana 3 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Ventana 4 de configuración del proyecto](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="ed417-143">Una vez que haga clic en Apply (Aplicar), Unity intentará reiniciarse para que el sistema de entrada entre en vigor, haga clic en **Apply** para reiniciar el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="ed417-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="ed417-144">Configuración de valores adicionales del proyecto</span><span class="sxs-lookup"><span data-stu-id="ed417-144">Configure additional project settings</span></span>

<span data-ttu-id="ed417-145">En el menú de Unity, seleccione **Edit** > **Project Settings** (Editar > Configuración del proyecto) para abrir la ventana Project Settings (Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="ed417-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="ed417-146">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:</span><span class="sxs-lookup"><span data-stu-id="ed417-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configuración de publicación de Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="ed417-149">"Package name" es el identificador único para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ed417-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="ed417-150">Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ed417-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="ed417-151">"Product Name" es el nombre que se muestra en el menú Inicio de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ed417-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="ed417-152">Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.</span><span class="sxs-lookup"><span data-stu-id="ed417-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="ed417-153">Complemento XR para Unity 2019/2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="ed417-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="ed417-154">Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en **Start** (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ed417-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="ed417-155">El primer paso es apuntar Mixed Reality Feature Tool a **Project path** (Ruta de acceso del proyecto) mediante el botón de **puntos suspensivos**. Haga clic en el botón de puntos suspensivos junto a la ruta de acceso del proyecto y examine la carpeta del proyecto en el explorador, por ejemplo, _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="ed417-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="ed417-156">Cuando haya ubicado la carpeta del proyecto, haga clic en el botón Open (Abrir) para volver a Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ed417-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="ed417-157">A continuación, haga clic en **Discover Features** (Detectar características).</span><span class="sxs-lookup"><span data-stu-id="ed417-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="ed417-158">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="ed417-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="ed417-159">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="ed417-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="ed417-160">Mixed Reality Feature Tool realiza la validación para asegurarse de que se ha dirigido a una carpeta de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ed417-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="ed417-161">La carpeta debe contener las carpetas Assets, Packages y Project Settings.</span><span class="sxs-lookup"><span data-stu-id="ed417-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="ed417-162">Para facilitar la búsqueda de elementos, las características se agrupan por categoría. Haga clic en la lista desplegable **Mixed Reality Toolkit** para buscar los paquetes relacionados con Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ed417-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="ed417-163">Active la casilla **Mixed Reality Toolkit Foundation**, y haga clic en la lista desplegable a un lado para seleccionar **MRTK 2.7.0** y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.</span><span class="sxs-lookup"><span data-stu-id="ed417-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="ed417-164">A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).</span><span class="sxs-lookup"><span data-stu-id="ed417-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="ed417-165">Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="ed417-166">Configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ed417-166">Configuring the Unity project</span></span>

<span data-ttu-id="ed417-167">Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="ed417-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ed417-168">Si no aparece, puede abrirlo de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK):</span><span class="sxs-lookup"><span data-stu-id="ed417-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Apertura de la herramienta del configurador de MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="ed417-170">Haga clic **Built-in Unity Plugin(non-OpenXR)** (Complemento de Unity integrado [distinto de OpenXR]) para habilitar la administración de complementos de XR y agregue al proyecto los paquetes necesarios.</span><span class="sxs-lookup"><span data-stu-id="ed417-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="ed417-171">Herramienta del configurador de MRTK</span><span class="sxs-lookup"><span data-stu-id="ed417-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="ed417-172">La captura de pantalla anterior es de Unity 2020, si usa Unity 2019, seleccione **XR SDK/XR Management** (SDK de XR/Administración de XR).</span><span class="sxs-lookup"><span data-stu-id="ed417-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="ed417-173">Con esto se importarán los paquetes de Unity necesarios para la administración de complementos de XR. Una vez hecho esto, haga clic en **Show Settings** (Mostrar configuración) en MRTK Project Configurator (Configurador del proyecto MRTK).</span><span class="sxs-lookup"><span data-stu-id="ed417-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![Ventana de configuración del reproductor](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="ed417-175">Con esto se abre la ventana **Project Settings** (Configuración del proyecto). En la ventana Project Settings (Configuración del proyecto) en **XR Plug-in Management** (Administración de complementos de XR), asegúrese de estar en la configuración de la Plataforma universal de Windows, y asegúrese también de que **Initialize XR on Startup** (Inicializar XR en el inicio) está activada y marque la casilla **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="ed417-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![Ventana de configuración del reproductor Enable Mixed Reality-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="ed417-177">Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="ed417-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="ed417-178">Si no es así, use el menú de Unity para abrirla.</span><span class="sxs-lookup"><span data-stu-id="ed417-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="ed417-179">En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), haga clic en **Next** (Siguiente) y, luego, use la lista desplegable Audio spatializer (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="ed417-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK Project Configurator: xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="ed417-181">La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:</span><span class="sxs-lookup"><span data-stu-id="ed417-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="ed417-182">Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw.</span><span class="sxs-lookup"><span data-stu-id="ed417-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="ed417-183">Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ed417-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="ed417-184">Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="ed417-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="ed417-185">Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.</span><span class="sxs-lookup"><span data-stu-id="ed417-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="ed417-186">La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="ed417-187">Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="ed417-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="ed417-188">Para obtener más información sobre este tema, puede consultar los <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="ed417-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="ed417-189">Haga clic en **Next** (Siguiente) y, a continuación, en **Done** (Listo) en la ventana MRTK Project Configurator (Configurador del proyecto de MRTK) para finalizar la configuración del proyecto de Unity para XRSDK.</span><span class="sxs-lookup"><span data-stu-id="ed417-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="ed417-190">Configuración de valores adicionales del proyecto</span><span class="sxs-lookup"><span data-stu-id="ed417-190">Configure additional project settings</span></span>

<span data-ttu-id="ed417-191">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="ed417-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="ed417-192">En la ventana Project Settings (Configuración del proyecto), seleccione **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings** (Administración de complementos de XR > Windows Mixed Reality > Configuración del entorno de ejecución) y, a continuación, use el menú desplegable **Depth Buffer Format** (Formato de profundidad del búfer) para seleccionar **16-bit depth** (Profundidad de 16 bits):</span><span class="sxs-lookup"><span data-stu-id="ed417-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Habilitar la profundidad 16 en Unity](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="ed417-194">Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="ed417-195">Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación Performance (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ed417-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="ed417-196">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:</span><span class="sxs-lookup"><span data-stu-id="ed417-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configuración de publicación de Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="ed417-199">"Package name" es el identificador único para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ed417-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="ed417-200">Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ed417-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="ed417-201">"Product Name" es el nombre que se muestra en el menú Inicio de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ed417-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="ed417-202">Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.</span><span class="sxs-lookup"><span data-stu-id="ed417-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ed417-203">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="ed417-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="ed417-204">Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en **Start** (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ed417-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="ed417-205">El primer paso es apuntar Mixed Reality Feature Tool a **Project path** (Ruta de acceso del proyecto) mediante el botón de **puntos suspensivos**. Haga clic en el botón de puntos suspensivos junto a la ruta de acceso del proyecto y examine la carpeta del proyecto en el explorador, por ejemplo, _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="ed417-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="ed417-206">Cuando haya ubicado la carpeta del proyecto, haga clic en el botón Open (Abrir) para volver a Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ed417-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="ed417-207">A continuación, haga clic en **Discover Features** (Detectar características).</span><span class="sxs-lookup"><span data-stu-id="ed417-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="ed417-208">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="ed417-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="ed417-209">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="ed417-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="ed417-210">Mixed Reality Feature Tool realiza la validación para asegurarse de que se ha dirigido a una carpeta de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ed417-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="ed417-211">La carpeta debe contener las carpetas Assets, Packages y Project Settings.</span><span class="sxs-lookup"><span data-stu-id="ed417-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="ed417-212">Para facilitar la búsqueda de elementos, las características se agrupan por categoría. Haga clic en la lista desplegable **Mixed Reality Toolkit** para buscar los paquetes relacionados con Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ed417-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="ed417-213">Active **Mixed Reality Toolkit Foundation**, y haga clic en la lista desplegable a un lado para seleccionar **MRTK 2.7.0** y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.</span><span class="sxs-lookup"><span data-stu-id="ed417-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="ed417-214">A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).</span><span class="sxs-lookup"><span data-stu-id="ed417-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="ed417-215">Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="ed417-216">Configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ed417-216">Configuring the Unity project</span></span>

<span data-ttu-id="ed417-217">Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="ed417-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ed417-218">Si no aparece, puede abrirlo de forma manual; para ello, vaya a **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar proyecto para MRTK):</span><span class="sxs-lookup"><span data-stu-id="ed417-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Ruta del menú Configure Unity Project (Configurar proyecto de Unity) de Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="ed417-220">Haga clic en **Legacy XR** (XR heredado) para habilitar Legacy XR y para agregar los paquetes necesarios al proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="ed417-222">Haga clic en el botón siguiente para habilitar la configuración de canalización de XR para Legacy XR (XR heredado).</span><span class="sxs-lookup"><span data-stu-id="ed417-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Ventana de configuración de MRTK de Unity](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="ed417-224">En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), asegúrese de que todas las opciones estén marcadas y, además, use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="ed417-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Ventana de configuración de MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="ed417-226">La aplicación de la configuración predeterminada de MRTK es opcional, pero se recomienda encarecidamente, ya que le ayudará a configurar algunas opciones de Unity recomendadas:</span><span class="sxs-lookup"><span data-stu-id="ed417-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="ed417-227">Set Single Pass Instanced rendering path (Establecer la ruta de representación de instancia de paso único): Mejora el rendimiento de los gráficos al ejecutar la canalización de representación para ambos ojos en la misma llamada a Draw.</span><span class="sxs-lookup"><span data-stu-id="ed417-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="ed417-228">Para obtener más información sobre este tema, puede consultar la sección [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Representación con instancias de un solo paso) de la documentación [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ed417-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="ed417-229">Set default Spatial Awareness layer (Establecer la capa de reconocimiento espacial predeterminada): Crea una capa de Unity denominada Spatial Awareness (Reconocimiento espacial) y configura MRTK para que use esta capa para la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="ed417-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="ed417-230">Para obtener más información sobre las capas de Unity, puede consultar la documentación <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> (Personalización del área de trabajo) de Unity.</span><span class="sxs-lookup"><span data-stu-id="ed417-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="ed417-231">La definición de la propiedad Audio spatializer (Espacializador de audio) es opcional, pero puede mejorar la experiencia de audio en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="ed417-232">Si la establece en MS HRTF Spatializer (Espacializador de audio MS HRTF), este complemento de espacializador se usará cuando la propiedad AudioSource.spatial de Unity esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="ed417-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="ed417-233">Para obtener más información sobre este tema, puede consultar los <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriales de audio espacial</a>.</span><span class="sxs-lookup"><span data-stu-id="ed417-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="ed417-234">Haga clic en **Next** (Siguiente) y, a continuación, en el botón **Done** (Listo) en la ventana MRTK Project Configurator (Configurador del proyecto de MRTK) para finalizar la configuración del proyecto de Unity para Legacy XR (XR heredado).</span><span class="sxs-lookup"><span data-stu-id="ed417-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="ed417-235">Configuración de valores adicionales del proyecto</span><span class="sxs-lookup"><span data-stu-id="ed417-235">Configure additional project settings</span></span>

<span data-ttu-id="ed417-236">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="ed417-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="ed417-237">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y, a continuación, use la lista desplegable **Depth Format** (Formato de profundidad) para seleccionar **16-bit depth** (Profundidad de 16 bits):</span><span class="sxs-lookup"><span data-stu-id="ed417-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Habilitar la profundidad 16 en Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="ed417-239">Reducir el formato de profundidad a 16 bits es opcional, pero puede ayudar a mejorar el rendimiento de los gráficos en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="ed417-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="ed417-240">Para obtener más información sobre este tema, puede consultar la sección <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> (Uso compartido del búfer de profundidad [HoloLens]) de la documentación Performance (Rendimiento) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ed417-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="ed417-241">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:</span><span class="sxs-lookup"><span data-stu-id="ed417-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Configuración de publicación de Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="ed417-244">"Package name" es el identificador único para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ed417-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="ed417-245">Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ed417-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="ed417-246">"Product Name" es el nombre que se muestra en el menú Inicio de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ed417-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="ed417-247">Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.</span><span class="sxs-lookup"><span data-stu-id="ed417-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
