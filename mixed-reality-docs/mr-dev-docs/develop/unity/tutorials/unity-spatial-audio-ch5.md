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
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Usar la reverberación para agregar distancia al audio espacial

## <a name="overview"></a>Introducción

En el tutorial anterior, ha agregado la espacialización de los sonidos para darles una idea de la dirección de este tutorial, agregará un efecto de reverberación para que suene un sentido de distancia.

## <a name="objectives"></a>Objetivos

* Mejore la distancia de los orígenes de sonido percibidos agregando reverberación.
* Controle la distancia percibida del sonido con la distancia del agente de escucha al holograma.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Agregar un grupo de mezclador y un efecto de reverberación

En el tutorial de la interacción del botón de la [interactuación](unity-spatial-audio-ch2.md), hemos agregado un mezclador. El mezclador incluye un **Grupo** de forma predeterminada denominado **maestro**. Dado que solo deseamos aplicar un efecto de reverberación a algunos sonidos, vamos a agregar un segundo grupo para esos sonidos. Para agregar un grupo, haga clic con el botón derecho en el grupo maestro del **mezclador de audio** y elija **Agregar grupo secundario** y proporcione un nombre adecuado para el ejemplo de _efecto de sala_:

![Agregar grupo secundario](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

Cada **Grupo** tiene su propio conjunto de efectos. Agregue un efecto de reverberación al nuevo grupo; para ello, haga clic en **Agregar...** en el nuevo grupo y elija **SFX reverberación**:

![Agregar reverberación de SFX](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

En la terminología de audio, el audio original sin reverberar se denomina _trazado seco_ y el audio después de filtrar con el filtro de reverberación se denomina _ruta húmeda_. Ambas rutas de acceso se envían a la salida de audio y sus puntos fuertes relativos en esta mezcla se denominan _mezcla húmeda/seco_. La mezcla húmeda/seco afecta de una granidad al sentido de la distancia.

La **reverberación de SFX** incluye controles para ajustar la mezcla húmeda/seco dentro del efecto. Dado que el complemento **Spatializer de Microsoft** controla el trazado seco, usaremos la **reverberación SFX** solo para el trazado húmedo. En el panel Inspector de la **reverberación SFX**:

* Establezca la propiedad **nivel seco** en la configuración más baja (-10000 MB)
* Establezca la **propiedad Room** en el valor más alto (0 MB)

![Propiedades de reverberación de SFX](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

Los demás valores controlan el funcionamiento del salón simulado. En concreto, el **tiempo de caída** está relacionado con el tamaño de la sala percibida.

## <a name="enable-reverb-on-the-video-playback"></a>Habilitar reverberación en la reproducción de vídeo

Hay dos pasos para habilitar la reverberación en un origen de audio:

* Enrutar el **origen de audio** al **Grupo** adecuado
* Establecer el complemento de **Microsoft Spatializer** para pasar el audio al **Grupo** para su procesamiento

En los pasos siguientes, ajustará el script para controlar el enrutamiento de audio y adjuntará un script de control proporcionado con el complemento **Spatializer de Microsoft** para alimentar datos en la reverberación.

Con el **cuádruple** seleccionado en la jerarquía, haga clic en **Agregar componente** en la ventana del inspector y agregue el **nivel de envío (Script) del efecto de sala**:

![Agregar script de nivel de envío](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> A menos que habilite la característica de **nivel de envío de efecto de sala** del complemento Spatializer de **Microsoft** , no enviará ningún audio al motor de audio de Unity para que el procesamiento surta efecto.

El componente de **nivel de envío de efecto de sala** incluye un control de gráfico que establece el nivel de audio que se envía al motor de audio de Unity para el procesamiento de reverberación. Para abrir el control de gráfico, haga clic en el **nivel de envío del efecto de sala**.  Haga clic y arrastre la curva verde hacia abajo para establecer el nivel en about-30dB:

![Ajustar curva de reverberación](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

A continuación, quite las marcas de comentario de las cuatro líneas comentadas en el script **SpatializeOnOff** . El script tendrá ahora el siguiente aspecto:

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

Una vez que se quitan los comentarios de estas líneas, se agregan dos propiedades al inspector del **script SpatializeOnOff**. asígnelos en la ventana del inspector del componente **SpatializeOnOff** de la **cuádruple**.

Con el objeto cuádruple todavía seleccionado en la jerarquía, en la ventana del inspector, busque el componente de **script SpatializeOnOff** y:

* Establecer la propiedad de **grupo de efectos de sala** en el nuevo grupo de mezcla de efectos de sala
* Establecer la propiedad del **Grupo maestro** en el grupo de mezclador principal

![Spatial en OFF extendido](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a>Enhorabuena

Ha completado los tutoriales de audio espacial de HoloLens 2 para Unity. Pruebe la aplicación en HoloLens 2 o Unity. Al hacer clic en el botón de la aplicación para activar la espacialización, el script enrutará el audio del vídeo al grupo de efectos de la habitación para agregar la reverberación. Al cambiar a estéreo, enrutará el audio al grupo maestro y evitará que se agregue la reverberación.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
