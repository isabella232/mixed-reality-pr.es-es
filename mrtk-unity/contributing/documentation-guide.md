---
title: Guía de documentación
description: directrices y estándares de documentación para MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 37233141bd43f27db47935574bac7630b8bea8d7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121393"
---
# <a name="documentation-guidelines"></a>Directrices de documentación

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

En este documento se describen las directrices de documentación y los estándares de Mixed Reality Toolkit (MRTK). Esto proporciona una introducción a los aspectos técnicos de la escritura y generación de documentación, para resaltar los problemas comunes y para describir el estilo de escritura recomendado.

Se supone que la propia página sirve como ejemplo, por lo que usa el estilo previsto y las características de marcado más comunes de la documentación.

- [Origen](#source-documentation)
- [Cómo hacerlo](#how-to-documentation)
- [Diseño](#design-documentation)
- [Notas de rendimiento](#performance-notes)
- [Cambios importantes](#breaking-changes)

---

## <a name="functionality-and-markup"></a>Funcionalidad y marcado

En esta sección se describen las características que se necesitan con frecuencia. Para ver cómo funcionan, consulte el código fuente de la página.

1. Listas numeradas
   1. Listas numeradas anidadas con al menos 3 espacios en blanco iniciales
   1. El número real del código es irrelevante; El análisis se ocupará de establecer el número de elemento correcto.

- Listas de puntos de viñeta
  - Listas de puntos de viñeta anidadas
- Texto en **negrita** con \* \* asterisco doble\*\*
- _texto_ *cursiva* \_ con carácter de subrayado o asterisco \_ \* único\*
- Texto `highlighted as code` dentro de una \` oración mediante comillas atrás\`
- Vínculos a páginas de documentos Directrices [de documentación de MRTK](documentation-guide.md)
- Vínculos [a delimitadores dentro de una página](#style); Los delimitadores se forman reemplazando espacios por guiones y convertiendo a minúsculas.

En el caso de los ejemplos de código, usamos los bloques con tres signos de subrayado y especificamos csharp como lenguaje para el resaltado \` \` \` de sintaxis: 

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Al mencionar código dentro de una oración `use a single backtick` .

### <a name="todos"></a>TODOs

Evite el uso de TODOs en documentos, ya que con el tiempo estos TODOs (como los TODOs de código) tienden a acumular información sobre cómo deben actualizarse y por qué se pierden.

Si es absolutamente necesario agregar un todo, siga estos pasos:

1. Presentar un nuevo problema en GitHub que describa el contexto detrás de todo y proporcionar suficiente información que otro colaborador podría comprender y, a continuación, abordar la tarea pendiente.
2. Haga referencia a la dirección URL del problema en la lista de tareas de los documentos.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>Secciones resaltadas

Para resaltar puntos específicos del lector, use *> [!NOTE]* , y para generar los estilos *> [!WARNING]* *> [!IMPORTANT]* siguientes. Se recomienda usar notas para puntos generales y puntos de advertencia o importantes solo para casos relevantes especiales.

> [!NOTE]
> Ejemplo de una nota

> [!WARNING]
> Ejemplo de una advertencia

> [!IMPORTANT]
> Ejemplo de un comentario importante

## <a name="page-layout"></a>Diseño de página

### <a name="introduction"></a>Introducción

La parte inmediatamente posterior al título del capítulo principal debe servir como una breve introducción sobre la que se trata el capítulo. No haga que esto sea demasiado largo; en su lugar, agregue sub titulares. Permiten vincular a secciones y se pueden guardar como marcadores.

### <a name="main-body"></a>Cuerpo principal

Use titulares de dos y tres niveles para estructurar el resto.

**Minisecciones**

Use una línea de texto en negrita para los bloques que deben destacar. Esto se podría reemplazar por titulares de cuatro niveles en algún momento.

### <a name="see-also-section"></a>Sección "Ver también"

La mayoría de las páginas deben terminar con un capítulo denominado *Vea también*. Este capítulo es simplemente una lista con viñetas de vínculos a páginas relacionadas con este tema. Estos vínculos también pueden aparecer en el texto de la página cuando corresponda, pero esto no es necesario. De forma similar, el texto de la página puede contener vínculos a páginas que no están relacionadas con el tema principal; no deben incluirse en la *lista Ver* también. Vea [el capítulo "Ver también"](#see-also) de esta página como ejemplo para la elección de vínculos.

## <a name="table-of-contents-toc"></a>Tabla de contenido (TOC)

Los archivos Toc se usan para generar las barras de navegación en la documentación de github.io MRTK.
Cada vez que se agrega un nuevo archivo de documentación, asegúrese de que haya una entrada para ese archivo en uno de los archivos toc.yml de la carpeta de documentación. Solo los artículos enumerados en los archivos toc se mostrarán en la navegación de los documentos para desarrolladores. Puede haber un archivo toc para cada subcarpeta de la carpeta de documentación que se puede vincular a cualquier archivo toc existente para agregarlo como una subsección a la parte correspondiente de la navegación.

## <a name="style"></a>Estilo

### <a name="writing-style"></a>Estilo de escritura

Regla general: intente parecer **profesional.** Esto suele significar evitar un "tono de conversación". Intente también evitar hiperboles y estorbolismo.

1. No intente ser (en exceso) divertido.
2. Nunca escriba "I"
3. Evite "we". Normalmente, esto se puede volver a cambiar fácilmente mediante "MRTK". Ejemplo: "se admite esta característica" -> "MRTK admite esta característica" o "se admiten las siguientes características...".
4. Del mismo modo, intente evitar "you". Ejemplo: "Con este sencillo cambio, el sombreador se vuelve configurable" -> "Los sombreadores se pueden configurar con poco esfuerzo".
5. No use "frases desasechas".
6. Evite parecer demasiado entusiasmado, no es necesario vender nada.
7. Del mismo modo, evite ser muy drástico. Rara vez se necesitan signos de exclamación.

### <a name="capitalization"></a>Uso de mayúsculas

- Use **el caso sentence para los titulares.** Por ejemplo, en mayúsculas la primera letra y los nombres, pero nada más.
- Use el inglés normal para todo lo demás. Esto significa **que no se capitalizan palabras arbitrarias,** incluso si tienen un significado especial en ese contexto. Prefiere *texto en cursiva* para resaltar determinadas palabras; vea [a continuación](#emphasis-and-highlighting).
- Cuando un vínculo se inserta en una oración (que es el método preferido), el nombre del capítulo estándar siempre usa letras mayúsculas, lo que incrustó la regla de que no hay mayúsculas arbitrarias dentro del texto. Por lo tanto, use un nombre de vínculo personalizado para corregir el uso de mayúsculas y mayúsculas. Por ejemplo, este es un vínculo a la documentación [de control de límites.](../features/ux-building-blocks/bounds-control.md)
- Haga mayúsculas en los nombres, como *Unity.*
- NO escriba en mayúsculas "editor" al escribir el *editor de Unity.*

### <a name="emphasis-and-highlighting"></a>Énfasis y resaltado

Hay dos maneras de resaltar o resaltar palabras, en negrita o en cursiva. El efecto del texto  en negrita es que el texto en negrita se mantiene y, por tanto, se puede observar fácilmente mientras se desliza un fragmento de texto o incluso se desplaza por una página. Negrita es excelente para resaltar frases que los usuarios deben recordar. Sin embargo, **use texto en negrita rara vez**, porque suele distraer.

A menudo, se quiere "agrupar" algo que pertenezca lógicamente junto o resaltar un término específico, porque tiene un significado especial. No es necesario destacar este tipo de cosas en el texto general. Use texto cursiva como *método ligero para* resaltar algo.

De forma similar, cuando un nombre de archivo, una ruta de acceso o una entrada de menú se mencionan en texto, prefieren hacer cursiva para agruparlo lógicamente, sin distraer.

En general, intente evitar **el resaltado de texto innecesario.** Los términos especiales se pueden resaltar una vez para que el lector sea consciente, no repita este resaltado en todo el texto, cuando ya no sirve para nada y solo distrae.

### <a name="mentioning-menu-entries"></a>Mencionar entradas de menú

Al mencionar una entrada de menú en la que un usuario debe hacer clic, la convención actual es: *Project > Files > Create > Leaf*

### <a name="links"></a>Vínculos

Inserte tantos vínculos útiles a otras páginas como sea posible, pero cada vínculo solo una vez. Supongamos que un lector hace clic en cada vínculo de la página y piensa en lo molesto que sería, si la misma página se abre 20 veces.

Prefiere los vínculos insertados en una oración:

- BAD: Las directrices son útiles. Consulte [este capítulo para](../contributing/documentation-guide.md) obtener más información.
- GOOD: [Las directrices](documentation-guide.md) son útiles.

Evite los vínculos externos, ya que pueden quedar obsoletos o contener contenido protegido por derechos de autor.

Al agregar un vínculo, considere si también debe aparecer en la [sección](#see-also) Ver también. De forma similar, compruebe si se debe agregar un vínculo a la nueva página a la página vinculada.

### <a name="images--screenshots"></a>Imágenes o capturas de pantalla

**Use capturas de pantalla con moderación.** Mantener imágenes en la documentación es mucho trabajo, los pequeños cambios en la interfaz de usuario pueden hacer que muchas capturas de pantalla no funcionen. Las reglas siguientes reducirán el esfuerzo de mantenimiento:

1. No use capturas de pantalla para los aspectos que se pueden describir en el texto. Especialmente, **nunca captura de pantalla una cuadrícula de propiedades** con el único propósito de mostrar los nombres y valores de propiedad.
2. No incluya cosas en una captura de pantalla que sean irrelevantes de lo que se muestra. Por ejemplo, cuando se muestra un efecto de representación, realice una captura de pantalla de la ventanilla, pero excluya cualquier interfaz de usuario que la rodea. Al mostrar alguna interfaz de usuario, intente mover las ventanas para que solo esa parte importante esté en la imagen.
3. Al incluir la interfaz de usuario de captura de pantalla, solo se muestran las partes importantes. Por ejemplo, al hablar de botones en una barra de herramientas, haga una imagen pequeña que muestre los botones de la barra de herramientas importantes, pero excluya todo lo que le rodea.
4. Use solo imágenes que sean fáciles de reproducir. Esto significa que no pinte marcadores ni resaltados en capturas de pantalla. En primer lugar, no hay ninguna regla coherente en cuanto a su aspecto. En segundo lugar, reproducir este tipo de captura de pantalla es un esfuerzo adicional. En su lugar, describa las partes importantes del texto. Hay excepciones a esta regla, pero son poco frecuentes.
5. Obviamente, es mucho más esfuerzo volver a crear un GIF animado. Es de esperar que sea responsable de volver a crearla hasta el final del tiempo, o esperar que los usuarios lo lancen, si no quieren dedicar ese tiempo.
6. Mantenga el número de imágenes de un artículo bajo. A menudo, un buen método consiste en realizar una captura de pantalla general de alguna herramienta, que muestra todo y, a continuación, describir el resto en texto. Esto facilita la sustitución de la captura de pantalla cuando sea necesario.

Otros aspectos:

- La interfaz de usuario del editor para las capturas de pantalla debe usar el editor de temas de color gris claro, ya que no todos los usuarios tienen acceso al tema oscuro y nos gustaría mantener las cosas lo más coherentes posible.
- El ancho de imagen predeterminado es de 500 píxeles, ya que se muestra bien en la mayoría de los monitores. Intente no desviarse demasiado de él. 800 píxeles de ancho debe ser el máximo.
- Use PNG para capturas de pantalla de la interfaz de usuario.
- Use PNG o JPG para capturas de pantalla de ventanilla 3D. Prefiere la calidad sobre la relación de compresión.

### <a name="list-of-component-properties"></a>Lista de propiedades de componente

Al documentar una lista de propiedades, use texto en negrita para resaltar el nombre de la propiedad y, a continuación, saltos de línea y texto normal para describirlos. No use sub capítulos ni listas de puntos de viñeta.

Además, no olvide finalizar todas las oraciones con un punto.

## <a name="page-completion-checklist"></a>Lista de comprobación de finalización de páginas

1. Asegúrese de que se han seguido las instrucciones de este documento.
1. Examine la estructura del documento y vea si el nuevo documento se puede mencionar en la [sección Ver](#see-also) también de otras páginas.
1. Si está disponible, haga que alguien con conocimientos del tema lea la página para obtener una corrección técnica.
1. Haga que alguien lea a prueba la página para el estilo y el formato. Puede ser alguien que no esté familiarizado con el tema, lo que también es una buena idea para obtener comentarios sobre lo comprensible que es la documentación.

## <a name="source-documentation"></a>Documentación de origen

La documentación de la API se generará automáticamente a partir de los archivos de origen de MRTK. Para facilitar esto, los archivos de código fuente deben contener lo siguiente:

- [Bloques de resumen de clase, struct y enumeración](#class-struct-enum-summary-blocks)
- [Bloques de resumen de propiedades, métodos y eventos](#property-method-event-summary-blocks)
- [Versión de introducción de características y dependencias](#feature-introduction-version-and-dependencies)
- [Campos serializados](#serialized-fields)
- [Valores de enumeración](#enumeration-values)

Además de lo anterior, el código debe estar bien comentado para permitir el mantenimiento, las correcciones de errores y la facilidad de personalización.

### <a name="class-struct-enum-summary-blocks"></a>Bloques de resumen de clase, estructura y enumeración

Si se agrega una clase, una estructura o una enumeración a MRTK, se debe describir su propósito. Esto es para tomar la forma de un bloque de resumen encima de la clase .

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

Si hay dependencias de nivel de clase, deben documentarse en un bloque de comentarios, inmediatamente debajo del resumen.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Las solicitudes de extracción enviadas sin resúmenes para clases, estructuras o enumeraciones no se aprobarán.

### <a name="property-method-event-summary-blocks"></a>Bloques de resumen de propiedades, métodos y eventos

Las propiedades, los métodos y los eventos (PME), así como los campos, se documentan con bloques de resumen, independientemente de la visibilidad del código (pública, privada, protegida e interna). La herramienta de generación de documentación es responsable de filtrar y publicar solo las características públicas y protegidas.

NOTA: No se requiere un bloque **de** resumen para los métodos de Unity (por ejemplo: Activo, Iniciar, Actualizar).

La documentación de PME **es necesaria** para que se apruebe una solicitud de extracción.

Como parte de un bloque de resumen de PME, se requiere el significado y el propósito de los parámetros y los datos devueltos.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Versión de introducción de características y dependencias

Como parte de la documentación de resumen de la API, la información relacionada con la versión de MRTK en la que se introdujo la característica y las dependencias deben documentarse en un bloque de comentarios.

Las dependencias deben incluir dependencias de extensión o plataforma.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Campos serializados

Es un procedimiento recomendado usar el atributo de información sobre herramientas de Unity para proporcionar documentación en tiempo de ejecución para los campos de un script en el inspector.

Para que las opciones de configuración se incluyan  en la documentación de la API, los scripts deben incluir al menos el contenido de la información sobre herramientas en un bloque de resumen.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Valores de enumeración

Al definir y enumerar, el código también debe documentar el significado de los valores de enumeración mediante un bloque de resumen. Opcionalmente, los bloques de comentarios se pueden usar para proporcionar detalles adicionales para mejorar la comprensión.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Documentación de procedimientos

Es posible que muchos Mixed Reality Toolkit no necesiten usar la documentación de la API. Estos usuarios aprovecharán nuestros prefabs y scripts reutilizables y creados previamente para crear sus experiencias.

Cada área de características contendrá uno o varios archivos markdown (.md) que describen en un nivel bastante alto, lo que se proporciona. Según el tamaño o la complejidad de un área de características determinada, puede que sea necesario tener archivos adicionales, hasta uno por cada característica proporcionada.

Cuando se agrega una característica (o se cambia el uso), se debe proporcionar documentación general.

Como parte de esta documentación, se deben proporcionar secciones de pasos, incluidas las ilustraciones, para ayudar a los clientes nuevos en una característica o concepto en la introducción.

## <a name="design-documentation"></a>Documentación de diseño

Mixed Reality proporciona una oportunidad para crear mundos completamente nuevos. Es probable que parte de esto implique la creación de recursos personalizados para su uso con MRTK. Para que esto sea lo más libre posible para los clientes, los componentes deben proporcionar documentación de diseño que describa cualquier formato u otros requisitos de recursos de arte.

Algunos ejemplos en los que la documentación de diseño puede resultar útil:

- Modelos de cursor
- Visualizaciones de asignaciones espaciales
- Archivos de efecto de sonido

Este tipo de documentación se **recomienda encarecidamente** y **se puede** solicitar como parte de una revisión de la solicitud de extracción.

Esto puede o no ser diferente de la recomendación de diseño en el sitio [de MS Developer](/windows/mixed-reality/design)

## <a name="performance-notes"></a>Notas de rendimiento

Algunas características importantes tienen un costo de rendimiento. A menudo, este código dependerá mucho de cómo estén configurados.

Por ejemplo:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

Las notas de rendimiento se recomiendan para los componentes de CPU o GPU intensivos y **se** pueden solicitar como parte de una revisión de la solicitud de extracción. Las notas de rendimiento aplicables se incluirán en la documentación de api **y** de información general.

## <a name="breaking-changes"></a>Últimos cambios

La documentación de cambios importantes consiste en un archivo de [nivel](../contributing/breaking-changes.md) superior que vincula a cada área de características breaking-changes.md.

El área de características breaking-changes.md archivos deben contener la lista de  todos los cambios importantes conocidos de una versión determinada, así como el historial de cambios importantes de versiones anteriores.

Por ejemplo:

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

La información contenida en el nivel de breaking-changes.md archivos se agregará a las notas de la versión de cada nueva versión de MRTK.

Los cambios importantes que forman parte de un cambio **deben** documentarse como parte de una solicitud de extracción.

## <a name="tools-for-editing-markdown"></a>Herramientas para editar MarkDown

[Visual Studio Code](https://code.visualstudio.com/) es una excelente herramienta para editar archivos markdown que forman parte de la documentación de MRTK.

Al escribir documentación, también se recomienda encarecidamente instalar las dos extensiones siguientes:

- Extensión Markdown de Docs para Visual Studio Code: use Alt+M para abrir un menú de opciones de creación de documentos.

- Corrector ortográfico de código: las palabras mal escritas se subrayan; Haga clic con el botón derecho en una palabra mal escrita para cambiarla o guárdela en el diccionario.

Ambos se empaquetan en el paquete de creación de Docs publicado por Microsoft.

## <a name="see-also"></a>Consulte también 

* [Vínculo de ejemplo](https://www.google.com)