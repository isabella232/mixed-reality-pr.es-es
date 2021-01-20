---
title: 'Tutoriales de audio espacial: 3. Espacialización del audio de un vídeo'
description: Importe un recurso de vídeo en el proyecto de Unity y cospatiala el audio del vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer, vídeo, importación, reproductor de vídeo
ms.openlocfilehash: 6474da522e650d23349a21c3deeac00222b8ce93
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578625"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="86a91-105">3. Espacialización del audio de un vídeo</span><span class="sxs-lookup"><span data-stu-id="86a91-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="86a91-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="86a91-106">Overview</span></span>

<span data-ttu-id="86a91-107">En este tutorial, obtendrá información sobre cómo espaciale el audio de un origen de vídeo y cómo probarlo en el editor de Unity y en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="86a91-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="86a91-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="86a91-108">Objectives</span></span>

* <span data-ttu-id="86a91-109">Importar un vídeo y agregar un reproductor de vídeo</span><span class="sxs-lookup"><span data-stu-id="86a91-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="86a91-110">Reproducir el vídeo en un Quadrangle</span><span class="sxs-lookup"><span data-stu-id="86a91-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="86a91-111">Enrute el audio del vídeo al Quadrangle y Spatial el audio</span><span class="sxs-lookup"><span data-stu-id="86a91-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="86a91-112">Importar un vídeo y agregar un reproductor de vídeo a la escena</span><span class="sxs-lookup"><span data-stu-id="86a91-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="86a91-113">En este tutorial, puede usar [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) del proyecto de ejemplo de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="86a91-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="86a91-114">Para importar vídeo en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="86a91-114">To import Video into the unity project.</span></span> <span data-ttu-id="86a91-115">en el menú de Unity, seleccione **recurso**  >  **importar nuevo** 
 activo importar activo. ![](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="86a91-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="86a91-116">En la ventana **importar nuevo recurso...** , seleccione el archivo **Microsoft HoloLens-Spatial Sound-PTPvx7mDon4** que descargó y haga clic en el botón **abrir** para importar el recurso en el proyecto:</span><span class="sxs-lookup"><span data-stu-id="86a91-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Seleccionar activo](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="86a91-118">Ajustar la configuración de calidad en el clip de vídeo puede garantizar una reproducción fluida de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="86a91-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="86a91-119">Seleccione el archivo de vídeo en la ventana **proyecto** y, en la ventana del inspector del archivo de vídeo, **invalide** la configuración de las aplicaciones de la **tienda Windows** y:</span><span class="sxs-lookup"><span data-stu-id="86a91-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="86a91-120">Habilitar **Transcode**</span><span class="sxs-lookup"><span data-stu-id="86a91-120">Enable **Transcode**</span></span>
* <span data-ttu-id="86a91-121">Establecer **códec** en H264</span><span class="sxs-lookup"><span data-stu-id="86a91-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="86a91-122">Establecer el **modo de velocidad de bits** en baja</span><span class="sxs-lookup"><span data-stu-id="86a91-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="86a91-123">Establecer **calidad espacial** en calidad espacial media</span><span class="sxs-lookup"><span data-stu-id="86a91-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="86a91-124">Después de estos ajustes, haga clic en aplicar para cambiar la configuración de calidad en el clip de vídeo.</span><span class="sxs-lookup"><span data-stu-id="86a91-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Cambio de propiedad de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="86a91-126">Haga clic con el botón derecho en la jerarquía, seleccione  >  **reproductor** de vídeo de vídeo para agregar el componente reproductor de vídeo.</span><span class="sxs-lookup"><span data-stu-id="86a91-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Agregar reproductor de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="86a91-128">Reproducir vídeo en un Quadrangle</span><span class="sxs-lookup"><span data-stu-id="86a91-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="86a91-129">El objeto **reproductor de vídeo** necesita un objeto de juego con textura para representar el vídeo.</span><span class="sxs-lookup"><span data-stu-id="86a91-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="86a91-130">Haga clic con el botón derecho en la jerarquía, seleccione **objeto 3D**  >  **cuádruple** para crear un cuádruple y configure su componente de **transformación** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="86a91-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="86a91-131">**Posición**: X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="86a91-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="86a91-132">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="86a91-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="86a91-133">**Escala**: X = 1,28, y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="86a91-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Agregar un cuádruple](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="86a91-135">Ahora debe texturar el **cuádruple** con el vídeo, en la ventana **proyecto** , haga clic con el botón derecho y elija **crear**  >  **textura de representación** para crear un componente de textura de representación, escriba un nombre adecuado para la textura de representación, por ejemplo, _textura de audio espacial_:</span><span class="sxs-lookup"><span data-stu-id="86a91-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Crear textura de representación](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="86a91-137">Seleccione la **textura de representación** y, en la ventana del inspector, establezca la propiedad **size** para que coincida con la resolución nativa del vídeo de 1280x720.</span><span class="sxs-lookup"><span data-stu-id="86a91-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="86a91-138">A continuación, para garantizar un buen rendimiento de la representación en HoloLens 2, establezca la propiedad de **búfer de profundidad** en una **profundidad de 16 bits como mínimo**.</span><span class="sxs-lookup"><span data-stu-id="86a91-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Representar propiedades de textura](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="86a91-140">A continuación, use la textura de **audio espacial** de textura de representación creada como textura para la **cuádruple**:</span><span class="sxs-lookup"><span data-stu-id="86a91-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="86a91-141">Arrastre la **textura de audio espacial** desde la ventana de **proyecto** hasta el **cuádruple** de la jerarquía para agregar la textura de representación a la cuádruple</span><span class="sxs-lookup"><span data-stu-id="86a91-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="86a91-142">Para garantizar un buen rendimiento en HoloLens 2, seleccione cuádruple en la jerarquía y, en la ventana del inspector del sombreador, seleccione el sombreador estándar del **Kit de herramientas de realidad mixta**  >   .</span><span class="sxs-lookup"><span data-stu-id="86a91-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Propiedades de textura cuádruple](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="86a91-144">Para configurar **el reproductor de vídeo** y mostrar la **textura** para reproducir el clip de vídeo, seleccione el **reproductor** de vídeo en la **jerarquía** y en la ventana del **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="86a91-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="86a91-145">Establezca la propiedad **clip de vídeo** en el archivo de vídeo descargado ' Microsoft HoloLens-Spatial Sound-PTPvx7mDon4 '</span><span class="sxs-lookup"><span data-stu-id="86a91-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="86a91-146">Marque la casilla **bucle**</span><span class="sxs-lookup"><span data-stu-id="86a91-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="86a91-147">Establecer la **textura de destino** en la nueva textura de representación de textura de **audio espacial**</span><span class="sxs-lookup"><span data-stu-id="86a91-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Propiedades del reproductor de vídeo](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="86a91-149">Spatial el audio del vídeo</span><span class="sxs-lookup"><span data-stu-id="86a91-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="86a91-150">En la ventana jerarquía, seleccione **cuádruple** objeto y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el **origen de audio** al que enrutará el audio del vídeo.</span><span class="sxs-lookup"><span data-stu-id="86a91-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="86a91-151">En el **origen de audio**:</span><span class="sxs-lookup"><span data-stu-id="86a91-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="86a91-152">Establecer la **salida** en el **mezclador de audio espacial**</span><span class="sxs-lookup"><span data-stu-id="86a91-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="86a91-153">Active la casilla **Spatial**</span><span class="sxs-lookup"><span data-stu-id="86a91-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="86a91-154">Mueve el control deslizante de **mezcla espacial** a 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="86a91-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Inspector de fuente de audio cuádruple](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="86a91-156">Para configurar el reproductor de vídeo para que enrute su audio al **origen de audio**, seleccione el **reproductor de vídeo** en la ventana jerarquía y, en el objeto reproductor de vídeo del inspector, realice los cambios siguientes.</span><span class="sxs-lookup"><span data-stu-id="86a91-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="86a91-157">Establecer el **modo de salida de audio** en **origen de audio**</span><span class="sxs-lookup"><span data-stu-id="86a91-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="86a91-158">Establezca la propiedad **origen de audio** en el **cuádruple**</span><span class="sxs-lookup"><span data-stu-id="86a91-158">Set the **Audio Source** property to the **Quad**</span></span>

![Reproductor de vídeo conjunto de audio origen](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="86a91-160">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="86a91-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="86a91-161">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="86a91-161">Congratulations</span></span>

<span data-ttu-id="86a91-162">En este tutorial, ha aprendido cómo enespaciale el audio desde un origen de vídeo pruebe la aplicación en una HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="86a91-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="86a91-163">Verá y oirá el vídeo y el audio del vídeo está espacial.</span><span class="sxs-lookup"><span data-stu-id="86a91-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="86a91-164">En el siguiente tutorial, aprenderá a habilitar y deshabilitar la espacialización en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="86a91-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86a91-165">Siguiente tutorial: 4. habilitar y deshabilitar la espacialización en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="86a91-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
