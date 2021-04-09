---
ms.openlocfilehash: 78605b17e93429ad974e1ca21e7859035f38d615
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088722"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="0ce41-101">Complemento XR para Unity 2019/2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="0ce41-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="0ce41-102">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="0ce41-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="0ce41-104">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):</span><span class="sxs-lookup"><span data-stu-id="0ce41-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="0ce41-106">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="0ce41-106">Wait for Unity to finish switching the platform:</span></span>

![Cambio de plataforma de Unity en curso](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="0ce41-108">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="0ce41-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Ventana Build (Compilación) de Unity con el icono de cerrar resaltado](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="0ce41-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="0ce41-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="0ce41-111">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="0ce41-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="0ce41-113">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y:</span><span class="sxs-lookup"><span data-stu-id="0ce41-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="0ce41-114">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0ce41-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="0ce41-115">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="0ce41-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="0ce41-116">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="0ce41-116">Set **Build Type** to **D3D**</span></span>
4.  <span data-ttu-id="0ce41-117">Establezca la **versión mínima de la plataforma** en **10.2.18362**</span><span class="sxs-lookup"><span data-stu-id="0ce41-117">Set **Minimum Platform Version** to **10.2.18362**</span></span>
5.  <span data-ttu-id="0ce41-118">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="0ce41-118">Set **UWP SDK** to **Latest installed**</span></span>
6.  <span data-ttu-id="0ce41-119">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="0ce41-119">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
7.  <span data-ttu-id="0ce41-120">Haga clic en el botón Switch Platform (Cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="0ce41-120">Click the Switch Platform button</span></span>


![Configuración de compilación de Unity con la configuración establecida para Plataforma universal de Windows](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="0ce41-122">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="0ce41-122">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="0ce41-123">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="0ce41-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="0ce41-124">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="0ce41-124">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="0ce41-126">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):</span><span class="sxs-lookup"><span data-stu-id="0ce41-126">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="0ce41-128">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="0ce41-128">Wait for Unity to finish switching the platform:</span></span>

![Cambio de plataforma de Unity en curso](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="0ce41-130">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="0ce41-130">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Ventana Build (Compilación) de Unity con el icono de cerrar resaltado](../images/mr-learning-base/base-02-section2-step1-4.png)