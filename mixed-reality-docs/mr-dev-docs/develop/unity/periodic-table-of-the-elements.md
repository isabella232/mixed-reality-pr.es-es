---
title: Tabla periódica de los elementos
description: Obtenga información sobre cómo crear una matriz de objetos en un espacio 3D con varios tipos de superficie mediante una colección Object con la aplicación de ejemplo Tabla periódica de elementos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles, MRTK, Mixed Reality Toolkit, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: aab6789939823b8c6e200bb5456118002b848e3c2f166abe50d4788ac8e7430d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211924"
---
# <a name="periodic-table-of-the-elements"></a>Tabla periódica de los elementos
![Tabla de períodos de la aplicación Elements](../images/MRDL_PeriodicTable_HL1.jpg)

>[!NOTE]
>En este artículo se describe un ejemplo exploratorio que hemos creado en [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un lugar donde compartimos nuestros aprendizajes y sugerencias para el desarrollo de aplicaciones de realidad mixta. Nuestros artículos y código relacionados con el diseño evolucionarán a medida que realicemos nuevas des descubrimientos.

>[!NOTE]
>Esta aplicación de ejemplo se diseñó para HoloLens 1.ª generación. Vea [Tabla periódica de Elements 2.0](periodic-table-of-the-elements-2.md) para obtener HoloLens 2 versión.

[Tabla periódica de los elementos es](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) una aplicación de ejemplo de código abierto de Microsoft Mixed Reality Design Labs. Obtenga información sobre cómo crear una matriz de objetos en un espacio 3D con varios tipos de superficie mediante una **[colección object](../../design/object-collection.md)**. Aprenda también a crear objetos interactuables que respondan a las entradas estándar de HoloLens. Puede usar los componentes de este proyecto para crear su propia experiencia de aplicación de realidad mixta.


## <a name="demo-video"></a>Vídeo de demostración 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Registrado con HoloLens 2 mediante Captura de realidad mixta

## <a name="about-the-app"></a>Acerca de la aplicación

Tabla periódica de los elementos visualiza los elementos químicas y cada una de sus propiedades en un espacio 3D. Incorpora las interacciones básicas de los HoloLens como la mirada y el toque en el aire. Los usuarios pueden obtener información sobre los elementos con modelos 3D animados. Pueden comprender visualmente el shell de electrones de un elemento y su núcleo, que se compone de protons y neutrones.

## <a name="background"></a>Segundo plano

Después de experimentar por primera HoloLens, sabía que quería experimentar con una aplicación de tabla periódica en realidad mixta. Dado que cada elemento tiene muchos puntos de datos que se muestran con texto, creo que sería una gran cuestión para explorar la composición tipográfica en un espacio 3D. Dar a los usuarios la oportunidad de visualizar el modelo de electrones del elemento fue otra parte interesante de este proyecto.

## <a name="design"></a>Diseño

Para la vista predeterminada de la tabla periódica, imagine cuadros tridimensionales que contendrán el modelo de electrones de cada elemento. La superficie de cada cuadro sería translúcida para que el usuario pudiera obtener una idea aproximada del volumen del elemento. Con la mirada y la pulsación en el aire, el usuario podría abrir una vista detallada de cada elemento. Para que la transición entre la vista de tabla y la vista de detalles sea fluida y natural, la he hecho similar a la interacción física de una apertura de cuadro en la vida real.

![Diseño del boceto](images/640px-sketch20170406.jpg)<br>
*Diseño de bocetos*

En la vista detallada, quería visualizar la información de cada elemento con texto representado de forma excelente en un espacio 3D. El modelo de electrones 3D animado se muestra en el área central y se puede ver desde distintos ángulos.

![Interacción](images/640px-periodictable-interaction.jpg)

![Prototipos](images/640px-periodictable-prototypes.jpg)<br>
*Prototipos de interacción*

El usuario puede cambiar el tipo de superficie pulsando en el aire los botones de la parte inferior de la tabla; puede cambiar entre plano, cilindro, esfera y dispersión.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controles y patrones comunes usados en esta aplicación

### <a name="interactable-object-button"></a>Objeto interactuable (botón)

[Un objeto interactuable](../../design/interactable-object.md) es un objeto que puede responder a las HoloLens básicas. Se proporciona como prefab/script, que se puede aplicar fácilmente a cualquier objeto. Por ejemplo, puede hacer que una cafetera de la escena sea interactuable y responder a entradas como mirada, pulsación en el aire, navegación y gestos de manipulación. [Más información](../../design/interactable-object.md)

![Objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Colección de objetos

[La colección](../../design/object-collection.md) de objetos es un objeto que le ayuda a crear varios objetos en varias formas. Admite plano, cilindro, esfera y dispersión. Puede configurar propiedades adicionales, como el radio, el número de filas y el espaciado. [Más información](../../design/object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar scripts y elementos prefabs para la aplicación Tabla periódica de elementos en Mixed Reality [Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Historia de porte para HoloLens 2

Lea la historia sobre cómo se actualizó la aplicación Tabla periódica de elementos con HoloLens 2 interacciones instintiva de la aplicación.

[Tabla periódica de los elementos 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también

* [MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabla periódica de los elementos 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)