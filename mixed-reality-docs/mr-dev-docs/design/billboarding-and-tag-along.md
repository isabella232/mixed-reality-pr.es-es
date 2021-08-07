---
title: Etiquetado y vista frontal continua
description: Obtenga información sobre cómo usar objetos con paneles, que siempre se orientan a sí mismos para enfrentarse al usuario en aplicaciones de realidad mixta.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, marca, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 7ffcbe1d3401601e92eb1ac81dfd84f2af9e8e79eeea809b01a1e943a85f0db9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214182"
---
# <a name="billboarding-and-tag-along"></a>Etiquetado y vista frontal continua

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>¿Qué es la afición?

La tecnología de diseño es un concepto de comportamiento que se puede aplicar a los objetos de la realidad mixta. Los objetos con ajuste siempre se orientan a sí mismos para enfrentarse al usuario. Los sistemas de texto y menús son casos de uso comunes, donde los objetos estáticos colocados en el entorno del usuario (bloqueados por el mundo) se ocultarían o ilegibles cuando los usuarios se desplazan.

Los objetos con la característica de acodado habilitada pueden girar libremente en el entorno del usuario. También se pueden restringir a un único eje en función de las consideraciones de diseño. Tenga en cuenta que los objetos delimitados pueden recortarse u occluir ellos mismos cuando se colocan demasiado cerca de otros objetos, o en HoloLens, superficies examinadas demasiado cercanas. Para evitarlo, piense en la superficie total que puede producir un objeto cuando gira en el eje habilitado para el movimiento.

<br>

---
## <a name="what-is-a-tag-along"></a>¿Qué es una etiqueta?

La etiqueta es un concepto de comportamiento que se puede agregar a los hologramas. Un objeto de etiqueta junto intenta permanecer en un intervalo que permite al usuario interactuar cómodamente.

![El panel HoloLens de etiquetas es un buen ejemplo de cómo se comporta la etiqueta](images/tagalong-1000px.jpg)<br>
*El HoloLens menú Inicio es un buen ejemplo de comportamiento de etiqueta*

Los objetos de etiquetas tienen parámetros, que pueden ajustar la forma en que se comportan. El contenido puede estar dentro o fuera de la línea de visión del usuario mientras el usuario se mueve por su entorno. A medida que se mueve, el contenido intenta permanecer dentro de la periferia del usuario deslizándose hacia el borde de la vista. El contenido podría estar temporalmente fuera de la vista en función de la rapidez con la que se mueva el usuario. Cuando el usuario mira hacia el objeto de etiqueta, se ve de forma más completa. Piense en que el contenido siempre está "a un vistazo" para que los usuarios nunca olviden en qué dirección se encuentra su contenido.

Los parámetros adicionales pueden hacer que el objeto de etiqueta se sienta conectado a la cabeza del usuario mediante una banda de almohadillas. La aceleración o la desceleración de la aceleración da peso al objeto, lo que hace que se sienta más presente físicamente. Este comportamiento de spring es una asequibilidad que ayuda al usuario a crear un modelo mental preciso de cómo funciona la etiqueta. El audio ayuda a proporcionar otras indicaciones para cuando los usuarios tienen objetos en modo de etiqueta. El audio debe reforzar la velocidad de movimiento; Un giro rápido de la cabeza debe proporcionar un efecto de sonido más perceptible, mientras que el recorrido a una velocidad natural debe tener un mínimo o ningún efecto de audio.

Al igual que sucede con el contenido realmente bloqueado con la cabeza, los objetos de etiqueta pueden resultar abrumadores o desconcierbles si se mueven demasiado o se desplazan demasiado en la vista del usuario. A medida que un usuario examina y, a continuación, se detiene rápidamente, sus sentidos le dicen que se ha detenido. Su equilibrio les informa de que su cabeza ha dejado de girar y su visión ve que el mundo deja de girar. Sin embargo, si la etiqueta continúa en movimiento cuando el usuario se ha detenido, puede confundir sus sentidos.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Etiquetado y etiquetado en MRTK (Mixed Reality Toolkit) para Unity
**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts para el comportamiento de etiquetado y etiquetado. Asigne el script Desasignar.cs a cualquier objeto para agregar comportamiento de navegación y hacer que el objeto siempre se enfrenta a usted. Para agregar el comportamiento de etiquetas, use el script RadialView.cs. Puede ajustar varias opciones, como el tiempo de lerping, la distancia y el grado.

* [MRTK: solucionador de vistas radiales](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK: script de Scripts](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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