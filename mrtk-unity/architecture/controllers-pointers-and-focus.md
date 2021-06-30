---
title: Controladores, punteros y foco
description: Interactuar con controladores, punteros y foco.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, punteros, controladores
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121623"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="7caf7-104">Controladores, punteros y foco</span><span class="sxs-lookup"><span data-stu-id="7caf7-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="7caf7-105">Los controladores, los punteros y el foco son conceptos de nivel superior que se basa en la base establecida por el sistema de entrada principal.</span><span class="sxs-lookup"><span data-stu-id="7caf7-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="7caf7-106">Juntos, proporcionan una gran parte del mecanismo para interactuar con los objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="7caf7-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="7caf7-107">Controladores</span><span class="sxs-lookup"><span data-stu-id="7caf7-107">Controllers</span></span>

<span data-ttu-id="7caf7-108">Los controladores son representaciones de un controlador físico (6 grados de libertad, mano articulada, etc.).</span><span class="sxs-lookup"><span data-stu-id="7caf7-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="7caf7-109">Los administradores de dispositivos los crean y son responsables de comunicarse con el sistema subyacente correspondiente y traducirlos en datos y eventos con forma de MRTK.</span><span class="sxs-lookup"><span data-stu-id="7caf7-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="7caf7-110">Por ejemplo, en la plataforma Windows Mixed Reality, es un controlador responsable de la interacción con las API de seguimiento de manos subyacentes de Windows para obtener información sobre las uniones, la posición y otras propiedades de la [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) mano. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)</span><span class="sxs-lookup"><span data-stu-id="7caf7-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="7caf7-111">Es responsable de convertir estos datos en eventos DE MRTK pertinentes (por ejemplo, llamando a RaisePoseInputChanged o RaiseHandJointsUpdated) y actualizando su propio estado interno para que las consultas de devuelvan los datos [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) correctos.</span><span class="sxs-lookup"><span data-stu-id="7caf7-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="7caf7-112">Por lo general, el ciclo de vida de un controlador implicará:</span><span class="sxs-lookup"><span data-stu-id="7caf7-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="7caf7-113">Un administrador de dispositivos crea un controlador tras la detección de un nuevo origen (por ejemplo, el administrador de dispositivos detecta y empieza a realizar el seguimiento de una mano).</span><span class="sxs-lookup"><span data-stu-id="7caf7-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="7caf7-114">En el bucle Update() del controlador, llama a su sistema de API subyacente.</span><span class="sxs-lookup"><span data-stu-id="7caf7-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="7caf7-115">En el mismo bucle de actualización, genera cambios en los eventos de entrada llamando directamente al propio sistema de entrada principal (por ejemplo, generando HandMeshUpdated o HandJointsUpdated).</span><span class="sxs-lookup"><span data-stu-id="7caf7-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="7caf7-116">Punteros y foco</span><span class="sxs-lookup"><span data-stu-id="7caf7-116">Pointers and focus</span></span>

<span data-ttu-id="7caf7-117">Los punteros se usan para interactuar con objetos de juego.</span><span class="sxs-lookup"><span data-stu-id="7caf7-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="7caf7-118">En esta sección se describe cómo se crean los punteros, cómo se actualizan y cómo determinan los objetos que están en el foco.</span><span class="sxs-lookup"><span data-stu-id="7caf7-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="7caf7-119">También se tratarán los distintos tipos de punteros que existen y los escenarios en los que están activos.</span><span class="sxs-lookup"><span data-stu-id="7caf7-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="7caf7-120">Categorías de puntero</span><span class="sxs-lookup"><span data-stu-id="7caf7-120">Pointer categories</span></span>

<span data-ttu-id="7caf7-121">Los punteros suelen estar en una de las siguientes categorías:</span><span class="sxs-lookup"><span data-stu-id="7caf7-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="7caf7-122">**Punteros lejanos**</span><span class="sxs-lookup"><span data-stu-id="7caf7-122">**Far pointers**</span></span>

  <span data-ttu-id="7caf7-123">Estos tipos de punteros se usan para interactuar con objetos que están lejos del usuario (muy lejos se define como simplemente "no cerca").</span><span class="sxs-lookup"><span data-stu-id="7caf7-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="7caf7-124">Por lo general, estos tipos de punteros convierten líneas que pueden llegar lejos al mundo y permiten al usuario interactuar con objetos que no están inmediatamente junto a ellos y manipularlos.</span><span class="sxs-lookup"><span data-stu-id="7caf7-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="7caf7-125">**Punteros cercanos**</span><span class="sxs-lookup"><span data-stu-id="7caf7-125">**Near pointers**</span></span>

  <span data-ttu-id="7caf7-126">Estos tipos de punteros se usan para interactuar con objetos que están lo suficientemente cerca del usuario para agarrar, tocar y manipular.</span><span class="sxs-lookup"><span data-stu-id="7caf7-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="7caf7-127">Por lo general, estos tipos de punteros interactúan con los objetos buscando objetos en proximidad (ya sea mediante la difusión por rayos a distancias pequeñas, realizando una conversión esférica en busca de objetos en la proximidad o enumerando listas de objetos que se consideran que se pueden agarrar o tocar).</span><span class="sxs-lookup"><span data-stu-id="7caf7-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="7caf7-128">**Teleportar punteros**</span><span class="sxs-lookup"><span data-stu-id="7caf7-128">**Teleport pointers**</span></span>

  <span data-ttu-id="7caf7-129">Estos tipos de punteros se conecta al sistema de teleportación para controlar el traslado del usuario a la ubicación de destino del puntero.</span><span class="sxs-lookup"><span data-stu-id="7caf7-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="7caf7-130">Mediación de puntero</span><span class="sxs-lookup"><span data-stu-id="7caf7-130">Pointer mediation</span></span>

<span data-ttu-id="7caf7-131">Dado que un solo controlador puede tener varios punteros (por ejemplo, la mano articulada puede tener punteros de interacción cercanos y lejanos), existe un componente responsable de mediar qué puntero debe estar activo.</span><span class="sxs-lookup"><span data-stu-id="7caf7-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="7caf7-132">Por ejemplo, a medida que la mano del usuario se acerca a un botón que se puede presionar, debe dejar de mostrarse y debe [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) estar activado.</span><span class="sxs-lookup"><span data-stu-id="7caf7-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="7caf7-133">Esto se controla mediante , que es responsable de determinar qué punteros están activos, en función del [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) estado de todos los punteros.</span><span class="sxs-lookup"><span data-stu-id="7caf7-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="7caf7-134">Una de las cosas clave que esto hace es deshabilitar punteros lejanos cuando un puntero cercano está cerca de un objeto (consulte [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).</span><span class="sxs-lookup"><span data-stu-id="7caf7-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="7caf7-135">Es posible proporcionar una implementación alternativa del mediador de puntero cambiando la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) propiedad en el perfil de puntero.</span><span class="sxs-lookup"><span data-stu-id="7caf7-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="7caf7-136">Cómo deshabilitar punteros</span><span class="sxs-lookup"><span data-stu-id="7caf7-136">How to disable pointers</span></span>

<span data-ttu-id="7caf7-137">Dado que el mediador de puntero ejecuta cada fotograma, termina controlando el estado activo o inactivo de todos los punteros.</span><span class="sxs-lookup"><span data-stu-id="7caf7-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="7caf7-138">Por lo tanto, si establece la propiedad IsInteractionEnabled de un puntero en el código, el mediador de puntero sobrescribirá cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="7caf7-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="7caf7-139">En su lugar, puede especificar para controlar si los punteros deben [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) estar on o off.</span><span class="sxs-lookup"><span data-stu-id="7caf7-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="7caf7-140">Tenga en cuenta que esto solo funcionará si usa el valor predeterminado [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) y [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) en MRTK.</span><span class="sxs-lookup"><span data-stu-id="7caf7-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="7caf7-141">Ejemplo: Deshabilitación de los rayos de mano en MRTK</span><span class="sxs-lookup"><span data-stu-id="7caf7-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="7caf7-142">El código siguiente desactivará los rayos de las manos en MRTK:</span><span class="sxs-lookup"><span data-stu-id="7caf7-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="7caf7-143">El código siguiente devolverá rayos de mano a su comportamiento predeterminado en MRTK:</span><span class="sxs-lookup"><span data-stu-id="7caf7-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="7caf7-144">El código siguiente forzará la activación de los rayos de mano, independientemente de si están cerca de un control que se pueda agarrar:</span><span class="sxs-lookup"><span data-stu-id="7caf7-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="7caf7-145">Vea [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) y para obtener más [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) ejemplos.</span><span class="sxs-lookup"><span data-stu-id="7caf7-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="7caf7-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="7caf7-146">FocusProvider</span></span>

<span data-ttu-id="7caf7-147">es el esfuerzo que es responsable de iterar en la lista de todos los punteros y averiguar cuál es el objeto centrado [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) para cada puntero.</span><span class="sxs-lookup"><span data-stu-id="7caf7-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="7caf7-148">En cada `Update()` llamada, esto hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7caf7-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="7caf7-149">Actualice todos los punteros, mediante la difusión por rayos y la detección de impactos según lo configurado por el propio puntero (por ejemplo, el puntero de esfera podría especificar sphereOverlap raycastMode, por lo que FocusProvider realizará una colisión basada en esferas).</span><span class="sxs-lookup"><span data-stu-id="7caf7-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="7caf7-150">Actualice el objeto con foco por puntero (es decir, si un objeto obtuvo el foco, también desencadenaría eventos en ese objeto, si un objeto perdiera el foco, desencadenaría la pérdida de foco, etc.).</span><span class="sxs-lookup"><span data-stu-id="7caf7-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="7caf7-151">Configuración y ciclo de vida del puntero</span><span class="sxs-lookup"><span data-stu-id="7caf7-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="7caf7-152">[Los punteros se pueden configurar](../features/input/pointers.md) en la *sección Punteros* del perfil del sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="7caf7-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="7caf7-153">La duración de un puntero suele ser la siguiente:</span><span class="sxs-lookup"><span data-stu-id="7caf7-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="7caf7-154">Un administrador de dispositivos detectará la presencia de un controlador.</span><span class="sxs-lookup"><span data-stu-id="7caf7-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="7caf7-155">A continuación, este administrador de dispositivos creará el conjunto de punteros asociado al controlador mediante una llamada a [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="7caf7-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="7caf7-156">FocusProvider, en su bucle Update(), iterará todos los punteros válidos y realizará la lógica de detección de impactos o raycast asociada.</span><span class="sxs-lookup"><span data-stu-id="7caf7-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="7caf7-157">Se usa para determinar el objeto que se centra en cada puntero determinado.</span><span class="sxs-lookup"><span data-stu-id="7caf7-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="7caf7-158">Dado que es posible tener varios orígenes de entrada activos al mismo tiempo (por ejemplo, dos manos activas presentes), también es posible tener varios objetos que tengan el foco al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="7caf7-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="7caf7-159">El administrador de dispositivos, al detectar que se perdió un origen del controlador, desmontará los punteros asociados al controlador perdido.</span><span class="sxs-lookup"><span data-stu-id="7caf7-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>