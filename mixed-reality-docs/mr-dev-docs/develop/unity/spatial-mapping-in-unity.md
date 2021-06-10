---
title: Asignación espacial en Unity
description: Obtenga información sobre cómo usar y administrar la representación y la colisión con la geometría real que le rodea en las aplicaciones de realidad mixta de Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, asignación espacial, representador, colisionador, malla, examen, componente, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: fa571a13ce192b29b2a35033b55061f3ffb707da
ms.sourcegitcommit: ec80ef1e496bf0b17a161735535517e87ffdd364
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110351783"
---
# <a name="spatial-mapping-in-unity"></a>Asignación espacial en Unity

[La asignación](../../design/spatial-mapping.md) espacial permite recuperar mallas de triángulo que representan las superficies del mundo alrededor de un dispositivo HoloLens. Puede usar los datos de la superficie para la selección de ubicación, oclusión y análisis de sala para proporcionar a los proyectos de Unity una mayor cantidad de inmersiones.

Unity incluye compatibilidad completa con la asignación espacial, que se expone a los desarrolladores de las maneras siguientes:

1. Componentes de asignación espacial disponibles en MixedRealityToolkit, que proporcionan una ruta de acceso cómoda y rápida para empezar a trabajar con la asignación espacial.
2. API de asignación espacial de nivel inferior, que proporcionan control total y permiten una personalización más sofisticada específica de la aplicación

Para usar la asignación espacial en la aplicación, la funcionalidad spatialPerception debe establecerse en AppxManifest.

## <a name="device-support"></a>Compatibilidad con dispositivos

| Característica | [HoloLens (primera generación)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [Cascos envolventes](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| Asignación espacial | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>Establecimiento de la funcionalidad SpatialPerception

Para que una aplicación consuma datos de asignación espacial, se debe habilitar la funcionalidad SpatialPerception.

Habilitación de la funcionalidad SpatialPerception:

1. En el Editor de Unity, abra el **panel "Configuración** del reproductor" (Editar > project settings > Player)
2. Seleccione en la **pestaña "Tienda Windows".**
3. Expanda **"Configuración de publicación"** y compruebe la **funcionalidad "SpatialPerception"** en la **lista "Funcionalidades".**

> [!NOTE]
> Si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o establecer manualmente esta funcionalidad en [AppxManifest](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)en Visual Studio .

La asignación espacial también requiere maxVersionTested de al menos 10.0.10586.0:

1. En Visual Studio, haga clic con el botón derecho en **Package.appxmanifest** en la Explorador de soluciones y seleccione **Ver código.**
2. Busque la línea que especifica **TargetDeviceFamily** y cambie **MaxVersionTested="10.0.10240.0"** a **MaxVersionTested="10.0.10586.0"**
3. **Guarde** package.appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introducción a los componentes de asignación espacial integrados de Unity

Unity ofrece dos componentes para agregar fácilmente la asignación espacial a la aplicación: Representador de **asignación espacial** y **Colisionador de asignación espacial.**

### <a name="spatial-mapping-renderer"></a>Representador de asignación espacial

El representador de asignación espacial permite la visualización de la malla de asignación espacial.

![Representador de asignación espacial en Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Colisionador de asignación espacial

El colisionador de asignación espacial permite la interacción de contenido holográfico (o carácter), como la física, con la malla de asignación espacial.

![Colisionador de asignación espacial en Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Uso de los componentes de asignación espacial integrados

Puede agregar ambos componentes a la aplicación si quiere visualizar e interactuar con superficies físicas.

Para usar estos dos componentes en la aplicación de Unity:

1. Seleccione un GameObject en el centro del área en la que desea detectar mallas de superficie espacial.
2. En la ventana Inspector, **agregue el colisionador** de  >  **asignación espacial XR**  >  **de componente** o **el representador de asignación espacial**.

Puede encontrar más detalles sobre cómo usar estos componentes en el sitio <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">de documentación de Unity.</a>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Ir más allá de los componentes de asignación espacial integrados

Estos componentes hacen que sea fácil arrastrar y colocar para empezar a trabajar con la asignación espacial.  Si desea ir más allá, hay dos rutas de acceso principales que explorar:

* Para realizar su propio procesamiento de malla de nivel inferior, consulte la sección siguiente sobre la API de script de asignación espacial de bajo nivel.
* Para realizar análisis de malla de nivel superior, consulte la sección siguiente sobre la biblioteca SpatialUnderstanding en <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

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

Especifique la región de espacio para la que cada objeto SurfaceObserver proporcionará datos llamando a SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. Puede volver a definir la región del espacio en el futuro simplemente llamando a uno de estos métodos de nuevo.

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

### <a name="handling-surface-changes"></a>Control de cambios de superficie

Hay varios casos principales para controlar: agregados y actualizados, que pueden usar la misma ruta de acceso de código y quitarse.

* En los casos agregados y actualizados, agregamos u obtienemos el Objeto GameObject que representa esta malla desde el diccionario, creamos una estructura SurfaceData con los componentes necesarios y, a continuación, llamamos a RequestMeshDataAsync para rellenar el GameObject con los datos de malla y la posición en la escena.
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

### <a name="handling-data-ready"></a>Control de datos listo

El controlador OnDataReady recibe un objeto SurfaceData. Los objetos WorldAnchor, MeshFilter y (opcionalmente) MeshCollider que contiene reflejan el estado más reciente de la superficie espacial asociada. Opcionalmente, analice o [procese los](../../design/spatial-mapping.md#mesh-processing) datos de malla mediante el acceso al miembro Mesh del objeto MeshFilter. Represente la superficie espacial con la malla más reciente y úsela (opcionalmente) para colisiones físicas y difusión de rayos. Es importante confirmar que el contenido de SurfaceData no es NULL.

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
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>Análisis de malla de nivel superior: Spatial Understanding

> [!CAUTION]
> La comprensión espacial ha quedado en desuso en favor de [Scene Understanding.](../../design/scene-understanding.md)

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit es</a> una colección de código de utilidad para el desarrollo holográfico basado en las API holográficas de Unity.

### <a name="spatial-understanding"></a>Comprensión espacial

Al colocar hologramas en el mundo físico, a menudo es deseable ir más allá de los planos de malla y superficie de la asignación espacial. Cuando la selección de ubicación se realiza por procedimientos, es deseable un mayor nivel de comprensión del entorno. Esto normalmente requiere tomar decisiones sobre lo que es el suelo, el límite superior y las paredes. También tiene la capacidad de optimizar frente a un conjunto de restricciones de selección de ubicación para determinar las mejores ubicaciones físicas para los objetos holográficos.

Durante el desarrollo de Young Conker y Fragments, Asobo Studios se enfrentaba a este problema de frente mediante el desarrollo de un solucionador de sala. Cada uno de estos juegos tenía necesidades específicas del juego, pero compartían la tecnología de comprensión espacial básica. La biblioteca HoloToolkit.SpatialUnderstanding encapsula esta tecnología, lo que le permite encontrar rápidamente espacios vacíos en las paredes, colocar objetos en el límite, identificar colocados para que el carácter se sitúe y una gran cantidad de otras consultas de comprensión espacial.

Se incluye todo el código fuente, lo que le permite personalizarlo según sus necesidades y compartir sus mejoras con la comunidad. El código del solucionador de C++ se ha encapsulado en un archivo DLL de UWP y se ha expuesto a Unity con una colocación de prefab incluida en MixedRealityToolkit.

### <a name="understanding-modules"></a>Descripción de los módulos

Hay tres interfaces principales expuestas por el módulo: topología para consultas espaciales y de superficie sencillas, forma para la detección de objetos y solucionador de colocación de objetos para la colocación basada en restricciones de conjuntos de objetos. Cada uno de ellos se describe a continuación. Además de las tres interfaces de módulo principal, se puede usar una interfaz de conversión de rayos para recuperar los tipos de superficie etiquetados y se puede copiar una malla de espacio de juego estanca personalizada.

### <a name="ray-casting"></a>Conversión de rayos

Una vez completado el examen de la sala, las etiquetas se generan internamente para superficies como el suelo, el techo y las paredes. La función toma un rayo y devuelve si el rayo colisiona con una superficie conocida y, si es así, información sobre esa superficie en `PlayspaceRaycast` forma de `RaycastResult` .

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

Internamente, la transmisión por rayos se calcula en la representación de vóxel en cubo de 8 cm calculada del espacio de reproducción. Cada vóxel contiene un conjunto de elementos de superficie con datos de topología procesados (también conocido como tablas). Se comparan las tablas contenidas en la celda de vóxel intersección y la mejor coincidencia que se usa para buscar la información de la topología. Estos datos de topología contienen el etiquetado devuelto en forma de enumeración "SurfaceTypes", así como el área de superficie de la superficie intersectada.

En el ejemplo de Unity, el cursor convierte un rayo en cada fotograma. En primer lugar, contra los colisiondores de Unity. En segundo lugar, frente a la representación mundial del módulo de comprensión. Y, por último, de nuevo elementos de la interfaz de usuario. En esta aplicación, la interfaz de usuario obtiene prioridad, después el resultado de la comprensión y, por último, los colisiondores de Unity. SurfaceType se notifica como texto junto al cursor.

![El tipo de superficie se etiqueta junto al cursor](images/su-raycastresults-300px.jpg)<br>
*El tipo de superficie se etiqueta junto al cursor*

### <a name="topology-queries"></a>Consultas de topología

Dentro del archivo DLL, el administrador de topologías controla el etiquetado del entorno. Como se mencionó anteriormente, gran parte de los datos se almacenan en tablas, contenidas dentro de un volumen de vóxel. Además, la estructura "PlaySpaceInfos" se usa para almacenar información sobre el espacio de juego, incluida la alineación del mundo (más detalles sobre esto a continuación), el suelo y la altura del límite superior. La heurística se usa para determinar el suelo, el techo y las paredes. Por ejemplo, la superficie horizontal más grande y más baja con un área de superficie superior a 1 m2 se considera el suelo.

> [!NOTE]
> La ruta de acceso de la cámara durante el proceso de examen también se usa en este proceso.

Un subconjunto de las consultas expuestas por el administrador de topologías se expone a través de la dll. Las consultas de topología expuestas son las siguientes.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Cada una de las consultas tiene un conjunto de parámetros, específicos del tipo de consulta. En el ejemplo siguiente, el usuario especifica el alto mínimo & ancho del volumen deseado, la altura de colocación mínima por encima del suelo y la cantidad mínima de autorización delante del volumen. Todas las medidas están en metros.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada una de estas consultas toma una matriz preasignada de estructuras "TopologyResult". El parámetro "locationCount" especifica la longitud de la matriz pasada. El valor devuelto informa del número de ubicaciones devueltas. Este número nunca es mayor que el parámetro "locationCount" pasado.

"TopologyResult" contiene la posición central del volumen devuelto, la dirección orientada (es decir, normal) y las dimensiones del espacio encontrado.

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> En el ejemplo de Unity, cada una de estas consultas está vinculada a un botón en el panel de interfaz de usuario virtual. El ejemplo codifica los parámetros de cada una de estas consultas a valores razonables. Vea SpaceVisualizer.cs en el código de ejemplo para obtener más ejemplos.

### <a name="shape-queries"></a>Dar forma a las consultas

En el archivo dll, el analizador de formas ("ShapeAnalyzer_W") usa el analizador de topología para coincidir con las formas personalizadas definidas por el usuario. El ejemplo de Unity define un conjunto de formas y expone los resultados a través del menú de consulta en la aplicación, dentro de la pestaña forma. La intención es que el usuario pueda definir sus propias consultas de forma de objeto y usarlas, según sea necesario para su aplicación.

El análisis de formas solo funciona en superficies horizontales. Un diván, por ejemplo, se define mediante la superficie del puesto plano y la parte superior plana del respaldo del diván. La consulta de formas busca dos superficies de un tamaño, un alto y un intervalo de aspecto específicos, con las dos superficies alineadas y conectadas. Con la terminología de las API, el puesto del diván y la parte posterior son componentes de forma y los requisitos de alineación son restricciones de componentes de forma.

A continuación se muestra una consulta de ejemplo definida en el ejemplo de Unity (ShapeDefinition.cs) para objetos "sittable".

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

Cada consulta de forma se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componentes y un conjunto de restricciones de forma que enumeran las dependencias entre los componentes. Este ejemplo incluye tres restricciones en una única definición de componente y ninguna restricción de forma entre componentes (ya que solo hay un componente).

Por el contrario, la forma del diván tiene dos componentes de forma y cuatro restricciones de forma. Los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Las funciones contenedoras se proporcionan en el módulo de Unity para facilitar la creación de definiciones de formas personalizadas. La lista completa de restricciones de componentes y formas se puede encontrar en "SpatialUnderstandingDll.cs" dentro de las estructuras "ShapeComponentConstraint" y "ShapeConstraint".

![La forma del rectángulo se encuentra en esta superficie](images/su-shapequery-300px.jpg)<br>
*La forma del rectángulo se encuentra en esta superficie*

### <a name="object-placement-solver"></a>Solucionador de colocación de objetos

El solucionador de colocación de objetos se puede usar para identificar ubicaciones ideales en la sala física para colocar los objetos. El solucionador encontrará la mejor ubicación de ajuste dadas las restricciones y las reglas de objeto. Además, las consultas de objetos se conservan hasta que se quita el objeto con llamadas "Solver_RemoveObject" o "Solver_RemoveAllObjects", lo que permite la colocación restringida de varios objetos. Las consultas de selección de ubicación de objetos constan de tres partes: tipo de selección de ubicación con parámetros, una lista de reglas y una lista de restricciones. Para ejecutar una consulta, use la API siguiente.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

Esta función toma un nombre de objeto, una definición de selección de ubicación y una lista de reglas y restricciones. Los contenedores de C# proporcionan funciones auxiliares de construcción para facilitar la construcción de reglas y restricciones. La definición de selección de ubicación contiene el tipo de consulta, es decir, uno de los siguientes.

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

Cada uno de los tipos de selección de ubicación tiene un conjunto de parámetros únicos para el tipo. La estructura "ObjectPlacementDefinition" contiene un conjunto de funciones auxiliares estáticas para crear estas definiciones. Por ejemplo, para buscar un lugar donde colocar un objeto en el suelo, puede usar la siguiente función. public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Además del tipo placement, puede proporcionar un conjunto de reglas y restricciones. No se pueden infringir las reglas. Las posibles ubicaciones de selección de ubicación que cumplen el tipo y las reglas se optimizan con el conjunto de restricciones para seleccionar la ubicación de ubicación óptima. Las funciones de creación estática proporcionadas pueden crear cada una de las reglas y restricciones. A continuación se proporciona una regla de ejemplo y una función de construcción de restricciones.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La siguiente consulta de selección de ubicación de objetos busca un lugar donde colocar un cubo de medio metro en el borde de una superficie, lejos de otros objetos situados anteriormente y cerca del centro de la sala.

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

Si se realiza correctamente, se devuelve una estructura "ObjectPlacementResult" que contiene la posición de colocación, las dimensiones y la orientación. Además, la colocación se agrega a la lista interna del archivo DLL de objetos colocados. Las consultas de selección de ubicación posteriores tendrán en cuenta este objeto. El archivo "LevelSolver.cs" del ejemplo de Unity contiene más consultas de ejemplo.

![Resultados de la selección de ubicación de objetos](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: Cuadros azules en los que el resultado de las consultas de tres posiciones en el suelo se encuentra fuera de las reglas de posición de la cámara*

Al resolver la ubicación de colocación de varios objetos necesarios para un escenario de nivel o aplicación, primero debe resolver objetos imprescindibles y grandes para maximizar la probabilidad de que se pueda encontrar un espacio. El orden de selección de ubicación es importante. Si no se pueden encontrar colocaciones de objetos, pruebe con configuraciones menos restringidas. Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de sala.

### <a name="room-scanning-process"></a>Proceso de examen de sala

Aunque la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genérica como para satisfacer las necesidades de toda la gama de espacios con problemas, el módulo de comprensión espacial se creó para admitir las necesidades de dos juegos específicos. Su solución se estructura en torno a un proceso específico y un conjunto de suposiciones, que se resumen a continuación.

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

"dibujo" del espacio de juego controlado por el usuario: durante la fase de examen, el usuario se mueve y busca alrededor del ritmo de reproducción, pintando eficazmente las áreas, que deben incluirse. La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase. Configuración del hogar u oficina interior: las funciones de consulta están diseñadas en torno a superficies planas y paredes en ángulos derecho. Se trata de una limitación temporal. Sin embargo, durante la fase de análisis, se completa un análisis del eje principal para optimizar la teselación de malla a lo largo de los ejes principal y secundario. El archivo SpatialUnderstanding.cs incluido administra el proceso de fase de examen. Llama a las siguientes funciones.

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

El flujo de examen, controlado por el comportamiento "SpatialUnderstanding", llama a InitScan y, a continuación, UpdateScan a cada fotograma. Cuando la consulta de estadísticas informa de una cobertura razonable, el usuario puede usar airtap para llamar a RequestFinish para indicar el final de la fase de examen. Se sigue llamando a UpdateScan hasta que su valor devuelto indica que el archivo DLL ha completado el procesamiento.

### <a name="understanding-mesh"></a>Descripción de Mesh

La dll de comprensión almacena internamente el espacio de reproducción como una cuadrícula de cubos de vóxel de 8 cm de tamaño. Durante la parte inicial del análisis, se completa un análisis de componentes principales para determinar los ejes de la sala. Internamente, almacena su espacio de vóxel alineado con estos ejes. Una malla se genera aproximadamente cada segundo mediante la extracción del isosurface del volumen de vóxel.

![Malla generada a partir del volumen de vóxel](images/su-custommesh.jpg)<br>
*Malla generada a partir del volumen de vóxel*

## <a name="troubleshooting"></a>Solución de problemas

* Asegúrese de que ha establecido [la funcionalidad SpatialPerception.](#setting-the-spatialperception-capability)
* Cuando se pierde el seguimiento, el siguiente evento OnSurfaceChanged quitará todas las mallas.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Asignación espacial en Mixed Reality Toolkit

Para más información sobre el uso de la asignación espacial con Mixed Reality Toolkit, consulte la sección de reconocimiento [espacial](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) de los documentos de MRTK.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, está en medio de la exploración de los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Texto](text-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también

* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* [Sistemas de coordenadas de Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
