---
title: Botón
description: Aprenda a desencadenar una acción inmediata con botones, que es uno de los componentes fundamentales de la realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality, controles, interacción, interfaz de usuario, experiencia de usuario, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, botón
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682986"
---
# <a name="button"></a>Button

![Button](images/UX_Hero_Button.jpg)

Un botón es uno de los elementos de interfaz de usuario más fundamentales y fundamentales de la realidad mixta. Permite a los usuarios desencadenar acciones inmediatas. Puesto que no hay comentarios físicos en la realidad mixta, es fundamental proporcionar suficientes comentarios visuales y de audio para aumentar la confianza de interacción del usuario. 

En HoloLens 2 diseño de botón, basado en muchas iteraciones de diseño, prototipos y estudios de investigación de usuarios, hemos integrado varias asequiciones visuales y indicaciones de audio que ayudan a la percepción e interacción de profundidad del usuario en un espacio vacío. 

## <a name="visual-affordances"></a>Asequibilidades visuales

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![Botón con efecto de luz de proximidad mostrado](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **Luz de proximidad**<br>
    :::column-end:::
    :::column:::
       ![Botón seleccionado con el efecto de resaltado de foco mostrado](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **Resaltado del foco**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Botón que se presiona con efecto de compresión de compresión](images/UX_Button_Affordance_Compression.jpg)<br>
       **Compresión de la caja de seguridad**<br>
    :::column-end:::
    :::column:::
       ![Botón que se presiona con el efecto de pulsación de desencadenador mostrado](images/UX_Button_Affordance_Pulse.jpg)<br>
        **Pulse on trigger (Pulse on trigger)**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>Indicaciones de audio

Los comentarios de audio adecuados pueden mejorar considerablemente la experiencia del usuario. HoloLens 2 botón de la aplicación proporciona comentarios de audio para comunicar las indicaciones siguientes:
* **Contacto comienza:** reproducir sonido cuando comienza la interacción táctil (interacción cercana)
* **Extremos de contacto:** reproducir sonido en el extremo táctil (interacción cercana)
* **Comienza el gesto** de acercar: reproducir el sonido en la selección de acercamiento (interacción lejana con la mirada o los rayos)
* **Extremos de acercamiento:** reproducir sonido en la versión de acercamiento (interacción lejana con mirada o rayos)

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>Comandos de voz<br>
        Para los botones de la realidad mixta, es importante admitir opciones de interacción alternativas. De forma predeterminada, se recomienda que los comandos de voz sean compatibles con los botones. En HoloLens 2 de botones de la cuenta, proporcionamos información sobre herramientas durante el estado del mouse para mejorar la detectabilidad.
    :::column-end:::
        :::column:::
       ![Entrada de voz](images/UX_Hero_VoiceCommand.jpg)<br>
        *Imagen: Información sobre herramientas para el comando de voz*
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>Recomendaciones de tamaño

Para asegurarse de que todos los objetos interactuables se puedan tocar fácilmente, se recomienda asegurarse de que el objeto interactuable cumple un tamaño mínimo en función de la distancia que se coloca desde el usuario. El ángulo visual a menudo se mide en grados de arco visual. El ángulo visual se basa en la distancia entre los ojos del usuario y el objeto y permanece constante, mientras que el tamaño físico del destino puede cambiar a medida que cambia la distancia desde el usuario. Para determinar el tamaño físico necesario de un objeto en función de la distancia del usuario, pruebe a usar una calculadora de ángulo visual como [esta](https://elvers.us/perception/visualAngle/).

A continuación se muestran las recomendaciones para los tamaños mínimos de contenido interactuable.

### <a name="target-size-for-direct-hand-interaction"></a>Tamaño de destino para la interacción directa con la mano

| Distancia | Ángulo | Size |
|---------|---------|---------|
| 45 cm  | no menor que 2° | 1,6 x 1,6 cm |

![Tamaño de destino para la interacción directa con la mano](images/TargetSizingNear.jpg)<br>
*Tamaño de destino para la interacción directa con la mano*

<br>

### <a name="target-size-for-buttons"></a>Tamaño de destino de los botones

Al crear botones para la interacción directa, se recomienda un tamaño mínimo mayor de 3,2 x 3,2 cm para asegurarse de que hay suficiente espacio para contener un icono y, posiblemente, algún texto.

| Distancia | Tamaño mínimo |
|---------|---------|
| 45 cm  | 3,2 x 3,2 cm |

![Tamaño de destino de los botones](images/TargetSizingButtons.png)<br>
*Tamaño de destino de los botones*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamaño de destino para la interacción de rayos de mano o mirada
| Distancia | Ángulo | Size |
|---------|---------|---------|
| 2 m  | no menor que 1° | 3,5 x 3,5 cm |

![Tamaño de destino para la interacción de rayos de mano o mirada](images/TargetSizingFar.jpg)<br>
*Tamaño de destino para la interacción de rayos de mano o mirada*

<br>

---

## <a name="design-guidelines"></a>Guías de diseño

### <a name="avoid-transparent-backplate"></a>Evitar la placa trasera transparente
Al diseñar la interfaz de usuario de menú con botones, se recomienda usar una placa trasera opaca. Las placas traseras transparentes no se recomiendan por los siguientes motivos:
* Es difícil interactuar con porque es difícil entender la profundidad con la que se debe presionar el botón para desencadenar el evento.
* Problema de legibilidad en un entorno físico complejo
* Hologramas muestra a través de la placa transparente puede mostrar un problema de efecto de la nada cuando se usa con la tecnología de estabilización LSR de profundidad.

Consulte [Diseño de contenido para la presentación holográfica](designing-content-for-holographic-display.md) para obtener más detalles sobre las opciones de color y las directrices para la visualización holográfica.

![Ejemplos de interfaz de usuario ](images/color_transparent_examples.jpg)
 *transparente Ejemplos de placa trasera de interfaz de usuario transparente*

<br>

### <a name="use-shared-backplate"></a>Uso de una placa trasera compartida
En el caso de varios botones, se recomienda usar la placa trasera compartida en lugar de la placa posterior del botón individual.

* Reducir el ruido visual y la complejidad
* Borrar agrupación  

![Ejemplos de placa trasera compartida Ejemplos ](images/Button_Design_SharedBackplate.png
)
 *de placa trasera de interfaz de usuario compartida*

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>Botón en MRTK (Mixed Reality Toolkit)
**[MRTK para Unity y](/windows/mixed-reality/mrtk-unity/)** **[MRTK para Unreal](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** proporcionan varios tipos de objetos prefabs de botón, incluidos HoloLens 2 de estilo. El HoloLens 2 componente de botón contiene todos los comentarios visuales y los detalles de interacción que se introdujeron en esta página. Al usarlo, puede aprovechar el resultado de muchas iteraciones de diseño e investigaciones de usuario que nuestros diseñadores, desarrolladores e investigadores han llevado a cabo.

Consulte el botón [MRTK - para](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) obtener más instrucciones y ejemplos personalizados.

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