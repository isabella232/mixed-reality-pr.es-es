---
title: Objeto con el que se puede interactuar
description: Obtenga información sobre cómo desencadenar eventos, proporcionar indicaciones visuales e interactuar con objetos en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, controles, interacción, indicaciones, interfaz de usuario, experiencia de usuario, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, audio
ms.openlocfilehash: f1fe68c7f35fecb9fbee888893fb15a83a8595ec
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2021
ms.locfileid: "122683006"
---
# <a name="interactable-object"></a>Objeto con el que se puede interactuar

![Objetos interactibles](images/UX_Hero_Interactable.jpg)

Un botón ha sido durante mucho tiempo una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta tridimensional, ya no tenemos que limitarnos a este mundo de abstracción. Cualquier elemento puede ser **un objeto interactuable** que desencadene un evento. Un objeto interactuable puede ser cualquier cosa, desde una cafetera en una mesa hasta un globo en el aire. Seguimos utilizando botones tradicionales en determinadas situaciones, como en la interfaz de usuario del cuadro de diálogo. La representación visual del botón depende del contexto.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>Propiedades importantes del objeto interactuable

### <a name="visual-cues"></a>Indicaciones visuales

Las indicaciones visuales son indicaciones sensoras de la luz, recibidas por el ojo y procesadas por el sistema visual durante la percepción visual. Dado que el sistema visual es dominante en muchas especies, especialmente en los seres humanos, las indicaciones visuales son una gran fuente de información sobre cómo se percibe el mundo.

Dado que los objetos holográficos se mezclan con el entorno del mundo real en realidad mixta, podría ser difícil comprender con qué objetos puede interactuar. Para los objetos que se pueden interactuar en su experiencia, es importante proporcionar indicaciones visuales diferenciadas para cada estado de entrada. Esto ayuda al usuario a comprender qué parte de la experiencia es interactuable y hace que el usuario esté seguro mediante un método de interacción coherente.

<br>

---

### <a name="far-interactions"></a>Interacciones lejanas

Para cualquier objeto que el usuario pueda interactuar con la mirada, el rayo de la mano y el rayo del controlador de movimiento, se recomienda tener una indicación visual diferente para estos tres estados de entrada:

:::row:::
    :::column:::
       ![Objeto interactuable con estado predeterminado](images/interactibleobject-states-default.jpg)<br>
       **Estado predeterminado (observación)**<br>
        Estado de inactividad predeterminado del objeto.
    El cursor no está en el objeto . No se detecta la mano.
    :::column-end:::
    :::column:::
       ![Objeto interactuable con el destino y el estado del mouse](images/interactibleobject-states-targeted.jpg)<br>
        **Estado de destino (mantener el puntero)**<br>
        Cuando el destino del objeto es el cursor de mirada, la proximidad de los dedos o el puntero del controlador de movimiento.
    El cursor está en el objeto . Se detecta la mano, está lista.
    :::column-end:::
    :::column:::
       ![Objeto interactuable con estado presionado](images/interactibleobject-states-pressed.jpg)<br>
       **Estado presionado**<br>
        Cuando se presiona el objeto con un gesto de pulsar en el aire, presione el dedo o el botón de selección del controlador de movimiento.
    El cursor está en el objeto . Se detecta la mano, se pulsa en el aire.
    :::column-end:::
:::row-end:::

<br>

---

Puede usar técnicas como el resaltado o el escalado para proporcionar indicaciones visuales para el estado de entrada del usuario. En realidad mixta, puede encontrar ejemplos de visualización de diferentes estados de entrada en el menú Inicio y con botones de barra de la aplicación. 

Este es el aspecto de estos estados en un **botón holográfico:**

:::row:::
    :::column:::
       ![Botón holográfico en estado predeterminado](images/MRTK_InteractableState-default.jpg)<br>
       **Estado predeterminado (observación)**<br>
    :::column-end:::
    :::column:::
       ![Botón holográfico en estado de destino y mantener el puntero](images/MRTK_InteractableState-targeted.jpg)<br>
        **Estado de destino (mantener el puntero)**<br>
    :::column-end:::
    :::column:::
       ![Botón holográfico en estado presionado](images/MRTK_InteractableState-pressed.jpg)<br>
       **Estado presionado**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Interacciones cercanas (directas) 

HoloLens 2 admite la entrada de seguimiento de manos articulada, que permite interactuar con objetos. Sin comentarios hápticos y una percepción de profundidad perfecta, puede ser difícil saber a qué distancia está la mano de un objeto o si lo está tocándose. Es importante proporcionar suficientes indicaciones visuales para comunicar el estado del objeto, en particular el estado de las manos en función de ese objeto.

Use comentarios visuales para comunicar los estados siguientes:
* **Default (Observation):** estado de inactividad predeterminado del objeto.
* **Mantener** el puntero: cuando una mano está cerca de un holograma, cambie los objetos visuales para comunicar que la mano tiene como destino el holograma. 
* **Distancia y punto de** interacción: a medida que la mano se aproxima a un holograma, diseña comentarios para comunicar el punto de interacción proyectado y a qué distancia del objeto se encuentra el dedo
* **Contacto comienza:** cambia los objetos visuales (claro, color) para comunicar que se ha producido un toque.
* **Se entiende:** cambia los objetos visuales (claro, color) cuando se sujete el objeto
* **Extremos de contacto:** cambio de objetos visuales (claro, color) cuando ha finalizado la función táctil

<br>

---

:::row:::
    :::column:::
        ![Mantener el puntero (lejos)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Mantener el puntero (lejos)**<br>
        Resaltado basado en la proximidad de la mano.
    :::column-end:::
    :::column:::
        ![Mantener el puntero (cerca)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Mantener el puntero (cerca)**<br>
        Resalte los cambios de tamaño en función de la distancia a la mano.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Pulsar y presionar](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Pulsar y presionar**<br>
        Visual más comentarios de audio.
    :::column-end:::
    :::column:::
        ![Agarran](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Agarran**<br>
        Visual más comentarios de audio.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Un [botón en HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) es un ejemplo de cómo se visualizan los distintos estados de interacción de entrada:

:::row:::
    :::column:::
        ![Default](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Valor predeterminado**<br>
    :::column-end:::
    :::column:::
        ![Al mantener el puntero](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Al mantener el puntero**<br>
        Mostrar un efecto de iluminación basado en proximidad.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Tocar**<br>
        Mostrar efecto de efecto de
    :::column-end:::
    :::column:::
        ![Presione](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Presione**<br>
        Mueva la placa frontal.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>La indicación visual "anillo" en HoloLens 2<br>
        En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción de profundidad del usuario. Un anillo cerca de su dedo se muestra hacia arriba y se escala verticalmente a medida que el dedo se acerca al objeto. El anillo finalmente converge en un punto cuando se alcanza el estado presionado. Esta asequibilidad visual ayuda al usuario a comprender hasta qué punto está lejos del objeto.<br>
        <br>
        *Bucle de vídeo: ejemplo de comentarios visuales basados en la proximidad a un cuadro de límite*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Comentarios visuales sobre proximidad a mano](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Indicaciones de audio

En el caso de las interacciones directas con las manos, los comentarios de audio adecuados pueden mejorar drásticamente la experiencia del usuario. Use comentarios de audio para comunicar las indicaciones siguientes:
* **Contacto comienza:** reproducir sonido cuando comienza la táctil
* **Extremos de contacto:** reproducir sonido en el extremo táctil
* **Inicio de la toma:** reproducir sonido cuando se inicia la toma
* **Extremos de agarre:** reproducir sonido cuando finaliza el agarre

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Comandos de voz<br>
        Para los objetos que se pueden interactuar, es importante admitir opciones de interacción alternativas. De forma predeterminada, se recomienda que [se admiten comandos](../out-of-scope/voice-design.md) de voz para cualquier objeto que sea interactuable. Para mejorar la detectabilidad, también puede proporcionar información sobre herramientas durante el estado del mouse.<br>
        <br>
        *Imagen: Información sobre herramientas para el comando de voz*
    :::column-end:::
        :::column:::
       ![comandos de voz](images/640px-interactibleobject-voicecommand.png)<br>
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

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamaño de destino para la interacción de rayos de mano o mirada
| Distancia | Ángulo | Size |
|---------|---------|---------|
| 2 m  | no menor que 1° | 3,5 x 3,5 cm |

![Tamaño de destino para la interacción de rayos de mano o mirada](images/TargetSizingFar.jpg)<br>
*Tamaño de destino para la interacción de rayos de mano o mirada*

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Objeto interactuable en MRTK (Mixed Reality Toolkit) para Unity

En **[MRTK,](https://github.com/Microsoft/MixedRealityToolkit-Unity)** puede usar el script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para que los objetos respondan a varios tipos de estados de interacción de entrada. Admite varios tipos de temas que permiten definir estados visuales mediante el control de propiedades de objeto como el color, el tamaño, el material y el sombreador.

* [Interactuable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [Escena de ejemplos de interacción con la mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

El sombreador Estándar de MixedRealityToolkit  proporciona varias opciones, como la luz de proximidad, que le ayuda a crear indicaciones visuales y de audio.

* [Sombreador estándar de MRTK](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

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