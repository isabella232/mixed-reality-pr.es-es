---
title: Mapeo espacial en Unreal
description: Guía para el uso del mapeo espacial en Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354391"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="4b67e-104">Mapeo espacial en Unreal</span><span class="sxs-lookup"><span data-stu-id="4b67e-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="4b67e-105">El mapeo espacial permite colocar objetos sobre superficies del mundo físico mediante la visualización del mundo de alrededor de HoloLens, lo que hace que los hologramas parezcan más reales al usuario.</span><span class="sxs-lookup"><span data-stu-id="4b67e-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="4b67e-106">El mapeo espacial también ancla objetos en el mundo del usuario aprovechando las indicaciones detalladas del mundo real. Con ello, se ayuda a convencer al usuario de que estos hologramas están realmente en su espacio; los hologramas que flotan en el espacio o se mueven con el usuario no se verán como reales.</span><span class="sxs-lookup"><span data-stu-id="4b67e-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="4b67e-107">Es aconsejable colocar elementos para mayor confort, siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="4b67e-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="4b67e-108">Puede encontrar más información sobre la calidad del mapeo espacial, la ubicación, la oclusión, la representación, etc., en el documento [Asignación espacial](../../design/spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="4b67e-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="4b67e-109">Habilitación del mapeo espacial</span><span class="sxs-lookup"><span data-stu-id="4b67e-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="4b67e-110">Para habilitar el mapeo espacial en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="4b67e-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="4b67e-111">Abra **Editar > Configuración del proyecto** y desplácese hacia abajo hasta la sección **Plataformas**.</span><span class="sxs-lookup"><span data-stu-id="4b67e-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="4b67e-112">Seleccione **HoloLens** y marque **Percepción espacial**.</span><span class="sxs-lookup"><span data-stu-id="4b67e-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![Captura de pantalla de las funcionalidades de configuración del proyecto de HoloLens con la percepción espacial resaltada](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="4b67e-114">Para participar en el mapeo espacial y depurar **MRMesh** en un juego HoloLens:</span><span class="sxs-lookup"><span data-stu-id="4b67e-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="4b67e-115">Abra **ARSessionConfig** y expanda la sección **ARSettings > World Mapping (Mapeo del mundo)** .</span><span class="sxs-lookup"><span data-stu-id="4b67e-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="4b67e-116">Active **Generate Mesh Data from Tracked Geometry** (Generar datos de malla a partir de la geometría de seguimiento), que indica al complemento de HoloLens que empiece a obtener los datos de mapeo espacial de forma asincrónica y los exponga en Unreal a través de **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="4b67e-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="4b67e-117">Marque **Render Mesh Data in Wireframe (Representar datos de malla en contorno reticular)** para mostrar un contorno reticular blanco de cada triángulo de **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="4b67e-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Almacén de anclajes espaciales listo](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="4b67e-119">Mapeo espacial en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="4b67e-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="4b67e-120">Puede modificar los parámetros siguientes para actualizar el comportamiento en tiempo de ejecución del mapeo espacial:</span><span class="sxs-lookup"><span data-stu-id="4b67e-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="4b67e-121">Abra **Editar > Configuración del proyecto**, desplácese hacia abajo hasta la sección **Plataformas** y seleccione **HoloLens > Spatial Mapping (Mapeo espacial)** :</span><span class="sxs-lookup"><span data-stu-id="4b67e-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Configuración del proyecto de anclajes espaciales](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="4b67e-123">**Max Triangles Per Cubic Meter** (Máximo de triángulos por metro cúbico) actualice la densidad de los triángulos en la malla de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="4b67e-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="4b67e-124">**Spatial Meshing Volume Size** (Tamaño del volumen de la malla espacial) es el tamaño del cubo alrededor del jugador para representar y actualizar los datos de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="4b67e-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="4b67e-125">Si se espera que el entorno en tiempo de ejecución de la aplicación sea elevado, es posible que este valor tenga que ser grande para que coincida con el espacio del mundo real.</span><span class="sxs-lookup"><span data-stu-id="4b67e-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="4b67e-126">Por otro lado, este valor puede ser menor si la aplicación solo necesita colocar hologramas en superficies inmediatamente alrededor del usuario.</span><span class="sxs-lookup"><span data-stu-id="4b67e-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="4b67e-127">A medida que el usuario se desplaza por el mundo, el volumen de mapeo espacial se moverá con él.</span><span class="sxs-lookup"><span data-stu-id="4b67e-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="4b67e-128">Utilización de MRMesh</span><span class="sxs-lookup"><span data-stu-id="4b67e-128">Working with MRMesh</span></span>

<span data-ttu-id="4b67e-129">En primer lugar, debe iniciar la asignación espacial:</span><span class="sxs-lookup"><span data-stu-id="4b67e-129">First, you need to start Spatial Mapping:</span></span>

![Plano técnico de la función ToggleARCapture con el tipo de captura de asignación espacial resaltado](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="4b67e-131">Una vez que se haya capturado la asignación espacial para el espacio, se recomienda desactivar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="4b67e-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="4b67e-132">La asignación espacial se puede completar una vez transcurrido un período de tiempo determinado, o cuando los rayos enviados en cada dirección devuelvan colisiones con MRMesh.</span><span class="sxs-lookup"><span data-stu-id="4b67e-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="4b67e-133">Para obtener acceso a **MRMesh** en tiempo de ejecución:</span><span class="sxs-lookup"><span data-stu-id="4b67e-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="4b67e-134">Agregue un componente **ARTrackableNotify** a un actor de Blueprint.</span><span class="sxs-lookup"><span data-stu-id="4b67e-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Notificaciones supervisadas de AR de anclajes espaciales](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="4b67e-136">Seleccione el componente **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**.</span><span class="sxs-lookup"><span data-stu-id="4b67e-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="4b67e-137">Haga clic en el botón **+** en los eventos que quiera supervisar.</span><span class="sxs-lookup"><span data-stu-id="4b67e-137">Click the **+** button on the events you want to monitor.</span></span> 

![Eventos de Spatial Anchors](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="4b67e-139">En este caso, se supervisa el evento **On Add Tracked Geometry** (Al agregar geometría de seguimiento), que busca mallas del mundo válidas que coincidan con los datos de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="4b67e-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="4b67e-140">Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="4b67e-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="4b67e-141">Puede cambiar el material de la malla en el gráfico de eventos de Blueprint o en C++.</span><span class="sxs-lookup"><span data-stu-id="4b67e-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="4b67e-142">En la captura de pantalla siguiente se muestra la ruta de Blueprint:</span><span class="sxs-lookup"><span data-stu-id="4b67e-142">The screenshot below shows the Blueprint route:</span></span> 

![Ejemplo de anclajes espaciales](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="4b67e-144">Asignación espacial en C++</span><span class="sxs-lookup"><span data-stu-id="4b67e-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="4b67e-145">En el archivo build.cs del juego, agregue **AugmentedReality** y **MRMesh** en la lista PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="4b67e-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

<span data-ttu-id="4b67e-146">Para acceder a MRMesh, suscríbase a los delegados **OnTrackableAdded**:</span><span class="sxs-lookup"><span data-stu-id="4b67e-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> <span data-ttu-id="4b67e-147">Hay delegados similares para eventos actualizados y eliminados (**AddOnTrackableUpdatedDelegate_Handle** y **AddOnTrackableRemovedDelegate_Handle**, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="4b67e-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="4b67e-148">Puede encontrar la lista completa de eventos en la API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="4b67e-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b67e-149">Consulta también</span><span class="sxs-lookup"><span data-stu-id="4b67e-149">See also</span></span>
* [<span data-ttu-id="4b67e-150">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="4b67e-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
