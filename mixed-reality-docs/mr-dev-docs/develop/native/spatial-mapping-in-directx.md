---
title: Asignación espacial en DirectX
description: Obtenga información sobre cómo implementar la asignación espacial en la aplicación DirectX y cómo usar la aplicación de ejemplo de asignación espacial en el SDK de plataforma Windows universal.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows realidad mixta, asignación espacial, entorno, interacción, directx, winrt, api, código de ejemplo, UWP, SDK, tutorial
ms.openlocfilehash: e7f0735ea28703d3a9f18198901ffa5f06676f78b7b8962bf20824e05f793061
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198851"
---
# <a name="spatial-mapping-in-directx"></a>Asignación espacial en DirectX

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.

En este tema se [](../../design/spatial-mapping.md) describe cómo implementar la asignación espacial en la aplicación DirectX, incluida una explicación detallada de la aplicación de ejemplo de asignación espacial empaquetada con el SDK de plataforma Windows universal.

En este tema se usa código del ejemplo de código [holographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) para UWP.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de C++17 compatible con C++17, como se usa en la plantilla de proyecto holográfico de [C++.](creating-a-holographic-directx-project.md)  Los conceptos son equivalentes para un proyecto de C++/WinRT, aunque deberás traducir el código.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Asignación espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>Introducción al desarrollo de DirectX

El desarrollo de aplicaciones nativas para la asignación espacial usa las API [del Windows. Espacio de nombres Perception.Spatial.](/uwp/api/Windows.Perception.Spatial) Estas API le dan control total de la funcionalidad de asignación espacial, de la misma manera que Unity expone las API de [asignación espacial.](../unity/spatial-mapping-in-unity.md)

### <a name="perception-apis"></a>API de percepción

Los tipos principales proporcionados para el desarrollo de asignaciones espaciales son los siguientes:
* [SpatialSurfaceObserver proporciona](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) información sobre las superficies de las regiones de espacio especificadas por la aplicación cerca del usuario, en forma de objetos SpatialSurfaceInfo.
* [SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) describe una sola superficie espacial existente, incluido un identificador único, el volumen de límite y la hora del último cambio. Proporcionará un objeto SpatialSurfaceMesh de forma asincrónica a petición.
* [SpatialSurfaceMeshOptions contiene](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshOptions) parámetros que se usan para personalizar los objetos SpatialSurfaceMesh solicitados desde SpatialSurfaceInfo.
* [SpatialSurfaceMesh representa](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) los datos de malla para una sola superficie espacial. Los datos de las posiciones de los vértices, las normales de vértice y los índices de triángulo se encuentran en los objetos SpatialSurfaceMeshBuffer del miembro.
* [SpatialSurfaceMeshBuffer](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshBuffer) encapsula un único tipo de datos de malla.

Al desarrollar una aplicación con estas API, el flujo de programa básico tendrá este aspecto (como se muestra en la aplicación de ejemplo que se describe a continuación):
- **Configuración de SpatialSurfaceObserver**
  - Llame [a RequestAccessAsync](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver)para asegurarse de que el usuario ha concedido permiso para que la aplicación use las funcionalidades de asignación espacial del dispositivo.
  - Cree una instancia de un objeto SpatialSurfaceObserver.
  - Llame [a SetBoundingVolumes](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) para especificar las regiones de espacio en las que desea obtener información sobre las superficies espaciales. Puede modificar estas regiones en el futuro llamando de nuevo a esta función. Cada región se especifica mediante [SpatialBoundingVolume](/uwp/api/Windows.Perception.Spatial.SpatialBoundingVolume).
  - Regístrese para el evento [ObservedSurfacesChanged,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) que se activa cada vez que haya nueva información disponible sobre las superficies espaciales en las regiones de espacio que haya especificado.
- **Procesar eventos ObservedSurfacesChanged**
  - En el controlador de eventos, llame a [GetObservedSurfaces para](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) recibir un mapa de objetos SpatialSurfaceInfo. Con este mapa, puede actualizar los registros de las superficies espaciales [que existen en el entorno del usuario.](../../design/spatial-mapping.md#mesh-caching)
  - Para cada objeto SpatialSurfaceInfo, puede consultar [TryGetBounds](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) para determinar las extensiones [](../../design/coordinate-systems.md) espaciales de la superficie, expresadas en un sistema de coordenadas espaciales de su elección.
  - Si decide solicitar una malla para una superficie espacial, llame a [TryComputeLatestMeshAsync.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) Puede proporcionar opciones que especifiquen la densidad de los triángulos y el formato de los datos de malla devueltos.
- **Malla de recepción y proceso**
  - Cada llamada a TryComputeLatestMeshAsync devolverá asincrónicamente un objeto SpatialSurfaceMesh.
  - Desde este objeto, puede acceder a los objetos SpatialSurfaceMeshBuffer contenidos, lo que proporciona acceso a los índices de triángulo, las posiciones de vértice y las normales de vértice de la malla si los solicita. Estos datos estarán en un formato directamente compatible con las API [de Direct3D 11](/windows/win32/api/d3d11/nf-d3d11-id3d11device-createbuffer) que se usan para representar mallas.
  - Desde aquí, la aplicación [](../../design/spatial-mapping.md#mesh-processing) puede analizar o procesar opcionalmente los datos de malla y usarlos para la representación y la física de rayos [y colisiones.](../../design/spatial-mapping.md#raycasting-and-collision) [](../../design/spatial-mapping.md#rendering)
  - Un detalle importante que se debe tener en cuenta es que debe aplicar una escala a las posiciones de los vértices de malla (por ejemplo, en el sombreador de vértices usado para representar las mallas) para convertirlas de las unidades enteras optimizadas en las que se almacenan en el búfer, a metros. Puede recuperar esta escala llamando a [VertexPositionScale.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)

### <a name="troubleshooting"></a>Solución de problemas
* No olvide escalar las posiciones de los vértices de malla en el sombreador de vértices mediante la escala devuelta por [SpatialSurfaceMesh.VertexPositionScale.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Tutorial de ejemplo de código de asignación espacial

El [ejemplo de código](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) asignación espacial holográfica incluye código que puede usar para empezar a cargar mallas de superficie en la aplicación, incluida la infraestructura para administrar y representar mallas de superficie.

Ahora, se explica cómo agregar funcionalidad de asignación de superficie a la aplicación DirectX. Puede agregar este código al proyecto de plantilla de [aplicación Windows Holographic,](creating-a-holographic-directx-project.md) o bien puede continuar explorando el ejemplo de código mencionado anteriormente. Este ejemplo de código se basa en la plantilla Windows aplicación Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configuración de la aplicación para usar la funcionalidad spatialPerception

La aplicación puede usar la funcionalidad de asignación espacial. Esto es necesario porque la malla espacial es una representación del entorno del usuario, que se puede considerar datos privados. Declare esta funcionalidad en el archivo package.appxmanifest de la aplicación. Este es un ejemplo:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funcionalidad procede del espacio de **nombres uap2.** Para obtener acceso a este espacio de nombres en el manifiesto, inscluyéndolo como atributo *xlmns* en el elemento &lt; Package>. Este es un ejemplo:

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Comprobación de la compatibilidad con características de asignación espacial

Windows Mixed Reality admite una amplia gama de dispositivos, incluidos los dispositivos, que no admiten la asignación espacial. Si la aplicación puede usar la asignación espacial o debe usar la asignación espacial para proporcionar funcionalidad, debe comprobar que se admite la asignación espacial antes de intentar usarla. Por ejemplo, si la aplicación de realidad mixta requiere la asignación espacial, debería mostrar un mensaje en ese sentido si un usuario intenta ejecutarlo en un dispositivo sin asignación espacial. O bien, la aplicación puede representar su propio entorno virtual en lugar del entorno del usuario, lo que proporciona una experiencia similar a la que ocurriría si la asignación espacial estuviera disponible. En cualquier caso, esta API permite que la aplicación tenga en cuenta cuándo no va a obtener datos de asignación espacial y responder de la manera adecuada.

Para comprobar la compatibilidad con la asignación espacial del dispositivo actual, primero asegúrese de que el contrato de UWP está en el nivel 4 o superior y, a continuación, llame a SpatialSurfaceObserver::IsSupported(). Aquí se muestra cómo hacerlo en el contexto del ejemplo de código [asignación](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) espacial holográfica. El soporte técnico se comprueba justo antes de solicitar acceso.

La API SpatialSurfaceObserver::IsSupported() está disponible a partir de la versión 15063 del SDK. Si es necesario, redestinar el proyecto a la versión 15063 de la plataforma antes de usar esta API.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

Cuando el contrato de UWP es menor que el nivel 4, la aplicación debe continuar como si el dispositivo fuera capaz de realizar la asignación espacial.

### <a name="request-access-to-spatial-mapping-data"></a>Solicitud de acceso a los datos de asignación espacial

La aplicación debe solicitar permiso para acceder a los datos de asignación espacial antes de intentar crear observadores de superficie. Este es un ejemplo basado en nuestro ejemplo de código de Asignación de surface, con más detalles proporcionados más adelante en esta página:

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Creación de un observador de superficie

El espacio de nombres **Windows::P erception::Spatial::Surfaces** incluye la clase [SpatialSurfaceObserver,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) que observa uno o varios volúmenes especificados en [SpatialCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem). Use una [instancia de SpatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) para acceder a los datos de la malla de superficie en tiempo real.

Desde **AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Como se indicó en la sección anterior, debe solicitar acceso a los datos de asignación espacial antes de que la aplicación pueda usarlos. Este acceso se concede automáticamente en el HoloLens.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

A continuación, debe configurar el observador de superficie para observar un volumen de límite específico. En este caso, observamos un cuadro de 20 x 20 x 5 metros, centrado en el origen del sistema de coordenadas.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

En su lugar, puede establecer varios volúmenes de límite.

*Se trata de un seudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

También es posible usar otras formas de límite, como un frustum de vista o un rectángulo de selección que no está alineado en el eje.

*Se trata de un seudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Si la aplicación necesita hacer algo diferente cuando los datos de asignación de superficie no están disponibles, puede  escribir código para responder al caso en el que [SpatialPerceptionAccessStatus](/uwp/api/Windows.Perception.Spatial.SpatialPerceptionAccessStatus) no está permitido; por ejemplo, no se permitirá en equipos con dispositivos envolventes conectados porque esos dispositivos no tienen hardware para la asignación espacial. En el caso de estos dispositivos, debe basarse en la fase espacial para obtener información sobre el entorno del usuario y la configuración del dispositivo.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inicialización y actualización de la colección de malla de superficie

Si el observador de superficie se creó correctamente, podemos seguir inicializando nuestra colección de malla de superficie. Aquí, usamos la API del modelo de extracción para obtener el conjunto actual de superficies observadas de inmediato:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

También hay un modelo de inserción disponible para obtener datos de malla de superficie. Puede diseñar la aplicación para que use solo el modelo de extracción si lo elige, en cuyo caso sondeará los datos con tanta frecuencia (por ejemplo, una vez por fotograma) o durante un período de tiempo específico, como durante la configuración del juego. Si es así, el código anterior es lo que necesita.

En nuestro ejemplo de código, decidimos demostrar el uso de ambos modelos con fines empíricos. Aquí, nos suscribemos a un evento para recibir datos de malla de superficie actualizados cada vez que el sistema reconoce un cambio.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Nuestro ejemplo de código también está configurado para responder a estos eventos. Veamos cómo lo hacemos.

**NOTA:** Es posible que esta no sea la manera más eficaz para que la aplicación controle los datos de malla. Este código está escrito para mayor claridad y no está optimizado.

Los datos de la malla de superficie se proporcionan en un mapa de solo lectura que almacena objetos [SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) mediante [Platform::Guids como](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) valores de clave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Para procesar estos datos, buscamos primero los valores de clave que no están en nuestra colección. Más adelante en este tema se presentarán detalles sobre cómo se almacenan los datos en nuestra aplicación de ejemplo.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

También tenemos que quitar las mallas de superficie que están en nuestra colección de mallas de superficie, pero que ya no están en la colección del sistema. Para ello, es necesario hacer algo parecido a lo contrario de lo que se acaba de mostrar para agregar y actualizar mallas. recorremos en bucle la colección de la aplicación y compruebamos si el **GUID** que tenemos está en la colección del sistema. Si no está en la colección del sistema, la quitamos de la nuestra.

Desde nuestro controlador de eventos en AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Implementación de la poda de malla en RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Adquisición y uso de búferes de datos de malla de superficie

Obtener la información de la malla de superficie era tan fácil como extraer una recopilación de datos y procesar las actualizaciones de esa colección. Ahora, vamos a detallar cómo puede usar los datos.

En nuestro ejemplo de código, elegimos usar las mallas de superficie para la representación. Se trata de un escenario común para oclusión de hologramas detrás de superficies reales. También puede representar las mallas, o representar las versiones procesadas de ellas, para mostrar al usuario qué áreas de la sala se examinan antes de empezar a proporcionar funcionalidad de aplicación o juego.

El ejemplo de código inicia el proceso cuando recibe actualizaciones de surface mesh desde el controlador de eventos que se ha descrito en la sección anterior. La línea de código importante de esta función es la llamada para actualizar la malla de *superficie:* en este momento ya hemos procesado la información de la malla y estamos a punto de obtener los datos de vértices e índices para usarlos como creemos oportuno.

Desde RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

Nuestro código de ejemplo está diseñado para que una clase de datos, **SurfaceMesh,** controle el procesamiento y la representación de datos de malla. Estas mallas son de las **que RealtimeSurfaceMeshRenderer** mantiene realmente un mapa. Cada uno tiene una referencia a SpatialSurfaceMesh de la que provenía, por lo que puede usarla en cualquier momento que necesite acceder a los búferes de índice o vértice de malla u obtener una transformación para la malla. Por ahora, marcamos la malla como que necesita una actualización.

Desde SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

La próxima vez que se le pida a la malla que se dibuje, comprobará primero la marca. Si se necesita una actualización, los búferes de vértices e índices se actualizarán en la GPU.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

En primer lugar, se adquieren los búferes de datos sin procesar:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

A continuación, crearemos búferes de dispositivo Direct3D con los datos de malla proporcionados por el HoloLens:

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**NOTA:** Para la función auxiliar CreateDirectXBuffer usada en el fragmento de código anterior, consulte el ejemplo de código de asignación de Surface: SurfaceMesh.cpp, GetDataFromIBuffer.h. Ahora se ha completado la creación de recursos del dispositivo y se considera que la malla está cargada y lista para actualizarse y representarse.

### <a name="update-and-render-surface-meshes"></a>Actualización y representación de mallas de superficie

Nuestra clase SurfaceMesh tiene una función de actualización especializada. Cada [SpatialSurfaceMesh](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) tiene su propia transformación y nuestro ejemplo usa el sistema de coordenadas actual para **que spatialStationaryReferenceFrame** adquiera la transformación. A continuación, actualiza el búfer constante del modelo en la GPU.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Cuando es el momento de representar mallas de superficie, se hace algún trabajo de preparación antes de representar la colección. Configuramos la canalización del sombreador para la configuración de representación actual y configuramos la fase del ensamblador de entrada. La clase auxiliar de cámara holográfica **CameraResources.cpp** ya ha configurado el búfer constante de vista/proyección en este momento.

Desde **RealtimeSurfaceMeshRenderer::Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

Una vez hecho esto, se recorren en bucle las mallas y se les dice a cada uno que se dibuje a sí mismo. **NOTA:** Este código de ejemplo no está optimizado para usar ningún tipo de selección de frustum, pero debe incluir esta característica en la aplicación.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

Las mallas individuales son responsables de configurar el búfer de vértice e índice, el paso y el búfer constante de transformación del modelo. Al igual que con el cubo girando en la plantilla Windows aplicación Holográfica, se representa en búferes estereográficos mediante la creación de instancias.

Desde **SurfaceMesh::D raw**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>Opciones de representación con asignación de superficie

El ejemplo de código Asignación de superficie ofrece código para la representación solo de oclusión de datos de malla de superficie y para la representación en pantalla de datos de malla de superficie. La ruta de acceso que elija , o ambas, depende de la aplicación. En este documento se le recorrerán las dos configuraciones.

**Representación de búferes de oclusión para el efecto holográfico**

Empiece por borrar la vista de destino de representación de la cámara virtual actual.

Desde AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Se trata de un paso de "representación previa". Aquí, creamos un búfer de oclusión solicitando al representador de malla que represente solo la profundidad. En esta configuración, no adjuntamos una vista de destino de representación y el representador de malla establece la fase del sombreador de píxeles en **nullptr** para que la GPU no se preocupe de dibujar píxeles. La geometría se rasterizará en el búfer de profundidad y la canalización de gráficos se detendrá allí.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

Podemos dibujar hologramas con una prueba de profundidad adicional en el búfer de oclusión de Surface Mapping. En este ejemplo de código, representamos píxeles en el cubo de un color diferente si están detrás de una superficie.

Desde AppMain.cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

Basado en el código de SpecialEffectPixelShader.hlsl:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**Nota:** Para nuestra **rutina GatherDepthLess,** consulte el ejemplo de código de asignación de surface: SpecialEffectPixelShader.hlsl.

**Representación de datos de malla de superficie en la pantalla**

También podemos dibujar las mallas de superficie en los búferes de pantalla estéreo. Hemos elegido dibujar caras llenas con iluminación, pero puede dibujar tramas de cable, procesar mallas antes de la representación, aplicar un mapa de textura, y así sucesivamente.

Aquí, nuestro ejemplo de código indica al representador de malla que dibuje la colección. Esta vez no se especifica un paso de solo profundidad, se adjuntará un sombreador de píxeles y se completará la canalización de representación con los destinos especificados para la cámara virtual actual.

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Consulte también
* [Creación de un proyecto de DirectX holográfico](creating-a-holographic-directx-project.md)
* [Windows. Perception.Spatial API](/uwp/api/Windows.Perception.Spatial)