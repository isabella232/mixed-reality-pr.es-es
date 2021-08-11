---
title: 'Tutoriales de audio espacial: 5. Usar la reverberación para agregar distancia al audio espacial'
description: Agregue un efecto de reverberación para mejorar la sensación de variación de distancia al audio espacial.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, audio mixer, SFX reverb
ms.openlocfilehash: 8adc92eb96cb8ebd2cc5fff14d522bcfe72733cc5748183dd6db59d753e12a3e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193012"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Usar la reverberación para agregar distancia al audio espacial

## <a name="overview"></a>Información general

En el tutorial anterior, ha agregado espacialización para los sonidos para darles una sensación de dirección en este tutorial, agregará un efecto de reverberación para dar a los sonidos una sensación de distancia.

## <a name="objectives"></a>Objetivos

* Mejore la distancia percibida de los orígenes de sonido mediante la adición de reverberación.
* Controle la distancia percibida del sonido mediante la distancia del agente de escucha al holograma.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Agregar un grupo mezclador y un efecto de reverberación

En [el Tutorial de interacción de botón espacialización,](unity-spatial-audio-ch2.md)agregamos un mezclador. El mezclador incluye un **grupo de** forma predeterminada denominado **Maestro.** Dado que solo queremos aplicar un efecto de reverberación a algunos sonidos, vamos a agregar un segundo grupo para esos sonidos. Para agregar un grupo, haga clic con el botón derecho en el grupo Maestro en audio **Mixer** elija Agregar **grupo** secundario y asigne un nombre adecuado para, por ejemplo, Efecto _de sala_:

![Agregar grupo secundario](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

Cada **grupo** tiene su propio conjunto de efectos. Para agregar un efecto de reverberación al nuevo grupo, haga clic en **Agregar...** en el nuevo grupo y elija **SFX Reverb**:

![Agregar SFX Reverb](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

En la terminología de audio, el audio original sin reverberar se denomina ruta de acceso sin efectos y el audio después de filtrar con el filtro de reverberación se denomina ruta _de acceso con efectos._ Ambas rutas de acceso se envían a la salida de audio y sus puntos fuertes relativos en esta mezcla se denominan mezcla sin efectos y _sin efectos._ La mezcla con efectos y sin efectos afecta en gran medida a la sensación de distancia.

La **reverberación de SFX** incluye controles para ajustar la mezcla con efectos y sin efectos dentro del efecto. Dado que **el complemento Microsoft Spatializer** controla el trazado sin efectos, usaremos **SFX Reverb** solo para la ruta de acceso con efectos. En el panel Inspector de **SFX Reverb**:

* Establezca la **propiedad Dry Level** en la configuración más baja (-10000 mB)
* Establezca la **propiedad Room** en la configuración más alta (0 mB)

![Propiedades de SFX Reverb](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

La otra configuración controla la sensación de la sala simulada. En concreto, el **tiempo de decadencia** está relacionado con el tamaño percibido de la sala.

## <a name="enable-reverb-on-the-video-playback"></a>Habilitación de la reverberación en la reproducción de vídeo

Hay dos pasos para habilitar la reverberación en un origen de audio:

* Enrutar **el origen de** audio al grupo **adecuado**
* Establecer el **complemento Microsoft Spatializer** para pasar audio al **grupo para** su procesamiento

En los pasos siguientes, ajustará el script para controlar el enrutamiento de audio y adjuntará un script de control proporcionado con el complemento **Microsoft Spatializer** para alimentar los datos en la reverberación.

Con el **cuadrántico** seleccionado en la jerarquía, haga clic **en Agregar componente** en la ventana Inspector y agregue el nivel de envío de efecto de sala **(script):**

![Agregar script de nivel de envío](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> A menos que **habilite** la característica Nivel de envío de efecto de sala del complemento Espacializer de **Microsoft,** no enviará ningún audio al motor de audio de Unity para el procesamiento de efectos.

El **componente Nivel de envío de efecto** de sala incluye un control de gráfico que establece el nivel del audio enviado al motor de audio de Unity para el procesamiento de reverberación. Para abrir el control de gráfico, haga clic en el **nivel de envío efecto de sala**.  Haga clic y arrastre la curva verde hacia abajo para establecer el nivel en aproximadamente -30dB:

![Ajuste de la curva de reverberación](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

A continuación, descomprima las 4 líneas comentadas en el script **SpatializeOnOff.** El script tendrá ahora este aspecto:

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

Una vez que estas líneas se han descomprimido, agrega dos propiedades al inspector del **script SpatializeOnOff**. asígnelos en la ventana Inspector **del componente SpatializeOnOff** del **quad**.

Con el objeto Quad aún seleccionado en la jerarquía , en la ventana Inspector, busque el componente **De script SpatializeOnOff** y :

* Establezca la propiedad **Grupo de efectos de la sala** en el nuevo grupo de mezcladores Efecto de sala.
* Establezca la **propiedad Grupo maestro** en el grupo mezclador maestro

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>Enhorabuena

Ha completado los tutoriales HoloLens 2 de audio espacial para Unity. Pruebe la aplicación en un HoloLens 2 o Unity. Al hacer clic en el botón de la aplicación para activar la espacialización, el script enruta el audio del vídeo al grupo de efectos de sala para agregar la reverberación. Al cambiar a estéreo, enruta el audio al grupo Maestro y evita agregar reverberación.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
