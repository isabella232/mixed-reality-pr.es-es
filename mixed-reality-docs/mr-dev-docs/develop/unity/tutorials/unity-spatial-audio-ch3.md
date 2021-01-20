---
title: 'Tutoriales de audio espacial: 3. Espacialización del audio de un vídeo'
description: Importe un recurso de vídeo en el proyecto de Unity y cospatiala el audio del vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer, vídeo, importación, reproductor de vídeo
ms.openlocfilehash: 6474da522e650d23349a21c3deeac00222b8ce93
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578625"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Espacialización del audio de un vídeo

## <a name="overview"></a>Introducción

En este tutorial, obtendrá información sobre cómo espaciale el audio de un origen de vídeo y cómo probarlo en el editor de Unity y en HoloLens 2.

## <a name="objectives"></a>Objetivos

* Importar un vídeo y agregar un reproductor de vídeo
* Reproducir el vídeo en un Quadrangle
* Enrute el audio del vídeo al Quadrangle y Spatial el audio

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importar un vídeo y agregar un reproductor de vídeo a la escena

En este tutorial, puede usar [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) del proyecto de ejemplo de audio espacial.

Para importar vídeo en el proyecto de Unity. en el menú de Unity, seleccione **recurso**  >  **importar nuevo** 
 activo importar activo. ![](images/spatial-audio/spatial-audio-03-section1-step1-1.png)

En la ventana **importar nuevo recurso...** , seleccione el archivo **Microsoft HoloLens-Spatial Sound-PTPvx7mDon4** que descargó y haga clic en el botón **abrir** para importar el recurso en el proyecto:

![Seleccionar activo](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

Ajustar la configuración de calidad en el clip de vídeo puede garantizar una reproducción fluida de HoloLens 2. Seleccione el archivo de vídeo en la ventana **proyecto** y, en la ventana del inspector del archivo de vídeo, **invalide** la configuración de las aplicaciones de la **tienda Windows** y:

* Habilitar **Transcode**
* Establecer **códec** en H264
* Establecer el **modo de velocidad de bits** en baja
* Establecer **calidad espacial** en calidad espacial media

Después de estos ajustes, haga clic en aplicar para cambiar la configuración de calidad en el clip de vídeo.

![Cambio de propiedad de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

Haga clic con el botón derecho en la jerarquía, seleccione  >  **reproductor** de vídeo de vídeo para agregar el componente reproductor de vídeo.

![Agregar reproductor de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a>Reproducir vídeo en un Quadrangle

El objeto **reproductor de vídeo** necesita un objeto de juego con textura para representar el vídeo.

Haga clic con el botón derecho en la jerarquía, seleccione **objeto 3D**  >  **cuádruple** para crear un cuádruple y configure su componente de **transformación** como se indica a continuación:

* **Posición**: X = 0, Y = 0, Z = 2
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1,28, y = 0,72, Z = 1

![Agregar un cuádruple](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

Ahora debe texturar el **cuádruple** con el vídeo, en la ventana **proyecto** , haga clic con el botón derecho y elija **crear**  >  **textura de representación** para crear un componente de textura de representación, escriba un nombre adecuado para la textura de representación, por ejemplo, _textura de audio espacial_:

![Crear textura de representación](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

Seleccione la **textura de representación** y, en la ventana del inspector, establezca la propiedad **size** para que coincida con la resolución nativa del vídeo de 1280x720. A continuación, para garantizar un buen rendimiento de la representación en HoloLens 2, establezca la propiedad de **búfer de profundidad** en una **profundidad de 16 bits como mínimo**.

![Representar propiedades de textura](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

A continuación, use la textura de **audio espacial** de textura de representación creada como textura para la **cuádruple**:

1. Arrastre la **textura de audio espacial** desde la ventana de **proyecto** hasta el **cuádruple** de la jerarquía para agregar la textura de representación a la cuádruple
2. Para garantizar un buen rendimiento en HoloLens 2, seleccione cuádruple en la jerarquía y, en la ventana del inspector del sombreador, seleccione el sombreador estándar del **Kit de herramientas de realidad mixta**  >   .

![Propiedades de textura cuádruple](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

Para configurar **el reproductor de vídeo** y mostrar la **textura** para reproducir el clip de vídeo, seleccione el **reproductor** de vídeo en la **jerarquía** y en la ventana del **Inspector** .

* Establezca la propiedad **clip de vídeo** en el archivo de vídeo descargado ' Microsoft HoloLens-Spatial Sound-PTPvx7mDon4 '
* Marque la casilla **bucle**
* Establecer la **textura de destino** en la nueva textura de representación de textura de **audio espacial**

![Propiedades del reproductor de vídeo](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatial el audio del vídeo

En la ventana jerarquía, seleccione **cuádruple** objeto y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el **origen de audio** al que enrutará el audio del vídeo.

En el **origen de audio**:

* Establecer la **salida** en el **mezclador de audio espacial**
* Active la casilla **Spatial**
* Mueve el control deslizante de **mezcla espacial** a 1 (3D)

![Inspector de fuente de audio cuádruple](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

Para configurar el reproductor de vídeo para que enrute su audio al **origen de audio**, seleccione el **reproductor de vídeo** en la ventana jerarquía y, en el objeto reproductor de vídeo del inspector, realice los cambios siguientes.

* Establecer el **modo de salida de audio** en **origen de audio**
* Establezca la propiedad **origen de audio** en el **cuádruple**

![Reproductor de vídeo conjunto de audio origen](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido cómo enespaciale el audio desde un origen de vídeo pruebe la aplicación en una HoloLens 2 o en el editor de Unity. Verá y oirá el vídeo y el audio del vídeo está espacial.

En el siguiente tutorial, aprenderá a habilitar y deshabilitar la espacialización en tiempo de ejecución.

> [!div class="nextstepaction"]
> [Siguiente tutorial: 4. habilitar y deshabilitar la espacialización en tiempo de ejecución](unity-spatial-audio-ch4.md)
