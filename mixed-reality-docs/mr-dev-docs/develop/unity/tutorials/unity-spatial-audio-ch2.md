---
title: 'Tutoriales de audio espacial: 2. Sonidos de interacción del botón de espacialización'
description: Agregue un botón al proyecto y espacialice los sonidos de interacción del botón.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con la cabeza, reverberación, Microsoft Spatializer, prefabs, curva de volumen
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712848"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="05edc-105">2. Sonidos de interacción del botón de espacialización</span><span class="sxs-lookup"><span data-stu-id="05edc-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="05edc-106">Información general</span><span class="sxs-lookup"><span data-stu-id="05edc-106">Overview</span></span>

<span data-ttu-id="05edc-107">En este tutorial, aprenderá a espacializar los sonidos de interacción del botón y también a usar un clip de audio para probar la interacción de botones espacializados.</span><span class="sxs-lookup"><span data-stu-id="05edc-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="05edc-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="05edc-108">Objectives</span></span>

* <span data-ttu-id="05edc-109">Agregar y espacializar los sonidos de clic del botón</span><span class="sxs-lookup"><span data-stu-id="05edc-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="05edc-110">Adición de un botón</span><span class="sxs-lookup"><span data-stu-id="05edc-110">Add a button</span></span>

<span data-ttu-id="05edc-111">Para agregar el prefab  Botón, en la ventana Proyecto, seleccione **Paquetes** y escriba "PressableButtonHoloLens2" en la barra de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="05edc-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Prefab de botón en Recursos](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

<span data-ttu-id="05edc-113">El botón prefab es la entrada representada por un icono azul.</span><span class="sxs-lookup"><span data-stu-id="05edc-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="05edc-114">Haga clic y arrastre **el objeto prefab PressableButtonHoloLens2** a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="05edc-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="05edc-115">Con el **objeto PressableButtonHoloLens2** aún seleccionado, en la ventana Inspector, configure el componente **Transformar** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="05edc-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="05edc-116">**Position:** X = 0, Y = -0.4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="05edc-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="05edc-117">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="05edc-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="05edc-118">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="05edc-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Transformación de botón](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

<span data-ttu-id="05edc-120">Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **PressableButtonHoloLens2** y, a continuación, acercar ligeramente:</span><span class="sxs-lookup"><span data-stu-id="05edc-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="05edc-121">Comentarios del botón Espacializar</span><span class="sxs-lookup"><span data-stu-id="05edc-121">Spatialize button feedback</span></span>

<span data-ttu-id="05edc-122">En este paso, espacializará los comentarios de audio del botón.</span><span class="sxs-lookup"><span data-stu-id="05edc-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="05edc-123">Para obtener sugerencias de diseño relacionadas, vea [diseño de sonido espacial.](../../../design/spatial-sound-design.md)</span><span class="sxs-lookup"><span data-stu-id="05edc-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="05edc-124">En la ventana **Mezclador de audio,** definirá destinos denominados **Grupos de mezcladores** para la reproducción de audio desde componentes **de origen de** audio.</span><span class="sxs-lookup"><span data-stu-id="05edc-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="05edc-125">Para abrir la ventana **Mezclador de audio,** en el menú de Unity, seleccione **Ventana** Mezclador de audio de  >    >  **audio:** ![ Abrir ventana mezcladora de audio](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="05edc-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span></span>

 <span data-ttu-id="05edc-126">Cree un **mezclador** haciendo clic en "+" junto a **Mezcladores** y escriba un nombre adecuado para el mezclador, por ejemplo, _Mezclador de audio espacial._</span><span class="sxs-lookup"><span data-stu-id="05edc-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="05edc-127">El nuevo mezclador incluirá un grupo **predeterminado denominado** **Maestro.**</span><span class="sxs-lookup"><span data-stu-id="05edc-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Panel mezclador con el primer mezclador](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> <span data-ttu-id="05edc-129">Hasta que se habilita la reverberación en el quinto capítulo: Uso de [la reverberación](unity-spatial-audio-ch5.md)para agregar distancia al audio espacial, el medidor de volumen del mezclador no muestra la actividad de los sonidos que se reproducen a través de Microsoft Spatializer.</span><span class="sxs-lookup"><span data-stu-id="05edc-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="05edc-130">En la ventana Hierarchy (Jerarquía), seleccione **PressableButtonHoloLens2** y, en la ventana Inspector, busque el componente Audio Source (Origen de **audio)** y Configure the Audio Source component (Configurar el componente de origen de audio) como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="05edc-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="05edc-131">En la **propiedad Salida,** haga clic en el selector y elija el **mezclador** que ha creado.</span><span class="sxs-lookup"><span data-stu-id="05edc-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="05edc-132">Active la casilla **Espacializar.**</span><span class="sxs-lookup"><span data-stu-id="05edc-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="05edc-133">Mueva el **control deslizante de Spatial Blend** a 3D (1).</span><span class="sxs-lookup"><span data-stu-id="05edc-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Origen de audio de botón](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="05edc-135">Si mueve **Spatial Blend** a 1 (3D) sin activar la casilla **Spatialize** (Espacializar), Unity usará su espacializador de desplazamiento panorámico, en lugar de **Microsoft Spatializer** con HRFS.</span><span class="sxs-lookup"><span data-stu-id="05edc-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="05edc-136">Ajuste de la curva volumen</span><span class="sxs-lookup"><span data-stu-id="05edc-136">Adjust the Volume curve</span></span>

<span data-ttu-id="05edc-137">De forma predeterminada, Unity atenuará los sonidos espacializados a medida que se alejan más del agente de escucha.</span><span class="sxs-lookup"><span data-stu-id="05edc-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="05edc-138">Cuando esta atenuación se aplica a los sonidos de comentarios de interacción, la interfaz puede ser más difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="05edc-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="05edc-139">Para deshabilitar esta atenuación, debe ajustar la curva **Volumen** en el **componente Origen de** audio.</span><span class="sxs-lookup"><span data-stu-id="05edc-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="05edc-140">En la ventana Hierarchy (Jerarquía), seleccione **PressableButtonHoloLens2** y, en la ventana Inspector, vaya a Audio Source 3D Sound Settings (Configuración de sonido 3D de origen de **audio)** y  >   Configure (Configurar) como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="05edc-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="05edc-141">Establezca la **propiedad Rolloff de** volumen en Linear Rolloff (Reversión lineal).</span><span class="sxs-lookup"><span data-stu-id="05edc-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="05edc-142">Arrastre el punto de conexión **en la curva** Volumen (la curva roja) desde "0" en el eje y hasta "1".</span><span class="sxs-lookup"><span data-stu-id="05edc-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="05edc-143">Para ajustar la forma de la curva **volumen** para que sea plana, arrastre el control de forma de curva blanca para que sea paralelo al eje X.</span><span class="sxs-lookup"><span data-stu-id="05edc-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Configuración de sonido 3D de botón](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="05edc-145">Prueba del audio de espacialización</span><span class="sxs-lookup"><span data-stu-id="05edc-145">Testing the spatialize audio</span></span>

<span data-ttu-id="05edc-146">Para probar el audio de espacialización en el editor de Unity, debe agregar un clip de audio en el componente **Origen** de audio con la opción **Bucle** activada en el objeto **PressableButtonHoloLens2.**</span><span class="sxs-lookup"><span data-stu-id="05edc-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="05edc-147">En el modo de reproducción, mueva el objeto **PressableButtonHoloLens2** de izquierda a derecha y compárelo con y sin audio espacial habilitado en la estación de trabajo.</span><span class="sxs-lookup"><span data-stu-id="05edc-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="05edc-148">También puede cambiar la configuración del origen de audio para las pruebas mediante:</span><span class="sxs-lookup"><span data-stu-id="05edc-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="05edc-149">Mover la **propiedad Spatial Blend** entre 0 y 1 (sonido 2D no espacializado y 3D espacializado)</span><span class="sxs-lookup"><span data-stu-id="05edc-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="05edc-150">Comprobación y desactivación de la **propiedad Spatialize**</span><span class="sxs-lookup"><span data-stu-id="05edc-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="05edc-151">Pruebe la aplicación en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="05edc-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="05edc-152">En la aplicación, puede hacer clic en el botón y escuchar los sonidos de interacción del botón espacializado.</span><span class="sxs-lookup"><span data-stu-id="05edc-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="05edc-153">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="05edc-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="05edc-154">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="05edc-154">Congratulations</span></span>

<span data-ttu-id="05edc-155">En este tutorial ha aprendido a espacializar los sonidos de interacción del botón y a usar un clip de audio para probar la interacción de botones espacializados.</span><span class="sxs-lookup"><span data-stu-id="05edc-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="05edc-156">En el siguiente tutorial aprenderá a espacializar el audio desde un origen de vídeo.</span><span class="sxs-lookup"><span data-stu-id="05edc-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="05edc-157">Tutorial siguiente: 3. Espacialización del audio de un vídeo</span><span class="sxs-lookup"><span data-stu-id="05edc-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
