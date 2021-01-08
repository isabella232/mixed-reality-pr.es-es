---
title: Tipografía
description: Aprenda a diseñar e implementar texto como un elemento importante para la entrega de información en su experiencia de aplicación de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, estilo, fuente, tipografía, IU, experiencia de usuario, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens
ms.openlocfilehash: 38acc8c0d2c7dbd7bcb192f82bb1bb52838323ac
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007655"
---
# <a name="typography"></a><span data-ttu-id="5c724-104">Tipografía</span><span class="sxs-lookup"><span data-stu-id="5c724-104">Typography</span></span>

![Ejemplo de tipografía en HoloLens](images/typography-cover.png)<br>


<span data-ttu-id="5c724-106">El texto es un elemento importante para entregar información en la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5c724-106">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="5c724-107">Al igual que la tipografía en las pantallas 2D, el objetivo es que sea clara y legible.</span><span class="sxs-lookup"><span data-stu-id="5c724-107">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="5c724-108">Con el aspecto tridimensional de la realidad mixta, existe la posibilidad de afectar al texto y a la experiencia global del usuario de una manera incluso mayor.</span><span class="sxs-lookup"><span data-stu-id="5c724-108">With the three-dimensional aspect of mixed reality, there's an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="5c724-109">Cuando hablemos sobre el tipo en 3D, se tiende a pensar en el texto 3D extruido.</span><span class="sxs-lookup"><span data-stu-id="5c724-109">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="5c724-110">A excepción de algunos diseños de logotipo y otras aplicaciones limitadas, el texto extruido tiende a degradar la legibilidad del texto.</span><span class="sxs-lookup"><span data-stu-id="5c724-110">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="5c724-111">Aunque estamos diseñando experiencias para 3D, usamos 2D para el tipo porque es más legible y más fácil de leer.</span><span class="sxs-lookup"><span data-stu-id="5c724-111">Even though we're designing experiences for 3D, we use 2D for the type because it's more legible and easier to read.</span></span>

<span data-ttu-id="5c724-112">En HoloLens, el tipo se construye con hologramas que usan la luz basada en el sistema de colores aditivo.</span><span class="sxs-lookup"><span data-stu-id="5c724-112">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="5c724-113">Al igual que otros hologramas, el tipo se puede colocar en el entorno real, donde se puede bloquear y observar en cualquier ángulo.</span><span class="sxs-lookup"><span data-stu-id="5c724-113">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="5c724-114">El efecto de [Parallax](https://en.wikipedia.org/wiki/Parallax) entre el tipo y el entorno también agrega profundidad a la experiencia.</span><span class="sxs-lookup"><span data-stu-id="5c724-114">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="5c724-115">Tipografía en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5c724-115">Typography in mixed reality</span></span>

<span data-ttu-id="5c724-116">Las reglas tipográficas de realidad mixta no son diferentes de cualquier otra cosa.</span><span class="sxs-lookup"><span data-stu-id="5c724-116">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="5c724-117">El texto del mundo físico y del mundo virtual debe ser legible y legible.</span><span class="sxs-lookup"><span data-stu-id="5c724-117">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="5c724-118">El texto podría estar en un muro o superpuesto en un objeto físico.</span><span class="sxs-lookup"><span data-stu-id="5c724-118">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="5c724-119">Podría ser flotante junto con una interfaz de usuario digital.</span><span class="sxs-lookup"><span data-stu-id="5c724-119">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="5c724-120">Sea cual sea el contexto, se aplican las mismas reglas tipográficas para lectura y reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="5c724-120">Whatever the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="5c724-121">Crear una jerarquía clara</span><span class="sxs-lookup"><span data-stu-id="5c724-121">Create clear hierarchy</span></span>

<span data-ttu-id="5c724-122">Cree el contraste y la jerarquía mediante el uso de diferentes tamaños y pesos de tipos.</span><span class="sxs-lookup"><span data-stu-id="5c724-122">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="5c724-123">La definición de una rampa de tipos y su continuación a lo largo de la experiencia de la aplicación proporcionará una excelente experiencia de usuario con una jerarquía de información coherente.</span><span class="sxs-lookup"><span data-stu-id="5c724-123">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="5c724-124">![Ejemplos de rampa de tipos](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5c724-124">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="5c724-125">*Definir la rampa de tipos y seguirla a lo largo de la experiencia de la aplicación*</span><span class="sxs-lookup"><span data-stu-id="5c724-125">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="5c724-126">Limitar las fuentes</span><span class="sxs-lookup"><span data-stu-id="5c724-126">Limit your fonts</span></span>

<span data-ttu-id="5c724-127">Evite usar más de dos familias de fuentes diferentes en un único contexto.</span><span class="sxs-lookup"><span data-stu-id="5c724-127">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="5c724-128">Demasiadas fuentes interrumpirán la armonía y la coherencia de su experiencia y dificultarán el consumo de información.</span><span class="sxs-lookup"><span data-stu-id="5c724-128">Too many fonts will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="5c724-129">En HoloLens, dado que la información se superpone en el entorno físico, el uso de demasiados estilos de fuente degradará la experiencia.</span><span class="sxs-lookup"><span data-stu-id="5c724-129">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="5c724-130">Segoe UI es la fuente de todos los diseños digitales de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c724-130">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="5c724-131">Se usa de forma coherente en el shell de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5c724-131">It's used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="5c724-132">Puede descargar el archivo de fuente de Segoe UI desde la [página del kit de herramientas de diseño de Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).</span><span class="sxs-lookup"><span data-stu-id="5c724-132">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="5c724-133">Más información sobre el Segoe UI tipo de letra</span><span class="sxs-lookup"><span data-stu-id="5c724-133">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="5c724-134">Evitar los pesos de fuente finos</span><span class="sxs-lookup"><span data-stu-id="5c724-134">Avoid thin font weights</span></span>

<span data-ttu-id="5c724-135">Evite usar pesos de fuentes ligeras o semiligeras para tamaños de tipo en 42 PT, ya que los trazos verticales finos vibrarán y disminuirán la legibilidad.</span><span class="sxs-lookup"><span data-stu-id="5c724-135">Avoid using light or semilight font weights for type sizes under 42 pt because thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="5c724-136">Las fuentes modernas con un grosor de trazo suficiente funcionan bien.</span><span class="sxs-lookup"><span data-stu-id="5c724-136">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="5c724-137">Por ejemplo, Helvetica y Arial son legibles en HoloLens con pesos normales o en negrita.</span><span class="sxs-lookup"><span data-stu-id="5c724-137">For example, Helvetica and Arial are legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="5c724-138">Color</span><span class="sxs-lookup"><span data-stu-id="5c724-138">Color</span></span>

<span data-ttu-id="5c724-139">En HoloLens, dado que los hologramas se construyen con un sistema de luz aditiva, el texto en blanco es muy legible.</span><span class="sxs-lookup"><span data-stu-id="5c724-139">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="5c724-140">Puede encontrar ejemplos de texto en blanco en el menú Inicio y en la barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5c724-140">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="5c724-141">Aunque el texto en blanco funciona bien sin una placa trasera en HoloLens, un fondo físico complejo podría dificultar la lectura del tipo.</span><span class="sxs-lookup"><span data-stu-id="5c724-141">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="5c724-142">Se recomienda usar texto en blanco en una placa trasera oscura o de color para mejorar el foco del usuario y minimizar la distracción de un fondo físico.</span><span class="sxs-lookup"><span data-stu-id="5c724-142">We recommend using white text on a dark or colored back plate to improve the user's focus and minimize the distraction from a physical background.</span></span>

<br>


<span data-ttu-id="5c724-143">![Se recomienda usar texto en blanco en una plancha de fondo oscuro o de color. ](images/typography-whiteonblack2-1000px.jpg)
 *Ejemplos de texto en blanco en una plancha de fondo oscuro o de color.*</span><span class="sxs-lookup"><span data-stu-id="5c724-143">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="5c724-144">Para usar texto oscuro, debe usar una placa trasera brillante para que sea legible.</span><span class="sxs-lookup"><span data-stu-id="5c724-144">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="5c724-145">En los sistemas de color aditivos, el color negro se muestra como transparente.</span><span class="sxs-lookup"><span data-stu-id="5c724-145">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="5c724-146">Esto significa que no verá el texto en negro sin una plancha de fondo de color.</span><span class="sxs-lookup"><span data-stu-id="5c724-146">This means you won't see the black text without a colored back plate.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5c724-147">![Ejemplos de blanco sobre negro y negro en texto en blanco](images/typography-whiteonblack.png)</span><span class="sxs-lookup"><span data-stu-id="5c724-147">![Examples of white on black and black on white text](images/typography-whiteonblack.png)</span></span><br>
        <span data-ttu-id="5c724-148">*Ejemplos de blanco sobre negro y negro en texto en blanco*</span><span class="sxs-lookup"><span data-stu-id="5c724-148">*Examples of white on black and black on white text*</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5c724-149">![Ejemplos de texto en negro en las aplicaciones del sistema: tienda y configuración](images/640px-typography-blackonwhite.jpg)</span><span class="sxs-lookup"><span data-stu-id="5c724-149">![Examples of black text in the system apps - Store and Settings](images/640px-typography-blackonwhite.jpg)</span></span><br>
        <span data-ttu-id="5c724-150">*Ejemplos de texto en negro en las aplicaciones del sistema: tienda y configuración*</span><span class="sxs-lookup"><span data-stu-id="5c724-150">*Examples of black text in the system apps - Store and Settings*</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a><span data-ttu-id="5c724-151">Tamaño de fuente recomendado</span><span class="sxs-lookup"><span data-stu-id="5c724-151">Recommended font size</span></span>

<span data-ttu-id="5c724-152">Como cabe esperar, los tamaños de tipo que usamos en un equipo o un dispositivo de tableta (normalmente entre 12 – 32pt.) son pequeños a una distancia de 2 metros.</span><span class="sxs-lookup"><span data-stu-id="5c724-152">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look small at a distance of 2 meters.</span></span> <span data-ttu-id="5c724-153">Depende de las características de cada fuente, pero, en general, el ángulo de visualización mínimo recomendado y el alto de la fuente para la legibilidad se encuentran en torno a 0.35 °-0,4 °/12.21-13.97 mm según nuestros estudios de investigación de usuarios.</span><span class="sxs-lookup"><span data-stu-id="5c724-153">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97 mm based on our user research studies.</span></span> <span data-ttu-id="5c724-154">Es aproximadamente 35-40 PT con el factor de escala introducido en la página de [texto en Unity](../develop/unity/text-in-unity.md) .</span><span class="sxs-lookup"><span data-stu-id="5c724-154">It's about 35-40 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md) page.</span></span> 

<span data-ttu-id="5c724-155">En el caso de la interacción cercana en 0,45 m (45 cm), el ángulo de visualización de la fuente mínima de lectura y el alto son 0,4 °-0,5 °/3.14 – 3,9 mm.</span><span class="sxs-lookup"><span data-stu-id="5c724-155">For the near interaction at 0.45 m(45 cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="5c724-156">Es aproximadamente 9-12 pt con el factor de escala introducido en el [texto en Unity](../develop/unity/text-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="5c724-156">It's about 9-12 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md).</span></span>

<span data-ttu-id="5c724-157">![Contenido del intervalo de interacción Near y Far ](images/typography-distance-1000px.jpg)
 *en el intervalo de interacción Near y Far*</span><span class="sxs-lookup"><span data-stu-id="5c724-157">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="5c724-158">El tamaño mínimo de fuente legible</span><span class="sxs-lookup"><span data-stu-id="5c724-158">The minimum legible font size</span></span>

| <span data-ttu-id="5c724-159">Distancia</span><span class="sxs-lookup"><span data-stu-id="5c724-159">Distance</span></span> | <span data-ttu-id="5c724-160">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="5c724-160">Viewing angle</span></span> | <span data-ttu-id="5c724-161">Alto de texto</span><span class="sxs-lookup"><span data-stu-id="5c724-161">Text height</span></span> | <span data-ttu-id="5c724-162">Tamaño de fuente \* \*</span><span class="sxs-lookup"><span data-stu-id="5c724-162">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="5c724-163">45 cm (distancia de manipulación directa)</span><span class="sxs-lookup"><span data-stu-id="5c724-163">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="5c724-164">0,4 °-0,5 °</span><span class="sxs-lookup"><span data-stu-id="5c724-164">0.4°-0.5°</span></span> | <span data-ttu-id="5c724-165">3.14:3,9 mm</span><span class="sxs-lookup"><span data-stu-id="5c724-165">3.14–3.9mm</span></span> | <span data-ttu-id="5c724-166">8.9:11.13 pt</span><span class="sxs-lookup"><span data-stu-id="5c724-166">8.9–11.13pt</span></span> |
| <span data-ttu-id="5c724-167">2 m</span><span class="sxs-lookup"><span data-stu-id="5c724-167">2 m</span></span> | <span data-ttu-id="5c724-168">0.35 °-0,4 °</span><span class="sxs-lookup"><span data-stu-id="5c724-168">0.35°-0.4°</span></span> | <span data-ttu-id="5c724-169">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="5c724-169">12.21–13.97mm</span></span> | <span data-ttu-id="5c724-170">34.63-39.58 PT</span><span class="sxs-lookup"><span data-stu-id="5c724-170">34.63-39.58 pt</span></span> |

### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="5c724-171">Tamaño de fuente cómodamente legible</span><span class="sxs-lookup"><span data-stu-id="5c724-171">The comfortably legible font size</span></span>

| <span data-ttu-id="5c724-172">Distancia</span><span class="sxs-lookup"><span data-stu-id="5c724-172">Distance</span></span> | <span data-ttu-id="5c724-173">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="5c724-173">Viewing angle</span></span> | <span data-ttu-id="5c724-174">Alto de texto</span><span class="sxs-lookup"><span data-stu-id="5c724-174">Text height</span></span> | <span data-ttu-id="5c724-175">Tamaño de fuente \* \*</span><span class="sxs-lookup"><span data-stu-id="5c724-175">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="5c724-176">45 cm (distancia de manipulación directa)</span><span class="sxs-lookup"><span data-stu-id="5c724-176">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="5c724-177">0,65 °-0,8 °</span><span class="sxs-lookup"><span data-stu-id="5c724-177">0.65°-0.8°</span></span> | <span data-ttu-id="5c724-178">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="5c724-178">5.1-6.3 mm</span></span> | <span data-ttu-id="5c724-179">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="5c724-179">14.47-17.8 pt</span></span> |
| <span data-ttu-id="5c724-180">2 m</span><span class="sxs-lookup"><span data-stu-id="5c724-180">2 m</span></span> | <span data-ttu-id="5c724-181">0,6 °-0,75 °</span><span class="sxs-lookup"><span data-stu-id="5c724-181">0.6°-0.75°</span></span> | <span data-ttu-id="5c724-182">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="5c724-182">20.9-26.2 mm</span></span> | <span data-ttu-id="5c724-183">59.4-74.2 PT</span><span class="sxs-lookup"><span data-stu-id="5c724-183">59.4-74.2 pt</span></span> |


<span data-ttu-id="5c724-184">Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos.</span><span class="sxs-lookup"><span data-stu-id="5c724-184">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="5c724-185">Evite usar familias de fuentes ligeras o semiligeras en tamaño reducido, ya que los trazos verticales finos vibrarán y disminuirán la legibilidad.</span><span class="sxs-lookup"><span data-stu-id="5c724-185">Avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="5c724-186">Las fuentes modernas con un grosor de trazo suficiente funcionan bien.</span><span class="sxs-lookup"><span data-stu-id="5c724-186">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="5c724-187">Por ejemplo, Helvetica y Arial parecen magníficas y son legibles en HoloLens con pesos normales o en negrita.</span><span class="sxs-lookup"><span data-stu-id="5c724-187">For example, Helvetica and Arial look gorgeous and are legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="5c724-188">**Para obtener información más detallada sobre el cálculo del tamaño de texto en Unity, consulte el [texto en Unity](../develop/unity/text-in-unity.md) .**</span><span class="sxs-lookup"><span data-stu-id="5c724-188">**For more detailed information about text size calculation in Unity, refer to [Text in Unity](../develop/unity/text-in-unity.md)**</span></span>

<span data-ttu-id="5c724-189">![Visualización del ángulo de ](images/Text_In_Unity_ViewingAngle.jpg)
 *visualización de la distancia, el ángulo y el alto del texto*</span><span class="sxs-lookup"><span data-stu-id="5c724-189">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

<br>

---

## <a name="resources"></a><span data-ttu-id="5c724-190">Recursos</span><span class="sxs-lookup"><span data-stu-id="5c724-190">Resources</span></span>

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[<span data-ttu-id="5c724-191">Fuentes Segoe</span><span class="sxs-lookup"><span data-stu-id="5c724-191">Segoe fonts</span></span>](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    <span data-ttu-id="5c724-192">(Archivo zip)</span><span class="sxs-lookup"><span data-stu-id="5c724-192">(Zip file)</span></span><br>
    ### <a name="hololens-fontbr"></a>[<span data-ttu-id="5c724-193">Fuente de HoloLens</span><span class="sxs-lookup"><span data-stu-id="5c724-193">HoloLens font</span></span>](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    <span data-ttu-id="5c724-194">(Archivo zip)</span><span class="sxs-lookup"><span data-stu-id="5c724-194">(Zip file)</span></span><br>
    <br>
    <span data-ttu-id="5c724-195">*Imagen: la fuente HoloLens proporciona los glifos de símbolos usados en Windows Mixed Reality.*</span><span class="sxs-lookup"><span data-stu-id="5c724-195">*Image: The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>
    :::column-end:::
        :::column:::
        ![La fuente HoloLens proporciona los glifos de símbolos usados en Windows Mixed Reality.](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a><span data-ttu-id="5c724-197">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5c724-197">See also</span></span>

* [<span data-ttu-id="5c724-198">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="5c724-198">Text in Unity</span></span>](../develop/unity/text-in-unity.md)
* [<span data-ttu-id="5c724-199">Color, luz y materiales</span><span class="sxs-lookup"><span data-stu-id="5c724-199">Color, light, and materials</span></span>](../color,-light-and-materials.md)
