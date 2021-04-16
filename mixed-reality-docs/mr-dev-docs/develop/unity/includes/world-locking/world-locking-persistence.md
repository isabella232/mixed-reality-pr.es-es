---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528800"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="5944d-101">World Locking Tools (recomendado)</span><span class="sxs-lookup"><span data-stu-id="5944d-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="5944d-102">De forma predeterminada, World Locking Tools restaurará el sistema de coordenadas de Unity en relación con el mundo físico entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="5944d-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="5944d-103">Esto significa que para que un holograma aparezca en el mismo lugar en el mundo físico después de salir y volver a ejecutar la aplicación, el holograma solo necesita volver a tener la misma posición.</span><span class="sxs-lookup"><span data-stu-id="5944d-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Componente de contexto de bloqueo del mundo en el inspector de Unity](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="5944d-105">Si la aplicación necesita un control  más **preciso,** se pueden deshabilitar el guardado automático y la carga automática en el inspector y administrar la persistencia desde un script como se describe en la sección de persistencia de la [documentación](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span><span class="sxs-lookup"><span data-stu-id="5944d-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="5944d-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="5944d-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="5944d-107">Una API adicional denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="5944d-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="5944d-108">XRAnchorStore es una representación de los anclajes guardados en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5944d-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="5944d-109">Los anclajes se pueden conservar desde **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en **el nuevo ARAnchors** o eliminarse del almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="5944d-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="5944d-110">Estos anclajes se guardarán y cargarán en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5944d-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="5944d-111">El almacenamiento de delimitadores entre dispositivos se admite a través de Azure Spatial Anchors en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="5944d-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="5944d-112">Espacios de nombres</span><span class="sxs-lookup"><span data-stu-id="5944d-112">Namespaces</span></span>

<span data-ttu-id="5944d-113">Para **Unity 2020 y OpenXR:**</span><span class="sxs-lookup"><span data-stu-id="5944d-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="5944d-114">o **Unity 2019/2020 + Complemento XR de Windows:**</span><span class="sxs-lookup"><span data-stu-id="5944d-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="5944d-115">Métodos públicos</span><span class="sxs-lookup"><span data-stu-id="5944d-115">Public methods</span></span>

```cs 
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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="5944d-116">Obtención de una referencia de almacén de anclajes</span><span class="sxs-lookup"><span data-stu-id="5944d-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="5944d-117">Para cargar XRAnchorStore con **Unity 2020 y OpenXR,** use el método de extensión en XRAnchorSubsystem, el subsistema de arAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="5944d-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="5944d-118">Para cargar XRAnchorStore con **Unity 2019/2020** y el complemento XR de Windows, use el método de extensión en XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), el subsistema de arReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="5944d-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="5944d-119">Carga de un almacén de anclajes</span><span class="sxs-lookup"><span data-stu-id="5944d-119">Loading an anchor store</span></span>

<span data-ttu-id="5944d-120">Para cargar un almacén de anclajes **en Unity 2020 y OpenXR,** acceda a él desde el subsistema de ARAnchorManager como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="5944d-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="5944d-121">o con **Unity 2019/2020 y el complemento XR de Windows:**</span><span class="sxs-lookup"><span data-stu-id="5944d-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="5944d-122">Para ver un ejemplo completo de anclajes persistentes o no persistentes, consulte los scripts GameObject y AnchorsSample.cs del ejemplo Anchors -> Anchors En la escena de ejemplo del complemento [OpenXR](../../openxr-getting-started.md#hololens-2-samples)de Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="5944d-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de pantalla del panel de jerarquía abierto en el Editor de Unity con el ejemplo de delimitadores resaltado](../../images/openxr-features-img-04.png)

![Captura de pantalla del panel del inspector abierto en el Editor de Unity con el script de ejemplo de delimitadores resaltado](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="5944d-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="5944d-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="5944d-126">**WorldAnchorStore** es la clave para crear experiencias holográficas en las que los hologramas permanecen en posiciones específicas del mundo real en instancias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5944d-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="5944d-127">A continuación, los usuarios pueden anclar hologramas individuales donde quieran y encontrarlos más adelante en el mismo lugar a través de muchos usos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5944d-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="5944d-128">**Espacio de nombres:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="5944d-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="5944d-129">**Clase:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="5944d-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="5944d-130">WorldAnchorStore le permitirá conservar la ubicación de WorldAnchor entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="5944d-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="5944d-131">Para conservar los hologramas en las sesiones, deberá realizar un seguimiento por separado de los Objetos GameObject que usan un delimitador de mundo determinado.</span><span class="sxs-lookup"><span data-stu-id="5944d-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="5944d-132">A menudo tiene sentido crear una raíz de GameObject con un delimitador de mundo y tener hologramas secundarios delimitados por él con un desplazamiento de posición local.</span><span class="sxs-lookup"><span data-stu-id="5944d-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="5944d-133">Para cargar hologramas de sesiones anteriores:</span><span class="sxs-lookup"><span data-stu-id="5944d-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="5944d-134">Obtener WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5944d-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="5944d-135">Carga de datos de la aplicación relacionados con el anclaje mundial, que le proporciona el identificador del anclaje mundial.</span><span class="sxs-lookup"><span data-stu-id="5944d-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="5944d-136">Carga de un delimitador de mundo desde su identificador</span><span class="sxs-lookup"><span data-stu-id="5944d-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="5944d-137">Para guardar hologramas para sesiones futuras:</span><span class="sxs-lookup"><span data-stu-id="5944d-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="5944d-138">Obtener WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5944d-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="5944d-139">Guardar un delimitador de mundo especificando un identificador</span><span class="sxs-lookup"><span data-stu-id="5944d-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="5944d-140">Guardar los datos de la aplicación relacionados con el delimitador del mundo junto con un identificador</span><span class="sxs-lookup"><span data-stu-id="5944d-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="5944d-141">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5944d-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="5944d-142">Querrá mantener una referencia a WorldAnchorStore para saber cuándo está listo para realizar una operación.</span><span class="sxs-lookup"><span data-stu-id="5944d-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="5944d-143">Puesto que se trata de una llamada asincrónica, posiblemente en cuanto se inicie, querrá llamar a:</span><span class="sxs-lookup"><span data-stu-id="5944d-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="5944d-144">StoreLoaded en este caso es nuestro controlador cuando WorldAnchorStore ha completado la carga:</span><span class="sxs-lookup"><span data-stu-id="5944d-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="5944d-145">Ahora tenemos una referencia a WorldAnchorStore, que usaremos para guardar y cargar anclajes de mundo específicos.</span><span class="sxs-lookup"><span data-stu-id="5944d-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="5944d-146">Guardar un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="5944d-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="5944d-147">Para guardarlo, basta con que asignemos un nombre a lo que guardamos y pasarlo al WorldAnchor que hemos conseguido antes cuando queremos guardar.</span><span class="sxs-lookup"><span data-stu-id="5944d-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="5944d-148">Nota: Se producirá un error al intentar guardar dos delimitadores en la misma cadena (almacenar. Guardar devolverá false).</span><span class="sxs-lookup"><span data-stu-id="5944d-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="5944d-149">Elimine el guardado anterior antes de guardar el nuevo:</span><span class="sxs-lookup"><span data-stu-id="5944d-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="5944d-150">Carga de un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="5944d-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="5944d-151">Y para cargar:</span><span class="sxs-lookup"><span data-stu-id="5944d-151">And to load:</span></span>

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

<span data-ttu-id="5944d-152">Además, podemos usar store. Delete() para quitar un delimitador que hemos guardado y almacenado previamente. Clear() para quitar todos los datos guardados previamente.</span><span class="sxs-lookup"><span data-stu-id="5944d-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="5944d-153">Enumeración de delimitadores existentes</span><span class="sxs-lookup"><span data-stu-id="5944d-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="5944d-154">Para detectar delimitadores almacenados previamente, llame a GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="5944d-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="5944d-155">Conservación de hologramas para varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="5944d-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="5944d-156">Puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para crear un anclaje de nube duradero a partir de un WorldAnchor local, que la aplicación puede encontrar en varios dispositivos HoloLens, iOS y Android, incluso si esos dispositivos no están presentes juntos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="5944d-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="5944d-157">Dado que los delimitadores de nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="5944d-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="5944d-158">Para empezar a crear experiencias compartidas en Unity, pruebe los inicios rápidos de 5 minutos <a href="/azure/spatial-anchors/unity-overview" target="_blank">de Azure Spatial Anchors Unity.</a></span><span class="sxs-lookup"><span data-stu-id="5944d-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="5944d-159">Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">y buscar anclajes en Unity.</a></span><span class="sxs-lookup"><span data-stu-id="5944d-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
