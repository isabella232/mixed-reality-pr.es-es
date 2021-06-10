---
title: Etiquetado y vista frontal continua
description: Aprenda a usar objetos con paneles, que siempre se orientan a sí mismos para enfrentarse al usuario en aplicaciones de realidad mixta.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, paneles, etiquetas, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600344"
---
# <a name="billboarding-and-tag-along"></a>Etiquetado y vista frontal continua

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>¿Qué es la asociación?

La asociación es un concepto de comportamiento que se puede aplicar a objetos en realidad mixta. Los objetos con paneles siempre se orientan a sí mismos para enfrentarse al usuario. Los sistemas de texto y menú son casos de uso comunes, donde los objetos estáticos colocados en el entorno del usuario (bloqueados por el mundo) se ocultarían o no serían legibles cuando los usuarios se mueven.

Los objetos con el acodado habilitado pueden girar libremente en el entorno del usuario. También se pueden restringir a un solo eje en función de las consideraciones de diseño. Tenga en cuenta que los objetos delimitados pueden recortarse u occluir ellos mismos cuando se colocan demasiado cerca de otros objetos, o en HoloLens, demasiado cerca de las superficies examinadas. Para evitarlo, piense en la superficie total que puede producir un objeto cuando se gira en el eje habilitado para el movimiento de paneles.

<br>

---
## <a name="what-is-a-tag-along"></a>¿Qué es una etiqueta?

La etiqueta es un concepto de comportamiento que se puede agregar a los hologramas. Un objeto de etiquetas intenta permanecer en un intervalo que permite al usuario interactuar cómodamente.

![El panel de pines de HoloLens es un excelente ejemplo de cómo se comporta la etiqueta](images/tagalong-1000px.jpg)<br>
*El menú Inicio HoloLens es un excelente ejemplo de comportamiento de etiquetas*

Los objetos de etiquetas tienen parámetros, que pueden ajustar la forma en que se comportan. El contenido puede estar dentro o fuera de la línea de visión del usuario mientras el usuario se mueve por su entorno. A medida que se mueve, el contenido intenta permanecer dentro de la periferia del usuario deslizándose hacia el borde de la vista. El contenido podría estar temporalmente fuera de la vista en función de la rapidez con la que se mueva el usuario. Cuando el usuario mira hacia el objeto de etiqueta, se ve más a la vista. Piense que el contenido siempre está "a un vistazo" para que los usuarios nunca olviden en qué dirección se encuentra su contenido.

Los parámetros adicionales pueden hacer que el objeto de etiqueta se sinta adjunto a la cabeza del usuario mediante una banda de almohadillas. La aceleración o la reducción de la aceleración de la aceleración da peso al objeto, lo que hace que se sienta más presente físicamente. Este comportamiento de spring es una ayuda que ayuda al usuario a crear un modelo mental preciso de cómo funciona la etiqueta. El audio ayuda a proporcionar otras indicaciones para cuando los usuarios tienen objetos en modo de etiqueta. El audio debe reforzar la velocidad de movimiento; Un giro rápido en la cabeza debe proporcionar un efecto de sonido más perceptible, mientras que la marcha a una velocidad natural debe tener un mínimo o ningún efecto de audio.

Al igual que sucede con el contenido realmente bloqueado, los objetos de etiquetas pueden resultar abrumadores o abrumadores si se mueven demasiado en la vista del usuario. A medida que un usuario examina y, a continuación, se detiene rápidamente, sus sentidos le dicen que se ha detenido. Su equilibrio les informa de que su cabeza ha dejado de girar y su visión ve que el mundo deja de girar. Sin embargo, si la etiqueta continúa en movimiento cuando el usuario se ha detenido, puede confundir sus sentidos.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Etiquetado y etiquetado en MRTK (Mixed Reality Toolkit) para Unity
**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts para el comportamiento de etiquetado y etiquetado. Asigne el script de Recordset.cs a cualquier objeto para agregar el comportamiento de afilación y hacer que el objeto siempre se le aleme. Para agregar el comportamiento de etiquetas, use el script RadialView.cs. Puede ajustar varias opciones, como el tiempo de lerping, la distancia y el grado.

* [MRTK: solucionador de vistas radiales](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK: script de Scripts](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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