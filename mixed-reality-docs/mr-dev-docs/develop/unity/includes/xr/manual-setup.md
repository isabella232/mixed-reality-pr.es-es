---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535730"
---
# <a name="openxr"></a>[<span data-ttu-id="a7a6d-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="a7a6d-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="a7a6d-102">Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="a7a6d-103">Siga las [instrucciones de instalación y uso y](../../welcome-to-mr-feature-tool.md) seleccione el paquete Mixed Reality complemento **OpenXR** en la **categoría Soporte técnico de la** plataforma:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="a7a6d-105">Establecimiento del destino de compilación</span><span class="sxs-lookup"><span data-stu-id="a7a6d-105">Setting your build target</span></span>

<span data-ttu-id="a7a6d-106">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

<span data-ttu-id="a7a6d-108">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="a7a6d-109">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="a7a6d-110">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="a7a6d-111">Establezca **Architecture** (Arquitectura) en **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="a7a6d-112">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="a7a6d-113">Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).</span><span class="sxs-lookup"><span data-stu-id="a7a6d-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="a7a6d-114">Establezca **Versión del SDK de destino** en Instalado más **reciente**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="a7a6d-116">Configuración de la administración de complementos XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="a7a6d-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="a7a6d-117">Para establecer OpenXR como runtime en Unity:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="a7a6d-118">En el Editor de Unity, vaya **a Editar > configuración del proyecto.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="a7a6d-119">En la lista de configuración, seleccione **Administración de complementos XR.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="a7a6d-120">Seleccione **Instalar administración de complementos XR** si aparece Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos ![ XR resaltada](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="a7a6d-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="a7a6d-121">Active la **casilla Initialize XR on Startup (Inicializar XR al iniciar)**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="a7a6d-122">Si el destino es Desktop VR, permanezca en la pestaña PC Independiente (el monitor) y active las casillas **OpenXR** **y Windows Mixed Reality de características.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="a7a6d-123">Si el destino es HoloLens 2, cambie a la pestaña Plataforma universal de Windows (el logotipo de Windows) y seleccione los cuadros **OpenXR** **y Microsoft HoloLens de características.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración de complementos XR resaltada](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="a7a6d-125">Si ve un icono de advertencia amarillo junto a **Complemento OpenXR,** haga clic en el icono y seleccione **Corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="a7a6d-126">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto de OpenXR](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="a7a6d-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="a7a6d-128">Optimization</span></span>

<span data-ttu-id="a7a6d-129">Si va a desarrollar para HoloLens 2, seleccione el elemento de menú Mixed Reality > **Project > Apply recommended project settings for HoloLens 2** (Aplicar configuración de proyecto recomendada para HoloLens 2 obtener un mejor rendimiento de la aplicación).</span><span class="sxs-lookup"><span data-stu-id="a7a6d-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](../../images/openxr-img-08.png)

<span data-ttu-id="a7a6d-131">Ya está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="a7a6d-132">Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="a7a6d-133">Proyectos de ejemplo de Unity para OpenXR y HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a7a6d-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="a7a6d-134">Consulte el repositorio de ejemplos de [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para ver proyectos de Unity de ejemplo que muestran cómo compilar aplicaciones de Unity para cascos HoloLens 2 o Mixed Reality mediante el complemento Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="a7a6d-135">O bien, si está listo para empezar a trabajar por su cuenta desde un proyecto en blanco, vaya al artículo [Configuración de la](../../camera-in-unity.md) cámara.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="a7a6d-136">Windows XR</span><span class="sxs-lookup"><span data-stu-id="a7a6d-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="a7a6d-137">El complemento XR de Windows está en desuso en Unity 2021.1 y se quitará en Unity 2021.2.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="a7a6d-138">Para el desarrollo de Unity 2020, Microsoft recomienda el complemento OpenXR en su lugar.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="a7a6d-139">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

<span data-ttu-id="a7a6d-141">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="a7a6d-142">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="a7a6d-143">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="a7a6d-144">Establezca **Architecture** (Arquitectura) en **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="a7a6d-145">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="a7a6d-146">Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).</span><span class="sxs-lookup"><span data-stu-id="a7a6d-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="a7a6d-147">Establezca **Versión del SDK de destino** en Instalado más **reciente**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="a7a6d-148">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="a7a6d-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

<span data-ttu-id="a7a6d-150">Después de configurar la plataforma, debe dejar [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="a7a6d-151">En el Editor de Unity, vaya **a Editar > configuración del** proyecto y seleccione Administración de complementos **XR.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="a7a6d-152">Seleccione **Install XR Plugin Management (Instalar administración de complementos XR)** si aparece.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-152">Select **Install XR Plugin Management** if it appears</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="a7a6d-154">Seleccione **Initialize XR on Startup (Inicializar XR)** **al iniciar Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="a7a6d-156">Seleccione la **sección XR Plug-in Management** Windows Mixed Reality (Administración de complementos XR), active todas las casillas y establezca Depth Buffer Format (Formato del búfer de profundidad) en Depth Buffer 16 Bit (Búfer de  >   profundidad de  **16 bits).**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity Windows Mixed Reality sección resaltada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="a7a6d-158">XR heredado</span><span class="sxs-lookup"><span data-stu-id="a7a6d-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="a7a6d-159">El XR heredado está en desuso en Unity 2019 y se ha quitado en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="a7a6d-160">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

<span data-ttu-id="a7a6d-162">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="a7a6d-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="a7a6d-163">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="a7a6d-164">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="a7a6d-165">Establezca **Architecture** (Arquitectura) en **ARM64**.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="a7a6d-166">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="a7a6d-167">Establezca **Build Type** (Tipo de compilación) en **D3D Project** (Proyecto de D3D).</span><span class="sxs-lookup"><span data-stu-id="a7a6d-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="a7a6d-168">Establezca **Versión del SDK de destino** en Instalado más **reciente**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="a7a6d-169">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="a7a6d-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

<span data-ttu-id="a7a6d-171">Después de configurar la plataforma, debe hacer [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="a7a6d-172">Abra **Configuración del reproductor...** desde la **configuración de compilación... ventana** y expanda el **grupo XR Settings (Configuración de XR).**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="a7a6d-173">En la **sección Configuración de XR,** seleccione **Virtual Reality Supported (Virtual Reality compatible)** para agregar la lista Dispositivos de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="a7a6d-174">Establezca **Depth Format (Formato de** profundidad) en profundidad de **16 bits** y active Enable Depth Buffer Sharing **(Habilitar uso compartido de búfer de profundidad).**</span><span class="sxs-lookup"><span data-stu-id="a7a6d-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="a7a6d-175">En **Stereo Rendering Mode** (Modo de representación estéreo), seleccione **Single Pass Instanced** (Instancia de paso único)</span><span class="sxs-lookup"><span data-stu-id="a7a6d-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="a7a6d-176">Seleccione **WSA Holographic Remoting Supported (Comunicación** remota holográfica de WSA compatible) si desea usar la comunicación remota del modo de reproducción holográfica.</span><span class="sxs-lookup"><span data-stu-id="a7a6d-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la sección Configuración del reproductor resaltada](../../images/wmr-config-img-9.png)
