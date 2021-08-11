---
title: 'Case study - Looking through holes in your reality (Caso práctico: mirar por un agujero en tu realidad)'
description: En este caso práctico se explica la implementación del efecto "ventana mágica" en HoloLens, lo que permite al usuario ver detrás de las paredes, debajo del suelo y en las aperturas virtuales.
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, ventana mágica, paralax
ms.openlocfilehash: 0769d8a7bd2b5bdf1ef1fe50f1bbcd2f284b8503bf66b8fdb09b2206b716ea65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228187"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Case study - Looking through holes in your reality (Caso práctico: mirar por un agujero en tu realidad)

Cuando los usuarios piensen en la realidad mixta y en lo que pueden hacer con Microsoft HoloLens, normalmente se adhieren a preguntas como "¿Qué objetos puedo agregar a mi habitación?". o "¿Qué puedo usar sobre mi espacio?" Me gustaría resaltar otra área que puede considerar, básicamente un truco mágico, con la misma tecnología para examinar o a través de objetos físicos reales a su alrededor.

## <a name="the-tech"></a>La tecnología

Si ha trabajado con los universos a medida que atraviesan las paredes de **[RoboRaid,](https://www.youtube.com/watch?v=Hf9qkURqtbM)** ha desbloqueado una caja fuerte en **[fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)** o ha tenido la suerte de ver el hangar infinito unSC en la experiencia de Halo 5 en E3 en **[2015,](https://www.youtube.com/watch?v=QDw5QjDtFy8)** ha visto de lo que estoy hablando. En función de su imaginación, este truco visual se puede usar para colocar huecos temporales en el yeso o para ocultar mundos bajo un panel de suelo flexible.

![RoboRaid agrega canalizaciones tridimensionales y otra estructura detrás de las paredes, visibles solo a través de los huecos creados a medida que los contratornadores se separan.](../develop/unity/images/roboraid-640px.png)

RoboRaid agrega canalizaciones tridimensionales y otra estructura detrás de las paredes, visibles solo a través de los huecos creados a medida que los contratornadores se separan.

Con uno de estos hologramas únicos en HoloLens, una aplicación puede proporcionar la sensación de contenido detrás de las paredes o a través del suelo de la misma manera que la realidad se presenta a través de una ventana real. Muévese a la izquierda y podrá ver lo que esté en el lado derecho. Más cerca, y puede ver un poco más de todo. La principal diferencia es que los huecos reales le permiten pasar, mientras que el suelo no le permitirá atravesar ese contenido holográfico mágico. (Agregaré una tarea al trabajo pendiente).

## <a name="behind-the-scenes"></a>Entre bambalinas

Este truco es una combinación de dos efectos. En primer lugar, el contenido holográfico se ancla al mundo mediante "anclajes espaciales". El uso de delimitadores para hacer que el contenido esté "bloqueado por el mundo" significa que lo que está viendo no se aleja visualmente de los objetos físicos cercanos, incluso cuando se mueve o el sistema de asignación espacial subyacente actualiza su modelo 3D de la sala.

En segundo lugar, ese contenido holográfico se limita visualmente a un espacio muy específico, por lo que solo se puede ver a través del hueco en la realidad. Esa oclusión es necesaria para requerir la búsqueda a través de un hueco lógico, una ventana o una puerta, lo que vende el truco. Sin que algo bloquee la mayor parte de la vista, una fisuración en el espacio de una dimensión secreta de Perossic podría parecerse a un dinosaurio mal colocado.

![No se trata de una captura de pantalla real, sino de una ilustración de cómo se ve el secreto bajo el mundo de Mr Basics 101 en HoloLens. El gabinete negro no aparece, pero puede ver el contenido a través de un hueco virtual. (Al mirar a través de un dispositivo real, el suelo parecería desaparecer aún más porque los ojos se centran a una distancia más larga como si no hubiera ni siquiera allí).](images/origamiholecomposited-640px.png)

No se trata de una captura de pantalla real, sino de una ilustración de cómo se ve el secreto bajo el mundo de [mr Basics 101](../develop/unity/tutorials/holograms-101.md) en HoloLens. El gabinete negro no aparece, pero puede ver el contenido a través de un hueco virtual. (Al mirar a través de un dispositivo real, el suelo parecería desaparecer aún más porque los ojos se centran a una distancia más larga como si no hubiera ni siquiera allí).

### <a name="world-locking-holographic-content"></a>Contenido holográfico de bloqueo mundial

En Unity, hacer que el contenido holográfico permanezca bloqueado es tan fácil como agregar un componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

El componente WorldAnchor ajustará constantemente la posición y la rotación de su GameObject (y, por tanto, cualquier otra cosa debajo de ese objeto en la jerarquía) para mantenerlo estable en relación con los objetos físicos cercanos. Al crear el contenido, cándalo de forma que el pivote raíz del objeto se centre en este hueco virtual. (Si el pivote del objeto está profundo en la pared, sus pequeños retoques en la posición y la rotación serán mucho más perceptibles y es posible que el hueco no tenga un aspecto muy estable).

### <a name="occluding-everything-but-the-virtual-hole"></a>Oclusión de todo menos el hueco virtual

Hay varias maneras de bloquear selectivamente la vista a lo que está oculto en las paredes. La más sencilla aprovecha el hecho de que HoloLens una pantalla aditiva, lo que significa que los objetos totalmente negros aparecen invisibles. Puede hacerlo en Unity sin realizar ningún sombreador o trucos de material especiales: solo tiene que crear un material negro y asignarlo a un objeto que incluye cuadros en el contenido. Si no le gusta realizar el modelado 3D, solo tiene que usar una serie de objetos Quad predeterminados y superponerse ligeramente. Hay una serie de inconvenientes en este enfoque, pero es la manera más rápida de conseguir que algo funcione y conseguir que una prueba de concepto de baja fidelidad funcione es excelente, aunque sospeche que podría querer refactorizarlo más adelante.

Un inconveniente importante del enfoque anterior de la "caja negra" es que no se fotografió bien. Aunque el efecto puede parecer perfecto a través de la presentación de HoloLens, las capturas de pantalla que se tomen mostrarán un objeto negro grande en lugar de lo que queda de la pared o el suelo. El motivo es que el hardware físico y las capturas de pantalla de hologramas compuestos y la realidad son diferentes. Vamos a desviarnos un momento en algunas matemáticas falsas...

*Alerta matemática falsa. Estos números y fórmulas están diseñados para ilustrar un punto, no para ser cualquier tipo de métrica precisa.*

Lo que se ve a través de HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

Lo que se ve en capturas de pantalla y vídeo:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

En inglés: lo que se ve a través de HoloLens es una combinación sencilla de realidad oscura (como a través de gafas de sol) y los hologramas que la aplicación quiere mostrar. Pero cuando se toma una captura de pantalla, la imagen de la cámara se combina con los hologramas de la aplicación según el valor de transparencia por píxel.

Una manera de solucionar este problema es cambiar el material de la "caja negra" para que solo escriba en el búfer de profundidad y ordenar con todos los demás materiales opacos. Para obtener un ejemplo de esto, consulte el archivo [WindowOcclusion.shader en MixedRealityToolkit en GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Las líneas pertinentes se copian aquí:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Tenga en cuenta que la línea "Desplazamiento 50, 100" es para tratar problemas no relacionados, por lo que probablemente tendría sentido dejar eso fuera).

La implementación de un material de oclusión invisible como ese permitirá que la aplicación dibuje un cuadro que sea correcto en la pantalla y en las capturas de pantalla de realidad mixta. En el caso de los puntos adicionales, puede intentar mejorar aún más el rendimiento de ese cuadro si hace cosas inteligentes para dibujar incluso menos píxeles invisibles, pero eso realmente puede entrar en los problemas y normalmente no será necesario.

![Este es el secreto de los conceptos básicos de MR 101 a medida que Unity lo dibuja, excepto las partes externas del cuadro de oclusión. Tenga en cuenta que el pivote para el sub mundo está en el centro de la caja, lo que ayuda a mantener el hueco lo más estable posible con respecto a su planta real.](images/underworld-occluded-640px.png)

Este es el secreto bajo el mundo de [Mr Basics 101](../develop/unity/tutorials/holograms-101.md) a medida que Unity lo dibuja, excepto las partes externas del cuadro de oclusión. Tenga en cuenta que el pivote para el sub mundo está en el centro de la caja, lo que ayuda a mantener el hueco lo más estable posible con respecto a su planta real.

## <a name="do-it-yourself"></a>Hágalo usted mismo

¿Tiene HoloLens y desea probar el efecto por sí mismo? Lo más fácil que puede hacer (no es necesario codificar) es instalar la aplicación gratuita de Visor 3D y, a continuación, cargar el archivo download [the.fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) que he proporcionado en GitHub para ver un modelo de flor en la sala. Cárbalo en HoloLens, y puede ver la sensación en el trabajo. Cuando está delante del modelo, solo puede ver en el pequeño hueco: todo lo demás es invisible. Mire el modelo desde cualquier otro lado y desaparece por completo. Use los controles de movimiento, rotación y escala de Visor 3D para colocar el hueco virtual en cualquier superficie vertical en la que pueda pensar para generar algunas ideas.

![Al ver este modelo en el editor de Unity, se mostrará una caja negra grande alrededor de la maceta. En HoloLens, el cuadro desaparece, lo que da lugar a un efecto de ventana mágica.](images/magicwindowflowerpotineditor.png)

Al ver este modelo en el editor de Unity, se mostrará una caja negra grande alrededor de la maceta. En HoloLens, el cuadro desaparece, lo que da lugar a un efecto de ventana mágica.

Si desea compilar una aplicación que use esta técnica, consulte el tutorial mr [basics 101](../develop/unity/tutorials/holograms-101.md) en el tutorial [Mixed Reality tutoriales](../develop/unity/tutorials.md). El capítulo 7 termina con una explosión en el suelo que revela un sub mundo oculto (como se indicó anteriormente). Quién que los tutoriales tenían que ser desarroba?

Estas son algunas ideas sobre dónde puede tomar esta idea a continuación:
* Piense en formas de hacer que el contenido dentro del hueco virtual sea interactivo. Permitir que los usuarios tengan algún impacto más allá de sus paredes puede mejorar realmente la sensación de asociar que este truco puede proporcionar.
* Piense en formas de volver a ver los objetos en áreas conocidas. Por ejemplo, ¿cómo puede colocar un hueco holográfico en la mesa de café y ver el suelo debajo de él?

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Ingeniero de software sénior @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también
* [MR Basics 101: proyecto completo con dispositivo](../develop/unity/tutorials/holograms-101.md)
* [Sistemas de coordenadas](../design/coordinate-systems.md)
* [Delimitadores espaciales](../design/spatial-anchors.md)
* [Asignación espacial](../design/spatial-mapping.md)
