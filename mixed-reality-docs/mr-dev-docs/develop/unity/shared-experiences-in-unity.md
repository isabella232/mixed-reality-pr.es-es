---
title: Experiencias compartidas en Unity
description: Aprenda a compartir los mismos hologramas entre varios usuarios en una aplicación de Unity con Azure Spatial Anchors.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure Spatial Anchors, ASA, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: f7725c8282d1b5a93d555ac0f55ee936b910ff6c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244183"
---
# <a name="shared-experiences-in-unity"></a>Experiencias compartidas en Unity

Una experiencia compartida permite que varios usuarios, cada uno con su propio dispositivo HoloLens, iOS o Android, puedan ver e interactuar colectivamente con el mismo holograma. Hologramas se sitúan en un punto fijo del espacio a través del uso compartido de delimitadores espaciales.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

### <a name="automated-with-world-locking-tools"></a>Automatizado con World Locking Tools

Al igual que con los delimitadores locales, World Locking Tools puede usar un grupo de Azure Spatial Anchors para bloquear espacios de coordenadas completos en relación con el mundo físico, en lugar de usar delimitadores individuales para bloquear objetos individuales. El bloqueo de todo el espacio no solo proporciona un entorno más propicio para un diseño preciso, sino que también es más eficaz tanto en tiempo de desarrollo como en recursos en tiempo de ejecución.

Para obtener más información y ejemplos que aprovechan Azure Spatial Anchors para compartir sistemas de coordenadas entre dispositivos HoloLens, Android e iOS, así como conservar espacios entre sesiones, consulte la documentación de [World Locking Tools](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html).

### <a name="manual-configuration-of-azure-spatial-anchors"></a>Configuración manual de Azure Spatial Anchors

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> anclajes espaciales duraderos con respaldo en la nube que la aplicación puede encontrar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común entre varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.

También puede usar Azure Spatial Anchors para <a href="/azure/spatial-anchors/overview" target="_blank">la</a> persistencia asincrónica de hologramas en HoloLens, iOS y Android.  Al compartir un anclaje espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

Para empezar a crear experiencias compartidas en Unity, pruebe los inicios rápidos de 5 minutos <a href="/azure/spatial-anchors/unity-overview" target="_blank">de Azure Spatial Anchors Unity.</a>

Una vez Spatial Anchors azure está configurado, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity.</a>

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se puede usar Azure Spatial Anchors, las transferencias de [delimitadores locales](../../out-of-scope/local-anchor-transfers-in-unity.md) permiten que un dispositivo HoloLens exporte un delimitador para que un segundo HoloLens pueda importarlo.  Este enfoque no se admite en dispositivos iOS y Android y proporciona una recuperación de anclaje menos sólida que Azure Spatial Anchors.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, está en la antes de explorar las API y las funcionalidades de Mixed Reality plataforma. Desde aquí, puede continuar con la sección siguiente:

> [!div class="nextstepaction"]
> [Cámara localizable](locatable-camera-in-unity.md)

O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:

> [!div class="nextstepaction"]
> [Implementación en HoloLens o Windows Mixed Reality cascos envolventes](../platform-capabilities-and-apis/using-visual-studio.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#3-advanced-features) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Experiencias compartidas en realidad mixta](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK Spatial Anchors Azure para Unity</a>