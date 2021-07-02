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
# <a name="progress-indicator"></a><span data-ttu-id="8dffd-104">Indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="8dffd-104">Progress indicator</span></span>

![Indicadores de progreso](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="8dffd-106">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="8dffd-106">Example scene</span></span>

<span data-ttu-id="8dffd-107">En la escena se pueden encontrar ejemplos de cómo usar indicadores `ProgressIndicatorExamples` de progreso.</span><span class="sxs-lookup"><span data-stu-id="8dffd-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="8dffd-108">En esta escena se muestra cada uno de los objetos prefabs del indicador de progreso incluidos en el SDK.</span><span class="sxs-lookup"><span data-stu-id="8dffd-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="8dffd-109">También se muestra cómo usar indicadores de progreso junto con algunas tareas asincrónicas comunes, como la carga de escena.</span><span class="sxs-lookup"><span data-stu-id="8dffd-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="8dffd-110">Ejemplo: Abrir, actualizar & cerrar un indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="8dffd-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="8dffd-111">Los indicadores de progreso implementan la [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interfaz .</span><span class="sxs-lookup"><span data-stu-id="8dffd-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="8dffd-112">Esta interfaz se puede recuperar de un Elemento GameObject mediante `GetComponent` .</span><span class="sxs-lookup"><span data-stu-id="8dffd-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="8dffd-113">Los `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` métodos y devuelven [Tasks](xref:System.Threading.Tasks.Task).</span><span class="sxs-lookup"><span data-stu-id="8dffd-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="8dffd-114">Se recomienda esperar estas tareas en un método asincrónico.</span><span class="sxs-lookup"><span data-stu-id="8dffd-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="8dffd-115">Los objetos prefabs del indicador de progreso predeterminado de MRTK deben estar inactivos cuando se colocan en una escena.</span><span class="sxs-lookup"><span data-stu-id="8dffd-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="8dffd-116">Cuando se `IProgressIndicator.OpenAsync()` llama a sus métodos, los indicadores de progreso se activarán y desactivarán automáticamente sus objetos gameobject.</span><span class="sxs-lookup"><span data-stu-id="8dffd-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="8dffd-117">(Este patrón no es un requisito de la interfaz IProgressIndicator).</span><span class="sxs-lookup"><span data-stu-id="8dffd-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="8dffd-118">Establezca la propiedad del `Progress` indicador en un valor de 0-1 para actualizar su progreso mostrado.</span><span class="sxs-lookup"><span data-stu-id="8dffd-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="8dffd-119">Establezca su `Message` propiedad para actualizar el mensaje que se muestra.</span><span class="sxs-lookup"><span data-stu-id="8dffd-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="8dffd-120">Diferentes implementaciones pueden mostrar este contenido de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="8dffd-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="8dffd-121">Estados de indicador</span><span class="sxs-lookup"><span data-stu-id="8dffd-121">Indicator states</span></span>

<span data-ttu-id="8dffd-122">La propiedad de un `State` indicador determina qué operaciones son válidas.</span><span class="sxs-lookup"><span data-stu-id="8dffd-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="8dffd-123">Llamar a un método no válido normalmente hará que el indicador informe de un error y no realiza ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="8dffd-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="8dffd-124">Estado</span><span class="sxs-lookup"><span data-stu-id="8dffd-124">State</span></span> | <span data-ttu-id="8dffd-125">Operaciones válidas</span><span class="sxs-lookup"><span data-stu-id="8dffd-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="8dffd-126">`AwaitTransitionAsync()` se puede usar para asegurarse de que un indicador está completamente abierto o cerrado antes de usarlo.</span><span class="sxs-lookup"><span data-stu-id="8dffd-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
