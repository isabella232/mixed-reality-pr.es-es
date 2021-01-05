---
title: Entrada de voz
description: La entrada de voz es una entrada básica para los auriculares de la realidad de HoloLens y Windows Mixed Reality. Voice se puede usar para comandos, dictado, Cortana y mucho más.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, voz, Cortana, voz, entrada, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, mira fijamente
ms.openlocfilehash: 09f99083d769be80d8c15016b3de8713eae76515
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848136"
---
# <a name="voice-input"></a><span data-ttu-id="e4e5b-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="e4e5b-105">Voice input</span></span>

![Entrada de voz](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="e4e5b-107">La voz es una de las formas clave de entrada en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="e4e5b-108">Permite comandos directamente de un holograma sin tener que usar [gestos de mano](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="e4e5b-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="e4e5b-109">La entrada de voz es una manera natural de comunicar tus intenciones.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="e4e5b-110">La voz es especialmente adecuada en el recorrido de interfaces complejas, ya que permite a los usuarios cortar menús anidados con un comando.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="e4e5b-111">La entrada de voz se basa en el [mismo motor](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que admite la voz en todas las _aplicaciones universales de Windows_.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="e4e5b-112">En HoloLens, el reconocimiento de voz siempre funcionará en el idioma de visualización de Windows configurado en la configuración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="e4e5b-113">Voz y miras</span><span class="sxs-lookup"><span data-stu-id="e4e5b-113">Voice and gaze</span></span>

<span data-ttu-id="e4e5b-114">Cuando se usan comandos de voz, la punta o la vista rápida es el mecanismo de selección de destino típico, con un cursor para "seleccionar" o para canalizar el comando a una aplicación que se está viendo.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="e4e5b-115">Es posible que ni siquiera sea necesario mostrar un cursor de miración _("verlo, decirlo")_.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="e4e5b-116">Algunos comandos de voz no requieren un destino, como "ir a Inicio" o "Hola Cortana".</span><span class="sxs-lookup"><span data-stu-id="e4e5b-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="e4e5b-117">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="e4e5b-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e4e5b-118"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="e4e5b-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="e4e5b-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e4e5b-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e4e5b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e4e5b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e4e5b-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="e4e5b-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e4e5b-122">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="e4e5b-122">Voice input</span></span></td>
        <td><span data-ttu-id="e4e5b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="e4e5b-123">✔️</span></span></td>
        <td><span data-ttu-id="e4e5b-124">✔️</span><span class="sxs-lookup"><span data-stu-id="e4e5b-124">✔️</span></span></td>
        <td><span data-ttu-id="e4e5b-125">✔️ (con micrófono)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="e4e5b-126">Comando "seleccionar"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-126">The "select" command</span></span>

<span data-ttu-id="e4e5b-127">**HoloLens (1ª generación)**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="e4e5b-128">Incluso sin agregar específicamente compatibilidad con voz a su aplicación, los usuarios pueden activar los hologramas simplemente diciendo el comando de voz del sistema "Select".</span><span class="sxs-lookup"><span data-stu-id="e4e5b-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="e4e5b-129">Esto se comporta igual que una [pulsación aérea](gaze-and-commit.md#composite-gestures) en HoloLens, presionando el botón seleccionar en el [clic de hololens](https://docs.microsoft.com/hololens/hololens1-clicker)o presionando el desencadenador en un controlador de [movimiento de Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="e4e5b-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](https://docs.microsoft.com/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="e4e5b-130">Oirá un sonido y verá que aparece una información sobre herramientas con "seleccionar" como confirmación.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="e4e5b-131">"Select" está habilitado por un algoritmo de detección de palabras clave de bajo consumo, lo que significa que puede decirlo en cualquier momento con un impacto mínimo en la duración de la batería.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="e4e5b-132">Incluso puede decir "seleccionar" con sus manos en su lado.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="e4e5b-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="e4e5b-134">Para usar el comando "seleccionar" de voz en HoloLens 2, primero debe abrir el cursor de miración para usarlo como puntero.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="e4e5b-135">El comando para ponerlo al día es fácil de recordar (simplemente, por ejemplo, "Select").</span><span class="sxs-lookup"><span data-stu-id="e4e5b-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="e4e5b-136">Para salir del modo, vuelva a usar las manos con el toque de aire, cerca de un botón con los dedos o mediante el gesto del sistema.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="e4e5b-137">*Imagen: "seleccionar" para usar el comando de voz para la selección*</span><span class="sxs-lookup"><span data-stu-id="e4e5b-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Un usuario puede decir "seleccionar" para usar el comando de voz para una selección.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="e4e5b-139">Hola Cortana</span><span class="sxs-lookup"><span data-stu-id="e4e5b-139">Hey Cortana</span></span>

<span data-ttu-id="e4e5b-140">Puede decir "Hola Cortana" para abrir Cortana en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="e4e5b-141">No tiene que esperar a que parezca que sigue preguntando su pregunta o le dé una instrucción.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="e4e5b-142">Por ejemplo, intente decir "Hola a Cortana, ¿cuál es el tiempo?".</span><span class="sxs-lookup"><span data-stu-id="e4e5b-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="e4e5b-143">como una sola oración.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-143">as a single sentence.</span></span> <span data-ttu-id="e4e5b-144">Para obtener más información sobre Cortana y lo que puede hacer, pregúntele.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="e4e5b-145">Por ejemplo, "Hola Cortana, ¿qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="e4e5b-146">y desplegarán una lista de comandos de trabajo y sugeridos.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="e4e5b-147">Si ya está **en la aplicación** de Cortana, seleccione el</span><span class="sxs-lookup"><span data-stu-id="e4e5b-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="e4e5b-148">en la barra lateral para desplegar el mismo menú.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="e4e5b-149">**Comandos específicos de HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="e4e5b-150">"¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-150">"What can I say?"</span></span>
* <span data-ttu-id="e4e5b-151">"Ir a Inicio"-en lugar de a la [floración](system-gesture.md#bloom) para ir al [menú Inicio](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="e4e5b-152">"Launch <app> "</span><span class="sxs-lookup"><span data-stu-id="e4e5b-152">"Launch <app>"</span></span>
* <span data-ttu-id="e4e5b-153">"Moverse <app> aquí"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-153">"Move <app> here"</span></span>
* <span data-ttu-id="e4e5b-154">"Tomar una imagen"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-154">"Take a picture"</span></span>
* <span data-ttu-id="e4e5b-155">"Iniciar grabación"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-155">"Start recording"</span></span>
* <span data-ttu-id="e4e5b-156">"Detener grabación"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-156">"Stop recording"</span></span>
* <span data-ttu-id="e4e5b-157">"Mostrar rayo manos"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-157">"Show hand ray"</span></span>
* <span data-ttu-id="e4e5b-158">"Ocultar rayo manos"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-158">"Hide hand ray"</span></span>
* <span data-ttu-id="e4e5b-159">"Aumentar el brillo"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-159">"Increase the brightness"</span></span>
* <span data-ttu-id="e4e5b-160">"Reducir el brillo"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="e4e5b-161">"Aumentar el volumen"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-161">"Increase the volume"</span></span>
* <span data-ttu-id="e4e5b-162">"Reducir el volumen"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-162">"Decrease the volume"</span></span>
* <span data-ttu-id="e4e5b-163">"Silenciar" o "dessilenciar"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="e4e5b-164">"Apagar el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-164">"Shut down the device"</span></span>
* <span data-ttu-id="e4e5b-165">"Reiniciar el dispositivo"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-165">"Restart the device"</span></span>
* <span data-ttu-id="e4e5b-166">"Ir a suspensión"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-166">"Go to sleep"</span></span>
* <span data-ttu-id="e4e5b-167">"¿Qué hora es?"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-167">"What time is it?"</span></span>
* <span data-ttu-id="e4e5b-168">"¿Cuánta batería he dejado?"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="e4e5b-169">"Verlo, decirlo"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="e4e5b-170">HoloLens tiene un modelo "ver ti" para la entrada de voz, donde las etiquetas de los botones indican a los usuarios los comandos de voz que también pueden decir.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="e4e5b-171">Por ejemplo, al examinar una ventana de la aplicación en HoloLens (1ª generación), un usuario puede decir el comando "ajustar" para ajustar la posición de la aplicación en el mundo.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="e4e5b-172">*Imagen: un usuario puede decir el comando "ajustar", que se ve en la barra de la aplicación para ajustar la posición de la aplicación.*</span><span class="sxs-lookup"><span data-stu-id="e4e5b-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e4e5b-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="e4e5b-174">![Al mirar una ventana de la aplicación o un holograma, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="e4e5b-175">Cuando las aplicaciones siguen esta regla, los usuarios pueden comprender fácilmente qué decir para controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="e4e5b-176">Mientras Gazing en un botón de HoloLens (1ª generación), verá una información sobre herramientas de "permanencia de voz" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para hablar de ella.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="e4e5b-177">Para mostrar la información sobre herramientas de voz en HoloLens 2, muestre el cursor de voz indicando "seleccionar" o "Qué puedo decir" (vea la imagen).</span><span class="sxs-lookup"><span data-stu-id="e4e5b-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="e4e5b-178">*Imagen: "ver, por ejemplo," los comandos aparecen debajo de los botones*</span><span class="sxs-lookup"><span data-stu-id="e4e5b-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="e4e5b-180">Comandos de voz para la manipulación rápida de hologramas</span><span class="sxs-lookup"><span data-stu-id="e4e5b-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="e4e5b-181">Hay muchos comandos de voz que puede decir mientras Gazing en un holograma para realizar rápidamente tareas de manipulación.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="e4e5b-182">Estos comandos de voz funcionan en las ventanas de la aplicación y en los objetos 3D que ha colocado en el mundo.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="e4e5b-183">**Comandos de manipulación de hologramas**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="e4e5b-184">Me encuentro</span><span class="sxs-lookup"><span data-stu-id="e4e5b-184">Face me</span></span>
* <span data-ttu-id="e4e5b-185">Mayor | Enhance</span><span class="sxs-lookup"><span data-stu-id="e4e5b-185">Bigger | Enhance</span></span>
* <span data-ttu-id="e4e5b-186">Disminuye</span><span class="sxs-lookup"><span data-stu-id="e4e5b-186">Smaller</span></span>

<span data-ttu-id="e4e5b-187">En HoloLens 2, también puede crear interacciones más naturales en combinación con la mirada, que proporciona implícitamente información contextual sobre lo que se está haciendo referencia.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="e4e5b-188">Por ejemplo, podría ver un holograma y decir "colocarlo" y, a continuación, buscar _el_ lugar en el que desea colocarlo y decir " _aquí_".</span><span class="sxs-lookup"><span data-stu-id="e4e5b-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="e4e5b-189">O bien, podría ver una pieza holográfica en una máquina compleja y decir: "proporcione más información acerca de _esto_".</span><span class="sxs-lookup"><span data-stu-id="e4e5b-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="e4e5b-190">Detección de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="e4e5b-190">Discovering voice commands</span></span>

<span data-ttu-id="e4e5b-191">Algunos comandos, como los comandos para la manipulación rápida anterior, se pueden ocultar.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="e4e5b-192">Para obtener información sobre los comandos que puede usar, mira fijamente a un objeto y, por ejemplo, "¿Qué puedo decir?".</span><span class="sxs-lookup"><span data-stu-id="e4e5b-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="e4e5b-193">Aparece una lista de posibles comandos.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-193">A list of possible commands pops up.</span></span> <span data-ttu-id="e4e5b-194">También puede usar el cursor de mirar hacia abajo para buscar y mostrar la información sobre herramientas de voz de cada botón delante.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="e4e5b-195">Si desea una lista completa, simplemente indique "Mostrar todos los comandos" en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="e4e5b-196">Dictado</span><span class="sxs-lookup"><span data-stu-id="e4e5b-196">Dictation</span></span>

<span data-ttu-id="e4e5b-197">En lugar de escribir con [grifos de aire](gaze-and-commit.md#composite-gestures), el dictado de voz puede ser más eficaz para escribir texto en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="e4e5b-198">Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="e4e5b-199">![El dictado de voz comienza seleccionando el botón micrófono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="e4e5b-200">*El dictado de voz comienza seleccionando el botón micrófono del teclado.*</span><span class="sxs-lookup"><span data-stu-id="e4e5b-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="e4e5b-201">Siempre que el teclado Holographic esté activo, puede cambiar al modo de dictado en lugar de escribir.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="e4e5b-202">Seleccione el micrófono en el lateral del cuadro de entrada de texto para comenzar.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="e4e5b-203">Agregar comandos de voz a la aplicación</span><span class="sxs-lookup"><span data-stu-id="e4e5b-203">Adding voice commands to your app</span></span>

<span data-ttu-id="e4e5b-204">Considera la posibilidad de agregar comandos de voz a cualquier experiencia que compiles.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="e4e5b-205">Voice es un método eficaz para controlar el sistema y las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="e4e5b-206">Dado que los usuarios hablan con distintos tipos de dialectos y acentos, la elección adecuada de palabras clave de voz garantizará que los comandos de los usuarios se interpreten sin ambigüedades.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="e4e5b-207">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="e4e5b-207">Best practices</span></span>

<span data-ttu-id="e4e5b-208">A continuación se muestran algunas prácticas que te ayudarán a realizar sin problemas las tareas de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="e4e5b-209">**Usa comandos concisos**: cuando sea posible, elige palabras clave de dos o más sílabas.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="e4e5b-210">Las palabras de una sílaba tienden a tener diferentes pronunciaciones de las vocales dependiendo del acento de la persona.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="e4e5b-211">Ejemplo: "reproducir vídeo" es mejor que "reproducir el vídeo seleccionado actualmente"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="e4e5b-212">**Usar vocabulario simple** : por ejemplo, "show Note" es mejor que "show letrero"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="e4e5b-213">Asegúrese de que los **comandos no sean destructivos** : Asegúrese de que las acciones de comando de voz no sean destructivas y se puedan deshacer fácilmente en caso de que otra persona que hable cerca del usuario desencadene accidentalmente un comando.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="e4e5b-214">**Evite comandos de sonido similares** : Evite registrar varios comandos de voz que suenen de forma similar.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="e4e5b-215">Ejemplo: "Mostrar más" y "Mostrar tienda" puede ser similar.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="e4e5b-216">**Anular el registro de la aplicación cuando no se usa** : cuando la aplicación no se encuentra en un estado en el que un comando de voz determinado es válido, considere la posibilidad de anular el registro para que otros comandos no estén confundidos para ese.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="e4e5b-217">**Prueba con diferentes acentos**: prueba la aplicación con usuarios con diferentes acentos.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="e4e5b-218">**Mantén la coherencia en los comandos de voz**: si "Volver" va a la página anterior, mantén este comportamiento en tus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="e4e5b-219">**Evitar el uso de comandos del sistema** : los siguientes comandos de voz están reservados para el sistema, por lo que no se deben usar en las aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="e4e5b-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="e4e5b-220">"Hola Cortana"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="e4e5b-221">"Seleccionar"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-221">"Select"</span></span>
   * <span data-ttu-id="e4e5b-222">"Ir a Inicio"</span><span class="sxs-lookup"><span data-stu-id="e4e5b-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="e4e5b-223">Ventajas de la entrada de voz</span><span class="sxs-lookup"><span data-stu-id="e4e5b-223">Advantages of voice input</span></span>

<span data-ttu-id="e4e5b-224">Las entradas de voz son una manera natural de comunicar nuestras intenciones.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="e4e5b-225">La voz es especialmente útil en los **recorridos** de la interfaz, ya que puede ayudar a los usuarios a recorrer varios pasos de una interfaz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="e4e5b-226">Un usuario podría decir "volver atrás" mientras mira una página web, en lugar de tener que subir y presionar el botón atrás en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="e4e5b-227">Esta pequeña hora de guardar tiene un **efecto emocional** eficaz sobre la percepción del usuario de la experiencia y les da una pequeña cantidad de mejorar enormemente.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="e4e5b-228">El uso de la voz es también un método práctico de entrada cuando tenemos las manos ocupadas o estamos **realizando varias tareas a la vez**.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="e4e5b-229">En los dispositivos en los que es difícil escribir en un teclado, el **dictado de voz** puede ser una forma alternativa eficaz de escribir texto.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="e4e5b-230">Por último, en algunos casos en los que el **intervalo de precisión** de la mirada y el gesto es limitado, la voz puede ayudar a eliminar la ambigüedad de la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="e4e5b-231">**Cómo puede beneficiar al usuario la utilización de la voz**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="e4e5b-232">Reduce el tiempo: debe hacer que el objetivo final sea más eficaz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="e4e5b-233">Minimiza el esfuerzo: debe hacer que las tareas se realicen de forma más fluida y sin esfuerzo.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="e4e5b-234">Reduce la carga cognitiva: es una forma intuitiva y fácil de aprender y recordar.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="e4e5b-235">Es social aceptable: debe ajustarse a las normas de un comportamiento de la sociedad.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="e4e5b-236">Es fácil de convertir en rutina: puede convertirse fácilmente en un comportamiento habitual.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="e4e5b-237">Desafíos de la entrada de voz</span><span class="sxs-lookup"><span data-stu-id="e4e5b-237">Challenges for voice input</span></span>

<span data-ttu-id="e4e5b-238">Aunque la entrada de voz es excelente para muchas aplicaciones diferentes, también enfrenta varios desafíos.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="e4e5b-239">La comprensión de las ventajas y los desafíos de la entrada de voz permite a los desarrolladores de aplicaciones tomar decisiones más inteligentes sobre cómo y Cuándo usar la entrada de voz y crear una excelente experiencia para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="e4e5b-240">**Entrada de voz para el control de entrada continuo** El control específico es uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="e4e5b-241">Por ejemplo, un usuario podría querer cambiar su volumen en su aplicación de música.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="e4e5b-242">Puede decir "más alto", pero no está claro cuánto debe ser el sistema para crear el volumen.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="e4e5b-243">El usuario podría decir: "hacer que sea un poco más alto", pero "un poco" es difícil de cuantificar.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="e4e5b-244">El movimiento o el escalado de los hologramas con la voz es igualmente difícil.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="e4e5b-245">**Confiabilidad de la detección de entrada de voz** Aunque los sistemas de entrada de voz son mejores y mejores, a veces pueden oír e interpretar de forma incorrecta un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="e4e5b-246">La clave es abordar el desafío en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="e4e5b-247">Proporcione comentarios a los usuarios cuando el sistema esté escuchando y lo que el sistema entienda clarifica los posibles problemas que comprenden la voz de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="e4e5b-248">**Entrada de voz en espacios compartidos** Es posible que la voz no sea socialmente aceptable en espacios que comparta con otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="e4e5b-249">Estos son algunos ejemplos:</span><span class="sxs-lookup"><span data-stu-id="e4e5b-249">Here are a few examples:</span></span>
* <span data-ttu-id="e4e5b-250">Es posible que el usuario no quiera molestar a otros (por ejemplo, en una biblioteca tranquila o en una oficina compartida).</span><span class="sxs-lookup"><span data-stu-id="e4e5b-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="e4e5b-251">Es posible que los usuarios no se vean tan complicados como hablar en el público.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="e4e5b-252">Un usuario puede sentirse incómodo dictar un mensaje personal o confidencial (incluidas las contraseñas) mientras que otros están escuchando</span><span class="sxs-lookup"><span data-stu-id="e4e5b-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="e4e5b-253">**Entrada de voz de palabras únicas o desconocidas** Las dificultades para la entrada de voz también se muestran cuando los usuarios están dictando palabras que pueden ser desconocidas para el sistema, como sobrenombres, ciertas palabras jergas o abreviaturas.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="e4e5b-254">**Comandos de voz de aprendizaje** Aunque el objetivo final es conversar naturalmente con el sistema, a menudo las aplicaciones todavía dependen de comandos de voz específicos predefinidos.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="e4e5b-255">Un desafío asociado a un conjunto importante de comandos de voz es cómo enseñarlas sin sobrecargar al usuario y cómo ayudar al usuario a mantenerlas.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="e4e5b-256">Estados de la respuesta a la voz</span><span class="sxs-lookup"><span data-stu-id="e4e5b-256">Voice feedback states</span></span>

<span data-ttu-id="e4e5b-257">Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtiene una respuesta clara** de que el sistema **le ha oído correctamente**.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="e4e5b-258">Estas dos señales hacen que el usuario se sienta seguro utilizando la voz como entrada principal.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="e4e5b-259">A continuación se muestra un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y cómo se lo comunica al usuario.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="e4e5b-260">![1. estado normal del cursor](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="e4e5b-261">**1. estado normal del cursor**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4e5b-262">![2. comunica comentarios de voz y luego desaparece](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="e4e5b-263">**2. comunica comentarios de voz y luego desaparece**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e4e5b-264">![3.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-264">![\*3.</span></span> <span data-ttu-id="e4e5b-265">Estado normal del cursor](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="e4e5b-266">**3. vuelve al estado normal del cursor**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="e4e5b-267">Cosas principales que los usuarios deben saber sobre los comandos de voz en la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="e4e5b-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="e4e5b-268">**Suseleccione "seleccionar"** mientras el destino es un botón (puede utilizarlo en cualquier lugar para seleccionar un botón).</span><span class="sxs-lookup"><span data-stu-id="e4e5b-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="e4e5b-269">Puedes decir el **nombre de etiqueta de un botón de la barra de la aplicación** en algunas aplicaciones para realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="e4e5b-270">Por ejemplo, al mirar una aplicación, un usuario puede decir el comando "quitar" para quitar la aplicación del mundo (esto ahorra tiempo al tener que seleccionarla con la mano).</span><span class="sxs-lookup"><span data-stu-id="e4e5b-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="e4e5b-271">Puede iniciar la escucha de Cortana diciendo **"Hola Cortana".**</span><span class="sxs-lookup"><span data-stu-id="e4e5b-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="e4e5b-272">Puedes preguntarle cosas ("Hola Cortana, cuál es la altura de la torre Eiffel"), decirle que abra una aplicación ("Hola Cortana, abre Netflix") o que abra el menú Inicio ("Hola Cortana, llévame al principio") y mucho más.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="e4e5b-273">Preguntas y dudas comunes que tienen los usuarios acerca del uso de la voz</span><span class="sxs-lookup"><span data-stu-id="e4e5b-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="e4e5b-274">What can I say? (¿Qué puedo decir?)</span><span class="sxs-lookup"><span data-stu-id="e4e5b-274">What can I say?</span></span>
* <span data-ttu-id="e4e5b-275">¿Cómo sé si el sistema me escuchó correctamente?</span><span class="sxs-lookup"><span data-stu-id="e4e5b-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="e4e5b-276">El sistema se equivoca todo el tiempo con mis comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="e4e5b-277">No reacciona cuando digo un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="e4e5b-278">Reacciona de forma equivocada cuando digo un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="e4e5b-279">¿Cómo dirijo mi voz a una aplicación o un comando de la aplicación específicos?</span><span class="sxs-lookup"><span data-stu-id="e4e5b-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="e4e5b-280">¿Puedo usar la voz para comandar cosas en el marco holográfico en HoloLens?</span><span class="sxs-lookup"><span data-stu-id="e4e5b-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="e4e5b-281">Comunicación</span><span class="sxs-lookup"><span data-stu-id="e4e5b-281">Communication</span></span>

<span data-ttu-id="e4e5b-282">En el caso de las aplicaciones que desean aprovechar las opciones de procesamiento de entrada de audio personalizadas proporcionadas por HoloLens, es importante comprender las distintas [categorías de flujo de audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que puede consumir la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="e4e5b-283">Windows 10 admite varias categorías de secuencias diferentes y HoloLens usa tres de ellas para habilitar el procesamiento personalizado con el fin de optimizar la calidad de audio del micrófono adaptada a la voz, la comunicación y otros, que se pueden usar para los escenarios de captura de audio de entorno ambiente (es decir, "videocámara").</span><span class="sxs-lookup"><span data-stu-id="e4e5b-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="e4e5b-284">La categoría AudioCategory_Communications Stream está personalizada para escenarios de calidad y narración de llamadas y proporciona al cliente una secuencia de audio mono de 16 bits de 16 kHz de la voz del usuario</span><span class="sxs-lookup"><span data-stu-id="e4e5b-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="e4e5b-285">La categoría AudioCategory_Speech Stream está personalizada para el motor de voz de HoloLens (Windows) y le proporciona una secuencia mono de 16 kHz de 24 bits de la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="e4e5b-286">Los motores de voz de terceros pueden usar esta categoría si es necesario.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="e4e5b-287">La categoría AudioCategory_Other Stream está personalizada para la grabación de audio del entorno ambiente y proporciona al cliente una secuencia de audio estéreo de 24 bits 48 kHz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="e4e5b-288">Todo este procesamiento de audio se acelera en hardware, lo que significa que las características agotan una gran cantidad de energía que si se realizara el mismo procesamiento en la CPU de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="e4e5b-289">Evite ejecutar otro procesamiento de entrada de audio en la CPU para maximizar la duración de la batería del sistema y aprovechar el procesamiento de entrada de audio descargado integrado.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="e4e5b-290">Idiomas</span><span class="sxs-lookup"><span data-stu-id="e4e5b-290">Languages</span></span>

<span data-ttu-id="e4e5b-291">HoloLens 2 [es compatible con varios idiomas](https://docs.microsoft.com/hololens/hololens2-language-support).</span><span class="sxs-lookup"><span data-stu-id="e4e5b-291">HoloLens 2 [supports multiple languages](https://docs.microsoft.com/hololens/hololens2-language-support).</span></span> <span data-ttu-id="e4e5b-292">Tenga en cuenta que los comandos de voz siempre se ejecutarán en el idioma para mostrar del sistema aunque se instalen varios teclados o cuando las aplicaciones intenten crear un reconocedor de voz en otro idioma.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e4e5b-293">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="e4e5b-293">Troubleshooting</span></span>

<span data-ttu-id="e4e5b-294">Si tiene algún problema con "Select" y "Hola Cortana", intente cambiar a un espacio más silencioso, desplazarse fuera del origen del ruido o hablar de más alto.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="e4e5b-295">En este momento, todo el reconocimiento de voz en HoloLens se ajusta y optimiza específicamente a los hablantes nativos de Estados Unidos inglés.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="e4e5b-296">En el caso de la versión 2017 de Windows Mixed Reality Developer Edition, la lógica de administración de puntos de conexión de audio funcionará bien (siempre) después de cerrar la sesión y volver a iniciarla en el escritorio del equipo después de la conexión inicial de HMD.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="e4e5b-297">Antes de que el primer evento de cierre de sesión o de salida después de pasar a WMR OOBE, el usuario podría experimentar varios problemas de funcionalidad de audio que van desde sin audio hasta sin conmutación de audio, en función de cómo se haya configurado el sistema antes de conectarse a HMD por primera vez.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e4e5b-298">Entrada de voz en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="e4e5b-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e4e5b-299">Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, puede asignar fácilmente comandos de voz en cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="e4e5b-300">Use el **Perfil de entrada de voz** de MRTK para definir sus palabras clave.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="e4e5b-301">Mediante la asignación del script **SpeechInputHandler** , puede hacer que cualquier objeto responda a las palabras clave definidas en el perfil de entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="e4e5b-302">SpeechInputHandler también proporciona una etiqueta de confirmación de voz para mejorar la confianza del usuario.</span><span class="sxs-lookup"><span data-stu-id="e4e5b-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="e4e5b-303">Comando MRTK-Voice</span><span class="sxs-lookup"><span data-stu-id="e4e5b-303">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)

---

## <a name="see-also"></a><span data-ttu-id="e4e5b-304">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e4e5b-304">See also</span></span>

* [<span data-ttu-id="e4e5b-305">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="e4e5b-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e4e5b-306">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="e4e5b-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e4e5b-307">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="e4e5b-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="e4e5b-308">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="e4e5b-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)
