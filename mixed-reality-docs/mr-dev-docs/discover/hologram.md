---
title: ¿Qué es un holograma?
description: HoloLens permite ver e interactuar con hologramas tridimensionales, objetos hechos de luz y sonido que aparecen en el mundo que le rodea.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologramas, diseño, interacción, cascos de realidad mixta, cascos de realidad mixta de Windows, ¿qué es la realidad aumentada?
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634336"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="3a677-104">¿Qué es un holograma?</span><span class="sxs-lookup"><span data-stu-id="3a677-104">What is a hologram?</span></span>

<span data-ttu-id="3a677-105">HoloLens permite ver **hologramas,** que son objetos de luz y sonido que aparecen en el mundo que le rodea, como objetos reales.</span><span class="sxs-lookup"><span data-stu-id="3a677-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="3a677-106">Hologramas responder a los comandos [de](../design/gaze-and-commit.md)mirada, [gestos](../design/gaze-and-commit.md#composite-gestures) [y voz](../design/voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="3a677-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="3a677-107">Incluso pueden interactuar con [superficies del mundo real](../design/spatial-mapping.md) a su alrededor.</span><span class="sxs-lookup"><span data-stu-id="3a677-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="3a677-108">Hologramas son objetos digitales que forman parte de su mundo.</span><span class="sxs-lookup"><span data-stu-id="3a677-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="3a677-109">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="3a677-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3a677-110"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="3a677-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3a677-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3a677-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3a677-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3a677-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3a677-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="3a677-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3a677-114">Hologramas</span><span class="sxs-lookup"><span data-stu-id="3a677-114">Holograms</span></span></td>
        <td><span data-ttu-id="3a677-115">✔️</span><span class="sxs-lookup"><span data-stu-id="3a677-115">✔️</span></span></td>
        <td><span data-ttu-id="3a677-116">✔️</span><span class="sxs-lookup"><span data-stu-id="3a677-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="3a677-117">Un holograma está hecho de luz y sonido</span><span class="sxs-lookup"><span data-stu-id="3a677-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="3a677-118">Claro</span><span class="sxs-lookup"><span data-stu-id="3a677-118">Light</span></span>

<span data-ttu-id="3a677-119">Los hologramas que HoloLens [representan](../develop/platform-capabilities-and-apis/rendering.md) aparecen en el marco holográfico directamente delante de los ojos de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="3a677-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="3a677-120">Hologramas agregar luz a su mundo, lo que significa que verá tanto la luz de la pantalla como la luz del mundo circundante.</span><span class="sxs-lookup"><span data-stu-id="3a677-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="3a677-121">Puesto HoloLens una pantalla de suma que agrega luz, el color negro se representará de forma transparente.</span><span class="sxs-lookup"><span data-stu-id="3a677-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="3a677-122">Hologramas pueden tener apariencias y comportamientos muy diferentes.</span><span class="sxs-lookup"><span data-stu-id="3a677-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="3a677-123">Algunas son realistas y sólidas, y otras son resaltes y etéreas.</span><span class="sxs-lookup"><span data-stu-id="3a677-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="3a677-124">Puede usar hologramas para resaltar las características de su entorno o usarlas como elementos en la interfaz de usuario de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3a677-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![Manos que manipulan un holograma](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="3a677-126">Sonido</span><span class="sxs-lookup"><span data-stu-id="3a677-126">Sound</span></span>

<span data-ttu-id="3a677-127">Hologramas también puede generar [sonidos](../design/spatial-sound.md), que parecen procedentes de un lugar específico de su entorno.</span><span class="sxs-lookup"><span data-stu-id="3a677-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="3a677-128">En HoloLens, el sonido procede de dos altavoces que se encuentran directamente encima de los oídos.</span><span class="sxs-lookup"><span data-stu-id="3a677-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="3a677-129">Igual que las pantallas holográficas, los altavoces son aditivos, lo que introduce sonidos nuevos sin bloquear los sonidos del entorno.</span><span class="sxs-lookup"><span data-stu-id="3a677-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="3a677-130">Se puede colocar un holograma en el mundo o etiquetar junto con usted</span><span class="sxs-lookup"><span data-stu-id="3a677-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="3a677-131">Si tiene una ubicación fija para un holograma, [puede](../design/coordinate-systems.md) colocarlo con precisión en ese punto del mundo.</span><span class="sxs-lookup"><span data-stu-id="3a677-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="3a677-132">A medida que se desenlace, el holograma aparece insaltez en función del mundo que le rodea, al igual que un objeto físico.</span><span class="sxs-lookup"><span data-stu-id="3a677-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="3a677-133">Si usa un delimitador [espacial](../design/coordinate-systems.md#spatial-anchors) para anclar el objeto, el sistema incluso puede recordar dónde lo dejó cuando vuelva más tarde.</span><span class="sxs-lookup"><span data-stu-id="3a677-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Dos hombres que usan el diseño de Microsoft Dynamics 365 en un espacio comercial](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="3a677-135">En su lugar, algunos hologramas siguen al usuario.</span><span class="sxs-lookup"><span data-stu-id="3a677-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="3a677-136">Se posicionan en función del usuario.</span><span class="sxs-lookup"><span data-stu-id="3a677-136">They position themselves based on the user.</span></span> <span data-ttu-id="3a677-137">Puede elegir llevar un holograma con usted y colocarlo en la pared una vez que llegue a otra habitación.</span><span class="sxs-lookup"><span data-stu-id="3a677-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="3a677-138">**procedimientos recomendados**</span><span class="sxs-lookup"><span data-stu-id="3a677-138">**Best practices**</span></span>

* <span data-ttu-id="3a677-139">Algunos escenarios exigen que los hologramas permanezcan fácilmente reconocibles o visibles a lo largo de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="3a677-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="3a677-140">Hay dos enfoques de alto nivel para este tipo de posicionamiento.</span><span class="sxs-lookup"><span data-stu-id="3a677-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="3a677-141">Vamos a llamarlos **display-locked** y **body-locked**.</span><span class="sxs-lookup"><span data-stu-id="3a677-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="3a677-142">**El contenido bloqueado para** mostrar está bloqueado en el dispositivo de visualización.</span><span class="sxs-lookup"><span data-stu-id="3a677-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="3a677-143">Este tipo de contenido es complicado por varias razones, incluida una sensación poco natural de "clingyness" que hace que muchos usuarios se sientan frustrados y quieran "apagarlo".</span><span class="sxs-lookup"><span data-stu-id="3a677-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="3a677-144">En general, los diseñadores han descubierto que es mejor evitar el contenido de bloqueo de pantalla.</span><span class="sxs-lookup"><span data-stu-id="3a677-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="3a677-145">**El contenido bloqueado en** el cuerpo puede ser mucho más forzante.</span><span class="sxs-lookup"><span data-stu-id="3a677-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="3a677-146">El bloqueo del cuerpo es cuando se tete un holograma al cuerpo del usuario o al vector de mirada en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="3a677-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="3a677-147">Muchas experiencias han adoptado un comportamiento de bloqueo del cuerpo en el que el holograma sigue la mirada del usuario, lo que permite al usuario girar su cuerpo y desplazarse por el espacio sin perder el holograma.</span><span class="sxs-lookup"><span data-stu-id="3a677-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="3a677-148">La incorporación de un retraso ayuda a que los movimientos del holograma se sientan más naturales.</span><span class="sxs-lookup"><span data-stu-id="3a677-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="3a677-149">Por ejemplo, alguna interfaz de usuario principal del sistema operativo Windows Holographic usa una variación en el bloqueo de cuerpo que sigue la mirada del usuario con un retraso suave y elástico mientras el usuario se vuelve la cabeza.</span><span class="sxs-lookup"><span data-stu-id="3a677-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="3a677-150">Coloque el holograma a una distancia de visualización cómoda, normalmente a unos 1-2 metros de distancia de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="3a677-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="3a677-151">Permita que los elementos se desenlacen si deben estar continuamente en el marco holográfico, o considere la posibilidad de mover el contenido a un lado de la pantalla cuando el usuario cambie su punto de vista.</span><span class="sxs-lookup"><span data-stu-id="3a677-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="3a677-152">Para obtener más información, consulte la técnica [de](../design/billboarding-and-tag-along.md) etiquetado y etiquetado.</span><span class="sxs-lookup"><span data-stu-id="3a677-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="3a677-153">**Colocar hologramas en la zona óptima: entre 1,25 m y 5 m**</span><span class="sxs-lookup"><span data-stu-id="3a677-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="3a677-154">Dos metros es la distancia de visualización más óptima.</span><span class="sxs-lookup"><span data-stu-id="3a677-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="3a677-155">La experiencia comenzará a degradarse a medida que se acerque a más de 1 metro.</span><span class="sxs-lookup"><span data-stu-id="3a677-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="3a677-156">A distancias inferiores a 1 metro, es más probable que los hologramas que se mueven con regularidad en profundidad sean problemáticos que los hologramas estacionados.</span><span class="sxs-lookup"><span data-stu-id="3a677-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="3a677-157">Considere la posibilidad de recortar o desvanejar correctamente el contenido cuando se acerca demasiado, por lo que no se convierte al usuario en una experiencia de visualización agradable.</span><span class="sxs-lookup"><span data-stu-id="3a677-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![Distancia óptima para colocar hologramas del usuario.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="3a677-159">Un holograma interactúa con usted y con su mundo</span><span class="sxs-lookup"><span data-stu-id="3a677-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="3a677-160">Hologramas no solo se trata de la luz y el sonido; también son una parte activa de su mundo.</span><span class="sxs-lookup"><span data-stu-id="3a677-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="3a677-161">Mire un holograma y un gesto con la mano, y un holograma puede empezar a seguirle.</span><span class="sxs-lookup"><span data-stu-id="3a677-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="3a677-162">Dé un comando de voz y el holograma puede responder.</span><span class="sxs-lookup"><span data-stu-id="3a677-162">Give a voice command, and the hologram can reply.</span></span>

![Grupo de trabajadores de la utilidad pública que usan Microsoft HoloLens 2 para colaborar en un proyecto de desarrollo de granjas eólicas](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="3a677-164">Hologramas habilitar interacciones personales que no son posibles en otra parte.</span><span class="sxs-lookup"><span data-stu-id="3a677-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="3a677-165">Dado que HoloLens sabe dónde está en el mundo, un carácter holográfico puede mirarle directamente a los ojos e iniciar una conversación con usted.</span><span class="sxs-lookup"><span data-stu-id="3a677-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="3a677-166">Un holograma también puede interactuar con su entorno.</span><span class="sxs-lookup"><span data-stu-id="3a677-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="3a677-167">Por ejemplo, puede colocar una bola holográfica sobre una tabla.</span><span class="sxs-lookup"><span data-stu-id="3a677-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="3a677-168">A continuación, con [una pulsación](../design/gaze-and-commit.md#composite-gestures)en el aire, observe el salto de la bola y haga sonido a medida que llega a la tabla.</span><span class="sxs-lookup"><span data-stu-id="3a677-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="3a677-169">Hologramas objetos del mundo real también pueden oclusión.</span><span class="sxs-lookup"><span data-stu-id="3a677-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="3a677-170">Por ejemplo, un carácter holográfico podría atravesar una puerta y detrás de una pared, fuera de la vista.</span><span class="sxs-lookup"><span data-stu-id="3a677-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="3a677-171">**Sugerencias para integrar hologramas y el mundo real**</span><span class="sxs-lookup"><span data-stu-id="3a677-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="3a677-172">La alineación con las reglas de reanidad hace que los hologramas sean más fáciles de relacionar y más fáciles de relacionar.</span><span class="sxs-lookup"><span data-stu-id="3a677-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="3a677-173">Por ejemplo: coloque un perro holográfico en el suelo & un jarrón en la tabla en lugar de hacer que flotan en el espacio.</span><span class="sxs-lookup"><span data-stu-id="3a677-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="3a677-174">Muchos diseñadores han descubierto que pueden integrar hologramas más reconocibles mediante la creación de una "sombra negativa" en la superficie en la que se encuentra el holograma.</span><span class="sxs-lookup"><span data-stu-id="3a677-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="3a677-175">Para ello, crean un brillo suave en el suelo alrededor del holograma y, a continuación, restan la "sombra" del brillo.</span><span class="sxs-lookup"><span data-stu-id="3a677-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="3a677-176">El brillo suave se integra con la luz del mundo real.</span><span class="sxs-lookup"><span data-stu-id="3a677-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="3a677-177">La sombra se usa para dar tierra al holograma en el entorno.</span><span class="sxs-lookup"><span data-stu-id="3a677-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="3a677-178">Un holograma es lo que</span><span class="sxs-lookup"><span data-stu-id="3a677-178">A hologram is what</span></span> <br><span data-ttu-id="3a677-179">puede soñar</span><span class="sxs-lookup"><span data-stu-id="3a677-179">you can dream up</span></span><br>
        <span data-ttu-id="3a677-180">Como desarrollador holográfico, tiene la capacidad de dividir su creatividad en pantallas 2D y en el mundo que le rodea.</span><span class="sxs-lookup"><span data-stu-id="3a677-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="3a677-181">¿Qué *compilará?*</span><span class="sxs-lookup"><span data-stu-id="3a677-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3a677-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3a677-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3a677-183">![Mundo imaginario holográfico en la sala de estar](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="3a677-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="3a677-184">Siguiente punto de comprobación de detección</span><span class="sxs-lookup"><span data-stu-id="3a677-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="3a677-185">Está en el recorrido [de detección](get-started-with-mr.md) que hemos diseñado y explorando los conceptos básicos de Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3a677-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="3a677-186">Desde aquí, puede continuar con el siguiente tema básico:</span><span class="sxs-lookup"><span data-stu-id="3a677-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a677-187">Ampliar el proceso de diseño</span><span class="sxs-lookup"><span data-stu-id="3a677-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)