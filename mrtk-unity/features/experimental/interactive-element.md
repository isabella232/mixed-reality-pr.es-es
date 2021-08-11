---
title: Elemento interactivo
description: Documentación de MRTK de InteractiveElement
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, elemento interactivo, interactable
ms.openlocfilehash: 6d8f36c4780844e991eb32943645402503fab8340c6843dbb607f1c11033d912
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220607"
---
# <a name="interactive-element-experimental"></a>Elemento interactivo [Experimental]

Un punto de entrada centralizado simplificado al sistema de entrada de MRTK. Contiene métodos de administración de estados, administración de eventos y la lógica de configuración de estado para los estados de interacción principal.

Interactive Element es una característica experimental compatible con Unity 2019.3 y versiones 2019.3, ya que usa una funcionalidad nueva de Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).

### <a name="interactive-element-inspector"></a>Inspector de elementos interactivos

Durante el modo de reproducción, el inspector de elementos interactivos proporciona comentarios visuales que indican si el estado actual está activo o no. Si un estado está activo, se resaltará con un color cian.  Si el estado no está activo, el color no cambia. Los números situados junto a los estados del inspector son los valores de estado; si el estado está activo, el valor es 1, si el estado no está activo, el valor es 0.

![Elemento interactivo con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>Estados principales

El elemento interactivo contiene estados principales y admite la adición de [estados personalizados.](#custom-states)  Un estado principal es aquel que ya tiene la lógica de configuración de estado definida en `BaseInteractiveElement` . A continuación se muestra una lista de los estados principales controlados por entrada actuales: 

### <a name="current-core-states"></a>Estados principales actuales

- [Predeterminado](#default-state) 

Estados principales de interacción cercana y lejana:
- [Foco](#focus-state) 

Estados principales de interacción cercana:

- [Enfoque cercano](#focus-near-state)
- [Tocar](#touch-state)

Estados principales de interacción lejana:
- [Enfoque lejos](#focus-far-state)
- [Seleccione Lejos.](#select-far-state)

Otros estados principales:
- [Se ha hecho clic](#clicked-state)
- [Activar y desactivar](#toggle-on-and-toggle-off-state)
- [Palabra clave de voz](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Cómo agregar un estado principal a través de Inspector

1. Vaya a **Add Core State (Agregar estado** principal) en el inspector de Interactive Element (Elemento interactivo).

    ![Agregar un estado principal a través de Inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. Seleccione el **botón Seleccionar estado** para elegir el estado principal que desea agregar. Los estados del menú se ordenan por tipo de interacción.

    ![Agregar un estado principal a través de Inspector con el estado seleccionado](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. Abra el plegado Configuración de eventos para ver los eventos y las propiedades asociados al estado.

    ![Agregar un estado principal a través de Inspector con la configuración de eventos](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>Cómo agregar un estado principal mediante script

Use el `AddNewState(stateName)` método para agregar un estado principal. Para obtener una lista de los nombres de estado principales disponibles, use `CoreInteractionState` la enumeración .

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>Estructura interna de estados 

Los estados del elemento interactivo son de tipo `InteractionState` .  contiene `InteractionState` las siguientes propiedades:

- **Name**: nombre del estado.
- **Valor:** el valor de estado.  Si el estado está en, el valor de estado es 1. Si el estado está desactivado, el valor de estado es 0.
- **Activo:** indica si el estado está activo actualmente o no. El valor de la propiedad Active es true cuando el estado está activado, false si el estado está desactivado. 
- **Tipo de interacción:** el tipo de interacción de un estado es el tipo de interacción para el que está pensado un estado. 
  - `None`: no admite ninguna forma de interacción de entrada.
  - `Near`: compatibilidad con la interacción cercana. La entrada se considera una interacción cercana cuando una mano articulada tiene contacto directo con otro objeto de juego, es decir, la posición de la mano articulada está cerca de la posición del objeto de juego en el espacio mundial.
  - `Far`: compatibilidad con la interacción lejana. La entrada se considera interacción lejana cuando no se requiere el contacto directo con el objeto de juego. Por ejemplo, la entrada a través del rayo o la mirada del controlador se considera entrada de interacción lejana.
  - `NearAndFar`: abarca la compatibilidad con la interacción cercana y lejana. 
  - `Other`: compatibilidad con la interacción independiente del puntero.
- **Configuración de eventos:** la configuración de eventos para un estado es el punto de entrada del perfil de eventos serializados. 

Todas estas propiedades se establecen internamente en `State Manager` el contenido del elemento interactivo. Para modificar los estados, use los métodos auxiliares siguientes:

**Métodos auxiliares de configuración de estado**

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

La obtención de la configuración de eventos de un estado es específica del propio estado. Cada estado principal tiene un tipo de configuración de eventos específico que se describe a continuación en las secciones que describen cada estado principal.

Este es un ejemplo generalizado de cómo obtener la configuración de eventos de un estado:

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>Estado predeterminado

El estado Predeterminado siempre está presente en un elemento interactivo.  Este estado solo estará activo cuando todos los demás estados no estén activos.  Si cualquier otro estado se activa, el estado Predeterminado se establecerá en desactivado internamente. 

Un elemento interactivo se inicializa con los estados Predeterminado y Enfoque presentes en la lista de estados. El estado Predeterminado siempre debe estar presente en la lista de estados. 

#### <a name="getting-default-state-events"></a>Obtener eventos de estado predeterminados

Tipo de configuración de evento para el estado predeterminado: `StateEvents`

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a>Estado de enfoque

El estado de enfoque es un estado de interacción cercano y lejano que se puede pensar como la realidad mixta equivalente a mantener el puntero. El factor distintivo entre la interacción cercana y lejana para el estado focus es el tipo de puntero activo actual.  Si el tipo de puntero para el estado De foco es el Puntero de ándes, la interacción se considera una interacción cercana.  Si el puntero principal no es el puntero Descaro, la interacción se considera interacción lejana. El estado de foco está presente en el elemento interactivo de forma predeterminada.

**Comportamiento del estado de enfoque** 
 ![ Estado de enfoque con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**Inspector de estado de enfoque** 
 ![ Estado de foco en Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>Obtener eventos de estado de enfoque

Tipo de configuración de eventos para el estado de enfoque: `FocusEvents`

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a>Enfoque cercano frente al comportamiento lejano del foco 

![Enfoque cerca y lejos con la interacción de la mano virtual](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Focus Near State

El estado Focus Near (Enfoque cercano) se establece cuando se genera un evento de foco y el puntero principal es el puntero Pointere, una indicación de interacción cercana. 

**Enfoque del comportamiento de estado cercano** 
 ![ Enfoque en el estado cercano con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Focus Near State Inspector** 
 ![ Foco cerca del componente en el inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>Obtención de eventos de estado de enfoque

Tipo de configuración de evento para focusNear State: `FocusEvents`

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a>Estado lejos del foco

El estado Lejos del foco se establece cuando el puntero principal no es el puntero Desalomado.  Por ejemplo, el puntero de rayo del controlador predeterminado y el puntero GGV (mirada, gesto, voz) se consideran punteros de interacción lejana.

**Comportamiento del estado lejano del foco** 
 ![ Estado de enfoque lejos con la interacción de la mano virtual](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**Focus Far State Inspector** 
 ![ Componente lejos del foco en el inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>Obtener eventos de estado lejano de enfoque

Tipo de configuración de evento para FocusFar State: `FocusEvents`

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a>Estado táctil

El estado Táctil es un estado de interacción cercano que se establece cuando una mano articulada tocan el objeto directamente.  Un toque directo significa que el dedo índice de la mano articulada está muy cerca de la posición mundial del objeto. De forma predeterminada, `NearInteractionTouchableVolume` se adjunta un componente al objeto si el estado Táctil se agrega a la lista de estados.  La presencia de un  `NearInteractionTouchableVolume` componente o es necesaria para detectar eventos `NearInteractionTouchable` Touch.  La diferencia entre y es que detecta un toque basado en el colisionador del objeto y detecta la función táctil dentro de un área `NearInteractionTouchableVolume` `NearInteractionTouchable` definida de un `NearInteractionTouchableVolume` `NearInteractionTouchable` plano.

**Comportamiento del estado táctil** 
 ![ Estado táctil con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**Touch State Inspector** 
 ![ Componente de estado táctil en el inspector](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>Obtener eventos de estado táctil

Tipo de configuración de eventos para Touch State: `TouchEvents`

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a>Seleccione Estado lejano.

El estado Select Far (Seleccionar extremo) `IMixedRealityPointerHandler` es el que se ha presentado.  Este estado es un estado de interacción lejana que detecta el clic de interacción lejana (pulsación en el aire) y se mantiene a través del uso de punteros de interacción lejana, como el puntero de rayo del controlador predeterminado o el puntero GGV.  El estado Select Far (Seleccionar extremo) tiene una opción en el plegado de configuración de eventos denominado `Global` . Si `Global` es true, se registra `IMixedRealityPointerHandler` como un controlador de entrada global.  No es necesario centrarse en un objeto para desencadenar eventos del sistema de entrada si un controlador está registrado como global.  Por ejemplo, si un usuario quiere saber cada vez que se realiza el gesto de pulsar o seleccionar el aire independientemente del objeto en el foco, establezca `Global` en true. 

**Seleccionar comportamiento de estado lejano** 
 ![ Selección lejos con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Seleccione Inspector de estado lejano.** 
 ![ Selección del componente lejano en el inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>Obtención de eventos de estado lejano selectos

Tipo de configuración de eventos para SelectFar State: `SelectFarEvents`

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a>Estado en el que se hizo clic

El estado Clicked se desencadena mediante un clic de interacción lejana (Seleccionar estado lejano) de forma predeterminada.  Este estado se cambia internamente a on, invoca el evento OnClicked y, a continuación, se cambia inmediatamente a desactivado. 

> [!NOTE]
> Los comentarios visuales en el inspector basados en la actividad de estado no están presentes para el estado Clicked porque está encendido y apagado inmediatamente. 

**Comportamiento de estado en el que se ha hecho clic** 
 ![ Estado en el que se hizo clic con interacciones de manos virtuales](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

**Inspector de estado en el que se ha hecho clic** 
 ![ Haga clic en el componente de estado en el inspector.](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Ejemplo de estado con clic cercano y lejano**  
El estado en el que se ha hecho clic se puede desencadenar a través de puntos de entrada adicionales mediante el `interactiveElement.TriggerClickedState()` método .  Por ejemplo, si un usuario desea que una interacción táctil cercana desencadene también un clic en un objeto, agregaría el método como agente de escucha en `TriggerClickedState()` estado táctil.   

![Estado cercano y lejano con interacciones de manos virtuales](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>Obtener eventos de estado en los que se hace clic

Tipo de configuración de eventos para el estado clicked: `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Activar y desactivar estado

Los estados Alternar activar y Desactivar son un par y ambos deben estar presentes para el comportamiento de alternancia.  De forma predeterminada, los estados Alternar activado y Desactivar se desencadenan mediante un clic de interacción lejana (Seleccionar estado lejano).  De forma predeterminada, el estado Alternar desactivado está activo al iniciar, lo que significa que el botón de alternancia se inicializará como desactivado.  Si un usuario desea que el estado Toggle On esté activo al principio, en el estado Toggle On (Alternar activado) establezca `IsSelectedOnStart` en true.

**ToggleOn y Toggle Off State Behavior** 
 ![ Activar y desactivar con interacciones de manos virtuales](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**ToggleOn y Toggle Off State Inspector** 
 ![ Alternar componente en el inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Ejemplo de estados de alternancia cercanos y lejanos**  
De forma similar al estado Clic, la configuración de estado de alternancia puede tener varios puntos de entrada mediante el `interactiveElement.SetToggleStates()` método . Por ejemplo, si un usuario desea tocar como punto de entrada adicional para establecer los estados de alternancia, agrega el método a uno de los eventos en `SetToggleStates()` el estado Touch. 

![Alternancia cercana y lejana con interacciones de manos virtuales](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>Obtener eventos de estado de activación y desactivación

Tipo de configuración de eventos para el estado ToggleOn: `ToggleOnEvents`  
Tipo de configuración de evento para el estado ToggleOff: `ToggleOffEvents`

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a>Estado de palabra clave de voz

El estado de palabra clave de voz escucha las palabras clave definidas en el Mixed Reality voz. Cualquier palabra clave nueva DEBE registrarse en el perfil de comandos de voz antes del tiempo de ejecución (pasos a continuación). 

**Comportamiento del estado de la palabra clave de voz** 
 ![ Palabra clave de voz con interacción virtual](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**Speech Keyword State Inspector** 
 ![ Componente de palabra clave de voz en el inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> El estado de la palabra clave de voz se desencadenó en el editor presionando la tecla F5 en el gif anterior. La configuración en las pruebas del editor para voz se describe a continuación. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>Cómo registrar un comando o palabra clave de Voz

1. Selección del **objeto de juego MixedRealityToolkit**

1. Seleccione **Copiar y personalizar el** perfil actual.

1. Vaya a la sección Entrada y seleccione **Clonar para** habilitar la modificación del perfil de entrada.

1. Desplácese hacia abajo hasta la sección Voz en el perfil de entrada y clone el perfil de voz.

    ![Perfil de palabra clave de voz en el objeto de juego MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. Seleccione Agregar un nuevo comando de voz.

    ![Adición de una nueva palabra clave de voz en el perfil de MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. Escriba la palabra clave new. Opcional: cambie KeyCode a F5 (u otro KeyCode) para permitir las pruebas en el editor. 

    ![Configuración de la palabra clave de voz en el perfil de MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Vuelva al inspector de estado palabra clave de voz de elemento interactivo y seleccione **Agregar palabra clave.** 

    ![Agregar palabra clave al componente de elemento interactivo](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Validación y registro de palabras clave](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. Escriba la nueva palabra clave que se acaba de registrar en el perfil de voz.

    ![Especificación de la nueva palabra clave de voz](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Para probar el estado de palabra clave de voz en el editor, presione el código de clave que se definió en el paso 6 (F5) para simular el evento reconocido de palabra clave de voz.

#### <a name="getting-speech-keyword-state-events&quot;></a>Obtención de eventos de estado de palabra clave de voz

Tipo de configuración de eventos para speechKeyword State: `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a>Estados personalizados

### <a name="how-to-create-a-custom-state-via-inspector"></a>Cómo crear un estado personalizado a través de Inspector 

El estado personalizado creado a través de inspector se inicializará con la configuración de eventos de estado predeterminada. La configuración de eventos predeterminada para un estado personalizado es de tipo y contiene los eventos `StateEvents` OnStateOn y OnStateOff.

1. Vaya a **Crear estado personalizado en** el inspector del elemento interactivo.
    
    ![Creación de un estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Escriba el nombre del nuevo estado. Este nombre debe ser único y no puede ser el mismo que los estados principales existentes. 
    
    ![Escribir el nombre de un nuevo estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Seleccione **Establecer nombre de estado** para agregarlo a la lista de estados.
    
    ![Agregar estado personalizado a la lista de estados](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Este estado personalizado se inicializa con la configuración de `StateEvents` eventos predeterminada que contiene los eventos y `OnStateOn` `OnStateOff` . Para crear una configuración de eventos personalizada para un nuevo estado, consulte: [Creación de un estado personalizado con una configuración de eventos personalizada.](#creating-a-custom-state-with-a-custom-event-configuration)
    
    ![Nuevo estado que se muestra en el componente de elemento interactivo](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>Cómo crear un estado personalizado mediante script

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>Crear un estado personalizado con una configuración de eventos personalizada 

Los archivos de ejemplo de un estado personalizado denominado **Teclado** se encuentran aquí: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

En los pasos siguientes se muestra un ejemplo existente de creación de una configuración de eventos de estado personalizado y archivos receptores.

1. Piense en un nombre de estado.  Este nombre debe ser único y no puede ser el mismo que los estados principales existentes. Para los fines de este ejemplo, el nombre de estado será **Keyboard**.

1. Cree dos archivos .cs denominados state name + "Receiver" y state name + "Events". La nomenclatura de estos archivos se tiene en cuenta internamente y debe seguir la convención de nombre de estado + Evento/Receptor. 

    ![Scripts de estado de teclado](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Consulte los archivos KeyboardEvents.cs y KeyboardReceiver.cs para obtener más detalles sobre el contenido del archivo. Las nuevas clases de configuración de eventos deben heredar de `BaseInteractionEventConfiguration` y las nuevas clases de receptor de eventos deben heredar de `BaseEventReceiver` .  En el archivo se encuentran ejemplos sobre la configuración de estado para el estado del `CustomStateSettingExample.cs` teclado. 

1. Agregue el estado al elemento interactivo con el nombre de estado; el nombre de estado se reconocerá si existen archivos de configuración de eventos y receptores de eventos.  Las propiedades del archivo de configuración de eventos personalizados deben aparecer en el inspector.

    ![Adición de estado personalizado al elemento interactivo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ Estado personalizado reconocido en el elemento interactivo](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Para obtener más ejemplos de archivos de configuración de eventos y receptores de eventos, consulte los archivos en estas rutas de acceso:    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>Escena de ejemplo 

La escena de ejemplo de Elemento interactivo + Visualizador de estado se encuentra aquí: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![Escena de ejemplo con elemento interactivo y visualizador de estado](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Botón comprimible

La escena de ejemplo contiene elementos prefab denominados y , estos elementos prefabs reflejan el comportamiento de los botones, que se construyen mediante el elemento interactivo y el `CompressableButton` `CompressableButtonToggle` `PressableButtonHoloLens2` visualizador de estado. El `CompressableButton` componente es actualmente una combinación de con como una clase `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` base. 

## <a name="state-visualizer-experimental"></a>Visualizador de estado [Experimental]

El componente Visualizador de estado agrega animaciones a un objeto en función de los estados definidos en un componente de elemento interactivo vinculado. Este componente crea recursos de animación, los coloca en la carpeta MixedRealityToolkit.Generated y habilita la configuración simplificada de fotogramas clave de animación mediante la adición de propiedades Animatable a un objeto de juego de destino. Para habilitar las transiciones de animación entre estados, se crea un recurso controlador de Animator y se genera una máquina de estados predeterminada con parámetros asociados y cualquier transición de estado.  La máquina de estados se puede ver en la ventana Animator de Unity.

### <a name="state-visualizer-and-unity-animation-system"></a>Visualizador de estado y sistema de animación de Unity

El visualizador de estado aprovecha actualmente el sistema de animación de Unity. 

Cuando se presiona el botón Generar nuevos **clips** de animación en el visualizador de estado, se generan nuevos recursos de clips de animación en función de los nombres de estado del elemento interactivo y se colocan en la carpeta MixedRealityToolkit.Generated. La propiedad Clip de animación de cada contenedor de estado se establece en el clip de animación asociado.

![Clips de animación en el componente visualizador de estado](../images/interactive-element/StateVisualizer/AnimationClips.png)

También [se genera una máquina de estado](https://docs.unity3d.com/Manual/AnimationOverview.html) del animador para administrar transiciones fluidas entre clips de animación.  De forma predeterminada, la máquina de estados usa [cualquier estado para](https://docs.unity3d.com/Manual/class-State.html) permitir transiciones entre cualquier estado en interactive element. 

[Los visualizadores de estado](https://docs.unity3d.com/Manual/AnimationParameters.html) desencadenados en el animador también se generan para cada estado; los parámetros del desencadenador se usan en el visualizador de estado para desencadenar una animación.

![Máquina de estado de Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>Limitaciones en tiempo de ejecución 

El visualizador de estado debe agregarse a un objeto a través del inspector y no se puede agregar mediante script.  Las propiedades que modifican AnimatorStateMachine/AnimationController se encuentran en un espacio de nombres del editor ( ) que se quita `UnityEditor.Animations` cuando se construye la aplicación.

## <a name="how-to-use-the-state-visualizer"></a>Uso del visualizador de estado

1. Crear un cubo
1. Attach Interactive Element
1. Adjuntar visualizador de estado
1. Seleccione **Generate New Animation Clips (Generar clips de animación nuevos).**

    ![Generación de nuevos clips de animación](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Mostrar clips de animación generados en el visualizador y los componentes de elementos interactivos](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. En el contenedor focus state (Estado de enfoque), **seleccione Add Target (Agregar destino).**

    ![Adición del destino del visualizador de estado](../images/interactive-element/StateVisualizer/AddTarget.png)

1. Arrastre el objeto de juego actual al campo de destino. 

    ![Establecimiento del destino del visualizador de estado](../images/interactive-element/StateVisualizer/SetTarget.png)

1. Abrir el plegable Propiedades animables de cubo
1. Seleccione el menú desplegable de la propiedad Animatable y seleccione **Color.**

    ![Configuración del color del visualizador de estado](../images/interactive-element/StateVisualizer/SetColor.png)

1. Seleccione **Agregar la propiedad Color Animatable**

    ![Selección de la propiedad animable de color del visualizador](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. Elegir un color 

    ![Elección de un color del visualizador de la rueda de colores](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Presione Reproducir y observe el cambio de color transitorio.

    ![Ejemplo de cambio de color transitorio con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Propiedades que se pueden animar

El propósito principal de las propiedades animables es simplificar la configuración de fotogramas clave del clip de animación.  Si un usuario está familiarizado con el sistema de animación de Unity y prefiere establecer directamente fotogramas clave en los clips de animación generados, simplemente no puede agregar propiedades Animatable a un objeto de destino y abrir el clip en la ventana Animación de Unity (animación Windows > animación > animación). 

Si usa las propiedades Animatable para la animación, el tipo de curva se establece en EaseInOut.

**Propiedades actuales de Animatable:**
- [Desplazamiento de escala](#scale-offset)
- [Desplazamiento de posición](#position-offset)
- [Color](#color)
- [Color del sombreador](#shader-color)
- [Float del sombreador](#shader-float)
- [Vector de sombreador](#shader-vector)

### <a name="scale-offset"></a>Desplazamiento de escala

La propiedad Animatable de desplazamiento de escala toma la escala actual del objeto y agrega el desplazamiento definido.

![Desplazamiento de escala con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Desplazamiento de posición

La propiedad Animatable Position Offset toma la posición actual del objeto y agrega el desplazamiento definido.

![Desplazamiento de posición con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

La propiedad Color Animatable representa el color principal de un material si el material tiene una propiedad de color principal. Esta propiedad anima la `material._Color` propiedad .

![Cambio de color de foco con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Color del sombreador

La propiedad Color Animatable del sombreador hace referencia a una propiedad de sombreador de color de tipo. Se requiere un nombre de propiedad para todas las propiedades del sombreador. El siguiente gif muestra cómo animar una propiedad de color de sombreador denominada Fill_Color que no es el color del material principal.  Observe los valores cambiantes en el inspector de material.

![Color de sombreado con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Float del sombreador

La propiedad Float Animatable del sombreador hace referencia a una propiedad de sombreador de tipo float. Se requiere un nombre de propiedad para todas las propiedades del sombreador. En el gif siguiente, observe los valores cambiantes en el inspector de material para la propiedad Metal metalórtico. 

![Sombreador flotante con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Vector de sombreador

La propiedad Vector Animatable del sombreador hace referencia a una propiedad de sombreador de tipo Vector4. Se requiere un nombre de propiedad para todas las propiedades del sombreador. En el gif siguiente, observe los valores cambiantes en el inspector de material para la propiedad Tiling (Main Tex_ST). 

![Vector de sombreador con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Cómo buscar nombres de propiedades de sombreador animables

1. Vaya a Ventana > animación > animación
1. Asegúrese de que el objeto con el visualizador de estado está seleccionado en la jerarquía.
1. Selección de cualquier clip de animación en la ventana Animación
1. Seleccione **Agregar propiedad y** abra el plegado Representador de malla. 

    ![Adición de la propiedad animation en la ventana Animator](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. Esta lista contiene los nombres de todos los nombres de propiedad Animatable. 

    ![Propiedades de animación del representador de malla en la ventana Animator](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>Consulte también

- [**Botones**](../ux-building-blocks/button.md)
- [**Bounds (Control)**](../ux-building-blocks/bounds-control.md)
- [**Colección de objetos Grid**](../ux-building-blocks/object-collection.md)
- [**RadialView Solver**](../ux-building-blocks/solvers/solver.md)
