---
title: Punto de acceso de teletransporte
description: Documentación sobre el componente teleport hotspot en MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema Teleport, zona de teleport
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 755b0e8f53be2f393b52395309ed9ab0fad96cadc2e4289400cfff45a99aa6a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189468"
---
# <a name="teleport-hotspot"></a>Punto de acceso de teletransporte

El punto de acceso de teleport es un componente que se puede agregar al objeto gameobject para asegurarse de que el usuario está en una determinada posición y orientación cuando se teletransporta a esa ubicación.

## <a name="usage"></a>Uso

### <a name="how-to-create-a-teleport-hotspot"></a>Creación de un punto de acceso de teleport

Para crear una zona de teleport, agregue el componente TeleportHotspot a un objeto que también tenga un componente de colisionador. 

![Componente de punto de acceso de teleport](../images/teleport/TeleportHotspotComponent.png)

Ahora, el indicador del puntero de teleport cambiará de color cuando se dirija a través de un TeleportHotspot. Cuando la acción de teleport se complete a través del punto de acceso, el usuario se teletransportará al centro de TeleportHotspot.

Si la marca de orientación de invalidación está desactivada, la orientación del usuario coincidirá con la del punto de acceso de teletransporte.

![Ejemplo de punto de acceso de teleport](../images/teleport/TeleportHotspotExample.gif)
