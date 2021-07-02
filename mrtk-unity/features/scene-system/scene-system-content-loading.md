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
# <a name="scene-system-content-loading"></a>Carga de contenido del sistema de escena

Todas las operaciones de carga de contenido son asincrónicas y, de forma predeterminada, toda la carga de contenido es aditiva. Las escenas de iluminación y administrador nunca se ven afectadas por las operaciones de carga de contenido. Para obtener información sobre cómo supervisar el progreso de la carga y la activación de la escena, vea [Supervisión de la carga de contenido.](scene-system-load-progress.md)

## <a name="loading-content"></a>Carga de contenido

Para cargar escenas de contenido, use el `LoadContent` método :

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Carga de una sola escena

El equivalente de una carga de escena única se puede lograr a través del argumento `mode` opcional. `LoadSceneMode.Single` primero descargará todas las escenas de contenido cargadas antes de continuar con la carga.

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

## <a name="next--previous-scene-loading"></a>Carga de la escena siguiente o anterior

El contenido se puede cargar de forma singly en orden de índice de compilación. Esto es útil para presentar aplicaciones que llevan a los usuarios a través de un conjunto de escenas de demostración una a una.

![Escenas actuales en la compilación en la configuración del reproductor](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Tenga en cuenta que la siguiente carga de contenido o anterior usa LoadSceneMode.Single de forma predeterminada para asegurarse de que se descarga el contenido anterior.

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

`PrevContentExists` devolverá true si hay al menos una escena de contenido con un índice de compilación inferior al índice de compilación más bajo cargado actualmente. `NextContentExists` devolverá true si hay al menos una escena de contenido que tenga un índice de compilación mayor que el índice de compilación más alto cargado actualmente.

Si el `wrap` argumento es true, el contenido volverá al primer y último índice de compilación. Esto elimina la necesidad de comprobar el contenido siguiente o anterior:

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

## <a name="loading-by-tag"></a>Carga por etiqueta

![Carga de escenas de contenido por etiqueta](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

A veces es conveniente cargar escenas de contenido en grupos. Por ejemplo, una fase de una experiencia puede estar formada por varias escenas, todas las cuales deben cargarse simultáneamente para funcionar. Para facilitar esto, puede etiquetar las escenas y, a continuación, cargarlas o descargarlas con esa etiqueta.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

La carga por etiqueta también puede ser útil si los intérpretes quieren incorporar o quitar elementos de una experiencia sin tener que modificar scripts. Por ejemplo, la ejecución de este script con los dos conjuntos de etiquetas siguientes produce resultados diferentes:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Prueba de contenido

Nombre de la escena | Etiqueta de escena | Cargado por script
---|---|---
DebugXiainPhysics | Terreno | •
StructureTesting | Estructuras | •
DeserciónTools | Vegetación | •
Mountain | Terreno | •
Cabin | Estructuras | •
Árboles | Vegetación | •

### <a name="final-content"></a>Contenido final

Nombre de la escena | Etiqueta de escena | Cargado por script
---|---|---
DebugXiainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
DeserciónTools | DoNotInclude |
Mountain | Terreno | •
Cabin | Estructuras | •
Árboles | Vegetación | •

---

## <a name="editor-behavior"></a>Comportamiento del editor

Puede realizar todas estas operaciones en el editor y en modo de reproducción mediante el inspector de servicio del sistema de [escena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) En el modo de edición, las cargas de escena serán instantáneas, mientras que en el modo de reproducción puede observar el progreso de la carga y usar [tokens de activación.](scene-system-load-progress.md)

![Sistema de escena en el inspector con la carga de contenido resaltada](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
