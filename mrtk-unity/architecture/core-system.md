---
title: Sistema principal
description: Sistema de entrada, administradores de dispositivos y proveedores de datos en MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, eventos
ms.openlocfilehash: 79ebd3855cd991db168233f00058ab5d42f87d83
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121604"
---
# <a name="core-system"></a>Sistema principal

En el centro del sistema de entrada se encuentra [InputSystem](../features/input/overview.md), que es un servicio que es responsable de inicializar y operar toda la funcionalidad relacionada con la entrada asociada a MRTK.

> [!NOTE]
> Se supone que los lectores ya han leído y tienen un conocimiento básico de la [sección de terminología.](terminology.md)

Este servicio es responsable de:

- Lectura del perfil [del sistema de entrada](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Iniciar los proveedores [de datos configurados](../features/input/input-providers.md) (por ejemplo, `Windows Mixed Reality Device Manager` y `OpenVR Device Manager` ).
- Creación de instancias de [GazeProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)que es un componente que es responsable de proporcionar información de mirada con la cabeza de estilo HoloLens (primera generación), además de HoloLens 2 información de mirada con los ojos de estilo.
- Creación de instancias de [FocusProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)que es un componente responsable de determinar los objetos que tienen el foco. Esto se describe con más profundidad en la [sección punteros y foco](controllers-pointers-and-focus.md#pointers-and-focus) de la documentación.
- Proporcionar puntos de registro para todos los eventos de entrada (como [agentes de escucha globales).](#global-listeners)
- Proporcionar funcionalidades de distribución de eventos para esos eventos de entrada.

## <a name="input-events"></a>Eventos de entrada

Por lo general, los eventos de entrada se desencadenan en dos canales diferentes:

### <a name="objects-in-focus"></a>Objetos en el foco

Los eventos se pueden enviar directamente a un Elemento GameObject que tenga el foco. Por ejemplo, un objeto podría tener un script que implemente [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) .
Este objeto obtiene eventos táctiles cuando se centra en una mano que está cerca de él. Estos tipos de eventos "sumen" la jerarquía de GameObject hasta que encuentre un GameObject capaz de controlar el evento.

Para ello, use [ExecuteHierarchy desde la](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) implementación predeterminada del sistema de entrada.

### <a name="global-listeners"></a>Agentes de escucha globales

Los eventos se pueden enviar a agentes de escucha globales. Es posible registrarse para todos los eventos de entrada mediante la interfaz del sistema de [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) entrada. Se recomienda usar el método [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) para registrar eventos globales: la función en desuso hará que los agentes de escucha reciban una notificación de TODOS los eventos de entrada, en lugar de solo los eventos de entrada de un tipo determinado (donde el tipo se define mediante la interfaz de `Register` eventos).

Tenga [en](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) cuenta que los agentes de escucha de reserva son otro tipo de agentes de escucha globales que también se desaconseja porque recibirán cada evento de entrada único que no se haya manipulado en ningún otro lugar de la escena.

### <a name="order-of-event-dispatch"></a>Orden de envío de eventos

Por lo general, los eventos se envían a los agentes de escucha de la siguiente manera. Tenga en cuenta que si alguno de los pasos siguientes marca el evento como [manipulado,](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)el proceso de distribución de eventos se detiene.

1. El evento se envía a los agentes de escucha globales.
2. El evento se envía a los diálogos modales del objeto centrado.
3. El evento se envía al objeto centrado.
4. El evento se envía a los agentes de escucha de reserva.

## <a name="device-managers-and-data-providers"></a>Administradores de dispositivos y proveedores de datos

Estas entidades son responsables de la interacción con las API de nivel inferior (como las API de Windows Mixed Reality o las API de OpenVR) y de traducir datos de esos sistemas en aquellas que se ajusten a las abstracciones de entrada de nivel superior de MRTK. Son responsables de detectar, crear y administrar la duración de los [controladores](controllers-pointers-and-focus.md#controllers).

El flujo básico de un administrador de dispositivos implica:

1. El servicio del sistema de entrada crea instancias del administrador de dispositivos.
2. El administrador de dispositivos se registra con su sistema subyacente (por ejemplo, el administrador de dispositivos Windows Mixed Reality se registrará para los eventos [de](../features/input/input-events.md) entrada [y gesto.](../features/input/gestures.md#gesture-events)
3. Crea controladores que detecta desde el sistema subyacente (por ejemplo, el proveedor podría detectar la presencia de manos articuladas).
4. En su bucle Update(), llame a UpdateController() para sondear el nuevo estado del sistema subyacente y actualizar su representación del controlador.
