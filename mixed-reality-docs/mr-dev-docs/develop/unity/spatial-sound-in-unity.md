---
title: Sonido espacial en Unity
description: Reproducir sonido espacial desde un punto 3D específico dentro de la escena de Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala
ms.openlocfilehash: 9c5f71b2d9d13fa40f0d1674237d2da6c769e584
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691866"
---
# <a name="spatial-sound-in-unity"></a>Sonido espacial en Unity

Esta página contiene vínculos a recursos de sonido espacial en Unity.

## <a name="spatializer-options"></a>Opciones de Spatializer
Las opciones de Spatializer para aplicaciones de realidad mixta incluyen:
* *MS HRTF Spatializer* . Unity lo proporciona como parte del paquete opcional de *Windows Mixed Reality* .
  * Esto se ejecuta en la CPU en una arquitectura de "origen único" de mayor costo.
  * Esto se proporciona por compatibilidad con versiones anteriores con las aplicaciones de HoloLens originales.
* *Microsoft Spatializer* . Está disponible en el [repositorio de github de Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Usa una arquitectura de "varios orígenes" de menor costo.
  * En HoloLens 2, se descarga en un acelerador de hardware.

En el caso de las nuevas aplicaciones, se recomienda *Microsoft Spatializer* .

## <a name="enable-spatialization"></a>Habilitar la espacialización

Use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ y elija **Microsoft Spatializer** en la configuración de audio del proyecto. A continuación:
* Adjuntar un **origen de audio** a un objeto de la jerarquía
* Active la casilla **Habilitar la espacialización**
* Mueve el control deslizante de **mezcla espacial** a ' 1 '
* Asegúrese de que el audio espacial está habilitado en la estación de trabajo del desarrollador. Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas y asegurándose de que el sonido espacial esté establecido en un valor distinto de "desactivado". Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **Windows Sonic para auriculares** .

>[!NOTE]
>Si se produce un error en Unity al no poder cargar el complemento Microsoft. SpatialAudio. Spatializer. Unity porque falta una de sus dependencias, compruebe que dispone de la versión más reciente del [Microsoft Visual C++ redistribuible](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalada en su equipo.

Para obtener información, consulte:
* [Repositorio de GitHub de Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Tutorial de spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentación del origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentación de spatializer de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atenuación basada en la distancia
La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con una rolloff logarítmica. Es posible que esta configuración funcione para su escenario, o puede que los orígenes se expongan demasiado rápido o demasiado lentamente. Para obtener información, consulte:
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

Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de realidad mixta. Desde aquí, puede continuar con el siguiente bloque de creación:

> [!div class="nextstepaction"]
> [Texto](text-in-unity.md)

O salte a las funcionalidades y API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Siempre puede volver a los puntos de [control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Diseño sonoro en realidad mixta](../../design/spatial-sound-design.md)
* [Tutorial de spatializer de Microsoft](tutorials/unity-spatial-audio-ch1.md)
