---
title: Mirada con la cabeza y confirmación
description: Empiece a trabajar con el modelo de entrada y de confirmación del encabezado, incluido el ajuste de tamaño, la ubicación y la estabilización de destino.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realidad mixta, miración rápida, interacción, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, destino, enfoque, suavizado
ms.openlocfilehash: a69b855e2246327affeeb0f771f565b94ea65cb2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582288"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="a83c2-104">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="a83c2-104">Head-gaze and commit</span></span>

<span data-ttu-id="a83c2-105">La acción de _mirar y confirmar_ es un caso especial del modelo de entrada de [mirada y de confirmación](gaze-and-commit.md) que implica el destino de un objeto con la dirección del encabezado de un usuario.</span><span class="sxs-lookup"><span data-stu-id="a83c2-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="a83c2-106">Puede actuar en el destino con una entrada secundaria, como el gesto de mano tocar o "seleccionar" comando de voz.</span><span class="sxs-lookup"><span data-stu-id="a83c2-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="a83c2-107">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a83c2-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a83c2-108"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="a83c2-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="a83c2-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a83c2-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a83c2-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a83c2-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a83c2-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="a83c2-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a83c2-112">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="a83c2-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="a83c2-113">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="a83c2-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a83c2-114">✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</span><span class="sxs-lookup"><span data-stu-id="a83c2-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="a83c2-115">➕ Opción alternativa</span><span class="sxs-lookup"><span data-stu-id="a83c2-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="a83c2-116">Ajuste de tamaño del destino y comentarios</span><span class="sxs-lookup"><span data-stu-id="a83c2-116">Target sizing and feedback</span></span>

<span data-ttu-id="a83c2-117">El vector de miras hacia abajo se ha mostrado varias veces para que se pueda usar para lograr objetivos más precisos, pero a menudo funciona mejor para la segmentación bruta: adquisición de destinos más grandes.</span><span class="sxs-lookup"><span data-stu-id="a83c2-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="a83c2-118">Los tamaños mínimos de destino de 1 grado a 1,5 grados permiten acciones de usuario correctas en la mayoría de los escenarios, aunque los destinos de 3 grados a menudo permiten una mayor velocidad.</span><span class="sxs-lookup"><span data-stu-id="a83c2-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="a83c2-119">El tamaño que tiene como destino el usuario es, en efecto, un área 2D incluso para los elementos 3D, lo que se enfrente a la proyección debe ser el área de destino.</span><span class="sxs-lookup"><span data-stu-id="a83c2-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="a83c2-120">Proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario tiene como destino) es útil.</span><span class="sxs-lookup"><span data-stu-id="a83c2-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="a83c2-121">Esto puede incluir tratamientos como efectos visibles de "mantener el mouse", resaltados de audio o clics o alineación clara de un cursor con un elemento.</span><span class="sxs-lookup"><span data-stu-id="a83c2-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="a83c2-122">![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a83c2-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="a83c2-123">*Tamaño óptimo de destino a una distancia de 2 metros*</span><span class="sxs-lookup"><span data-stu-id="a83c2-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="a83c2-124">![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a83c2-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="a83c2-125">*Ejemplo de resaltado de un objeto establecido como destino de la mirada*</span><span class="sxs-lookup"><span data-stu-id="a83c2-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="a83c2-126">Situación del destino</span><span class="sxs-lookup"><span data-stu-id="a83c2-126">Target placement</span></span>

<span data-ttu-id="a83c2-127">A menudo, los usuarios no pueden encontrar elementos de la interfaz de usuario ubicados demasiado altos o bajos en su campo de vista.</span><span class="sxs-lookup"><span data-stu-id="a83c2-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="a83c2-128">La mayor parte de su atención termina en áreas en torno a su enfoque principal, que es aproximadamente en el nivel de ojo.</span><span class="sxs-lookup"><span data-stu-id="a83c2-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="a83c2-129">Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos.</span><span class="sxs-lookup"><span data-stu-id="a83c2-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="a83c2-130">Dado que la tendencia de los usuarios a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de visión es aproximadamente de 10 grados), la agrupación de los elementos de la interfaz de usuario en el grado en que se relacionan conceptualmente puede usar los comportamientos de encadenamiento de atención entre el elemento y el elemento cuando un usuario mueve su vista hacia abajo por un área</span><span class="sxs-lookup"><span data-stu-id="a83c2-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="a83c2-131">Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.</span><span class="sxs-lookup"><span data-stu-id="a83c2-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="a83c2-132">![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a83c2-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="a83c2-133">*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="a83c2-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="a83c2-134">Mejora de los comportamientos de establecimiento de destino</span><span class="sxs-lookup"><span data-stu-id="a83c2-134">Improving targeting behaviors</span></span>

<span data-ttu-id="a83c2-135">Si la intención del usuario de destinar algo puede determinarse o aproximarse, puede ser útil aceptar los intentos de interacción aproximados como si estuviesen dirigidos correctamente.</span><span class="sxs-lookup"><span data-stu-id="a83c2-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="a83c2-136">Estos son algunos de los métodos correctos que se pueden incorporar en experiencias de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="a83c2-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="a83c2-137">Estabilización de la mirada con la cabeza ("pozos de gravedad")</span><span class="sxs-lookup"><span data-stu-id="a83c2-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="a83c2-138">Esto se debe activar la mayoría o la totalidad del tiempo.</span><span class="sxs-lookup"><span data-stu-id="a83c2-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="a83c2-139">Esta técnica elimina las vibraciones de cabeza natural y cuello que los usuarios podrían tener como movimiento debido a los comportamientos de mirar y hablar.</span><span class="sxs-lookup"><span data-stu-id="a83c2-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="a83c2-140">Algoritmos de vínculo más cercano</span><span class="sxs-lookup"><span data-stu-id="a83c2-140">Closest link algorithms</span></span>

<span data-ttu-id="a83c2-141">Estos algoritmos funcionan mejor en áreas con contenido interactivo disperso.</span><span class="sxs-lookup"><span data-stu-id="a83c2-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="a83c2-142">Si hay una probabilidad alta de que pueda determinar con qué un usuario estaba intentando interactuar, puede complementar sus capacidades de destino suponiendo cierto nivel de intento.</span><span class="sxs-lookup"><span data-stu-id="a83c2-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="a83c2-143">Acciones de la</span><span class="sxs-lookup"><span data-stu-id="a83c2-143">Backdating and postdating actions</span></span>

<span data-ttu-id="a83c2-144">Este mecanismo es útil en las tareas que requieren velocidad.</span><span class="sxs-lookup"><span data-stu-id="a83c2-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="a83c2-145">Cuando un usuario está pasando por una serie de destinos y maniobras de activación a velocidad, resulta útil asumir algún intento.</span><span class="sxs-lookup"><span data-stu-id="a83c2-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="a83c2-146">También resulta útil permitir que los pasos perdidos actúen en los destinos que el usuario tenía enfocado ligeramente antes o ligeramente después de la pulsación (50 ms antes/después era efectivo en las primeras pruebas).</span><span class="sxs-lookup"><span data-stu-id="a83c2-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="a83c2-147">Suavizado</span><span class="sxs-lookup"><span data-stu-id="a83c2-147">Smoothing</span></span>

<span data-ttu-id="a83c2-148">Este mecanismo es útil para los movimientos de las acciones, lo que reduce la ligera vibración y wobbles debido a las características de movimiento del cabezal natural.</span><span class="sxs-lookup"><span data-stu-id="a83c2-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="a83c2-149">Al suavizar los movimientos de las acciones, smoothándose por el tamaño y la distancia de los movimientos en lugar de a lo largo del tiempo.</span><span class="sxs-lookup"><span data-stu-id="a83c2-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="a83c2-150">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="a83c2-150">Magnetism</span></span>

<span data-ttu-id="a83c2-151">Este mecanismo puede considerarse como una versión más general de los algoritmos de vínculo más cercanos: dibujar un cursor hacia un destino o simplemente aumentar hitboxes, ya sea visible o no, a medida que los usuarios se aproximan a los objetivos más probables mediante el uso de algún conocimiento del diseño interactivo para un mejor enfoque de la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="a83c2-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="a83c2-152">Esto puede ser eficaz para destinos pequeños.</span><span class="sxs-lookup"><span data-stu-id="a83c2-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="a83c2-153">Permanencia del foco</span><span class="sxs-lookup"><span data-stu-id="a83c2-153">Focus stickiness</span></span>

<span data-ttu-id="a83c2-154">A la hora de determinar qué elementos interactivos cercanos se deben dar, centrarse en, el ajuste del foco proporciona una inclinación al elemento que está enfocado actualmente.</span><span class="sxs-lookup"><span data-stu-id="a83c2-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="a83c2-155">Esto ayuda a reducir los comportamientos de cambio de foco errático al flotar en un punto medio entre dos elementos con ruido natural.</span><span class="sxs-lookup"><span data-stu-id="a83c2-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="a83c2-156">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a83c2-156">See also</span></span>

* [<span data-ttu-id="a83c2-157">Interacción basada en los ojos</span><span class="sxs-lookup"><span data-stu-id="a83c2-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="a83c2-158">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="a83c2-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="a83c2-159">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="a83c2-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a83c2-160">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="a83c2-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a83c2-161">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="a83c2-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="a83c2-162">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="a83c2-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a83c2-163">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="a83c2-163">Voice input</span></span>](voice-input.md)