---
title: Indicación del progreso
description: Obtenga información sobre cómo los controles de progreso proporcionan comentarios al usuario sobre la ejecución de una operación de larga duración en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, interfaz de usuario, experiencia de usuario, indicador de progreso, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 8d397f627b55409d640ac6925a72d6bf169e207c27cb2a90bcee990c7a8d7683
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207889"
---
# <a name="progress-indicator"></a>Indicador de progreso

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Un control de progreso proporciona comentarios sobre una operación de ejecución larga en curso. Cuando un indicador de progreso está visible, los usuarios pueden ver el tiempo de espera y no pueden interactuar con la aplicación.

<br>

---

## <a name="types-of-progress"></a>Tipos de progreso

Es importante proporcionar al usuario información sobre lo que sucede. En realidad mixta, el entorno físico u los objetos pueden distraer fácilmente a los usuarios si la aplicación no tiene buenos comentarios visuales. Para situaciones que tarden unos segundos, como cuando se cargan datos o se actualiza una escena, es una buena idea mostrar un indicador visual. Hay dos opciones para mostrar al usuario que hay una operación en curso: una **barra de progreso** o un anillo de **progreso**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra de progreso<br>
        Una barra progreso muestra el porcentaje completado de una tarea. Debe usarse durante una operación cuya duración se conoce (determina), pero su progreso no debe bloquear la interacción del usuario con la aplicación.<br>
        <br>
        *Imagen: ejemplo de barra de progreso en HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Círculo de progreso<br>
        Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea la interacción del usuario hasta que se complete la operación.<br>
        <br>
        *Imagen: Ejemplo de anillo de progreso en HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Ejemplo de anillo de progreso en HoloLens dispositivo](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Progreso con un objeto personalizado<br>
        Puede agregar a la personalidad y la identidad de marca de la aplicación personalizando el control Progreso con sus propios objetos 2D/3D personalizados.<br>
        <br>
        *Imagen: Ejemplo de progreso con malla personalizada en HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Ejemplo de progreso con malla personalizada en HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Procedimientos recomendados

* Ajuste estrechamente [el formato o](billboarding-and-tag-along.md) la etiqueta junto a la presentación de Progreso, ya que el usuario puede mover fácilmente la cabeza a un espacio vacío y perder el contexto. Es posible que la aplicación parezca que se ha bloqueado si el usuario no puede ver nada. La marcación y la etiqueta se han integrado en el prefab Progreso.
* Siempre es bueno proporcionar información de estado sobre lo que sucede al usuario. El objeto prefab Progreso proporciona varios estilos visuales, incluido el Windows de tipo de anillo estándar para proporcionar el estado. También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Indicador de progreso en MRTK (Mixed Reality Toolkit) para Unity

* [MRTK: prefabs del indicador de progreso](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK: servicio de transición de escena](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


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