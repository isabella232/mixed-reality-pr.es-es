---
title: Pérdida de seguimiento en Unity
description: Obtenga información sobre cómo controlar la pérdida de seguimiento manual y predeterminado en una aplicación de Unity Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, pérdida de seguimiento, imagen de pérdida de seguimiento, sondeo, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009855"
---
# <a name="tracking-loss-in-unity"></a>Pérdida de seguimiento en Unity

Cuando el dispositivo no se encuentra en el mundo, la aplicación experimenta "pérdida de seguimiento". De forma predeterminada, Unity pausará el bucle de actualización y mostrará una imagen de bienvenida al usuario en cualquier momento en que se pierda el seguimiento. Una vez que se recupera el seguimiento, la imagen de la pantalla de presentación desaparece y el bucle de actualización continúa.

Como alternativa, el usuario puede controlar manualmente esta transición mediante la opción de configuración. Todo el contenido parecerá quedar bloqueado durante la pérdida del seguimiento si no se hace nada para controlarlo.

## <a name="default-handling"></a>Control predeterminado

El bucle de actualización y todos los mensajes y eventos se detendrán por la duración de la pérdida de seguimiento de forma predeterminada. Al mismo tiempo, se mostrará una imagen al usuario. Puede personalizar esta imagen; para ello, vaya a editar >Configuración->Player, haga clic en imagen de bienvenida y establezca la imagen de pérdida del seguimiento de holográfica.

## <a name="manual-handling"></a>Control manual

Para controlar manualmente la pérdida de seguimiento, debe ir a **Editar**  >  **configuración de proyecto**  >    >  **plataforma universal de Windows de la pestaña Configuración**  >  de la **imagen de bienvenida**  >  de **Windows Holographic** y desactive "en el seguimiento de pérdida pausar y Mostrar imagen". Después, debe controlar los cambios de seguimiento con las API especificadas a continuación.

**Espacio de nombres:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldManager*

* El administrador mundial expone un evento para detectar el seguimiento perdido/ganado (*WorldManager. OnPositionalLocatorStateChanged*) y una propiedad para consultar el estado actual (*WorldManager. State*)
* Cuando el estado de seguimiento no está activo, la cámara no parece traducirse en el mundo virtual, ni siquiera cuando el usuario se traduce. Los objetos dejarán de corresponder a cualquier ubicación física y todos aparecerán como cuerpo bloqueado.

Al controlar los cambios de seguimiento por su cuenta, debe sondear la propiedad State de cada fotograma o controlar el evento *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Sondeo

El estado más importante es *PositionalLocatorState. Active*, lo que significa que el seguimiento es totalmente funcional. Cualquier otro estado solo producirá diferencias de rotación en la cámara principal. Por ejemplo:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Controlar el evento OnPositionalLocatorStateChanged

Además, también puede suscribirse a *OnPositionalLocatorStateChanged* para controlar las transiciones:

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
