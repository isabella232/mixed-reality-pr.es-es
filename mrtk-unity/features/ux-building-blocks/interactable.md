---
title: Interactuable
description: Información general sobre el componente de script interactable en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Interactable, Eventos,
ms.openlocfilehash: a0aee99d01ae59a8ebedc4d62a4b0aaf844a7afaa6961bbfd05238dd9d5b673d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206815"
---
# <a name="interactable"></a>Interactuable

![Interactuable](../images/interactable/InteractableExamples.png)

El componente es un contenedor todo en uno para que cualquier objeto pueda interactuar fácilmente y [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) responder a la entrada.  Interactable actúa como un elemento de entrada para todos los tipos de entrada, [](#events) incluidos el toque, los rayos de las manos, la voz, etc. y canaliza estas interacciones en eventos y respuestas [de temas](visual-themes.md) visuales. Este componente proporciona una manera sencilla de crear botones, cambiar el color de los objetos con el foco, etc.

## <a name="how-to-configure-interactable"></a>Configuración de Interactable

El componente permite tres secciones principales de configuración:

1) [Configuración de entrada general](#general-input-settings)
1) [Temas visuales dirigidos](visual-themes.md) a varios Objetos GameObject
1) [Controladores de eventos](#events)

### <a name="general-input-settings"></a>Configuración de entrada general

![General Interactable Configuración](../images/interactable/InputFeatures_short.png)

**States**

*States* es un [parámetro ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) que define las fases de interacciones, como presionar o observar, para perfiles [interactuables](#interactable-profiles) y [temas visuales.](visual-themes.md)

**DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) se incluye con MRTK de fábrica y es el parámetro predeterminado para los componentes *interactables.*

![Ejemplo de ScriptableObject de estados en inspector](../images/interactable/DefaultInteractableStates.png)

El *recurso DefaultInteractableStates* contiene cuatro estados y utiliza la implementación [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) del modelo de estado.

* **Valor** predeterminado: no ocurre nada, es el estado base más aislado.

* **Foco:** se apunta al objeto . Se trata de un estado único, no hay ningún otro estado establecido actualmente, pero se clasificará por rango Predeterminado.

* **Presione**: se apunta al objeto y se presiona un botón o una mano. El estado Press (Presionar) clasifica Default (Predeterminado) y Focus (Foco). Este estado también se establecerá como reserva en La presión física.

* **Deshabilitado:** el botón no debe ser interactivo y los comentarios visuales permitirán al usuario saber si, por algún motivo, este botón no se puede usar en este momento. En teoría, el estado deshabilitado podría contener todos los demás estados, pero cuando habilitado está desactivado, el estado Deshabilitado se convierte en el resto de estados.

Un valor de bit (#) se asigna al estado en función del orden de la lista.

> [!NOTE]
> Por lo general, se recomienda usar **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) al crear componentes *interactables.*
>
> Sin embargo, hay 17 estados interactuables disponibles que se pueden usar para impulsar temas, aunque algunos están diseñados para ser controlados por otros componentes. Esta es una lista de aquellos con funcionalidad integrada.
>
> * Visitada: se ha hecho clic en Interactable.
> * Alternancia: el botón está en un estado alternado o índice de dimensión es un número impar.
> * Gesto: se presionó la mano o el controlador y se ha movido desde la posición original.
> * VoiceCommand: se usó un comando de voz para desencadenar Interactable.
> * PhysicalTouch: actualmente se detecta una entrada táctil, que se [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) usa para habilitar.
> * Agarre: una mano está agarrándose actualmente en los límites del objeto, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) para habilitar

**Habilitado**

Alterna si un objeto Interactable se iniciará habilitado o no. Esto corresponde a en [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) el código.

La *propiedad habilitada de Interactable* es diferente de la propiedad habilitada configurada a través de GameObject/Component (es decir, SetActive, etc.). Deshabilitar GameObject o MonoBehaviour *interactable* deshabilitará la ejecución de todo en la clase, incluidos la entrada, los temas visuales, los eventos, etc. Deshabilitar a través [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) de deshabilitará la mayoría del control de entrada y restablecerá los estados de entrada relacionados. Sin embargo, la clase ejecutará todos los fotogramas y recibirá eventos de entrada que se omitirán. Esto es útil para mostrar interactuable en un estado deshabilitado que se puede hacer a través de temas visuales. Un ejemplo típico de esto sería un botón enviar en espera de que se completen todos los campos de entrada necesarios.

**Acciones de entrada**

Seleccione la acción [de entrada del](../input/input-actions.md) perfil de asignación de controlador o configuración de entrada al que debe reaccionar el componente *Interactable.*

Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .

**IsGlobal**

Si es true, marcará el componente como un agente de escucha de entrada global para la acción [de entrada seleccionada.](../input/input-actions.md) El comportamiento predeterminado es false, lo que restringirá la entrada solo a *este colisionador* o GameObject interactuable.

Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .

**Comando de voz**

[Comando de voz](../input/speech.md), desde el perfil de comandos de voz de MRTK, para desencadenar un evento OnClick para la interacción de voz.

Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .

**Requiere foco**

Si es true, el comando de voz solo activará *interactuable* si y solo si ya tiene el foco de un puntero. Si es false, *Interactable* actuará como un agente de escucha global para el comando de voz seleccionado. El comportamiento predeterminado es true, ya que varios agentes de escucha de voz globales pueden ser difíciles de organizar en una escena.

Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .

**Modo de selección**

Esta propiedad define la lógica de selección. Cuando se hace clic en un objeto *Interactable,* itera en el siguiente nivel *de* dimensión. *Las dimensiones* son similares a rank y definen un estado fuera de las entradas (es decir, con el foco, presione etc.). Son útiles para definir estados de alternancia u otros estados de varias rangos asociados a un botón. El seguimiento del nivel de dimensión actual se realiza mediante `Interactable.DimensionIndex` .

Los modos de selección disponibles son:

* **Botón**  -  *Dimensiones* = 1, simple interactable en el que se puede *hacer clic*
* **Alternar**  -  *Dimensiones* = 2, *alternativas interactuables* entre *el estado de* on / *off*
* **Varias dimensiones**  -  *Dimensiones >* = 3, cada clic aumenta el nivel de dimensión actual + 1. Resulta útil para definir un estado de botón en una lista, etc.

*Interactable* también permite definir varios temas por *dimensión.* Por ejemplo, *cuando SelectionMode=Toggle*, se puede aplicar un tema cuando se *deselecciona* *Interactable* y se aplica otro tema cuando se selecciona el *componente*.

El modo de selección actual se puede consultar en tiempo de ejecución a través de [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) . La actualización del modo en tiempo de ejecución se puede lograr estableciendo la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) propiedad para que coincida con la funcionalidad deseada. Además, se puede acceder a la dimensión actual, útil para los modos *Alternar* y Multi *dimension,* a través de [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .

### <a name="interactable-profiles"></a>Perfiles interactuables

*Los perfiles* son elementos que crean una relación entre gameObject y un [tema visual.](visual-themes.md) El perfil define qué contenido manipulará un tema cuando se [produzca un cambio de estado.](#general-input-settings)

Los temas funcionan mucho como materiales. Son objetos que pueden incluir scripts que contienen una lista de propiedades que se asignarán a un objeto en función del estado actual. Los temas también se pueden volver a usar y se pueden asignar a través de varios objetos de experiencia de usuario *interactuable.*

**Restablecer al destruir**

Los temas visuales modifican varias propiedades en un GameObject de destino, en función de la clase y el tipo de motor de tema seleccionados. Si *restablecer al destruir es* true cuando se destruye el componente Interactable, el componente restablecerá todas las propiedades modificadas de los temas activos a sus valores originales. De lo contrario, cuando se destruye, el componente Interactable dejará las propiedades modificadas tal y como están. En este último caso, el último estado de los valores se conservará a menos que otro componente externo lo haya modificado. El valor predeterminado es false.

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>Eventos

Cada *componente interactuable* tiene un *evento OnClick* que se produce cuando el componente se selecciona simplemente. Sin embargo, *Interactable* se puede usar para detectar eventos de entrada que no sean solo *OnClick.*

Haga clic en *el botón Agregar* evento para agregar un nuevo tipo de definición de receptor de eventos. Una vez agregado, seleccione el tipo de evento deseado.

![Ejemplo de eventos](../images/interactable/Events.png))

Hay diferentes tipos de receptores de eventos para responder a diferentes tipos de entrada. MRTK se suministra con el siguiente conjunto de receptores de serie.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

Se puede crear un receptor personalizado creando una nueva clase que extienda [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .

![Ejemplo de receptor de alternancia de eventos](../images/interactable/Event_toggle.png)

*Ejemplo de un receptor de eventos toggle*

### <a name="interactable-receivers"></a>Receptores interactuables

 El componente permite definir eventos fuera del [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente *interactuable de* origen. *InteractableReceiver escuchará* un tipo de evento filtrado desencadenado por otro *objeto Interactable.* Si la propiedad *Interactable* no está  asignada directamente, la propiedad Ámbito de búsqueda define la dirección en la que *InteractableReceiver* escucha eventos que están en sí mismo, en un elemento primario o en un elemento GameObject secundario.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) actúa de forma similar, pero para una lista de eventos de coincidencia.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>Creación de eventos personalizados

Al [igual que los temas](visual-themes.md#custom-theme-engines)visuales, los eventos se pueden extender para detectar cualquier patrón de estado o para exponer la funcionalidad.

Los eventos personalizados se pueden crear de dos maneras principales:

1) [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase)Extienda la clase para crear un evento personalizado que se mostrará en la lista desplegable de tipos de eventos. Se proporciona un evento de Unity de forma predeterminada, pero se pueden agregar eventos de Unity adicionales o se puede establecer el evento para ocultar los eventos de Unity. Esta funcionalidad permite a un diseñador trabajar con un ingeniero en un proyecto para crear un evento personalizado que el diseñador puede configurar en el editor.

1) [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)Extienda la clase para crear un componente de evento completamente personalizado que pueda residir en *interactuable* u otro objeto. hará [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) referencia a *Interactable para* detectar cambios de estado.

#### <a name="example-of-extending-receiverbase"></a>Ejemplo de extensión `ReceiverBase`

La [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) clase muestra información de estado sobre un objeto *Interactable* y es un ejemplo de cómo crear un receptor de eventos personalizado.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

Los métodos siguientes son útiles para invalidar o implementar al crear un receptor de eventos personalizado. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) es un método abstracto que se puede usar para detectar patrones de estado o transiciones. Además, los [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) métodos y son útiles para crear lógica de eventos personalizada cuando se selecciona *Interactable.*

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>Mostrar campos de receptor de eventos personalizados en el inspector

Los scripts *de ReceiverBase* [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) usan atributos para exponer propiedades personalizadas en el inspector. Este es un ejemplo de Vector3, una propiedad personalizada con información sobre herramientas y etiquetas. Esta propiedad se mostrará como configurable en el inspector cuando se selecciona un GameObject *interactuable* y se agrega el tipo *de receptor* de eventos asociado.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Uso de Interactable

### <a name="building-a-simple-button"></a>Creación de un botón sencillo

Se puede crear un botón simple agregando el *componente Interactable* a un GameObject que está configurado para recibir eventos de entrada. Puede tener un colisionador en él o en un elemento secundario para recibir la entrada. Si usa *Interactable* with a Unity UI based GameObjects (Objetos GameObject basados en interfaz de usuario de Unity), debe estar en Canvas GameObject.

Tome el botón un paso más allá, mediante la creación de un nuevo perfil, la asignación del propio GameObject y la creación de un nuevo tema. Además, use el *evento OnClick* para que suceda algo.

> [!NOTE]
> Hacer que [un botón se presione](button.md) requiere el componente [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) . Además, el componente es necesario para embudo de los eventos [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) de presión en el componente *Interactable.*

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Creación de botones de alternancia y de varias dimensiones

#### <a name="toggle-button"></a>Botón de alternancia

Para que un botón pueda alternar, cambie el [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo para escribir `Toggle` . En la *sección Perfiles,* se agrega un nuevo tema alternado para cada perfil que se usa cuando se activa *interactuable.*

Mientras se establece en Toggle, se puede usar la casilla [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) *IsToggled* para establecer el valor predeterminado del control en la inicialización en tiempo de ejecución.

*CanSelect* significa que *Interactable* puede pasar de *desactivado* a *on,* mientras que *CanDeselect* significa inverso.

![Ejemplo de temas visuales de alternancia de perfil](../images/interactable/Profile_toggle.png)

Los desarrolladores pueden usar las interfaces y para obtener o establecer el estado de alternancia [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) de un objeto *Interactable* mediante código.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Alternar colección de botones

Es habitual tener una lista de botones de alternancia donde solo uno puede estar activo en un momento dado, también conocido como un conjunto radial o botones de radio, etc.

Use el [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente para habilitar esta funcionalidad. Este control garantiza que solo se *active un interactuable* en un momento dado. *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) también es un excelente punto de partida.

Para crear un grupo de botones radiales personalizado:

1) Crear varios *botones* y objetos GameObjects interactuables
1) Establecer cada *interactuable* con *SelectionMode* = Toggle, *CanSelect* = true y *CanDeselect* = false
1) Cree un elemento GameObject primario vacío en *todos los elementos Interactables* y agregue el *componente InteractableToggleCollection.*
1) Agregar todos *los elementos Interactable a* *ToggleList* en *InteractableToggleCollection*
1) Establezca la *propiedad InteractableToggleCollection.CurrentIndex* para determinar qué botón está seleccionado de forma predeterminada al principio.

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>Botón multidimensional

El modo de selección de varias dimensiones se usa para crear botones secuenciales, o un botón que tiene más de dos pasos, como controlar la velocidad con tres valores, Rápido (1x), Más rápido (2x) o Más rápido (3x).

Como las dimensiones son un valor numérico, se pueden agregar hasta 9 temas para controlar la etiqueta de texto o la textura del botón para cada configuración de velocidad, usando un tema diferente para cada paso.

Cada evento de clic avanzará en 1 en tiempo `DimensionIndex` de ejecución hasta que se alcance el `Dimensions` valor. A continuación, el ciclo se restablecerá a 0.

![Ejemplo de perfil multidimensional](../images/interactable/Profile_multiDimensions.png)

Los desarrolladores pueden evaluar [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) para determinar qué dimensión está activa actualmente.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Creación de Interactable en tiempo de ejecución

*Interactable* se puede agregar fácilmente a cualquier GameObject en tiempo de ejecución. En el ejemplo siguiente se muestra cómo asignar un perfil con un [tema visual](visual-themes.md).

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a>Eventos interactuables a través de código

Se puede agregar una acción al evento base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) a través del código con el ejemplo siguiente.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Use la [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) función para agregar receptores de eventos dinámicamente en tiempo de ejecución.

En el código de ejemplo siguiente se muestra cómo agregar un [objeto InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escucha la entrada y salida del foco, y, además, definir código de acción para realizar cuando se desencierten las instancias de evento.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

En el código de ejemplo siguiente se muestra cómo agregar un [objeto InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escucha las transiciones de estado seleccionadas o deseleccionada en interactuables con alternancia y, además, define el código de acción que se debe realizar cuando se activen las instancias de evento. 

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a>Consulte también

* [Temas visuales](visual-themes.md)
* [Acciones de entrada](../input/input-actions.md)
* [Comandos de voz](../input/speech.md)
* [Botones](button.md)
* [Sombreador estándar de MRTK](../rendering/MRTK-standard-shader.md)
