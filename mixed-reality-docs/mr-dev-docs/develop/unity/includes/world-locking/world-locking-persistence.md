---
ms.openlocfilehash: 96da41f28533c227fb106d8842907747f34098ec
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2021
ms.locfileid: "110349954"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools (recomendado)](#tab/wlt)

De forma predeterminada, World Locking Tools restaurará el sistema de coordenadas de Unity con respecto al mundo físico entre sesiones. Esto significa que para que un holograma aparezca en el mismo lugar del mundo físico después de salir y volver a ejecutar la aplicación, el holograma solo debe tener la misma posición de nuevo.

![Componente de contexto de bloqueo de mundo en el inspector de Unity](../../images/world-locking-tools-img-02.png)

Si la aplicación necesita un control  más **preciso,** se pueden deshabilitar el guardado automático y la carga automática en el inspector y administrar la persistencia desde un script, como se describe en la sección de persistencia de la [documentación](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Una API adicional denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones. XRAnchorStore es una representación de los delimitadores guardados en un dispositivo. Los delimitadores se pueden conservar desde **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en **los nuevos ARAnchors** o eliminarse del almacenamiento.

> [!NOTE]
> Estos anclajes se guardarán y cargarán en el mismo dispositivo. El almacenamiento de anclajes entre dispositivos se admite a través de Azure Spatial Anchors en una versión futura.

### <a name="namespaces"></a>Espacios de nombres

Para **Unity 2020 y OpenXR:** 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

o **Unity 2019/2020 + Complemento XR de Windows:** 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>Métodos públicos

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

### <a name="getting-an-anchor-store-reference"></a>Obtención de una referencia de almacén de anclajes 

Para cargar XRAnchorStore con **Unity 2020 y OpenXR,** use el método de extensión en XRAnchorSubsystem, el subsistema de arAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Para cargar XRAnchorStore con **Unity 2019/2020** y el complemento XR de Windows, use el método de extensión en XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), el subsistema de arReferencePointManager/ARAnchorManager:

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>Carga de un almacén de anclajes

Para cargar un almacén de anclajes **en Unity 2020 y OpenXR,** acceda a él desde el subsistema de ARAnchorManager de la siguiente manera:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

o con **Unity 2019/2020 y el complemento XR de Windows:**

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

Para ver un ejemplo completo de anclajes persistentes o no persistentes, consulte los scripts GameObject y AnchorsSample.cs del ejemplo Anchors -> Anchors En la escena de ejemplo del complemento [OpenXR](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2)de Mixed Reality :

![Captura de pantalla del panel de jerarquía abierto en el Editor de Unity con el ejemplo de delimitadores resaltado](../../images/openxr-features-img-04.png)

![Captura de pantalla del panel del inspector abierto en el Editor de Unity con el script de ejemplo de delimitadores resaltado](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

**WorldAnchorStore** es la clave para crear experiencias holográficas en las que los hologramas permanecen en posiciones específicas del mundo real en instancias de la aplicación. A continuación, los usuarios pueden anclar hologramas individuales donde quieran y encontrarlos más adelante en el mismo lugar a través de muchos usos de la aplicación.

**Espacio de nombres:** *UnityEngine.XR.WSA.Persistence*<br>
**Clase:** *WorldAnchorStore*

WorldAnchorStore le permitirá conservar la ubicación de WorldAnchor entre sesiones. Para conservar los hologramas en las sesiones, deberá realizar un seguimiento por separado de los Objetos GameObject que usan un delimitador de mundo determinado. A menudo tiene sentido crear una raíz de GameObject con un delimitador de mundo y tener hologramas secundarios delimitados por él con un desplazamiento de posición local.

Para cargar hologramas de sesiones anteriores:

1. Obtener WorldAnchorStore
2. Carga de datos de la aplicación relacionados con el anclaje mundial, que le proporciona el identificador del delimitador mundial.
3. Carga de un delimitador de mundo desde su identificador

Para guardar hologramas para sesiones futuras:

1. Obtener WorldAnchorStore
2. Guardar un delimitador de mundo especificando un identificador
3. Guardar los datos de la aplicación relacionados con el delimitador del mundo junto con un identificador

### <a name="getting-the-worldanchorstore"></a>Obtención de WorldAnchorStore

Querrá mantener una referencia a WorldAnchorStore para saber cuándo está listo para realizar una operación. Puesto que se trata de una llamada asincrónica, posiblemente en cuanto se inicie, querrá llamar a:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded en este caso es nuestro controlador cuando WorldAnchorStore ha completado la carga:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Ahora tenemos una referencia a WorldAnchorStore, que usaremos para guardar y cargar anclajes de mundo específicos.

### <a name="saving-a-worldanchor"></a>Guardar un WorldAnchor

Para guardarlo, basta con que asignemos un nombre a lo que guardamos y pasarlo al WorldAnchor que tenemos antes cuando queremos guardar. Nota: Se producirá un error al intentar guardar dos delimitadores en la misma cadena (almacenar. Guardar devolverá false). Elimine el guardado anterior antes de guardar el nuevo:

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

Además, podemos usar store. Delete() para quitar un delimitador que anteriormente guardamos y almacenamos. Clear() para quitar todos los datos guardados anteriormente.

### <a name="enumerating-existing-anchors"></a>Enumerar delimitadores existentes

Para detectar delimitadores almacenados previamente, llame a GetAllIds.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Conservación de hologramas para varios dispositivos

Puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors para</a> crear un anclaje de nube duradero a partir de un WorldAnchor local, que la aplicación puede localizar a continuación en varios dispositivos HoloLens, iOS y Android, incluso si esos dispositivos no están presentes juntos al mismo tiempo.  Dado que los delimitadores de nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.

Para empezar a crear experiencias compartidas en Unity, pruebe los inicios rápidos de 5 minutos <a href="/azure/spatial-anchors/unity-overview" target="_blank">de Azure Spatial Anchors Unity.</a>

Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear y buscar <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">delimitadores en Unity.</a>
