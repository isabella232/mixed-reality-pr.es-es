---
title: Información general del servicio Scene Transition
description: documentación de Scene Transition en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, SceneTransition,
ms.openlocfilehash: 5ea76b572b3cddc097e8266d3c31f152b63a13aa
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144279"
---
# <a name="scene-transition-service"></a><span data-ttu-id="63e31-104">Servicio de transición de escena</span><span class="sxs-lookup"><span data-stu-id="63e31-104">Scene transition service</span></span>

<span data-ttu-id="63e31-105">Esta extensión simplifica el negocio de desvanechar una escena, mostrar un indicador de progreso, cargar una escena y, a continuación, volver a desvanerse.</span><span class="sxs-lookup"><span data-stu-id="63e31-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="63e31-106">Las operaciones de escena están controladas por el servicio SceneSystem, pero cualquier operación basada en tareas se puede usar para impulsar una transición.</span><span class="sxs-lookup"><span data-stu-id="63e31-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="63e31-107">Habilitación de la extensión</span><span class="sxs-lookup"><span data-stu-id="63e31-107">Enabling the extension</span></span>

<span data-ttu-id="63e31-108">Para habilitar la extensión, abra el perfil RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="63e31-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="63e31-109">Haga clic en Registrar un nuevo proveedor de servicios para agregar una nueva configuración.</span><span class="sxs-lookup"><span data-stu-id="63e31-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="63e31-110">En el campo Tipo de componente, seleccione SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="63e31-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="63e31-111">En el campo Perfil de configuración, seleccione el perfil de transición de escena predeterminado incluido con la extensión.</span><span class="sxs-lookup"><span data-stu-id="63e31-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="63e31-112">Opciones de perfil</span><span class="sxs-lookup"><span data-stu-id="63e31-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="63e31-113">Uso del indicador de progreso predeterminado</span><span class="sxs-lookup"><span data-stu-id="63e31-113">Use default progress indicator</span></span>

<span data-ttu-id="63e31-114">Si está activada, se usará el prefab del indicador de progreso predeterminado cuando no se proporciona ningún objeto de indicador de progreso al llamar a Si se proporciona un objeto de indicador de progreso, se omitirá `DoSceneTransition.` el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="63e31-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="63e31-115">Uso del color de atenuación</span><span class="sxs-lookup"><span data-stu-id="63e31-115">Use fade color</span></span>

<span data-ttu-id="63e31-116">Si está activada, el servicio de transición aplicará un atenuación durante la transición.</span><span class="sxs-lookup"><span data-stu-id="63e31-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="63e31-117">Esta configuración se puede cambiar en tiempo de ejecución a través de la propiedad del `UseFadeColor` servicio.</span><span class="sxs-lookup"><span data-stu-id="63e31-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="63e31-118">Color de atenuación</span><span class="sxs-lookup"><span data-stu-id="63e31-118">Fade color</span></span>

<span data-ttu-id="63e31-119">Controla el color del efecto de atenuación.</span><span class="sxs-lookup"><span data-stu-id="63e31-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="63e31-120">Se omite Alpha.</span><span class="sxs-lookup"><span data-stu-id="63e31-120">Alpha is ignored.</span></span> <span data-ttu-id="63e31-121">Esta configuración se puede cambiar en tiempo de ejecución antes de una transición a través de la propiedad del `FadeColor` servicio.</span><span class="sxs-lookup"><span data-stu-id="63e31-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="63e31-122">Destinos de atenuación</span><span class="sxs-lookup"><span data-stu-id="63e31-122">Fade targets</span></span>

<span data-ttu-id="63e31-123">Controla qué cámaras tendrán aplicado un efecto de atenuación.</span><span class="sxs-lookup"><span data-stu-id="63e31-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="63e31-124">Esta configuración se puede cambiar en tiempo de ejecución a través de la propiedad del `FadeTargets` servicio.</span><span class="sxs-lookup"><span data-stu-id="63e31-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="63e31-125">Configuración</span><span class="sxs-lookup"><span data-stu-id="63e31-125">Setting</span></span> | <span data-ttu-id="63e31-126">Cámaras de destino</span><span class="sxs-lookup"><span data-stu-id="63e31-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="63e31-127">Principal</span><span class="sxs-lookup"><span data-stu-id="63e31-127">Main</span></span> | <span data-ttu-id="63e31-128">Aplica el efecto de atenuación a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="63e31-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="63e31-129">UI</span><span class="sxs-lookup"><span data-stu-id="63e31-129">UI</span></span> | <span data-ttu-id="63e31-130">Aplica el efecto de atenuación a las cámaras de la capa de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="63e31-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="63e31-131">(No afecta a la interfaz de usuario superpuesta)</span><span class="sxs-lookup"><span data-stu-id="63e31-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="63e31-132">Todo</span><span class="sxs-lookup"><span data-stu-id="63e31-132">All</span></span> | <span data-ttu-id="63e31-133">Se aplica a las cámaras principal y de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="63e31-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="63e31-134">Personalizado</span><span class="sxs-lookup"><span data-stu-id="63e31-134">Custom</span></span> | <span data-ttu-id="63e31-135">Se aplica a un conjunto personalizado de cámaras proporcionadas a través de `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="63e31-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="63e31-136">Tiempo de espera de atenuación/atenuación en el tiempo</span><span class="sxs-lookup"><span data-stu-id="63e31-136">Fade out time / fade in time</span></span>

<span data-ttu-id="63e31-137">Configuración predeterminada para la duración de un desvanecimiento al entrar o salir de una transición.</span><span class="sxs-lookup"><span data-stu-id="63e31-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="63e31-138">Esta configuración se puede cambiar en tiempo de ejecución a través de las propiedades `FadeOutTime` y del `FadeInTime` servicio.</span><span class="sxs-lookup"><span data-stu-id="63e31-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="63e31-139">Tipo de atenuador de cámara</span><span class="sxs-lookup"><span data-stu-id="63e31-139">Camera fader type</span></span>

<span data-ttu-id="63e31-140">Clase `ICameraFader` que se va a usar para aplicar un efecto de atenuación a las cámaras.</span><span class="sxs-lookup"><span data-stu-id="63e31-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="63e31-141">La clase `CameraFaderQuad` predeterminada crea una instancia de un cuadrántico con un material transparente delante de la cámara de destino cerca del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="63e31-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="63e31-142">Otro enfoque podría ser usar un sistema de efectos posteriores.</span><span class="sxs-lookup"><span data-stu-id="63e31-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="63e31-143">Uso de la extensión</span><span class="sxs-lookup"><span data-stu-id="63e31-143">Using the extension</span></span>

<span data-ttu-id="63e31-144">Para usar el servicio de transición, pase las tareas que se ejecutan mientras la cámara está atenuada.</span><span class="sxs-lookup"><span data-stu-id="63e31-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="63e31-145">Uso de tareas del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="63e31-145">Using scene system tasks</span></span>

<span data-ttu-id="63e31-146">En la mayoría de los casos, se usarán las tareas proporcionadas por el servicio SceneSystem:</span><span class="sxs-lookup"><span data-stu-id="63e31-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a><span data-ttu-id="63e31-147">Uso de tareas personalizadas</span><span class="sxs-lookup"><span data-stu-id="63e31-147">Using custom tasks</span></span>

<span data-ttu-id="63e31-148">En otros casos, es posible que quiera realizar una transición sin cargar realmente una escena:</span><span class="sxs-lookup"><span data-stu-id="63e31-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

<span data-ttu-id="63e31-149">O bien, puede que quiera cargar una escena sin usar el servicio SceneSystem:</span><span class="sxs-lookup"><span data-stu-id="63e31-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a><span data-ttu-id="63e31-150">Uso de varias tareas</span><span class="sxs-lookup"><span data-stu-id="63e31-150">Using multiple tasks</span></span>

<span data-ttu-id="63e31-151">También puede proporcionar varias tareas, que se ejecutarán en orden:</span><span class="sxs-lookup"><span data-stu-id="63e31-151">You can also supply multiple tasks, which will be executed in order:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a><span data-ttu-id="63e31-152">Uso del indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="63e31-152">Using the progress indicator</span></span>

<span data-ttu-id="63e31-153">Un indicador de progreso es cualquier cosa que implementa la `IProgressIndicator` interfaz .</span><span class="sxs-lookup"><span data-stu-id="63e31-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="63e31-154">Esto puede tener la forma de una pantalla de presentación, un indicador de carga de etiquetas 3D o cualquier otra cosa que proporciona comentarios sobre el progreso de la transición.</span><span class="sxs-lookup"><span data-stu-id="63e31-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="63e31-155">Si `UseDefaultProgressIndicator` está activada en el perfil SceneTransitionService, se crea una instancia de un indicador de progreso cuando se inicia una transición.</span><span class="sxs-lookup"><span data-stu-id="63e31-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="63e31-156">Durante la transición, se puede acceder a las propiedades y de este indicador a través de `Progress` `Message` los métodos y de ese `SetProgressValue` `SetProgressMessage` servicio.</span><span class="sxs-lookup"><span data-stu-id="63e31-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

<span data-ttu-id="63e31-157">Como alternativa, al llamar `DoSceneTransition` a , puede proporcionar su propio indicador de progreso a través del argumento `progressIndicator` opcional.</span><span class="sxs-lookup"><span data-stu-id="63e31-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="63e31-158">Esto invalidará el indicador de progreso predeterminado.</span><span class="sxs-lookup"><span data-stu-id="63e31-158">This will override the default progress indicator.</span></span>
