---
title: Delimitadores espaciales compartidos en DirectX
description: Obtenga información sobre cómo sincronizar dos dispositivos de HoloLens compartiendo los delimitadores espaciales locales y de Azure en las aplicaciones de DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, sincronizar, delimitador espacial, transferencia, multijugador, vista, escenario, tutorial, código de ejemplo, Azure, delimitadores espaciales de Azure, ASA
ms.openlocfilehash: cf823809d1f6b9bf4bc44a6aa1e8f0e16fd76a16
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583106"
---
# <a name="shared-experiences-in-directx"></a>Experiencias compartidas en DirectX

> [!NOTE]
> Este artículo está relacionado con las API nativas de WinRT heredadas.  En el caso de los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](../native/openxr-getting-started.md)**.

Una experiencia compartida es aquella en la que varios usuarios con sus propios dispositivos HoloLens, iOS o Android, ven colectivamente el mismo holograma e interactúan con él. El holograma se coloca en un punto fijo en el espacio mediante el uso compartido del delimitador espacial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Puede usar <a href="/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para crear delimitadores espaciales con respaldo en la nube duraderos, que la aplicación puede encontrar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

También puede usar <a href="/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para la persistencia asincrónica de hologramas en dispositivos de HoloLens, iOS y Android.  Al compartir un delimitador espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

Para empezar a crear experiencias compartidas en la aplicación de HoloLens, pruebe la guía de inicio rápido de HoloLens de 5 minutos de <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">delimitadores espaciales de Azure</a>.

Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">crear y buscar delimitadores en HoloLens</a>.  También hay tutoriales disponibles para <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , lo que le permite compartir los mismos delimitadores en todos los dispositivos.

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se pueden usar delimitadores espaciales de Azure, las [transferencias de delimitadores locales](../../out-of-scope/local-anchor-transfers-in-directx.md) permiten que un dispositivo hololens exporte un anclaje para que lo importe un segundo dispositivo hololens.  Este enfoque proporciona una recuperación de delimitador menos sólida que los delimitadores espaciales de Azure, y los dispositivos iOS y Android no son compatibles con este enfoque.

## <a name="see-also"></a>Consulte también

* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de anclajes espaciales de Azure para HoloLens</a>