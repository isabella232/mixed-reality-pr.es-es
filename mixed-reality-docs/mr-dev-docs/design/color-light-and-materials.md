---
title: Color, luz y materiales
description: El diseño de contenido para la realidad mixta requiere una cuidadosa consideración del color, la iluminación y los materiales de todos los recursos visuales.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, color, luz, materiales, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 2e1626e72d49107c2a83bf1123b306d3ee5c8640
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600364"
---
# <a name="color-light-and-materials"></a>Color, luz y materiales

![Color, luz y materiales](images/RemoteRendering.jpg)

El diseño de contenido para la realidad mixta requiere una cuidadosa consideración del color, la iluminación y los materiales de todos los recursos virtuales. Los propósitos éticos pueden incluir el uso de luz y material para establecer el tono de un entorno envolvente, mientras que los propósitos funcionales pueden incluir el uso de colores sorprendentes para alertar a los usuarios de una acción inminente. Cada una de estas decisiones debe ponderarse con las oportunidades y restricciones del dispositivo de destino de su experiencia.

A continuación se muestran instrucciones específicas para representar recursos en cascos envolventes y holográficos. Muchas de ellas están estrechamente vinculadas a otras áreas técnicas [](color-light-and-materials.md#see-also) y se puede encontrar una lista de temas relacionados en la sección Ver también al final de este artículo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Representación en dispositivos envolventes frente a holográficos

El contenido representado en cascos envolventes aparecerá visualmente diferente en comparación con el contenido representado en cascos holográficos. Aunque los cascos envolventes suelen representar el contenido de la forma esperada en una pantalla 2D, los cascos holográficos como HoloLens usan pantallas RGB secuenciales de color y de visualización a través para representar hologramas.

Tómese siempre tiempo para probar sus experiencias holográficas en un casco holográfico. La apariencia del contenido, incluso si se ha creado específicamente para dispositivos holográficos, será diferente como se ve en monitores secundarios, instantáneas y en la vista del espectador. No olvide recorrer las experiencias con un dispositivo, probar la iluminación de hologramas y observar desde todos los lados (así como desde arriba y abajo) cómo se representa el contenido. Asegúrese de probar con una variedad de configuraciones de brillo en el dispositivo. Es poco probable que todos los usuarios compartan un supuesto valor predeterminado y un conjunto diverso de condiciones de iluminación.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Aspectos básicos de la representación en dispositivos holográficos

* **Los dispositivos holográficos** tienen pantallas de suma: los hologramas se crean mediante la adición de luz a la luz del mundo real; el blanco aparecerá de forma brillante, mientras que el negro aparecerá transparente.

* **El impacto en los colores varía en función** del entorno del usuario: hay muchas condiciones de iluminación diversas en la habitación de un usuario. Cree contenido con los niveles de contraste adecuados para ayudar a mejorar la claridad.

* **Evitar la iluminación dinámica:** los hologramas que se encienden uniformemente en experiencias holográficas son los más eficaces. Es probable que el uso de iluminación dinámica avanzada supere las funcionalidades de los dispositivos móviles. Cuando se requiere iluminación dinámica, se recomienda usar el [sombreador Mixed Reality Toolkit Standard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md). 

## <a name="designing-with-color"></a>Diseño con color

Debido a la naturaleza de las pantallas de adiciones, determinados colores pueden aparecer diferentes en las pantallas holográficas. Algunos colores aparecerán en entornos de iluminación, mientras que otros aparecerán como menos afectados. Los colores es cool tienden a retroceder al fondo, mientras que los colores en caliente saltan al primer plano. Tenga en cuenta estos factores a medida que explora el color en sus experiencias:

* **Representación de colores claros:** el blanco aparece claro y se debe usar con moderación. En la mayoría de los casos, considere un valor blanco alrededor de R 235 G 235 B 235. Las áreas brillantes de gran tamaño pueden causar molestias en el usuario. Para la placa trasera de la ventana de interfaz de usuario, se recomienda usar colores oscuros.

* **Representación de colores oscuros:** debido a la naturaleza de las pantallas de suma, los colores oscuros aparecen transparentes. Un objeto negro sólido no aparecerá diferente del mundo real. Consulte canal alfa a continuación. Para dar la apariencia de "negro", pruebe un valor RGB gris muy oscuro, como 16,16,16.

* **Uniformidad del color:** normalmente, los hologramas se representan lo suficientemente claros como para mantener la uniformidad del color, sea cual sea el fondo. Las áreas grandes pueden volverse blotchy. Evite regiones grandes de color sólido y brillante.

* **Gama:** HoloLens se beneficia de una "amplia gama" de color, conceptualmente similar a Adobe RGB. Como resultado, algunos colores pueden mostrar diferentes calidades y representación en el dispositivo.

* **Gamma:** el brillo y el contraste de la imagen representada variarán entre los dispositivos envolventes y holográficos. A menudo, estas diferencias de dispositivo parecen hacer que las áreas oscuras de color y sombras, más o menos brillantes.

* **Separación de** colores: también denominada "separación de colores" o "fringing de color", la separación de colores se produce normalmente con hologramas móviles (incluido el cursor) cuando un usuario realiza un seguimiento de los objetos con los ojos.

## <a name="technical-considerations"></a>Consideraciones técnicas

* **Aliasing:** tenga en cuenta los alias, escalonados o "pasos de escalón" donde el borde de la geometría de un holograma se encuentra con el mundo real. El uso de texturas con detalles elevados puede ayudar a este efecto. Las texturas se deben asignar y habilitar el filtrado. Considere la posibilidad de desvanerse los bordes de los hologramas o agregar una textura que cree un borde de borde negro alrededor de los objetos. Evite la geometría fina siempre que sea posible.

* **Canal alfa:** debe borrar el canal alfa para que sea totalmente transparente para cualquier parte en la que no esté representando un holograma. Dejar el alfa sin definir conduce a artefactos visuales al tomar imágenes o vídeos desde el dispositivo o con la vista del espectador.

* **Suavizado de textura:** dado que la luz se suma en pantallas holográficas, es mejor evitar regiones grandes de color sólido y brillante, ya que a menudo no producen el efecto visual previsto.

## <a name="design-guidelines-for-holographic-display"></a>Directrices de diseño para la presentación holográfica

![Color y oclusión de manos](images/color_handocclusion.jpg)

Al diseñar contenido para pantallas holográficas, hay varios elementos que debe considerar para lograr la mejor experiencia. Visite [Diseño de contenido para la presentación holográfica](designing-content-for-holographic-display.md) para obtener instrucciones y recomendaciones.

## <a name="storytelling-with-light-and-color"></a>Narración con luz y color

La luz y el color pueden ayudar a que los hologramas aparezcan de forma más natural en el entorno de un usuario y ofrecer orientación y ayuda para el usuario. Para las experiencias holográficas, tenga en cuenta estos factores a medida que explora la iluminación y el color:

:::row:::
    :::column:::
* **Aderezo:** un efecto de "viñeta" para los materiales oscuros puede ayudar a centrar la atención del usuario en el centro del campo de vista. Este efecto oscurece el material del holograma en algún radio del vector de mirada del usuario. Esto también es eficaz cuando el usuario ve hologramas desde un ángulo oblicuo o de glancing.

* **Énfasis:** preste atención a objetos o puntos de interacción mediante el contraste de colores, brillo e iluminación. Para obtener una vista más detallada de los métodos de iluminación en la narración, vea [Pixel Quetography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Imagen: uso del color para mostrar el énfasis en la narración de elementos, que se muestra aquí en una escena de [Fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*
    :::column-end:::
        :::column:::
        ![Uso de color para mostrar énfasis en los elementos de narración, que se muestran aquí en una escena de Fragmentos.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Materiales

:::row:::
    :::column:::
Los materiales son elementos fundamentales para crear hologramas realistas. Al proporcionar las características visuales adecuadas, puede crear objetos holográficos atractivos que se puedan combinar bien con el entorno físico. Los materiales también son importantes para proporcionar comentarios visuales para los distintos tipos de interacciones de entrada del usuario.  

[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity) un sombreador estándar de MRTK con varias opciones de efecto visual que se pueden usar para los comentarios visuales. Por ejemplo, puede usar la propiedad "Luz de proximidad" para proporcionar un efecto de iluminación cuando el dedo del usuario se aproxima a la superficie del objeto. Más información sobre el [sombreador estándar de MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *Bucle de vídeo: ejemplo de comentarios visuales basados en la proximidad a un cuadro de límite* 
     ![ Comentarios visuales sobre proximidad a mano](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Vea también
* [Diseño de contenido para la pantalla holográfica](designing-content-for-holographic-display.md)
* [Separación de colores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Hologramas](../discover/hologram.md)
* [Lenguaje de diseño de Microsoft: color](https://www.microsoft.com/design/color)
* [Plataforma universal de Windows: color](/windows/uwp/style/color)