---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719818"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Una API adicional denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones. XRAnchorStore es una representación de los delimitadores guardados en un dispositivo. Los delimitadores se pueden conservar de **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en nuevo **ARAnchors** o eliminarse del almacenamiento.

> [!NOTE]
> Estos delimitadores se guardan y se cargan en el mismo dispositivo. El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.

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

Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRAnchorSubsystem, el subsistema de ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Para ver un ejemplo completo de los delimitadores de persistencia y despersistencia, consulte el script delimitadores-> delimitadores de ejemplo GameObject y AnchorsSample. CS en la [escena de ejemplo de complemento de realidad mixta OpenXR](../openxr-getting-started.md#hololens-2-samples):

![Captura de pantalla del panel de jerarquías abierto en el editor de Unity con el ejemplo de anclajes resaltado](../images/openxr-features-img-04.png)

![Captura de pantalla del panel de inspectores abierta en el editor de Unity con el script de ejemplo de delimitadores resaltado](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento de Unity 2019/2020 + Windows XR](#tab/winxr)

Una API denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones. XRAnchorStore es una representación de los delimitadores guardados en un dispositivo. Los delimitadores se pueden conservar de **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en nuevo **ARAnchors** o eliminarse del almacenamiento.

> [!NOTE]
> Estos delimitadores se guardan y se cargan en el mismo dispositivo. El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.

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

Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), el subsistema de ARReferencePointManager/ARAnchorManager:

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación para Unity 2019:

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

o para Unity 2020:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

**WorldAnchorStore** es la clave para crear experiencias holográficas en las que los hologramas permanecen en posiciones específicas del mundo real entre instancias de la aplicación. Después, los usuarios pueden anclar los hologramas individuales dondequiera que quieran y encontrarlos más adelante en el mismo punto en muchos usos de la aplicación.

**Espacio de nombres:** *UnityEngine. XR. WSA. Persistence*<br>
**Clase:** *WorldAnchorStore*

El WorldAnchorStore le permitirá conservar la ubicación de los WorldAnchor de las sesiones. Para conservar los hologramas en todas las sesiones, deberá realizar un seguimiento por separado de los GameObjects que usan un delimitador mundial determinado. A menudo tiene sentido crear una raíz GameObject con un delimitador mundial y tener los hologramas secundarios anclados por él con un desplazamiento de posición local.

Para cargar hologramas de sesiones anteriores:

1. Obtención de WorldAnchorStore
2. Cargar datos de la aplicación relacionados con el anclaje mundial, que le proporciona el identificador del anclaje mundial
3. Carga de un delimitador mundial desde su identificador

Para guardar los hologramas para las sesiones futuras:

1. Obtención de WorldAnchorStore
2. Guardar un delimitador mundial especificando un identificador
3. Guardar datos de la aplicación relacionados con el delimitador mundial junto con un identificador

### <a name="getting-the-worldanchorstore"></a>Obtención de WorldAnchorStore

Querrá mantener una referencia a WorldAnchorStore para que sepa cuándo está listo para realizar una operación. Dado que se trata de una llamada asincrónica, posiblemente en cuanto se inicia, desea llamar a:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

En este caso, StoreLoaded es el controlador para cuando se haya completado la carga de WorldAnchorStore:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Ahora tenemos una referencia a WorldAnchorStore, que usaremos para guardar y cargar delimitadores del mundo específicos.

### <a name="saving-a-worldanchor"></a>Guardar un WorldAnchor

Para ahorrar, simplemente necesitamos asignar un nombre a lo que estamos guardando y pasarlo en el WorldAnchor que obtuvimos antes cuando queremos ahorrar. Nota: Si intenta guardar dos delimitadores en la misma cadena, se producirá un error (Store. Save devolverá FALSE). Elimine el guardado anterior antes de guardar el nuevo:

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

### <a name="loading-a-worldanchor"></a>Carga de un WorldAnchor

Y para cargar:

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

Además, podemos usar Store. Elimine () para quitar un delimitador que se guardó y almacenó anteriormente. Borre () para quitar todos los datos guardados previamente.

### <a name="enumerating-existing-anchors"></a>Enumerar delimitadores existentes

Para detectar los delimitadores almacenados previamente, llame a GetAllIds.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistencia de hologramas para varios dispositivos

Puede usar los <a href="/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede ubicar a continuación en varios dispositivos HoloLens, iOS y Android, incluso si dichos dispositivos no están presentes juntos al mismo tiempo.  Dado que los delimitadores en la nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.

Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.

Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.
