---
title: Diseño de contenido para la pantalla holográfica
description: Obtenga información sobre las instrucciones de diseño y los procedimientos recomendados para la visualización de Holographic en dispositivos HoloLens.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Diseño de la interfaz de usuario, pantalla holográfica, diseño de contenido, tema oscuro, tema claro, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, diseño, píxeles
ms.openlocfilehash: 6bf65b9e40e42f1609b1108b366ac65637fcf106
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759280"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="bab39-104">Diseño de contenido para la pantalla holográfica</span><span class="sxs-lookup"><span data-stu-id="bab39-104">Designing content for holographic display</span></span>

![Ubicación del lado de ulnar](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="bab39-106">Al diseñar contenido para pantallas holográficas, hay varios elementos que debe tener en cuenta para lograr la mejor experiencia.</span><span class="sxs-lookup"><span data-stu-id="bab39-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="bab39-107">Enumeramos algunas de las recomendaciones siguientes y puede obtener más información acerca de las características de las pantallas holográficas en la página [color, Light y materiales](color-light-and-materials.md) .</span><span class="sxs-lookup"><span data-stu-id="bab39-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="bab39-108">Desafíos con color brillante en una superficie grande</span><span class="sxs-lookup"><span data-stu-id="bab39-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="bab39-109">En función de nuestra experiencia de investigación y pruebas de HoloLens, encontramos que el uso de colores brillantes en un área grande de la pantalla puede producir varios problemas:</span><span class="sxs-lookup"><span data-stu-id="bab39-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="bab39-110">**Fatiga ocular**</span><span class="sxs-lookup"><span data-stu-id="bab39-110">**Eye fatigue**</span></span> 

<span data-ttu-id="bab39-111">Dado que la pantalla holográfica es aditiva, los hologramas con colores brillantes usan más luz.</span><span class="sxs-lookup"><span data-stu-id="bab39-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="bab39-112">El color sólido y opaco en un área grande de la pantalla puede producir fácilmente fatiga ocular para el usuario.</span><span class="sxs-lookup"><span data-stu-id="bab39-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="bab39-113">**Oclusión de mano**</span><span class="sxs-lookup"><span data-stu-id="bab39-113">**Hand occlusion**</span></span> 

<span data-ttu-id="bab39-114">El color brillante dificulta que los usuarios vean sus manos al interactuar directamente con los objetos.</span><span class="sxs-lookup"><span data-stu-id="bab39-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="bab39-115">Dado que el usuario no puede ver sus manos, resulta difícil percibir la profundidad o la distancia entre la mano y el dedo en la superficie de destino.</span><span class="sxs-lookup"><span data-stu-id="bab39-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="bab39-116">El cursor de dedo ayuda a compensar este problema, pero puede seguir siendo desafiante en una superficie blanca brillante.</span><span class="sxs-lookup"><span data-stu-id="bab39-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="bab39-117">![El color y la oclusión de mano ](images/color_handocclusion.jpg)
 *dificultan ver la mano en el fondo de contenido de color brillante*</span><span class="sxs-lookup"><span data-stu-id="bab39-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="bab39-118">**Uniformidad de color**</span><span class="sxs-lookup"><span data-stu-id="bab39-118">**Color uniformity**</span></span>

<span data-ttu-id="bab39-119">Debido a las características de las pantallas holográficas, un gran área brillante en la pantalla puede volverse manchada.</span><span class="sxs-lookup"><span data-stu-id="bab39-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="bab39-120">El uso de esquemas de color oscuros le permite minimizar este problema.</span><span class="sxs-lookup"><span data-stu-id="bab39-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="bab39-121">Instrucciones de diseño para las opciones de color</span><span class="sxs-lookup"><span data-stu-id="bab39-121">Design guidelines for color choices</span></span>

<span data-ttu-id="bab39-122">**Usar color oscuro para el fondo de la interfaz de usuario**</span><span class="sxs-lookup"><span data-stu-id="bab39-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="bab39-123">Mediante el uso de la combinación de colores oscuro, puede minimizar la fatiga ocular y mejorar la confianza en las interacciones de las manos directas.</span><span class="sxs-lookup"><span data-stu-id="bab39-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="bab39-124">![Ejemplos de color oscuro usado para el fondo del contenido ](images/color_dark_examples.jpg)
 *ejemplos de color oscuro usado para el fondo del contenido*</span><span class="sxs-lookup"><span data-stu-id="bab39-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="bab39-125">**Usar el grosor de fuente seminegrita o negrita**</span><span class="sxs-lookup"><span data-stu-id="bab39-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="bab39-126">HoloLens permite que su experiencia muestre texto bonito de alta resolución.</span><span class="sxs-lookup"><span data-stu-id="bab39-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="bab39-127">Sin embargo, se recomienda evitar los pesos de fuente finos, como la luz o la semiluz, ya que los trazos verticales pueden vibrar en un tamaño de fuente pequeño.</span><span class="sxs-lookup"><span data-stu-id="bab39-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="bab39-128">![El grosor de fuente de negrita o seminegrita (panel superior) mejora la legibilidad en ](images/color_font_examples.jpg)
 *negrita o el espesor de fuente seminegrita (panel superior) mejora la legibilidad*</span><span class="sxs-lookup"><span data-stu-id="bab39-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="bab39-129">**Uso del material de HolographicBackplate de MRTK**</span><span class="sxs-lookup"><span data-stu-id="bab39-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="bab39-130">El material de HolographicBackplate se aplica a varios paneles de interfaz de usuario en el shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bab39-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="bab39-131">Una de sus características es un efecto de Iridescence que es visible para los usuarios cuando cambian su posición en función del panel.</span><span class="sxs-lookup"><span data-stu-id="bab39-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="bab39-132">El color de fondo se desplaza sutilmente a lo largo de un espectro predefinido, creando un efecto visual atractivo y dinámico sin interferir en la legibilidad del contenido.</span><span class="sxs-lookup"><span data-stu-id="bab39-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="bab39-133">Este sutil cambio de color también sirve para compensar las irregularidades de los colores menores.</span><span class="sxs-lookup"><span data-stu-id="bab39-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="bab39-134">Desafíos con la plancha de la interfaz de usuario transparente o translúcida</span><span class="sxs-lookup"><span data-stu-id="bab39-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="bab39-135">![Ejemplos de interfaz de usuario transparente ](images/color_transparent_examples.jpg)
 *ejemplos de planchas de interfaz de usuario transparentes*</span><span class="sxs-lookup"><span data-stu-id="bab39-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="bab39-136">**Complejidad visual y accesibilidad**</span><span class="sxs-lookup"><span data-stu-id="bab39-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="bab39-137">Dado que los objetos holográfica se fusionan con el entorno físico, el contenido o la legibilidad de la interfaz de usuario en ventanas transparentes o translúcidas podrían degradarse.</span><span class="sxs-lookup"><span data-stu-id="bab39-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="bab39-138">Además, cuando los objetos holográficas transparentes se superponen entre sí, podría dificultar la interacción del usuario debido a la profundidad confusa.</span><span class="sxs-lookup"><span data-stu-id="bab39-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="bab39-139">**Rendimiento**</span><span class="sxs-lookup"><span data-stu-id="bab39-139">**Performance**</span></span>

<span data-ttu-id="bab39-140">Para que los objetos transparentes o translúcidos se representen correctamente, deben ordenarse y combinarse con cualquier objeto que exista en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="bab39-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="bab39-141">La ordenación de objetos transparentes tiene un costo de CPU modesto, la fusión tiene un costo de GPU considerable, ya que no permite que la GPU realice la eliminación de la superficie oculta a través de la selección de z (es decir,</span><span class="sxs-lookup"><span data-stu-id="bab39-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="bab39-142">pruebas de profundidad).</span><span class="sxs-lookup"><span data-stu-id="bab39-142">depth testing).</span></span> <span data-ttu-id="bab39-143">No permitir la eliminación de superficies ocultas aumenta el número de operaciones necesarias para el píxel representado final.</span><span class="sxs-lookup"><span data-stu-id="bab39-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="bab39-144">Esto coloca más restricciones de velocidad de relleno.</span><span class="sxs-lookup"><span data-stu-id="bab39-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="bab39-145">**Problema de estabilidad de holograma con tecnología LSR de profundidad**</span><span class="sxs-lookup"><span data-stu-id="bab39-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="bab39-146">Para mejorar la Reproyección holográfica o la estabilidad del holograma, una aplicación puede enviar un búfer de profundidad al sistema para cada fotograma representado.</span><span class="sxs-lookup"><span data-stu-id="bab39-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="bab39-147">Cuando se usa el búfer de profundidad para la Reproyección, es necesario escribir un búfer de profundidad para cada píxel representado de color con una profundidad correspondiente.</span><span class="sxs-lookup"><span data-stu-id="bab39-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="bab39-148">Cualquier píxel con un valor de profundidad también debe tener un valor de color.</span><span class="sxs-lookup"><span data-stu-id="bab39-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="bab39-149">Si no se siguen las instrucciones anteriores, las áreas de la imagen representada que carecen de información de profundidad válida se pueden reproyectar de forma que generen artefactos, que a menudo son visibles como una distorsión de tipo onda.</span><span class="sxs-lookup"><span data-stu-id="bab39-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="bab39-150">Instrucciones de diseño para elementos transparentes</span><span class="sxs-lookup"><span data-stu-id="bab39-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="bab39-151">**Uso del fondo de la interfaz de usuario opaca**</span><span class="sxs-lookup"><span data-stu-id="bab39-151">**Use opaque UI background**</span></span>

<span data-ttu-id="bab39-152">De forma predeterminada, los objetos transparentes o translúcidos no escriben la profundidad para permitir una combinación adecuada.</span><span class="sxs-lookup"><span data-stu-id="bab39-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="bab39-153">Algunas formas de mitigar este problema son el uso de objetos opacos, la garantía de que los objetos translúcidos aparecen cerca de los objetos opacos (por ejemplo, un botón translúcido delante de una placa posterior opaca), lo que fuerza la escritura de los objetos translúcidos (no aplicable en todos los escenarios) o la representación de objetos proxy, que solo contribuyen con valores de profundidad</span><span class="sxs-lookup"><span data-stu-id="bab39-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="bab39-154">Soluciones dentro de MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="bab39-154">Solutions within MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="bab39-155">Mediante el uso de una placa de fondo sólida y opaca, podemos proteger la legibilidad y la confianza de la interacción.</span><span class="sxs-lookup"><span data-stu-id="bab39-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="bab39-156">**Minimizar el número de píxeles afectados**</span><span class="sxs-lookup"><span data-stu-id="bab39-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="bab39-157">Si el proyecto debe utilizar objetos transparentes, intente minimizar el número de píxeles afectados.</span><span class="sxs-lookup"><span data-stu-id="bab39-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="bab39-158">Por ejemplo, si un objeto solo está visible en determinadas condiciones (como un efecto de resplandor aditivo), deshabilite el objeto cuando sea totalmente invisible (en lugar de establecer el color aditivo en negro).</span><span class="sxs-lookup"><span data-stu-id="bab39-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="bab39-159">En el caso de las formas 2D simples creadas con una cuádruple con una máscara alfa, considere la posibilidad de crear en su lugar una representación de malla de la forma con un sombreador opaco.</span><span class="sxs-lookup"><span data-stu-id="bab39-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="bab39-160">Ejemplos de interfaz de usuario oscuras en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="bab39-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="bab39-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona muchos ejemplos de bloques de creación de interfaz de usuario basados en las combinaciones de colores oscuras.</span><span class="sxs-lookup"><span data-stu-id="bab39-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="bab39-162">Menú Near</span><span class="sxs-lookup"><span data-stu-id="bab39-162">Near Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/near-menu.md)
* [<span data-ttu-id="bab39-163">Diálogo</span><span class="sxs-lookup"><span data-stu-id="bab39-163">Dialog</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md)
* [<span data-ttu-id="bab39-164">Menú de la mano</span><span class="sxs-lookup"><span data-stu-id="bab39-164">Hand Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="bab39-165">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bab39-165">See also</span></span>

* [<span data-ttu-id="bab39-166">Color, luz y materiales</span><span class="sxs-lookup"><span data-stu-id="bab39-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="bab39-167">Cursores</span><span class="sxs-lookup"><span data-stu-id="bab39-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="bab39-168">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="bab39-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="bab39-169">Botón</span><span class="sxs-lookup"><span data-stu-id="bab39-169">Button</span></span>](button.md)
* [<span data-ttu-id="bab39-170">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="bab39-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bab39-171">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="bab39-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="bab39-172">Manipulación</span><span class="sxs-lookup"><span data-stu-id="bab39-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bab39-173">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="bab39-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="bab39-174">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="bab39-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="bab39-175">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="bab39-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="bab39-176">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="bab39-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="bab39-177">Teclado</span><span class="sxs-lookup"><span data-stu-id="bab39-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="bab39-178">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="bab39-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="bab39-179">Claqueta</span><span class="sxs-lookup"><span data-stu-id="bab39-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="bab39-180">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="bab39-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="bab39-181">Sombreador</span><span class="sxs-lookup"><span data-stu-id="bab39-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="bab39-182">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="bab39-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="bab39-183">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="bab39-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="bab39-184">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="bab39-184">Surface magnetism</span></span>](surface-magnetism.md)
