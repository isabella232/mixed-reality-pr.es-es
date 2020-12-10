---
title: Sonido espacial en Unity
description: Reproducir sonido espacial desde un punto 3D específico dentro de la escena de Unity.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta, spatializer, reverberación
ms.openlocfilehash: 1efe287855cc5b7738069c6d8183c2ecb5bd6d59
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010146"
---
# <a name="spatial-sound-in-unity"></a>Sonido espacial en Unity

Esta página contiene vínculos a recursos de sonido espacial en Unity.

## <a name="spatializer-options"></a>Opciones de Spatializer
Las opciones de Spatializer para aplicaciones de realidad mixta incluyen:
* Unity proporciona el *MS HRTF Spatializer* como parte del paquete opcional de *Windows Mixed Reality* .
  * Se ejecuta en la CPU en una arquitectura de "origen único" de mayor costo.
  * Se proporciona para la compatibilidad con versiones anteriores con las aplicaciones de HoloLens originales.
* *Microsoft Spatializer* está disponible en el [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Usa una arquitectura de "varios orígenes" de menor costo.
  * Descargado en un acelerador de hardware de HoloLens 2. 

En el caso de las nuevas aplicaciones, se recomienda *Microsoft Spatializer*.

## <a name="enable-spatialization"></a>Habilitar la espacialización

Use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ y elija **Microsoft Spatializer** en la configuración de audio del proyecto. Después:
* Adjuntar un **origen de audio** a un objeto de la jerarquía
* Active la casilla **Habilitar la espacialización**
* Mueve el control deslizante de **mezcla espacial** a ' 1 '
* Asegúrese de que el audio espacial está habilitado en la estación de trabajo del desarrollador. 
    * Haga clic con el botón derecho en el icono de volumen en la barra de tareas y asegúrese de que el sonido espacial esté establecido en un valor distinto de "desactivado". 
    * Elija **Windows Sonic para auriculares** para obtener la mejor representación de lo que escuchará en HoloLens 2.

>[!NOTE]
>Si se produce un error en Unity al no poder cargar el complemento Microsoft. SpatialAudio. Spatializer. Unity porque falta una de sus dependencias, compruebe que dispone de la versión más reciente del [Microsoft Visual C++ redistribuible](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalada en su equipo.

Para más información, consulte:
* [Repositorio de GitHub de Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Tutorial de spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentación del origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentación de spatializer de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atenuación basada en la distancia
La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con una rolloff logarítmica. Es posible que esta configuración funcione para su escenario, o puede que los orígenes se expongan demasiado rápido o demasiado lentamente. Para más información, consulte:
* [Diseño sonoro en la realidad mixta](../../design/spatial-sound-design.md) para la configuración recomendada.
* [Documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obtener instrucciones sobre cómo establecer estas curvas.

## <a name="reverb"></a>Reverbera
De forma predeterminada, el _Spatializer de Microsoft_ deshabilita los efectos posteriores a Spatializer. Para habilitar la reverberación y otros efectos para los orígenes espaciales:
* Asociar el componente de **nivel de envío del efecto de sala** a cada origen
* Ajuste la curva de nivel de envío de cada origen para controlar la ganancia del audio que se devuelve al gráfico para el procesamiento de efectos

Consulte [el capítulo 5 del tutorial de spatializer](tutorials/unity-spatial-audio-ch5.md) para obtener más información.

## <a name="unity-spatial-sound-examples"></a>Ejemplos de sonido espacial de Unity
Para ver ejemplos de sonido espacial en Unity, consulte:
* [Demostraciones de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Proyecto de ejemplo de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de la realidad mixta. Desde aquí, puede continuar con el siguiente bloque de creación:

> [!div class="nextstepaction"]
> [Texto](text-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Diseño sonoro en realidad mixta](../../design/spatial-sound-design.md)
* [Tutorial de spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
