---
title: 'Tutoriales de audio espacial: 4. Habilitar y deshabilitar el audio espacial en tiempo de ejecución'
description: Use un botón para habilitar y deshabilitar la espacialización del audio en tiempo de ejecución.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer
ms.openlocfilehash: 26143975707b2cd6141803a6335cec89db5bbd26
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590737"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. habilitar y deshabilitar la espacialización en tiempo de ejecución

## <a name="overview"></a>Información general

En este tutorial, obtendrá información sobre cómo habilitar y deshabilitar la espacialización en tiempo de ejecución y probarlo en el editor de Unity y en HoloLens 2.

## <a name="objectives"></a>Objetivos

* Agregar un nuevo script para controlar la espacialización en un objeto de juego
* Controlar el script de control de la espacialización desde acciones de botón

## <a name="add-spatialization-control-script"></a>Agregar script de control de espacialización

 Haga clic con el botón derecho en la ventana del proyecto y elija **crear**  >  **script de c#** para crear un nuevo script de c#, escriba un nombre adecuado para el script, por ejemplo, _SpatializeOnOff_:

![Creación del script](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

Haga doble clic en el script en la ventana del proyecto para abrirlo en Visual Studio. Reemplace el contenido del script predeterminado por lo siguiente:

> [!NOTE]
> Se comentan varias líneas del script. En el siguiente capítulo se quitarán los comentarios de estas líneas [: usar reverberación para agregar distancia al audio espacial](unity-spatial-audio-ch5.md).

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
> Para habilitar o deshabilitar la espacialización, el script solo ajusta la propiedad **spatialBlend** , quedando la propiedad de la **espacialización** habilitada. En este modo, Unity sigue aplicando la curva de **volumen** . De lo contrario, si el usuario deshabilitara la espacialización desde el origen, se oíría el aumento brusco del volumen.
> Si prefiere deshabilitar completamente la espacialización, modifique el script para ajustar también la propiedad booleana de la **espacialización** de la variable **SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Adjunte el script y colóquelo en el botón

Seleccione **cuádruple** en la jerarquía y, en la ventana del inspector, use el botón Agregar componente para agregar **SpatializeOnOff (Script)** .

![Agregar script a cuádruple](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

En la jerarquía, busque **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

Con el objeto **cuádruple** todavía seleccionado en la jerarquía, en la ventana del inspector, busque el componente **de Spatial en OFF (Script)** y arrastre y coloque el componente **TextMeshPro** de PressableButtonHoloLens2.

![Buscar el objeto PressableButtonHoloLens2 en la jerarquía](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

Para establecer el botón para que llame al script **SpatializeOnOff** cuando se lance el botón, debe configurar el script interactuable.

En la ventana jerarquía, seleccione el **PressableButtonHoloLens2**. En la ventana del inspector, busque el componente **interactuable (Script)** y haga clic en el icono + en el evento onclick ().

* Con el objeto **PressableButtonHoloLens2** todavía seleccionado en la ventana de jerarquía, haga clic **en la ventana** de la jerarquía y arrástrela hasta el campo vacío de **ninguno (objeto)** del evento que acaba de agregar para hacer que el objeto ButtonParent escuche el evento click del botón desde este botón:

* Haga clic en la lista desplegable **Ninguna función** del mismo evento. Después, seleccione **SpatializeOnOff**  >  **SwapSpatialization ()** para activar y desactivar el audio espacial

![Configuración de acción de botón](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a habilitar y deshabilitar la espacialización en tiempo de ejecución, probar la aplicación en una HoloLens 2 o en el editor de Unity. En la aplicación, ahora puede hacer clic en el botón para activar y desactivar la espacialización del audio.

En el siguiente tutorial, agregará un efecto de reverberación para que suene un sentido de distancia.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Siguiente tutorial: 5. usar reverberación para agregar distancia al audio espacial](unity-spatial-audio-ch5.md)
