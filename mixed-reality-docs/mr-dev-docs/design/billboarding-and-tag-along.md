---
title: Etiquetado y vista frontal continua
description: Los objetos con la cartelera siempre se orientan a sí mismos para que se enfrente al usuario.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, la cartelera, el etiquetado
ms.openlocfilehash: 266fb314ae4fccdc25e94b20d04262666be5a1b6
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692142"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="c17d5-104">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="c17d5-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="c17d5-105">¿Qué es la cartelera?</span><span class="sxs-lookup"><span data-stu-id="c17d5-105">What is billboarding?</span></span>

<span data-ttu-id="c17d5-106">La cartelera es un concepto de comportamiento que se puede aplicar a los objetos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c17d5-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="c17d5-107">Los objetos con la cartelera siempre se orientan a sí mismos para que se enfrente al usuario.</span><span class="sxs-lookup"><span data-stu-id="c17d5-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="c17d5-108">Esto es especialmente útil en el caso de los sistemas de texto y de menús en los que los objetos estáticos que se colocan en el entorno del usuario (con bloqueo mundial) quedarían ocultos o ilegibles si el usuario se desplazara.</span><span class="sxs-lookup"><span data-stu-id="c17d5-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="c17d5-109">Los objetos con la cartelera habilitada pueden girar libremente en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="c17d5-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="c17d5-110">También se pueden restringir a un único eje en función de las consideraciones de diseño.</span><span class="sxs-lookup"><span data-stu-id="c17d5-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="c17d5-111">Tenga en cuenta que los objetos con recortes se pueden recortar o tapaba si se colocan demasiado cerca de otros objetos, o en HoloLens, hay demasiadas cerrar superficies digitalizadas.</span><span class="sxs-lookup"><span data-stu-id="c17d5-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="c17d5-112">Para evitar esto, piense en la superficie total que un objeto puede producir cuando se gira en el eje habilitado para la cartelera.</span><span class="sxs-lookup"><span data-stu-id="c17d5-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="c17d5-113">¿Qué es una etiqueta?</span><span class="sxs-lookup"><span data-stu-id="c17d5-113">What is a tag-along?</span></span>

<span data-ttu-id="c17d5-114">La etiqueta es un concepto de comportamiento que se puede Agregar a los hologramas.</span><span class="sxs-lookup"><span data-stu-id="c17d5-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="c17d5-115">Una etiqueta a lo largo del objeto intenta permanecer en un intervalo que permite al usuario interactuar de forma cómoda.</span><span class="sxs-lookup"><span data-stu-id="c17d5-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="c17d5-116">![El panel de PIN de HoloLens es un buen ejemplo de cómo se comparan las etiquetas](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c17d5-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="c17d5-117">*El menú Inicio de HoloLens es un buen ejemplo de comportamiento de etiqueta.*</span><span class="sxs-lookup"><span data-stu-id="c17d5-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="c17d5-118">Los objetos de etiqueta incluyen parámetros que pueden ajustarse de la forma en que se comportan.</span><span class="sxs-lookup"><span data-stu-id="c17d5-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="c17d5-119">El contenido puede estar dentro o fuera de la línea de visión del usuario mientras se desee mientras el usuario se mueve por su entorno.</span><span class="sxs-lookup"><span data-stu-id="c17d5-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="c17d5-120">A medida que el usuario se mueve, el contenido intentará permanecer dentro del perímetro del usuario desplazándose hacia el borde de la vista, en función de la rapidez con la que se mueva el usuario puede dejar el contenido temporalmente fuera de la vista.</span><span class="sxs-lookup"><span data-stu-id="c17d5-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="c17d5-121">Cuando el usuario mira hacia el objeto de etiqueta, resulta más completo ver.</span><span class="sxs-lookup"><span data-stu-id="c17d5-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="c17d5-122">Piense que el contenido siempre es "un vistazo", por lo que los usuarios nunca olvidan en qué dirección se encuentra el contenido.</span><span class="sxs-lookup"><span data-stu-id="c17d5-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="c17d5-123">Los parámetros adicionales pueden hacer que la etiqueta a lo largo del objeto se adjunte al encabezado del usuario mediante una banda elástica.</span><span class="sxs-lookup"><span data-stu-id="c17d5-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="c17d5-124">La amortiguación de aceleración o desaceleración da peso al objeto, lo que hace que se sienta más físicamente presente.</span><span class="sxs-lookup"><span data-stu-id="c17d5-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="c17d5-125">Este comportamiento del muelle es una prestación que ayuda al usuario a crear un modelo mental exacto de cómo funciona la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="c17d5-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="c17d5-126">Audio le ayuda a proporcionar prestaciones adicionales para cuando los usuarios tienen objetos en el modo de etiqueta.</span><span class="sxs-lookup"><span data-stu-id="c17d5-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="c17d5-127">El audio debe reforzar la velocidad de movimiento; un cambio de cabeza rápido debe proporcionar un efecto de sonido más perceptible mientras el recorrido de una velocidad natural debe tener un audio mínimo si se produce algún efecto.</span><span class="sxs-lookup"><span data-stu-id="c17d5-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="c17d5-128">Al igual que el contenido bloqueado realmente por el encabezado, los objetos de etiquetas pueden resultar abrumadores o nauseating si se mueven de forma desigual o muelle demasiado en la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="c17d5-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="c17d5-129">A medida que un usuario busca y luego se detiene rápidamente, sus sentidos les indica que se han detenido.</span><span class="sxs-lookup"><span data-stu-id="c17d5-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="c17d5-130">Su saldo les informa de que su cabeza ha dejado de activar y su visión ve que el mundo deja de activar.</span><span class="sxs-lookup"><span data-stu-id="c17d5-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="c17d5-131">Sin embargo, si la etiqueta se mantiene en movimiento cuando el usuario se detiene, puede confundir sus sentidos.</span><span class="sxs-lookup"><span data-stu-id="c17d5-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c17d5-132">La cartelera y la etiqueta en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="c17d5-132">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="c17d5-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts para el comportamiento de la cartelera y la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="c17d5-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="c17d5-134">Basta con asignar el script Billboard.cs a cualquier objeto para agregar el comportamiento de la cartelera y hacer que el objeto siempre se enfrente a usted.</span><span class="sxs-lookup"><span data-stu-id="c17d5-134">Simply assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="c17d5-135">Para agregar el comportamiento de etiqueta, use el script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="c17d5-135">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="c17d5-136">Puede ajustar varias opciones, como lerping Time, Distance y degree.</span><span class="sxs-lookup"><span data-stu-id="c17d5-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="c17d5-137">MRTK: Solver de vista radial</span><span class="sxs-lookup"><span data-stu-id="c17d5-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="c17d5-138">MRTK: script de la cartelera</span><span class="sxs-lookup"><span data-stu-id="c17d5-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="c17d5-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c17d5-139">See also</span></span>

* [<span data-ttu-id="c17d5-140">Cursores</span><span class="sxs-lookup"><span data-stu-id="c17d5-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c17d5-141">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="c17d5-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c17d5-142">Botón</span><span class="sxs-lookup"><span data-stu-id="c17d5-142">Button</span></span>](button.md)
* [<span data-ttu-id="c17d5-143">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="c17d5-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c17d5-144">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c17d5-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c17d5-145">Manipulación</span><span class="sxs-lookup"><span data-stu-id="c17d5-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c17d5-146">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="c17d5-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c17d5-147">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="c17d5-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c17d5-148">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="c17d5-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c17d5-149">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="c17d5-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c17d5-150">Teclado</span><span class="sxs-lookup"><span data-stu-id="c17d5-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c17d5-151">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="c17d5-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c17d5-152">Claqueta</span><span class="sxs-lookup"><span data-stu-id="c17d5-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="c17d5-153">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="c17d5-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="c17d5-154">Sombreador</span><span class="sxs-lookup"><span data-stu-id="c17d5-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="c17d5-155">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="c17d5-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c17d5-156">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="c17d5-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c17d5-157">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="c17d5-157">Surface magnetism</span></span>](surface-magnetism.md)
