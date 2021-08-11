---
title: Delimitadores espaciales compartidos en DirectX
description: Aprenda a sincronizar dos dispositivos HoloLens mediante el uso compartido de anclajes espaciales locales y de Azure en aplicaciones DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, synchronize, spatial anchor, transfer, multiplayer, view, scenario, walkthrough, sample code, Azure, Azure Spatial Anchors, ASA
ms.openlocfilehash: df78d9e2477fe377d61d2f2c13fc35e0a25b0b2cc37eeb883a69d2041fe42f9b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193549"
---
# <a name="shared-experiences-in-directx"></a>Experiencias compartidas en DirectX

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](../native/openxr-getting-started.md)**.

Una experiencia compartida es una en la que varios usuarios con su propio dispositivo HoloLens, iOS o Android ven colectivamente e interactúan con el mismo holograma. El holograma se coloca en un punto fijo del espacio mediante el uso compartido de delimitadores espaciales.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para crear anclajes espaciales duraderos basados en la nube, que la aplicación puede localizar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común entre varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

También puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia asincrónica de hologramas en HoloLens, iOS y Android.  Al compartir un anclaje espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

Para empezar a crear experiencias compartidas en HoloLens aplicación, pruebe la guía de inicio rápido de <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">5</a>minutos de Azure Spatial Anchors HoloLens .

Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear y buscar <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">delimitadores en HoloLens</a>.  También hay tutoriales disponibles <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">para Android e iOS,</a> lo que le permite compartir los mismos anclajes en todos los dispositivos.

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se puede usar Azure Spatial Anchors, las transferencias de [delimitadores locales](../../out-of-scope/local-anchor-transfers-in-directx.md) permiten que un dispositivo HoloLens exporte un delimitador para que lo importe un segundo HoloLens dispositivo.  Este enfoque proporciona una recuperación de anclaje menos sólida que Azure Spatial Anchors, y este enfoque no admite dispositivos iOS y Android.

## <a name="see-also"></a>Consulte también

* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de Azure Spatial Anchors para HoloLens</a>