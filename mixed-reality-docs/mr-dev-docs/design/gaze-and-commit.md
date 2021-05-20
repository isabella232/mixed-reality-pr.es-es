---
title: Mirada y confirmación
description: Obtenga información sobre el modelo de entrada de mirada y confirmación, incluidos dos tipos de mirada (mirada con la cabeza y mirada con los ojos) y varios tipos de confirmación.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality, mirada, objetivo de mirada, interacción, diseño, seguimiento de los ojos, seguimiento de la cabeza, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196570"
---
# <a name="gaze-and-commit"></a>Mirada y confirmación

_La mirada y confirmación_ es un modelo de entrada fundamental que está estrechamente relacionado con la forma en que interactuamos con nuestros equipos mediante el mouse: haga clic _& clic en_. En esta página, se presentan dos tipos de entrada de mirada (mirada con la cabeza y los ojos) y diferentes tipos de acciones de confirmación. _La mirada y la confirmación_ se consideran un modelo de entrada lejana con manipulación indirecta. Se usa mejor para interactuar con contenido holográfico que está fuera de alcance.

Los cascos de realidad mixta pueden usar la posición y la orientación de la cabeza del usuario para determinar el vector de dirección de la cabeza. Piense en la mirada como un rayo que apunta directamente directamente entre los ojos del usuario. Esto es una aproximación bastante general de dónde mira el usuario. La aplicación puede formar una intersección con objetos virtuales o reales y dibujar un cursor en esa ubicación para que el usuario sepa a qué se dirigirá.

Además de la mirada con la cabeza, algunos cascos de realidad mixta, como HoloLens 2, incluyen sistemas de seguimiento ocular que producen un vector de mirada con los ojos. Esto proporciona una medida específica de adónde mira el usuario. En ambos casos, la mirada representa una señal importante para la intención del usuario. Entre mejor el sistema pueda interpretar y predecir las acciones previstas del usuario, mayor será la satisfacción y el rendimiento del usuario.

A continuación se muestran algunos ejemplos de cómo usted como desarrollador de realidad mixta puede beneficiarse de la mirada con la cabeza o los ojos:
* La aplicación puede formar intersección con la mirada con los hologramas de la escena para determinar dónde está la atención del usuario (más precisa con la mirada con los ojos).
* La aplicación puede canalizar gestos y presiones del controlador en función de la mirada del usuario, lo que permite al usuario seleccionar, activar, agarrar, desplazarse o interactuar sin problemas con sus hologramas.
* La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real mediante la intersección de su rayo de mirada con la malla de asignación espacial.
* La aplicación puede saber cuándo el usuario no busca en la dirección de un objeto importante, lo que puede llevar a la aplicación a proporcionar indicaciones visuales y de audio para dirigirse hacia ese objeto.

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
         <tr>
        <td>Mirada con los ojos y confirmación</td>
        <td>❌ No disponible</td>
        <td>✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</td>
        <td>❌ No disponible</td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demostración de conceptos de diseño de seguimiento de la cabeza y los ojos

Si quiere ver los conceptos de diseño de Head and Eye Tracking en acción, consulte la demostración de vídeo Diseño de **hologramas:** seguimiento de la cabeza y seguimiento de los ojos a continuación. Cuando haya terminado, continúe para obtener un análisis más detallado de temas específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo se tomó de la aplicación "Diseño de hologramas" HoloLens 2 aplicación. Descargue y disfrute de la experiencia [completa aquí.](https://aka.ms/dhapp)*

## <a name="gaze"></a>Mirar

### <a name="eye--or-head-gaze"></a>¿Mirada con los ojos o con la cabeza?
Hay varias consideraciones cuando se enfrenta a la pregunta de si debe usar el modelo de entrada "mirada con los ojos y confirmación" o "mirada con la cabeza y confirmación". Si está desarrollando para un casco envolvente o para HoloLens (1.ª generación), la elección es sencilla: mirada con la cabeza y confirmación. Si va a desarrollar para HoloLens 2, la elección se vuelve un poco más difícil. Es importante comprender las ventajas y los desafíos que se incluyen con cada uno de ellos.
Hemos compilado algunas ventajas y desventajas generales en la tabla siguiente para contrastar el objetivo de la cabeza frente a la mirada con los ojos. Esto está lejos de completarse y se recomienda obtener más información sobre el objetivo de la mirada con los ojos en la realidad mixta aquí:
* [Seguimiento de los HoloLens 2:](eye-tracking.md)introducción general de nuestra nueva funcionalidad de seguimiento de los HoloLens 2 incluir algunas instrucciones para desarrolladores. 
* [Interacción con la mirada con los](eye-gaze-interaction.md)ojos: consideraciones y recomendaciones de diseño al planear el uso del seguimiento de los ojos como entrada.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Objetivo de la mirada con los ojos</strong></td>
        <td><strong>Establecer el destino de la mirada con la cabeza</strong></td>
    </tr>
    <tr>
        <td>¡rápido!</td>
        <td>más despacio</td>
    </tr>
    <tr>
        <td>Poco esfuerzo (casi todos los movimientos corporales necesarios)</td>
        <td>Puede ser fatiguing: posibles molestias (por ejemplo, presión de cuello)</td>
    </tr>
    <tr>
        <td>No requiere un cursor, pero se recomiendan comentarios sutiles</td>
        <td>Requiere mostrar un cursor</td>
    </tr>
    <tr>
        <td>Sin movimientos de los ojos suavizados; por ejemplo, no es bueno para dibujar</td>
        <td>Más controlado y explícito</td>
    </tr>
    <tr>
        <td>Difícil para destinos pequeños (por ejemplo, botones pequeños o vínculos web)</td>
        <td>¡fidedigno! ¡Excelente reserva!</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Tanto si usa la mirada con la cabeza como la mirada con los ojos para el modelo de entrada de mirada y confirmación, cada uno incluye distintos conjuntos de restricciones de diseño. Se tratan por separado en los [artículos de](gaze-and-commit-eyes.md) mirada con los ojos y confirmación y mirada con la cabeza [y confirmación.](gaze-and-commit-head.md)

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        Para la mirada con la cabeza, la mayoría de las aplicaciones deben usar un [cursor](cursors.md) u otra indicación auditiva o visual para proporcionar al usuario confianza en lo que están a punto de interactuar. Normalmente, este cursor se coloca en el mundo donde su rayo de mirada con la cabeza forma primero una intersección con un objeto, que puede ser un holograma o una superficie real.<br>
        <br>
        En el caso de  la mirada con los ojos, por lo general se recomienda no mostrar un cursor, ya que esto puede llegar a distraer e incoerablemente al usuario. En su lugar, resalte de forma sutil los destinos visuales o use un cursor de ojo atractivo para proporcionar confianza sobre lo que el usuario está a punto de interactuar. Para obtener más información, consulte nuestra guía de diseño para [obtener información](eye-tracking.md) detallada sobre HoloLens 2.
    :::column-end:::
        :::column:::
       ![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)<br>
       *Imagen: un cursor visual de ejemplo para mostrar la mirada*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
Después de hablar  sobre diferentes maneras de mirar un destino, vamos a hablar un poco más sobre la parte de confirmación en la mirada _y confirmar_. 
Después de tener como destino un objeto o elemento de interfaz de usuario, el usuario puede interactuar o hacer clic en él mediante una entrada secundaria. Esto se conoce como el paso de confirmación del modelo de entrada. 

Se admiten los siguientes métodos de confirmación:
- Gesto de pulsar en el aire (es decir, elevar la mano delante de usted y reunir el dedo índice y el dedo)
- Diga _"seleccionar"_ o uno de los comandos de voz de destino.
- Presionar un solo botón en un [clicker de HoloLens](/hololens/hololens1-clicker)
- Presione el botón "A" en un gamepad de Xbox.
- Presione el botón "A" en un controlador adaptable de Xbox.

### <a name="gaze-and-air-tap-gesture"></a>Gesto de mirada y pulsación en el aire
Pulsar en el aire es hacer el gesto de pulsar con la mano vertical. Para usar una pulsación en el aire, coloque el dedo índice en la posición lista, luego práctese con el dedo y vuelva a subir el dedo del índice hasta liberarlo. En HoloLens (1.ª generación), el toque de aire es la entrada secundaria más común.


:::row:::
    :::column:::
       ![Dedo en la posición lista](images/readyandpress-ready.jpg)<br>
       **Dedo en la posición lista**<br>
    :::column-end:::
    :::column:::
       ![Presione el dedo hacia abajo para pulsar o hacer clic en](images/readyandpress-press.jpg)<br>
        **Presione el dedo hacia abajo para pulsar o hacer clic en**<br>
    :::column-end:::
:::row-end:::


La pulsación en el aire también está disponible HoloLens 2. Se ha relajado con la versión original. Ahora se admiten casi todos los tipos de pesquete, siempre y cuando la mano esté vertical y deteniendo. Esto facilita a los usuarios aprender y usar el gesto. Esta nueva pulsación en el aire reemplaza la anterior a través de la misma API, por lo que las aplicaciones existentes tendrán el nuevo comportamiento automáticamente después de volver a compilar HoloLens 2.

<br>

---

### <a name="gaze-and-select-voice-command&quot;></a>Comando de voz &quot;Seleccionar&quot; y mirada
Los comandos de voz son uno de los métodos de interacción principales de la realidad mixta. Proporciona un eficaz mecanismo de manos libres para controlar el sistema. Hay diferentes tipos de modelos de interacción de voz:

- El comando genérico &quot;Select&quot; que usa una acción de clic o confirmación como entrada secundaria.
- Los comandos object (por ejemplo, &quot;Close&quot; o &quot;Make it bigger") realizan y confirman una acción como entrada secundaria.
- Los comandos globales (por ejemplo, "Ir al inicio") no requieren un destino.
- Las interfaces de usuario de conversación o entidades como Cortana tienen una funcionalidad de lenguaje natural de inteligencia artificial.
- Comandos de voz personalizados

Para obtener más información sobre los detalles y una lista completa de los comandos de voz disponibles y cómo usarlos, consulte nuestra guía [de comandos de](../out-of-scope/voice-design.md) voz.

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Gaze y HoloLens Clicker

:::row:::
    :::column:::
        HoloLens Clicker es el primer dispositivo periférico creado específicamente para HoloLens. Se incluye con HoloLens (1.ª generación) Development Edition. HoloLens Clicker permite que un usuario haga clic con movimiento mínimo de la mano y se confirme como una entrada secundaria. HoloLens Clicker se conecta a HoloLens (1ª generación) o HoloLens 2 mediante Bluetooth de bajo consumo (BTLE).<br>
        <br>
        [Más información e instrucciones para emparejar el dispositivo](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagen: HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Control inalámbrico de Mirada y Xbox

:::row:::
    :::column:::
        El controlador inalámbrico xbox realiza una acción de clic como entrada secundaria mediante el botón "A". El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema. Si quieres personalizar el controlador, usa la aplicación Accesorios de Xbox para configurar el controlador inalámbrico xbox.<br>
        <br>
        [Cómo emparejar un controlador de Xbox con el equipo](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagen: Xbox Wireless Controller*
    :::column-end:::
        :::column:::
       ![Controlador inalámbrico de Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Mirada y controlador adaptable de Xbox
Diseñado principalmente para satisfacer las necesidades de los jugadores con movilidad limitada, el controlador adaptable de Xbox es un centro unificado para dispositivos que ayuda a que la realidad mixta sea más accesible.

El controlador adaptable de Xbox realiza una acción de clic como entrada secundaria mediante el botón "A". El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema. Si desea personalizar el controlador, use la aplicación Accesorios de Xbox para configurar el controlador adaptable de Xbox.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Conecte dispositivos externos, como conmutadores, botones, montajes y flechas, para crear una experiencia de controlador personalizada que sea exclusiva de usted. Las entradas de botones, de botones y desencadenadores se controlan con dispositivos de asistencia conectados a través de conectores de 3,5 mm y puertos USB.

![Puertos del Xbox Adaptive Controller](images/xbox-adaptive-controller-ports.jpg)<br>
*Puertos del Xbox Adaptive Controller*

[Instrucciones para emparejar el dispositivo](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Más información disponible en el sitio de Xbox</a>

<br>

---

## <a name="composite-gestures"></a>Gestos compuestos

### <a name="air-tap"></a>Pulsar en el aire
El gesto de pulsación de aire (y los demás gestos siguientes) reacciona solo a una pulsación específica. Para detectar otras pulsaciones, como Menu o Ctrl, la aplicación debe usar directamente las interacciones de nivel inferior descritas en la sección anterior de los dos gestos de componente clave.

### <a name="tap-and-hold"></a>Mantener pulsado
Mantener pulsado simplemente consiste en mantener la posición del dedo hacia abajo al pulsar en el aire. La combinación de pulsación y retención del aire permite varias interacciones más complejas de "hacer clic y arrastrar" cuando se combina con el movimiento de los brazos, como la selección de un objeto en lugar de activarlo o las interacciones secundarias del mouse, como mostrar un menú contextual.
Sin embargo, se debe tener cuidado al diseñar para este gesto, ya que los usuarios pueden ser propensos a relajar sus posturas de mano durante cualquier gesto extendido.

### <a name="manipulation"></a>Manipulación
Los gestos de manipulación se pueden usar para mover, cambiar el tamaño o girar un holograma cuando quiera que el holograma reaccione 1:1 a los movimientos de las manos del usuario. Uno de los usos de estos movimientos 1:1 es permitir al usuario dibujar o pintar en el mundo.
El destino inicial de un gesto de manipulación debe establecerse con la mirada o apuntando. Una vez que se inicia la pulsación y la retención, cualquier manipulación de objetos se controla mediante movimientos de mano, lo que permite al usuario mirar alrededor mientras manipula.

### <a name="navigation"></a>Navegación
Los gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de la interfaz de usuario, como los menús circulares. Se mantiene pulsado para iniciar el gesto y, después, se mueve la mano dentro de un cubo 3D normalizado centrado alrededor de la pulsación inicial. Puede mover la mano a lo largo del eje X, Y o Z de un valor de -1 a 1, siendo 0 el punto inicial.
La navegación se puede utilizar para crear gestos de zoom o desplazamiento continuo basado en la velocidad, similares al desplazamiento en una interfaz de usuario 2D cuando se hace clic con el botón central del ratón para después mover el ratón hacia arriba y abajo.

La navegación con raíles hace referencia a la capacidad de reconocer los movimientos en determinado eje hasta que se alcanza un umbral determinado en ese eje. Esto solo es útil cuando el desarrollador habilita el movimiento en más de un eje en una aplicación, por ejemplo, si una aplicación está configurada para reconocer gestos de navegación en los ejes X e Y, pero también en el eje X especificado con raíles. En este caso, el sistema reconocerá los movimientos de las manos a través del eje X siempre que permanezcan dentro de un raíl imaginario (guía) en el eje X, si también se produce el movimiento de la mano en el eje Y.

En las aplicaciones 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, hacer zoom o arrastrar dentro de la aplicación. Esto inserta entradas táctiles virtuales en la aplicación para simular gestos táctiles del mismo tipo. Los usuarios pueden seleccionar cuál de estas acciones se lleva a cabo al alternar entre las herramientas de la barra encima de la aplicación; para ello, seleccione el botón o diga "<Scroll/Drag/Zoom> Tool".

[Más información sobre los gestos compuestos](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconocedores de gestos

Una ventaja de usar el reconocimiento de gestos es que solo puede configurar un reconocedor de gestos para los gestos que el holograma de destino puede aceptar. La plataforma solo realiza la desambiguación según sea necesario para distinguir esos gestos admitidos concretos. De este modo, un holograma que solo admite el toque de aire puede aceptar cualquier período de tiempo entre presionar y soltar, mientras que un holograma que admita pulsar y mantener pulsado puede promover la pulsación a una retención después del umbral de tiempo de retención.

## <a name="hand-recognition"></a>Reconocimiento de la mano
HoloLens reconoce los gestos de la mano mediante el seguimiento de la posición de una o ambas manos si son visibles para el dispositivo. HoloLens ve las manos cuando están en el estado preparado (parte posterior de la mano hacia ti con el dedo índice arriba) o el estado presionado (parte posterior de la mano hacia ti con el dedo índice hacia abajo). Cuando las manos están en otras poses, HoloLens las omite.
Por cada mano que HoloLens detecte, puede acceder a su posición sin orientación y su estado presionado. A medida que la mano se acerca al borde del marco gestual, obtendrás un vector de dirección que puedes mostrar al usuario para que sepa cómo mover la mano para volver a ponerla donde HoloLens pueda verla.

## <a name="gesture-frame"></a>Marco gestual
En el caso de los gestos en HoloLens, la mano debe estar dentro de un marco de gestos, en un intervalo que las cámaras de detección de gestos puedan ver adecuadamente, desde la sensibilidad hasta la sensibilidad y entre las manos. Los usuarios deben estar entrenados en esta área de reconocimiento tanto para el éxito de la acción como para su propia comodidad. Inicialmente, muchos usuarios asumirán que el marco de gestos debe estar dentro de su vista a través de HoloLens y mantener los manos presionados para interactuar. Al usar HoloLens Clicker, no es necesario que las manos se encuentran dentro del marco de gestos.

En concreto, en el caso de los gestos continuos, hay cierto riesgo de que los usuarios muevan las manos fuera del marco de gestos mientras están en medio del gesto al mover un objeto holográfico, por ejemplo, y perder el resultado previsto.

Hay tres cosas que hay que tener en cuenta:

- Educación del usuario sobre la existencia del marco de gestos y los límites aproximados. Esto se enseña durante la configuración de HoloLens.

- Notificación a los usuarios cuando sus gestos se acercan o traspasan los límites del marco de gestos dentro de una aplicación hasta el punto de que un gesto perdido conduce a resultados no deseados. La investigación ha mostrado las principales calidades de este sistema de notificación. El shell de HoloLens proporciona un buen ejemplo de este tipo de notificación: visual, en el cursor central, que indica la dirección en la que se realiza el cruce de límites.

- Se deben minimizar las consecuencias de traspasar los límites del marco gestual. En general, esto significa que el resultado de un gesto debe detenerse en el límite y no invertirse. Por ejemplo, si un usuario mueve algún objeto holográfico a través de una sala, el movimiento debe detenerse cuando se infringe el marco de gestos y no se devuelve al punto inicial. Es posible que el usuario experimente cierta frustración, pero podría comprender más rápidamente los límites y no tener que reiniciar todas las acciones previstas cada vez.



## <a name="see-also"></a>Consulte también
* [Interacción basada en los ojos](eye-gaze-interaction.md)
* [Seguimiento de los ojos en HoloLens 2](eye-tracking.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)