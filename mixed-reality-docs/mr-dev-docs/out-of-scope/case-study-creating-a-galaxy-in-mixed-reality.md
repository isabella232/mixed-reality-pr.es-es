---
title: 'Caso práctico: Creación de una galaxy en realidad mixta'
description: Obtenga información sobre la aplicación "Galaxy Explorer" y cómo se creó para microsft HoloLens y después de un sondeo de Twitter de 24 horas por parte de desarrolladores de la comunidad.
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, compartir su idea, caso práctico
ms.openlocfilehash: 5891fbc052c52cd90176214d1eff8ef019a2bcfc80dbd5264489deced0fb1664
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208088"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Caso práctico: Creación de una galaxy en realidad mixta

Antes Microsoft HoloLens enviar, preguntamos a nuestra comunidad de desarrolladores qué tipo de aplicación les gustaría ver una compilación de equipo interno con experiencia para el nuevo dispositivo. Se han compartido más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador fue una idea llamada [Galaxy Explorer.](../develop/unity/galaxy-explorer.md)

Andy Zibits, el director de arte del proyecto, y Karim Suscin, ingeniero de gráficos del equipo, hablan sobre el esfuerzo de colaboración entre el arte y la ingeniería que condujo a la creación de una representación precisa e interactiva de la galaxy Milky Way en Galaxy Explorer.

## <a name="the-tech"></a>La tecnología

Nuestro [equipo,](../develop/unity/galaxy-explorer.md#meet-the-team) que está integrado por dos diseñadores, tres desarrolladores, cuatro intérpretes, un productor y un evaluador, tenía seis semanas para crear una aplicación totalmente funcional que permitiría a los usuarios conocer y explorar la inmensidad y la diversidad de nuestra galaxy De la manera de la leche.

Queríamos aprovechar al máximo la capacidad de HoloLens para representar objetos 3D directamente en el espacio vivo, por lo que decidimos crear una galaxy de aspecto realista donde las personas puedan acercarse y ver estrellas individuales, cada una en sus propias historias.

En la primera semana de desarrollo, se han creado algunos objetivos para nuestra representación de la galaxy De la manera de la leche: era necesario tener profundidad, movimiento y sensación volumétrica, llena de estrellas que ayudarían a crear la forma de la galaxy.

El problema con la creación de una galaxy animada que tenía miles de millones de estrellas era que el gran número de elementos únicos que se necesitan actualizar sería demasiado grande por fotograma para que HoloLens animara con la CPU. Nuestra solución implicaba una combinación compleja de arte y ciencia.

## <a name="behind-the-scenes"></a>Entre bambalinas

Para permitir que los usuarios exploren estrellas individuales, nuestro primer paso fue averiguar cuántas partículas podríamos representar a la vez.

### <a name="rendering-particles"></a>Representación de partículas

Las CPU actuales son excelentes para procesar tareas en serie y hasta algunas tareas paralelas a la vez (en función de cuántos núcleos tengan), pero las GPU son mucho más eficaces para procesar miles de operaciones en paralelo. Sin embargo, dado que normalmente no comparten la misma memoria que la CPU, el intercambio de datos entre la CPU<>GPU puede convertirse rápidamente en un cuello de botella. Nuestra solución era crear una galaxy en la GPU y tenía que estar completamente en la GPU.

Iniciamos pruebas de esfuerzo con miles de partículas de punto en varios patrones. Esto nos permitió obtener la galaxy en HoloLens ver lo que funcionó y lo que no.

### <a name="creating-the-position-of-the-stars"></a>Creación de la posición de las estrellas

Uno de nuestros miembros del equipo ya había escrito el código de C# que generaría estrellas en su posición inicial. Las estrellas están en una elipse y su posición se puede describir mediante (**curveOffset**, **ellipseSize**, **elevation**) donde **curveOffset** es el ángulo de la estrella a lo largo de la elipse, **ellipseSize** es la dimensión de la elipse a lo largo de X y Z, y eleva la elevación adecuada de la estrella dentro de la galaxy. Por lo tanto, podemos crear un búfer[(ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)de Unity) que se inicializaría con cada atributo de estrella y lo enviaría a la GPU donde se encontraría durante el resto de la experiencia. Para dibujar este búfer, usamos [DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) de Unity, que permite ejecutar un sombreador (código en una GPU) en un conjunto arbitrario de puntos sin tener una malla real que represente la galaxy:

**Cpu:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**Gpu:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Comenzamos con patrones circulares sin procesar con miles de partículas. Esto nos dio la prueba que necesitamos de que podríamos administrar muchas partículas y ejecutarlas a velocidades de rendimiento, pero no estamos satisfechos con la forma general de la galaxy. Para mejorar la forma, hemos intentado varios patrones y sistemas de partícula con rotación. Inicialmente, eran promisorias porque el número de partículas y el rendimiento eran coherentes, pero la forma se interrumpió cerca del centro y las estrellas emitían externamente, lo que no era realista. Necesitamos una emisión que nos permita manipular el tiempo y hacer que las partículas se muevan de forma realista, cada vez más cerca del centro de la galaxy.

![Hemos intentado varios patrones y sistemas de partícula que giraban, como estos.](images/galaxy-patterns-500px.png)

Hemos intentado varios patrones y sistemas de partícula que giraban, como estos.

Nuestro equipo realizó algunas investigaciones sobre la forma en que funcionan las ramas e hicimos un sistema de partículas personalizado específicamente para la galaxy para que podamos mover las partículas sobre elipses en función de[la](https://en.wikipedia.org/wiki/Density_wave_theory)"teoría de onda de densidad", que teoriza que los brazos de una galaxy son áreas de mayor densidad pero en flujo constante, como un atfijo de tráfico. Parece estable y sólido, pero las estrellas se mueven dentro y fuera de los brazos a medida que se mueven por sus puntos suspensivos respectivos. En nuestro sistema, las partículas nunca existen en la CPU: generamos las tarjetas y las orientamos todas en la GPU, por lo que todo el sistema es simplemente el estado inicial + el tiempo. Ha progresado de la siguiente forma:

![Progresión del sistema de partícula con representación en GPU](images/spiral-galaxy-arms-500px.jpg)

Progresión del sistema de partícula con representación en GPU


Una vez que se agregan los puntos suspensivos suficientes y se establecen para girar, las ramas empezaron a formar "ramas" donde converge el movimiento de estrellas. El espaciado de las estrellas a lo largo de cada trazado elíptico recibió cierta aleatoriedad y cada estrella recibió un poco de aleatoriedad posicional agregada. Esto creó una distribución de aspecto mucho más natural del movimiento de estrella y la forma de los brazos. Por último, hemos agregado la capacidad de controlar el color en función de la distancia desde el centro.

### <a name="creating-the-motion-of-the-stars"></a>Creación del movimiento de las estrellas

Para animar el movimiento de estrella general, es necesario agregar un ángulo constante para cada fotograma y hacer que las estrellas se muevan a lo largo de sus puntos suspensivos a una velocidad radial constante. Este es el motivo principal para usar **curveOffset.** Esto no es técnicamente correcto, ya que las estrellas se moverán más rápido a lo largo de los lados largos de los puntos suspensivos, pero el movimiento general se notó bien.

![Las estrellas se mueven más rápido en el arco largo, más lento en los bordes.](images/ellipse-movement.jpg)

Las estrellas se mueven más rápido en el arco largo, más lento en los bordes.


Con eso, cada estrella se describe por completo por (**curveOffset**, **ellipseSize**, **elevation**, **Age**) donde **Age** es una acumulación del tiempo total que ha transcurrido desde que se cargó la escena.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

Esto nos permitió generar decenas de miles de estrellas una vez al principio de la aplicación y, a continuación, animamos un conjunto único de estrellas a lo largo de las curvas establecidas. Puesto que todo está en la GPU, el sistema puede animar todas las estrellas en paralelo sin costo alguno para la CPU.

![Este es el aspecto que tiene al dibujar quads en blanco.](images/drawing-white-quads-300px.jpg)

Este es el aspecto que tiene al dibujar quads en blanco.



Para convertir cada cara de cuatro caras en la cámara, hemos usado un sombreador de geometría para transformar cada posición de estrella en un rectángulo 2D en la pantalla que contendrá nuestra textura de estrella.

![Rombos en lugar de cuádros.](images/drawing-white-quads-300px.jpg)

Rombos en lugar de cuádros.


Dado que queríamos limitar el sobredesanado (número de veces que se procesará un píxel) tanto como sea posible, giramos los quads para que tengan menos superposición.

### <a name="adding-clouds"></a>Adición de nubes

Hay muchas maneras de obtener una sensación volumétrica con las partículas, desde la marcha de rayos dentro de un volumen hasta dibujar tantas partículas como sea posible para simular una nube. La marcha de rayos en tiempo real era demasiado costosa y difícil de crear, por lo que primero intentamos crear un sistema de impostores mediante un método para representar bosques en juegos, con una gran cantidad de imágenes 2D de árboles frente a la cámara. Cuando hacemos esto en un juego, podemos tener texturas de árboles representados desde una cámara que gira alrededor, guardar todas esas imágenes y, en tiempo de ejecución, seleccionar la imagen que coincida con la dirección de la vista. Esto no funciona bien cuando las imágenes son hologramas. La diferencia entre el ojo izquierdo y el derecho lo hace para que necesitemos una resolución mucho mayor, o simplemente parece plano, con alias o repetitivo.

En el segundo intento, intentamos tener tantas partículas como sea posible. Los mejores objetos visuales se lograron al dibujar aditivamente las partículas y desenfocarlas antes de agregarlas a la escena. Los problemas típicos con ese enfoque estaban relacionados con cuántas partículas podríamos dibujar en un solo momento y la cantidad de área de pantalla que cubren mientras se mantienen 60 fps. Desenfocar la imagen resultante para obtener esta sensación de nube suele ser una operación muy costosa.

![Sin textura, este es el aspecto que tendrían las nubes con una opacidad del 2 %.](images/clouds-without-texture-300px.jpg)

Sin textura, este es el aspecto que tendrían las nubes con una opacidad del 2 %.



Ser aditiva y tener una gran cantidad de ellos significa que tendríamos varios cuádros uno encima del otro, sombreando repetidamente el mismo píxel. En el centro de la galaxy, el mismo píxel tiene cientos de cuádros uno encima del otro y esto tenía un costo enorme al realizarse a pantalla completa.

Hacer nubes de pantalla completa e intentar desenfocarlas habría sido una mala idea, por lo que decidimos dejar que el hardware nos realizara el trabajo.

### <a name="a-bit-of-context-first"></a>Un poco de contexto en primer lugar

Al usar texturas en un juego, el tamaño de textura rara vez coincidirá con el área en la que queremos usarlo, pero podemos usar otro tipo de filtrado de textura para obtener la tarjeta gráfica para interpolar el color que queremos a partir de los píxeles de la textura[(filtrado](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)de textura). El filtrado que nos interesa es [el filtrado bilineal](/windows/win32/direct3d9/bilinear-texture-filtering) que calculará el valor de cualquier píxel mediante los 4 vecinos más cercanos.

![Original antes del filtrado](images/texture-1.png)

![Resultado después del filtrado](images/texture-2.png)

Con esta propiedad, vemos que cada vez que intentamos dibujar una textura en un área el doble de grande, desenfoca el resultado.

En lugar de representarse en una pantalla completa y perder esos milisegundos valiosos que podríamos estar gastando en otra cosa, se representa en una versión minúscula de la pantalla. A continuación, al copiar esta textura y extenderla por un factor de 2 varias veces, volveremos a la pantalla completa mientras desenfocamos el contenido del proceso.

![x3 vuelve a la resolución completa.](images/galaxy-resolutions-300px.png)

x3 vuelve a la resolución completa.



Esto nos permitió obtener la parte de la nube con solo una fracción del costo original. En lugar de agregar nubes a la resolución completa, solo pintamos 1/64 de los píxeles y simplemente se vuelve a extender la textura a la resolución completa.

![Izquierda, con una escala de 1/8 a resolución completa; y a la derecha, con 3 escalas con potencia de 2.](images/stars-upscaled-300px.jpg)

Izquierda, con una escala de 1/8 a resolución completa; y a la derecha, con 3 escalas con potencia de 2.


Tenga en cuenta que intentar pasar de 1/64 del tamaño al tamaño completo en una sola vez sería completamente diferente, ya que la tarjeta gráfica seguiría utilizando 4 píxeles en nuestra configuración para sombrear un área más grande y empezarían a aparecer artefactos.

A continuación, si agregamos estrellas de resolución completa con tarjetas más pequeñas, se obtiene la galaxy completa:

![Resultado casi final de la representación de la galaxy mediante estrellas de resolución completa](images/full-galaxy-500px.png)

Una vez que hemos estado en el camino correcto con la forma, agregamos una capa de nubes, intercambiamos los puntos temporales por los que pintamos en Photoshop y agregamos algún color adicional. El resultado fue una láctea de milky way por la que nuestros equipos de ingeniería y de arte se encontraban bien y cumplieron nuestros objetivos de profundidad, volumen y movimiento, todo ello sin que se imponía la CPU.

![Nuestra última milky way galaxy en 3D.](images/final-galaxy-500px.jpg)

Nuestra última milky way galaxy en 3D.


### <a name="more-to-explore"></a>Más información para explorar

Hemos abierto el código de la aplicación Galaxy Explorer y lo hemos puesto a [disposición](https://github.com/Microsoft/GalaxyExplorer) GitHub para que los desarrolladores lo compilen.

¿Le interesa obtener más información sobre el proceso de desarrollo de Galaxy Explorer? Consulte todas las actualizaciones anteriores del proyecto en el [Microsoft HoloLens canal de YouTube.](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Suscin es</b> un ingeniero de software y un entusiasta de los objetos visuales sofisticados. Fue ingeniero gráfico para Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> es un director de arte y un entusiasta del espacio que ha administrado el equipo de modelado en 3D para Galaxy Explorer y que busca aún más partículas.</td>
</tr>
</table>


## <a name="see-also"></a>Consulte también
* [Galaxy Explorer en GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Actualizaciones de proyectos de Galaxy Explorer en YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)