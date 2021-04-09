---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097757"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="aac58-101">Complemento XR para Unity 2019/2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="aac58-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="aac58-102">Garantía de la funcionalidad del micrófono e incorporación del proveedor de datos de entrada de voz</span><span class="sxs-lookup"><span data-stu-id="aac58-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="aac58-103">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="aac58-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Enable microphone capability (Habilitar la funcionalidad del micrófono)](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="aac58-105">La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="aac58-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="aac58-106">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="aac58-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="aac58-107">En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):</span><span class="sxs-lookup"><span data-stu-id="aac58-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="aac58-108">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="aac58-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Proveedor de datos para agregar nuevos comandos de voz](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="aac58-110">Asigne **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="aac58-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Adición de la configuración de los nuevos comandos de voz](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="aac58-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="aac58-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="aac58-113">Garantía de la funcionalidad del micrófono e incorporación del proveedor de datos de entrada de voz</span><span class="sxs-lookup"><span data-stu-id="aac58-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="aac58-114">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="aac58-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Habilitar la funcionalidad del micrófono para OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="aac58-116">La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="aac58-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="aac58-117">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="aac58-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="aac58-118">En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):</span><span class="sxs-lookup"><span data-stu-id="aac58-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="aac58-119">Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="aac58-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Adición de nuevos comandos de voz para OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="aac58-121">Asigne **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="aac58-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Adición de la configuración de los nuevos comandos de voz para OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="aac58-123">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="aac58-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="aac58-124">Asegurarse de que la funcionalidad del micrófono está habilitada</span><span class="sxs-lookup"><span data-stu-id="aac58-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="aac58-125">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="aac58-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Enable microphone capability (Habilitar la funcionalidad del micrófono)](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="aac58-127">La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="aac58-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="aac58-128">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="aac58-128">However, if it is not enabled, make sure you enable it now.</span></span>
