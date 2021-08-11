---
title: Marco holográfico
description: Obtenga información sobre cómo los usuarios ven el mundo de la realidad mixta a través del marco holográfico y cómo diseñar mejor la experiencia.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, marco holográfico, campo de vista, FOV, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, interacciones, navegación, menú
ms.openlocfilehash: be24f2b583541e6ed0adff25b3d8edd6c3fe5285aea93d0a4d6df8ee61e5c070
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226390"
---
# <a name="holographic-frame"></a>Marco holográfico

Los usuarios ven el mundo de la realidad mixta a través de una ventanilla rectangular que funciona con el casco. En el dispositivo HoloLens, esta área rectangular se denomina trama holográfica y permite a los usuarios ver contenido digital superpuesto en el mundo real que les rodea. El diseño de experiencias optimizadas para el marco holográfico crea oportunidades, mitiga los desafíos y mejora la experiencia del usuario de las aplicaciones de realidad mixta.

## <a name="designing-for-content"></a>Diseño de contenido

A menudo, los diseñadores experimentan la necesidad de limitar el ámbito de su experiencia a lo que el usuario puede ver inmediatamente, lo que sacrificará la escala real para asegurarse de que el usuario ve un objeto en su totalidad. De forma similar, los diseñadores con aplicaciones complejas suelen sobrecargar el marco holográfico con contenido, sobrecargar a los usuarios con interacciones difíciles e interfaces desordenadas. Los diseñadores que crean contenido de realidad mixta no necesitan limitar la experiencia a directamente delante del usuario y dentro de su vista inmediata. Si se asigna el mundo físico alrededor del usuario, todas estas superficies deben considerarse un lienzo potencial para el contenido digital y las interacciones. Un diseño adecuado de las interacciones y el contenido dentro de una experiencia debe animar al usuario a moverse por su espacio, dirigir su atención al contenido clave y ayudar a ver todo el potencial de la realidad mixta.

Quizás la técnica más importante para fomentar el movimiento y la exploración dentro de una aplicación es permitir que los **usuarios se ajusten a la experiencia**. Dé a los usuarios un breve período de tiempo "sin tareas" con el dispositivo. Esto puede ser tan sencillo como colocar un objeto en el espacio y permitir a los usuarios moverse por él o narrar una introducción a la experiencia. Este tiempo debe estar libre de cualquier tarea crítica o gestos específicos, como pulsar el aire. El propósito es permitir que los usuarios puedan ver el contenido a través del dispositivo antes de requerir interactividad o avanzar a través de la aplicación. Esto es especialmente importante para los usuarios por primera vez, ya que se sientan cómodos al ver el contenido a través del marco holográfico y la naturaleza de los hologramas.

### <a name="large-objects"></a>Objetos grandes

A menudo, el contenido que una experiencia requiere, especialmente el contenido real, será mayor que el marco holográfico. Los objetos que normalmente no caben dentro del marco holográfico deben reducirse para ajustarse cuando se introducen por primera vez (ya sea a una escala más pequeña o a una distancia). La clave es permitir **que los usuarios vean el tamaño completo del objeto antes** de que la escala sobresalte el marco. Por ejemplo, se debe mostrar un esqueleto holográfico para ajustarse completamente al marco. Esto permite a los usuarios formar una comprensión espacial de la forma general del animales, antes de ajustar su tamaño a escala [real](scale.md) cerca del usuario.

Con el tamaño completo del objeto en mente, los usuarios tienen una expectativa de dónde moverse y buscar partes específicas de ese objeto. En una experiencia con contenido inmersivo, ayuda a tener una manera de hacer referencia al tamaño completo de ese contenido. Por ejemplo, si la experiencia implica recorrer un modelo de una casa virtual, ayuda a tener una versión más pequeña del tamaño de la casa para identificar dónde se encuentran dentro de la casa.

Para obtener un ejemplo de diseño para objetos de gran tamaño, vea [Cars.](holographic-frame.md#volvo-cars)

### <a name="many-objects"></a>Muchos objetos

Las experiencias con muchos objetos o componentes deben considerar la posibilidad de usar todo el espacio alrededor del usuario para evitar abarrote el marco holográfico directamente delante del usuario. Se recomienda ralentizar la introducción de contenido a una experiencia, especialmente con experiencias que planean servir muchos objetos al usuario. La clave es permitir que **los usuarios** comprendan el diseño de contenido de la experiencia, lo que les ayuda a comprender espacialmente lo que les rodea como actualizaciones de contenido.

Una técnica para lograrlo es proporcionar puntos persistentes (también conocidos como puntos de referencia) en la experiencia que delimita el contenido al mundo real. Por ejemplo, un punto de referencia podría ser un objeto físico en el mundo real, como una tabla donde aparece contenido digital o un objeto digital, como un conjunto de pantallas digitales donde el contenido aparece con frecuencia. Los objetos también se pueden colocar en la periferia del marco holográfico para animar al usuario a buscar contenido clave. La detección de contenido más allá de la periferia puede ser ayudada por [directores de atención.](holographic-frame.md#attention-directors)

La colocación de objetos en la periferia puede animar a los usuarios a mirar hacia el lado, lo que puede ayudar a los directores de atención, como se describe a continuación. Para más información sobre las consideraciones sobre los fotogramas holográficos, consulte la [documentación de](comfort.md#holographic-frame-considerations) confort.

<br>

---

## <a name="interaction-considerations"></a>Consideraciones de interacción

Al igual que con el contenido, las interacciones en una experiencia de realidad mixta no deben limitarse a lo que el usuario puede ver inmediatamente. Las interacciones pueden tener lugar en cualquier lugar del espacio real alrededor del usuario. Estas interacciones pueden ayudar a animar a los usuarios a moverse y explorar experiencias.

### <a name="attention-directors"></a>Directores de atención

Indicar puntos de interés o interacciones clave puede ser fundamental para el progreso de los usuarios a través de una experiencia. La atención y el movimiento del usuario del marco holográfico se pueden dirigir de manera sutil o pesada. Recuerde equilibrar los directores de atención con períodos de exploración gratuita en la realidad mixta (especialmente al principio de una experiencia) para evitar abrume al usuario. En general, hay dos tipos de directores de atención:
* **Directores visuales:** La manera más fácil de indicar al usuario que debe moverse en una dirección específica es proporcionar una indicación visual. Esto se puede hacer a través de un efecto visual (por ejemplo, una ruta de acceso que el usuario puede seguir visualmente hacia la siguiente parte de la experiencia) o incluso como flechas direccionales simples. Cualquier indicador visual debe estar conectado al entorno del usuario, no al marco holográfico o al cursor.
* **Directores de audio:** [el sonido](spatial-sound-design.md) espacial puede proporcionar una manera eficaz de establecer objetos en una escena. Puede alertar a los usuarios sobre los objetos que entran en una experiencia o dirigir la atención a un punto específico del espacio moviendo la vista del usuario hacia los objetos clave. El uso de directores de audio para guiar la atención del usuario puede ser más sutil y menos intrusivo que los directores visuales. En algunos casos, puede ser mejor empezar con un director de audio y, a continuación, pasar a un director visual si el usuario no reconoce la indicación. Los directores de audio también se pueden emparejar con directores visuales para agregar énfasis.

### <a name="commanding-navigation-and-menus"></a>Comandos, navegación y menús

Idealmente, las interfaces de las experiencias de realidad mixta se emparejan estrechamente con el contenido digital que controlan. Por lo tanto, los menús 2D flotantes libres a menudo no son ideales para la interacción y pueden ser difíciles para los usuarios demasiado cómodos con dentro del marco holográfico. Para las experiencias que requieren elementos de interfaz como [](billboarding-and-tag-along.md) menús o campos de texto, considere la posibilidad de usar un método de etiquetas para seguir el marco holográfico después de un breve retraso. Evite bloquear el contenido en el marco como una pantalla de cara, ya que esto puede desorientar al usuario e interrumpir la sensación de desenlace de otros objetos digitales de la escena.

También puede colocar elementos de interfaz directamente en el contenido específico que controlan, lo que permite que las interacciones se producen de forma natural alrededor del espacio físico del usuario. Por ejemplo, dividir un menú complejo en partes independientes, con cada botón o grupo de controles asociados al objeto específico al que afecta la interacción. Para seguir con este concepto, considere el uso de objetos [interactuables.](interactable-object.md)

### <a name="gaze-and-gaze-targeting"></a>Mirada y mirada dirigidas

El marco holográfico presenta una herramienta para que el desarrollador desencadene interacciones y evalúe dónde reside la atención de un usuario. [La](gaze-and-commit.md) mirada es una de las interacciones clave en [HoloLens,](interaction-fundamentals.md)donde la mirada se puede emparejar con [gestos](gaze-and-commit.md#composite-gestures) (como con pulsación de aire) o voz [(lo](voice-input.md) que permite interacciones basadas en voz más cortas y naturales). Por lo tanto, esto hace que el marco holográfico sea un espacio para observar contenido digital e interactuar con él. Si la experiencia requiere la interacción con varios objetos alrededor del espacio del usuario (por ejemplo, la selección múltiple de objetos alrededor del espacio del usuario con mirada y gesto), considere la posibilidad de incorporar esos objetos a la vista del usuario o limitar la cantidad de movimiento de la cabeza necesario para promover la comodidad del [usuario.](comfort.md)

La mirada también se puede usar para realizar un seguimiento de la atención del usuario a través de una experiencia y ver a qué objetos o partes de la escena llamó más atención el usuario. Esto puede ser especialmente útil para depurar una experiencia, lo que permite que herramientas analíticas como mapas térmicos vean dónde los usuarios dedican más tiempo o a los que les faltan determinados objetos o interacción. El seguimiento de la mirada también puede proporcionar una herramienta eficaz para facilitar las experiencias (consulte el [ejemplo de Lowe's Kitchen).](holographic-frame.md#lowes-kitchen)

Si quiere ver los conceptos de diseño de Head and Eye Tracking en acción, consulte la demostración de vídeo **Designing Hologramas - Head Tracking and Eye Tracking** (Diseño de Hologramas: seguimiento de la cabeza y seguimiento de los ojos a continuación:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo se tomó de la aplicación "Designing Holograms" para HoloLens 2. Descargue y disfrute de la experiencia completa [aquí](https://aka.ms/dhapp).*

<br>

---

## <a name="performance"></a>Rendimiento

El uso adecuado del marco holográfico es fundamental para las [experiencias de calidad del](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) rendimiento. Un desafío técnico común (y facilidad de uso) es sobrecargar el marco del usuario con contenido digital, lo que hace que el rendimiento de la representación se degrade. En su lugar, considere la posibilidad de usar todo el espacio alrededor del usuario para organizar el contenido digital, mediante las técnicas descritas anteriormente, para reducir la carga de representación y garantizar una calidad de presentación óptima.

El contenido digital dentro del marco holográfico del HoloLens también [](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) se puede emparejar con el plano de estabilización para lograr un rendimiento óptimo y estabilidad [del holograma.](../develop/platform-capabilities-and-apis/hologram-stability.md)

<br>

---

## <a name="examples"></a>Ejemplos

### <a name="volvo-cars"></a>Automóviles de Cars

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

En la experiencia de showroom de Cars, se invita a los clientes a obtener información sobre las funcionalidades de un nuevo automóvil en una experiencia HoloLens guiada por un asociado de Associate. Cuando se enfrentaba a un desafío con el marco holográfico: un automóvil de tamaño completo es demasiado grande para colocarse junto a un usuario. La solución era comenzar la experiencia con un punto de referencia físico, una tabla central en la sala de presentación, con un modelo digital más pequeño del automóvil colocado encima de la tabla. Esto garantiza que el usuario vea el coche completo cuando se introduce, lo que permite una sensación de comprensión espacial una vez que el automóvil crece a su escala real más adelante en la experiencia.

La experiencia de Asíns también hace uso de directores visuales, lo que crea un efecto visual largo desde el modelo de automóvil a pequeña escala en la mesa hasta una pared de la sala de presentación. Esto conduce a un efecto de "ventana mágica", que muestra la vista completa del automóvil a distancia, lo que ilustra más características del automóvil a escala real. El movimiento de la cabeza es horizontal, sin ninguna interacción directa del usuario (en su lugar, recopila indicaciones visualmente y de la narración de la experiencia del asociado de Associate).

<br>

---

### <a name="lowes-kitchen"></a>Lowe's Kitchen

Una experiencia de tienda de Lowe's invita a los clientes a un simulacro a escala completa de una cocina para presentar diversas oportunidades de renovación, como se ve a través de la HoloLens. La cocina de la tienda proporciona un fondo físico para objetos digitales, un lienzo en blanco de electrodomésticos, contracargues y gabinetes para que la experiencia de realidad mixta se desarrolle.

Las superficies físicas actúan como puntos de referencia estáticos para que el usuario se base en la experiencia, ya que un asociado de Lowe's guía al usuario a través de diferentes opciones de producto y finaliza. De esta manera, el asociado puede dirigir verbalmente la atención del usuario al "refrigerador" o al "centro de la cocina" para mostrar contenido digital.

![Un asociado de Lowe usa una tableta para guiar a los clientes a través de HoloLens experiencia.](images/loweskitchen-750px.jpg)<br>
*Un asociado de Lowe usa una tableta para guiar a los clientes a través de HoloLens experiencia.*

La experiencia del usuario se administra, en parte, mediante una experiencia de tableta controlada por el asociado de Lowe. Parte del rol del asociado en este caso también sería limitar el movimiento excesivo de la cabeza, dirigir su atención sin problemas a través de los puntos de interés de la cocina. La experiencia de tableta también proporciona la asociación de Lowe con los datos de mirada en forma de una vista de mapa térmico de la cocina, lo que ayuda a comprender dónde se encuentra el usuario (por ejemplo, en un área específica de ebanés) para proporcionarles una guía de orientación con mayor precisión.

Para obtener un vistazo más profundo a la experiencia de Lowe's Kitchen, consulte la nota clave de [Microsoft en Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragments

En el juego de HoloLens Fragments, la sala de estar se transforma en una escena delictiva virtual en la que se muestran pistas y evidencias, y una sala de reuniones virtual, donde se habla con los caracteres que se senten en el ambiente y se inclinan en las paredes.

![Los fragmentos se diseñaron para tener lugar en el hogar de un usuario, con caracteres que interactúan con objetos y superficies del mundo real.](images/fragments-750px.jpg)<br>
*Los fragmentos se diseñaron para tener lugar en el hogar de un usuario, con caracteres que interactúan con objetos y superficies del mundo real.*

Cuando los usuarios comienzan inicialmente la experiencia, se les da un breve período de ajuste con poca o ninguna interacción. En su lugar, se les recomienda que busquen y se orienten y se aseguren de que la sala está correctamente asignada para el contenido interactivo del juego.

A lo largo de la experiencia, los caracteres se convierten en puntos focales y actúan como directores visuales (movimientos de la cabeza entre caracteres, girar para mirar o gestos hacia áreas de interés). El juego también se basa en indicaciones visuales más destacadas cuando un usuario tarda demasiado tiempo en encontrar un objeto o evento y hace un uso pesado del audio espacial (especialmente con voces de caracteres al entrar en una escena).

<br>

---

### <a name="destination-mars"></a>Destino: Marte

En la experiencia destination: Mars que se ofrece en el Centro Espacial [De la NASA,](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)los visitantes fueron invitados a un viaje inmersivo a la superficie de Marte, guiados por la representación virtual del insóptico astronauta Buzz Aldrin.

![Un Aldrin virtual se convierte en el punto focal para los usuarios de Destino: Marte.](images/destinationmars-750px.png)<br>
*Un Aldrin virtual se convierte en el punto focal para los usuarios de Destino: Marte.*

Como experiencia inmersiva, se ha animado a estos usuarios a mirar alrededor, moviendo la cabeza en todas las direcciones para ver el panorama virtual de Mar dialecto. Aunque para garantizar la comodidad de los usuarios, la narración y la presencia virtual de Buzz Aldrin proporcionaron un punto focal a lo largo de la experiencia. Esta grabación virtual de Timbre (creada por los estudios de Captura de realidad mixta de [Microsoft)](https://www.microsoft.com/mixed-reality/capture-studios)se sitúa en tamaño real y humano, en la esquina de la sala, lo que permite a los usuarios verlo en una vista casi completa. La narración de Buzz indicó a los usuarios que se centren en distintos puntos del entorno (por ejemplo, un conjunto de rocas marianas en el suelo o un monte a la distancia) con cambios específicos en la escena u objetos introducidos por él.

![Los narradores virtuales pasarán a seguir el movimiento de un usuario, lo que crea un punto focal eficaz a lo largo de la experiencia.](images/gazereset-750px.png)<br>
*Los narradores virtuales pasarán a seguir el movimiento de un usuario, lo que crea un punto focal eficaz a lo largo de la experiencia.*

La representación realista de Timbre proporcionaba un punto focal eficaz, completo con técnicas sutiles para convertir a Timbre hacia el usuario para que se sienta como si se encontrara allí, hablando con usted. A medida que el usuario se mueve sobre la experiencia, Timbre se desplazará hacia usted a un umbral antes de volver a un estado neutro si el usuario se mueve demasiado más allá de su periferia. Si el usuario se parece completamente a Timbre (por ejemplo, para ver algo en otra parte de la escena) y vuelve a Timbre, la posición direccional del narrador se centrará una vez más en el usuario. Técnicas como esta proporcionan una sensación eficaz de relajación y crean un punto focal dentro del marco holográfico, lo que reduce el movimiento excesivo de la cabeza y promueve la comodidad [del usuario.](comfort.md)

## <a name="see-also"></a>Consulte también
* [Interacciones instintivas](interaction-fundamentals.md)
* [Comodidad](comfort.md)
* [Escala](scale.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Estabilidad de hologramas](../develop/platform-capabilities-and-apis/hologram-stability.md)
