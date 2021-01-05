---
title: Mirada con la cabeza y permanencia
description: Introducción al modelo de entrada de mirada con la cabeza y permanencia
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Realidad mixta, miradas, viviendas, interacción, diseño, auriculares de realidad mixta, auriculares Windows Mixed Reality, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, experiencia de usuario, directrices, vista de lista
ms.openlocfilehash: 060d78ec629905ac9f2134851998ec131d85f0cd
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847368"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="05f63-104">Mirada con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="05f63-104">Head-gaze and dwell</span></span>

<span data-ttu-id="05f63-105">Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible.</span><span class="sxs-lookup"><span data-stu-id="05f63-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="05f63-106">Los comandos de voz, al igual que los gestos, pueden ser poco fiables en determinados contextos, por ejemplo en condiciones de ruido excesivamente alto.</span><span class="sxs-lookup"><span data-stu-id="05f63-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="05f63-107">Además, aún no se ha generalizado el uso de la voz para controlar equipos, aunque claramente está ganando popularidad.</span><span class="sxs-lookup"><span data-stu-id="05f63-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="05f63-108">El mecanismo de mirada con la cabeza y permanencia es el más conocido y fácil de dominar para trabajar con visualización frontal y manos libres en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="05f63-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="05f63-109">Además, el modelo de mirada con la cabeza y permanencia es completamente fiable, independientemente de las interferencias de ruido o las restricciones de silencio del entorno operativo.</span><span class="sxs-lookup"><span data-stu-id="05f63-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="05f63-110">Escenarios</span><span class="sxs-lookup"><span data-stu-id="05f63-110">Scenarios</span></span>

<span data-ttu-id="05f63-111">La mirada y la vivienda son excelentes en escenarios en los que las manos de una persona están ocupadas por otras tareas.</span><span class="sxs-lookup"><span data-stu-id="05f63-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="05f63-112">La característica también es útil cuando la voz no es 100% confiable o disponible debido a restricciones ambientales o sociales.</span><span class="sxs-lookup"><span data-stu-id="05f63-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="05f63-113">Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil.</span><span class="sxs-lookup"><span data-stu-id="05f63-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="05f63-114">Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor.</span><span class="sxs-lookup"><span data-stu-id="05f63-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="05f63-115">En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="05f63-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="05f63-116">El encabezado y la vivienda permiten a la persona que usa HoloLens navegar por confianza su material de referencia sin interrumpir su flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="05f63-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="05f63-117">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="05f63-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05f63-118"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="05f63-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="05f63-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="05f63-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="05f63-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="05f63-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="05f63-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="05f63-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05f63-122">Mirada con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="05f63-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="05f63-123">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="05f63-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="05f63-124">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="05f63-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="05f63-125">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="05f63-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="05f63-126">Principios de diseño</span><span class="sxs-lookup"><span data-stu-id="05f63-126">Design principles</span></span>

<span data-ttu-id="05f63-127">**Evitar miradas a discreción**</span><span class="sxs-lookup"><span data-stu-id="05f63-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="05f63-128">El modelo de mirada con la cabeza y permanencia requiere información visual para ser intuitivo, pero demasiada información puede resultar estresante.</span><span class="sxs-lookup"><span data-stu-id="05f63-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="05f63-129">Los comentarios deben ayudar a un usuario a saber lo que tienen como destino, pero no seleccionarlo para su intención.</span><span class="sxs-lookup"><span data-stu-id="05f63-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="05f63-130">Al leer texto, iconos y etiquetas, debe proporcionar tiempo a los usuarios para absorber la información antes de seleccionarla.</span><span class="sxs-lookup"><span data-stu-id="05f63-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="05f63-131">**Buscar una velocidad adecuada**</span><span class="sxs-lookup"><span data-stu-id="05f63-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="05f63-132">Las interacciones de permanencia pueden tener distintos temporizadores, en función del impacto de la navegación. Para las funciones frecuentes, suele ser mejor un tiempo de relleno más rápido, mientras que para las funciones relevantes suele resultar mejor un tiempo de relleno más prolongado.</span><span class="sxs-lookup"><span data-stu-id="05f63-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="05f63-133">Si se usa un efecto de relleno para mostrar estos temporizadores, las curvas de animación del color de relleno pueden influir positivamente para transmitir una sensación de tiempo de relleno más rápido.</span><span class="sxs-lookup"><span data-stu-id="05f63-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="05f63-134">Debe prestarse especial atención para permitir al usuario decidir si cambiar a velocidad de relleno rápida, media o lenta.</span><span class="sxs-lookup"><span data-stu-id="05f63-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="05f63-135">**Evitar el efecto yo-yo**</span><span class="sxs-lookup"><span data-stu-id="05f63-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="05f63-136">El efecto yo-yo es un patrón incómodo de movimiento de cabeza que se produce cuando la colocación del contenido y los controles de cabeza y vista del cabezal y la vivienda obligan a las personas a buscarse y reducirse repetidamente.</span><span class="sxs-lookup"><span data-stu-id="05f63-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="05f63-137">Por ejemplo, una lista de navegación con el botón de AvPág y el botón de permanencia en la parte inferior induce un bucle de-mirar a la vivienda, buscar en los resultados, buscar en la vivienda, etc.</span><span class="sxs-lookup"><span data-stu-id="05f63-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="05f63-138">El patrón resultante es inestable, por lo que se recomienda colocar los controles de navegación en una ubicación centralizada que requiera menos.</span><span class="sxs-lookup"><span data-stu-id="05f63-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="05f63-139">La colocación de los botones de permanencia en función de sus efectos es importante para la comodidad.</span><span class="sxs-lookup"><span data-stu-id="05f63-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="05f63-140">s</span><span class="sxs-lookup"><span data-stu-id="05f63-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="05f63-141">Directrices y procedimientos recomendados para la experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="05f63-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="05f63-142">Tamaños de los destinos</span><span class="sxs-lookup"><span data-stu-id="05f63-142">Target sizes</span></span>

<span data-ttu-id="05f63-143">Para que se pueda acceder fácilmente, los objetivos de la vista de cabeza y de la vivienda deben ser lo suficientemente grandes como para examinarlos de forma cómoda y mantener una ventaja estable en el destino durante el tiempo previsto.</span><span class="sxs-lookup"><span data-stu-id="05f63-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="05f63-144">Se recomienda un tamaño mínimo de destino de 2 grados para lograr la experiencia más cómoda.</span><span class="sxs-lookup"><span data-stu-id="05f63-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="05f63-145">Información visual</span><span class="sxs-lookup"><span data-stu-id="05f63-145">Visual feedback</span></span>

<span data-ttu-id="05f63-146">Al utilizar un relleno radial para representar el temporizador de permanencia, empieza desde el centro del botón.</span><span class="sxs-lookup"><span data-stu-id="05f63-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="05f63-147">Una respuesta coherente es menos confusa que si cada botón tiene una dirección distinta.</span><span class="sxs-lookup"><span data-stu-id="05f63-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="05f63-148">Esta regla se puede romper a pesar de las interacciones direccionales (por ejemplo, NAV arriba/abajo/izquierda/derecha, etc.).</span><span class="sxs-lookup"><span data-stu-id="05f63-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="05f63-149">Por ejemplo, Microsoft Dynamics 365 Guides hace una excepción para los botones SIGUIENTE/ATRÁS, que son rellenos de izquierda y derecha.</span><span class="sxs-lookup"><span data-stu-id="05f63-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="05f63-150">Considere la posibilidad de invertir el relleno radial desde fuera, en escenarios como la alternancia de un botón.</span><span class="sxs-lookup"><span data-stu-id="05f63-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="05f63-151">La sensación inversa a pulsar un botón es un patrón visual que resulta útil mantener.</span><span class="sxs-lookup"><span data-stu-id="05f63-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="05f63-152">Muestra progresiva</span><span class="sxs-lookup"><span data-stu-id="05f63-152">Progressive disclosure</span></span>

<span data-ttu-id="05f63-153">La muestra progresiva significa que solo se muestran los detalles pertinentes en cada etapa de una interacción.</span><span class="sxs-lookup"><span data-stu-id="05f63-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="05f63-154">En el caso de la vivienda, esto significa que el destino de la vivienda se revela en el resaltado (por ejemplo, en un control de lista).</span><span class="sxs-lookup"><span data-stu-id="05f63-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="05f63-155">Objetivos demasiado grandes</span><span class="sxs-lookup"><span data-stu-id="05f63-155">Oversized targets</span></span>

<span data-ttu-id="05f63-156">La región de permanencia puede ser mayor que el icono inactivo para que resulte más fácil de usar, al igual que el botón Atrás en Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="05f63-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="05f63-157">Evitar el parpadeo con información retrasada</span><span class="sxs-lookup"><span data-stu-id="05f63-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="05f63-158">Utiliza un breve retraso antes de iniciar la información visual para evitar el parpadeo cuando un usuario pase sobre un objetivo de permanencia.</span><span class="sxs-lookup"><span data-stu-id="05f63-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="05f63-159">En el caso de los botones interactivos con frecuencia, mantenga el retraso corto para que la aplicación se sienta reactiva.</span><span class="sxs-lookup"><span data-stu-id="05f63-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="05f63-160">En el caso de los botones que se interactúan con poca frecuencia, un retraso más largo puede ser adecuado para evitar la sensación de interfaz twitchy.</span><span class="sxs-lookup"><span data-stu-id="05f63-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="05f63-161">Patrones de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="05f63-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="05f63-162">Botones de alta frecuencia</span><span class="sxs-lookup"><span data-stu-id="05f63-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="05f63-163">Los botones de alta frecuencia son botones que se usan habitualmente en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="05f63-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="05f63-164">Un buen ejemplo son los botones Siguiente y Atrás de Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="05f63-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="05f63-165">**Recomendaciones**</span><span class="sxs-lookup"><span data-stu-id="05f63-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="05f63-166">Los botones de alta frecuencia deben ser grandes y más fáciles de visitar</span><span class="sxs-lookup"><span data-stu-id="05f63-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="05f63-167">Manténgase cerca de la altura para evitar una presión ergonómica.</span><span class="sxs-lookup"><span data-stu-id="05f63-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="05f63-168">*Imagen: botón siguiente de las guías de Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="05f63-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Botón siguiente de las guías de Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="05f63-170">Botones de baja frecuencia</span><span class="sxs-lookup"><span data-stu-id="05f63-170">Low frequency buttons</span></span>

<span data-ttu-id="05f63-171">Los botones de baja frecuencia son botones que no interactúan con tan solo en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="05f63-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="05f63-172">Un buen ejemplo podría ser un botón para acceder al menú de configuración o un botón para borrar todo el trabajo.</span><span class="sxs-lookup"><span data-stu-id="05f63-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="05f63-173">Intenta mantener estos botones apartados de las rutas frecuentes de la mirada con la cabeza para evitar activarlos accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="05f63-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="05f63-174">Confirmaciones</span><span class="sxs-lookup"><span data-stu-id="05f63-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="05f63-175">Cuando una acción tiene un impacto significativo, como la carga de dinero, la eliminación de trabajo o el inicio de un proceso largo, es útil confirmar que una persona está pensada para seleccionar un botón.</span><span class="sxs-lookup"><span data-stu-id="05f63-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="05f63-176">**Recomendaciones**</span><span class="sxs-lookup"><span data-stu-id="05f63-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="05f63-177">Muestra el resaltado de la selección en el botón principal.</span><span class="sxs-lookup"><span data-stu-id="05f63-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="05f63-178">Muestra el objetivo de permanencia al mismo tiempo que el resaltado de selección.</span><span class="sxs-lookup"><span data-stu-id="05f63-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="05f63-179">Para el botón secundario, muestra el objetivo de permanencia al mirar con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="05f63-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="05f63-180">*Imagen: cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="05f63-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="05f63-182">Botones de alternancia</span><span class="sxs-lookup"><span data-stu-id="05f63-182">Toggle buttons</span></span>

<span data-ttu-id="05f63-183">Los botones de alternancia requieren una lógica matizada para que funcionen correctamente.</span><span class="sxs-lookup"><span data-stu-id="05f63-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="05f63-184">Cuando una persona se aloja en un botón de alternancia y lo activa, debe salir del botón y volver a iniciar la lógica de permanencia.</span><span class="sxs-lookup"><span data-stu-id="05f63-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="05f63-185">Es importante que los botones que se van a alternar tengan un estado activo e inactivo.</span><span class="sxs-lookup"><span data-stu-id="05f63-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="05f63-186">Vistas de lista</span><span class="sxs-lookup"><span data-stu-id="05f63-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="05f63-187">Las vistas de lista presentan un desafío determinado para la entrada de encabezado y de continuación.</span><span class="sxs-lookup"><span data-stu-id="05f63-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="05f63-188">Los usuarios pueden examinar el contenido sin tener que tiptoe en torno a los objetivos de la vivienda.</span><span class="sxs-lookup"><span data-stu-id="05f63-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="05f63-189">**Recomendaciones**</span><span class="sxs-lookup"><span data-stu-id="05f63-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="05f63-190">Hacer que la fila completa se resalte cuando se mira por la cabeza, pero no comienza la permanencia, a menos que la punta de la mirada esté en el destino de vivienda específico.</span><span class="sxs-lookup"><span data-stu-id="05f63-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="05f63-191">Muestre solo el destino de permanencia cuando la fila esté resaltada para reducir el ruido visual.</span><span class="sxs-lookup"><span data-stu-id="05f63-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="05f63-192">Ser claros y coherentes con la posición de los objetivos de la vivienda.</span><span class="sxs-lookup"><span data-stu-id="05f63-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="05f63-193">No muestre todos los destinos de permanencia a la vez para evitar la interfaz de usuario repetida.</span><span class="sxs-lookup"><span data-stu-id="05f63-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="05f63-194">Reutilice el mismo patrón tantas veces como sea posible para establecer la familiaridad de la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="05f63-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="05f63-195">*Imagen: lista de guías de Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="05f63-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Lista de guías de Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="05f63-197">Consulte también</span><span class="sxs-lookup"><span data-stu-id="05f63-197">See also</span></span>

* [<span data-ttu-id="05f63-198">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="05f63-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="05f63-199">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="05f63-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="05f63-200">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="05f63-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="05f63-201">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="05f63-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="05f63-202">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="05f63-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="05f63-203">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="05f63-203">Voice input</span></span>](voice-input.md)
