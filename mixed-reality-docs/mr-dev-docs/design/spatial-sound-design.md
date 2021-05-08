---
title: Uso de sonido espacial en aplicaciones de realidad mixta
description: El sonido espacial es una herramienta eficaz para la accesibilidad, la accesibilidad y el diseño de la experiencia de usuario en aplicaciones de realidad mixta.
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, sonido espacial, diseño, estilo, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, gestos, interacciones, atenuación
ms.openlocfilehash: d51fbdf16d7186c386f124c773f75dacc8c157fd
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489215"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Uso del sonido en aplicaciones de realidad mixta

Puede usar sonido para informar y reforzar el modelo mental del usuario del estado de la aplicación. Use la espacialización, cuando corresponda, para colocar sonidos en el mundo de la realidad mixta. Al conectar el auditor y el objeto visual de esta manera, profundiza la naturaleza intuitiva de las interacciones y aumenta la confianza del usuario.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>Cuándo agregar sonidos

Las aplicaciones de realidad mixta suelen tener una mayor necesidad de sonido que las aplicaciones 2D, debido a su falta de una interfaz táctil. Agregue sonidos cuando informe al usuario o refuerce las interacciones.

### <a name="inform-and-reinforce"></a>Informar y reforzar

* En el caso de los eventos que el usuario no inicia, como las notificaciones, use sonido para informar al usuario de que se ha producido un cambio.
* Las interacciones pueden tener varias fases. Use sonido para reforzar las transiciones de fase.

Consulte los ejemplos siguientes de interacciones, eventos y características de sonido sugeridas.

### <a name="exercise-restraint"></a>Ejercicio de restricción

Los usuarios no tienen una capacidad ilimitada de información de audio.
* Cada sonido debe comunicar información específica y valiosa.
* Cuando la aplicación reproduce un sonido para informar al usuario, reduzca temporalmente el volumen de otros sonidos.
* Para los sonidos de mantener el puntero del botón (consulte la siguiente información), agregue un retraso de tiempo para evitar que se desencadene un sonido excesivo.

### <a name="dont-rely-solely-on-sounds"></a>No se base únicamente en sonidos

Los sonidos que se usan bien son valiosos para los usuarios. Pero asegúrese de que la aplicación se puede uso incluso con el sonido desactivado.
* Los usuarios pueden tener dificultades auditivas.
* La aplicación se puede usar en un entorno ruidoso.
* Los usuarios pueden tener problemas de privacidad u otros motivos para deshabilitar el audio del dispositivo.

## <a name="how-to-sonify-interactions"></a>Cómo sonificar interacciones

Los tipos de interacción en la realidad mixta incluyen gestos, manipulación directa y voz. Use las siguientes características sugeridas para seleccionar o diseñar sonidos para estas interacciones.

### <a name="gesture-interactions"></a>Interacciones de gestos

En realidad mixta, los usuarios pueden interactuar con botones mediante un mouse. Las acciones de botón suelen producirse cuando el usuario suelta en lugar de presionar el botón para dar al usuario la oportunidad de cancelar la interacción. Use sonidos para reforzar estas fases. Para ayudar a los usuarios a dirigirse a botones lejanos, considere también la posibilidad de usar un sonido de puntero al mantener el puntero.
* Los sonidos con botón deben ser un "clic" corto y táctil.<br/>Ejemplo: [MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Los sonidos de botón "descomprimir" deben tener una sensación táctil similar. Un tono más alto que el sonido de la presión refuerza la sensación de finalización.<br/>Ejemplo: [MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* En el caso de los sonidos de mantener el puntero, considere la posibilidad de usar un sonido sutil y no amenazante, como un sonido con frecuencia baja o un fuerte.

### <a name="direct-manipulation"></a>Manipulación directa

En HoloLens 2, el seguimiento de manos articulado admite la manipulación directa de elementos de la interfaz de usuario. Los sonidos son importantes cuando no hay ningún otro comentario físico.

Un *sonido de pulsación* de botón es importante porque el usuario no obtiene ninguna otra indicación cuando llega a la parte inferior del trazo de tecla. Los indicadores de sonido del viaje clave pueden ser pequeños, sutiles y ocluyen. Al igual que con las interacciones de gestos, las pulsaciones de botón deben obtener un sonido corto y táctil como un clic. Los despresores deben tener un sonido de clic similar, pero con un tono elevado.
* Ejemplo: [MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Ejemplo: [MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

Es difícil confirmar visualmente una acción de captura o lanzamiento. La mano del usuario a menudo estará en el camino de cualquier efecto visual y los objetos con forma dura carecen de un análogo visual real de "agarrar". Los sonidos pueden comunicar eficazmente interacciones de captura y liberación correctas.
* Las acciones de agarre deben tener un sonido táctil corto y ligeramente desenredado que le pida la idea de que los dedos se cierren alrededor de un objeto. A veces también hay un sonido "whoosh" que conduce al sonido de captura para comunicar el movimiento de la mano.<br/>Ejemplo: [MRTK_Move_Start.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Las acciones de lanzamiento deben obtener un sonido similarmente corto y táctil. Normalmente es menor que el sonido de agarre y en orden inverso, con un impacto y, a continuación, un "whoosh" para comunicar que el objeto se está asentando en su lugar.<br/>Ejemplo: [MRTK_Move_End.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Una *interacción* de dibujo debe obtener un sonido persistente en bucle con el volumen determinado por el movimiento de la mano del usuario. Debe guardarse en modo silencioso cuando la mano del usuario está todavía y más alta cuando la mano se mueve rápidamente.

### <a name="voice-interactions"></a>Interacciones de voz

Las interacciones de voz suelen tener elementos visuales sutiles. Use sonidos para reforzar las fases de interacción. Es posible que quiera usar sonidos más tonales para distinguirlos de los sonidos de gesto y de manipulación directa.

* Use un tono de sonido positivo para las confirmaciones *de comandos de voz*. Los tonos ascendentes y los intervalos de música principales son efectivos.
* Use un tono más corto y menos positivo para los errores de *comandos de voz.* Evite sonidos negativos. En su lugar, use un sonido más percusivo y neutro para comunicar que la aplicación está pasando de la interacción.
* Si la aplicación tiene una palabra de reactivación, use un tono corto y suave cuando el dispositivo *empiece a escuchar*. Use un sonido de bucle sutil mientras la aplicación *está escuchando.*

### <a name="notifications"></a>Notificaciones

Las notificaciones señalan los cambios de estado de la aplicación y otros eventos que el usuario no inició. Los cambios de estado pueden incluir finalizaciones de procesos, mensajes y llamadas telefónicas.

En realidad mixta, los objetos a veces se mueven fuera del campo de vista del usuario. Empareje *el movimiento de* objetos animados con un sonido espacializado que depende del tipo de objeto y la velocidad de movimiento.
* Ayuda a reproducir un sonido espacializado al final de una animación para informar al usuario de la nueva posición del objeto.
* Para los movimientos graduales, un sonido "whoosh" durante el movimiento ayuda al usuario a realizar el seguimiento del objeto.

*Los sonidos de* notificación de mensajes se pueden escuchar repetidamente, a veces en sucesión rápida. Es importante que no se destaen ni suenen. Los sonidos tonales positivos de rango medio son efectivos.

* Los sonidos de llamadas entrantes deben tener calidades similares a las de un teléfono móvil. Estos sonidos son frases en bucle que se reproducen hasta que el usuario responde a la llamada.
* La conexión de comunicación de voz y la desconexión deben tener un sonido breve y tonal. El sonido de conexión debe ser un tono positivo para indicar una conexión correcta. El sonido de desconexión debe ser un sonido neutro para indicar la finalización de la llamada.

## <a name="handle-spatialization"></a>Control de la espacialización

La espacialización usa micrófonos estéreo o altavoces para colocar sonidos en el mundo de la realidad mixta.

### <a name="which-sounds-to-spatialize"></a>Qué sonidos se espacializarán

Un sonido debe espacializarse cuando está asociado a un evento que tiene una ubicación espacial. Esto incluye la interfaz de usuario, voces de IA incorporadas e indicadores visuales.

Espacialice *los elementos de la* interfaz de usuario para ayudar a desasociar el "espacio" sónico del usuario limitando el número de sonidos estéreo que escucha. Las interacciones de manipulación, como tocar, agarrar y liberar, son más naturales cuando se espacializan los comentarios de audio. Tenga en cuenta la siguiente información sobre la atenuación de distancia para estos elementos.

Espacialice *los indicadores visuales* y las voces de inteligencia artificial *incorporadas* para informar intuitivamente a los usuarios cuando estas cosas están fuera del campo de visión.
    
En cambio, evite la espacialización para voces *de* IA sin caras y otros elementos que carecen de una ubicación espacial bien definida. La espacialización sin un elemento visual relacionado puede distraer a los usuarios para que piensen que hay un elemento visual que no pueden encontrar.

La espacialización incluye algún costo de CPU. Muchas aplicaciones tienen como máximo dos sonidos que se reproducen simultáneamente. En ese caso, el costo de la espacialización es probablemente insignificante. Puede usar el monitor de velocidad de fotogramas mrtk para controlar el impacto de agregar espacialización.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>Cuándo y cómo aplicar la atenuación basada en la distancia

En el mundo físico, los sonidos que están más lejos son más silenciosos. El motor de audio puede modelar esta atenuación en función de la distancia de origen. Use la atenuación basada en la distancia cuando comunique la información pertinente.

Las distancias a *los indicadores visuales,* *los hologramas animados* y otros sonidos informativos son relevantes para el usuario. Use la atenuación basada en la distancia para proporcionar indicaciones de forma intuitiva.

Ajuste la curva de atenuación de cada origen para que se ajuste al tamaño de los espacios del mundo de realidad mixta. La curva predeterminada del motor de audio suele estar pensada para espacios grandes (hasta la mitad del recorrido).

Los sonidos que *refuerzan las fases progresivas* de las acciones de botón y otras interacciones no deben aplicarse atenuación. Los efectos de reforzamiento de estos sonidos son más importantes que comunicar la distancia con el botón. Las variaciones pueden distraer, especialmente con los teclados, cuando se pueden escuchar varios clics de botón en sucesión.

### <a name="which-spatialization-technology-to-use"></a>Qué tecnología de espacialización se va a usar

Con auriculares o altavoces HoloLens, use tecnologías de espacialización basadas en la función de transferencia relacionada con la cabeza (HRTF). Estas tecnologías modela la propagación del sonido alrededor de la cabeza en el mundo físico. Incluso cuando una fuente de sonido está en el extremo de la cabeza, el sonido se propaga al oído lejano con alguna atenuación y retraso. El movimiento panorámico del hablante solo se basa en la atenuación y aplica la atenuación total en el oído izquierdo cuando los sonidos están en el lado derecho y al revés. Esta técnica puede ser poco cómoda para los agentes de escucha "normales" e inaccesible para los agentes de escucha que tienen discapacidad auditiva en un solo oído.

## <a name="next-steps"></a>Pasos siguientes

* [Uso de sonido espacial en Unity](../develop/unity/spatial-sound-in-unity.md)
* [Caso práctico de Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Caso práctico de HoloTour](case-study-spatial-sound-design-for-holotour.md)
