---
title: 'Caso práctico: Uso de sonido espacial en RoboRaid'
description: El sonido espacial es una de las características más interesantes de Microsoft HoloLens, lo que permite a los usuarios percibir lo que sucede a su alrededor cuando los objetos están fuera de la vista.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, sonido espacial, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, cpu
ms.openlocfilehash: f4a47fe119dffbd32d264cc8e21ae2b3ade7cfcccef8e7e18fbb4491783d0542
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209008"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Caso práctico: Uso de sonido espacial en RoboRaid

En este artículo se describen los desafíos a los que se enfrenta Microsoft HoloLens Experience Team al crear audio para el sonido de [roboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) en primera persona de realidad mixta.

## <a name="the-tech"></a>La tecnología

[El sonido](spatial-sound.md) espacial es una de las características más interesantes de Microsoft HoloLens, lo que permite a los usuarios percibir lo que sucede a su alrededor cuando los objetos no están en la línea de visión.

En RoboRaid, el uso más obvio y eficaz del sonido espacial es alertar al jugador de algo que sucede fuera de su visión periférico. Por ejemplo, el breacher puede entrar desde cualquiera de las paredes examinadas de la sala. Si no está frente a la ubicación en la que está entrar, es posible que la pierda. Para alertar de esta situación, escuchará un poco de audio distinto procedente de la entrada del usuario, lo que le permite saber que necesita actuar rápidamente para detenerlo.

## <a name="behind-the-scenes"></a>Entre bambalinas

La creación de sonido espacial para HoloLens aplicaciones es tan nueva y única que los problemas pueden ser difíciles de resolver porque no hay ningún proyecto pasado al que hacer referencia. Esperamos que estos ejemplos de los desafíos de audio a los que nos enfrentamos al crear RoboRaid le ayudarán a crear audio para sus propias aplicaciones.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenga en cuenta los impuestos de la CPU.

El sonido espacial puede ser exigente en la CPU. Para una experiencia ocupada como RoboRaid, era fundamental mantener el número de instancias de sonido espacial en menos de ocho en un momento dado. Normalmente, era tan fácil como establecer el límite de instancias para diferentes eventos de audio. Todas las instancias que se suceden después de alcanzar el límite se han alcanzado. Por ejemplo, cuando se generan drones, sus drones se limitan a tres instancias en un momento dado. Teniendo en cuenta que solo pueden generarse unos cuatro drones a la vez, hay muchas cosas, ya que el cerebro no puede realizar un seguimiento de tantos eventos de audio similares. Esto libera recursos para otros eventos de sonido espacial, como las explosións del adversario o los preparativos para el ataque.

### <a name="rewarding-a-successful-dodge"></a>Recompensa de un éxito de carreras

El mecanismo de cobertura es uno de los mecanismos de juego más importantes de RoboRaid y también algo que creemos que era realmente único para la experiencia HoloLens usuario. Por lo tanto, queríamos hacer que los éxitos de las carreras son muy satisfactorios para el jugador. Hemos conseguido que doppler "whizz-by" suene atractivo bastante pronto en el desarrollo. Inicialmente, mi plan era usar un bucle y manipularlo en tiempo real mediante volumen, tono y filtro. La implementación de esto sería muy elaborado. Antes de confirmar los recursos para compilar esto, creamos un prototipo económico con un recurso con el efecto Doppler recién creado para averiguar cómo se siente. Nuestro actor de desarrollo lo hizo para que este recurso de remolino se reproducira exactamente 0,7 segundos antes de que el proyecto pasara por la orida del jugador y los resultados se sintase increíble. No hace falta decir que hemos puesto en marcha la solución más compleja e implementado el prototipo.

*(Para obtener más información sobre cómo crear un recurso de audio con el efecto Doppler integrado, vea [100 Whooshes en 2 minutos).](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/)* 
<br>
![El hecho de que el proyecto de un adversario se dote correctamente recompensa al jugador con un sonido de llorón satisfactorio.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Tratamiento de sonidos ineficaces

Originalmente, queríamos reproducir un sonido de explosión detrás del jugador una vez que se ha atajado correctamente el proyecto adversario, pero decidimos hacer esto por varias razones. En primer lugar, no ha sido tan eficaz como el llorón de SFX que se usó para el viento. En el momento en que el proyecto alcanza una pared detrás de usted, habría ocurrido algo más en el juego que enmascararía ese sonido. En segundo lugar, no se produjo una colisión en el suelo, por lo que no pudimos hacer que la explosión se produjese cuando el projectile alcanzó el suelo en lugar de las paredes. Y, por último, estaba el costo de CPU del sonido espacial. El adversario de escorpión de la resistencia (uno que se puede arrastrar dentro de la pared) tiene un ataque especial que lanza unos ocho projectiles. No solo eso hizo que se creara un desastre enorme en la combinación, sino que también introdujo un crujido descomando porque estaba afectando demasiado a la CPU.

### <a name="communicating-a-hit"></a>Comunicación de una pulsación

Un problema interesante con el que nos encontramos en HoloLens era lo difícil que era comunicar eficazmente que se había alcanzado a un jugador. Lo que hace que una experiencia de realidad mixta sea correcta es la sensación de que la historia le está ocurriendo. Esto significa que tiene que pensar que está enfrentando a un robot robot en su propia sala.

Obviamente, los jugadores no se van a sentir nada cuando se les abate, por lo que hemos tenido que encontrar una manera de convencir al jugador de que les ha ocurrido algo malo. En los juegos convencionales, es posible que vea una animación que le permite saber que el carácter ha alcanzado un éxito, o que la pantalla podría parpadear en rojo y que el carácter podría gruñer un poco. Dado que estos tipos de indicaciones no funcionan en una experiencia de realidad mixta, hemos decidido combinar la indicación visual con un sonido desenlazado que indica que ha sufrido daños. He creado un sonido grande y lo he hecho tan destacado en la mezcla que lo ha achacado todo. A continuación, para que se destaúe aún más, agregamos un breve sonido de advertencia como si un sub se hubiera receptorado. 
<br>
![Cuando un reproductor recibe un impacto en RoboRaid, ve una indicación visual, pero también obtiene una indicación de audio que le indica que han sufrido daños.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obtención de un sonido grande de altavoces pequeños

HoloLens los altavoces son pequeños y ligeros para satisfacer las necesidades del dispositivo, por lo que no puede esperar que escuche demasiado de bajo nivel. De forma similar al desarrollo para teléfonos inteligentes o dispositivos de juegos de mano, los diseñadores de sonido y los compositores deben tener en cuenta el contenido de frecuencia de su audio. Siempre diseño sonidos o escribo música con un intervalo de frecuencia completo porque llevar cascos es una opción para los usuarios. Sin embargo, para garantizar la compatibilidad con HoloLens hablantes, en ocasiones se ejecuta una prueba colocando un EQ en el maestro de cualquier VEZ en la que esté trabajando. La configuración de EQ consta de un filtro de paso alto alrededor de 600 Hz a 700 Hz (no demasiado alto) y un filtro de paso bajo a unos 10 000 (escarpado). Esto debería darle una idea aproximada de cómo se reproducirán los sonidos en el dispositivo.

Si confía en los sonidos para dar la sensación de cambio de sonido en la música, es posible que la música pierda completamente la sensación de raíz al aplicar esta configuración de EQ. Para solucionar este problema, he agregado otra capa a la capa que es una octave más alta (con algunos armónicos enriquecidos) y la he combinado para obtener la sensación de raíz. A veces, el uso de distorsión para amperar los armónicos dará suficiente contenido de frecuencia en el intervalo superior para hacer que nuestro cerebro piense que hay algo debajo de él. Esto es así para SFX, como impactos, explosións o sonidos en momentos especiales, como los superataques de un jefe. Realmente no puede confiar en el bajo nivel para dar al jugador una sensación de impacto o peso. Al igual que con la música, el uso de distorsión para dar algún toque ha ayudado definitivamente.

### <a name="making-your-audio-cues-stand-out"></a>Destacar las indicaciones de audio

Por supuesto, todos los miembros del equipo querían música popular, ruidos fuertes y ruidosas. pero también querían poder escuchar la voz en voz o cualquier otra indicación de audio crítica para el juego.

En un juego de consola con toda la frecuencia, tiene más opciones para dividir las frecuencias en función de la importancia del sonido. Para RoboRaid, estaba limitado en el número de intervalos de frecuencias que podía curvar a partir de sonidos. Si usa un filtro de paso bajo y se curva demasiado desde el extremo superior del espectro, no le queda nada en el sonido porque no hay mucho bajo.

Para que RoboRaid suene lo más grande posible en el dispositivo, hemos tenido que reducir el intervalo dinámico de toda la experiencia y hemos hecho un uso extensivo del patín mediante la creación de una jerarquía clara de importancia para los distintos tipos de sonidos. He establecido el afijo de -2 dB a -6 dB en función de la importancia. Personalmente no me gusta el afijo obvio en los juegos, por lo que he dedicado mucho tiempo a ajustar el tiempo de entrada y salida de atenuación y la cantidad de atenuación del volumen. Configuramos bus independientes para sonido espacial, sonido no espacial, VO y bus sin reverberación para música. A continuación, creamos buss de alta prioridad, críticos y no críticos, por lo que los recursos se configuraron para ir a los bus adecuados.

I hope audio professionals out there will have as much fun and excitement working on their own apps as I did working on RoboRaid. No puedo esperar a ver (y escuchar) lo que los actores externos a Microsoft encontrarán para HoloLens.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Un truco que he descubierto para hacer que ciertos eventos (como las explosións) suenen "más grandes", como si llenaran la sala, era crear un recurso mono para el sonido espacial y mezclarlo con un recurso estéreo 2D, que se reproduciría en 3D. Se requiere cierta optimización, ya que tener demasiada información en el contenido estéreo disminuirá la direccionalidad de los recursos mono. Sin embargo, obtener el equilibrio correcto dará lugar a sonidos enormes que harán que los jugadores se desenlásen la cabeza en la dirección correcta.

Puede probar sonidos grandes usted mismo con los recursos de audio siguientes:

**Escenario 1**
1. Descargue [roboraid_enemy_explo_mono.wav y](images/roboraid-enemy-explo-mono.wav) establezca esta opción para reproducir el sonido espacial y asignarlo a un evento.
2. Descargue [roboraid_enemy_explo_stereo.wav y](images/roboraid-enemy-explo-stereo.wav) establezca para reproducir en estéreo 2D y asígnelo al mismo evento que antes. Dado que estos recursos se normalizan en Unity, atenuar el volumen de ambos recursos para que no se recorte.
3. Reproducir ambos sonidos juntos. Mueva la cabeza para sentir lo espacial que suena.

**Escenario 2**
1. Descargue [roboraid_enemy_explo_summed.wav y establezca](images/roboraid-enemy-explo-summed.wav) para reproducir a través del sonido espacial y asignarlo a un evento.
2. Reprodgue este recurso por sí mismo y compárelo con el evento del escenario 1.
3. Pruebe un equilibrio diferente de archivos mono y estéreo.

## <a name="see-also"></a>Consulte también

* [Sonido espacial](spatial-sound.md)
* [RoboRaid para Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
