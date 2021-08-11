---
title: Mirada con la cabeza y confirmación
description: Introducción al modelo de entrada de mirada con la cabeza y confirmación, incluido el tamaño de destino, la colocación y la estabilización.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, mirada, objetivo de mirada, interacción, diseño, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, destino, foco, suavizado
ms.openlocfilehash: 641e403df23b2559429ca80aa06f384c4845ee347518adca2cfde1b3dbe874dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223668"
---
# <a name="head-gaze-and-commit"></a>Mirada con la cabeza y confirmación

_La mirada con la cabeza_ y [](gaze-and-commit.md) la confirmación es un caso especial del modelo de entrada de mirada y confirmación que implica dirigirse a un objeto con una dirección principal de los usuarios. Puede actuar en el destino con una entrada secundaria, como el gesto de la mano pulsación en el aire o el comando de voz "Seleccionar". 

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

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demostración de los conceptos de diseño de seguimiento de la cabeza y los ojos

Si quiere ver en acción los conceptos de diseño de seguimiento de cabeza y manos, consulte nuestra demostración de vídeo **Diseño de hologramas: Seguimiento de cabeza y seguimiento de manos** a continuación. Cuando haya terminado, continúe para profundizar más en detalle en temas específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo se tomó de la aplicación "Designing Holograms" para HoloLens 2. Descargue y disfrute de la experiencia completa [aquí](https://aka.ms/dhapp).*

## <a name="target-sizing-and-feedback"></a>Ajuste de tamaño del destino y comentarios

Se ha mostrado repetidamente que el vector de mirada con la cabeza se puede usar para la selección de destinos correcta, pero a menudo funciona mejor para la selección de destinos brutos, ya que se adquieren objetivos más grandes. Los tamaños de destino mínimos de 1 a 1,5 grados permiten acciones correctas del usuario en la mayoría de los escenarios, aunque los objetivos de 3 grados a menudo permiten una mayor velocidad. El tamaño que el usuario tiene como destino es efectivamente un área 2D incluso para los elementos 3D, la proyección a la que se enfrentan debe ser el área de destino. Proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario tiene como destino) es útil. Esto puede incluir tratamientos como efectos visibles de "mantener el puntero", resaltados o clics de audio, o una alineación clara de un cursor con un elemento.

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de destino óptimo a una distancia de 2 metros*

<br>

![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-940px.jpg)<br>
*Ejemplo de resaltado de un objeto establecido como destino de la mirada*

## <a name="target-placement"></a>Situación del destino

A menudo, los usuarios no encuentran elementos de la interfaz de usuario que se encuentran demasiado alto o bajo en su campo de vista. La mayor parte de su atención termina en áreas alrededor de su foco principal, que es aproximadamente a nivel de los ojos. Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos. Dada la tendencia de los usuarios a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de atención de la visión es aproximadamente de 10 grados), agrupar los elementos de la interfaz de usuario hasta el grado en que están relacionados conceptualmente puede usar comportamientos de encadenamiento de atención de elemento a elemento a medida que un usuario mueve la mirada a través de un área. Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.

![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*

## <a name="improving-targeting-behaviors&quot;></a>Mejora de los comportamientos de establecimiento de destino

Si la intención del usuario de dirigirse a algo se puede determinar o aproximar estrechamente, puede ser útil aceptar intentos de interacción casi desasistidos como si se hubieran dirigido correctamente. Estos son algunos métodos de éxito que se pueden incorporar en experiencias de realidad mixta:

### <a name=&quot;head-gaze-stabilization-gravity-wells&quot;></a>Estabilización de la mirada con la cabeza (&quot;pozos de gravedad")

Esto debe estar activado la mayoría del tiempo o todo el tiempo. Esta técnica elimina los movimientos naturales de cabeza y cuello que los usuarios pueden tener también debido a los comportamientos de mirar y hablar.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo más cercano

Estos algoritmos funcionan mejor en áreas con contenido interactivo disperso. Si hay una alta probabilidad de que pueda determinar con qué estaba intentando interactuar un usuario, puede complementar sus capacidades de destino suponiendo algún nivel de intención.

### <a name="backdating-and-postdating-actions"></a>Acciones de backdating y postdating

Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario se mueve a través de una serie de maniobras de destino y activación a gran velocidad, resulta útil asumir alguna intención. También es útil permitir que los pasos perdidos actúen en los destinos que el usuario tenía en el foco ligeramente antes o ligeramente después de la pulsación (50 ms antes o después de que fuera efectivo en las primeras pruebas).

### <a name="smoothing"></a>Suavizado

Este mecanismo es útil para la ruta de desplazamiento, lo que reduce la ligera vibración y los problemas debido a las características naturales del movimiento de la cabeza. Al suavizar los movimientos de trazado, suaviza el tamaño y la distancia de los movimientos en lugar de hacerlo a lo largo del tiempo.

### <a name="magnetism"></a>Magnetismo

Este mecanismo se puede pensar como una versión más general de los algoritmos de vínculo más cercanos: dibujar un cursor hacia un destino o simplemente aumentar los cuadros de acceso, ya sea visiblemente o no, a medida que los usuarios se aproximan a los destinos probables mediante el uso de cierto conocimiento del diseño interactivo para abordar mejor la intención del usuario. Esto puede ser eficaz para destinos pequeños.

### <a name="focus-stickiness"></a>Permanencia del foco

Al determinar qué elementos interactivos cercanos se va a dar, el foco a, la stickiness del foco proporciona un sesgo al elemento que está actualmente centrado. Esto ayuda a reducir los comportamientos erráticos de cambio de foco al flotar en un punto medio entre dos elementos con ruido natural.

## <a name="see-also"></a>Consulte también

* [Interacción basada en los ojos](eye-gaze-interaction.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)