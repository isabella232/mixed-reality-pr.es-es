---
title: Sonido espacial en Unity
description: Aprenda a reproducir y atenuar sonidos espaciales desde un punto 3D específico dentro de la escena de Unity con ejemplos.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de la sala, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit, espacializador, reverberación
ms.openlocfilehash: e6e56732a888fd096335a114fceba557519b01bf8df84a7670b9265f46c75a34
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228231"
---
# <a name="spatial-sound-in-unity"></a>Sonido espacial en Unity

Esta página se vincula a recursos para el sonido espacial en Unity.

## <a name="spatializer-options"></a>Opciones del espacializador

Las opciones de espacializador para aplicaciones de realidad mixta incluyen:
* Unity proporciona el *espacializador MS HRTF* como parte del *Windows Mixed Reality* paquete opcional.
  * Se ejecuta en la CPU en una arquitectura de "origen único" de mayor costo.
  * Se proporciona para la compatibilidad con versiones anteriores con aplicaciones HoloLens originales.
* *Microsoft Spatializer está* disponible en el repositorio de GitHub microsoft [spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Usa una arquitectura de "varios orígenes" de menor costo.
  * Se descarga en un acelerador de hardware en el HoloLens 2. 

Para las nuevas aplicaciones, se recomienda *Microsoft Spatializer*.

## <a name="enable-spatialization"></a>Habilitación de la espacialización

Use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft.SpatialAudio.Spatializer.Unity_ y elija **Microsoft Spatializer** en la configuración de audio del proyecto. Después:
* Adjuntar un **origen de audio** a un objeto de la jerarquía
* Active la casilla **Habilitar espacialización.**
* Mover el **control deslizante de Spatial Blend** a "1"
* Asegúrese de que el audio espacial está habilitado en la estación de trabajo para desarrolladores. 
    * Haga clic con el botón derecho en el icono de volumen de la barra de tareas y asegúrese de que Sonido espacial está establecido en algo distinto de "desactivado". 
    * Elija **Windows Sonic para auriculares** obtener la mejor representación de lo que escuchará en HoloLens 2.

>[!NOTE]
>Si recibe un error en Unity sobre no poder cargar el complemento Microsoft.SpatialAudio.Spatializer.Unity porque falta una de sus dependencias, compruebe que tiene instalada la versión más reciente de [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) en el equipo.

Para más información, consulte:
* [Repositorio de GitHub espacializador de Microsoft](https://github.com/microsoft/spatialaudio-unity)
* [Tutorial del espacializador de Microsoft](tutorials/unity-spatial-audio-ch1.md)
* [Documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentación del espacializador de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atenuación basada en la distancia

La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con un lanzamiento logarítmico. Esta configuración puede funcionar en su escenario o puede que los orígenes se atenúan demasiado rápido o demasiado lentamente. Para más información, consulte:
* [Diseño de sonido en realidad mixta para](../../design/spatial-sound-design.md) la configuración recomendada.
* [Documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obtener instrucciones sobre cómo establecer estas curvas.

## <a name="reverb"></a>Reverberación

Microsoft _Spatializer deshabilita_ los efectos posteriores al espacializador de forma predeterminada. Para habilitar la reverberación y otros efectos para orígenes espacializados:
* Adjuntar el componente **Room Effect Send Level (Nivel de envío de efecto** de sala) a cada origen
* Ajuste la curva de nivel de envío de cada origen para controlar la ganancia en el audio enviado de vuelta al gráfico para el procesamiento de efectos.

Consulte [el capítulo 5 del tutorial del espacializador](tutorials/unity-spatial-audio-ch5.md) para obtener más información.

## <a name="unity-spatial-sound-examples"></a>Ejemplos de sonido espacial de Unity

Para obtener ejemplos de sonido espacial en Unity, consulte:
* [Demostraciones de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* El [proyecto de ejemplo de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra a la mitad de la exploración de los Mixed Reality de creación principales. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Texto](text-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también

* [Diseño de sonido en realidad mixta](../../design/spatial-sound-design.md)
* [Tutorial del espacializador de Microsoft](tutorials/unity-spatial-audio-ch1.md)
