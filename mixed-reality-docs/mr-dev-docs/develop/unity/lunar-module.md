---
title: Módulo lunar
description: Aprenda a extender los gestos base de HoloLens con el seguimiento de dos manos y la entrada del controlador de Xbox, crear objetos reactivos e implementar sistemas de menús.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Aplicaciones de ejemplo, Diseño, MRTK, Mixed Reality Toolkit, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 2afa40a31a5105bfe0ae674942e2bf88fd16f232b40827efb2446c2b4ad849ba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196633"
---
# <a name="lunar-module"></a>Módulo lunar

>[!NOTE]
>En este artículo se describe un ejemplo exploratorio que hemos creado en [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un lugar donde compartimos nuestros aprendizajes y sugerencias para el desarrollo de aplicaciones de realidad mixta. Nuestros artículos y código relacionados con el diseño evolucionarán a medida que realicemos nuevas des descubrimientos.

[Lunar Module](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) es una aplicación de ejemplo de código abierto de Microsoft Mixed Reality Design Labs. Obtenga información sobre cómo extender los gestos base de HoloLens con el seguimiento de dos manos y la entrada del controlador de Xbox, crear objetos que sean reactivos para la asignación de superficies y la búsqueda de plano, e implementar sistemas de menús sencillos. Todos los componentes del proyecto están disponibles para su uso en sus propias experiencias de aplicación de realidad mixta.

## <a name="demo-video"></a>Vídeo de demostración 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Registrado con HoloLens 2 mediante Captura de realidad mixta

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Replanteamiento de experiencias clásicas para Windows Mixed Reality

En lo alto del ambiente, un pequeño navoso del módulo Deón se encuentra metódicomente en un terreno irregular debajo. Nuestro piloto sin miedo detecta un área de aterrizaje adecuada. El descenso es muy duro, pero afortunadamente, este recorrido se ha realizado muchas veces antes...

![Interfaz original del lander lunar de Alejos de 1979](images/640px-atari-lunar-lander.png)<br>
*Interfaz original del lander lunar de Alejos de 1979*

[Lunar Lander es](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) un clásico clásico en el que los jugadores intentan pilotar un lander lunar en un punto plano del terreno lunar. Cualquier persona que nazca en la décadas de 1970 probablemente haya pasado horas en un campo con los ojos pegados a este vector que se desploma desde el cielo. A medida que un jugador navega por su nave hacia un área de aterrizaje, el terreno se escala para revelar progresivamente más detalles. El éxito significa el aterrizaje dentro del umbral seguro de velocidad horizontal y vertical. Los puntos se conceden por el tiempo invertido en el aterrizaje y el combustible restante, con un multiplicador basado en el tamaño del área de aterrizaje.

Aparte del juego, la era de juegos hizo que la innovación constante de los esquemas de control. Desde las configuraciones de botones y botones de cuatro vías más sencillas (que se ven en el icono [Pac-Man)](https://en.wikipedia.org/wiki/Pac-Man)hasta los esquemas muy específicos y complicados que se vieron a finales de los 90 y los 00 (como los de simuladores y raíles). El esquema de entrada que se usa en la máquina Lunar Lander es interesante por dos motivos: el atractivo de los obstáculos y la intrusión.

![Consola de consola de Lunar Lander de Amgr](images/atariconsole.png)<br>
*Consola lunar lander de Ander*

¿Por qué Atensión y tantas otras empresas de juegos han decidido replantearse la entrada?

La máquina más reciente y con más flash le intrigurá de forma natural a un niños que pasee por un paseo por un paseo. Sin embargo, Lunar Lander presenta una mecánica de entrada nueva que sale de la muchedumbre.

Lunar Lander usa dos botones para girar el navón **a** la izquierda y la derecha, y un resalte para controlar la cantidad de movimiento que produce el naveo. Esta presión proporciona a los usuarios un cierto nivel de delicaduración que no puede proporcionar un tóctea normal. También resulta ser un componente común a las modernas cabinas de avión. Arge quería que Lunar Lander insenso al usuario en la sensación de que, de hecho, estaba pilotando un módulo lunar. Este concepto se conoce como **táctil.**

La sensibilidad táctil es la experiencia de los comentarios sensores al realizar acciones repetitivas. En este caso, la acción repetitiva de ajustar el acelerador y la rotación, que nuestros ojos ven y nuestros ojos escuchan, ayuda a conectar al jugador con el acto de aterrizaje de un avión en la superficie lunar. Este concepto puede estar vinculado al concepto de "flujo". Cuando un usuario está totalmente completo en una tarea que tiene la combinación adecuada de desafío y recompensa, o simplemente, está "en la zona".

Posiblemente, el tipo más destacado de la mezcla en la realidad mixta es la espacialidad. Todo el punto de la realidad mixta es hacernos insensatos a la idea de que estos objetos digitales existen en el mundo real. Estamos sintetizando hologramas en nuestro entorno, espacialmente inmersos en entornos y experiencias completos. Esto no significa que no podamos seguir empleando otros tipos de experiencias igual que lo hizo A still with tactile lander en Lunar Lander.

## <a name="designing-with-immersion"></a>Diseño con insondación

¿Cómo se puede aplicar la sensibilidad táctil a una continuación volumétrica actualizada del clásico de A classic? Antes de abordar el esquema de entrada, es necesario abordar la construcción del juego para el espacio tridimensional.

![Visualización de la asignación de superficie en HoloLens](images/surfacemapping.png)<br>
*Visualización de la asignación espacial en HoloLens*

Al aprovechar el entorno de un usuario, tenemos de forma eficaz opciones de terreno infinito para el aterrizaje del módulo lunar. Para que el juego sea el más parecido al título original, un usuario podría manipular y colocar plataformas de aterrizaje con distintas dificultades en su entorno.

![Vuelo del módulo lunar](images/640px-lm-hero.jpg)<br>
*Vuelo del módulo lunar*

Exigir al usuario que aprenda el esquema de entrada, controlar el envío y tener un objetivo pequeño en el que llegar es mucho pedir. Una experiencia de juego correcta incluye la combinación adecuada de desafío y recompensa. El usuario puede elegir un nivel de dificultad, con el modo más sencillo que simplemente requiere que el usuario aterrizó correctamente en un área definida por el usuario en una superficie examinada por el HoloLens. Una vez que un usuario se queda con el juego, puede aumentar la dificultad según le conste.

### <a name="adding-input-for-hand-gestures"></a>Adición de entrada para gestos de mano

HoloLens entrada base solo tiene dos gestos: [Air Tap y Bloom](../../design/gaze-and-commit.md#composite-gestures). Los usuarios no necesitan recordar matices contextuales ni una lista de gestos específicos que hacen que la interfaz de la plataforma sea versátil y fácil de aprender. Aunque el sistema solo puede exponer estos dos gestos, HoloLens como dispositivo es puede realizar un seguimiento de dos manos a la vez. Nuestra oda a Lunar Lander es una [aplicación inmersiva, lo que significa que podemos ampliar el conjunto base de gestos para aprovechar las dos manos y agregar nuestros propios medios de forma perfectamente táctil para la navegación del módulo lunar.

Al volver al esquema de control original, es necesario resolver **para la rotación y la rotación.** La advertencia es la rotación en el nuevo contexto agrega un eje adicional (técnicamente dos, pero el eje Y es menos importante para el aterrizaje). Los dos movimientos de envío distintos se prestan de forma natural para asignarse a cada mano:

![Pulse y arrastre el gesto para girar la lander en los tres ejes.](images/module-handdrag.gif)<br>
*Pulse y arrastre el gesto para girar la lander en los tres ejes.*

**Empuje**

La maneta de la máquina original de la galería asignada a una escala de valores, cuanto más alta se movió la maneta, más se aplicó a la nave. Un matiz importante que se debe señalar aquí es cómo el usuario puede quitarse el control y mantener un valor deseado. Podemos usar de forma eficaz el comportamiento de pulsar y arrastrar para lograr el mismo resultado. El valor de la estocada comienza en cero. El usuario pulsa y arrastra para aumentar el valor. En ese momento, podrían dejar ir para mantenerlo. Cualquier cambio en el valor del gesto de pulsar y arrastrar sería el delta del valor original.

**Rotación**

Esto es un poco más complicado. Tener botones holográficos de "girar" para pulsar permite disfrutar de una experiencia perfecta. No hay un control físico para aprovechar, por lo que el comportamiento debe ser la manipulación de un objeto que representa el lander o con el propio lander. Se ha llegado a un método mediante pulsar y arrastrar, que permite a un usuario "insertar y extraer" de forma eficaz en la dirección a la que quiere que se enfrenta. Cada vez que un usuario pulsa y mantiene presionado, el punto en el espacio donde se inició el gesto se convierte en el origen de la rotación. Al arrastrar desde el origen, se convierte la diferencia de la traducción de la mano (X,Y,Z) y se aplica a la diferencia de los valores de rotación del lander. O más sencillamente, al arrastrar <-> izquierda a la *derecha, <->* hacia abajo, hacia delante <-> hacia atrás en espacios gira el envío en consecuencia.

Puesto que HoloLens realizar un seguimiento de las dos manos, la rotación se puede asignar a la derecha mientras la izquierda controla el movimiento. La delicaduración es el factor que impulsa el éxito en este juego. La *sensación* de estas interacciones es la prioridad más alta absoluta. Especialmente en el contexto de la sensibilidad táctil. Un envío que reaccione demasiado rápido sería difícil de dirigir, mientras que uno demasiado lento requeriría que el usuario "insertara y extraera" en el envío durante un período de tiempo difícilmente largo.

### <a name="adding-input-for-game-controllers"></a>Adición de entrada para controladores de juego

Aunque los gestos de mano en el HoloLens proporcionan un método nuevo de control de detalle, todavía hay una cierta falta de comentarios táctiles "verdaderos" que se obtienen de los controles análogos. La conexión de un controlador de juego de Xbox nos permite recuperar esta sensación de integridad física al mismo tiempo que aprovecha los palos de control para mantener el control más preciso.

Hay varias maneras de aplicar el esquema de control relativamente directo al controlador de Xbox. Puesto que estamos intentando estar lo más cerca posible de la configuración original de la galería, **la** opción Desencadene se asigna mejor al botón de desencadenador. Estos botones son controles análogos,  lo que significa que tienen estados de encendido y apagado más que sencillos, en realidad responden al grado de presión que se les coloca. Esto nos proporciona una construcción similar a la del **impulsor de la iniciativa**. A diferencia del juego original y el gesto de la mano, este control cortará la presión del envío una vez que un usuario deje de presionar el desencadenador. Sigue otorgando al usuario el mismo grado de delicaduración que el juego original.

![El control de posición izquierdo se asigna a Yaw y Roll, mientras que el dedo derecho se asigna a Pitch and Roll](images/thumbsticksidebyside.gif)<br>
*El control de posición izquierdo se asigna a yaw y roll; el control de posición derecho se asigna al lanzamiento y lanzamiento*

Los controladores dobles se prestan de forma natural para controlar la rotación de envíos. Desafortunadamente, hay tres ejes en los que el envío puede girar y dos huellas digitales que admiten dos ejes. Este error de coincidencia significa que un control de un eje es un control de un solo control; o hay superposición de ejes para las huellas digitales. La solución anterior terminó sintiéndose "rota", ya que las huellas digitales mezclan de forma inherente sus valores X e Y locales. La última solución requería algunas pruebas para encontrar qué ejes redundantes son los más naturales. En el ejemplo final se *usa yaw* and *roll* (ejes Y y X) para el control de posición izquierdo, y *pitch* and *roll* (ejes Z y X) para el control de posición derecho. Esto parecía lo más natural, ya que *el lanzamiento* parece emparejarse bien de forma independiente *con yaw* y *pitch*. Como nota lateral, el uso de ambos dedos para el lanzamiento *también* duplica el valor de rotación; es bastante divertido tener bucles lander do.

En esta aplicación de ejemplo se muestra cómo el reconocimiento espacial y la sensibilidad táctil pueden cambiar significativamente una experiencia gracias a las Windows Mixed Reality de entrada extensibles de la aplicación. Aunque Lunar Lander puede estar a punto de llegar a los 40 años, los conceptos expuestos con ese pequeño octágono con las manos seguirán vivo para siempre. Al mirar el futuro, ¿por qué no mirar el pasado?

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar scripts y requisitos previos para la aplicación de ejemplo Módulo lunar en [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también

* [MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tabla periódica de los elementos 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)