---
title: 'Tutoriales de audio espacial: 2. Sonidos de interacción del botón de espacialización'
description: Agregue un botón al proyecto y Spatial los sonidos de interacción del botón.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer, Prefabs, curva de volumen
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590767"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="cd1e8-105">2. Sonidos de interacción del botón de espacialización</span><span class="sxs-lookup"><span data-stu-id="cd1e8-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="cd1e8-106">Información general</span><span class="sxs-lookup"><span data-stu-id="cd1e8-106">Overview</span></span>

<span data-ttu-id="cd1e8-107">En este tutorial, obtendrá información sobre cómo espaciale los sonidos de interacción del botón y aprenderá a usar un clip de audio para probar la interacción del botón espacial.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="cd1e8-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cd1e8-108">Objectives</span></span>

* <span data-ttu-id="cd1e8-109">Agregar y espaciales los sonidos de clic del botón</span><span class="sxs-lookup"><span data-stu-id="cd1e8-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="cd1e8-110">Adición de un botón</span><span class="sxs-lookup"><span data-stu-id="cd1e8-110">Add a button</span></span>

<span data-ttu-id="cd1e8-111">Para agregar el botón recurso prefabricado, en la ventana **proyecto** , seleccione **paquetes** y escriba "PressableButtonHoloLens2" en la barra de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Botón recurso prefabricado en activos](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="cd1e8-113">El botón recurso prefabricado es la entrada representada por un icono azul.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="cd1e8-114">Haga clic y arrastre **PressableButtonHoloLens2** recurso prefabricado a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="cd1e8-115">Con el objeto **PressableButtonHoloLens2** aún seleccionado, en la ventana del inspector, configure el componente de **transformación** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="cd1e8-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="cd1e8-116">**Posición**: X = 0, y =-0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="cd1e8-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="cd1e8-117">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cd1e8-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="cd1e8-118">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="cd1e8-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Transformación de botón](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="cd1e8-120">Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **PressableButtonHoloLens2** y, a continuación, hacer zoom ligeramente de nuevo:</span><span class="sxs-lookup"><span data-stu-id="cd1e8-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="cd1e8-121">Comentario del botón de Spatial</span><span class="sxs-lookup"><span data-stu-id="cd1e8-121">Spatialize button feedback</span></span>

<span data-ttu-id="cd1e8-122">En este paso, creará un espacial de los comentarios de audio para el botón.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="cd1e8-123">Para obtener sugerencias de diseño relacionadas, consulte [diseño de sonido espacial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="cd1e8-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="cd1e8-124">En la ventana **mezclador de audio** , definirá destinos denominados grupos de **mezclador** para la reproducción de audio de componentes de origen de **audio** .</span><span class="sxs-lookup"><span data-stu-id="cd1e8-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="cd1e8-125">Para abrir la ventana **mezclador de audio** , en el menú de Unity, seleccione **Windows**  >  **audio**  >  **audio mixer**: ![ abrir la ventana mezclador de audio.](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="cd1e8-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="cd1e8-126">Para crear un **mezclador** , haga clic en el "+" junto a **mixers** y escriba un nombre adecuado para el mezclador, por ejemplo, _mezclador de audio espacial_.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="cd1e8-127">El nuevo mezclador incluirá un **Grupo** predeterminado denominado **maestro**.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Panel de mezclador con el primer mezclador](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="cd1e8-129">Hasta que se habilita la reverberación en el [quinto capítulo: usar reverberación para agregar distancia al audio espacial](unity-spatial-audio-ch5.md), el medidor de volumen del mezclador no muestra la actividad de los sonidos que se reproducen a través de Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="cd1e8-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="cd1e8-130">En la ventana jerarquía, seleccione **PressableButtonHoloLens2** en la ventana del inspector busque el componente **origen de audio** y configure el componente origen de audio como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="cd1e8-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="cd1e8-131">En la propiedad **salida** , haga clic en el selector y elija el **mezclador** que creó.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="cd1e8-132">Active la casilla **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="cd1e8-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="cd1e8-133">Mueva el control deslizante de **mezcla espacial** a 3D (1).</span><span class="sxs-lookup"><span data-stu-id="cd1e8-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Origen de audio de botón](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="cd1e8-135">Si mueve la **mezcla espacial** a 1 (3D) sin activar la casilla **Spatial** , Unity usará su spatializer de movimiento panorámico, en lugar de **spatializer de Microsoft** con HRTFs.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="cd1e8-136">Ajustar la curva del volumen</span><span class="sxs-lookup"><span data-stu-id="cd1e8-136">Adjust the Volume curve</span></span>

<span data-ttu-id="cd1e8-137">De forma predeterminada, Unity atenúa los sonidos espaciales a medida que se alejan del agente de escucha.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="cd1e8-138">Cuando se aplica esta atenuación a los sonidos de interacción, la interfaz puede resultar más difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="cd1e8-139">Para deshabilitar esta atenuación, debe ajustar la curva del **volumen** en el componente **origen de audio** .</span><span class="sxs-lookup"><span data-stu-id="cd1e8-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="cd1e8-140">En la ventana de jerarquía, seleccione el **PressableButtonHoloLens2** y, a continuación, en la ventana del inspector, navegue hasta configuración de sonido 3D de **origen de audio**  >   y configure de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="cd1e8-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="cd1e8-141">Establezca la propiedad **Volume rolloff** en rolloff lineal</span><span class="sxs-lookup"><span data-stu-id="cd1e8-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="cd1e8-142">Arrastre el punto de conexión en la curva de **volumen** (la curva roja) desde ' 0 ' en el eje y hasta ' 1 '</span><span class="sxs-lookup"><span data-stu-id="cd1e8-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="cd1e8-143">Para ajustar la forma de la curva de **volumen** para que sea plana, arrastre el control de forma de curva blanca para que sea paralelo al eje X.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Configuración de sonido 3D del botón](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="cd1e8-145">Prueba del audio espacial</span><span class="sxs-lookup"><span data-stu-id="cd1e8-145">Testing the spatialize audio</span></span>

<span data-ttu-id="cd1e8-146">Para probar el audio espacial en el editor de Unity, tiene que agregar un clip de audio en la opción componente de **origen de audio** with **Loop** activada en el objeto **PressableButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="cd1e8-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="cd1e8-147">En el modo de reproducción, mueva el objeto **PressableButtonHoloLens2** de izquierda a derecha y compare con y sin el audio espacial habilitado en la estación de trabajo.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="cd1e8-148">También puede cambiar la configuración de origen de audio para realizar pruebas:</span><span class="sxs-lookup"><span data-stu-id="cd1e8-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="cd1e8-149">Movimiento de la propiedad de **Blend espacial** entre 0-1 (sonido en 2D no espacial y 3D)</span><span class="sxs-lookup"><span data-stu-id="cd1e8-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="cd1e8-150">Activar y desactivar la propiedad **Spatial**</span><span class="sxs-lookup"><span data-stu-id="cd1e8-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="cd1e8-151">Pruebe la aplicación en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="cd1e8-152">En la aplicación, puede hacer clic en el botón y oír los sonidos de interacción del botón espacial.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="cd1e8-153">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="cd1e8-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="cd1e8-154">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="cd1e8-154">Congratulations</span></span>

<span data-ttu-id="cd1e8-155">En este tutorial, ha aprendido a espaciales los sonidos de interacción del botón y a usar un clip de audio para probar la interacción de los botones espaciales.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="cd1e8-156">En el siguiente tutorial aprenderá a encargar el audio de un origen de vídeo.</span><span class="sxs-lookup"><span data-stu-id="cd1e8-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cd1e8-157">Siguiente tutorial: 3. espacialización de audio desde un vídeo</span><span class="sxs-lookup"><span data-stu-id="cd1e8-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
