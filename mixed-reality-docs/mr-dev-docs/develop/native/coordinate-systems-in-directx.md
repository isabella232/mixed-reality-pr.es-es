---
title: Sistemas de coordenadas de DirectX
description: Obtenga información sobre los sistemas de coordenadas en DirectX Mixed Reality con localizadores espaciales, marcos de referencia y delimitadores espaciales.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Mixed Reality, localizador espacial, marco de referencia espacial, sistema de coordenadas espaciales, fase espacial, código de ejemplo, estabilización de imágenes, anclaje espacial, almacén de anclaje espacial, pérdida de seguimiento, tutorial, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 5da521568ef15f0c512984c96846939bd30063d3485709d4b6568dc9b155052a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196467"
---
# <a name="coordinate-systems-in-directx"></a>Sistemas de coordenadas de DirectX

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.

[Los sistemas de](../../design/coordinate-systems.md) coordenadas forman la base para la comprensión espacial que ofrecen Windows Mixed Reality API.

Los dispositivos vr o VR de una sola habitación de hoy en día establecen un sistema de coordenadas principal para su espacio de seguimiento. Mixed Reality dispositivos como HoloLens están diseñados para entornos indefinidos de gran tamaño, con el dispositivo detectando y aprendiendo sobre su entorno a medida que el usuario le guía. El dispositivo se adapta a mejorar continuamente el conocimiento sobre las salas del usuario, pero da lugar a sistemas de coordenadas que cambian su relación entre sí a lo largo de la duración de las aplicaciones. Windows Mixed Reality admite una amplia gama de dispositivos, desde cascos envolventes sentados hasta marcos de referencia conectados al mundo.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de C++17 compatible con C++/WinRT, como se usa en la plantilla de proyecto holográfico de [C++.](creating-a-holographic-directx-project.md)  Los conceptos son equivalentes para un proyecto de C++/WinRT, aunque deberá traducir el código.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemas de coordenadas espaciales en Windows

El tipo principal que se usa para razonar sobre los sistemas de coordenadas del mundo real Windows es <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Una instancia de este tipo representa un sistema de coordenadas arbitrario, que proporciona un método para obtener datos de la matriz de transformación que puede usar para transformar entre dos sistemas de coordenadas sin comprender los detalles de cada uno.

Los métodos que devuelven información espacial aceptarán un parámetro SpatialCoordinateSystem para que pueda decidir el sistema de coordenadas en el que es más útil devolver esas coordenadas. La información espacial se representa como puntos, rayos o volúmenes en el entorno del usuario, y las unidades de estas coordenadas siempre estarán en metros.

SpatialCoordinateSystem tiene una relación dinámica con otros sistemas de coordenadas, incluidos los que representan la posición del dispositivo. En cualquier momento, el dispositivo puede localizar algunos sistemas de coordenadas y no otros. Para la mayoría de los sistemas de coordenadas, la aplicación debe estar lista para controlar los períodos de tiempo durante los que no se pueden encontrar.

La aplicación no debe crear spatialCoordinateSystems directamente, sino que se deben consumir a través de las API de Perception. Hay tres orígenes principales de sistemas de coordenadas en las API de Perception, cada uno de los cuales se asigna a un concepto descrito en la página [Sistemas de coordenadas:](../../design/coordinate-systems.md)
* Para obtener un marco de referencia de tipo stationary, cree <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">un objeto SpatialStationaryFrameOfReference</a> u obtenga uno del objeto <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference actual.</a>
* Para obtener un delimitador espacial, cree un <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">spatialAnchor</a>.
* Para obtener un marco adjunto de referencia, cree <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">un objeto SpatialLocatorAttachedFrameOfReference.</a>

Todos los sistemas de coordenadas devueltos por estos objetos son a la derecha, con +y hacia arriba, +x a la derecha y +z hacia atrás. Puede recordar en qué dirección apunta el eje Z positivo señalando los dedos de la mano izquierda o derecha en la dirección X positiva y en curling en la dirección y positiva. La dirección en la que apunta el control, ya sea hacia usted o lejos de usted, es la dirección en la que apunta el eje Z positivo para ese sistema de coordenadas. En la ilustración siguiente se muestran estos dos sistemas de coordenadas.

![Sistemas de coordenadas izquierdo y derecho](images/left-hand-right-hand.gif)<br>
*Sistemas de coordenadas izquierdo y derecho*

Use la <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">clase SpatialLocator</a> para crear un marco de referencia adjunto o estacionado para arrancar en spatialcoordinateSystem en función de la posición HoloLens trabajo. Continúe con la sección siguiente para obtener más información sobre este proceso.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Colocación de hologramas en el mundo mediante una fase espacial

Se accede al sistema de coordenadas Windows Mixed Reality cascos envolventes opacos mediante la propiedad <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">estática SpatialStageFrameOfReference::Current.</a> Esta API proporciona:

* Un sistema de coordenadas
* Información sobre si el reproductor está sentado o móvil
* Límite de un área segura para recorrer si el reproductor es móvil
* Indicación de si el casco es direccional. 
* Controlador de eventos para las actualizaciones de la fase espacial.

En primer lugar, se obtiene la fase espacial y se suscribe a las actualizaciones: 

Código para la **inicialización de la fase espacial**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

En el método OnCurrentChanged, la aplicación debe inspeccionar la fase espacial y actualizar la experiencia del jugador. En este ejemplo, se proporciona una visualización del límite de la fase y la posición inicial especificada por el usuario y el intervalo de vistas y el intervalo de propiedades de movimiento de la fase. También retrocluyemos a nuestro propio sistema de coordenadas stationary, cuando no se puede proporcionar una fase.


Actualización del código **para la fase espacial**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

El conjunto de vértices que definen el límite de la fase se proporciona en el sentido de las agujas del reloj. El Windows Mixed Reality shell dibuja una barrera en el límite cuando el usuario se aproxima a ella, pero es posible que desee triangular el área que se puede recorrer para sus propios fines. El siguiente algoritmo se puede usar para triangular la fase.


Código para la **triangularización de la fase espacial**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Colocación de hologramas en el mundo mediante un marco de referencia estacionados

La [clase SpatialStationaryFrameOfReference](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference) representa un [](../../design/coordinate-systems.md#stationary-frame-of-reference) marco de referencia que permanece estacional en relación con el entorno del usuario a medida que el usuario se mueve. Este marco de referencia da prioridad a mantener las coordenadas estables cerca del dispositivo. Un uso clave de spatialStationaryFrameOfReference es actuar como el sistema de coordenadas del mundo subyacente dentro de un motor de representación al representar hologramas.

Para obtener un objeto SpatialStationaryFrameOfReference, use la clase [SpatialLocator](/uwp/api/Windows.Perception.Spatial.SpatialLocator) y llame a [CreateStationaryFrameOfReferenceAtCurrentLocation](/uwp/api/Windows.Perception.Spatial.SpatialLocator).

En el código Windows plantilla de aplicación holográfica:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Los marcos de referencia estacionados están diseñados para proporcionar una posición de mejor ajuste con respecto al espacio total. Las posiciones individuales dentro de ese marco de referencia pueden desviarse ligeramente. Esto es normal a medida que el dispositivo aprende más sobre el entorno.
* Cuando se requiere una colocación precisa de hologramas individuales, se debe usar spatialAnchor para delimitar el holograma individual a una posición en el mundo real, por ejemplo, un punto que el usuario indica que es de especial interés. Las posiciones de anclaje no se desvian, pero se pueden corregir. el delimitador usará la posición corregida a partir del siguiente fotograma después de que se haya producido la corrección.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Colocación de hologramas en el mundo mediante anclajes espaciales

[Los delimitadores espaciales](../../design/coordinate-systems.md#spatial-anchors) son una excelente manera de colocar hologramas en un lugar específico del mundo real, con lo que el sistema garantiza que el anclaje permanece en su lugar con el tiempo. En este tema se explica cómo crear y usar un delimitador y cómo trabajar con datos de anclaje.

Puede crear un SpatialAnchor en cualquier posición y orientación dentro de SpatialCoordinateSystem de su elección. El dispositivo debe ser capaz de localizar ese sistema de coordenadas en este momento y el sistema no debe haber alcanzado su límite de anclajes espaciales.

Una vez definido, el sistema de coordenadas de spatialAnchor se ajusta continuamente para mantener la posición y orientación precisas de su ubicación inicial. A continuación, puede usar spatialanchor para representar hologramas que aparecerán fijos en el entorno del usuario en esa ubicación exacta.

Los efectos de los ajustes que mantienen el anclaje en su lugar se amplían a medida que aumenta la distancia desde el delimitador. Debe evitar la representación de contenido relativo a un delimitador que está a más de 3 metros del origen de ese delimitador.

La [propiedad CoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) obtiene un sistema de coordenadas que permite colocar contenido relativo al delimitador, con aceleración aplicada cuando el dispositivo ajusta la ubicación precisa del delimitador.

Use la [propiedad RawCoordinateSystem y](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) el evento [RawCoordinateSystemAdjusted](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) correspondiente para administrar estos ajustes usted mismo.

### <a name="persist-and-share-spatial-anchors"></a>Conservar y compartir delimitadores espaciales

Puede conservar un spatialAnchor localmente mediante la clase [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore) y, a continuación, recuperarlo en una sesión de aplicación futura en el mismo HoloLens dispositivo.

Con <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, puede crear un anclaje de nube duradero a partir de un SpatialAnchor local, que la aplicación puede localizar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común entre varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física en tiempo real. 

También puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia asincrónica de hologramas en HoloLens, iOS y Android.  Al compartir un anclaje espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

Para empezar a crear experiencias compartidas en HoloLens aplicación, pruebe la guía de inicio rápido de <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">5</a>minutos de Azure Spatial Anchors HoloLens .

Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear y buscar <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">delimitadores en HoloLens</a>.  También hay tutoriales disponibles <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">para Android e iOS,</a> lo que le permite compartir los mismos anclajes en todos los dispositivos.

### <a name="create-spatialanchors-for-holographic-content"></a>Creación de SpatialAnchors para contenido holográfico

Para este ejemplo de código, hemos modificado la plantilla Windows aplicación holográfica para crear delimitadores cuando se detecta **el** gesto Presionado. A continuación, el cubo se coloca en el delimitador durante el paso de representación.

Dado que la clase auxiliar admite varios delimitadores, podemos colocar tantos cubos como queremos usar este ejemplo de código.

> [!NOTE]
> Los IDs de los delimitadores son algo que se controla en la aplicación. En este ejemplo, hemos creado un esquema de nomenclatura que es secuencial en función del número de anclajes almacenados actualmente en la colección de delimitadores de la aplicación.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Cargar y almacenar en caché de forma asincrónica SpatialAnchorStore

Veamos cómo escribir una clase SampleSpatialAnchorHelper que ayuda a controlar esta persistencia, lo que incluye:
* Almacenar una colección de delimitadores en memoria, indexadas por una clave Platform::String.
* Carga de delimitadores de SpatialAnchorStore del sistema, que se mantiene independiente de la colección local en memoria.
* Guardar la colección local en memoria de delimitadores en SpatialAnchorStore cuando la aplicación decide hacerlo.

Aquí se muestra cómo guardar objetos [SpatialAnchor](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) en [SpatialAnchorStore.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)

Cuando se inicia la clase, se solicita SpatialAnchorStore de forma asincrónica. Esto implica la E/S del sistema, ya que la API carga el almacén de anclajes y esta API se hace asincrónica para que la E/S no sea de bloqueo.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Se le dará un spatialAnchorStore que puede usar para guardar los delimitadores. Se trata de un IMapView que asocia valores de clave que son Cadenas, con valores de datos que son SpatialAnchors. En nuestro código de ejemplo, almacenamos esto en una variable miembro de clase privada a la que se puede acceder a través de una función pública de nuestra clase auxiliar.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>No olvide enlazar los eventos de suspensión y reanudación para guardar y cargar el almacén de anclajes.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Guardar contenido en el almacén de anclajes

Cuando el sistema suspenda la aplicación, debe guardar los anclajes espaciales en el almacén de anclajes. También puede optar por guardar los delimitadores en el almacén de anclajes en otras ocasiones, ya que es necesario para la implementación de la aplicación.

Cuando esté listo para intentar guardar los delimitadores en memoria en SpatialAnchorStore, puede recorrer en bucle la colección e intentar guardar cada uno de ellos.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Carga de contenido desde el almacén de anclajes cuando se reanuda la aplicación

Puede restaurar los anclajes guardados en AnchorStore transfirándolos desde el IMapView del almacén de anclajes a su propia base de datos en memoria de SpatialAnchors cuando se reanude la aplicación o en cualquier momento.

Para restaurar delimitadores desde SpatialAnchorStore, restaure cada uno de los que le interese en su propia colección en memoria.

Necesita su propia base de datos en memoria de SpatialAnchors para asociar cadenas con los spatialanchors que cree. En nuestro código de ejemplo, elegimos usar un Windows::Foundation::Collections::IMap para almacenar los delimitadores, lo que facilita el uso del mismo valor de clave y datos para SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Es posible que un delimitador restaurado no sea localizable de inmediato. Por ejemplo, podría ser un delimitador en una sala independiente o en un edificio diferente por completo. Los anclajes recuperados de AnchorStore deben probarse para comprobar la capacidad de locatability antes de usarlos.

<br>

>[!NOTE]
>En este código de ejemplo, se recuperan todos los delimitadores de AnchorStore. Esto no es un requisito; La aplicación también podría elegir y elegir un subconjunto determinado de delimitadores mediante el uso de valores de clave string que sean significativos para la implementación.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Borrar el almacén de anclajes, cuando sea necesario

A veces, es necesario borrar el estado de la aplicación y escribir nuevos datos. A continuación se muestra cómo hacerlo con [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore).

Con nuestra clase auxiliar, es casi innecesario encapsular la función Clear. Elegimos hacerlo en nuestra implementación de ejemplo, porque nuestra clase auxiliar tiene la responsabilidad de ser propietaria de la instancia de SpatialAnchorStore.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Ejemplo: Relación de los sistemas de coordenadas de anclaje con los sistemas de coordenadas de marco de referencia estacionado

Supongamos que tiene un delimitador y desea relacionar algo en el sistema de coordenadas del delimitador con el SpatialStationaryReferenceFrame que ya está usando para el otro contenido. Puede usar [TryGetTransformTo para obtener](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) una transformación del sistema de coordenadas del delimitador al del marco de referencia estacionada:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Este proceso le resulta útil de dos maneras:
1. Indica si los dos marcos de referencia se pueden entender entre sí, y .
2. Si es así, proporciona una transformación para pasar directamente de un sistema de coordenadas al otro.

Con esta información, tiene un conocimiento de la relación espacial entre los objetos entre los dos marcos de referencia.

Para la representación, a menudo puede obtener mejores resultados agrupando objetos según su marco de referencia o delimitador original. Realice un pase de dibujo independiente para cada grupo. Las matrices de vistas son más precisas para los objetos con transformaciones de modelo que se crean inicialmente con el mismo sistema de coordenadas.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Creación de hologramas mediante un marco de referencia conectado al dispositivo

Hay ocasiones en las que desea [](../../design/coordinate-systems.md#attached-frame-of-reference) representar un holograma que permanece conectado a la ubicación del dispositivo, por ejemplo, un panel con información de depuración o un mensaje informativo cuando el dispositivo solo puede determinar su orientación y no su posición en el espacio. Para ello, usamos un marco adjunto de referencia.

La clase SpatialLocatorAttachedFrameOfReference define sistemas de coordenadas, que son relativos al dispositivo en lugar de al mundo real. Este marco tiene un encabezado fijo relativo al entorno del usuario que apunta en la dirección a la que se enfrentaba el usuario cuando se creó el marco de referencia. A partir de ese momento, todas las orientaciones de este marco de referencia son relativas a ese encabezado fijo, incluso cuando el usuario gira el dispositivo.

Por HoloLens, el origen del sistema de coordenadas de este marco se encuentra en el centro de rotación de la cabeza del usuario, de modo que su posición no se ve afectada por la rotación de la cabeza. La aplicación puede especificar un desplazamiento con respecto a este punto para colocar los hologramas delante del usuario.

Para obtener spatialLocatorAttachedFrameOfReference, use la clase SpatialLocator y llame a CreateAttachedFrameOfReferenceAtCurrentHeading.

Esto se aplica a todo el intervalo de Windows Mixed Reality dispositivos.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Uso de un marco de referencia asociado al dispositivo

En estas secciones se habla de lo que hemos cambiado en la plantilla de aplicación Windows Holographic para habilitar un marco de referencia conectado al dispositivo mediante esta API. Este holograma "conectado" funcionará junto con hologramas estacionados o anclados, y también se puede usar cuando el dispositivo no pueda encontrar temporalmente su posición en el mundo.

En primer lugar, cambiamos la plantilla para almacenar spatialLocatorAttachedFrameOfReference en lugar de spatialStationaryFrameOfReference:

Desde **HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Desde **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante la actualización, ahora obtenemos el sistema de coordenadas en la marca de tiempo obtenida de con la predicción de fotogramas.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Obtener una posición de puntero espacial y seguir la mirada del usuario

Queremos que nuestro holograma de ejemplo siga la mirada del [usuario,](../../design/gaze-and-commit.md)de forma similar a cómo el shell holográfico puede seguir la mirada del usuario. Para ello, es necesario obtener SpatialPointerPose de la misma marca de tiempo.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

SpatialPointerPose tiene la información necesaria para colocar el holograma según el [encabezado actual del usuario.](gaze-in-directx.md)

Para la comodidad del usuario, usamos la interpolación lineal ("lerp") para suavizar el cambio de posición durante un período de tiempo. Esto es más cómodo para el usuario que bloquear el holograma en su mirada. La alineación de la posición del holograma de etiqueta también nos permite estabilizar el holograma mediante la estabilización del movimiento. Si no lo hacemos, el usuario vería la vibración del holograma debido a lo que normalmente se considera movimientos imperceptibles de la cabeza del usuario.

Desde **StationaryQuadRenderer::P ositionHologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>En el caso de un panel de depuración, puede cambiar la posición del holograma hacia el lado para que no obstruya la vista. Este es un ejemplo de cómo podría hacerlo.

Para **StationaryQuadRenderer::P ositionHologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Girar el holograma para dar la cara a la cámara

No basta con colocar el holograma, que en este caso es un cuadrángrama. también debemos girar el objeto para enfrentarse al usuario. Esta rotación se produce en el espacio mundial, porque este tipo de movimiento permite que el holograma siga formando parte del entorno del usuario. El ajuste de espacio de vista no es tan cómodo porque el holograma se bloquea en la orientación de la pantalla. En ese caso, también tendría que interpolar entre las matrices de vista izquierda y derecha para adquirir una transformación de espacio de vista que no interrumpa la representación estéreo. En este caso, giramos en los ejes X y Z para enfrentarnos al usuario.

Desde **StationaryQuadRenderer::Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Representación del holograma conectado

En este ejemplo, también elegimos representar el holograma en el sistema de coordenadas de SpatialLocatorAttachedReferenceFrame, que es donde colocamos el holograma. (Si decidimos representar con otro sistema de coordenadas, tendríamos que adquirir una transformación del sistema de coordenadas del marco de referencia conectado al dispositivo a ese sistema de coordenadas).

Desde **HolographicTagAlongSampleMain::Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

Eso es todo. El holograma ahora "persiguirá" una posición de 2 metros delante de la dirección de la mirada del usuario.

>[!NOTE]
>En este ejemplo también se carga contenido adicional; vea StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Control de la pérdida de seguimiento

Cuando el dispositivo no se encuentra en el mundo, la aplicación experimenta "pérdida de seguimiento". Windows Mixed Reality aplicaciones deben ser capaces de controlar estas interrupciones en el sistema de seguimiento posicional. Estas interrupciones se pueden observar y las respuestas creadas mediante el evento LocatabilityChanged en el spatialLocator predeterminado.

Desde **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Cuando la aplicación recibe un evento LocatabilityChanged, puede cambiar el comportamiento según sea necesario. Por ejemplo, en el estado PositionalTrackingInhibited, la aplicación [](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) puede pausar el funcionamiento normal y representar un holograma de etiquetas que muestra un mensaje de advertencia.

La Windows aplicación Holográfica incluye un controlador LocatabilityChanged ya creado automáticamente. De forma predeterminada, muestra una advertencia en la consola de depuración cuando el seguimiento posicional no está disponible. Puede agregar código a este controlador para proporcionar una respuesta según sea necesario desde la aplicación.

Desde **AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>Asignación espacial

Las [API de asignación](spatial-mapping-in-directx.md) espacial usan sistemas de coordenadas para obtener transformaciones de modelo para mallas de superficie.

## <a name="see-also"></a>Consulte también
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* [Delimitadores espaciales](../../design/spatial-anchors.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)