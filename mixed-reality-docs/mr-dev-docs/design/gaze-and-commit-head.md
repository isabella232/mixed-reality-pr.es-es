---
title: Mirada con la cabeza y confirmación
description: Empiece a trabajar con el modelo de entrada y de confirmación del encabezado, incluido el ajuste de tamaño, la ubicación y la estabilización de destino.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realidad mixta, miración rápida, interacción, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, destino, enfoque, suavizado
ms.openlocfilehash: a69b855e2246327affeeb0f771f565b94ea65cb2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582288"
---
# <a name="head-gaze-and-commit"></a>Mirada con la cabeza y confirmación

La acción de _mirar y confirmar_ es un caso especial del modelo de entrada de [mirada y de confirmación](gaze-and-commit.md) que implica el destino de un objeto con la dirección del encabezado de un usuario. Puede actuar en el destino con una entrada secundaria, como el gesto de mano tocar o "seleccionar" comando de voz. 

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mirada con la cabeza y confirmación</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</td>
        <td>➕ Opción alternativa</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>Ajuste de tamaño del destino y comentarios

El vector de miras hacia abajo se ha mostrado varias veces para que se pueda usar para lograr objetivos más precisos, pero a menudo funciona mejor para la segmentación bruta: adquisición de destinos más grandes. Los tamaños mínimos de destino de 1 grado a 1,5 grados permiten acciones de usuario correctas en la mayoría de los escenarios, aunque los destinos de 3 grados a menudo permiten una mayor velocidad. El tamaño que tiene como destino el usuario es, en efecto, un área 2D incluso para los elementos 3D, lo que se enfrente a la proyección debe ser el área de destino. Proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario tiene como destino) es útil. Esto puede incluir tratamientos como efectos visibles de "mantener el mouse", resaltados de audio o clics o alineación clara de un cursor con un elemento.

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño óptimo de destino a una distancia de 2 metros*

<br>

![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-940px.jpg)<br>
*Ejemplo de resaltado de un objeto establecido como destino de la mirada*

## <a name="target-placement"></a>Situación del destino

A menudo, los usuarios no pueden encontrar elementos de la interfaz de usuario ubicados demasiado altos o bajos en su campo de vista. La mayor parte de su atención termina en áreas en torno a su enfoque principal, que es aproximadamente en el nivel de ojo. Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos. Dado que la tendencia de los usuarios a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de visión es aproximadamente de 10 grados), la agrupación de los elementos de la interfaz de usuario en el grado en que se relacionan conceptualmente puede usar los comportamientos de encadenamiento de atención entre el elemento y el elemento cuando un usuario mueve su vista hacia abajo por un área Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.

![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Mejora de los comportamientos de establecimiento de destino

Si la intención del usuario de destinar algo puede determinarse o aproximarse, puede ser útil aceptar los intentos de interacción aproximados como si estuviesen dirigidos correctamente. Estos son algunos de los métodos correctos que se pueden incorporar en experiencias de realidad mixta:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilización de la mirada con la cabeza ("pozos de gravedad")

Esto se debe activar la mayoría o la totalidad del tiempo. Esta técnica elimina las vibraciones de cabeza natural y cuello que los usuarios podrían tener como movimiento debido a los comportamientos de mirar y hablar.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo más cercano

Estos algoritmos funcionan mejor en áreas con contenido interactivo disperso. Si hay una probabilidad alta de que pueda determinar con qué un usuario estaba intentando interactuar, puede complementar sus capacidades de destino suponiendo cierto nivel de intento.

### <a name="backdating-and-postdating-actions"></a>Acciones de la

Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario está pasando por una serie de destinos y maniobras de activación a velocidad, resulta útil asumir algún intento. También resulta útil permitir que los pasos perdidos actúen en los destinos que el usuario tenía enfocado ligeramente antes o ligeramente después de la pulsación (50 ms antes/después era efectivo en las primeras pruebas).

### <a name="smoothing"></a>Suavizado

Este mecanismo es útil para los movimientos de las acciones, lo que reduce la ligera vibración y wobbles debido a las características de movimiento del cabezal natural. Al suavizar los movimientos de las acciones, smoothándose por el tamaño y la distancia de los movimientos en lugar de a lo largo del tiempo.

### <a name="magnetism"></a>Magnetismo

Este mecanismo puede considerarse como una versión más general de los algoritmos de vínculo más cercanos: dibujar un cursor hacia un destino o simplemente aumentar hitboxes, ya sea visible o no, a medida que los usuarios se aproximan a los objetivos más probables mediante el uso de algún conocimiento del diseño interactivo para un mejor enfoque de la intención del usuario. Esto puede ser eficaz para destinos pequeños.

### <a name="focus-stickiness"></a>Permanencia del foco

A la hora de determinar qué elementos interactivos cercanos se deben dar, centrarse en, el ajuste del foco proporciona una inclinación al elemento que está enfocado actualmente. Esto ayuda a reducir los comportamientos de cambio de foco errático al flotar en un punto medio entre dos elementos con ruido natural.

## <a name="see-also"></a>Consulte también

* [Interacción basada en los ojos](eye-gaze-interaction.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)