---
title: Diseño de contenido para la pantalla holográfica
description: Obtenga información sobre las directrices de diseño y los procedimientos recomendados para la visualización holográfica.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Diseño de la interfaz de usuario, pantalla holográfica, diseño de contenido, tema oscuro, tema claro, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, diseño, píxeles
ms.openlocfilehash: 4a95f5df50a600035d9127c73f86a5d8be5e7131
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847987"
---
# <a name="designing-content-for-holographic-display"></a>Diseño de contenido para la pantalla holográfica

![Ubicación del lado de ulnar](images/UX_Hero_DarkTheme.jpg)

Al diseñar contenido para pantallas holográficas, hay varios elementos que debe tener en cuenta para lograr la mejor experiencia. Enumeramos algunas de las recomendaciones siguientes y puede obtener más información acerca de las características de las pantallas holográficas en la página [color, Light y materiales](color-light-and-materials.md) .

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Desafíos con color brillante en una superficie grande 
En función de nuestra experiencia de investigación y pruebas de HoloLens, encontramos que el uso de colores brillantes en un área grande de la pantalla puede producir varios problemas: 

**Fatiga ocular** 

Dado que la pantalla holográfica es aditiva, los hologramas con colores brillantes usan más luz. El color sólido y opaco en un área grande de la pantalla puede producir fácilmente fatiga ocular para el usuario. 

**Oclusión de mano** 

El color brillante dificulta que los usuarios vean sus manos al interactuar directamente con los objetos. Dado que el usuario no puede ver sus manos, resulta difícil percibir la profundidad o la distancia entre la mano y el dedo en la superficie de destino. El cursor de dedo ayuda a compensar este problema, pero puede seguir siendo desafiante en una superficie blanca brillante. 

![El color y la oclusión de mano ](images/color_handocclusion.jpg)
 *dificultan ver la mano en el fondo de contenido de color brillante*

**Uniformidad de color**

Debido a las características de las pantallas holográficas, un gran área brillante en la pantalla puede volverse manchada. El uso de esquemas de color oscuros le permite minimizar este problema. 

## <a name="design-guidelines-for-color-choices"></a>Instrucciones de diseño para las opciones de color

**Usar color oscuro para el fondo de la interfaz de usuario**

Mediante el uso de la combinación de colores oscuro, puede minimizar la fatiga ocular y mejorar la confianza en las interacciones de las manos directas. 

![Ejemplos de color oscuro usado para el fondo del contenido ](images/color_dark_examples.jpg)
 *ejemplos de color oscuro usado para el fondo del contenido*

**Usar el grosor de fuente seminegrita o negrita**

HoloLens permite que su experiencia muestre texto bonito de alta resolución. Sin embargo, se recomienda evitar los pesos de fuente finos, como la luz o la semiluz, ya que los trazos verticales pueden vibrar en un tamaño de fuente pequeño. 

![El grosor de fuente de negrita o seminegrita (panel superior) mejora la legibilidad en ](images/color_font_examples.jpg)
 *negrita o el espesor de fuente seminegrita (panel superior) mejora la legibilidad*

**Uso del material de HolographicBackplate de MRTK**

El material de HolographicBackplate se aplica a varios paneles de interfaz de usuario en el shell de HoloLens. Una de sus características es un efecto de Iridescence que es visible para los usuarios cuando cambian su posición en función del panel. El color de fondo se desplaza sutilmente a lo largo de un espectro predefinido, creando un efecto visual atractivo y dinámico sin interferir en la legibilidad del contenido. Este sutil cambio de color también sirve para compensar las irregularidades de los colores menores. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Desafíos con la plancha de la interfaz de usuario transparente o translúcida 

![Ejemplos de interfaz de usuario transparente ](images/color_transparent_examples.jpg)
 *ejemplos de planchas de interfaz de usuario transparentes*

**Complejidad visual y accesibilidad**

Dado que los objetos holográfica se fusionan con el entorno físico, el contenido o la legibilidad de la interfaz de usuario en ventanas transparentes o translúcidas podrían degradarse. Además, cuando los objetos holográficas transparentes se superponen entre sí, podría dificultar la interacción del usuario debido a la profundidad confusa.

**Rendimiento**

Para que los objetos transparentes o translúcidos se representen correctamente, deben ordenarse y combinarse con cualquier objeto que exista en segundo plano. La ordenación de objetos transparentes tiene un costo de CPU modesto, la fusión tiene un costo de GPU considerable, ya que no permite que la GPU realice la eliminación de la superficie oculta a través de la selección de z (es decir, pruebas de profundidad). No permitir la eliminación de superficies ocultas aumenta el número de operaciones necesarias para el píxel representado final. Esto coloca más restricciones de velocidad de relleno.

**Problema de estabilidad de holograma con tecnología LSR de profundidad**

Para mejorar la Reproyección holográfica o la estabilidad del holograma, una aplicación puede enviar un búfer de profundidad al sistema para cada fotograma representado. Cuando se usa el búfer de profundidad para la Reproyección, es necesario escribir un búfer de profundidad para cada píxel representado de color con una profundidad correspondiente. Cualquier píxel con un valor de profundidad también debe tener un valor de color. Si no se siguen las instrucciones anteriores, las áreas de la imagen representada que carecen de información de profundidad válida se pueden reproyectar de forma que generen artefactos, que a menudo son visibles como una distorsión de tipo onda.


## <a name="design-guidelines-for-transparent-elements"></a>Instrucciones de diseño para elementos transparentes

**Uso del fondo de la interfaz de usuario opaca**

De forma predeterminada, los objetos transparentes o translúcidos no escriben la profundidad para permitir una combinación adecuada. Algunas formas de mitigar este problema son el uso de objetos opacos, la garantía de que los objetos translúcidos aparecen cerca de los objetos opacos (por ejemplo, un botón translúcido delante de una placa posterior opaca), lo que fuerza la escritura de los objetos translúcidos (no aplicable en todos los escenarios) o la representación de objetos proxy, que solo contribuyen con valores de profundidad

Soluciones dentro de MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

Mediante el uso de una placa de fondo sólida y opaca, podemos proteger la legibilidad y la confianza de la interacción.

**Minimizar el número de píxeles afectados**

Si el proyecto debe utilizar objetos transparentes, intente minimizar el número de píxeles afectados. Por ejemplo, si un objeto solo está visible en determinadas condiciones (como un efecto de resplandor aditivo), deshabilite el objeto cuando sea totalmente invisible (en lugar de establecer el color aditivo en negro). En el caso de las formas 2D simples creadas con una cuádruple con una máscara alfa, considere la posibilidad de crear en su lugar una representación de malla de la forma con un sombreador opaco. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Ejemplos de interfaz de usuario oscuras en MRTK (kit de herramientas de realidad mixta) para Unity

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona muchos ejemplos de bloques de creación de interfaz de usuario basados en las combinaciones de colores oscuras.

* [Menú Near](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [Diálogo](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [Menú de la mano](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)

<br>

---

## <a name="see-also"></a>Consulte también

* [Color, luz y materiales](color-light-and-materials.md)
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
