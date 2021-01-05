---
title: Objeto con el que se puede interactuar
description: Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, señales, interfaz de usuario, experiencia de usuario, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, audio
ms.openlocfilehash: fb7004c22602683e4edb1e38784cac5c0b7479c4
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847864"
---
# <a name="interactable-object"></a><span data-ttu-id="7d825-105">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="7d825-105">Interactable object</span></span>

![Objetos interactivos](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="7d825-107">Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="7d825-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="7d825-108">En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.</span><span class="sxs-lookup"><span data-stu-id="7d825-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="7d825-109">Cualquier elemento puede ser un **objeto interactuable** que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="7d825-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="7d825-110">Un objeto interactuable puede ser cualquier cosa, desde una taza de café de una tabla hasta un globo de midair.</span><span class="sxs-lookup"><span data-stu-id="7d825-110">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="7d825-111">Todavía hacemos uso de botones tradicionales en ciertas situaciones, como en la interfaz de usuario del cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7d825-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="7d825-112">La representación visual del botón depende del contexto.</span><span class="sxs-lookup"><span data-stu-id="7d825-112">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="7d825-113">Propiedades importantes del objeto interactuable</span><span class="sxs-lookup"><span data-stu-id="7d825-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="7d825-114">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="7d825-114">Visual cues</span></span>

<span data-ttu-id="7d825-115">Las indicaciones visuales son indicaciones organolépticas de la luz, recibidas por el ojo y procesadas por el sistema visual durante la percepción visual.</span><span class="sxs-lookup"><span data-stu-id="7d825-115">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="7d825-116">Dado que el sistema visual es dominante en muchas especies, especialmente en los seres humanos, las indicaciones visuales son una gran fuente de información sobre cómo se percibe el mundo.</span><span class="sxs-lookup"><span data-stu-id="7d825-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="7d825-117">Dado que los objetos holográficas se mezclan con el entorno real en realidad mixta, podría ser difícil comprender con qué objetos puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="7d825-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="7d825-118">En el caso de cualquier objeto interactuable de su experiencia, es importante proporcionar indicaciones visuales diferenciadas para cada estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="7d825-118">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="7d825-119">Esto ayuda al usuario a comprender qué parte de su experiencia es interactivable y hace que el usuario esté seguro mediante el uso de un método de interacción coherente.</span><span class="sxs-lookup"><span data-stu-id="7d825-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="7d825-120">Interacciones lejanas</span><span class="sxs-lookup"><span data-stu-id="7d825-120">Far interactions</span></span>

<span data-ttu-id="7d825-121">En el caso de los objetos a los que el usuario pueda interactuar con la mirada, el rayo y el rayo del controlador de movimiento, se recomienda tener una indicación visual diferente para estos tres Estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="7d825-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="7d825-122">![interactibleobject-Estados-predeterminado](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="7d825-123">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="7d825-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="7d825-124">Estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-124">Default idle state of the object.</span></span>
    <span data-ttu-id="7d825-125">El cursor no está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-125">The cursor isn't on the object.</span></span> <span data-ttu-id="7d825-126">No se detecta la mano.</span><span class="sxs-lookup"><span data-stu-id="7d825-126">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7d825-127">![interactibleobject-Estados-dirigidos](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="7d825-128">**Estado de destino (mantener el mouse)**</span><span class="sxs-lookup"><span data-stu-id="7d825-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="7d825-129">Cuando el objeto se destine con el cursor de miración, la proximidad del dedo o el puntero del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="7d825-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="7d825-130">El cursor está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-130">The cursor is on the object.</span></span> <span data-ttu-id="7d825-131">La mano se detecta y está lista.</span><span class="sxs-lookup"><span data-stu-id="7d825-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7d825-132">![interactibleobject-Estados-presionado](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="7d825-133">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="7d825-133">**Pressed state**</span></span><br>
        <span data-ttu-id="7d825-134">Cuando el objeto se presiona con un gesto de pulsación de aire, presionar el dedo o el botón seleccionar del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="7d825-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="7d825-135">El cursor está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-135">The cursor is on the object.</span></span> <span data-ttu-id="7d825-136">Se detecta una mano, se puntea en el aire.</span><span class="sxs-lookup"><span data-stu-id="7d825-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="7d825-137">Puede usar técnicas como resaltado o escalado para proporcionar indicaciones visuales para el estado de entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="7d825-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="7d825-138">En la realidad mixta, puede encontrar ejemplos de visualización de distintos Estados de entrada en el menú Inicio y con botones de barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7d825-138">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="7d825-139">Este es el aspecto de estos Estados en un **botón holográfica**:</span><span class="sxs-lookup"><span data-stu-id="7d825-139">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="7d825-140">![interactibleobject-Estados-predeterminado](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="7d825-141">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="7d825-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7d825-142">![interactibleobject-Estados-dirigidos](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="7d825-143">**Estado de destino (mantener el mouse)**</span><span class="sxs-lookup"><span data-stu-id="7d825-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7d825-144">![interactibleobject-Estados-presionado](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="7d825-145">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="7d825-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="7d825-146">Interacciones cercanas (directas)</span><span class="sxs-lookup"><span data-stu-id="7d825-146">Near interactions (direct)</span></span> 

<span data-ttu-id="7d825-147">HoloLens 2 admite la entrada de seguimiento de mano articulada, que permite interactuar con objetos.</span><span class="sxs-lookup"><span data-stu-id="7d825-147">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="7d825-148">Sin comentarios hápticos e percepción de profundidad perfecta, puede ser difícil saber hasta dónde se encuentra la mano de un objeto o si se está tocando.</span><span class="sxs-lookup"><span data-stu-id="7d825-148">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="7d825-149">Es importante proporcionar suficientes indicaciones visuales para comunicar el estado del objeto, en particular el estado de las manos basadas en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-149">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="7d825-150">Use los comentarios visuales para comunicar los siguientes Estados:</span><span class="sxs-lookup"><span data-stu-id="7d825-150">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="7d825-151">**Predeterminado (observación)**: estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="7d825-152">**Mantener el mouse**: cuando una mano está cerca de un holograma, cambie los objetos visuales para comunicar que esa mano está dirigida al holograma.</span><span class="sxs-lookup"><span data-stu-id="7d825-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="7d825-153">**Distancia y punto de interacción**: a medida que la mano se aproxima a un holograma, el diseño de comentarios para comunicar el punto de interacción previsto y la distancia desde el objeto que es el dedo</span><span class="sxs-lookup"><span data-stu-id="7d825-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="7d825-154">**Inicio de contacto**: cambie los objetos visuales (Light, color) para comunicar que se ha producido una entrada táctil</span><span class="sxs-lookup"><span data-stu-id="7d825-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="7d825-155">**Agarre**: cambiar objetos visuales (claros, de color) cuando se agarre el objeto</span><span class="sxs-lookup"><span data-stu-id="7d825-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="7d825-156">**Extremos de contacto**: cambios visuales (claros, de color) cuando la entrada táctil ha finalizado</span><span class="sxs-lookup"><span data-stu-id="7d825-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="7d825-157">![Mantener el mouse (lejano)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="7d825-158">**Mantener el mouse (lejano)**</span><span class="sxs-lookup"><span data-stu-id="7d825-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="7d825-159">Resaltado en función de la proximidad de la mano.</span><span class="sxs-lookup"><span data-stu-id="7d825-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7d825-160">![Mantener el mouse (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="7d825-161">**Mantener el mouse (Near)**</span><span class="sxs-lookup"><span data-stu-id="7d825-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="7d825-162">Resaltar cambios de tamaño en función de la distancia a la mano.</span><span class="sxs-lookup"><span data-stu-id="7d825-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="7d825-163">![Tocar y presionar](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="7d825-164">**Tocar y presionar**</span><span class="sxs-lookup"><span data-stu-id="7d825-164">**Touch / press**</span></span><br>
        <span data-ttu-id="7d825-165">Comentarios de Visual Plus audio.</span><span class="sxs-lookup"><span data-stu-id="7d825-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7d825-166">![Visión](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="7d825-167">**Visión**</span><span class="sxs-lookup"><span data-stu-id="7d825-167">**Grasp**</span></span><br>
        <span data-ttu-id="7d825-168">Comentarios de Visual Plus audio.</span><span class="sxs-lookup"><span data-stu-id="7d825-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="7d825-169">Un [botón de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) es un ejemplo de cómo se visualizan los distintos Estados de interacción de entrada:</span><span class="sxs-lookup"><span data-stu-id="7d825-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7d825-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="7d825-171">**Valor predeterminado**</span><span class="sxs-lookup"><span data-stu-id="7d825-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7d825-172">![Al mantener el puntero](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="7d825-173">**Al mantener el puntero**</span><span class="sxs-lookup"><span data-stu-id="7d825-173">**Hover**</span></span><br>
        <span data-ttu-id="7d825-174">Revela un efecto de iluminación basado en proximidad.</span><span class="sxs-lookup"><span data-stu-id="7d825-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="7d825-175">![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="7d825-176">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="7d825-176">**Touch**</span></span><br>
        <span data-ttu-id="7d825-177">Mostrar efecto de rizo.</span><span class="sxs-lookup"><span data-stu-id="7d825-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7d825-178">![Presione](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="7d825-179">**Presione**</span><span class="sxs-lookup"><span data-stu-id="7d825-179">**Press**</span></span><br>
        <span data-ttu-id="7d825-180">Mueva la placa frontal.</span><span class="sxs-lookup"><span data-stu-id="7d825-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="7d825-181">La indicación visual "Ring" en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d825-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="7d825-182">En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción del usuario de la profundidad.</span><span class="sxs-lookup"><span data-stu-id="7d825-182">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="7d825-183">Se muestra un anillo cerca de su dedo y se reduce verticalmente a medida que la mano se acerca al objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="7d825-184">El anillo finalmente converge en un punto cuando se alcanza el estado presionado.</span><span class="sxs-lookup"><span data-stu-id="7d825-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="7d825-185">Esta prestación visual ayuda al usuario a comprender hasta qué punto proceden del objeto.</span><span class="sxs-lookup"><span data-stu-id="7d825-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="7d825-186">*Bucle de vídeo: ejemplo de comentarios visuales basados en proximidad a un cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="7d825-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="7d825-187">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="7d825-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="7d825-188">![Comentarios visuales en proximidad](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="7d825-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="7d825-189">Señales de audio</span><span class="sxs-lookup"><span data-stu-id="7d825-189">Audio cues</span></span>

<span data-ttu-id="7d825-190">En el caso de las interacciones directas, los comentarios de audio adecuados pueden mejorar drásticamente la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="7d825-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="7d825-191">Use comentarios de audio para comunicar las siguientes indicaciones:</span><span class="sxs-lookup"><span data-stu-id="7d825-191">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="7d825-192">**Inicio de contacto**: reproducir un sonido cuando se inicie Touch</span><span class="sxs-lookup"><span data-stu-id="7d825-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="7d825-193">**Contactos** finales: reproducir sonido en el extremo táctil</span><span class="sxs-lookup"><span data-stu-id="7d825-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="7d825-194">**Inicio** de la toma: reproducir sonido cuando se inicie la captura</span><span class="sxs-lookup"><span data-stu-id="7d825-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="7d825-195">Acabado de **agarre**: reproducir un sonido al finalizar la toma</span><span class="sxs-lookup"><span data-stu-id="7d825-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="7d825-196">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="7d825-196">Voice commanding</span></span><br>
        <span data-ttu-id="7d825-197">En el caso de los objetos interactuables, es importante admitir opciones de interacción alternativas.</span><span class="sxs-lookup"><span data-stu-id="7d825-197">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="7d825-198">De forma predeterminada, se recomienda que se admitan los [comandos de voz](../out-of-scope/voice-design.md) para cualquier objeto que sea interactuable.</span><span class="sxs-lookup"><span data-stu-id="7d825-198">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="7d825-199">Para mejorar la capacidad de detección, también puede proporcionar una información sobre herramientas durante el estado de mantener el mouse.</span><span class="sxs-lookup"><span data-stu-id="7d825-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="7d825-200">*Image: información sobre herramientas para el comando Voice*</span><span class="sxs-lookup"><span data-stu-id="7d825-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comandos de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="7d825-202">Recomendaciones de tamaño</span><span class="sxs-lookup"><span data-stu-id="7d825-202">Sizing recommendations</span></span> 

<span data-ttu-id="7d825-203">Para asegurarse de que todos los objetos interactivos se pueden tocar fácilmente, se recomienda asegurarse de que el interactuable cumple un tamaño mínimo en función de la distancia que se coloca del usuario.</span><span class="sxs-lookup"><span data-stu-id="7d825-203">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="7d825-204">El ángulo visual se mide a menudo en grados de arco visual. El ángulo visual se basa en la distancia entre los ojos del usuario y el objeto y permanece constante, mientras que el tamaño físico del destino puede cambiar a medida que cambia la distancia del usuario.</span><span class="sxs-lookup"><span data-stu-id="7d825-204">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="7d825-205">Para determinar el tamaño físico necesario de un objeto en función de la distancia del usuario, pruebe a usar una calculadora de ángulo visual como [esta](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="7d825-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="7d825-206">A continuación se muestran las recomendaciones para tamaños mínimos de contenido interactuable.</span><span class="sxs-lookup"><span data-stu-id="7d825-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="7d825-207">Tamaño de destino para la interacción directa</span><span class="sxs-lookup"><span data-stu-id="7d825-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="7d825-208">Distancia</span><span class="sxs-lookup"><span data-stu-id="7d825-208">Distance</span></span> | <span data-ttu-id="7d825-209">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="7d825-209">Viewing angle</span></span> | <span data-ttu-id="7d825-210">Size</span><span class="sxs-lookup"><span data-stu-id="7d825-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="7d825-211">45 cm</span><span class="sxs-lookup"><span data-stu-id="7d825-211">45 cm</span></span>  | <span data-ttu-id="7d825-212">no menor que 2 °</span><span class="sxs-lookup"><span data-stu-id="7d825-212">no smaller than 2°</span></span> | <span data-ttu-id="7d825-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="7d825-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="7d825-214">![Tamaño de destino para la interacción directa](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="7d825-215">*Tamaño de destino para la interacción directa*</span><span class="sxs-lookup"><span data-stu-id="7d825-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="7d825-216">Tamaño de destino de los botones</span><span class="sxs-lookup"><span data-stu-id="7d825-216">Target size for buttons</span></span>

<span data-ttu-id="7d825-217">Al crear botones para la interacción directa, se recomienda un tamaño mínimo mayor de 3,2 x 3,2 cm para asegurarse de que hay espacio suficiente para contener un icono y un posible texto.</span><span class="sxs-lookup"><span data-stu-id="7d825-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="7d825-218">Distancia</span><span class="sxs-lookup"><span data-stu-id="7d825-218">Distance</span></span> | <span data-ttu-id="7d825-219">Tamaño mínimo</span><span class="sxs-lookup"><span data-stu-id="7d825-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="7d825-220">45 cm</span><span class="sxs-lookup"><span data-stu-id="7d825-220">45 cm</span></span>  | <span data-ttu-id="7d825-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="7d825-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="7d825-222">![Tamaño de destino de los botones](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="7d825-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="7d825-223">*Tamaño de destino de los botones*</span><span class="sxs-lookup"><span data-stu-id="7d825-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="7d825-224">Tamaño de destino para la interacción de mano o de rayo</span><span class="sxs-lookup"><span data-stu-id="7d825-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="7d825-225">Distancia</span><span class="sxs-lookup"><span data-stu-id="7d825-225">Distance</span></span> | <span data-ttu-id="7d825-226">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="7d825-226">Viewing angle</span></span> | <span data-ttu-id="7d825-227">Size</span><span class="sxs-lookup"><span data-stu-id="7d825-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="7d825-228">2 m</span><span class="sxs-lookup"><span data-stu-id="7d825-228">2 m</span></span>  | <span data-ttu-id="7d825-229">no menor que 1 °</span><span class="sxs-lookup"><span data-stu-id="7d825-229">no smaller than 1°</span></span> | <span data-ttu-id="7d825-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="7d825-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="7d825-231">![Tamaño de destino para la interacción de mano o de rayo](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d825-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="7d825-232">*Tamaño de destino para la interacción de mano o de rayo*</span><span class="sxs-lookup"><span data-stu-id="7d825-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="7d825-233">Objeto interactuable en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="7d825-233">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="7d825-234">En **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, puede usar el script [**interactúable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para que los objetos respondan a diversos tipos de Estados de interacción de entrada.</span><span class="sxs-lookup"><span data-stu-id="7d825-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="7d825-235">Admite varios tipos de temas que permiten definir Estados visuales mediante el control de las propiedades del objeto como el color, el tamaño, el material y el sombreador.</span><span class="sxs-lookup"><span data-stu-id="7d825-235">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="7d825-236">Interactuable</span><span class="sxs-lookup"><span data-stu-id="7d825-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="7d825-237">Button</span><span class="sxs-lookup"><span data-stu-id="7d825-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="7d825-238">Escena de ejemplos de interacción de mano</span><span class="sxs-lookup"><span data-stu-id="7d825-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="7d825-239">El sombreador estándar de MixedRealityToolkit proporciona varias opciones, como la **luz de proximidad** , que le ayuda a crear indicaciones visuales y de audio.</span><span class="sxs-lookup"><span data-stu-id="7d825-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="7d825-240">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="7d825-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="7d825-241">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7d825-241">See also</span></span>

* [<span data-ttu-id="7d825-242">Cursores</span><span class="sxs-lookup"><span data-stu-id="7d825-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="7d825-243">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="7d825-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="7d825-244">Botón</span><span class="sxs-lookup"><span data-stu-id="7d825-244">Button</span></span>](button.md)
* [<span data-ttu-id="7d825-245">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="7d825-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="7d825-246">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="7d825-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="7d825-247">Manipulación</span><span class="sxs-lookup"><span data-stu-id="7d825-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7d825-248">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="7d825-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="7d825-249">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="7d825-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="7d825-250">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="7d825-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="7d825-251">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="7d825-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="7d825-252">Teclado</span><span class="sxs-lookup"><span data-stu-id="7d825-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="7d825-253">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="7d825-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="7d825-254">Claqueta</span><span class="sxs-lookup"><span data-stu-id="7d825-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="7d825-255">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="7d825-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="7d825-256">Sombreador</span><span class="sxs-lookup"><span data-stu-id="7d825-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="7d825-257">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="7d825-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="7d825-258">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="7d825-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="7d825-259">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="7d825-259">Surface magnetism</span></span>](surface-magnetism.md)
