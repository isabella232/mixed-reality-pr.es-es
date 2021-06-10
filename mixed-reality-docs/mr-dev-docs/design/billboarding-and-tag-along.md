---
title: Etiquetado y vista frontal continua
description: Aprenda a usar objetos con paneles, que siempre se orientan a sí mismos para enfrentarse al usuario en aplicaciones de realidad mixta.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, paneles, etiquetas, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600344"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="76727-104">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="76727-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="76727-105">¿Qué es la asociación?</span><span class="sxs-lookup"><span data-stu-id="76727-105">What is billboarding?</span></span>

<span data-ttu-id="76727-106">La asociación es un concepto de comportamiento que se puede aplicar a objetos en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="76727-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="76727-107">Los objetos con paneles siempre se orientan a sí mismos para enfrentarse al usuario.</span><span class="sxs-lookup"><span data-stu-id="76727-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="76727-108">Los sistemas de texto y menú son casos de uso comunes, donde los objetos estáticos colocados en el entorno del usuario (bloqueados por el mundo) se ocultarían o no serían legibles cuando los usuarios se mueven.</span><span class="sxs-lookup"><span data-stu-id="76727-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="76727-109">Los objetos con el acodado habilitado pueden girar libremente en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="76727-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="76727-110">También se pueden restringir a un solo eje en función de las consideraciones de diseño.</span><span class="sxs-lookup"><span data-stu-id="76727-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="76727-111">Tenga en cuenta que los objetos delimitados pueden recortarse u occluir ellos mismos cuando se colocan demasiado cerca de otros objetos, o en HoloLens, demasiado cerca de las superficies examinadas.</span><span class="sxs-lookup"><span data-stu-id="76727-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="76727-112">Para evitarlo, piense en la superficie total que puede producir un objeto cuando se gira en el eje habilitado para el movimiento de paneles.</span><span class="sxs-lookup"><span data-stu-id="76727-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="76727-113">¿Qué es una etiqueta?</span><span class="sxs-lookup"><span data-stu-id="76727-113">What is a tag-along?</span></span>

<span data-ttu-id="76727-114">La etiqueta es un concepto de comportamiento que se puede agregar a los hologramas.</span><span class="sxs-lookup"><span data-stu-id="76727-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="76727-115">Un objeto de etiquetas intenta permanecer en un intervalo que permite al usuario interactuar cómodamente.</span><span class="sxs-lookup"><span data-stu-id="76727-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="76727-116">![El panel de pines de HoloLens es un excelente ejemplo de cómo se comporta la etiqueta](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="76727-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="76727-117">*El menú Inicio HoloLens es un excelente ejemplo de comportamiento de etiquetas*</span><span class="sxs-lookup"><span data-stu-id="76727-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="76727-118">Los objetos de etiquetas tienen parámetros, que pueden ajustar la forma en que se comportan.</span><span class="sxs-lookup"><span data-stu-id="76727-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="76727-119">El contenido puede estar dentro o fuera de la línea de visión del usuario mientras el usuario se mueve por su entorno.</span><span class="sxs-lookup"><span data-stu-id="76727-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="76727-120">A medida que se mueve, el contenido intenta permanecer dentro de la periferia del usuario deslizándose hacia el borde de la vista.</span><span class="sxs-lookup"><span data-stu-id="76727-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="76727-121">El contenido podría estar temporalmente fuera de la vista en función de la rapidez con la que se mueva el usuario.</span><span class="sxs-lookup"><span data-stu-id="76727-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="76727-122">Cuando el usuario mira hacia el objeto de etiqueta, se ve más a la vista.</span><span class="sxs-lookup"><span data-stu-id="76727-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="76727-123">Piense que el contenido siempre está "a un vistazo" para que los usuarios nunca olviden en qué dirección se encuentra su contenido.</span><span class="sxs-lookup"><span data-stu-id="76727-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="76727-124">Los parámetros adicionales pueden hacer que el objeto de etiqueta se sinta adjunto a la cabeza del usuario mediante una banda de almohadillas.</span><span class="sxs-lookup"><span data-stu-id="76727-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="76727-125">La aceleración o la reducción de la aceleración de la aceleración da peso al objeto, lo que hace que se sienta más presente físicamente.</span><span class="sxs-lookup"><span data-stu-id="76727-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="76727-126">Este comportamiento de spring es una ayuda que ayuda al usuario a crear un modelo mental preciso de cómo funciona la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="76727-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="76727-127">El audio ayuda a proporcionar otras indicaciones para cuando los usuarios tienen objetos en modo de etiqueta.</span><span class="sxs-lookup"><span data-stu-id="76727-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="76727-128">El audio debe reforzar la velocidad de movimiento; Un giro rápido en la cabeza debe proporcionar un efecto de sonido más perceptible, mientras que la marcha a una velocidad natural debe tener un mínimo o ningún efecto de audio.</span><span class="sxs-lookup"><span data-stu-id="76727-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="76727-129">Al igual que sucede con el contenido realmente bloqueado, los objetos de etiquetas pueden resultar abrumadores o abrumadores si se mueven demasiado en la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="76727-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="76727-130">A medida que un usuario examina y, a continuación, se detiene rápidamente, sus sentidos le dicen que se ha detenido.</span><span class="sxs-lookup"><span data-stu-id="76727-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="76727-131">Su equilibrio les informa de que su cabeza ha dejado de girar y su visión ve que el mundo deja de girar.</span><span class="sxs-lookup"><span data-stu-id="76727-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="76727-132">Sin embargo, si la etiqueta continúa en movimiento cuando el usuario se ha detenido, puede confundir sus sentidos.</span><span class="sxs-lookup"><span data-stu-id="76727-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="76727-133">Etiquetado y etiquetado en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="76727-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="76727-134">**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts para el comportamiento de etiquetado y etiquetado.</span><span class="sxs-lookup"><span data-stu-id="76727-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="76727-135">Asigne el script de Recordset.cs a cualquier objeto para agregar el comportamiento de afilación y hacer que el objeto siempre se le aleme.</span><span class="sxs-lookup"><span data-stu-id="76727-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="76727-136">Para agregar el comportamiento de etiquetas, use el script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="76727-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="76727-137">Puede ajustar varias opciones, como el tiempo de lerping, la distancia y el grado.</span><span class="sxs-lookup"><span data-stu-id="76727-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="76727-138">MRTK: solucionador de vistas radiales</span><span class="sxs-lookup"><span data-stu-id="76727-138">MRTK - Radial View Solver</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [<span data-ttu-id="76727-139">MRTK: script de Scripts</span><span class="sxs-lookup"><span data-stu-id="76727-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="76727-140">Vea también</span><span class="sxs-lookup"><span data-stu-id="76727-140">See also</span></span>

* [<span data-ttu-id="76727-141">Cursores</span><span class="sxs-lookup"><span data-stu-id="76727-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="76727-142">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="76727-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="76727-143">Botón</span><span class="sxs-lookup"><span data-stu-id="76727-143">Button</span></span>](button.md)
* [<span data-ttu-id="76727-144">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="76727-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="76727-145">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="76727-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="76727-146">Manipulación</span><span class="sxs-lookup"><span data-stu-id="76727-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="76727-147">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="76727-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="76727-148">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="76727-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="76727-149">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="76727-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="76727-150">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="76727-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="76727-151">Teclado</span><span class="sxs-lookup"><span data-stu-id="76727-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="76727-152">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="76727-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="76727-153">Claqueta</span><span class="sxs-lookup"><span data-stu-id="76727-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="76727-154">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="76727-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="76727-155">Sombreador</span><span class="sxs-lookup"><span data-stu-id="76727-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="76727-156">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="76727-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="76727-157">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="76727-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="76727-158">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="76727-158">Surface magnetism</span></span>](surface-magnetism.md)