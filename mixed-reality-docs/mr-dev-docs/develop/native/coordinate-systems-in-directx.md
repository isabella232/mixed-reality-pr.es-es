---
title: Sistemas de coordenadas de DirectX
description: Obtenga información sobre los sistemas de coordenadas en DirectX y Mixed Reality con localizadores espaciales, fotogramas de referencia y delimitadores espaciales.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Realidad mixta, localizador espacial, marco de referencia espacial, sistema de coordenadas espaciales, fase espacial, código de ejemplo, estabilización de imágenes, delimitador espacial, almacén de delimitador espacial, pérdida de seguimiento, tutorial, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 055eff0bb04228cb0a19b9ea208bfc9c00ce2dbe
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006865"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="9db76-104">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="9db76-104">Coordinate systems in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="9db76-105">Este artículo está relacionado con las API nativas de WinRT heredadas.</span><span class="sxs-lookup"><span data-stu-id="9db76-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="9db76-106">En el caso de los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="9db76-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="9db76-107">[Los sistemas de coordenadas](../../design/coordinate-systems.md) constituyen la base para la comprensión espacial ofrecida por las API de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="9db76-107">[Coordinate systems](../../design/coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="9db76-108">Los dispositivos de la plataforma de VR de una sola habitación o de la primera sala establecen un sistema de coordenadas principal para su espacio de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="9db76-108">Today's seated VR or single-room VR devices establish one primary coordinate system for their tracked space.</span></span> <span data-ttu-id="9db76-109">Los dispositivos de realidad mixta como HoloLens están diseñados para entornos de gran tamaño sin definir, con el dispositivo que detecta y aprende sobre su entorno a medida que el usuario se recorre.</span><span class="sxs-lookup"><span data-stu-id="9db76-109">Mixed Reality devices like HoloLens are designed for large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="9db76-110">El dispositivo se adapta para mejorar continuamente el conocimiento sobre los salones del usuario, pero los sistemas de coordenadas cambian su relación entre sí a lo largo de la duración de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="9db76-110">The device adapts to continually improving knowledge about the user's rooms, but results in coordinate systems that change their relationship to one another over the apps lifetime.</span></span> <span data-ttu-id="9db76-111">Windows Mixed Reality es compatible con una amplia gama de dispositivos, desde los auriculares envolventes colocados a través de fotogramas de referencia conectados al mundo.</span><span class="sxs-lookup"><span data-stu-id="9db76-111">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="9db76-112">Los fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de C + +17 compatible con C++/WinRT tal y como se usa en la [plantilla de proyecto de C++ Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="9db76-112">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9db76-113">Los conceptos son equivalentes para un proyecto/WinRT de C++, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="9db76-113">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="9db76-114">Sistemas de coordenadas espaciales en Windows</span><span class="sxs-lookup"><span data-stu-id="9db76-114">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="9db76-115">El tipo básico que se usa para los sistemas de coordenadas del mundo real en Windows es el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="9db76-115">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="9db76-116">Una instancia de este tipo representa un sistema de coordenadas arbitrario, que proporciona un método para obtener los datos de la matriz de transformación que se pueden usar para transformar entre dos sistemas de coordenadas sin conocer los detalles de cada uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="9db76-116">An instance of this type represents an arbitrary coordinate system, providing a method for getting transformation matrix data that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="9db76-117">Los métodos que devuelven información espacial aceptarán un parámetro SpatialCoordinateSystem para permitirle decidir el sistema de coordenadas en el que es más útil para las coordenadas que se van a devolver.</span><span class="sxs-lookup"><span data-stu-id="9db76-117">Methods that return spatial information will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="9db76-118">La información espacial se representa como puntos, rayos o volúmenes en el entorno del usuario, y las unidades de estas coordenadas siempre estarán en metros.</span><span class="sxs-lookup"><span data-stu-id="9db76-118">Spatial information is represented as points, rays, or volumes in the user's surroundings, and the units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="9db76-119">Un SpatialCoordinateSystem tiene una relación dinámica con otros sistemas de coordenadas, incluidos los que representan la posición del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9db76-119">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="9db76-120">En cualquier momento, el dispositivo puede localizar algunos sistemas de coordenadas y no otros.</span><span class="sxs-lookup"><span data-stu-id="9db76-120">At any point, the device can locate some coordinate systems and not others.</span></span> <span data-ttu-id="9db76-121">Para la mayoría de los sistemas de coordenadas, la aplicación debe estar preparada para controlar los períodos de tiempo durante los cuales no se pueden encontrar.</span><span class="sxs-lookup"><span data-stu-id="9db76-121">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="9db76-122">La aplicación no debe crear SpatialCoordinateSystems directamente, sino que se deben usar a través de las API de percepción.</span><span class="sxs-lookup"><span data-stu-id="9db76-122">Your application shouldn't create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="9db76-123">Existen tres orígenes principales de sistemas de coordenadas en las API de percepción, cada uno de los cuales se asigna a un concepto descrito en la página [sistemas de coordenadas](../../design/coordinate-systems.md) :</span><span class="sxs-lookup"><span data-stu-id="9db76-123">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](../../design/coordinate-systems.md) page:</span></span>
* <span data-ttu-id="9db76-124">Para obtener un marco estacionario de referencia, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> u obtenga uno de la <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>actual.</span><span class="sxs-lookup"><span data-stu-id="9db76-124">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="9db76-125">Para obtener un delimitador espacial, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="9db76-125">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="9db76-126">Para obtener un marco de referencia asociado, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="9db76-126">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="9db76-127">Todos los sistemas de coordenadas devueltos por estos objetos son zurdos, con + y hacia arriba, + x a la derecha y + z hacia atrás.</span><span class="sxs-lookup"><span data-stu-id="9db76-127">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="9db76-128">Puede recordar en qué dirección apunta el eje z positivo apuntando los dedos de la mano izquierda o derecha en la dirección x positiva y enrollándose en la dirección y positiva.</span><span class="sxs-lookup"><span data-stu-id="9db76-128">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="9db76-129">La dirección en la que se encuentra el punto de control, ya sea hacia delante o fuera, es la dirección en la que apunta el eje z positivo para ese sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="9db76-129">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="9db76-130">En la ilustración siguiente se muestran estos dos sistemas de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="9db76-130">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="9db76-131">![Sistemas de coordenadas del lado izquierdo y derecho](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="9db76-131">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="9db76-132">*Sistemas de coordenadas del lado izquierdo y derecho*</span><span class="sxs-lookup"><span data-stu-id="9db76-132">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="9db76-133">Use la clase <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> para crear un marco fijo o adjunto de referencia para arrancar en un SpatialCoordinateSystem basado en la posición de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9db76-133">Use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference to bootstrap into a SpatialCoordinateSystem based on the HoloLens position.</span></span> <span data-ttu-id="9db76-134">Continúe con la siguiente sección para obtener más información sobre este proceso.</span><span class="sxs-lookup"><span data-stu-id="9db76-134">Continue to the next section to learn more about this process.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="9db76-135">Colocar hologramas en el mundo mediante una fase espacial</span><span class="sxs-lookup"><span data-stu-id="9db76-135">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="9db76-136">Se tiene acceso al sistema de coordenadas para los auriculares con forma de la realidad mixta de Windows con la que se usa la propiedad estática <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> .</span><span class="sxs-lookup"><span data-stu-id="9db76-136">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="9db76-137">Esta API proporciona:</span><span class="sxs-lookup"><span data-stu-id="9db76-137">This API provides:</span></span>

* <span data-ttu-id="9db76-138">Un sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="9db76-138">A coordinate system</span></span>
* <span data-ttu-id="9db76-139">Información sobre si el reproductor está sentado o es móvil</span><span class="sxs-lookup"><span data-stu-id="9db76-139">Information about whether the player is seated or mobile</span></span>
* <span data-ttu-id="9db76-140">El límite de un área segura para recorrer si el reproductor es móvil</span><span class="sxs-lookup"><span data-stu-id="9db76-140">The boundary of a safe area for walking around if the player is mobile</span></span>
* <span data-ttu-id="9db76-141">Una indicación de si el casco es direccional.</span><span class="sxs-lookup"><span data-stu-id="9db76-141">An indication of whether the headset is directional.</span></span> 
* <span data-ttu-id="9db76-142">Un controlador de eventos para las actualizaciones de la fase espacial.</span><span class="sxs-lookup"><span data-stu-id="9db76-142">An event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="9db76-143">En primer lugar, se obtiene la fase espacial y se suscriben las actualizaciones a ella:</span><span class="sxs-lookup"><span data-stu-id="9db76-143">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="9db76-144">Código para la **inicialización de la fase espacial**</span><span class="sxs-lookup"><span data-stu-id="9db76-144">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="9db76-145">En el método OnCurrentChanged, la aplicación debe inspeccionar la fase espacial y actualizar la experiencia del reproductor.</span><span class="sxs-lookup"><span data-stu-id="9db76-145">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience.</span></span> <span data-ttu-id="9db76-146">En este ejemplo, se proporciona una visualización del límite de fase y la posición de inicio especificada por el usuario, así como el intervalo de vista y rango de propiedades de movimiento de la fase.</span><span class="sxs-lookup"><span data-stu-id="9db76-146">In this example, we provide a visualization of the stage boundary and the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="9db76-147">También reviertemos a nuestro propio sistema de coordenadas estacionales, cuando no se puede proporcionar una fase.</span><span class="sxs-lookup"><span data-stu-id="9db76-147">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="9db76-148">Código para la actualización de la **fase espacial**</span><span class="sxs-lookup"><span data-stu-id="9db76-148">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="9db76-149">El conjunto de vértices que definen el límite de la fase se proporciona en el orden de las agujas del reloj.</span><span class="sxs-lookup"><span data-stu-id="9db76-149">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="9db76-150">El shell de Windows Mixed Reality dibuja una barrera en el límite cuando el usuario la trata, pero es posible que desee triangular el área que se puede examinar para sus propios fines.</span><span class="sxs-lookup"><span data-stu-id="9db76-150">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it, but you may want to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="9db76-151">El siguiente algoritmo se puede usar para triangular de la fase.</span><span class="sxs-lookup"><span data-stu-id="9db76-151">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="9db76-152">Código para **triangulación en la fase espacial**</span><span class="sxs-lookup"><span data-stu-id="9db76-152">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="9db76-153">Colocar hologramas en el mundo con un marco estacionario de referencia</span><span class="sxs-lookup"><span data-stu-id="9db76-153">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="9db76-154">La clase [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) representa un marco de referencia que [permanece estacionario](../../design/coordinate-systems.md#stationary-frame-of-reference) en relación con el entorno del usuario a medida que el usuario se desplaza.</span><span class="sxs-lookup"><span data-stu-id="9db76-154">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](../../design/coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="9db76-155">Este marco de referencia prioriza la conservación de las coordenadas al lado del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9db76-155">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="9db76-156">Un uso clave de una SpatialStationaryFrameOfReference es actuar como el sistema de coordenadas universal subyacente dentro de un motor de representación al representar hologramas.</span><span class="sxs-lookup"><span data-stu-id="9db76-156">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="9db76-157">Para obtener un SpatialStationaryFrameOfReference, use la clase [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) y llame a [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="9db76-157">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="9db76-158">En el código de plantilla de la aplicación Holographic de Windows:</span><span class="sxs-lookup"><span data-stu-id="9db76-158">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="9db76-159">Los fotogramas de referencia estacionarios están diseñados para proporcionar una posición con ajuste perfecto en relación con el espacio global.</span><span class="sxs-lookup"><span data-stu-id="9db76-159">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="9db76-160">Las posiciones individuales dentro de ese marco de referencia pueden desplazarse ligeramente.</span><span class="sxs-lookup"><span data-stu-id="9db76-160">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="9db76-161">Esto es normal, ya que el dispositivo aprende más sobre el entorno.</span><span class="sxs-lookup"><span data-stu-id="9db76-161">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="9db76-162">Cuando se requiere una ubicación precisa de hologramas individuales, se debe usar un SpatialAnchor para delimitar el holograma individual a una posición en el mundo real; por ejemplo, un punto que el usuario indica que sea de especial interés.</span><span class="sxs-lookup"><span data-stu-id="9db76-162">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="9db76-163">Las posiciones de anclaje no se desplazan, pero se pueden corregir. el delimitador usará la posición corregida a partir del fotograma siguiente después de que se haya realizado la corrección.</span><span class="sxs-lookup"><span data-stu-id="9db76-163">Anchor positions don't drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="9db76-164">Colocar hologramas en el mundo mediante delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="9db76-164">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="9db76-165">Los [delimitadores espaciales](../../design/coordinate-systems.md#spatial-anchors) son una excelente manera de colocar hologramas en un lugar específico del mundo real, con el sistema que garantiza que el delimitador permanece en su lugar con el tiempo.</span><span class="sxs-lookup"><span data-stu-id="9db76-165">[Spatial anchors](../../design/coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="9db76-166">En este tema se explica cómo crear y usar un delimitador y cómo trabajar con datos de delimitador.</span><span class="sxs-lookup"><span data-stu-id="9db76-166">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="9db76-167">Puede crear un SpatialAnchor en cualquier posición y orientación dentro del SpatialCoordinateSystem de su elección.</span><span class="sxs-lookup"><span data-stu-id="9db76-167">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="9db76-168">El dispositivo debe ser capaz de localizar ese sistema de coordenadas en el momento y el sistema no debe haber alcanzado el límite de delimitadores espaciales.</span><span class="sxs-lookup"><span data-stu-id="9db76-168">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="9db76-169">Una vez definido, el sistema de coordenadas de un SpatialAnchor se ajusta continuamente para mantener la posición y orientación precisas de su ubicación inicial.</span><span class="sxs-lookup"><span data-stu-id="9db76-169">Once defined, the coordinate system of a SpatialAnchor adjusts continually to keep the precise position and orientation of its initial location.</span></span> <span data-ttu-id="9db76-170">Después, puede usar esta SpatialAnchor para representar hologramas que aparecerán fijos en el entorno del usuario en esa ubicación exacta.</span><span class="sxs-lookup"><span data-stu-id="9db76-170">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="9db76-171">Los efectos de los ajustes que mantienen el anclaje en su lugar se amplían a medida que el delimitador aumenta.</span><span class="sxs-lookup"><span data-stu-id="9db76-171">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="9db76-172">Debe evitar la representación del contenido en relación con un delimitador que supere los 3 metros del origen de ese delimitador.</span><span class="sxs-lookup"><span data-stu-id="9db76-172">You should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="9db76-173">La propiedad [coordenadas](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) obtiene un sistema de coordenadas que le permite colocar el contenido en relación con el delimitador, con una aceleración aplicada cuando el dispositivo ajusta la ubicación precisa del delimitador.</span><span class="sxs-lookup"><span data-stu-id="9db76-173">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="9db76-174">Use la propiedad [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) y el evento [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) correspondiente para administrar estos ajustes.</span><span class="sxs-lookup"><span data-stu-id="9db76-174">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="9db76-175">Persistencia y uso compartido de delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="9db76-175">Persist and share spatial anchors</span></span>

<span data-ttu-id="9db76-176">Puede conservar un SpatialAnchor localmente mediante la clase [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) y, a continuación, recuperarlo en una sesión de aplicación futura en el mismo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9db76-176">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="9db76-177">Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a>, puede crear un delimitador de la nube durable desde un SpatialAnchor local, que la aplicación puede ubicar en varios dispositivos HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="9db76-177">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="9db76-178">Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="9db76-178">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location in real time.</span></span> 

<span data-ttu-id="9db76-179">También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para la persistencia asincrónica de hologramas en dispositivos de HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="9db76-179">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="9db76-180">Al compartir un delimitador espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="9db76-180">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="9db76-181">Para empezar a crear experiencias compartidas en la aplicación de HoloLens, pruebe la guía de inicio rápido de HoloLens de 5 minutos de <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">delimitadores espaciales de Azure</a>.</span><span class="sxs-lookup"><span data-stu-id="9db76-181">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="9db76-182">Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">crear y buscar delimitadores en HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="9db76-182">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="9db76-183">También hay tutoriales disponibles para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , lo que le permite compartir los mismos delimitadores en todos los dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9db76-183">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="9db76-184">Crear SpatialAnchors para contenido holográfica</span><span class="sxs-lookup"><span data-stu-id="9db76-184">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="9db76-185">En este ejemplo de código, se modificó la plantilla de aplicación de Windows Holographic para crear delimitadores cuando se detecta el gesto **presionado** .</span><span class="sxs-lookup"><span data-stu-id="9db76-185">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="9db76-186">Después, el cubo se coloca en el delimitador durante la fase de representación.</span><span class="sxs-lookup"><span data-stu-id="9db76-186">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="9db76-187">Dado que la clase auxiliar admite varios delimitadores, podemos colocar tantos cubos como deseen usar este ejemplo de código.</span><span class="sxs-lookup"><span data-stu-id="9db76-187">Since multiple anchors are supported by the helper class, we can place as many cubes as we want to use this code sample!</span></span>

> [!NOTE]
> <span data-ttu-id="9db76-188">Los identificadores de los delimitadores son algo que usted controla en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9db76-188">The IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="9db76-189">En este ejemplo, se ha creado un esquema de nomenclatura que es secuencial en función del número de delimitadores almacenados actualmente en la colección de delimitadores de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9db76-189">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="9db76-190">Cargar y almacenar en caché de forma asincrónica el SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9db76-190">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="9db76-191">Veamos cómo escribir una clase SampleSpatialAnchorHelper que ayude a controlar esta persistencia, incluidos:</span><span class="sxs-lookup"><span data-stu-id="9db76-191">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="9db76-192">Almacenar una colección de delimitadores en memoria, indizada por una clave Platform:: String.</span><span class="sxs-lookup"><span data-stu-id="9db76-192">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="9db76-193">Cargar delimitadores de la SpatialAnchorStore del sistema, que se mantiene independiente de la colección en memoria local.</span><span class="sxs-lookup"><span data-stu-id="9db76-193">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="9db76-194">Guardar la colección local en memoria de los delimitadores en el SpatialAnchorStore cuando la aplicación decida hacerlo.</span><span class="sxs-lookup"><span data-stu-id="9db76-194">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="9db76-195">Aquí se muestra cómo guardar objetos [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) en [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="9db76-195">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="9db76-196">Cuando se inicia la clase, se solicita SpatialAnchorStore de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="9db76-196">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="9db76-197">Esto implica la e/s del sistema, ya que la API carga el almacén de delimitadores y esta API se hace asincrónica para que la e/s no sea de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="9db76-197">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="9db76-198">Se le proporcionará un SpatialAnchorStore que puede usar para guardar los delimitadores.</span><span class="sxs-lookup"><span data-stu-id="9db76-198">You'll be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="9db76-199">Se trata de un IMapView que asocia valores de clave que son cadenas, con valores de datos que son SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="9db76-199">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="9db76-200">En el código de ejemplo, se almacena en una variable de miembro de clase privada que es accesible a través de una función pública de nuestra clase auxiliar.</span><span class="sxs-lookup"><span data-stu-id="9db76-200">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="9db76-201">No olvide enlazar los eventos de suspensión y reanudación para guardar y cargar el almacén delimitado.</span><span class="sxs-lookup"><span data-stu-id="9db76-201">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="9db76-202">Guardar el contenido en el almacén delimitado</span><span class="sxs-lookup"><span data-stu-id="9db76-202">Save content to the anchor store</span></span>

<span data-ttu-id="9db76-203">Cuando el sistema suspende la aplicación, debe guardar los anclajes espaciales en el almacén delimitado.</span><span class="sxs-lookup"><span data-stu-id="9db76-203">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="9db76-204">También puede optar por guardar los delimitadores en el almacén de delimitadores en otros momentos, según considere que es necesario para la implementación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9db76-204">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="9db76-205">Cuando esté listo para intentar guardar los delimitadores en memoria en SpatialAnchorStore, puede crear un bucle a través de la colección e intentar guardar cada una de ellas.</span><span class="sxs-lookup"><span data-stu-id="9db76-205">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="9db76-206">Carga de contenido desde el almacén delimitado cuando se reanuda la aplicación</span><span class="sxs-lookup"><span data-stu-id="9db76-206">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="9db76-207">Puede restaurar los delimitadores guardados en el AnchorStore si los transfiere del IMapView del almacén delimitador a su propia base de datos en memoria de SpatialAnchors cuando se reanuda la aplicación o en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="9db76-207">You can restore saved anchors in the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors when your app resumes or at any time.</span></span>

<span data-ttu-id="9db76-208">Para restaurar los delimitadores de SpatialAnchorStore, restaure cada uno que le interese a su propia colección en memoria.</span><span class="sxs-lookup"><span data-stu-id="9db76-208">To restore anchors from the SpatialAnchorStore, restore each one that you're interested in to your own in-memory collection.</span></span>

<span data-ttu-id="9db76-209">Necesita su propia base de datos en memoria de SpatialAnchors para asociar cadenas con el SpatialAnchors que cree.</span><span class="sxs-lookup"><span data-stu-id="9db76-209">You need your own in-memory database of SpatialAnchors to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="9db76-210">En el código de ejemplo, elegimos usar un Windows:: Foundation:: Collections:: IMap para almacenar los delimitadores, lo que facilita el uso de la misma clave y el mismo valor de datos para el SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="9db76-210">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="9db76-211">Un delimitador que se restaure podría no ser localizable de inmediato.</span><span class="sxs-lookup"><span data-stu-id="9db76-211">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="9db76-212">Por ejemplo, podría tratarse de un delimitador en un salón independiente o en un edificio diferente.</span><span class="sxs-lookup"><span data-stu-id="9db76-212">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="9db76-213">Los delimitadores recuperados de AnchorStore deben probarse para encontrar la ubicación antes de usarlos.</span><span class="sxs-lookup"><span data-stu-id="9db76-213">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="9db76-214">En este código de ejemplo, recuperamos todos los delimitadores de AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="9db76-214">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="9db76-215">Esto no es un requisito; también podría elegir un determinado subconjunto de delimitadores usando valores de clave de cadena que son significativos para su implementación.</span><span class="sxs-lookup"><span data-stu-id="9db76-215">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="9db76-216">Borrar el almacén delimitador, cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="9db76-216">Clear the anchor store, when needed</span></span>

<span data-ttu-id="9db76-217">A veces, debe borrar el estado de la aplicación y escribir datos nuevos.</span><span class="sxs-lookup"><span data-stu-id="9db76-217">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="9db76-218">Aquí se muestra cómo hacerlo con el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="9db76-218">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="9db76-219">Con nuestra clase auxiliar, casi innecesaria para encapsular la función Clear.</span><span class="sxs-lookup"><span data-stu-id="9db76-219">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="9db76-220">Decidimos hacerlo en nuestra implementación de ejemplo, porque a nuestra clase auxiliar se le da la responsabilidad de poseer la instancia de SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="9db76-220">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="9db76-221">Ejemplo: vinculación de sistemas de coordenadas de anclaje a sistemas de coordenadas de fotogramas de referencia estacionales</span><span class="sxs-lookup"><span data-stu-id="9db76-221">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="9db76-222">Supongamos que tiene un delimitador y quiere relacionar algo en el sistema de coordenadas del delimitador con el SpatialStationaryReferenceFrame que ya está usando para el otro contenido.</span><span class="sxs-lookup"><span data-stu-id="9db76-222">Let's say you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame you’re already using for your other content.</span></span> <span data-ttu-id="9db76-223">Puede usar [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) para obtener una transformación del sistema de coordenadas del delimitador al marco de referencia estacionaria:</span><span class="sxs-lookup"><span data-stu-id="9db76-223">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to get a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="9db76-224">Este proceso resulta útil de dos maneras:</span><span class="sxs-lookup"><span data-stu-id="9db76-224">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="9db76-225">Indica si los dos fotogramas de referencia se pueden entender entre sí, y;</span><span class="sxs-lookup"><span data-stu-id="9db76-225">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="9db76-226">En ese caso, proporciona una transformación para pasar directamente de un sistema de coordenadas a otro.</span><span class="sxs-lookup"><span data-stu-id="9db76-226">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="9db76-227">Con esta información, se conoce la relación espacial entre los objetos entre los dos fotogramas de referencia.</span><span class="sxs-lookup"><span data-stu-id="9db76-227">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="9db76-228">Para la representación, a menudo puede obtener mejores resultados mediante la agrupación de objetos según su marco de referencia original o el delimitador.</span><span class="sxs-lookup"><span data-stu-id="9db76-228">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="9db76-229">Realice un paso de dibujo independiente para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="9db76-229">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="9db76-230">Las matrices de vistas son más precisas para los objetos con transformaciones del modelo que se crean Inicialmente mediante el mismo sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="9db76-230">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="9db76-231">Crear hologramas mediante un marco de referencia conectado al dispositivo</span><span class="sxs-lookup"><span data-stu-id="9db76-231">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="9db76-232">Hay ocasiones en las que desea representar un holograma que [permanece adjunto](../../design/coordinate-systems.md#attached-frame-of-reference) a la ubicación del dispositivo, por ejemplo un panel con información de depuración o un mensaje informativo cuando el dispositivo solo puede determinar su orientación y no su posición en el espacio.</span><span class="sxs-lookup"><span data-stu-id="9db76-232">There are times when you want to render a hologram that [remains attached](../../design/coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="9db76-233">Para ello, usamos un marco de referencia asociado.</span><span class="sxs-lookup"><span data-stu-id="9db76-233">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="9db76-234">La clase SpatialLocatorAttachedFrameOfReference define los sistemas de coordenadas, que son relativos al dispositivo en lugar de al mundo real.</span><span class="sxs-lookup"><span data-stu-id="9db76-234">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems, which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="9db76-235">Este marco tiene un encabezado fijo en relación con el entorno del usuario que apunta a la dirección a la que estaba situado el usuario cuando se creó el marco de referencia.</span><span class="sxs-lookup"><span data-stu-id="9db76-235">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="9db76-236">A partir de entonces, todas las orientaciones de este marco de referencia son relativas a ese título fijo, incluso cuando el usuario gira el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9db76-236">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="9db76-237">En el caso de HoloLens, el origen del sistema de coordenadas de este fotograma se encuentra en el centro de rotación del encabezado del usuario, de modo que su posición no se ve afectada por la rotación del cabezal.</span><span class="sxs-lookup"><span data-stu-id="9db76-237">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="9db76-238">La aplicación puede especificar un desplazamiento relativo a este punto para colocar los hologramas delante del usuario.</span><span class="sxs-lookup"><span data-stu-id="9db76-238">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="9db76-239">Para obtener un SpatialLocatorAttachedFrameOfReference, use la clase SpatialLocator y llame a CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="9db76-239">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="9db76-240">Esto se aplica a todo el intervalo de dispositivos de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="9db76-240">This applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="9db76-241">Uso de un marco de referencia conectado al dispositivo</span><span class="sxs-lookup"><span data-stu-id="9db76-241">Use a reference frame attached to the device</span></span>

<span data-ttu-id="9db76-242">En estas secciones se habla sobre lo que hemos cambiado en la plantilla de aplicación de Windows Holographic para habilitar un marco de referencia de dispositivo de referencia mediante esta API.</span><span class="sxs-lookup"><span data-stu-id="9db76-242">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="9db76-243">Este holograma "adjunto" funcionará junto con los hologramas fijos o anclados y también se puede usar cuando el dispositivo no pueda encontrar su posición en el mundo temporalmente.</span><span class="sxs-lookup"><span data-stu-id="9db76-243">This "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="9db76-244">En primer lugar, hemos cambiado la plantilla para almacenar un SpatialLocatorAttachedFrameOfReference en lugar de un SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="9db76-244">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="9db76-245">Desde **HolographicTagAlongSampleMain. h**:</span><span class="sxs-lookup"><span data-stu-id="9db76-245">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="9db76-246">Desde **HolographicTagAlongSampleMain. cpp**:</span><span class="sxs-lookup"><span data-stu-id="9db76-246">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="9db76-247">Durante la actualización, ahora obtenemos el sistema de coordenadas en la marca de tiempo obtenida de con la predicción de fotogramas.</span><span class="sxs-lookup"><span data-stu-id="9db76-247">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="9db76-248">Obtener una pose de puntero espacial y seguir el</span><span class="sxs-lookup"><span data-stu-id="9db76-248">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="9db76-249">Queremos que el holograma de ejemplo siga la [mirada](../../design/gaze-and-commit.md)del usuario, de forma similar a cómo el shell holográfica puede seguir a la mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="9db76-249">We want our example hologram to follow the user's [gaze](../../design/gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="9db76-250">Para ello, es necesario obtener el SpatialPointerPose de la misma marca de tiempo.</span><span class="sxs-lookup"><span data-stu-id="9db76-250">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="9db76-251">Este SpatialPointerPose tiene la información necesaria para colocar el holograma según el [encabezado actual del usuario](gaze-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="9db76-251">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="9db76-252">Para la comodidad del usuario, usamos la interpolación lineal ("lerp") para suavizar el cambio en la posición en un período de tiempo.</span><span class="sxs-lookup"><span data-stu-id="9db76-252">For user comfort, we use linear interpolation ("lerp") to smooth the change in position over a period of time.</span></span> <span data-ttu-id="9db76-253">Esto es más cómodo para el usuario que bloquear el holograma a su mirada.</span><span class="sxs-lookup"><span data-stu-id="9db76-253">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="9db76-254">Lerping la posición de la etiqueta en el holograma también nos permite estabilizar el holograma mediante la amortiguación del movimiento.</span><span class="sxs-lookup"><span data-stu-id="9db76-254">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement.</span></span> <span data-ttu-id="9db76-255">Si no hacemos esto, el usuario verá la vibración del holograma debido a lo que se suele considerar como movimientos imperceptibles del encabezado del usuario.</span><span class="sxs-lookup"><span data-stu-id="9db76-255">If we didn't do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="9db76-256">Desde **StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="9db76-256">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="9db76-257">En el caso de un panel de depuración, puede optar por volver a colocar el holograma en la parte lateral un poco para que no obstruya la vista.</span><span class="sxs-lookup"><span data-stu-id="9db76-257">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it doesn't obstruct your view.</span></span> <span data-ttu-id="9db76-258">Este es un ejemplo de cómo podría hacerlo.</span><span class="sxs-lookup"><span data-stu-id="9db76-258">Here's an example of how you might do that.</span></span>

<span data-ttu-id="9db76-259">Para **StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="9db76-259">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="9db76-260">Girar el holograma para que se enfrente a la cámara</span><span class="sxs-lookup"><span data-stu-id="9db76-260">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="9db76-261">No basta con colocar el holograma, que en este caso es un cuádruple; También debemos girar el objeto para que se enfrente al usuario.</span><span class="sxs-lookup"><span data-stu-id="9db76-261">It isn't enough to position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="9db76-262">Esta rotación se produce en el espacio universal, ya que este tipo de cartelera permite que el holograma siga siendo parte del entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="9db76-262">This rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="9db76-263">La cartelera de espacio de vista no es tan cómoda porque el holograma se bloquea a la orientación de la pantalla. en ese caso, también tendría que interpolar entre las matrices de la vista izquierda y derecha para adquirir una transformación de la cartelera de espacio de vista que no interrumpa la representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="9db76-263">View-space billboarding isn't as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices to acquire a view-space billboard transform that doesn't disrupt stereo rendering.</span></span> <span data-ttu-id="9db76-264">Aquí, giramos en los ejes X y Z para que se enfrente al usuario.</span><span class="sxs-lookup"><span data-stu-id="9db76-264">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="9db76-265">Desde **StationaryQuadRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="9db76-265">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="9db76-266">Representar el holograma adjunto</span><span class="sxs-lookup"><span data-stu-id="9db76-266">Render the attached hologram</span></span>

<span data-ttu-id="9db76-267">En este ejemplo, también optamos por representar el holograma en el sistema de coordenadas de SpatialLocatorAttachedReferenceFrame, que es donde colocamos el holograma.</span><span class="sxs-lookup"><span data-stu-id="9db76-267">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="9db76-268">(Si se hubiera decidido representar con otro sistema de coordenadas, es necesario adquirir una transformación del sistema de coordenadas del fotograma de referencia conectado al dispositivo a ese sistema de coordenadas).</span><span class="sxs-lookup"><span data-stu-id="9db76-268">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="9db76-269">Desde **HolographicTagAlongSampleMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="9db76-269">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="9db76-270">Eso es todo.</span><span class="sxs-lookup"><span data-stu-id="9db76-270">That's it!</span></span> <span data-ttu-id="9db76-271">Ahora, el holograma "persecución" es una posición de 2 metros delante de la dirección del usuario.</span><span class="sxs-lookup"><span data-stu-id="9db76-271">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="9db76-272">En este ejemplo también se carga contenido adicional; Consulte StationaryQuadRenderer. cpp.</span><span class="sxs-lookup"><span data-stu-id="9db76-272">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="9db76-273">Control de la pérdida de seguimiento</span><span class="sxs-lookup"><span data-stu-id="9db76-273">Handling tracking loss</span></span>

<span data-ttu-id="9db76-274">Cuando el dispositivo no se encuentra en el mundo, la aplicación experimenta "pérdida de seguimiento".</span><span class="sxs-lookup"><span data-stu-id="9db76-274">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="9db76-275">Las aplicaciones de Windows Mixed Reality deben ser capaces de controlar tales interrupciones en el sistema de seguimiento posicional.</span><span class="sxs-lookup"><span data-stu-id="9db76-275">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="9db76-276">Estas interrupciones se pueden observar y las respuestas se crean mediante el evento LocatabilityChanged en el SpatialLocator predeterminado.</span><span class="sxs-lookup"><span data-stu-id="9db76-276">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="9db76-277">Desde **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="9db76-277">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="9db76-278">Cuando la aplicación recibe un evento LocatabilityChanged, puede cambiar el comportamiento según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="9db76-278">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="9db76-279">Por ejemplo, en el estado PositionalTrackingInhibited, la aplicación puede pausar el funcionamiento normal y representar una [etiqueta a lo largo](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) de un holograma que muestre un mensaje de advertencia.</span><span class="sxs-lookup"><span data-stu-id="9db76-279">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="9db76-280">La plantilla de aplicación de Windows Holographic incluye un controlador LocatabilityChanged que ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="9db76-280">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="9db76-281">De forma predeterminada, se muestra una advertencia en la consola de depuración cuando el seguimiento posicional no está disponible.</span><span class="sxs-lookup"><span data-stu-id="9db76-281">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="9db76-282">Puede agregar código a este controlador para proporcionar una respuesta según sea necesario desde la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9db76-282">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="9db76-283">Desde **AppMain. cpp:**</span><span class="sxs-lookup"><span data-stu-id="9db76-283">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="9db76-284">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="9db76-284">Spatial mapping</span></span>

<span data-ttu-id="9db76-285">Las API de [asignación espacial](spatial-mapping-in-directx.md) hacen uso de los sistemas de coordenadas para obtener las transformaciones del modelo para las mallas de superficie.</span><span class="sxs-lookup"><span data-stu-id="9db76-285">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="9db76-286">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9db76-286">See also</span></span>
* [<span data-ttu-id="9db76-287">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="9db76-287">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="9db76-288">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="9db76-288">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* <span data-ttu-id="9db76-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="9db76-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="9db76-290">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="9db76-290">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="9db76-291">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="9db76-291">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="9db76-292">Asignación espacial en DirectX</span><span class="sxs-lookup"><span data-stu-id="9db76-292">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
