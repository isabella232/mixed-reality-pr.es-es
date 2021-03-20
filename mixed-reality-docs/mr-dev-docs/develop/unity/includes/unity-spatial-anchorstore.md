---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719818"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="9e18b-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="9e18b-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="9e18b-102">Una API adicional denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="9e18b-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="9e18b-103">XRAnchorStore es una representación de los delimitadores guardados en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e18b-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="9e18b-104">Los delimitadores se pueden conservar de **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en nuevo **ARAnchors** o eliminarse del almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="9e18b-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="9e18b-105">Estos delimitadores se guardan y se cargan en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e18b-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="9e18b-106">El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="9e18b-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="9e18b-107">Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRAnchorSubsystem, el subsistema de ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="9e18b-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="9e18b-108">Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="9e18b-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="9e18b-109">Para ver un ejemplo completo de los delimitadores de persistencia y despersistencia, consulte el script delimitadores-> delimitadores de ejemplo GameObject y AnchorsSample. CS en la [escena de ejemplo de complemento de realidad mixta OpenXR](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="9e18b-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de pantalla del panel de jerarquías abierto en el editor de Unity con el ejemplo de anclajes resaltado](../images/openxr-features-img-04.png)

![Captura de pantalla del panel de inspectores abierta en el editor de Unity con el script de ejemplo de delimitadores resaltado](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="9e18b-112">Complemento de Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="9e18b-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="9e18b-113">Una API denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="9e18b-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="9e18b-114">XRAnchorStore es una representación de los delimitadores guardados en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e18b-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="9e18b-115">Los delimitadores se pueden conservar de **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en nuevo **ARAnchors** o eliminarse del almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="9e18b-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="9e18b-116">Estos delimitadores se guardan y se cargan en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e18b-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="9e18b-117">El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="9e18b-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="9e18b-118">Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), el subsistema de ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="9e18b-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="9e18b-119">Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación para Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="9e18b-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="9e18b-120">o para Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="9e18b-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="9e18b-121">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="9e18b-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="9e18b-122">**WorldAnchorStore** es la clave para crear experiencias holográficas en las que los hologramas permanecen en posiciones específicas del mundo real entre instancias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9e18b-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="9e18b-123">Después, los usuarios pueden anclar los hologramas individuales dondequiera que quieran y encontrarlos más adelante en el mismo punto en muchos usos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9e18b-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="9e18b-124">**Espacio de nombres:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="9e18b-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="9e18b-125">**Clase:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="9e18b-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="9e18b-126">El WorldAnchorStore le permitirá conservar la ubicación de los WorldAnchor de las sesiones.</span><span class="sxs-lookup"><span data-stu-id="9e18b-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="9e18b-127">Para conservar los hologramas en todas las sesiones, deberá realizar un seguimiento por separado de los GameObjects que usan un delimitador mundial determinado.</span><span class="sxs-lookup"><span data-stu-id="9e18b-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="9e18b-128">A menudo tiene sentido crear una raíz GameObject con un delimitador mundial y tener los hologramas secundarios anclados por él con un desplazamiento de posición local.</span><span class="sxs-lookup"><span data-stu-id="9e18b-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="9e18b-129">Para cargar hologramas de sesiones anteriores:</span><span class="sxs-lookup"><span data-stu-id="9e18b-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="9e18b-130">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9e18b-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9e18b-131">Cargar datos de la aplicación relacionados con el anclaje mundial, que le proporciona el identificador del anclaje mundial</span><span class="sxs-lookup"><span data-stu-id="9e18b-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="9e18b-132">Carga de un delimitador mundial desde su identificador</span><span class="sxs-lookup"><span data-stu-id="9e18b-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="9e18b-133">Para guardar los hologramas para las sesiones futuras:</span><span class="sxs-lookup"><span data-stu-id="9e18b-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="9e18b-134">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9e18b-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9e18b-135">Guardar un delimitador mundial especificando un identificador</span><span class="sxs-lookup"><span data-stu-id="9e18b-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="9e18b-136">Guardar datos de la aplicación relacionados con el delimitador mundial junto con un identificador</span><span class="sxs-lookup"><span data-stu-id="9e18b-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="9e18b-137">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9e18b-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="9e18b-138">Querrá mantener una referencia a WorldAnchorStore para que sepa cuándo está listo para realizar una operación.</span><span class="sxs-lookup"><span data-stu-id="9e18b-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="9e18b-139">Dado que se trata de una llamada asincrónica, posiblemente en cuanto se inicia, desea llamar a:</span><span class="sxs-lookup"><span data-stu-id="9e18b-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="9e18b-140">En este caso, StoreLoaded es el controlador para cuando se haya completado la carga de WorldAnchorStore:</span><span class="sxs-lookup"><span data-stu-id="9e18b-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="9e18b-141">Ahora tenemos una referencia a WorldAnchorStore, que usaremos para guardar y cargar delimitadores del mundo específicos.</span><span class="sxs-lookup"><span data-stu-id="9e18b-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="9e18b-142">Guardar un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="9e18b-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="9e18b-143">Para ahorrar, simplemente necesitamos asignar un nombre a lo que estamos guardando y pasarlo en el WorldAnchor que obtuvimos antes cuando queremos ahorrar.</span><span class="sxs-lookup"><span data-stu-id="9e18b-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="9e18b-144">Nota: Si intenta guardar dos delimitadores en la misma cadena, se producirá un error (Store. Save devolverá FALSE).</span><span class="sxs-lookup"><span data-stu-id="9e18b-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="9e18b-145">Elimine el guardado anterior antes de guardar el nuevo:</span><span class="sxs-lookup"><span data-stu-id="9e18b-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="9e18b-146">Carga de un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="9e18b-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="9e18b-147">Y para cargar:</span><span class="sxs-lookup"><span data-stu-id="9e18b-147">And to load:</span></span>

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

<span data-ttu-id="9e18b-148">Además, podemos usar Store. Elimine () para quitar un delimitador que se guardó y almacenó anteriormente. Borre () para quitar todos los datos guardados previamente.</span><span class="sxs-lookup"><span data-stu-id="9e18b-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="9e18b-149">Enumerar delimitadores existentes</span><span class="sxs-lookup"><span data-stu-id="9e18b-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="9e18b-150">Para detectar los delimitadores almacenados previamente, llame a GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="9e18b-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="9e18b-151">Persistencia de hologramas para varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="9e18b-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="9e18b-152">Puede usar los <a href="/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede ubicar a continuación en varios dispositivos HoloLens, iOS y Android, incluso si dichos dispositivos no están presentes juntos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="9e18b-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="9e18b-153">Dado que los delimitadores en la nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="9e18b-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="9e18b-154">Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="9e18b-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="9e18b-155">Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="9e18b-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
