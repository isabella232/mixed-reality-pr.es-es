---
title: Diseño de contenido para la pantalla holográfica
description: Instrucciones de diseño y prácticas recomendadas para la visualización holográfica
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Diseño de la interfaz de usuario, pantalla holográfica, diseño de contenido, tema oscuro, tema claro, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, diseño, píxeles
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702641"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="fb02e-104">Diseño de contenido para la pantalla holográfica</span><span class="sxs-lookup"><span data-stu-id="fb02e-104">Designing content for holographic display</span></span>

![Ubicación del lado de ulnar](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="fb02e-106">Al diseñar contenido para pantallas holográficas, hay varios elementos que debe tener en cuenta para lograr la mejor experiencia.</span><span class="sxs-lookup"><span data-stu-id="fb02e-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="fb02e-107">Enumeramos algunas de las recomendaciones siguientes y puede obtener más información acerca de las características de las pantallas holográficas en la página [color, Light y materiales](color-light-and-materials.md) .</span><span class="sxs-lookup"><span data-stu-id="fb02e-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="fb02e-108">Desafíos con color brillante en una superficie grande</span><span class="sxs-lookup"><span data-stu-id="fb02e-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="fb02e-109">En función de la investigación y las pruebas de los distintos tipos de experiencias de HoloLens, encontramos que el uso de colores brillantes en un área grande de la pantalla puede producir varios problemas:</span><span class="sxs-lookup"><span data-stu-id="fb02e-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="fb02e-110">**Fatiga ocular**</span><span class="sxs-lookup"><span data-stu-id="fb02e-110">**Eye fatigue**</span></span> 

<span data-ttu-id="fb02e-111">Dado que la pantalla holográfica es aditiva, el color brillante usa más luz para mostrar los hologramas.</span><span class="sxs-lookup"><span data-stu-id="fb02e-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="fb02e-112">El color sólido y opaco en un área grande de la pantalla puede producir fácilmente fatiga ocular para el usuario.</span><span class="sxs-lookup"><span data-stu-id="fb02e-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="fb02e-113">**Oclusión de mano**</span><span class="sxs-lookup"><span data-stu-id="fb02e-113">**Hand occlusion**</span></span> 

<span data-ttu-id="fb02e-114">El color brillante dificulta que los usuarios vean sus manos al interactuar directamente con los objetos.</span><span class="sxs-lookup"><span data-stu-id="fb02e-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="fb02e-115">Puesto que el usuario no puede ver sus manos, resulta difícil percibir la profundidad o la distancia entre la mano y el dedo en la superficie de destino.</span><span class="sxs-lookup"><span data-stu-id="fb02e-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="fb02e-116">El cursor de dedo ayuda a compensar este problema, pero puede seguir siendo desafiante en una superficie blanca brillante.</span><span class="sxs-lookup"><span data-stu-id="fb02e-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="fb02e-117">![El color y la oclusión de mano ](images/color_handocclusion.jpg)
 *dificultan ver la mano en el fondo de contenido de color brillante*</span><span class="sxs-lookup"><span data-stu-id="fb02e-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="fb02e-118">**Uniformidad de color**</span><span class="sxs-lookup"><span data-stu-id="fb02e-118">**Color uniformity**</span></span>

<span data-ttu-id="fb02e-119">Debido a las características de las pantallas holográficas, un gran área brillante en la pantalla puede volverse manchada.</span><span class="sxs-lookup"><span data-stu-id="fb02e-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="fb02e-120">El uso de esquemas de color oscuros le permite minimizar este problema.</span><span class="sxs-lookup"><span data-stu-id="fb02e-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="fb02e-121">Guías de diseño</span><span class="sxs-lookup"><span data-stu-id="fb02e-121">Design guidelines</span></span>

<span data-ttu-id="fb02e-122">**Usar color oscuro para el fondo de la interfaz de usuario**</span><span class="sxs-lookup"><span data-stu-id="fb02e-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="fb02e-123">Mediante el uso de la combinación de colores oscuro, puede minimizar la fatiga ocular y mejorar la confianza en las interacciones de las manos directas.</span><span class="sxs-lookup"><span data-stu-id="fb02e-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="fb02e-124">![Ejemplos de interfaz de usuario oscura ](images/color_dark_examples.jpg)
 *ejemplos de color oscuro usado para el fondo de contenido*</span><span class="sxs-lookup"><span data-stu-id="fb02e-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="fb02e-125">**Usar el grosor de fuente seminegrita o negrita**</span><span class="sxs-lookup"><span data-stu-id="fb02e-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="fb02e-126">HoloLens permite que su experiencia muestre texto bonito de alta resolución.</span><span class="sxs-lookup"><span data-stu-id="fb02e-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="fb02e-127">Sin embargo, se recomienda evitar los pesos de fuente finos, como la luz o la semiluz, ya que los trazos verticales pueden vibrar en un tamaño de fuente pequeño.</span><span class="sxs-lookup"><span data-stu-id="fb02e-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="fb02e-128">![Ejemplos de la interfaz de usuario oscura: ](images/color_font_examples.jpg)
 *el grosor de fuente en negrita o seminegrita (panel superior) mejora la legibilidad*</span><span class="sxs-lookup"><span data-stu-id="fb02e-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="fb02e-129">**Uso del material de HolographicBackplate de MRTK**</span><span class="sxs-lookup"><span data-stu-id="fb02e-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="fb02e-130">El material de HolographicBackplate se aplica a varios paneles de interfaz de usuario en el shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb02e-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="fb02e-131">Una de sus características es un efecto de Iridescence que es visible para los usuarios mientras cambian su posición en relación con el panel.</span><span class="sxs-lookup"><span data-stu-id="fb02e-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="fb02e-132">El color de fondo se desplaza sutilmente a lo largo de un espectro predefinido, creando un efecto visual atractivo y dinámico sin interferir en la legibilidad del contenido.</span><span class="sxs-lookup"><span data-stu-id="fb02e-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="fb02e-133">Este sutil cambio de color también sirve para compensar las irregularidades de los colores menores.</span><span class="sxs-lookup"><span data-stu-id="fb02e-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="fb02e-134">Desafíos con la plancha de la interfaz de usuario transparente o translúcida</span><span class="sxs-lookup"><span data-stu-id="fb02e-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="fb02e-135">![Ejemplos de interfaz de usuario transparente ](images/color_transparent_examples.jpg)
 *ejemplos de planchas de interfaz de usuario transparentes*</span><span class="sxs-lookup"><span data-stu-id="fb02e-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="fb02e-136">**Complejidad visual y accesibilidad**</span><span class="sxs-lookup"><span data-stu-id="fb02e-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="fb02e-137">Dado que los objetos holográficas se mezclan con el entorno físico, la legibilidad del contenido o la interfaz de usuario en la ventana transparente o translúcida podría degradarse.</span><span class="sxs-lookup"><span data-stu-id="fb02e-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="fb02e-138">Además, cuando los objetos holográficas transparentes se superponen entre sí, podría dificultar la interacción del usuario debido a la profundidad confusa.</span><span class="sxs-lookup"><span data-stu-id="fb02e-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="fb02e-139">**Rendimiento**</span><span class="sxs-lookup"><span data-stu-id="fb02e-139">**Performance**</span></span>

<span data-ttu-id="fb02e-140">Para que los objetos transparentes o translúcidos se representen correctamente, deben ordenarse y combinarse con cualquier objeto que exista en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="fb02e-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="fb02e-141">La ordenación de objetos transparentes tiene un costo de CPU modesto, la fusión tiene un costo de GPU considerable, ya que no permite que la GPU realice la eliminación de la superficie oculta a través de la selección de z (es decir,</span><span class="sxs-lookup"><span data-stu-id="fb02e-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="fb02e-142">pruebas de profundidad).</span><span class="sxs-lookup"><span data-stu-id="fb02e-142">depth testing).</span></span> <span data-ttu-id="fb02e-143">No permitir la eliminación de superficies ocultas aumenta el número de operaciones que se deben calcular para el último píxel representado y, por lo tanto, pone más presión en las restricciones de velocidad de relleno.</span><span class="sxs-lookup"><span data-stu-id="fb02e-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="fb02e-144">**Problema de estabilidad de holograma con tecnología LSR de profundidad**</span><span class="sxs-lookup"><span data-stu-id="fb02e-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="fb02e-145">Para mejorar la Reproyección holográfica o la estabilidad del holograma, una aplicación puede enviar un búfer de profundidad al sistema para cada fotograma representado.</span><span class="sxs-lookup"><span data-stu-id="fb02e-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="fb02e-146">Cuando se usa el búfer de profundidad para la Reproyección, una regla es que para cada píxel de color representado, se debe escribir un valor de profundidad correspondiente en el búfer de profundidad (y cualquier píxel con un valor de profundidad también debe tener un valor de color).</span><span class="sxs-lookup"><span data-stu-id="fb02e-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="fb02e-147">Si no se siguen las instrucciones anteriores, las áreas de la imagen representada que carecen de información de profundidad válida se pueden reproyectar de forma que generen artefactos (a menudo visibles como una distorsión de tipo onda).</span><span class="sxs-lookup"><span data-stu-id="fb02e-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="fb02e-148">Guías de diseño</span><span class="sxs-lookup"><span data-stu-id="fb02e-148">Design guidelines</span></span>
<span data-ttu-id="fb02e-149">**Uso del fondo de la interfaz de usuario opaca**</span><span class="sxs-lookup"><span data-stu-id="fb02e-149">**Use opaque UI background**</span></span>

<span data-ttu-id="fb02e-150">De forma predeterminada, los objetos transparentes o translúcidos no escriben la profundidad para permitir una combinación adecuada.</span><span class="sxs-lookup"><span data-stu-id="fb02e-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="fb02e-151">Algunas formas de mitigar este problema son el uso de objetos opacos, la garantía de que los objetos translúcidos aparecen cerca de los objetos opacos (por ejemplo, un botón translúcido delante de una placa posterior opaca), forzando a los objetos translúcido a escribir la profundidad (no aplicable en todos los escenarios) o la representación de objetos de proxy que solo contribuyen con valores de profundidad</span><span class="sxs-lookup"><span data-stu-id="fb02e-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="fb02e-152">Soluciones dentro de MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="fb02e-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="fb02e-153">Mediante el uso de una placa de fondo sólida y opaca, podemos proteger la legibilidad y la confianza de la interacción.</span><span class="sxs-lookup"><span data-stu-id="fb02e-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="fb02e-154">**Minimizar el número de píxeles afectados**</span><span class="sxs-lookup"><span data-stu-id="fb02e-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="fb02e-155">Si el proyecto debe utilizar objetos transparentes, intente minimizar el número de píxeles afectados.</span><span class="sxs-lookup"><span data-stu-id="fb02e-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="fb02e-156">Por ejemplo, si un objeto solo está visible en determinadas condiciones (como un efecto de resplandor aditivo), deshabilite el objeto cuando sea totalmente invisible (en lugar de establecer el color aditivo en negro).</span><span class="sxs-lookup"><span data-stu-id="fb02e-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="fb02e-157">En el caso de las formas 2D simples creadas con una cuádruple con una máscara alfa, considere la posibilidad de crear en su lugar una representación de malla de la forma con un sombreador opaco.</span><span class="sxs-lookup"><span data-stu-id="fb02e-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="fb02e-158">Ejemplos de interfaz de usuario oscuras en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="fb02e-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="fb02e-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona muchos ejemplos de bloques de creación de interfaz de usuario basados en las combinaciones de colores oscuras.</span><span class="sxs-lookup"><span data-stu-id="fb02e-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="fb02e-160">Menú Near</span><span class="sxs-lookup"><span data-stu-id="fb02e-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="fb02e-161">Diálogo</span><span class="sxs-lookup"><span data-stu-id="fb02e-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="fb02e-162">Menú de la mano</span><span class="sxs-lookup"><span data-stu-id="fb02e-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="fb02e-163">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fb02e-163">See also</span></span>
* [<span data-ttu-id="fb02e-164">Color, luz y materiales</span><span class="sxs-lookup"><span data-stu-id="fb02e-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="fb02e-165">Cursores</span><span class="sxs-lookup"><span data-stu-id="fb02e-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="fb02e-166">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="fb02e-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="fb02e-167">Botón</span><span class="sxs-lookup"><span data-stu-id="fb02e-167">Button</span></span>](button.md)
* [<span data-ttu-id="fb02e-168">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="fb02e-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fb02e-169">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="fb02e-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="fb02e-170">Manipulación</span><span class="sxs-lookup"><span data-stu-id="fb02e-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fb02e-171">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="fb02e-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="fb02e-172">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="fb02e-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="fb02e-173">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="fb02e-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="fb02e-174">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="fb02e-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="fb02e-175">Teclado</span><span class="sxs-lookup"><span data-stu-id="fb02e-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="fb02e-176">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="fb02e-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="fb02e-177">Claqueta</span><span class="sxs-lookup"><span data-stu-id="fb02e-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="fb02e-178">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="fb02e-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="fb02e-179">Sombreador</span><span class="sxs-lookup"><span data-stu-id="fb02e-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="fb02e-180">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="fb02e-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="fb02e-181">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="fb02e-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="fb02e-182">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="fb02e-182">Surface magnetism</span></span>](surface-magnetism.md)
