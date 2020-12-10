---
title: Tabla periódica de los elementos
description: La tabla periódica de los elementos es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft. Aprende cómo diseñar una matriz de objetos en el espacio 3D con distintos tipos de superficie mediante una colección de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles, MRTK, kit de herramientas de realidad mixta, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: a4099c889fee886e63d3a8b773398a250621f26e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010186"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="c6739-105">Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="c6739-105">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="c6739-106">En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c6739-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="c6739-107">Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.</span><span class="sxs-lookup"><span data-stu-id="c6739-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="c6739-108">[La tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6739-108">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="c6739-109">Obtenga información sobre cómo diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una **[colección de objetos](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="c6739-109">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="c6739-110">También aprenderá a crear objetos interactivos que respondan a entradas estándar de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c6739-110">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="c6739-111">Puede usar los componentes de este proyecto para crear su propia experiencia de aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c6739-111">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabla de puntos de la aplicación Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="c6739-113">Vídeo de demostración</span><span class="sxs-lookup"><span data-stu-id="c6739-113">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="c6739-114">Grabado con HoloLens 2 mediante la captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c6739-114">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="c6739-115">Acerca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c6739-115">About the app</span></span>

<span data-ttu-id="c6739-116">La tabla periódica de los elementos visualiza los elementos químicos y cada una de sus propiedades en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="c6739-116">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="c6739-117">Incorpora las interacciones básicas de HoloLens, como mira fijamente y el aire TAP.</span><span class="sxs-lookup"><span data-stu-id="c6739-117">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="c6739-118">Los usuarios pueden obtener información sobre los elementos con modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="c6739-118">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="c6739-119">Pueden comprender visualmente el shell de electrones de un elemento y su núcleo, que se compone de protoneladas y neutrons.</span><span class="sxs-lookup"><span data-stu-id="c6739-119">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="c6739-120">Información previa</span><span class="sxs-lookup"><span data-stu-id="c6739-120">Background</span></span>

<span data-ttu-id="c6739-121">Después de haber experimentado HoloLens, sabía que quería experimentar con una aplicación de tabla periódica en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c6739-121">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="c6739-122">Puesto que cada elemento tiene muchos puntos de datos que se muestran con texto, pensé que sería una buena cuestión para explorar la composición tipográfica en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="c6739-122">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="c6739-123">Dar a los usuarios la oportunidad de visualizar el modelo de electrones del elemento fue otra parte interesante de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c6739-123">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="c6739-124">Diseño</span><span class="sxs-lookup"><span data-stu-id="c6739-124">Design</span></span>

<span data-ttu-id="c6739-125">En la vista predeterminada de la tabla periódica, se imaginan cuadros tridimensionales que contendrían el modelo de electrones de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="c6739-125">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="c6739-126">La superficie de cada cuadro sería traslúcida, de modo que el usuario podría obtener una idea aproximada del volumen del elemento.</span><span class="sxs-lookup"><span data-stu-id="c6739-126">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="c6739-127">Con fijamente y TAP, el usuario podría abrir una vista detallada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="c6739-127">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="c6739-128">Para que la transición entre la vista de tabla y la vista de detalles sea suave y natural, lo hice de manera similar a la interacción física de una caja de apertura en la vida real.</span><span class="sxs-lookup"><span data-stu-id="c6739-128">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="c6739-129">![Boceto de diseño](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6739-129">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="c6739-130">*Dibujos de diseño*</span><span class="sxs-lookup"><span data-stu-id="c6739-130">*Design sketches*</span></span>

<span data-ttu-id="c6739-131">En la vista de detalle, quería visualizar la información de cada elemento con texto representado con un gran espacio en 3D.</span><span class="sxs-lookup"><span data-stu-id="c6739-131">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="c6739-132">El modelo de electrones 3D animado se muestra en el área central y se puede ver desde distintos ángulos.</span><span class="sxs-lookup"><span data-stu-id="c6739-132">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interacción](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="c6739-134">![Prototipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6739-134">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="c6739-135">*Prototipos de interacción*</span><span class="sxs-lookup"><span data-stu-id="c6739-135">*Interaction prototypes*</span></span>

<span data-ttu-id="c6739-136">El usuario puede cambiar el tipo de superficie mediante la pulsación de los botones de la parte inferior de la tabla. puede cambiar entre plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="c6739-136">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="c6739-137">Controles comunes y patrones usados en esta aplicación</span><span class="sxs-lookup"><span data-stu-id="c6739-137">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="c6739-138">Objeto interactuable (botón)</span><span class="sxs-lookup"><span data-stu-id="c6739-138">Interactable object (button)</span></span>

<span data-ttu-id="c6739-139">El [objeto interactuable](../../design/interactable-object.md) es un objeto, que puede responder a entradas básicas de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c6739-139">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="c6739-140">Se proporciona como recurso prefabricado/script, que se puede aplicar fácilmente a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="c6739-140">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="c6739-141">Por ejemplo, puede hacer que una copa de café en la escena sea interactuable y responder a entradas como, por ejemplo, gestos de mira, navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="c6739-141">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="c6739-142">Más información</span><span class="sxs-lookup"><span data-stu-id="c6739-142">Learn more</span></span>](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="c6739-144">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="c6739-144">Object collection</span></span>

<span data-ttu-id="c6739-145">[Colección de objetos](../../design/object-collection.md) es un objeto, que le ayuda a diseñar varios objetos en varias formas.</span><span class="sxs-lookup"><span data-stu-id="c6739-145">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="c6739-146">Admite plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="c6739-146">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="c6739-147">Puede configurar propiedades adicionales como RADIUS, el número de filas y el espaciado.</span><span class="sxs-lookup"><span data-stu-id="c6739-147">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="c6739-148">Más información</span><span class="sxs-lookup"><span data-stu-id="c6739-148">Learn more</span></span>](../../design/object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="c6739-150">Detalles técnicos</span><span class="sxs-lookup"><span data-stu-id="c6739-150">Technical details</span></span>

<span data-ttu-id="c6739-151">Puede encontrar scripts y Prefabs para la tabla periódica de la aplicación Elements en el laboratorio de diseño de la [realidad mixta de github](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="c6739-151">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="c6739-152">Portabilidad de la historia de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c6739-152">Porting story for HoloLens 2</span></span>

<span data-ttu-id="c6739-153">Lea el artículo sobre cómo se actualizó la tabla periódica de la aplicación Elements con las interacciones instinctual de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c6739-153">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="c6739-154">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="c6739-154">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="c6739-155">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="c6739-155">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c6739-156"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="c6739-156"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="c6739-157">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c6739-157">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="c6739-158">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c6739-158">See also</span></span>

* <span data-ttu-id="c6739-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="c6739-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="c6739-160">[Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="c6739-160">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="c6739-161">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="c6739-161">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="c6739-162">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="c6739-162">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)