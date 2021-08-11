---
title: Escala
description: Una clave para mostrar contenido que parezca real en forma de holograma es imitar las estadísticas visuales del mundo real de la manera más semejante posible.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, estilo, diseño, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, escala, hologramas
ms.openlocfilehash: 0b643b7f4b53795afa6bac9b54e55565233ac1d96a6a58d5389a8a4b7db8d7cc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223016"
---
# <a name="scale"></a>Escala

La clave para mostrar contenido holográfico realista es imitar las estadísticas visuales del mundo real lo más de cerca posible. Incorpore indicaciones visuales para ayudar a los usuarios del mundo real a comprender dónde están los objetos, lo grandes que son y de qué están hechos. La escala de un objeto es una de las indicaciones visuales más importantes, ya que proporciona al visor una idea del tamaño de los objetos e indicaciones a su ubicación. Además, la visualización de objetos a escala real es uno de los diferenciadores clave de la experiencia para la realidad mixta en general, algo que no ha sido posible en la visualización basada en pantalla anterior.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Cómo sugerir la escala de objetos y entornos

Hay muchas maneras de sugerir la escala de un objeto, algunas de las cuales tienen posibles efectos en otros factores perceptuales. La clave es mostrar objetos con un tamaño "real" y mantener ese tamaño realista a medida que los usuarios se mueven. Hologramas ocupará una cantidad diferente del ángulo visual de un usuario a medida que se acerque o se acerque más lejos, de la misma manera que lo hacen los objetos reales.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Usar la distancia de los objetos a medida que se presentan al usuario

Un método común es usar la distancia de los objetos a medida que se presentan al usuario. Por ejemplo, considere la posibilidad de visualizar un automóvil de familia grande delante del usuario. Si el automóvil estaba directamente delante de ellos dentro de la longitud del brazo, sería demasiado grande para caber en el campo de vista del usuario. Los objetos de cierre requieren que el usuario mueva la cabeza y el cuerpo para comprender la totalidad del objeto. Si el automóvil se coloca más lejos (a través de la sala), el usuario puede establecer una sensación de escala viendo todo el objeto en su campo de visión. A continuación, los usuarios podrían acercarse al objeto para una inspección más detallada.

:::row:::
    :::column:::
        **[Así, Usaba esta](https://www.youtube.com/watch?v=DilzwF90vec)** técnica para crear una experiencia de sala de presentación para un automóvil nuevo, usando la escala del automóvil holográfico de una manera que se sintía realista e intuitiva para el usuario. La experiencia comienza con el holograma del automóvil en una tabla física, lo que permite al usuario comprender el tamaño total y la forma del modelo. Más adelante en la experiencia, el automóvil se expande a una escala más allá del tamaño del campo de visión del dispositivo. Dado que el usuario ya ha adquirido un marco de referencia del modelo más pequeño, puede navegar adecuadamente por las características del automóvil.<br>
        <br>
        *Imagen: Experiencia de Cars para HoloLens*
    :::column-end:::
        :::column:::
       ![Experiencia de Cars para HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Uso de hologramas para modificar el espacio real del usuario

Otro método consiste en usar hologramas para modificar el espacio real del usuario, reemplazar las paredes o el suelo existentes por entornos o anexar "huecos" o "ventanas". Esto permite que los objetos de gran tamaño parezcan "interrumpir" el espacio físico. Por ejemplo, un árbol grande podría no caber en las salas de la mayoría de los usuarios, pero al colocar un cielo virtual en su parte superior, el espacio físico se expande a la virtual. Esto permite al usuario recorrer la base del árbol virtual y recopilar una sensación de escala y apariencia real. A continuación, los usuarios pueden buscar para ver que se extiende mucho más allá del espacio físico de la sala.

:::row:::
    :::column:::
        **[Minecraft un concepto experiencias](https://minecraft.net/)** con una técnica similar. Al agregar una ventana virtual a una superficie física, los objetos existentes en la sala se colocan en el contexto de un entorno mucho mayor, más allá de las limitaciones de escala física de la sala.<br>
        <br>
        *Imagen: experiencia Minecraft concepto de HoloLens*
    :::column-end:::
        :::column:::
       ![Minecraft de concepto para HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentación con la escala

Los diseñadores han experimentado con la modificación de la escala cambiando el tamaño "real" mostrado del objeto. Al mismo tiempo, mantienen una posición de objeto única para aproximarse a un objeto que se mueve hacia el visor sin ningún movimiento real. Esto se ha probado en algunos casos como una manera de simular una visualización de los elementos de cerca, a la vez que se respetan las posibles limitaciones de confort de ver contenido virtual más cerca de lo que sugeriría la "zona de confort".

Sin embargo, esto puede crear algunos artefactos posibles en la experiencia:
* Para los objetos virtuales que representan algún objeto con un tamaño "conocido" para el visor, cambiar la escala sin cambiar la posición conduce a indicaciones visuales en conflicto. Es posible que los ojos todavía "vean" el objeto con cierta profundidad debido a indicaciones de permanencia. Para obtener más información, consulte el [artículo Confort.](comfort.md) El tamaño actúa como una indicación monocular de que el objeto puede estar cada vez más cerca. Estas indicaciones en conflicto conducen a percepciones confusas: los espectadores suelen ver que el objeto permanece en su lugar (debido a la indicación de profundidad constante), pero crece rápidamente.
* En algunos casos, el cambio de escala se ve como una indicación de "pendiente", donde el objeto puede o no ser visto para cambiar la escala por un visor, pero parece que se mueve directamente hacia los ojos del visor (lo que puede ser una incomodidad).
* Con las superficies de comparación en el mundo real, estos cambios de escalado a veces se ven como cambios de posición en varios ejes: los objetos parecen bajar en lugar de acercarse (similar en una proyección 2D del movimiento 3D en algunos casos).
* Por último, para los objetos sin un tamaño conocido del "mundo real" (por ejemplo, formas arbitrarias con tamaños arbitrarios, elementos de interfaz de usuario, entre otros), el cambio de escala puede actuar funcionalmente como una manera de imitar los cambios en la distancia. Los visores no tienen tantas indicaciones de arriba abajo preexistentes para comprender el tamaño verdadero o la ubicación del objeto, por lo que la escala se puede procesar como una indicación más importante.

<br>

---

## <a name="see-also"></a>Consulte también
* [Color, luz y materiales](./color-light-and-materials.md)
* [Tipografía](typography.md)
* [Diseño de sonido espacial](spatial-sound-design.md)