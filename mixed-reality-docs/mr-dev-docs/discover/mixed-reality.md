---
title: ¿Qué es Mixed Reality?
description: Debate sobre la realidad mixta, demostración del uso de dispositivos de AR y VR en el espectro de la realidad mixta.
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: Mixed Reality, holographic, AR, VR, MR, XR, augmented reality, virtual reality, explanation, case study, mixed reality headset, windows mixed reality headset, virtual reality headset, what is virtual reality, what is augmented reality
ms.localizationpriority: high
ms.openlocfilehash: 088bc9a978bd236069ddc1beab40387c607b906e
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634326"
---
# <a name="what-is-mixed-reality"></a>¿Qué es Mixed Reality?

La realidad mixta es la nueva ola en la informática seguida por sistemas centrales, equipos y smartphones. La realidad mixta es cada vez más popular entre consumidores y empresas.  Nos libera de las experiencias limitadas a una pantalla, al ofrecer interacciones instintivas con los datos de nuestros espacios cotidianos, entre nuestras cosas y con nuestros amigos.  Los exploradores en línea, por cientos de millones en todo el mundo, han experimentado realidad mixta a través de sus dispositivos portátiles.  La AR móvil ofrece las soluciones de realidad mixta más populares en la actualidad en las redes sociales. Es posible que los usuarios ni siquiera se den cuenta de que los filtros de AR que usan en Instagram son experiencias de realidad mixta.  Microsoft Mixed Reality tiene como cometido llevar todas estas experiencias de usuario al siguiente nivel, con una combinación de increíbles representaciones holográficas de personas, modelos 3D holográficos de alta fidelidad y el mundo real que los rodea.

![Apuntar y confirmar con las manos en HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

La realidad mixta es una mezcla de universos físicos y digitales, que permite interacciones 3D naturales e intuitivas entre personas, equipos y el ambiente. Esta nueva realidad se basa en la visión artificial, el procesamiento gráfico, las tecnologías de visualización, los sistemas de entrada y la informática en la nube. El término "realidad mixta" se introdujo originalmente en un documento de 1994 de Paul Milgram y Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)" (Una taxonomía de pantallas visuales de realidad mixta). En el documento se exploraba el concepto de *continuo de la virtualidad* y la taxonomía de las pantallas visuales. Desde entonces, la aplicación de realidad mixta ha ido más allá de las pantallas a fin de incluir lo siguiente:

* Comprensión del entorno: mapeo y anclajes espaciales.
* Comprensión humana: seguimiento de manos, seguimiento ocular y entrada de voz.
* Sonido espacial.
* Ubicaciones y posicionamiento en los espacios tanto físicos como virtuales.
* Colaboración en recursos 3D en espacios de realidad mixta.

![Imagen del espectro de la realidad mixta](images/mixedrealityspectrum-worlds.png)<br>
*Imagen: la realidad mixta es el resultado de fusionar el mundo físico con el mundo digital.*

<br>

---

## <a name="environmental-input-and-perception"></a>Entrada y percepción del entorno

En las últimas décadas, la relación entre personas y equipos ha seguido evolucionando por medio de los métodos de entrada.  Ha surgido una nueva disciplina, que se conoce como interacción entre humanos y equipos o HCI. La entrada humana ahora puede incluir teclados, mouse, entrada táctil, manuscrita, voz y seguimiento del esqueleto de Kinect.

Los avances en los sensores y la potencia de procesamiento crean nuevas percepciones informáticas de los entornos en función de los métodos de entrada avanzados. Es por esto que los nombres de las API en Windows que revelan la información del entorno se denominan [API de percepción](/uwp/api/Windows.Perception). Las entradas del ambiente pueden capturar: 

* la posición del cuerpo de una persona en el mundo físico ([seguimiento de la cabeza](../design/coordinate-systems.md)); 
* objetos, superficies y límites ([mapeo espacial](../design/spatial-mapping.md) y [comprensión de la escena](../design/scene-understanding.md)); 
* iluminación y sonido ambiente;
* reconocimiento de objetos;
* ubicaciones físicas.

<br>

![Diagrama de Venn que muestra las interacciones entre equipos, seres humanos y entornos](images/mixed-reality-venn-diagram-300px.png)<br> 
*Imagen: interacciones entre equipos, seres humanos y entornos.*

<br>

Una combinación de los tres elementos esenciales preparan el escenario donde crear verdaderas experiencias de realidad mixta:

* Procesamiento informático con tecnología de la nube
* Métodos de entrada avanzados
* Percepciones ambientales

A medida que nos movemos por el mundo físico, los movimientos se mapean en una realidad digital. Los límites físicos influyen en las experiencias de realidad mixta del mundo digital, como juegos o instrucciones basadas en tareas en una planta de fabricación. Con las entradas y percepciones ambientales, las experiencias comienzan a combinarse entre las realidades físicas y digitales.

<br>

---

## <a name="the-mixed-reality-spectrum"></a>Espectro de la realidad mixta

La realidad mixta combina los mundos físicos y digitales.  Estas dos realidades marcan los extremos polares de un espectro conocido como *continuo de la virtualidad*. Hacemos referencia a este espectro de realidades como el *espectro de realidad mixta*.  En un extremo del espectro, tenemos la realidad física en la que se encuentran las personas. En el otro extremo del espectro, tenemos la realidad digital correspondiente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realidad aumentada frente a virtual

La mayoría de los teléfonos móviles del mercado de hoy en día tienen poca o ninguna funcionalidad de percepción ambiental. Las experiencias que ofrecen estos teléfonos no pueden combinar la realidad física y la digital. 

Las experiencias que superponen gráficos, streamings de vídeo u hologramas el mundo físico se denominan "realidad aumentada". Las experiencias que tapan la visión para presentar una experiencia digital totalmente envolvente son de realidad virtual. Las experiencias que pueden realizar la transición entre realidades aumentadas y virtuales forman la realidad mixta, donde se puede:

* Colocar un objeto digital, como un holograma, en el mundo físico, como si estuviera presente físicamente.
* Estar presente personal y digitalmente en el mundo físico, en forma de avatar, para colaborar de manera asincrónica con otros usuarios en distintos momentos.
* En la realidad virtual, los límites físicos, como las paredes y el mobiliario, aparecen digitalmente dentro de la experiencia para que los usuarios eviten encontrarse con obstáculos físicos.

<br>

![Espectro de la realidad mixta](images/mixedrealityspectrum.png)<br>
*Imagen: Espectro de la realidad mixta*

<br>

Hoy en día, la mayoría de las experiencias de realidad aumentada y virtual representan un pequeño subconjunto del espectro mayor de realidad mixta. Windows 10 se ha creado pensando en todo el espectro y permite combinar representaciones digitales de personas, lugares y cosas con el mundo real.

## <a name="devices-and-experiences"></a>Dispositivos y experiencias

Hay dos tipos principales de dispositivos que proporcionan experiencias de Windows Mixed Reality:
1. Los **dispositivos holográficos** se caracterizan por la capacidad del dispositivo para colocar contenido digital en el mundo real como si estuviera ahí.
2. Los **dispositivos envolventes de VR** se caracterizan por la capacidad que tienen de crear una sensación de presencia, ya que bloquean el mundo físico y lo sustituyen por una experiencia digital totalmente envolvente.

<table>
<tr>
<th width="30%"> Característica</th><th width="35%"> Dispositivos holográficos</th><th width="35%"> Dispositivos envolventes</th>
</tr><tr>
<td><strong>Dispositivo de ejemplo</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Pantalla</strong></td><td> Visualización transparente. Permite al usuario ver el entorno físico cuando usa el casco.</td><td> Visualización opaca. Bloquea el entorno físico cuando se lleva el casco.</td>
</tr><tr>
<td><strong>Movimiento</strong></td><td> Movimiento de seis grados de libertad completo, rotación y traslación.</td><td> Movimiento de seis grados de libertad completo, rotación y traslación.</td>
</tr>
</table> 

> [!NOTE]
> Independientemente de si un dispositivo está anclado a un equipo independiente (a través de un cable USB o Wi-Fi) o no está anclado, no se refleja si es holográfico o envolvente. Las características que mejoran la movilidad suelen brindar mejores experiencias. Los dispositivos holográficos y envolventes se pueden estar anclados o no.

Las experiencias de realidad mixta son el resultado de los avances tecnológicos. Actualmente no hay ningún dispositivo que pueda ejecutar experiencias en todo el espectro. Windows 10 proporciona una plataforma de realidad mixta común para los desarrolladores y los fabricantes de dispositivos. Cualquier dispositivo dado de hoy en día puede admitir un intervalo específico dentro del espectro de realidad mixta. En el futuro, se esperan nuevos dispositivos con un intervalo más amplio: los dispositivos holográficos serán más envolventes, y los dispositivos envolventes serán más holográficos.

<br>

![Tipos de dispositivos en el espectro de realidad mixta](images/Final_WhatIsMixedReality07.png)<br>
*Imagen: lugar en el que existen los dispositivos en el espectro de realidad mixta*

Como desarrollador de aplicaciones o juegos, ¿qué tipo de experiencia quiere crear? Las experiencias normalmente tienen como destino un punto específico o una parte del espectro. Deberá tener en cuenta las funcionalidades de los dispositivos de destino. Las experiencias que dependen del mundo físico se ejecutarán mejor en HoloLens.

* **Hacia la izquierda (realidad casi física).** Los usuarios permanecen presentes en su realidad física y no se les hace creer que han abandonado esa realidad.
* **En el centro (realidad totalmente mixta).** Estas experiencias combinan el mundo real y el mundo digital. Por ejemplo, en la película [Jumanji](https://en.wikipedia.org/wiki/Jumanji), la estructura física de la casa en la que tuvo lugar la trama se combinó con un ambiente selvático.
* **Hacia la derecha (realidad casi digital).** Los usuarios experimentan una realidad digital y no saben lo que ocurre en la realidad física que les rodea.

## <a name="next-discovery-checkpoint"></a>Siguiente punto de comprobación de detección

Se encuentra en el principio del [recorrido de detección](get-started-with-mr.md) que hemos diseñado para usted, explorando los conceptos básicos de la realidad mixta. Desde aquí, puede continuar con el siguiente tema básico: 

> [!div class="nextstepaction"]
> [¿Qué es un holograma?](hologram.md)
