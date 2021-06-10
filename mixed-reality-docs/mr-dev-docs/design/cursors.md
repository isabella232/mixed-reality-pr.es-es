---
title: Cursores
description: Un cursor, o indicador del vector de destino, proporciona comentarios continuos para que el usuario comprenda lo que HoloLens entiende sobre sus intenciones.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1.ª generación), HoloLens 2, Mixed Reality, cursores, destino, mirada, gestos, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, rayos, entrada
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600384"
---
# <a name="cursors"></a>Cursores

![Cursores](images/UX_Hero_Cursor.jpg)

Un cursor proporciona comentarios continuos en función de dónde cree el casco que un usuario se centra actualmente en un momento determinado. Los comentarios del cursor incluyen qué área, holograma o punto del entorno virtual responde a la entrada. Aunque el cursor es una representación digital de dónde entiende el dispositivo la atención del usuario, eso no es lo mismo que determinar las intenciones del usuario. Los comentarios del cursor también permiten a los usuarios saber qué respuestas del sistema deben esperar. Puede usar los comentarios para comunicar su intención al dispositivo, lo que aumenta la confianza del usuario.

Hay tres tipos de cursores: **dedo, rayo** y mirada **con la cabeza.** Estos cursores de punto funcionan con diferentes modalidades de entrada en HoloLens, HoloLens 2 y cascos envolventes. A continuación se muestran instrucciones sobre qué tipo de cursor usar para cada tipo de casco y modelo de interacción. En Mixed Reality Toolkit (MRTK), hemos creado módulos de cursores de arrastrar y colocar para ayudarle a crear la experiencia de apuntamiento correcta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Cursor de dedo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Cursor de rayo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursor de mirada con la cabeza</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursor de dedo

El cursor de dedo solo está disponible en[](direct-manipulation.md)el HoloLens 2 para mejorar el modo de interacción "manipulación directa con las manos". Hemos adjuntado anillos a las puntas de ambos dedos de índice para comprender mejor dónde apunta el dedo. El tamaño del anillo se basa en la proximidad del dedo a la superficie de la interfaz de usuario, que se reduce a un punto pequeño cuando el dedo toca la interfaz de usuario. Cuanto más cerca se acerque el dedo, más pequeño es el anillo. <br>

![cursor de dedo](images/finger-cursor.png)<br>
**Estados de comentarios visuales del cursor** de dedo 1: el anillo se reduce a un punto. 2: el anillo se alinea con la superficie. 3: el anillo es vector de dedo a dedo. 4: Sin anillo.

## <a name="ray-cursor"></a>Cursor de rayo

Los cursores de rayos se asocian al final de los rayos de puntero lejano para permitir la manipulación de objetos que están fuera del alcance de las manos. En los cascos envolventes, los rayos se lanzan desde los controladores de movimiento y terminan en cursores de punto. En HoloLens 2, aplicamos el modelo mental de estos rayos de controlador de movimiento y los rayos de mano diseñados que se originan a partir de los dedos y terminan en cursores en forma de anillo que son coherentes con los cursores de dedo usados en la manipulación directa. <br>
:::row:::
    :::column:::
        ![Controlador de cursor ray](images/ray-cursor-controller.png)<br>
        **Cursores de rayos de controladores de movimiento**<br>
    :::column-end:::
    :::column:::
        ![Mano del cursor ray](images/ray-cursor-hand.png)<br>
        **Cursores de rayo de las manos**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursor de mirada con la cabeza

El cursor de mirada con la cabeza es un punto que se adjunta al final de un vector de mirada con la cabeza invisible que usa la posición y la rotación de la cabeza hasta el punto. Para ejecutar acciones, este cursor que apunta se empareja con varias entradas de confirmación, como pulsación en el aire, comandos de voz, permanencia y presionar el botón. En HoloLens 2, la mirada con la cabeza se empareja mejor con cualquier entrada de confirmación que no sea pulsación en el aire, ya que habrá un conflicto de interacción entre el toque de aire y los rayos de mano lejanos. <br>
:::row:::
    :::column:::
        ![Mano del cursor de mirada con la cabeza](images/head-gaze-cursor-hand.png)<br>
        **Cursor de mirada con la cabeza con gesto de mano**<br>
    :::column-end:::
    :::column:::
        ![Voz del cursor de mirada con la cabeza](images/head-gaze-cursor-voice.png)<br>
        **Cursor de mirada con la cabeza con el comando de voz**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Recomendaciones de personalización de cursores

Si desea personalizar los comportamientos y las apariencias de los comentarios del cursor, estas son algunas recomendaciones de diseño:

### <a name="cursor-scale"></a>Escala de cursores

* El cursor no debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar fácilmente con el contenido y verlo.
* En función de la experiencia que cree, el escalado del cursor a medida que el usuario examina también es una consideración importante. Por ejemplo, a medida que el usuario mira más lejos en su experiencia, el cursor no debe ser demasiado pequeño, de modo que se pierda.
* Al escalar el cursor, considere la posibilidad de aplicarle una animación suave a medida que se escala para darle una sensación orgánica.
* Evite la obstrución de contenido. Los hologramas son lo que hace que la experiencia sea fácil de recordar y el cursor no debería quitarse de ellos.

### <a name="directionless-cursor-shape"></a>Forma de cursor sin dirección

* Aunque no hay ninguna forma de cursor derecha, se recomienda usar una forma sin dirección como un torus. Un cursor que apunta en alguna dirección (por ejemplo, un cursor de flecha tradicional) podría confundir al usuario para que siempre tenga ese aspecto.
* Una excepción a esto es cuando se usa el cursor para comunicar la instrucción de interacción al usuario. Por ejemplo, al escalar hologramas en el sistema operativo Mixed Reality, el cursor incluye temporalmente flechas que indica al usuario cómo mover la mano para escalar el holograma.

### <a name="look-and-feel"></a>Buscar y sentir

* Un cursor con forma de anillo o torus funciona para muchas aplicaciones.
* Elija un color y una forma que represente mejor la experiencia que está creando.
* Los cursores son especialmente propensos a la [separación de colores.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* Un cursor pequeño con opacidad equilibrada lo mantiene informativo sin dominar la jerarquía visual.
* Tenga en cuenta el uso de sombras o resaltados detrás del cursor, ya que podrían impedir el contenido y distraerse de la tarea en la mano.
* Los cursores deben alinearse con las superficies de la aplicación y desenlace. Los usuarios tendrán la sensación de que el sistema puede ver dónde están buscando, pero también de que el sistema es consciente de su entorno. Por ejemplo, el cursor del sistema operativo Mixed Reality se alinea con las superficies del mundo del usuario, lo que crea una sensación de conocimiento del mundo incluso cuando el usuario no mira directamente un holograma.
* El bloqueo magnético del cursor en un elemento interactivo cuando está cerca del usuario puede ayudar a mejorar la confianza de que el usuario interactuará con ese elemento cuando use una acción de selección.

### <a name="visual-cues"></a>Indicaciones visuales

* Si la experiencia se centra en un solo holograma, el cursor debe alinear y alejarse solo de ese holograma y cambiar de forma al mirar fuera de ese holograma. Esto puede transmitir al usuario que el holograma es manejable y que puede interactuar con él.
* Si la aplicación usa la asignación espacial, el cursor podría alinear y alinear todas las superficies que ve. Esto proporciona comentarios a los usuarios para que HoloLens y la aplicación puedan ver su espacio. Esto refuerza el hecho de que los hologramas son reales y en nuestro mundo, y ayuda a reducir la brecha entre real y virtual.
* Tenga una idea de lo que debe hacer el cursor cuando no haya hologramas ni superficies a la vista. Colocarlo a una distancia predeterminada delante del usuario es una opción.

### <a name="possible-actions"></a>Acciones posibles

* El cursor se puede representar mediante iconos diferentes para transmitir las posibles acciones que puede realizar un holograma, como el escalado o la rotación.
* Agregue solo información adicional sobre el cursor si significa algo para el usuario. De lo contrario, es posible que los usuarios no observen los cambios de estado o se confundan con el cursor.

### <a name="input-state"></a>Estado de entrada

* Podríamos usar el cursor para mostrar el estado de entrada o la intención del usuario. Por ejemplo, podríamos mostrar un icono que le dice al usuario que el sistema ve su estado de mano y que la aplicación sabe que está listo para tomar medidas.
* También podríamos usar el cursor para mostrar a los usuarios que el sistema ha oído los comandos de voz a través de un cambio momentánario de color.

* Los siguientes estados de cursor se pueden implementar de maneras diferentes. Puede implementar estos estados diferentes mediante el modelado del cursor como una máquina de estados. Por ejemplo:
    * El estado de inactividad es donde se muestra el cursor predeterminado.
    * El estado listo es cuando se ha detectado la mano del usuario en la posición lista.
    * El estado de interacción es cuando el usuario está realizando una interacción determinada.
    * El estado de las acciones posibles o el estado del mouse es cuando se transmiten las posibles acciones que se pueden realizar en un holograma.

También puede implementar estos estados de una manera capaz de mostrar distintos recursos de arte cuando detecte estados diferentes.

<br>

---

## <a name="going-cursor-free"></a>Ir "sin cursor"

Se recomienda diseñar sin un cursor cuando la sensación de inmersiones es un componente clave de una experiencia y cuando las interacciones de apuntar (a través de la mirada y el gesto) no requieren una gran precisión. El sistema todavía necesita cumplir los requisitos normales de un cursor: proporcionar a los usuarios comentarios continuos sobre la comprensión del sistema de su apuntar y ayudarles a comunicar sus intenciones al sistema. Esto puede ser factible a través de otros cambios de estado apreciables.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursor en MRTK (Mixed Reality Toolkit) para Unity

De forma predeterminada, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona un cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tiene el mismo estado visual que el cursor del sistema del shell. Se asigna en el perfil de entrada de MRTK, en Punteros. Puede reemplazar o personalizar este cursor por su experiencia. Para la experiencia con la entrada de seguimiento de los ojos, MRTK también proporciona EyeGazeCursor, que tiene un objeto visual sutil para minimizar la distracción.

* [MRTK: perfil de puntero](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK: sistema de entrada](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK: punteros](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Consulte también

* [Gestos](gaze-and-commit.md#composite-gestures)
* [Mirada-cabeza y confirmación](gaze-and-commit.md)