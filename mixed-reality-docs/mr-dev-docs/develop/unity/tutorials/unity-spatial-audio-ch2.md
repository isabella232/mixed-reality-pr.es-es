---
title: Sonidos de interacción del botón de espacialización
description: Obtenga información sobre cómo agregar un botón y cómo espaciale los sonidos de interacción del botón en una aplicación de realidad mixta.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer, Prefabs, curva de volumen
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007365"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="66c07-104">Sonidos de interacción del botón de espacialización</span><span class="sxs-lookup"><span data-stu-id="66c07-104">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="66c07-105">Objetivos</span><span class="sxs-lookup"><span data-stu-id="66c07-105">Objectives</span></span>

<span data-ttu-id="66c07-106">En este segundo capítulo del módulo de audio espacial de los tutoriales de HoloLens 2, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="66c07-106">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="66c07-107">Adición de un botón</span><span class="sxs-lookup"><span data-stu-id="66c07-107">Add a button</span></span>
* <span data-ttu-id="66c07-108">Spatial los sonidos del clic del botón</span><span class="sxs-lookup"><span data-stu-id="66c07-108">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="66c07-109">Adición de un botón</span><span class="sxs-lookup"><span data-stu-id="66c07-109">Add a button</span></span>

<span data-ttu-id="66c07-110">En el panel **proyecto** , seleccione **recursos** y escriba "PressableButtonHoloLens2" en la barra de búsqueda:</span><span class="sxs-lookup"><span data-stu-id="66c07-110">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Botón recurso prefabricado en activos](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="66c07-112">El botón recurso prefabricado es la entrada representada por un icono azul, en lugar de un icono blanco.</span><span class="sxs-lookup"><span data-stu-id="66c07-112">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="66c07-113">Arrastre recurso prefabricado con el nombre **PressableButtonHoloLens2** al panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="66c07-113">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="66c07-114">En el panel **Inspector** del nuevo botón, establezca la propiedad **Position** en (0,-0,4, 2) para que aparezca delante del usuario cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="66c07-114">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="66c07-115">El componente de **transformación** del botón tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="66c07-115">The **Transform** component of the button will look like this:</span></span>

![Transformación de botón](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="66c07-117">Comentario del botón de Spatial</span><span class="sxs-lookup"><span data-stu-id="66c07-117">Spatialize button feedback</span></span>

<span data-ttu-id="66c07-118">En este paso, creará un espacial de los comentarios de audio para el botón.</span><span class="sxs-lookup"><span data-stu-id="66c07-118">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="66c07-119">Para obtener sugerencias de diseño relacionadas, consulte [diseño de sonido espacial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="66c07-119">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="66c07-120">El panel **mezclador de audio** permite definir destinos, denominados grupos de **mezclador**, para la reproducción de audio de componentes de origen de **audio** .</span><span class="sxs-lookup"><span data-stu-id="66c07-120">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="66c07-121">Abra el panel del **mezclador de audio** en la barra de menús con el **mezclador de audio > audio-> de Windows**</span><span class="sxs-lookup"><span data-stu-id="66c07-121">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="66c07-122">Para crear un **mezclador** , haga clic en el "+" junto a **mixers**.</span><span class="sxs-lookup"><span data-stu-id="66c07-122">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="66c07-123">El nuevo mezclador incluirá un **Grupo** predeterminado denominado **maestro**.</span><span class="sxs-lookup"><span data-stu-id="66c07-123">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="66c07-124">El panel del **mezclador** tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="66c07-124">Your **Mixer** pane will now look like this:</span></span>

![Panel de mezclador con el primer mezclador](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="66c07-126">Hasta que se habilita la reverberación en el [capítulo 5](unity-spatial-audio-ch5.md), el medidor de volumen del mezclador no muestra la actividad de los sonidos que se reproducen a través de Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="66c07-126">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="66c07-127">Haga clic en **PressableButtonHoloLens2** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="66c07-127">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="66c07-128">En el panel **Inspector** :</span><span class="sxs-lookup"><span data-stu-id="66c07-128">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="66c07-129">Buscar el componente de **origen de audio**</span><span class="sxs-lookup"><span data-stu-id="66c07-129">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="66c07-130">En la propiedad **salida** , haga clic en el selector y elija el mezclador.</span><span class="sxs-lookup"><span data-stu-id="66c07-130">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="66c07-131">Active la casilla **Spatial**</span><span class="sxs-lookup"><span data-stu-id="66c07-131">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="66c07-132">Mueva el control deslizante de **mezcla espacial** a 3D (1).</span><span class="sxs-lookup"><span data-stu-id="66c07-132">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="66c07-133">En las versiones de Unity anteriores a 2019, la casilla ' Spatial ' está en la parte inferior del panel del **Inspector** para el **origen de audio**.</span><span class="sxs-lookup"><span data-stu-id="66c07-133">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="66c07-134">Después de estos cambios, el componente de **origen de audio** de su **PressableButtonHoloLens2** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="66c07-134">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Origen de audio de botón](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="66c07-136">Si mueve la **mezcla espacial** a 1 (3D) sin activar la casilla **Spatial** , Unity usará su spatializer de movimiento panorámico, en lugar de **spatializer de Microsoft** con HRTFs.</span><span class="sxs-lookup"><span data-stu-id="66c07-136">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="66c07-137">Ajustar la curva del volumen</span><span class="sxs-lookup"><span data-stu-id="66c07-137">Adjust the Volume curve</span></span>

<span data-ttu-id="66c07-138">De forma predeterminada, Unity atenúa los sonidos espaciales a medida que se alejan del agente de escucha.</span><span class="sxs-lookup"><span data-stu-id="66c07-138">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="66c07-139">Cuando se aplica esta atenuación a los sonidos de interacción, la interfaz puede resultar más difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="66c07-139">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="66c07-140">Para deshabilitar esta atenuación, ajuste la curva del **volumen** .</span><span class="sxs-lookup"><span data-stu-id="66c07-140">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="66c07-141">En el componente **origen de audio** del panel **Inspector** de **PressableButtonHoloLens2**, hay una sección denominada configuración de **sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="66c07-141">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="66c07-142">En esa sección:</span><span class="sxs-lookup"><span data-stu-id="66c07-142">In that section:</span></span>
1. <span data-ttu-id="66c07-143">Establezca la propiedad **Volume rolloff** en lineal.</span><span class="sxs-lookup"><span data-stu-id="66c07-143">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="66c07-144">Arrastre el punto de conexión en la curva de **volumen** (la curva roja) desde ' 0 ' en el eje y hasta ' 1 '</span><span class="sxs-lookup"><span data-stu-id="66c07-144">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="66c07-145">Para ajustar la forma de la curva de **volumen** para que sea plana, arrastre el control de forma de curva blanca para que sea paralelo al eje X.</span><span class="sxs-lookup"><span data-stu-id="66c07-145">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="66c07-146">Después de estos cambios, la sección **configuración de sonido 3D** de las propiedades de **origen de audio** del **PressableButtonHoloLens2** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="66c07-146">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Configuración de sonido 3D del botón](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="66c07-148">Prueba del audio espacial</span><span class="sxs-lookup"><span data-stu-id="66c07-148">Testing the spatialize audio</span></span>

<span data-ttu-id="66c07-149">No dude en probar los nuevos sonidos de interacción del botón espacial:</span><span class="sxs-lookup"><span data-stu-id="66c07-149">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="66c07-150">Entrar en el modo de juego en el editor de Unity, idealmente con una muestra de audio en bucle en la escena</span><span class="sxs-lookup"><span data-stu-id="66c07-150">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="66c07-151">Mueva el objeto con el origen de audio de izquierda a derecha y compare con y sin el audio espacial habilitado.</span><span class="sxs-lookup"><span data-stu-id="66c07-151">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="66c07-152">Puede cambiar la configuración de origen de audio para realizar pruebas por:</span><span class="sxs-lookup"><span data-stu-id="66c07-152">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="66c07-153">Movimiento de la propiedad de Blend espacial entre 0-1 (sonido en 2D no espacial y 3D)</span><span class="sxs-lookup"><span data-stu-id="66c07-153">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="66c07-154">Activar y desactivar la propiedad Spatial</span><span class="sxs-lookup"><span data-stu-id="66c07-154">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="66c07-155">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="66c07-155">Next steps</span></span>

<span data-ttu-id="66c07-156">Pruebe la aplicación en HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="66c07-156">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="66c07-157">En la aplicación, puede tocar el botón y oír los sonidos de interacción del botón espacial.</span><span class="sxs-lookup"><span data-stu-id="66c07-157">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="66c07-158">Al realizar pruebas en el editor de Unity, presione la barra espaciadora y desplácese con la rueda de desplazamiento para activar la simulación de mano.</span><span class="sxs-lookup"><span data-stu-id="66c07-158">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="66c07-159">Para obtener más información, consulte la [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="66c07-159">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66c07-160">Capítulo 3</span><span class="sxs-lookup"><span data-stu-id="66c07-160">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

