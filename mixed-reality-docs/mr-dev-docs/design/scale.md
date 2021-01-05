---
title: Escala
description: Una clave para mostrar contenido que parezca real en forma de holograma es imitar las estadísticas visuales del mundo real de la manera más semejante posible.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, estilo, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, escala, hologramas
ms.openlocfilehash: 6711a58fb4dde2aa28272c3003e642c4f4d3e236
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848272"
---
# <a name="scale"></a>Escala

La clave para mostrar contenido holográfica realista es imitar las estadísticas visuales del mundo real lo más cerca posible. Incorpore indicaciones visuales para ayudar a los usuarios del mundo real a comprender dónde están los objetos, lo grande que son y de qué se han hecho. La escala de un objeto es una de las indicaciones visuales más importantes, ya que proporciona al visor un sentido del tamaño y las indicaciones de los objetos en su ubicación. Además, la visualización de objetos en escala real es uno de los diferenciadores de experiencia clave para la realidad mixta en general, algo que no ha sido posible en la visualización anterior basada en la pantalla.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Cómo sugerir la escala de objetos y entornos

Hay muchas maneras de sugerir la escala de un objeto, algunas de las cuales tienen efectos posibles en otros factores de percepción. La clave uno es mostrar los objetos en un tamaño "real" y mantener ese tamaño realista a medida que los usuarios se mueven. Los hologramas ocuparán una cantidad diferente del ángulo visual de un usuario a medida que se acerquen o alejen, del mismo modo que los objetos reales.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Usar la distancia de los objetos a medida que se presentan al usuario

Un método común es usar la distancia de los objetos a medida que se presentan al usuario. Por ejemplo, considere la posibilidad de visualizar un automóvil de gran familia delante del usuario. Si el coche estaba delante de ellos en la longitud de ARM, sería demasiado grande para caber en el campo de vista del usuario. Los objetos de cierre requieren que el usuario mueva el encabezado y el cuerpo para comprender el objeto completo. Si el coche se coloca más lejos (en todo el salón), el usuario puede establecer un sentido de escala viendo todo el objeto en su campo de vista. Después, los usuarios pueden moverse más cerca del objeto para obtener una inspección más detallada.

:::row:::
    :::column:::
        **[Volvo usó esta técnica para crear una](https://www.youtube.com/watch?v=DilzwF90vec)** experiencia de sala de exposición para un coche nuevo, usando la escala del coche holográfica de una forma que se sentía realista e intuitiva para el usuario. La experiencia comienza con el holograma del automóvil en una tabla física, lo que permite al usuario comprender el tamaño y la forma totales del modelo. Más adelante en la experiencia, el coche se expande a una escala más allá del tamaño del campo de vista del dispositivo. Puesto que el usuario ya ha adquirido un marco de referencia del modelo más pequeño, puede desplazarse de forma adecuada en torno a las características del coche.<br>
        <br>
        *Imagen: la experiencia de Volvo Cars para HoloLens*
    :::column-end:::
        :::column:::
       ![Experiencia de Volvo Cars para HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usar hologramas para modificar el espacio real del usuario

Otro método consiste en usar hologramas para modificar el espacio real del usuario, reemplazando los planos laterales o techos existentes con entornos o anexando ' huecos ' o ' Windows '. Esto permite que los objetos con un tamaño superior parezcan "desplazarse" del espacio físico. Por ejemplo, un árbol grande podría no caber en la mayoría de los salones de los usuarios, pero al colocar un cielo virtual en el límite superior, el espacio físico se expande en el virtual. Esto permite al usuario desplazarse por la base del árbol virtual y recopilar una idea de la escala y la apariencia del mundo real. A continuación, los usuarios pueden buscar para ver si se extiende mucho más allá del espacio físico del salón.

:::row:::
    :::column:::
        **[Minecraft desarrolló experiencias de concepto](https://minecraft.net/)** mediante una técnica similar. Al agregar una ventana virtual a una superficie física, los objetos existentes en el salón se colocan en el contexto de un entorno de gran tamaño, más allá de las limitaciones de escala física de la habitación.<br>
        <br>
        *Imagen: Minecraft concepto Experience para HoloLens*
    :::column-end:::
        :::column:::
       ![Experiencia de concepto de Minecraft para HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentación con escala

Los diseñadores han experimentado la modificación de la escala cambiando el tamaño "real" mostrado del objeto. Al mismo tiempo, mantienen una única posición de objeto para aproximar un objeto que se desplaza hacia el visor sin ningún movimiento real. Esto se probó en algunos casos como una forma de simular la visualización vertical de los elementos, a la vez que sigue respetando las posibles limitaciones de comodidad de ver el contenido virtual más cerca de la "zona de confort" que sugeriría.

Sin embargo, esto puede crear algunos artefactos posibles en la experiencia:
* En el caso de los objetos virtuales que representan algún objeto con un tamaño ' conocido ' en el visor, el cambio de la escala sin cambiar la posición conduce a indicaciones visuales en conflicto. Los ojos todavía pueden "ver" el objeto a cierta profundidad debido a las indicaciones de vergence. Para obtener más información, vea el artículo de la [comodidad](comfort.md) . El tamaño actúa como una indicación de cierre que el objeto podría estar más cerca. Estas claves conflictivas conducen a una percepción de confusión: los visores ven a menudo el objeto como permanece en su lugar (debido a la indicación de profundidad constante), pero aumentan rápidamente.
* En algunos casos, el cambio de escala se considera como una indicación de "tela" en su lugar, donde el objeto puede o no verse para cambiar la escala de un visor, pero parece moverse directamente hacia los ojos del espectador (lo que puede ser un repentino incómodo).
* Con las superficies de comparación en el mundo real, los cambios de escalado a veces se ven como una posición cambiante a lo largo de varios ejes: los objetos parecen inferiores en lugar de moverse más hacia abajo (similar en una proyección 2D del movimiento 3D en algunos casos).
* Por último, para los objetos que no tienen un tamaño conocido del "mundo real" (por ejemplo, formas arbitrarias con tamaños arbitrarios, elementos de la interfaz de usuario, etc.), cambiar la escala puede actuar funcionalmente como una manera de imitar los cambios de distancia. Los visores no tienen tantas guías arriba preexistentes para comprender el tamaño o la ubicación verdaderos del objeto, por lo que la escala se puede procesar como una pista más importante.

<br>

---

## <a name="see-also"></a>Consulte también
* [Color, luz y materiales](../color,-light-and-materials.md)
* [Tipografía](typography.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
