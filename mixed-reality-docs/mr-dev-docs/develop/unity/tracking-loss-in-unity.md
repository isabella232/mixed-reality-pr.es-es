---
title: Pérdida de seguimiento en Unity
description: Obtenga información sobre cómo controlar la pérdida de seguimiento manual y predeterminada dentro de una aplicación de realidad mixta de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, pérdida de seguimiento, imagen de pérdida de seguimiento, sondeo, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: fe11c88bec60042901bd7ebb5c55116da97b6e28f0e44e889ef517a03d67245a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211357"
---
# <a name="tracking-loss-in-unity"></a>Pérdida de seguimiento en Unity

Cuando el dispositivo no se encuentra en el mundo, la aplicación experimenta "pérdida de seguimiento". De forma predeterminada, Unity pausará el bucle de actualización y mostrará una imagen de presentación al usuario cada vez que se pierda el seguimiento. Una vez recuperado el seguimiento, la imagen de presentación desaparece y el bucle de actualización continúa.

Como alternativa, el usuario puede controlar manualmente esta transición si no lo hace. Todo el contenido parecerá estar bloqueado durante la pérdida de seguimiento si no se hace nada para controlarlo.

## <a name="default-handling"></a>Control predeterminado

El bucle de actualización y todos los mensajes y eventos se detendrán mientras dure el seguimiento de la pérdida de forma predeterminada. Al mismo tiempo, se mostrará una imagen al usuario. Para personalizar esta imagen, vaya a Edit->Configuración->Player ,haga clic en Splash Image (Imagen de presentación) y establecerá la imagen Holographic Tracking Loss (Pérdida de seguimiento holográfico).

## <a name="manual-handling"></a>Control manual

Para controlar manualmente la pérdida de seguimiento, debe ir a la pestaña Editar configuración de la plataforma universal de Windows de Project Configuración Player Windows y desactivar  >    >    >    >    >  "On Tracking Loss Pause and Show Image". Después, debe controlar los cambios de seguimiento con las API especificadas a continuación.

**Espacio de nombres:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldManager*

* World Manager expone un evento para detectar el seguimiento perdido o obtenido (*WorldManager.OnPositionalLocatorStateChanged*) y una propiedad para consultar el estado actual (*WorldManager.state*)
* Cuando el estado de seguimiento no está activo, la cámara no parecerá traducirse en el mundo virtual aunque el usuario lo traduzca. Los objetos ya no se corresponderán con ninguna ubicación física y todos aparecerán bloqueados.

Al controlar los cambios de seguimiento por su cuenta, debe sondear la propiedad de estado de cada fotograma o controlar el evento *OnPositionalLocatorStateChanged.*

### <a name="polling"></a>Sondeo

El estado más importante es *PositionalLocatorState.Active,* lo que significa que el seguimiento es totalmente funcional. Cualquier otro estado dará como resultado solo diferencias de rotación en la cámara principal. Por ejemplo:

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Control del evento OnPositionalLocatorStateChanged

Más cómodamente, también puede suscribirse a *OnPositionalLocatorStateChanged* para controlar las transiciones:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>Consulte también

* [Control de la pérdida de seguimiento en DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
