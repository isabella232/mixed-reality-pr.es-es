---
title: Manos libres
description: Obtenga información acerca de las dificultades a las que pueden encontrarse los usuarios con una interfaz de manos y controladores y sobre diversas alternativas gratuitas.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realidad mixta, manos libres, miradas a la mano, la interacción, el diseño, el casco de realidad mixta, el casco de la realidad mixta de Windows, el casco de realidad virtual, HoloLens, MRTK, el kit de herramientas de realidad mixta, la entrada de voz, la facilidad de uso
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847678"
---
# <a name="hands-free"></a><span data-ttu-id="8877b-104">Manos libres</span><span class="sxs-lookup"><span data-stu-id="8877b-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="8877b-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="8877b-105">Scenarios</span></span>

<span data-ttu-id="8877b-106">Tal como se describe en [información general sobre el modelo de interacción](interaction-fundamentals.md), una vez que haya identificado los usuarios y sus objetivos, pregúntese qué desafíos ambientales o en situaciones pueden enfrentarse a medida que trabajan para realizar sus tareas.</span><span class="sxs-lookup"><span data-stu-id="8877b-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you've identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="8877b-107">Por ejemplo, muchos usuarios necesitan usar sus manos para lograr sus objetivos del mundo real y tienen dificultades para interactuar con una interfaz basada en manos y controladores.</span><span class="sxs-lookup"><span data-stu-id="8877b-107">For example, many users need to use their hands to accomplish their real-world goals, and they'll have difficulty interacting with a hands-and-controllers based interface.</span></span>

<span data-ttu-id="8877b-108">Algunos escenarios específicos incluyen:</span><span class="sxs-lookup"><span data-stu-id="8877b-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="8877b-109">Guiar al usuario por una tarea mientras tiene las manos ocupadas.</span><span class="sxs-lookup"><span data-stu-id="8877b-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="8877b-110">Consultar materiales mientras el usuario tiene las manos ocupadas.</span><span class="sxs-lookup"><span data-stu-id="8877b-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="8877b-111">Fatiga manual.</span><span class="sxs-lookup"><span data-stu-id="8877b-111">Hand fatigue</span></span>
* <span data-ttu-id="8877b-112">Guantes en los que no se puede realizar un seguimiento.</span><span class="sxs-lookup"><span data-stu-id="8877b-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="8877b-113">Llevar algo en las manos.</span><span class="sxs-lookup"><span data-stu-id="8877b-113">Carrying something in their hands</span></span>
* <span data-ttu-id="8877b-114">Awkwardness social al usar gestos de gran tamaño</span><span class="sxs-lookup"><span data-stu-id="8877b-114">Social awkwardness when using large hand gestures</span></span>
* <span data-ttu-id="8877b-115">Espacios estrechos.</span><span class="sxs-lookup"><span data-stu-id="8877b-115">Tight spaces</span></span>

## <a name="hands-free-modalities"></a><span data-ttu-id="8877b-116">Modalidades de manos libres</span><span class="sxs-lookup"><span data-stu-id="8877b-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="8877b-117">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="8877b-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="8877b-118">El uso de la voz para el comando y el control de una interfaz ofrece una manera cómoda de trabajar de forma gratuita y usar accesos directos para omitir varios pasos si lo desea.</span><span class="sxs-lookup"><span data-stu-id="8877b-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to skip multiple steps if you want.</span></span> <span data-ttu-id="8877b-119">Con la entrada de voz, el usuario puede leer el nombre de cualquier botón en voz alta para activarlo _("verlo, decirlo")_ y conversar con un agente digital que puede realizar tareas por usted.</span><span class="sxs-lookup"><span data-stu-id="8877b-119">With voice input, the user can read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>

### <a name="gaze-and-dwell"></a>[<span data-ttu-id="8877b-120">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="8877b-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="8877b-121">En algunas situaciones sin experiencia, el uso de la voz no es lo ideal o incluso posible.</span><span class="sxs-lookup"><span data-stu-id="8877b-121">In some hands-free situations, using your voice isn't ideal or even possible.</span></span> <span data-ttu-id="8877b-122">Los entornos de fábrica, la privacidad o las normas sociales de alta carga pueden ser restricciones.</span><span class="sxs-lookup"><span data-stu-id="8877b-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="8877b-123">El modelo de vista y la vivienda permite al usuario navegar por una aplicación sin ninguna información adicional aparte de su ojo o mirarnos: el usuario simplemente mantiene Gazing (con sus cabezales o ojos) en el destino y permanece en él durante un momento para activarlo.</span><span class="sxs-lookup"><span data-stu-id="8877b-123">The gaze + dwell model allows the user to navigate an app without any extra input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="8877b-124">Para obtener más información acerca de las consideraciones de diseño individuales para mirarlas y la vivienda, eche [un vistazo a la vista de miras + la vivienda](gaze-and-dwell-eyes.md) y [el cabezal y la vivienda](gaze-and-dwell-head.md).</span><span class="sxs-lookup"><span data-stu-id="8877b-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="8877b-125">Transición dentro y fuera de manos libres</span><span class="sxs-lookup"><span data-stu-id="8877b-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="8877b-126">En estos casos, la liberación de las manos de la interacción con los hologramas para la navegación y los comandos puede abarcar de ser un requisito absoluto para el funcionamiento de la aplicación, de un extremo a otro, a una mayor comodidad en la que el usuario puede realizar la transición en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="8877b-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="8877b-127">Si la aplicación requiere que siempre se use de forma gratuita, ya sea mediante la permanencia, comandos de voz personalizados o el único comando de voz, "seleccionar", asegúrese de tomar las adaptaciones adecuadas en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="8877b-127">If the application requires that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="8877b-128">Si el usuario de destino tiene que cambiar de manos libres a su discreción, es importante tener en cuenta los siguientes principios.</span><span class="sxs-lookup"><span data-stu-id="8877b-128">If your target user needs to switch from hands to hands-free at their discretion, then it's important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="8877b-129">Supongamos que el usuario ya está en el modo al que desea cambiar</span><span class="sxs-lookup"><span data-stu-id="8877b-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="8877b-130">Por ejemplo, si el usuario está en la fábrica, viendo una referencia de vídeo en su HoloLens y decide tomar una llave para empezar a trabajar, lo más probable es que comience a trabajar en manos libres sin tener que dejar la llave inglesa para presionar un botón.</span><span class="sxs-lookup"><span data-stu-id="8877b-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="8877b-131">Puede invocar una sesión de voz con un comando de voz, hospedar en una interfaz de usuario ya visible para comenzar la permanencia o decir la palabra "seleccionar".</span><span class="sxs-lookup"><span data-stu-id="8877b-131">She can invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="8877b-132">El usuario puede:</span><span class="sxs-lookup"><span data-stu-id="8877b-132">The user can:</span></span> 
* <span data-ttu-id="8877b-133">Cambiar a manos libres sin manos libres</span><span class="sxs-lookup"><span data-stu-id="8877b-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="8877b-134">Cambiar a manos con las manos</span><span class="sxs-lookup"><span data-stu-id="8877b-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="8877b-135">Cambiar al controlador mediante un controlador</span><span class="sxs-lookup"><span data-stu-id="8877b-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="8877b-136">Crear formas redundantes de cambiar de modo</span><span class="sxs-lookup"><span data-stu-id="8877b-136">Create redundant ways to switch modes</span></span>

<span data-ttu-id="8877b-137">Aunque el primer principio es acerca del acceso, el segundo es acerca de la disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="8877b-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="8877b-138">No debe haber una única manera de pasar de un modo a otro.</span><span class="sxs-lookup"><span data-stu-id="8877b-138">There shouldn't just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="8877b-139">Algunos ejemplos serían:</span><span class="sxs-lookup"><span data-stu-id="8877b-139">Some examples would be:</span></span> 
* <span data-ttu-id="8877b-140">Un botón para iniciar las interacciones de voz</span><span class="sxs-lookup"><span data-stu-id="8877b-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="8877b-141">Un comando de voz para realizar la transición a, con el encabezado de la mirada y la vivienda</span><span class="sxs-lookup"><span data-stu-id="8877b-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="8877b-142">Agregar un guion de series</span><span class="sxs-lookup"><span data-stu-id="8877b-142">Add a dash of drama</span></span>

<span data-ttu-id="8877b-143">Un cambio de modo es un gran negocio.</span><span class="sxs-lookup"><span data-stu-id="8877b-143">A mode switch is a big deal.</span></span> <span data-ttu-id="8877b-144">Es importante que cuando estas transiciones sucedan que se trata de un modificador explícito, incluso un cambio drástico, para que el usuario sepa lo que ha sucedido.</span><span class="sxs-lookup"><span data-stu-id="8877b-144">It's important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 

## <a name="usability-checklist"></a><span data-ttu-id="8877b-145">Lista de comprobación de usabilidad</span><span class="sxs-lookup"><span data-stu-id="8877b-145">Usability checklist</span></span>

<span data-ttu-id="8877b-146">**¿Puede el usuario hacer todo lo posible y todo lo que sea gratuito?**</span><span class="sxs-lookup"><span data-stu-id="8877b-146">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="8877b-147">Cada interactúable debe ser accesible sin complicaciones</span><span class="sxs-lookup"><span data-stu-id="8877b-147">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="8877b-148">Asegúrese de que haya un reemplazo para todos los gestos personalizados, como el cambio de tamaño, la colocación, los deslizamientos, los grifos, etc.</span><span class="sxs-lookup"><span data-stu-id="8877b-148">Ensure that there's a replacement for all custom gestures, such as resizing, placing, swipes, taps, and so on.</span></span>
* <span data-ttu-id="8877b-149">Asegúrese de que el usuario tiene el control seguro de la presencia de la interfaz de usuario, la ubicación y el nivel de detalle siempre</span><span class="sxs-lookup"><span data-stu-id="8877b-149">Ensure that the user has confident control of UI presence, placement, and verbosity always</span></span>
    * <span data-ttu-id="8877b-150">Sacar la interfaz de usuario del camino</span><span class="sxs-lookup"><span data-stu-id="8877b-150">Getting UI out of the way</span></span>
    * <span data-ttu-id="8877b-151">Interfaz de usuario de direccionamiento fuera del campo de vista (campo de campo)</span><span class="sxs-lookup"><span data-stu-id="8877b-151">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="8877b-152">¿Cuánto veo, dónde?</span><span class="sxs-lookup"><span data-stu-id="8877b-152">How much I see, where, when</span></span>

<span data-ttu-id="8877b-153">**¿La mecánica de la interacción se enseña y se refuerza con las prestaciones adecuadas?**</span><span class="sxs-lookup"><span data-stu-id="8877b-153">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="8877b-154">¿Entiende el usuario...</span><span class="sxs-lookup"><span data-stu-id="8877b-154">Does the user understand ...</span></span>
* <span data-ttu-id="8877b-155">... ¿En qué modo se encuentran?</span><span class="sxs-lookup"><span data-stu-id="8877b-155">... What mode they are in?</span></span>
* <span data-ttu-id="8877b-156">... ¿Qué pueden hacer en este modo?</span><span class="sxs-lookup"><span data-stu-id="8877b-156">... What they can do in this mode?</span></span>
* <span data-ttu-id="8877b-157">... ¿Cuál es el estado actual?</span><span class="sxs-lookup"><span data-stu-id="8877b-157">... What is the current state?</span></span>
* <span data-ttu-id="8877b-158">... ¿Cómo pueden realizar la transición?</span><span class="sxs-lookup"><span data-stu-id="8877b-158">... How they can transition out?</span></span>
    
<span data-ttu-id="8877b-159">**¿La interfaz de usuario está optimizada para manos libres?**</span><span class="sxs-lookup"><span data-stu-id="8877b-159">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="8877b-160">Ejemplo: las prestaciones de permanencia no están integradas en patrones 2D típicos</span><span class="sxs-lookup"><span data-stu-id="8877b-160">Example: Dwell affordances aren't built in to typical 2D patterns</span></span>
* <span data-ttu-id="8877b-161">Ejemplo: el destinatario de la voz es mejor con el resaltado de objetos</span><span class="sxs-lookup"><span data-stu-id="8877b-161">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="8877b-162">Ejemplo: las interacciones de voz son mejores con títulos que se deben activar</span><span class="sxs-lookup"><span data-stu-id="8877b-162">Example: Voice interactions are better with captions that need to be turned on</span></span>

## <a name="see-also"></a><span data-ttu-id="8877b-163">Consulte también</span><span class="sxs-lookup"><span data-stu-id="8877b-163">See also</span></span>

* [<span data-ttu-id="8877b-164">Seguimiento de los ojos en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8877b-164">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="8877b-165">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="8877b-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8877b-166">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="8877b-166">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="8877b-167">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="8877b-167">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8877b-168">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="8877b-168">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="8877b-169">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="8877b-169">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="8877b-170">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="8877b-170">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="8877b-171">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="8877b-171">Voice input</span></span>](voice-input.md)
