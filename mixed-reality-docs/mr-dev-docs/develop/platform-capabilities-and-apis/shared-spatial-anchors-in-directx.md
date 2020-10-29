---
title: Delimitadores espaciales compartidos en DirectX
description: Explica cómo sincronizar dos dispositivos HoloLens compartiendo los delimitadores espaciales.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, sincronizar, delimitador espacial, transferencia, multijugador, vista, escenario, tutorial, código de ejemplo, Azure, delimitadores espaciales de Azure, ASA
ms.openlocfilehash: 2d6485e46a9802e1ee7e5adc12d6e0d026c79ae9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692015"
---
# <a name="shared-experiences-in-directx"></a>Experiencias compartidas en DirectX

> [!NOTE]
> Este artículo está relacionado con las API nativas de WinRT heredadas.  En el caso de los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](../native/openxr-getting-started.md)** .

Una experiencia compartida es aquella en la que varios usuarios, cada uno con sus propios dispositivos HoloLens, iOS o Android, ven colectivamente e interactúan con el mismo holograma que se coloca en un punto fijo en el espacio. Esto se logra mediante el uso compartido del delimitador espacial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para crear delimitadores espaciales con respaldo en la nube duraderos, que la aplicación puede encontrar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

También se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia de hologramas asincrónicos en dispositivos Android, iOS y HoloLens.  Al compartir un delimitador espacial en la nube duradera, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, aunque los dispositivos no estén presentes juntos simultáneamente.

Para empezar a crear experiencias compartidas en la aplicación de HoloLens, pruebe la guía de inicio rápido de HoloLens de 5 minutos de <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">delimitadores espaciales de Azure</a>.

Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">crear y buscar delimitadores en HoloLens</a>.  También hay tutoriales disponibles para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , lo que le permite compartir los mismos delimitadores en todos los dispositivos.

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se pueden usar delimitadores espaciales de Azure, las [transferencias de delimitadores locales](../../out-of-scope/local-anchor-transfers-in-directx.md) permiten que un dispositivo hololens exporte un delimitador para que lo importe un segundo dispositivo hololens.  Tenga en cuenta que este enfoque proporciona una recuperación de delimitador menos sólida que los delimitadores espaciales de Azure, y los dispositivos iOS y Android no son compatibles con este enfoque.

## <a name="see-also"></a>Consulte también
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de anclajes espaciales de Azure para HoloLens</a>