---
title: Anclajes espaciales en Unity
description: Obtenga información sobre cómo crear, almacenar y obtener delimitadores espaciales en aplicaciones de realidad mixta de Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, anclajes espaciales, almacenamiento delimitado, HoloLens, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623625"
---
# <a name="spatial-anchors-in-unity"></a>Anclajes espaciales en Unity

Los delimitadores espaciales guardan los hologramas en el espacio real entre las sesiones de la aplicación. Una vez guardada en el almacén de delimitadores de HoloLens, se pueden encontrar y cargar en sesiones diferentes y es una alternativa ideal cuando no hay conectividad a Internet.

> [!IMPORTANT]
> Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube. Si desea usar servicios en la nube de Azure para almacenar los anclajes, existe un documento que le guiará por la integración de [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors). Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.

## <a name="understanding-anchors"></a>Descripción de los delimitadores

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>Usar AnchorStore

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de realidad mixta. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Asignación espacial](spatial-mapping-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Persistencia del delimitador espacial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a>
* [Escalas de experiencia](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Pérdida de seguimiento en Unity](tracking-loss-in-unity.md)
* [Delimitadores espaciales](../../design/spatial-anchors.md)
* [Experiencias compartidas en Unity](shared-experiences-in-unity.md)