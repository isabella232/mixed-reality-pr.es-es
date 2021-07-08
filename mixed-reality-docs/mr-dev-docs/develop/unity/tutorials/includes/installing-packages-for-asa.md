---
ms.openlocfilehash: 0a89ef77bee7eff83d4599c46ffd2681c99b2165
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175576"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="86900-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="86900-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="86900-102">En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, compruebe tener instalado **AR Foundation** > **4.1.7**.</span><span class="sxs-lookup"><span data-stu-id="86900-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![Unity Package Manager con AR Foundation seleccionado](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="86900-104">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="86900-104">Importing the tutorial assets</span></span>

<span data-ttu-id="86900-105">Agregue el SDK de Azure Spatial Anchors V2.10 al proyecto. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="86900-105">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="86900-106">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="86900-106">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="86900-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="86900-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="86900-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="86900-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="86900-109">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="86900-109">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](../images/mr-learning-asa/asa-02-section3-step1-2-OpenXR.png)

> [!TIP]
> <span data-ttu-id="86900-111">Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](../mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="86900-111">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="86900-112">Complemento de XR para Unity 2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="86900-112">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="86900-113">En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation > 4.0.12** y haga clic en el botón **Install** (Instalar) para instalar el paquete:</span><span class="sxs-lookup"><span data-stu-id="86900-113">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![Unity Package Manager con AR Foundation seleccionado](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="86900-115">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="86900-115">Importing the tutorial assets</span></span>

<span data-ttu-id="86900-116">Agregue el SDK de Azure Spatial Anchors V2.10 al proyecto. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="86900-116">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="86900-117">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="86900-117">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="86900-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="86900-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="86900-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="86900-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="86900-120">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="86900-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](../images/mr-learning-asa/asa-02-section3-step1-2-XRSDK.PNG)

> [!TIP]
> <span data-ttu-id="86900-122">Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](../mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="86900-122">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="86900-123">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="86900-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="86900-124">En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation > 3.1.3** y haga clic en el botón **Install** (Instalar) para instalar el paquete:</span><span class="sxs-lookup"><span data-stu-id="86900-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![Unity Package Manager con AR Foundation seleccionado](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="86900-126">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="86900-126">Importing the tutorial assets</span></span>

<span data-ttu-id="86900-127">Agregue el SDK de Azure Spatial Anchors V2.7.2 al proyecto. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="86900-127">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="86900-128">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="86900-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="86900-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="86900-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="86900-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="86900-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage)

<span data-ttu-id="86900-131">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="86900-131">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](../images/mr-learning-asa/asa-02-section3-step1-2-Legacy.png)

> [!NOTE]
> <span data-ttu-id="86900-133">Si ve que las advertencias de CS0618 con respecto a "WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)" están en desuso, puede omitir estas advertencias.</span><span class="sxs-lookup"><span data-stu-id="86900-133">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="86900-134">Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](../mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="86900-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>
