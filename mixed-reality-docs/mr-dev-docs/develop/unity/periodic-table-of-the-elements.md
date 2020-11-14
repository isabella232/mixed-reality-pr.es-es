---
title: Tabla periódica de los elementos
description: La tabla periódica de los elementos es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft, donde puede aprender a diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una colección de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles
ms.openlocfilehash: 82ffa19b27c1d2687b67df659cb3bb50544748fc
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573269"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="8a4dc-104">Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="8a4dc-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="8a4dc-105">En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="8a4dc-106">Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="8a4dc-107">[La tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="8a4dc-108">Con este proyecto, puede obtener información sobre cómo diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una **[colección de objetos](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="8a4dc-109">También aprenderá a crear objetos interactivos que respondan a entradas estándar de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="8a4dc-110">Puede usar los componentes de este proyecto para crear su propia experiencia de aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabla de puntos de la aplicación Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="8a4dc-112">Vídeo de demostración</span><span class="sxs-lookup"><span data-stu-id="8a4dc-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="8a4dc-113">Grabado con HoloLens 2 mediante la captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="8a4dc-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="8a4dc-114">Acerca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="8a4dc-114">About the app</span></span>

<span data-ttu-id="8a4dc-115">La tabla periódica de los elementos visualiza los elementos químicos y cada una de sus propiedades en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="8a4dc-116">Incorpora las interacciones básicas de HoloLens, como mira fijamente y el aire TAP.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="8a4dc-117">Los usuarios pueden obtener información sobre los elementos con modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="8a4dc-118">Pueden comprender visualmente el shell de electrones de un elemento y su núcleo, que se compone de protoneladas y neutrons.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="8a4dc-119">Información previa</span><span class="sxs-lookup"><span data-stu-id="8a4dc-119">Background</span></span>

<span data-ttu-id="8a4dc-120">Después de la primera vez que se experimentó HoloLens, una aplicación de tabla periódica era una idea de la que quería experimentar en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-120">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="8a4dc-121">Puesto que cada elemento tiene muchos puntos de datos que se muestran con texto, pensé que sería una buena cuestión para explorar la composición tipográfica en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="8a4dc-122">Ser capaz de visualizar el modelo de electrones del elemento fue otra parte interesante de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-122">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="8a4dc-123">Diseño</span><span class="sxs-lookup"><span data-stu-id="8a4dc-123">Design</span></span>

<span data-ttu-id="8a4dc-124">En la vista predeterminada de la tabla periódica, se imaginan cuadros tridimensionales que contendrían el modelo de electrones de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="8a4dc-125">La superficie de cada cuadro sería traslúcida, de modo que el usuario podría obtener una idea aproximada del volumen del elemento.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="8a4dc-126">Con fijamente y TAP, el usuario podría abrir una vista detallada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="8a4dc-127">Para que la transición entre la vista de tabla y la vista de detalles sea suave y natural, lo hice de manera similar a la interacción física de una caja de apertura en la vida real.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="8a4dc-128">![Boceto de diseño](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="8a4dc-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="8a4dc-129">*Dibujos de diseño*</span><span class="sxs-lookup"><span data-stu-id="8a4dc-129">*Design sketches*</span></span>

<span data-ttu-id="8a4dc-130">En la vista de detalle, quería visualizar la información de cada elemento con texto representado con un gran espacio en 3D.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="8a4dc-131">El modelo de electrones 3D animado se muestra en el área central y se puede ver desde distintos ángulos.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interacción](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="8a4dc-133">![Prototipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="8a4dc-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="8a4dc-134">*Prototipos de interacción*</span><span class="sxs-lookup"><span data-stu-id="8a4dc-134">*Interaction prototypes*</span></span>

<span data-ttu-id="8a4dc-135">El usuario puede cambiar el tipo de superficie mediante la pulsación de los botones de la parte inferior de la tabla. puede cambiar entre plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="8a4dc-136">Controles comunes y patrones usados en esta aplicación</span><span class="sxs-lookup"><span data-stu-id="8a4dc-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="8a4dc-137">Objeto interactuable (botón)</span><span class="sxs-lookup"><span data-stu-id="8a4dc-137">Interactable object (button)</span></span>

<span data-ttu-id="8a4dc-138">[Objeto interactuable](../../design/interactable-object.md) es un objeto que puede responder a entradas básicas de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-138">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="8a4dc-139">Se proporciona como recurso prefabricado/script, que se puede aplicar fácilmente a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-139">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="8a4dc-140">Por ejemplo, puede hacer que una copa de café en la escena sea interactuable y responder a entradas como, por ejemplo, gestos de toque, pulsación de aire, navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="8a4dc-141">Más información</span><span class="sxs-lookup"><span data-stu-id="8a4dc-141">Learn more</span></span>](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="8a4dc-143">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="8a4dc-143">Object collection</span></span>

<span data-ttu-id="8a4dc-144">[Colección de objetos](../../design/object-collection.md) es un objeto que ayuda a diseñar varios objetos en varias formas.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-144">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="8a4dc-145">Admite plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-145">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="8a4dc-146">Puede configurar propiedades adicionales como RADIUS, el número de filas y el espaciado.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="8a4dc-147">Más información</span><span class="sxs-lookup"><span data-stu-id="8a4dc-147">Learn more</span></span>](../../design/object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="8a4dc-149">Detalles técnicos</span><span class="sxs-lookup"><span data-stu-id="8a4dc-149">Technical details</span></span>

<span data-ttu-id="8a4dc-150">Puede encontrar scripts y Prefabs para la tabla periódica de la aplicación Elements en el laboratorio de diseño de la [realidad mixta de github](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="8a4dc-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="8a4dc-151">Portabilidad de la historia de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8a4dc-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="8a4dc-152">Lea el artículo sobre cómo se actualizó la tabla periódica de la aplicación Elements con las interacciones instinctual de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8a4dc-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="8a4dc-153">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="8a4dc-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="8a4dc-154">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="8a4dc-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="8a4dc-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="8a4dc-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="8a4dc-156">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="8a4dc-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8a4dc-157">Consulte también</span><span class="sxs-lookup"><span data-stu-id="8a4dc-157">See also</span></span>

* <span data-ttu-id="8a4dc-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="8a4dc-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="8a4dc-159">[Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="8a4dc-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="8a4dc-160">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="8a4dc-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="8a4dc-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="8a4dc-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)