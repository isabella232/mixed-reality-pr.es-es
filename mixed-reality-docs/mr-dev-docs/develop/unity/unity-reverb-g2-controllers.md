---
title: Controladores de HP reverberación G2 en Unity
description: Obtenga información sobre cómo configurar y usar los nuevos controladores de HP reverberación G2 en aplicaciones SteamVR y Windows Mixed Reality Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberación, reverberación G2, HP reverberación G2, realidad mixta, desarrollo, controladores de movimiento, entrada de usuario, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos
ms.openlocfilehash: fa9b80076d65978ae1602fc4f9519d7e11c651b5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583570"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="a2a3a-104">Controladores de HP reverberación G2 en Unity</span><span class="sxs-lookup"><span data-stu-id="a2a3a-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="a2a3a-105">Los controladores de movimiento de HP son un nuevo tipo de controlador de Windows Mixed Reality: la misma tecnología de seguimiento con un conjunto de entradas disponibles ligeramente diferente:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="a2a3a-106">Touchpad se ha reemplazado por dos botones: A y B para el controlador derecho y X e y para el controlador izquierdo.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="a2a3a-107">El agarre es ahora un desencadenador que publica un flujo de valores entre 0,0 y 1,0 en lugar de un botón con Estados presionados y no presionados.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="a2a3a-108">Dado que no se puede acceder a las nuevas entradas a través de las API de Unity y Windows existentes, necesita el paquete UPM **Microsoft. MixedReality. Input** dedicado.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="a2a3a-109">**Las clases de este paquete no reemplazan a las API existentes de Windows y Unity, sino que las complementan.**</span><span class="sxs-lookup"><span data-stu-id="a2a3a-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="a2a3a-110">Las características que normalmente están disponibles para los controladores clásicos de Windows Mixed Reality y los controladores de movimiento de HP son accesibles a través de la misma ruta de acceso del código con las API existentes.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="a2a3a-111">Solo las nuevas entradas requieren el uso del paquete Microsoft. MixedReality. Input adicional.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="a2a3a-112">Introducción al controlador de movimiento de HP</span><span class="sxs-lookup"><span data-stu-id="a2a3a-112">HP Motion Controller overview</span></span>

<span data-ttu-id="a2a3a-113">*Microsoft. MixedReality. Input. MotionController* representa un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="a2a3a-114">Cada instancia de *MotionController* tiene un *XR. WSA. Input. InteractionSource* del mismo nivel, que se puede correlacionar mediante la mano, el ID. de proveedor, el ID. de producto y la versión.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="a2a3a-115">Puede obtener instancias de MotionController mediante la creación de un *MotionControllerWatcher* y la suscripción a sus eventos, de forma similar al uso de eventos *InteractionManager* para detectar nuevas instancias de *InteractionSource* .</span><span class="sxs-lookup"><span data-stu-id="a2a3a-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="a2a3a-116">Los métodos y propiedades de MotionController describen las entradas admitidas por el controlador, incluidos sus botones, desencadenadores, eje 2D y stick analógico.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="a2a3a-117">La clase MotionController también expone métodos para tener acceso a Estados de entrada a través de la clase *MotionControllerReading* .</span><span class="sxs-lookup"><span data-stu-id="a2a3a-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="a2a3a-118">La clase MotionControllerReading representa una instantánea del estado del controlador en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a><span data-ttu-id="a2a3a-119">Instalación de Microsoft. MixedReality. Input mediante el administrador de paquetes de Unity</span><span class="sxs-lookup"><span data-stu-id="a2a3a-119">Installing Microsoft.MixedReality.Input using the Unity Package Manager</span></span> 

<span data-ttu-id="a2a3a-120">El administrador de paquetes de Unity usa un [archivo de manifiesto](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.jsen) para determinar qué paquetes se deben instalar y los registros (servidores) desde los que se pueden instalar.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-120">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) they can be installed from.</span></span> <span data-ttu-id="a2a3a-121">Antes de poder usar el paquete Microsoft. MixedReality. Input, deberá registrar el servidor de componentes de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-121">Before you can use the Microsoft.MixedReality.Input package, you'll need to register the Mixed Reality component server.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="a2a3a-122">Registrar el servidor de componentes de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="a2a3a-122">Registering the Mixed Reality component server</span></span> 

<span data-ttu-id="a2a3a-123">Para cada proyecto que vaya a usar el paquete de entrada de realidad mixta, el manifest.jsen el archivo (en la carpeta paquetes) necesita agregar el registro con ámbito de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-123">For each project that will be using the Mixed Reality Input package, the manifest.json file (in the Packages folder) needs the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="a2a3a-124">Para modificar manifest.jscorrectamente en para admitir la realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-124">To properly modify manifest.json to support Mixed Reality:</span></span> 
    1. <span data-ttu-id="a2a3a-125">Abra <projectRoot> /Packages/manifest.jsen un editor de texto, como Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-125">Open <projectRoot>/Packages/manifest.json in a text editor, such as Visual Studio Code.</span></span> 
    2. <span data-ttu-id="a2a3a-126">En la parte superior del archivo de manifiesto, agregue el servidor de realidad mixta a la sección del registro con ámbito y guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-126">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span> 
    
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

### <a name="adding-the-microsoftmixedrealityinput-package"></a><span data-ttu-id="a2a3a-127">Agregar el paquete Microsoft. MixedReality. Input</span><span class="sxs-lookup"><span data-stu-id="a2a3a-127">Adding the Microsoft.MixedReality.Input package</span></span> 

<span data-ttu-id="a2a3a-128">Modifique la sección de dependencias del <projectRoot> /Packages/manifest.jsen el archivo en el editor de texto para agregar el paquete com. Microsoft. mixedreality. Input y guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-128">Modify the dependencies section of the <projectRoot>/Packages/manifest.json file in the text editor to add com.microsoft.mixedreality.input package and save the file.</span></span> 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="a2a3a-129">Usar Microsoft. MixedReality. Input</span><span class="sxs-lookup"><span data-stu-id="a2a3a-129">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="a2a3a-130">Valores de entrada</span><span class="sxs-lookup"><span data-stu-id="a2a3a-130">Input values</span></span>

<span data-ttu-id="a2a3a-131">Un MotionController puede exponer dos tipos de entradas:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-131">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="a2a3a-132">Los botones y los Estados de los desencadenadores se expresan mediante un valor Float único entre 0,0 y 1,0 que indica cuánto están presionados.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-132">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="a2a3a-133">Un botón solo puede devolver 0,0 (cuando no se presiona) o 1,0 (cuando se presiona) mientras un desencadenador puede devolver valores continuos entre 0,0 (totalmente liberados) a 1,0 (totalmente presionado).</span><span class="sxs-lookup"><span data-stu-id="a2a3a-133">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="a2a3a-134">El estado del Stick está expresado por un Vector2 cuyos componentes X e y están entre-1,0 y 1,0.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-134">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="a2a3a-135">Puede usar *MotionController. GetPressableInputs ()* para devolver una lista de entradas que devuelven un valor presionado (botones y desencadenadores) o el método *MotionController. GetXYInputs ()* para devolver una lista de entradas que devuelven un valor de 2 ejes.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-135">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="a2a3a-136">Una instancia de MotionControllerReading representa el estado del controlador en un momento dado:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-136">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="a2a3a-137">*GetPressedValue ()* recupera el estado de un botón o un desencadenador.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-137">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="a2a3a-138">*GetXYValue ()* recupera el estado de un stick.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-138">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="a2a3a-139">Creación de una memoria caché para mantener una colección de instancias de MotionController y sus Estados</span><span class="sxs-lookup"><span data-stu-id="a2a3a-139">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="a2a3a-140">Empiece creando una instancia de MotionControllerWatcher y registrando Controladores para sus eventos *MotionControllerAdded* y *MotionControllerRemoved* para mantener una memoria caché de instancias de MotionController disponibles.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-140">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="a2a3a-141">Esta memoria caché debe ser un monobehavior adjunto a un GameObject como se muestra en el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-141">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

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

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="a2a3a-142">Lectura de nuevas entradas mediante sondeo</span><span class="sxs-lookup"><span data-stu-id="a2a3a-142">Reading new inputs by polling</span></span> 

<span data-ttu-id="a2a3a-143">Puede leer el estado actual de cada controlador conocido a través de *MotionController. TryGetReadingAtTime* durante el método *Update* de la clase monobehavior.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-143">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="a2a3a-144">Desea pasar *DateTime. Now* como parámetro timestamp para asegurarse de que se lee el estado más reciente del controlador.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-144">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

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

<span data-ttu-id="a2a3a-145">Puede obtener el valor de entrada actual de los controladores mediante la mano del controlador:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-145">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

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

<span data-ttu-id="a2a3a-146">Por ejemplo, para leer el valor de agarre análogo de un InteractionSource:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-146">For example, to read the analog grasp value of an InteractionSource:</span></span> 

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

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="a2a3a-147">Generar eventos a partir de las nuevas entradas</span><span class="sxs-lookup"><span data-stu-id="a2a3a-147">Generating events from the new inputs</span></span> 

<span data-ttu-id="a2a3a-148">En lugar de sondear el estado de un controlador una vez por fotograma, tiene la opción de controlar todos los cambios de estado como eventos, lo que le permite controlar incluso las acciones más rápidas que duran menos que un fotograma.</span><span class="sxs-lookup"><span data-stu-id="a2a3a-148">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="a2a3a-149">Para que este enfoque funcione, la memoria caché de los controladores de movimiento debe procesar todos los Estados publicados por un controlador desde el último fotograma, lo que se puede hacer mediante el almacenamiento de la marca de tiempo de los últimos MotionControllerReading recuperados de un MotionController y la llamada a *MotionController. TryGetReadingAfterTime ()*:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-149">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

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

<span data-ttu-id="a2a3a-150">Ahora que ha actualizado las clases internas de caché, la clase monobehavior puede exponer dos eventos: pressed y released, y generarlos desde su método Update ():</span><span class="sxs-lookup"><span data-stu-id="a2a3a-150">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

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

<span data-ttu-id="a2a3a-151">La estructura de los ejemplos de código anteriores hace que el registro de eventos sea mucho más legible:</span><span class="sxs-lookup"><span data-stu-id="a2a3a-151">The structure in the above code examples makes registering events much more readable:</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="a2a3a-152">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a2a3a-152">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->