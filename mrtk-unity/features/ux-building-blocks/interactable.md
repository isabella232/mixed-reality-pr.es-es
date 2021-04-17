---
title: Interactuable
description: Información general sobre el componente de script interactable en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Interactable, Eventos,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581567"
---
# <a name="interactable"></a><span data-ttu-id="10892-104">Interactuable</span><span class="sxs-lookup"><span data-stu-id="10892-104">Interactable</span></span>

![Interactuable](../images/interactable/InteractableExamples.png)

<span data-ttu-id="10892-106">El componente es un contenedor todo en uno para que cualquier objeto pueda interactuar fácilmente y [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) responder a la entrada. </span><span class="sxs-lookup"><span data-stu-id="10892-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="10892-107">Interactable actúa como un elemento de entrada para todos los tipos de entrada, [](#events) incluidos el toque, los rayos de las manos, la voz, etc. y canaliza estas interacciones en eventos y respuestas [de temas](visual-themes.md) visuales.</span><span class="sxs-lookup"><span data-stu-id="10892-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="10892-108">Este componente proporciona una manera sencilla de crear botones, cambiar el color de los objetos con el foco, etc.</span><span class="sxs-lookup"><span data-stu-id="10892-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="10892-109">Configuración de Interactable</span><span class="sxs-lookup"><span data-stu-id="10892-109">How to configure Interactable</span></span>

<span data-ttu-id="10892-110">El componente permite tres secciones principales de configuración:</span><span class="sxs-lookup"><span data-stu-id="10892-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="10892-111">Configuración de entrada general</span><span class="sxs-lookup"><span data-stu-id="10892-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="10892-112">[Temas visuales dirigidos](visual-themes.md) a varios Objetos GameObject</span><span class="sxs-lookup"><span data-stu-id="10892-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="10892-113">Controladores de eventos</span><span class="sxs-lookup"><span data-stu-id="10892-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="10892-114">Configuración de entrada general</span><span class="sxs-lookup"><span data-stu-id="10892-114">General input settings</span></span>

![Configuración general que se puede interactuar](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="10892-116">**States**</span><span class="sxs-lookup"><span data-stu-id="10892-116">**States**</span></span>

<span data-ttu-id="10892-117">*States* es un [parámetro ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) que define las fases de interacción, como presionar o observar, para perfiles [interactuables](#interactable-profiles) y [temas visuales.](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="10892-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="10892-118">**DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) se incluye con MRTK de fábrica y es el parámetro predeterminado para los componentes *interactables.*</span><span class="sxs-lookup"><span data-stu-id="10892-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![Ejemplo de ScriptableObject de estados en inspector](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="10892-120">El *recurso DefaultInteractableStates* contiene cuatro estados y utiliza la implementación [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) del modelo de estado.</span><span class="sxs-lookup"><span data-stu-id="10892-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="10892-121">**Valor** predeterminado: no ocurre nada, es el estado base más aislado.</span><span class="sxs-lookup"><span data-stu-id="10892-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="10892-122">**Foco:** el objeto al que se apunta.</span><span class="sxs-lookup"><span data-stu-id="10892-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="10892-123">Se trata de un estado único, no hay ningún otro estado establecido actualmente, pero se clasificará por rango Predeterminado.</span><span class="sxs-lookup"><span data-stu-id="10892-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="10892-124">**Presione**: se apunta al objeto y se presiona un botón o una mano.</span><span class="sxs-lookup"><span data-stu-id="10892-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="10892-125">El estado Press (Presionar) clasifica Default (Predeterminado) y Focus (Foco).</span><span class="sxs-lookup"><span data-stu-id="10892-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="10892-126">Este estado también se establecerá como reserva en La presión física.</span><span class="sxs-lookup"><span data-stu-id="10892-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="10892-127">**Deshabilitado:** el botón no debe ser interactivo y los comentarios visuales permitirán al usuario saber si, por algún motivo, este botón no se puede usar en este momento.</span><span class="sxs-lookup"><span data-stu-id="10892-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="10892-128">En teoría, el estado deshabilitado podría contener todos los demás estados, pero cuando Enabled está desactivado, el estado Disabled (Deshabilitado) se establece en todos los demás estados.</span><span class="sxs-lookup"><span data-stu-id="10892-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="10892-129">Un valor de bits (#) se asigna al estado en función del orden de la lista.</span><span class="sxs-lookup"><span data-stu-id="10892-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="10892-130">Por lo general, se recomienda usar **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) al crear componentes *interactuables.*</span><span class="sxs-lookup"><span data-stu-id="10892-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="10892-131">Sin embargo, hay 17 estados interactuables disponibles que se pueden usar para impulsar temas, aunque algunos están diseñados para ser controlados por otros componentes.</span><span class="sxs-lookup"><span data-stu-id="10892-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="10892-132">Esta es una lista de los que tienen funcionalidad integrada.</span><span class="sxs-lookup"><span data-stu-id="10892-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="10892-133">Visitado: se ha hecho clic en interactuable.</span><span class="sxs-lookup"><span data-stu-id="10892-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="10892-134">Alternancia: el botón está en un estado alternado o índice de dimensión es un número impar.</span><span class="sxs-lookup"><span data-stu-id="10892-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="10892-135">Gesto: se ha presionado la mano o el controlador y se ha movido desde la posición original.</span><span class="sxs-lookup"><span data-stu-id="10892-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="10892-136">VoiceCommand: se usó un comando de voz para desencadenar interactuable.</span><span class="sxs-lookup"><span data-stu-id="10892-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="10892-137">PhysicalTouch: actualmente se detecta una entrada táctil, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) para habilitar.</span><span class="sxs-lookup"><span data-stu-id="10892-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="10892-138">Agarrar: una mano está agarrándose actualmente en los límites del objeto, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) para habilitar</span><span class="sxs-lookup"><span data-stu-id="10892-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="10892-139">**Habilitado**</span><span class="sxs-lookup"><span data-stu-id="10892-139">**Enabled**</span></span>

<span data-ttu-id="10892-140">Alterna si un elemento Interactable se iniciará habilitado o no.</span><span class="sxs-lookup"><span data-stu-id="10892-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="10892-141">Esto corresponde a en [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) el código.</span><span class="sxs-lookup"><span data-stu-id="10892-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="10892-142">La *propiedad habilitada de Interactable* es diferente de la propiedad habilitada configurada a través de GameObject/Component (es decir,</span><span class="sxs-lookup"><span data-stu-id="10892-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="10892-143">SetActive, etc.).</span><span class="sxs-lookup"><span data-stu-id="10892-143">SetActive etc).</span></span> <span data-ttu-id="10892-144">Al deshabilitar GameObject o MonoBehaviour *interactuable,* se deshabilitará la ejecución de todo el contenido de la clase, incluidos la entrada, los temas visuales, los eventos, etc. Deshabilitar a través [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) de deshabilitará la mayoría del control de entrada y restablecerá los estados de entrada relacionados.</span><span class="sxs-lookup"><span data-stu-id="10892-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="10892-145">Sin embargo, la clase todavía ejecutará cada fotograma y recibirá eventos de entrada que se omitirán.</span><span class="sxs-lookup"><span data-stu-id="10892-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="10892-146">Esto es útil para mostrar interactuable en un estado deshabilitado que se puede realizar a través de temas visuales.</span><span class="sxs-lookup"><span data-stu-id="10892-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="10892-147">Un ejemplo típico de esto sería un botón enviar en espera de que se completen todos los campos de entrada necesarios.</span><span class="sxs-lookup"><span data-stu-id="10892-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="10892-148">**Acciones de entrada**</span><span class="sxs-lookup"><span data-stu-id="10892-148">**Input Actions**</span></span>

<span data-ttu-id="10892-149">Seleccione la acción [de entrada del](../input/input-actions.md) perfil de asignación de controlador o configuración de entrada al que debe reaccionar el componente *Interactable.*</span><span class="sxs-lookup"><span data-stu-id="10892-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="10892-150">Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .</span><span class="sxs-lookup"><span data-stu-id="10892-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="10892-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="10892-151">**IsGlobal**</span></span>

<span data-ttu-id="10892-152">Si es true, marcará el componente como un agente de escucha de entrada global para la acción [de entrada seleccionada.](../input/input-actions.md)</span><span class="sxs-lookup"><span data-stu-id="10892-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="10892-153">El comportamiento predeterminado es false, lo que restringirá la entrada solo a *este colisionador* o GameObject interactuable.</span><span class="sxs-lookup"><span data-stu-id="10892-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="10892-154">Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .</span><span class="sxs-lookup"><span data-stu-id="10892-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="10892-155">**Comando de voz**</span><span class="sxs-lookup"><span data-stu-id="10892-155">**Speech Command**</span></span>

<span data-ttu-id="10892-156">[Comando de voz](../input/speech.md), desde el perfil de comandos de voz de MRTK, para desencadenar un evento OnClick para la interacción de voz.</span><span class="sxs-lookup"><span data-stu-id="10892-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="10892-157">Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .</span><span class="sxs-lookup"><span data-stu-id="10892-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="10892-158">**Requiere foco**</span><span class="sxs-lookup"><span data-stu-id="10892-158">**Requires Focus**</span></span>

<span data-ttu-id="10892-159">Si es true, el comando de voz solo activará *interactuable* si y solo si ya tiene el foco de un puntero.</span><span class="sxs-lookup"><span data-stu-id="10892-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="10892-160">Si es false, *Interactable* actuará como agente de escucha global para el comando de voz seleccionado.</span><span class="sxs-lookup"><span data-stu-id="10892-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="10892-161">El comportamiento predeterminado es true, ya que varios agentes de escucha de voz globales pueden ser difíciles de organizar en una escena.</span><span class="sxs-lookup"><span data-stu-id="10892-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="10892-162">Esta propiedad se puede configurar en tiempo de ejecución en código a través de [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .</span><span class="sxs-lookup"><span data-stu-id="10892-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="10892-163">**Modo de selección**</span><span class="sxs-lookup"><span data-stu-id="10892-163">**Selection Mode**</span></span>

<span data-ttu-id="10892-164">Esta propiedad define la lógica de selección.</span><span class="sxs-lookup"><span data-stu-id="10892-164">This property defines the selection logic.</span></span> <span data-ttu-id="10892-165">Cuando se hace clic en un objeto *Interactable,* itera en un siguiente nivel *de* dimensión.</span><span class="sxs-lookup"><span data-stu-id="10892-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="10892-166">*Las dimensiones* son similares a rank y definen un estado fuera de las entradas (es decir,</span><span class="sxs-lookup"><span data-stu-id="10892-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="10892-167">focus, press etc.</span><span class="sxs-lookup"><span data-stu-id="10892-167">focus, press etc).</span></span> <span data-ttu-id="10892-168">Son útiles para definir estados de alternancia u otros estados de varias rangos asociados a un botón.</span><span class="sxs-lookup"><span data-stu-id="10892-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="10892-169">Realiza el seguimiento del nivel de dimensión `Interactable.DimensionIndex` actual.</span><span class="sxs-lookup"><span data-stu-id="10892-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="10892-170">Los modos de selección disponibles son:</span><span class="sxs-lookup"><span data-stu-id="10892-170">The selection modes available are:</span></span>

* <span data-ttu-id="10892-171">**Botón**  -  *Dimensiones* = 1, Simple Clickable *Interactable*</span><span class="sxs-lookup"><span data-stu-id="10892-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="10892-172">**Alternar**  -  *Dimensiones* = 2, *alternativas interactuables* entre *el estado de on* / *off*</span><span class="sxs-lookup"><span data-stu-id="10892-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="10892-173">**Varias dimensiones**  -  *Dimensiones >* = 3, cada clic aumenta el nivel de dimensión actual + 1.</span><span class="sxs-lookup"><span data-stu-id="10892-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="10892-174">Resulta útil para definir un estado de botón en una lista, etc.</span><span class="sxs-lookup"><span data-stu-id="10892-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="10892-175">*Interactable* también permite definir varios temas por *dimensión.*</span><span class="sxs-lookup"><span data-stu-id="10892-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="10892-176">Por ejemplo, *cuando SelectionMode=Toggle*, se puede aplicar un tema cuando se *deselecciona* *Interactable* y otro tema cuando se selecciona el *componente*.</span><span class="sxs-lookup"><span data-stu-id="10892-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="10892-177">El modo de selección actual se puede consultar en tiempo de ejecución a través de [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) .</span><span class="sxs-lookup"><span data-stu-id="10892-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="10892-178">La actualización del modo en tiempo de ejecución se puede lograr estableciendo la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) propiedad para que coincida con la funcionalidad deseada.</span><span class="sxs-lookup"><span data-stu-id="10892-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="10892-179">Además, se puede acceder a la dimensión actual, útil *para los* modos Alternar y Multi *dimension,* a través de [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .</span><span class="sxs-lookup"><span data-stu-id="10892-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="10892-180">Perfiles interactuables</span><span class="sxs-lookup"><span data-stu-id="10892-180">Interactable profiles</span></span>

<span data-ttu-id="10892-181">*Los perfiles* son elementos que crean una relación entre gameobject y tema [visual.](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="10892-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="10892-182">El perfil define qué contenido va a manipular un tema cuando se [produzca un cambio de estado.](#general-input-settings)</span><span class="sxs-lookup"><span data-stu-id="10892-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="10892-183">Los temas funcionan muy parecidos a los materiales.</span><span class="sxs-lookup"><span data-stu-id="10892-183">Themes work a lot like materials.</span></span> <span data-ttu-id="10892-184">Son objetos que pueden incluirse en scripts y que contienen una lista de propiedades que se asignarán a un objeto en función del estado actual.</span><span class="sxs-lookup"><span data-stu-id="10892-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="10892-185">Los temas también se pueden volver a usar y se pueden asignar a través de varios *objetos UX interactuables.*</span><span class="sxs-lookup"><span data-stu-id="10892-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="10892-186">**Restablecer al destruir**</span><span class="sxs-lookup"><span data-stu-id="10892-186">**Reset On Destroy**</span></span>

<span data-ttu-id="10892-187">Los temas visuales modifican varias propiedades en un GameObject de destino, en función de la clase y el tipo de motor de tema seleccionados.</span><span class="sxs-lookup"><span data-stu-id="10892-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="10892-188">Si *restablecer al destruir es* true cuando se destruye el componente interactuable, el componente restablecerá todas las propiedades modificadas de los temas activos a sus valores originales.</span><span class="sxs-lookup"><span data-stu-id="10892-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="10892-189">De lo contrario, cuando se destruye, el componente Interactable dejará las propiedades modificadas tal y como están.</span><span class="sxs-lookup"><span data-stu-id="10892-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="10892-190">En este último caso, el último estado de los valores se conservará a menos que otro componente externo lo haya modificado.</span><span class="sxs-lookup"><span data-stu-id="10892-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="10892-191">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="10892-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="10892-192">Eventos</span><span class="sxs-lookup"><span data-stu-id="10892-192">Events</span></span>

<span data-ttu-id="10892-193">Cada *componente interactuable* tiene un *evento OnClick* que se produce cuando el componente se selecciona simplemente.</span><span class="sxs-lookup"><span data-stu-id="10892-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="10892-194">Sin embargo, *Interactable* se puede usar para detectar eventos de entrada que no sean solo *OnClick.*</span><span class="sxs-lookup"><span data-stu-id="10892-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="10892-195">Haga clic en *el botón Agregar* evento para agregar un nuevo tipo de definición de receptor de eventos.</span><span class="sxs-lookup"><span data-stu-id="10892-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="10892-196">Una vez agregado, seleccione el tipo de evento deseado.</span><span class="sxs-lookup"><span data-stu-id="10892-196">Once added, select the type of Event desired.</span></span>

![Ejemplo de eventos](../images/interactable/Events.png)<span data-ttu-id="10892-198">)</span><span class="sxs-lookup"><span data-stu-id="10892-198">)</span></span>

<span data-ttu-id="10892-199">Hay diferentes tipos de receptores de eventos para responder a distintos tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="10892-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="10892-200">MRTK se suministra con el siguiente conjunto de receptores de serie.</span><span class="sxs-lookup"><span data-stu-id="10892-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="10892-201">Se puede crear un receptor personalizado creando una nueva clase que extienda [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .</span><span class="sxs-lookup"><span data-stu-id="10892-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![Ejemplo de receptor de alternancia de eventos](../images/interactable/Event_toggle.png)

<span data-ttu-id="10892-203">*Ejemplo de un receptor de eventos toggle*</span><span class="sxs-lookup"><span data-stu-id="10892-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="10892-204">Receptores interactuables</span><span class="sxs-lookup"><span data-stu-id="10892-204">Interactable receivers</span></span>

 <span data-ttu-id="10892-205">El componente permite definir eventos fuera del [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente *interactuable de* origen.</span><span class="sxs-lookup"><span data-stu-id="10892-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="10892-206">*InteractableReceiver* escuchará un tipo de evento filtrado desencadenado por otro *objeto Interactable.*</span><span class="sxs-lookup"><span data-stu-id="10892-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="10892-207">Si la propiedad *Interactable* no se  asigna directamente, la propiedad Ámbito de búsqueda define la dirección en la que *InteractableReceiver* escucha eventos que están en sí mismo, en un elemento primario o en un Elemento GameObject secundario.</span><span class="sxs-lookup"><span data-stu-id="10892-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="10892-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) actúa de forma similar, pero para obtener una lista de eventos de coincidencia.</span><span class="sxs-lookup"><span data-stu-id="10892-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="10892-209">Creación de eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="10892-209">Create custom events</span></span>

<span data-ttu-id="10892-210">Al [igual que los temas](visual-themes.md#custom-theme-engines)visuales, los eventos se pueden extender para detectar cualquier patrón de estado o para exponer la funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="10892-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="10892-211">Los eventos personalizados se pueden crear de dos maneras principales:</span><span class="sxs-lookup"><span data-stu-id="10892-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="10892-212">[`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase)Extienda la clase para crear un evento personalizado que se mostrará en la lista desplegable de tipos de eventos.</span><span class="sxs-lookup"><span data-stu-id="10892-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="10892-213">Se proporciona un evento de Unity de forma predeterminada, pero se pueden agregar eventos de Unity adicionales o se puede establecer el evento para ocultar los eventos de Unity.</span><span class="sxs-lookup"><span data-stu-id="10892-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="10892-214">Esta funcionalidad permite a un diseñador trabajar con un ingeniero en un proyecto para crear un evento personalizado que el diseñador puede configurar en el editor.</span><span class="sxs-lookup"><span data-stu-id="10892-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="10892-215">[`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)Extienda la clase para crear un componente de evento completamente personalizado que pueda residir en *interactuable* u otro objeto.</span><span class="sxs-lookup"><span data-stu-id="10892-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="10892-216">hará [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) referencia a *Interactable para* detectar cambios de estado.</span><span class="sxs-lookup"><span data-stu-id="10892-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="10892-217">Ejemplo de extensión `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="10892-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="10892-218">La [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) clase muestra información de estado sobre un objeto *Interactable* y es un ejemplo de cómo crear un receptor de eventos personalizado.</span><span class="sxs-lookup"><span data-stu-id="10892-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="10892-219">Los métodos siguientes son útiles para invalidar o implementar al crear un receptor de eventos personalizado.</span><span class="sxs-lookup"><span data-stu-id="10892-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="10892-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) es un método abstracto que se puede usar para detectar patrones de estado o transiciones.</span><span class="sxs-lookup"><span data-stu-id="10892-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="10892-221">Además, los [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) métodos y son útiles para crear lógica de eventos personalizada cuando se selecciona *Interactable.*</span><span class="sxs-lookup"><span data-stu-id="10892-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="10892-222">Mostrar campos de receptor de eventos personalizados en el inspector</span><span class="sxs-lookup"><span data-stu-id="10892-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="10892-223">Los scripts *de ReceiverBase* [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) usan atributos para exponer propiedades personalizadas en el inspector.</span><span class="sxs-lookup"><span data-stu-id="10892-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="10892-224">Este es un ejemplo de Vector3, una propiedad personalizada con información sobre herramientas y etiquetas.</span><span class="sxs-lookup"><span data-stu-id="10892-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="10892-225">Esta propiedad se mostrará como configurable en el inspector cuando se selecciona un GameObject *interactuable* y se agrega el tipo *de receptor* de eventos asociado.</span><span class="sxs-lookup"><span data-stu-id="10892-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="10892-226">Uso de Interactable</span><span class="sxs-lookup"><span data-stu-id="10892-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="10892-227">Creación de un botón sencillo</span><span class="sxs-lookup"><span data-stu-id="10892-227">Building a simple button</span></span>

<span data-ttu-id="10892-228">Se puede crear un botón simple agregando el *componente Interactable* a un GameObject que está configurado para recibir eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="10892-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="10892-229">Puede tener un colisionador en él o en un elemento secundario para recibir la entrada.</span><span class="sxs-lookup"><span data-stu-id="10892-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="10892-230">Si usa *Interactable* with a Unity UI based GameObjects (Objetos GameObject basados en interfaz de usuario de Unity), debe estar en Canvas GameObject.</span><span class="sxs-lookup"><span data-stu-id="10892-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="10892-231">Tome el botón un paso más allá, creando un nuevo perfil, asignando el propio GameObject y creando un nuevo tema.</span><span class="sxs-lookup"><span data-stu-id="10892-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="10892-232">Además, use el *evento OnClick* para que suceda algo.</span><span class="sxs-lookup"><span data-stu-id="10892-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="10892-233">Hacer que [un botón se puede presionar](button.md) requiere el componente [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) .</span><span class="sxs-lookup"><span data-stu-id="10892-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="10892-234">Además, el componente [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) es necesario para canalizar eventos de presión al *componente Interactable.*</span><span class="sxs-lookup"><span data-stu-id="10892-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="10892-235">Creación de botones de alternancia y de varias dimensiones</span><span class="sxs-lookup"><span data-stu-id="10892-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="10892-236">Botón de alternancia</span><span class="sxs-lookup"><span data-stu-id="10892-236">Toggle button</span></span>

<span data-ttu-id="10892-237">Para que un botón pueda alternar, cambie el [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo para escribir `Toggle` .</span><span class="sxs-lookup"><span data-stu-id="10892-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="10892-238">En la *sección Perfiles,* se agrega un nuevo tema alternado para cada perfil que se usa cuando se activa *interactuable.*</span><span class="sxs-lookup"><span data-stu-id="10892-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="10892-239">Mientras se establece en Toggle, se puede usar la casilla [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) *IsToggled* para establecer el valor predeterminado del control en la inicialización en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="10892-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="10892-240">*CanSelect* significa que *Interactable* puede pasar de *desactivado a* *on,* mientras que *CanDeselect* significa inverso.</span><span class="sxs-lookup"><span data-stu-id="10892-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![Ejemplo de temas visuales de alternancia de perfil](../images/interactable/Profile_toggle.png)

<span data-ttu-id="10892-242">Los desarrolladores pueden usar [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) las interfaces y para obtener o establecer el estado de alternancia de un objeto *Interactable* mediante código.</span><span class="sxs-lookup"><span data-stu-id="10892-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="10892-243">Alternar colección de botones</span><span class="sxs-lookup"><span data-stu-id="10892-243">Toggle button collection</span></span>

<span data-ttu-id="10892-244">Es habitual tener una lista de botones de alternancia donde solo uno puede estar activo en un momento dado, también conocido como un conjunto radial o botones de radio, etc.</span><span class="sxs-lookup"><span data-stu-id="10892-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="10892-245">Use el [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente para habilitar esta funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="10892-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="10892-246">Este control garantiza que solo se *active un interactable* en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="10892-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="10892-247">*RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) también es un excelente punto de partida desde el principio.</span><span class="sxs-lookup"><span data-stu-id="10892-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="10892-248">Para crear un grupo de botones radiales personalizado:</span><span class="sxs-lookup"><span data-stu-id="10892-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="10892-249">Creación de *varios objetos* GameObject o botones interactuables</span><span class="sxs-lookup"><span data-stu-id="10892-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="10892-250">Establecer cada *interactable* con *SelectionMode* = Toggle, *CanSelect* = true y *CanDeselect* = false</span><span class="sxs-lookup"><span data-stu-id="10892-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="10892-251">Cree un elemento GameObject primario vacío en *todos los elementos Interactables* y agregue el *componente InteractableToggleCollection.*</span><span class="sxs-lookup"><span data-stu-id="10892-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="10892-252">Agregar todos *los elementos Interactables* a *ToggleList* en *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="10892-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="10892-253">Establezca la *propiedad InteractableToggleCollection.CurrentIndex* para determinar qué botón está seleccionado de forma predeterminada al principio.</span><span class="sxs-lookup"><span data-stu-id="10892-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="10892-254">Botón multidimensional</span><span class="sxs-lookup"><span data-stu-id="10892-254">Multi-dimensional button</span></span>

<span data-ttu-id="10892-255">El modo de selección de varias dimensiones se usa para crear botones secuenciales, o un botón que tiene más de dos pasos, como controlar la velocidad con tres valores, Rápido (1x), Más rápido (2x) o Más rápido (3x).</span><span class="sxs-lookup"><span data-stu-id="10892-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="10892-256">Como las dimensiones son un valor numérico, se pueden agregar hasta 9 temas para controlar la etiqueta de texto o la textura del botón para cada configuración de velocidad, usando un tema diferente para cada paso.</span><span class="sxs-lookup"><span data-stu-id="10892-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="10892-257">Cada evento de clic avanzará en 1 en tiempo `DimensionIndex` de ejecución hasta que se alcance el `Dimensions` valor.</span><span class="sxs-lookup"><span data-stu-id="10892-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="10892-258">A continuación, el ciclo se restablecerá a 0.</span><span class="sxs-lookup"><span data-stu-id="10892-258">Then the cycle will reset to 0.</span></span>

![Ejemplo de perfil multidimensional](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="10892-260">Los desarrolladores pueden evaluar [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) para determinar qué dimensión está activa actualmente.</span><span class="sxs-lookup"><span data-stu-id="10892-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="10892-261">Creación de Interactable en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="10892-261">Create Interactable at runtime</span></span>

<span data-ttu-id="10892-262">*Interactable* se puede agregar fácilmente a cualquier GameObject en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="10892-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="10892-263">En el ejemplo siguiente se muestra cómo asignar un perfil con un [tema visual](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="10892-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a><span data-ttu-id="10892-264">Eventos interactuables a través de código</span><span class="sxs-lookup"><span data-stu-id="10892-264">Interactable events via code</span></span>

<span data-ttu-id="10892-265">Se puede agregar una acción al evento base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) a través del código con el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="10892-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="10892-266">Use la función [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) para agregar receptores de eventos dinámicamente en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="10892-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="10892-267">En el código de ejemplo siguiente se muestra cómo agregar un [objeto InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escucha la entrada y salida del foco y, además, definir el código de acción que se realizará cuando se desenfoque la instancia de evento.</span><span class="sxs-lookup"><span data-stu-id="10892-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="10892-268">En el código de ejemplo siguiente se muestra cómo agregar un [objeto InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escucha las transiciones de estado seleccionadas o deseleccionada en interactuables con alternancia y, además, define el código de acción que se realizará cuando se activen las instancias de evento. </span><span class="sxs-lookup"><span data-stu-id="10892-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a><span data-ttu-id="10892-269">Consulte también</span><span class="sxs-lookup"><span data-stu-id="10892-269">See also</span></span>

* [<span data-ttu-id="10892-270">Temas visuales</span><span class="sxs-lookup"><span data-stu-id="10892-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="10892-271">Acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="10892-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="10892-272">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="10892-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="10892-273">Botones</span><span class="sxs-lookup"><span data-stu-id="10892-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="10892-274">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="10892-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
