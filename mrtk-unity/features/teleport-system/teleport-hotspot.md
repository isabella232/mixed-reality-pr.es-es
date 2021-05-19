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
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="646c2-104">Teleport Hotspot [Experimental]</span><span class="sxs-lookup"><span data-stu-id="646c2-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="646c2-105">El punto de acceso de teleport es un componente que se puede agregar al objeto gameobject para asegurarse de que el usuario está en una determinada posición y orientación cuando se teletransporta a esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="646c2-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="646c2-106">Uso</span><span class="sxs-lookup"><span data-stu-id="646c2-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="646c2-107">Creación de un punto de acceso de teleport</span><span class="sxs-lookup"><span data-stu-id="646c2-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="646c2-108">Para crear una zona de teleport, agregue el componente TeleportHotspot a un objeto que también tenga un componente de colisionador.</span><span class="sxs-lookup"><span data-stu-id="646c2-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente teleport hotspot](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="646c2-110">Ahora, el indicador del puntero de teleport cambiará de color cuando se dirija a través de un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="646c2-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="646c2-111">Cuando la acción de teleport se complete a través del punto de acceso, el usuario se teletransportará al centro de TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="646c2-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="646c2-112">Si la marca de orientación de invalidación está desactivada, la orientación del usuario coincidirá con la del punto de acceso de teletransporte.</span><span class="sxs-lookup"><span data-stu-id="646c2-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Ejemplo de punto de acceso de teleport](../images/teleport/TeleportHotspotExample.gif)
