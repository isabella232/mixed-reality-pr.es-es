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
# <a name="monitoring-content-loading"></a><span data-ttu-id="c3bc2-104">Supervisión de la carga de contenido</span><span class="sxs-lookup"><span data-stu-id="c3bc2-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="c3bc2-105">Progreso de la operación de escena</span><span class="sxs-lookup"><span data-stu-id="c3bc2-105">Scene operation progress</span></span>

<span data-ttu-id="c3bc2-106">Cuando se carga o descarga contenido, la `SceneOperationInProgress` propiedad devuelve true.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="c3bc2-107">Puede supervisar el progreso de esta operación a través de la `SceneOperationProgress` propiedad .</span><span class="sxs-lookup"><span data-stu-id="c3bc2-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="c3bc2-108">El `SceneOperationProgress` valor es el promedio de todas las operaciones de escena asincrónicas actuales.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="c3bc2-109">Al principio de una carga de contenido, `SceneOperationProgress` será cero.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="c3bc2-110">Una vez completado por `SceneOperationProgress` completo, se establecerá en 1 y permanecerá en 1 hasta que se lleve a cabo la siguiente operación.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="c3bc2-111">Tenga en cuenta que solo las operaciones de escena de contenido afectan a estas propiedades.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="c3bc2-112">Estas propiedades reflejan el estado de una *operación completa* de principio a fin, incluso si esa operación incluye varios pasos:</span><span class="sxs-lookup"><span data-stu-id="c3bc2-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

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

### <a name="progress-examples"></a><span data-ttu-id="c3bc2-113">Ejemplos de progreso</span><span class="sxs-lookup"><span data-stu-id="c3bc2-113">Progress examples</span></span>

<span data-ttu-id="c3bc2-114">`SceneOperationInProgress` puede ser útil si se debe suspender la actividad mientras se carga contenido:</span><span class="sxs-lookup"><span data-stu-id="c3bc2-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

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

<span data-ttu-id="c3bc2-115">`SceneOperationProgress` se puede usar para mostrar diálogos de progreso:</span><span class="sxs-lookup"><span data-stu-id="c3bc2-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

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

## <a name="monitoring-with-actions"></a><span data-ttu-id="c3bc2-116">Supervisión con acciones</span><span class="sxs-lookup"><span data-stu-id="c3bc2-116">Monitoring with actions</span></span>

<span data-ttu-id="c3bc2-117">Scene System proporciona varias acciones para que sepa cuándo se cargan o descargan las escenas.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="c3bc2-118">Cada acción retransmite el nombre de la escena afectada.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="c3bc2-119">Si una operación de carga o descarga implica varias escenas, las acciones pertinentes se invocarán una vez por cada escena afectada.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="c3bc2-120">También se invocan todas a la vez cuando la operación de carga o descarga se *completa.*</span><span class="sxs-lookup"><span data-stu-id="c3bc2-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="c3bc2-121">Por este motivo, se recomienda usar acciones *OnWillUnload* para detectar el contenido que se destruirá, en lugar de usar acciones *OnUnloaded* para detectar contenido destructor después del hecho. </span><span class="sxs-lookup"><span data-stu-id="c3bc2-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="c3bc2-122">Por otro lado, dado que las acciones *OnLoaded* solo se invocan cuando todas las escenas se activan y se cargan por completo, se garantiza que el uso de acciones *OnLoaded* para detectar y usar contenido nuevo sea seguro.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="c3bc2-123">Acción</span><span class="sxs-lookup"><span data-stu-id="c3bc2-123">Action</span></span> | <span data-ttu-id="c3bc2-124">Cuando se invoca</span><span class="sxs-lookup"><span data-stu-id="c3bc2-124">When it's invoked</span></span> | <span data-ttu-id="c3bc2-125">Escenas de contenido</span><span class="sxs-lookup"><span data-stu-id="c3bc2-125">Content Scenes</span></span> | <span data-ttu-id="c3bc2-126">Escenas de iluminación</span><span class="sxs-lookup"><span data-stu-id="c3bc2-126">Lighting Scenes</span></span> | <span data-ttu-id="c3bc2-127">Escenas de administrador</span><span class="sxs-lookup"><span data-stu-id="c3bc2-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="c3bc2-128">Justo antes de cargar una escena de contenido</span><span class="sxs-lookup"><span data-stu-id="c3bc2-128">Just prior to a content scene load</span></span> | <span data-ttu-id="c3bc2-129">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="c3bc2-130">Una vez que todas las escenas de contenido de una operación de carga se han cargado y activado por completo</span><span class="sxs-lookup"><span data-stu-id="c3bc2-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="c3bc2-131">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="c3bc2-132">Justo antes de una operación de descarga de la escena de contenido</span><span class="sxs-lookup"><span data-stu-id="c3bc2-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="c3bc2-133">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="c3bc2-134">Una vez que se han descargado completamente todas las escenas de contenido de una operación de descarga</span><span class="sxs-lookup"><span data-stu-id="c3bc2-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="c3bc2-135">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="c3bc2-136">Justo antes de la carga de una escena de iluminación</span><span class="sxs-lookup"><span data-stu-id="c3bc2-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="c3bc2-137">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="c3bc2-138">Una vez que una escena de iluminación se ha cargado y activado por completo</span><span class="sxs-lookup"><span data-stu-id="c3bc2-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="c3bc2-139">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="c3bc2-140">Justo antes de que se descargue una escena de iluminación</span><span class="sxs-lookup"><span data-stu-id="c3bc2-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="c3bc2-141">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="c3bc2-142">Una vez que se ha descargado completamente una escena de iluminación</span><span class="sxs-lookup"><span data-stu-id="c3bc2-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="c3bc2-143">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="c3bc2-144">Justo antes de una carga de escena</span><span class="sxs-lookup"><span data-stu-id="c3bc2-144">Just prior to a scene load</span></span> | <span data-ttu-id="c3bc2-145">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-145">•</span></span> | <span data-ttu-id="c3bc2-146">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-146">•</span></span> | <span data-ttu-id="c3bc2-147">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="c3bc2-148">Una vez que todas las escenas de una operación están totalmente cargadas y activadas</span><span class="sxs-lookup"><span data-stu-id="c3bc2-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="c3bc2-149">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-149">•</span></span> | <span data-ttu-id="c3bc2-150">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-150">•</span></span> | <span data-ttu-id="c3bc2-151">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="c3bc2-152">Justo antes de la descarga de una escena</span><span class="sxs-lookup"><span data-stu-id="c3bc2-152">Just prior to a scene unload</span></span> | <span data-ttu-id="c3bc2-153">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-153">•</span></span> | <span data-ttu-id="c3bc2-154">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-154">•</span></span> | <span data-ttu-id="c3bc2-155">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="c3bc2-156">Una vez que una escena se descarga completamente</span><span class="sxs-lookup"><span data-stu-id="c3bc2-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="c3bc2-157">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-157">•</span></span> | <span data-ttu-id="c3bc2-158">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-158">•</span></span> | <span data-ttu-id="c3bc2-159">•</span><span class="sxs-lookup"><span data-stu-id="c3bc2-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="c3bc2-160">Ejemplos de acciones</span><span class="sxs-lookup"><span data-stu-id="c3bc2-160">Action examples</span></span>

<span data-ttu-id="c3bc2-161">Otro ejemplo de diálogo de progreso mediante acciones y una corertina en lugar de Actualizar:</span><span class="sxs-lookup"><span data-stu-id="c3bc2-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

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

## <a name="controlling-scene-activation"></a><span data-ttu-id="c3bc2-162">Control de la activación de la escena</span><span class="sxs-lookup"><span data-stu-id="c3bc2-162">Controlling scene activation</span></span>

<span data-ttu-id="c3bc2-163">De forma predeterminada, las escenas de contenido se establecen para activarse cuando se cargan.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="c3bc2-164">Si desea controlar manualmente la activación de la escena, puede pasar un a `SceneActivationToken` cualquier método de carga de contenido.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="c3bc2-165">Si una sola operación carga varias escenas de contenido, este token de activación se aplicará a todas las escenas.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

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

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="c3bc2-166">Comprobación del contenido que se carga</span><span class="sxs-lookup"><span data-stu-id="c3bc2-166">Checking which content is loaded</span></span>

<span data-ttu-id="c3bc2-167">La `ContentSceneNames` propiedad proporciona una matriz de escenas de contenido disponibles en orden de índice de compilación.</span><span class="sxs-lookup"><span data-stu-id="c3bc2-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="c3bc2-168">Puede comprobar si estas escenas se cargan a través de `IsContentLoaded(string contentName)` .</span><span class="sxs-lookup"><span data-stu-id="c3bc2-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
