---
ms.openlocfilehash: 7c86356a960929839f36cf326c5dd1a1005e64d2
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984341"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="eb539-101">Complemento XR para Unity 2019/2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="eb539-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="eb539-102">Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en Start (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="eb539-102">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![Ventana de MixedRealityFeatureTool para el complemento de XR para Windows](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="eb539-104">Para facilitar la búsqueda de elementos, las características se agrupan por categoría. Haga clic en la lista desplegable **Mixed Reality Toolkit** para buscar los paquetes relacionados con Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="eb539-104">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Ventana de MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="eb539-106">Active la opción **Mixed Reality Toolkit Foundation** y haga clic en la lista desplegable situada junto a ella para seleccionar la versión más reciente de MRTK y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.</span><span class="sxs-lookup"><span data-stu-id="eb539-106">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the latest MRTK version, then click on **Get features** button to download the selected packages.</span></span>

![Seleccionar Mixed Reality Toolkit Foundation](../images/mr-learning-base/base-02-section4-step1-4.png)


<span data-ttu-id="eb539-108">También debe establecer la ubicación del proyecto de Unity de destino para proporcionar el valor apropiado en **Project path** (Ruta de acceso del proyecto). Haga clic en los **tres puntos** que encontrará al lado del campo Project path (Ruta de acceso del proyecto) y vaya a la carpeta del proyecto en el explorador, por ejemplo _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="eb539-108">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="eb539-109">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="eb539-109">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="eb539-110">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="eb539-110">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="eb539-111">A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).</span><span class="sxs-lookup"><span data-stu-id="eb539-111">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Validar Mixed Reality Toolkit Foundation](../images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="eb539-113">Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.</span><span class="sxs-lookup"><span data-stu-id="eb539-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Aprobar Mixed Reality Toolkit Foundation](../images/mr-learning-base/base-02-section4-step1-6.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="eb539-115">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="eb539-115">Unity 2020 + OpenXR</span></span>](#tab/openxr)
<span data-ttu-id="eb539-116">En la parte inferior izquierda de la ventana, haga clic en el símbolo de engranaje para abrir el menú de configuración.</span><span class="sxs-lookup"><span data-stu-id="eb539-116">In the bottom left hand of the window, click on the gear symbol to open the settings menu.</span></span>

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="eb539-118">En **Configuración de características**, active la casilla **Include preview releases** (Incluir versiones preliminares) y, a continuación, haga clic en el botón **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="eb539-118">Under **Feature Settings**, check the **Include preview releases** box and then click the **OK** button.</span></span>

![Ventana de configuración de MixedRealityFeatureTool](../images/mrft-settings.png)

> [!NOTE]
><span data-ttu-id="eb539-120">Si no ve ninguna opción para incluir versiones preliminares, asegúrese de que está usando la versión más reciente de la herramienta de características de MR.</span><span class="sxs-lookup"><span data-stu-id="eb539-120">If you do not see an option to include preview releases, make sure you're using the latest version of the MR Feature Tool.</span></span>

<span data-ttu-id="eb539-121">Ahora que la configuración está completa, haga clic en **Start** (Iniciar) para empezar a trabajar con la herramienta de características de Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="eb539-121">Now that your settings are configured, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![Pantalla de inicio de la ventana de MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="eb539-123">Para facilitar la búsqueda de elementos, las características se agrupan por categoría. Haga clic en la lista desplegable **Mixed Reality Toolkit** para buscar los paquetes relacionados con Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="eb539-123">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>
<span data-ttu-id="eb539-124">Seleccione **Mixed Reality Toolkit Foundation** y haga clic en la lista desplegable que aparece junto a ella para seleccionar la versión de MRTK requerida. Para esta serie de tutoriales, seleccione el **paquete en versión preliminar 2.7**.</span><span class="sxs-lookup"><span data-stu-id="eb539-124">Check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select the latest **2.7 preview package**.</span></span>

![Ventana de MixedRealityFeatureTool para Unity 2020 y OpenXR](../images/mrft-mrtk.png)

<span data-ttu-id="eb539-126">En la lista desplegable **Platform Support** (Compatibilidad con plataformas), seleccione **Mixed Reality OpenXR Plugin** (Complemento OpenXR para Mixed Reality).</span><span class="sxs-lookup"><span data-stu-id="eb539-126">Under the **Platform Support** dropdown, select **Mixed Reality OpenXR Plugin**.</span></span> <span data-ttu-id="eb539-127">Asegúrese de que se haya seleccionado la última versión en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="eb539-127">Make sure the latest version is selected in the dropdown.</span></span>
<span data-ttu-id="eb539-128">![Selección del complemento OpenXR para Mixed Reality](../images/mrft-openxr.png)</span><span class="sxs-lookup"><span data-stu-id="eb539-128">![Selecting Mixed Reality OpenXR Plugin](../images/mrft-openxr.png)</span></span>

<span data-ttu-id="eb539-129">Haga clic en el botón **Get Features** (Obtener características) para descargar los paquetes seleccionados.</span><span class="sxs-lookup"><span data-stu-id="eb539-129">Click on the **Get features** button to download the selected packages.</span></span>

<span data-ttu-id="eb539-130">También debe establecer la ubicación del proyecto de Unity de destino para proporcionar el valor apropiado en **Project path** (Ruta de acceso del proyecto). Haga clic en los **tres puntos** que encontrará al lado del campo Project path (Ruta de acceso del proyecto) y vaya a la carpeta del proyecto en el explorador, por ejemplo _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="eb539-130">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="eb539-131">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="eb539-131">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="eb539-132">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="eb539-132">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="eb539-133">A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).</span><span class="sxs-lookup"><span data-stu-id="eb539-133">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Validar Mixed Reality Toolkit Foundation](../images/mrft-openxr-validate2.png)

<span data-ttu-id="eb539-135">Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.</span><span class="sxs-lookup"><span data-stu-id="eb539-135">Click on the **Approve** button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Aprobar Mixed Reality Toolkit Foundation](../images/mrft-openxr-import.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="eb539-137">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="eb539-137">Legacy WSA</span></span>](#tab/wsa)
<span data-ttu-id="eb539-138">Una vez que **MixedRealityFeatureTool** se haya abierto, haga clic en Start (Iniciar) para empezar a usar la herramienta Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="eb539-138">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool para WSA heredado](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="eb539-140">Para facilitar la búsqueda de elementos, las características se agrupan por categoría. Haga clic en la lista desplegable **Mixed Reality Toolkit** para buscar los paquetes relacionados con Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="eb539-140">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Ventana de MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="eb539-142">Active la opción **Mixed Reality Toolkit Foundation** y haga clic en la lista desplegable situada junto a ella para seleccionar la versión más reciente de MRTK y, a continuación, haga clic en el botón **Get features** (Obtener características) para descargar los paquetes seleccionados.</span><span class="sxs-lookup"><span data-stu-id="eb539-142">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the latest MRTK version, then click on **Get features** button to download the selected packages.</span></span>

![Seleccionar Mixed Reality Toolkit Foundation](../images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="eb539-144">También debe establecer la ubicación del proyecto de Unity de destino para proporcionar el valor apropiado en **Project path** (Ruta de acceso del proyecto). Haga clic en los **tres puntos** que encontrará al lado del campo Project path (Ruta de acceso del proyecto) y vaya a la carpeta del proyecto en el explorador, por ejemplo _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="eb539-144">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="eb539-145">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="eb539-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="eb539-146">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="eb539-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="eb539-147">A continuación, haga clic en el botón **Validate** (Validar) para validar el paquete seleccionado y aparecerá un cuadro emergente con el mensaje **No validation issues were detected** (No se detectaron problemas de validación). Haga clic en **Ok** (Aceptar) para cerrar el elemento emergente y haga clic en el botón **Import** (Importar).</span><span class="sxs-lookup"><span data-stu-id="eb539-147">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Validar Mixed Reality Toolkit Foundation](../images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="eb539-149">Haga clic en el botón **Approve** (Aprobar) para agregar **Mixed Reality Toolkit** al proyecto.</span><span class="sxs-lookup"><span data-stu-id="eb539-149">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Aprobar Mixed Reality Toolkit Foundation](../images/mr-learning-base/base-02-section4-step1-6.png)

