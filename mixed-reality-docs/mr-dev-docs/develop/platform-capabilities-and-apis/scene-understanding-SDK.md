---
title: SDK de descripción de la escena
description: Obtenga información sobre cómo instalar y usar el SDK de Scene Understanding, incluidos componentes, mallas y objetos en aplicaciones de realidad mixta.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Scene Understanding, Spatial Mapping, Windows Mixed Reality, Unity
ms.openlocfilehash: 1b93f3137e1ac1309ee56e974a0fa33608114f16dfb65a13e369490f45d6beb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193648"
---
# <a name="scene-understanding-sdk-overview"></a>Introducción al SDK de descripción de la escena

La comprensión de la escena transforma los datos no estructurados del sensor del entorno que el Mixed Reality captura y los convierte en una representación abstracta eficaz. El SDK actúa como capa de comunicación entre la aplicación y el entorno de ejecución de Scene Understanding. Su objetivo es imitar construcciones estándar existentes, como gráficos de escena 3D para representaciones 3D y rectángulos y paneles 2D para aplicaciones 2D. Aunque las construcciones que scene understanding imita se asignarán a marcos concretos, en general SceneUnderstanding es un marco independiente que permite la interoperabilidad entre diversos marcos que interactúan con él. A medida que Scene Understanding evoluciona, el rol del SDK es garantizar que las nuevas representaciones y funcionalidades se sigan exponendo dentro de un marco unificado. En este documento, primero presentaremos conceptos de alto nivel que le ayudarán a familiarizarse con el entorno o el uso de desarrollo y, a continuación, proporcionaremos documentación más detallada para clases y construcciones específicas.

## <a name="where-do-i-get-the-sdk"></a>¿Dónde puedo obtener el SDK?

El SDK SceneUnderstanding se puede descargar a través [de Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md).

**Nota:** La versión más reciente depende de los paquetes de versión preliminar y deberá habilitar los paquetes de versión preliminar para verla.

Para la versión 0.5.2022-rc y versiones posteriores, Scene Understanding admite proyecciones de lenguaje para C# y C++ que permiten a las aplicaciones desarrollar aplicaciones para plataformas Win32 o UWP. Desde esta versión, SceneUnderstanding admite la compatibilidad con Unity en el editor que no incluye SceneObserver, que se usa únicamente para comunicarse con HoloLens2. 

SceneUnderstanding requiere Windows SDK versión 18362 o posterior. 

## <a name="conceptual-overview"></a>Información conceptual

### <a name="the-scene"></a>La escena

El dispositivo de realidad mixta integra constantemente información sobre lo que ve en su entorno. Scene Understanding embudos all of these data sources and produce one single cohesive abstraction. Scene Understanding genera Scenes, que son una composición de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representan una instancia de una sola cosa (por ejemplo, una pared, un límite superior o un suelo). Los propios objetos scene son una composición de [SceneComponents, que representan partes más granulares que constituyen este SceneObject. Algunos ejemplos de componentes son quads y mallas, pero en el futuro podrían representar rectángulos delimitadores, mallas de colisión, metadatos, etc.

El proceso de convertir los datos del sensor sin procesar en una escena es una operación potencialmente costosa que podría tardar segundos en usar espacios medios (~10 x 10 m) en minutos para espacios grandes (~50 x 50 m) y, por tanto, no es algo que el dispositivo esté calculando sin solicitud de aplicación. En su lugar, la aplicación desencadena la generación de escena a petición. La clase SceneObserver tiene métodos estáticos que pueden calcular o deserializar una escena, con los que puede enumerar o interactuar. La acción "Compute" se ejecuta a petición y se ejecuta en la CPU, pero en un proceso independiente (el controlador Mixed Reality). Sin embargo, mientras calculamos en otro proceso, los datos de la escena resultantes se almacenan y mantienen en la aplicación en el objeto Scene. 

A continuación se muestra un diagrama que ilustra este flujo de proceso y muestra ejemplos de dos aplicaciones que se interfiriendo con el entorno de ejecución de Scene Understanding. 

![Diagrama de procesos](images/SU-ProcessFlow.png)

En el lado izquierdo hay un diagrama del entorno de ejecución de realidad mixta, que siempre está en funcionamiento en su propio proceso. Este tiempo de ejecución es responsable de realizar el seguimiento de dispositivos, la asignación espacial y otras operaciones que Scene Understanding usa para comprender y razonar sobre el mundo que le rodea. En el lado derecho del diagrama, se muestran dos aplicaciones teóricas que usan Scene Understanding. La primera aplicación se interfaces con MRTK, que usa el SDK de Scene Understanding internamente, la segunda aplicación calcula y usa dos instancias de escena independientes. Las tres escenas de este diagrama generan instancias distintas de las escenas, el controlador no está siguiendo el estado global que se comparte entre las aplicaciones y los objetos de escena de una escena no se encuentran en otra. Scene Understanding proporciona un mecanismo para realizar un seguimiento a lo largo del tiempo, pero esto se hace mediante el SDK. El código de seguimiento ya se está ejecutando en el SDK en el proceso de la aplicación.

Dado que cada escena almacena sus datos en el espacio de memoria de la aplicación, puede suponer que todas las funciones del objeto Scene o sus datos internos siempre se ejecutan en el proceso de la aplicación.

### <a name="layout"></a>Layout

Para trabajar con Scene Understanding, puede ser útil conocer y comprender cómo el tiempo de ejecución representa los componentes de forma lógica y física. La escena representa los datos con un diseño específico que se eligió para ser sencillos al tiempo que se mantiene una estructura subyacente que es ajustable para satisfacer los requisitos futuros sin necesidad de revisiones importantes. Para ello, la escena almacena todos los componentes (bloques de creación de todos los objetos de escena) en una lista plana y define la jerarquía y la composición a través de referencias donde componentes específicos hacen referencia a otros.

A continuación se muestra un ejemplo de una estructura en su forma plana y lógica.

<table>
<tr><th>Diseño lógico</th><th>Diseño físico</th></tr>
<tr>
<td>
<ul>
  Escena
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

En esta ilustración se resalta la diferencia entre el diseño físico y lógico de la escena. A la izquierda, vemos el diseño jerárquico de los datos que la aplicación ve al enumerar la escena. A la derecha, vemos que la escena consta de 12 componentes distintos a los que se puede acceder individualmente si es necesario. Al procesar una nueva escena, se espera que las aplicaciones desistan de esta jerarquía de forma lógica; sin embargo, al realizar el seguimiento entre las actualizaciones de la escena, es posible que algunas aplicaciones solo estén interesadas en dirigirse a componentes específicos que se comparten entre dos escenas.

## <a name="api-overview"></a>Introducción a la API

En la sección siguiente se proporciona información general de alto nivel de las construcciones de Scene Understanding. La lectura de esta sección le permitirá comprender cómo se representan las escenas y para qué se usan los distintos componentes. En la sección siguiente se proporcionarán ejemplos de código concretos y detalles adicionales que se glosarán en esta introducción.

Todos los tipos descritos a continuación residen en el espacio de `Microsoft.MixedReality.SceneUnderstanding` nombres .

### <a name="scenecomponents"></a>SceneComponents

Ahora que comprende el diseño lógico de las escenas, ahora podemos presentar el concepto de SceneComponents y cómo se usan para crear la jerarquía. SceneComponents son las descomposicións más granulares de SceneUnderstanding que representan un único elemento principal, por ejemplo, una malla, un cuadrándulo o un rectángulo delimitador. SceneComponents son elementos que se pueden actualizar de forma independiente y a los que otros SceneComponents pueden hacer referencia, por lo que tienen una sola propiedad global con un identificador único, que permiten este tipo de mecanismo de seguimiento o referencia. Los identificadores se usan para la composición lógica de la jerarquía de la escena, así como para la persistencia de objetos (el acto de actualizar una escena con respecto a otra). 

Si está tratando cada escena recién calculada como distinta y simplemente enumera todos los datos dentro de ella, los identificadores son en gran medida transparentes para usted. Sin embargo, si planea realizar un seguimiento de los componentes a través de varias actualizaciones, usará los identificadores para indexar y buscar SceneComponents entre objetos scene.

### <a name="sceneobjects"></a>SceneObjects

Un SceneObject es un SceneComponent que representa una instancia de una "cosa", por ejemplo, una pared, un suelo, un límite superior, etc.... expresado por su propiedad Kind. SceneObjects son geométricos y, por tanto, tienen funciones y propiedades que representan su ubicación en el espacio, pero no contienen ninguna estructura geométrica o lógica. En su lugar, SceneObjects hace referencia a otros SceneComponents, específicamente SceneQuads y SceneMeshes, que proporcionan las diversas representaciones compatibles con el sistema. Cuando se calcula una nueva escena, lo más probable es que la aplicación enumere los SceneObjects de la escena para procesar lo que le interesa.

SceneObjects puede tener cualquiera de los siguientes elementos:

<table>
<tr>
<th>SceneObjectKind</th> <th>Description</th>
</tr>
<tr><td>Segundo plano</td><td>Se sabe que SceneObject no es <b>uno</b> de los otros tipos reconocidos de objeto de escena. Esta clase no debe confundirse con Desconocido, donde se sabe que background no es de la pared, el suelo o el límite superior, etc.... mientras que desconocido aún no se ha clasificado por categorías.</b></td></tr>
<tr><td>Pared</td><td>Una pared física. Se supone que las paredes son estructuras ambientales legibles.</td></tr>
<tr><td>Floor</td><td>Los suelos son cualquier superficie en la que se puede recorrer. Nota: Los suelos no son suelos. Tenga en cuenta también que los suelos asumen cualquier superficie a pie y, por tanto, no hay ninguna suposición explícita de una planta singular. Estructuras de varios niveles, rampas, etc.... debe clasificarse como floor.</td></tr>
<tr><td>Ceiling</td><td>Superficie superior de una sala.</td></tr>
<tr><td>Plataforma</td><td>Una gran superficie plana en la que podría colocar hologramas. Tienden a representar tablas, contratops y otras superficies horizontales de gran tamaño.</td></tr>
<tr><td>World</td><td>Una etiqueta reservada para datos geométricos que es independiente del etiquetado. La malla generada estableciendo la marca de actualización EnableWorldMesh se clasificaría como world.</td></tr>
<tr><td>Unknown</td><td>Este objeto de escena aún no se ha clasificado y se le ha asignado un tipo. Esto no debe confundirse con Background, ya que este objeto podría ser cualquier cosa, el sistema todavía no ha llegado con una clasificación lo suficientemente fuerte para él.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh es un SceneComponent que aproxima la geometría de objetos geométricos arbitrarios mediante una lista de triángulos. SceneMeshes se usa en varios contextos diferentes, pueden representar componentes de la estructura de celdas estancas o como WorldMesh, que representa la malla de asignación espacial sin enlazar asociada a la escena. Los datos de índice y vértice proporcionados con cada malla usan el mismo diseño conocido que los búferes de vértice e índice que se usan para representar [mallas](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) de triángulo en todas las API de representación modernas. En Scene Understanding, las mallas usan índices de 32 bits y es posible que deba dividirse en fragmentos para determinados motores de representación.

#### <a name="winding-order-and-coordinate-systems"></a>Orden de viento y sistemas de coordenadas

Se espera que todas las mallas producidas por Scene Understanding devuelvan mallas en un Right-Handed de coordenadas mediante el orden de sinuoso en el sentido de las agujas del reloj. 

Nota: Las compilaciones del sistema operativo anteriores 191105 .191105 pueden tener un error conocido en el que las mallas "World Counter-Clockwise" devolvían en orden de sinuoso, que posteriormente se ha corregido.

### <a name="scenequad"></a>SceneQuad

SceneQuad es un SceneComponent que representa superficies 2d que ocupan el mundo 3d. SceneQuads se puede usar de forma similar a ARKit ARPlaneAnchor o ARCore Planes, pero ofrecen una funcionalidad más alta como lienzos 2d para que los usen las aplicaciones planas o la experiencia de usuario aumentada. Las API específicas 2D se proporcionan para los quads que hacen que la colocación y el diseño sean fáciles de usar, y el desarrollo (a excepción de la representación) con quads debe ser más parecido a trabajar con lienzos 2d que con mallas 3d.

#### <a name="scenequad-shape"></a>Forma SceneQuad

SceneQuads define una superficie rectangular limitada en 2d. Sin embargo, SceneQuads representa superficies con formas arbitrarias y potencialmente complejas (por ejemplo, una tabla con forma de anillo). Para representar la forma compleja de la superficie de un quad, puede usar la API GetSurfaceMask para representar la forma de la superficie en un búfer de imagen que proporcione. Si sceneObject que tiene el cuadrándulo también tiene una malla, los triángulos de malla deben ser equivalentes a esta imagen representado, ambos representan la geometría real de la superficie, ya sea en coordenadas 2d o 3d.

## <a name="scene-understanding-sdk-details-and-reference"></a>Referencia y detalles del SDK de descripción de la escena

> [!NOTE] 
> Al usar MRTK, tenga en cuenta que interactuará con MRTK y, por tanto, puede omitir esta sección [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) en la mayoría de las circunstancias. Consulte los documentos [de MRTK Scene Understanding para](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) obtener más información.

La siguiente sección le ayudará a familiarizarse con los conceptos básicos de SceneUnderstanding. Esta sección debe proporcionar los conceptos básicos, en cuyo momento debe tener suficiente contexto para examinar las aplicaciones de ejemplo para ver cómo se usa SceneUnderstanding holísticamente.

### <a name="initialization"></a>Inicialización

El primer paso para trabajar con SceneUnderstanding es que la aplicación obtenga referencia a un objeto Scene. Esto se puede hacer de dos maneras: una escena se puede calcular mediante el controlador o una escena existente que se calculó en el pasado puede deseriarse. Este último es útil para trabajar con SceneUnderstanding durante el desarrollo, donde las aplicaciones y las experiencias se pueden crear prototipos rápidamente sin un dispositivo de realidad mixta.

Las escenas se calculan mediante SceneObserver. Antes de crear una escena, la aplicación debe consultar el dispositivo para asegurarse de que admite SceneUnderstanding, así como para solicitar acceso al usuario para obtener información que SceneUnderstanding necesita.

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Si no se llama a RequestAccessAsync(), se producirá un error al calcular una nueva escena. A continuación, calcularemos una nueva escena que se basa en el casco Mixed Reality y tiene un radio de 10 metros.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>Inicialización a partir de datos (también conocido como . la ruta de acceso del equipo)

Aunque las escenas se pueden calcular para el consumo directo, también se pueden calcular en formato serializado para su uso posterior. Esto ha demostrado ser útil para el desarrollo, ya que permite a los desarrolladores trabajar en Scene Understanding y probarlo sin necesidad de un dispositivo. El acto de serializar una escena es casi idéntico a calcularla; los datos se devuelven a la aplicación en lugar de que el SDK lo deserialice localmente. A continuación, puede deserializarlo usted mismo o guardarlo para su uso futuro.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>Enumeración SceneObject

Ahora que la aplicación tiene una escena, la aplicación buscará e interactuará con SceneObjects. Para ello, acceda a **la propiedad SceneObjects:**

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>Componentes de actualización y refinamiento de componentes

Hay otra función que recupera componentes de la escena denominada ***FindComponent.*** Esta función es útil al actualizar objetos de seguimiento y buscarlos en escenas posteriores. El código siguiente calculará una nueva escena con respecto a una escena anterior y, a continuación, buscará el suelo en la nueva escena.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Acceso a mallas y quads desde objetos de escena

Una vez que se han encontrado sceneObjects, lo más probable es que la aplicación quiera acceder a los datos contenidos en los quads o mallas de los que se compone. Se accede a estos datos con las propiedades ***Quads** _ y _ *_Meshes_**. El código siguiente enumerará todos los quads y mallas de nuestro objeto floor.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Observe que es SceneObject el que tiene la transformación relativa al origen de la escena. Esto se debe a que SceneObject representa una instancia de una "cosa" y es localizable en el espacio, los quads y las mallas representan la geometría que se transforma en relación con su elemento primario. Es posible que sceneObjects independientes haga referencia a los mismos SceneMesh/SceneQuad SceneComponents, y también es posible que sceneObject tenga más de un SceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Tratar con transformaciones

Scene Understanding ha realizado un intento intencionado de alinearse con las representaciones de escena 3D tradicionales al tratar con transformaciones. Por lo tanto, cada escena se limita a un único sistema de coordenadas muy parecido a las representaciones ambientales 3D más comunes. SceneObjects proporciona su ubicación en relación con ese sistema de coordenadas. Si la aplicación está tratando con escenas que extienden el límite de lo que proporciona un único origen, puede delimitar SceneObjects a SpatialAnchors o generar varias escenas y combinarlas, pero por motivos de simplicidad se supone que existen escenas estancas en su propio origen que se localizan mediante un NodeId definido por Scene.OriginSpatialGraphNodeId.

El siguiente código de Unity, por ejemplo, muestra cómo usar Windows Perception y las API de Unity para alinear los sistemas de coordenadas. Consulte [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) y [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) para obtener más información sobre las API de percepción de Windows y los objetos nativos de [Mixed Reality en Unity](/windows/mixed-reality/unity-xrdevice-advanced) para obtener más información sobre cómo obtener un spatialcoordinateSystem que se corresponda con el origen mundial de Unity.

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

Cada `SceneObject` tiene una transformación, que luego se aplica a ese objeto. En Unity, convertemos a coordenadas a la derecha y asignamos transformaciones locales como tal:

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>cuádruple

Los quads se diseñaron para ayudar a los escenarios de selección de ubicación en 2D y deben considerarse como extensiones para elementos de experiencia de usuario de lienzo 2D. Aunque los quads son componentes de SceneObjects y se pueden representar en 3D, las propias API quad asumen que quads son estructuras 2D. Ofrecen información como la extensión, la forma y proporcionan API para la selección de ubicación.

Los quads tienen extensiones rectangulares, pero representan superficies 2D con forma arbitraria. Para habilitar la selección de ubicación en estas superficies 2D que interactúan con los quads del entorno 3D, se ofrecen utilidades para que esta interacción sea posible. Actualmente, Scene Understanding proporciona dos funciones de este tipo, **FindCentermostPlacement** y **GetSurfaceMask.** FindCentermostPlacement es una API de alto nivel que busca una posición en el cuadrángolo donde se puede colocar un objeto e intentará encontrar la mejor ubicación para el objeto, lo que garantiza que el cuadro de límite que proporcione permanecerá en la superficie subyacente.

> [!NOTE]
> Las coordenadas de la salida son relativas al quad en "quad space" y la esquina superior izquierda es (x = 0, y = 0), igual que lo sería con otros tipos de ventanas Rect. Asegúrese de tener esto en cuenta al trabajar con los orígenes de sus propios objetos. 

En el ejemplo siguiente se muestra cómo buscar la ubicación colocable más central y delimitar un holograma al cuadránculo.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

Los pasos 1 a 4 dependen en gran medida de su marco o implementación concretos, pero los temas deben ser similares. Es importante tener en cuenta que el quad simplemente representa un plano 2D delimitado que se localiza en el espacio. Al hacer que el motor o el marco sepan dónde está el cuádigo y raíz de los objetos en relación con el cuadrángrama, los hologramas se ubicarán correctamente con respecto al mundo real. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>En malla

Las mallas representan representaciones geométricas de objetos o entornos. De forma muy similar a la asignación [espacial,](../../design/spatial-mapping.md)los datos de índice de malla y vértice proporcionados con cada malla de superficie espacial usan el mismo diseño conocido que los búferes de vértice e índice que se usan para representar mallas de triángulo en todas las API de representación modernas. Las posiciones de vértice se proporcionan en el sistema de coordenadas de `Scene` . Las API específicas que se usan para hacer referencia a estos datos son las siguientes:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

El código siguiente proporciona un ejemplo de generación de una lista de triángulos a partir de la estructura de malla:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Los búferes de índice o vértice deben ser >= los recuentos de índice o vértice, pero de lo contrario pueden tener un tamaño arbitrario que permita una reutilización eficaz de la memoria.

### <a name="collidermesh"></a>ColliderMesh

Los objetos de escena proporcionan acceso a los datos de malla y malla de colisionador a través de las propiedades Meshes y ColliderMeshes. Estas mallas siempre coincidirán, lo que significa que el índice i'th de la propiedad Meshes representa la misma geometría que el índice i'th de la propiedad ColliderMeshes. Si el runtime/objeto admite mallas de colisionador, se garantiza que obtiene el polígono más bajo y la aproximación de orden más alto y es una buena práctica usar ColliderMeshes dondequiera que la aplicación use colisiondores. Si el sistema no admite colisiones, el objeto Mesh devuelto en ColliderMeshes será el mismo objeto que la malla que reduce las restricciones de memoria.

## <a name="developing-with-scene-understanding"></a>Desarrollo con la comprensión de la escena

En este punto, debe comprender los principales bloques de creación de la escena que comprenden el entorno de ejecución y el SDK. La mayor parte de la potencia y complejidad radica en los patrones de acceso, la interacción con marcos 3D y las herramientas que se pueden escribir sobre estas API para realizar tareas más avanzadas, como el planeamiento espacial, el análisis de sala, la navegación, la física, etc. Esperamos capturar estos datos en ejemplos que, con suerte, deberían guiarlo en la dirección adecuada para hacer que sus escenarios resalten. Si hay ejemplos o escenarios que no estamos abordando, háganoslo saber e intentaremos documentar o crear prototipos de lo que necesita.

### <a name="where-can-i-get-sample-code"></a>¿Dónde puedo obtener código de ejemplo?

El código de ejemplo de Scene Understanding para Unity se puede encontrar en nuestra [página de ejemplo de Unity.](https://github.com/sceneunderstanding-microsoft/unitysample) Esta aplicación le permitirá comunicarse con el dispositivo y representar los distintos objetos de escena, o bien, le permitirá cargar una escena serializada en el equipo y le permitirá experimentar Scene Understanding sin un dispositivo.

### <a name="where-can-i-get-sample-scenes"></a>¿Dónde puedo obtener escenas de ejemplo?

Si tiene holoLens2, puede guardar cualquier escena que haya capturado guardando la salida de ComputeSerializedAsync en el archivo y deserializarla por su comodidad. 

Si no tiene un dispositivo HoloLens2 pero quiere jugar con Scene Understanding, deberá descargar una escena capturada previamente. El ejemplo Scene Understanding se distribuye actualmente con escenas serializadas que se pueden descargar y usar según su propia comodidad. Puede encontrarlos aquí:

[Escenas de ejemplo de descripción de la escena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Consulta también

* [Asignación espacial](../../design/spatial-mapping.md)
* [Descripción de escenas](../../design/scene-understanding.md)
* [Ejemplo de Unity](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)