---
title: 'Caso práctico: uso de sonido espacial en RoboRaid'
description: El sonido espacial es una de las características más emocionantes de Microsoft HoloLens, lo que permite a los usuarios percibir qué está ocurriendo en torno a ellos cuando los objetos no están a la vista.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, sonido espacial, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, CPU
ms.openlocfilehash: 95650ea7097f16d257c80c11443b84936bece435
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847544"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Caso práctico: uso de sonido espacial en RoboRaid

En este artículo se describen los desafíos a los que se enfrenta el equipo de experiencia de Microsoft HoloLens al crear audio para el [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) de primera persona de realidad mixta.

## <a name="the-tech"></a>La tecnología

El [sonido espacial](spatial-sound.md) es una de las características más emocionantes de Microsoft HoloLens, lo que permite a los usuarios percibir lo que sucede en torno a ellos cuando los objetos no se encuentran en la línea de visión.

En RoboRaid, el uso más obvio y eficaz del sonido espacial es avisar al jugador de algo que ocurre fuera de su visión del periférico. Por ejemplo, el violador puede entrar en cualquiera de las paredes digitalizadas de la habitación. Si no está orientado a la ubicación en la que está escribiendo, puede que se lo pierda. Para avisarle de esta invasión, oirá un poco de audio procedente del punto en el que está introduciendo el incumplimiento, lo que le permite saber que debe actuar rápidamente para detenerlo.

## <a name="behind-the-scenes"></a>Entre bambalinas

Crear sonido espacial para aplicaciones de HoloLens es tan nuevo y único que los problemas pueden ser difíciles de resolver, ya que no hay proyectos pasados a los que hacer referencia. Afortunadamente, estos ejemplos de los desafíos de audio que nos enfrentamos al hacer RoboRaid le ayudarán a crear audio para sus propias aplicaciones.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenga en cuentan el uso de la CPU

El sonido espacial puede ser exigente en la CPU. En el caso de una experiencia ocupada como RoboRaid, era fundamental mantener el número de instancias de sonido espacial en menos de ocho en un momento dado. Normalmente, era tan sencillo como establecer el límite de instancias para diferentes eventos de audio. Se eliminan todas las instancias que se producen después de alcanzar el límite. Por ejemplo, cuando se genera drones, sus Screams se limitan a tres instancias en un momento dado. Considerar solo cuatro drones se puede generar a la vez, hay tres screamss, ya que no hay forma de que su cerebro pueda realizar un seguimiento de los muchos eventos de audio de sonido similar. Esto liberó recursos para otros eventos de sonido espacial, como explosiones de enemigo o enemigos en preparación para disparar.

### <a name="rewarding-a-successful-dodge"></a>Recompensar una sobreexposición correcta

El mecánico de dodging es una de las mecánicas de juego más importantes de RoboRaid y también algo que pensamos que era verdaderamente exclusiva de la experiencia de HoloLens. Por lo tanto, queríamos realizar grandes sobreexposicións en el reproductor. Obtuvimos el Doppler "Whizz-by" para que suene bastante atractivo en el desarrollo. Inicialmente, mi plan era usar un bucle y manipularlo en tiempo real mediante el volumen, el paso y el filtro. La implementación de esto iba a ser muy elaborada. Antes de confirmar los recursos para compilar esto, creamos un prototipo barato con un recurso con el efecto Doppler que preparamos en solo para averiguar cómo creía. Nuestro desarrollo de talentos lo hizo de modo que este recurso Whizz se reproduciría exactamente el 0,7 segundo antes de que el proyectil pase por los oídos del jugador y los resultados se sentían sorprendentes. No es necesario decir que se ha reparado la solución más compleja y se ha implementado el prototipo.

*(Para obtener más información sobre la creación de un recurso de audio con el efecto Doppler integrado, vea [100 Whooshes en 2 minutos](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/)).* 
<br>
![Dodging correctamente las recompensas de un enemigo en el jugador con un sonido Whizz satisfactorio.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Deszanjar sonidos ineficaces

Originalmente, habíamos querido jugar un sonido de explosión detrás del jugador una vez que ha sobrepasado correctamente el proyectil del enemigo, pero hemos decidido deshacerse por varios motivos. En primer lugar, no se sienta tan efectivo como Whizz-by SFX que usamos para la inexposición. En el momento en que el proyectil llega a una pared detrás, se habría producido algo más en el juego que enmascararía ese sonido. En segundo lugar, no teníamos colisiones en el piso, por lo que no pudimos reproducir la explosión cuando el proyectil alcanzó el piso en lugar de las paredes. Y, por último, el costo de CPU del sonido espacial. El enemigo de Elite Scorpion (uno que puede rastrear dentro de la pared) tiene un ataque especial que alcanza los ocho proyectiles. No solo hizo que un gran desorden en la combinación, sino que también presentaba entrecortados, porque hacía que la CPU estuviera demasiado duro.

### <a name="communicating-a-hit"></a>Comunicar una visita

Un problema interesante que hemos encontrado en HoloLens era lo difícil que era comunicar de forma eficaz que se había alcanzado un reproductor. Lo que hace que una experiencia de realidad mixta sea correcta es la sensación de que se está produciendo la historia. Esto significa que debe creer que está lidiando una invasión del robot extranjero en su propia habitación.

Obviamente, los jugadores no sentirán nada cuando se alcancen, por lo que tuvimos que encontrar una manera de convencer al jugador de que ha sucedido algo mal. En los juegos convencionales, es posible que vea una animación que le permita saber que el personaje ha tenido un golpe, o que la pantalla puede parpadear en rojo y que el carácter podría resultar un poco. Dado que estos tipos de indicaciones no funcionan en una experiencia de realidad mixta, decidimos combinar la indicación visual con un sonido exagerado que indica que ha sacado el daño. He creado un gran sonido y lo hemos destacado en la combinación de que ha sobrepuesto todo. A continuación, para que se resalte aún más, hemos agregado un breve sonido de advertencia como si se hubiera receptora un subproceso nuclear. 
<br>
![Cuando se alcanza un jugador en RoboRaid, se ve una indicación visual, pero también se obtiene una señal de audio exagerada que indica que han sufrido daños.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obtener sonido grande de pequeños altavoces

Los oradores de HoloLens son pequeños y ligeros para adaptarse a las necesidades del dispositivo, por lo que no se puede esperar que escuche demasiado bajo. De forma similar al desarrollo para dispositivos smartphones o dispositivos de juegos de mano, los diseñadores y Composers de sonido deben tener en cuenta el contenido de la frecuencia de su audio. Siempre se diseñan sonidos o se escribe música con un intervalo de frecuencia completo porque la utilización de auriculares es una opción para los usuarios. Sin embargo, para garantizar la compatibilidad con los hablantes de HoloLens, ejecuto una prueba ocasionalmente colocando un EC en el patrón de cualquier DAW en el que estoy trabajando. La configuración de ECUALIZAción está formada por un filtro de paso alto de alrededor de 600 Hz a 700 Hz (no demasiado pronunciada) y un filtro de paso bajo alrededor de 10 000 (con pendiente). Esto le dará una idea aproximada de cómo se reproducirán los sonidos en el dispositivo.

Si se basa en graves para dar la sensación de cambiar el valor de cuerda en la música, es posible que la música pierda por completo el sentido de la raíz al aplicar esta configuración de EC. Para solucionarlo, agregué otra capa al graves que es una octava superior (con algunos armónicos ricos) y la combina para obtener el sentido de la raíz. A veces, el uso de la distorsión para aumentar el valor de los armónicos proporcionará suficiente contenido de frecuencia en el intervalo superior para que nuestro cerebro piense que hay algo debajo. Esto es así para SFX como impactos, explosiones o sonidos para momentos especiales, como los ataques de superusuario de un jefe. En realidad, no puede confiar en el low-end para dar al jugador una sensación de impacto o peso. Al igual que con la música, el uso de distorsión para dar una información a algo muy útil.

### <a name="making-your-audio-cues-stand-out"></a>Destaque las señales de audio

Naturalmente, todos los miembros del equipo querían bombasticr música, armas de alto volumen y explosiones de loco; pero también querían ser capaces de oír VoiceOver o cualquier otra pista de audio crítica del juego.

En un juego de consola con una gama completa de frecuencia, tiene más opciones para dividir las frecuencias en función de la importancia del sonido. En el caso de RoboRaid, se limitaba el número de intervalos de frecuencias que podía curvar de los sonidos. Si usa un filtro de paso bajo y una curva demasiado en el extremo superior del espectro, no quedará nada en el sonido porque no hay mucho más bajo.

Para que el sonido RoboRaid sea tan grande como en el dispositivo, tuvimos que reducir el intervalo dinámico de toda la experiencia y realizar un uso extensivo de la misma creando una jerarquía clara de importancia para los diferentes tipos de sonidos. Configuro la cadena de-2 dB a-6 dB en función de la importancia. Personalmente no me gusta la untonía obvia en los juegos, por lo que he dedicado mucho tiempo a optimizar el tiempo de transición y salida y la cantidad de atenuación del volumen. Se configuran buses independientes para sonido espacial, sonido no espacial, VO y bus seco sin reverberación para música. Después, creamos buses de alta prioridad, críticos y no críticos para que los recursos se configuraran para ir a los buses adecuados.

Espero que los profesionales de audio salgan del trabajo en sus propias aplicaciones mientras trabajaba en RoboRaid. No puedo esperar para ver (y oír) el contenido de las personas con talento ajenos a Microsoft para HoloLens.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Un truco que he descubierto para realizar determinados eventos (como explosiones) suena "más grande", al igual que están llenando el salón, era crear un recurso mono para el sonido espacial y combinarlo con un recurso estéreo 2D para reproducirlo en 3D. Lleva cierto ajuste, ya que tener demasiada información en el contenido estéreo disminuirá la direccionalidad de los recursos mono. Sin embargo, el hecho de obtener el equilibrio tiene como resultado grandes sonidos que permitirán a los jugadores activar sus cabezales en la dirección correcta.

Puede probar los sonidos de gran tamaño con los recursos de audio siguientes:

**Escenario 1**
1. Descargue [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) y establézcalo para que se reproduzca a través de un sonido espacial y asígnelo a un evento.
2. Descargue [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) y establézcalo en reproducción en estéreo 2D y asígnelo al mismo evento que el anterior. Dado que estos recursos se normalizan en Unity, atenuar el volumen de ambos recursos para que no se recorte.
3. Reproducir ambos sonidos juntos. Mueva el dedo para sentir cómo suena espacial.

**Escenario 2**
1. Descargue [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) y establézcalo para reproducirlo a través de un sonido espacial y asignarlo a un evento.
2. Reproduzca este recurso y compárelo con el evento del escenario 1.
3. Pruebe un equilibrio diferente de archivos mono y estéreo.

## <a name="see-also"></a>Consulte también

* [Sonido espacial](spatial-sound.md)
* [RoboRaid para Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
