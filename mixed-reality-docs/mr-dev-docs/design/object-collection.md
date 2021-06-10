---
title: Colección de objetos
description: La colección de objetos es un control de diseño, que ayuda a crear una matriz de objetos en una forma tridimensional predefinida.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controles, diseño, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, colección de objetos, 2D, 3D, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 9648f3bd22a09c53de2f903ed8ba0274c634db7c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600204"
---
# <a name="object-collection"></a><span data-ttu-id="271e6-104">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="271e6-104">Object collection</span></span>

![Colección de objetos usada en la aplicación Tabla periódica de elementos](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="271e6-106">La colección de objetos es un control de diseño, que ayuda a crear una matriz de objetos en una forma tridimensional predefinida.</span><span class="sxs-lookup"><span data-stu-id="271e6-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="271e6-107">Admite varios estilos de superficie: \*\*plano, cilindro, esfera y **radial.**</span><span class="sxs-lookup"><span data-stu-id="271e6-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="271e6-108">Puede ajustar el radio y el tamaño de los objetos y el espacio entre ellos.</span><span class="sxs-lookup"><span data-stu-id="271e6-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="271e6-109">La colección de objetos admite cualquier objeto de Unity: 2D y 3D.</span><span class="sxs-lookup"><span data-stu-id="271e6-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="271e6-110">En el **[kit Mixed Reality herramientas,](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** hemos creado un script de Unity y ejemplos que le ayudarán a crear una colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="271e6-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="271e6-111">Ejemplos de colección de objetos</span><span class="sxs-lookup"><span data-stu-id="271e6-111">Object collection examples</span></span>

<span data-ttu-id="271e6-112">[Tabla periódica de los elementos es](../develop/unity/periodic-table-of-the-elements.md) una aplicación de ejemplo que muestra cómo funciona la colección object.</span><span class="sxs-lookup"><span data-stu-id="271e6-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="271e6-113">Usa la colección Object para crear cuadros de elementos químicas 3D en distintas formas.</span><span class="sxs-lookup"><span data-stu-id="271e6-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="271e6-114">![Ejemplos de colección de objetos que se muestran en la aplicación Tabla periódica de elementos](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="271e6-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="271e6-115">*Ejemplos de colección de objetos que se muestran en la aplicación de ejemplo Tabla periódica de elementos*</span><span class="sxs-lookup"><span data-stu-id="271e6-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="271e6-116">Objetos 3D</span><span class="sxs-lookup"><span data-stu-id="271e6-116">3D objects</span></span>

<span data-ttu-id="271e6-117">Puede usar la colección Object para establecer objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="271e6-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="271e6-118">En el ejemplo siguiente se muestra un plano y un diseño de cilindro de algunos objetos de la butaca 3D.</span><span class="sxs-lookup"><span data-stu-id="271e6-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="271e6-119">![Ejemplos de diseños planos y cilíndricas de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="271e6-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="271e6-120">*Ejemplos de diseños planos y cilíndricas de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="271e6-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="271e6-121">Objetos 2D</span><span class="sxs-lookup"><span data-stu-id="271e6-121">2D objects</span></span>

<span data-ttu-id="271e6-122">También puede usar imágenes 2D con la colección Object.</span><span class="sxs-lookup"><span data-stu-id="271e6-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="271e6-123">En los ejemplos siguientes se muestra cómo se pueden mostrar imágenes 2D en una cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="271e6-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Un ejemplo de imágenes 2D con la colección Object](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="271e6-125">![Ejemplos de uso de la colección de objetos con imágenes 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="271e6-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="271e6-126">*Ejemplos de uso de la colección de objetos con imágenes 2D*</span><span class="sxs-lookup"><span data-stu-id="271e6-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="271e6-127">Colección de objetos en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="271e6-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="271e6-128">MRTK: colección de objetos</span><span class="sxs-lookup"><span data-stu-id="271e6-128">MRTK - Object collection</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="271e6-129">Vea también</span><span class="sxs-lookup"><span data-stu-id="271e6-129">See also</span></span>

* [<span data-ttu-id="271e6-130">Cursores</span><span class="sxs-lookup"><span data-stu-id="271e6-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="271e6-131">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="271e6-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="271e6-132">Botón</span><span class="sxs-lookup"><span data-stu-id="271e6-132">Button</span></span>](button.md)
* [<span data-ttu-id="271e6-133">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="271e6-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="271e6-134">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="271e6-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="271e6-135">Manipulación</span><span class="sxs-lookup"><span data-stu-id="271e6-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="271e6-136">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="271e6-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="271e6-137">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="271e6-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="271e6-138">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="271e6-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="271e6-139">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="271e6-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="271e6-140">Teclado</span><span class="sxs-lookup"><span data-stu-id="271e6-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="271e6-141">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="271e6-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="271e6-142">Claqueta</span><span class="sxs-lookup"><span data-stu-id="271e6-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="271e6-143">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="271e6-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="271e6-144">Sombreador</span><span class="sxs-lookup"><span data-stu-id="271e6-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="271e6-145">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="271e6-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="271e6-146">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="271e6-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="271e6-147">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="271e6-147">Surface magnetism</span></span>](surface-magnetism.md)