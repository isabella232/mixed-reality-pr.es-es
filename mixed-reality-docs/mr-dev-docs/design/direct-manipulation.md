---
title: Manipulación directa con las manos
description: Obtenga información sobre la manipulación directa, un modelo de entrada en que los usuarios tocan los hologramas directamente con sus manos.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hands near, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset, MRTK, Mixed Reality Toolkit, button, colliders, bounding box, 2D, instinctual gestures
ms.openlocfilehash: 8316452b8308e159612a81d097c352cf1d935362
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759327"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="53b5d-104">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="53b5d-104">Direct manipulation with hands</span></span>

![Botón](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="53b5d-106">La manipulación directa es un modelo de entrada de datos que implica tocar hologramas directamente con las manos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="53b5d-107">La idea que impulsa este concepto es que los objetos se comporten exactamente igual que lo hacen en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="53b5d-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="53b5d-108">Para activar los botones no hay más que presionarlos, para elegir los objetos no hay más que agarrarlos y el contenido 2D se comporta como una pantalla táctil virtual.</span><span class="sxs-lookup"><span data-stu-id="53b5d-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="53b5d-109">La manipulación directa emplea prestaciones, lo que significa que es fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="53b5d-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="53b5d-110">No hay que enseñar ningún gesto simbólico a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="53b5d-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="53b5d-111">Todas las interacciones se crean en torno a un elemento visual que se puede tocar o agarrar.</span><span class="sxs-lookup"><span data-stu-id="53b5d-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="53b5d-112">Se considera un modelo de entrada "cercano" porque se usa con preferencia para interactuar con contenido que está al alcance de los brazos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="53b5d-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="53b5d-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="53b5d-114"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="53b5d-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="53b5d-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="53b5d-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="53b5d-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="53b5d-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="53b5d-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="53b5d-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="53b5d-118">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="53b5d-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="53b5d-119">❌ No se admite</span><span class="sxs-lookup"><span data-stu-id="53b5d-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="53b5d-120">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="53b5d-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="53b5d-121">➕ Se admite.</span><span class="sxs-lookup"><span data-stu-id="53b5d-121">➕ Supported.</span></span>  <span data-ttu-id="53b5d-122">En el caso de la interfaz de usuario, se recomienda <a href="point-and-commit.md">apuntar y confirmar con las manos</a> en su lugar.</span><span class="sxs-lookup"><span data-stu-id="53b5d-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="53b5d-123">La manipulación directa es un modelo de entrada principal de HoloLens 2, que usa el nuevo sistema articulado de seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="53b5d-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="53b5d-124">El modelo de entrada también está disponible en los cascos envolventes mediante el uso de controladores de movimiento, pero no se recomienda como medio principal de interacción fuera de la manipulación de objetos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="53b5d-125">La manipulación directa no está disponible en HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="53b5d-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="53b5d-126">Dedo de colisión</span><span class="sxs-lookup"><span data-stu-id="53b5d-126">Collidable fingertip</span></span>

<span data-ttu-id="53b5d-127">En HoloLens 2, se reconocen las manos del usuario y se interpretan como modelos óseos de las manos derecha e izquierda.</span><span class="sxs-lookup"><span data-stu-id="53b5d-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="53b5d-128">Para implementar la idea de tocar los hologramas directamente con las manos, se tendrían que acoplar cinco colisionadores a los cinco dedos del modelo óseo de cada mano.</span><span class="sxs-lookup"><span data-stu-id="53b5d-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="53b5d-129">Aun así, dada la falta de información procedente del tacto, diez dedos de colisión pueden provocar colisiones inesperadas e impredecibles con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="53b5d-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="53b5d-130">Sugerimos colocar solo un colisionador en cada dedo índice.</span><span class="sxs-lookup"><span data-stu-id="53b5d-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="53b5d-131">Los dedos índice de colisión se pueden seguir usando como puntos táctiles activos para diversos gestos táctiles que implican otros dedos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="53b5d-132">Los gestos táctiles incluyen presionar con un dedo, pulsar con un dedo, presionar con dos dedos y presionar con cinco dedos, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="53b5d-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="53b5d-133">![dedo de colisión](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="53b5d-134">**Dedo de colisión**</span><span class="sxs-lookup"><span data-stu-id="53b5d-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-135">![Presión de un dedo](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="53b5d-136">**Presión de un dedo**</span><span class="sxs-lookup"><span data-stu-id="53b5d-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-137">![Pulsación de un dedo](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="53b5d-138">**Pulsación de un dedo**</span><span class="sxs-lookup"><span data-stu-id="53b5d-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-139">![Presión de cinco dedos](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="53b5d-140">**Presión de cinco dedos**</span><span class="sxs-lookup"><span data-stu-id="53b5d-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="53b5d-141">Colisionador esférico</span><span class="sxs-lookup"><span data-stu-id="53b5d-141">Sphere collider</span></span>

<span data-ttu-id="53b5d-142">En lugar de usar una forma genérica aleatoria, se recomienda usar un colisionador esférico.</span><span class="sxs-lookup"><span data-stu-id="53b5d-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="53b5d-143">A continuación, puedes representarlo visualmente para proporcionar mejores indicaciones a objetivos cercanos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="53b5d-144">Para aumentar la precisión del toque, el diámetro de la esfera debe coincidir con el grosor del dedo índice.</span><span class="sxs-lookup"><span data-stu-id="53b5d-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="53b5d-145">Será más fácil recuperar la variable de grosor del dedo con una llamada a la API de mano.</span><span class="sxs-lookup"><span data-stu-id="53b5d-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="53b5d-146">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="53b5d-146">Fingertip cursor</span></span>

<span data-ttu-id="53b5d-147">Además de representar una esfera de colisión en el dedo índice, hemos creado un cursor de dedo avanzado para llegar mejor a objetivos cercanos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="53b5d-148">Es un cursor en forma de anillo acoplado al dedo índice.</span><span class="sxs-lookup"><span data-stu-id="53b5d-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="53b5d-149">En función de la proximidad, reacciona dinámicamente a un destino en lo que respecta a la orientación y el tamaño, como se detalla a continuación:</span><span class="sxs-lookup"><span data-stu-id="53b5d-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="53b5d-150">Cuando un dedo índice se mueve hacia un holograma, el cursor está siempre paralelo a la superficie del holograma y su tamaño se reduce gradualmente.</span><span class="sxs-lookup"><span data-stu-id="53b5d-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="53b5d-151">En cuanto el dedo toca la superficie, el tamaño del cursor se reduce hasta convertirse en un punto y emite un evento de toque.</span><span class="sxs-lookup"><span data-stu-id="53b5d-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="53b5d-152">Con la información interactiva, los usuarios pueden realizar tareas en objetivos cercanos de forma muy precisa, como desencadenar un hipervínculo o presionar un botón, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="53b5d-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="53b5d-153">![Cursor de dedo lejano](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="53b5d-154">**Cursor de dedo lejano**</span><span class="sxs-lookup"><span data-stu-id="53b5d-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-155">![Cursor de dedo cercano](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="53b5d-156">**Cursor de dedo cercano**</span><span class="sxs-lookup"><span data-stu-id="53b5d-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-157">![Cursor de dedo de contacto](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="53b5d-158">**Cursor de dedo de contacto**</span><span class="sxs-lookup"><span data-stu-id="53b5d-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="53b5d-159">Rectángulo de selección con sombreador de proximidad</span><span class="sxs-lookup"><span data-stu-id="53b5d-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="53b5d-160">El propio holograma también requiere la capacidad de proporcionar información visual y sonora para compensar la falta de información táctil.</span><span class="sxs-lookup"><span data-stu-id="53b5d-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="53b5d-161">Con ese fin generamos el concepto de rectángulo de selección con sombreador de proximidad.</span><span class="sxs-lookup"><span data-stu-id="53b5d-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="53b5d-162">Un rectángulo de selección es un área volumétrica mínima que rodea a un objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="53b5d-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="53b5d-163">El rectángulo de selección tiene un mecanismo de representación interactivo denominado sombreador de proximidad.</span><span class="sxs-lookup"><span data-stu-id="53b5d-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="53b5d-164">Así es como se comporta el sombreador de proximidad:</span><span class="sxs-lookup"><span data-stu-id="53b5d-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="53b5d-165">![Mantener el puntero (lejos) con comentarios visuales](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="53b5d-166">**Mantener el puntero (lejos)**</span><span class="sxs-lookup"><span data-stu-id="53b5d-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="53b5d-167">Cuando el dedo índice está dentro del alcance, se proyecta un foco con forma de dedo en la superficie del rectángulo de selección.</span><span class="sxs-lookup"><span data-stu-id="53b5d-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-168">![Mantener el puntero (cerca) con comentarios visuales](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="53b5d-169">**Mantener el puntero (cerca)**</span><span class="sxs-lookup"><span data-stu-id="53b5d-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="53b5d-170">Cuando el dedo se acerca a la superficie, el foco se reduce.</span><span class="sxs-lookup"><span data-stu-id="53b5d-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-171">![Inicio de contacto](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="53b5d-172">**Inicio de contacto**</span><span class="sxs-lookup"><span data-stu-id="53b5d-172">**Contact begins**</span></span><br>
       <span data-ttu-id="53b5d-173">En cuanto el dedo toca la superficie, todo el rectángulo de selección cambia de color o genera efectos visuales que reflejan dicho estado.</span><span class="sxs-lookup"><span data-stu-id="53b5d-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-174">![Fin de contacto](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="53b5d-175">**Fin de contacto**</span><span class="sxs-lookup"><span data-stu-id="53b5d-175">**Contact ends**</span></span><br>
       <span data-ttu-id="53b5d-176">También se puede activar un efecto de sonido que mejore la información visual del toque.</span><span class="sxs-lookup"><span data-stu-id="53b5d-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="53b5d-177">Botón presionable</span><span class="sxs-lookup"><span data-stu-id="53b5d-177">Pressable button</span></span>

<span data-ttu-id="53b5d-178">Con el dedo de colisión, los usuarios ya están listos para interactuar con el componente fundamental de la interfaz de usuario holográfica, como un botón presionable.</span><span class="sxs-lookup"><span data-stu-id="53b5d-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="53b5d-179">Un botón presionable es un botón holográfico adaptado a una presión directa del dedo.</span><span class="sxs-lookup"><span data-stu-id="53b5d-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="53b5d-180">Una vez más, debido a la falta de información táctil, el botón presionable cuenta con un par de mecanismos para abordar los problemas relacionados con la información táctil.</span><span class="sxs-lookup"><span data-stu-id="53b5d-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="53b5d-181">El primer mecanismo es un rectángulo de selección con sombreador de proximidad, del que se ha proporcionado la información pertinente en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="53b5d-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="53b5d-182">Permite a los usuarios mejorar la sensación de proximidad a la hora de acercarse y entrar en contacto con un botón.</span><span class="sxs-lookup"><span data-stu-id="53b5d-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="53b5d-183">El segundo mecanismo es la depresión.</span><span class="sxs-lookup"><span data-stu-id="53b5d-183">The second mechanism is depression.</span></span> <span data-ttu-id="53b5d-184">La depresión crea una sensación de presión al tocar un botón con un dedo.</span><span class="sxs-lookup"><span data-stu-id="53b5d-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="53b5d-185">El mecanismo garantiza que el botón se mueve estrechamente junto con el dedo por el eje de profundidad.</span><span class="sxs-lookup"><span data-stu-id="53b5d-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="53b5d-186">El botón se puede desencadenar cuando se alcanza una profundidad elegida (al presionar) o se sale de dicha profundidad (al soltar) después de atravesarlo.</span><span class="sxs-lookup"><span data-stu-id="53b5d-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="53b5d-187">El efecto de sonido se debe agregar para mejorar la información cuando se desencadena el botón.</span><span class="sxs-lookup"><span data-stu-id="53b5d-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="53b5d-188">![botón presionable lejano](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="53b5d-189">**El dedo está lejos**</span><span class="sxs-lookup"><span data-stu-id="53b5d-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-190">![botón presionable cercano](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="53b5d-191">**El dedo se acerca**</span><span class="sxs-lookup"><span data-stu-id="53b5d-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-192">![empieza el contacto con el botón presionable](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="53b5d-193">**Inicio de contacto**</span><span class="sxs-lookup"><span data-stu-id="53b5d-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-194">![presión del botón presionable](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="53b5d-195">**Presión**</span><span class="sxs-lookup"><span data-stu-id="53b5d-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="53b5d-196">Interacción con una tableta táctil 2D</span><span class="sxs-lookup"><span data-stu-id="53b5d-196">2D slate interaction</span></span>

<span data-ttu-id="53b5d-197">Una [tableta táctil](slate.md) 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web.</span><span class="sxs-lookup"><span data-stu-id="53b5d-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="53b5d-198">El concepto de diseño para interactuar con una tableta táctil 2D mediante la manipulación directa es el mismo que al interactuar con una pantalla táctil física.</span><span class="sxs-lookup"><span data-stu-id="53b5d-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="53b5d-199">Para interactuar con el contacto de la tableta táctil</span><span class="sxs-lookup"><span data-stu-id="53b5d-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="53b5d-200">![Tocar](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="53b5d-201">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="53b5d-201">**Touch**</span></span><br>
       <span data-ttu-id="53b5d-202">Utiliza el dedo índice para presionar un botón o un hipervínculo.</span><span class="sxs-lookup"><span data-stu-id="53b5d-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-203">![Desplazar](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="53b5d-204">**Desplazar**</span><span class="sxs-lookup"><span data-stu-id="53b5d-204">**Scroll**</span></span><br>
        <span data-ttu-id="53b5d-205">Utiliza el dedo índice para desplazar el contenido de la tableta táctil hacia arriba y abajo.</span><span class="sxs-lookup"><span data-stu-id="53b5d-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="53b5d-207">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="53b5d-207">**Zoom**</span></span><br>
       <span data-ttu-id="53b5d-208">Los dos dedos índices del usuario se utilizan para acercar y alejar el contenido de la tableta táctil, en función del movimiento relativo de los dedos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="53b5d-209">Para manipular la propia tableta táctil 2D</span><span class="sxs-lookup"><span data-stu-id="53b5d-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="53b5d-210">![Gráfico en el que se muestra la característica de agarrar y arrastrar](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="53b5d-211">**Mover**</span><span class="sxs-lookup"><span data-stu-id="53b5d-211">**Move**</span></span><br>
       <span data-ttu-id="53b5d-212">Mueve las manos a las esquinas y bordes para mostrar las prestaciones de manipulación más cercanas.</span><span class="sxs-lookup"><span data-stu-id="53b5d-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="53b5d-213">Agarra la barra holográfica de la parte superior de la tableta táctil 2D para mover toda la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="53b5d-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-214">![Gráfico en el que se muestra la característica de escalar](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="53b5d-215">**Escalar**</span><span class="sxs-lookup"><span data-stu-id="53b5d-215">**Scale**</span></span><br>
        <span data-ttu-id="53b5d-216">Agarre las prestaciones de manipulación y realice un escalado uniforme mediante las prestaciones de esquina.</span><span class="sxs-lookup"><span data-stu-id="53b5d-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-217">![Redistribuir](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="53b5d-218">**Redistribuir**</span><span class="sxs-lookup"><span data-stu-id="53b5d-218">**Reflow**</span></span><br>
       <span data-ttu-id="53b5d-219">Agarre las prestaciones de manipulación y realice la redistribución a través de las prestaciones de borde.</span><span class="sxs-lookup"><span data-stu-id="53b5d-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="53b5d-220">Manipulación de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="53b5d-220">3D object manipulation</span></span>

<span data-ttu-id="53b5d-221">HoloLens 2 permite a los usuarios habilitar sus manos para dirigir y manipular objetos holográficos 3D mediante la aplicación de un rectángulo de selección a cada objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="53b5d-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="53b5d-222">El rectángulo de selección proporciona una mejor percepción de la profundidad gracias a su sombreador de proximidad.</span><span class="sxs-lookup"><span data-stu-id="53b5d-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="53b5d-223">Con el rectángulo de selección, hay dos enfoques de diseño para la manipulación de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="53b5d-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="53b5d-224">Manipulación con prestaciones</span><span class="sxs-lookup"><span data-stu-id="53b5d-224">Affordance-based manipulation</span></span>

<span data-ttu-id="53b5d-225">La manipulación con prestaciones te permite manipular el objeto 3D a través de un rectángulo de selección por las prestaciones de manipulación que hay a su alrededor.</span><span class="sxs-lookup"><span data-stu-id="53b5d-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="53b5d-226">![Gráfico en el que se muestra un rectángulo de selección de objetos y la característica de movimiento](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="53b5d-227">**Mover**</span><span class="sxs-lookup"><span data-stu-id="53b5d-227">**Move**</span></span><br>
       <span data-ttu-id="53b5d-228">En cuanto la mano de un usuario esté cerca de un objeto 3D, se mostrarán el rectángulo de selección y la prestación más cercana.</span><span class="sxs-lookup"><span data-stu-id="53b5d-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="53b5d-229">Los usuarios pueden agarrar el rectángulo de selección para mover todo el objeto.</span><span class="sxs-lookup"><span data-stu-id="53b5d-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-230">![Gráfico en el que se muestra al usuario agarrando el borde de un objeto para girar](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="53b5d-231">**Girar**</span><span class="sxs-lookup"><span data-stu-id="53b5d-231">**Rotate**</span></span><br>
        <span data-ttu-id="53b5d-232">Los usuarios pueden agarrar las prestaciones de borde para girar.</span><span class="sxs-lookup"><span data-stu-id="53b5d-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-233">![Gráfico en el que se muestra el usuario agarrando la esquina de un objeto para escalar](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="53b5d-234">**Escalar**</span><span class="sxs-lookup"><span data-stu-id="53b5d-234">**Scale**</span></span><br>
       <span data-ttu-id="53b5d-235">Los usuarios pueden agarrar las prestaciones de esquina para escalar de forma uniforme.</span><span class="sxs-lookup"><span data-stu-id="53b5d-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="53b5d-236">Manipulación sin prestaciones</span><span class="sxs-lookup"><span data-stu-id="53b5d-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="53b5d-237">La manipulación sin prestaciones no acopla ninguna prestación al rectángulo de selección.</span><span class="sxs-lookup"><span data-stu-id="53b5d-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="53b5d-238">Los usuarios solo pueden mostrar el rectángulo de selección e interactuar directamente con él.</span><span class="sxs-lookup"><span data-stu-id="53b5d-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="53b5d-239">Si el rectángulo de selección se agarra con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano.</span><span class="sxs-lookup"><span data-stu-id="53b5d-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="53b5d-240">Cuando el objeto se agarra con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="53b5d-241">La manipulación específica requiere precisión.</span><span class="sxs-lookup"><span data-stu-id="53b5d-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="53b5d-242">Se recomienda usar la **manipulación con prestaciones**, ya que proporciona un alto nivel de granularidad.</span><span class="sxs-lookup"><span data-stu-id="53b5d-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="53b5d-243">Para la manipulación flexible, se recomienda usar la **manipulación sin prestaciones**, ya que permite experiencias instantáneas y divertidas.</span><span class="sxs-lookup"><span data-stu-id="53b5d-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="53b5d-244">Gestos instintivos</span><span class="sxs-lookup"><span data-stu-id="53b5d-244">Instinctual gestures</span></span>

<span data-ttu-id="53b5d-245">Con HoloLens (1.ª generación), enseñamos a los usuarios un par de gestos predefinidos, como eclosionar y pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="53b5d-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="53b5d-246">En el caso de HoloLens 2, no pedimos a los usuarios que memoricen gestos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="53b5d-247">Todos los gestos que los usuarios necesitan (cuando deben interactuar con hologramas y contenido) son instintivos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="53b5d-248">Para lograr gestos instintivos ayuda a los usuarios a realizar los gestos mediante el diseño de prestaciones de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="53b5d-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="53b5d-249">Por ejemplo, si se anima al usuario a arrastrar un objeto o un punto de control acercando dos dedos, el objeto o el punto de control deben ser pequeños.</span><span class="sxs-lookup"><span data-stu-id="53b5d-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="53b5d-250">Si queremos que realice el agarre con cinco dedos, el objeto o el punto de control deberían ser relativamente grandes.</span><span class="sxs-lookup"><span data-stu-id="53b5d-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="53b5d-251">Al igual que los botones, un botón pequeño limitaría a los usuarios a presionarlo con un solo dedo.</span><span class="sxs-lookup"><span data-stu-id="53b5d-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="53b5d-252">Un botón grande instaría a los usuarios a presionarlo con las palmas de las manos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="53b5d-253">![Gráfico en el que se muestra al usuario agarrando un objeto pequeño para moverlo](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="53b5d-254">**Objeto pequeño**</span><span class="sxs-lookup"><span data-stu-id="53b5d-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-255">![Gráfico en el que se muestra al usuario agarrando un objeto mediano para moverlo](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="53b5d-256">**Objeto mediano**</span><span class="sxs-lookup"><span data-stu-id="53b5d-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="53b5d-257">![Gráfico en el que se muestra al usuario agarrando un objeto grande para moverlo](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="53b5d-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="53b5d-258">**Objeto grande**</span><span class="sxs-lookup"><span data-stu-id="53b5d-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="53b5d-259">Diseño simétrico entre las manos y 6 controladores DoF</span><span class="sxs-lookup"><span data-stu-id="53b5d-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="53b5d-260">Es posible que hayas observado que hay paralelos de interacción que podemos dibujar en AR y controladores de movimiento en VR.</span><span class="sxs-lookup"><span data-stu-id="53b5d-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="53b5d-261">Las dos entradas pueden usarse para desencadenar manipulaciones directas en sus respectivos entornos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="53b5d-262">En HoloLens 2, la realización de las operaciones de agarrar y arrastrar con las manos a corta distancia funciona de forma muy parecida a como lo hace el botón de agarrar en los controladores de movimiento de WMR.</span><span class="sxs-lookup"><span data-stu-id="53b5d-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="53b5d-263">Esto proporciona a los usuarios familiaridad en la interacción entre las dos plataformas, lo que puede resultar útil si alguna vez decide portar la aplicación entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="53b5d-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="53b5d-264">Optimización con el seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="53b5d-264">Optimize with eye tracking</span></span>

<span data-ttu-id="53b5d-265">La manipulación directa puede parecer mágica si funciona según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="53b5d-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="53b5d-266">No obstante, también puede resultar frustrante si no se puede mover la mano a ningún lugar sin desencadenar involuntariamente un holograma.</span><span class="sxs-lookup"><span data-stu-id="53b5d-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="53b5d-267">El seguimiento de los ojos puede ayudar a identificar mejor la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="53b5d-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="53b5d-268">**Cuándo**: se reduce accidentalmente, lo que desencadena una respuesta de manipulación.</span><span class="sxs-lookup"><span data-stu-id="53b5d-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="53b5d-269">El seguimiento de los ojos permite saber mejor lo que hace un usuario en cada momento.</span><span class="sxs-lookup"><span data-stu-id="53b5d-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="53b5d-270">Por ejemplo, imagine que está leyendo un texto (con instrucciones) de una holografía cuando se dispone a agarrar su herramienta del mundo real.</span><span class="sxs-lookup"><span data-stu-id="53b5d-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="53b5d-271">Al hacerlo, mueve la mano accidentalmente por unos botones holográficos interactivos que no se habías percatado de que estaban ahí.</span><span class="sxs-lookup"><span data-stu-id="53b5d-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="53b5d-272">Por ejemplo, pueden estar fuera del campo de visión del usuario.</span><span class="sxs-lookup"><span data-stu-id="53b5d-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="53b5d-273">Si el usuario lleva un tiempo sin mirar un holograma, pero se ha detectado un evento de tocar o agarrar para él, es probable que la interacción sea involuntaria.</span><span class="sxs-lookup"><span data-stu-id="53b5d-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="53b5d-274">**Cuál**:  además de solucionar activaciones positivas falsas, otro ejemplo incluye una mejor identificación de qué hologramas agarrar o usar, ya que es posible que el punto de intersección preciso no esté claro desde tu perspectiva, sobre todo si hay varios hologramas colocados unos cerca de otros.</span><span class="sxs-lookup"><span data-stu-id="53b5d-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="53b5d-275">Aunque en HoloLens 2 el seguimiento de los ojos tiene limitaciones en función de la precisión con la que puede determinar la mirada con los ojos, puede resultar útil para las interacciones cercanas debido a la disparidad de profundidad al interactuar con la entrada a mano.</span><span class="sxs-lookup"><span data-stu-id="53b5d-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="53b5d-276">Esto significa que a veces es difícil determinar si la mano está detrás o delante de un holograma, por ejemplo, para agarrar con precisión un widget de manipulación.</span><span class="sxs-lookup"><span data-stu-id="53b5d-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="53b5d-277">**A dónde**: usa información acerca de lo que mira un usuario con gestos que se realizan rápidamente.</span><span class="sxs-lookup"><span data-stu-id="53b5d-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="53b5d-278">Agarra un holograma y tíralo hacia su destino previsto.</span><span class="sxs-lookup"><span data-stu-id="53b5d-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="53b5d-279">Aunque es posible que a veces esto funcione, la realización rápida de gestos con la mano puede dar lugar a destinos muy imprecisos.</span><span class="sxs-lookup"><span data-stu-id="53b5d-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="53b5d-280">Sin embargo, el seguimiento de los ojos podría mejorar la precisión del gesto.</span><span class="sxs-lookup"><span data-stu-id="53b5d-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="53b5d-281">Manipulación en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="53b5d-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="53b5d-282">Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede conseguir un comportamiento de manipulación común con el script **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="53b5d-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="53b5d-283">Con ManipulationHandler, puede agarrar y mover objetos directamente con las manos o con el haz de mano.</span><span class="sxs-lookup"><span data-stu-id="53b5d-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="53b5d-284">También admite la manipulación con dos manos para escalar y girar un objeto.</span><span class="sxs-lookup"><span data-stu-id="53b5d-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="53b5d-285">MRTK: manipulación</span><span class="sxs-lookup"><span data-stu-id="53b5d-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-manipulator.md)

---

## <a name="see-also"></a><span data-ttu-id="53b5d-286">Consulta también</span><span class="sxs-lookup"><span data-stu-id="53b5d-286">See also</span></span>

* [<span data-ttu-id="53b5d-287">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="53b5d-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="53b5d-288">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="53b5d-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="53b5d-289">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="53b5d-289">Instinctual interactions</span></span>](interaction-fundamentals.md)