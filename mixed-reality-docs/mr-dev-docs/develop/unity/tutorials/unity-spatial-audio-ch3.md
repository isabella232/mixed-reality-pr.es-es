---
title: 'Tutoriales de audio espacial: 3. Espacialización del audio de un vídeo'
description: Importe un recurso de vídeo en el proyecto de Unity y espacialice el audio del vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, video importing, Video Player
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712921"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="f5695-105">3. Espacialización del audio de un vídeo</span><span class="sxs-lookup"><span data-stu-id="f5695-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="f5695-106">Información general</span><span class="sxs-lookup"><span data-stu-id="f5695-106">Overview</span></span>

<span data-ttu-id="f5695-107">En este tutorial, aprenderá a espacializar el audio desde un origen de vídeo y probarlo en el editor de Unity y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f5695-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="f5695-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f5695-108">Objectives</span></span>

* <span data-ttu-id="f5695-109">Importación de un vídeo y adición de un reproductor de vídeo</span><span class="sxs-lookup"><span data-stu-id="f5695-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="f5695-110">Reproducir el vídeo en un cuadrángulo</span><span class="sxs-lookup"><span data-stu-id="f5695-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="f5695-111">Enrutar audio desde el vídeo al cuadrángulo y espacializar el audio</span><span class="sxs-lookup"><span data-stu-id="f5695-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="f5695-112">Importación de un vídeo y adición de un reproductor de vídeo a la escena</span><span class="sxs-lookup"><span data-stu-id="f5695-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="f5695-113">Para este tutorial, use este [vídeo del](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) proyecto de ejemplo de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="f5695-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="f5695-114">Para importar Vídeo en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="f5695-114">To import Video into the unity project.</span></span> <span data-ttu-id="f5695-115">En el menú de Unity, **seleccione Asset** Import  >  **New Asset** 
 ![ Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="f5695-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span></span>

<span data-ttu-id="f5695-116">En la ventana Importar nuevo **recurso...** , seleccione el archivo **Microsoft HoloLens - Spatial Sound-PTPvx7mGall4** que descargó y haga clic en el botón Abrir para importar el recurso en el proyecto: </span><span class="sxs-lookup"><span data-stu-id="f5695-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Selección del recurso](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

<span data-ttu-id="f5695-118">El ajuste de la configuración de calidad del clip de vídeo puede garantizar una reproducción sin problemas en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f5695-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="f5695-119">Seleccione el archivo de vídeo en la **ventana Proyecto** y, en la ventana Inspector del archivo de **vídeo,** invalide la configuración de aplicaciones de la **Tienda Windows** y:</span><span class="sxs-lookup"><span data-stu-id="f5695-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="f5695-120">Habilitar **transcodificación**</span><span class="sxs-lookup"><span data-stu-id="f5695-120">Enable **Transcode**</span></span>
* <span data-ttu-id="f5695-121">Establezca **Códec** en H264</span><span class="sxs-lookup"><span data-stu-id="f5695-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="f5695-122">Establecer **el modo de velocidad de bits** en Bajo</span><span class="sxs-lookup"><span data-stu-id="f5695-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="f5695-123">Establecer **la calidad espacial** en Calidad espacial media</span><span class="sxs-lookup"><span data-stu-id="f5695-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="f5695-124">Después de estos ajustes, haga clic en Aplicar para cambiar la configuración de calidad en el clip de vídeo.</span><span class="sxs-lookup"><span data-stu-id="f5695-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Cambio de propiedad de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

<span data-ttu-id="f5695-126">Haga clic con el botón derecho en Jerarquía, seleccione **Reproductor**  >  **de vídeo para** agregar el componente Reproductor de vídeo.</span><span class="sxs-lookup"><span data-stu-id="f5695-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Agregar reproductor de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="f5695-128">Reproducir vídeo en un cuadrángulo</span><span class="sxs-lookup"><span data-stu-id="f5695-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="f5695-129">El **objeto Reproductor de** vídeo necesita un objeto de juego con textura para representar el vídeo.</span><span class="sxs-lookup"><span data-stu-id="f5695-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="f5695-130">Haga clic con el botón derecho en Hierarchy (Jerarquía), seleccione 3D Object Quad (Cuatro objetos **3D)** para crear un quad y  >   configurar su **componente Transform** (Transformar) como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="f5695-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="f5695-131">**Posición:** X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="f5695-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="f5695-132">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f5695-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f5695-133">**Escala:** X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="f5695-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Adición de un cuadrándular](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

<span data-ttu-id="f5695-135">Ahora tiene que  texturar el cuadrángulo con el vídeo. En la ventana Proyecto, haga clic con el botón derecho y elija Crear textura de representación para crear un componente Render Texture (Representar textura), escriba un nombre adecuado para La textura de representación, por    >   ejemplo, Textura de _audio espacial_:</span><span class="sxs-lookup"><span data-stu-id="f5695-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Crear textura de representación](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

<span data-ttu-id="f5695-137">Seleccione Render **Texture (Representar textura)** y, en la ventana Inspector, establezca la propiedad **Size** para que coincida con la resolución nativa del vídeo de 1280 x 720.</span><span class="sxs-lookup"><span data-stu-id="f5695-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="f5695-138">A continuación, para garantizar un buen rendimiento de la representación HoloLens 2, establezca la propiedad **Búfer** de profundidad en **Al menos 16 bits de profundidad.**</span><span class="sxs-lookup"><span data-stu-id="f5695-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Propiedades de textura de representación](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

<span data-ttu-id="f5695-140">A continuación, use la textura de **audio espacial** render texture creada como textura para el **cuadrángulo**:</span><span class="sxs-lookup"><span data-stu-id="f5695-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="f5695-141">Arrastre la **textura de audio espacial** desde la ventana **Proyecto** al **cuadrángulo** de la jerarquía para agregar la textura de representación al cuadrángulo.</span><span class="sxs-lookup"><span data-stu-id="f5695-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="f5695-142">Para garantizar un buen rendimiento en HoloLens 2, seleccione Quad en la jerarquía y, en la ventana Inspector del **sombreador, seleccione** el sombreador estándar Mixed Reality  >   Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f5695-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Propiedades de textura quad](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

<span data-ttu-id="f5695-144">Para establecer el **Reproductor de vídeo** y **Representar** textura para  reproducir el clip de vídeo, seleccione **el Reproductor** de vídeo en la jerarquía y, en la **ventana Inspector,**</span><span class="sxs-lookup"><span data-stu-id="f5695-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="f5695-145">Establezca la **propiedad Clip de** vídeo en el archivo de vídeo descargado "Microsoft HoloLens - Spatial Sound-PTPvx7mGall4"</span><span class="sxs-lookup"><span data-stu-id="f5695-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="f5695-146">Active la casilla **Bucle**</span><span class="sxs-lookup"><span data-stu-id="f5695-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="f5695-147">Establecer **textura de destino** en la nueva textura de representación Textura de audio **espacial**</span><span class="sxs-lookup"><span data-stu-id="f5695-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Propiedades del reproductor de vídeo](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="f5695-149">Espacialización del audio del vídeo</span><span class="sxs-lookup"><span data-stu-id="f5695-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="f5695-150">En la ventana Hierarchy (Jerarquía), seleccione **Quad** object (Objeto Quad) y, en la ventana Inspector, use el botón Add **Component** (Agregar componente) para agregar audio **source** (Origen de audio) al que enrutará el audio desde el vídeo.</span><span class="sxs-lookup"><span data-stu-id="f5695-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="f5695-151">En el **origen de audio**:</span><span class="sxs-lookup"><span data-stu-id="f5695-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="f5695-152">Establezca **Output (Salida)** en **spatial audio mixer (Mezclador de audio espacial)**</span><span class="sxs-lookup"><span data-stu-id="f5695-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="f5695-153">Active la **casilla Espacializar**</span><span class="sxs-lookup"><span data-stu-id="f5695-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="f5695-154">Mover el **control deslizante de Spatial Blend** a 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="f5695-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Inspector de origen de audio cuadrángulo](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

<span data-ttu-id="f5695-156">Para establecer el Reproductor de vídeo para enrutar su audio al origen **de audio,** seleccione el Reproductor de vídeo en la ventana Jerarquía y, en el objeto Reproductor de vídeo del Inspector, realice los cambios siguientes. </span><span class="sxs-lookup"><span data-stu-id="f5695-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="f5695-157">Establezca el modo **de salida de audio** en Origen de **audio**</span><span class="sxs-lookup"><span data-stu-id="f5695-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="f5695-158">Establezca la **propiedad Origen de** audio en el **cuadrángulo.**</span><span class="sxs-lookup"><span data-stu-id="f5695-158">Set the **Audio Source** property to the **Quad**</span></span>

![Origen de audio del conjunto de reproductores de vídeo](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> <span data-ttu-id="f5695-160">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="f5695-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f5695-161">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="f5695-161">Congratulations</span></span>

<span data-ttu-id="f5695-162">En este tutorial, ha aprendido a espacializar el audio desde un origen de vídeo Pruebe la aplicación en un HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="f5695-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="f5695-163">Verá y escuchará el vídeo, y el audio del vídeo se espacializa.</span><span class="sxs-lookup"><span data-stu-id="f5695-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="f5695-164">En el siguiente tutorial, aprenderá a habilitar y deshabilitar la espacialización en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="f5695-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f5695-165">Tutorial siguiente: 4. Habilitación y deshabilitación de la espacialización en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="f5695-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
