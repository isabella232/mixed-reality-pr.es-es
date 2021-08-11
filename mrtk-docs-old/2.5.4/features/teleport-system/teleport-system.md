---
title: TeleportSystemOverview
description: Información general sobre la habilitación y deshabilitación del sistema de teletransporte en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK, sistema de teletransporte
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197645"
---
# <a name="teleport-system"></a>Sistema de teletransporte

El sistema de teletransporte es un subsistente de MRTK que controla el teletransporte del usuario cuando la aplicación está usando una pantalla opaca. En el caso de las experiencias de AR (como HoloLens), el sistema de teletransporte no está activo. Para disfrutar de experiencias de HMD envolventes (OpenVR, WMR), se puede habilitar el sistema de teletransporte.

## <a name="enabling-and-disabling"></a>Habilitación y deshabilitación

Para habilitar o deshabilitar el sistema de teletransporte, puede activar o desactivar la casilla en su perfil.
Para ello, seleccione el objeto MixedRealityToolkit en la escena, haga clic en "Teletransportar" y, a continuación, active la casilla "Enable Teleport System" (Habilitar el sistema de teletransporte).

Esto también puede hacerse en el entorno en tiempo de ejecución:

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

El sistema de teletransporte expone eventos a través de la interfaz [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) para proporcionar señales de cuándo comienzan, finalizan o se cancelan las acciones de teletransporte.
Consulte la documentación vinculada sobre la API para obtener más detalles sobre la mecánica de los eventos y su carga asociada.

## <a name="usage"></a>Uso

### <a name="how-to-register-for-teleportation-events"></a>Registro de eventos de teletransporte

El código siguiente muestra cómo crear una clase MonoBehaviour que escuchará los eventos de teletransporte. En este código se da por supuesto que el sistema de teletransporte está habilitado.

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
