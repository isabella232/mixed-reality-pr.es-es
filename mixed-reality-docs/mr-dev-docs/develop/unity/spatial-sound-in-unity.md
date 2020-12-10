---
title: Sonido espacial en Unity
description: Reproducir sonido espacial desde un punto 3D específico dentro de la escena de Unity.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta, spatializer, reverberación
ms.openlocfilehash: 1efe287855cc5b7738069c6d8183c2ecb5bd6d59
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010146"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="2e9fc-104">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="2e9fc-104">Spatial sound in Unity</span></span>

<span data-ttu-id="2e9fc-105">Esta página contiene vínculos a recursos de sonido espacial en Unity.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="2e9fc-106">Opciones de Spatializer</span><span class="sxs-lookup"><span data-stu-id="2e9fc-106">Spatializer options</span></span>
<span data-ttu-id="2e9fc-107">Las opciones de Spatializer para aplicaciones de realidad mixta incluyen:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="2e9fc-108">Unity proporciona el *MS HRTF Spatializer* como parte del paquete opcional de *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="2e9fc-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="2e9fc-109">Se ejecuta en la CPU en una arquitectura de "origen único" de mayor costo.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="2e9fc-110">Se proporciona para la compatibilidad con versiones anteriores con las aplicaciones de HoloLens originales.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="2e9fc-111">*Microsoft Spatializer* está disponible en el [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="2e9fc-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="2e9fc-112">Usa una arquitectura de "varios orígenes" de menor costo.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="2e9fc-113">Descargado en un acelerador de hardware de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="2e9fc-114">En el caso de las nuevas aplicaciones, se recomienda *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="2e9fc-115">Habilitar la espacialización</span><span class="sxs-lookup"><span data-stu-id="2e9fc-115">Enable spatialization</span></span>

<span data-ttu-id="2e9fc-116">Use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ y elija **Microsoft Spatializer** en la configuración de audio del proyecto.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="2e9fc-117">Después:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-117">Then:</span></span>
* <span data-ttu-id="2e9fc-118">Adjuntar un **origen de audio** a un objeto de la jerarquía</span><span class="sxs-lookup"><span data-stu-id="2e9fc-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="2e9fc-119">Active la casilla **Habilitar la espacialización**</span><span class="sxs-lookup"><span data-stu-id="2e9fc-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="2e9fc-120">Mueve el control deslizante de **mezcla espacial** a ' 1 '</span><span class="sxs-lookup"><span data-stu-id="2e9fc-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="2e9fc-121">Asegúrese de que el audio espacial está habilitado en la estación de trabajo del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="2e9fc-122">Haga clic con el botón derecho en el icono de volumen en la barra de tareas y asegúrese de que el sonido espacial esté establecido en un valor distinto de "desactivado".</span><span class="sxs-lookup"><span data-stu-id="2e9fc-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="2e9fc-123">Elija **Windows Sonic para auriculares** para obtener la mejor representación de lo que escuchará en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="2e9fc-124">Si se produce un error en Unity al no poder cargar el complemento Microsoft. SpatialAudio. Spatializer. Unity porque falta una de sus dependencias, compruebe que dispone de la versión más reciente del [Microsoft Visual C++ redistribuible](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalada en su equipo.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="2e9fc-125">Para más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-125">For more information, see:</span></span>
* [<span data-ttu-id="2e9fc-126">Repositorio de GitHub de Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="2e9fc-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="2e9fc-127">Tutorial de spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="2e9fc-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="2e9fc-128">Documentación del origen de audio de Unity</span><span class="sxs-lookup"><span data-stu-id="2e9fc-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="2e9fc-129">Documentación de spatializer de Unity</span><span class="sxs-lookup"><span data-stu-id="2e9fc-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="2e9fc-130">Atenuación basada en la distancia</span><span class="sxs-lookup"><span data-stu-id="2e9fc-130">Distance-based attenuation</span></span>
<span data-ttu-id="2e9fc-131">La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con una rolloff logarítmica.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="2e9fc-132">Es posible que esta configuración funcione para su escenario, o puede que los orígenes se expongan demasiado rápido o demasiado lentamente.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="2e9fc-133">Para más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-133">For more information, see:</span></span>
* <span data-ttu-id="2e9fc-134">[Diseño sonoro en la realidad mixta](../../design/spatial-sound-design.md) para la configuración recomendada.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="2e9fc-135">[Documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obtener instrucciones sobre cómo establecer estas curvas.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="2e9fc-136">Reverbera</span><span class="sxs-lookup"><span data-stu-id="2e9fc-136">Reverb</span></span>
<span data-ttu-id="2e9fc-137">De forma predeterminada, el _Spatializer de Microsoft_ deshabilita los efectos posteriores a Spatializer.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="2e9fc-138">Para habilitar la reverberación y otros efectos para los orígenes espaciales:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="2e9fc-139">Asociar el componente de **nivel de envío del efecto de sala** a cada origen</span><span class="sxs-lookup"><span data-stu-id="2e9fc-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="2e9fc-140">Ajuste la curva de nivel de envío de cada origen para controlar la ganancia del audio que se devuelve al gráfico para el procesamiento de efectos</span><span class="sxs-lookup"><span data-stu-id="2e9fc-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="2e9fc-141">Consulte [el capítulo 5 del tutorial de spatializer](tutorials/unity-spatial-audio-ch5.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="2e9fc-142">Ejemplos de sonido espacial de Unity</span><span class="sxs-lookup"><span data-stu-id="2e9fc-142">Unity spatial sound examples</span></span>
<span data-ttu-id="2e9fc-143">Para ver ejemplos de sonido espacial en Unity, consulte:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="2e9fc-144">Demostraciones de MRTK</span><span class="sxs-lookup"><span data-stu-id="2e9fc-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="2e9fc-145">[Proyecto de ejemplo de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="2e9fc-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2e9fc-146">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="2e9fc-146">Next Development Checkpoint</span></span>

<span data-ttu-id="2e9fc-147">Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="2e9fc-148">Desde aquí, puede continuar con el siguiente bloque de creación:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e9fc-149">Texto</span><span class="sxs-lookup"><span data-stu-id="2e9fc-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="2e9fc-150">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="2e9fc-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e9fc-151">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="2e9fc-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="2e9fc-152">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="2e9fc-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e9fc-153">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e9fc-153">See also</span></span>
* [<span data-ttu-id="2e9fc-154">Diseño sonoro en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="2e9fc-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="2e9fc-155">Tutorial de spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="2e9fc-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
