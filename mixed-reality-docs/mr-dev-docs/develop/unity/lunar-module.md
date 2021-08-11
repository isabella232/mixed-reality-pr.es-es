---
title: Módulo lunar
description: Aprenda a extender los gestos base de HoloLens con el seguimiento de dos manos y la entrada del controlador de Xbox, crear objetos reactivos e implementar sistemas de menús.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Aplicaciones de ejemplo, Diseño, MRTK, Mixed Reality Toolkit, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual
ms.openlocfilehash: 50ca50acd2960ac7bfbd3a3595d7a3dfa4e69f06848919afe7c8f430c41aeaaf
ms.sourcegitcommit: 5977109661a1db4ee2be8ed532479342093303d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116862620"
---
# <a name="lunar-module"></a>Módulo lunar
![Módulo lunar](../images/MRDL_LunarModule.jpg)

>[!NOTE]
>En este artículo se describe un ejemplo exploratorio que hemos creado en [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un lugar donde compartimos nuestros aprendizajes y sugerencias para el desarrollo de aplicaciones de realidad mixta. Nuestros artículos y código relacionados con el diseño evolucionarán a medida que realicemos nuevas des descubrimientos.

>[!NOTE]
>Esta aplicación de ejemplo se diseñó para HoloLens 1.ª generación.

[Lunar Module](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) es una aplicación de ejemplo de código abierto de Microsoft Mixed Reality Design Labs. Obtenga información sobre cómo extender los gestos base de HoloLens con el seguimiento a dos manos y la entrada del controlador de Xbox, crear objetos que sean reactivos para la asignación de superficie y la búsqueda de plano, e implementar sistemas de menú sencillos. Todos los componentes del proyecto están disponibles para su uso en sus propias experiencias de aplicación de realidad mixta.

## <a name="demo-video"></a>Vídeo de demostración 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Grabado con HoloLens 2 con Captura de realidad mixta

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Replanteamiento de las experiencias clásicas para Windows Mixed Reality

En lo alto de la ambiente, un pequeño navoso del módulo Denón hace metódicos sondeos sobre el terreno irregular que hay a continuación. Nuestro piloto sin miedo detecta un área de aterrizaje adecuada. El descenso es muy duro, pero afortunadamente, este recorrido se ha realizado muchas veces antes...

![Interfaz original del lander lunar de Aagi de 1979](images/640px-atari-lunar-lander.png)<br>
*Interfaz original del lander lunar de Aagi de 1979*

[Lunar Lander es](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) un clásico clásico en el que los jugadores intentan pilotar un lander lunar en un punto plano del terreno lunar. Cualquier persona que nazca en los años 70 probablemente haya pasado horas en una galería con los ojos pegados a este vector que se desploma desde el cielo. A medida que un jugador navega por su navía hacia un área de aterrizaje, el terreno se escala para revelar progresivamente más detalles. El éxito significa que se alcanza el umbral seguro de velocidad horizontal y vertical. Los puntos se conceden por el tiempo invertido en el aterrizaje y el combustible restante, con un multiplicador basado en el tamaño del área de aterrizaje.

Aparte del juego, la era de juegos hizo que la innovación constante de los esquemas de control. Desde las configuraciones más sencillas de botones y botones de cuatro vías (que se ven en el icono [Pac-Man)](https://en.wikipedia.org/wiki/Pac-Man)hasta los esquemas muy específicos y complicados vistos a finales de los 90 y 00 (como los de simuladores de carreras y raíles). El esquema de entrada que se usa en la máquina Lunar Lander es interesante por dos motivos: el atractivo del abate y la intrusión.

![Consola de consola de Lunar Lander de Amgr](images/atariconsole.png)<br>
*Consola lunar lander de Amgr*

¿Por qué Aagi y tantas otras compañías de juegos deciden replantearse la entrada?

Un niños que pasee por un paseo por una galería se verá intriguido de forma natural por la máquina más reciente e inteligente. Pero Lunar Lander cuenta con una mecánica de entrada nueva que sale de la muchedumbre.

Lunar Lander usa dos botones para girar el navón **hacia** la izquierda y la derecha, y una presión para controlar la cantidad de movimiento que produce el naveo. Esta presión proporciona a los usuarios un cierto nivel de delicadización que no puede proporcionar un tódor normal. También se trata de un componente común a las modernas cabinas de avión. Arge quería que Lunar Lander dejara inmerso al usuario en la sensación de que, de hecho, estaba pilotando un módulo lunar. Este concepto se conoce como **inmersiones táctiles.**

La sensibilidad táctil es la experiencia de los comentarios sensores al realizar acciones repetitivas. En este caso, la acción repetitiva de ajustar el acelerador y la rotación, que ven los ojos y los oídos de nuestros oídos, ayuda a conectar al jugador al acto de aterrizaje de un navón en la superficie lunar. Este concepto puede estar asociado al concepto de "flujo". Cuando un usuario es totalmente consciente de una tarea que tiene la combinación adecuada de desafío y recompensa, o simplemente, está "en la zona".

Posiblemente, el tipo más destacado de inmersiones en la realidad mixta es la espacialidad. Todo el punto de la realidad mixta es infirirnos en que estos objetos digitales existen en el mundo real. Estamos sintetizando hologramas en nuestro entorno, espacialmente inmersos en entornos y experiencias completos. Esto no significa que no podamos seguir empleando otros tipos de inmersiones en nuestras experiencias como lo hizo Aagi con la inmersiones táctiles en Lunar Lander.

## <a name="designing-with-immersion"></a>Diseño con inmersión

¿Cómo se puede aplicar la sensibilidad táctil a una continuación volumétrica actualizada del clásico de A classic? Antes de abordar el esquema de entrada, es necesario abordar la construcción del juego para el espacio tridimensional.

![Visualización de la asignación de superficie en HoloLens](images/surfacemapping.png)<br>
*Visualización de la asignación espacial en HoloLens*

Al aprovechar el entorno de un usuario, disponemos de opciones infinitas de terreno para el aterrizaje del módulo lunar. Para que el juego sea más parecido al título original, un usuario podría manipular y colocar plataformas de aterrizaje de distintas dificultades en su entorno.

Requerir al usuario que aprenda el esquema de entrada, controlar el envío y tener un objetivo pequeño en el que desaterrar es mucho pedir. Una experiencia de juego correcta incluye la combinación adecuada de desafío y recompensa. El usuario puede elegir un nivel de dificultad, ya que el modo más sencillo simplemente requiere que el usuario se desaterze correctamente en un área definida por el usuario en una superficie examinada por el HoloLens. Una vez que un usuario se queda con el juego, puede aumentar la dificultad según le conste.

### <a name="adding-input-for-hand-gestures"></a>Adición de entrada para gestos de mano

HoloLens entrada base solo tiene dos gestos: [Air Tap y Bloom.](../../design/gaze-and-commit.md#composite-gestures) Los usuarios no necesitan recordar matices contextuales ni una lista de gestos específicos que hacen que la interfaz de la plataforma sea versátil y fácil de aprender. Aunque el sistema solo puede exponer estos dos gestos, HoloLens como un dispositivo puede realizar un seguimiento de dos manos a la vez. Nuestra oda a Lunar Lander es una [aplicación inmersiva, lo que significa que podemos ampliar el conjunto base de gestos para aprovechar dos manos y agregar nuestros propios medios perfectamente táctiles para la navegación del módulo lunar.

Al volver a ver el esquema de control original, era necesario resolver para la rotación **y la rotación.** La advertencia es que la rotación en el nuevo contexto agrega un eje adicional (técnicamente dos, pero el eje Y es menos importante para el aterrizaje). Los dos movimientos de envío distintos se prestan de forma natural para asignarse a cada mano:

![Pulse y arrastre el gesto para girar el lander en los tres ejes.](images/module-handdrag.gif)<br>
*Pulse y arrastre el gesto para girar el lander en los tres ejes.*

**Empuje**

La maneta de la máquina original de la galería se asigna a una escala de valores; cuanto mayor sea la posición de la marcha, más tiempo se aplicó al navido. Un matiz importante que se debe señalar aquí es cómo el usuario puede quitar la mano del control y mantener un valor deseado. Podemos usar eficazmente el comportamiento de pulsar y arrastrar para lograr el mismo resultado. El valor de la estocada comienza en cero. El usuario pulsa y arrastra para aumentar el valor. En ese momento, podrían dejar ir para mantenerla. Cualquier cambio en el valor del gesto de pulsar y arrastrar sería el delta del valor original.

**Rotación**

Esto es un poco más complicado. Tener botones holográficos de "girar" para pulsar permite disfrutar de una experiencia increíble. No hay un control físico que aprovechar, por lo que el comportamiento debe ser la manipulación de un objeto que representa el lander o con el propio lander. Se ha llegado a un método mediante pulsar y arrastrar, que permite a un usuario "insertar y extraer" de forma eficaz en la dirección a la que quiere que se encare. Cada vez que un usuario pulsa y mantiene presionado, el punto en el espacio donde se inició el gesto se convierte en el origen de la rotación. Al arrastrar desde el origen, se convierte la diferencia de la traducción de la mano (X,Y,Z) y se aplica a la diferencia de los valores de rotación del lander. O, más simplemente, arrastrar a la izquierda *<-> derecha,* hacia arriba <-> hacia abajo, hacia delante <-> hacia atrás en espacios gira el envío en consecuencia.

Puesto que HoloLens puede realizar un seguimiento de dos manos, la rotación se puede asignar a la mano derecha mientras la izquierda controla el movimiento. La delicadía es el factor que impulsa el éxito en este juego. La *sensación* de estas interacciones es la prioridad más alta absoluta. Especialmente en el contexto de la inmersión táctil. Un envío que reaccione con demasiada rapidez sería difícil de dirigir, mientras que uno demasiado lento requeriría que el usuario "insertara y extraera" en el navía durante un período de tiempo relativamente largo.

### <a name="adding-input-for-game-controllers"></a>Adición de entrada para controladores de juegos

Aunque los gestos de mano en el HoloLens proporcionan un método nuevo de control más preciso, todavía hay una cierta falta de comentarios táctiles "verdaderos" que se obtienen de los controles análogos. La conexión de un controlador de juego de Xbox nos permite devolver esta sensación de integridad al mismo tiempo que aprovecha los palos de control para mantener un control más preciso.

Hay varias maneras de aplicar el esquema de control relativamente directo al controlador de Xbox. Puesto que estamos intentando estar lo más cerca posible de la configuración original de la galería, **la** opción Desenlazador se asigna mejor al botón de desencadenador. Estos botones son controles análogos,  lo que significa que tienen más que estados de encendido y apagado sencillos, que realmente responden al grado de presión que se les coloca. Esto nos proporciona una construcción similar a la del **eje de apoyo .** A diferencia del juego original y el gesto de la mano, este control cortará el descontrol del envío una vez que un usuario deje de presionar el desencadenador. Todavía proporciona al usuario el mismo grado de finura que el juego original.

![El control de posición izquierdo se asigna a Yaw y Roll, el control de posición derecho se asigna a Pitch and Roll](images/thumbsticksidebyside.gif)<br>
*El control de posición izquierdo se asigna a yaw y roll; el botón de posición derecho se asigna a pitch and roll*

Las dos huellas digitales se prestan de forma natural para controlar la rotación de envíos. Desafortunadamente, hay tres ejes en los que el navés puede girar y dos huellas digitales que admiten dos ejes. Este error de coincidencia significa que un control de un eje es un control de un solo control; o hay superposición de ejes para las huellas digitales. La solución anterior terminó sintiéndose "rota", ya que las huellas digitales mezclan de forma inherente sus valores X e Y locales. La última solución requería algunas pruebas para encontrar qué ejes redundantes son los más naturales. En el ejemplo final se *usa yaw* and *roll* (ejes Y y X) para el control de posición izquierdo, y *pitch* and *roll* (ejes Z y X) para el control de posición derecho. Esto parecía lo más natural, ya que *el lanzamiento* parece emparejarse bien de forma independiente *con yaw* y *pitch*. Como nota lateral, el uso de ambos dedos para el lanzamiento *también* duplica el valor de rotación; es bastante divertido tener bucles lander do.

En esta aplicación de ejemplo se muestra cómo el reconocimiento espacial y la sensibilidad táctil pueden cambiar significativamente una experiencia gracias a las Windows Mixed Reality de entrada extensibles de la aplicación. Aunque Lunar Lander puede estar a punto de llegar a los 40 años, los conceptos expuestos con ese pequeño octágono con las manos seguirán vivo para siempre. Al mirar el futuro, ¿por qué no mirar el pasado?

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar scripts y requisitos previos para la aplicación de ejemplo Módulo lunar en Mixed Reality [Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también

* [MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabla periódica de los elementos 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)