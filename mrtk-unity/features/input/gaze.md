---
title: Mirar
description: Docummentation on types of Gaze in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, Gaze,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176917"
---
# <a name="gaze"></a><span data-ttu-id="bd394-104">Mirar</span><span class="sxs-lookup"><span data-stu-id="bd394-104">Gaze</span></span>

<span data-ttu-id="bd394-105">[La](/windows/mixed-reality/gaze) mirada es una forma de entrada que interactúa con el mundo en función de dónde esté mirando el usuario.</span><span class="sxs-lookup"><span data-stu-id="bd394-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="bd394-106">La mirada existe en dos tipos diferentes</span><span class="sxs-lookup"><span data-stu-id="bd394-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="bd394-107">Mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="bd394-107">Head gaze</span></span>

<span data-ttu-id="bd394-108">Este tipo de mirada se basa en la dirección que mira la cabeza o la cámara.</span><span class="sxs-lookup"><span data-stu-id="bd394-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="bd394-109">La mirada con la cabeza está activa en sistemas que no admiten la mirada con los ojos o en [casos](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) en los que el hardware puede admitir la mirada con los ojos, pero no se ha realizado el conjunto correcto de permisos y configuración.</span><span class="sxs-lookup"><span data-stu-id="bd394-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="bd394-110">La mirada con la cabeza suele asociarse HoloLens interacciones de estilo 1 que implican mirar el objeto colocándolo en el centro del marco holográfico y, a continuación, realizando el gesto de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="bd394-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="bd394-111">Mirada con ojo</span><span class="sxs-lookup"><span data-stu-id="bd394-111">Eye gaze</span></span>

<span data-ttu-id="bd394-112">Este tipo de mirada se basa en la mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="bd394-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="bd394-113">La mirada con los ojos solo está presente en sistemas que admiten el seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="bd394-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="bd394-114">Consulte la documentación [de seguimiento de los](eye-tracking/eye-tracking-main.md) ojos para obtener más información sobre cómo usar la mirada con los ojos.</span><span class="sxs-lookup"><span data-stu-id="bd394-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="bd394-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="bd394-115">GazeProvider</span></span>

<span data-ttu-id="bd394-116">Gaze functionality (head and eye) (Funcionalidad de mirada (tanto la cabeza como el ojo) la [proporciona GazeProvider.](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)</span><span class="sxs-lookup"><span data-stu-id="bd394-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="bd394-117">Este proveedor se puede configurar en la sección *Puntero* del perfil del sistema de entrada:</span><span class="sxs-lookup"><span data-stu-id="bd394-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![Punto de entrada de configuración de mirada](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="bd394-119">Al igual que otros orígenes de entrada, el proveedor de mirada interactúa con los objetos de la escena mediante el uso de un puntero (vea este documento para obtener información [sobre punteros).](../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="bd394-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="bd394-120">En el caso del proveedor de mirada, su puntero se implementa a través `InternalGazePointer` de y no se configura a través de un perfil.</span><span class="sxs-lookup"><span data-stu-id="bd394-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="bd394-121">Es posible reemplazar gazeprovider de acciones por  una implementación alternativa cambiando tipo de proveedor de mirada para hacer referencia a una clase diferente que implementa [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) e [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span><span class="sxs-lookup"><span data-stu-id="bd394-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="bd394-122">Por lo general, se recomienda usar GazeProvider (y presentar problemas al encontrar errores), ya que volver a implementar GazeProvider no es trivial.</span><span class="sxs-lookup"><span data-stu-id="bd394-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="bd394-123">Posturas alternativas de mirada proporcionadas por la plataforma</span><span class="sxs-lookup"><span data-stu-id="bd394-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="bd394-124">De forma predeterminada, MRTK GazeProvider usa el centro del marco de la cámara como origen de la mirada.</span><span class="sxs-lookup"><span data-stu-id="bd394-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="bd394-125">Algunas plataformas, como Windows Mixed Reality en HoloLens 2, proporcionan una posición de mirada definida alternativamente.</span><span class="sxs-lookup"><span data-stu-id="bd394-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="bd394-126">Esto se administra a través de `Use Head Gaze Override` la configuración en la configuración de mirada.</span><span class="sxs-lookup"><span data-stu-id="bd394-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="bd394-127">Cuando se habilita, se usará la invalidación de mirada alternativa.</span><span class="sxs-lookup"><span data-stu-id="bd394-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="bd394-128">Cuando se deshabilita, se usará el origen del centro de marco predeterminado.</span><span class="sxs-lookup"><span data-stu-id="bd394-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="bd394-129">En concreto, para HoloLens 2, el ángulo de mirada se elevará varios grados para tener en cuenta la comodidad del usuario al usar la cabeza para la orientación.</span><span class="sxs-lookup"><span data-stu-id="bd394-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="bd394-130">Uso</span><span class="sxs-lookup"><span data-stu-id="bd394-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="bd394-131">Cómo obtener el destino de mirada actual</span><span class="sxs-lookup"><span data-stu-id="bd394-131">How get the current gaze target</span></span>

<span data-ttu-id="bd394-132">En este ejemplo se muestra cómo obtener el objeto de juego actual que es el objetivo de la mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="bd394-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="bd394-133">Cómo obtener la dirección y el origen de la mirada actuales</span><span class="sxs-lookup"><span data-stu-id="bd394-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="bd394-134">En este ejemplo se muestra cómo obtener vector3 que representa la dirección de la mirada del usuario y el origen (el punto desde el que se va la dirección).</span><span class="sxs-lookup"><span data-stu-id="bd394-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
