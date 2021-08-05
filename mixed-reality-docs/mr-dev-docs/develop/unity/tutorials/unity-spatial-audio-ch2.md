---
title: 'Tutoriales de audio espacial: 2. Sonidos de interacción del botón de espacialización'
description: Agregue un botón al proyecto y espacialice los sonidos de interacción del botón.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, prefabs, volume curve
ms.openlocfilehash: e0f916ecf8cd8da81e0738b082021c76c55a7f2031517a37b959575e1b21ce16
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209876"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Sonidos de interacción del botón de espacialización

## <a name="overview"></a>Información general

En este tutorial, aprenderá a espacializar los sonidos de interacción del botón y también a usar un clip de audio para probar la interacción de los botones espacializados.  

## <a name="objectives"></a>Objetivos

* Agregar y espacializar los sonidos de clic del botón

## <a name="add-a-button"></a>Adición de un botón

Para agregar el objeto Prefab Button, en la **Project,** seleccione **Paquetes** y escriba "PressableButtonHoloLens2" en la barra de búsqueda.

![Botón prefab en recursos](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

El botón prefab es la entrada representada por un icono azul. Haga clic y arrastre el objeto **prefab PressableButtonHoloLens2** a la jerarquía. Con el **objeto PressableButtonHoloLens2** aún seleccionado, en la ventana Inspector, configure el componente **Transformar** de la siguiente manera:

* **Posición:** X = 0, Y = -0,4, Z = 2
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Transformación de botón](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **PressableButtonHoloLens2** y, a continuación, acercar ligeramente de nuevo:

## <a name="spatialize-button-feedback"></a>Comentarios del botón Espacializar

En este paso, espacializará los comentarios de audio del botón. Para obtener sugerencias de diseño relacionadas, vea [diseño de sonido espacial](../../../design/spatial-sound-design.md).

En la **ventana Audio Mixer** definirá los destinos denominados Mixer **Groups**, para la reproducción de audio desde componentes de **origen de** audio.

Para abrir la **ventana Audio Mixer, en** el menú de Unity, seleccione Window  >  **Audio**  >  **Mixer**: Open Audio Mixer ![ Window](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 Cree un **Mixer** haciendo clic en "+" junto a **Mezcladores** y escriba un nombre adecuado para el Mixer por ejemplo, _Spatial Audio Mixer_. El nuevo mezclador incluirá un grupo **predeterminado denominado** **Maestro.**

![Mixer panel con el primer mezclador](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> Hasta que se habilita la reverberación en el quinto capítulo: Con [reverberación](unity-spatial-audio-ch5.md)para agregar distancia al audio espacial, el medidor de volumen del mezclador no muestra la actividad de los sonidos reproducdos a través de Microsoft Spatializer.

En la ventana Hierarchy (Jerarquía), seleccione **PressableButtonHoloLens2** y, en la ventana Inspector, busque el componente Audio Source (Origen de **audio)** y Configure the Audio Source component (Configurar el componente Audio Source) como se muestra a continuación:

1. En la **propiedad Salida,** haga clic en el selector y **elija el Mixer** que ha creado.
2. Active la **casilla Espacializar.**
3. Mueva el **control deslizante de Spatial Blend** a 3D (1).

![Origen de audio de botón](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> Si mueve **Spatial Blend** a 1 (3D) sin activar la casilla **Spatialize** (Espacializar), Unity usará su espacializador panorámico, en lugar de **Microsoft Spatializer** con HRFS.

## <a name="adjust-the-volume-curve"></a>Ajuste de la curva de volumen

De forma predeterminada, Unity atenuará los sonidos espacializados a medida que se alejan más del agente de escucha. Cuando esta atenuación se aplica a los sonidos de comentarios de interacción, la interfaz puede ser más difícil de usar.

Para deshabilitar esta atenuación, debe ajustar la curva **Volumen** en el **componente Origen de** audio.

En la ventana Hierarchy (Jerarquía), seleccione **PressableButtonHoloLens2** y, en la ventana Inspector, vaya a **Audio Source**  >  **3D Sound Configuración** and Configure (Configurar) como se muestra a continuación:

1. Establezca la **propiedad Rolloff del volumen** en Linear Rolloff
2. Arrastre el punto de conexión **en la curva Volumen** (la curva roja) desde "0" en el eje y hasta "1".
3. Para ajustar la forma de la curva **volumen** para que sea plana, arrastre el control de forma de curva blanca para que sea paralelo al eje X.

![Configuración de sonido 3D de botón](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>Prueba del audio de espacialización

Para probar el audio de espacialización en el editor de Unity, tiene que agregar un clip de audio en el componente **Origen** de audio con la opción **Bucle** activada en el objeto **PressableButtonHoloLens2.**

En el modo de reproducción, mueva el objeto **PressableButtonHoloLens2** de izquierda a derecha y compare con y sin audio espacial habilitado en la estación de trabajo. También puede cambiar la configuración del origen de audio para las pruebas mediante:

* Mover la **propiedad Spatial Blend** entre 0 y 1 (sonido 2D no espacializado y 3D espacializado)
* Comprobación y desactivación de la **propiedad Spatialize**

Pruebe la aplicación en HoloLens 2. En la aplicación, puede hacer clic en el botón y escuchar los sonidos de interacción del botón espacializado.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Enhorabuena

En este tutorial ha aprendido a espacializar los sonidos de interacción del botón y a usar un clip de audio para probar la interacción de botón espacializado. En el siguiente tutorial aprenderá a espacializar el audio desde un origen de vídeo.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Espacialización del audio de un vídeo](unity-spatial-audio-ch3.md)
