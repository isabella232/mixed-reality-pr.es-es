---
title: Configuración del proyecto sin MRTK
description: Aprenda a configurar un nuevo proyecto de Unity para Windows Mixed Reality sin el kit de herramientas de realidad mixta.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117629"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="e4fef-104">Configuración de un proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="e4fef-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="e4fef-105">Windows Mixed Reality (WMR) es una plataforma de Microsoft introducida como parte del sistema operativo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e4fef-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="e4fef-106">La plataforma WMR permite crear aplicaciones que representan contenido digital en dispositivos de visualización holográfica y VR.</span><span class="sxs-lookup"><span data-stu-id="e4fef-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="e4fef-107">Aunque Microsoft y la comunidad han creado herramientas de código abierto, como el kit de herramientas de la [realidad mixta (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , que configurará automáticamente el entorno de WMR, muchos desarrolladores quieren crear sus experiencias desde cero.</span><span class="sxs-lookup"><span data-stu-id="e4fef-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="e4fef-108">En la siguiente documentación se muestra cómo configurar correctamente un proyecto para el desarrollo de realidad mixta, tanto si usa MRTK como si no.</span><span class="sxs-lookup"><span data-stu-id="e4fef-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="e4fef-109">La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.</span><span class="sxs-lookup"><span data-stu-id="e4fef-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="e4fef-110">Siempre puede importar MRTK más adelante, por lo que no hay ninguna penalización en primer lugar en la ruta manual.</span><span class="sxs-lookup"><span data-stu-id="e4fef-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="e4fef-111">Si elige la configuración manual de WMR, la configuración que debe cambiar se divide en dos categorías: por proyecto y por escena.</span><span class="sxs-lookup"><span data-stu-id="e4fef-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="e4fef-112">Configuración por proyecto</span><span class="sxs-lookup"><span data-stu-id="e4fef-112">Per-project settings</span></span>

<span data-ttu-id="e4fef-113">Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="e4fef-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana de configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltada](images/wmr-config-img-3.png)

<span data-ttu-id="e4fef-115">Si tiene como destino HoloLens 2, debe cambiar a la Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="e4fef-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="e4fef-116">Seleccionar **archivo > configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="e4fef-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="e4fef-117">Seleccione **plataforma universal de Windows** en la lista plataforma y seleccione **Switch Platform (cambiar plataforma** ).</span><span class="sxs-lookup"><span data-stu-id="e4fef-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="e4fef-118">Establecimiento de la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="e4fef-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="e4fef-119">Establecimiento del **dispositivo de destino** en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e4fef-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="e4fef-120">Establecer el **tipo de compilación** en **D3D**</span><span class="sxs-lookup"><span data-stu-id="e4fef-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="e4fef-121">Establecimiento del **SDK de UWP** en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="e4fef-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="e4fef-122">Establezca la **configuración de compilación** en **Release** porque hay problemas de rendimiento conocidos con debug</span><span class="sxs-lookup"><span data-stu-id="e4fef-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

<span data-ttu-id="e4fef-124">Después de establecer la plataforma, debe dejar que Unity sepa crear una [vista envolvente](../../design/app-views.md) en lugar de una vista 2D cuando se exporte.</span><span class="sxs-lookup"><span data-stu-id="e4fef-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="e4fef-125">Para XRSDK</span><span class="sxs-lookup"><span data-stu-id="e4fef-125">For XRSDK</span></span> 

1. <span data-ttu-id="e4fef-126">En el editor de Unity, navegue a **editar > configuración del proyecto** y seleccione **Administración de complementos de XR** .</span><span class="sxs-lookup"><span data-stu-id="e4fef-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="e4fef-127">Seleccione **instalar administración de complementos de XR**</span><span class="sxs-lookup"><span data-stu-id="e4fef-127">Select **Install XR Plugin Management**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-5.png)

3. <span data-ttu-id="e4fef-129">Seleccione **inicializar XR en el inicio** y **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="e4fef-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-7.png)

4. <span data-ttu-id="e4fef-131">Expanda la sección **Administración de complementos de XR** y seleccione la pestaña Configuración de la **plataforma de Windows universal** .</span><span class="sxs-lookup"><span data-stu-id="e4fef-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="e4fef-132">Si usa Unity 2020 o una versión posterior, verá las opciones para comprobar **OpenXR (versión preliminar)** o **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="e4fef-132">If you are using Unity 2020 or later, you will see the options to check **OpenXR (preview)** or **Windows Mixed Reality**</span></span>
6. <span data-ttu-id="e4fef-133">Puede elegir en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e4fef-133">You can choose either runtime.</span></span>  <span data-ttu-id="e4fef-134">Si está desarrollando específicamente para HoloLens 2 o la reverberación de HP G2 y decide probar **OpenXR (versión preliminar)**, seleccione el cuadro OpenXR (versión preliminar) y revise nuestra guía sobre cómo [usar el complemento Mixed Reality OpenXR para Unity](openxr-getting-started.md) para que se configure correctamente para estos dispositivos antes de volver a este tutorial.</span><span class="sxs-lookup"><span data-stu-id="e4fef-134">If you are specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR (preview)**, select the OpenXR (preview) box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>
7. <span data-ttu-id="e4fef-135">Si decide elegir el complemento de **Windows Mixed Reality** , active todas las casillas y establezca el **modo de envío de profundidad** en profundidad de **16 bits** .</span><span class="sxs-lookup"><span data-stu-id="e4fef-135">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="e4fef-137">Para XR heredado</span><span class="sxs-lookup"><span data-stu-id="e4fef-137">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="e4fef-138">El XR heredado está en desuso en Unity 2019 y se quitó en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="e4fef-138">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="e4fef-139">Abra **configuración del reproductor...** en la **configuración de compilación... y** expanda el grupo de **configuración XR**</span><span class="sxs-lookup"><span data-stu-id="e4fef-139">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="e4fef-140">En la sección **configuración de XR** , seleccione **realidad virtual compatible** para agregar la lista de dispositivos de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="e4fef-140">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="e4fef-141">Establecer el **formato de profundidad** en profundidad de **16 bits** y habilitar el **uso compartido del búfer de profundidad**</span><span class="sxs-lookup"><span data-stu-id="e4fef-141">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="e4fef-142">Establecer el **modo de representación estéreo** en **una instancia de paso único**</span><span class="sxs-lookup"><span data-stu-id="e4fef-142">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="e4fef-143">Seleccione **WSA Holographic Remoting compatible** si desea usar Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="e4fef-143">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración del reproductor resaltada](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="e4fef-145">Actualización del manifiesto</span><span class="sxs-lookup"><span data-stu-id="e4fef-145">Updating the manifest</span></span>

<span data-ttu-id="e4fef-146">La aplicación ahora puede controlar la representación holográfica y la entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="e4fef-146">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="e4fef-147">Sin embargo, la aplicación debe declarar las capacidades adecuadas en el manifiesto para aprovechar ciertas funciones.</span><span class="sxs-lookup"><span data-stu-id="e4fef-147">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="e4fef-148">Para encontrar las capacidades de los proyectos, vaya a **configuración del reproductor > configuración de Plataforma universal de Windows > configuración de publicación > funcionalidades**.</span><span class="sxs-lookup"><span data-stu-id="e4fef-148">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="e4fef-149">Se recomienda que realice las declaraciones de manifiesto en Unity para incluirlas en todos los proyectos futuros que exporte.</span><span class="sxs-lookup"><span data-stu-id="e4fef-149">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="e4fef-150">Las capacidades aplicables para habilitar las API de Unity usadas con frecuencia para la realidad mixta son:</span><span class="sxs-lookup"><span data-stu-id="e4fef-150">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="e4fef-151">Capacidad</span><span class="sxs-lookup"><span data-stu-id="e4fef-151">Capability</span></span>  |  <span data-ttu-id="e4fef-152">API que requieren funcionalidad</span><span class="sxs-lookup"><span data-stu-id="e4fef-152">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="e4fef-153">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="e4fef-153">SpatialPerception</span></span>  |  <span data-ttu-id="e4fef-154">SurfaceObserver (acceso a mallas de [asignación espacial](../../design/spatial-mapping.md) en HoloLens) &mdash; *no se necesita ninguna funcionalidad para el seguimiento espacial general de los auriculares*</span><span class="sxs-lookup"><span data-stu-id="e4fef-154">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="e4fef-155">Web</span><span class="sxs-lookup"><span data-stu-id="e4fef-155">WebCam</span></span>  |  <span data-ttu-id="e4fef-156">Fotocaptura y videocaptura</span><span class="sxs-lookup"><span data-stu-id="e4fef-156">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="e4fef-157">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="e4fef-157">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="e4fef-158">Fotocaptura o videocaptura, respectivamente (al almacenar el contenido capturado)</span><span class="sxs-lookup"><span data-stu-id="e4fef-158">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="e4fef-159">Micrófono</span><span class="sxs-lookup"><span data-stu-id="e4fef-159">Microphone</span></span>  |  <span data-ttu-id="e4fef-160">VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="e4fef-160">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="e4fef-161">InternetClient</span><span class="sxs-lookup"><span data-stu-id="e4fef-161">InternetClient</span></span>  |  <span data-ttu-id="e4fef-162">DictationRecognizer (y para usar el generador de perfiles de Unity)</span><span class="sxs-lookup"><span data-stu-id="e4fef-162">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="e4fef-163">Configuración de calidad</span><span class="sxs-lookup"><span data-stu-id="e4fef-163">Quality settings</span></span>

<span data-ttu-id="e4fef-164">HoloLens tiene una GPU de clase móvil.</span><span class="sxs-lookup"><span data-stu-id="e4fef-164">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="e4fef-165">Si su aplicación tiene como destino HoloLens, querrá empezar con la configuración de calidad de la aplicación ajustada para obtener un rendimiento más rápido y asegurarse de que mantiene la velocidad de fotogramas completa.</span><span class="sxs-lookup"><span data-stu-id="e4fef-165">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="e4fef-166">Una vez que tenga más en el desarrollo, puede considerar la posibilidad de hacer ping a la configuración de calidad para encontrar el equilibrio adecuado entre calidad y rendimiento:</span><span class="sxs-lookup"><span data-stu-id="e4fef-166">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="e4fef-167">Seleccione **editar > configuración del proyecto > calidad**</span><span class="sxs-lookup"><span data-stu-id="e4fef-167">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="e4fef-168">Seleccione la **lista desplegable** en el logotipo de la  **tienda Windows**   y seleccione  **muy baja**.</span><span class="sxs-lookup"><span data-stu-id="e4fef-168">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="e4fef-169">Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna de la tienda Windows y la fila muy baja es verde.</span><span class="sxs-lookup"><span data-stu-id="e4fef-169">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="e4fef-170">En la sección **Shadows**   , seleccione **deshabilitar sombras** .</span><span class="sxs-lookup"><span data-stu-id="e4fef-170">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="e4fef-171">![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración de calidad resaltada](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="e4fef-171">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="e4fef-172">*Configuración de calidad de Unity*</span><span class="sxs-lookup"><span data-stu-id="e4fef-172">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="e4fef-173">Configuración por escena</span><span class="sxs-lookup"><span data-stu-id="e4fef-173">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="e4fef-174">Configuración de la cámara de Unity</span><span class="sxs-lookup"><span data-stu-id="e4fef-174">Unity camera settings</span></span>

<span data-ttu-id="e4fef-175">Con la **realidad virtual compatible** activada, el componente de [cámara Unity](camera-in-unity.md) controla el [seguimiento de los cabezales y la representación Stereoscopic](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e4fef-175">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="e4fef-176">Esto significa que no es necesario reemplazar el objeto de cámara principal por una cámara personalizada.</span><span class="sxs-lookup"><span data-stu-id="e4fef-176">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="e4fef-177">Si su aplicación tiene como destino HoloLens específicamente, debe cambiar algunas opciones de configuración para optimizar las pantallas transparentes del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e4fef-177">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="e4fef-178">Esta configuración permite que el contenido holográfica se muestre a través del mundo físico:</span><span class="sxs-lookup"><span data-stu-id="e4fef-178">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="e4fef-179">En la **jerarquía**, seleccione la **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="e4fef-179">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="e4fef-180">En el panel **Inspector** , establezca la **posición** de la transformación en **0, 0, 0** para que la ubicación del encabezado del usuario se inicie en el origen del mundo Unity.</span><span class="sxs-lookup"><span data-stu-id="e4fef-180">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="e4fef-181">Cambie las **marcas de borrado** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="e4fef-181">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="e4fef-182">Cambie el color de **fondo** a **RGBA 0, 0, 0 y 0**.</span><span class="sxs-lookup"><span data-stu-id="e4fef-182">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="e4fef-183">Los negros se representan como transparentes en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e4fef-183">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="e4fef-184">Cambiar los **planos de recorte, cerca** de [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).</span><span class="sxs-lookup"><span data-stu-id="e4fef-184">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="e4fef-185">![Captura de pantalla de la pestaña inspector abierta en el editor de Unity](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="e4fef-185">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="e4fef-186">*Configuración de la cámara de Unity*</span><span class="sxs-lookup"><span data-stu-id="e4fef-186">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4fef-187">Si elimina y crea una nueva cámara, asegúrese de que la nueva cámara esté etiquetada como **MainCamera**.</span><span class="sxs-lookup"><span data-stu-id="e4fef-187">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e4fef-188">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="e4fef-188">Next steps</span></span>

<span data-ttu-id="e4fef-189">Ahora que el proyecto está listo, puede empezar a desarrollar su experiencia de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="e4fef-189">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="e4fef-190">Agregar [bloques de creación principales](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="e4fef-190">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="e4fef-191">Consulte las [funcionalidades de la plataforma y las API](unity-development-overview.md#3-advanced-features) disponibles</span><span class="sxs-lookup"><span data-stu-id="e4fef-191">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="e4fef-192">Obtener información sobre cómo [implementar la aplicación](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="e4fef-192">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="e4fef-193">Usar el [simulador de realidad mixta](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="e4fef-193">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="e4fef-194">Consulta también</span><span class="sxs-lookup"><span data-stu-id="e4fef-194">See also</span></span>
* [<span data-ttu-id="e4fef-195">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="e4fef-195">Install the tools</span></span>](../install-the-tools.md)