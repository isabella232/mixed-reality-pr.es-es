---
title: Menú Mano
description: Los menús de mano permiten a los usuarios abrir rápidamente la interfaz de usuario adjunta a mano para las funciones usadas con frecuencia.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: hand, menu, button, quick access, layout, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600334"
---
# <a name="hand-menu"></a>Menú Mano

![Ubicación de la mano de Ulnar](images/UX_Hero_HandMenu.jpg)

El menú de mano es uno de los patrones de experiencia de usuario más únicos HoloLens 2. Permite abrir rápidamente la interfaz de usuario adjunta a mano. Puesto que es accesible en cualquier momento y se puede mostrar y ocultar fácilmente, es ideal para acciones rápidas.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Encontrará nuestros procedimientos recomendados para trabajar con menús de mano en la lista siguiente. También puede encontrar una escena de ejemplo que muestra el menú de mano [en MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).

<br>

---

## <a name="best-practices"></a>Procedimientos recomendados

**Mantener pequeño el número de botones** 

Debido a la distancia cercana entre un menú con la mano bloqueada y los ojos, y la tendencia de los usuarios a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de atención de la visión es aproximadamente de 10 grados), se recomienda mantener el número de botones pequeño. En función de nuestra exploración, una columna con tres botones funciona bien manteniendo todo el contenido dentro del campo de vista (FOV) incluso cuando un usuario mueve las manos al centro de la FOV. 

**Uso del menú de mano para una acción rápida** 

Elevar un arm y mantener la posición podría provocar fácilmente la agotamiento del arm. Use un método bloqueado a mano para el menú que requiera una interacción corta. Si el menú es complejo y requiere tiempos de interacción prolongados, considere la posibilidad de usar bloqueados por el mundo o bloqueados por el cuerpo en su lugar. 

**Ángulo de botón o panel**

Los menús deben avanzar hacia el cuello opuesto y el centro de la cabeza: esto permite que un movimiento natural de la mano interactúe con el menú con la mano opuesta y evita cualquier posición de mano difícil o poco cómoda al tocar botones. 

**Considere la posibilidad de admitir una operación con una mano o con manos libres**

No suponga que las dos manos del usuario siempre están disponibles. Tenga en cuenta una amplia gama de contextos cuando una o ambas manos no estén disponibles y asegúrese de que el diseño tenga en cuenta esas situaciones. Para admitir un menú con una mano, puede intentar cambiar la ubicación del menú de bloqueado a bloqueado al mundo cuando la mano se voltea (se queda abajo). Para escenarios con manos libres, considere la posibilidad de usar un comando de voz para invocar el menú de mano.

**Evite agregar botones cerca de la ruedas (botón inicio del sistema)**

Si los botones del menú de la mano se colocan demasiado cerca del botón inicio, puede desencadenarse accidentalmente al interactuar con el menú de mano.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Menú de mano con controles de interfaz de usuario grandes y complejos

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
Se recomienda limitar el número de botones o controles de interfaz de usuario en los menús adjuntos a mano. Esto se debe a que la interacción extendida con un gran número de elementos de la interfaz de usuario puede provocar la agotamiento del arm. Si su experiencia requiere un menú grande, proporcione una manera fácil para que el usuario bloquee el menú. Una técnica que se recomienda es bloquear el menú world-lock y, después, cuando la mano se desasocie o se desasocie del usuario. Una segunda técnica consiste en permitir al usuario tomar directamente el menú con la otra mano. Cuando el usuario suelta el menú, el menú debería bloquearse. De este modo, un usuario puede interactuar con varios elementos de la interfaz de usuario de forma cómoda y segura durante un largo período de tiempo. 

Cuando el menú esté bloqueado por el mundo, asegúrese de proporcionar una manera de mover el menú y cierre el menú cuando ya no sea necesario. Para que el menú sea móvil, proporcione identificadores en los lados o en la parte superior del menú. Agregue un botón Cerrar para permitir que se cierre el menú. Permita que el menú se vuelva a asociar a la mano cuando el usuario se enfrenta al usuario. También se recomienda exigir que los usuarios mire a su mano para evitar activaciones falsas (consulte a continuación).

**Menú grande que muestra un problema de facilidad de uso**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Menú world-locked en la lista desplegable**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Extracción manual & para bloquear el menú**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>Cómo evitar la activación falsa

Si solo usas la forma de un evento para desencadenar el menú de la mano, es posible que aparezca accidentalmente cuando no lo necesites (falso positivo), ya que las personas mueven las manos de forma intencionada (para la comunicación y la manipulación de objetos) y sin querer. Para reducir las activaciones falsas, agregue un paso adicional además del evento de pie arriba para invocar el menú de la mano (por ejemplo, los dedos completamente abiertos o el usuario que mira intencionadamente a su mano).

**Requerir una mano plana**

Al requerir una mano abierta sin formato, puede evitar la activación falsa que podría producirse cuando el usuario manipula objetos o gestos mientras se comunica dentro de un entorno. 

**Requerir mirada**

Al exigir al usuario que mire con la mano (ya sea con la mirada con los ojos o la mirada con la cabeza), evita las falsas activaciones porque el usuario tiene que dirigir su atención a la mano como un paso de activación secundario (con un umbral de distancia ajustable que se usa para permitir la comodidad del usuario).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Prácticas recomendadas de selección de ubicación del menú de mano

En la anatomía humana, la estructura ulnar es una estructura que se ejecuta cerca del ulna. El ulna es un fragmento largo que se encuentra en el antebrazo que se extiende desde el dedo más pequeño hasta el más pequeño.

A continuación se muestran dos ubicaciones recomendadas en función de nuestras exploraciones:

:::row:::
    :::column:::
        ![Ubicación de la mano lateral de Ulnar dentro de la mano](images/UlnarSideHandMenu.gif)<br>
        **A. Ulnar dentro de la mano**<br>
        Esta posición es confiable porque las manos no se superponen entre sí. Esto es fundamental para la detección y el seguimiento precisos de las manos.
    :::column-end:::
    :::column:::
        ![Ubicación de la mano lateral de Ulnar por encima de la mano](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar sobre la mano**<br>
        Esta ubicación es cómoda para los usuarios porque no necesitan subir demasiado el mano para interactuar con el menú de la mano. Se recomienda colocar menús **13 cm** por encima de la mano y alinear los botones dentro de la mano de ulnar. [Más información sobre el tamaño óptimo del botón](interactable-object.md)<br>
        <br>
        Por motivos técnicos, se recomienda esta ubicación con una implementación necesaria: el desarrollador tendrá que inmovilizar el menú una vez que la mano opuesta del usuario se acerca a interactuar con él. Esto evitará la vibración de las manos superpuestas y también permite una selección de destino más rápida de los botones.<br>
        <br>
        HoloLens 2 cámaras identifican las manos con precisión cuando están separadas entre sí. Las manos superpuestas pueden hacer que los menús de las manos se muevan de la ubicación del anclaje.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>Posiciones de menú que no se recomiendan

Hemos realizado una investigación del usuario con diferentes diseños y ubicaciones de menús, no se recomiendan las siguientes ubicaciones de menú; busque las desventajas de cada estudio a continuación:

:::row:::
    :::column:::
        ![Arm superior](images/AboveArm.gif)<br>
        **Encima del arm**<br>
        1 - Difícil de mantener un buen seguimiento de las manos<br>
        2 - Provoca la agotamiento del usuario debido a una posición no natural
    :::column-end:::
    :::column:::
        ![Dedos superiores](images/AboveFingers.gif)<br>
        **Dedos superiores**<br>
        1 - Agotamiento de la mano debido a la mano durante mucho tiempo<br>
        2 - Problemas de seguimiento de las manos en el índice y los dedos centrales
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Manola central anterior](images/handCenter.gif)<br>
        **Manola de centro superior**<br>
        1 - Problemas de seguimiento de las manos debido a la superposición de las manos<br>
        2 - Agotamiento de las manos debido a la mano durante mucho tiempo para interactuar con los menús
    :::column-end:::
    :::column:::
        ![Dedo superior del ](images/TopFingerTip.gif) **dedo**<br>
        1 - Problemas de seguimiento de manos<br>
        2 - Agotamiento de la mano al mantener la mano por encima de la posición normal<br>
        3 - Problemas al presionar botones con otros dedos por accidente debido a un espacio limitado entre los dedos
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Parte posterior del arm](images/BackOfTheArm.gif)<br>
        **Parte posterior del arm**<br>
        1 - Puede desencadenar el botón inicio por accidente<br>
        2 - No es una posición natural o cómoda
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menú de mano en MRTK (Mixed Reality Toolkit) para Unity

**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts y escenas de ejemplo para el menú de mano. El script del solucionador HandConstraintPalmUp permite adjuntar objetos a las manos con varias opciones configurables. Los ejemplos de menú de mano de MRTK incluyen opciones útiles, como el requisito de mano plana y mirada para evitar la activación falsa.

* [Documentación del menú de mano](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [Escena de ejemplo de menú de mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

Puede probar ejemplos de menú de mano en HoloLens 2 con la aplicación Centro de ejemplos de MRTK.

* [Escena del menú de mano en el centro de ejemplos de MRTK](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a>Vea también

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