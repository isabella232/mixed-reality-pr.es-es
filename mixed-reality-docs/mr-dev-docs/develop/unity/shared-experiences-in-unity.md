---
title: Experiencias compartidas en Unity
description: Aprenda a compartir los mismos hologramas entre varios usuarios en una aplicación de Unity con Azure Spatial Anchors.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure Spatial Anchors, ASA, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: b9fdd09740dc6197c46a2d017f61e97898f213cd44bb504cbbf306f6a7ae21ec
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195927"
---
# <a name="shared-experiences-in-unity"></a>Experiencias compartidas en Unity

Una experiencia compartida permite que varios usuarios, cada uno con su propio dispositivo HoloLens, iOS o Android, puedan ver e interactuar colectivamente con el mismo holograma. Hologramas se sitúan en un punto fijo del espacio a través del uso compartido de delimitadores espaciales.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> anclajes espaciales duraderos con respaldo en la nube, que la aplicación puede localizar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común entre varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física. 

También puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia asincrónica de hologramas en HoloLens, iOS y Android.  Al compartir un anclaje espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

Para empezar a crear experiencias compartidas en Unity, pruebe los inicios rápidos de 5 minutos <a href="/azure/spatial-anchors/unity-overview" target="_blank">de Azure Spatial Anchors Unity.</a>

Una vez Spatial Anchors azure está configurado, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity.</a>

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se puede usar Azure Spatial Anchors, las transferencias de [delimitadores locales](../../out-of-scope/local-anchor-transfers-in-unity.md) permiten que un dispositivo HoloLens exporte un delimitador para que un segundo HoloLens pueda importarlo.  Este enfoque no se admite en dispositivos iOS y Android y proporciona una recuperación de anclaje menos sólida que Azure Spatial Anchors.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra en medio de la exploración de las API y las funcionalidades de Mixed Reality plataforma. Desde aquí, puede continuar con la sección siguiente:

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