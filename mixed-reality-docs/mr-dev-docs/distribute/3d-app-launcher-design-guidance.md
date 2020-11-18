---
title: Guía de diseño del iniciador de aplicaciones 3D
description: Un iniciador de aplicaciones 3D es un objeto "físico" de la casa de la realidad mixta del usuario que puede seleccionar para iniciar una aplicación.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, iniciador de aplicaciones 3D, auriculares envolventes, cubo activo, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, UWP, Win32, iluminación, color
ms.openlocfilehash: a501b4bdc86df17f6d005c2f7ccf4fe6a94a4b43
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703481"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="32b2c-104">Guía de diseño del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="32b2c-104">3D app launcher design guidance</span></span>

<span data-ttu-id="32b2c-105">Cuando se coloca en un casco de Windows Mixed Reality inmersivo (VR), se introduce la Página principal de Windows Mixed Reality, visualizada como una casa en un acantilado rodeado por montañas y agua (aunque puede [elegir otros entornos e incluso crear el suyo propio](../design/add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="32b2c-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="32b2c-106">Dentro del espacio de este hogar, un usuario puede organizar y organizar los objetos 3D y las aplicaciones que le interesan de la forma que deseen.</span><span class="sxs-lookup"><span data-stu-id="32b2c-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="32b2c-107">Un **iniciador de aplicaciones 3D** es un objeto "físico" de la casa de la realidad mixta del usuario que puede seleccionar para iniciar una aplicación.</span><span class="sxs-lookup"><span data-stu-id="32b2c-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="32b2c-108">![Ejemplo: selector de aplicaciones 3D de pájaros de punto flotante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="32b2c-109">*Ejemplo de selector de aplicaciones 3D de pájaros de flotación (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="32b2c-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="32b2c-110">proceso de creación del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="32b2c-110">3D app launcher creation process</span></span>

<span data-ttu-id="32b2c-111">Hay tres pasos para crear un iniciador de aplicaciones 3D:</span><span class="sxs-lookup"><span data-stu-id="32b2c-111">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="32b2c-112">Diseño y concepto (este artículo)</span><span class="sxs-lookup"><span data-stu-id="32b2c-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="32b2c-113">Modelado y exportación</span><span class="sxs-lookup"><span data-stu-id="32b2c-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="32b2c-114">Integrarlo en la aplicación:</span><span class="sxs-lookup"><span data-stu-id="32b2c-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="32b2c-115">Aplicaciones para UWP</span><span class="sxs-lookup"><span data-stu-id="32b2c-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="32b2c-116">Aplicaciones de Win32</span><span class="sxs-lookup"><span data-stu-id="32b2c-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="32b2c-117">Conceptos de diseño</span><span class="sxs-lookup"><span data-stu-id="32b2c-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="32b2c-118">Fantástico, aún conocido</span><span class="sxs-lookup"><span data-stu-id="32b2c-118">Fantastic yet familiar</span></span>

<span data-ttu-id="32b2c-119">El entorno de Windows Mixed Reality en el que se encuentra su iniciador de aplicaciones es parte familiar, parte fantástica o Sci-Fi.</span><span class="sxs-lookup"><span data-stu-id="32b2c-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="32b2c-120">Los mejores iniciadores siguen las reglas de este mundo.</span><span class="sxs-lookup"><span data-stu-id="32b2c-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="32b2c-121">Piense en cómo puede tomar un objeto conocido y representativo de la aplicación, pero doblar algunas de las reglas de realidad real.</span><span class="sxs-lookup"><span data-stu-id="32b2c-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="32b2c-122">Se generará una instrucción mágica.</span><span class="sxs-lookup"><span data-stu-id="32b2c-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="32b2c-123">Intuitivo</span><span class="sxs-lookup"><span data-stu-id="32b2c-123">Intuitive</span></span>

<span data-ttu-id="32b2c-124">Al mirar el iniciador de la aplicación, su finalidad es iniciar la aplicación: debe ser obvio y no debe causar ninguna confusión.</span><span class="sxs-lookup"><span data-stu-id="32b2c-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="32b2c-125">Por ejemplo, asegúrese de que el iniciador es un representante tan obvio de la aplicación que no se confundirá con una pieza de Décor en el centro de acantilado.</span><span class="sxs-lookup"><span data-stu-id="32b2c-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="32b2c-126">El iniciador de la aplicación debe invitar a los usuarios a que lo toquen o lo seleccionen.</span><span class="sxs-lookup"><span data-stu-id="32b2c-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="32b2c-127">![Ejemplo: selector de aplicaciones 3D de nota nueva](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="32b2c-128">*Ejemplo de iniciador de aplicaciones 3D de nota nueva (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="32b2c-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="32b2c-129">Escala de inicio</span><span class="sxs-lookup"><span data-stu-id="32b2c-129">Home scale</span></span>

<span data-ttu-id="32b2c-130">los iniciadores de aplicaciones 3D viven en la casa de acantilado y su tamaño predeterminado deben tener sentido con los demás objetos "físicos" del espacio.</span><span class="sxs-lookup"><span data-stu-id="32b2c-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="32b2c-131">Si coloca el iniciador junto a, por ejemplo, una planta de casa o algún mobiliario, debe sentir en casa y en el tamaño.</span><span class="sxs-lookup"><span data-stu-id="32b2c-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="32b2c-132">Un buen punto de partida es ver cómo observa 30 centímetros cúbicos, pero recuerde que los usuarios pueden escalar o reducir verticalmente si lo desean.</span><span class="sxs-lookup"><span data-stu-id="32b2c-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="32b2c-133">Propiedad propia</span><span class="sxs-lookup"><span data-stu-id="32b2c-133">Own-able</span></span>

<span data-ttu-id="32b2c-134">El iniciador de aplicaciones debe sentirse como un objeto al que le encantaría tener una persona en su espacio.</span><span class="sxs-lookup"><span data-stu-id="32b2c-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="32b2c-135">Se encontrarán prácticamente con estas cosas, por lo que el selector debe sentirse como algo que el usuario pensó que era lo suficientemente conveniente para buscar y mantener cerca.</span><span class="sxs-lookup"><span data-stu-id="32b2c-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="32b2c-136">![Ejemplo: astro Warp 3D del iniciador de aplicaciones](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="32b2c-137">*Ejemplo de selector de aplicación de Astro Warp 3D (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="32b2c-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="32b2c-138">Reconocible</span><span class="sxs-lookup"><span data-stu-id="32b2c-138">Recognizable</span></span>

<span data-ttu-id="32b2c-139">El selector de aplicaciones 3D debe expresar al instante "la marca de la aplicación" para las personas que lo ven.</span><span class="sxs-lookup"><span data-stu-id="32b2c-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="32b2c-140">Si tiene un carácter de estrella o un objeto que se puede identificar especialmente en la aplicación, se recomienda usarlo como gran parte del diseño.</span><span class="sxs-lookup"><span data-stu-id="32b2c-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="32b2c-141">En un mundo de realidad mixta, un objeto dibujará más interés de los usuarios que solo un logotipo por sí solo.</span><span class="sxs-lookup"><span data-stu-id="32b2c-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="32b2c-142">Los objetos reconocibles comunican la marca rápida y claramente.</span><span class="sxs-lookup"><span data-stu-id="32b2c-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="32b2c-143">Volumétricos</span><span class="sxs-lookup"><span data-stu-id="32b2c-143">Volumetric</span></span>

<span data-ttu-id="32b2c-144">La aplicación merece más que simplemente colocar su logotipo en un plano plano y llamarlo un día.</span><span class="sxs-lookup"><span data-stu-id="32b2c-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="32b2c-145">El iniciador debe sentirse como un objeto físico emocionante, 3D en el espacio del usuario.</span><span class="sxs-lookup"><span data-stu-id="32b2c-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="32b2c-146">Un buen enfoque es imaginar que la aplicación iba a tener un globo en el día de Navidad de Macy.</span><span class="sxs-lookup"><span data-stu-id="32b2c-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="32b2c-147">Pregúntese a sí mismo, ¿qué me gustaría que mis personas se tratara de la calle?</span><span class="sxs-lookup"><span data-stu-id="32b2c-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="32b2c-148">¿Qué aspecto sería fantástico en todos los ángulos de visualización?</span><span class="sxs-lookup"><span data-stu-id="32b2c-148">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="32b2c-149">![Solo logotipo ](images/20171016-140436-mixedreality-640px.jpg) *del logotipo*</span><span class="sxs-lookup"><span data-stu-id="32b2c-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="32b2c-150">![Más reconocible con un carácter ](images/20171016-140557-mixedreality-640px.jpg) *más reconocible con un carácter*</span><span class="sxs-lookup"><span data-stu-id="32b2c-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="32b2c-151">![Un enfoque plano, no sorprendentemente, se siente plano plano ](images/20171016-155101-mixedreality-640px.jpg) *, no sorprendentemente* .</span><span class="sxs-lookup"><span data-stu-id="32b2c-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="32b2c-152">![Un enfoque volumétrico mejor exhibe el enfoque volumétrico de la aplicación para mostrar ](images/20171016-161407-mixedreality-640px.jpg) *mejor la aplicación*</span><span class="sxs-lookup"><span data-stu-id="32b2c-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="32b2c-153">Sugerencias para buenos modelos 3D</span><span class="sxs-lookup"><span data-stu-id="32b2c-153">Tips for good 3D models</span></span>

* <span data-ttu-id="32b2c-154">Cuando planee las dimensiones del iniciador de aplicaciones, capte aproximadamente un cubo 30cm.</span><span class="sxs-lookup"><span data-stu-id="32b2c-154">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="32b2c-155">Por lo tanto, una relación de tamaño de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="32b2c-155">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="32b2c-156">Los modelos deben tener menos de 10.000 polígonos.</span><span class="sxs-lookup"><span data-stu-id="32b2c-156">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="32b2c-157">Más información sobre recuentos de triángulos y niveles de detalles (LODs)</span><span class="sxs-lookup"><span data-stu-id="32b2c-157">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="32b2c-158">Pruebe en un casco envolvente.</span><span class="sxs-lookup"><span data-stu-id="32b2c-158">Test on an immersive headset.</span></span>
* <span data-ttu-id="32b2c-159">Cree detalles en la geometría del modelo siempre que sea posible: no se base en las texturas para obtener detalles.</span><span class="sxs-lookup"><span data-stu-id="32b2c-159">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="32b2c-160">Compilar la geometría cerrada con "ajuste del agua".</span><span class="sxs-lookup"><span data-stu-id="32b2c-160">Build “water tight” closed geometry.</span></span> <span data-ttu-id="32b2c-161">Ningún hueco que no esté modelado en.</span><span class="sxs-lookup"><span data-stu-id="32b2c-161">No holes that are not modeled in.</span></span>
* <span data-ttu-id="32b2c-162">Use materiales naturales en el objeto.</span><span class="sxs-lookup"><span data-stu-id="32b2c-162">Use natural materials in your object.</span></span> <span data-ttu-id="32b2c-163">Imagine que la diseña en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="32b2c-163">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="32b2c-164">Asegúrese de que el modelo se lea bien en diferentes distancias y tamaños.</span><span class="sxs-lookup"><span data-stu-id="32b2c-164">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="32b2c-165">Cuando el modelo esté listo, lea las instrucciones de [exportación de activos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="32b2c-165">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="32b2c-166">![Modelo con detalles sutiles en la textura](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-166">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="32b2c-167">*Modelo con detalles sutiles en la textura*</span><span class="sxs-lookup"><span data-stu-id="32b2c-167">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="32b2c-168">Qué evitar</span><span class="sxs-lookup"><span data-stu-id="32b2c-168">What to avoid</span></span>

* <span data-ttu-id="32b2c-169">No utilice detalles de contraste alto ni texturas y patrones pequeños y ocupados.</span><span class="sxs-lookup"><span data-stu-id="32b2c-169">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="32b2c-170">No use geometría fina: no funciona bien a la larga y dará un alias incorrecto.</span><span class="sxs-lookup"><span data-stu-id="32b2c-170">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="32b2c-171">No permita que partes del modelo se extienda demasiado más allá de la relación de tamaño de 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="32b2c-171">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="32b2c-172">Se crearán problemas de escalado.</span><span class="sxs-lookup"><span data-stu-id="32b2c-172">It will create scaling problems.</span></span>

<span data-ttu-id="32b2c-173">![Evitar patrones de alto contraste y pequeño ocupado](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-173">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="32b2c-174">*Evite patrones de alto contraste, pequeños y ocupados*</span><span class="sxs-lookup"><span data-stu-id="32b2c-174">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="32b2c-175">Cómo controlar el tipo</span><span class="sxs-lookup"><span data-stu-id="32b2c-175">How to handle type</span></span>

* <span data-ttu-id="32b2c-176">Se recomienda que el tipo comprenda aproximadamente 1/3 del iniciador de la aplicación (o más).</span><span class="sxs-lookup"><span data-stu-id="32b2c-176">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="32b2c-177">El tipo es lo principal que da a los usuarios una idea de que el iniciador es, de hecho, un iniciador para que sea estupendo si es bastante importante.</span><span class="sxs-lookup"><span data-stu-id="32b2c-177">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="32b2c-178">Evite hacer el tipo superwide: intente mantenerlo dentro de los límites de las dimensiones básicas de los iniciadores de aplicaciones (más o menos).</span><span class="sxs-lookup"><span data-stu-id="32b2c-178">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="32b2c-179">El tipo plano puede funcionar, pero tenga en cuenta que puede ser difícil de ver desde determinados ángulos y en determinados entornos.</span><span class="sxs-lookup"><span data-stu-id="32b2c-179">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="32b2c-180">Considere la posibilidad de colocarlo en un objeto sólido o telón de fondo para ayudarle con esto.</span><span class="sxs-lookup"><span data-stu-id="32b2c-180">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="32b2c-181">La adición de una dimensión a su tipo se siente agradable en 3D.</span><span class="sxs-lookup"><span data-stu-id="32b2c-181">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="32b2c-182">Sombrear los lados del tipo con un color más oscuro, puede ayudar a mejorar la legibilidad.</span><span class="sxs-lookup"><span data-stu-id="32b2c-182">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="32b2c-183">![El tipo plano sin telón de fondo puede ser difícil de ver desde determinados ángulos y en determinados ](images/flattype-640px.png) *tipos planos de entornos sin un telón de fondo puede ser difícil de ver desde determinados ángulos y en determinados entornos* .</span><span class="sxs-lookup"><span data-stu-id="32b2c-183">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="32b2c-184">![El tipo con un telón de fondo integrado puede funcionar bien ](images/flattypeandbkg-640px.png) *con un telón de fondo integrado* .</span><span class="sxs-lookup"><span data-stu-id="32b2c-184">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="32b2c-185">![El tipo extruido puede funcionar bien si se sombrean los lados el ](images/20171016-160221-mixedreality-640px.jpg) *tipo extruido puede funcionar bien si se sombrean los lados* .</span><span class="sxs-lookup"><span data-stu-id="32b2c-185">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="32b2c-186">**Tipos de colores que funcionan**</span><span class="sxs-lookup"><span data-stu-id="32b2c-186">**Type colors that work**</span></span>

* <span data-ttu-id="32b2c-187">Blanco</span><span class="sxs-lookup"><span data-stu-id="32b2c-187">White</span></span>
* <span data-ttu-id="32b2c-188">Negro</span><span class="sxs-lookup"><span data-stu-id="32b2c-188">Black</span></span>
* <span data-ttu-id="32b2c-189">Color semisaturado brillante</span><span class="sxs-lookup"><span data-stu-id="32b2c-189">Bright semi-saturated color</span></span>

<span data-ttu-id="32b2c-190">![Escriba los colores que funcionan.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-190">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="32b2c-191">*Tipos de colores que funcionan*</span><span class="sxs-lookup"><span data-stu-id="32b2c-191">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="32b2c-192">Colores para evitar</span><span class="sxs-lookup"><span data-stu-id="32b2c-192">Colors to avoid</span></span>

<span data-ttu-id="32b2c-193">Los colores de tipo que causan problemas son:</span><span class="sxs-lookup"><span data-stu-id="32b2c-193">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="32b2c-194">Tonos medios</span><span class="sxs-lookup"><span data-stu-id="32b2c-194">Mid-tones</span></span>
* <span data-ttu-id="32b2c-195">Gris</span><span class="sxs-lookup"><span data-stu-id="32b2c-195">Gray</span></span>
* <span data-ttu-id="32b2c-196">Colores saturados o colores dessaturados</span><span class="sxs-lookup"><span data-stu-id="32b2c-196">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="32b2c-197">![Escriba los colores que causan problemas.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-197">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="32b2c-198">*Colores de tipo que causan problemas*</span><span class="sxs-lookup"><span data-stu-id="32b2c-198">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="32b2c-199">Iluminación</span><span class="sxs-lookup"><span data-stu-id="32b2c-199">Lighting</span></span>

<span data-ttu-id="32b2c-200">La iluminación del iniciador de la aplicación procede del entorno del centro de acantilado.</span><span class="sxs-lookup"><span data-stu-id="32b2c-200">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="32b2c-201">Asegúrese de probar el iniciador en varios lugares de la casa para que tenga buenos puntos de luz y sombras.</span><span class="sxs-lookup"><span data-stu-id="32b2c-201">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="32b2c-202">La buena noticia es que, si ha seguido las otras instrucciones de diseño de este documento, el iniciador debe tener una forma bastante buena para la mayor iluminación en la casa del acantilado.</span><span class="sxs-lookup"><span data-stu-id="32b2c-202">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="32b2c-203">Los buenos lugares para probar el aspecto del iniciador en las diversas luces del entorno son el estudio, la sala multimedia, en cualquier parte fuera y en el patio de vuelta (el área concreta con el césped).</span><span class="sxs-lookup"><span data-stu-id="32b2c-203">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="32b2c-204">Otra buena prueba es colocarla en la mitad de la luz y la mitad de la sombra y ver su aspecto.</span><span class="sxs-lookup"><span data-stu-id="32b2c-204">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="32b2c-205">![Asegúrese de que el iniciador tiene buenos problemas tanto en las luces como en las sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="32b2c-205">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="32b2c-206">*Asegúrese de que el iniciador tiene buenos problemas tanto en las luces como en las sombras*</span><span class="sxs-lookup"><span data-stu-id="32b2c-206">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="32b2c-207">Texturización</span><span class="sxs-lookup"><span data-stu-id="32b2c-207">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="32b2c-208">Crear las texturas</span><span class="sxs-lookup"><span data-stu-id="32b2c-208">Authoring your textures</span></span>

<span data-ttu-id="32b2c-209">El formato final del iniciador de aplicaciones 3D será un archivo. glb, que se realiza mediante la canalización PBR (representación basada físicamente).</span><span class="sxs-lookup"><span data-stu-id="32b2c-209">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="32b2c-210">Esto puede ser un proceso complicado; ahora es un buen momento para emplear un artista técnico si aún no lo ha hecho.</span><span class="sxs-lookup"><span data-stu-id="32b2c-210">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="32b2c-211">Si es Brave implementación personal-ER, dedicar tiempo a [investigar y obtener información sobre la terminología de PBR](https://wiki.polycount.com/wiki/PBR) y lo que está ocurriendo en el capó antes de comenzar le ayudará a evitar errores comunes.</span><span class="sxs-lookup"><span data-stu-id="32b2c-211">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="32b2c-212">![Ejemplo: aplicación de notas nuevas](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="32b2c-212">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="32b2c-213">*Ejemplo de iniciador de aplicaciones 3D de nota nueva (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="32b2c-213">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="32b2c-214">Herramienta de creación recomendada</span><span class="sxs-lookup"><span data-stu-id="32b2c-214">Recommended authoring tool</span></span>

<span data-ttu-id="32b2c-215">Se recomienda usar el [pintor de sustancias](https://www.allegorithmic.com/products/substance-painter) de Allegorithmic para crear el archivo final.</span><span class="sxs-lookup"><span data-stu-id="32b2c-215">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="32b2c-216">Si no está familiarizado con la creación de sombreadores de PBR en el pintor de sustancias, este es un [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="32b2c-216">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="32b2c-217">(Como alternativa [en 3D](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)o [marmoset toolbag](https://www.marmoset.co/toolbag/) también funcionaría si está más familiarizado con uno de ellos).</span><span class="sxs-lookup"><span data-stu-id="32b2c-217">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="32b2c-218">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="32b2c-218">Best practices</span></span>

* <span data-ttu-id="32b2c-219">Si el objeto iniciador de la aplicación se creó para PBR, debe ser bastante sencillo convertirlo en el entorno de la casa de acantilado.</span><span class="sxs-lookup"><span data-stu-id="32b2c-219">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="32b2c-220">Nuestro sombreador espera un flujo de trabajo de metal/rugosidad: el sombreador de PBR inreal es un fax de cierre.</span><span class="sxs-lookup"><span data-stu-id="32b2c-220">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="32b2c-221">Al exportar las texturas, tenga en cuenta los [tamaños de textura recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .</span><span class="sxs-lookup"><span data-stu-id="32b2c-221">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="32b2c-222">Asegúrese de crear los objetos para la iluminación en tiempo real, lo que significa:</span><span class="sxs-lookup"><span data-stu-id="32b2c-222">Make sure to build your objects for real-time lighting — this means:</span></span>
  * <span data-ttu-id="32b2c-223">Evitar sombras cocidas (o sombras pintadas)</span><span class="sxs-lookup"><span data-stu-id="32b2c-223">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="32b2c-224">Evitar la iluminación horneada en las texturas</span><span class="sxs-lookup"><span data-stu-id="32b2c-224">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="32b2c-225">Use uno de los paquetes de creación de material de PBR para obtener los mapas correctos generados para nuestro sombreador</span><span class="sxs-lookup"><span data-stu-id="32b2c-225">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="32b2c-226">Consulte también</span><span class="sxs-lookup"><span data-stu-id="32b2c-226">See also</span></span>

* [<span data-ttu-id="32b2c-227">Cree modelos 3D para su uso en la Página principal de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="32b2c-227">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="32b2c-228">Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)</span><span class="sxs-lookup"><span data-stu-id="32b2c-228">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="32b2c-229">Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)</span><span class="sxs-lookup"><span data-stu-id="32b2c-229">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
