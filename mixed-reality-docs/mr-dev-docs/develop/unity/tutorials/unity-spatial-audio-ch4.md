---
title: 'Tutoriales de audio espacial: 4. Habilitar y deshabilitar el audio espacial en tiempo de ejecución'
description: Use un botón para habilitar y deshabilitar la espacialización del audio en tiempo de ejecución.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712760"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="55c2d-105">4. Habilitación y deshabilitación de la espacialización en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="55c2d-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="55c2d-106">Información general</span><span class="sxs-lookup"><span data-stu-id="55c2d-106">Overview</span></span>

<span data-ttu-id="55c2d-107">En este tutorial, aprenderá a habilitar y deshabilitar la espacialización en tiempo de ejecución y a probarlo en el editor de Unity HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="55c2d-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="55c2d-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="55c2d-108">Objectives</span></span>

* <span data-ttu-id="55c2d-109">Agregar un nuevo script para controlar la espacialización en un objeto de juego</span><span class="sxs-lookup"><span data-stu-id="55c2d-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="55c2d-110">Controlar el script de control de espacialización a partir de acciones de botón</span><span class="sxs-lookup"><span data-stu-id="55c2d-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="55c2d-111">Agregar script de control de espacialización</span><span class="sxs-lookup"><span data-stu-id="55c2d-111">Add spatialization control script</span></span>

 <span data-ttu-id="55c2d-112">Haga clic con el botón derecho en la ventana Proyecto y elija Crear script de C# para crear un nuevo script de C#, escriba un nombre adecuado para el script, por  >   ejemplo, _SpatializeOnOff_:</span><span class="sxs-lookup"><span data-stu-id="55c2d-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Creación del script](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

<span data-ttu-id="55c2d-114">Haga doble clic en el script en la ventana Proyecto para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55c2d-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="55c2d-115">Reemplace el contenido predeterminado del script por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="55c2d-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="55c2d-116">Se comentan varias líneas del script. Estas líneas se descomprimirán en [El capítulo siguiente: Uso de reverberación para](unity-spatial-audio-ch5.md)agregar distancia al audio espacial.</span><span class="sxs-lookup"><span data-stu-id="55c2d-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="55c2d-117">Para habilitar o deshabilitar la espacialización, el script solo ajusta la propiedad **spatialBlend** y deja habilitada la propiedad **de** espacialización.</span><span class="sxs-lookup"><span data-stu-id="55c2d-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="55c2d-118">En este modo, Unity sigue aplicando la curva **volumen.**</span><span class="sxs-lookup"><span data-stu-id="55c2d-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="55c2d-119">De lo contrario, si el usuario fuera a deshabilitar la espacialización cuando estuviera lejos del origen, escucharía el aumento brusco del volumen.</span><span class="sxs-lookup"><span data-stu-id="55c2d-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="55c2d-120">Si prefiere deshabilitar completamente la espacialización, modifique el script para ajustar también la propiedad **booleana de** espacialización de la variable **SourceObject.**</span><span class="sxs-lookup"><span data-stu-id="55c2d-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="55c2d-121">Adjunte el script y unidades desde el botón</span><span class="sxs-lookup"><span data-stu-id="55c2d-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="55c2d-122">Seleccione **Quad** en la jerarquía y, en la ventana Inspector, use el botón Agregar componente para agregar **SpatializeOnOff(Script)**</span><span class="sxs-lookup"><span data-stu-id="55c2d-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Agregar script a quad](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

<span data-ttu-id="55c2d-124">En la jerarquía, **busque PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.</span><span class="sxs-lookup"><span data-stu-id="55c2d-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="55c2d-125">Con el objeto **Quad** aún seleccionado en la jerarquía, en la ventana Inspector, busque el componente **Spatialize On Off (Script) (Espacializar desactivado [script])** y arrastre y coloque textMeshPro Component (Componente **TextMeshPro)** de PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="55c2d-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Buscar el objeto PressableButtonHoloLens2 en la jerarquía](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

<span data-ttu-id="55c2d-127">Para establecer el botón para llamar al script **SpatializeOnOff** cuando se libera el botón, debe configurar el script que se puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="55c2d-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="55c2d-128">En la ventana Jerarquía, seleccione **PressableButtonHoloLens2**.</span><span class="sxs-lookup"><span data-stu-id="55c2d-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="55c2d-129">En la ventana Inspector, busque el **componente Interactable (Script) y** haga clic en el icono + en el evento OnClick ().</span><span class="sxs-lookup"><span data-stu-id="55c2d-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="55c2d-130">Con el objeto **PressableButtonHoloLens2** aún seleccionado en la ventana Jerarquía, haga clic y arrastre el objeto **Quad** desde la ventana Jerarquía al campo **Ninguno (objeto)** vacío del evento que acaba de agregar para que el objeto ButtonParent escuche el evento de clic de botón desde este botón:</span><span class="sxs-lookup"><span data-stu-id="55c2d-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="55c2d-131">Haga clic en la lista desplegable **Ninguna función** del mismo evento.</span><span class="sxs-lookup"><span data-stu-id="55c2d-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="55c2d-132">A continuación, **seleccione SpatializeOnOff**  >  **SwapSpatialization () para** activar y desactivar el audio espacial.</span><span class="sxs-lookup"><span data-stu-id="55c2d-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Configuración de la acción de botón](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="55c2d-134">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="55c2d-134">Congratulations</span></span>

<span data-ttu-id="55c2d-135">En este tutorial, ha aprendido a habilitar y deshabilitar la espacialización en tiempo de ejecución, probar la aplicación en un HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="55c2d-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="55c2d-136">En la aplicación, ahora puede hacer clic en el botón para activar y desactivar la espacialización del audio.</span><span class="sxs-lookup"><span data-stu-id="55c2d-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="55c2d-137">En el siguiente tutorial agregará un efecto de reverberación para dar una sensación de distancia a los sonidos.</span><span class="sxs-lookup"><span data-stu-id="55c2d-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="55c2d-138">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="55c2d-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55c2d-139">Tutorial siguiente: 5. Uso de reverberación para agregar distancia al audio espacial</span><span class="sxs-lookup"><span data-stu-id="55c2d-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
