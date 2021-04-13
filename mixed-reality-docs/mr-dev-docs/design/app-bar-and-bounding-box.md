---
title: Cuadro de límite y barra de la aplicación
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 0ccec5240854de9a7db6a79d5b90b97f1e6b81de
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299910"
---
# <a name="bounding-box-and-app-bar"></a>Cuadro de límite y barra de la aplicación
![El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>¿Cuál es el cuadro de límite?

El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta. Esta característica proporciona al usuario una indicación visual de que el objeto es ajustable actualmente. En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario. Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Escalado de un objeto<br>
        Las esquinas del cuadro de límite indican al usuario que el objeto se puede escalar. Los identificadores siguen un patrón muy entendido para ajustar la escala. Esta indicación visual muestra a los usuarios el área total del objeto, aunque no sea visible fuera de un modo de ajuste. Sin esta característica, es posible que un objeto ajustado a otro objeto o superficie parezca que se comporte como si hubiera espacio alrededor que no debiera estar ahí.<br>
        <br>
        *Bucle de vídeo: escalado de un objeto a través del cuadro de límite*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Punto de vista de HoloLens de escalado de un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Girar un objeto<br>
        Las prestaciones rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación. Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados. No solo se pueden ajustar y escalar, sino que ahora giran.<br>
        <br>
        *Bucle de vídeo: girar un objeto a través del cuadro de límite*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Punto de vista de HoloLens de girar un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Comentarios visuales sobre la proximidad en HoloLens 2<br>
        En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción del usuario de la profundidad. Se muestra un anillo cerca de su dedo y se reduce verticalmente a medida que la mano se acerca al objeto. El anillo finalmente converge en un punto cuando se alcanza el estado presionado. Esta prestación visual ayuda al usuario a comprender hasta qué punto proceden del objeto.<br>
        <br>
        *Bucle de vídeo: ejemplo de comentarios visuales basados en proximidad a un cuadro de límite*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Comentarios visuales en proximidad](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Para el desarrollo de aplicaciones de Unity, consulte [cuadro de límite en el kit de herramientas de realidad mixta (Unity).](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>¿Qué es la barra de la aplicación?

La barra de la aplicación es un menú de nivel de objeto, que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma. Este patrón se usa normalmente para permitir que los usuarios quiten y ajusten los hologramas. La barra de la aplicación se diseñó principalmente como una manera de administrar objetos colocados en el entorno de un usuario. Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en realidad mixta.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra de la aplicación sigue al usuario<br>
        Puesto que este patrón se usa con objetos que están bloqueados por todo el mundo, a medida que un usuario se desplaza por el objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario. Aunque técnicamente no se trata de una característica, esta característica consigue el mismo resultado. Impedir que la posición de un usuario tapaba o bloquee la funcionalidad que, de otro modo, estará disponible desde una ubicación diferente en su entorno. <br>
        <br>
        *Bucle de vídeo: desplazarse por un holograma, la barra de la aplicación sigue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Recorrer un holograma. A continuación se muestra la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cuadro de límite en MRTK (kit de herramientas de realidad mixta) para Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts y Prefabs para el cuadro de límite y la barra de la aplicación. Puede Agregar un cuadro de límite mediante la asignación del script BoundingBox. CS en cualquier objeto.

* [MRTK: cuadro de límite](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a>Consulte también

* [Cursores](cursors.md)
* [Haces de mano](point-and-commit.md)
* [Botón](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipulación](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Cerca](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Información sobre herramientas](tooltip.md)
* [Claqueta](slate.md)
* [Control deslizante](slider.md)
* [Sombreador](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
