---
title: Diseño de contenido para la pantalla holográfica
description: Obtenga información sobre las directrices de diseño y los procedimientos recomendados para la visualización holográfica en dispositivos HoloLens.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Diseño de la interfaz de usuario, pantalla holográfica, diseño de contenido, tema oscuro, tema claro, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, diseño, píxeles
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600324"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="4c4bd-104">Diseño de contenido para la pantalla holográfica</span><span class="sxs-lookup"><span data-stu-id="4c4bd-104">Designing content for holographic display</span></span>

![Ubicación de la mano de Ulnar](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="4c4bd-106">Al diseñar contenido para pantallas holográficas, hay varios elementos que debe tener en cuenta para lograr la mejor experiencia.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="4c4bd-107">Hemos enumerado algunas de nuestras recomendaciones a continuación y puede obtener más información sobre las características de las pantallas holográficas en la página [Color, luz y materiales.](color-light-and-materials.md)</span><span class="sxs-lookup"><span data-stu-id="4c4bd-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="4c4bd-108">Desafíos con el color brillante en una superficie grande</span><span class="sxs-lookup"><span data-stu-id="4c4bd-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="4c4bd-109">En función de la investigación y las pruebas de la experiencia de HoloLens, encontramos que el uso de colores brillantes en una gran área de la pantalla puede causar varios problemas:</span><span class="sxs-lookup"><span data-stu-id="4c4bd-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="4c4bd-110">**Agotamiento de los ojos**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-110">**Eye fatigue**</span></span> 

<span data-ttu-id="4c4bd-111">Puesto que la presentación holográfica es aditiva, los hologramas con colores brillantes usan más luz.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="4c4bd-112">Un color sólido y brillante en una gran área de la pantalla puede provocar fácilmente la agotamiento de los ojos para el usuario.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="4c4bd-113">**Oclusión de manos**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-113">**Hand occlusion**</span></span> 

<span data-ttu-id="4c4bd-114">El color brillante dificulta que el usuario vea sus manos al interactuar directamente con los objetos.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="4c4bd-115">Dado que el usuario no puede ver sus manos, resulta difícil percibir la profundidad o distancia entre la mano y el dedo hasta la superficie de destino.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="4c4bd-116">El cursor de dedo ayuda a compensar este problema, pero todavía puede ser difícil en una superficie blanca brillante.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="4c4bd-117">![Color y oclusión de la mano Difícil de ver la mano en la ](images/color_handocclusion.jpg)
 *placa posterior de contenido de color brillante*</span><span class="sxs-lookup"><span data-stu-id="4c4bd-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="4c4bd-118">**Uniformidad de color**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-118">**Color uniformity**</span></span>

<span data-ttu-id="4c4bd-119">Debido a las características de las pantallas holográficas, una gran área brillante de la pantalla puede volverse blotchy.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="4c4bd-120">Mediante el uso de esquemas de color oscuro, puede minimizar este problema.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="4c4bd-121">Directrices de diseño para opciones de color</span><span class="sxs-lookup"><span data-stu-id="4c4bd-121">Design guidelines for color choices</span></span>

<span data-ttu-id="4c4bd-122">**Uso del color oscuro para el fondo de la interfaz de usuario**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="4c4bd-123">Mediante el uso de la combinación de colores oscuros, puede minimizar la agotamiento de los ojos y mejorar la confianza en las interacciones directas con las manos.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="4c4bd-124">![Ejemplos de color oscuro usado para el fondo del contenido ](images/color_dark_examples.jpg)
 *Ejemplos de color oscuro usado para el fondo del contenido*</span><span class="sxs-lookup"><span data-stu-id="4c4bd-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="4c4bd-125">**Usar el grosor de la fuente semibólica o en negrita**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="4c4bd-126">HoloLens permite que su experiencia muestre texto de alta resolución.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="4c4bd-127">Sin embargo, se recomienda evitar los pesos de fuente finos, como la luz o la semi light, ya que los trazos verticales pueden fluctuar en un tamaño de fuente pequeño.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="4c4bd-128">![El grosor de la fuente en negrita o en negrita (panel superior) mejora la legibilidad En negrita o ](images/color_font_examples.jpg)
 *en negrita (panel superior) mejora la legibilidad.*</span><span class="sxs-lookup"><span data-stu-id="4c4bd-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="4c4bd-129">**Uso del material HolographicBackplate de MRTK**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="4c4bd-130">El material holographicBackplate se aplica a varios paneles de interfaz de usuario en el shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="4c4bd-131">Una de sus características es un efecto iridiscencia que es visible para los usuarios a medida que cambian de posición en función del panel.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="4c4bd-132">El color de la placa posterior cambia sutilmente a través de un espectro predefinido, lo que crea un efecto visual atractivo y dinámico sin interferir con la legibilidad del contenido.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="4c4bd-133">Este sutil cambio de color también sirve para compensar las pequeñas irregularidades de color.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="4c4bd-134">Desafíos con la placa trasera transparente o translúcida de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="4c4bd-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="4c4bd-135">![Ejemplos de interfaz de usuario ](images/color_transparent_examples.jpg)
 *transparente Ejemplos de placa trasera de interfaz de usuario transparente*</span><span class="sxs-lookup"><span data-stu-id="4c4bd-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="4c4bd-136">**Complejidad visual y accesibilidad**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="4c4bd-137">Dado que los objetos holográficos se combinan con el entorno físico, el contenido o la legibilidad de la interfaz de usuario en ventanas transparentes o translúcidas podrían degradarse.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="4c4bd-138">Además, cuando los objetos holográficos transparentes se sobrelanan entre sí, podría dificultar la interacción del usuario debido a la profundidad confusa.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="4c4bd-139">**Rendimiento**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-139">**Performance**</span></span>

<span data-ttu-id="4c4bd-140">Para que los objetos transparentes o translúcidos se representen correctamente, deben ordenarse y combinarse con cualquier objeto que exista en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="4c4bd-141">La ordenación de objetos transparentes tiene un costo de CPU moderado, la combinación tiene un costo considerable de GPU porque no permite que la GPU realice la eliminación de la superficie oculta mediante la selección z (es decir,</span><span class="sxs-lookup"><span data-stu-id="4c4bd-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="4c4bd-142">pruebas de profundidad).</span><span class="sxs-lookup"><span data-stu-id="4c4bd-142">depth testing).</span></span> <span data-ttu-id="4c4bd-143">No permitir la eliminación de la superficie oculta aumenta el número de operaciones necesarias para el píxel representado final.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="4c4bd-144">Esto aumenta las restricciones de la tasa de relleno de presión.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="4c4bd-145">**Problema de estabilidad del holograma con la tecnología LSR de profundidad**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="4c4bd-146">Para mejorar la reproducción holográfica o la estabilidad del holograma, una aplicación puede enviar un búfer de profundidad al sistema para cada fotograma representado.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="4c4bd-147">Al usar el búfer de profundidad para la reproducción, debe escribir un búfer de profundidad para cada color representado en píxeles con una profundidad correspondiente.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="4c4bd-148">Cualquier píxel con un valor de profundidad también debe tener un valor de color.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="4c4bd-149">Si no se sigue la guía anterior, las áreas de la imagen representada que carecen de información de profundidad válida se pueden volver a proyectar de forma que se produzcan artefactos, que a menudo son visibles como una distorsión de onda.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="4c4bd-150">Directrices de diseño para elementos transparentes</span><span class="sxs-lookup"><span data-stu-id="4c4bd-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="4c4bd-151">**Uso del fondo opaco de la interfaz de usuario**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-151">**Use opaque UI background**</span></span>

<span data-ttu-id="4c4bd-152">De forma predeterminada, los objetos transparentes o translúcidos no escriben profundidad para permitir una mezcla adecuada.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="4c4bd-153">Entre las formas de mitigar este problema se incluyen el uso de objetos opacos, la garantía de que los objetos translúcidos aparecen cerca de los objetos opacos (por ejemplo, un botón translúcido delante de una placa trasera opaca), forzar a los objetos translúcidos a escribir profundidad (no aplicable en todos los escenarios) o representar objetos proxy, que solo aportan valores de profundidad al final del fotograma.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="4c4bd-154">Soluciones dentro de MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="4c4bd-154">Solutions within MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="4c4bd-155">Mediante el uso de una placa trasera sólida y opaca, podemos proteger la legibilidad y la confianza de interacción.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="4c4bd-156">**Minimizar el número de píxeles afectados**</span><span class="sxs-lookup"><span data-stu-id="4c4bd-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="4c4bd-157">Si el proyecto debe usar objetos transparentes, intente minimizar el número de píxeles afectados.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="4c4bd-158">Por ejemplo, si un objeto solo está visible en determinadas condiciones (por ejemplo, un efecto de adiciones), deshabilite el objeto cuando sea totalmente invisible (en lugar de establecer el color de suma en negro).</span><span class="sxs-lookup"><span data-stu-id="4c4bd-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="4c4bd-159">Para formas 2D sencillas creadas con un cuadrándido con una máscara alfa, considere la posibilidad de crear una representación de malla de la forma con un sombreador opaco en su lugar.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="4c4bd-160">Ejemplos de interfaz de usuario oscura en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="4c4bd-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="4c4bd-161">**[MRTK proporciona muchos](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ejemplos de bloques de creación de interfaz de usuario basados en las esquemas de color oscuro.</span><span class="sxs-lookup"><span data-stu-id="4c4bd-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="4c4bd-162">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="4c4bd-162">Near Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [<span data-ttu-id="4c4bd-163">Diálogo</span><span class="sxs-lookup"><span data-stu-id="4c4bd-163">Dialog</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [<span data-ttu-id="4c4bd-164">Menú de mano</span><span class="sxs-lookup"><span data-stu-id="4c4bd-164">Hand Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a><span data-ttu-id="4c4bd-165">Vea también</span><span class="sxs-lookup"><span data-stu-id="4c4bd-165">See also</span></span>

* [<span data-ttu-id="4c4bd-166">Color, luz y materiales</span><span class="sxs-lookup"><span data-stu-id="4c4bd-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="4c4bd-167">Cursores</span><span class="sxs-lookup"><span data-stu-id="4c4bd-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4c4bd-168">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="4c4bd-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="4c4bd-169">Botón</span><span class="sxs-lookup"><span data-stu-id="4c4bd-169">Button</span></span>](button.md)
* [<span data-ttu-id="4c4bd-170">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="4c4bd-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4c4bd-171">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="4c4bd-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4c4bd-172">Manipulación</span><span class="sxs-lookup"><span data-stu-id="4c4bd-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4c4bd-173">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="4c4bd-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="4c4bd-174">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="4c4bd-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="4c4bd-175">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="4c4bd-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4c4bd-176">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="4c4bd-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="4c4bd-177">Teclado</span><span class="sxs-lookup"><span data-stu-id="4c4bd-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="4c4bd-178">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="4c4bd-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="4c4bd-179">Claqueta</span><span class="sxs-lookup"><span data-stu-id="4c4bd-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="4c4bd-180">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="4c4bd-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="4c4bd-181">Sombreador</span><span class="sxs-lookup"><span data-stu-id="4c4bd-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="4c4bd-182">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="4c4bd-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4c4bd-183">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="4c4bd-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="4c4bd-184">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="4c4bd-184">Surface magnetism</span></span>](surface-magnetism.md)