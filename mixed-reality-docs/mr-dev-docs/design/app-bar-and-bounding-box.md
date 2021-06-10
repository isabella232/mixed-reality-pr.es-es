---
title: Cuadro de límite y barra de la aplicación
description: La barra aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de la aplicación, rectángulo de selección, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 750fb238e5b7f22998a86f71607498c8f6982076
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600524"
---
# <a name="bounding-box-and-app-bar"></a>Cuadro de límite y barra de la aplicación
![El límite es la interfaz estándar para la manipulación de objetos en Mixed Reality.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>¿Qué es el rectángulo de selección?

El límite es la interfaz estándar para la manipulación de objetos en Mixed Reality. Esta característica proporciona al usuario una indicación visual de que el objeto es ajustable actualmente. En HoloLens 2, el rectángulo de selección funciona con la manipulación directa de la mano y responde a la proximidad del dedo del usuario. Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Escalado de un objeto<br>
        Las esquinas del cuadro de límite le dicen al usuario que el objeto se puede escalar. Los identificadores siguen un patrón ampliamente comprendido para ajustar la escala. Esta indicación visual muestra a los usuarios el área total del objeto, incluso si no está visible fuera de un modo de ajuste. Sin esta característica, un objeto ajustado a otro objeto o superficie puede parecer que se comporta como si hubiera espacio alrededor que no debería estar ahí.<br>
        <br>
        *Bucle de vídeo: Escalado de un objeto mediante el rectángulo de selección*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Punto de vista de HoloLens de escalado de un objeto a través del rectángulo de selección](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotación de un objeto<br>
        Las asequibilidades rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación. Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados. No solo se pueden ajustar y escalar, sino que ahora también se giran.<br>
        <br>
        *Bucle de vídeo: Rotación de un objeto a través del rectángulo de selección*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Punto de vista de HoloLens de rotación de un objeto a través del rectángulo de selección](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Comentarios visuales sobre la proximidad a mano en HoloLens 2<br>
        En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción de profundidad del usuario. Un anillo cerca de su dedo se muestra hacia arriba y se escala verticalmente a medida que el dedo se acerca al objeto. El anillo finalmente converge en un punto cuando se alcanza el estado presionado. Esta asequibilidad visual ayuda al usuario a comprender hasta qué punto está lejos del objeto.<br>
        <br>
        *Bucle de vídeo: ejemplo de comentarios visuales basados en la proximidad a un cuadro de límite*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Comentarios visuales sobre proximidad a mano](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Para el desarrollo de aplicaciones de Unity, consulte [Rectángulo de selección en Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>¿Qué es la barra de aplicaciones?

La barra Aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma. Este patrón se usa normalmente para permitir que los usuarios quiten y ajusten hologramas. La barra de la aplicación se diseñó principalmente como una manera de administrar los objetos colocados en el entorno de un usuario. Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en la realidad mixta.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra de la aplicación sigue al usuario<br>
        Puesto que este patrón se usa con objetos que están bloqueados por el mundo, a medida que un usuario se mueve alrededor del objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercanos al usuario. Aunque técnicamente no se utiliza el diseño de paneles, esta característica logra eficazmente el mismo resultado. Impedir que la posición de un usuario occlude o bloquee la funcionalidad que, de lo contrario, estaría disponible desde una ubicación diferente en su entorno. <br>
        <br>
        *Bucle de vídeo: Recorrido alrededor de un holograma, la barra de la aplicación sigue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Recorrer un holograma. La barra De la aplicación sigue.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cuadro de límite en MRTK (Mixed Reality Toolkit) para Unity
**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts y requisitos previos para el cuadro de límite y la barra de la aplicación. Puede agregar un cuadro de límite asignando el script BoundingBox.cs a cualquier objeto.

* [MRTK: rectángulo de selección](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a>Vea también

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