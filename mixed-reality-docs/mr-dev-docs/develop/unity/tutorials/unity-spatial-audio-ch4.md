---
title: 'Tutoriales de audio espacial: 4. Habilitar y deshabilitar el audio espacial en tiempo de ejecución'
description: Use un botón para habilitar y deshabilitar la espacialización del audio en tiempo de ejecución.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer
ms.openlocfilehash: 2599e2f360afa4518102ab9535608e9d378264ae87f84a36823d460f934d6a05
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213229"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. Habilitación y deshabilitación de la espacialización en tiempo de ejecución

## <a name="overview"></a>Información general

En este tutorial, aprenderá a habilitar y deshabilitar la espacialización en tiempo de ejecución y a probarla en el editor de Unity HoloLens 2.

## <a name="objectives"></a>Objetivos

* Agregar un nuevo script para controlar la espacialización en un objeto de juego
* Controlar el script de control de espacialización a partir de acciones de botón

## <a name="add-spatialization-control-script"></a>Agregar script de control de espacialización

 Haga clic con el botón derecho en la ventana Project y elija Crear script de C# para crear un nuevo script de C#, escriba un nombre adecuado para el script, por  >   ejemplo, _SpatializeOnOff_:

![Creación del script](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

Haga doble clic en el script en Project ventana para abrirlo en Visual Studio. Reemplace el contenido predeterminado del script por lo siguiente:

> [!NOTE]
> Se comentan varias líneas del script. Estas líneas se descomprimirán en [El capítulo siguiente: Uso de reverberación para](unity-spatial-audio-ch5.md)agregar distancia al audio espacial.

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
> Para habilitar o deshabilitar la espacialización, el script solo ajusta la propiedad **spatialBlend** y deja habilitada la propiedad **spatialization.** En este modo, Unity sigue aplicando la **curva volumen.** De lo contrario, si el usuario fuera a deshabilitar la espacialización cuando estuviera lejos del origen, escucharía el aumento brusco del volumen.
> Si prefiere deshabilitar completamente la espacialización, modifique el script para ajustar también la propiedad **booleana de** espacialización de la variable **SourceObject.**

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Adjunte el script y unidades desde el botón

Seleccione **Quad** en la jerarquía y, en la ventana Inspector, use el botón Agregar componente para agregar **SpatializeOnOff(Script)**

![Agregar script a quad](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

En la jerarquía, **busque PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

Con el objeto **Quad** aún seleccionado en la jerarquía, en la ventana Inspector, busque el componente **Spatialize On Off (Script) (Espacializar desactivado [script])** y arrastre y coloque textMeshPro Component (Componente **TextMeshPro)** de PressableButtonHoloLens2.

![Buscar el objeto PressableButtonHoloLens2 en la jerarquía](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

Para establecer el botón para llamar al script **SpatializeOnOff** cuando se libera el botón, debe configurar el script que se puede interactuar.

En la ventana Jerarquía, seleccione **PressableButtonHoloLens2**. En la ventana Inspector, busque el **componente Interactable (Script) y** haga clic en el icono + en el evento OnClick ().

* Con el objeto **PressableButtonHoloLens2** aún seleccionado en la ventana Jerarquía, haga clic y arrastre el objeto **Quad** desde la ventana Jerarquía al campo **Ninguno (objeto)** vacío del evento que acaba de agregar para que el objeto ButtonParent escuche el evento de clic de botón desde este botón:

* Haga clic en la lista desplegable **Ninguna función** del mismo evento. A **continuación, seleccione SpatializeOnOff**  >  **SwapSpatialization () para** activar y desactivar el audio espacial

![Configuración de acción de botón](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a habilitar y deshabilitar la espacialización en tiempo de ejecución, probar la aplicación en un HoloLens 2 o en el editor de Unity. En la aplicación, ahora puede hacer clic en el botón para activar y desactivar la espacialización del audio.

En el siguiente tutorial agregará un efecto de reverberación para dar una idea de la distancia a los sonidos.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Tutorial siguiente: 5. Uso de reverberación para agregar distancia al audio espacial](unity-spatial-audio-ch5.md)
