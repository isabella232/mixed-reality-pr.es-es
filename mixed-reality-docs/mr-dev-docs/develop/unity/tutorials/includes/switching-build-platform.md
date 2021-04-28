---
ms.openlocfilehash: d7232ca645c2a8cfb2508b090fdb7ae02c2ab010
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984413"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="400ed-101">Complemento XR para Unity 2019/2020 y Windows</span><span class="sxs-lookup"><span data-stu-id="400ed-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="400ed-102">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="400ed-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="400ed-104">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):</span><span class="sxs-lookup"><span data-stu-id="400ed-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="400ed-106">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="400ed-106">Wait for Unity to finish switching the platform:</span></span>

![Cambio de plataforma de Unity en curso](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="400ed-108">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="400ed-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Ventana Build (Compilación) de Unity con el icono de cerrar resaltado](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="400ed-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="400ed-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="400ed-111">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="400ed-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="400ed-113">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y:</span><span class="sxs-lookup"><span data-stu-id="400ed-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="400ed-114">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="400ed-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="400ed-115">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="400ed-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="400ed-116">Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).</span><span class="sxs-lookup"><span data-stu-id="400ed-116">Set **Build Type** to **D3D Project**</span></span>
4.  <span data-ttu-id="400ed-117">Establezca la **versión del SDK de destino** en **Instalada la más reciente**.</span><span class="sxs-lookup"><span data-stu-id="400ed-117">Set **Target SDK Version** to **Latest Installed**</span></span>
5.  <span data-ttu-id="400ed-118">Establezca **Minimum Platform Version** (Versión mínima de la plataforma) en **10.0.18362**.</span><span class="sxs-lookup"><span data-stu-id="400ed-118">Set **Minimum Platform Version** to **10.0.18362**</span></span>
6.  <span data-ttu-id="400ed-119">Establezca la **versión de Visual Studio**  en **Instalada la más reciente**.</span><span class="sxs-lookup"><span data-stu-id="400ed-119">Set **Visual Studio Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="400ed-120">Establezca **Compilar y ejecutar en** en **Dispositivo USB**.</span><span class="sxs-lookup"><span data-stu-id="400ed-120">Set **Build and Run on** to **USB Device**</span></span>
8.  <span data-ttu-id="400ed-121">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="400ed-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9.  <span data-ttu-id="400ed-122">Haga clic en el botón Switch Platform (Cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="400ed-122">Click the Switch Platform button</span></span>


![Configuración de compilación de Unity con la configuración establecida para Plataforma universal de Windows](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="400ed-124">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="400ed-124">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="400ed-125">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="400ed-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="400ed-126">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="400ed-126">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Ruta de menú de Build Settings… (Configuración de compilación…) de Unity](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="400ed-128">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):</span><span class="sxs-lookup"><span data-stu-id="400ed-128">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Ventana Build Settings (Configuración de compilación) de Unity con UWP seleccionado para cambiar de plataforma desde Standalone (Independiente)](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="400ed-130">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="400ed-130">Wait for Unity to finish switching the platform:</span></span>

![Cambio de plataforma de Unity en curso](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="400ed-132">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="400ed-132">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Ventana Build (Compilación) de Unity con el icono de cerrar resaltado](../images/mr-learning-base/base-02-section2-step1-4.png)
