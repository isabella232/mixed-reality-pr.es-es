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
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="e15ae-104">Zona activa de teletransportar [experimental]</span><span class="sxs-lookup"><span data-stu-id="e15ae-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="e15ae-105">La zona activa teletranspórtate es un componente que puede Agregar a su GameObject para asegurarse de que el usuario se encuentra en una determinada posición y orientación cuando se transporta a esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="e15ae-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="e15ae-106">Uso</span><span class="sxs-lookup"><span data-stu-id="e15ae-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="e15ae-107">Creación de una zona activa de teletransportar</span><span class="sxs-lookup"><span data-stu-id="e15ae-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="e15ae-108">Para crear una zona activa teletranspórtate, agregue el componente TeleportHotspot a un objeto que también tenga un componente Colisionador.</span><span class="sxs-lookup"><span data-stu-id="e15ae-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Componente de zona activa de teletransportar](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="e15ae-110">Ahora, el indicador del puntero teletranspórtate cambiará de color cuando se le dirija sobre un TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="e15ae-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="e15ae-111">Cuando la acción de teletransportar se completa sobre la zona activa, el usuario se transporta al centro de la TeleportHotspot.</span><span class="sxs-lookup"><span data-stu-id="e15ae-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="e15ae-112">Si la marca de orientación de invalidación está desactivada, la orientación del usuario coincidirá con la de la zona activa que se transporta.</span><span class="sxs-lookup"><span data-stu-id="e15ae-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Ejemplo de zona interactiva de teletransportar](../images/teleport/TeleportHotspotExample.gif)
