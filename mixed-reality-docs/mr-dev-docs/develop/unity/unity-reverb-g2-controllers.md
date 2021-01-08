---
title: Controladores de HP reverberación G2 en Unity
description: Obtenga información sobre cómo configurar y usar los nuevos controladores de HP reverberación G2 en aplicaciones SteamVR y Windows Mixed Reality Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberación, reverberación G2, HP reverberación G2, realidad mixta, desarrollo, controladores de movimiento, entrada de usuario, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos
ms.openlocfilehash: 1c9d8f1279f81ea1d8020e2a3c689dae86496221
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009835"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Controladores de HP reverberación G2 en Unity

Los controladores de movimiento de HP son un nuevo tipo de controlador de Windows Mixed Reality: la misma tecnología de seguimiento con un conjunto de entradas disponibles ligeramente diferente: 

* Touchpad se ha reemplazado por dos botones: A y B para el controlador derecho y X e y para el controlador izquierdo. 
* El agarre es ahora un desencadenador que publica un flujo de valores entre 0,0 y 1,0 en lugar de un botón con Estados presionados y no presionados. 

Dado que no se puede acceder a las nuevas entradas a través de las API de Unity y Windows existentes, necesita el paquete UPM **Microsoft. MixedReality. Input** dedicado. 

> [!IMPORTANT]
> **Las clases de este paquete no reemplazan a las API existentes de Windows y Unity, sino que las complementan.** Las características que normalmente están disponibles para los controladores clásicos de Windows Mixed Reality y los controladores de movimiento de HP son accesibles a través de la misma ruta de acceso del código con las API existentes. Solo las nuevas entradas requieren el uso del paquete Microsoft. MixedReality. Input adicional. 

## <a name="hp-motion-controller-overview"></a>Introducción al controlador de movimiento de HP

*Microsoft. MixedReality. Input. MotionController* representa un controlador de movimiento. Cada instancia de *MotionController* tiene un *XR. WSA. Input. InteractionSource* del mismo nivel, que se puede correlacionar mediante la mano, el ID. de proveedor, el ID. de producto y la versión. 

Puede obtener instancias de MotionController mediante la creación de un *MotionControllerWatcher* y la suscripción a sus eventos, de forma similar al uso de eventos *InteractionManager* para detectar nuevas instancias de *InteractionSource* . Los métodos y propiedades de MotionController describen las entradas admitidas por el controlador, incluidos sus botones, desencadenadores, eje 2D y stick analógico. La clase MotionController también expone métodos para tener acceso a Estados de entrada a través de la clase *MotionControllerReading* . La clase MotionControllerReading representa una instantánea del estado del controlador en un momento dado. 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a>Instalación de Microsoft. MixedReality. Input mediante el administrador de paquetes de Unity 

El administrador de paquetes de Unity usa un [archivo de manifiesto](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.jsen) para determinar qué paquetes se deben instalar y los registros (servidores) desde los que se pueden instalar. Antes de poder usar el paquete Microsoft. MixedReality. Input, deberá registrar el servidor de componentes de realidad mixta.

### <a name="registering-the-mixed-reality-component-server"></a>Registrar el servidor de componentes de realidad mixta 

Para cada proyecto que vaya a usar el paquete de entrada de realidad mixta, el manifest.jsen el archivo (en la carpeta paquetes) necesita agregar el registro con ámbito de realidad mixta. Para modificar manifest.jscorrectamente en para admitir la realidad mixta: 
    1. Abra <projectRoot> /Packages/manifest.jsen un editor de texto, como Visual Studio Code. 
    2. En la parte superior del archivo de manifiesto, agregue el servidor de realidad mixta a la sección del registro con ámbito y guarde el archivo. 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a>Agregar el paquete Microsoft. MixedReality. Input 

Modifique la sección de dependencias del <projectRoot> /Packages/manifest.jsen el archivo en el editor de texto para agregar el paquete com. Microsoft. mixedreality. Input y guarde el archivo. 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a>Usar Microsoft. MixedReality. Input 

### <a name="input-values"></a>Valores de entrada

Un MotionController puede exponer dos tipos de entradas: 

* Los botones y los Estados de los desencadenadores se expresan mediante un valor Float único entre 0,0 y 1,0 que indica cuánto están presionados.
    * Un botón solo puede devolver 0,0 (cuando no se presiona) o 1,0 (cuando se presiona) mientras un desencadenador puede devolver valores continuos entre 0,0 (totalmente liberados) a 1,0 (totalmente presionado). 
* El estado del Stick está expresado por un Vector2 cuyos componentes X e y están entre-1,0 y 1,0. 

Puede usar *MotionController. GetPressableInputs ()* para devolver una lista de entradas que devuelven un valor presionado (botones y desencadenadores) o el método *MotionController. GetXYInputs ()* para devolver una lista de entradas que devuelven un valor de 2 ejes. 

Una instancia de MotionControllerReading representa el estado del controlador en un momento dado: 

* *GetPressedValue ()* recupera el estado de un botón o un desencadenador. 
* *GetXYValue ()* recupera el estado de un stick. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>Creación de una memoria caché para mantener una colección de instancias de MotionController y sus Estados 

Empiece creando una instancia de MotionControllerWatcher y registrando Controladores para sus eventos *MotionControllerAdded* y *MotionControllerRemoved* para mantener una memoria caché de instancias de MotionController disponibles. Esta memoria caché debe ser un monobehavior adjunto a un GameObject como se muestra en el código siguiente:

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a>Lectura de nuevas entradas mediante sondeo 

Puede leer el estado actual de cada controlador conocido a través de *MotionController. TryGetReadingAtTime* durante el método *Update* de la clase monobehavior. Desea pasar *DateTime. Now* como parámetro timestamp para asegurarse de que se lee el estado más reciente del controlador. 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

Puede obtener el valor de entrada actual de los controladores mediante la mano del controlador: 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

Por ejemplo, para leer el valor de agarre análogo de un InteractionSource: 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a>Generar eventos a partir de las nuevas entradas 

En lugar de sondear el estado de un controlador una vez por fotograma, tiene la opción de controlar todos los cambios de estado como eventos, lo que le permite controlar incluso las acciones más rápidas que duran menos que un fotograma. Para que este enfoque funcione, la memoria caché de los controladores de movimiento debe procesar todos los Estados publicados por un controlador desde el último fotograma, lo que se puede hacer mediante el almacenamiento de la marca de tiempo de los últimos MotionControllerReading recuperados de un MotionController y la llamada a *MotionController. TryGetReadingAfterTime ()*: 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

Ahora que ha actualizado las clases internas de caché, la clase monobehavior puede exponer dos eventos: pressed y released, y generarlos desde su método Update (): 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

La estructura de los ejemplos de código anteriores hace que el registro de eventos sea mucho más legible: 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a>Consulte también

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->