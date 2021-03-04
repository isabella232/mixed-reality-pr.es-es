---
title: Cursores
description: Un cursor, o indicador del vector de destino, proporciona comentarios continuos para que el usuario comprenda lo que HoloLens entiende sobre sus intenciones.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª generación), HoloLens 2, realidad mixta, cursores, destinatarios, mirados, gestos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, rayos, entrada
ms.openlocfilehash: 0b35c832e6d13ff10d14686909754de60b83fa23
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759421"
---
# <a name="cursors"></a>Cursores

![Cursores](images/UX_Hero_Cursor.jpg)

Un cursor proporciona comentarios continuos basados en el lugar en que el casco cree que el foco actual de los usuarios se encuentra en un momento dado. Los comentarios del cursor incluyen el área, el holograma o el punto del entorno virtual que responde a la entrada. Aunque el cursor es una representación digital del lugar en el que el dispositivo entiende la atención del usuario, no es lo mismo que determinar las intenciones del usuario. Los comentarios del cursor también permiten a los usuarios saber qué respuestas del sistema se esperan. Puede usar los comentarios para comunicar su intención al dispositivo, lo que aumenta la confianza del usuario.

Hay 3 tipos de cursores: **Finger, Ray** y **Head-mirate**. Estos cursores de señalización funcionan con diferentes modalidades de entrada en HoloLens, HoloLens 2 y auriculares envolvente. A continuación se ofrecen instrucciones sobre qué tipo de cursor se debe utilizar para cada tipo de auriculares y modelo de interacción. En el kit de herramientas de realidad mixta (MRTK), hemos creado módulos de cursores de arrastrar y colocar para ayudarle a crear la experiencia adecuada.

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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
        <td>Cursor de miras hacia abajo</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursor de dedo

El cursor de dedo solo está disponible en HoloLens 2 para mejorar el modo de interacción "[manipulación directa con manos](direct-manipulation.md)". Hemos adjuntado anillos a las sugerencias de ambos dedos de índice para comprender mejor Dónde está señalando el dedo. El tamaño del anillo se basa en la proximidad del dedo a la superficie de la interfaz de usuario, que se reduce a un punto pequeño cuando el dedo toca la interfaz de usuario. Cuanto más se acerque el dedo, menor será el anillo. <br>

![cursor de dedo](images/finger-cursor.png)<br>
**Estados de comentarios visuales del cursor de dedo** 1: el anillo se reduce a un punto. 2: el anillo se alinea con la superficie. 3: el anillo es perpendicular al vector de dedo. 4: sin anillo.

## <a name="ray-cursor"></a>Cursor de rayo

Los cursores de rayo se adjuntan al final de los rayos que apuntan mucho para permitir la manipulación de objetos que no están disponibles. En los auriculares envolventes, los rayos salen de los controladores de movimiento y finalizan los cursores de punto. En HoloLens 2, se aplica el modelo mental de estos rayos de controlador de movimiento y se diseñan rayos de mano que se originan a partir de las palmeras y se acaban en cursores en forma de anillo que son coherentes con los cursores de dedo utilizados en la manipulación directa. <br>
:::row:::
    :::column:::
        ![Controlador de cursor de rayo](images/ray-cursor-controller.png)<br>
        **Cursores de rayo de controladores de movimiento**<br>
    :::column-end:::
    :::column:::
        ![Mano de cursor de rayo](images/ray-cursor-hand.png)<br>
        **Cursores de rayo de manos**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursor de miras hacia abajo

El cursor de mira hacia abajo es un punto que se adjunta al final de un vector de miras hacia arriba invisible que usa la posición y la rotación del encabezado al punto. Para ejecutar acciones, este cursor señalador se empareja con varias entradas de confirmación, como la pulsación de aire, los comandos de voz, la permanencia y la pulsación de botones. En HoloLens 2, el encabezado de la mirada es mejor con cualquier entrada de confirmación que no se pulse en el aire, ya que habrá un conflicto de interacción entre la derivación del aire y los rayos de mano. <br>
:::row:::
    :::column:::
        ![Mano de cursor de mira](images/head-gaze-cursor-hand.png)<br>
        **Cursor de mira hacia abajo con el gesto de mano**<br>
    :::column-end:::
    :::column:::
        ![Voz de cursor de mirada](images/head-gaze-cursor-voice.png)<br>
        **Cursor de mira hacia abajo con el comando de voz**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Recomendaciones de personalización de cursores

Si desea personalizar los comportamientos y los aspectos de los comentarios del cursor, estas son algunas recomendaciones de diseño:

### <a name="cursor-scale"></a>Escala del cursor

* El cursor no debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar fácilmente con el contenido y verlo.
* Dependiendo de la experiencia que cree, el escalado del cursor a medida que el usuario busca también es una consideración importante. Por ejemplo, a medida que el usuario mira mejor su experiencia, el cursor no debe ser demasiado pequeño, por lo que se pierde.
* Al escalar el cursor, considere la posibilidad de aplicarle una animación de software a medida que se escale para darle una sensación orgánica.
* Evite obstruir el contenido. Los hologramas son lo que hacen que la experiencia sea memorable y el cursor no debe apartarse de ellas.

### <a name="directionless-cursor-shape"></a>Forma cursor no direccional

* Aunque no hay una forma de cursor derecha, se recomienda usar una forma sin dirección como un toro. Un cursor que apunta en alguna dirección (por ejemplo, un cursor de flecha tradicional) puede confundir al usuario para que siempre mire ese modo.
* Una excepción a esto es cuando se usa el cursor para comunicar la instrucción de interacción al usuario. Por ejemplo, al escalar los hologramas en el sistema operativo de realidad mixta, el cursor incluye de forma temporal flechas que indican al usuario Cómo trasladar la mano para escalar el holograma.

### <a name="look-and-feel"></a>Apariencia y funcionamiento

* Un anillo o cursor con forma de aro funciona para muchas aplicaciones.
* Elija un color y una forma que mejor represente la experiencia que está creando.
* Los cursores son especialmente propensos a la [separación de colores](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).
* Un cursor pequeño con opacidad equilibrada mantiene informativa sin dominar la jerarquía visual.
* Tenga en Cognizant el uso de sombras o resaltados detrás del cursor, ya que podrían obstruir el contenido y distraerse de la tarea a mano.
* Los cursores deben alinearse con las superficies de la aplicación y Hug. Los usuarios tendrán la sensación de que el sistema puede ver dónde están buscando, pero también que el sistema es consciente de su entorno. Por ejemplo, el cursor en el sistema operativo de realidad mixta se alinea con las superficies del mundo del usuario, lo que crea un sentimiento de sensibilización del mundo incluso cuando el usuario no está mirando directamente a un holograma.
* El bloqueo magnético del cursor en un elemento interactivo cuando está cerca del usuario puede ayudar a mejorar la confianza de que el usuario interactuará con ese elemento cuando use una acción de selección.

### <a name="visual-cues"></a>Indicaciones visuales

* Si su experiencia se centra en un solo holograma, el cursor debe alinearse y Hug solo ese holograma y cambiar de forma cuando mira el holograma. Esto puede transmitir al usuario que el holograma es accionable y puede interactuar con él.
* Si la aplicación usa la asignación espacial, el cursor podría alinear y Hug cada superficie que ve. Esto proporciona comentarios a los usuarios de que HoloLens y su aplicación pueden ver su espacio. Esto refuerza el hecho de que los hologramas son reales y en nuestro mundo y ayudan a salvar la brecha entre real y virtual.
* Tenga una idea de lo que debe hacer el cursor cuando no haya ningún holograma o superficie en la vista. Colocarlo a una distancia predeterminada delante del usuario es una opción.

### <a name="possible-actions"></a>Acciones posibles

* El cursor se puede representar mediante iconos diferentes para transmitir posibles acciones que puede realizar un holograma, como el escalado o la rotación.
* Agregue solo información adicional sobre el cursor si significa algo al usuario. De lo contrario, es posible que los usuarios no perciban los cambios de estado u obtengan una confusión con el cursor.

### <a name="input-state"></a>Estado de entrada

* Podríamos usar el cursor para mostrar el estado de entrada o la intención del usuario. Por ejemplo, podríamos mostrar un icono que indica al usuario que el sistema ve su estado de mano y que la aplicación sabe que está listo para tomar medidas.
* También podríamos usar el cursor para mostrar a los usuarios que el sistema ha escuchado comandos de voz a través de un cambio de color momentáneo

* Los siguientes Estados de cursor se pueden implementar de maneras diferentes. Puede implementar estos Estados diferentes modelando el cursor como una máquina de Estados. Por ejemplo:
    * Estado de inactividad es donde se muestra el cursor predeterminado.
    * El estado listo es cuando ha detectado la mano del usuario en la posición listo.
    * El estado de interacción es cuando el usuario realiza una interacción determinada.
    * El estado de las acciones posibles o el estado de desplazamiento es cuando se transmiten las posibles acciones que se pueden realizar en un holograma.

También puede implementar estos Estados de forma que pueda mostrar los distintos activos gráficos cuando detecte Estados diferentes.

<br>

---

## <a name="going-cursor-free"></a>"Sin cursor"

Se recomienda diseñar sin un cursor cuando el sentido de la inmersión es un componente clave de una experiencia y cuando las interacciones que señalan (a través de la mirada y el gesto) no requieren una gran precisión. El sistema aún debe cumplir los requisitos normales de un cursor: proporcionar a los usuarios comentarios continuos sobre el conocimiento del sistema y ayudarles a comunicar sus intenciones al sistema. Esto puede ser factible a través de otros cambios de estado perceptibles.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursor en MRTK (kit de herramientas de realidad mixta) para Unity

De forma predeterminada, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona un cursor recurso prefabricado ([DefaultCursor. recurso prefabricado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tiene el mismo estado visual que el cursor del sistema del shell. Se asigna en el perfil de entrada de MRTK, en Punteros. Puede reemplazar o personalizar este cursor para su experiencia. Para la experiencia con la entrada de seguimiento ocular, MRTK también proporciona EyeGazeCursor, que tiene un efecto visual sutil para minimizar la distracción.

* [MRTK: perfil de puntero](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/mixed-reality-configuration-guide.md#pointer-configuration)
* [MRTK: sistema de entrada](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [MRTK: punteros](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a>Consulte también

* [Gestos](gaze-and-commit.md#composite-gestures)
* [Mirada-cabeza y confirmación](gaze-and-commit.md)