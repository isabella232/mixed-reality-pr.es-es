---
title: Objeto con el que se puede interactuar
description: Aprenda a desencadenar eventos, proporcionar indicaciones visuales e interactuar con objetos en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, señales, interfaz de usuario, experiencia de usuario, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, audio
ms.openlocfilehash: d0dc8ce6425d597d04b47a6c8b08f72534488594
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007205"
---
# <a name="interactable-object"></a><span data-ttu-id="66e5e-104">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="66e5e-104">Interactable object</span></span>

![Objetos interactivos](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="66e5e-106">Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="66e5e-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="66e5e-107">En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.</span><span class="sxs-lookup"><span data-stu-id="66e5e-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="66e5e-108">Cualquier elemento puede ser un **objeto interactuable** que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="66e5e-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="66e5e-109">Un objeto interactuable puede ser cualquier cosa, desde una taza de café de una tabla hasta un globo de midair.</span><span class="sxs-lookup"><span data-stu-id="66e5e-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="66e5e-110">Todavía hacemos uso de botones tradicionales en ciertas situaciones, como en la interfaz de usuario del cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="66e5e-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="66e5e-111">La representación visual del botón depende del contexto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="66e5e-112">Propiedades importantes del objeto interactuable</span><span class="sxs-lookup"><span data-stu-id="66e5e-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="66e5e-113">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="66e5e-113">Visual cues</span></span>

<span data-ttu-id="66e5e-114">Las indicaciones visuales son indicaciones organolépticas de la luz, recibidas por el ojo y procesadas por el sistema visual durante la percepción visual.</span><span class="sxs-lookup"><span data-stu-id="66e5e-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="66e5e-115">Dado que el sistema visual es dominante en muchas especies, especialmente en los seres humanos, las indicaciones visuales son una gran fuente de información sobre cómo se percibe el mundo.</span><span class="sxs-lookup"><span data-stu-id="66e5e-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="66e5e-116">Dado que los objetos holográficas se mezclan con el entorno real en realidad mixta, podría ser difícil comprender con qué objetos puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="66e5e-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="66e5e-117">En el caso de cualquier objeto interactuable de su experiencia, es importante proporcionar indicaciones visuales diferenciadas para cada estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="66e5e-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="66e5e-118">Esto ayuda al usuario a comprender qué parte de su experiencia es interactivable y hace que el usuario esté seguro mediante el uso de un método de interacción coherente.</span><span class="sxs-lookup"><span data-stu-id="66e5e-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="66e5e-119">Interacciones lejanas</span><span class="sxs-lookup"><span data-stu-id="66e5e-119">Far interactions</span></span>

<span data-ttu-id="66e5e-120">En el caso de los objetos a los que el usuario pueda interactuar con la mirada, el rayo y el rayo del controlador de movimiento, se recomienda tener una indicación visual diferente para estos tres Estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="66e5e-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="66e5e-121">![interactibleobject-Estados-predeterminado](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-121">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="66e5e-122">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="66e5e-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="66e5e-123">Estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-123">Default idle state of the object.</span></span>
    <span data-ttu-id="66e5e-124">El cursor no está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-124">The cursor isn't on the object.</span></span> <span data-ttu-id="66e5e-125">No se detecta la mano.</span><span class="sxs-lookup"><span data-stu-id="66e5e-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="66e5e-126">![interactibleobject-Estados-dirigidos](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-126">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="66e5e-127">**Estado de destino (mantener el mouse)**</span><span class="sxs-lookup"><span data-stu-id="66e5e-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="66e5e-128">Cuando el objeto se destine con el cursor de miración, la proximidad del dedo o el puntero del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="66e5e-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="66e5e-129">El cursor está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-129">The cursor is on the object.</span></span> <span data-ttu-id="66e5e-130">La mano se detecta y está lista.</span><span class="sxs-lookup"><span data-stu-id="66e5e-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="66e5e-131">![interactibleobject-Estados-presionado](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-131">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="66e5e-132">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="66e5e-132">**Pressed state**</span></span><br>
        <span data-ttu-id="66e5e-133">Cuando el objeto se presiona con un gesto de pulsación de aire, presionar el dedo o el botón seleccionar del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="66e5e-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="66e5e-134">El cursor está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-134">The cursor is on the object.</span></span> <span data-ttu-id="66e5e-135">Se detecta una mano, se puntea en el aire.</span><span class="sxs-lookup"><span data-stu-id="66e5e-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="66e5e-136">Puede usar técnicas como resaltado o escalado para proporcionar indicaciones visuales para el estado de entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="66e5e-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="66e5e-137">En la realidad mixta, puede encontrar ejemplos de visualización de distintos Estados de entrada en el menú Inicio y con botones de barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="66e5e-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="66e5e-138">Este es el aspecto de estos Estados en un **botón holográfica**:</span><span class="sxs-lookup"><span data-stu-id="66e5e-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="66e5e-139">![interactibleobject-Estados-predeterminado](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-139">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="66e5e-140">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="66e5e-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="66e5e-141">![interactibleobject-Estados-dirigidos](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-141">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="66e5e-142">**Estado de destino (mantener el mouse)**</span><span class="sxs-lookup"><span data-stu-id="66e5e-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="66e5e-143">![interactibleobject-Estados-presionado](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-143">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="66e5e-144">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="66e5e-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="66e5e-145">Interacciones cercanas (directas)</span><span class="sxs-lookup"><span data-stu-id="66e5e-145">Near interactions (direct)</span></span> 

<span data-ttu-id="66e5e-146">HoloLens 2 admite la entrada de seguimiento de mano articulada, que permite interactuar con objetos.</span><span class="sxs-lookup"><span data-stu-id="66e5e-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="66e5e-147">Sin comentarios hápticos e percepción de profundidad perfecta, puede ser difícil saber hasta dónde se encuentra la mano de un objeto o si se está tocando.</span><span class="sxs-lookup"><span data-stu-id="66e5e-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="66e5e-148">Es importante proporcionar suficientes indicaciones visuales para comunicar el estado del objeto, en particular el estado de las manos basadas en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="66e5e-149">Use los comentarios visuales para comunicar los siguientes Estados:</span><span class="sxs-lookup"><span data-stu-id="66e5e-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="66e5e-150">**Predeterminado (observación)**: estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="66e5e-151">**Mantener el mouse**: cuando una mano está cerca de un holograma, cambie los objetos visuales para comunicar que esa mano está dirigida al holograma.</span><span class="sxs-lookup"><span data-stu-id="66e5e-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="66e5e-152">**Distancia y punto de interacción**: a medida que la mano se aproxima a un holograma, el diseño de comentarios para comunicar el punto de interacción previsto y la distancia desde el objeto que es el dedo</span><span class="sxs-lookup"><span data-stu-id="66e5e-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="66e5e-153">**Inicio de contacto**: cambie los objetos visuales (Light, color) para comunicar que se ha producido una entrada táctil</span><span class="sxs-lookup"><span data-stu-id="66e5e-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="66e5e-154">**Agarre**: cambiar objetos visuales (claros, de color) cuando se agarre el objeto</span><span class="sxs-lookup"><span data-stu-id="66e5e-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="66e5e-155">**Extremos de contacto**: cambios visuales (claros, de color) cuando la entrada táctil ha finalizado</span><span class="sxs-lookup"><span data-stu-id="66e5e-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="66e5e-156">![Mantener el mouse (lejano)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="66e5e-157">**Mantener el mouse (lejano)**</span><span class="sxs-lookup"><span data-stu-id="66e5e-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="66e5e-158">Resaltado en función de la proximidad de la mano.</span><span class="sxs-lookup"><span data-stu-id="66e5e-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="66e5e-159">![Mantener el mouse (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="66e5e-160">**Mantener el mouse (Near)**</span><span class="sxs-lookup"><span data-stu-id="66e5e-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="66e5e-161">Resaltar cambios de tamaño en función de la distancia a la mano.</span><span class="sxs-lookup"><span data-stu-id="66e5e-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="66e5e-162">![Tocar y presionar](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="66e5e-163">**Tocar y presionar**</span><span class="sxs-lookup"><span data-stu-id="66e5e-163">**Touch / press**</span></span><br>
        <span data-ttu-id="66e5e-164">Comentarios de Visual Plus audio.</span><span class="sxs-lookup"><span data-stu-id="66e5e-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="66e5e-165">![Visión](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="66e5e-166">**Visión**</span><span class="sxs-lookup"><span data-stu-id="66e5e-166">**Grasp**</span></span><br>
        <span data-ttu-id="66e5e-167">Comentarios de Visual Plus audio.</span><span class="sxs-lookup"><span data-stu-id="66e5e-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="66e5e-168">Un [botón de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) es un ejemplo de cómo se visualizan los distintos Estados de interacción de entrada:</span><span class="sxs-lookup"><span data-stu-id="66e5e-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="66e5e-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="66e5e-170">**Valor predeterminado**</span><span class="sxs-lookup"><span data-stu-id="66e5e-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="66e5e-171">![Al mantener el puntero](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="66e5e-172">**Al mantener el puntero**</span><span class="sxs-lookup"><span data-stu-id="66e5e-172">**Hover**</span></span><br>
        <span data-ttu-id="66e5e-173">Revela un efecto de iluminación basado en proximidad.</span><span class="sxs-lookup"><span data-stu-id="66e5e-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="66e5e-174">![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="66e5e-175">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="66e5e-175">**Touch**</span></span><br>
        <span data-ttu-id="66e5e-176">Mostrar efecto de rizo.</span><span class="sxs-lookup"><span data-stu-id="66e5e-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="66e5e-177">![Presione](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="66e5e-178">**Presione**</span><span class="sxs-lookup"><span data-stu-id="66e5e-178">**Press**</span></span><br>
        <span data-ttu-id="66e5e-179">Mueva la placa frontal.</span><span class="sxs-lookup"><span data-stu-id="66e5e-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="66e5e-180">La indicación visual "Ring" en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="66e5e-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="66e5e-181">En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción del usuario de la profundidad.</span><span class="sxs-lookup"><span data-stu-id="66e5e-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="66e5e-182">Se muestra un anillo cerca de su dedo y se reduce verticalmente a medida que la mano se acerca al objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="66e5e-183">El anillo finalmente converge en un punto cuando se alcanza el estado presionado.</span><span class="sxs-lookup"><span data-stu-id="66e5e-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="66e5e-184">Esta prestación visual ayuda al usuario a comprender hasta qué punto proceden del objeto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="66e5e-185">*Bucle de vídeo: ejemplo de comentarios visuales basados en proximidad a un cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="66e5e-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="66e5e-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="66e5e-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="66e5e-187">![Comentarios visuales en proximidad](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="66e5e-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="66e5e-188">Señales de audio</span><span class="sxs-lookup"><span data-stu-id="66e5e-188">Audio cues</span></span>

<span data-ttu-id="66e5e-189">En el caso de las interacciones directas, los comentarios de audio adecuados pueden mejorar drásticamente la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="66e5e-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="66e5e-190">Use comentarios de audio para comunicar las siguientes indicaciones:</span><span class="sxs-lookup"><span data-stu-id="66e5e-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="66e5e-191">**Inicio de contacto**: reproducir un sonido cuando se inicie Touch</span><span class="sxs-lookup"><span data-stu-id="66e5e-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="66e5e-192">**Contactos** finales: reproducir sonido en el extremo táctil</span><span class="sxs-lookup"><span data-stu-id="66e5e-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="66e5e-193">**Inicio** de la toma: reproducir sonido cuando se inicie la captura</span><span class="sxs-lookup"><span data-stu-id="66e5e-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="66e5e-194">Acabado de **agarre**: reproducir un sonido al finalizar la toma</span><span class="sxs-lookup"><span data-stu-id="66e5e-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="66e5e-195">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="66e5e-195">Voice commanding</span></span><br>
        <span data-ttu-id="66e5e-196">En el caso de los objetos interactuables, es importante admitir opciones de interacción alternativas.</span><span class="sxs-lookup"><span data-stu-id="66e5e-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="66e5e-197">De forma predeterminada, se recomienda que se admitan los [comandos de voz](../out-of-scope/voice-design.md) para cualquier objeto que sea interactuable.</span><span class="sxs-lookup"><span data-stu-id="66e5e-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="66e5e-198">Para mejorar la capacidad de detección, también puede proporcionar una información sobre herramientas durante el estado de mantener el mouse.</span><span class="sxs-lookup"><span data-stu-id="66e5e-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="66e5e-199">*Image: información sobre herramientas para el comando Voice*</span><span class="sxs-lookup"><span data-stu-id="66e5e-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comandos de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="66e5e-201">Recomendaciones de tamaño</span><span class="sxs-lookup"><span data-stu-id="66e5e-201">Sizing recommendations</span></span> 

<span data-ttu-id="66e5e-202">Para asegurarse de que todos los objetos interactivos se pueden tocar fácilmente, se recomienda asegurarse de que el interactuable cumple un tamaño mínimo en función de la distancia que se coloca del usuario.</span><span class="sxs-lookup"><span data-stu-id="66e5e-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="66e5e-203">El ángulo visual se mide a menudo en grados de arco visual. El ángulo visual se basa en la distancia entre los ojos del usuario y el objeto y permanece constante, mientras que el tamaño físico del destino puede cambiar a medida que cambia la distancia del usuario.</span><span class="sxs-lookup"><span data-stu-id="66e5e-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="66e5e-204">Para determinar el tamaño físico necesario de un objeto en función de la distancia del usuario, pruebe a usar una calculadora de ángulo visual como [esta](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="66e5e-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="66e5e-205">A continuación se muestran las recomendaciones para tamaños mínimos de contenido interactuable.</span><span class="sxs-lookup"><span data-stu-id="66e5e-205">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="66e5e-206">Tamaño de destino para la interacción directa</span><span class="sxs-lookup"><span data-stu-id="66e5e-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="66e5e-207">Distancia</span><span class="sxs-lookup"><span data-stu-id="66e5e-207">Distance</span></span> | <span data-ttu-id="66e5e-208">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="66e5e-208">Viewing angle</span></span> | <span data-ttu-id="66e5e-209">Size</span><span class="sxs-lookup"><span data-stu-id="66e5e-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="66e5e-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="66e5e-210">45 cm</span></span>  | <span data-ttu-id="66e5e-211">no menor que 2 °</span><span class="sxs-lookup"><span data-stu-id="66e5e-211">no smaller than 2°</span></span> | <span data-ttu-id="66e5e-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="66e5e-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="66e5e-213">![Tamaño de destino para la interacción directa](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="66e5e-214">*Tamaño de destino para la interacción directa*</span><span class="sxs-lookup"><span data-stu-id="66e5e-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="66e5e-215">Tamaño de destino de los botones</span><span class="sxs-lookup"><span data-stu-id="66e5e-215">Target size for buttons</span></span>

<span data-ttu-id="66e5e-216">Al crear botones para la interacción directa, se recomienda un tamaño mínimo mayor de 3,2 x 3,2 cm para asegurarse de que hay espacio suficiente para contener un icono y un posible texto.</span><span class="sxs-lookup"><span data-stu-id="66e5e-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="66e5e-217">Distancia</span><span class="sxs-lookup"><span data-stu-id="66e5e-217">Distance</span></span> | <span data-ttu-id="66e5e-218">Tamaño mínimo</span><span class="sxs-lookup"><span data-stu-id="66e5e-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="66e5e-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="66e5e-219">45 cm</span></span>  | <span data-ttu-id="66e5e-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="66e5e-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="66e5e-221">![Tamaño de destino de los botones](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="66e5e-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="66e5e-222">*Tamaño de destino de los botones*</span><span class="sxs-lookup"><span data-stu-id="66e5e-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="66e5e-223">Tamaño de destino para la interacción de mano o de rayo</span><span class="sxs-lookup"><span data-stu-id="66e5e-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="66e5e-224">Distancia</span><span class="sxs-lookup"><span data-stu-id="66e5e-224">Distance</span></span> | <span data-ttu-id="66e5e-225">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="66e5e-225">Viewing angle</span></span> | <span data-ttu-id="66e5e-226">Size</span><span class="sxs-lookup"><span data-stu-id="66e5e-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="66e5e-227">2 m</span><span class="sxs-lookup"><span data-stu-id="66e5e-227">2 m</span></span>  | <span data-ttu-id="66e5e-228">no menor que 1 °</span><span class="sxs-lookup"><span data-stu-id="66e5e-228">no smaller than 1°</span></span> | <span data-ttu-id="66e5e-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="66e5e-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="66e5e-230">![Tamaño de destino para la interacción de mano o de rayo](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="66e5e-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="66e5e-231">*Tamaño de destino para la interacción de mano o de rayo*</span><span class="sxs-lookup"><span data-stu-id="66e5e-231">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="66e5e-232">Objeto interactuable en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="66e5e-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="66e5e-233">En **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, puede usar el script [**interactúable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para que los objetos respondan a diversos tipos de Estados de interacción de entrada.</span><span class="sxs-lookup"><span data-stu-id="66e5e-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="66e5e-234">Admite varios tipos de temas que permiten definir Estados visuales mediante el control de las propiedades del objeto como el color, el tamaño, el material y el sombreador.</span><span class="sxs-lookup"><span data-stu-id="66e5e-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="66e5e-235">Interactuable</span><span class="sxs-lookup"><span data-stu-id="66e5e-235">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="66e5e-236">Button</span><span class="sxs-lookup"><span data-stu-id="66e5e-236">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="66e5e-237">Escena de ejemplos de interacción de mano</span><span class="sxs-lookup"><span data-stu-id="66e5e-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="66e5e-238">El sombreador estándar de MixedRealityToolkit proporciona varias opciones, como la **luz de proximidad** , que le ayuda a crear indicaciones visuales y de audio.</span><span class="sxs-lookup"><span data-stu-id="66e5e-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="66e5e-239">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="66e5e-239">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="66e5e-240">Consulte también</span><span class="sxs-lookup"><span data-stu-id="66e5e-240">See also</span></span>

* [<span data-ttu-id="66e5e-241">Cursores</span><span class="sxs-lookup"><span data-stu-id="66e5e-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="66e5e-242">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="66e5e-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="66e5e-243">Botón</span><span class="sxs-lookup"><span data-stu-id="66e5e-243">Button</span></span>](button.md)
* [<span data-ttu-id="66e5e-244">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="66e5e-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="66e5e-245">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="66e5e-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="66e5e-246">Manipulación</span><span class="sxs-lookup"><span data-stu-id="66e5e-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="66e5e-247">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="66e5e-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="66e5e-248">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="66e5e-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="66e5e-249">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="66e5e-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="66e5e-250">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="66e5e-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="66e5e-251">Teclado</span><span class="sxs-lookup"><span data-stu-id="66e5e-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="66e5e-252">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="66e5e-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="66e5e-253">Claqueta</span><span class="sxs-lookup"><span data-stu-id="66e5e-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="66e5e-254">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="66e5e-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="66e5e-255">Sombreador</span><span class="sxs-lookup"><span data-stu-id="66e5e-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="66e5e-256">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="66e5e-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="66e5e-257">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="66e5e-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="66e5e-258">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="66e5e-258">Surface magnetism</span></span>](surface-magnetism.md)
