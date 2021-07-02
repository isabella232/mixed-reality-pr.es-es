---
title: Carga de contenido del sistema de escena
description: Documentación sobre la carga del sistema de escena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177582"
---
# <a name="scene-system-content-loading"></a><span data-ttu-id="77f01-104">Carga de contenido del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="77f01-104">Scene system content loading</span></span>

<span data-ttu-id="77f01-105">Todas las operaciones de carga de contenido son asincrónicas y, de forma predeterminada, toda la carga de contenido es aditiva.</span><span class="sxs-lookup"><span data-stu-id="77f01-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="77f01-106">Las escenas de iluminación y administrador nunca se ven afectadas por las operaciones de carga de contenido.</span><span class="sxs-lookup"><span data-stu-id="77f01-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="77f01-107">Para obtener información sobre cómo supervisar el progreso de la carga y la activación de la escena, vea [Supervisión de la carga de contenido.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="77f01-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="77f01-108">Carga de contenido</span><span class="sxs-lookup"><span data-stu-id="77f01-108">Loading content</span></span>

<span data-ttu-id="77f01-109">Para cargar escenas de contenido, use el `LoadContent` método :</span><span class="sxs-lookup"><span data-stu-id="77f01-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="77f01-110">Carga de una sola escena</span><span class="sxs-lookup"><span data-stu-id="77f01-110">Single scene loading</span></span>

<span data-ttu-id="77f01-111">El equivalente de una carga de escena única se puede lograr a través del argumento `mode` opcional.</span><span class="sxs-lookup"><span data-stu-id="77f01-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="77f01-112">`LoadSceneMode.Single` primero descargará todas las escenas de contenido cargadas antes de continuar con la carga.</span><span class="sxs-lookup"><span data-stu-id="77f01-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a><span data-ttu-id="77f01-113">Carga de la escena siguiente o anterior</span><span class="sxs-lookup"><span data-stu-id="77f01-113">Next / previous scene loading</span></span>

<span data-ttu-id="77f01-114">El contenido se puede cargar de forma singly en orden de índice de compilación.</span><span class="sxs-lookup"><span data-stu-id="77f01-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="77f01-115">Esto es útil para presentar aplicaciones que llevan a los usuarios a través de un conjunto de escenas de demostración una a una.</span><span class="sxs-lookup"><span data-stu-id="77f01-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Escenas actuales en la compilación en la configuración del reproductor](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="77f01-117">Tenga en cuenta que la siguiente carga de contenido o anterior usa LoadSceneMode.Single de forma predeterminada para asegurarse de que se descarga el contenido anterior.</span><span class="sxs-lookup"><span data-stu-id="77f01-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

<span data-ttu-id="77f01-118">`PrevContentExists` devolverá true si hay al menos una escena de contenido con un índice de compilación inferior al índice de compilación más bajo cargado actualmente.</span><span class="sxs-lookup"><span data-stu-id="77f01-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="77f01-119">`NextContentExists` devolverá true si hay al menos una escena de contenido que tenga un índice de compilación mayor que el índice de compilación más alto cargado actualmente.</span><span class="sxs-lookup"><span data-stu-id="77f01-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="77f01-120">Si el `wrap` argumento es true, el contenido volverá al primer y último índice de compilación.</span><span class="sxs-lookup"><span data-stu-id="77f01-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="77f01-121">Esto elimina la necesidad de comprobar el contenido siguiente o anterior:</span><span class="sxs-lookup"><span data-stu-id="77f01-121">This removes the need to check for next / previous content:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a><span data-ttu-id="77f01-122">Carga por etiqueta</span><span class="sxs-lookup"><span data-stu-id="77f01-122">Loading by tag</span></span>

![Carga de escenas de contenido por etiqueta](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="77f01-124">A veces es conveniente cargar escenas de contenido en grupos.</span><span class="sxs-lookup"><span data-stu-id="77f01-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="77f01-125">Por ejemplo, una fase de una experiencia puede estar formada por varias escenas, todas las cuales deben cargarse simultáneamente para funcionar.</span><span class="sxs-lookup"><span data-stu-id="77f01-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="77f01-126">Para facilitar esto, puede etiquetar las escenas y, a continuación, cargarlas o descargarlas con esa etiqueta.</span><span class="sxs-lookup"><span data-stu-id="77f01-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="77f01-127">La carga por etiqueta también puede ser útil si los intérpretes quieren incorporar o quitar elementos de una experiencia sin tener que modificar scripts.</span><span class="sxs-lookup"><span data-stu-id="77f01-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="77f01-128">Por ejemplo, la ejecución de este script con los dos conjuntos de etiquetas siguientes produce resultados diferentes:</span><span class="sxs-lookup"><span data-stu-id="77f01-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="77f01-129">Prueba de contenido</span><span class="sxs-lookup"><span data-stu-id="77f01-129">Testing content</span></span>

<span data-ttu-id="77f01-130">Nombre de la escena</span><span class="sxs-lookup"><span data-stu-id="77f01-130">Scene Name</span></span> | <span data-ttu-id="77f01-131">Etiqueta de escena</span><span class="sxs-lookup"><span data-stu-id="77f01-131">Scene Tag</span></span> | <span data-ttu-id="77f01-132">Cargado por script</span><span class="sxs-lookup"><span data-stu-id="77f01-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="77f01-133">DebugXiainPhysics</span><span class="sxs-lookup"><span data-stu-id="77f01-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="77f01-134">Terreno</span><span class="sxs-lookup"><span data-stu-id="77f01-134">Terrain</span></span> | <span data-ttu-id="77f01-135">•</span><span class="sxs-lookup"><span data-stu-id="77f01-135">•</span></span>
<span data-ttu-id="77f01-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="77f01-136">StructureTesting</span></span> | <span data-ttu-id="77f01-137">Estructuras</span><span class="sxs-lookup"><span data-stu-id="77f01-137">Structures</span></span> | <span data-ttu-id="77f01-138">•</span><span class="sxs-lookup"><span data-stu-id="77f01-138">•</span></span>
<span data-ttu-id="77f01-139">DeserciónTools</span><span class="sxs-lookup"><span data-stu-id="77f01-139">VegetationTools</span></span> | <span data-ttu-id="77f01-140">Vegetación</span><span class="sxs-lookup"><span data-stu-id="77f01-140">Vegetation</span></span> | <span data-ttu-id="77f01-141">•</span><span class="sxs-lookup"><span data-stu-id="77f01-141">•</span></span>
<span data-ttu-id="77f01-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="77f01-142">Mountain</span></span> | <span data-ttu-id="77f01-143">Terreno</span><span class="sxs-lookup"><span data-stu-id="77f01-143">Terrain</span></span> | <span data-ttu-id="77f01-144">•</span><span class="sxs-lookup"><span data-stu-id="77f01-144">•</span></span>
<span data-ttu-id="77f01-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="77f01-145">Cabin</span></span> | <span data-ttu-id="77f01-146">Estructuras</span><span class="sxs-lookup"><span data-stu-id="77f01-146">Structures</span></span> | <span data-ttu-id="77f01-147">•</span><span class="sxs-lookup"><span data-stu-id="77f01-147">•</span></span>
<span data-ttu-id="77f01-148">Árboles</span><span class="sxs-lookup"><span data-stu-id="77f01-148">Trees</span></span> | <span data-ttu-id="77f01-149">Vegetación</span><span class="sxs-lookup"><span data-stu-id="77f01-149">Vegetation</span></span> | <span data-ttu-id="77f01-150">•</span><span class="sxs-lookup"><span data-stu-id="77f01-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="77f01-151">Contenido final</span><span class="sxs-lookup"><span data-stu-id="77f01-151">Final content</span></span>

<span data-ttu-id="77f01-152">Nombre de la escena</span><span class="sxs-lookup"><span data-stu-id="77f01-152">Scene Name</span></span> | <span data-ttu-id="77f01-153">Etiqueta de escena</span><span class="sxs-lookup"><span data-stu-id="77f01-153">Scene Tag</span></span> | <span data-ttu-id="77f01-154">Cargado por script</span><span class="sxs-lookup"><span data-stu-id="77f01-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="77f01-155">DebugXiainPhysics</span><span class="sxs-lookup"><span data-stu-id="77f01-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="77f01-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="77f01-156">DoNotInclude</span></span> |
<span data-ttu-id="77f01-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="77f01-157">StructureTesting</span></span> | <span data-ttu-id="77f01-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="77f01-158">DoNotInclude</span></span> |
<span data-ttu-id="77f01-159">DeserciónTools</span><span class="sxs-lookup"><span data-stu-id="77f01-159">VegetationTools</span></span> | <span data-ttu-id="77f01-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="77f01-160">DoNotInclude</span></span> |
<span data-ttu-id="77f01-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="77f01-161">Mountain</span></span> | <span data-ttu-id="77f01-162">Terreno</span><span class="sxs-lookup"><span data-stu-id="77f01-162">Terrain</span></span> | <span data-ttu-id="77f01-163">•</span><span class="sxs-lookup"><span data-stu-id="77f01-163">•</span></span>
<span data-ttu-id="77f01-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="77f01-164">Cabin</span></span> | <span data-ttu-id="77f01-165">Estructuras</span><span class="sxs-lookup"><span data-stu-id="77f01-165">Structures</span></span> | <span data-ttu-id="77f01-166">•</span><span class="sxs-lookup"><span data-stu-id="77f01-166">•</span></span>
<span data-ttu-id="77f01-167">Árboles</span><span class="sxs-lookup"><span data-stu-id="77f01-167">Trees</span></span> | <span data-ttu-id="77f01-168">Vegetación</span><span class="sxs-lookup"><span data-stu-id="77f01-168">Vegetation</span></span> | <span data-ttu-id="77f01-169">•</span><span class="sxs-lookup"><span data-stu-id="77f01-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="77f01-170">Comportamiento del editor</span><span class="sxs-lookup"><span data-stu-id="77f01-170">Editor behavior</span></span>

<span data-ttu-id="77f01-171">Puede realizar todas estas operaciones en el editor y en modo de reproducción mediante el inspector de servicio del sistema de [escena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="77f01-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="77f01-172">En el modo de edición, las cargas de escena serán instantáneas, mientras que en el modo de reproducción puede observar el progreso de la carga y usar [tokens de activación.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="77f01-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Sistema de escena en el inspector con la carga de contenido resaltada](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
