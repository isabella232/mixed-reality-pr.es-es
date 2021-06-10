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
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="90b8b-104">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="90b8b-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="90b8b-105">[La asignación](../../design/spatial-mapping.md) espacial permite recuperar mallas de triángulo que representan las superficies del mundo alrededor de un dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="90b8b-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="90b8b-106">Puede usar los datos de la superficie para la selección de ubicación, oclusión y análisis de sala para proporcionar a los proyectos de Unity una mayor cantidad de inmersiones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="90b8b-107">Unity incluye compatibilidad completa con la asignación espacial, que se expone a los desarrolladores de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="90b8b-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>

1. <span data-ttu-id="90b8b-108">Componentes de asignación espacial disponibles en MixedRealityToolkit, que proporcionan una ruta de acceso cómoda y rápida para empezar a trabajar con la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="90b8b-109">API de asignación espacial de nivel inferior, que proporcionan control total y permiten una personalización más sofisticada específica de la aplicación</span><span class="sxs-lookup"><span data-stu-id="90b8b-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="90b8b-110">Para usar la asignación espacial en la aplicación, la funcionalidad spatialPerception debe establecerse en AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="90b8b-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="90b8b-111">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="90b8b-111">Device support</span></span>

| <span data-ttu-id="90b8b-112">Característica</span><span class="sxs-lookup"><span data-stu-id="90b8b-112">Feature</span></span> | [<span data-ttu-id="90b8b-113">HoloLens (primera generación)</span><span class="sxs-lookup"><span data-stu-id="90b8b-113">HoloLens (first gen)</span></span>](/hololens/hololens1-hardware) | [<span data-ttu-id="90b8b-114">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="90b8b-114">HoloLens 2</span></span>](/hololens/hololens2-hardware) | [<span data-ttu-id="90b8b-115">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="90b8b-115">Immersive headsets</span></span>](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| <span data-ttu-id="90b8b-116">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="90b8b-116">Spatial mapping</span></span> | <span data-ttu-id="90b8b-117">✔️</span><span class="sxs-lookup"><span data-stu-id="90b8b-117">✔️</span></span> | <span data-ttu-id="90b8b-118">✔️</span><span class="sxs-lookup"><span data-stu-id="90b8b-118">✔️</span></span> | ❌ |

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="90b8b-119">Establecimiento de la funcionalidad SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="90b8b-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="90b8b-120">Para que una aplicación consuma datos de asignación espacial, se debe habilitar la funcionalidad SpatialPerception.</span><span class="sxs-lookup"><span data-stu-id="90b8b-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="90b8b-121">Habilitación de la funcionalidad SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="90b8b-121">How to enable the SpatialPerception capability:</span></span>

1. <span data-ttu-id="90b8b-122">En el Editor de Unity, abra el **panel "Configuración** del reproductor" (Editar > project settings > Player)</span><span class="sxs-lookup"><span data-stu-id="90b8b-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="90b8b-123">Seleccione en la **pestaña "Tienda Windows".**</span><span class="sxs-lookup"><span data-stu-id="90b8b-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="90b8b-124">Expanda **"Configuración de publicación"** y compruebe la **funcionalidad "SpatialPerception"** en la **lista "Funcionalidades".**</span><span class="sxs-lookup"><span data-stu-id="90b8b-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="90b8b-125">Si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o establecer manualmente esta funcionalidad en [AppxManifest](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)en Visual Studio .</span><span class="sxs-lookup"><span data-stu-id="90b8b-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="90b8b-126">La asignación espacial también requiere maxVersionTested de al menos 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="90b8b-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>

1. <span data-ttu-id="90b8b-127">En Visual Studio, haga clic con el botón derecho en **Package.appxmanifest** en la Explorador de soluciones y seleccione **Ver código.**</span><span class="sxs-lookup"><span data-stu-id="90b8b-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="90b8b-128">Busque la línea que especifica **TargetDeviceFamily** y cambie **MaxVersionTested="10.0.10240.0"** a **MaxVersionTested="10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="90b8b-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="90b8b-129">**Guarde** package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="90b8b-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="90b8b-130">Introducción a los componentes de asignación espacial integrados de Unity</span><span class="sxs-lookup"><span data-stu-id="90b8b-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="90b8b-131">Unity ofrece dos componentes para agregar fácilmente la asignación espacial a la aplicación: Representador de **asignación espacial** y **Colisionador de asignación espacial.**</span><span class="sxs-lookup"><span data-stu-id="90b8b-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="90b8b-132">Representador de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="90b8b-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="90b8b-133">El representador de asignación espacial permite la visualización de la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Representador de asignación espacial en Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="90b8b-135">Colisionador de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="90b8b-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="90b8b-136">El colisionador de asignación espacial permite la interacción de contenido holográfico (o carácter), como la física, con la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Colisionador de asignación espacial en Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="90b8b-138">Uso de los componentes de asignación espacial integrados</span><span class="sxs-lookup"><span data-stu-id="90b8b-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="90b8b-139">Puede agregar ambos componentes a la aplicación si quiere visualizar e interactuar con superficies físicas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="90b8b-140">Para usar estos dos componentes en la aplicación de Unity:</span><span class="sxs-lookup"><span data-stu-id="90b8b-140">To use these two components in your Unity app:</span></span>

1. <span data-ttu-id="90b8b-141">Seleccione un GameObject en el centro del área en la que desea detectar mallas de superficie espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="90b8b-142">En la ventana Inspector, **agregue el colisionador** de  >  **asignación espacial XR**  >  **de componente** o **el representador de asignación espacial**.</span><span class="sxs-lookup"><span data-stu-id="90b8b-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="90b8b-143">Puede encontrar más detalles sobre cómo usar estos componentes en el sitio <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">de documentación de Unity.</a></span><span class="sxs-lookup"><span data-stu-id="90b8b-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="90b8b-144">Ir más allá de los componentes de asignación espacial integrados</span><span class="sxs-lookup"><span data-stu-id="90b8b-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="90b8b-145">Estos componentes hacen que sea fácil arrastrar y colocar para empezar a trabajar con la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="90b8b-146">Si desea ir más allá, hay dos rutas de acceso principales que explorar:</span><span class="sxs-lookup"><span data-stu-id="90b8b-146">When you want to go further, there are two main paths to explore:</span></span>

* <span data-ttu-id="90b8b-147">Para realizar su propio procesamiento de malla de nivel inferior, consulte la sección siguiente sobre la API de script de asignación espacial de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="90b8b-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="90b8b-148">Para realizar análisis de malla de nivel superior, consulte la sección siguiente sobre la biblioteca SpatialUnderstanding en <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="90b8b-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="90b8b-149">Uso de la API de asignación espacial de Unity de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="90b8b-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="90b8b-150">Si necesita más control que los componentes Representador de asignación espacial y Colisionador de asignación espacial, use las API de asignación espacial de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="90b8b-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="90b8b-151">**Espacio de nombres:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="90b8b-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="90b8b-152">**Tipos:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="90b8b-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="90b8b-153">Hemos descrito el flujo sugerido para una aplicación que usa las API de asignación espacial en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="90b8b-154">Configuración de SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="90b8b-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="90b8b-155">Cree una instancia de un objeto SurfaceObserver para cada región de espacio definida por la aplicación para la que necesite datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

<span data-ttu-id="90b8b-156">Especifique la región de espacio para la que cada objeto SurfaceObserver proporcionará datos llamando a SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="90b8b-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="90b8b-157">Puede volver a definir la región del espacio en el futuro simplemente llamando a uno de estos métodos de nuevo.</span><span class="sxs-lookup"><span data-stu-id="90b8b-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="90b8b-158">Al llamar a SurfaceObserver.Update(), debe proporcionar un controlador para cada superficie espacial de la región de espacio de SurfaceObserver para la que el sistema de asignación espacial tiene información nueva.</span><span class="sxs-lookup"><span data-stu-id="90b8b-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="90b8b-159">El controlador recibe, para una superficie espacial:</span><span class="sxs-lookup"><span data-stu-id="90b8b-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a><span data-ttu-id="90b8b-160">Control de cambios de superficie</span><span class="sxs-lookup"><span data-stu-id="90b8b-160">Handling Surface Changes</span></span>

<span data-ttu-id="90b8b-161">Hay varios casos principales para controlar: agregados y actualizados, que pueden usar la misma ruta de acceso de código y quitarse.</span><span class="sxs-lookup"><span data-stu-id="90b8b-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>

* <span data-ttu-id="90b8b-162">En los casos agregados y actualizados, agregamos u obtienemos el Objeto GameObject que representa esta malla desde el diccionario, creamos una estructura SurfaceData con los componentes necesarios y, a continuación, llamamos a RequestMeshDataAsync para rellenar el GameObject con los datos de malla y la posición en la escena.</span><span class="sxs-lookup"><span data-stu-id="90b8b-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="90b8b-163">En el caso quitado, se quita el Objeto GameObject que representa esta malla del diccionario y se destruye.</span><span class="sxs-lookup"><span data-stu-id="90b8b-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="90b8b-164">Control de datos listo</span><span class="sxs-lookup"><span data-stu-id="90b8b-164">Handling Data Ready</span></span>

<span data-ttu-id="90b8b-165">El controlador OnDataReady recibe un objeto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="90b8b-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="90b8b-166">Los objetos WorldAnchor, MeshFilter y (opcionalmente) MeshCollider que contiene reflejan el estado más reciente de la superficie espacial asociada.</span><span class="sxs-lookup"><span data-stu-id="90b8b-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="90b8b-167">Opcionalmente, analice o [procese los](../../design/spatial-mapping.md#mesh-processing) datos de malla mediante el acceso al miembro Mesh del objeto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="90b8b-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="90b8b-168">Represente la superficie espacial con la malla más reciente y úsela (opcionalmente) para colisiones físicas y difusión de rayos.</span><span class="sxs-lookup"><span data-stu-id="90b8b-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="90b8b-169">Es importante confirmar que el contenido de SurfaceData no es NULL.</span><span class="sxs-lookup"><span data-stu-id="90b8b-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="90b8b-170">Iniciar el procesamiento en las actualizaciones</span><span class="sxs-lookup"><span data-stu-id="90b8b-170">Start processing on updates</span></span>

<span data-ttu-id="90b8b-171">Se debe llamar a SurfaceObserver.Update() en un retraso, no a todos los fotogramas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatial-understanding"></a><span data-ttu-id="90b8b-172">Análisis de malla de nivel superior: Spatial Understanding</span><span class="sxs-lookup"><span data-stu-id="90b8b-172">Higher-level mesh analysis: Spatial Understanding</span></span>

> [!CAUTION]
> <span data-ttu-id="90b8b-173">La comprensión espacial ha quedado en desuso en favor de [Scene Understanding.](../../design/scene-understanding.md)</span><span class="sxs-lookup"><span data-stu-id="90b8b-173">Spatial Understanding has been deprecated in favor of [Scene Understanding](../../design/scene-understanding.md).</span></span>

<span data-ttu-id="90b8b-174"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit es</a> una colección de código de utilidad para el desarrollo holográfico basado en las API holográficas de Unity.</span><span class="sxs-lookup"><span data-stu-id="90b8b-174">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="90b8b-175">Comprensión espacial</span><span class="sxs-lookup"><span data-stu-id="90b8b-175">Spatial Understanding</span></span>

<span data-ttu-id="90b8b-176">Al colocar hologramas en el mundo físico, a menudo es deseable ir más allá de los planos de malla y superficie de la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-176">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="90b8b-177">Cuando la selección de ubicación se realiza por procedimientos, es deseable un mayor nivel de comprensión del entorno.</span><span class="sxs-lookup"><span data-stu-id="90b8b-177">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="90b8b-178">Esto normalmente requiere tomar decisiones sobre lo que es el suelo, el límite superior y las paredes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-178">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="90b8b-179">También tiene la capacidad de optimizar frente a un conjunto de restricciones de selección de ubicación para determinar las mejores ubicaciones físicas para los objetos holográficos.</span><span class="sxs-lookup"><span data-stu-id="90b8b-179">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="90b8b-180">Durante el desarrollo de Young Conker y Fragments, Asobo Studios se enfrentaba a este problema de frente mediante el desarrollo de un solucionador de sala.</span><span class="sxs-lookup"><span data-stu-id="90b8b-180">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="90b8b-181">Cada uno de estos juegos tenía necesidades específicas del juego, pero compartían la tecnología de comprensión espacial básica.</span><span class="sxs-lookup"><span data-stu-id="90b8b-181">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="90b8b-182">La biblioteca HoloToolkit.SpatialUnderstanding encapsula esta tecnología, lo que le permite encontrar rápidamente espacios vacíos en las paredes, colocar objetos en el límite, identificar colocados para que el carácter se sitúe y una gran cantidad de otras consultas de comprensión espacial.</span><span class="sxs-lookup"><span data-stu-id="90b8b-182">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="90b8b-183">Se incluye todo el código fuente, lo que le permite personalizarlo según sus necesidades y compartir sus mejoras con la comunidad.</span><span class="sxs-lookup"><span data-stu-id="90b8b-183">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="90b8b-184">El código del solucionador de C++ se ha encapsulado en un archivo DLL de UWP y se ha expuesto a Unity con una colocación de prefab incluida en MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="90b8b-184">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="90b8b-185">Descripción de los módulos</span><span class="sxs-lookup"><span data-stu-id="90b8b-185">Understanding Modules</span></span>

<span data-ttu-id="90b8b-186">Hay tres interfaces principales expuestas por el módulo: topología para consultas espaciales y de superficie sencillas, forma para la detección de objetos y solucionador de colocación de objetos para la colocación basada en restricciones de conjuntos de objetos.</span><span class="sxs-lookup"><span data-stu-id="90b8b-186">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="90b8b-187">Cada uno de ellos se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="90b8b-187">Each of these is described below.</span></span> <span data-ttu-id="90b8b-188">Además de las tres interfaces de módulo principal, se puede usar una interfaz de conversión de rayos para recuperar los tipos de superficie etiquetados y se puede copiar una malla de espacio de juego estanca personalizada.</span><span class="sxs-lookup"><span data-stu-id="90b8b-188">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="90b8b-189">Conversión de rayos</span><span class="sxs-lookup"><span data-stu-id="90b8b-189">Ray Casting</span></span>

<span data-ttu-id="90b8b-190">Una vez completado el examen de la sala, las etiquetas se generan internamente para superficies como el suelo, el techo y las paredes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-190">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="90b8b-191">La función toma un rayo y devuelve si el rayo colisiona con una superficie conocida y, si es así, información sobre esa superficie en `PlayspaceRaycast` forma de `RaycastResult` .</span><span class="sxs-lookup"><span data-stu-id="90b8b-191">The `PlayspaceRaycast` function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a `RaycastResult`.</span></span>

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

<span data-ttu-id="90b8b-192">Internamente, la transmisión por rayos se calcula en la representación de vóxel en cubo de 8 cm calculada del espacio de reproducción.</span><span class="sxs-lookup"><span data-stu-id="90b8b-192">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="90b8b-193">Cada vóxel contiene un conjunto de elementos de superficie con datos de topología procesados (también conocido como tablas).</span><span class="sxs-lookup"><span data-stu-id="90b8b-193">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="90b8b-194">Se comparan las tablas contenidas en la celda de vóxel intersección y la mejor coincidencia que se usa para buscar la información de la topología.</span><span class="sxs-lookup"><span data-stu-id="90b8b-194">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="90b8b-195">Estos datos de topología contienen el etiquetado devuelto en forma de enumeración "SurfaceTypes", así como el área de superficie de la superficie intersectada.</span><span class="sxs-lookup"><span data-stu-id="90b8b-195">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="90b8b-196">En el ejemplo de Unity, el cursor convierte un rayo en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="90b8b-196">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="90b8b-197">En primer lugar, contra los colisiondores de Unity.</span><span class="sxs-lookup"><span data-stu-id="90b8b-197">First, against Unity’s colliders.</span></span> <span data-ttu-id="90b8b-198">En segundo lugar, frente a la representación mundial del módulo de comprensión.</span><span class="sxs-lookup"><span data-stu-id="90b8b-198">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="90b8b-199">Y, por último, de nuevo elementos de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="90b8b-199">And finally, again UI elements.</span></span> <span data-ttu-id="90b8b-200">En esta aplicación, la interfaz de usuario obtiene prioridad, después el resultado de la comprensión y, por último, los colisiondores de Unity.</span><span class="sxs-lookup"><span data-stu-id="90b8b-200">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="90b8b-201">SurfaceType se notifica como texto junto al cursor.</span><span class="sxs-lookup"><span data-stu-id="90b8b-201">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="90b8b-202">![El tipo de superficie se etiqueta junto al cursor](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="90b8b-202">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="90b8b-203">*El tipo de superficie se etiqueta junto al cursor*</span><span class="sxs-lookup"><span data-stu-id="90b8b-203">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="90b8b-204">Consultas de topología</span><span class="sxs-lookup"><span data-stu-id="90b8b-204">Topology Queries</span></span>

<span data-ttu-id="90b8b-205">Dentro del archivo DLL, el administrador de topologías controla el etiquetado del entorno.</span><span class="sxs-lookup"><span data-stu-id="90b8b-205">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="90b8b-206">Como se mencionó anteriormente, gran parte de los datos se almacenan en tablas, contenidas dentro de un volumen de vóxel.</span><span class="sxs-lookup"><span data-stu-id="90b8b-206">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="90b8b-207">Además, la estructura "PlaySpaceInfos" se usa para almacenar información sobre el espacio de juego, incluida la alineación del mundo (más detalles sobre esto a continuación), el suelo y la altura del límite superior.</span><span class="sxs-lookup"><span data-stu-id="90b8b-207">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="90b8b-208">La heurística se usa para determinar el suelo, el techo y las paredes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-208">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="90b8b-209">Por ejemplo, la superficie horizontal más grande y más baja con un área de superficie superior a 1 m2 se considera el suelo.</span><span class="sxs-lookup"><span data-stu-id="90b8b-209">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span>

> [!NOTE]
> <span data-ttu-id="90b8b-210">La ruta de acceso de la cámara durante el proceso de examen también se usa en este proceso.</span><span class="sxs-lookup"><span data-stu-id="90b8b-210">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="90b8b-211">Un subconjunto de las consultas expuestas por el administrador de topologías se expone a través de la dll.</span><span class="sxs-lookup"><span data-stu-id="90b8b-211">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="90b8b-212">Las consultas de topología expuestas son las siguientes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-212">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="90b8b-213">Cada una de las consultas tiene un conjunto de parámetros, específicos del tipo de consulta.</span><span class="sxs-lookup"><span data-stu-id="90b8b-213">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="90b8b-214">En el ejemplo siguiente, el usuario especifica el alto mínimo & ancho del volumen deseado, la altura de colocación mínima por encima del suelo y la cantidad mínima de autorización delante del volumen.</span><span class="sxs-lookup"><span data-stu-id="90b8b-214">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="90b8b-215">Todas las medidas están en metros.</span><span class="sxs-lookup"><span data-stu-id="90b8b-215">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="90b8b-216">Cada una de estas consultas toma una matriz preasignada de estructuras "TopologyResult".</span><span class="sxs-lookup"><span data-stu-id="90b8b-216">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="90b8b-217">El parámetro "locationCount" especifica la longitud de la matriz pasada.</span><span class="sxs-lookup"><span data-stu-id="90b8b-217">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="90b8b-218">El valor devuelto informa del número de ubicaciones devueltas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-218">The return value reports the number of returned locations.</span></span> <span data-ttu-id="90b8b-219">Este número nunca es mayor que el parámetro "locationCount" pasado.</span><span class="sxs-lookup"><span data-stu-id="90b8b-219">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="90b8b-220">"TopologyResult" contiene la posición central del volumen devuelto, la dirección orientada (es decir, normal) y las dimensiones del espacio encontrado.</span><span class="sxs-lookup"><span data-stu-id="90b8b-220">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

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
> <span data-ttu-id="90b8b-221">En el ejemplo de Unity, cada una de estas consultas está vinculada a un botón en el panel de interfaz de usuario virtual.</span><span class="sxs-lookup"><span data-stu-id="90b8b-221">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="90b8b-222">El ejemplo codifica los parámetros de cada una de estas consultas a valores razonables.</span><span class="sxs-lookup"><span data-stu-id="90b8b-222">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="90b8b-223">Vea SpaceVisualizer.cs en el código de ejemplo para obtener más ejemplos.</span><span class="sxs-lookup"><span data-stu-id="90b8b-223">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="90b8b-224">Dar forma a las consultas</span><span class="sxs-lookup"><span data-stu-id="90b8b-224">Shape Queries</span></span>

<span data-ttu-id="90b8b-225">En el archivo dll, el analizador de formas ("ShapeAnalyzer_W") usa el analizador de topología para coincidir con las formas personalizadas definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="90b8b-225">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="90b8b-226">El ejemplo de Unity define un conjunto de formas y expone los resultados a través del menú de consulta en la aplicación, dentro de la pestaña forma. La intención es que el usuario pueda definir sus propias consultas de forma de objeto y usarlas, según sea necesario para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="90b8b-226">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="90b8b-227">El análisis de formas solo funciona en superficies horizontales.</span><span class="sxs-lookup"><span data-stu-id="90b8b-227">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="90b8b-228">Un diván, por ejemplo, se define mediante la superficie del puesto plano y la parte superior plana del respaldo del diván.</span><span class="sxs-lookup"><span data-stu-id="90b8b-228">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="90b8b-229">La consulta de formas busca dos superficies de un tamaño, un alto y un intervalo de aspecto específicos, con las dos superficies alineadas y conectadas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-229">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="90b8b-230">Con la terminología de las API, el puesto del diván y la parte posterior son componentes de forma y los requisitos de alineación son restricciones de componentes de forma.</span><span class="sxs-lookup"><span data-stu-id="90b8b-230">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="90b8b-231">A continuación se muestra una consulta de ejemplo definida en el ejemplo de Unity (ShapeDefinition.cs) para objetos "sittable".</span><span class="sxs-lookup"><span data-stu-id="90b8b-231">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="90b8b-232">Cada consulta de forma se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componentes y un conjunto de restricciones de forma que enumeran las dependencias entre los componentes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-232">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="90b8b-233">Este ejemplo incluye tres restricciones en una única definición de componente y ninguna restricción de forma entre componentes (ya que solo hay un componente).</span><span class="sxs-lookup"><span data-stu-id="90b8b-233">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="90b8b-234">Por el contrario, la forma del diván tiene dos componentes de forma y cuatro restricciones de forma.</span><span class="sxs-lookup"><span data-stu-id="90b8b-234">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="90b8b-235">Los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="90b8b-235">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="90b8b-236">Las funciones contenedoras se proporcionan en el módulo de Unity para facilitar la creación de definiciones de formas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-236">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="90b8b-237">La lista completa de restricciones de componentes y formas se puede encontrar en "SpatialUnderstandingDll.cs" dentro de las estructuras "ShapeComponentConstraint" y "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="90b8b-237">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="90b8b-238">![La forma del rectángulo se encuentra en esta superficie](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="90b8b-238">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="90b8b-239">*La forma del rectángulo se encuentra en esta superficie*</span><span class="sxs-lookup"><span data-stu-id="90b8b-239">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="90b8b-240">Solucionador de colocación de objetos</span><span class="sxs-lookup"><span data-stu-id="90b8b-240">Object Placement Solver</span></span>

<span data-ttu-id="90b8b-241">El solucionador de colocación de objetos se puede usar para identificar ubicaciones ideales en la sala física para colocar los objetos.</span><span class="sxs-lookup"><span data-stu-id="90b8b-241">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="90b8b-242">El solucionador encontrará la mejor ubicación de ajuste dadas las restricciones y las reglas de objeto.</span><span class="sxs-lookup"><span data-stu-id="90b8b-242">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="90b8b-243">Además, las consultas de objetos se conservan hasta que se quita el objeto con llamadas "Solver_RemoveObject" o "Solver_RemoveAllObjects", lo que permite la colocación restringida de varios objetos.</span><span class="sxs-lookup"><span data-stu-id="90b8b-243">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="90b8b-244">Las consultas de selección de ubicación de objetos constan de tres partes: tipo de selección de ubicación con parámetros, una lista de reglas y una lista de restricciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-244">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="90b8b-245">Para ejecutar una consulta, use la API siguiente.</span><span class="sxs-lookup"><span data-stu-id="90b8b-245">To run a query, use the following API.</span></span>

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

<span data-ttu-id="90b8b-246">Esta función toma un nombre de objeto, una definición de selección de ubicación y una lista de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-246">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="90b8b-247">Los contenedores de C# proporcionan funciones auxiliares de construcción para facilitar la construcción de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-247">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="90b8b-248">La definición de selección de ubicación contiene el tipo de consulta, es decir, uno de los siguientes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-248">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="90b8b-249">Cada uno de los tipos de selección de ubicación tiene un conjunto de parámetros únicos para el tipo.</span><span class="sxs-lookup"><span data-stu-id="90b8b-249">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="90b8b-250">La estructura "ObjectPlacementDefinition" contiene un conjunto de funciones auxiliares estáticas para crear estas definiciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-250">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="90b8b-251">Por ejemplo, para buscar un lugar donde colocar un objeto en el suelo, puede usar la siguiente función.</span><span class="sxs-lookup"><span data-stu-id="90b8b-251">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="90b8b-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Además del tipo placement, puede proporcionar un conjunto de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="90b8b-253">No se pueden infringir las reglas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-253">Rules cannot be violated.</span></span> <span data-ttu-id="90b8b-254">Las posibles ubicaciones de selección de ubicación que cumplen el tipo y las reglas se optimizan con el conjunto de restricciones para seleccionar la ubicación de ubicación óptima.</span><span class="sxs-lookup"><span data-stu-id="90b8b-254">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="90b8b-255">Las funciones de creación estática proporcionadas pueden crear cada una de las reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-255">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="90b8b-256">A continuación se proporciona una regla de ejemplo y una función de construcción de restricciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-256">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="90b8b-257">La siguiente consulta de selección de ubicación de objetos busca un lugar donde colocar un cubo de medio metro en el borde de una superficie, lejos de otros objetos situados anteriormente y cerca del centro de la sala.</span><span class="sxs-lookup"><span data-stu-id="90b8b-257">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="90b8b-258">Si se realiza correctamente, se devuelve una estructura "ObjectPlacementResult" que contiene la posición de colocación, las dimensiones y la orientación.</span><span class="sxs-lookup"><span data-stu-id="90b8b-258">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="90b8b-259">Además, la colocación se agrega a la lista interna del archivo DLL de objetos colocados.</span><span class="sxs-lookup"><span data-stu-id="90b8b-259">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="90b8b-260">Las consultas de selección de ubicación posteriores tendrán en cuenta este objeto.</span><span class="sxs-lookup"><span data-stu-id="90b8b-260">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="90b8b-261">El archivo "LevelSolver.cs" del ejemplo de Unity contiene más consultas de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="90b8b-261">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="90b8b-262">![Resultados de la selección de ubicación de objetos](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="90b8b-262">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="90b8b-263">*Figura 3: Cuadros azules en los que el resultado de las consultas de tres posiciones en el suelo se encuentra fuera de las reglas de posición de la cámara*</span><span class="sxs-lookup"><span data-stu-id="90b8b-263">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="90b8b-264">Al resolver la ubicación de colocación de varios objetos necesarios para un escenario de nivel o aplicación, primero debe resolver objetos imprescindibles y grandes para maximizar la probabilidad de que se pueda encontrar un espacio.</span><span class="sxs-lookup"><span data-stu-id="90b8b-264">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="90b8b-265">El orden de selección de ubicación es importante.</span><span class="sxs-lookup"><span data-stu-id="90b8b-265">Placement order is important.</span></span> <span data-ttu-id="90b8b-266">Si no se pueden encontrar colocaciones de objetos, pruebe con configuraciones menos restringidas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-266">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="90b8b-267">Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de sala.</span><span class="sxs-lookup"><span data-stu-id="90b8b-267">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="90b8b-268">Proceso de examen de sala</span><span class="sxs-lookup"><span data-stu-id="90b8b-268">Room Scanning Process</span></span>

<span data-ttu-id="90b8b-269">Aunque la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genérica como para satisfacer las necesidades de toda la gama de espacios con problemas, el módulo de comprensión espacial se creó para admitir las necesidades de dos juegos específicos.</span><span class="sxs-lookup"><span data-stu-id="90b8b-269">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="90b8b-270">Su solución se estructura en torno a un proceso específico y un conjunto de suposiciones, que se resumen a continuación.</span><span class="sxs-lookup"><span data-stu-id="90b8b-270">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="90b8b-271">"dibujo" del espacio de juego controlado por el usuario: durante la fase de examen, el usuario se mueve y busca alrededor del ritmo de reproducción, pintando eficazmente las áreas, que deben incluirse.</span><span class="sxs-lookup"><span data-stu-id="90b8b-271">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="90b8b-272">La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.</span><span class="sxs-lookup"><span data-stu-id="90b8b-272">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="90b8b-273">Configuración del hogar u oficina interior: las funciones de consulta están diseñadas en torno a superficies planas y paredes en ángulos derecho.</span><span class="sxs-lookup"><span data-stu-id="90b8b-273">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="90b8b-274">Se trata de una limitación temporal.</span><span class="sxs-lookup"><span data-stu-id="90b8b-274">This is a soft limitation.</span></span> <span data-ttu-id="90b8b-275">Sin embargo, durante la fase de análisis, se completa un análisis del eje principal para optimizar la teselación de malla a lo largo de los ejes principal y secundario.</span><span class="sxs-lookup"><span data-stu-id="90b8b-275">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="90b8b-276">El archivo SpatialUnderstanding.cs incluido administra el proceso de fase de examen.</span><span class="sxs-lookup"><span data-stu-id="90b8b-276">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="90b8b-277">Llama a las siguientes funciones.</span><span class="sxs-lookup"><span data-stu-id="90b8b-277">It calls the following functions.</span></span>

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

<span data-ttu-id="90b8b-278">El flujo de examen, controlado por el comportamiento "SpatialUnderstanding", llama a InitScan y, a continuación, UpdateScan a cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="90b8b-278">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="90b8b-279">Cuando la consulta de estadísticas informa de una cobertura razonable, el usuario puede usar airtap para llamar a RequestFinish para indicar el final de la fase de examen.</span><span class="sxs-lookup"><span data-stu-id="90b8b-279">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="90b8b-280">Se sigue llamando a UpdateScan hasta que su valor devuelto indica que el archivo DLL ha completado el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="90b8b-280">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="90b8b-281">Descripción de Mesh</span><span class="sxs-lookup"><span data-stu-id="90b8b-281">Understanding Mesh</span></span>

<span data-ttu-id="90b8b-282">La dll de comprensión almacena internamente el espacio de reproducción como una cuadrícula de cubos de vóxel de 8 cm de tamaño.</span><span class="sxs-lookup"><span data-stu-id="90b8b-282">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="90b8b-283">Durante la parte inicial del análisis, se completa un análisis de componentes principales para determinar los ejes de la sala.</span><span class="sxs-lookup"><span data-stu-id="90b8b-283">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="90b8b-284">Internamente, almacena su espacio de vóxel alineado con estos ejes.</span><span class="sxs-lookup"><span data-stu-id="90b8b-284">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="90b8b-285">Una malla se genera aproximadamente cada segundo mediante la extracción del isosurface del volumen de vóxel.</span><span class="sxs-lookup"><span data-stu-id="90b8b-285">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

<span data-ttu-id="90b8b-286">![Malla generada a partir del volumen de vóxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="90b8b-286">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="90b8b-287">*Malla generada a partir del volumen de vóxel*</span><span class="sxs-lookup"><span data-stu-id="90b8b-287">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="90b8b-288">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="90b8b-288">Troubleshooting</span></span>

* <span data-ttu-id="90b8b-289">Asegúrese de que ha establecido [la funcionalidad SpatialPerception.](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="90b8b-289">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="90b8b-290">Cuando se pierde el seguimiento, el siguiente evento OnSurfaceChanged quitará todas las mallas.</span><span class="sxs-lookup"><span data-stu-id="90b8b-290">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="90b8b-291">Asignación espacial en Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="90b8b-291">Spatial Mapping in Mixed Reality Toolkit</span></span>

<span data-ttu-id="90b8b-292">Para más información sobre el uso de la asignación espacial con Mixed Reality Toolkit, consulte la sección de reconocimiento [espacial](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) de los documentos de MRTK.</span><span class="sxs-lookup"><span data-stu-id="90b8b-292">For more information on using Spatial Mapping with Mixed Reality Toolkit, see the [spatial awareness section](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="90b8b-293">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="90b8b-293">Next Development Checkpoint</span></span>

<span data-ttu-id="90b8b-294">Si sigue el recorrido de desarrollo de Unity que hemos diseñado, está en medio de la exploración de los bloques de creación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="90b8b-294">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="90b8b-295">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="90b8b-295">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90b8b-296">Texto</span><span class="sxs-lookup"><span data-stu-id="90b8b-296">Text</span></span>](text-in-unity.md)

<span data-ttu-id="90b8b-297">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="90b8b-297">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90b8b-298">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="90b8b-298">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="90b8b-299">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="90b8b-299">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="90b8b-300">Consulte también</span><span class="sxs-lookup"><span data-stu-id="90b8b-300">See also</span></span>

* [<span data-ttu-id="90b8b-301">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="90b8b-301">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="90b8b-302">Sistemas de coordenadas de Unity</span><span class="sxs-lookup"><span data-stu-id="90b8b-302">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="90b8b-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="90b8b-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="90b8b-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="90b8b-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="90b8b-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="90b8b-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="90b8b-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="90b8b-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
