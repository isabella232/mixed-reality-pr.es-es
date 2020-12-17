---
title: Configuración del proyecto sin MRTK
description: Instrucciones para configurar un proyecto de Unity para Windows Mixed Reality
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento
ms.openlocfilehash: 1337001e8cc5c280c5789acbc8f10f40bca9b763
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613430"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="64a7c-104">Configurar el proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="64a7c-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="64a7c-105">Windows Mixed Reality (WMR) es una plataforma de Microsoft introducida como parte del sistema operativo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="64a7c-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="64a7c-106">La plataforma WMR permite crear aplicaciones que representan contenido digital en dispositivos de visualización holográfica y VR.</span><span class="sxs-lookup"><span data-stu-id="64a7c-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="64a7c-107">Aunque Microsoft y la comunidad han creado herramientas de código abierto, como el kit de herramientas de la [realidad mixta (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , que configurará automáticamente el entorno de WMR, muchos desarrolladores quieren crear sus experiencias desde cero.</span><span class="sxs-lookup"><span data-stu-id="64a7c-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="64a7c-108">En la siguiente documentación se muestra cómo configurar correctamente un proyecto para el desarrollo de realidad mixta, tanto si usa MRTK como si no.</span><span class="sxs-lookup"><span data-stu-id="64a7c-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="64a7c-109">La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.</span><span class="sxs-lookup"><span data-stu-id="64a7c-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="64a7c-110">Siempre puede importar MRTK más adelante, por lo que no hay ninguna penalización en primer lugar en la ruta manual.</span><span class="sxs-lookup"><span data-stu-id="64a7c-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="64a7c-111">Si elige la configuración manual de WMR, la configuración que debe cambiar se divide en dos categorías: por proyecto y por escena.</span><span class="sxs-lookup"><span data-stu-id="64a7c-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="64a7c-112">Configuración por proyecto</span><span class="sxs-lookup"><span data-stu-id="64a7c-112">Per-project settings</span></span>

<span data-ttu-id="64a7c-113">Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="64a7c-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana de configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltada](images/wmr-config-img-3.png)

<span data-ttu-id="64a7c-115">Si tiene como destino HoloLens 2, debe cambiar a la Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="64a7c-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="64a7c-116">Seleccionar **archivo > configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="64a7c-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="64a7c-117">Seleccione **plataforma universal de Windows** en la lista plataforma y seleccione **Switch Platform (cambiar plataforma** ).</span><span class="sxs-lookup"><span data-stu-id="64a7c-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="64a7c-118">Establecimiento de la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="64a7c-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="64a7c-119">Establecimiento del **dispositivo de destino** en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="64a7c-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="64a7c-120">Establecer el **tipo de compilación** en **D3D**</span><span class="sxs-lookup"><span data-stu-id="64a7c-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="64a7c-121">Establecimiento del **SDK de UWP** en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="64a7c-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="64a7c-122">Establezca la **configuración de compilación** en **Release** porque hay problemas de rendimiento conocidos con debug</span><span class="sxs-lookup"><span data-stu-id="64a7c-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

<span data-ttu-id="64a7c-124">Después de establecer la plataforma, debe dejar que Unity sepa crear una [vista envolvente](../../design/app-views.md) en lugar de una vista 2D cuando se exporte.</span><span class="sxs-lookup"><span data-stu-id="64a7c-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="64a7c-125">Para XRSDK</span><span class="sxs-lookup"><span data-stu-id="64a7c-125">For XRSDK</span></span> 

1. <span data-ttu-id="64a7c-126">En el editor de Unity, navegue a **editar > configuración del proyecto** y seleccione **Administración de complementos de XR** .</span><span class="sxs-lookup"><span data-stu-id="64a7c-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="64a7c-127">Seleccione **instalar administración de complementos de XR**</span><span class="sxs-lookup"><span data-stu-id="64a7c-127">Select **Install XR Plugin Management**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-5.png)

3. <span data-ttu-id="64a7c-129">Seleccione **inicializar XR en el inicio** y **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="64a7c-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-7.png)

4. <span data-ttu-id="64a7c-131">Expanda la sección **Administración de complementos de XR** y seleccione **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="64a7c-131">Expand the **XR Plug-in Management** section and select **Windows Mixed Reality**</span></span>
5. <span data-ttu-id="64a7c-132">Active todas las casillas y establezca el **modo de envío de profundidad** en profundidad de **16 bits**</span><span class="sxs-lookup"><span data-stu-id="64a7c-132">Check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="64a7c-134">Para XR heredado</span><span class="sxs-lookup"><span data-stu-id="64a7c-134">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="64a7c-135">El XR heredado está en desuso en Unity 2019 y se quitó en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="64a7c-135">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="64a7c-136">Abra **configuración del reproductor...** en la **configuración de compilación... y** expanda el grupo de **configuración XR**</span><span class="sxs-lookup"><span data-stu-id="64a7c-136">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="64a7c-137">En la sección **configuración de XR** , seleccione **realidad virtual compatible** para agregar la lista de dispositivos de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="64a7c-137">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="64a7c-138">Establecer el **formato de profundidad** en profundidad de **16 bits** y habilitar el **uso compartido del búfer de profundidad**</span><span class="sxs-lookup"><span data-stu-id="64a7c-138">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="64a7c-139">Establecer el **modo de representación estéreo** en **una instancia de paso único**</span><span class="sxs-lookup"><span data-stu-id="64a7c-139">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="64a7c-140">Seleccione **WSA Holographic Remoting compatible** si desea usar Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="64a7c-140">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración del reproductor resaltada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="64a7c-142">Actualización del manifiesto</span><span class="sxs-lookup"><span data-stu-id="64a7c-142">Updating the manifest</span></span>

<span data-ttu-id="64a7c-143">La aplicación ahora puede controlar la representación holográfica y la entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="64a7c-143">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="64a7c-144">Sin embargo, la aplicación debe declarar las capacidades adecuadas en el manifiesto para aprovechar ciertas funciones.</span><span class="sxs-lookup"><span data-stu-id="64a7c-144">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="64a7c-145">Para encontrar las capacidades de los proyectos, vaya a **configuración del reproductor > configuración de Plataforma universal de Windows > configuración de publicación > funcionalidades**.</span><span class="sxs-lookup"><span data-stu-id="64a7c-145">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="64a7c-146">Se recomienda que realice las declaraciones de manifiesto en Unity para incluirlas en todos los proyectos futuros que exporte.</span><span class="sxs-lookup"><span data-stu-id="64a7c-146">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="64a7c-147">Las capacidades aplicables para habilitar las API de Unity usadas con frecuencia para la realidad mixta son:</span><span class="sxs-lookup"><span data-stu-id="64a7c-147">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="64a7c-148">Capacidad</span><span class="sxs-lookup"><span data-stu-id="64a7c-148">Capability</span></span>  |  <span data-ttu-id="64a7c-149">API que requieren funcionalidad</span><span class="sxs-lookup"><span data-stu-id="64a7c-149">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="64a7c-150">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="64a7c-150">SpatialPerception</span></span>  |  <span data-ttu-id="64a7c-151">SurfaceObserver (acceso a mallas de [asignación espacial](../../design/spatial-mapping.md) en HoloLens) &mdash; *no se necesita ninguna funcionalidad para el seguimiento espacial general de los auriculares*</span><span class="sxs-lookup"><span data-stu-id="64a7c-151">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="64a7c-152">Web</span><span class="sxs-lookup"><span data-stu-id="64a7c-152">WebCam</span></span>  |  <span data-ttu-id="64a7c-153">Fotocaptura y videocaptura</span><span class="sxs-lookup"><span data-stu-id="64a7c-153">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="64a7c-154">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="64a7c-154">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="64a7c-155">Fotocaptura o videocaptura, respectivamente (al almacenar el contenido capturado)</span><span class="sxs-lookup"><span data-stu-id="64a7c-155">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="64a7c-156">Micrófono</span><span class="sxs-lookup"><span data-stu-id="64a7c-156">Microphone</span></span>  |  <span data-ttu-id="64a7c-157">VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="64a7c-157">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="64a7c-158">InternetClient</span><span class="sxs-lookup"><span data-stu-id="64a7c-158">InternetClient</span></span>  |  <span data-ttu-id="64a7c-159">DictationRecognizer (y para usar el generador de perfiles de Unity)</span><span class="sxs-lookup"><span data-stu-id="64a7c-159">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="64a7c-160">Configuración de calidad</span><span class="sxs-lookup"><span data-stu-id="64a7c-160">Quality settings</span></span>

<span data-ttu-id="64a7c-161">HoloLens tiene una GPU de clase móvil.</span><span class="sxs-lookup"><span data-stu-id="64a7c-161">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="64a7c-162">Si su aplicación tiene como destino HoloLens, querrá que la configuración de calidad de la aplicación se ajuste para obtener un rendimiento más rápido para asegurarse de que mantiene la velocidad de fotogramas completa:</span><span class="sxs-lookup"><span data-stu-id="64a7c-162">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>

1. <span data-ttu-id="64a7c-163">Seleccione **editar > configuración del proyecto > calidad**</span><span class="sxs-lookup"><span data-stu-id="64a7c-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="64a7c-164">Seleccione la **lista desplegable** en el logotipo de la **tienda Windows** y seleccione **muy baja**.</span><span class="sxs-lookup"><span data-stu-id="64a7c-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="64a7c-165">Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna de la tienda Windows y la fila **muy baja** es verde.</span><span class="sxs-lookup"><span data-stu-id="64a7c-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green</span></span>
3. <span data-ttu-id="64a7c-166">En la sección **Shadows** , seleccione **deshabilitar sombras** .</span><span class="sxs-lookup"><span data-stu-id="64a7c-166">In the **Shadows** section, select **Disable Shadows**</span></span>

<span data-ttu-id="64a7c-167">![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración de calidad resaltada](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="64a7c-167">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="64a7c-168">*Configuración de calidad de Unity*</span><span class="sxs-lookup"><span data-stu-id="64a7c-168">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="64a7c-169">Configuración por escena</span><span class="sxs-lookup"><span data-stu-id="64a7c-169">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="64a7c-170">Configuración de la cámara de Unity</span><span class="sxs-lookup"><span data-stu-id="64a7c-170">Unity camera settings</span></span>

<span data-ttu-id="64a7c-171">Con la **realidad virtual compatible** activada, el componente de [cámara Unity](camera-in-unity.md) controla el [seguimiento de los cabezales y la representación Stereoscopic](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="64a7c-171">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="64a7c-172">Esto significa que no es necesario reemplazar el objeto de cámara principal por una cámara personalizada.</span><span class="sxs-lookup"><span data-stu-id="64a7c-172">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="64a7c-173">Si su aplicación tiene como destino HoloLens específicamente, debe cambiar algunas opciones de configuración para optimizar las pantallas transparentes del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="64a7c-173">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="64a7c-174">Esta configuración permite que el contenido holográfica se muestre a través del mundo físico:</span><span class="sxs-lookup"><span data-stu-id="64a7c-174">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="64a7c-175">En la **jerarquía**, seleccione la **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="64a7c-175">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="64a7c-176">En el panel **Inspector** , establezca la **posición** de la transformación en **0, 0, 0** para que la ubicación del encabezado del usuario se inicie en el origen del mundo Unity.</span><span class="sxs-lookup"><span data-stu-id="64a7c-176">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="64a7c-177">Cambie las **marcas de borrado** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="64a7c-177">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="64a7c-178">Cambie el color de **fondo** a **RGBA 0, 0, 0 y 0**.</span><span class="sxs-lookup"><span data-stu-id="64a7c-178">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="64a7c-179">Los negros se representan como transparentes en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="64a7c-179">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="64a7c-180">Cambiar los **planos de recorte, cerca** de [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).</span><span class="sxs-lookup"><span data-stu-id="64a7c-180">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="64a7c-181">![Captura de pantalla de la pestaña inspector abierta en el editor de Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="64a7c-181">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="64a7c-182">*Configuración de la cámara de Unity*</span><span class="sxs-lookup"><span data-stu-id="64a7c-182">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64a7c-183">Si elimina y crea una nueva cámara, asegúrese de que la nueva cámara esté etiquetada como **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="64a7c-183">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="64a7c-184">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="64a7c-184">Next steps</span></span>

<span data-ttu-id="64a7c-185">Ahora que el proyecto está listo, puede empezar a desarrollar su experiencia de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="64a7c-185">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="64a7c-186">Agregar [bloques de creación principales](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="64a7c-186">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="64a7c-187">Consulte las [funcionalidades de la plataforma y las API](unity-development-overview.md#3-platform-capabilities-and-apis) disponibles</span><span class="sxs-lookup"><span data-stu-id="64a7c-187">Check out available [platform capabilities and APIs](unity-development-overview.md#3-platform-capabilities-and-apis)</span></span>
* <span data-ttu-id="64a7c-188">Obtener información sobre cómo [implementar la aplicación](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset)</span><span class="sxs-lookup"><span data-stu-id="64a7c-188">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset)</span></span>
* <span data-ttu-id="64a7c-189">Usar el [simulador de realidad mixta](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="64a7c-189">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="64a7c-190">Consulta también</span><span class="sxs-lookup"><span data-stu-id="64a7c-190">See also</span></span>
* [<span data-ttu-id="64a7c-191">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="64a7c-191">Install the tools</span></span>](../install-the-tools.md)