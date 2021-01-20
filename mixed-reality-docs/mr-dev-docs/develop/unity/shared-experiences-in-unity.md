---
title: Experiencias compartidas en Unity
description: Aprenda a compartir los mismos hologramas entre varios usuarios de una aplicación de Unity con los delimitadores espaciales de Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Uso compartido, delimitador, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, anclajes espaciales de Azure, ASA, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 7762a76e1eaa944f69153b13fb0f380c7dce643e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583360"
---
# <a name="shared-experiences-in-unity"></a>Experiencias compartidas en Unity

Una experiencia compartida permite que varios usuarios, cada uno con sus propios dispositivos HoloLens, iOS o Android, vean el mismo holograma e interactúen con él de forma colectiva. Los hologramas se colocan en un punto fijo en el espacio a través del uso compartido del delimitador espacial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Los <a href="/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> crean delimitadores espaciales con respaldo en la nube duraderos, que la aplicación puede ubicar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física. 

También puede usar <a href="/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para la persistencia asincrónica de hologramas en dispositivos de HoloLens, iOS y Android.  Al compartir un delimitador espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.

Una vez configurados los anclajes espaciales de Azure, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se pueden usar delimitadores espaciales de Azure, las [transferencias de delimitadores locales](../../out-of-scope/local-anchor-transfers-in-unity.md) permiten que un dispositivo hololens exporte un delimitador para que una segunda HoloLens pueda importarlo.  Este enfoque no se admite en dispositivos iOS y Android, y proporciona una recuperación de delimitador menos sólida que los delimitadores espaciales de Azure.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar las API y funcionalidades de la plataforma de realidad mixta. Desde aquí, puede continuar con la siguiente sección:

> [!div class="nextstepaction"]
> [Cámara localizable](locatable-camera-in-unity.md)

O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:

> [!div class="nextstepaction"]
> [Implementación en HoloLens o con auriculares de Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#3-advanced-features) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Experiencias compartidas en realidad mixta](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a>