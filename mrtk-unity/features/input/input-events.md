---
title: Eventos de entrada
description: Documentación de InputEvents en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, eventos,
ms.openlocfilehash: c8871aa575e2aa4507e9dbbdcc8bdf0fc0604633
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176787"
---
# <a name="input-events"></a><span data-ttu-id="fb704-104">Eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="fb704-104">Input events</span></span>

<span data-ttu-id="fb704-105">En la lista siguiente se describen todas las interfaces de eventos de entrada disponibles que se implementarán mediante un componente monobehaviour personalizado.</span><span class="sxs-lookup"><span data-stu-id="fb704-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="fb704-106">El sistema de entrada de MRTK llamará a estas interfaces para controlar la lógica de aplicación personalizada en función de las interacciones de entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="fb704-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="fb704-107">[Los eventos de entrada de](pointers.md#pointer-event-interfaces) puntero se controlan de forma ligeramente diferente a los tipos de eventos de entrada estándar siguientes.</span><span class="sxs-lookup"><span data-stu-id="fb704-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb704-108">De forma predeterminada, un script recibirá eventos de entrada solo si es el Elemento GameObject en el foco por un puntero o elemento primario de un Elemento GameObject en el foco.</span><span class="sxs-lookup"><span data-stu-id="fb704-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="fb704-109">Controlador</span><span class="sxs-lookup"><span data-stu-id="fb704-109">Handler</span></span> | <span data-ttu-id="fb704-110">Eventos</span><span class="sxs-lookup"><span data-stu-id="fb704-110">Events</span></span> | <span data-ttu-id="fb704-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="fb704-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="fb704-112">Origen detectado o perdido</span><span class="sxs-lookup"><span data-stu-id="fb704-112">Source Detected / Lost</span></span> | <span data-ttu-id="fb704-113">Se genera cuando se detecta o se pierde un origen de entrada, como cuando se detecta o se pierde el seguimiento de una mano articulada.</span><span class="sxs-lookup"><span data-stu-id="fb704-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="fb704-114">Posición de origen modificada</span><span class="sxs-lookup"><span data-stu-id="fb704-114">Source Pose Changed</span></span> | <span data-ttu-id="fb704-115">Se genera en los cambios de posición de origen.</span><span class="sxs-lookup"><span data-stu-id="fb704-115">Raised on source pose changes.</span></span> <span data-ttu-id="fb704-116">La posición de origen representa la posición general del origen de entrada.</span><span class="sxs-lookup"><span data-stu-id="fb704-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="fb704-117">Las poses específicas, como el control o la posición del puntero en un controlador doF de seis, se pueden obtener a través de `IMixedRealityInputHandler<MixedRealityPose>` .</span><span class="sxs-lookup"><span data-stu-id="fb704-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="fb704-118">Entrada hacia abajo o hacia arriba</span><span class="sxs-lookup"><span data-stu-id="fb704-118">Input Down / Up</span></span> | <span data-ttu-id="fb704-119">Se genera en los cambios en las entradas binarias, como los botones.</span><span class="sxs-lookup"><span data-stu-id="fb704-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="fb704-120">Entrada cambiada</span><span class="sxs-lookup"><span data-stu-id="fb704-120">Input Changed</span></span> | <span data-ttu-id="fb704-121">Se genera en los cambios en las entradas del tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="fb704-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="fb704-122">**T** puede tomar los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="fb704-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="fb704-123">- *float* (por ejemplo, devuelve un desencadenador análogo)</span><span class="sxs-lookup"><span data-stu-id="fb704-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="fb704-124">- *Vector2* (por ejemplo, devuelve la dirección del control de posición del mando)</span><span class="sxs-lookup"><span data-stu-id="fb704-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="fb704-125">- *Vector3* (por ejemplo, la posición de retorno del dispositivo con seguimiento)</span><span class="sxs-lookup"><span data-stu-id="fb704-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="fb704-126">- *Cuaternión* (por ejemplo, devuelve la orientación del dispositivo con seguimiento)</span><span class="sxs-lookup"><span data-stu-id="fb704-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="fb704-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (por ejemplo, devuelve un dispositivo con seguimiento completo)</span><span class="sxs-lookup"><span data-stu-id="fb704-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="fb704-128">Palabra clave de voz reconocida</span><span class="sxs-lookup"><span data-stu-id="fb704-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="fb704-129">Se genera al reconocer una de las palabras clave configuradas en el perfil *de comandos de voz*.</span><span class="sxs-lookup"><span data-stu-id="fb704-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="fb704-130">Dictado</span><span class="sxs-lookup"><span data-stu-id="fb704-130">Dictation</span></span><br/> <span data-ttu-id="fb704-131">Hipótesis</span><span class="sxs-lookup"><span data-stu-id="fb704-131">Hypothesis</span></span> <br/> <span data-ttu-id="fb704-132">Resultado</span><span class="sxs-lookup"><span data-stu-id="fb704-132">Result</span></span> <br/> <span data-ttu-id="fb704-133">Completo</span><span class="sxs-lookup"><span data-stu-id="fb704-133">Complete</span></span> <br/> <span data-ttu-id="fb704-134">Error</span><span class="sxs-lookup"><span data-stu-id="fb704-134">Error</span></span> | <span data-ttu-id="fb704-135">Los sistemas de dictado los elevan para informar de los resultados de una sesión de dictado.</span><span class="sxs-lookup"><span data-stu-id="fb704-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="fb704-136">Eventos de gesto en:</span><span class="sxs-lookup"><span data-stu-id="fb704-136">Gesture events on:</span></span> <br/> <span data-ttu-id="fb704-137">Iniciado</span><span class="sxs-lookup"><span data-stu-id="fb704-137">Started</span></span> <br/> <span data-ttu-id="fb704-138">Actualizado</span><span class="sxs-lookup"><span data-stu-id="fb704-138">Updated</span></span> <br/> <span data-ttu-id="fb704-139">Completado</span><span class="sxs-lookup"><span data-stu-id="fb704-139">Completed</span></span> <br/> <span data-ttu-id="fb704-140">Canceled</span><span class="sxs-lookup"><span data-stu-id="fb704-140">Canceled</span></span> | <span data-ttu-id="fb704-141">Se genera al detectar gestos.</span><span class="sxs-lookup"><span data-stu-id="fb704-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="fb704-142">Gesto actualizado o completado</span><span class="sxs-lookup"><span data-stu-id="fb704-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="fb704-143">Se genera al detectar gestos que contienen datos adicionales del tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="fb704-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="fb704-144">Vea [**eventos de gesto**](gestures.md#gesture-events) para obtener más información sobre los valores posibles para **T**.</span><span class="sxs-lookup"><span data-stu-id="fb704-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="fb704-145">Juntas de mano actualizadas</span><span class="sxs-lookup"><span data-stu-id="fb704-145">Hand Joints Updated</span></span> | <span data-ttu-id="fb704-146">Se genera mediante controladores de mano articulados cuando se actualizan las uniones de mano.</span><span class="sxs-lookup"><span data-stu-id="fb704-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="fb704-147">Malla de mano actualizada</span><span class="sxs-lookup"><span data-stu-id="fb704-147">Hand Mesh Updated</span></span> | <span data-ttu-id="fb704-148">Se genera mediante controladores de mano articulados cuando se actualiza una malla de mano.</span><span class="sxs-lookup"><span data-stu-id="fb704-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="fb704-149">Acción iniciada/finalizada</span><span class="sxs-lookup"><span data-stu-id="fb704-149">Action Started / Ended</span></span> | <span data-ttu-id="fb704-150">Se genera para indicar el inicio y el final de la acción para las entradas asignadas a acciones.</span><span class="sxs-lookup"><span data-stu-id="fb704-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="fb704-151">Eventos de entrada en acción</span><span class="sxs-lookup"><span data-stu-id="fb704-151">Input events in action</span></span>

<span data-ttu-id="fb704-152">En el nivel de script, los eventos de entrada se pueden consumir implementando una de las interfaces de controlador de eventos que se muestran en la tabla anterior.</span><span class="sxs-lookup"><span data-stu-id="fb704-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="fb704-153">Cuando se produce un evento de entrada a través de una interacción del usuario, tiene lugar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="fb704-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="fb704-154">El sistema de entrada MRTK reconoce que se ha producido un evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="fb704-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="fb704-155">El sistema de entrada MRTK desaconse la función de interfaz pertinente del evento de entrada a todos los [controladores de entrada globales registrados](#register-for-global-input-events)</span><span class="sxs-lookup"><span data-stu-id="fb704-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="fb704-156">Para cada puntero activo registrado con el sistema de entrada:</span><span class="sxs-lookup"><span data-stu-id="fb704-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="fb704-157">El sistema de entrada determina qué GameObject está en el foco para el puntero actual.</span><span class="sxs-lookup"><span data-stu-id="fb704-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="fb704-158">El sistema de entrada usa el sistema de eventos de [Unity](https://docs.unity3d.com/Manual/EventSystem.html) para abrir la función de interfaz pertinente para todos los componentes correspondientes en el GameObject centrado.</span><span class="sxs-lookup"><span data-stu-id="fb704-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="fb704-159">Si en algún momento se ha marcado un evento de entrada como [usado,](#how-to-stop-input-events)el proceso finalizará y ningún gameObject más recibirá devoluciones de llamada.</span><span class="sxs-lookup"><span data-stu-id="fb704-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="fb704-160">Ejemplo: los componentes que implementan la interfaz se buscarán cuando se reconozca [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="fb704-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="fb704-161">Nota: El sistema de eventos de Unity se burbujas para buscar el Elemento GameObject primario si no se encuentra ningún componente que coincida con la interfaz deseada en el Elemento GameObject actual.</span><span class="sxs-lookup"><span data-stu-id="fb704-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="fb704-162">Si no se registran controladores de entrada globales y no se encuentra ningún GameObject con un componente o interfaz que coincida, el sistema de entrada llamará a cada controlador de entrada registrado de reserva.</span><span class="sxs-lookup"><span data-stu-id="fb704-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="fb704-163">[Los eventos de entrada](pointers.md#pointer-event-interfaces) de puntero se controlan de una manera ligeramente diferente a las interfaces de eventos de entrada enumeradas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fb704-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="fb704-164">En concreto, los eventos de entrada de puntero solo los controla el elemento GameObject en el foco mediante el puntero que ha desencadenado el evento de entrada, así como cualquier controlador de entrada global.</span><span class="sxs-lookup"><span data-stu-id="fb704-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="fb704-165">Los eventos de entrada normales se controlan mediante GameObjects en el foco para todos los punteros activos.</span><span class="sxs-lookup"><span data-stu-id="fb704-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="fb704-166">Ejemplo de interfaz de eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="fb704-166">Input event interface example</span></span>

<span data-ttu-id="fb704-167">El código siguiente muestra el uso de la [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interfaz .</span><span class="sxs-lookup"><span data-stu-id="fb704-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="fb704-168">Cuando el usuario dice las palabras "más pequeño" o "más grande" mientras se centra en un Elemento GameObject con esta clase, GameObject se escalará a sí mismo a la mitad o `ShowHideSpeechHandler` al doble.</span><span class="sxs-lookup"><span data-stu-id="fb704-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

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
> <span data-ttu-id="fb704-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) Los eventos de entrada requieren que las palabras clave deseadas estén registradas previamente en el perfil de comandos de voz [de MRTK](speech.md).</span><span class="sxs-lookup"><span data-stu-id="fb704-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="fb704-170">Registro para eventos de entrada globales</span><span class="sxs-lookup"><span data-stu-id="fb704-170">Register for global input events</span></span>

<span data-ttu-id="fb704-171">Para crear un componente que escuche eventos de entrada globales, sin tener en cuenta qué GameObject puede estar en el foco, un componente debe registrarse en el sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="fb704-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="fb704-172">Una vez registrado, todas las instancias de este MonoBehaviour recibirán eventos de entrada junto con cualquier GameObject que esté actualmente en el foco y otros agentes de escucha registrados globalmente.</span><span class="sxs-lookup"><span data-stu-id="fb704-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="fb704-173">Si un evento de entrada se ha [marcado como usado,](#how-to-stop-input-events)los controladores registrados globales seguirán recibiendo devoluciones de llamada.</span><span class="sxs-lookup"><span data-stu-id="fb704-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="fb704-174">Sin embargo, ningún elemento GameObjects centrado recibirá el evento.</span><span class="sxs-lookup"><span data-stu-id="fb704-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="fb704-175">Ejemplo de registro de entrada global</span><span class="sxs-lookup"><span data-stu-id="fb704-175">Global input registration example</span></span>

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

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="fb704-176">Registro para eventos de entrada de reserva</span><span class="sxs-lookup"><span data-stu-id="fb704-176">Register for fallback input events</span></span>

<span data-ttu-id="fb704-177">Los controladores de entrada de reserva son similares a los controladores de entrada globales registrados, pero se tratan como el último recurso para el control de eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="fb704-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="fb704-178">Solo si no se han encontrado controladores de entrada globales y no hay gameObjects en el foco, se aprovecharán los controladores de entrada de reserva.</span><span class="sxs-lookup"><span data-stu-id="fb704-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="fb704-179">Ejemplo de controlador de entrada de reserva</span><span class="sxs-lookup"><span data-stu-id="fb704-179">Fallback input handler example</span></span>

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

## <a name="how-to-stop-input-events"></a><span data-ttu-id="fb704-180">Cómo detener eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="fb704-180">How to stop input events</span></span>

<span data-ttu-id="fb704-181">Cada interfaz de evento de entrada proporciona [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) un objeto de datos como parámetro a cada función de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="fb704-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="fb704-182">Este objeto de datos de evento se extiende desde el propio objeto de [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) Unity.</span><span class="sxs-lookup"><span data-stu-id="fb704-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="fb704-183">Para evitar que un evento de entrada se propague a través de su ejecución como se [describe,](#input-events-in-action)un componente puede llamar a para marcar [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) el evento como utilizado.</span><span class="sxs-lookup"><span data-stu-id="fb704-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="fb704-184">Esto impedirá que cualquier otro Elemento GameObject reciba el evento de entrada actual, a excepción de los controladores de entrada globales.</span><span class="sxs-lookup"><span data-stu-id="fb704-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="fb704-185">Un componente que llama al `Use()` método impedirá que otros GameObjects lo reciban.</span><span class="sxs-lookup"><span data-stu-id="fb704-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="fb704-186">Sin embargo, otros componentes del elemento GameObject actual seguirán recibiendo el evento de entrada y se desatendrán las funciones de interfaz relacionadas.</span><span class="sxs-lookup"><span data-stu-id="fb704-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb704-187">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fb704-187">See also</span></span>

- [<span data-ttu-id="fb704-188">Punteros</span><span class="sxs-lookup"><span data-stu-id="fb704-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="fb704-189">Voz</span><span class="sxs-lookup"><span data-stu-id="fb704-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="fb704-190">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="fb704-190">Input State</span></span>](input-state.md)
