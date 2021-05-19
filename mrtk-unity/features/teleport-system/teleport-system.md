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
# <a name="teleport-system"></a>Sistema de teletransporte

El sistema de teletransporte es un subsistente de MRTK que controla la teleportación del usuario cuando la aplicación usa una pantalla opaca. En el caso de las experiencias de AR (como HoloLens), el sistema de teleportación no está activo. Para las experiencias DE HMD envolventes (OpenVR, WMR), se puede habilitar el sistema de teleportado.

## <a name="enabling-and-disabling"></a>Habilitación y deshabilitación

El sistema de teletransporte se puede habilitar o deshabilitar activando la casilla en su perfil.
Para ello, seleccione el objeto MixedRealityToolkit en la escena, haga clic en "Teleport" y, a continuación, active la casilla "Habilitar teleport system".

Esto también se puede hacer en tiempo de ejecución:

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

## <a name="events"></a>Eventos

El sistema de teletransporte expone eventos a través de la interfaz para proporcionar señales sobre cuándo comienzan, finalizan o se cancelan [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) las acciones de teleport.
Consulte la documentación de la API vinculada para obtener más detalles sobre la mecánica de los eventos y su carga asociada.

## <a name="usage"></a>Uso

### <a name="how-to-register-for-teleportation-events"></a>Registro de eventos de teleportación

El código siguiente muestra cómo crear un MonoBehaviour que escuchará los eventos de teleportación. En este código se da por supuesto que el sistema de teleportado está habilitado.

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

## <a name="teleporting-on-mrtk"></a>Teleporting on MRTK

Para teleportar con un controlador en dispositivos de MR con configuraciones predeterminadas, use la huella digital. Para teleportar con las manos articuladas, haga un gesto con la mano con la mano hacia arriba con el índice y el control de posición hacia fuera, para lo que debe completar el teleporte rizado del dedo índice. Para teleportar con la simulación de entrada, consulte la documentación actualizada [del servicio de simulación de entrada](../input-simulation/input-simulation-service.md).

  ![Gesto de teleportar](../images/teleport/handteleport.gif)