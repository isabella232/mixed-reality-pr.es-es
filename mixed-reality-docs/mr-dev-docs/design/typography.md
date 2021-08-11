---
title: Tipografía
description: Aprenda a diseñar e implementar texto como un elemento importante para entregar información en la experiencia de la aplicación de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, estilo, fuente, tipografía, interfaz de usuario, experiencia de usuario, texto, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens
ms.openlocfilehash: 7df2386f3478c0b0b79d198a3342bc9a9a061f6e5a305baedcd91be9c2f09f04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200326"
---
# <a name="typography"></a>Tipografía

![Ejemplo de tipografía en HoloLens](images/typography-cover.png)<br>


El texto es un elemento importante para entregar información en la experiencia de la aplicación. Al igual que la tipografía en las pantallas 2D, el objetivo es que sea clara y legible. Con el aspecto tridimensional de la realidad mixta, existe la oportunidad de afectar al texto y a la experiencia general del usuario de una manera aún mayor.

Cuando se habla del tipo en 3D, se tiende a pensar en texto 3D volumétrico y extruido. A excepción de algunos diseños de logotipos y algunas otras aplicaciones limitadas, el texto extruido tiende a degradar la legibilidad del texto. Aunque estamos diseñando experiencias para 3D, usamos 2D para el tipo porque es más legible y fácil de leer.

En HoloLens, el tipo se construye con hologramas mediante luz basada en el sistema de colores aditivos. Al igual que otros hologramas, el tipo se puede colocar en el entorno real, donde se puede bloquear y observar desde cualquier ángulo. El [efecto de paralaje](https://en.wikipedia.org/wiki/Parallax) entre el tipo y el entorno también agrega profundidad a la experiencia.

## <a name="typography-in-mixed-reality"></a>Tipografía en realidad mixta

Las reglas tipográficas de la realidad mixta no son diferentes de las de cualquier otro lugar. El texto tanto en el mundo físico como en el virtual debe ser legible y legible. El texto podría estar en una pared o superpuesto en un objeto físico. Podría estar flotante junto con una interfaz de usuario digital. Sea cual sea el contexto, aplicamos las mismas reglas tipográficas para la lectura y el reconocimiento.

### <a name="create-clear-hierarchy"></a>Creación de una jerarquía clara

Cree el contraste y la jerarquía mediante diferentes tamaños de tipo y pesos. Definir una rampa de tipos y seguirla a lo largo de la experiencia de la aplicación proporcionará una excelente experiencia de usuario con una jerarquía de información coherente.

![Ejemplos de rampa de tipos](images/typography-ramp-1000px.jpg)<br>
*Definir la rampa de tipos y seguirla a lo largo de la experiencia de la aplicación*

### <a name="limit-your-fonts"></a>Limitar las fuentes

Evite usar más de dos familias de fuentes diferentes en un único contexto. Demasiadas fuentes interrumpirán la sintonía y la coherencia de la experiencia y dificultarán el consumo de información. En HoloLens, dado que la información se sobrelada sobre el entorno físico, el uso de demasiados estilos de fuente degradará la experiencia. Segoe UI es la fuente de todos los diseños digitales de Microsoft. Se usa de forma coherente en el Windows Mixed Reality shell. Puede descargar el archivo de Segoe UI fuente desde la página Windows [kit de herramientas](/windows/uwp/design-downloads/)de diseño .

[Más información sobre el tipo Segoe UI tipo de letra](/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitar pesos de fuente finos

Evite usar pesos de fuentes ligeras o semiluz para tamaños de tipo inferiores a 42 pt, ya que los trazos verticales finos vibren y degradan la legibilidad. Las fuentes modernas con suficiente grosor de trazo funcionan bien. Por ejemplo, Helvetica y Arial son legibles en HoloLens pesos normales o en negrita.

### <a name="color"></a>Color

En HoloLens, dado que los hologramas se construyen con un sistema de luz aditiva, el texto blanco es muy legible. Puede encontrar ejemplos de texto en blanco en la menú Inicio y la barra Aplicación. Aunque el texto en blanco funciona bien sin una placa trasera en HoloLens, un fondo físico complejo podría dificultar la lectura del tipo. Se recomienda usar texto blanco en un fondo oscuro o coloreado para mejorar el foco del usuario y minimizar la distracción de un fondo físico.

<br>


![Se recomienda usar texto blanco en un fondo oscuro o coloreado. ](images/typography-whiteonblack2-1000px.jpg)
 *Ejemplos de texto blanco en un fondo oscuro o coloreado.*
<br>

Para usar texto oscuro, debe usar una placa de fondo brillante para que sea legible. En los sistemas de colores aditivos, el negro se muestra como transparente. Esto significa que no verá el texto negro sin una placa trasera de color.

:::row:::
    :::column:::
        ![Ejemplos de blanco sobre negro y negro sobre texto en blanco](images/typography-whiteonblack.png)<br>
        *Ejemplos de blanco sobre negro y negro sobre texto en blanco*<br>
    :::column-end:::
    :::column:::
        ![Ejemplos de texto negro en las aplicaciones del sistema: Tienda y Configuración](images/640px-typography-blackonwhite.jpg)<br>
        *Ejemplos de texto negro en las aplicaciones del sistema: Tienda y Configuración*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Tamaño de fuente recomendado

Como puede esperar, los tamaños de tipo que usamos en un equipo o un dispositivo de tableta (normalmente entre 12 y 32pt) tienen un aspecto pequeño a una distancia de 2 metros. Depende de las características de cada fuente, pero en general, el ángulo de visualización mínimo recomendado y la altura de la fuente para la legibilidad son aproximadamente de 0,35°-0,4°/12,21-13,97 mm según nuestros estudios de investigación de usuario. Se trata de entre 35 y 40 puntos con el factor de escalado introducido en la [página Texto en Unity.](../develop/unity/text-in-unity.md) 

Para la interacción cercana a 0,45 m (45 cm), el ángulo de visualización de la fuente legible mínima y la altura son de 0,4°-0,5° /3,14–3,9 mm. Se trata de entre 9 y 12 puntos con el factor de escalado introducido en [Texto en Unity.](../develop/unity/text-in-unity.md)

![Intervalo de interacción cercano y lejano ](images/typography-distance-1000px.jpg)
 *Contenido en un intervalo de interacción cercano y lejano*

### <a name="the-minimum-legible-font-size"></a>El tamaño mínimo de fuente legible

| Distancia | Ángulo | Alto del texto | Tamaño de fuente** |
|---------|---------|---------|---------|
| 45 cm (distancia de manipulación directa) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58 pt |

### <a name="the-comfortably-legible-font-size"></a>Tamaño de fuente legible cómodo

| Distancia | Ángulo | Alto del texto | Tamaño de fuente** |
|---------|---------|---------|---------|
| 45 cm (distancia de manipulación directa) | 0.65°-0.8° | 5,1-6,3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2 pt |


Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos. Evite el uso de familias de fuentes ligeras o semi ligeras en tamaño pequeño, ya que los trazos verticales finos se vibraciónrán y degradarán la legibilidad. Las fuentes modernas con suficiente grosor de trazo funcionan bien. Por ejemplo, Helvetica y Arial parecen impresionantes y son legibles en HoloLens con pesos normales o en negrita.

**Para obtener información más detallada sobre el cálculo del tamaño de texto en Unity, consulte [Texto en Unity.](../develop/unity/text-in-unity.md)**

![Ángulo de ](images/Text_In_Unity_ViewingAngle.jpg)
 *visualización Distancia de visualización, ángulo y alto del texto*

<br>

---

## <a name="resources"></a>Recursos

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Fuentes Segoe](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (Archivo ZIP)<br>
    ### <a name="hololens-fontbr"></a>[HoloLens fuente](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (Archivo ZIP)<br>
    <br>
    *Imagen: la fuente HoloLens proporciona los glifos de símbolos usados en Windows Mixed Reality.*
    :::column-end:::
        :::column:::
        ![La HoloLens fuente proporciona los glifos de símbolos usados en Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Consulte también

* [Texto en Unity](../develop/unity/text-in-unity.md)
* [Color, luz y materiales](./color-light-and-materials.md)