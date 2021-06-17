---
title: Objeto con el que se puede interactuar
description: Obtenga información sobre cómo desencadenar eventos, proporcionar indicaciones visuales e interactuar con objetos en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, controles, interacción, indicaciones, interfaz de usuario, experiencia de usuario, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, audio
ms.openlocfilehash: b25c25a6dd48bcc85a556787099734d147d18df2
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110214"
---
# <a name="interactable-object"></a><span data-ttu-id="30a56-104">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="30a56-104">Interactable object</span></span>

![Objetos interactuables](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="30a56-106">Un botón ha sido durante mucho tiempo una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="30a56-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="30a56-107">En el mundo de la realidad mixta tridimensional, ya no tenemos que limitarnos a este mundo de abstracción.</span><span class="sxs-lookup"><span data-stu-id="30a56-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="30a56-108">Cualquier elemento puede ser un **objeto interactuable** que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="30a56-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="30a56-109">Un objeto interactuable puede ser cualquier cosa, desde una cafetera de una mesa hasta un globo en el aire.</span><span class="sxs-lookup"><span data-stu-id="30a56-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="30a56-110">Todavía usamos los botones tradicionales en determinadas situaciones, como en la interfaz de usuario del cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="30a56-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="30a56-111">La representación visual del botón depende del contexto.</span><span class="sxs-lookup"><span data-stu-id="30a56-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="30a56-112">Propiedades importantes del objeto que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="30a56-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="30a56-113">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="30a56-113">Visual cues</span></span>

<span data-ttu-id="30a56-114">Las indicaciones visuales son indicaciones sensoras de la luz, recibidas por el ojo y procesadas por el sistema visual durante la percepción visual.</span><span class="sxs-lookup"><span data-stu-id="30a56-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="30a56-115">Dado que el sistema visual es dominante en muchas especie, especialmente en los seres humanos, las indicaciones visuales son una gran fuente de información sobre cómo se percibe el mundo.</span><span class="sxs-lookup"><span data-stu-id="30a56-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="30a56-116">Puesto que los objetos holográficos se combinan con el entorno real en la realidad mixta, podría ser difícil comprender con qué objetos puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="30a56-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="30a56-117">Para los objetos que pueden interactuar en su experiencia, es importante proporcionar indicaciones visuales diferenciadas para cada estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="30a56-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="30a56-118">Esto ayuda al usuario a comprender qué parte de su experiencia es interactuable y hace que el usuario esté seguro mediante un método de interacción coherente.</span><span class="sxs-lookup"><span data-stu-id="30a56-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="30a56-119">Interacciones lejanas</span><span class="sxs-lookup"><span data-stu-id="30a56-119">Far interactions</span></span>

<span data-ttu-id="30a56-120">Para cualquier objeto que el usuario pueda interactuar con la mirada, el rayo de la mano y el rayo del controlador de movimiento, se recomienda tener una indicación visual diferente para estos tres estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="30a56-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="30a56-121">![Objeto interactuable con estado predeterminado](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="30a56-122">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="30a56-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="30a56-123">Estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="30a56-123">Default idle state of the object.</span></span>
    <span data-ttu-id="30a56-124">El cursor no está en el objeto .</span><span class="sxs-lookup"><span data-stu-id="30a56-124">The cursor isn't on the object.</span></span> <span data-ttu-id="30a56-125">No se detecta la mano.</span><span class="sxs-lookup"><span data-stu-id="30a56-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="30a56-126">![Objeto que se puede interactuar con el estado de destino y de mantener el puntero](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="30a56-127">**Estado de destino (mantener el puntero)**</span><span class="sxs-lookup"><span data-stu-id="30a56-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="30a56-128">Cuando el objeto tiene como destino el cursor de mirada, la proximidad del dedo o el puntero del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="30a56-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="30a56-129">El cursor está en el objeto .</span><span class="sxs-lookup"><span data-stu-id="30a56-129">The cursor is on the object.</span></span> <span data-ttu-id="30a56-130">Se detecta la mano, está lista.</span><span class="sxs-lookup"><span data-stu-id="30a56-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="30a56-131">![Objeto interactuable con estado presionado](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="30a56-132">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="30a56-132">**Pressed state**</span></span><br>
        <span data-ttu-id="30a56-133">Cuando el objeto se presiona con un gesto de pulsación en el aire, presione el dedo o el botón de selección del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="30a56-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="30a56-134">El cursor está en el objeto .</span><span class="sxs-lookup"><span data-stu-id="30a56-134">The cursor is on the object.</span></span> <span data-ttu-id="30a56-135">Se detecta la mano, se pulsa en el aire.</span><span class="sxs-lookup"><span data-stu-id="30a56-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="30a56-136">Puede usar técnicas como el resaltado o el escalado para proporcionar indicaciones visuales para el estado de entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="30a56-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="30a56-137">En realidad mixta, puede encontrar ejemplos de visualización de distintos estados de entrada en el menú Inicio y con botones de la barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30a56-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="30a56-138">Este es el aspecto de estos estados en un **botón holográfico:**</span><span class="sxs-lookup"><span data-stu-id="30a56-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="30a56-139">![Botón holográfico en estado predeterminado](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="30a56-140">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="30a56-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="30a56-141">![Botón holográfico en estado de destino y mantener el puntero](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="30a56-142">**Estado de destino (mantener el puntero)**</span><span class="sxs-lookup"><span data-stu-id="30a56-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="30a56-143">![Botón holográfico en estado presionado](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="30a56-144">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="30a56-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="30a56-145">Interacciones cercanas (directas)</span><span class="sxs-lookup"><span data-stu-id="30a56-145">Near interactions (direct)</span></span> 

<span data-ttu-id="30a56-146">HoloLens 2 admite la entrada de seguimiento de manos articulada, que permite interactuar con objetos.</span><span class="sxs-lookup"><span data-stu-id="30a56-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="30a56-147">Sin comentarios hápticos y una percepción de profundidad perfecta, puede ser difícil saber a qué distancia está la mano de un objeto o si lo está tocándose.</span><span class="sxs-lookup"><span data-stu-id="30a56-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="30a56-148">Es importante proporcionar suficientes indicaciones visuales para comunicar el estado del objeto, en particular el estado de las manos en función de ese objeto.</span><span class="sxs-lookup"><span data-stu-id="30a56-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="30a56-149">Use comentarios visuales para comunicar los estados siguientes:</span><span class="sxs-lookup"><span data-stu-id="30a56-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="30a56-150">**Default (Observation):** estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="30a56-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="30a56-151">**Mantener** el puntero: cuando una mano está cerca de un holograma, cambie los objetos visuales para comunicar que la mano tiene como destino el holograma.</span><span class="sxs-lookup"><span data-stu-id="30a56-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="30a56-152">**Distancia y punto de** interacción: a medida que la mano se acerca a un holograma, diseña los comentarios para comunicar el punto de interacción proyectado y lo lejos que está el dedo del objeto.</span><span class="sxs-lookup"><span data-stu-id="30a56-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="30a56-153">**Contacto comienza:** cambia los objetos visuales (claro, color) para comunicar que se ha producido un toque.</span><span class="sxs-lookup"><span data-stu-id="30a56-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="30a56-154">**Se entiende:** cambia los objetos visuales (claro, color) cuando se sujete el objeto.</span><span class="sxs-lookup"><span data-stu-id="30a56-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="30a56-155">**Extremos de contacto:** cambia los objetos visuales (claro, color) cuando la función táctil ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="30a56-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="30a56-156">![Mantener el puntero (lejos)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="30a56-157">**Mantener el puntero (lejos)**</span><span class="sxs-lookup"><span data-stu-id="30a56-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="30a56-158">Resaltado en función de la proximidad de la mano.</span><span class="sxs-lookup"><span data-stu-id="30a56-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="30a56-159">![Mantener el puntero (cerca)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="30a56-160">**Mantener el puntero (cerca)**</span><span class="sxs-lookup"><span data-stu-id="30a56-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="30a56-161">Resalte los cambios de tamaño en función de la distancia a la mano.</span><span class="sxs-lookup"><span data-stu-id="30a56-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="30a56-162">![Tocar o presionar](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="30a56-163">**Tocar o presionar**</span><span class="sxs-lookup"><span data-stu-id="30a56-163">**Touch / press**</span></span><br>
        <span data-ttu-id="30a56-164">Visual más comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="30a56-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="30a56-165">![Agarran](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="30a56-166">**Agarran**</span><span class="sxs-lookup"><span data-stu-id="30a56-166">**Grasp**</span></span><br>
        <span data-ttu-id="30a56-167">Visual más comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="30a56-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="30a56-168">Un [botón en HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) es un ejemplo de cómo se visualizan los distintos estados de interacción de entrada:</span><span class="sxs-lookup"><span data-stu-id="30a56-168">A [button on HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="30a56-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="30a56-170">**Valor predeterminado**</span><span class="sxs-lookup"><span data-stu-id="30a56-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="30a56-171">![Al mantener el puntero](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="30a56-172">**Al mantener el puntero**</span><span class="sxs-lookup"><span data-stu-id="30a56-172">**Hover**</span></span><br>
        <span data-ttu-id="30a56-173">Mostrar un efecto de iluminación basado en proximidad.</span><span class="sxs-lookup"><span data-stu-id="30a56-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="30a56-174">![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="30a56-175">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="30a56-175">**Touch**</span></span><br>
        <span data-ttu-id="30a56-176">Mostrar efecto de ondulación.</span><span class="sxs-lookup"><span data-stu-id="30a56-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="30a56-177">![Presione](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="30a56-178">**Pulse**</span><span class="sxs-lookup"><span data-stu-id="30a56-178">**Press**</span></span><br>
        <span data-ttu-id="30a56-179">Mueva la placa frontal.</span><span class="sxs-lookup"><span data-stu-id="30a56-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="30a56-180">La indicación visual "anillo" en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="30a56-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="30a56-181">En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción de profundidad del usuario.</span><span class="sxs-lookup"><span data-stu-id="30a56-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="30a56-182">Un anillo cerca de su dedo se muestra verticalmente y se escala verticalmente a medida que el dedo se acerca al objeto.</span><span class="sxs-lookup"><span data-stu-id="30a56-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="30a56-183">El anillo finalmente converge en un punto cuando se alcanza el estado presionado.</span><span class="sxs-lookup"><span data-stu-id="30a56-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="30a56-184">Esta asequibilidad visual ayuda al usuario a comprender lo lejos que está del objeto.</span><span class="sxs-lookup"><span data-stu-id="30a56-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="30a56-185">*Bucle de vídeo: ejemplo de comentarios visuales basados en la proximidad a un rectángulo de selección*</span><span class="sxs-lookup"><span data-stu-id="30a56-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="30a56-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="30a56-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="30a56-187">![Comentarios visuales sobre la proximidad a mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="30a56-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="30a56-188">Indicaciones de audio</span><span class="sxs-lookup"><span data-stu-id="30a56-188">Audio cues</span></span>

<span data-ttu-id="30a56-189">En el caso de las interacciones directas con las manos, los comentarios de audio adecuados pueden mejorar considerablemente la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="30a56-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="30a56-190">Use comentarios de audio para comunicar las indicaciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="30a56-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="30a56-191">**Contacto comienza:** reproducir sonido cuando comienza la táctil</span><span class="sxs-lookup"><span data-stu-id="30a56-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="30a56-192">**Extremos de contacto:** reproducir sonido en el extremo táctil</span><span class="sxs-lookup"><span data-stu-id="30a56-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="30a56-193">**Comienza la toma:** reproducir sonido cuando se inicia la toma</span><span class="sxs-lookup"><span data-stu-id="30a56-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="30a56-194">**Extremos de toma:** reproducir sonido cuando finaliza la toma</span><span class="sxs-lookup"><span data-stu-id="30a56-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="30a56-195">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="30a56-195">Voice commanding</span></span><br>
        <span data-ttu-id="30a56-196">Para los objetos que se pueden interactuar, es importante admitir opciones de interacción alternativas.</span><span class="sxs-lookup"><span data-stu-id="30a56-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="30a56-197">De forma predeterminada, se recomienda que [los comandos de](../out-of-scope/voice-design.md) voz sean compatibles con cualquier objeto que pueda interactuar.</span><span class="sxs-lookup"><span data-stu-id="30a56-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="30a56-198">Para mejorar la detectabilidad, también puede proporcionar información sobre herramientas durante el estado del mouse.</span><span class="sxs-lookup"><span data-stu-id="30a56-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="30a56-199">*Imagen: Información sobre herramientas para el comando de voz*</span><span class="sxs-lookup"><span data-stu-id="30a56-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comandos de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="30a56-201">Recomendaciones de tamaño</span><span class="sxs-lookup"><span data-stu-id="30a56-201">Sizing recommendations</span></span>

<span data-ttu-id="30a56-202">Para asegurarse de que todos los objetos interactuables se puedan tocar fácilmente, se recomienda asegurarse de que el objeto interactuable cumple un tamaño mínimo en función de la distancia que se coloca desde el usuario.</span><span class="sxs-lookup"><span data-stu-id="30a56-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="30a56-203">El ángulo visual se suele medir en grados de arco visual. El ángulo visual se basa en la distancia entre los ojos del usuario y el objeto y permanece constante, mientras que el tamaño físico del destino puede cambiar a medida que cambia la distancia desde el usuario.</span><span class="sxs-lookup"><span data-stu-id="30a56-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="30a56-204">Para determinar el tamaño físico necesario de un objeto en función de la distancia del usuario, pruebe a usar una calculadora de ángulo visual como [esta](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="30a56-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="30a56-205">A continuación se muestran las recomendaciones para los tamaños mínimos de contenido interactuable.</span><span class="sxs-lookup"><span data-stu-id="30a56-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="30a56-206">Tamaño de destino para la interacción directa con la mano</span><span class="sxs-lookup"><span data-stu-id="30a56-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="30a56-207">Distancia</span><span class="sxs-lookup"><span data-stu-id="30a56-207">Distance</span></span> | <span data-ttu-id="30a56-208">Ángulo</span><span class="sxs-lookup"><span data-stu-id="30a56-208">Viewing angle</span></span> | <span data-ttu-id="30a56-209">Size</span><span class="sxs-lookup"><span data-stu-id="30a56-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="30a56-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="30a56-210">45 cm</span></span>  | <span data-ttu-id="30a56-211">no menor que 2°</span><span class="sxs-lookup"><span data-stu-id="30a56-211">no smaller than 2°</span></span> | <span data-ttu-id="30a56-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="30a56-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="30a56-213">![Tamaño de destino para la interacción directa con la mano](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="30a56-214">*Tamaño de destino para la interacción directa con la mano*</span><span class="sxs-lookup"><span data-stu-id="30a56-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="30a56-215">Tamaño de destino de los botones</span><span class="sxs-lookup"><span data-stu-id="30a56-215">Target size for buttons</span></span>

<span data-ttu-id="30a56-216">Al crear botones para la interacción directa, se recomienda un tamaño mínimo mayor de 3,2 x 3,2 cm para asegurarse de que hay suficiente espacio para contener un icono y, posiblemente, algún texto.</span><span class="sxs-lookup"><span data-stu-id="30a56-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="30a56-217">Distancia</span><span class="sxs-lookup"><span data-stu-id="30a56-217">Distance</span></span> | <span data-ttu-id="30a56-218">Tamaño mínimo</span><span class="sxs-lookup"><span data-stu-id="30a56-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="30a56-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="30a56-219">45 cm</span></span>  | <span data-ttu-id="30a56-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="30a56-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="30a56-221">![Tamaño de destino de los botones](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="30a56-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="30a56-222">*Tamaño de destino de los botones*</span><span class="sxs-lookup"><span data-stu-id="30a56-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="30a56-223">Tamaño objetivo para la interacción de rayos de mano o mirada</span><span class="sxs-lookup"><span data-stu-id="30a56-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="30a56-224">Distancia</span><span class="sxs-lookup"><span data-stu-id="30a56-224">Distance</span></span> | <span data-ttu-id="30a56-225">Ángulo</span><span class="sxs-lookup"><span data-stu-id="30a56-225">Viewing angle</span></span> | <span data-ttu-id="30a56-226">Size</span><span class="sxs-lookup"><span data-stu-id="30a56-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="30a56-227">2 m</span><span class="sxs-lookup"><span data-stu-id="30a56-227">2 m</span></span>  | <span data-ttu-id="30a56-228">no menor que 1°</span><span class="sxs-lookup"><span data-stu-id="30a56-228">no smaller than 1°</span></span> | <span data-ttu-id="30a56-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="30a56-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="30a56-230">![Tamaño objetivo para la interacción de rayos de mano o mirada](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="30a56-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="30a56-231">*Tamaño objetivo para la interacción de rayos de mano o mirada*</span><span class="sxs-lookup"><span data-stu-id="30a56-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="30a56-232">Objeto interactuable en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="30a56-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="30a56-233">En **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, puede usar el script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para que los objetos respondan a varios tipos de estados de interacción de entrada.</span><span class="sxs-lookup"><span data-stu-id="30a56-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="30a56-234">Admite varios tipos de temas que permiten definir estados visuales mediante el control de propiedades de objeto como color, tamaño, material y sombreador.</span><span class="sxs-lookup"><span data-stu-id="30a56-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="30a56-235">Interactuable</span><span class="sxs-lookup"><span data-stu-id="30a56-235">Interactable</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [<span data-ttu-id="30a56-236">Button</span><span class="sxs-lookup"><span data-stu-id="30a56-236">Button</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [<span data-ttu-id="30a56-237">Escena de ejemplos de interacción con la mano</span><span class="sxs-lookup"><span data-stu-id="30a56-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="30a56-238">El sombreador Estándar de MixedRealityToolkit  proporciona varias opciones, como la luz de proximidad, que le ayuda a crear indicaciones visuales y de audio.</span><span class="sxs-lookup"><span data-stu-id="30a56-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="30a56-239">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="30a56-239">MRTK Standard Shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="30a56-240">Vea también</span><span class="sxs-lookup"><span data-stu-id="30a56-240">See also</span></span>

* [<span data-ttu-id="30a56-241">Cursores</span><span class="sxs-lookup"><span data-stu-id="30a56-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="30a56-242">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="30a56-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="30a56-243">Botón</span><span class="sxs-lookup"><span data-stu-id="30a56-243">Button</span></span>](button.md)
* [<span data-ttu-id="30a56-244">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="30a56-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="30a56-245">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="30a56-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="30a56-246">Manipulación</span><span class="sxs-lookup"><span data-stu-id="30a56-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="30a56-247">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="30a56-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="30a56-248">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="30a56-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="30a56-249">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="30a56-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="30a56-250">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="30a56-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="30a56-251">Teclado</span><span class="sxs-lookup"><span data-stu-id="30a56-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="30a56-252">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="30a56-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="30a56-253">Claqueta</span><span class="sxs-lookup"><span data-stu-id="30a56-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="30a56-254">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="30a56-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="30a56-255">Sombreador</span><span class="sxs-lookup"><span data-stu-id="30a56-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="30a56-256">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="30a56-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="30a56-257">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="30a56-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="30a56-258">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="30a56-258">Surface magnetism</span></span>](surface-magnetism.md)