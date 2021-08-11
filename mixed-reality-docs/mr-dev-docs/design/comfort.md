---
title: Comodidad
description: Durante la visualización natural, el sistema visual humano se basa en varias fuentes de información o "indicaciones" para interpretar las formas 3D y la posición relativa de los objetos.
author: erickjpaul
ms.author: erpau
ms.date: 06/25/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, design, comfort, HoloLens 2, HoloLens (1st gen), mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit, locomotion
ms.openlocfilehash: 87cf45628a530da65d9feb29556afb7c4a8ee1d3f13385cbf521d2621ac0c2ae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226440"
---
# <a name="comfort"></a>Comodidad

Durante la visualización natural, el sistema visual humano se basa en varias fuentes de información o "indicaciones" para interpretar las formas 3D y las posiciones relativas de los objetos. Algunas señales se basan en un solo ojo o en una señal monocular, e incluyen:

* [Perspectiva lineal](https://en.wikipedia.org/wiki/Perspective_(graphical))
* [Tamaño conocido](https://en.wikipedia.org/wiki/Size#Perception_of_size)
* Oclusión
* [Desenfoque de profundidad de campo](https://en.wikipedia.org/wiki/Depth_of_field)
* [Acomodación](https://en.wikipedia.org/wiki/Accommodation_(eye)). 

Otras señales se basan en ambos ojos o en señales binoculares, e incluyen:

* [Vergencia](https://en.wikipedia.org/wiki/Vergence): son esencialmente las rotaciones relativas de los ojos necesarias para mirar un objeto.
* [Disparidad binocular](https://en.wikipedia.org/wiki/Stereopsis): es el patrón de diferencias entre las proyecciones de la escena en la parte posterior de los dos ojos. 

Para garantizar la máxima comodidad de los cascos de realidad virtual, es importante crear y presentar el contenido de una manera que imite las señales del mundo real. Desde una perspectiva física, también es importante diseñar contenido que no requiera realizar movimientos agotadores del cuello o de los brazos. En este artículo, analizaremos las consideraciones clave que hay que tener en cuenta para lograr estos objetivos.

## <a name="vergence-accommodation-conflict"></a>Conflicto entre la vergencia y la acomodación

Para ver claramente los objetos, los humanos deben [acomodar la vista](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), o enfocar los ojos, según la distancia del objeto. Al mismo tiempo, la rotación de ambos ojos debe [converger](https://en.wikipedia.org/wiki/Convergence_(eye)) en la distancia del objeto para evitar que aparezcan imágenes dobles. En la visualización natural, la vergencia y la acomodación están vinculadas. Al ver algo cercano (por ejemplo, una mosca cerca de la nariz), los ojos se cruzan y se acomodan a un punto cercano. Por el contrario, si ve algo en el infinito óptico (aproximadamente a partir de 6 m o más lejos para la visión normal), las líneas de visión de los ojos pasan a ser paralelas y los cristalinos se acomodan al infinito. 

En la mayoría de cascos de realidad virtual, los usuarios siempre acomodan la vista a la distancia focal de la pantalla para obtener una imagen nítida, pero la convergen en la distancia del objeto de interés para obtener una sola imagen. Cuando los usuarios acomodan la vista a varias distancias y la convergen en estas, el vínculo natural entre las dos señales se rompe y esto puede causar fatiga o molestias visuales.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="guidance-for-holographic-devices"></a>Instrucciones para dispositivos holográficos

Las pantallas de HoloLens están fijadas a una distancia óptica de aproximadamente 2 m del usuario. Por lo tanto, los usuarios siempre deben acomodar la vista aproximadamente a 2 m para obtener una imagen clara en el dispositivo. Los desarrolladores de aplicaciones pueden guiar el lugar en el que convergen los ojos de los usuarios al colocar contenido y hologramas en varias profundidades. La incomodidad que se crea cuando la vergencia y la acomodación entran en conflicto se puede evitar o minimizar al mantener el contenido en el que los usuarios convergen lo más cerca posible de 2 m. Por ejemplo, en una escena con mucha profundidad, puede colocar las áreas de interés a unos 2 m del usuario cuando sea posible. Cuando el contenido no se pueda colocar aproximadamente a 2 m, la incomodidad que se crea debido al conflicto entre la vergencia y la acomodación es mayor cuando la mirada del usuario cambia constantemente entre varias distancias. En otras palabras, es mucho más cómodo ver un holograma estático que se mantiene a 50 cm de distancia que mirar un holograma a 50 cm que se acerca y se aleja del usuario con el tiempo.

![Distancia óptima para colocar hologramas respecto al usuario.](images/distanceguiderendering-950px.png)<br>
*Distancia óptima para colocar hologramas respecto al usuario*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Procedimientos recomendados para HoloLens (1.ª generación) y HoloLens 2

Para obtener la máxima comodidad, **la zona óptima para la colocación del holograma está entre 1,25 y 5 m**. En cada caso, los diseñadores deben intentar estructurar las escenas de contenido para animar a los usuarios a interactuar a 1 m o más lejos del contenido (por ejemplo, para ajustar los [parámetros de tamaño del contenido y la ubicación predeterminada](gaze-and-commit.md)). 

Aunque en ocasiones es posible que sea necesario mostrar el contenido más cerca de 1 m, se recomienda no presentar ningún holograma más cerca de 40 cm. Por lo tanto, es recomendable empezar a **atenuar el contenido a 40 cm y colocar un plano de recorte de representación a 30 cm** para evitar cualquier objeto más cercano.

Los objetos que se mueven al fondo tienen más probabilidad que los objetos estáticos de producir incomodidad debida al conflicto entre la vergencia y la acomodación. Del mismo modo, requerir que los usuarios cambien rápidamente entre un enfoque cercano y uno lejano (por ejemplo, debido a que un holograma emergente requiere una interacción directa) puede provocar molestias y fatiga visuales. Así pues, se debe prestar **atención adicional para minimizar la frecuencia con la que los usuarios ven contenido que se mueve en profundidad o cuando cambian rápidamente de enfoque entre hologramas cercanos y lejanos**. 

### <a name="other-considerations-for-hololens-2-and-near-interaction-distances"></a>Otras consideraciones adicionales para HoloLens 2 y las distancias de interacción cercanas

Al diseñar contenido para la interacción directa (cercana) en HoloLens 2 o **en cualquier aplicación en la que el contenido se deba colocar más cerca de 1 m, se debe prestar más atención para garantizar la comodidad del usuario**. La probabilidad de que se produzcan molestias debidas al conflicto entre la vergencia y la acomodación aumenta exponencialmente con una distancia de visualización menor. Asimismo, los usuarios pueden experimentar un mayor desenfoque al ver el contenido a distancias de interacción cercanas, por lo que se recomienda probar el contenido representado tanto en la zona de ubicación óptima del holograma como más cerca (menos de 1 m hasta el plano de recorte) para garantizar que sigue siendo claro y cómodo de ver. 

**Es recomendable crear una "asignación de profundidad" para las aplicaciones en función de la cantidad de tiempo que se espera que un usuario vea el contenido que está cerca (menos de 1 m) y que se mueve en profundidad**. Un ejemplo es evitar poner al usuario en esas situaciones más del 25 % del tiempo. Si se supera la asignación de profundidad, se recomienda realizar pruebas de usuario minuciosas para garantizar que la experiencia sigue siendo cómoda. 

En general, también se recomienda realizar pruebas minuciosas para asegurarse de que todos los requisitos de interacción (por ejemplo, la velocidad de movimiento, la capacidad de alcance, etc.) a distancias de interacción cercanas sigan resultando cómodos para los usuarios. 

### <a name="guidance-for-immersive-devices"></a>Instrucciones para dispositivos envolventes

En el caso de los dispositivos envolventes, se siguen aplicando las instrucciones y los procedimientos recomendados para HoloLens, pero los valores específicos de la zona de confort cambian en función de la distancia focal a la pantalla. En general, las distancias focales a estas pantallas están entre 1,25 m y 2,5 m. En caso de duda, evite la representación de objetos de interés que estén demasiado cerca de los usuarios y, en su lugar, intente mantener la mayor parte del contenido a 1 m o más de distancia.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distancia interpupilar y desplazamiento vertical

Al ver el contenido digital en cascos de realidad virtual (HMD), la posición de los ojos de un espectador con respecto a la posición de visualización del contenido digital es fundamental. En concreto, la distancia interpupilar ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) y el desplazamiento vertical (VO) son importantes para ver con comodidad el contenido digital en HMD. 

La IPD hace referencia a la distancia entre las pupilas o el centro de los ojos de un individuo. El VO hace referencia al posible desplazamiento vertical del contenido digital que se muestra en cada ojo en relación con el eje horizontal de los ojos del espectador (en particular, NO es lo mismo que el desplazamiento horizontal o la disparidad binocular). La falta de coincidencia de uno o ambos factores en un usuario concreto puede empeorar los efectos de las molestias que puede causar el conflicto entre la vergencia y la acomodación. Sin embargo, también pueden producirse molestias cuando se minimiza el conflicto de V-A (por ejemplo, para el contenido que se muestra en la distancia focal de 2 m de HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Instrucciones para dispositivos holográficos

#### <a name="hololens-1st-gen"></a>HoloLens (1.ª generación)

En el caso de HoloLens (1.ª generación), la IPD se calcula y se establece durante la [calibración](/hololens/hololens-calibration) del dispositivo. Para los nuevos usuarios de un dispositivo que ya está configurado, se debe ejecutar la calibración o establecer la IPD manualmente. El VO depende completamente del ajuste del dispositivo. En concreto, para minimizar el VO, el dispositivo debe reposar sobre la cabeza de un usuario, de modo que las pantallas estén niveladas con el eje de sus ojos. 

#### <a name="hololens-2"></a>HoloLens 2

En el caso de HoloLens 2, la IPD se calcula y se establece durante la [calibración](/hololens/hololens-calibration) del dispositivo o de los ojos. En el caso de los nuevos usuarios de un dispositivo que ya está configurado, se debe ejecutar la calibración para asegurarse de que la IPD está establecida correctamente. El VO se corrige automáticamente en HoloLens 2. 

### <a name="guidance-for-immersive-devices"></a>Instrucciones para dispositivos envolventes

Los HMD de Windows Mixed Reality no tienen calibración automática para IPD o VO. La IPD se puede establecer manualmente en el software (en la configuración del Portal de realidad mixta, consulte [Calibración](/hololens/hololens-calibration)); igualmente, algunos HMD tienen un control deslizante mecánico que permite al usuario ajustar la separación de las lentes hasta una posición cómoda que coincide aproximadamente con su IPD. 

## <a name="rendering-rates"></a>Velocidades de representación

Las aplicaciones de realidad mixta son únicas, ya que los usuarios pueden moverse libremente por el mundo e interactuar con el contenido virtual como si fueran objetos reales. Para mantener esta impresión, es fundamental representar los hologramas para que parezcan estables en el mundo y tengan una animación suave. La representación a un [mínimo de 60 fotogramas por segundo (FPS)](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ayuda a lograr este objetivo. Existen algunos dispositivos de Mixed Reality que admiten la representación en velocidades de fotogramas superiores a 60 FPS y, para estos dispositivos, se recomienda realizar la representación a una velocidad de fotogramas superior para proporcionar una experiencia de usuario óptima.

**Más detalles**

Para dibujar hologramas para que parezca que [son estables en el mundo real o virtual](../develop/platform-capabilities-and-apis/hologram-stability.md), las aplicaciones deben representar las imágenes desde la posición del usuario. Dado que la representación de imágenes lleva tiempo, HoloLens y otros dispositivos de Windows Mixed Reality predicen dónde se encontrará la cabeza de un usuario cuando se muestren las imágenes en las pantallas. Este algoritmo de predicción es una aproximación. El hardware y los algoritmos de Windows Mixed Reality ajustan la imagen representada para que tenga en cuenta la discrepancia entre la posición de la cabeza prevista y la real. Este proceso hace que la imagen que ve el usuario se muestre como si se representara desde la ubicación correcta y los hologramas parecen estables. Las actualizaciones funcionan mejor para los pequeños cambios en la posición de la cabeza y no pueden tener en cuenta completamente algunas de las diferencias de las imágenes representadas, como las causadas por el efecto de paralaje de movimiento.

**Al representar hologramas a una velocidad de fotogramas mínima de 60 FPS, permite crear hologramas estables de dos formas:**
1. Al reducir la aparición de interrupciones, que se caracterizan por un movimiento desigual e imágenes dobles. El movimiento de hologramas más rápido y las velocidades de representación más bajas se asocian a interrupciones más pronunciadas. Por lo tanto, esforzarte para mantener siempre 60 FPS (o la velocidad de representación máxima del dispositivo) te ayudará a evitar las interrupciones en los hologramas en movimiento.
2. Al minimizar la latencia general. En un motor con un subproceso de juego y otro de representación que se ejecutan de forma sincrónica, la ejecución a 30 FPS puede agregar 33,3 ms de latencia adicional. Al reducir la latencia, se reduce el error de predicción y se aumenta la estabilidad del holograma.

**Análisis de rendimiento**

Hay diferentes herramientas que se pueden usar para realizar pruebas comparativas de la velocidad de fotogramas de la aplicación, como por ejemplo:
* GPUView
* Depurador de gráficos de Visual Studio
* Generadores de perfiles integrados en motores 3D, como Frame Debugger en Unity

## <a name="self-motion-and-user-locomotion"></a>Automovimiento y locomoción del usuario

La única limitación es el tamaño del espacio físico. Si quieres permitir que los usuarios se muevan más en el entorno virtual de lo que pueden en sus salas reales, se debe implementar una forma de movimiento puramente virtual. Sin embargo, el movimiento virtual continuado que no coincide con el movimiento físico real del usuario a menudo puede provocar mareos. Esto se debe a que las *indicaciones visuales* del movimiento que realiza uno mismo provenientes del *mundo virtual* entran en conflicto con las [indicaciones vestibulares](https://en.wikipedia.org/wiki/Vestibular_system) del *mundo real*.

Afortunadamente, tenemos algunas sugerencias para implementar la locomoción del usuario que pueden ayudar a evitar el problema:
* Debe otorgar siempre al usuario el control de sus movimientos, ya que el automovimiento inesperado es especialmente problemático.
* Recuerde que los seres humanos son muy sensibles a la dirección de la gravedad. Por lo tanto, se deben evitar especialmente los movimientos verticales no iniciados por el usuario.

### <a name="guidance-for-holographic-devices"></a>Instrucciones para dispositivos holográficos

Un método para permitir que el usuario se mueva a otra ubicación en un entorno virtual de gran tamaño es dar la impresión de que está moviendo un objeto pequeño en la escena. Este efecto se puede lograr de la siguiente manera:
   1. Proporciona una interfaz en la que el usuario pueda seleccionar un punto del entorno virtual al que quiera moverse.
   2. Tras la selección, reduce la representación de la escena a un disco alrededor del punto deseado.
   3. Mientras se mantiene el punto seleccionado, permite al usuario moverlo como si fuera un objeto pequeño. A continuación, el usuario puede acercar la selección a sus pies.
   4. Una vez se anule la selección, reanuda la representación de toda la escena.

### <a name="guidance-for-immersive-devices"></a>Instrucciones para dispositivos envolventes

El enfoque del dispositivo holográfico anterior no funciona tan bien en un dispositivo envolvente porque requiere que la aplicación represente un gran vacío negro u otro entorno predeterminado mientras se mueve el "disco". Este tratamiento interrumpe la sensación de inmersión. Un truco para la locomoción del usuario en un casco envolvente es el enfoque de "parpadeo". Esta implementación proporciona al usuario control sobre su movimiento y una breve impresión de movimiento, pero hace que sea tan breve que el usuario tiene menos probabilidades de sentirse desorientado por el automovimiento puramente virtual:
   1. Proporciona una interfaz en la que el usuario pueda seleccionar un punto del entorno virtual al que quiere moverse.
   2. Una vez realizada la selección, comienza un rápido movimiento simulado (100 m/s) hacia esa ubicación mientras se atenúa rápidamente la representación.
   3. Vuelve a atenuar la representación después de finalizar la traslación.

## <a name="heads-up-displays"></a>Indicadores en pantalla

En los videojuegos de tiros en primera persona, los indicadores en pantalla (HUD) presentan directamente en la pantalla y de forma persistente información como el estado del jugador, mapas en miniatura e inventarios. Los HUD funcionan bien para mantener al jugador informado sin que tenga que interrumpir la experiencia del juego. En las experiencias de realidad mixta, los HUD pueden resultar bastante incómodos y deben adaptarse al contexto más envolvente. En concreto, es probable que resulten incómodos aquellos HUD que permanecen bloqueados de forma rígida a la orientación de la cabeza del usuario. Si una aplicación requiere un HUD, te recomendamos que la bloques en el *cuerpo* en lugar de en la cabeza. Este tratamiento se puede implementar como un conjunto de pantallas que se desplazan de manera inmediata con el usuario, pero que no giran con la cabeza del usuario hasta que se alcanza un umbral de rotación. Una vez que se realiza la rotación, el HUD puede reorientarse para presentar la información en el campo visual del usuario. Evite la implementación de la rotación y la traslación del HUD 1:1 basadas en los movimientos de la cabeza del usuario.

## <a name="text-legibility"></a>Legibilidad del texto

Una legibilidad del texto óptima puede ayudar a reducir la fatiga ocular y mantener la comodidad del usuario, especialmente en las aplicaciones o escenarios que requieren que los usuarios lean mientras usan un HMD. La legibilidad del texto depende de varios factores, entre los que se incluyen:
* Propiedades de visualización, como la densidad de píxeles, el brillo y el contraste. 
* Propiedades de la lente, como la aberración cromática
* Propiedades del texto o la fuente, como el grosor, el espaciado, las serifas y el color de la fuente o el fondo.  

En general, se recomienda probar aplicaciones específicas para mejorar la legibilidad y definir tamaños de fuente lo más grandes posible para lograr una experiencia cómoda. Puede encontrar instrucciones más detalladas para dispositivos holográficos y envolvente en nuestras páginas [Tipografía](typography.md) y [Texto en Unity](../develop/unity/text-in-unity.md).

## <a name="holographic-frame-considerations"></a>Consideraciones sobre el marco holográfico

En cuanto a las experiencias de realidad mixta con objetos grandes o muchos objetos, es fundamental tener en cuenta la cantidad de movimiento de cabeza y cuello necesaria para interactuar con el contenido. Las experiencias pueden dividirse en tres categorías en términos de movimiento de la cabeza: 
* **Horizontal** (de lado a lado)
* **Vertical** (arriba y abajo)
* **Envolvente** (horizontal y vertical)
 
Siempre que sea posible, limite la mayoría de las interacciones con las categorías horizontal o vertical; lo ideal es que la mayoría de las experiencias tengan lugar en el centro del marco holográfico, para que el usuario mantenga la cabeza en una posición neutra. Igualmente, evite las interacciones que hagan que el usuario tenga que mover constantemente la vista a una posición de la cabeza no natural (por ejemplo, que siempre tenga que mirar hacia arriba para acceder a una interacción del menú clave).

![La región óptima del contenido es de 0 a 35 grados por debajo del horizonte](images/optimal-field-of-view-2.png).<br>
*La región óptima del contenido es de 0 a 35 grados por debajo del horizonte*.

El movimiento horizontal de la cabeza es más para las interacciones frecuentes, mientras que los movimientos verticales se deben reservar para eventos poco comunes. Por ejemplo, una experiencia que implique una escala de tiempo horizontal larga debe limitar el movimiento vertical de la cabeza para las interacciones (como mirar hacia abajo un menú).

Considere la posibilidad de promover el movimiento del cuerpo completo, en lugar de simplemente la cabeza. Para ello, coloque objetos alrededor del espacio del usuario. Las experiencias con objetos móviles o de gran tamaño deben prestar especial atención al movimiento de la cabeza, sobre todo cuando requieren un movimiento frecuente a lo largo de los ejes horizontal y vertical.

## <a name="gaze-direction"></a>Dirección de la mirada

Para evitar la fatiga ocular y en el cuello, el contenido debe diseñarse de modo que se evite el movimiento excesivo de ojos y cuello.
* **Evita** ángulos de mirada superiores a 10 grados por encima del horizonte (movimiento vertical).
* **Evita** ángulos de mirada superiores a 60 grados por debajo del horizonte (movimiento vertical).
* **Evite** rotaciones del cuello superiores a 45 grados desde el centro (movimiento horizontal).

Se considera que el ángulo de mirada óptimo (en reposo) está entre 10 y 20 grados por debajo del horizonte, ya que la cabeza tiende a inclinarse ligeramente hacia abajo, especialmente durante las actividades.

## <a name="arm-positions"></a>Posiciones de los brazos

Los usuarios pueden acumular fatiga muscular en los casos en los que deben mantener una mano levantada a lo largo de una experiencia. Así mismo, pueden encontrar agotador el hecho de tener que realizar gestos de pulsación en el aire de forma repetida durante largos períodos de tiempo. Por lo tanto, es recomendable diseñar experiencias que eviten la necesidad de realizar gestos de manera constante y repetida. Este objetivo puede lograrse mediante la incorporación de pausas breves y al ofrecer una combinación de gestos y voz para interactuar con la aplicación.

## <a name="see-also"></a>Consulta también
* [Gaze](gaze-and-commit.md)
* [Estabilidad de hologramas](../develop/platform-capabilities-and-apis/hologram-stability.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Marco holográfico](holographic-frame.md)
* [Calibración](/hololens/hololens-calibration)
