---
title: Indicación del progreso
description: Obtenga información sobre cómo los controles de progreso proporcionan comentarios al usuario de que se está llevando a cabo una operación de ejecución prolongada en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, IU, experiencia de usuario, indicador de progreso, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: f323559c9a50a6f01636f0aba0bddc93b547125b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759851"
---
# <a name="progress-indicator"></a>Indicador de progreso

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Un control de progreso proporciona comentarios de que se está llevando a cabo una operación de ejecución prolongada. Cuando un indicador de progreso está visible, los usuarios pueden ver el tiempo de espera y no pueden interactuar con la aplicación.

<br>

---

## <a name="types-of-progress"></a>Tipos de progreso

Es importante proporcionar información de usuario sobre lo que está ocurriendo. En realidad mixta, los usuarios pueden distraerse fácilmente por el entorno físico u objetos si la aplicación no tiene buenos comentarios visuales. En situaciones en las que se tardan unos segundos, como cuando se cargan los datos o se actualiza una escena, es una buena idea mostrar un indicador visual. Hay dos opciones para mostrar el usuario que está realizando una operación: una **barra de progreso** o un **anillo de progreso**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra de progreso<br>
        Una barra de progreso muestra el porcentaje completado de una tarea. Se debe usar durante una operación cuya duración se conoce (determinan), pero su progreso no debe bloquear la interacción del usuario con la aplicación.<br>
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
        Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea la interacción del usuario hasta que se haya completado la operación.<br>
        <br>
        *Imagen: ejemplo de anillo de progreso en HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Ejemplo de anillo de progreso en el dispositivo HoloLens](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Progreso con un objeto personalizado<br>
        Puede Agregar a la identidad de personalidad y marca de la aplicación personalizando el control de progreso con sus propios objetos 2D/3D personalizados.<br>
        <br>
        *Imagen: progreso con el ejemplo de malla personalizada en HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Progreso con el ejemplo de malla personalizada en HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Procedimientos recomendados

* Encadenar estrechamente la [cartelera o etiqueta, junto](billboarding-and-tag-along.md) con la presentación de progreso, ya que el usuario puede trasladar fácilmente el encabezado a un espacio vacío y perder el contexto. La aplicación podría parecerse a que se ha bloqueado si el usuario no puede ver nada. La cartelera y el etiquetado están integrados en el recurso prefabricado de progreso.
* Siempre es conveniente proporcionar información de estado sobre lo que está ocurriendo al usuario. El recurso prefabricado de progreso proporciona varios estilos visuales, incluido el progreso de tipo anillo estándar de Windows para proporcionar el estado. También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Indicador de progreso en MRTK (kit de herramientas de realidad mixta) para Unity

* [MRTK: indicador de progreso Prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK: servicio de transición de escenas](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/extensions/scene-transition-service.md)


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
