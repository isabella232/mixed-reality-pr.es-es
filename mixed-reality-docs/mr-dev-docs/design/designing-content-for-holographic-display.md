---
title: Diseño de contenido para la pantalla holográfica
description: Obtenga información sobre las directrices de diseño y los procedimientos recomendados para la visualización holográfica en dispositivos HoloLens.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Diseño de la interfaz de usuario, pantalla holográfica, diseño de contenido, tema oscuro, tema claro, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, diseño, píxeles
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600324"
---
# <a name="designing-content-for-holographic-display"></a>Diseño de contenido para la pantalla holográfica

![Ubicación de la mano de Ulnar](images/UX_Hero_DarkTheme.jpg)

Al diseñar contenido para pantallas holográficas, hay varios elementos que debe tener en cuenta para lograr la mejor experiencia. Hemos enumerado algunas de nuestras recomendaciones a continuación y puede obtener más información sobre las características de las pantallas holográficas en la página [Color, luz y materiales.](color-light-and-materials.md)

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Desafíos con el color brillante en una superficie grande 

En función de la investigación y las pruebas de la experiencia de HoloLens, encontramos que el uso de colores brillantes en una gran área de la pantalla puede causar varios problemas: 

**Agotamiento de los ojos** 

Puesto que la presentación holográfica es aditiva, los hologramas con colores brillantes usan más luz. Un color sólido y brillante en una gran área de la pantalla puede provocar fácilmente la agotamiento de los ojos para el usuario. 

**Oclusión de manos** 

El color brillante dificulta que el usuario vea sus manos al interactuar directamente con los objetos. Dado que el usuario no puede ver sus manos, resulta difícil percibir la profundidad o distancia entre la mano y el dedo hasta la superficie de destino. El cursor de dedo ayuda a compensar este problema, pero todavía puede ser difícil en una superficie blanca brillante. 

![Color y oclusión de la mano Difícil de ver la mano en la ](images/color_handocclusion.jpg)
 *placa posterior de contenido de color brillante*

**Uniformidad de color**

Debido a las características de las pantallas holográficas, una gran área brillante de la pantalla puede volverse blotchy. Mediante el uso de esquemas de color oscuro, puede minimizar este problema. 

## <a name="design-guidelines-for-color-choices"></a>Directrices de diseño para opciones de color

**Uso del color oscuro para el fondo de la interfaz de usuario**

Mediante el uso de la combinación de colores oscuros, puede minimizar la agotamiento de los ojos y mejorar la confianza en las interacciones directas con las manos. 

![Ejemplos de color oscuro usado para el fondo del contenido ](images/color_dark_examples.jpg)
 *Ejemplos de color oscuro usado para el fondo del contenido*

**Usar el grosor de la fuente semibólica o en negrita**

HoloLens permite que su experiencia muestre texto de alta resolución. Sin embargo, se recomienda evitar los pesos de fuente finos, como la luz o la semi light, ya que los trazos verticales pueden fluctuar en un tamaño de fuente pequeño. 

![El grosor de la fuente en negrita o en negrita (panel superior) mejora la legibilidad En negrita o ](images/color_font_examples.jpg)
 *en negrita (panel superior) mejora la legibilidad.*

**Uso del material HolographicBackplate de MRTK**

El material holographicBackplate se aplica a varios paneles de interfaz de usuario en el shell de HoloLens. Una de sus características es un efecto iridiscencia que es visible para los usuarios a medida que cambian de posición en función del panel. El color de la placa posterior cambia sutilmente a través de un espectro predefinido, lo que crea un efecto visual atractivo y dinámico sin interferir con la legibilidad del contenido. Este sutil cambio de color también sirve para compensar las pequeñas irregularidades de color. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Desafíos con la placa trasera transparente o translúcida de la interfaz de usuario 

![Ejemplos de interfaz de usuario ](images/color_transparent_examples.jpg)
 *transparente Ejemplos de placa trasera de interfaz de usuario transparente*

**Complejidad visual y accesibilidad**

Dado que los objetos holográficos se combinan con el entorno físico, el contenido o la legibilidad de la interfaz de usuario en ventanas transparentes o translúcidas podrían degradarse. Además, cuando los objetos holográficos transparentes se sobrelanan entre sí, podría dificultar la interacción del usuario debido a la profundidad confusa.

**Rendimiento**

Para que los objetos transparentes o translúcidos se representen correctamente, deben ordenarse y combinarse con cualquier objeto que exista en segundo plano. La ordenación de objetos transparentes tiene un costo de CPU moderado, la combinación tiene un costo considerable de GPU porque no permite que la GPU realice la eliminación de la superficie oculta mediante la selección z (es decir, pruebas de profundidad). No permitir la eliminación de la superficie oculta aumenta el número de operaciones necesarias para el píxel representado final. Esto aumenta las restricciones de la tasa de relleno de presión.

**Problema de estabilidad del holograma con la tecnología LSR de profundidad**

Para mejorar la reproducción holográfica o la estabilidad del holograma, una aplicación puede enviar un búfer de profundidad al sistema para cada fotograma representado. Al usar el búfer de profundidad para la reproducción, debe escribir un búfer de profundidad para cada color representado en píxeles con una profundidad correspondiente. Cualquier píxel con un valor de profundidad también debe tener un valor de color. Si no se sigue la guía anterior, las áreas de la imagen representada que carecen de información de profundidad válida se pueden volver a proyectar de forma que se produzcan artefactos, que a menudo son visibles como una distorsión de onda.


## <a name="design-guidelines-for-transparent-elements"></a>Directrices de diseño para elementos transparentes

**Uso del fondo opaco de la interfaz de usuario**

De forma predeterminada, los objetos transparentes o translúcidos no escriben profundidad para permitir una mezcla adecuada. Entre las formas de mitigar este problema se incluyen el uso de objetos opacos, la garantía de que los objetos translúcidos aparecen cerca de los objetos opacos (por ejemplo, un botón translúcido delante de una placa trasera opaca), forzar a los objetos translúcidos a escribir profundidad (no aplicable en todos los escenarios) o representar objetos proxy, que solo aportan valores de profundidad al final del fotograma.

Soluciones dentro de MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity  

Mediante el uso de una placa trasera sólida y opaca, podemos proteger la legibilidad y la confianza de interacción.

**Minimizar el número de píxeles afectados**

Si el proyecto debe usar objetos transparentes, intente minimizar el número de píxeles afectados. Por ejemplo, si un objeto solo está visible en determinadas condiciones (por ejemplo, un efecto de adiciones), deshabilite el objeto cuando sea totalmente invisible (en lugar de establecer el color de suma en negro). Para formas 2D sencillas creadas con un cuadrándido con una máscara alfa, considere la posibilidad de crear una representación de malla de la forma con un sombreador opaco en su lugar. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Ejemplos de interfaz de usuario oscura en MRTK (Mixed Reality Toolkit) para Unity

**[MRTK proporciona muchos](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ejemplos de bloques de creación de interfaz de usuario basados en las esquemas de color oscuro.

* [Menú Cerca](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [Diálogo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [Menú de mano](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a>Vea también

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