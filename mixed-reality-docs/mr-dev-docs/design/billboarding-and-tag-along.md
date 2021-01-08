---
title: Etiquetado y vista frontal continua
description: Obtenga información sobre cómo usar objetos con la cartelera, que siempre se orientan a los usuarios en aplicaciones de realidad mixta.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, la cartelera, la etiqueta, junto con el casco de realidad mixta, el casco de la realidad mixta de Windows, el casco de realidad virtual, HoloLens, MRTK, el kit de herramientas de realidad mixta
ms.openlocfilehash: 92caa1bcd325cefecc6d3820b819cecfce6fc09c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009624"
---
# <a name="billboarding-and-tag-along"></a>Etiquetado y vista frontal continua

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>¿Qué es la cartelera?

La cartelera es un concepto de comportamiento que se puede aplicar a los objetos de realidad mixta. Los objetos con la cartelera siempre se orientan a sí mismos para que se enfrente al usuario. Los sistemas de texto y de menú son casos de uso comunes, donde los objetos estáticos que se colocan en el entorno del usuario (con bloqueo mundial) estarán ocultos o ilegibles cuando los usuarios se desplacen.

Los objetos con la cartelera habilitada pueden girar libremente en el entorno del usuario. También se pueden restringir a un único eje en función de las consideraciones de diseño. Tenga en cuenta que los objetos con cartelera se pueden recortar o tapaba cuando se colocan demasiado cerca de otros objetos, o bien en HoloLens, demasiado cerca de las superficies digitalizadas. Para evitar esto, piense en la superficie total que un objeto puede producir cuando se gira en el eje habilitado para la cartelera.

<br>

---
## <a name="what-is-a-tag-along"></a>¿Qué es una etiqueta?

La etiqueta es un concepto de comportamiento que se puede Agregar a los hologramas. Una etiqueta a lo largo del objeto intenta permanecer en un intervalo que permite al usuario interactuar de forma cómoda.

![El panel de PIN de HoloLens es un buen ejemplo de cómo se comparan las etiquetas](images/tagalong-1000px.jpg)<br>
*El menú Inicio de HoloLens es un buen ejemplo de comportamiento de etiqueta.*

Los objetos de etiqueta incluyen parámetros, que pueden ajustarse de la forma en que se comportan. El contenido puede estar dentro o fuera de la línea de visión del usuario mientras el usuario se mueve por el entorno. A medida que se mueve, el contenido intenta permanecer dentro del perímetro del usuario desplazándose hacia el borde de la vista. El contenido podría estar temporalmente fuera de la vista, en función de la rapidez con la que se mueva el usuario. Cuando el usuario mira hacia el objeto de etiqueta, resulta más completo ver. Piense que el contenido siempre es "un vistazo", por lo que los usuarios nunca olvidan en qué dirección se encuentra el contenido.

Los parámetros adicionales pueden hacer que la etiqueta a lo largo del objeto se adjunte al encabezado del usuario mediante una banda elástica. La amortiguación de aceleración o desaceleración da peso al objeto, lo que hace que se sienta más físicamente presente. Este comportamiento del muelle es una prestación que ayuda al usuario a crear un modelo mental exacto de cómo funciona la etiqueta. Audio le ayuda a proporcionar otras guías para cuando los usuarios tienen objetos en el modo de etiqueta. El audio debe reforzar la velocidad de movimiento; un cambio de cabeza rápido debe proporcionar un efecto de sonido más perceptible, mientras que recorrer una velocidad natural debe tener efectos de audio mínimos o no.

Al igual que el contenido bloqueado realmente por el encabezado, los objetos de etiquetas pueden resultar abrumadores o nauseating si se mueven de forma desigual o muelle demasiado en la vista del usuario. A medida que un usuario mira, se detiene rápidamente, sus sentidos les indican que se han detenido. Su saldo les informa de que su cabeza ha dejado de activar y su visión ve que el mundo deja de activar. Sin embargo, si la etiqueta se mantiene en movimiento cuando el usuario se detiene, puede confundir sus sentidos.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>La cartelera y la etiqueta en MRTK (kit de herramientas de realidad mixta) para Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts para el comportamiento de la cartelera y la etiqueta. Asigne el script Billboard.cs en cualquier objeto para agregar el comportamiento de la cartelera y hacer que el objeto siempre se enfrente a usted. Para agregar el comportamiento de etiqueta, use el script RadialView.cs. Puede ajustar varias opciones, como lerping Time, Distance y degree.

* [MRTK: Solver de vista radial](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK: script de la cartelera](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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
