---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097083"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="4f06a-101">Complemento XR para Unity 2019/2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="4f06a-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="4f06a-102">Garantía de la funcionalidad de entrada de mirada e incorporación del proveedor de datos de mirada</span><span class="sxs-lookup"><span data-stu-id="4f06a-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="4f06a-103">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="4f06a-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4f06a-105">La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="4f06a-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="4f06a-106">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="4f06a-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="4f06a-107">En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):</span><span class="sxs-lookup"><span data-stu-id="4f06a-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="4f06a-108">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="4f06a-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Incorporación del proveedor de datos de mirada 1](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="4f06a-110">Asigne **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="4f06a-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Incorporación del proveedor de datos de mirada 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="4f06a-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="4f06a-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="4f06a-113">Garantía de la funcionalidad de entrada de mirada e incorporación del proveedor de datos de mirada</span><span class="sxs-lookup"><span data-stu-id="4f06a-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="4f06a-114">En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):</span><span class="sxs-lookup"><span data-stu-id="4f06a-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="4f06a-115">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="4f06a-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Incorporación del proveedor de datos de mirada 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="4f06a-117">Asigne **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="4f06a-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Incorporación del proveedor de datos de mirada 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="4f06a-119">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="4f06a-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="4f06a-120">Asegurarse de que está habilitada la funcionalidad de entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="4f06a-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="4f06a-121">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="4f06a-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4f06a-123">La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="4f06a-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="4f06a-124">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="4f06a-124">However, if it is not enabled, make sure you enable it now.</span></span>
