---
title: Colección de objetos
description: Información general de la colección de objetos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, colección de objetos,
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177052"
---
# <a name="object-collection"></a><span data-ttu-id="98120-104">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="98120-104">Object collection</span></span>

![Colección de objetos](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="98120-106">La colección de objetos es un script que ayuda a crear una matriz de objetos en formas tridimensionales predefinidas.</span><span class="sxs-lookup"><span data-stu-id="98120-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="98120-107">Admite varios estilos de superficie, como plano, cilindro, esfera y radial.</span><span class="sxs-lookup"><span data-stu-id="98120-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="98120-108">Puesto que admite cualquier objeto en Unity, se puede usar para el diseño de objetos 2D y 3D.</span><span class="sxs-lookup"><span data-stu-id="98120-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="98120-109">Scripts de colección de objetos</span><span class="sxs-lookup"><span data-stu-id="98120-109">Object collection scripts</span></span>

- <span data-ttu-id="98120-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) admite los tipos de superficie de cilindro, plano, esfera y radial</span><span class="sxs-lookup"><span data-stu-id="98120-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="98120-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) admite la colección de estilos dispersos</span><span class="sxs-lookup"><span data-stu-id="98120-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="98120-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) proporciona algunas opciones adicionales a GridObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="98120-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="98120-113">**Nota:** TileGridObjectCollection no extiende [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) y tiene varios errores (vea el problema [6237).](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)</span><span class="sxs-lookup"><span data-stu-id="98120-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="98120-114">Por lo tanto, se recomienda usar [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .</span><span class="sxs-lookup"><span data-stu-id="98120-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Colección de objetos grid: cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="98120-116">Colección de objetos grid: cilindro</span><span class="sxs-lookup"><span data-stu-id="98120-116">Grid Object Collection - Cylinder</span></span> | ![Colección de objetos grid: Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="98120-118">Colección de objetos grid: Sphere</span><span class="sxs-lookup"><span data-stu-id="98120-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Colección de objetos grid: radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="98120-120">Colección de objetos grid: radial</span><span class="sxs-lookup"><span data-stu-id="98120-120">Grid Object Collection - Radial</span></span> | ![Colección de objetos grid: plano](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="98120-122">Colección de objetos grid: plano</span><span class="sxs-lookup"><span data-stu-id="98120-122">Grid Object Collection - Plane</span></span> |
|![Colección de objetos dispersos](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="98120-124">Colección de objetos dispersos</span><span class="sxs-lookup"><span data-stu-id="98120-124">Scattered Object Collection</span></span> | ![Colección de objetos de cuadrícula de mosaicos](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="98120-126">Colección de objetos de cuadrícula de mosaicos</span><span class="sxs-lookup"><span data-stu-id="98120-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="98120-127">Uso de una colección de objetos</span><span class="sxs-lookup"><span data-stu-id="98120-127">How to use an object collection</span></span>

<span data-ttu-id="98120-128">Para crear una colección, cree un Objeto GameObject vacío y asígnele uno de los scripts de colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="98120-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="98120-129">Cualquier objeto se puede agregar como elemento secundario de GameObject.</span><span class="sxs-lookup"><span data-stu-id="98120-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="98120-130">Una vez que haya terminado de agregar objetos secundarios, haga clic en el *botón Actualizar colección* en el panel del inspector para generar la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="98120-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="98120-131">Los objetos se colocarán en la escena según los parámetros de la colección.</span><span class="sxs-lookup"><span data-stu-id="98120-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="98120-132">También se puede acceder a Update Collection a través del código.</span><span class="sxs-lookup"><span data-stu-id="98120-132">Update Collection can be accessed through the code too.</span></span>

![Script de colección de objetos](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="98120-134">`GridObjectCollection` alineación de contenido</span><span class="sxs-lookup"><span data-stu-id="98120-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="98120-135">El contenido de GridObjectCollection se puede alinear para que el objeto primario esté delimitado a la parte superior/media/inferior y a la izquierda,centro/derecha de la colección.</span><span class="sxs-lookup"><span data-stu-id="98120-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="98120-136">Use la **propiedad anchor** para especificar la alineación del contenido.</span><span class="sxs-lookup"><span data-stu-id="98120-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="98120-137">`GridObjectCollection` orden de diseño</span><span class="sxs-lookup"><span data-stu-id="98120-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="98120-138">Use el **campo Diseño** para especificar el orden de fila o columna que se han diseñado los secundarios:</span><span class="sxs-lookup"><span data-stu-id="98120-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="98120-139">**Columna a continuación,** fila: los elementos secundarios se menten primero horizontalmente (por columna) y luego verticalmente (por fila).</span><span class="sxs-lookup"><span data-stu-id="98120-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="98120-140">Use **Columnas num** (o propiedad Columnas en el código) para especificar el número de columnas de la cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="98120-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![Diseño de columna y fila](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="98120-142">**Fila y columna:** los elementos secundarios se menten primero verticalmente (por fila) y luego horizontalmente (por columnas).</span><span class="sxs-lookup"><span data-stu-id="98120-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="98120-143">Use **Num Rows** (o la propiedad Rows en el código) para especificar el número de filas de la cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="98120-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![Diseño de fila y columna](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="98120-145">**Horizontal:** los secundarios se menten en una sola fila solo con columnas</span><span class="sxs-lookup"><span data-stu-id="98120-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="98120-146">**Vertical:** los elementos secundarios se menten en una sola columna solo con filas.</span><span class="sxs-lookup"><span data-stu-id="98120-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="98120-147">Ejemplos de colección de objetos</span><span class="sxs-lookup"><span data-stu-id="98120-147">Object collection examples</span></span>

<span data-ttu-id="98120-148">La escena de ejemplo `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) contiene varios ejemplos de tipos de colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="98120-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="98120-149">[La tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo que muestra cómo funcionan las colecciones de objetos.</span><span class="sxs-lookup"><span data-stu-id="98120-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="98120-150">Usa la colección de objetos para crear los cuadros de elementos 3D en formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="98120-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="98120-151">Tipos de colección de objetos</span><span class="sxs-lookup"><span data-stu-id="98120-151">Object collection types</span></span>

<span data-ttu-id="98120-152">**Objetos 3D**</span><span class="sxs-lookup"><span data-stu-id="98120-152">**3D objects**</span></span>

<span data-ttu-id="98120-153">Una colección de objetos se puede usar para el diseño de objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="98120-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="98120-154">En el ejemplo siguiente se muestran los diseños de plano y cilíndrica de objetos de modelo de butaca 3D mediante una colección.</span><span class="sxs-lookup"><span data-stu-id="98120-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![Colección de objetos 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="98120-156">**Objetos 2D**</span><span class="sxs-lookup"><span data-stu-id="98120-156">**2D Objects**</span></span>

<span data-ttu-id="98120-157">También se puede crear una colección de objetos a partir de imágenes 2D.</span><span class="sxs-lookup"><span data-stu-id="98120-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="98120-158">Por ejemplo, se pueden colocar varias imágenes en un estilo de cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="98120-158">For example, multiple images can be placed in a grid style.</span></span>

![Colección de objetos 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
