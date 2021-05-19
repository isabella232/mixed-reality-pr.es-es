---
title: Introducción al sistema de teleportar
description: Información general sobre cómo habilitar y deshabilitar el sistema teleport en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, teleport system,
ms.openlocfilehash: a44ad1827597dd0b27bc88a9420a3b251f934afd
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144143"
---
# <a name="teleport-system"></a><span data-ttu-id="8d789-104">Sistema de teletransporte</span><span class="sxs-lookup"><span data-stu-id="8d789-104">Teleport System</span></span>

<span data-ttu-id="8d789-105">El sistema de teletransporte es un subsistente de MRTK que controla la teleportación del usuario cuando la aplicación usa una pantalla opaca.</span><span class="sxs-lookup"><span data-stu-id="8d789-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="8d789-106">En el caso de las experiencias de AR (como HoloLens), el sistema de teleportación no está activo.</span><span class="sxs-lookup"><span data-stu-id="8d789-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="8d789-107">Para las experiencias DE HMD envolventes (OpenVR, WMR), se puede habilitar el sistema de teleportado.</span><span class="sxs-lookup"><span data-stu-id="8d789-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="8d789-108">Habilitación y deshabilitación</span><span class="sxs-lookup"><span data-stu-id="8d789-108">Enabling and disabling</span></span>

<span data-ttu-id="8d789-109">El sistema de teletransporte se puede habilitar o deshabilitar activando la casilla en su perfil.</span><span class="sxs-lookup"><span data-stu-id="8d789-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="8d789-110">Para ello, seleccione el objeto MixedRealityToolkit en la escena, haga clic en "Teleport" y, a continuación, active la casilla "Habilitar teleport system".</span><span class="sxs-lookup"><span data-stu-id="8d789-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="8d789-111">Esto también se puede hacer en tiempo de ejecución:</span><span class="sxs-lookup"><span data-stu-id="8d789-111">This can also be done at runtime:</span></span>

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a><span data-ttu-id="8d789-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="8d789-112">Events</span></span>

<span data-ttu-id="8d789-113">El sistema de teletransporte expone eventos a través de la interfaz para proporcionar señales sobre cuándo comienzan, finalizan o se cancelan [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) las acciones de teleport.</span><span class="sxs-lookup"><span data-stu-id="8d789-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="8d789-114">Consulte la documentación de la API vinculada para obtener más detalles sobre la mecánica de los eventos y su carga asociada.</span><span class="sxs-lookup"><span data-stu-id="8d789-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="8d789-115">Uso</span><span class="sxs-lookup"><span data-stu-id="8d789-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="8d789-116">Registro de eventos de teleportación</span><span class="sxs-lookup"><span data-stu-id="8d789-116">How to register for teleportation events</span></span>

<span data-ttu-id="8d789-117">El código siguiente muestra cómo crear un MonoBehaviour que escuchará los eventos de teleportación.</span><span class="sxs-lookup"><span data-stu-id="8d789-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="8d789-118">En este código se da por supuesto que el sistema de teleportado está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8d789-118">This code assumes that the teleport system is enabled.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="8d789-119">Teleporting on MRTK</span><span class="sxs-lookup"><span data-stu-id="8d789-119">Teleporting on MRTK</span></span>

<span data-ttu-id="8d789-120">Para teleportar con un controlador en dispositivos de MR con configuraciones predeterminadas, use la huella digital.</span><span class="sxs-lookup"><span data-stu-id="8d789-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="8d789-121">Para teleportar con las manos articuladas, haga un gesto con la mano con la mano hacia arriba con el índice y el control de posición hacia fuera, para lo que debe completar el teleporte rizado del dedo índice.</span><span class="sxs-lookup"><span data-stu-id="8d789-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="8d789-122">Para teleportar con la simulación de entrada, consulte la documentación actualizada [del servicio de simulación de entrada](../input-simulation/input-simulation-service.md).</span><span class="sxs-lookup"><span data-stu-id="8d789-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Gesto de teleportar](../images/teleport/handteleport.gif)