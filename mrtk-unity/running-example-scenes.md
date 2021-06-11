---
title: Ejecución de las escenas de ejemplo
description: Obtenga información sobre cómo adquirir y usar las escenas de ejemplo de MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: mixed reality toolkit, MRTK, examples, HoloLens, HoloLens 2, shaders, tooltips, hand interaction, clipping, bounding boxes, buttons, hand menus, slate, slider
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911885"
---
# <a name="example-scenes"></a><span data-ttu-id="0e7be-104">Escenas de ejemplo</span><span class="sxs-lookup"><span data-stu-id="0e7be-104">Example scenes</span></span>

<span data-ttu-id="0e7be-105">MRTK proporciona varios tipos de escenas de ejemplo que muestran las características y los bloques de creación de MRTK para la experiencia del usuario espacial.</span><span class="sxs-lookup"><span data-stu-id="0e7be-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="0e7be-106">Experimentar y diseccionar escenas de ejemplo podría ser útil para comprender las características y aplicarlas a los proyectos.</span><span class="sxs-lookup"><span data-stu-id="0e7be-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="0e7be-107">Cómo adquirir escenas de ejemplo</span><span class="sxs-lookup"><span data-stu-id="0e7be-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="0e7be-108">Uso de Mixed Reality feature tool y el administrador de paquetes de Unity</span><span class="sxs-lookup"><span data-stu-id="0e7be-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="0e7be-109">Puede descargar e importar el paquete **Mixed Reality Toolkit Examples** mediante Mixed Reality Feature [Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="0e7be-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="0e7be-110">En Unity, use el menú **Ventana > Administrador de paquetes > En proyecto > personalizado** y seleccione Mixed Reality Toolkit Examples (Ejemplos del kit de **herramientas).**</span><span class="sxs-lookup"><span data-stu-id="0e7be-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="0e7be-111">En la lista del lado derecho del panel, haga clic en el botón Importar en **proyecto** junto a los nombres de escena de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="0e7be-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="0e7be-112">Por ejemplo, puede hacer clic en **el botón Importar** en proyecto junto a **Demostraciones - HandTracking**.</span><span class="sxs-lookup"><span data-stu-id="0e7be-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="0e7be-113">Una vez importados, podrá encontrarlos en la carpeta Assets > Samples (Recursos **> Ejemplos).**</span><span class="sxs-lookup"><span data-stu-id="0e7be-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="0e7be-114">**La escena HandInteractionExamples** es un excelente lugar para empezar a experimentar las interacciones espaciales de MRTK y los bloques de creación de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="0e7be-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="0e7be-115">Descarga e importación directas de paquetes desde GitHub</span><span class="sxs-lookup"><span data-stu-id="0e7be-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="0e7be-116">Si no usa Mixed Reality Feature Tool, puede descargar e importar directamente **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** desde la página de lanzamiento de GITHub de [MRTK.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="0e7be-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="0e7be-117">Use **Assets > Import Package > Custom Package (Recursos** > paquete personalizado) para importar el paquete .unitypackage descargado.</span><span class="sxs-lookup"><span data-stu-id="0e7be-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="0e7be-118">Una vez importado, podrá encontrar escenas de ejemplo en **Assets > MRTK > Examples > Demos**.</span><span class="sxs-lookup"><span data-stu-id="0e7be-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>