---
title: Indicador de progreso
description: Información general del indicador de progreso en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 268d13d00bc0bcf1d522eaa6809dab9892624e11
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176574"
---
# <a name="progress-indicator"></a>Indicador de progreso

![Indicadores de progreso](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Escena de ejemplo

En la escena se pueden encontrar ejemplos de cómo usar indicadores `ProgressIndicatorExamples` de progreso. En esta escena se muestra cada uno de los objetos prefabs del indicador de progreso incluidos en el SDK. También se muestra cómo usar indicadores de progreso junto con algunas tareas asincrónicas comunes, como la carga de escena.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>Ejemplo: Abrir, actualizar & cerrar un indicador de progreso

Los indicadores de progreso implementan la [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interfaz . Esta interfaz se puede recuperar de un Elemento GameObject mediante `GetComponent` .

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

Los `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` métodos y devuelven [Tasks](xref:System.Threading.Tasks.Task). Se recomienda esperar estas tareas en un método asincrónico.

Los objetos prefabs del indicador de progreso predeterminado de MRTK deben estar inactivos cuando se colocan en una escena. Cuando se `IProgressIndicator.OpenAsync()` llama a sus métodos, los indicadores de progreso se activarán y desactivarán automáticamente sus objetos gameobject. (Este patrón no es un requisito de la interfaz IProgressIndicator).

Establezca la propiedad del `Progress` indicador en un valor de 0-1 para actualizar su progreso mostrado. Establezca su `Message` propiedad para actualizar el mensaje que se muestra. Diferentes implementaciones pueden mostrar este contenido de maneras diferentes.

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>Estados de indicador

La propiedad de un `State` indicador determina qué operaciones son válidas. Llamar a un método no válido normalmente hará que el indicador informe de un error y no realiza ninguna acción.

Estado | Operaciones válidas
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` se puede usar para asegurarse de que un indicador está completamente abierto o cerrado antes de usarlo.

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
