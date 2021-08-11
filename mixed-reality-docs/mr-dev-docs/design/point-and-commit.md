---
title: Apuntar y confirmar con las manos
description: Conozca los aspectos básicos del modelo de entrada de apunte y confirmación para la compatibilidad con gestos en aplicaciones de realidad mixta.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, interaction, design, HoloLens, hands, far, point and commit , mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, hand rays, object manipulation, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 7cf3aa3dd77776fce00d45b0ec086bf1d2e8c06241fd4525276783c2abfd51d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194646"
---
# <a name="point-and-commit-with-hands"></a>Apuntar y confirmar con las manos

![Cursores](images/UX_Hero_HandRay.jpg)

"Apuntar y confirmar con las manos" es un modelo de entrada que permite a los usuarios seleccionar y manipular contenido 2D y 3D que esté fuera de su alcance. Esta técnica de interacción "lejana" es exclusiva de la realidad mixta, ya que los usuarios no interactúan de forma natural con el mundo real. Por ejemplo, en la película de superhéroes *X-Men*, el personaje [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) es capaz de manipular objetos lejanos a distancia con las manos. Esto no es algo que los seres humanos puedan hacer en el mundo real. Por ello, tanto en HoloLens (AR) como en Mixed Reality (MR), equipamos a los usuarios con este poder mágico para romper las restricciones físicas del mundo real. No solo es una experiencia holográfica divertida, sino que también hace que las interacciones de los usuarios sean más eficaces.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Modelo de entrada</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Apuntar y confirmar con las manos</td>
     <td>❌ No se admite</td>
     <td>✔️ Recomendado</td>
     <td>✔️ Recomendado</td>
</tr>
</table>


_"Apuntar y confirmar con las manos"_ es una de las nuevas características que usa el nuevo sistema articulado de seguimiento de la mano. Este modelo de entrada es también el modelo de entrada principal de los auriculares envolventes, gracias al uso de controladores de movimiento.

<br>

---

## <a name="hand-rays"></a>Rayos de las manos

En HoloLens 2, hemos creado un haz que sale desde el centro de la palma de la mano. Dicho rayo se trata como una extensión de la mano. Un cursor con forma de anillo se acopla al final del rayo para indicar la ubicación en que el rayo se cruza con un objeto de destino. El objeto en que se posa el cursor puede recibir comandos gestuales de la mano.

Este comando gestual básico se desencadena al usar los dedos pulgar e índice para realizar la acción de pulsar en el aire. Si se usa el haz de mano para apuntar y la acción de pulsar en el aire para confirmar, los usuarios pueden activar un botón o un hipervínculo. Si usan más gestos compuestos, los usuarios pueden navegar por el contenido web y manipular objetos 3D a distancia. El diseño visual del rayo de la mano también debe reaccionar a estos estados de apuntar y confirmar, como se describe y se muestra a continuación: 

:::row:::
    :::column:::
        ![haces de mano que apuntan](images/hand-rays-pointing.jpg)<br>
        **Estado de apuntar**<br>
        En el estado *señalar*, el rayo es una línea discontinua y el cursor tiene forma de anillo.
    :::column-end:::
    :::column:::
        ![haces de mano que confirman](images/hand-rays-commit.jpg)<br>
        **Estado de confirmación**<br>
        En el estado *confirmar*, el rayo se convierte en una línea sólida y el cursor se reduce a un punto.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a>Transición entre cerca y lejos

En lugar de usar gestos específicos como "señalar con el dedo índice" para dirigir el rayo, hemos diseñado el rayo para que salga del centro de la palma de la mano del usuario. De este modo, tenemos los cinco dedos disponibles para realizar más gestos de manipulación, como el contacto y la captura. Con este diseño, creamos solo un modelo mental, se usa el mismo conjunto de gestos de las manos para la interacción cercana y la lejana. Puedes usar el mismo gesto de arrastrar para manipular objetos que se encuentren a distinta distancia. La invocación de los haces es automática y se basa en la proximidad:

:::row:::
    :::column:::
        ![Manipulación cercana](images/transition-near-manipulation.jpg)<br>
        **Manipulación cercana**<br>
        Cuando a un objeto se llega estirando el brazo (aproximadamente 50 cm), los haces se desactivan automáticamente, lo que fomenta la interacción cercana.
    :::column-end:::
    :::column:::
        ![Manipulación lejana](images/transition-far-manipulation.jpg)<br>
        **Manipulación lejana**<br>
        Cuando el objeto está a más de 50 cm, los rayos se activan. La transición suave y sin problemas.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>Interacción con una tableta táctil 2D

Una tableta táctil 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web. El concepto de diseño para la interacción lejana con una tableta táctil 2D es usar los rayos de las manos para buscar el objetivo y pulsar en el aire para seleccionarlo. Después de buscar el destino con un rayo de la mano, los usuarios pueden pulsar en el aire para desencadenar un hipervínculo o un botón. Pueden usar una mano para "pulsar en el aire y arrastrar" a fin de desplazar el contenido de la tableta táctil hacia arriba y hacia abajo. El movimiento relativo de usar las dos manos para pulsar en el aire y arrastrar puede acercar y alejar el contenido de la tableta táctil.

Si se seleccionan como destino del rayo las esquinas y los bordes aparece la prestación de manipulación más cercana. Al "agarrar y arrastrar" las prestaciones de manipulación, los usuarios pueden realizar un escalado uniforme mediante las prestaciones de la esquina y redistribuir la tableta táctil mediante las prestaciones del borde. El procedimiento de agarrar y arrastrar la barra holográfica de la parte superior de la tableta táctil 2D permite a los usuarios mover toda la tableta táctil.

:::row:::
    :::column:::
       ![Hacer clic en la interacción con una tableta táctil 2D](images/2d-slate-interaction-click.jpg)<br>
       **Hacer clic**<br>
    :::column-end:::
    :::column:::
       ![Desplazar en la interacción con una tableta táctil 2D](images/2d-slate-interaction-scroll.jpg)<br>
        **Desplazar**<br>
    :::column-end:::
    :::column:::
       ![Zoom en la interacción con una tableta táctil 2D](images/2d-slate-interaction-zoom.jpg)<br>
       **Zoom**<br>
    :::column-end:::
:::row-end:::

<br>

**Para manipular la tableta táctil 2D**<br>

* los usuarios apuntan el rayo de la mano a las esquinas y bordes y aparece la prestación de manipulación más cercana. 
* Al aplicar un gesto de manipulación en la prestación, los usuarios pueden realizar un escalado uniforme mediante la prestación de la esquina y redistribuir la tableta táctil mediante la prestación del borde. 
* Al aplicar un gesto de manipulación a la barra holográfica de la parte superior de la tableta táctil 2D, los usuarios pueden mover toda la tableta táctil.<br>

<br>

---

## <a name="3d-object-manipulation"></a>Manipulación de objetos 3D

En la manipulación directa, hay dos formas de que los usuarios manipulen objetos 3D, la manipulación con prestaciones y la manipulación sin prestaciones. En el modelo para apuntar y confirmar, los usuarios pueden conseguir exactamente las mismas tareas a través de los haces de mano. No es necesario realizar ningún aprendizaje adicional.<br>

### <a name="affordance-based-manipulation"></a>Manipulación con prestaciones

Los usuarios usan los rayos de las manos para apuntar y mostrar el rectángulo de selección y las prestaciones de manipulación. Los usuarios pueden aplicar el gesto de manipulación al rectángulo de selección para mover todo el objeto, a las prestaciones del borde para girarlo y a las prestaciones de la esquina para escalarlo de forma uniforme. <br>

:::row:::
    :::column:::
       ![Movimiento lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-move.jpg)<br>
       **Mover**<br>
    :::column-end:::
    :::column:::
       ![Giro lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-rotate.jpg)<br>
        **Girar**<br>
    :::column-end:::
    :::column:::
       ![Escala lejana en la manipulación de objetos 3D](images/3d-object-manipulation-far-scale.jpg)<br>
       **Escalar**<br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a>Manipulación sin prestaciones

Los usuarios señalan con los rayos de las manos para mostrar el rectángulo de selección y, después, le aplican directamente los gestos de manipulación. Con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano. Con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.<br>

<br>

---

## <a name="instinctual-gestures"></a>Gestos instintivos

El concepto de gestos instintivos para señalar y confirmar es similar a la de la [manipulación directa con las manos](direct-manipulation.md). Los gestos que los usuarios realizan en un objeto 3D los guía el diseño de las prestaciones de interfaz de usuario. Por ejemplo, un punto de control pequeño podría motivar a los usuarios a acercar los dedos pulgar e índice, mientras que si un usuario quiere agarrar un objeto mayor, debe usar los cinco dedos.

:::row:::
    :::column:::
       ![gestos instintivos para objetos lejanos pequeños](images/instinctual-gestures-far-smallobject.jpg)<br>
       **Objeto pequeño**<br>
    :::column-end:::
    :::column:::
       ![gestos instintivos para objetos lejanos medianos](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **Objeto mediano**<br>
    :::column-end:::
    :::column:::
       ![gestos instintivos para objetos lejanos grandes](images/instinctual-gestures-far-largeobject.jpg)<br>
       **Objeto grande**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Diseño simétrico entre las manos y 6 controladores DoF 

El concepto de señalar y confirmar de la interacción lejana se creó y definió para el portal de realidad mixta (PRM). En este escenario, el usuario lleva un casco envolvente e interactúa con objetos 3D a través de los controladores de movimiento. Los controladores de movimiento lanzar rayos para señalar y manipular objetos lejanos. Hay botones en los controladores para confirmar más acciones diferentes. Aprovecharemos el modelo de interacción de rayos y los acoplaremos a ambas manos. Con este diseño simétrico, los usuarios que están familiarizados con MRP no necesitan aprender otro modelo de interacción para señalar y manipular a distancia cuando usan HoloLens 2, y viceversa.    

:::row:::
    :::column:::
        ![diseño simétrico para haces con controladores](images/symmetric-design-for-rays-controllers.jpg)<br>
        **Haces de controlador**<br>
    :::column-end:::
    :::column:::
        ![diseño simétrico para haces con manos](images/symmetric-design-for-rays-hands.jpg)<br>
        **Haces de mano**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a>Haz de mano en MRTK (Mixed Reality Toolkit) para Unity

De forma predeterminada, MRTK proporciona un haz de mano prefabricado ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) que tiene el mismo estado visual que el haz de mano del sistema del shell. Se asigna en el perfil de entrada de MRTK, en Punteros. En un casco envolvente, se usan los mismos haces para los controladores de movimiento.

* [MRTK: perfil de puntero](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK: sistema de entrada](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK: punteros](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Consulte también

* [Manipulación directa con las manos](direct-manipulation.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Interacciones instintivas](interaction-fundamentals.md)