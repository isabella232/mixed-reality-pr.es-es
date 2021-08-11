---
title: Colección de objetos
description: Información general de la colección de objetos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, colección de objetos,
ms.openlocfilehash: 6705bd7093dbcd81912153872e4fd07c703fc5c0b9c081e0287589a7c8e959ac
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197560"
---
# <a name="object-collection"></a>Colección de objetos

![Colección de objetos](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

La colección de objetos es un script que ayuda a crear una matriz de objetos en formas tridimensionales predefinidas. Admite varios estilos de superficie, como plano, cilindro, esfera y radial. Puesto que admite cualquier objeto en Unity, se puede usar para el diseño de objetos 2D y 3D.

## <a name="object-collection-scripts"></a>Scripts de colección de objetos

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) admite los tipos de superficie de cilindro, plano, esfera y radial
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) admite la colección de estilos dispersos  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) proporciona algunas opciones adicionales a GridObjectCollection. **Nota:** TileGridObjectCollection no extiende y tiene varios [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) errores (vea [el problema 6237).](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237) Por lo tanto, se recomienda usar [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

|![Colección de objetos grid: cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Colección de objetos grid: cilindro | ![Colección de objetos grid: Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) Colección de objetos grid: Sphere |
|:--- | :--- |
|![Colección de objetos grid: radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) Colección de objetos grid: radial | ![Colección de objetos grid: plano](../images/object-collection/MRTK_ObjectCollectionPlane.png) Colección de objetos grid: plano |
|![Colección de objetos dispersos](../images/object-collection/MRTK_ObjectCollectionScattered.png) Colección de objetos dispersos | ![Colección de objetos de cuadrícula de mosaicos](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Colección de objetos de cuadrícula de mosaicos |

## <a name="how-to-use-an-object-collection"></a>Uso de una colección de objetos

Para crear una colección, cree un Objeto GameObject vacío y asígnele uno de los scripts de colección de objetos. Cualquier objeto se puede agregar como elemento secundario de GameObject. Cuando haya terminado de agregar objetos secundarios, haga clic en el *botón Actualizar colección* del panel del inspector para generar la colección de objetos. Los objetos se colocarán en la escena según los parámetros de la colección. También se puede acceder a Update Collection a través del código.

![Script de colección de objetos](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` alineación del contenido

El contenido de GridObjectCollection se puede alinear para que el objeto primario esté delimitado a la parte superior,media/inferior y a la izquierda,centro/derecha de la colección. Use la **propiedad anchor** para especificar la alineación del contenido.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` orden de diseño

Use el **campo Diseño** para especificar el orden de fila o columna que se han dispuesto los secundarios:

**Columna y fila:** los elementos secundarios se menten primero horizontalmente (por columna) y luego verticalmente (por fila). Use **Columnas num** (o propiedad Columnas en el código) para especificar el número de columnas de la cuadrícula.

![Diseño de columna y fila](../images/object-collection/MRTK_ColumnThenRow.png)

**Fila y columna:** los elementos secundarios se menten primero verticalmente (por fila) y luego horizontalmente (por columnas). Use **Num Rows** (o la propiedad Rows en el código) para especificar el número de filas de la cuadrícula.

![Diseño de fila y columna](../images/object-collection/MRTK_RowThenColumn.png)

**Horizontal:** los secundarios se menten en una sola fila usando solo columnas.

**Vertical:** los elementos secundarios se menten en una sola columna usando solo filas.

## <a name="object-collection-examples"></a>Ejemplos de colección de objetos

La escena de ejemplo `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) contiene varios ejemplos de tipos de colección de objetos.

[La tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo que muestra cómo funcionan las colecciones de objetos. Usa la colección de objetos para el diseño de los cuadros de elementos 3D en formas diferentes.

## <a name="object-collection-types"></a>Tipos de colección de objetos

**Objetos 3D**

Una colección de objetos se puede usar para el diseño de objetos 3D importados. En el ejemplo siguiente se muestran los diseños planos y cilíndricas de los objetos de modelo de la cátedra 3D mediante una colección.

![Colección de objetos 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**Objetos 2D**

Una colección de objetos también se puede crear a partir de imágenes 2D. Por ejemplo, se pueden colocar varias imágenes en un estilo de cuadrícula.

![Colección de objetos 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
