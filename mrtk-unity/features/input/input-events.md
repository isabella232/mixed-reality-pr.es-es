---
title: Eventos de entrada
description: Documentación de InputEvents en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, eventos,
ms.openlocfilehash: 450c6dbbed8fc9bbb1a648b7a22f0de66747cbaf
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145221"
---
# <a name="input-events"></a>Eventos de entrada

En la lista siguiente se describen todas las interfaces de eventos de entrada disponibles que se implementarán mediante un componente monobehaviour personalizado. El sistema de entrada de MRTK llamará a estas interfaces para controlar la lógica de aplicación personalizada en función de las interacciones de entrada del usuario. [Los eventos de entrada de](pointers.md#pointer-event-interfaces) puntero se controlan de forma ligeramente diferente a los tipos de eventos de entrada estándar siguientes.

> [!IMPORTANT]
> De forma predeterminada, un script recibirá eventos de entrada solo si es el Elemento GameObject en el foco por un puntero o elemento primario de un Elemento GameObject en el foco.

| Controlador | Eventos | Descripción |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | Origen detectado o perdido | Se genera cuando se detecta o se pierde un origen de entrada, como cuando se detecta o se pierde el seguimiento de una mano articulada. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | Posición de origen cambiada | Se genera en los cambios de posición de origen. La posición de origen representa la posición general del origen de entrada. Las poses específicas, como la posición de control o puntero en un controlador de seis DOF, se pueden obtener a través de `IMixedRealityInputHandler<MixedRealityPose>` . |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Entrada hacia abajo o hacia arriba | Se genera en los cambios en las entradas binarias, como los botones. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Entrada cambiada | Se genera en los cambios en las entradas del tipo especificado. **T** puede tomar los siguientes valores: <br/> - *float* (por ejemplo, devuelve un desencadenador análogo)<br/> - *Vector2* (por ejemplo, devuelve la dirección del mando del mando) <br/> - *Vector3* (por ejemplo, la posición de retorno del dispositivo con seguimiento) <br/> - *Cuaternión* (por ejemplo, devuelve la orientación del dispositivo con seguimiento)<br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (por ejemplo, devuelve un dispositivo con seguimiento completo) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Palabra clave de voz reconocida | Se genera al reconocer una de las palabras clave configuradas en el perfil *de comandos de voz*. |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | Dictado<br/> Hipótesis <br/> Resultado <br/> Completo <br/> Error | Creado por sistemas de dictado para informar de los resultados de una sesión de dictado. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Eventos de gesto en: <br/> Iniciado <br/> Actualizado <br/> Completado <br/> Canceled | Se genera al detectar gestos. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Gesto actualizado o completado | Se genera al detectar gestos que contienen datos adicionales del tipo especificado. Vea [**eventos de gesto**](gestures.md#gesture-events) para obtener más información sobre los valores posibles para **T**. |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | Uniones de mano actualizadas | Se genera mediante controladores de mano articulados cuando se actualizan las uniones de mano. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | Malla de mano actualizada | Se genera mediante controladores de mano articulados cuando se actualiza una malla de mano. |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | Acción iniciada/finalizada | Se genera para indicar el inicio y el final de la acción para las entradas asignadas a acciones. |

## <a name="input-events-in-action"></a>Eventos de entrada en acción

En el nivel de script, los eventos de entrada se pueden consumir implementando una de las interfaces de controlador de eventos que se muestran en la tabla anterior. Cuando se produce un evento de entrada a través de una interacción del usuario, tiene lugar lo siguiente:

1. El sistema de entrada MRTK reconoce que se ha producido un evento de entrada.
1. El sistema de entrada MRTK desaconse la función de interfaz pertinente del evento de entrada a todos los [controladores de entrada globales registrados](#register-for-global-input-events)
1. Para cada puntero activo registrado con el sistema de entrada:
    1. El sistema de entrada determina qué GameObject está en el foco para el puntero actual.
    1. El sistema de entrada utiliza el sistema de eventos de [Unity](https://docs.unity3d.com/Manual/EventSystem.html) para usar la función de interfaz pertinente para todos los componentes correspondientes en el GameObject centrado.
    1. Si en algún momento se ha marcado un evento de entrada como [usado,](#how-to-stop-input-events)el proceso finalizará y ningún gameObject más recibirá devoluciones de llamada.
        - Ejemplo: los componentes que implementan la interfaz [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) se buscarán cuando se reconozca un comando de voz.
        - Nota: El sistema de eventos de Unity se burbujas para buscar el Elemento GameObject primario si no se encuentra ningún componente que coincida con la interfaz deseada en el GameObject actual.
1. Si no se registra ningún controlador de entrada global y no se encuentra gameObject con un componente o interfaz que coincida, el sistema de entrada llamará a cada controlador de entrada registrado de reserva.

> [!NOTE]
> [Los eventos de entrada](pointers.md#pointer-event-interfaces) de puntero se controlan de una manera ligeramente diferente a las interfaces de eventos de entrada enumeradas anteriormente. En concreto, los eventos de entrada de puntero solo los controla gameObject en el foco mediante el puntero que ha desencadenado el evento de entrada, así como cualquier controlador de entrada global. GameObjects controla los eventos de entrada normales en el foco para todos los punteros activos.

### <a name="input-event-interface-example"></a>Ejemplo de interfaz de evento de entrada

El código siguiente muestra el uso de la [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interfaz . Cuando el usuario dice las palabras "más pequeño" o "más grande" mientras se centra en un GameObject con esta clase, GameObject se escalará a la mitad o al `ShowHideSpeechHandler` doble.

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) Los eventos de entrada requieren que las palabras clave deseadas estén registradas previamente en el perfil de comandos de voz [de MRTK](speech.md).

## <a name="register-for-global-input-events"></a>Registro para eventos de entrada globales

Para crear un componente que escuche eventos de entrada globales, sin tener en cuenta qué GameObject puede estar en el foco, un componente debe registrarse en el sistema de entrada. Una vez registrado, las instancias de este MonoBehaviour recibirán eventos de entrada junto con cualquier GameObject actualmente en el foco y otros agentes de escucha registrados globalmente.

Si un evento de entrada se ha [marcado como usado,](#how-to-stop-input-events)los controladores registrados globales seguirán recibiendo devoluciones de llamada. Sin embargo, ningún elemento GameObjects centrado recibirá el evento.

### <a name="global-input-registration-example"></a>Ejemplo de registro de entrada global

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a>Registro para eventos de entrada de reserva

Los controladores de entrada de reserva son similares a los controladores de entrada globales registrados, pero se tratan como el último recurso para el control de eventos de entrada. Solo si no se han encontrado controladores de entrada globales y no hay ningún gameObject en el foco, se aprovecharán los controladores de entrada de reserva.

### <a name="fallback-input-handler-example"></a>Ejemplo de controlador de entrada de reserva

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a>Cómo detener eventos de entrada

Cada interfaz de evento de entrada proporciona [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) un objeto de datos como parámetro a cada función de la interfaz. Este objeto de datos de evento se extiende desde el propio objeto de [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) Unity.

Para evitar que un evento de entrada se propague a través de su ejecución como se [describe,](#input-events-in-action)un componente puede llamar a para marcar [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) el evento como utilizado. Esto impedirá que cualquier otro Elemento GameObject reciba el evento de entrada actual, a excepción de los controladores de entrada globales.

> [!NOTE]
> Un componente que llama al `Use()` método impedirá que otros GameObjects lo reciban. Sin embargo, otros componentes del elemento GameObject actual seguirán recibiendo el evento de entrada y se desatendrán las funciones de interfaz relacionadas.

## <a name="see-also"></a>Consulte también

- [Punteros](pointers.md)
- [Voz](speech.md)
- [Estado de entrada](input-state.md)
