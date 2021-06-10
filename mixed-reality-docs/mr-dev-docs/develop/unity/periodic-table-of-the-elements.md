---
title: Tabla periódica de los elementos
description: Obtenga información sobre cómo crear una matriz de objetos en un espacio 3D con varios tipos de superficie mediante una colección Object con la aplicación de ejemplo Tabla periódica de elementos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles, MRTK, kit de herramientas de Mixed Reality, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743409"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="1a6ff-104">Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="1a6ff-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="1a6ff-105">En este artículo se describe un ejemplo exploratorio que hemos creado en [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un lugar donde compartimos nuestros aprendizajes y sugerencias para el desarrollo de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="1a6ff-106">Nuestros artículos y código relacionados con el diseño evolucionarán a medida que realicemos nuevas des descubrimientos.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="1a6ff-107">[Tabla periódica de los elementos es](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) una aplicación de ejemplo de código abierto de Microsoft Mixed Reality Design Labs.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="1a6ff-108">Obtenga información sobre cómo crear una matriz de objetos en un espacio 3D con varios tipos de superficie mediante una **[colección object](../../design/object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="1a6ff-109">Aprenda también a crear objetos interactuables que respondan a entradas estándar de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="1a6ff-110">Puede usar los componentes de este proyecto para crear su propia experiencia de aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabla de períodos de la aplicación Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="1a6ff-112">Vídeo de demostración</span><span class="sxs-lookup"><span data-stu-id="1a6ff-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="1a6ff-113">Registrado con HoloLens 2 mediante Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="1a6ff-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="1a6ff-114">Acerca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="1a6ff-114">About the app</span></span>

<span data-ttu-id="1a6ff-115">La tabla periódica de los elementos visualiza los elementos químicas y cada una de sus propiedades en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="1a6ff-116">Incorpora las interacciones básicas de HoloLens, como la mirada y el toque en el aire.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="1a6ff-117">Los usuarios pueden obtener información sobre los elementos con modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="1a6ff-118">Pueden comprender visualmente el shell de electrones de un elemento y su núcleo, que se compone de protons y neutrones.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="1a6ff-119">Información previa</span><span class="sxs-lookup"><span data-stu-id="1a6ff-119">Background</span></span>

<span data-ttu-id="1a6ff-120">Después de experimentar HoloLens por primera vez, sabía que quería experimentar con una aplicación de tabla periódica en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="1a6ff-121">Dado que cada elemento tiene muchos puntos de datos que se muestran con texto, creo que sería una gran cuestión para explorar la composición tipográfica en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="1a6ff-122">Dar a los usuarios la oportunidad de visualizar el modelo de electrones del elemento fue otra parte interesante de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="1a6ff-123">Diseño</span><span class="sxs-lookup"><span data-stu-id="1a6ff-123">Design</span></span>

<span data-ttu-id="1a6ff-124">Para la vista predeterminada de la tabla periódica, imagine cuadros tridimensionales que contendrán el modelo de electrones de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="1a6ff-125">La superficie de cada cuadro sería translúcida para que el usuario pudiera obtener una idea aproximada del volumen del elemento.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="1a6ff-126">Con la mirada y la pulsación en el aire, el usuario podría abrir una vista detallada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="1a6ff-127">Para que la transición entre la vista de tabla y la vista de detalles sea fluida y natural, la he hecho similar a la interacción física de una apertura de cuadro en la vida real.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="1a6ff-128">![Diseño del boceto](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a6ff-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="1a6ff-129">*Diseño de bocetos*</span><span class="sxs-lookup"><span data-stu-id="1a6ff-129">*Design sketches*</span></span>

<span data-ttu-id="1a6ff-130">En la vista detallada, quería visualizar la información de cada elemento con texto representado de forma excelente en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="1a6ff-131">El modelo de electrones 3D animado se muestra en el área central y se puede ver desde distintos ángulos.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interacción](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="1a6ff-133">![Prototipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a6ff-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="1a6ff-134">*Prototipos de interacción*</span><span class="sxs-lookup"><span data-stu-id="1a6ff-134">*Interaction prototypes*</span></span>

<span data-ttu-id="1a6ff-135">El usuario puede cambiar el tipo de superficie pulsando en el aire los botones de la parte inferior de la tabla; puede cambiar entre plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="1a6ff-136">Controles y patrones comunes usados en esta aplicación</span><span class="sxs-lookup"><span data-stu-id="1a6ff-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="1a6ff-137">Objeto interactuable (botón)</span><span class="sxs-lookup"><span data-stu-id="1a6ff-137">Interactable object (button)</span></span>

<span data-ttu-id="1a6ff-138">[Un objeto interactuable](../../design/interactable-object.md) es un objeto que puede responder a entradas básicas de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="1a6ff-139">Se proporciona como prefab/script, que se puede aplicar fácilmente a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="1a6ff-140">Por ejemplo, puede hacer que una cafetera de la escena sea interactuable y responder a entradas como mirada, pulsación en el aire, navegación y gestos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="1a6ff-141">Más información</span><span class="sxs-lookup"><span data-stu-id="1a6ff-141">Learn more</span></span>](../../design/interactable-object.md)

![Objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="1a6ff-143">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="1a6ff-143">Object collection</span></span>

<span data-ttu-id="1a6ff-144">[La colección](../../design/object-collection.md) de objetos es un objeto que ayuda a crear varios objetos de varias formas.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="1a6ff-145">Admite plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="1a6ff-146">Puede configurar propiedades adicionales, como el radio, el número de filas y el espaciado.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="1a6ff-147">Más información</span><span class="sxs-lookup"><span data-stu-id="1a6ff-147">Learn more</span></span>](../../design/object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="1a6ff-149">Detalles técnicos</span><span class="sxs-lookup"><span data-stu-id="1a6ff-149">Technical details</span></span>

<span data-ttu-id="1a6ff-150">Puede encontrar scripts y objetos prefabs para la aplicación Tabla periódica de elementos en [Mixed Reality Design Labs de GitHub.](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="1a6ff-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="1a6ff-151">Historia de porte para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1a6ff-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="1a6ff-152">Lea la historia sobre cómo se actualizó la aplicación Tabla periódica de elementos con HoloLens 2 interacciones instintiva de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1a6ff-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="1a6ff-153">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="1a6ff-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="1a6ff-154">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="1a6ff-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="1a6ff-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="1a6ff-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="1a6ff-156">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="1a6ff-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="1a6ff-157">Vea también</span><span class="sxs-lookup"><span data-stu-id="1a6ff-157">See also</span></span>

* <span data-ttu-id="1a6ff-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="1a6ff-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="1a6ff-159">[Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="1a6ff-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="1a6ff-160">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="1a6ff-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="1a6ff-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="1a6ff-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)