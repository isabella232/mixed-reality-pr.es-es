---
title: 'Caso práctico: expansión de las capacidades de asignación espacial de HoloLens'
description: Al crear nuestras primeras aplicaciones para Microsoft HoloLens, nos hemos interesado en ver hasta qué punto podríamos insertar los límites de la asignación espacial en el dispositivo.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, asignación espacial
ms.openlocfilehash: f0438990c39570f9188e2e150a8cbe7907d72f7e2be260c72e41646565b8d89e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210451"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Caso práctico: expansión de las capacidades de asignación espacial de HoloLens

Al crear nuestras primeras aplicaciones para Microsoft HoloLens, nos hemos interesado en ver hasta qué punto podríamos insertar los límites de la asignación espacial en el dispositivo. Jeff Evertt, ingeniero de software de Microsoft Studios, explica cómo se desarrolló una nueva tecnología a partir de la necesidad de tener más control sobre cómo se colocan los hologramas en el entorno real de un usuario.

> [!NOTE]
> HoloLens 2 implementa una nueva instancia de [Scene Understanding Runtime,](../design/scene-understanding.md)que proporciona a los desarrolladores de Mixed Reality una representación de entorno estructurada y de alto nivel diseñada para que el desarrollo para aplicaciones con control del entorno sea intuitivo. 

## <a name="watch-the-video"></a>Visualización del vídeo

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Más allá de la asignación espacial

Mientras trabajamos en [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) y [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dos de los primeros juegos para HoloLens, descubrimos que, cuando se realizaba la colocación de procedimientos de hologramas en el mundo físico, se necesitaba un mayor nivel de comprensión sobre el entorno del usuario. Cada juego tenía sus propias necesidades de colocación específicas: en Fragmentos, por ejemplo, queríamos poder distinguir entre diferentes superficies,como el suelo o una tabla, para colocar pistas en ubicaciones pertinentes. También queríamos poder identificar las superficies en las que podrían estar sentados los caracteres holográficos de tamaño real, como un diván o una mesa. En Young Conker, queríamos que Conker y sus adversarios puedan usar superficies elevados en la sala de un jugador como plataformas.

[Asobo Studios,](https://www.asobostudio.com/index.html)nuestro asociado de desarrollo para estos juegos, se enfrentaba a este problema de frente y creaba una tecnología que amplía las capacidades de asignación espacial de HoloLens. Con esto, podríamos analizar la habitación de un jugador e identificar superficies como paredes, tablas, cocinas y plantas. También nos ha dado la capacidad de optimizar frente a un conjunto de restricciones para determinar la mejor ubicación para los objetos holográficos.

## <a name="the-spatial-understanding-code"></a>Código de comprensión espacial

Hemos tomado el código original de Asobo y hemos creado una biblioteca que encapsula esta tecnología. Microsoft y Asobo ahora han abierto este código y lo han puesto a disposición en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para que lo use en sus propios proyectos. Se incluye todo el código fuente, lo que le permite personalizarlo según sus necesidades y compartir sus mejoras con la comunidad. El código del solucionador de C++ se ha encapsulado en un archivo DLL de UWP y se ha expuesto a Unity con un prefab desplegable contenido en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

Hay muchas consultas útiles incluidas en el ejemplo de Unity que le permitirán encontrar espacios vacíos en las paredes, colocar objetos en el límite superior o en espacios grandes en el suelo, identificar lugares para que los caracteres se encuentren y una gran cantidad de otras consultas de comprensión espacial.

Aunque la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genérica como para satisfacer las necesidades de toda la gama de espacios de problemas, el módulo de comprensión espacial se creó para admitir las necesidades de dos juegos específicos. Por lo tanto, su solución se estructura en torno a un proceso específico y un conjunto de suposiciones:
* **Espacio de reproducción de tamaño fijo:** el usuario especifica el tamaño máximo del espacio de reproducción en la llamada init.
* **Proceso de un solo examen:** el proceso requiere una fase de análisis discreta en la que el usuario se desista, definiendo el espacio de juego. Las funciones de consulta no funcionarán hasta que se haya finalizado el examen.
* Espacio de juego controlado por el usuario **"pintar":** durante la fase de examen, el usuario se mueve y busca alrededor del espacio de juego, pintando de forma eficaz las áreas que se deben incluir. La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.
* **Configuración del hogar u oficina** interior: las funciones de consulta están diseñadas en torno a superficies planas y paredes en ángulos derecho. Se trata de una limitación temporal. Sin embargo, durante la fase de análisis, se completa un análisis del eje principal para optimizar la teselación de malla a lo largo de los ejes principal y secundario.

### <a name="room-scanning-process"></a>Proceso de examen de sala

Al cargar el módulo de comprensión espacial, lo primero que hará es examinar el espacio, de modo que todas las superficies utilizables,como el suelo, el límite superior y las paredes, se identifiquen y se etiqueten. Durante el proceso de examen, puede mirar alrededor de la sala y "pintar" las áreas que se deben incluir en el examen.

La malla que se ve durante esta fase es un elemento importante de los comentarios visuales que permite a los usuarios saber qué partes de la sala se están analizando. El archivo DLL del módulo de comprensión espacial almacena internamente el espacio de juego como una cuadrícula de cubos de vóxel de 8 cm de tamaño. Durante la parte inicial del análisis, se completa un análisis de componentes principales para determinar los ejes de la sala. Internamente, almacena su espacio de vóxel alineado con estos ejes. Una malla se genera aproximadamente cada segundo mediante la extracción del isosurface del volumen de vóxel.

![Malla de asignación espacial en blanco y comprensión de la malla de espacio de juego en verde](images/spatial-mapping-500px.png)

Malla de asignación espacial en blanco y comprensión de la malla de espacio de juego en verde



El archivo SpatialUnderstanding.cs incluido administra el proceso de fase de examen. Llama a las siguientes funciones:
* **SpatialUnderstanding_Init:** se llama una vez al principio.
* **GeneratePlayspace_InitScan:** indica que debe comenzar la fase de examen.
* **GeneratePlayspace_UpdateScan_DynamicScan:** se llamó a cada fotograma para actualizar el proceso de examen. La posición y la orientación de la cámara se pasan y se usan para el proceso de dibujo del espacio de juego, descrito anteriormente.
* **GeneratePlayspace_RequestFinish:** se llama para finalizar el espacio de reproducción. Esto usará las áreas "dibujadas" durante la fase de examen para definir y bloquear el espacio de reproducción. La aplicación puede consultar estadísticas durante la fase de análisis, así como consultar la malla personalizada para proporcionar comentarios de los usuarios.
* **Import_UnderstandingMesh:** durante el examen, el comportamiento **SpatialUnderstandingCustomMesh** proporcionado por el módulo y colocado en el prefab de comprensión consultará periódicamente la malla personalizada generada por el proceso. Además, esto se hace una vez más después de que se haya finalizado el examen.

El flujo de examen, controlado por el comportamiento **SpatialUnderstanding** llama a **InitScan** y, a continuación, **UpdateScan** a cada fotograma. Cuando la consulta de estadísticas informa de una cobertura razonable, el usuario puede llamar a **RequestFinish** para indicar el final de la fase de análisis. Se sigue llamando a **UpdateScan** hasta que su valor devuelto indica que el archivo DLL ha completado el procesamiento.

## <a name="the-queries"></a>Las consultas

Una vez completado el examen, podrá acceder a tres tipos diferentes de consultas en la interfaz :
* **Consultas de topología:** son consultas rápidas que se basan en la topología de la sala examinada.
* **Consultas de formas:** usan los resultados de las consultas de topología para buscar superficies horizontales que coincidan bien con las formas personalizadas que defina.
* **Consultas de colocación de** objetos: son consultas más complejas que encuentran la ubicación más adecuada en función de un conjunto de reglas y restricciones para el objeto.

Además de las tres consultas principales, hay una interfaz de difusión por rayos que se puede usar para recuperar tipos de superficie etiquetados y se puede copiar una malla de sala estanca personalizada.

### <a name="topology-queries"></a>Consultas de topología

Dentro del archivo DLL, el administrador de topologías controla el etiquetado del entorno. Como se mencionó anteriormente, gran parte de los datos se almacenan en tablas, que se encuentran dentro de un volumen de vóxel. Además, la estructura **PlaySpaceInfos** se usa para almacenar información sobre el espacio de juego, incluida la alineación del mundo (más detalles sobre esto a continuación), el suelo y la altura del límite superior.

La heurística se usa para determinar el suelo, el techo y las paredes. Por ejemplo, la superficie horizontal más grande y más baja con más de 1 m2 de superficie se considera el suelo. Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de examen también se usa en este proceso.

Un subconjunto de las consultas expuestas por el administrador de topologías se expone a través del archivo DLL. Las consultas de topología expuestas son las siguientes:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Cada una de las consultas tiene un conjunto de parámetros, específicos del tipo de consulta. En el ejemplo siguiente, el usuario especifica el alto mínimo & ancho del volumen deseado, la altura de colocación mínima por encima del suelo y la cantidad mínima de autorización delante del volumen. Todas las medidas están en metros.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada una de estas consultas toma una matriz preasignada de **estructuras TopologyResult.** El **parámetro locationCount** especifica la longitud de la matriz pasada. El valor devuelto informa del número de ubicaciones devueltas. Este número nunca es mayor que el parámetro **locationCount** pasado.

**TopologyResult contiene** la posición central del volumen devuelto, la dirección orientada (es decir, normal) y las dimensiones del espacio encontrado.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Tenga en cuenta que, en el ejemplo de Unity, cada una de estas consultas está vinculada a un botón en el panel de interfaz de usuario virtual. El ejemplo codifica los parámetros de cada una de estas consultas a valores razonables. Vea *SpaceVisualizer.cs en* el código de ejemplo para obtener más ejemplos.

### <a name="shape-queries"></a>Dar forma a las consultas

Dentro del archivo DLL, el analizador de formas **(ShapeAnalyzer_W**) usa el analizador de topología para que coincida con las formas personalizadas definidas por el usuario. El ejemplo de Unity tiene un conjunto predefinido de formas que se muestran en el menú de consulta, en la pestaña forma.

Tenga en cuenta que el análisis de formas solo funciona en superficies horizontales. Un diván, por ejemplo, se define mediante la superficie del puesto plano y la parte superior plana del respaldo del diván. La consulta de formas busca dos superficies de un tamaño, un alto y un intervalo de aspecto específicos, con las dos superficies alineadas y conectadas. Mediante la terminología de las API, el puesto del diván y la parte superior de la parte posterior del diván son componentes de forma y los requisitos de alineación son restricciones de componente de forma.

Una consulta de ejemplo definida en el ejemplo de Unity (**ShapeDefinition.cs**), para objetos "sittable" es la siguiente:




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Cada consulta de forma se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componentes y un conjunto de restricciones de forma que enumera las dependencias entre los componentes. Este ejemplo incluye tres restricciones en una única definición de componente y ninguna restricción de forma entre componentes (ya que solo hay un componente).

Por el contrario, la forma del diván tiene dos componentes de forma y cuatro restricciones de forma. Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Las funciones contenedoras se proporcionan en el módulo de Unity para facilitar la creación de definiciones de formas personalizadas. La lista completa de restricciones de componentes y formas se puede encontrar **en SpatialUnderstandingDll.cs** dentro de las estructuras **ShapeComponentConstraint** y **ShapeConstraint.**

![El rectángulo azul resalta los resultados de la consulta de forma de la butaca.](images/chair-shape-query-500px.png)

El rectángulo azul resalta los resultados de la consulta de forma de la butaca.



### <a name="object-placement-solver"></a>Solucionador de colocación de objetos

Las consultas de colocación de objetos se pueden usar para identificar ubicaciones ideales en la sala física para colocar los objetos. El solucionador encontrará la ubicación más adecuada dadas las restricciones y las reglas de objeto. Además, las consultas de objetos se conservan hasta que el objeto se quita con Solver_RemoveObject **o** **Solver_RemoveAllObjects** llamadas, lo que permite la selección de ubicación restringida de varios objetos.

Las consultas de colocación de objetos constan de tres partes: tipo de selección de ubicación con parámetros, una lista de reglas y una lista de restricciones. Para ejecutar una consulta, use la API siguiente:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Esta función toma un nombre de objeto, una definición de selección de ubicación y una lista de reglas y restricciones. Los contenedores de C# proporcionan funciones auxiliares de construcción para facilitar la construcción de reglas y restricciones. La definición de selección de ubicación contiene el tipo de consulta, es decir, uno de los siguientes:




```
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

Cada uno de los tipos de selección de ubicación tiene un conjunto de parámetros únicos para el tipo. La **estructura ObjectPlacementDefinition** contiene un conjunto de funciones auxiliares estáticas para crear estas definiciones. Por ejemplo, para buscar un lugar donde colocar un objeto en el suelo, puede usar la siguiente función: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Además del tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones. No se pueden infringir las reglas. Las posibles ubicaciones de selección de ubicación que satisfacen el tipo y las reglas se optimizan con respecto al conjunto de restricciones para seleccionar la ubicación de ubicación óptima. Las funciones de creación estática proporcionadas pueden crear cada una de las reglas y restricciones. A continuación se proporciona una regla de ejemplo y una función de construcción de restricciones.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La siguiente consulta de colocación de objetos busca un lugar donde colocar un cubo de medio metro en el borde de una superficie, lejos de otros objetos que anteriormente se colocaron y cerca del centro de la sala.




```
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

Si se realiza correctamente, se devuelve una estructura **ObjectPlacementResult** que contiene la posición de colocación, las dimensiones y la orientación. Además, la colocación se agrega a la lista interna del archivo DLL de objetos colocados. Las consultas de selección de ubicación posteriores tendrán en cuenta este objeto. El **archivo LevelSolver.cs del** ejemplo de Unity contiene más consultas de ejemplo.

![Los cuadros azules muestran el resultado de tres consultas Place On Floor con reglas de "lejos de la posición de la cámara".](images/away-from-camera-position-500px.png)

Los cuadros azules muestran el resultado de tres consultas Place On Floor con reglas de "lejos de la posición de la cámara".


**Sugerencias:**
* Al resolver la ubicación de colocación de varios objetos necesarios para un escenario de nivel o aplicación, primero debe resolver objetos imprescindibles y grandes para maximizar la probabilidad de que se pueda encontrar un espacio.
* El orden de selección de ubicación es importante. Si no se pueden encontrar colocaciones de objetos, pruebe con configuraciones menos restringidas. Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de sala.

### <a name="ray-casting"></a>Conversión de rayos

Además de las tres consultas principales, se puede usar una interfaz de conversión de rayos para recuperar los tipos de superficie etiquetados y se puede copiar una malla de espacio de juego estanca personalizada una vez que se ha analizado y finalizado la sala, las etiquetas se generan internamente para superficies como el suelo, el límite superior y las paredes. La **función PlayspaceRaycast** toma un rayo y devuelve si el rayo colisiona con una superficie conocida y, si es así, información sobre esa superficie en forma de **RaycastResult**. 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Internamente, la difusión por rayos se calcula en la representación de vóxel en cubo de 8 cm calculada del espacio de reproducción. Cada vóxel contiene un conjunto de elementos de superficie con datos de topología procesados (también conocidos como tablas). Se comparan las tablas contenidas dentro de la celda de vóxel intersecada y la mejor coincidencia que se usa para buscar la información de la topología. Estos datos de topología contienen el etiquetado devuelto en forma de enumeración **SurfaceTypes,** así como el área de superficie de la superficie intersectada.

En el ejemplo de Unity, el cursor convierte un rayo en cada fotograma. En primer lugar, contra los colisiondores de Unity; en segundo lugar, frente a la representación mundial del módulo de comprensión; y, por último, en los elementos de la interfaz de usuario. En esta aplicación, la interfaz de usuario obtiene prioridad, después el resultado de la comprensión y, por último, los colisiondores de Unity. SurfaceType **se** notifica como texto junto al cursor.

![Intersección de informes de resultados de raycast con el suelo.](images/raycast-result-500px.jpg)

Intersección de informes de resultados de raycast con el suelo.


## <a name="get-the-code"></a>Obtención del código

El código abierto está disponible en [MixedRealityToolkit.](https://github.com/Microsoft/MixedRealityToolkit-Unity) Háganoslo [saber en HoloLens foros](https://forums.hololens.com/) para desarrolladores si usa el código en un proyecto. No podemos esperar a ver lo que hace con él.

## <a name="about-the-author"></a>Acerca del autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt es</b> un director de ingeniería de software que ha trabajado en HoloLens desde los primeros días, desde la experimentación hasta el desarrollo. Antes HoloLens, trabajó en xbox Kinect y en el sector de juegos en una amplia variedad de plataformas y juegos. Jeff le encanta la robótica, los gráficos y las cosas con luces parpadeantes que suenan. Le gusta aprender cosas nuevas y trabajar en software, hardware y, especialmente, en el espacio en el que ambos se cruzan.</td>
</tr>
</table>



## <a name="see-also"></a>Consulta también
* [Asignación espacial](../design/spatial-mapping.md)
* [Descripción de escenas](../design/scene-understanding.md)
* [Visualización de la exploración de la sala](../design/room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: lecciones de la primera línea del HoloLens desarrollo](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
