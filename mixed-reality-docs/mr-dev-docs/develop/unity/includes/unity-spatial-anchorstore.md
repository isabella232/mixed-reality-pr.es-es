---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603397"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="7fa7c-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="7fa7c-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="7fa7c-102">Estos delimitadores se guardan y se cargan en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="7fa7c-103">El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="7fa7c-104">Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRAnchorSubsystem, el subsistema de ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="7fa7c-105">Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="7fa7c-106">Para ver un ejemplo completo de los delimitadores persistentes o no persistentes, consulte el script delimitadores-> delimitadores de ejemplo GameObject y AnchorsSample.cs en la [escena de ejemplo de complemento Mixed Reality OpenXR](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="7fa7c-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de pantalla del panel de jerarquías abierto en el editor de Unity con el ejemplo de anclajes resaltado](../images/openxr-features-img-04.png)

![Captura de pantalla del panel de inspectores abierta en el editor de Unity con el script de ejemplo de delimitadores resaltado](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="7fa7c-109">Complemento de Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="7fa7c-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="7fa7c-110">Estos delimitadores se guardan y se cargan en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="7fa7c-111">El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="7fa7c-112">Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), el subsistema de ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="7fa7c-113">Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación para Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="7fa7c-114">o para Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="7fa7c-115">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="7fa7c-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="7fa7c-116">**Espacio de nombres:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="7fa7c-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="7fa7c-117">**Clase:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="7fa7c-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="7fa7c-118">El WorldAnchorStore le permitirá conservar la ubicación de los WorldAnchor de las sesiones.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="7fa7c-119">Para conservar los hologramas en todas las sesiones, deberá realizar un seguimiento por separado de los GameObjects que usan un delimitador mundial determinado.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="7fa7c-120">A menudo tiene sentido crear una raíz GameObject con un delimitador mundial y tener los hologramas secundarios anclados por él con un desplazamiento de posición local.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="7fa7c-121">Para cargar hologramas de sesiones anteriores:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="7fa7c-122">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="7fa7c-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="7fa7c-123">Cargar datos de la aplicación relacionados con el anclaje mundial, que le proporciona el identificador del anclaje mundial</span><span class="sxs-lookup"><span data-stu-id="7fa7c-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="7fa7c-124">Carga de un delimitador mundial desde su identificador</span><span class="sxs-lookup"><span data-stu-id="7fa7c-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="7fa7c-125">Para guardar los hologramas para las sesiones futuras:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="7fa7c-126">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="7fa7c-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="7fa7c-127">Guardar un delimitador mundial especificando un identificador</span><span class="sxs-lookup"><span data-stu-id="7fa7c-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="7fa7c-128">Guardar datos de la aplicación relacionados con el delimitador mundial junto con un identificador</span><span class="sxs-lookup"><span data-stu-id="7fa7c-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="7fa7c-129">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="7fa7c-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="7fa7c-130">Querrá mantener una referencia a WorldAnchorStore para que sepa cuándo está listo para realizar una operación.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="7fa7c-131">Dado que se trata de una llamada asincrónica, posiblemente en cuanto se inicia, desea llamar a:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="7fa7c-132">En este caso, StoreLoaded es el controlador para cuando se haya completado la carga de WorldAnchorStore:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="7fa7c-133">Ahora tenemos una referencia a WorldAnchorStore, que usaremos para guardar y cargar delimitadores del mundo específicos.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="7fa7c-134">Guardar un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="7fa7c-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="7fa7c-135">Para ahorrar, simplemente necesitamos asignar un nombre a lo que estamos guardando y pasarlo en el WorldAnchor que obtuvimos antes cuando queremos ahorrar.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="7fa7c-136">Nota: Si intenta guardar dos delimitadores en la misma cadena, se producirá un error (Store. Save devolverá FALSE).</span><span class="sxs-lookup"><span data-stu-id="7fa7c-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="7fa7c-137">Elimine el guardado anterior antes de guardar el nuevo:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-137">Delete the previous save before saving the new one:</span></span>

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="7fa7c-138">Carga de un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="7fa7c-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="7fa7c-139">Y para cargar:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-139">And to load:</span></span>

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

<span data-ttu-id="7fa7c-140">Además, podemos usar Store. Elimine () para quitar un delimitador que se guardó y almacenó anteriormente. Borre () para quitar todos los datos guardados previamente.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="7fa7c-141">Enumerar delimitadores existentes</span><span class="sxs-lookup"><span data-stu-id="7fa7c-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="7fa7c-142">Para detectar los delimitadores almacenados previamente, llame a GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="7fa7c-143">Creación de una experiencia de escala mundial</span><span class="sxs-lookup"><span data-stu-id="7fa7c-143">Building a world-scale experience</span></span>

<span data-ttu-id="7fa7c-144">**Espacio de nombres:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="7fa7c-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="7fa7c-145">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="7fa7c-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="7fa7c-146">En el caso de **experiencias** reales en HoloLens que permitan a los usuarios ir más allá de 5 metros, necesitará nuevas técnicas más allá de las que se usan para experiencias a escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="7fa7c-147">Una técnica clave que se va a usar es crear un [delimitador espacial](../../../design/coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas precisamente en su lugar en el mundo físico, con independencia de cuánto se haya desplazado el usuario y, a continuación, [volver a buscar esos hologramas en sesiones posteriores](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="7fa7c-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="7fa7c-148">En Unity, puede crear un delimitador espacial agregando el componente Unity de **WorldAnchor** a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="7fa7c-149">Agregar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="7fa7c-149">Adding a World Anchor</span></span>

<span data-ttu-id="7fa7c-150">Para agregar un delimitador mundial, llame a `AddComponent<WorldAnchor>()` en el objeto de juego con la transformación que quiere delimitar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="7fa7c-151">Ya está.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-151">That's it!</span></span> <span data-ttu-id="7fa7c-152">Este objeto de juego se anclará ahora a su ubicación actual en el mundo físico; puede ver que las coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar la alineación física.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="7fa7c-153">Consulte [carga de un anclaje mundial](#loading-a-worldanchor) para volver a encontrar esta ubicación anclada en una sesión de aplicación futura.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="7fa7c-154">Quitar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="7fa7c-154">Removing a World Anchor</span></span>

<span data-ttu-id="7fa7c-155">Si ya no desea que el GameObject esté bloqueado en una ubicación física del mundo y no tiene intención de moverlo a este fotograma, puede llamar simplemente a Destroy en el componente del mundo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="7fa7c-156">Si desea trasladar GameObject este fotograma, debe llamar a DestroyImmediate en su lugar.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="7fa7c-157">Mover un GameObject anclado mundial</span><span class="sxs-lookup"><span data-stu-id="7fa7c-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="7fa7c-158">No se puede cambiar GameObject mientras un delimitador internacional está en él.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="7fa7c-159">Si necesita trasladar el GameObject de este marco, debe:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="7fa7c-160">DestroyImmediate el componente de anclaje mundial</span><span class="sxs-lookup"><span data-stu-id="7fa7c-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="7fa7c-161">Movimiento del GameObject</span><span class="sxs-lookup"><span data-stu-id="7fa7c-161">Move the GameObject</span></span>
3. <span data-ttu-id="7fa7c-162">Agregue un nuevo componente de anclaje mundial a GameObject.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="7fa7c-163">Control de los cambios de ubicación</span><span class="sxs-lookup"><span data-stu-id="7fa7c-163">Handling Locatability Changes</span></span>

<span data-ttu-id="7fa7c-164">Es posible que WorldAnchor no se pueda localizar en el mundo físico en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="7fa7c-165">Si esto ocurre, Unity no actualizará la transformación del objeto delimitado.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="7fa7c-166">Esto también puede cambiar mientras se ejecuta una aplicación.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-166">This also can change while an app is running.</span></span> <span data-ttu-id="7fa7c-167">Si no se controla el cambio en la localización, el objeto no aparecerá en la ubicación física correcta del mundo.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="7fa7c-168">Para recibir notificaciones sobre los cambios de Ubicación:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="7fa7c-169">Suscribirse al evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="7fa7c-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="7fa7c-170">Controlar el evento</span><span class="sxs-lookup"><span data-stu-id="7fa7c-170">Handle the event</span></span>

<span data-ttu-id="7fa7c-171">Se llamará al evento **OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado que se pueda localizar y que no se pueda localizar.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="7fa7c-172">A continuación, controle el evento:</span><span class="sxs-lookup"><span data-stu-id="7fa7c-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="7fa7c-173">A veces, los delimitadores se colocan inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="7fa7c-174">En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando AddComponent <WorldAnchor> () devuelva.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="7fa7c-175">Como resultado, el evento OnTrackingChanged no se desencadenará.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="7fa7c-176">Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="7fa7c-177">Persistencia de hologramas para varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="7fa7c-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="7fa7c-178">Puede usar los <a href="/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede ubicar a continuación en varios dispositivos HoloLens, iOS y Android, incluso si dichos dispositivos no están presentes juntos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="7fa7c-179">Dado que los delimitadores en la nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="7fa7c-180">Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="7fa7c-181">Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="7fa7c-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
