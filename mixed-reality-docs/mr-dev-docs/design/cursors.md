---
title: Cursores
description: Un cursor, o indicador del vector de destino, proporciona comentarios continuos para que el usuario comprenda lo que HoloLens entiende sobre sus intenciones.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª generación), HoloLens 2, realidad mixta, cursores, destinatarios, mirados, gestos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, rayos, entrada
ms.openlocfilehash: 3d1bc215f7f5c37f1c2c3ae33c3bc2e4031b354a
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848001"
---
# <a name="cursors"></a><span data-ttu-id="d5c98-104">Cursores</span><span class="sxs-lookup"><span data-stu-id="d5c98-104">Cursors</span></span>

![Cursores](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="d5c98-106">Un cursor proporciona comentarios continuos basados en el lugar en que el casco cree que el foco actual de los usuarios se encuentra en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="d5c98-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="d5c98-107">Los comentarios del cursor incluyen el área, el holograma o el punto del entorno virtual que responde a la entrada.</span><span class="sxs-lookup"><span data-stu-id="d5c98-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="d5c98-108">Aunque el cursor es una representación digital del lugar en el que el dispositivo entiende la atención del usuario, no es lo mismo que determinar las intenciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="d5c98-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="d5c98-109">Los comentarios del cursor también permiten a los usuarios saber qué respuestas del sistema se esperan.</span><span class="sxs-lookup"><span data-stu-id="d5c98-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="d5c98-110">Puede usar los comentarios para comunicar su intención al dispositivo, lo que aumenta la confianza del usuario.</span><span class="sxs-lookup"><span data-stu-id="d5c98-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="d5c98-111">Hay 3 tipos de cursores: **Finger, Ray** y **Head-mirate**.</span><span class="sxs-lookup"><span data-stu-id="d5c98-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="d5c98-112">Estos cursores de señalización funcionan con diferentes modalidades de entrada en HoloLens, HoloLens 2 y auriculares envolvente.</span><span class="sxs-lookup"><span data-stu-id="d5c98-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="d5c98-113">A continuación se ofrecen instrucciones sobre qué tipo de cursor se debe utilizar para cada tipo de auriculares y modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="d5c98-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="d5c98-114">En el kit de herramientas de realidad mixta (MRTK), hemos creado módulos de cursores de arrastrar y colocar para ayudarle a crear la experiencia adecuada.</span><span class="sxs-lookup"><span data-stu-id="d5c98-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="d5c98-115">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="d5c98-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d5c98-116"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="d5c98-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d5c98-117"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d5c98-117"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d5c98-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d5c98-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d5c98-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="d5c98-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d5c98-120">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="d5c98-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="d5c98-121">✔️</span><span class="sxs-lookup"><span data-stu-id="d5c98-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="d5c98-122">Cursor de rayo</span><span class="sxs-lookup"><span data-stu-id="d5c98-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="d5c98-123">✔️</span><span class="sxs-lookup"><span data-stu-id="d5c98-123">✔️</span></span></td>
        <td><span data-ttu-id="d5c98-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d5c98-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d5c98-125">Cursor de miras hacia abajo</span><span class="sxs-lookup"><span data-stu-id="d5c98-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="d5c98-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d5c98-126">✔️</span></span></td>
        <td><span data-ttu-id="d5c98-127">✔️</span><span class="sxs-lookup"><span data-stu-id="d5c98-127">✔️</span></span></td>
        <td><span data-ttu-id="d5c98-128">✔️</span><span class="sxs-lookup"><span data-stu-id="d5c98-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="d5c98-129">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="d5c98-129">Finger cursor</span></span>

<span data-ttu-id="d5c98-130">El cursor de dedo solo está disponible en HoloLens 2 para mejorar el modo de interacción "[manipulación directa con manos](direct-manipulation.md)".</span><span class="sxs-lookup"><span data-stu-id="d5c98-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="d5c98-131">Hemos adjuntado anillos a las sugerencias de ambos dedos de índice para comprender mejor Dónde está señalando el dedo.</span><span class="sxs-lookup"><span data-stu-id="d5c98-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="d5c98-132">El tamaño del anillo se basa en la proximidad del dedo a la superficie de la interfaz de usuario, que se reduce a un punto pequeño cuando el dedo toca la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="d5c98-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="d5c98-133">Cuanto más se acerque el dedo, menor será el anillo.</span><span class="sxs-lookup"><span data-stu-id="d5c98-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="d5c98-134">![cursor de dedo](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="d5c98-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="d5c98-135">**Estados de comentarios visuales del cursor de dedo** 1: el anillo se reduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="d5c98-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="d5c98-136">2: el anillo se alinea con la superficie.</span><span class="sxs-lookup"><span data-stu-id="d5c98-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="d5c98-137">3: el anillo es perpendicular al vector de dedo.</span><span class="sxs-lookup"><span data-stu-id="d5c98-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="d5c98-138">4: sin anillo.</span><span class="sxs-lookup"><span data-stu-id="d5c98-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="d5c98-139">Cursor de rayo</span><span class="sxs-lookup"><span data-stu-id="d5c98-139">Ray cursor</span></span>

<span data-ttu-id="d5c98-140">Los cursores de rayo se adjuntan al final de los rayos que apuntan mucho para permitir la manipulación de objetos que no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="d5c98-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="d5c98-141">En los auriculares envolventes, los rayos salen de los controladores de movimiento y finalizan los cursores de punto.</span><span class="sxs-lookup"><span data-stu-id="d5c98-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="d5c98-142">En HoloLens 2, se aplica el modelo mental de estos rayos de controlador de movimiento y se diseñan rayos de mano que se originan a partir de las palmeras y se acaban en cursores en forma de anillo que son coherentes con los cursores de dedo utilizados en la manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="d5c98-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="d5c98-143">![Controlador de cursor de rayo](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="d5c98-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="d5c98-144">**Cursores de rayo de controladores de movimiento**</span><span class="sxs-lookup"><span data-stu-id="d5c98-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d5c98-145">![Mano de cursor de rayo](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="d5c98-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="d5c98-146">**Cursores de rayo de manos**</span><span class="sxs-lookup"><span data-stu-id="d5c98-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="d5c98-147">Cursor de miras hacia abajo</span><span class="sxs-lookup"><span data-stu-id="d5c98-147">Head-gaze cursor</span></span>

<span data-ttu-id="d5c98-148">El cursor de mira hacia abajo es un punto que se adjunta al final de un vector de miras hacia arriba invisible que usa la posición y la rotación del encabezado al punto.</span><span class="sxs-lookup"><span data-stu-id="d5c98-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="d5c98-149">Para ejecutar acciones, este cursor señalador se empareja con varias entradas de confirmación, como la pulsación de aire, los comandos de voz, la permanencia y la pulsación de botones.</span><span class="sxs-lookup"><span data-stu-id="d5c98-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="d5c98-150">En HoloLens 2, el encabezado de la mirada es mejor con cualquier entrada de confirmación que no se pulse en el aire, ya que habrá un conflicto de interacción entre la derivación del aire y los rayos de mano.</span><span class="sxs-lookup"><span data-stu-id="d5c98-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="d5c98-151">![Mano de cursor de mira](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="d5c98-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="d5c98-152">**Cursor de mira hacia abajo con el gesto de mano**</span><span class="sxs-lookup"><span data-stu-id="d5c98-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d5c98-153">![Voz de cursor de mirada](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="d5c98-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="d5c98-154">**Cursor de mira hacia abajo con el comando de voz**</span><span class="sxs-lookup"><span data-stu-id="d5c98-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="d5c98-155">Recomendaciones de personalización de cursores</span><span class="sxs-lookup"><span data-stu-id="d5c98-155">Cursor customization recommendations</span></span>

<span data-ttu-id="d5c98-156">Si desea personalizar los comportamientos y los aspectos de los comentarios del cursor, estas son algunas recomendaciones de diseño:</span><span class="sxs-lookup"><span data-stu-id="d5c98-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="d5c98-157">Escala del cursor</span><span class="sxs-lookup"><span data-stu-id="d5c98-157">Cursor scale</span></span>

* <span data-ttu-id="d5c98-158">El cursor no debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar fácilmente con el contenido y verlo.</span><span class="sxs-lookup"><span data-stu-id="d5c98-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="d5c98-159">Dependiendo de la experiencia que cree, el escalado del cursor a medida que el usuario busca también es una consideración importante.</span><span class="sxs-lookup"><span data-stu-id="d5c98-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="d5c98-160">Por ejemplo, a medida que el usuario mira mejor su experiencia, el cursor no debe ser demasiado pequeño, por lo que se pierde.</span><span class="sxs-lookup"><span data-stu-id="d5c98-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="d5c98-161">Al escalar el cursor, considere la posibilidad de aplicarle una animación de software a medida que se escale para darle una sensación orgánica.</span><span class="sxs-lookup"><span data-stu-id="d5c98-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="d5c98-162">Evite obstruir el contenido.</span><span class="sxs-lookup"><span data-stu-id="d5c98-162">Avoid obstructing content.</span></span> <span data-ttu-id="d5c98-163">Los hologramas son lo que hacen que la experiencia sea memorable y el cursor no debe apartarse de ellas.</span><span class="sxs-lookup"><span data-stu-id="d5c98-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="d5c98-164">Forma cursor no direccional</span><span class="sxs-lookup"><span data-stu-id="d5c98-164">Directionless cursor shape</span></span>

* <span data-ttu-id="d5c98-165">Aunque no hay una forma de cursor derecha, se recomienda usar una forma sin dirección como un toro.</span><span class="sxs-lookup"><span data-stu-id="d5c98-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="d5c98-166">Un cursor que apunta en alguna dirección (por ejemplo, un cursor de flecha tradicional) puede confundir al usuario para que siempre mire ese modo.</span><span class="sxs-lookup"><span data-stu-id="d5c98-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="d5c98-167">Una excepción a esto es cuando se usa el cursor para comunicar la instrucción de interacción al usuario.</span><span class="sxs-lookup"><span data-stu-id="d5c98-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="d5c98-168">Por ejemplo, al escalar los hologramas en el sistema operativo de realidad mixta, el cursor incluye de forma temporal flechas que indican al usuario Cómo trasladar la mano para escalar el holograma.</span><span class="sxs-lookup"><span data-stu-id="d5c98-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="d5c98-169">Apariencia y funcionamiento</span><span class="sxs-lookup"><span data-stu-id="d5c98-169">Look and feel</span></span>

* <span data-ttu-id="d5c98-170">Un anillo o cursor con forma de aro funciona para muchas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d5c98-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="d5c98-171">Elija un color y una forma que mejor represente la experiencia que está creando.</span><span class="sxs-lookup"><span data-stu-id="d5c98-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="d5c98-172">Los cursores son especialmente propensos a la [separación de colores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="d5c98-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="d5c98-173">Un cursor pequeño con opacidad equilibrada mantiene informativa sin dominar la jerarquía visual.</span><span class="sxs-lookup"><span data-stu-id="d5c98-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="d5c98-174">Tenga en Cognizant el uso de sombras o resaltados detrás del cursor, ya que podrían obstruir el contenido y distraerse de la tarea a mano.</span><span class="sxs-lookup"><span data-stu-id="d5c98-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="d5c98-175">Los cursores deben alinearse con las superficies de la aplicación y Hug.</span><span class="sxs-lookup"><span data-stu-id="d5c98-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="d5c98-176">Los usuarios tendrán la sensación de que el sistema puede ver dónde están buscando, pero también que el sistema es consciente de su entorno.</span><span class="sxs-lookup"><span data-stu-id="d5c98-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="d5c98-177">Por ejemplo, el cursor en el sistema operativo de realidad mixta se alinea con las superficies del mundo del usuario, lo que crea un sentimiento de sensibilización del mundo incluso cuando el usuario no está mirando directamente a un holograma.</span><span class="sxs-lookup"><span data-stu-id="d5c98-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="d5c98-178">El bloqueo magnético del cursor en un elemento interactivo cuando está cerca del usuario puede ayudar a mejorar la confianza de que el usuario interactuará con ese elemento cuando use una acción de selección.</span><span class="sxs-lookup"><span data-stu-id="d5c98-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="d5c98-179">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="d5c98-179">Visual cues</span></span>

* <span data-ttu-id="d5c98-180">Si su experiencia se centra en un solo holograma, el cursor debe alinearse y Hug solo ese holograma y cambiar de forma cuando mira el holograma.</span><span class="sxs-lookup"><span data-stu-id="d5c98-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="d5c98-181">Esto puede transmitir al usuario que el holograma es accionable y puede interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="d5c98-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="d5c98-182">Si la aplicación usa la asignación espacial, el cursor podría alinear y Hug cada superficie que ve.</span><span class="sxs-lookup"><span data-stu-id="d5c98-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="d5c98-183">Esto proporciona comentarios a los usuarios de que HoloLens y su aplicación pueden ver su espacio.</span><span class="sxs-lookup"><span data-stu-id="d5c98-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="d5c98-184">Esto refuerza el hecho de que los hologramas son reales y en nuestro mundo y ayudan a salvar la brecha entre real y virtual.</span><span class="sxs-lookup"><span data-stu-id="d5c98-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="d5c98-185">Tenga una idea de lo que debe hacer el cursor cuando no haya ningún holograma o superficie en la vista.</span><span class="sxs-lookup"><span data-stu-id="d5c98-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="d5c98-186">Colocarlo a una distancia predeterminada delante del usuario es una opción.</span><span class="sxs-lookup"><span data-stu-id="d5c98-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="d5c98-187">Acciones posibles</span><span class="sxs-lookup"><span data-stu-id="d5c98-187">Possible actions</span></span>

* <span data-ttu-id="d5c98-188">El cursor se puede representar mediante iconos diferentes para transmitir posibles acciones que puede realizar un holograma, como el escalado o la rotación.</span><span class="sxs-lookup"><span data-stu-id="d5c98-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="d5c98-189">Agregue solo información adicional sobre el cursor si significa algo al usuario.</span><span class="sxs-lookup"><span data-stu-id="d5c98-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="d5c98-190">De lo contrario, es posible que los usuarios no perciban los cambios de estado u obtengan una confusión con el cursor.</span><span class="sxs-lookup"><span data-stu-id="d5c98-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="d5c98-191">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="d5c98-191">Input state</span></span>

* <span data-ttu-id="d5c98-192">Podríamos usar el cursor para mostrar el estado de entrada o la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="d5c98-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="d5c98-193">Por ejemplo, podríamos mostrar un icono que indica al usuario que el sistema ve su estado de mano y que la aplicación sabe que está listo para tomar medidas.</span><span class="sxs-lookup"><span data-stu-id="d5c98-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="d5c98-194">También podríamos usar el cursor para mostrar a los usuarios que el sistema ha escuchado comandos de voz a través de un cambio de color momentáneo</span><span class="sxs-lookup"><span data-stu-id="d5c98-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="d5c98-195">Los siguientes Estados de cursor se pueden implementar de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="d5c98-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="d5c98-196">Puede implementar estos Estados diferentes modelando el cursor como una máquina de Estados.</span><span class="sxs-lookup"><span data-stu-id="d5c98-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="d5c98-197">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d5c98-197">For example:</span></span>
    * <span data-ttu-id="d5c98-198">Estado de inactividad es donde se muestra el cursor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="d5c98-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="d5c98-199">El estado listo es cuando ha detectado la mano del usuario en la posición listo.</span><span class="sxs-lookup"><span data-stu-id="d5c98-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="d5c98-200">El estado de interacción es cuando el usuario realiza una interacción determinada.</span><span class="sxs-lookup"><span data-stu-id="d5c98-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="d5c98-201">El estado de las acciones posibles o el estado de desplazamiento es cuando se transmiten las posibles acciones que se pueden realizar en un holograma.</span><span class="sxs-lookup"><span data-stu-id="d5c98-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="d5c98-202">También puede implementar estos Estados de forma que pueda mostrar los distintos activos gráficos cuando detecte Estados diferentes.</span><span class="sxs-lookup"><span data-stu-id="d5c98-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="d5c98-203">"Sin cursor"</span><span class="sxs-lookup"><span data-stu-id="d5c98-203">Going "cursor-free"</span></span>

<span data-ttu-id="d5c98-204">Se recomienda diseñar sin un cursor cuando el sentido de la inmersión es un componente clave de una experiencia y cuando las interacciones que señalan (a través de la mirada y el gesto) no requieren una gran precisión.</span><span class="sxs-lookup"><span data-stu-id="d5c98-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="d5c98-205">El sistema aún debe cumplir los requisitos normales de un cursor: proporcionar a los usuarios comentarios continuos sobre el conocimiento del sistema y ayudarles a comunicar sus intenciones al sistema.</span><span class="sxs-lookup"><span data-stu-id="d5c98-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="d5c98-206">Esto puede ser factible a través de otros cambios de estado perceptibles.</span><span class="sxs-lookup"><span data-stu-id="d5c98-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d5c98-207">Cursor en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="d5c98-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="d5c98-208">De forma predeterminada, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona un cursor recurso prefabricado ([DefaultCursor. recurso prefabricado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tiene el mismo estado visual que el cursor del sistema del shell.</span><span class="sxs-lookup"><span data-stu-id="d5c98-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="d5c98-209">Se asigna en el perfil de entrada de MRTK, en punteros.</span><span class="sxs-lookup"><span data-stu-id="d5c98-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="d5c98-210">Puede reemplazar o personalizar este cursor para su experiencia.</span><span class="sxs-lookup"><span data-stu-id="d5c98-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="d5c98-211">Para la experiencia con la entrada de seguimiento ocular, MRTK también proporciona EyeGazeCursor, que tiene un efecto visual sutil para minimizar la distracción.</span><span class="sxs-lookup"><span data-stu-id="d5c98-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="d5c98-212">MRTK: perfil de puntero</span><span class="sxs-lookup"><span data-stu-id="d5c98-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="d5c98-213">MRTK: sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="d5c98-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="d5c98-214">MRTK: punteros</span><span class="sxs-lookup"><span data-stu-id="d5c98-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="d5c98-215">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d5c98-215">See also</span></span>

* [<span data-ttu-id="d5c98-216">Gestos</span><span class="sxs-lookup"><span data-stu-id="d5c98-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="d5c98-217">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="d5c98-217">Head-gaze and commit</span></span>](gaze-and-commit.md)
