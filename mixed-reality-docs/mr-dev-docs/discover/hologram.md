---
title: ¿Qué es un holograma?
description: HoloLens permite ver e interactuar con hologramas tridimensionales, objetos hechos de luz y sonido que aparecen en el mundo que le rodea.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologramas, diseño, interacción, cascos de realidad mixta, cascos de realidad mixta de Windows, ¿qué es la realidad aumentada?
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634336"
---
# <a name="what-is-a-hologram"></a>¿Qué es un holograma?

HoloLens permite ver **hologramas,** que son objetos de luz y sonido que aparecen en el mundo que le rodea, como objetos reales. Hologramas responder a los comandos [de](../design/gaze-and-commit.md)mirada, [gestos](../design/gaze-and-commit.md#composite-gestures) [y voz](../design/voice-input.md). Incluso pueden interactuar con [superficies del mundo real](../design/spatial-mapping.md) a su alrededor. Hologramas son objetos digitales que forman parte de su mundo.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

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
        <td>Hologramas</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>Un holograma está hecho de luz y sonido

### <a name="light"></a>Claro

Los hologramas que HoloLens [representan](../develop/platform-capabilities-and-apis/rendering.md) aparecen en el marco holográfico directamente delante de los ojos de los usuarios. Hologramas agregar luz a su mundo, lo que significa que verá tanto la luz de la pantalla como la luz del mundo circundante. Puesto HoloLens una pantalla de suma que agrega luz, el color negro se representará de forma transparente. 

Hologramas pueden tener apariencias y comportamientos muy diferentes. Algunas son realistas y sólidas, y otras son resaltes y etéreas. Puede usar hologramas para resaltar las características de su entorno o usarlas como elementos en la interfaz de usuario de la aplicación.

![Manos que manipulan un holograma](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Sonido

Hologramas también puede generar [sonidos](../design/spatial-sound.md), que parecen procedentes de un lugar específico de su entorno. En HoloLens, el sonido procede de dos altavoces que se encuentran directamente encima de los oídos. Igual que las pantallas holográficas, los altavoces son aditivos, lo que introduce sonidos nuevos sin bloquear los sonidos del entorno.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Se puede colocar un holograma en el mundo o etiquetar junto con usted

Si tiene una ubicación fija para un holograma, [puede](../design/coordinate-systems.md) colocarlo con precisión en ese punto del mundo. A medida que se desenlace, el holograma aparece insaltez en función del mundo que le rodea, al igual que un objeto físico. Si usa un delimitador [espacial](../design/coordinate-systems.md#spatial-anchors) para anclar el objeto, el sistema incluso puede recordar dónde lo dejó cuando vuelva más tarde.

![Dos hombres que usan el diseño de Microsoft Dynamics 365 en un espacio comercial](images/HLS19_retailLayoutHologram_001-940px.jpg)

En su lugar, algunos hologramas siguen al usuario. Se posicionan en función del usuario. Puede elegir llevar un holograma con usted y colocarlo en la pared una vez que llegue a otra habitación.

**procedimientos recomendados**

* Algunos escenarios exigen que los hologramas permanezcan fácilmente reconocibles o visibles a lo largo de la experiencia. Hay dos enfoques de alto nivel para este tipo de posicionamiento. Vamos a llamarlos **display-locked** y **body-locked**.
   * **El contenido bloqueado para** mostrar está bloqueado en el dispositivo de visualización. Este tipo de contenido es complicado por varias razones, incluida una sensación poco natural de "clingyness" que hace que muchos usuarios se sientan frustrados y quieran "apagarlo". En general, los diseñadores han descubierto que es mejor evitar el contenido de bloqueo de pantalla.
   * **El contenido bloqueado en** el cuerpo puede ser mucho más forzante. El bloqueo del cuerpo es cuando se tete un holograma al cuerpo del usuario o al vector de mirada en el espacio 3D. Muchas experiencias han adoptado un comportamiento de bloqueo del cuerpo en el que el holograma sigue la mirada del usuario, lo que permite al usuario girar su cuerpo y desplazarse por el espacio sin perder el holograma. La incorporación de un retraso ayuda a que los movimientos del holograma se sientan más naturales. Por ejemplo, alguna interfaz de usuario principal del sistema operativo Windows Holographic usa una variación en el bloqueo de cuerpo que sigue la mirada del usuario con un retraso suave y elástico mientras el usuario se vuelve la cabeza.
* Coloque el holograma a una distancia de visualización cómoda, normalmente a unos 1-2 metros de distancia de la cabeza.
* Permita que los elementos se desenlacen si deben estar continuamente en el marco holográfico, o considere la posibilidad de mover el contenido a un lado de la pantalla cuando el usuario cambie su punto de vista. Para obtener más información, consulte la técnica [de](../design/billboarding-and-tag-along.md) etiquetado y etiquetado.

**Colocar hologramas en la zona óptima: entre 1,25 m y 5 m**

Dos metros es la distancia de visualización más óptima. La experiencia comenzará a degradarse a medida que se acerque a más de 1 metro. A distancias inferiores a 1 metro, es más probable que los hologramas que se mueven con regularidad en profundidad sean problemáticos que los hologramas estacionados. Considere la posibilidad de recortar o desvanejar correctamente el contenido cuando se acerca demasiado, por lo que no se convierte al usuario en una experiencia de visualización agradable.

![Distancia óptima para colocar hologramas del usuario.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un holograma interactúa con usted y con su mundo

Hologramas no solo se trata de la luz y el sonido; también son una parte activa de su mundo. Mire un holograma y un gesto con la mano, y un holograma puede empezar a seguirle. Dé un comando de voz y el holograma puede responder.

![Grupo de trabajadores de la utilidad pública que usan Microsoft HoloLens 2 para colaborar en un proyecto de desarrollo de granjas eólicas](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Hologramas habilitar interacciones personales que no son posibles en otra parte. Dado que HoloLens sabe dónde está en el mundo, un carácter holográfico puede mirarle directamente a los ojos e iniciar una conversación con usted.

Un holograma también puede interactuar con su entorno. Por ejemplo, puede colocar una bola holográfica sobre una tabla. A continuación, con [una pulsación](../design/gaze-and-commit.md#composite-gestures)en el aire, observe el salto de la bola y haga sonido a medida que llega a la tabla.

Hologramas objetos del mundo real también pueden oclusión. Por ejemplo, un carácter holográfico podría atravesar una puerta y detrás de una pared, fuera de la vista.

**Sugerencias para integrar hologramas y el mundo real**

* La alineación con las reglas de reanidad hace que los hologramas sean más fáciles de relacionar y más fáciles de relacionar. Por ejemplo: coloque un perro holográfico en el suelo & un jarrón en la tabla en lugar de hacer que flotan en el espacio.
* Muchos diseñadores han descubierto que pueden integrar hologramas más reconocibles mediante la creación de una "sombra negativa" en la superficie en la que se encuentra el holograma. Para ello, crean un brillo suave en el suelo alrededor del holograma y, a continuación, restan la "sombra" del brillo. El brillo suave se integra con la luz del mundo real. La sombra se usa para dar tierra al holograma en el entorno.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Un holograma es lo que <br>puede soñar<br>
        Como desarrollador holográfico, tiene la capacidad de dividir su creatividad en pantallas 2D y en el mundo que le rodea.<br><br>
        ¿Qué *compilará?*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Mundo imaginario holográfico en la sala de estar](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Siguiente punto de comprobación de detección

Está en el recorrido [de detección](get-started-with-mr.md) que hemos diseñado y explorando los conceptos básicos de Mixed Reality. Desde aquí, puede continuar con el siguiente tema básico: 

> [!div class="nextstepaction"]
> [Ampliar el proceso de diseño](case-study-expanding-the-design-process-for-mixed-reality.md)