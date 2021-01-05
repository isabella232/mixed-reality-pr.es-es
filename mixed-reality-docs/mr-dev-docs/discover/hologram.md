---
title: ¿Qué es un holograma?
description: HoloLens le permite ver e interactuar con hologramas tridimensionales, objetos de luz y sonido que aparecen en el mundo.
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologramas, diseño, interacción, auriculares de realidad mixta, auriculares Windows Mixed Reality, qué es realidad aumentada
ms.openlocfilehash: b390910fcece8e6263d19f52c80b784efb2561f6
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757563"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="6fac2-104">¿Qué es un holograma?</span><span class="sxs-lookup"><span data-stu-id="6fac2-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="6fac2-105">HoloLens le permite crear **hologramas**, que son objetos de luz y sonido que aparecen en el mundo como objetos reales.</span><span class="sxs-lookup"><span data-stu-id="6fac2-105">HoloLens lets you create **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="6fac2-106">Los hologramas responden a los comandos de [mirados](../design/gaze-and-commit.md), [gestos](../design/gaze-and-commit.md#composite-gestures)y [voz](../design/voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="6fac2-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="6fac2-107">Incluso pueden interactuar con las [superficies del mundo real](../design/spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="6fac2-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="6fac2-108">Con los hologramas, puedes crear objetos digitales que formen parte de tu mundo.</span><span class="sxs-lookup"><span data-stu-id="6fac2-108">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="6fac2-109">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="6fac2-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6fac2-110"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="6fac2-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6fac2-111"><a href="../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6fac2-111"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6fac2-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6fac2-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6fac2-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="6fac2-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6fac2-114">Hologramas</span><span class="sxs-lookup"><span data-stu-id="6fac2-114">Holograms</span></span></td>
        <td><span data-ttu-id="6fac2-115">✔️</span><span class="sxs-lookup"><span data-stu-id="6fac2-115">✔️</span></span></td>
        <td><span data-ttu-id="6fac2-116">✔️</span><span class="sxs-lookup"><span data-stu-id="6fac2-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="6fac2-117">Un holograma se compone de luz y sonido</span><span class="sxs-lookup"><span data-stu-id="6fac2-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="6fac2-118">Los hologramas que HoloLens [representa](../develop/platform-capabilities-and-apis/rendering.md) aparecen en el marco holográfica directamente delante de los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="6fac2-118">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="6fac2-119">Los hologramas agregan luz a su mundo, lo que significa que puede ver la luz de la pantalla y la luz de su entorno.</span><span class="sxs-lookup"><span data-stu-id="6fac2-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="6fac2-120">HoloLens no quita la luz de los ojos, por lo que los hologramas no se pueden representar con el color negro.</span><span class="sxs-lookup"><span data-stu-id="6fac2-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="6fac2-121">En su lugar, el contenido negro aparece como transparente.</span><span class="sxs-lookup"><span data-stu-id="6fac2-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="6fac2-122">Los hologramas pueden tener muchos comportamientos y apariencias diferentes.</span><span class="sxs-lookup"><span data-stu-id="6fac2-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="6fac2-123">Algunos son reales y sólidos, mientras que otros están animados y Ethereal.</span><span class="sxs-lookup"><span data-stu-id="6fac2-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="6fac2-124">Puede usar hologramas para resaltar características en su entorno o usarlas como elementos en la interfaz de usuario de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6fac2-124">You can use holograms to highlight features in your surroundings or use them as elements in your app's user interface.</span></span>

![Manos de la manipulación de un holograma](images/hologram-hands-940px.jpg)

<span data-ttu-id="6fac2-126">Los hologramas también pueden hacer [sonidos](../design/spatial-sound.md), que parecerá que provienen de un lugar específico del entorno.</span><span class="sxs-lookup"><span data-stu-id="6fac2-126">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="6fac2-127">En HoloLens, el sonido procede de dos altavoces que se encuentran directamente encima de sus oídos, sin cubrirlos.</span><span class="sxs-lookup"><span data-stu-id="6fac2-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="6fac2-128">De forma similar a las pantallas, los oradores son aditivos, introduciendo nuevos sonidos sin bloquear los sonidos de su entorno.</span><span class="sxs-lookup"><span data-stu-id="6fac2-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="6fac2-129">Se puede colocar un holograma en el mundo o etiqueta junto con usted</span><span class="sxs-lookup"><span data-stu-id="6fac2-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="6fac2-130">Si tiene una ubicación determinada para un holograma, puede [colocarla](../design/coordinate-systems.md) precisamente en ese punto del mundo.</span><span class="sxs-lookup"><span data-stu-id="6fac2-130">When you have a particular location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="6fac2-131">A medida que recorre, el holograma parece estable en función del mundo.</span><span class="sxs-lookup"><span data-stu-id="6fac2-131">As you walk around, the hologram appears stable based on the world around you.</span></span> <span data-ttu-id="6fac2-132">Si usa un [delimitador espacial](../design/coordinate-systems.md#spatial-anchors) para anclar el objeto, el sistema puede incluso recordar dónde lo dejó cuando vuelva más tarde.</span><span class="sxs-lookup"><span data-stu-id="6fac2-132">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Dos hombres con el diseño de Microsoft Dynamics 365 en un espacio comercial](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="6fac2-134">Algunos hologramas siguen al usuario en su lugar, se colocan en función del usuario, independientemente de dónde se recorran.</span><span class="sxs-lookup"><span data-stu-id="6fac2-134">Some holograms follow the user instead, positioning themselves based on the user no matter where they walk.</span></span> <span data-ttu-id="6fac2-135">Incluso puede optar por un holograma y colocarlo en la pared una vez que llegue a otra habitación.</span><span class="sxs-lookup"><span data-stu-id="6fac2-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="6fac2-136">**procedimientos recomendados**</span><span class="sxs-lookup"><span data-stu-id="6fac2-136">**Best practices**</span></span>
* <span data-ttu-id="6fac2-137">Algunos escenarios pueden exigir que los hologramas se mantengan fácilmente reconocibles o visibles a lo largo de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="6fac2-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="6fac2-138">Hay dos enfoques de alto nivel para este tipo de posicionamiento.</span><span class="sxs-lookup"><span data-stu-id="6fac2-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="6fac2-139">Vamos a llamarlos **"display-locked"** y **"Body-locked"**.</span><span class="sxs-lookup"><span data-stu-id="6fac2-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="6fac2-140">Mostrar el contenido bloqueado está "bloqueado" en la pantalla del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6fac2-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="6fac2-141">Este tipo de contenido es complicado por varios motivos, por ejemplo, una sensación poco natural de "clingyness" que hace que muchos usuarios se sienten frustrados y quieran "sacudirlo".</span><span class="sxs-lookup"><span data-stu-id="6fac2-141">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="6fac2-142">En general, muchos diseñadores lo han descubierto mejor para evitar el contenido de bloqueo de pantalla.</span><span class="sxs-lookup"><span data-stu-id="6fac2-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="6fac2-143">El enfoque de cuerpo bloqueado es mucho más forgivable.</span><span class="sxs-lookup"><span data-stu-id="6fac2-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="6fac2-144">El bloqueo de cuerpo es cuando se ancla un holograma al cuerpo del usuario o al vector de miración en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="6fac2-144">Body-locking is when you tether a hologram to the user's body or gaze vector in 3d space.</span></span> <span data-ttu-id="6fac2-145">Muchas experiencias han adoptado un comportamiento de bloqueo de cuerpo en el que el holograma "sigue" a los usuarios mirados, lo que permite al usuario girar su cuerpo y desplazarse por el espacio sin perder el holograma.</span><span class="sxs-lookup"><span data-stu-id="6fac2-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="6fac2-146">Incorporar un retraso ayuda a que el movimiento de hologramas parezca más natural.</span><span class="sxs-lookup"><span data-stu-id="6fac2-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="6fac2-147">Por ejemplo, algunas interfaces de usuario principales del sistema operativo Holographic de Windows usan una variación en el bloqueo del cuerpo que sigue al mirador con un retraso suave y elástico mientras el usuario cambia la cabeza.</span><span class="sxs-lookup"><span data-stu-id="6fac2-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="6fac2-148">Coloque el holograma con una distancia de visualización cómoda normalmente de aproximadamente 1-2 metros de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="6fac2-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="6fac2-149">Proporcione una cantidad de desplazamiento para los elementos que deben estar continuamente en el marco holográfica, o considere la posibilidad de animar el contenido a un lado de la pantalla cuando el usuario cambie su punto de vista.</span><span class="sxs-lookup"><span data-stu-id="6fac2-149">Provide a drift amount for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="6fac2-150">**Colocar hologramas en la zona óptima: entre 1,25 m y 5 m**</span><span class="sxs-lookup"><span data-stu-id="6fac2-150">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="6fac2-151">Dos medidores son los más óptimos y la experiencia se degradará cuanto más se aproxime de 1 metro.</span><span class="sxs-lookup"><span data-stu-id="6fac2-151">Two meters is the most optimal, and the experience will degrade the closer you get from 1 meter.</span></span> <span data-ttu-id="6fac2-152">En distancias más cerca de un medidor, los hologramas que se mueven con frecuencia son más probables que sean problemáticos que los hologramas estacionarios.</span><span class="sxs-lookup"><span data-stu-id="6fac2-152">At distances nearer than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="6fac2-153">Considere la posibilidad de recortar o difuminar correctamente el contenido cuando se acerque demasiado, de modo que no se determine el usuario en una experiencia inesperada.</span><span class="sxs-lookup"><span data-stu-id="6fac2-153">Consider gracefully clipping or fading out your content when it gets too close so you don't jar the user into an unexpected experience.</span></span>

![Distancia óptima para colocar hologramas del usuario.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="6fac2-155">Un holograma interactúa con usted y su mundo</span><span class="sxs-lookup"><span data-stu-id="6fac2-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="6fac2-156">Los hologramas no solo están relacionados con la luz y el sonido; también son una parte activa de su mundo.</span><span class="sxs-lookup"><span data-stu-id="6fac2-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="6fac2-157">Mira un holograma y gesto con la mano y un holograma puede empezar a seguirlo.</span><span class="sxs-lookup"><span data-stu-id="6fac2-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="6fac2-158">Asigne un comando de voz a un holograma y puede responder.</span><span class="sxs-lookup"><span data-stu-id="6fac2-158">Give a voice command to a hologram, and it can reply.</span></span>

![Grupo de trabajadores de la utilidad gubernamental con Microsoft HoloLens 2 para colaborar en un proyecto de desarrollo de la granja de Wind](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="6fac2-160">Los hologramas permiten interacciones personales que no son posibles en ningún otro lugar.</span><span class="sxs-lookup"><span data-stu-id="6fac2-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="6fac2-161">Dado que HoloLens sabe dónde se encuentra en el mundo, un personaje Holographic puede tener una apariencia directa en los ojos mientras se recorre la habitación.</span><span class="sxs-lookup"><span data-stu-id="6fac2-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="6fac2-162">Un holograma también puede interactuar con su entorno.</span><span class="sxs-lookup"><span data-stu-id="6fac2-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="6fac2-163">Por ejemplo, puede colocar una bola de rebote holográfica sobre una tabla.</span><span class="sxs-lookup"><span data-stu-id="6fac2-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="6fac2-164">A continuación, con una [pulsación aérea](../design/gaze-and-commit.md#composite-gestures), vea el rebote de la bola y cree un sonido cuando llegue a la tabla.</span><span class="sxs-lookup"><span data-stu-id="6fac2-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound when it hits the table.</span></span>

<span data-ttu-id="6fac2-165">Los hologramas también pueden ser ocluidosdos por objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="6fac2-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="6fac2-166">Por ejemplo, un personaje Holographic podría recorrer una puerta y detrás de una pared, fuera de la vista.</span><span class="sxs-lookup"><span data-stu-id="6fac2-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="6fac2-167">**Sugerencias para la integración de hologramas y el mundo real**</span><span class="sxs-lookup"><span data-stu-id="6fac2-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="6fac2-168">La alineación de las reglas de Gravitational hace que los hologramas sean más fáciles de relacionar con y más increíble.</span><span class="sxs-lookup"><span data-stu-id="6fac2-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="6fac2-169">por ejemplo: ponga un perro holográfica en el suelo & un jarrón en la tabla en lugar de hacer que floten en el espacio.</span><span class="sxs-lookup"><span data-stu-id="6fac2-169">for example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="6fac2-170">Muchos diseñadores han descubierto que pueden integrar hologramas más increíble mediante la creación de una "sombra negativa" en la superficie en la que está sentado el holograma.</span><span class="sxs-lookup"><span data-stu-id="6fac2-170">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="6fac2-171">Para ello, se crea un resplandor blando en torno al holograma y, a continuación, se resta la "sombra" del resplandor.</span><span class="sxs-lookup"><span data-stu-id="6fac2-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="6fac2-172">El resplandor suave se integra con la luz del mundo real, que usa la sombra para el holograma en el entorno.</span><span class="sxs-lookup"><span data-stu-id="6fac2-172">The soft glow integrates with the light from the real world, which uses the shadow to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="6fac2-173">Un holograma es el</span><span class="sxs-lookup"><span data-stu-id="6fac2-173">A hologram is whatever</span></span> <br><span data-ttu-id="6fac2-174">puede soñar</span><span class="sxs-lookup"><span data-stu-id="6fac2-174">you can dream up</span></span><br>
        <span data-ttu-id="6fac2-175">Como desarrollador de Holographic, tiene la posibilidad de descomponer su creatividad de pantallas 2D y en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="6fac2-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="6fac2-176">¿Qué *va a compilar* ?</span><span class="sxs-lookup"><span data-stu-id="6fac2-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6fac2-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6fac2-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6fac2-178">![Mundo imaginario Holographic en salón](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="6fac2-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="6fac2-179">Siguiente punto de comprobación de detección</span><span class="sxs-lookup"><span data-stu-id="6fac2-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="6fac2-180">Si está siguiendo el [recorrido de detección](get-started-with-mr.md) hemos diseñado, está a mitad de explorar los aspectos básicos de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6fac2-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="6fac2-181">Desde aquí, puede continuar con el siguiente tema básico:</span><span class="sxs-lookup"><span data-stu-id="6fac2-181">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="6fac2-182">Ampliar el proceso de diseño</span><span class="sxs-lookup"><span data-stu-id="6fac2-182">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)

