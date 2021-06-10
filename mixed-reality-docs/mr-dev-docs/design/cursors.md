---
title: Cursores
description: Un cursor, o indicador del vector de destino, proporciona comentarios continuos para que el usuario comprenda lo que HoloLens entiende sobre sus intenciones.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1.ª generación), HoloLens 2, Mixed Reality, cursores, destino, mirada, gestos, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, rayos, entrada
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600384"
---
# <a name="cursors"></a><span data-ttu-id="30454-104">Cursores</span><span class="sxs-lookup"><span data-stu-id="30454-104">Cursors</span></span>

![Cursores](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="30454-106">Un cursor proporciona comentarios continuos en función de dónde cree el casco que un usuario se centra actualmente en un momento determinado.</span><span class="sxs-lookup"><span data-stu-id="30454-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="30454-107">Los comentarios del cursor incluyen qué área, holograma o punto del entorno virtual responde a la entrada.</span><span class="sxs-lookup"><span data-stu-id="30454-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="30454-108">Aunque el cursor es una representación digital de dónde entiende el dispositivo la atención del usuario, eso no es lo mismo que determinar las intenciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="30454-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="30454-109">Los comentarios del cursor también permiten a los usuarios saber qué respuestas del sistema deben esperar.</span><span class="sxs-lookup"><span data-stu-id="30454-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="30454-110">Puede usar los comentarios para comunicar su intención al dispositivo, lo que aumenta la confianza del usuario.</span><span class="sxs-lookup"><span data-stu-id="30454-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="30454-111">Hay tres tipos de cursores: **dedo, rayo** y mirada **con la cabeza.**</span><span class="sxs-lookup"><span data-stu-id="30454-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="30454-112">Estos cursores de punto funcionan con diferentes modalidades de entrada en HoloLens, HoloLens 2 y cascos envolventes.</span><span class="sxs-lookup"><span data-stu-id="30454-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="30454-113">A continuación se muestran instrucciones sobre qué tipo de cursor usar para cada tipo de casco y modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="30454-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="30454-114">En Mixed Reality Toolkit (MRTK), hemos creado módulos de cursores de arrastrar y colocar para ayudarle a crear la experiencia de apuntamiento correcta.</span><span class="sxs-lookup"><span data-stu-id="30454-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="30454-115">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="30454-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="30454-116"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="30454-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="30454-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="30454-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="30454-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="30454-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="30454-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="30454-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="30454-120">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="30454-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="30454-121">✔️</span><span class="sxs-lookup"><span data-stu-id="30454-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="30454-122">Cursor de rayo</span><span class="sxs-lookup"><span data-stu-id="30454-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="30454-123">✔️</span><span class="sxs-lookup"><span data-stu-id="30454-123">✔️</span></span></td>
        <td><span data-ttu-id="30454-124">✔️</span><span class="sxs-lookup"><span data-stu-id="30454-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="30454-125">Cursor de mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="30454-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="30454-126">✔️</span><span class="sxs-lookup"><span data-stu-id="30454-126">✔️</span></span></td>
        <td><span data-ttu-id="30454-127">✔️</span><span class="sxs-lookup"><span data-stu-id="30454-127">✔️</span></span></td>
        <td><span data-ttu-id="30454-128">✔️</span><span class="sxs-lookup"><span data-stu-id="30454-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="30454-129">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="30454-129">Finger cursor</span></span>

<span data-ttu-id="30454-130">El cursor de dedo solo está disponible en[](direct-manipulation.md)el HoloLens 2 para mejorar el modo de interacción "manipulación directa con las manos".</span><span class="sxs-lookup"><span data-stu-id="30454-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="30454-131">Hemos adjuntado anillos a las puntas de ambos dedos de índice para comprender mejor dónde apunta el dedo.</span><span class="sxs-lookup"><span data-stu-id="30454-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="30454-132">El tamaño del anillo se basa en la proximidad del dedo a la superficie de la interfaz de usuario, que se reduce a un punto pequeño cuando el dedo toca la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="30454-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="30454-133">Cuanto más cerca se acerque el dedo, más pequeño es el anillo.</span><span class="sxs-lookup"><span data-stu-id="30454-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="30454-134">![cursor de dedo](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="30454-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="30454-135">**Estados de comentarios visuales del cursor** de dedo 1: el anillo se reduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="30454-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="30454-136">2: el anillo se alinea con la superficie.</span><span class="sxs-lookup"><span data-stu-id="30454-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="30454-137">3: el anillo es vector de dedo a dedo.</span><span class="sxs-lookup"><span data-stu-id="30454-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="30454-138">4: Sin anillo.</span><span class="sxs-lookup"><span data-stu-id="30454-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="30454-139">Cursor de rayo</span><span class="sxs-lookup"><span data-stu-id="30454-139">Ray cursor</span></span>

<span data-ttu-id="30454-140">Los cursores de rayos se asocian al final de los rayos de puntero lejano para permitir la manipulación de objetos que están fuera del alcance de las manos.</span><span class="sxs-lookup"><span data-stu-id="30454-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="30454-141">En los cascos envolventes, los rayos se lanzan desde los controladores de movimiento y terminan en cursores de punto.</span><span class="sxs-lookup"><span data-stu-id="30454-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="30454-142">En HoloLens 2, aplicamos el modelo mental de estos rayos de controlador de movimiento y los rayos de mano diseñados que se originan a partir de los dedos y terminan en cursores en forma de anillo que son coherentes con los cursores de dedo usados en la manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="30454-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="30454-143">![Controlador de cursor ray](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="30454-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="30454-144">**Cursores de rayos de controladores de movimiento**</span><span class="sxs-lookup"><span data-stu-id="30454-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="30454-145">![Mano del cursor ray](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="30454-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="30454-146">**Cursores de rayo de las manos**</span><span class="sxs-lookup"><span data-stu-id="30454-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="30454-147">Cursor de mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="30454-147">Head-gaze cursor</span></span>

<span data-ttu-id="30454-148">El cursor de mirada con la cabeza es un punto que se adjunta al final de un vector de mirada con la cabeza invisible que usa la posición y la rotación de la cabeza hasta el punto.</span><span class="sxs-lookup"><span data-stu-id="30454-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="30454-149">Para ejecutar acciones, este cursor que apunta se empareja con varias entradas de confirmación, como pulsación en el aire, comandos de voz, permanencia y presionar el botón.</span><span class="sxs-lookup"><span data-stu-id="30454-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="30454-150">En HoloLens 2, la mirada con la cabeza se empareja mejor con cualquier entrada de confirmación que no sea pulsación en el aire, ya que habrá un conflicto de interacción entre el toque de aire y los rayos de mano lejanos.</span><span class="sxs-lookup"><span data-stu-id="30454-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="30454-151">![Mano del cursor de mirada con la cabeza](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="30454-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="30454-152">**Cursor de mirada con la cabeza con gesto de mano**</span><span class="sxs-lookup"><span data-stu-id="30454-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="30454-153">![Voz del cursor de mirada con la cabeza](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="30454-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="30454-154">**Cursor de mirada con la cabeza con el comando de voz**</span><span class="sxs-lookup"><span data-stu-id="30454-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="30454-155">Recomendaciones de personalización de cursores</span><span class="sxs-lookup"><span data-stu-id="30454-155">Cursor customization recommendations</span></span>

<span data-ttu-id="30454-156">Si desea personalizar los comportamientos y las apariencias de los comentarios del cursor, estas son algunas recomendaciones de diseño:</span><span class="sxs-lookup"><span data-stu-id="30454-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="30454-157">Escala de cursores</span><span class="sxs-lookup"><span data-stu-id="30454-157">Cursor scale</span></span>

* <span data-ttu-id="30454-158">El cursor no debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar fácilmente con el contenido y verlo.</span><span class="sxs-lookup"><span data-stu-id="30454-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="30454-159">En función de la experiencia que cree, el escalado del cursor a medida que el usuario examina también es una consideración importante.</span><span class="sxs-lookup"><span data-stu-id="30454-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="30454-160">Por ejemplo, a medida que el usuario mira más lejos en su experiencia, el cursor no debe ser demasiado pequeño, de modo que se pierda.</span><span class="sxs-lookup"><span data-stu-id="30454-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="30454-161">Al escalar el cursor, considere la posibilidad de aplicarle una animación suave a medida que se escala para darle una sensación orgánica.</span><span class="sxs-lookup"><span data-stu-id="30454-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="30454-162">Evite la obstrución de contenido.</span><span class="sxs-lookup"><span data-stu-id="30454-162">Avoid obstructing content.</span></span> <span data-ttu-id="30454-163">Los hologramas son lo que hace que la experiencia sea fácil de recordar y el cursor no debería quitarse de ellos.</span><span class="sxs-lookup"><span data-stu-id="30454-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="30454-164">Forma de cursor sin dirección</span><span class="sxs-lookup"><span data-stu-id="30454-164">Directionless cursor shape</span></span>

* <span data-ttu-id="30454-165">Aunque no hay ninguna forma de cursor derecha, se recomienda usar una forma sin dirección como un torus.</span><span class="sxs-lookup"><span data-stu-id="30454-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="30454-166">Un cursor que apunta en alguna dirección (por ejemplo, un cursor de flecha tradicional) podría confundir al usuario para que siempre tenga ese aspecto.</span><span class="sxs-lookup"><span data-stu-id="30454-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="30454-167">Una excepción a esto es cuando se usa el cursor para comunicar la instrucción de interacción al usuario.</span><span class="sxs-lookup"><span data-stu-id="30454-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="30454-168">Por ejemplo, al escalar hologramas en el sistema operativo Mixed Reality, el cursor incluye temporalmente flechas que indica al usuario cómo mover la mano para escalar el holograma.</span><span class="sxs-lookup"><span data-stu-id="30454-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="30454-169">Buscar y sentir</span><span class="sxs-lookup"><span data-stu-id="30454-169">Look and feel</span></span>

* <span data-ttu-id="30454-170">Un cursor con forma de anillo o torus funciona para muchas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="30454-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="30454-171">Elija un color y una forma que represente mejor la experiencia que está creando.</span><span class="sxs-lookup"><span data-stu-id="30454-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="30454-172">Los cursores son especialmente propensos a la [separación de colores.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)</span><span class="sxs-lookup"><span data-stu-id="30454-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="30454-173">Un cursor pequeño con opacidad equilibrada lo mantiene informativo sin dominar la jerarquía visual.</span><span class="sxs-lookup"><span data-stu-id="30454-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="30454-174">Tenga en cuenta el uso de sombras o resaltados detrás del cursor, ya que podrían impedir el contenido y distraerse de la tarea en la mano.</span><span class="sxs-lookup"><span data-stu-id="30454-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="30454-175">Los cursores deben alinearse con las superficies de la aplicación y desenlace.</span><span class="sxs-lookup"><span data-stu-id="30454-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="30454-176">Los usuarios tendrán la sensación de que el sistema puede ver dónde están buscando, pero también de que el sistema es consciente de su entorno.</span><span class="sxs-lookup"><span data-stu-id="30454-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="30454-177">Por ejemplo, el cursor del sistema operativo Mixed Reality se alinea con las superficies del mundo del usuario, lo que crea una sensación de conocimiento del mundo incluso cuando el usuario no mira directamente un holograma.</span><span class="sxs-lookup"><span data-stu-id="30454-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="30454-178">El bloqueo magnético del cursor en un elemento interactivo cuando está cerca del usuario puede ayudar a mejorar la confianza de que el usuario interactuará con ese elemento cuando use una acción de selección.</span><span class="sxs-lookup"><span data-stu-id="30454-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="30454-179">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="30454-179">Visual cues</span></span>

* <span data-ttu-id="30454-180">Si la experiencia se centra en un solo holograma, el cursor debe alinear y alejarse solo de ese holograma y cambiar de forma al mirar fuera de ese holograma.</span><span class="sxs-lookup"><span data-stu-id="30454-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="30454-181">Esto puede transmitir al usuario que el holograma es manejable y que puede interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="30454-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="30454-182">Si la aplicación usa la asignación espacial, el cursor podría alinear y alinear todas las superficies que ve.</span><span class="sxs-lookup"><span data-stu-id="30454-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="30454-183">Esto proporciona comentarios a los usuarios para que HoloLens y la aplicación puedan ver su espacio.</span><span class="sxs-lookup"><span data-stu-id="30454-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="30454-184">Esto refuerza el hecho de que los hologramas son reales y en nuestro mundo, y ayuda a reducir la brecha entre real y virtual.</span><span class="sxs-lookup"><span data-stu-id="30454-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="30454-185">Tenga una idea de lo que debe hacer el cursor cuando no haya hologramas ni superficies a la vista.</span><span class="sxs-lookup"><span data-stu-id="30454-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="30454-186">Colocarlo a una distancia predeterminada delante del usuario es una opción.</span><span class="sxs-lookup"><span data-stu-id="30454-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="30454-187">Acciones posibles</span><span class="sxs-lookup"><span data-stu-id="30454-187">Possible actions</span></span>

* <span data-ttu-id="30454-188">El cursor se puede representar mediante iconos diferentes para transmitir las posibles acciones que puede realizar un holograma, como el escalado o la rotación.</span><span class="sxs-lookup"><span data-stu-id="30454-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="30454-189">Agregue solo información adicional sobre el cursor si significa algo para el usuario.</span><span class="sxs-lookup"><span data-stu-id="30454-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="30454-190">De lo contrario, es posible que los usuarios no observen los cambios de estado o se confundan con el cursor.</span><span class="sxs-lookup"><span data-stu-id="30454-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="30454-191">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="30454-191">Input state</span></span>

* <span data-ttu-id="30454-192">Podríamos usar el cursor para mostrar el estado de entrada o la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="30454-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="30454-193">Por ejemplo, podríamos mostrar un icono que le dice al usuario que el sistema ve su estado de mano y que la aplicación sabe que está listo para tomar medidas.</span><span class="sxs-lookup"><span data-stu-id="30454-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="30454-194">También podríamos usar el cursor para mostrar a los usuarios que el sistema ha oído los comandos de voz a través de un cambio momentánario de color.</span><span class="sxs-lookup"><span data-stu-id="30454-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="30454-195">Los siguientes estados de cursor se pueden implementar de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="30454-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="30454-196">Puede implementar estos estados diferentes mediante el modelado del cursor como una máquina de estados.</span><span class="sxs-lookup"><span data-stu-id="30454-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="30454-197">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="30454-197">For example:</span></span>
    * <span data-ttu-id="30454-198">El estado de inactividad es donde se muestra el cursor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="30454-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="30454-199">El estado listo es cuando se ha detectado la mano del usuario en la posición lista.</span><span class="sxs-lookup"><span data-stu-id="30454-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="30454-200">El estado de interacción es cuando el usuario está realizando una interacción determinada.</span><span class="sxs-lookup"><span data-stu-id="30454-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="30454-201">El estado de las acciones posibles o el estado del mouse es cuando se transmiten las posibles acciones que se pueden realizar en un holograma.</span><span class="sxs-lookup"><span data-stu-id="30454-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="30454-202">También puede implementar estos estados de una manera capaz de mostrar distintos recursos de arte cuando detecte estados diferentes.</span><span class="sxs-lookup"><span data-stu-id="30454-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="30454-203">Ir "sin cursor"</span><span class="sxs-lookup"><span data-stu-id="30454-203">Going "cursor-free"</span></span>

<span data-ttu-id="30454-204">Se recomienda diseñar sin un cursor cuando la sensación de inmersiones es un componente clave de una experiencia y cuando las interacciones de apuntar (a través de la mirada y el gesto) no requieren una gran precisión.</span><span class="sxs-lookup"><span data-stu-id="30454-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="30454-205">El sistema todavía necesita cumplir los requisitos normales de un cursor: proporcionar a los usuarios comentarios continuos sobre la comprensión del sistema de su apuntar y ayudarles a comunicar sus intenciones al sistema.</span><span class="sxs-lookup"><span data-stu-id="30454-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="30454-206">Esto puede ser factible a través de otros cambios de estado apreciables.</span><span class="sxs-lookup"><span data-stu-id="30454-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="30454-207">Cursor en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="30454-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="30454-208">De forma predeterminada, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona un cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tiene el mismo estado visual que el cursor del sistema del shell.</span><span class="sxs-lookup"><span data-stu-id="30454-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="30454-209">Se asigna en el perfil de entrada de MRTK, en Punteros.</span><span class="sxs-lookup"><span data-stu-id="30454-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="30454-210">Puede reemplazar o personalizar este cursor por su experiencia.</span><span class="sxs-lookup"><span data-stu-id="30454-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="30454-211">Para la experiencia con la entrada de seguimiento de los ojos, MRTK también proporciona EyeGazeCursor, que tiene un objeto visual sutil para minimizar la distracción.</span><span class="sxs-lookup"><span data-stu-id="30454-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="30454-212">MRTK: perfil de puntero</span><span class="sxs-lookup"><span data-stu-id="30454-212">MRTK - Pointer profile</span></span>](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="30454-213">MRTK: sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="30454-213">MRTK - Input system</span></span>](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="30454-214">MRTK: punteros</span><span class="sxs-lookup"><span data-stu-id="30454-214">MRTK - Pointers</span></span>](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="30454-215">Consulte también</span><span class="sxs-lookup"><span data-stu-id="30454-215">See also</span></span>

* [<span data-ttu-id="30454-216">Gestos</span><span class="sxs-lookup"><span data-stu-id="30454-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="30454-217">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="30454-217">Head-gaze and commit</span></span>](gaze-and-commit.md)