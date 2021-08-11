---
title: Cuadro de límite y barra de la aplicación
description: La barra Aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, rectángulo de selección, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d7cacdcffeb552595e4ffd5ea5d1a734efb0451e03c5b6d5d39e5ea8caf3bd94
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198717"
---
# <a name="bounding-box-and-app-bar"></a>Cuadro de límite y barra de la aplicación
![El límite es la interfaz estándar para la manipulación de objetos en Mixed Reality.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>¿Qué es el cuadro de límite?

El límite es la interfaz estándar para la manipulación de objetos en Mixed Reality. Esta característica proporciona al usuario una indicación visual de que el objeto es ajustable actualmente. En HoloLens 2, el rectángulo de selección funciona con la manipulación directa de las manos y responde a la proximidad del dedo del usuario. Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Escalado de un objeto<br>
        Las esquinas del cuadro de límite le dicen al usuario que el objeto se puede escalar. Los identificadores siguen un patrón ampliamente comprendido para ajustar la escala. Esta indicación visual muestra a los usuarios el área total del objeto, incluso si no está visible fuera de un modo de ajuste. Sin esta característica, un objeto ajustado a otro objeto o superficie puede parecer que se comporta como si hubiera espacio alrededor que no debería estar ahí.<br>
        <br>
        *Bucle de vídeo: Escalado de un objeto mediante un rectángulo de selección*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens punto de vista del escalado de un objeto a través del rectángulo de selección](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotación de un objeto<br>
        Las asequiciones rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación. Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados. No solo se pueden ajustar y escalar, sino que ahora también se giran.<br>
        <br>
        *Bucle de vídeo: Rotación de un objeto mediante un rectángulo de selección*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens punto de vista de la rotación de un objeto a través del rectángulo de selección](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Comentarios visuales sobre la proximidad a mano en HoloLens 2<br>
        En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción de profundidad del usuario. Un anillo cerca de su dedo se muestra verticalmente y se escala verticalmente a medida que el dedo se acerca al objeto. El anillo finalmente converge en un punto cuando se alcanza el estado presionado. Esta asequibilidad visual ayuda al usuario a comprender lo lejos que está del objeto.<br>
        <br>
        *Bucle de vídeo: ejemplo de comentarios visuales basados en la proximidad a un rectángulo de selección*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Comentarios visuales sobre la proximidad a mano](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Para el desarrollo de aplicaciones de Unity, consulte [Rectángulo de selección en Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**

<br>

---

## <a name="what-is-the-app-bar"></a>¿Qué es la barra de aplicaciones?

La barra Aplicación es un menú de nivel de objeto, que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma. Este patrón se usa normalmente para permitir que los usuarios quiten y ajusten los hologramas. La barra de la aplicación se diseñó principalmente como una manera de administrar los objetos colocados en el entorno de un usuario. Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en la realidad mixta.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra Aplicación sigue al usuario<br>
        Puesto que este patrón se usa con objetos que están bloqueados por el mundo, a medida que un usuario se mueve alrededor del objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercanos al usuario. Aunque no es técnicamente un punto de conexión, esta característica logra eficazmente el mismo resultado. Impedir que la posición de un usuario occlude o bloquee la funcionalidad que, de lo contrario, estaría disponible desde una ubicación diferente en su entorno. <br>
        <br>
        *Bucle de vídeo: recorrido alrededor de un holograma, la barra de la aplicación sigue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Recorrer un holograma. La barra Aplicación sigue.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Rectángulo de selección en MRTK (Mixed Reality Toolkit) para Unity
**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts y requisitos previos para el cuadro de límite y la barra de aplicaciones. Puede agregar un cuadro de límite asignando el script BoundingBox.cs a cualquier objeto.

* [MRTK: rectángulo de selección](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


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