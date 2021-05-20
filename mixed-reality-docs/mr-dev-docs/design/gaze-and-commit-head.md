---
title: Mirada con la cabeza y confirmación
description: Introducción al modelo de entrada de mirada con la cabeza y confirmación, incluido el tamaño, la colocación y la estabilización del destino.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, mirada, mirada dirigida, interacción, diseño, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, destino, enfoque, suavizado
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196520"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="0ac8d-104">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="0ac8d-104">Head-gaze and commit</span></span>

<span data-ttu-id="0ac8d-105">_La mirada con la cabeza_ y [](gaze-and-commit.md) la confirmación son un caso especial del modelo de entrada de mirada y confirmación que implica el destino de un objeto con una dirección principal de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="0ac8d-106">Puede actuar en el destino con una entrada secundaria, como el gesto de la mano pulsación en el aire o el comando de voz "Seleccionar".</span><span class="sxs-lookup"><span data-stu-id="0ac8d-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="0ac8d-107">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="0ac8d-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0ac8d-108"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="0ac8d-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="0ac8d-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0ac8d-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="0ac8d-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0ac8d-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="0ac8d-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="0ac8d-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0ac8d-112">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="0ac8d-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="0ac8d-113">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="0ac8d-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0ac8d-114">✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</span><span class="sxs-lookup"><span data-stu-id="0ac8d-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="0ac8d-115">➕ Opción alternativa</span><span class="sxs-lookup"><span data-stu-id="0ac8d-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="0ac8d-116">Demostración de conceptos de diseño de seguimiento de la cabeza y los ojos</span><span class="sxs-lookup"><span data-stu-id="0ac8d-116">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="0ac8d-117">Si quiere ver los conceptos de diseño de Head and Eye Tracking en acción, consulte la demostración de vídeo Diseño de **hologramas:** seguimiento de la cabeza y seguimiento de los ojos a continuación.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-117">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="0ac8d-118">Cuando haya terminado, continúe para obtener un análisis más detallado de temas específicos.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-118">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="0ac8d-119">*Este vídeo se tomó de la aplicación "Diseño de hologramas" HoloLens 2 aplicación. Descargue y disfrute de la experiencia [completa aquí.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="0ac8d-119">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="0ac8d-120">Ajuste de tamaño del destino y comentarios</span><span class="sxs-lookup"><span data-stu-id="0ac8d-120">Target sizing and feedback</span></span>

<span data-ttu-id="0ac8d-121">Se ha mostrado repetidamente que el vector de mirada con la cabeza se puede usar para la selección de destino correcta, pero a menudo funciona mejor para la selección de destinos brutos: adquirir destinos más grandes.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-121">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="0ac8d-122">Los tamaños de destino mínimos de 1 grado a 1,5 grados permiten acciones correctas del usuario en la mayoría de los escenarios, aunque los destinos de 3 grados a menudo permiten una mayor velocidad.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-122">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="0ac8d-123">El tamaño que el usuario tiene como destino es efectivamente un área 2D incluso para los elementos 3D, la proyección que tenga como destino debe ser el área de destino.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-123">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="0ac8d-124">Proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario tiene como destino) es útil.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-124">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="0ac8d-125">Esto puede incluir tratamientos como efectos visibles de "mantener el mouse", resaltados o clics de audio, o borrar la alineación de un cursor con un elemento.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-125">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="0ac8d-126">![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0ac8d-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="0ac8d-127">*Tamaño de destino óptimo a 2 metros de distancia*</span><span class="sxs-lookup"><span data-stu-id="0ac8d-127">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="0ac8d-128">![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0ac8d-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="0ac8d-129">*Ejemplo de resaltado de un objeto establecido como destino de la mirada*</span><span class="sxs-lookup"><span data-stu-id="0ac8d-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="0ac8d-130">Situación del destino</span><span class="sxs-lookup"><span data-stu-id="0ac8d-130">Target placement</span></span>

<span data-ttu-id="0ac8d-131">A menudo, los usuarios no encuentran elementos de interfaz de usuario que se encuentran demasiado altos o bajos en su campo de vista.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-131">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="0ac8d-132">La mayor parte de su atención termina en áreas en torno a su enfoque principal, que es aproximadamente a nivel de los ojos.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-132">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="0ac8d-133">Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-133">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="0ac8d-134">Dada la tendencia de los usuarios a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de atención de la visión es aproximadamente de 10 grados), agrupar los elementos de la interfaz de usuario hasta el grado en que están relacionados conceptualmente puede usar comportamientos de encadenamiento de atención de elemento a elemento a medida que un usuario mueve la mirada a través de un área.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-134">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="0ac8d-135">Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-135">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="0ac8d-136">![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0ac8d-136">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="0ac8d-137&quot;>*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;0ac8d-137&quot;>*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name=&quot;improving-targeting-behaviors&quot;></a><span data-ttu-id=&quot;0ac8d-138&quot;>Mejora de los comportamientos de establecimiento de destino</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;0ac8d-138&quot;>Improving targeting behaviors</span></span>

<span data-ttu-id=&quot;0ac8d-139&quot;>Si la intención del usuario de dirigirse a algo se puede determinar o aproximar estrechamente, puede ser útil aceptar intentos de interacción casi desasistidos como si se hubieran dirigido correctamente.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;0ac8d-139&quot;>If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id=&quot;0ac8d-140&quot;>Estos son algunos métodos de éxito que se pueden incorporar en experiencias de realidad mixta:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;0ac8d-140&quot;>Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name=&quot;head-gaze-stabilization-gravity-wells&quot;></a><span data-ttu-id=&quot;0ac8d-141&quot;>Estabilización de la mirada con la cabeza (&quot;pozos de gravedad")</span><span class="sxs-lookup"><span data-stu-id="0ac8d-141">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="0ac8d-142">Esto debe estar activado la mayoría del tiempo o todo el tiempo.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-142">This should be turned on most or all of the time.</span></span> <span data-ttu-id="0ac8d-143">Esta técnica elimina los movimientos naturales de cabeza y cuello que los usuarios pueden tener también debido a comportamientos de aspecto y habla.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-143">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="0ac8d-144">Algoritmos de vínculo más cercano</span><span class="sxs-lookup"><span data-stu-id="0ac8d-144">Closest link algorithms</span></span>

<span data-ttu-id="0ac8d-145">Estos algoritmos funcionan mejor en áreas con contenido interactivo disperso.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-145">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="0ac8d-146">Si hay una alta probabilidad de que pueda determinar con qué estaba intentando interactuar un usuario, puede complementar sus capacidades de destino suponiendo algún nivel de intención.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-146">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="0ac8d-147">Acciones de backdating y postdating</span><span class="sxs-lookup"><span data-stu-id="0ac8d-147">Backdating and postdating actions</span></span>

<span data-ttu-id="0ac8d-148">Este mecanismo es útil en las tareas que requieren velocidad.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="0ac8d-149">Cuando un usuario se mueve a través de una serie de maniobras de destino y activación a gran velocidad, resulta útil asumir alguna intención.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-149">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="0ac8d-150">También es útil permitir que los pasos perdidos actúen en los destinos que el usuario tenía en el foco ligeramente antes o ligeramente después de la pulsación (50 ms antes o después de que fuera efectivo en las primeras pruebas).</span><span class="sxs-lookup"><span data-stu-id="0ac8d-150">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="0ac8d-151">Suavizado</span><span class="sxs-lookup"><span data-stu-id="0ac8d-151">Smoothing</span></span>

<span data-ttu-id="0ac8d-152">Este mecanismo es útil para la ruta de desplazamiento, lo que reduce la ligera vibración y los problemas debido a las características naturales del movimiento de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-152">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="0ac8d-153">Al suavizar los movimientos de trazado, suaviza el tamaño y la distancia de los movimientos en lugar de hacerlo a lo largo del tiempo.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-153">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="0ac8d-154">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="0ac8d-154">Magnetism</span></span>

<span data-ttu-id="0ac8d-155">Este mecanismo se puede pensar como una versión más general de los algoritmos de vínculo más cercanos: dibujar un cursor hacia un destino o simplemente aumentar los cuadros de acceso, ya sea visiblemente o no, a medida que los usuarios se aproximan a los destinos probables mediante el uso de cierto conocimiento del diseño interactivo para abordar mejor la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-155">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="0ac8d-156">Esto puede ser eficaz para destinos pequeños.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-156">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="0ac8d-157">Permanencia del foco</span><span class="sxs-lookup"><span data-stu-id="0ac8d-157">Focus stickiness</span></span>

<span data-ttu-id="0ac8d-158">Al determinar a qué elementos interactivos cercanos se va a dar, céntrate en él, la stickiness del foco proporciona un sesgo al elemento que está actualmente centrado.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-158">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="0ac8d-159">Esto ayuda a reducir los comportamientos erráticos de cambio de foco al flotar en un punto medio entre dos elementos con ruido natural.</span><span class="sxs-lookup"><span data-stu-id="0ac8d-159">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ac8d-160">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0ac8d-160">See also</span></span>

* [<span data-ttu-id="0ac8d-161">Interacción basada en los ojos</span><span class="sxs-lookup"><span data-stu-id="0ac8d-161">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="0ac8d-162">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="0ac8d-162">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="0ac8d-163">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="0ac8d-163">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0ac8d-164">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="0ac8d-164">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="0ac8d-165">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="0ac8d-165">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="0ac8d-166">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="0ac8d-166">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0ac8d-167">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="0ac8d-167">Voice input</span></span>](voice-input.md)