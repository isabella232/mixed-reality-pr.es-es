---
title: Delimitadores espaciales compartidos en DirectX
description: Aprenda a sincronizar dos dispositivos HoloLens mediante el uso compartido de anclajes espaciales locales y de Azure en aplicaciones DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, synchronize, spatial anchor, transfer, multiplayer, view, scenario, walkthrough, sample code, Azure, Azure Spatial Anchors, ASA
ms.openlocfilehash: 6b1b98539c05849064f1c33ed859bc925ed5fd31
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244329"
---
<!--Unity Note: No Unity specific content in this article. -->
# <a name="shared-experiences-in-directx"></a>Experiencias compartidas en DirectX

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR.](../native/openxr-getting-started.md)**

Una experiencia compartida es en la que varios usuarios con su propio dispositivo HoloLens, iOS o Android, ven colectivamente e interactúan con el mismo holograma. El holograma se coloca en un punto fijo del espacio mediante el uso compartido de delimitadores espaciales.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para crear anclajes espaciales duraderos basados en la nube, que la aplicación puede encontrar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común entre varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

También puede usar Azure Spatial Anchors para <a href="/azure/spatial-anchors/overview" target="_blank">la</a> persistencia asincrónica de hologramas en HoloLens, iOS y Dispositivos Android.  Al compartir un anclaje espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

Para empezar a crear experiencias compartidas en HoloLens aplicación, pruebe la guía de inicio rápido de 5 minutos <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Spatial Anchors HoloLens Azure.</a>

Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear y localizar <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">anclajes</a>en HoloLens .  Los tutoriales también están <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">disponibles para Android e iOS,</a> lo que le permite compartir los mismos anclajes en todos los dispositivos.

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se puede usar Azure Spatial Anchors, las transferencias de anclaje [local](../../out-of-scope/local-anchor-transfers-in-directx.md) permiten que un dispositivo HoloLens exporte un delimitador para importarlo un segundo HoloLens dispositivo.  Este enfoque proporciona una recuperación de anclaje menos sólida que azure Spatial Anchors, y este enfoque no admite dispositivos iOS y Android.

## <a name="see-also"></a>Consulte también

* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de Azure Spatial Anchors para HoloLens</a>