---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394589"
---
# <a name="openxr"></a>[<span data-ttu-id="49005-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="49005-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="49005-102">Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="49005-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="49005-103">Siga las [instrucciones de instalación y uso](../../welcome-to-mr-feature-tool.md) y seleccione el Mixed Reality complemento **OpenXR** en la categoría Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="49005-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="49005-105">Establecimiento del destino de compilación</span><span class="sxs-lookup"><span data-stu-id="49005-105">Setting your build target</span></span>

<span data-ttu-id="49005-106">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="49005-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

<span data-ttu-id="49005-108">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="49005-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="49005-109">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="49005-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="49005-110">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="49005-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="49005-111">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="49005-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="49005-112">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="49005-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="49005-113">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="49005-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="49005-114">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="49005-114">Set **UWP SDK** to **Latest installed**</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="49005-116">Configuración de la administración de complementos XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="49005-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="49005-117">Para establecer OpenXR como runtime en Unity:</span><span class="sxs-lookup"><span data-stu-id="49005-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="49005-118">En el Editor de Unity, vaya **a Editar > configuración del proyecto.**</span><span class="sxs-lookup"><span data-stu-id="49005-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="49005-119">En la lista de configuración, seleccione **Administración de complementos XR.**</span><span class="sxs-lookup"><span data-stu-id="49005-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="49005-120">Active los **cuadros Inicializar XR al inicio** y **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="49005-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="49005-121">Si el destino HoloLens 2, asegúrese de que está en la plataforma para UWP y **seleccione Microsoft HoloLens conjunto de características.**</span><span class="sxs-lookup"><span data-stu-id="49005-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración de complementos XR resaltada](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="49005-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="49005-123">Optimization</span></span>

<span data-ttu-id="49005-124">Si va a desarrollar para HoloLens 2, vaya a Mixed Reality> **OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance (Aplicar la configuración de proyecto recomendada para HoloLens 2 obtener un mejor rendimiento de la aplicación).</span><span class="sxs-lookup"><span data-stu-id="49005-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="49005-126">Si ve un icono de advertencia amarillo junto a **Complemento OpenXR,** haga clic en el icono y **seleccione Corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="49005-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="49005-127">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="49005-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto de OpenXR](../../images/openxr-img-06.png)

<span data-ttu-id="49005-129">Ya está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="49005-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="49005-130">Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="49005-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="49005-131">Proyectos de ejemplo de Unity para OpenXR y HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="49005-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="49005-132">Consulte el repositorio de ejemplos de [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para ver proyectos de Unity de ejemplo que muestran cómo compilar aplicaciones de Unity para cascos HoloLens 2 o Mixed Reality mediante el complemento Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="49005-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="49005-133">Windows XR</span><span class="sxs-lookup"><span data-stu-id="49005-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="49005-134">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="49005-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

<span data-ttu-id="49005-136">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="49005-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="49005-137">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="49005-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="49005-138">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="49005-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="49005-139">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="49005-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="49005-140">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="49005-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="49005-141">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="49005-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="49005-142">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="49005-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="49005-143">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="49005-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

<span data-ttu-id="49005-145">Después de configurar la plataforma, debe dejar [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte:</span><span class="sxs-lookup"><span data-stu-id="49005-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="49005-146">En el Editor de Unity, vaya **a Editar > configuración del** proyecto y seleccione Administración de complementos **XR.**</span><span class="sxs-lookup"><span data-stu-id="49005-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="49005-147">Seleccione **Install XR Plugin Management (Instalar administración de complementos XR).**</span><span class="sxs-lookup"><span data-stu-id="49005-147">Select **Install XR Plugin Management**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="49005-149">Seleccione **Initialize XR on Startup (Inicializar XR)** **al iniciar Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="49005-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="49005-151">Expanda la **sección XR Plug-in Management (Administración** de complementos XR) y seleccione la pestaña **Univeral Windows Platform Settings (Configuración de plataforma de Windows univeral).**</span><span class="sxs-lookup"><span data-stu-id="49005-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="49005-152">Si usa Unity 2020 o posterior, verá las opciones para comprobar **OpenXR** o **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="49005-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="49005-153">Puede elegir cualquiera de los entornos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="49005-153">You can choose either runtime.</span></span>  <span data-ttu-id="49005-154">Si va a desarrollar específicamente para HoloLens 2 o HP Reverb G2 y decide probar **OpenXR,** active la casilla OpenXR y revise nuestra guía Uso del complemento [de OpenXR](../../openxr-getting-started.md) de Mixed Reality para Unity para configurarse correctamente para estos dispositivos antes de volver a este tutorial.</span><span class="sxs-lookup"><span data-stu-id="49005-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="49005-155">A partir de Unity 2020 LTS, Microsoft está adoptando el desarrollo con OpenXR.</span><span class="sxs-lookup"><span data-stu-id="49005-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="49005-156">A medida que migramos a esta ruta de acceso, en Unity 2021.1 el complemento XR de Windows estará en desuso y se quitará en 2021.2, lo que hace que OpenXR sea la única ruta de acceso admitida.</span><span class="sxs-lookup"><span data-stu-id="49005-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="49005-157">Puede encontrar más información en [Uso del complemento Mixed Reality OpenXR.](../../openxr-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="49005-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="49005-158">Si decide elegir  el complemento de Windows Mixed Reality, active todas las casillas y establezca **Modo de envío de** profundidad en Profundidad **de 16 bits.**</span><span class="sxs-lookup"><span data-stu-id="49005-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity Windows Mixed Reality sección resaltada](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="49005-160">XR heredado</span><span class="sxs-lookup"><span data-stu-id="49005-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="49005-161">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="49005-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](../../images/wmr-config-img-3.png)

<span data-ttu-id="49005-163">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="49005-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="49005-164">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="49005-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="49005-165">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="49005-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="49005-166">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="49005-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="49005-167">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="49005-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="49005-168">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="49005-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="49005-169">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="49005-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="49005-170">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="49005-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](../../images/wmr-config-img-4.png)

<span data-ttu-id="49005-172">Después de configurar la plataforma, debe hacer [](../../../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.</span><span class="sxs-lookup"><span data-stu-id="49005-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="49005-173">El XR heredado está en desuso en Unity 2019 y se ha quitado en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="49005-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="49005-174">Abra **Configuración del reproductor...** desde la **configuración de compilación... ventana** y expanda el **grupo XR Settings (Configuración de XR).**</span><span class="sxs-lookup"><span data-stu-id="49005-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="49005-175">En la **sección Configuración de XR,** seleccione **Virtual Reality Supported (Virtual Reality compatible)** para agregar la lista Dispositivos de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="49005-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="49005-176">Establezca **Depth Format (Formato de** profundidad) en Profundidad de **16 bits** y habilite Depth Buffer Sharing (Uso compartido del búfer de **profundidad).**</span><span class="sxs-lookup"><span data-stu-id="49005-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="49005-177">Establecer **el modo de representación estéreo** en Instancia de paso **único**</span><span class="sxs-lookup"><span data-stu-id="49005-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="49005-178">Seleccione **WSA Holographic Remoting Supported** (Comunicación remota holográfica de WSA compatible) si quiere usar la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="49005-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la sección Configuración del reproductor resaltada](../../images/wmr-config-img-9.png)