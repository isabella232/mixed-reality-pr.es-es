---
title: 'Caso práctico: representación de personas en realidad mixta'
description: ¿Qué tipo de oportunidades surgen cuando no solo se crean elementos fantásticos, sino que se usan las capturas más realistas de entornos, objetos y personas en realidad mixta?
author: mavitazk
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, humanos, avatar, captura de realidad mixta, vídeo volumétrico
ms.openlocfilehash: db21b6b02ce76403c2c59e37384c1c1602d8a63e003a8b5b6601c5daf7b9c2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228566"
---
# <a name="case-study---representing-humans-in-mixed-reality"></a>Caso práctico: representación de personas en realidad mixta

James Turrell diseña con luz. Al entrar en su trabajo, se desenfoca la sensación de profundidad y enfoque. Las paredes parecen cercanas e infinitas, el brillo da paso a las sombras. Percepciones desconocidas diseñadas al equilibrar cuidadosamente el color de la luz y la luminosidad. [Turrell describe estos sentimientos](https://www.sculpture.org/documents/scmag02/nov02/turrell/turrell.shtml) como *"sentimiento* con los ojos", una manera de ampliar la comprensión de la realidad. Los mundos fantásticos, como los que turrell imagine, son herramientas eficaces para aprovechar nuestros sentidos, no a diferencia de los entornos envolventes de la realidad mixta actual.

![Wide Out: James Turrell (1998)](../develop/platform-capabilities-and-apis/images/wide-out-james-turrell.jpg)

## <a name="how-do-you-represent-complex-real-world-environments-in-mixed-reality"></a>¿Cómo se representan entornos complejos del mundo real en realidad mixta?

Representar el trabajo de Turrell en una experiencia envolvente supone un desafío atractivo. La iluminación, la escala y el audio espacial presentan oportunidades para representar su trabajo. Aunque el entorno geométrico de la exposición requeriría un modelado 3D relativamente sencillo, son secundarios para el enfoque del intérprete: el impacto de la luz en los sentidos.

El minimalismo sutorio de Turrell es la distinción de su trabajo, pero ¿qué ocurre si queremos representar una exposición con materiales más complejos en realidad mixta?

![Así: Ai Weicca (2013)](../develop/platform-capabilities-and-apis/images/bang-ai-weiwie.jpg)

En 2013, el intérprete Ai Weirn desveló un trabajo de arte enredado que incluye 886 infirecciones en la Bienal de Trías. [](https://www.designboom.com/art/ai-weiwei-bang-installation-at-venice-art-biennale-2013/) Cada uno de ellos provenía de una era en la que la inociación china era muy valorada, donde estos productos se habrían pasado entre generaciones. Los propios ambientes ( las complejidades de la bosque, la precisión de las piezas, su cuidadosa colocación) son fundamentales para el comentario de IA sobre la cultura moderna.

Los reencuentradores entregan el mensaje del intérprete a través de su autenticidad. Su representación realista es fundamental para la experiencia, lo que crea un desafío técnico: la creación de cada uno de los 886 ambientes a mano sería enormemente exhaustiva y costosa. ¿Cuánto tiempo se tardaría en modelar y colocarse? ¿Cómo se mantiene la autenticidad del material? Volver a crear estos objetos desde cero se convierte, de muchas maneras, en una interpretación de la propia ilustración. ¿Cómo se puede conservar la intención del intérprete?

## <a name="methods-of-capturing-mixed-reality-assets"></a>Métodos para capturar recursos de realidad mixta

La alternativa a crear algo desde cero es capturar lo real. A través de un conjunto cada vez más avanzado de métodos de captura, podemos desarrollar representaciones auténticas de cada uno de los tipos de recursos principales que se encuentran en la realidad mixta (entornos, objetos y personas).

Las amplias categorías van desde un vídeo 2D bien establecido hasta las formas más nuevas de vídeo volumétrico. En el caso de la exposición de Ai Weigrama, el examen (al que a menudo se hace referencia por su técnica fundamental, fotogrametría) se podría emplear durante la creación de la exposición, analizando cada uno de los propios ambientes. La captura de fotos y vídeos de 360° es otro método para virtualizar la experiencia mediante una cámara omnidireccional de alta calidad posicionada en toda la exposición. Con estas técnicas, se empieza a comprender el sentido de la escala, idealmente con los detalles suficientes para ver la constudencia de cada pieza. Todo esto mientras existe en un formato digital que permite nuevas vistas y perspectivas que no son posibles en la realidad.

![Vídeo de 2D a volumen](../develop/platform-capabilities-and-apis/images/2d-to-volumetric-video.png)

¿Qué tipo de oportunidades surgen cuando no solo se crean elementos fantásticos, sino que se usan las capturas más realistas de entornos, objetos y personas en realidad mixta? Explorar la superposición entre estos métodos ayuda a aclarar dónde se dirige el medio.

En entornos y objetos, el software de creación de imágenes de 360° está evolucionando para incluir elementos de fotogrametría. Al aislar la información de profundidad de las escenas, los vídeos avanzados de 360° ayudan a mitigar la sensación de tener la cabeza atascada en una lonja al mirar alrededor de una escena virtual.

Para las personas, surgen nuevos métodos que combinan y amplían la captura de movimiento y el examen: la captura de movimiento ha sido fundamental para llevar el movimiento humano detallado a efectos visuales y caracteres operísticos, mientras que el examen ha avanzado para capturar objetos visuales humanos detallados, como caras y manos. Con los avances en la tecnología de representación, un nuevo método denominado vídeo volumétrico se basa en estas técnicas, combinando información visual y de profundidad, para crear la próxima generación de capturas humanas en 3D.

## <a name="volumetric-video-and-the-pursuit-of-authentic-human-capture"></a>Vídeo volumétrico y la búsqueda de la captura humana autenticada

Los seres humanos son fundamentales para contar historias, en el sentido más literal: un humano hablando, realizando o como sujeto de la historia. Algunos de los momentos más envolventes y de apertura de los ojos de las primeras experiencias inmersivas de hoy en día son sociales. Desde compartir una experiencia de realidad mixta juntos en la sala de estar hasta ver a sus amigos en nuevos entornos. El elemento humano hace incluso la realidad más fantástica, una realidad.

![Mindshow in VR](../develop/platform-capabilities-and-apis/images/mindshow-in-vr-640px.jpg)

Los avatares de las experiencias envolventes permiten un nuevo tipo de relieve en la narración. Las aplicaciones más recientes están replanteando el concepto de propiedad del cuerpo virtual y configurando un salto generacional para eliminar la distancia entre las personas. Empresas como [Mindshow están](https://mindshow.com/) desarrollando herramientas creadoras que aprovechan avatares, lo que permite a los usuarios asumir roles y caracteres completamente nuevos. Otros están [explorando métodos](https://en.wikipedia.org/wiki/Uncanny_valley)de expresión de expresión, una oportunidad creadora potencialmente ilimitada de explorar la naturaleza (y la necesidad) de los atributos de tipo humano. En la actualidad, esta ausencia [](https://en.wikipedia.org/wiki/Uncanny_valley) de realismo ayuda a evitar el descafeinado valle de la sima humana junto con una gran cantidad de problemas técnicos para los desarrolladores diarios. Por estos motivos (y mucho más), es muy probable que los avatares no realistas se conviertan en el valor predeterminado para el futuro previsible. Sin embargo, aunque el realismo supone un desafío enorme para la realidad mixta, hay escenarios clave que requieren una representación autenticada de los seres humanos en *el espacio 3D.*

En Microsoft, un pequeño equipo que sale de Microsoft Research ha dedicado los últimos años a desarrollar un método para capturar personas a través de una forma de vídeo volumétrico. El proceso actual es similar a la producción de vídeo: en lugar de aplicar el movimiento a un recurso desasistido, es una grabación en 3D completa. El rendimiento y la imagen se capturan en tiempo real; no es el trabajo de un intérprete, es una representación auténtica. Y aunque la tecnología está empezando a expandirse en aplicaciones comerciales, las implicaciones del vídeo volumétrico son fundamentales para la visión de Microsoft de la informática [más personal.](https://www.youtube.com/watch?v=tcyj-_IEWt8)

![Vídeo volumétrico SIGGRAPH 2015](../develop/platform-capabilities-and-apis/images/volumetric-video-siggraph-2015.gif)

La captura humana auténtica desbloquea nuevas categorías únicas de experiencias en realidad mixta. Ver a alguien que reconozca, ya sea una celebridad, un compañero o un ser muy amada, crea una profundidad de insondabilidad nunca antes posible en un medio digital. Su cara, sus expresiones, el matiz en sus movimientos forman parte de lo que son. ¿Qué oportunidades se abren cuando podemos capturar estas calidades humanas en el espacio 3D?

En la actualidad, el equipo está presionando los límites del vídeo volumétrico centrándose en sectores como el entretenimiento y la educación: [Actiongram](https://www.microsoft.com/p/actiongram/9nblggh5ftmt) incluye personajes creativos y [celebridades](https://www.youtube.com/watch?v=BwWueXlsOrA) para crear historias de realidad mixta. [Destino: Marte muestra](https://www.jpl.nasa.gov/news/news.php?feature=6220), ahora en el Centro espacial de Nasa, un vídeo volumétrico del astronauta insóptico Buzz Aldrin. La experiencia permite a los visitantes recorrer la superficie de Marte con Buzz, ya que presenta la búsqueda de la colonización humana en Marte.

## <a name="humans-are-fundamental-to-mixed-reality"></a>Los seres humanos son fundamentales para la realidad mixta

Diseñar formas de hacer que estos vídeos parezcan naturales supone un desafío, pero uno en el que el equipo ve un potencial enorme. Y estas oportunidades se expandirán a medida que la tecnología sea más accesible y se mueva de las grabaciones a la captura en tiempo real.

[Holoportation es](https://www.microsoft.com/research/project/holoportation-3/) un trabajo de investigación que se basa en la misma tecnología fundamental, capturando de forma autenticada información visual y de profundidad, y representando el resultado en tiempo real. El equipo está explorando lo que significa la capacidad de representación humana realista para el futuro de las conversaciones y las experiencias compartidas. ¿Qué ocurre cuando se puede agregar a su entorno una captura tridimensional de alguien desde cualquier lugar del mundo?

![Futuro de la conversación](../develop/platform-capabilities-and-apis/images/girl-with-dress.jpg)

Desde la transformación en capas de un nuevo nivel de inmersión en aplicaciones cotidianas como Skype, hasta la transformación radical del concepto de reuniones digitales y viajes de negocios, el vídeo volumétrico abre escenarios únicos: un especialista que está prácticamente entrenando a médicos en un continente lejano o amigos digitales sentados en los divánes y en la sala. Agregar representaciones humanas auténticas a experiencias de realidad mixta dará forma radical al concepto de reuniones digitales y viajes de negocios.

Del mismo modo que el arte abstracto de James Turrell y el realismo crítico de Ai Weirrell ofrecen sus propios desafíos técnicos únicos, también lo hacen los métodos para representar a los humanos como avatares creativos y capturas realistas. Uno no se puede ignorar a la luz del otro y explorar el potencial de cada uno nos ayudará a comprender la interacción humana en este nuevo espacio.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Mark Vitazko" width="60" height="60" src="images/mark-vitazko.jpg"></td>
<td style="border-style: none"><b>Mark Vitazko</b><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>
