---
title: Tabla periódica de los elementos
description: Obtenga información sobre cómo diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una colección de objetos con la tabla periódica de la aplicación de ejemplo Elements.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles, MRTK, kit de herramientas de realidad mixta, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: fd525b0d41efa15ff55097456fb6b06dd3d60c25
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009365"
---
# <a name="periodic-table-of-the-elements"></a>Tabla periódica de los elementos

>[!NOTE]
>En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta. Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.

[La tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft. Obtenga información sobre cómo diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una **[colección de objetos](../../design/object-collection.md)**. También aprenderá a crear objetos interactivos que respondan a entradas estándar de HoloLens. Puede usar los componentes de este proyecto para crear su propia experiencia de aplicación de realidad mixta.

![Tabla de puntos de la aplicación Elements](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>Vídeo de demostración 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Grabado con HoloLens 2 mediante la captura de realidad mixta

## <a name="about-the-app"></a>Acerca de la aplicación

La tabla periódica de los elementos visualiza los elementos químicos y cada una de sus propiedades en un espacio 3D. Incorpora las interacciones básicas de HoloLens, como mira fijamente y el aire TAP. Los usuarios pueden obtener información sobre los elementos con modelos 3D animados. Pueden comprender visualmente el shell de electrones de un elemento y su núcleo, que se compone de protoneladas y neutrons.

## <a name="background"></a>Fondo

Después de haber experimentado HoloLens, sabía que quería experimentar con una aplicación de tabla periódica en realidad mixta. Puesto que cada elemento tiene muchos puntos de datos que se muestran con texto, pensé que sería una buena cuestión para explorar la composición tipográfica en un espacio 3D. Dar a los usuarios la oportunidad de visualizar el modelo de electrones del elemento fue otra parte interesante de este proyecto.

## <a name="design"></a>Diseño

En la vista predeterminada de la tabla periódica, se imaginan cuadros tridimensionales que contendrían el modelo de electrones de cada elemento. La superficie de cada cuadro sería traslúcida, de modo que el usuario podría obtener una idea aproximada del volumen del elemento. Con fijamente y TAP, el usuario podría abrir una vista detallada de cada elemento. Para que la transición entre la vista de tabla y la vista de detalles sea suave y natural, lo hice de manera similar a la interacción física de una caja de apertura en la vida real.

![Boceto de diseño](images/640px-sketch20170406.jpg)<br>
*Dibujos de diseño*

En la vista de detalle, quería visualizar la información de cada elemento con texto representado con un gran espacio en 3D. El modelo de electrones 3D animado se muestra en el área central y se puede ver desde distintos ángulos.

![Interacción](images/640px-periodictable-interaction.jpg)

![Prototipos](images/640px-periodictable-prototypes.jpg)<br>
*Prototipos de interacción*

El usuario puede cambiar el tipo de superficie mediante la pulsación de los botones de la parte inferior de la tabla. puede cambiar entre plano, cilindro, esfera y dispersión.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controles comunes y patrones usados en esta aplicación

### <a name="interactable-object-button"></a>Objeto interactuable (botón)

El [objeto interactuable](../../design/interactable-object.md) es un objeto, que puede responder a entradas básicas de HoloLens. Se proporciona como recurso prefabricado/script, que se puede aplicar fácilmente a cualquier objeto. Por ejemplo, puede hacer que una copa de café en la escena sea interactuable y responder a entradas como, por ejemplo, gestos de mira, navegación y manipulación. [Más información](../../design/interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Colección de objetos

[Colección de objetos](../../design/object-collection.md) es un objeto, que le ayuda a diseñar varios objetos en varias formas. Admite plano, cilindro, esfera y dispersión. Puede configurar propiedades adicionales como RADIUS, el número de filas y el espaciado. [Más información](../../design/object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar scripts y Prefabs para la tabla periódica de la aplicación Elements en el laboratorio de diseño de la [realidad mixta de github](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Portabilidad de la historia de HoloLens 2

Lea el artículo sobre cómo se actualizó la tabla periódica de la aplicación Elements con las interacciones instinctual de HoloLens 2.

[Tabla periódica de los elementos 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también

* [MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabla periódica de los elementos 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)