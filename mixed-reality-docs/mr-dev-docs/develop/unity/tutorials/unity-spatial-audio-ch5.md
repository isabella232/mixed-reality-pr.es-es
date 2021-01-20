---
title: 'Tutoriales de audio espacial: 5. Usar la reverberación para agregar distancia al audio espacial'
description: Agregue un efecto de reverberación para mejorar el sentido de la variación de distancia al audio espacial.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer, mezclador de audio, SFX reverberación
ms.openlocfilehash: 3d19bb0b22c507eb692a752aa318ecb82a1cf2f7
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578386"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="612ed-105">5. Usar la reverberación para agregar distancia al audio espacial</span><span class="sxs-lookup"><span data-stu-id="612ed-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="612ed-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="612ed-106">Overview</span></span>

<span data-ttu-id="612ed-107">En el tutorial anterior, ha agregado la espacialización de los sonidos para darles una idea de la dirección de este tutorial, agregará un efecto de reverberación para que suene un sentido de distancia.</span><span class="sxs-lookup"><span data-stu-id="612ed-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="612ed-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="612ed-108">Objectives</span></span>

* <span data-ttu-id="612ed-109">Mejore la distancia de los orígenes de sonido percibidos agregando reverberación.</span><span class="sxs-lookup"><span data-stu-id="612ed-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="612ed-110">Controle la distancia percibida del sonido con la distancia del agente de escucha al holograma.</span><span class="sxs-lookup"><span data-stu-id="612ed-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="612ed-111">Agregar un grupo de mezclador y un efecto de reverberación</span><span class="sxs-lookup"><span data-stu-id="612ed-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="612ed-112">En el tutorial de la interacción del botón de la [interactuación](unity-spatial-audio-ch2.md), hemos agregado un mezclador.</span><span class="sxs-lookup"><span data-stu-id="612ed-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="612ed-113">El mezclador incluye un **Grupo** de forma predeterminada denominado **maestro**.</span><span class="sxs-lookup"><span data-stu-id="612ed-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="612ed-114">Dado que solo deseamos aplicar un efecto de reverberación a algunos sonidos, vamos a agregar un segundo grupo para esos sonidos.</span><span class="sxs-lookup"><span data-stu-id="612ed-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="612ed-115">Para agregar un grupo, haga clic con el botón derecho en el grupo maestro del **mezclador de audio** y elija **Agregar grupo secundario** y proporcione un nombre adecuado para el ejemplo de _efecto de sala_:</span><span class="sxs-lookup"><span data-stu-id="612ed-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Agregar grupo secundario](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="612ed-117">Cada **Grupo** tiene su propio conjunto de efectos.</span><span class="sxs-lookup"><span data-stu-id="612ed-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="612ed-118">Agregue un efecto de reverberación al nuevo grupo; para ello, haga clic en **Agregar...** en el nuevo grupo y elija **SFX reverberación**:</span><span class="sxs-lookup"><span data-stu-id="612ed-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Agregar reverberación de SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="612ed-120">En la terminología de audio, el audio original sin reverberar se denomina _trazado seco_ y el audio después de filtrar con el filtro de reverberación se denomina _ruta húmeda_.</span><span class="sxs-lookup"><span data-stu-id="612ed-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="612ed-121">Ambas rutas de acceso se envían a la salida de audio y sus puntos fuertes relativos en esta mezcla se denominan _mezcla húmeda/seco_.</span><span class="sxs-lookup"><span data-stu-id="612ed-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="612ed-122">La mezcla húmeda/seco afecta de una granidad al sentido de la distancia.</span><span class="sxs-lookup"><span data-stu-id="612ed-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="612ed-123">La **reverberación de SFX** incluye controles para ajustar la mezcla húmeda/seco dentro del efecto.</span><span class="sxs-lookup"><span data-stu-id="612ed-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="612ed-124">Dado que el complemento **Spatializer de Microsoft** controla el trazado seco, usaremos la **reverberación SFX** solo para el trazado húmedo.</span><span class="sxs-lookup"><span data-stu-id="612ed-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="612ed-125">En el panel Inspector de la **reverberación SFX**:</span><span class="sxs-lookup"><span data-stu-id="612ed-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="612ed-126">Establezca la propiedad **nivel seco** en la configuración más baja (-10000 MB)</span><span class="sxs-lookup"><span data-stu-id="612ed-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="612ed-127">Establezca la **propiedad Room** en el valor más alto (0 MB)</span><span class="sxs-lookup"><span data-stu-id="612ed-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![Propiedades de reverberación de SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="612ed-129">Los demás valores controlan el funcionamiento del salón simulado.</span><span class="sxs-lookup"><span data-stu-id="612ed-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="612ed-130">En concreto, el **tiempo de caída** está relacionado con el tamaño de la sala percibida.</span><span class="sxs-lookup"><span data-stu-id="612ed-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="612ed-131">Habilitar reverberación en la reproducción de vídeo</span><span class="sxs-lookup"><span data-stu-id="612ed-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="612ed-132">Hay dos pasos para habilitar la reverberación en un origen de audio:</span><span class="sxs-lookup"><span data-stu-id="612ed-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="612ed-133">Enrutar el **origen de audio** al **Grupo** adecuado</span><span class="sxs-lookup"><span data-stu-id="612ed-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="612ed-134">Establecer el complemento de **Microsoft Spatializer** para pasar el audio al **Grupo** para su procesamiento</span><span class="sxs-lookup"><span data-stu-id="612ed-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="612ed-135">En los pasos siguientes, ajustará el script para controlar el enrutamiento de audio y adjuntará un script de control proporcionado con el complemento **Spatializer de Microsoft** para alimentar datos en la reverberación.</span><span class="sxs-lookup"><span data-stu-id="612ed-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="612ed-136">Con el **cuádruple** seleccionado en la jerarquía, haga clic en **Agregar componente** en la ventana del inspector y agregue el **nivel de envío (Script) del efecto de sala**:</span><span class="sxs-lookup"><span data-stu-id="612ed-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Agregar script de nivel de envío](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="612ed-138">A menos que habilite la característica de **nivel de envío de efecto de sala** del complemento Spatializer de **Microsoft** , no enviará ningún audio al motor de audio de Unity para que el procesamiento surta efecto.</span><span class="sxs-lookup"><span data-stu-id="612ed-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="612ed-139">El componente de **nivel de envío de efecto de sala** incluye un control de gráfico que establece el nivel de audio que se envía al motor de audio de Unity para el procesamiento de reverberación.</span><span class="sxs-lookup"><span data-stu-id="612ed-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="612ed-140">Para abrir el control de gráfico, haga clic en el **nivel de envío del efecto de sala**.</span><span class="sxs-lookup"><span data-stu-id="612ed-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="612ed-141">Haga clic y arrastre la curva verde hacia abajo para establecer el nivel en about-30dB:</span><span class="sxs-lookup"><span data-stu-id="612ed-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Ajustar curva de reverberación](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="612ed-143">A continuación, quite las marcas de comentario de las cuatro líneas comentadas en el script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="612ed-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="612ed-144">El script tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="612ed-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="612ed-145">Una vez que se quitan los comentarios de estas líneas, se agregan dos propiedades al inspector del **script SpatializeOnOff**.</span><span class="sxs-lookup"><span data-stu-id="612ed-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="612ed-146">asígnelos en la ventana del inspector del componente **SpatializeOnOff** de la **cuádruple**.</span><span class="sxs-lookup"><span data-stu-id="612ed-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="612ed-147">Con el objeto cuádruple todavía seleccionado en la jerarquía, en la ventana del inspector, busque el componente de **script SpatializeOnOff** y:</span><span class="sxs-lookup"><span data-stu-id="612ed-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="612ed-148">Establecer la propiedad de **grupo de efectos de sala** en el nuevo grupo de mezcla de efectos de sala</span><span class="sxs-lookup"><span data-stu-id="612ed-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="612ed-149">Establecer la propiedad del **Grupo maestro** en el grupo de mezclador principal</span><span class="sxs-lookup"><span data-stu-id="612ed-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatial en OFF extendido](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="612ed-151">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="612ed-151">Congratulations</span></span>

<span data-ttu-id="612ed-152">Ha completado los tutoriales de audio espacial de HoloLens 2 para Unity.</span><span class="sxs-lookup"><span data-stu-id="612ed-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="612ed-153">Pruebe la aplicación en HoloLens 2 o Unity.</span><span class="sxs-lookup"><span data-stu-id="612ed-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="612ed-154">Al hacer clic en el botón de la aplicación para activar la espacialización, el script enrutará el audio del vídeo al grupo de efectos de la habitación para agregar la reverberación.</span><span class="sxs-lookup"><span data-stu-id="612ed-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="612ed-155">Al cambiar a estéreo, enrutará el audio al grupo maestro y evitará que se agregue la reverberación.</span><span class="sxs-lookup"><span data-stu-id="612ed-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="612ed-156">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="612ed-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
