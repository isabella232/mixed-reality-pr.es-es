---
title: Elemento interactivo
description: Documentación de MrTK de InteractiveElement
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, elemento interactivo, interactuable
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144765"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="54bca-104">Elemento interactivo [Experimental]</span><span class="sxs-lookup"><span data-stu-id="54bca-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="54bca-105">Un punto de entrada centralizado simplificado al sistema de entrada de MRTK.</span><span class="sxs-lookup"><span data-stu-id="54bca-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="54bca-106">Contiene métodos de administración de estados, administración de eventos y la lógica de configuración de estado para los estados de interacción principal.</span><span class="sxs-lookup"><span data-stu-id="54bca-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="54bca-107">Interactive Element es una característica experimental compatible con Unity 2019.3 y versiones 2019.3, ya que usa una funcionalidad nueva de Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span><span class="sxs-lookup"><span data-stu-id="54bca-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="54bca-108">Inspector de elementos interactivos</span><span class="sxs-lookup"><span data-stu-id="54bca-108">Interactive Element Inspector</span></span>

<span data-ttu-id="54bca-109">Durante el modo de reproducción, el inspector de elementos interactivos proporciona comentarios visuales que indican si el estado actual está activo o no.</span><span class="sxs-lookup"><span data-stu-id="54bca-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="54bca-110">Si un estado está activo, se resaltará con un color cian.</span><span class="sxs-lookup"><span data-stu-id="54bca-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="54bca-111">Si el estado no está activo, el color no cambia.</span><span class="sxs-lookup"><span data-stu-id="54bca-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="54bca-112">Los números situados junto a los estados del inspector son los valores de estado; si el estado está activo, el valor es 1, si el estado no está activo, el valor es 0.</span><span class="sxs-lookup"><span data-stu-id="54bca-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![Elemento interactivo con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="54bca-114">Estados principales</span><span class="sxs-lookup"><span data-stu-id="54bca-114">Core States</span></span>

<span data-ttu-id="54bca-115">El elemento interactivo contiene estados principales y admite la adición de [estados personalizados.](#custom-states)</span><span class="sxs-lookup"><span data-stu-id="54bca-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="54bca-116">Un estado principal es aquel que ya tiene la lógica de configuración de estado definida en `BaseInteractiveElement` .</span><span class="sxs-lookup"><span data-stu-id="54bca-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="54bca-117">A continuación se muestra una lista de los estados principales controlados por entrada actuales:</span><span class="sxs-lookup"><span data-stu-id="54bca-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="54bca-118">Estados principales actuales</span><span class="sxs-lookup"><span data-stu-id="54bca-118">Current Core States</span></span>

- [<span data-ttu-id="54bca-119">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="54bca-119">Default</span></span>](#default-state) 

<span data-ttu-id="54bca-120">Estados principales de interacción cercana y lejana:</span><span class="sxs-lookup"><span data-stu-id="54bca-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="54bca-121">Foco</span><span class="sxs-lookup"><span data-stu-id="54bca-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="54bca-122">Estados principales de interacción cercana:</span><span class="sxs-lookup"><span data-stu-id="54bca-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="54bca-123">Enfoque cercano</span><span class="sxs-lookup"><span data-stu-id="54bca-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="54bca-124">Tocar</span><span class="sxs-lookup"><span data-stu-id="54bca-124">Touch</span></span>](#touch-state)

<span data-ttu-id="54bca-125">Estados principales de interacción lejana:</span><span class="sxs-lookup"><span data-stu-id="54bca-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="54bca-126">Enfoque lejos</span><span class="sxs-lookup"><span data-stu-id="54bca-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="54bca-127">Seleccione Lejos.</span><span class="sxs-lookup"><span data-stu-id="54bca-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="54bca-128">Otros estados principales:</span><span class="sxs-lookup"><span data-stu-id="54bca-128">Other Core States:</span></span>
- [<span data-ttu-id="54bca-129">Se ha hecho clic</span><span class="sxs-lookup"><span data-stu-id="54bca-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="54bca-130">Activar y desactivar</span><span class="sxs-lookup"><span data-stu-id="54bca-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="54bca-131">Palabra clave de voz</span><span class="sxs-lookup"><span data-stu-id="54bca-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="54bca-132">Cómo agregar un estado principal a través de Inspector</span><span class="sxs-lookup"><span data-stu-id="54bca-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="54bca-133">Vaya a **Agregar estado principal** en el inspector del elemento interactivo.</span><span class="sxs-lookup"><span data-stu-id="54bca-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![Agregar un estado principal a través de Inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="54bca-135">Seleccione el **botón Seleccionar estado** para elegir el estado principal que desea agregar.</span><span class="sxs-lookup"><span data-stu-id="54bca-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="54bca-136">Los estados del menú se ordenan por tipo de interacción.</span><span class="sxs-lookup"><span data-stu-id="54bca-136">The states in the menu are sorted by interaction type.</span></span>

    ![Agregar un estado principal a través de Inspector con el estado seleccionado](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="54bca-138">Abra el plegado Configuración de eventos para ver los eventos y las propiedades asociados al estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![Agregar un estado principal a través de Inspector con la configuración de eventos](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="54bca-140">Cómo agregar un estado principal mediante script</span><span class="sxs-lookup"><span data-stu-id="54bca-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="54bca-141">Use el `AddNewState(stateName)` método para agregar un estado principal.</span><span class="sxs-lookup"><span data-stu-id="54bca-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="54bca-142">Para obtener una lista de los nombres de estado principales disponibles, use `CoreInteractionState` la enumeración .</span><span class="sxs-lookup"><span data-stu-id="54bca-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="54bca-143">Estructura interna de estados</span><span class="sxs-lookup"><span data-stu-id="54bca-143">States Internal Structure</span></span> 

<span data-ttu-id="54bca-144">Los estados del elemento interactivo son de tipo `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="54bca-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="54bca-145">contiene `InteractionState` las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="54bca-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="54bca-146">**Nombre:** nombre del estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="54bca-147">**Valor:** el valor de estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-147">**Value**: The state value.</span></span>  <span data-ttu-id="54bca-148">Si el estado está en, el valor de estado es 1.</span><span class="sxs-lookup"><span data-stu-id="54bca-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="54bca-149">Si el estado está desactivado, el valor de estado es 0.</span><span class="sxs-lookup"><span data-stu-id="54bca-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="54bca-150">**Activo:** indica si el estado está activo actualmente o no.</span><span class="sxs-lookup"><span data-stu-id="54bca-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="54bca-151">El valor de la propiedad Active es true cuando el estado está activado, false si el estado está desactivado.</span><span class="sxs-lookup"><span data-stu-id="54bca-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="54bca-152">**Tipo de interacción:** el tipo de interacción de un estado es el tipo de interacción para el que está pensado un estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="54bca-153">`None`: no admite ninguna forma de interacción de entrada.</span><span class="sxs-lookup"><span data-stu-id="54bca-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="54bca-154">`Near`: compatibilidad con la interacción cercana.</span><span class="sxs-lookup"><span data-stu-id="54bca-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="54bca-155">La entrada se considera una interacción cercana cuando una mano articulada tiene contacto directo con otro objeto de juego, es decir, la posición de la mano articulada está cerca de la posición del objeto de juego en el espacio mundial.</span><span class="sxs-lookup"><span data-stu-id="54bca-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="54bca-156">`Far`: compatibilidad con la interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="54bca-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="54bca-157">La entrada se considera interacción lejana cuando no se requiere el contacto directo con el objeto de juego.</span><span class="sxs-lookup"><span data-stu-id="54bca-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="54bca-158">Por ejemplo, la entrada a través del rayo o la mirada del controlador se considera entrada de interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="54bca-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="54bca-159">`NearAndFar`: abarca la compatibilidad con la interacción cercana y lejana.</span><span class="sxs-lookup"><span data-stu-id="54bca-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="54bca-160">`Other`: compatibilidad con la interacción independiente del puntero.</span><span class="sxs-lookup"><span data-stu-id="54bca-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="54bca-161">**Configuración de** eventos: la configuración de eventos para un estado es el punto de entrada del perfil de eventos serializados.</span><span class="sxs-lookup"><span data-stu-id="54bca-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="54bca-162">Todas estas propiedades se establecen internamente en `State Manager` el contenido del elemento interactivo.</span><span class="sxs-lookup"><span data-stu-id="54bca-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="54bca-163">Para la modificación de estados, use los siguientes métodos auxiliares:</span><span class="sxs-lookup"><span data-stu-id="54bca-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="54bca-164">**Métodos auxiliares de configuración de estado**</span><span class="sxs-lookup"><span data-stu-id="54bca-164">**State Setting Helper Methods**</span></span>

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

<span data-ttu-id="54bca-165">La obtención de la configuración de eventos de un estado es específica del propio estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="54bca-166">Cada estado principal tiene un tipo de configuración de eventos específico que se describe a continuación en las secciones que describen cada estado principal.</span><span class="sxs-lookup"><span data-stu-id="54bca-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="54bca-167">Este es un ejemplo generalizado de cómo obtener la configuración de eventos de un estado:</span><span class="sxs-lookup"><span data-stu-id="54bca-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="54bca-168">Estado predeterminado</span><span class="sxs-lookup"><span data-stu-id="54bca-168">Default State</span></span>

<span data-ttu-id="54bca-169">El estado Predeterminado siempre está presente en un elemento interactivo.</span><span class="sxs-lookup"><span data-stu-id="54bca-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="54bca-170">Este estado solo estará activo cuando todos los demás estados no estén activos.</span><span class="sxs-lookup"><span data-stu-id="54bca-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="54bca-171">Si cualquier otro estado se activa, el estado Predeterminado se establecerá en desactivado internamente.</span><span class="sxs-lookup"><span data-stu-id="54bca-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="54bca-172">Un elemento interactivo se inicializa con los estados Predeterminado y Enfoque presentes en la lista de estados.</span><span class="sxs-lookup"><span data-stu-id="54bca-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="54bca-173">El estado Predeterminado siempre debe estar presente en la lista de estados.</span><span class="sxs-lookup"><span data-stu-id="54bca-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="54bca-174">Obtener eventos de estado predeterminados</span><span class="sxs-lookup"><span data-stu-id="54bca-174">Getting Default State Events</span></span>

<span data-ttu-id="54bca-175">Tipo de configuración de eventos para el estado predeterminado: `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="54bca-175">Event configuration type for the Default State: `StateEvents`</span></span>

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a><span data-ttu-id="54bca-176">Estado de enfoque</span><span class="sxs-lookup"><span data-stu-id="54bca-176">Focus State</span></span>

<span data-ttu-id="54bca-177">El estado de enfoque es un estado de interacción cercano y lejano que se puede pensar como la realidad mixta equivalente a mantener el puntero.</span><span class="sxs-lookup"><span data-stu-id="54bca-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="54bca-178">El factor distintivo entre la interacción cercana y lejana para el estado focus es el tipo de puntero activo actual.</span><span class="sxs-lookup"><span data-stu-id="54bca-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="54bca-179">Si el tipo de puntero para el estado de foco es el puntero de ándes, la interacción se considera una interacción cercana.</span><span class="sxs-lookup"><span data-stu-id="54bca-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="54bca-180">Si el puntero principal no es el puntero Desgarrón, la interacción se considera interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="54bca-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="54bca-181">El estado de foco está presente en el elemento interactivo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="54bca-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="54bca-182">**Comportamiento del estado de enfoque** 
 ![ Estado de enfoque con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="54bca-183">**Inspector de estado de enfoque** 
 ![ Estado de foco en Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;54bca-184&quot;>Obtener eventos de estado de enfoque</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;54bca-185&quot;>Tipo de configuración de eventos para el estado de enfoque: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="54bca-186">Enfoque cercano frente al comportamiento lejano del foco</span><span class="sxs-lookup"><span data-stu-id="54bca-186">Focus Near vs Focus Far Behavior</span></span> 

![Centrarse cerca y lejos con la interacción de la mano virtual](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="54bca-188">Estado cercano del foco</span><span class="sxs-lookup"><span data-stu-id="54bca-188">Focus Near State</span></span>

<span data-ttu-id="54bca-189">El estado Enfoque cercano se establece cuando se genera un evento de foco y el puntero principal es el puntero Desasoy, una indicación de interacción cercana.</span><span class="sxs-lookup"><span data-stu-id="54bca-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="54bca-190">**Comportamiento de enfoque de estado cercano** 
 ![ Enfoque al estado cercano con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="54bca-191">**Focus Near State Inspector** 
 ![ Foco cerca del componente en el inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;54bca-192&quot;>Obtener eventos de estado enfocados</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;54bca-193&quot;>Tipo de configuración de evento para el estado FocusNear: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="54bca-194">Estado lejano del foco</span><span class="sxs-lookup"><span data-stu-id="54bca-194">Focus Far State</span></span>

<span data-ttu-id="54bca-195">El estado Lejos del foco se establece cuando el puntero principal no es el puntero Desasoyé.</span><span class="sxs-lookup"><span data-stu-id="54bca-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="54bca-196">Por ejemplo, el puntero de rayo del controlador predeterminado y el puntero GGV (mirada, gesto, voz) se consideran punteros de interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="54bca-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="54bca-197">**Enfoque del comportamiento de estado lejano** 
 ![ Estado de enfoque lejos con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="54bca-198">**Focus Far State Inspector** 
 ![ Componente lejos del foco en el inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;54bca-199&quot;>Obtener eventos de estado lejano de enfoque</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;54bca-200&quot;>Tipo de configuración de evento para FocusFar State: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="54bca-201">Estado táctil</span><span class="sxs-lookup"><span data-stu-id="54bca-201">Touch State</span></span>

<span data-ttu-id="54bca-202">El estado Táctil es un estado de interacción cercano que se establece cuando una mano articulada toca el objeto directamente.</span><span class="sxs-lookup"><span data-stu-id="54bca-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="54bca-203">Una entrada táctil directa significa que el dedo índice de la mano articulada está muy cerca de la posición mundial del objeto.</span><span class="sxs-lookup"><span data-stu-id="54bca-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="54bca-204">De forma predeterminada, `NearInteractionTouchableVolume` se adjunta un componente al objeto si el estado Táctil se agrega a la lista de estados.</span><span class="sxs-lookup"><span data-stu-id="54bca-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="54bca-205">La presencia de un  `NearInteractionTouchableVolume` componente o es necesaria para detectar eventos `NearInteractionTouchable` táctiles.</span><span class="sxs-lookup"><span data-stu-id="54bca-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="54bca-206">La diferencia entre y es que detecta una función táctil basada en el colisionador del objeto y detecta la función táctil dentro de un `NearInteractionTouchableVolume` área definida de un `NearInteractionTouchable` `NearInteractionTouchableVolume` `NearInteractionTouchable` plano.</span><span class="sxs-lookup"><span data-stu-id="54bca-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="54bca-207">**Comportamiento del estado táctil** 
 ![ Estado táctil con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="54bca-208">**Touch State Inspector** 
 ![ Componente de estado táctil en el inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;54bca-209&quot;>Obtener eventos de estado táctil</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;54bca-210&quot;>Tipo de configuración de eventos para Touch State: `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a><span data-ttu-id="54bca-211">Seleccione Estado lejano.</span><span class="sxs-lookup"><span data-stu-id="54bca-211">Select Far State</span></span>

<span data-ttu-id="54bca-212">El estado Select Far (Seleccionar extremo) `IMixedRealityPointerHandler` es el que se ha presentado.</span><span class="sxs-lookup"><span data-stu-id="54bca-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="54bca-213">Este estado es un estado de interacción lejana que detecta el clic de interacción lejana (pulsación en el aire) y se mantiene a través del uso de punteros de interacción lejana, como el puntero de rayo del controlador predeterminado o el puntero GGV.</span><span class="sxs-lookup"><span data-stu-id="54bca-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="54bca-214">El estado Select Far (Seleccionar extremo) tiene una opción en el plegado de configuración de eventos denominado `Global` .</span><span class="sxs-lookup"><span data-stu-id="54bca-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="54bca-215">Si `Global` es true, se `IMixedRealityPointerHandler` registra como un controlador de entrada global.</span><span class="sxs-lookup"><span data-stu-id="54bca-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="54bca-216">No es necesario centrarse en un objeto para desencadenar eventos del sistema de entrada si un controlador está registrado como global.</span><span class="sxs-lookup"><span data-stu-id="54bca-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="54bca-217">Por ejemplo, si un usuario quiere saber cada vez que se realiza el gesto de pulsar o seleccionar el aire independientemente del objeto en el foco, establezca `Global` en true.</span><span class="sxs-lookup"><span data-stu-id="54bca-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="54bca-218">**Seleccionar comportamiento de estado lejano** 
 ![ Selección lejos con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="54bca-219">**Seleccione Inspector de estado lejano.** 
 ![ Selección del componente lejano en el inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;54bca-220&quot;>Obtención de eventos de estado lejano selectos</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;54bca-221&quot;>Tipo de configuración de eventos para SelectFar State: `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a><span data-ttu-id="54bca-222">Estado en el que se hizo clic</span><span class="sxs-lookup"><span data-stu-id="54bca-222">Clicked State</span></span>

<span data-ttu-id="54bca-223">El estado Clicked se desencadena mediante un clic de interacción lejana (Seleccionar estado lejano) de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="54bca-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="54bca-224">Este estado se cambia internamente a on, invoca el evento OnClicked y, a continuación, se cambia inmediatamente a desactivado.</span><span class="sxs-lookup"><span data-stu-id="54bca-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="54bca-225">Los comentarios visuales del inspector basados en la actividad de estado no están presentes para el estado Clicked porque está encendido y apagado inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="54bca-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="54bca-226">**Comportamiento de estado en el que se hizo clic** 
 ![ Estado en el que se hizo clic con interacciones de manos virtuales](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="54bca-227">**Inspector de estado en el que se ha hecho clic** 
 ![ Haga clic en el componente de estado en el inspector.](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="54bca-228">**Ejemplo de estado con clics cercanos y lejanos**</span><span class="sxs-lookup"><span data-stu-id="54bca-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="54bca-229">El estado en el que se ha hecho clic se puede desencadenar a través de puntos de entrada adicionales mediante el `interactiveElement.TriggerClickedState()` método .</span><span class="sxs-lookup"><span data-stu-id="54bca-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="54bca-230">Por ejemplo, si un usuario quiere una interacción táctil cercana para desencadenar también un clic en un objeto, agregaría el método como un agente de escucha en estado `TriggerClickedState()` táctil.</span><span class="sxs-lookup"><span data-stu-id="54bca-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![Estado cercano y lejano con interacciones de la mano virtual](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;54bca-232&quot;>Obtener eventos de estado en los que se ha hecho clic</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;54bca-233&quot;>Tipo de configuración de evento para el estado clicked: `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="54bca-234">Activar y desactivar el estado</span><span class="sxs-lookup"><span data-stu-id="54bca-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="54bca-235">Los estados Activar y Desactivar son un par y ambos deben estar presentes para el comportamiento de alternancia.</span><span class="sxs-lookup"><span data-stu-id="54bca-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="54bca-236">De forma predeterminada, los estados Activar y Desactivar se desencadenan mediante un clic de interacción lejana (Seleccionar estado lejano).</span><span class="sxs-lookup"><span data-stu-id="54bca-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="54bca-237">De forma predeterminada, el estado Alternar desactivado está activo al inicio, lo que significa que el botón de alternancia se inicializará en desactivado.</span><span class="sxs-lookup"><span data-stu-id="54bca-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="54bca-238">Si un usuario desea que el estado Alternar activado esté activo al inicio, en el estado Alternar activado se `IsSelectedOnStart` establece en true.</span><span class="sxs-lookup"><span data-stu-id="54bca-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="54bca-239">**Comportamiento de alternancia y desactivación del estado** 
 ![ Activar y desactivar con interacciones de la mano virtual](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="54bca-240">**ToggleOn y Toggle Off State Inspector** 
 ![ Alternancia del componente en el inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="54bca-241">**Ejemplo de estados de alternancia cercanos y lejanos**</span><span class="sxs-lookup"><span data-stu-id="54bca-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="54bca-242">De forma similar al estado Clic, la configuración de estado de alternancia puede tener varios puntos de entrada mediante el `interactiveElement.SetToggleStates()` método .</span><span class="sxs-lookup"><span data-stu-id="54bca-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="54bca-243">Por ejemplo, si un usuario desea tocar como punto de entrada adicional para establecer los estados de alternancia, agrega el método a uno de los eventos en el `SetToggleStates()` estado Táctil.</span><span class="sxs-lookup"><span data-stu-id="54bca-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![Alternancia cercana y lejana con interacciones de la mano virtual](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;54bca-245&quot;>Obtener activar y desactivar eventos de estado</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;54bca-246&quot;>Tipo de configuración de evento para el estado ToggleOn: `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;54bca-247&quot;>Tipo de configuración de evento para el estado ToggleOff: `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a><span data-ttu-id="54bca-248">Estado de palabra clave de voz</span><span class="sxs-lookup"><span data-stu-id="54bca-248">Speech Keyword State</span></span>

<span data-ttu-id="54bca-249">El estado de palabra clave de voz escucha las palabras clave definidas en el Mixed Reality voz.</span><span class="sxs-lookup"><span data-stu-id="54bca-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="54bca-250">Cualquier palabra clave nueva DEBE registrarse en el perfil de comandos de voz antes del tiempo de ejecución (pasos a continuación).</span><span class="sxs-lookup"><span data-stu-id="54bca-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="54bca-251">**Comportamiento del estado de la palabra clave de voz** 
 ![ Palabra clave de voz con interacción virtual](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="54bca-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="54bca-252">**Speech Keyword State Inspector** 
 ![ Componente de palabra clave de voz en el inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="54bca-253">El estado de la palabra clave de voz se desencadenó en el editor presionando la tecla F5 en el gif anterior.</span><span class="sxs-lookup"><span data-stu-id="54bca-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="54bca-254">La configuración en las pruebas del editor para voz se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="54bca-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="54bca-255">Cómo registrar un comando o palabra clave de Voz</span><span class="sxs-lookup"><span data-stu-id="54bca-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="54bca-256">Selección del **objeto de juego MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="54bca-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="54bca-257">Seleccione **Copiar y personalizar el** perfil actual.</span><span class="sxs-lookup"><span data-stu-id="54bca-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="54bca-258">Vaya a la sección Entrada y seleccione **Clonar para** habilitar la modificación del perfil de entrada.</span><span class="sxs-lookup"><span data-stu-id="54bca-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="54bca-259">Desplácese hacia abajo hasta la sección Voz en el perfil de entrada y clone el perfil de voz.</span><span class="sxs-lookup"><span data-stu-id="54bca-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![Perfil de palabra clave de voz en el objeto de juego MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="54bca-261">Seleccione Agregar un nuevo comando de voz.</span><span class="sxs-lookup"><span data-stu-id="54bca-261">Select Add a New Speech Command</span></span>

    ![Adición de una nueva palabra clave de voz en el perfil de MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="54bca-263">Escriba la palabra clave new.</span><span class="sxs-lookup"><span data-stu-id="54bca-263">Enter the new keyword.</span></span> <span data-ttu-id="54bca-264">Opcional: cambie KeyCode a F5 (u otro KeyCode) para permitir las pruebas en el editor.</span><span class="sxs-lookup"><span data-stu-id="54bca-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![Configuración de la palabra clave de voz en el perfil de MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="54bca-266">Vuelva al inspector de estado palabra clave de voz de elemento interactivo y seleccione **Agregar palabra clave.**</span><span class="sxs-lookup"><span data-stu-id="54bca-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![Agregar palabra clave al componente de elemento interactivo](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Validación y registro de palabras clave](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="54bca-269">Escriba la nueva palabra clave que se acaba de registrar en el perfil de voz.</span><span class="sxs-lookup"><span data-stu-id="54bca-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![Especificación de la nueva palabra clave de voz](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="54bca-271">Para probar el estado de la palabra clave de voz en el editor, presione el keycode que se definió en el paso 6 (F5) para simular el evento reconocido de palabra clave de voz.</span><span class="sxs-lookup"><span data-stu-id="54bca-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="54bca-272">Obtención de eventos de estado de palabras clave de voz</span><span class="sxs-lookup"><span data-stu-id="54bca-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="54bca-273">Tipo de configuración de eventos para speechKeyword State: `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="54bca-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a><span data-ttu-id="54bca-274">Estados personalizados</span><span class="sxs-lookup"><span data-stu-id="54bca-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="54bca-275">Cómo crear un estado personalizado a través de Inspector</span><span class="sxs-lookup"><span data-stu-id="54bca-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="54bca-276">El estado personalizado creado a través de inspector se inicializará con la configuración de eventos de estado predeterminada.</span><span class="sxs-lookup"><span data-stu-id="54bca-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="54bca-277">La configuración de eventos predeterminada para un estado personalizado es de tipo y contiene los eventos `StateEvents` OnStateOn y OnStateOff.</span><span class="sxs-lookup"><span data-stu-id="54bca-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="54bca-278">Vaya a **Create Custom State (Crear estado** personalizado) en el inspector para Interactive Element (Elemento interactivo).</span><span class="sxs-lookup"><span data-stu-id="54bca-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![Creación de un estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="54bca-280">Escriba el nombre del nuevo estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-280">Enter the name of the new state.</span></span> <span data-ttu-id="54bca-281">Este nombre debe ser único y no puede ser el mismo que el de los estados principales existentes.</span><span class="sxs-lookup"><span data-stu-id="54bca-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![Escribir el nombre de un nuevo estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="54bca-283">Seleccione **Set State Name (Establecer nombre de** estado) para agregarlo a la lista de estados.</span><span class="sxs-lookup"><span data-stu-id="54bca-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![Agregar estado personalizado a la lista de estados](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="54bca-285">Este estado personalizado se inicializa con la configuración `StateEvents` de eventos predeterminada que contiene los eventos y `OnStateOn` `OnStateOff` .</span><span class="sxs-lookup"><span data-stu-id="54bca-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="54bca-286">Para crear una configuración de eventos personalizada para un nuevo estado, consulte: [Creación de un estado personalizado con una configuración de eventos personalizada](#creating-a-custom-state-with-a-custom-event-configuration).</span><span class="sxs-lookup"><span data-stu-id="54bca-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![Nuevo estado que se muestra en el componente de elemento interactivo](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;54bca-288&quot;>Cómo crear un estado personalizado mediante script</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;54bca-288&quot;>How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="54bca-289">Crear un estado personalizado con una configuración de eventos personalizada</span><span class="sxs-lookup"><span data-stu-id="54bca-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="54bca-290">Los archivos de ejemplo de un estado personalizado denominado **Teclado** se encuentran aquí: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="54bca-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="54bca-291">En los pasos siguientes se muestra un ejemplo existente de creación de una configuración de eventos de estado personalizado y archivos receptores.</span><span class="sxs-lookup"><span data-stu-id="54bca-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="54bca-292">Piense en un nombre de estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-292">Think of a state name.</span></span>  <span data-ttu-id="54bca-293">Este nombre debe ser único y no puede ser el mismo que el de los estados principales existentes.</span><span class="sxs-lookup"><span data-stu-id="54bca-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="54bca-294">Para los fines de este ejemplo, el nombre de estado va a ser **Keyboard**.</span><span class="sxs-lookup"><span data-stu-id="54bca-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="54bca-295">Cree dos archivos .cs denominados state name + "Receiver" y state name + "Events".</span><span class="sxs-lookup"><span data-stu-id="54bca-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="54bca-296">La nomenclatura de estos archivos se tiene en cuenta internamente y debe seguir la convención state name + Event/Receiver.</span><span class="sxs-lookup"><span data-stu-id="54bca-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![Scripts de estado de teclado](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="54bca-298">Consulte los archivos KeyboardEvents.cs y KeyboardReceiver.cs para obtener más detalles sobre el contenido del archivo.</span><span class="sxs-lookup"><span data-stu-id="54bca-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="54bca-299">Las nuevas clases de configuración de eventos deben heredar de `BaseInteractionEventConfiguration` y las nuevas clases receptoras de eventos deben heredar de `BaseEventReceiver` .</span><span class="sxs-lookup"><span data-stu-id="54bca-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="54bca-300">En el archivo se encuentran ejemplos sobre la configuración de estado para el estado `CustomStateSettingExample.cs` de teclado.</span><span class="sxs-lookup"><span data-stu-id="54bca-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="54bca-301">Agregue el estado al elemento interactivo mediante el nombre de estado; el nombre de estado se reconocerá si existen archivos de configuración de eventos y receptor de eventos.</span><span class="sxs-lookup"><span data-stu-id="54bca-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="54bca-302">Las propiedades del archivo de configuración de eventos personalizados deben aparecer en el inspector.</span><span class="sxs-lookup"><span data-stu-id="54bca-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="54bca-303">![Agregar estado personalizado al elemento interactivo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ Estado personalizado reconocido en el elemento interactivo](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="54bca-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="54bca-304">Para obtener más ejemplos de configuración de eventos y archivos receptores de eventos, vea los archivos en estas rutas de acceso:</span><span class="sxs-lookup"><span data-stu-id="54bca-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="54bca-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="54bca-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="54bca-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="54bca-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="54bca-307">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="54bca-307">Example Scene</span></span> 

<span data-ttu-id="54bca-308">La escena de ejemplo de Interactive Element + State Visualizer se encuentra aquí: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="54bca-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![Escena de ejemplo con elemento interactivo y visualizador de estado](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="54bca-310">Botón comprimir</span><span class="sxs-lookup"><span data-stu-id="54bca-310">Compressable Button</span></span>

<span data-ttu-id="54bca-311">La escena de ejemplo contiene objetos prefabs denominados y , estos objetos prefabs reflejan el comportamiento de los botones, que se construyen mediante el elemento interactivo y el `CompressableButton` `CompressableButtonToggle` `PressableButtonHoloLens2` visualizador de estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="54bca-312">El `CompressableButton` componente es actualmente una combinación de con como clase `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` base.</span><span class="sxs-lookup"><span data-stu-id="54bca-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="54bca-313">Visualizador de estado [Experimental]</span><span class="sxs-lookup"><span data-stu-id="54bca-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="54bca-314">El componente Visualizador de estado agrega animaciones a un objeto en función de los estados definidos en un componente de elemento interactivo vinculado.</span><span class="sxs-lookup"><span data-stu-id="54bca-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="54bca-315">Este componente crea recursos de animación, los coloca en la carpeta MixedRealityToolkit.Generated y habilita la configuración simplificada de fotogramas clave de animación mediante la adición de propiedades Animatable a un objeto de juego de destino.</span><span class="sxs-lookup"><span data-stu-id="54bca-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="54bca-316">Para habilitar las transiciones de animación entre estados, se crea un recurso controlador de animador y se genera una máquina de estado predeterminada con parámetros asociados y cualquier transición de estado.</span><span class="sxs-lookup"><span data-stu-id="54bca-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="54bca-317">La máquina de estados se puede ver en la ventana Animator de Unity.</span><span class="sxs-lookup"><span data-stu-id="54bca-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="54bca-318">Visualizador de estado y sistema de animación de Unity</span><span class="sxs-lookup"><span data-stu-id="54bca-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="54bca-319">El visualizador de estado aprovecha actualmente el sistema de animación de Unity.</span><span class="sxs-lookup"><span data-stu-id="54bca-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="54bca-320">Cuando se presiona el botón Generar nuevos **clips** de animación en el visualizador de estado, se generan nuevos recursos de clips de animación en función de los nombres de estado del elemento interactivo y se colocan en la carpeta MixedRealityToolkit.Generated.</span><span class="sxs-lookup"><span data-stu-id="54bca-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="54bca-321">La propiedad Clip de animación de cada contenedor de estado se establece en el clip de animación asociado.</span><span class="sxs-lookup"><span data-stu-id="54bca-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![Clips de animación en el componente visualizador de estado](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="54bca-323">También [se genera una máquina de estado](https://docs.unity3d.com/Manual/AnimationOverview.html) de animador para administrar transiciones fluidas entre clips de animación.</span><span class="sxs-lookup"><span data-stu-id="54bca-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="54bca-324">De forma predeterminada, la máquina de estados usa [Cualquier estado](https://docs.unity3d.com/Manual/class-State.html) para permitir las transiciones entre cualquier estado del elemento interactivo.</span><span class="sxs-lookup"><span data-stu-id="54bca-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="54bca-325">[Los visualizadores de estado desencadenados](https://docs.unity3d.com/Manual/AnimationParameters.html) en el animador también se generan para cada estado; los parámetros del desencadenador se usan en el visualizador de estado para desencadenar una animación.</span><span class="sxs-lookup"><span data-stu-id="54bca-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Máquina de estado de Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="54bca-327">Limitaciones en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="54bca-327">Runtime Limitations</span></span> 

<span data-ttu-id="54bca-328">El visualizador de estado debe agregarse a un objeto a través del inspector y no se puede agregar mediante script.</span><span class="sxs-lookup"><span data-stu-id="54bca-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="54bca-329">Las propiedades que modifican AnimatorStateMachine/AnimationController se encuentran en un espacio de nombres del editor ( ) que se quita `UnityEditor.Animations` cuando se construye la aplicación.</span><span class="sxs-lookup"><span data-stu-id="54bca-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="54bca-330">Uso del visualizador de estado</span><span class="sxs-lookup"><span data-stu-id="54bca-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="54bca-331">Crear un cubo</span><span class="sxs-lookup"><span data-stu-id="54bca-331">Create a Cube</span></span>
1. <span data-ttu-id="54bca-332">Attach Interactive Element</span><span class="sxs-lookup"><span data-stu-id="54bca-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="54bca-333">Adjuntar visualizador de estado</span><span class="sxs-lookup"><span data-stu-id="54bca-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="54bca-334">Seleccione **Generate New Animation Clips (Generar nuevos clips de animación).**</span><span class="sxs-lookup"><span data-stu-id="54bca-334">Select **Generate New Animation Clips**</span></span>

    ![Generación de nuevos clips de animación](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Mostrar clips de animación generados en el visualizador y los componentes de elementos interactivos](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="54bca-337">En el contenedor de estado de enfoque, seleccione **Agregar destino.**</span><span class="sxs-lookup"><span data-stu-id="54bca-337">In the Focus state container, select **Add Target**</span></span>

    ![Adición del destino del visualizador de estado](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="54bca-339">Arrastre el objeto de juego actual al campo de destino.</span><span class="sxs-lookup"><span data-stu-id="54bca-339">Drag the current game object to the target field</span></span> 

    ![Establecimiento del destino del visualizador de estado](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="54bca-341">Abrir el plegable Propiedades animables de cubo</span><span class="sxs-lookup"><span data-stu-id="54bca-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="54bca-342">Seleccione el menú desplegable de la propiedad Animatable y seleccione **Color.**</span><span class="sxs-lookup"><span data-stu-id="54bca-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![Configuración del color del visualizador de estado](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="54bca-344">Seleccione **Agregar la propiedad Color Animatable**</span><span class="sxs-lookup"><span data-stu-id="54bca-344">Select **Add the Color Animatable Property**</span></span>

    ![Selección de la propiedad animable de color del visualizador](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="54bca-346">Elegir un color</span><span class="sxs-lookup"><span data-stu-id="54bca-346">Choose a Color</span></span> 

    ![Elección de un color de visualizador de la rueda de colores](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="54bca-348">Presione Reproducir y observe el cambio de color transitorio.</span><span class="sxs-lookup"><span data-stu-id="54bca-348">Press play and observe the transitional color change</span></span>

    ![Ejemplo de cambio de color transitorio con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="54bca-350">Propiedades que se pueden animar</span><span class="sxs-lookup"><span data-stu-id="54bca-350">Animatable Properties</span></span>

<span data-ttu-id="54bca-351">El propósito principal de las propiedades animables es simplificar la configuración de fotogramas clave del clip de animación.</span><span class="sxs-lookup"><span data-stu-id="54bca-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="54bca-352">Si un usuario está familiarizado con el sistema de animación de Unity y prefiere establecer directamente fotogramas clave en los clips de animación generados, simplemente no puede agregar propiedades animables a un objeto de destino y abrir el clip en la ventana Animación de Unity (Animación de Windows > > Animación).</span><span class="sxs-lookup"><span data-stu-id="54bca-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="54bca-353">Si usa las propiedades Animatable para la animación, el tipo de curva se establece en EaseInOut.</span><span class="sxs-lookup"><span data-stu-id="54bca-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="54bca-354">**Propiedades actuales de Animatable:**</span><span class="sxs-lookup"><span data-stu-id="54bca-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="54bca-355">Desplazamiento de escala</span><span class="sxs-lookup"><span data-stu-id="54bca-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="54bca-356">Desplazamiento de posición</span><span class="sxs-lookup"><span data-stu-id="54bca-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="54bca-357">Color</span><span class="sxs-lookup"><span data-stu-id="54bca-357">Color</span></span>](#color)
- [<span data-ttu-id="54bca-358">Color del sombreador</span><span class="sxs-lookup"><span data-stu-id="54bca-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="54bca-359">Float del sombreador</span><span class="sxs-lookup"><span data-stu-id="54bca-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="54bca-360">Vector de sombreador</span><span class="sxs-lookup"><span data-stu-id="54bca-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="54bca-361">Desplazamiento de escala</span><span class="sxs-lookup"><span data-stu-id="54bca-361">Scale Offset</span></span>

<span data-ttu-id="54bca-362">La propiedad Animatable de desplazamiento de escala toma la escala actual del objeto y agrega el desplazamiento definido.</span><span class="sxs-lookup"><span data-stu-id="54bca-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![Desplazamiento de escala con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="54bca-364">Desplazamiento de posición</span><span class="sxs-lookup"><span data-stu-id="54bca-364">Position Offset</span></span>

<span data-ttu-id="54bca-365">La propiedad Animatable Position Offset toma la posición actual del objeto y agrega el desplazamiento definido.</span><span class="sxs-lookup"><span data-stu-id="54bca-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![Desplazamiento de posición con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="54bca-367">Color</span><span class="sxs-lookup"><span data-stu-id="54bca-367">Color</span></span>

<span data-ttu-id="54bca-368">La propiedad Color Animatable representa el color principal de un material si el material tiene una propiedad de color principal.</span><span class="sxs-lookup"><span data-stu-id="54bca-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="54bca-369">Esta propiedad anima la `material._Color` propiedad .</span><span class="sxs-lookup"><span data-stu-id="54bca-369">This property animates the `material._Color` property.</span></span>

![Cambio de color de foco con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="54bca-371">Color del sombreador</span><span class="sxs-lookup"><span data-stu-id="54bca-371">Shader Color</span></span>

<span data-ttu-id="54bca-372">La propiedad Color Animatable del sombreador hace referencia a una propiedad de sombreador de color de tipo.</span><span class="sxs-lookup"><span data-stu-id="54bca-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="54bca-373">Se requiere un nombre de propiedad para todas las propiedades del sombreador.</span><span class="sxs-lookup"><span data-stu-id="54bca-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="54bca-374">El siguiente gif muestra cómo animar una propiedad de color de sombreador Fill_Color que no es el color del material principal.</span><span class="sxs-lookup"><span data-stu-id="54bca-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="54bca-375">Observe los valores cambiantes en el inspector de material.</span><span class="sxs-lookup"><span data-stu-id="54bca-375">Observe the changing values in the material inspector.</span></span>

![Color de sombreado con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="54bca-377">Float del sombreador</span><span class="sxs-lookup"><span data-stu-id="54bca-377">Shader Float</span></span>

<span data-ttu-id="54bca-378">La propiedad Float Animatable del sombreador hace referencia a una propiedad de sombreador de tipo float.</span><span class="sxs-lookup"><span data-stu-id="54bca-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="54bca-379">Se requiere un nombre de propiedad para todas las propiedades del sombreador.</span><span class="sxs-lookup"><span data-stu-id="54bca-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="54bca-380">En el gif siguiente, observe los valores cambiantes en el inspector de material para la propiedad Metal metalórtico.</span><span class="sxs-lookup"><span data-stu-id="54bca-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![Sombreador flotante con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="54bca-382">Vector de sombreador</span><span class="sxs-lookup"><span data-stu-id="54bca-382">Shader Vector</span></span>

<span data-ttu-id="54bca-383">La propiedad Vector Animatable del sombreador hace referencia a una propiedad de sombreador de tipo Vector4.</span><span class="sxs-lookup"><span data-stu-id="54bca-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="54bca-384">Se requiere un nombre de propiedad para todas las propiedades del sombreador.</span><span class="sxs-lookup"><span data-stu-id="54bca-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="54bca-385">En el gif siguiente, observe los valores cambiantes en el inspector de material para la propiedad Tiling (Main Tex_ST).</span><span class="sxs-lookup"><span data-stu-id="54bca-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![Vector de sombreador con interacción con la mano virtual](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="54bca-387">Cómo buscar nombres de propiedades de sombreador animables</span><span class="sxs-lookup"><span data-stu-id="54bca-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="54bca-388">Vaya a Ventana > animación > animación</span><span class="sxs-lookup"><span data-stu-id="54bca-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="54bca-389">Asegúrese de que el objeto con el visualizador de estado está seleccionado en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="54bca-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="54bca-390">Selección de cualquier clip de animación en la ventana Animación</span><span class="sxs-lookup"><span data-stu-id="54bca-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="54bca-391">Seleccione **Agregar propiedad y** abra el plegado representador de malla.</span><span class="sxs-lookup"><span data-stu-id="54bca-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![Adición de la propiedad animation en la ventana Animator](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="54bca-393">Esta lista contiene los nombres de todos los nombres de propiedad Animatable.</span><span class="sxs-lookup"><span data-stu-id="54bca-393">This list contains the names of all the Animatable property names</span></span> 

    ![Propiedades de animación del representador de malla en la ventana Animator](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="54bca-395">Consulte también</span><span class="sxs-lookup"><span data-stu-id="54bca-395">See also</span></span>

- [<span data-ttu-id="54bca-396">**Botones**</span><span class="sxs-lookup"><span data-stu-id="54bca-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="54bca-397">**Control de límites**</span><span class="sxs-lookup"><span data-stu-id="54bca-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="54bca-398">**Colección de objetos grid**</span><span class="sxs-lookup"><span data-stu-id="54bca-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="54bca-399">**RadialView Solver**</span><span class="sxs-lookup"><span data-stu-id="54bca-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
