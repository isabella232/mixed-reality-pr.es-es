---
title: Punto de acceso de teleport
description: Documentación sobre el componente teleport hotspot en MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema Teleport, zona de teleport
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 01ae900800c4a13ca7bafc3391ff51b752a95ae0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176203"
---
# <a name="teleport-hotspot"></a><span data-ttu-id="e5299-104">Punto de acceso de teleport</span><span class="sxs-lookup"><span data-stu-id="e5299-104">Teleport hotspot</span></span>

<span data-ttu-id="e5299-105">El punto de acceso de teleport es un componente que se puede agregar al objeto gameobject para asegurarse de que el usuario está en una posición y orientación determinadas cuando se teletransporta a esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="e5299-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="e5299-106">Uso</span><span class="sxs-lookup"><span data-stu-id="e5299-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="e5299-107">Creación de un punto de acceso de teleport</span><span class="sxs-lookup"><span data-stu-id="e5299-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="e5299-108">Para crear una zona de teleport, agregue el componente TeleportHotspot a un objeto que también tenga un componente de colisionador.</span><span class="sxs-lookup"><span data-stu-id="e5299-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente de punto de acceso de teleport](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="e5299-110">Ahora, el indicador del puntero de teleport cambiará de color cuando se dirija a través de un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="e5299-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="e5299-111">Cuando la acción de teleporte se complete a través del punto de acceso, el usuario se teletransportará al centro de TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="e5299-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="e5299-112">Si la marca de orientación de invalidación está desactivada, la orientación del usuario coincidirá con la del punto de acceso de teletransporte.</span><span class="sxs-lookup"><span data-stu-id="e5299-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Ejemplo de punto de acceso de teleport](../images/teleport/TeleportHotspotExample.gif)
