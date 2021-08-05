---
title: Servicio de transición de escenas
description: documentación sobre la transición de escena en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, SceneTransition,
ms.openlocfilehash: a66922f1c9d58018ee856c3054aa71f5213ec690c5f4780b32fd735eb59f2ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189237"
---
# <a name="scene-transition-service"></a>Servicio de transición de escenas

Esta extensión simplifica el negocio de desvanechar una escena, mostrar un indicador de progreso, cargar una escena y, a continuación, volver a desvanerse.

Las operaciones de escena están controladas por el servicio SceneSystem, pero cualquier operación basada en tareas se puede usar para impulsar una transición.

## <a name="enabling-the-extension"></a>Habilitación de la extensión

Para habilitar la extensión, abra el perfil registeredServiceProvider. Haga clic en Registrar un nuevo proveedor de servicios para agregar una nueva configuración. En el campo Tipo de componente, seleccione SceneTransitionService. En el campo Perfil de configuración, seleccione el perfil de transición de escena predeterminado incluido con la extensión.

## <a name="profile-options"></a>Opciones de perfil

### <a name="use-default-progress-indicator"></a>Uso del indicador de progreso predeterminado

Si está activada, se usará el objeto prefab del indicador de progreso predeterminado cuando no se proporciona ningún objeto de indicador de progreso al llamar a Si se proporciona un objeto de indicador de progreso, se omitirá `DoSceneTransition.` el valor predeterminado.

### <a name="use-fade-color"></a>Uso del color de atenuación

Si está activada, el servicio de transición aplicará un atenuación durante la transición. Esta configuración se puede cambiar en tiempo de ejecución a través de la propiedad del `UseFadeColor` servicio.

### <a name="fade-color"></a>Color de atenuación

Controla el color del efecto de atenuación. Se omite Alpha. Esta configuración se puede cambiar en tiempo de ejecución antes de una transición a través de la propiedad del `FadeColor` servicio.

### <a name="fade-targets"></a>Destinos de atenuación

Controla qué cámaras tendrán aplicado un efecto de atenuación. Esta configuración se puede cambiar en tiempo de ejecución a través de la propiedad del `FadeTargets` servicio.

Setting | Cámaras de destino
--- | --- | ---
Método Main | Aplica el efecto de atenuación a la cámara principal.
UI | Aplica el efecto de atenuación a las cámaras de la capa de interfaz de usuario. (No afecta a la interfaz de usuario superpuesta)
Todos | Se aplica a las cámaras principal y de interfaz de usuario.
Personalizado | Se aplica a un conjunto personalizado de cámaras proporcionadas a través de `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Tiempo de espera de atenuación/atenuación en el tiempo

Configuración predeterminada para la duración de un desvanecimiento al entrar o salir de una transición. Esta configuración se puede cambiar en tiempo de ejecución a través de las propiedades `FadeOutTime` y del `FadeInTime` servicio.

### <a name="camera-fader-type"></a>Tipo de atenuador de cámara

Clase `ICameraFader` que se va a usar para aplicar un efecto de atenuación a las cámaras. La clase `CameraFaderQuad` predeterminada crea una instancia de un cuadrántico con un material transparente delante de la cámara de destino cerca del plano de recorte. Otro enfoque podría ser usar un sistema de efectos posteriores.

## <a name="using-the-extension"></a>Uso de la extensión

Para usar el servicio de transición, pase las tareas que se ejecutan mientras la cámara está atenuada.

### <a name="using-scene-system-tasks"></a>Uso de tareas del sistema de escena

En la mayoría de los casos, se usarán las tareas proporcionadas por el servicio SceneSystem:

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

### <a name="using-custom-tasks"></a>Uso de tareas personalizadas

En otros casos, puede que desee realizar una transición sin cargar realmente una escena:

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

O bien, puede que quiera cargar una escena sin usar el servicio SceneSystem:

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

### <a name="using-multiple-tasks"></a>Uso de varias tareas

También puede proporcionar varias tareas, que se ejecutarán en orden:

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

## <a name="using-the-progress-indicator"></a>Uso del indicador de progreso

Un indicador de progreso es todo lo que implementa la `IProgressIndicator` interfaz . Esto puede tener la forma de una pantalla de presentación, un indicador de carga de etiquetas 3D o cualquier otra cosa que proporciona comentarios sobre el progreso de la transición.

Si `UseDefaultProgressIndicator` está activada en el perfil SceneTransitionService, se crea una instancia de un indicador de progreso cuando se inicia una transición. Durante la transición, se puede acceder a las propiedades y de este indicador a través de `Progress` `Message` los métodos y de ese `SetProgressValue` `SetProgressMessage` servicio.

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

Como alternativa, al llamar `DoSceneTransition` a , puede proporcionar su propio indicador de progreso a través del argumento `progressIndicator` opcional. Esto invalidará el indicador de progreso predeterminado.
