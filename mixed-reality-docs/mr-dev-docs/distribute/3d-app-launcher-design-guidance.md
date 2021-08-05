---
title: Guía de diseño del iniciador de aplicaciones 3D
description: Un iniciador de aplicaciones 3D es un objeto "físico" en la casa de realidad mixta del usuario que puede seleccionar para iniciar una aplicación.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, iniciador de aplicaciones 3D, casco envolvente, cubo en directo, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, UWP, Win32, iluminación, color
ms.openlocfilehash: 2d93930d63b251aa91d77c96b4d5250baba54c51de50388f690b3588b1580761
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188606"
---
# <a name="3d-app-launcher-design-guidance"></a>Guía de diseño del iniciador de aplicaciones 3D

Cuando se coloca un casco Windows Mixed Reality envolvente (VR), se escribe el Windows Mixed Reality inicio. La casa se visualiza como una casa en un monte rodeado de montaña y agua, pero puede elegir otros entornos e [incluso crear los suyos propios.](../design/add-custom-home-environments.md) Dentro del espacio de la casa, un usuario puede organizar y organizar los objetos 3D y las aplicaciones que le importan de la manera que quiera. Un **iniciador de aplicaciones 3D** es un objeto "físico" en la casa de realidad mixta del usuario que puede seleccionar para iniciar una aplicación.

![Ejemplo: Iniciador de aplicaciones floaty bird 3D](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Ejemplo del iniciador de aplicaciones floaty Bird 3D (aplicación ficticia)*

## <a name="3d-app-launcher-creation-process"></a>Proceso de creación del iniciador de aplicaciones 3D

Hay tres pasos para crear un iniciador de aplicaciones 3D:

1. Diseño y conceptos (este artículo)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrarlo en la aplicación:
    * [Aplicaciones para UWP](implementing-3d-app-launchers.md)
    * [Aplicaciones de Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Conceptos de diseño

### <a name="fantastic-yet-familiar"></a>Fantástico pero familiar

El Windows Mixed Reality en el que se encuentra el iniciador de aplicaciones es parte familiar, parte fantástica/sci-fi. Los mejores iniciadores siguen las reglas de este mundo. Piense en cómo puede tomar un objeto conocido y representativo de la aplicación, pero somete algunas de las reglas de la realidad real. La magia dará como resultado.

### <a name="intuitive"></a>Intuitiva

Cuando se observa el iniciador de aplicaciones, su propósito (iniciar la aplicación) debe ser obvio y no debe causar confusión. Por ejemplo, asegúrese de que el iniciador es un representante lo suficientemente obvio de la aplicación que no se confundirá con un fragmento de la Casa sobre el acantilado. El iniciador de aplicaciones debe invitar a personas a tocarla o seleccionarla.

![Ejemplo: Iniciador de aplicaciones 3D fresh Note](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Ejemplo del iniciador de aplicaciones 3D de Fresh Note (aplicación ficticia)*

### <a name="home-scale"></a>Escala de inicio

Los iniciadores de aplicaciones 3D se Casa sobre el acantilado y su tamaño predeterminado debe tener sentido con los demás objetos "físicos" del espacio. Si coloca el iniciador junto a, por ejemplo, una planta de casa o algunos residuos, debería sentirse como en casa, según el tamaño. Un buen punto de partida es ver cómo se examinan 30 pulgadas cúbicas, pero recuerde que los usuarios pueden escalar o reducir verticalmente si lo quieren.

### <a name="own-able"></a>Con capacidad propia

El iniciador de aplicaciones debería ser como un objeto que una persona estaría deseando tener en su espacio. Prácticamente se rodearán con estas cosas, por lo que el iniciador debería sentirse como algo que el usuario consideró lo suficientemente deseable como para buscar y mantenerse cerca.

![Ejemplo: Iniciador de aplicaciones 3D de Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Ejemplo del iniciador de aplicaciones 3D de Astro Warp (aplicación ficticia)*

### <a name="recognizable"></a>Reconocible

El iniciador de aplicaciones 3D debe expresar al instante "la marca de la aplicación" a las personas que la ven. Si tiene un carácter de estrella o un objeto especialmente identificable en la aplicación, se recomienda usarlo como una parte importante del diseño. En un mundo de realidad mixta, un objeto atraerá más interés de los usuarios que solo un logotipo. Los objetos reconocibles comunican la marca de forma rápida y clara.

### <a name="volumetric"></a>Volumétrico

La aplicación merece algo más que simplemente colocar el logotipo en un plano plano y llamarlo al día. El iniciador debe ser un objeto físico 3D emocionante en el espacio del usuario. Un buen enfoque es imaginar que la aplicación va a tener un globo en el día del día de la acción de Macy' Pregúntese, ¿qué sería realmente la sorpresa de la gente cuando salió por la calle? ¿Qué aspecto tendría de todos los ángulos de visualización?

:::row:::
    :::column:::
        ![Solo logotipo ](images/20171016-140436-mixedreality-640px.jpg) *solo logotipo*
    :::column-end:::
    :::column:::
        ![Más reconocible con un carácter ](images/20171016-140557-mixedreality-640px.jpg) *Más reconocible con un carácter*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![El enfoque plano, no sorprendentemente, parece plano, no ](images/20171016-155101-mixedreality-640px.jpg) *sorprendentemente, se siente plano.*
    :::column-end:::
    :::column:::
        ![El enfoque volumétrico muestra mejor el enfoque volumétrico de la ](images/20171016-161407-mixedreality-640px.jpg) *aplicación.*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>Sugerencias para buenos modelos 3D

* Al planear dimensiones para el iniciador de la aplicación, se busca aproximadamente un cubo de 30 cm. Por lo tanto, una relación de tamaño de 1:1:1.
* Los modelos deben tener menos de 10 000 polígonos. [Más información sobre los recuentos de triángulos y los niveles de detalles (LOD)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Pruebe con un casco envolvente.
* Cree detalles en la geometría del modelo siempre que sea posible; no se base en texturas para obtener detalles.
* Cree geometría cerrada "hermética". No hay ningún hueco en el que no se modele.
* Use materiales naturales en el objeto. Imagine crearla en el mundo real.
* Asegúrese de que el modelo se lee bien a diferentes distancias y tamaños.
* Cuando el modelo esté listo para usarse, lea las [directrices de exportación de recursos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modelo con detalles sutiles en la textura](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modelo con detalles sutiles en la textura*

### <a name="what-to-avoid"></a>Qué evitar

* No use detalles de contraste alto ni patrones y texturas pequeños y ocupados.
* No use geometría fina: no funciona bien a distancia y tendrá un alias mal.
* No permita que las partes del modelo se extienda mucho más allá de la relación de tamaño 1:1:1. Creará problemas de escalado.

![Evitar patrones de contraste alto y pequeños ocupados](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evitar patrones de contraste alto, pequeños y ocupados*

## <a name="how-to-handle-type"></a>Cómo controlar el tipo

* Se recomienda que el tipo ocupa aproximadamente 1/3 del iniciador de la aplicación (o más). El tipo es lo principal que da a los usuarios una idea de que el iniciador es, de hecho, un iniciador, por lo que es bueno si es sustancial.
* Evite hacer que el tipo sea super wide: intente mantenerlo dentro de los límites de las dimensiones principales de los iniciadores de la aplicación (más o menos).
* El tipo plano puede funcionar, pero puede ser difícil de ver desde ciertos ángulos y en determinados entornos. Considere la posibilidad de colocarlo como un objeto sólido o un fondo detrás de él para ayudarle con esto.
* Agregar una dimensión al tipo se siente bien en 3D. El sombreado de los lados del tipo de un color más oscuro diferente puede ayudar a mejorar la legibilidad.

:::row:::
    :::column:::
        ![El tipo plano sin fondo puede ser difícil de ver desde ciertos ángulos y, en determinados entornos, el tipo plano sin fondo puede ser difícil de ver desde ciertos ángulos y en ](images/flattype-640px.png) *determinados entornos.*
    :::column-end:::
    :::column:::
        ![El tipo con un fondo integrado puede funcionar bien. Tipo con un fondo ](images/flattypeandbkg-640px.png) *integrado puede funcionar bien*
    :::column-end:::
    :::column:::
        ![El tipo extruido puede funcionar bien si sombrea los lados El tipo extruido puede funcionar bien ](images/20171016-160221-mixedreality-640px.jpg) *si sombrea los lados.*
    :::column-end:::
:::row-end:::

**Colores de tipo que funcionan**

* Blanco
* Negro
* Color semi-saturado claro

![Escriba los colores que funcionan.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Colores de tipo que funcionan*

### <a name="colors-to-avoid"></a>Colores que se deben evitar

Los colores de tipo que causan problemas incluyen:

* Tono medio
* Gris
* Colores saturados o desaturados

![Colores de tipo que causan problemas.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Colores de tipo que causan problemas*

## <a name="lighting"></a>Iluminación

La iluminación del iniciador de aplicaciones procede del entorno Casa sobre el acantilado aplicación. Asegúrese de probar el iniciador en varios lugares de la casa para que tenga un buen aspecto, tanto en la luz como en las sombras. La buena noticia es que, si ha seguido las otras instrucciones de diseño de este documento, el iniciador debe estar en buen estado para la mayoría de la iluminación del Casa sobre el acantilado.

Los lugares adecuados para probar el aspecto del iniciador en las distintas luces del entorno son Studio, Media Room, en cualquier lugar fuera y en back-and-back (el área concreta con el suelo). Otra buena prueba es colocarla a media luz y media sombra y ver su aspecto.

![Asegúrese de que el iniciador se ve bien en la luz y las sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Asegúrese de que el iniciador se ve bien en la luz y las sombras.*

## <a name="texturing"></a>Texturizado

### <a name="authoring-your-textures"></a>Creación de texturas

El formato final del iniciador de aplicaciones 3D será un archivo .glb, que se realiza mediante la canalización PBR (Representación basada físicamente). Este puede ser un proceso complicado: ahora es un buen momento para emplear a un intérprete técnico si aún no lo ha hecho. Si es un héroe personal, ded su tiempo para investigar y aprender la terminología de [PBR](https://wiki.polycount.com/wiki/PBR) y lo que sucede en el pasado antes de empezar le ayudará a evitar errores comunes. 

![Ejemplo: Aplicación Fresh Note](images/pbr-freshnote1-640px-500px.png)<br>
*Ejemplo del iniciador de aplicaciones 3D de Fresh Note (aplicación ficticia)*

### <a name="recommended-authoring-tool"></a>Herramienta de creación recomendada

Se recomienda usar [El autor de la indespechación](https://www.allegorithmic.com/products/substance-painter) de la indesustración de Seorithmic para crear el archivo final. Si no está familiarizado con la creación de sombreadores PBR en El autor de la razón, este es un [tutorial.](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)

(Como [alternativa, 3D-Rare,](https://3dcoat.com/home/) [Quixel Suite 2](https://quixel.se/suite2/)o [Marmoset Toolbag](https://www.marmoset.co/toolbag/) también funcionaría si está más familiarizado con uno de estos).

### <a name="best-practices"></a>Procedimientos recomendados

* Si el objeto del iniciador de aplicaciones se ha escrito para PBR, debería ser sencillo convertirlo para el entorno Casa sobre el acantilado aplicación.
* Nuestro sombreador espera un flujo de trabajo Metal/Roughness: el sombreador PBR de Unreal es un facsímil cercano.
* Al exportar las texturas, tenga en cuenta los [tamaños de](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) textura recomendados.
* Asegúrese de compilar los objetos para la iluminación en tiempo real; esto significa:
  * Evitar sombras asonadas o sombras dibujadas
  * Evitar la iluminación asada en las texturas
  * Use uno de los paquetes de creación de material pbr para obtener los mapas adecuados generados para el sombreador.

## <a name="see-also"></a>Vea también

* [Cree modelos 3D para usarlos en el ambiente principal](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)](implementing-3d-app-launchers.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
