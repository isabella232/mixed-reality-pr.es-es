---
title: Teleport Hotspot
description: Documentación sobre el componente teleport hotspot en MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema Teleport, zona de teleport
ms.openlocfilehash: 0cbdad3c038d457109077b742d3f453d63436ae4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144429"
---
# <a name="teleport-hotspot-experimental"></a>Teleport Hotspot [Experimental]

El punto de acceso de teleport es un componente que se puede agregar al objeto gameobject para asegurarse de que el usuario está en una determinada posición y orientación cuando se teletransporta a esa ubicación.

## <a name="usage"></a>Uso

### <a name="how-to-create-a-teleport-hotspot"></a>Creación de un punto de acceso de teleport

Para crear una zona de teleport, agregue el componente TeleportHotspot a un objeto que también tenga un componente de colisionador. 

![Componente teleport hotspot](../images/teleport/TeleportHotspotComponent.png)

Ahora, el indicador del puntero de teleport cambiará de color cuando se dirija a través de un TeleportHotspot. Cuando la acción de teleport se complete a través del punto de acceso, el usuario se teletransportará al centro de TeleportHotspot.

Si la marca de orientación de invalidación está desactivada, la orientación del usuario coincidirá con la del punto de acceso de teletransporte.

![Ejemplo de punto de acceso de teleport](../images/teleport/TeleportHotspotExample.gif)
