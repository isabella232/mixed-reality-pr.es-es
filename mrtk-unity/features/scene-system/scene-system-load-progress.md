---
title: Progreso de carga del sistema de escenas
description: Documentación sobre la carga de contenido de escenas en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144408"
---
# <a name="monitoring-content-loading"></a>Supervisión de la carga de contenido

## <a name="scene-operation-progress"></a>Progreso de la operación de escena

Cuando se carga o descarga contenido, la `SceneOperationInProgress` propiedad devuelve true. Puede supervisar el progreso de esta operación a través de la `SceneOperationProgress` propiedad .

El `SceneOperationProgress` valor es el promedio de todas las operaciones de escena asincrónicas actuales. Al principio de una carga de contenido, `SceneOperationProgress` será cero. Una vez completado por `SceneOperationProgress` completo, se establecerá en 1 y permanecerá en 1 hasta que se lleve a cabo la siguiente operación. Tenga en cuenta que solo las operaciones de escena de contenido afectan a estas propiedades.

Estas propiedades reflejan el estado de una *operación completa* de principio a fin, incluso si esa operación incluye varios pasos:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a>Ejemplos de progreso

`SceneOperationInProgress` puede ser útil si se debe suspender la actividad mientras se carga contenido:

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

`SceneOperationProgress` se puede usar para mostrar diálogos de progreso:

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a>Supervisión con acciones

Scene System proporciona varias acciones para que sepa cuándo se cargan o descargan las escenas. Cada acción retransmite el nombre de la escena afectada.

Si una operación de carga o descarga implica varias escenas, las acciones pertinentes se invocarán una vez por cada escena afectada. También se invocan todas a la vez cuando la operación de carga o descarga se *completa.* Por este motivo, se recomienda usar acciones *OnWillUnload* para detectar el contenido que se destruirá, en lugar de usar acciones *OnUnloaded* para detectar contenido destructor después del hecho. 

Por otro lado, dado que las acciones *OnLoaded* solo se invocan cuando todas las escenas se activan y se cargan por completo, se garantiza que el uso de acciones *OnLoaded* para detectar y usar contenido nuevo sea seguro.

Acción | Cuando se invoca | Escenas de contenido | Escenas de iluminación | Escenas de administrador
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | Justo antes de cargar una escena de contenido | • | |  
`OnContentLoaded` | Una vez que todas las escenas de contenido de una operación de carga se han cargado y activado por completo | • | |
`OnWillUnloadContent` | Justo antes de una operación de descarga de la escena de contenido | • | |
`OnContentUnloaded` | Una vez que se han descargado completamente todas las escenas de contenido de una operación de descarga | • | |
`OnWillLoadLighting` | Justo antes de la carga de una escena de iluminación | | • |
`OnLightingLoaded` | Una vez que una escena de iluminación se ha cargado y activado por completo| | • |
`OnWillUnloadLighting` | Justo antes de que se descargue una escena de iluminación | | • |
`OnLightingUnloaded` | Una vez que se ha descargado completamente una escena de iluminación | | • |
`OnWillLoadScene` | Justo antes de una carga de escena | • | • | •
`OnSceneLoaded` | Una vez que todas las escenas de una operación están totalmente cargadas y activadas | • | • | •
`OnWillUnloadScene` | Justo antes de la descarga de una escena | • | • | •
`OnSceneUnloaded` | Una vez que una escena se descarga completamente |  • | • | •

### <a name="action-examples"></a>Ejemplos de acciones

Otro ejemplo de diálogo de progreso mediante acciones y una corertina en lugar de Actualizar:

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a>Control de la activación de la escena

De forma predeterminada, las escenas de contenido se establecen para activarse cuando se cargan. Si desea controlar manualmente la activación de la escena, puede pasar un a `SceneActivationToken` cualquier método de carga de contenido. Si una sola operación carga varias escenas de contenido, este token de activación se aplicará a todas las escenas.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a>Comprobación del contenido que se carga

La `ContentSceneNames` propiedad proporciona una matriz de escenas de contenido disponibles en orden de índice de compilación. Puede comprobar si estas escenas se cargan a través de `IsContentLoaded(string contentName)` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
