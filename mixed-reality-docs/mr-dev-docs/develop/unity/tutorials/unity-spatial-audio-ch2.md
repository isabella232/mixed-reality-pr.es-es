---
title: 'Tutoriales de audio espacial: 2. Sonidos de interacción del botón de espacialización'
description: Agregue un botón al proyecto y Spatial los sonidos de interacción del botón.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer, Prefabs, curva de volumen
ms.openlocfilehash: e4b2ed99f56fea82b1c72e4fce5205c14e1d3533
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578496"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Sonidos de interacción del botón de espacialización

## <a name="overview"></a>Introducción

En este tutorial, obtendrá información sobre cómo espaciale los sonidos de interacción del botón y aprenderá a usar un clip de audio para probar la interacción del botón espacial.  

## <a name="objectives"></a>Objetivos

* Agregar y espaciales los sonidos de clic del botón

## <a name="add-a-button"></a>Adición de un botón

Para agregar el botón recurso prefabricado, en la ventana **proyecto** , seleccione **activos** y escriba "PressableButtonHoloLens2" en la barra de búsqueda.

![Botón recurso prefabricado en activos](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

El botón recurso prefabricado es la entrada representada por un icono azul. Haga clic y arrastre **PressableButtonHoloLens2** recurso prefabricado a la jerarquía. Con el objeto **PressableButtonHoloLens2** aún seleccionado, en la ventana del inspector, configure el componente de **transformación** como se indica a continuación:

* **Posición**: X = 0, y =-0,4, Z = 2
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Transformación de botón](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **PressableButtonHoloLens2** y, a continuación, hacer zoom ligeramente de nuevo:

## <a name="spatialize-button-feedback"></a>Comentario del botón de Spatial

En este paso, creará un espacial de los comentarios de audio para el botón. Para obtener sugerencias de diseño relacionadas, consulte [diseño de sonido espacial](../../../design/spatial-sound-design.md).

En la ventana **mezclador de audio** , definirá destinos denominados grupos de **mezclador** para la reproducción de audio de componentes de origen de **audio** .

Para abrir la ventana **mezclador de audio** , en el menú de Unity, seleccione **Windows**  >  **audio**  >  **audio mixer**: ![ abrir la ventana mezclador de audio.](images/spatial-audio/spatial-audio-02-section2-step1-1.png)

 Para crear un **mezclador** , haga clic en el "+" junto a **mixers** y escriba un nombre adecuado para el mezclador, por ejemplo, _mezclador de audio espacial_. El nuevo mezclador incluirá un **Grupo** predeterminado denominado **maestro**.

![Panel de mezclador con el primer mezclador](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> Hasta que se habilita la reverberación en el [quinto capítulo: usar reverberación para agregar distancia al audio espacial](unity-spatial-audio-ch5.md), el medidor de volumen del mezclador no muestra la actividad de los sonidos que se reproducen a través de Microsoft Spatializer

En la ventana jerarquía, seleccione **PressableButtonHoloLens2** en la ventana del inspector busque el componente **origen de audio** y configure el componente origen de audio como se indica a continuación:

1. En la propiedad **salida** , haga clic en el selector y elija el **mezclador** que creó.
2. Active la casilla **Spatial** .
3. Mueva el control deslizante de **mezcla espacial** a 3D (1).

![Origen de audio de botón](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> Si mueve la **mezcla espacial** a 1 (3D) sin activar la casilla **Spatial** , Unity usará su spatializer de movimiento panorámico, en lugar de **spatializer de Microsoft** con HRTFs.

## <a name="adjust-the-volume-curve"></a>Ajustar la curva del volumen

De forma predeterminada, Unity atenúa los sonidos espaciales a medida que se alejan del agente de escucha. Cuando se aplica esta atenuación a los sonidos de interacción, la interfaz puede resultar más difícil de usar.

Para deshabilitar esta atenuación, debe ajustar la curva del **volumen** en el componente **origen de audio** .

En la ventana de jerarquía, seleccione el **PressableButtonHoloLens2** y, a continuación, en la ventana del inspector, navegue hasta configuración de sonido 3D de **origen de audio**  >   y configure de la manera siguiente:

1. Establezca la propiedad **Volume rolloff** en rolloff lineal
2. Arrastre el punto de conexión en la curva de **volumen** (la curva roja) desde ' 0 ' en el eje y hasta ' 1 '
3. Para ajustar la forma de la curva de **volumen** para que sea plana, arrastre el control de forma de curva blanca para que sea paralelo al eje X.

![Configuración de sonido 3D del botón](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a>Prueba del audio espacial

Para probar el audio espacial en el editor de Unity, tiene que agregar un clip de audio en la opción componente de **origen de audio** with **Loop** activada en el objeto **PressableButtonHoloLens2** .

En el modo de reproducción, mueva el objeto **PressableButtonHoloLens2** de izquierda a derecha y compare con y sin el audio espacial habilitado en la estación de trabajo. También puede cambiar la configuración de origen de audio para realizar pruebas:

* Movimiento de la propiedad de **Blend espacial** entre 0-1 (sonido en 2D no espacial y 3D)
* Activar y desactivar la propiedad **Spatial**

Pruebe la aplicación en HoloLens 2. En la aplicación, puede hacer clic en el botón y oír los sonidos de interacción del botón espacial.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a espaciales los sonidos de interacción del botón y a usar un clip de audio para probar la interacción de los botones espaciales. En el siguiente tutorial aprenderá a encargar el audio de un origen de vídeo.

> [!div class="nextstepaction"]
> [Siguiente tutorial: 3. espacialización de audio desde un vídeo](unity-spatial-audio-ch3.md)
