---
title: ProgressIndicator
description: Información general del indicador de progreso en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110122"
---
# <a name="progress-indicators"></a><span data-ttu-id="5040c-104">Indicadores de progreso</span><span class="sxs-lookup"><span data-stu-id="5040c-104">Progress Indicators</span></span>

![Indicadores de progreso](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="5040c-106">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="5040c-106">Example scene</span></span>

<span data-ttu-id="5040c-107">En la escena se pueden encontrar ejemplos de cómo usar indicadores de `ProgressIndicatorExamples` progreso.</span><span class="sxs-lookup"><span data-stu-id="5040c-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="5040c-108">En esta escena se muestra cada uno de los requisitos previos del indicador de progreso incluidos en el SDK.</span><span class="sxs-lookup"><span data-stu-id="5040c-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="5040c-109">También muestra cómo usar indicadores de progreso junto con algunas tareas asincrónicas comunes, como la carga de escenas.</span><span class="sxs-lookup"><span data-stu-id="5040c-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="5040c-110">Ejemplo: Abrir, actualizar & cerrar un indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="5040c-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="5040c-111">Los indicadores de progreso implementan la [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interfaz .</span><span class="sxs-lookup"><span data-stu-id="5040c-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="5040c-112">Esta interfaz se puede recuperar de un Objeto GameObject mediante `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="5040c-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="5040c-113">Los `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` métodos y devuelven [Tasks](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="5040c-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="5040c-114">Se recomienda esperar estas tareas en un método asincrónico.</span><span class="sxs-lookup"><span data-stu-id="5040c-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="5040c-115">Los objetos prefabs del indicador de progreso predeterminado de MRTK deben estar inactivos cuando se colocan en una escena.</span><span class="sxs-lookup"><span data-stu-id="5040c-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="5040c-116">Cuando se `IProgressIndicator.OpenAsync()` llama a sus métodos, los indicadores de progreso se activarán y desactivarán sus objetos gameobject automáticamente.</span><span class="sxs-lookup"><span data-stu-id="5040c-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="5040c-117">(Este patrón no es un requisito de la interfaz IProgressIndicator).</span><span class="sxs-lookup"><span data-stu-id="5040c-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="5040c-118">Establezca la propiedad del `Progress` indicador en un valor de 0 a 1 para actualizar su progreso mostrado.</span><span class="sxs-lookup"><span data-stu-id="5040c-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="5040c-119">Establezca su `Message` propiedad para actualizar el mensaje que se muestra.</span><span class="sxs-lookup"><span data-stu-id="5040c-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="5040c-120">Diferentes implementaciones pueden mostrar este contenido de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="5040c-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="5040c-121">Estados del indicador</span><span class="sxs-lookup"><span data-stu-id="5040c-121">Indicator states</span></span>

<span data-ttu-id="5040c-122">La propiedad de un `State` indicador determina qué operaciones son válidas.</span><span class="sxs-lookup"><span data-stu-id="5040c-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="5040c-123">Llamar a un método no válido normalmente hará que el indicador informe de un error y no realiza ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="5040c-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="5040c-124">Estado</span><span class="sxs-lookup"><span data-stu-id="5040c-124">State</span></span> | <span data-ttu-id="5040c-125">Operaciones válidas</span><span class="sxs-lookup"><span data-stu-id="5040c-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="5040c-126">`AwaitTransitionAsync()` se puede usar para asegurarse de que un indicador está totalmente abierto o cerrado antes de usarlo.</span><span class="sxs-lookup"><span data-stu-id="5040c-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
