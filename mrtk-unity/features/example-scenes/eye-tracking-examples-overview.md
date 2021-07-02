---
title: Introducción a los ejemplos de seguimiento de los ojos
description: Ejemplo para crear un seguimiento de los ojos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175542"
---
# <a name="eye-tracking-examples-overview"></a><span data-ttu-id="83df5-104">Introducción a los ejemplos de seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="83df5-104">Eye tracking examples overview</span></span>

<span data-ttu-id="83df5-105">En este tema se describe cómo empezar a trabajar rápidamente con el seguimiento de los ojos en MRTK mediante la creación de ejemplos de seguimiento ocular de MRTK (Assets/MRTK/Examples/Demos/EyeTracking).</span><span class="sxs-lookup"><span data-stu-id="83df5-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="83df5-106">Estos ejemplos le permiten experimentar una de nuestras nuevas funcionalidades mágicas de entrada: **Seguimiento de los ojos.**</span><span class="sxs-lookup"><span data-stu-id="83df5-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="83df5-107">La demostración incluye varios casos de uso, desde activaciones implícitas basadas en  los ojos hasta cómo combinar sin problemas información sobre lo que está viendo con la entrada de voz **y** mano.</span><span class="sxs-lookup"><span data-stu-id="83df5-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="83df5-108">Esto permite a los usuarios seleccionar y mover contenido holográfico de forma rápida y sin esfuerzo a través de su vista con solo mirar un destino y decir _"Seleccionar"_ o realizar un gesto con la mano.</span><span class="sxs-lookup"><span data-stu-id="83df5-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="83df5-109">Las demostraciones también incluyen un ejemplo de desplazamiento dirigido con mirada con los ojos, desplazamiento panorámico y zoom de texto e imágenes en una pizarra.</span><span class="sxs-lookup"><span data-stu-id="83df5-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="83df5-110">Por último, se proporciona un ejemplo para grabar y visualizar la atención visual del usuario en una pizarra 2D.</span><span class="sxs-lookup"><span data-stu-id="83df5-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="83df5-111">En la sección siguiente, encontrará más detalles sobre lo que incluye cada uno de los diferentes ejemplos del paquete de ejemplo de seguimiento ocular de MRTK (Assets/MRTK/Examples/Demos/EyeTracking):</span><span class="sxs-lookup"><span data-stu-id="83df5-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![Lista de escenas de seguimiento de los ojos](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="83df5-113">La siguiente sección es una introducción rápida de lo que son las escenas de demostración de seguimiento de los ojos individuales.</span><span class="sxs-lookup"><span data-stu-id="83df5-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="83df5-114">Las escenas de demostración de seguimiento de los ojos de MRTK [se cargan](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)aditivamente, lo que explicaremos a continuación cómo configurar.</span><span class="sxs-lookup"><span data-stu-id="83df5-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="83df5-115">Información general de los ejemplos de demostración de seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="83df5-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="83df5-116">**Selección de destino compatible con los ojos**</span><span class="sxs-lookup"><span data-stu-id="83df5-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="83df5-117">En este tutorial se muestra la facilidad de acceso a los datos de mirada con los ojos para seleccionar destinos.</span><span class="sxs-lookup"><span data-stu-id="83df5-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="83df5-118">Incluye un ejemplo de comentarios sutiles pero eficaces para proporcionar al usuario la confianza de que un destino se centra sin ser abrumador.</span><span class="sxs-lookup"><span data-stu-id="83df5-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="83df5-119">Además, hay un ejemplo sencillo de notificaciones inteligentes que desaparecen automáticamente después de leerse.</span><span class="sxs-lookup"><span data-stu-id="83df5-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="83df5-120">**Resumen:** selecciones de destino rápidas y sin esfuerzo mediante una combinación de ojos, voz y entrada de mano.</span><span class="sxs-lookup"><span data-stu-id="83df5-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="83df5-121">**Navegación con los ojos**</span><span class="sxs-lookup"><span data-stu-id="83df5-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="83df5-122">Imagine que está leyendo información en una pantalla lejana o en el lector electrónico y cuando llega al final del texto mostrado, el texto se desplaza automáticamente hacia arriba para mostrar más contenido.</span><span class="sxs-lookup"><span data-stu-id="83df5-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="83df5-123">O bien, ¿qué tal acercarse directamente hacia donde estaba mirando?</span><span class="sxs-lookup"><span data-stu-id="83df5-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="83df5-124">Estos son algunos de los ejemplos que se muestran en este tutorial con respecto a la navegación con los ojos.</span><span class="sxs-lookup"><span data-stu-id="83df5-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="83df5-125">Además, hay un ejemplo para la rotación de manos libres de hologramas 3D, ya que los hace girar automáticamente en función del foco actual.</span><span class="sxs-lookup"><span data-stu-id="83df5-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="83df5-126">**Resumen:** desplazamiento, desplazamiento panorámico, zoom, rotación 3D mediante una combinación de ojos, voz y entrada de mano.</span><span class="sxs-lookup"><span data-stu-id="83df5-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="83df5-127">**Posición compatible con los ojos**</span><span class="sxs-lookup"><span data-stu-id="83df5-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="83df5-128">En este tutorial se muestra un escenario de entrada denominado [Put-That-There](https://youtu.be/CbIn8p4_4CQ) que se reentraba a la investigación del laboratorio multimedia mit a principios de la década de 1980 con entrada de ojo, mano y voz.</span><span class="sxs-lookup"><span data-stu-id="83df5-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="83df5-129">La idea es sencilla: benefíciese de sus ojos para una selección y un posicionamiento de destino rápidos.</span><span class="sxs-lookup"><span data-stu-id="83df5-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="83df5-130">Basta con mirar un holograma y decir _"put this",_ mire dónde desea colocarlo y diga _"ahí!"._</span><span class="sxs-lookup"><span data-stu-id="83df5-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="83df5-131">Para colocar el holograma de forma más precisa, puede usar entradas adicionales de las manos, la voz o los controladores.</span><span class="sxs-lookup"><span data-stu-id="83df5-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="83df5-132">**Resumen:** colocación de hologramas con los ojos, la voz y la entrada de la mano *(arrastrar y colocar).*</span><span class="sxs-lookup"><span data-stu-id="83df5-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="83df5-133">Controles deslizantes compatibles con los ojos con los ojos y las manos.</span><span class="sxs-lookup"><span data-stu-id="83df5-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="83df5-134">**Visualización de la atención visual**</span><span class="sxs-lookup"><span data-stu-id="83df5-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="83df5-135">Los datos basados en la apariencia de los usuarios son una herramienta enormemente eficaz para evaluar la facilidad de uso de un diseño e identificar problemas en flujos de trabajo eficaces.</span><span class="sxs-lookup"><span data-stu-id="83df5-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="83df5-136">En este tutorial se de abordan diferentes visualizaciones de seguimiento de los ojos y cómo se ajustan a distintas necesidades.</span><span class="sxs-lookup"><span data-stu-id="83df5-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="83df5-137">Proporcionamos ejemplos básicos para registrar y cargar datos de seguimiento de los ojos y ejemplos de cómo visualizarlos.</span><span class="sxs-lookup"><span data-stu-id="83df5-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="83df5-138">**Resumen:** mapa de atención bidimensional (mapas térmicos) en pizarras.</span><span class="sxs-lookup"><span data-stu-id="83df5-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="83df5-139">Grabación & reproducir datos de seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="83df5-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="83df5-140">Configuración de los ejemplos de seguimiento de los ojos de MRTK</span><span class="sxs-lookup"><span data-stu-id="83df5-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="83df5-141">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="83df5-141">Prerequisites</span></span>

<span data-ttu-id="83df5-142">Tenga en cuenta que el uso de los ejemplos de seguimiento de los ojos en el dispositivo requiere un HoloLens 2 y un paquete de aplicación de ejemplo que se ha creado con la funcionalidad "Entrada de mirada" en appXManifest del paquete.</span><span class="sxs-lookup"><span data-stu-id="83df5-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="83df5-143">Para usar estos ejemplos de seguimiento de los [](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) ojos en el dispositivo, asegúrese de seguir estos pasos antes de compilar la aplicación en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83df5-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="83df5-144">1. Load EyeTrackingDemo-00-RootScene.unity</span><span class="sxs-lookup"><span data-stu-id="83df5-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="83df5-145">*EyeTrackingDemo-00-RootScene* es laescena base (raíz) que incluye todos los componentes principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="83df5-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="83df5-146">Esta es la escena que debe cargar primero y desde la que ejecutará las demostraciones de seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="83df5-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="83df5-147">Incluye un menú gráfico de escena que permite cambiar fácilmente entre las distintas muestras de seguimiento de los ojos que se [cargarán de forma aditiva.](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)</span><span class="sxs-lookup"><span data-stu-id="83df5-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![Menú de escena en el ejemplo de seguimiento de los ojos](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="83df5-149">La escena raíz incluye algunos componentes principales que se conservarán en las escenas cargadas aditivamente, como los perfiles configurados por MRTK y la cámara de escena.</span><span class="sxs-lookup"><span data-stu-id="83df5-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="83df5-150">_MixedRealityBasicSceneSetup_ (vea la captura de pantalla siguiente) incluye un script que cargará automáticamente la escena a la que se hace referencia al inicio.</span><span class="sxs-lookup"><span data-stu-id="83df5-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="83df5-151">De forma predeterminada, se trata _de EyeTrackingDemo-02-TargetSelection._</span><span class="sxs-lookup"><span data-stu-id="83df5-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![Ejemplo del script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="83df5-153">2. Agregar escenas al menú de compilación</span><span class="sxs-lookup"><span data-stu-id="83df5-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="83df5-154">Para cargar escenas de adición durante el tiempo de ejecución, primero debe agregar estas escenas al menú Build _Configuración -> Scenes in Build_ (Escenas de compilación).</span><span class="sxs-lookup"><span data-stu-id="83df5-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="83df5-155">Es importante que la escena raíz se muestra como la primera escena de la lista:</span><span class="sxs-lookup"><span data-stu-id="83df5-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![Menú crear Configuración escena para ejemplos de seguimiento de los ojos](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="83df5-157">3. Reproducir los ejemplos de seguimiento de los ojos en el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="83df5-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="83df5-158">Después de agregar las escenas de seguimiento de los ojos al Configuración de compilación y cargar _EyeTrackingDemo-00-RootScene,_ hay una última cosa que puede que quiera comprobar: ¿Está habilitado el script _"OnLoadStartScene"_ asociado a _MixedRealityBasicSceneSetup_ GameObject?</span><span class="sxs-lookup"><span data-stu-id="83df5-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="83df5-159">Esto es para que la escena raíz sepa qué escena de demostración se va a cargar primero.</span><span class="sxs-lookup"><span data-stu-id="83df5-159">This is to let the root scene know which demo scene to load first.</span></span>

![Ejemplo del script de OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="83df5-161">¡Vamos a deshacer!</span><span class="sxs-lookup"><span data-stu-id="83df5-161">Let's roll!</span></span> <span data-ttu-id="83df5-162">Presione _"Reproducir"._</span><span class="sxs-lookup"><span data-stu-id="83df5-162">Hit _"Play"_!</span></span>
<span data-ttu-id="83df5-163">Debería ver que aparecen varias gemas y el menú de la escena en la parte superior.</span><span class="sxs-lookup"><span data-stu-id="83df5-163">You should see several gems appear and the scene menu at the top.</span></span>

![Captura de pantalla de ejemplo de la escena de selección de destino et](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="83df5-165">También debería observar un pequeño círculo semitransparente en el centro de la vista del juego.</span><span class="sxs-lookup"><span data-stu-id="83df5-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="83df5-166">Esto actúa como un indicador (cursor) de la mirada con los ojos simulados: simplemente presione el botón derecho del _mouse_ y mueva el mouse para cambiar su posición.</span><span class="sxs-lookup"><span data-stu-id="83df5-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="83df5-167">Cuando el cursor mantenga el puntero sobre las gemas, observará que se ajustará al centro de la gema vista actualmente.</span><span class="sxs-lookup"><span data-stu-id="83df5-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="83df5-168">Se trata de una excelente manera de probar si los eventos se desencadenan según lo previsto _al "mirar"_ a un destino.</span><span class="sxs-lookup"><span data-stu-id="83df5-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="83df5-169">Tenga en cuenta que la mirada con los ojos _simulados_ a través del control del mouse es un complemento bastante deficiente para nuestros movimientos oculares rápidos e involuntarias.</span><span class="sxs-lookup"><span data-stu-id="83df5-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="83df5-170">Sin embargo, es excelente para probar la funcionalidad básica antes de iterar en el diseño implementando en el HoloLens 2 dispositivo.</span><span class="sxs-lookup"><span data-stu-id="83df5-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="83df5-171">Volver a la escena de ejemplo de seguimiento de los ojos: la gema gira siempre que se mira y se puede destruir "mirarla" y ...</span><span class="sxs-lookup"><span data-stu-id="83df5-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="83df5-172">Presionar _Entrar_ (que simula decir "seleccionar")</span><span class="sxs-lookup"><span data-stu-id="83df5-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="83df5-173">Decir _"seleccionar"_ en el micrófono</span><span class="sxs-lookup"><span data-stu-id="83df5-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="83df5-174">Al presionar _Espacio para_ mostrar la entrada de la mano simulada, haga clic en el botón izquierdo del mouse para realizar una acción de acercamiento simulada.</span><span class="sxs-lookup"><span data-stu-id="83df5-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="83df5-175">Se describe con más detalle cómo puede lograr estas interacciones en nuestro tutorial Selección de destino compatible con [**los ojos.**](../input/eye-tracking/eye-tracking-target-selection.md)</span><span class="sxs-lookup"><span data-stu-id="83df5-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="83df5-176">Al mover el cursor hasta la barra de menús superior de la escena, observará que el elemento que se mantiene el mouse se resaltará de forma sutil.</span><span class="sxs-lookup"><span data-stu-id="83df5-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="83df5-177">Puede seleccionar el elemento resaltado actualmente mediante uno de los métodos de confirmación descritos anteriormente (por ejemplo, presionar _Entrar)._</span><span class="sxs-lookup"><span data-stu-id="83df5-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="83df5-178">De este modo, puede cambiar entre las distintas escenas de ejemplo de seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="83df5-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="83df5-179">4. Cómo probar subescciones específicas</span><span class="sxs-lookup"><span data-stu-id="83df5-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="83df5-180">Al trabajar en un escenario específico, es posible que no quiera pasar por el menú de la escena cada vez.</span><span class="sxs-lookup"><span data-stu-id="83df5-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="83df5-181">En su lugar, puede que quiera empezar directamente desde la escena en la que está trabajando actualmente al presionar el _botón Reproducir._</span><span class="sxs-lookup"><span data-stu-id="83df5-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="83df5-182">No se preocupe.</span><span class="sxs-lookup"><span data-stu-id="83df5-182">No problem!</span></span> <span data-ttu-id="83df5-183">Esto es lo que puede hacer:</span><span class="sxs-lookup"><span data-stu-id="83df5-183">Here is what you can do:</span></span>

1. <span data-ttu-id="83df5-184">Carga de la _escena_ raíz</span><span class="sxs-lookup"><span data-stu-id="83df5-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="83df5-185">En la _escena raíz,_ deshabilite el script _"OnLoadStartScene"._</span><span class="sxs-lookup"><span data-stu-id="83df5-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="83df5-186">_Arrastre y coloque una de_ las escenas de prueba de seguimiento  de los ojos que se describen a continuación (o cualquier otra escena) en la vista Jerarquía, como se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="83df5-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![Ejemplo de escena de suma](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="83df5-188">Presione _Reproducir._</span><span class="sxs-lookup"><span data-stu-id="83df5-188">Press _Play_</span></span>

<span data-ttu-id="83df5-189">Tenga en cuenta que la carga de la sub escena como esta no es persistente: esto significa que si implementa la aplicación en el dispositivo HoloLens 2, solo cargará la escena raíz (suponiendo que aparezca en la parte superior de la compilación Configuración).</span><span class="sxs-lookup"><span data-stu-id="83df5-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="83df5-190">Además, al compartir el proyecto con otros usuarios, las sub escenas no se cargan automáticamente.</span><span class="sxs-lookup"><span data-stu-id="83df5-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="83df5-191">Ahora que sabe cómo hacer que las escenas de ejemplo de seguimiento de los ojos de MRTK funcionen, vamos a continuar profundizando en cómo seleccionar hologramas con los ojos: [Selección](../input/eye-tracking/eye-tracking-target-selection.md)de destino compatible con los ojos.</span><span class="sxs-lookup"><span data-stu-id="83df5-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="83df5-192">Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit)</span><span class="sxs-lookup"><span data-stu-id="83df5-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)
