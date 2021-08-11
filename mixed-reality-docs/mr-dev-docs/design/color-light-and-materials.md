---
title: Color, luz y materiales
description: El diseño de contenido para la realidad mixta requiere una cuidadosa consideración del color, la iluminación y los materiales de todos los recursos visuales.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, color, luz, materiales, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 50789faa44e6786c0d9fd0b146daa84f459df451bedc52f06073e742ea8064a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219870"
---
# <a name="color-light-and-materials"></a>Color, luz y materiales

![Color, luz y materiales](images/RemoteRendering.jpg)

El diseño de contenido para la realidad mixta requiere una cuidadosa consideración del color, la iluminación y los materiales de todos los recursos virtuales. Los propósitos éticos pueden incluir el uso de luz y material para establecer el tono de un entorno envolvente, mientras que los propósitos funcionales pueden incluir el uso de colores sorprendentes para alertar a los usuarios de una acción impensiva. Cada una de estas decisiones debe sopesarse con las oportunidades y restricciones del dispositivo de destino de su experiencia.

A continuación se muestran directrices específicas para representar recursos en cascos envolventes y holográficos. Muchas de ellas están estrechamente vinculadas a otras áreas técnicas [](color-light-and-materials.md#see-also) y se puede encontrar una lista de temas relacionados en la sección Consulte también al final de este artículo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Representación en dispositivos envolventes frente a holográficos

El contenido representado en cascos envolventes aparecerá visualmente diferente en comparación con el contenido representado en cascos holográficos. Aunque los cascos envolventes suelen representar contenido de la forma esperada en una pantalla 2D, los cascos holográficos como HoloLens usan pantallas RGB secuenciales de color a través para representar hologramas.

Tómese siempre tiempo para probar sus experiencias holográficas en un casco holográfico. La apariencia del contenido, incluso si se ha creado específicamente para dispositivos holográficos, variará como se ve en los monitores secundarios, las instantáneas y la vista del espectador. Recuerde recorrer experiencias con un dispositivo, probar la iluminación de hologramas y observar desde todos los lados (así como desde arriba y abajo) cómo se representa el contenido. Asegúrese de probar con una variedad de configuraciones de brillo en el dispositivo. Es poco probable que todos los usuarios compartan un supuesto valor predeterminado y un conjunto diverso de condiciones de iluminación.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Aspectos básicos de la representación en dispositivos holográficos

* **Los dispositivos holográficos** tienen pantallas Hologramas se crean agregando luz a la luz desde el mundo real; el blanco aparecerá de forma brillante, mientras que el negro aparecerá transparente.

* **El impacto en los colores varía en función** del entorno del usuario: hay muchas condiciones de iluminación diversas en la sala de un usuario. Cree contenido con los niveles de contraste adecuados para ayudar a mejorar la claridad.

* **Evite la iluminación** dinámica: las Hologramas que se encienden uniformemente en experiencias holográficas son las más eficaces. Es probable que el uso de iluminación dinámica avanzada supere las funcionalidades de los dispositivos móviles. Cuando se requiere iluminación dinámica, se recomienda usar el [sombreador Mixed Reality Toolkit estándar](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md). 

## <a name="designing-with-color"></a>Diseño con color

Debido a la naturaleza de las pantallas de adiciones, ciertos colores pueden aparecer diferentes en las pantallas holográficas. Algunos colores aparecerán en entornos de iluminación, mientras que otros aparecerán como menos afectados. Los colores es cool tienden a retroceder al fondo, mientras que los colores de color caliente saltan al primer plano. Tenga en cuenta estos factores a medida que explora el color en sus experiencias:

* **Representación de colores claros:** el blanco parece brillante y se debe usar con moderación. En la mayoría de los casos, considere un valor blanco alrededor de R 235 G 235 B 235. Las áreas brillantes grandes pueden causar molestias al usuario. Para la placa posterior de la ventana de la interfaz de usuario, se recomienda usar colores oscuros.

* **Representación de colores oscuros:** debido a la naturaleza de las pantallas de adiciones, los colores oscuros aparecen transparentes. Un objeto negro sólido no aparecerá diferente del mundo real. Consulte canal alfa a continuación. Para dar la apariencia de "negro", pruebe un valor RGB gris muy oscuro como 16,16,16.

* **Uniformidad de color:** normalmente, los hologramas se representan lo suficientemente brillantes como para mantener la uniformidad del color, sea cual sea el fondo. Las áreas grandes pueden volverse blotchy. Evite regiones grandes de color sólido y brillante.

* **Gama:** HoloLens ventajas de una "amplia gama" de color, conceptualmente similar a Adobe RGB. Como resultado, algunos colores pueden mostrar diferentes calidades y representación en el dispositivo.

* **Gamma:** el brillo y el contraste de la imagen representado variarán entre los dispositivos envolventes y holográficos. A menudo, estas diferencias de dispositivo parecen hacer que las áreas oscuras de color y sombras, más o menos brillantes.

* **Separación de** colores: también denominada "separación de colores" o "fringing de color", la separación de color se produce normalmente con hologramas móviles (incluido el cursor) cuando un usuario realiza un seguimiento de los objetos con los ojos.

## <a name="technical-considerations"></a>Consideraciones técnicas

* **Alias:** tenga en cuenta los alias, escalonados o "pasos de escalón" donde el borde de la geometría de un holograma se encuentra con el mundo real. El uso de texturas con un alto detalle puede ayudar a este efecto. Las texturas se deben asignar y habilitar el filtrado. Considere la posibilidad de desvanecio de los bordes de los hologramas o agregar una textura que cree un borde de borde negro alrededor de los objetos. Evite la geometría fina siempre que sea posible.

* **Canal alfa:** debe borrar el canal alfa para que sea totalmente transparente para cualquier parte en la que no esté representando un holograma. Dejar el alfa sin definir conduce a artefactos visuales al tomar imágenes o vídeos desde el dispositivo o con vista de espectador.

* **Suavizado de textura:** dado que la luz se suma en las pantallas holográficas, es mejor evitar grandes regiones de color sólido y brillante, ya que a menudo no producen el efecto visual previsto.

## <a name="design-guidelines-for-holographic-display"></a>Directrices de diseño para la presentación holográfica

![Oclusión de manos y colores](images/color_handocclusion.jpg)

Al diseñar contenido para pantallas holográficas, hay varios elementos que debe considerar para lograr la mejor experiencia. Visite [Diseño de contenido para la presentación holográfica](designing-content-for-holographic-display.md) para ver las directrices y recomendaciones.

## <a name="storytelling-with-light-and-color"></a>Narración con luz y color

La luz y el color pueden ayudar a que los hologramas aparezcan de forma más natural en el entorno de un usuario y ofrecer orientación y ayuda para el usuario. Para las experiencias holográficas, tenga en cuenta estos factores a medida que explora la iluminación y el color:

:::row:::
    :::column:::
* **Reescenamiento:** un efecto de "viñeta" para los materiales oscuros puede ayudar a centrar la atención del usuario en el centro del campo de vista. Este efecto oscuro el material del holograma en algún radio del vector de mirada del usuario. Esto también es efectivo cuando el usuario ve hologramas desde un ángulo oblicuo o de glancing.

* **Énfasis:** preste atención a objetos o puntos de interacción mediante el contraste de colores, brillo e iluminación. Para obtener una vista más detallada de los métodos de iluminación en la narración, vea [Pixel Icontography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Imagen: uso del color para mostrar el énfasis para contar historias de elementos, que se muestra aquí en una escena de [Fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*
    :::column-end:::
        :::column:::
        ![Uso del color para mostrar énfasis en los elementos de narración, que se muestran aquí en una escena de Fragmentos.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Materiales

:::row:::
    :::column:::
Los materiales son elementos fundamentales para crear hologramas realistas. Al proporcionar características visuales adecuadas, puede crear atractivos objetos holográficos que se puedan combinar bien con el entorno físico. Los materiales también son importantes para proporcionar comentarios visuales para los distintos tipos de interacciones de entrada del usuario.  

[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity) un sombreador estándar de MRTK con varias opciones de efecto visual que se pueden usar para los comentarios visuales. Por ejemplo, puede usar la propiedad "Proximity Light" para proporcionar un efecto de iluminación cuando el dedo del usuario se aproxima a la superficie del objeto. Más información sobre el [sombreador estándar de MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *Bucle de vídeo: ejemplo de comentarios visuales basados en la proximidad a un rectángulo de selección* 
     ![ Comentarios visuales sobre la proximidad a mano](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Consulte también
* [Diseño de contenido para la pantalla holográfica](designing-content-for-holographic-display.md)
* [Separación de colores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Hologramas](../discover/hologram.md)
* [Lenguaje de diseño de Microsoft: color](https://www.microsoft.com/design/color)
* [Plataforma Windows universal: color](/windows/uwp/style/color)