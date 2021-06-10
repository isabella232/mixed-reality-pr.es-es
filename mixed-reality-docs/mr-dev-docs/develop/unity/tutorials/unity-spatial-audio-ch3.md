---
title: 'Tutoriales de audio espacial: 3. Espacialización del audio de un vídeo'
description: Importe un recurso de vídeo en el proyecto de Unity y espacialice el audio del vídeo.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, video importing, Video Player
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712921"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Espacialización del audio de un vídeo

## <a name="overview"></a>Información general

En este tutorial, aprenderá a espacializar el audio desde un origen de vídeo y probarlo en el editor de Unity y HoloLens 2.

## <a name="objectives"></a>Objetivos

* Importación de un vídeo y adición de un reproductor de vídeo
* Reproducir el vídeo en un cuadrángulo
* Enrutar audio desde el vídeo al cuadrángulo y espacializar el audio

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importación de un vídeo y adición de un reproductor de vídeo a la escena

Para este tutorial, use este [vídeo del](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) proyecto de ejemplo de audio espacial.

Para importar Vídeo en el proyecto de Unity. En el menú de Unity, **seleccione Asset** Import  >  **New Asset** 
 ![ Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

En la ventana Importar nuevo **recurso...** , seleccione el archivo **Microsoft HoloLens - Spatial Sound-PTPvx7mGall4** que descargó y haga clic en el botón Abrir para importar el recurso en el proyecto: 

![Selección del recurso](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

El ajuste de la configuración de calidad del clip de vídeo puede garantizar una reproducción sin problemas en HoloLens 2. Seleccione el archivo de vídeo en la **ventana Proyecto** y, en la ventana Inspector del archivo de **vídeo,** invalide la configuración de aplicaciones de la **Tienda Windows** y:

* Habilitar **transcodificación**
* Establezca **Códec** en H264
* Establecer **el modo de velocidad de bits** en Bajo
* Establecer **la calidad espacial** en Calidad espacial media

Después de estos ajustes, haga clic en Aplicar para cambiar la configuración de calidad en el clip de vídeo.

![Cambio de propiedad de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

Haga clic con el botón derecho en Jerarquía, seleccione **Reproductor**  >  **de vídeo para** agregar el componente Reproductor de vídeo.

![Agregar reproductor de vídeo](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Reproducir vídeo en un cuadrángulo

El **objeto Reproductor de** vídeo necesita un objeto de juego con textura para representar el vídeo.

Haga clic con el botón derecho en Hierarchy (Jerarquía), seleccione 3D Object Quad (Cuatro objetos **3D)** para crear un quad y  >   configurar su **componente Transform** (Transformar) como se muestra a continuación:

* **Posición:** X = 0, Y = 0, Z = 2
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala:** X = 1,28, Y = 0,72, Z = 1

![Adición de un cuadrándular](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

Ahora tiene que  texturar el cuadrángulo con el vídeo. En la ventana Proyecto, haga clic con el botón derecho y elija Crear textura de representación para crear un componente Render Texture (Representar textura), escriba un nombre adecuado para La textura de representación, por    >   ejemplo, Textura de _audio espacial_:

![Crear textura de representación](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

Seleccione Render **Texture (Representar textura)** y, en la ventana Inspector, establezca la propiedad **Size** para que coincida con la resolución nativa del vídeo de 1280 x 720. A continuación, para garantizar un buen rendimiento de la representación HoloLens 2, establezca la propiedad **Búfer** de profundidad en **Al menos 16 bits de profundidad.**

![Propiedades de textura de representación](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

A continuación, use la textura de **audio espacial** render texture creada como textura para el **cuadrángulo**:

1. Arrastre la **textura de audio espacial** desde la ventana **Proyecto** al **cuadrángulo** de la jerarquía para agregar la textura de representación al cuadrángulo.
2. Para garantizar un buen rendimiento en HoloLens 2, seleccione Quad en la jerarquía y, en la ventana Inspector del **sombreador, seleccione** el sombreador estándar Mixed Reality  >   Toolkit.

![Propiedades de textura quad](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

Para establecer el **Reproductor de vídeo** y **Representar** textura para  reproducir el clip de vídeo, seleccione **el Reproductor** de vídeo en la jerarquía y, en la **ventana Inspector,**

* Establezca la **propiedad Clip de** vídeo en el archivo de vídeo descargado "Microsoft HoloLens - Spatial Sound-PTPvx7mGall4"
* Active la casilla **Bucle**
* Establecer **textura de destino** en la nueva textura de representación Textura de audio **espacial**

![Propiedades del reproductor de vídeo](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>Espacialización del audio del vídeo

En la ventana Hierarchy (Jerarquía), seleccione **Quad** object (Objeto Quad) y, en la ventana Inspector, use el botón Add **Component** (Agregar componente) para agregar audio **source** (Origen de audio) al que enrutará el audio desde el vídeo.

En el **origen de audio**:

* Establezca **Output (Salida)** en **spatial audio mixer (Mezclador de audio espacial)**
* Active la **casilla Espacializar**
* Mover el **control deslizante de Spatial Blend** a 1 (3D)

![Inspector de origen de audio cuadrángulo](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

Para establecer el Reproductor de vídeo para enrutar su audio al origen **de audio,** seleccione el Reproductor de vídeo en la ventana Jerarquía y, en el objeto Reproductor de vídeo del Inspector, realice los cambios siguientes. 

* Establezca el modo **de salida de audio** en Origen de **audio**
* Establezca la **propiedad Origen de** audio en el **cuadrángulo.**

![Origen de audio del conjunto de reproductores de vídeo](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a espacializar el audio desde un origen de vídeo Pruebe la aplicación en un HoloLens 2 o en el editor de Unity. Verá y escuchará el vídeo, y el audio del vídeo se espacializa.

En el siguiente tutorial, aprenderá a habilitar y deshabilitar la espacialización en tiempo de ejecución.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 4. Habilitación y deshabilitación de la espacialización en tiempo de ejecución](unity-spatial-audio-ch4.md)
