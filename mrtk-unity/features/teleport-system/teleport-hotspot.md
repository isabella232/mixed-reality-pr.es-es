---
title: TeleportHotspot
description: Documentación sobre el componente de zona Wi-Fi en MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK, sistema teletranspórtate, zona activa de teletransportar
ms.openlocfilehash: 986105dd771c38b1e26fd9f86df90224110591a4
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105582979"
---
# <a name="teleport-hotspot-experimental"></a>Zona activa de teletransportar [experimental]

La zona activa teletranspórtate es un componente que puede Agregar a su GameObject para asegurarse de que el usuario se encuentra en una determinada posición y orientación cuando se transporta a esa ubicación.

## <a name="usage"></a>Uso

### <a name="how-to-create-a-teleport-hotspot"></a>Creación de una zona activa de teletransportar

Para crear una zona activa teletranspórtate, agregue el componente TeleportHotspot a un objeto que también tenga un componente Colisionador. 

![Componente de zona activa de teletransportar](../images/teleport/TeleportHotspotComponent.png)

Ahora, el indicador del puntero teletranspórtate cambiará de color cuando se le dirija sobre un TeleportHotspot. Cuando la acción de teletransportar se completa sobre la zona activa, el usuario se transporta al centro de la TeleportHotspot.

Si la marca de orientación de invalidación está desactivada, la orientación del usuario coincidirá con la de la zona activa que se transporta.

![Ejemplo de zona interactiva de teletransportar](../images/teleport/TeleportHotspotExample.gif)
