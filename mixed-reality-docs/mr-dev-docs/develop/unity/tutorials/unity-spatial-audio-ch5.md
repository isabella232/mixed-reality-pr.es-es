---
title: Usar la reverberación para agregar distancia al audio espacial
description: Obtenga información sobre cómo agregar un efecto de reverberación para mejorar el sentido de la variación de distancia al audio espacial en una aplicación de realidad mixta.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer, mezclador de audio, SFX reverberación
ms.openlocfilehash: 6c04ac1e4b52c7eb6104d54c184c789bec413852
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006365"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="9b23e-104">Usar la reverberación para agregar distancia al audio espacial</span><span class="sxs-lookup"><span data-stu-id="9b23e-104">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="9b23e-105">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9b23e-105">Objectives</span></span>

<span data-ttu-id="9b23e-106">En los capítulos anteriores, agregamos la espacialización a los sonidos para darles sentido.</span><span class="sxs-lookup"><span data-stu-id="9b23e-106">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="9b23e-107">En este quinto capítulo, agregaremos un efecto de reverberación para que suene un sentido de distancia.</span><span class="sxs-lookup"><span data-stu-id="9b23e-107">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="9b23e-108">Nuestros objetivos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="9b23e-108">Our objectives are to:</span></span>
* <span data-ttu-id="9b23e-109">Mejorar la distancia de fuentes de sonido percibida mediante la adición de reverberación</span><span class="sxs-lookup"><span data-stu-id="9b23e-109">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="9b23e-110">Controlar la distancia percibida del sonido con la distancia del agente de escucha al holograma</span><span class="sxs-lookup"><span data-stu-id="9b23e-110">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="9b23e-111">Agregar un grupo de mezclador y un efecto de reverberación</span><span class="sxs-lookup"><span data-stu-id="9b23e-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="9b23e-112">En el [capítulo 2](unity-spatial-audio-ch2.md), agregamos un mezclador.</span><span class="sxs-lookup"><span data-stu-id="9b23e-112">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="9b23e-113">El mezclador incluye un **Grupo** de forma predeterminada denominado **maestro**.</span><span class="sxs-lookup"><span data-stu-id="9b23e-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="9b23e-114">Dado que solo deseamos aplicar un efecto de reverberación a algunos sonidos, vamos a agregar un segundo **Grupo** para esos sonidos.</span><span class="sxs-lookup"><span data-stu-id="9b23e-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="9b23e-115">Para agregar un **Grupo**, haga clic con el botón derecho en el grupo **maestro** en el **mezclador de audio** y elija **Agregar grupo secundario**:</span><span class="sxs-lookup"><span data-stu-id="9b23e-115">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![Agregar grupo secundario](images/spatial-audio/add-child-group.png)

<span data-ttu-id="9b23e-117">En este ejemplo, hemos denominado "efecto de sala" al nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="9b23e-117">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="9b23e-118">Cada **Grupo** tiene su propio conjunto de efectos.</span><span class="sxs-lookup"><span data-stu-id="9b23e-118">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="9b23e-119">Agregue un efecto de reverberación al nuevo grupo; para ello, haga clic en **Agregar...** en el nuevo grupo y elija **SFX reverberación**:</span><span class="sxs-lookup"><span data-stu-id="9b23e-119">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Agregar reverberación de SFX](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="9b23e-121">En la terminología de audio, el audio original sin reverberar se denomina _trazado seco_ y el audio después de filtrar con el filtro de reverberación se denomina _ruta húmeda_.</span><span class="sxs-lookup"><span data-stu-id="9b23e-121">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="9b23e-122">Ambas rutas de acceso se envían a la salida de audio y sus puntos fuertes relativos en esta mezcla se denominan _mezcla húmeda/seco_.</span><span class="sxs-lookup"><span data-stu-id="9b23e-122">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="9b23e-123">La mezcla húmeda/seco afecta de una granidad al sentido de la distancia.</span><span class="sxs-lookup"><span data-stu-id="9b23e-123">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="9b23e-124">La **reverberación de SFX** incluye controles para ajustar la mezcla húmeda/seco dentro del efecto.</span><span class="sxs-lookup"><span data-stu-id="9b23e-124">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="9b23e-125">Dado que el complemento **Spatializer de Microsoft** controla el trazado seco, usaremos la **reverberación SFX** solo para el trazado húmedo.</span><span class="sxs-lookup"><span data-stu-id="9b23e-125">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="9b23e-126">En el panel **Inspector** de la **reverberación SFX**:</span><span class="sxs-lookup"><span data-stu-id="9b23e-126">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="9b23e-127">Establezca la propiedad nivel seco en la configuración más baja (-10000 mB)</span><span class="sxs-lookup"><span data-stu-id="9b23e-127">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="9b23e-128">Establezca la propiedad Room en el valor más alto (0 mB)</span><span class="sxs-lookup"><span data-stu-id="9b23e-128">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="9b23e-129">Después de estos cambios, el panel del **Inspector** de la **reverberación SFX** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="9b23e-129">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![Propiedades de reverberación de SFX](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="9b23e-131">Los demás valores controlan el funcionamiento del salón simulado.</span><span class="sxs-lookup"><span data-stu-id="9b23e-131">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="9b23e-132">En concreto, el **tiempo de caída** está relacionado con el tamaño de la sala percibida.</span><span class="sxs-lookup"><span data-stu-id="9b23e-132">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="9b23e-133">Habilitar reverberación en la reproducción de vídeo</span><span class="sxs-lookup"><span data-stu-id="9b23e-133">Enable reverb on the video playback</span></span>

<span data-ttu-id="9b23e-134">Hay dos pasos para habilitar la reverberación en un origen de audio:</span><span class="sxs-lookup"><span data-stu-id="9b23e-134">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="9b23e-135">Enrutar el **origen de audio** al **Grupo** adecuado</span><span class="sxs-lookup"><span data-stu-id="9b23e-135">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="9b23e-136">Establecer el complemento de **Microsoft Spatializer** para pasar el audio al **Grupo** para su procesamiento</span><span class="sxs-lookup"><span data-stu-id="9b23e-136">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="9b23e-137">En los pasos siguientes, ajustaremos el script para controlar el enrutamiento de audio y adjuntaremos un script de control proporcionado con el complemento **Spatializer de Microsoft** para alimentar datos en la reverberación.</span><span class="sxs-lookup"><span data-stu-id="9b23e-137">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="9b23e-138">En el panel **Inspector** del **cuádruple**, haga clic en **Agregar componente** y agregue el script de nivel de envío del efecto de **sala** :</span><span class="sxs-lookup"><span data-stu-id="9b23e-138">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![Agregar script de nivel de envío](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="9b23e-140">A menos que habilite la característica de **nivel de envío de efecto de sala** del complemento Spatializer de **Microsoft** , no enviará ningún audio al motor de audio de Unity para que el procesamiento surta efecto.</span><span class="sxs-lookup"><span data-stu-id="9b23e-140">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="9b23e-141">El componente de **nivel de envío de efecto de sala** incluye un control de gráfico que establece el nivel de audio que se envía al motor de audio de Unity para el procesamiento de reverberación.</span><span class="sxs-lookup"><span data-stu-id="9b23e-141">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="9b23e-142">Haga clic y arrastre la curva hacia abajo para establecer el nivel en about-30dB:</span><span class="sxs-lookup"><span data-stu-id="9b23e-142">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![Ajustar curva de reverberación](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="9b23e-144">A continuación, quite las marcas de comentario de las cuatro líneas comentadas en el script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="9b23e-144">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="9b23e-145">El script tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="9b23e-145">The script will now look like this:</span></span>
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

<span data-ttu-id="9b23e-146">Al quitar los comentarios de estas líneas, se agregan dos propiedades al panel **Inspector** del script.</span><span class="sxs-lookup"><span data-stu-id="9b23e-146">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="9b23e-147">Para establecerlos, en el panel **Inspector** del componente **Spatial ON OFF** de la serie **cuádruple**:</span><span class="sxs-lookup"><span data-stu-id="9b23e-147">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="9b23e-148">Establecer la propiedad de **grupo de efectos de sala** en el nuevo grupo de mezcla de efectos de sala</span><span class="sxs-lookup"><span data-stu-id="9b23e-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="9b23e-149">Establecer la propiedad del **Grupo maestro** en el grupo de mezclador principal</span><span class="sxs-lookup"><span data-stu-id="9b23e-149">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="9b23e-150">Después de estos cambios, las propiedades **de Spatial en OFF** tendrán el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="9b23e-150">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Spatial en OFF extendido](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="9b23e-152">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="9b23e-152">Next steps</span></span>

<span data-ttu-id="9b23e-153">Pruebe la aplicación en HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="9b23e-153">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="9b23e-154">Ahora, cuando toque el botón en la aplicación para activar la espacialización, el script enrutará el audio del vídeo al grupo de efectos de la habitación para agregar la reverberación.</span><span class="sxs-lookup"><span data-stu-id="9b23e-154">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="9b23e-155">Al cambiar a estéreo, enrutará el audio al grupo maestro y evitará que se agregue la reverberación.</span><span class="sxs-lookup"><span data-stu-id="9b23e-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="9b23e-156">Ha completado los tutoriales de audio espacial de HoloLens 2 para Unity.</span><span class="sxs-lookup"><span data-stu-id="9b23e-156">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="9b23e-157">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="9b23e-157">Congratulations!</span></span>


