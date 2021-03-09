---
title: Apuntar y confirmar con las manos
description: Conozca los aspectos básicos del modelo de entrada de apunte y confirmación para la compatibilidad con gestos en aplicaciones de realidad mixta.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, interaction, design, HoloLens, hands, far, point and commit , mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, hand rays, object manipulation, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 8196b67f103bae346ba4da065ee6045ff231b004
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759871"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="0d849-104">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="0d849-104">Point and commit with hands</span></span>

![Cursores](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="0d849-106">"Apuntar y confirmar con las manos" es un modelo de entrada que permite a los usuarios seleccionar y manipular contenido 2D y 3D que esté fuera de su alcance.</span><span class="sxs-lookup"><span data-stu-id="0d849-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="0d849-107">Esta técnica de interacción "lejana" es exclusiva de la realidad mixta, ya que los usuarios no interactúan de forma natural con el mundo real.</span><span class="sxs-lookup"><span data-stu-id="0d849-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="0d849-108">Por ejemplo, en la película de superhéroes *X-Men*, el personaje [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) es capaz de manipular objetos lejanos a distancia con las manos.</span><span class="sxs-lookup"><span data-stu-id="0d849-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="0d849-109">Esto no es algo que los seres humanos puedan hacer en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="0d849-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="0d849-110">Por ello, tanto en HoloLens (AR) como en Mixed Reality (MR), equipamos a los usuarios con este poder mágico para romper las restricciones físicas del mundo real.</span><span class="sxs-lookup"><span data-stu-id="0d849-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="0d849-111">No solo es una experiencia holográfica divertida, sino que también hace que las interacciones de los usuarios sean más eficaces.</span><span class="sxs-lookup"><span data-stu-id="0d849-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="0d849-112">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="0d849-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="0d849-113"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="0d849-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="0d849-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0d849-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="0d849-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0d849-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="0d849-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="0d849-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="0d849-117">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="0d849-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="0d849-118">❌ No se admite</span><span class="sxs-lookup"><span data-stu-id="0d849-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="0d849-119">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="0d849-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="0d849-120">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="0d849-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="0d849-121">_"Apuntar y confirmar con las manos"_ es una de las nuevas características que usa el nuevo sistema articulado de seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="0d849-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="0d849-122">Este modelo de entrada es también el modelo de entrada principal de los auriculares envolventes, gracias al uso de controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="0d849-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="0d849-123">Rayos de las manos</span><span class="sxs-lookup"><span data-stu-id="0d849-123">Hand rays</span></span>

<span data-ttu-id="0d849-124">En HoloLens 2, hemos creado un haz que sale desde el centro de la palma de la mano.</span><span class="sxs-lookup"><span data-stu-id="0d849-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="0d849-125">Dicho rayo se trata como una extensión de la mano.</span><span class="sxs-lookup"><span data-stu-id="0d849-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="0d849-126">Un cursor con forma de anillo se acopla al final del rayo para indicar la ubicación en que el rayo se cruza con un objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="0d849-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="0d849-127">El objeto en que se posa el cursor puede recibir comandos gestuales de la mano.</span><span class="sxs-lookup"><span data-stu-id="0d849-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="0d849-128">Este comando gestual básico se desencadena al usar los dedos pulgar e índice para realizar la acción de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="0d849-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="0d849-129">Si se usa el haz de mano para apuntar y la acción de pulsar en el aire para confirmar, los usuarios pueden activar un botón o un hipervínculo.</span><span class="sxs-lookup"><span data-stu-id="0d849-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="0d849-130">Si usan más gestos compuestos, los usuarios pueden navegar por el contenido web y manipular objetos 3D a distancia.</span><span class="sxs-lookup"><span data-stu-id="0d849-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="0d849-131">El diseño visual del rayo de la mano también debe reaccionar a estos estados de apuntar y confirmar, como se describe y se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="0d849-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="0d849-132">![haces de mano que apuntan](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="0d849-133">**Estado de apuntar**</span><span class="sxs-lookup"><span data-stu-id="0d849-133">**Pointing state**</span></span><br>
        <span data-ttu-id="0d849-134">En el estado *señalar*, el rayo es una línea discontinua y el cursor tiene forma de anillo.</span><span class="sxs-lookup"><span data-stu-id="0d849-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="0d849-135">![haces de mano que confirman](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="0d849-136">**Estado de confirmación**</span><span class="sxs-lookup"><span data-stu-id="0d849-136">**Commit state**</span></span><br>
        <span data-ttu-id="0d849-137">En el estado *confirmar*, el rayo se convierte en una línea sólida y el cursor se reduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="0d849-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="0d849-138">Transición entre cerca y lejos</span><span class="sxs-lookup"><span data-stu-id="0d849-138">Transition between near and far</span></span>

<span data-ttu-id="0d849-139">En lugar de usar gestos específicos como "señalar con el dedo índice" para dirigir el rayo, hemos diseñado el rayo para que salga del centro de la palma de la mano del usuario.</span><span class="sxs-lookup"><span data-stu-id="0d849-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="0d849-140">De este modo, tenemos los cinco dedos disponibles para realizar más gestos de manipulación, como el contacto y la captura.</span><span class="sxs-lookup"><span data-stu-id="0d849-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="0d849-141">Con este diseño, creamos solo un modelo mental, se usa el mismo conjunto de gestos de las manos para la interacción cercana y la lejana.</span><span class="sxs-lookup"><span data-stu-id="0d849-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="0d849-142">Puedes usar el mismo gesto de arrastrar para manipular objetos que se encuentren a distinta distancia.</span><span class="sxs-lookup"><span data-stu-id="0d849-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="0d849-143">La invocación de los haces es automática y se basa en la proximidad:</span><span class="sxs-lookup"><span data-stu-id="0d849-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0d849-144">![Manipulación cercana](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="0d849-145">**Manipulación cercana**</span><span class="sxs-lookup"><span data-stu-id="0d849-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="0d849-146">Cuando a un objeto se llega estirando el brazo (aproximadamente 50 cm), los haces se desactivan automáticamente, lo que fomenta la interacción cercana.</span><span class="sxs-lookup"><span data-stu-id="0d849-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="0d849-147">![Manipulación lejana](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="0d849-148">**Manipulación lejana**</span><span class="sxs-lookup"><span data-stu-id="0d849-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="0d849-149">Cuando el objeto está a más de 50 cm, los rayos se activan.</span><span class="sxs-lookup"><span data-stu-id="0d849-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="0d849-150">La transición suave y sin problemas.</span><span class="sxs-lookup"><span data-stu-id="0d849-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="0d849-151">Interacción con una tableta táctil 2D</span><span class="sxs-lookup"><span data-stu-id="0d849-151">2D slate interaction</span></span>

<span data-ttu-id="0d849-152">Una tableta táctil 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web.</span><span class="sxs-lookup"><span data-stu-id="0d849-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="0d849-153">El concepto de diseño para la interacción lejana con una tableta táctil 2D es usar los rayos de las manos para buscar el objetivo y pulsar en el aire para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="0d849-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="0d849-154">Después de buscar el destino con un rayo de la mano, los usuarios pueden pulsar en el aire para desencadenar un hipervínculo o un botón.</span><span class="sxs-lookup"><span data-stu-id="0d849-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="0d849-155">Pueden usar una mano para "pulsar en el aire y arrastrar" a fin de desplazar el contenido de la tableta táctil hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="0d849-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="0d849-156">El movimiento relativo de usar las dos manos para pulsar en el aire y arrastrar puede acercar y alejar el contenido de la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="0d849-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="0d849-157">Si se seleccionan como destino del rayo las esquinas y los bordes aparece la prestación de manipulación más cercana.</span><span class="sxs-lookup"><span data-stu-id="0d849-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="0d849-158">Al "agarrar y arrastrar" las prestaciones de manipulación, los usuarios pueden realizar un escalado uniforme mediante las prestaciones de la esquina y redistribuir la tableta táctil mediante las prestaciones del borde.</span><span class="sxs-lookup"><span data-stu-id="0d849-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="0d849-159">El procedimiento de agarrar y arrastrar la barra holográfica de la parte superior de la tableta táctil 2D permite a los usuarios mover toda la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="0d849-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0d849-160">![Hacer clic en la interacción con una tableta táctil 2D](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="0d849-161">**Hacer clic**</span><span class="sxs-lookup"><span data-stu-id="0d849-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0d849-162">![Desplazar en la interacción con una tableta táctil 2D](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="0d849-163">**Desplazar**</span><span class="sxs-lookup"><span data-stu-id="0d849-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0d849-164">![Zoom en la interacción con una tableta táctil 2D](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="0d849-165">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="0d849-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="0d849-166">**Para manipular la tableta táctil 2D**</span><span class="sxs-lookup"><span data-stu-id="0d849-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="0d849-167">los usuarios apuntan el rayo de la mano a las esquinas y bordes y aparece la prestación de manipulación más cercana.</span><span class="sxs-lookup"><span data-stu-id="0d849-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="0d849-168">Al aplicar un gesto de manipulación en la prestación, los usuarios pueden realizar un escalado uniforme mediante la prestación de la esquina y redistribuir la tableta táctil mediante la prestación del borde.</span><span class="sxs-lookup"><span data-stu-id="0d849-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="0d849-169">Al aplicar un gesto de manipulación a la barra holográfica de la parte superior de la tableta táctil 2D, los usuarios pueden mover toda la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="0d849-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="0d849-170">Manipulación de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="0d849-170">3D object manipulation</span></span>

<span data-ttu-id="0d849-171">En la manipulación directa, hay dos formas de que los usuarios manipulen objetos 3D, la manipulación con prestaciones y la manipulación sin prestaciones.</span><span class="sxs-lookup"><span data-stu-id="0d849-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="0d849-172">En el modelo para apuntar y confirmar, los usuarios pueden conseguir exactamente las mismas tareas a través de los haces de mano.</span><span class="sxs-lookup"><span data-stu-id="0d849-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="0d849-173">No es necesario realizar ningún aprendizaje adicional.</span><span class="sxs-lookup"><span data-stu-id="0d849-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="0d849-174">Manipulación con prestaciones</span><span class="sxs-lookup"><span data-stu-id="0d849-174">Affordance-based manipulation</span></span>

<span data-ttu-id="0d849-175">Los usuarios usan los rayos de las manos para apuntar y mostrar el rectángulo de selección y las prestaciones de manipulación.</span><span class="sxs-lookup"><span data-stu-id="0d849-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="0d849-176">Los usuarios pueden aplicar el gesto de manipulación al rectángulo de selección para mover todo el objeto, a las prestaciones del borde para girarlo y a las prestaciones de la esquina para escalarlo de forma uniforme.</span><span class="sxs-lookup"><span data-stu-id="0d849-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="0d849-177">![Movimiento lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="0d849-178">**Mover**</span><span class="sxs-lookup"><span data-stu-id="0d849-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0d849-179">![Giro lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="0d849-180">**Girar**</span><span class="sxs-lookup"><span data-stu-id="0d849-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0d849-181">![Escala lejana en la manipulación de objetos 3D](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="0d849-182">**Escalar**</span><span class="sxs-lookup"><span data-stu-id="0d849-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="0d849-183">Manipulación sin prestaciones</span><span class="sxs-lookup"><span data-stu-id="0d849-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="0d849-184">Los usuarios señalan con los rayos de las manos para mostrar el rectángulo de selección y, después, le aplican directamente los gestos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="0d849-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="0d849-185">Con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano.</span><span class="sxs-lookup"><span data-stu-id="0d849-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="0d849-186">Con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.</span><span class="sxs-lookup"><span data-stu-id="0d849-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="0d849-187">Gestos instintivos</span><span class="sxs-lookup"><span data-stu-id="0d849-187">Instinctual gestures</span></span>

<span data-ttu-id="0d849-188">El concepto de gestos instintivos para señalar y confirmar es similar a la de la [manipulación directa con las manos](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="0d849-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="0d849-189">Los gestos que los usuarios realizan en un objeto 3D los guía el diseño de las prestaciones de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="0d849-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="0d849-190">Por ejemplo, un punto de control pequeño podría motivar a los usuarios a acercar los dedos pulgar e índice, mientras que si un usuario quiere agarrar un objeto mayor, debe usar los cinco dedos.</span><span class="sxs-lookup"><span data-stu-id="0d849-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0d849-191">![gestos instintivos para objetos lejanos pequeños](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="0d849-192">**Objeto pequeño**</span><span class="sxs-lookup"><span data-stu-id="0d849-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0d849-193">![gestos instintivos para objetos lejanos medianos](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="0d849-194">**Objeto mediano**</span><span class="sxs-lookup"><span data-stu-id="0d849-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0d849-195">![gestos instintivos para objetos lejanos grandes](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="0d849-196">**Objeto grande**</span><span class="sxs-lookup"><span data-stu-id="0d849-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="0d849-197">Diseño simétrico entre las manos y 6 controladores DoF</span><span class="sxs-lookup"><span data-stu-id="0d849-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="0d849-198">El concepto de señalar y confirmar de la interacción lejana se creó y definió para el portal de realidad mixta (PRM).</span><span class="sxs-lookup"><span data-stu-id="0d849-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="0d849-199">En este escenario, el usuario lleva un casco envolvente e interactúa con objetos 3D a través de los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="0d849-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="0d849-200">Los controladores de movimiento lanzar rayos para señalar y manipular objetos lejanos.</span><span class="sxs-lookup"><span data-stu-id="0d849-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="0d849-201">Hay botones en los controladores para confirmar más acciones diferentes.</span><span class="sxs-lookup"><span data-stu-id="0d849-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="0d849-202">Aprovecharemos el modelo de interacción de rayos y los acoplaremos a ambas manos.</span><span class="sxs-lookup"><span data-stu-id="0d849-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="0d849-203">Con este diseño simétrico, los usuarios que están familiarizados con MRP no necesitan aprender otro modelo de interacción para señalar y manipular a distancia cuando usan HoloLens 2, y viceversa.</span><span class="sxs-lookup"><span data-stu-id="0d849-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="0d849-204">![diseño simétrico para haces con controladores](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="0d849-205">**Haces de controlador**</span><span class="sxs-lookup"><span data-stu-id="0d849-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="0d849-206">![diseño simétrico para haces con manos](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="0d849-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="0d849-207">**Haces de mano**</span><span class="sxs-lookup"><span data-stu-id="0d849-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="0d849-208">Haz de mano en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="0d849-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="0d849-209">De forma predeterminada, MRTK proporciona un haz de mano prefabricado ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) que tiene el mismo estado visual que el haz de mano del sistema del shell.</span><span class="sxs-lookup"><span data-stu-id="0d849-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="0d849-210">Se asigna en el perfil de entrada de MRTK, en Punteros.</span><span class="sxs-lookup"><span data-stu-id="0d849-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="0d849-211">En un casco envolvente, se usan los mismos haces para los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="0d849-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="0d849-212">MRTK: perfil de puntero</span><span class="sxs-lookup"><span data-stu-id="0d849-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md#pointer-configuration)
* [<span data-ttu-id="0d849-213">MRTK: sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="0d849-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [<span data-ttu-id="0d849-214">MRTK: punteros</span><span class="sxs-lookup"><span data-stu-id="0d849-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a><span data-ttu-id="0d849-215">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0d849-215">See also</span></span>
* [<span data-ttu-id="0d849-216">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="0d849-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0d849-217">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="0d849-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0d849-218">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="0d849-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0d849-219">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="0d849-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="0d849-220">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="0d849-220">Instinctual interactions</span></span>](interaction-fundamentals.md)