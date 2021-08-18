---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905717"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>Sistema de reconocimiento espacial

En MRTK, consulte la [guía](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) de introducción al reconocimiento espacial para obtener información sobre cómo configurar varios observadores de malla espacial.

Para obtener información sobre los observadores en el dispositivo, consulte la guía [Configuración de observadores de](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) malla para dispositivos.

Para obtener información sobre la descripción de la escena de los observadores, consulte la Guía del observador [de descripción de la](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) escena.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

ARFoundation de Unity proporciona un componente ARMeshManager para la visualización integrada de mallas espaciales. Consulte [la documentación de Unity para](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) obtener más información sobre el uso.

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

Si prefiere trabajar directamente con [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) de Unity, consulte la documentación de [Unity](https://docs.unity3d.com/Manual/xrsdk-meshing.html) para obtener más información sobre el uso.

## <a name="windows-xr-plugin"></a>Windows Complemento XR

Windows El complemento XR proporciona algunos métodos de extensión adicionales para configurar XRMeshSubsystem, como establecer una esfera de límite o acceder a la representación de malla de plataforma subyacente. Todas estas otras extensiones se pueden encontrar [en la documentación de Unity.](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html)

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introducción a los componentes de asignación espacial integrados de Unity

Unity ofrece dos componentes para agregar fácilmente la asignación espacial a la aplicación, **representador** de asignación espacial y **colisionador de asignación espacial.**

### <a name="spatial-mapping-renderer"></a>Representador de asignación espacial

El representador de asignación espacial permite la visualización de la malla de asignación espacial.

![Representador de asignación espacial en Unity](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Colisionador de asignación espacial

El colisionador de asignación espacial permite la interacción de contenido holográfico (o carácter), como la física, con la malla de asignación espacial.

![Colisionador de asignación espacial en Unity](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Uso de los componentes de asignación espacial integrados

Puede agregar ambos componentes a la aplicación si quiere visualizar e interactuar con superficies físicas.

Para usar estos dos componentes en la aplicación de Unity:

1. Seleccione un GameObject en el centro del área en la que desea detectar mallas de superficie espacial.
2. En la ventana Inspector, **agregue el colisionador** de  >  **asignación espacial XR**  >  **de componente** o   el **representador de asignación espacial**.

Puede encontrar más detalles sobre cómo usar estos componentes en el sitio <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">de documentación de Unity.</a>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Ir más allá de los componentes de asignación espacial integrados

Estos componentes hacen que sea fácil arrastrar y colocar para empezar a trabajar con la asignación espacial. Si desea ir más allá, hay dos rutas de acceso principales que explorar:

* Para realizar su propio procesamiento de malla de nivel inferior, consulte la sección siguiente sobre la API de script de asignación espacial de bajo nivel.
* Para realizar análisis de malla de nivel superior, consulte la sección siguiente sobre la biblioteca SpatialUnderstanding en [MixedRealityToolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding).

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Uso de la API de asignación espacial de Unity de bajo nivel

Si necesita más control que los componentes Representador de asignación espacial y Colisionador de asignación espacial, use las API de asignación espacial de bajo nivel.

**Espacio de nombres:** *UnityEngine.XR.WSA*<br>
**Tipos:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*

Hemos descrito el flujo sugerido para una aplicación que usa las API de asignación espacial en las secciones siguientes.

### <a name="set-up-the-surfaceobservers"></a>Configuración de SurfaceObserver(s)

Cree una instancia de un objeto SurfaceObserver para cada región de espacio definida por la aplicación para la que necesite datos de asignación espacial.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Especifique la región de espacio para la que cada objeto SurfaceObserver proporciona datos llamando a SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. Puede volver a definir la región del espacio en el futuro llamando de nuevo a uno de estos métodos.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Al llamar a SurfaceObserver.Update(), debe proporcionar un controlador para cada superficie espacial de la región de espacio de SurfaceObserver para la que el sistema de asignación espacial tiene información nueva. El controlador recibe, para una superficie espacial:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Control de cambios en la superficie

Hay varios casos principales que se deben controlar: agregados y actualizados, que pueden usar la misma ruta de acceso de código y quitados.

* En los casos agregados y actualizados, agregamos u obtienemos el Objeto GameObject que representa esta malla del diccionario. Creamos una estructura SurfaceData con los componentes necesarios y, a continuación, llamamos a RequestMeshDataAsync para rellenar el Elemento GameObject con los datos de malla y, a continuación, lo colocamos en la escena.
* En el caso quitado, se quita el Objeto GameObject que representa esta malla del diccionario y se destruye.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a>Control de datos listos

El controlador OnDataReady recibe un objeto SurfaceData. Los objetos WorldAnchor, MeshFilter y (opcionalmente) MeshCollider que contiene reflejan el estado más reciente de la superficie espacial asociada. Opcionalmente, analice o [procese los datos](../../../design/spatial-mapping.md#mesh-processing) de malla mediante el acceso al miembro Mesh del objeto MeshFilter. Represente la superficie espacial con la malla más reciente y úsela (opcionalmente) para colisiones físicas y difusión de rayos. Es importante confirmar que el contenido de SurfaceData no es NULL.

### <a name="start-processing-on-updates"></a>Iniciar el procesamiento en las actualizaciones

Se debe llamar a SurfaceObserver.Update() en un retraso, no a todos los fotogramas.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
