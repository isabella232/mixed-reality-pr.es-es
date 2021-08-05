---
title: Bloqueo mundial y anclajes espaciales en Unity
description: Aprenda a usar World Locking Tools y anclajes espaciales en aplicaciones de realidad mixta de Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity, anclajes espaciales, almacén de anclajes, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, herramientas de bloqueo mundial, hologramas
ms.openlocfilehash: 34ef74ab968bff04188b1010eb4c863fd73d76ee6b1dd8a0bd89c7d4232a2be9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208888"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Bloqueo mundial y anclajes espaciales en Unity

![Imagen principal de las herramientas de bloqueo mundial](images/wlt-img-01.jpeg)

Conseguir que los hologramas permanezcan en su lugar, moverse con usted o, en algunos casos, colocarse en relación con otros hologramas es una gran parte de la creación de Mixed Reality aplicaciones. Este artículo le llevará por nuestra solución recomendada mediante World Locking Tools, pero también se trata la configuración manual de anclajes espaciales en los proyectos de Unity. Antes de entrar en cualquier código, es importante comprender cómo Unity controla el espacio de coordenadas y los anclajes en su propio motor.

## <a name="world-scale-coordinate-systems"></a>Sistemas de coordenadas a escala mundial

En la actualidad, al escribir juegos, aplicaciones de visualización de datos  o aplicaciones de realidad virtual, el enfoque típico es establecer un sistema de coordenadas universal absoluto al que todas las demás coordenadas puedan volver a asignarse de forma confiable. En ese entorno, siempre puede encontrar una transformación estable que defina una relación entre dos objetos cualquiera en ese mundo. Si no movió esos objetos, sus transformaciones relativas siempre seguirán siendo las mismas. Este tipo de sistema de coordenadas global es fácil de obtener cuando se representa un mundo puramente virtual en el que se conoce toda la geometría de antemano. En la actualidad, las aplicaciones de realidad virtual a escala de sala suelen establecer este tipo de sistema de coordenadas de escala de habitación absoluto con su origen en la planta.

En cambio, un dispositivo de realidad mixta sin ateso, como HoloLens, tiene una comprensión dinámica controlada por sensores del mundo, ajustando continuamente sus conocimientos con el tiempo del entorno del usuario a medida que atraviesan muchos metros a través de una planta completa de un edificio. En una experiencia a escala mundial, si colocaste todos los hologramas en un sistema de coordenadas rígidas naïve, esos hologramas acabarían desviando con el tiempo, ya sea en función del mundo o en relación entre sí.

Por ejemplo, el casco puede pensar actualmente que dos ubicaciones del mundo están a 4 metros de distancia y, después, refinar esa comprensión, aprendiendo que las ubicaciones están de hecho a 3,9 metros de distancia. Si esos hologramas se hubieran colocado inicialmente a 4 metros de distancia en un único sistema de coordenadas rígidas, uno de ellos siempre aparecería a 0,1 metros del mundo real.

Puede colocar manualmente **anclajes** espaciales en Unity para mantener la posición de un holograma en el mundo físico cuando el usuario es móvil; sin embargo, esto sacrificará la coherencia dentro del mundo virtual. Los distintos anclajes se mueven constantemente en relación entre sí y también se mueven a través del espacio de coordenadas global. En este escenario, tareas sencillas como el diseño se vuelven difíciles y la simulación física es problemática.

**World Locking Tools** le ofrece lo mejor de ambos mundos, estabilizando un único sistema de coordenadas rígidas mediante un suministro interno de anclajes espaciales distribuidos por toda la escena virtual a medida que el usuario se mueve. Las herramientas analizan las coordenadas de la cámara y los anclajes espaciales en cada fotograma. En lugar de cambiar las coordenadas de todo el mundo para compensar las correcciones en las coordenadas de la cabeza del usuario, las herramientas simplemente corrigen las coordenadas de la cabeza en su lugar.

## <a name="choosing-your-world-locking-approach"></a>Elección del enfoque de bloqueo del mundo

* **Nuestra recomendación** es usar **World Locking Tools para** todas las necesidades de posicionamiento del holograma. 
    * World Locking Tools proporciona un sistema de coordenadas estable que minimiza las incoherencias visibles entre los marcadores virtuales y reales. Dicho de otro modo, bloquea toda la escena con un grupo compartido de delimitadores, en lugar de bloquear cada grupo de objetos con el propio delimitador individual del grupo.
* **Para Unity 2019/2020 mediante OpenXR** o el complemento XR de Windows , debe usar **ARAnchorManager.**
* **Para versiones anteriores de Unity o proyectos de WSA,** debe usar **WorldAnchor.**

## <a name="setting-up-world-locking"></a>Configuración del bloqueo mundial 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>Bloqueo del mundo persistente

Los delimitadores espaciales ahorran hologramas en el espacio real entre sesiones de aplicación. Una vez guardados en el almacén de anclajes de HoloLens, se pueden encontrar y cargar en sesiones diferentes y son una reserva ideal cuando no hay conectividad a Internet.

> [!IMPORTANT]
> Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube. Si desea usar servicios en la nube de Azure para almacenar los anclajes, existe un documento que le guiará por la integración de [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors). Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>Uso compartido de espacios de coordenadas 

Si desea compartir un espacio de coordenadas bloqueado en el mundo, consulte la documentación completa [de la experiencia compartida](shared-experiences-in-unity.md).

Tenga en cuenta que Azure Spatial Anchors todavía no se admite directamente en World Locking Tools, por lo que las experiencias compartidas requerirán que cree manualmente anclajes espaciales.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido del punto de control de desarrollo de Unity que hemos diseñado, se encuentra a punto de explorar Mixed Reality bloques de creación principales. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Asignación espacial](spatial-mapping-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Introducción a World Locking Tools](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [Guías de inicio rápido](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [Tutoriales](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [Muestras](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [Persistencia del delimitador espacial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de Azure Spatial Anchors para Unity</a>
* [Escalas de experiencia](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Pérdida de seguimiento en Unity](tracking-loss-in-unity.md)
* [Delimitadores espaciales](../../design/spatial-anchors.md)
* [Experiencias compartidas en Unity](shared-experiences-in-unity.md)
