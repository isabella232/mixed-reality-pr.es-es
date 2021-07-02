---
title: Directrices de documentación
description: directrices y estándares de documentación para MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 95af19b71a9fe06dabad058e75f78d951262ba4a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175353"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="a2f38-104">Directrices de documentación</span><span class="sxs-lookup"><span data-stu-id="a2f38-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="a2f38-105">En este documento se describen las directrices y los estándares de documentación para Mixed Reality Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="a2f38-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="a2f38-106">Esto proporciona una introducción a los aspectos técnicos de la escritura y generación de documentación, para resaltar problemas comunes y para describir el estilo de escritura recomendado.</span><span class="sxs-lookup"><span data-stu-id="a2f38-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="a2f38-107">Se supone que la propia página sirve como ejemplo, por lo que usa el estilo previsto y las características de marcado más comunes de la documentación.</span><span class="sxs-lookup"><span data-stu-id="a2f38-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="a2f38-108">Origen</span><span class="sxs-lookup"><span data-stu-id="a2f38-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="a2f38-109">Cómo hacerlo</span><span class="sxs-lookup"><span data-stu-id="a2f38-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="a2f38-110">Diseño</span><span class="sxs-lookup"><span data-stu-id="a2f38-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="a2f38-111">Notas de rendimiento</span><span class="sxs-lookup"><span data-stu-id="a2f38-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="a2f38-112">Cambios importantes</span><span class="sxs-lookup"><span data-stu-id="a2f38-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="a2f38-113">Funcionalidad y marcado</span><span class="sxs-lookup"><span data-stu-id="a2f38-113">Functionality and markup</span></span>

<span data-ttu-id="a2f38-114">En esta sección se describen las características que se necesitan con frecuencia.</span><span class="sxs-lookup"><span data-stu-id="a2f38-114">This section describes frequently needed features.</span></span> <span data-ttu-id="a2f38-115">Para ver cómo funcionan, consulte el código fuente de la página.</span><span class="sxs-lookup"><span data-stu-id="a2f38-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="a2f38-116">Listas numeradas</span><span class="sxs-lookup"><span data-stu-id="a2f38-116">Numbered lists</span></span>
   1. <span data-ttu-id="a2f38-117">Listas numeradas anidadas con al menos 3 espacios en blanco iniciales</span><span class="sxs-lookup"><span data-stu-id="a2f38-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="a2f38-118">El número real del código es irrelevante; El análisis se encarga de establecer el número de elemento correcto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="a2f38-119">Listas de puntos de viñeta</span><span class="sxs-lookup"><span data-stu-id="a2f38-119">Bullet point lists</span></span>
  - <span data-ttu-id="a2f38-120">Listas de puntos de viñeta anidadas</span><span class="sxs-lookup"><span data-stu-id="a2f38-120">Nested bullet point lists</span></span>
- <span data-ttu-id="a2f38-121">Texto en **negrita** con \* \* asterisco doble\*\*</span><span class="sxs-lookup"><span data-stu-id="a2f38-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="a2f38-122">_texto_ *cursiva* \_ con carácter de subrayado o asterisco \_ \* único\*</span><span class="sxs-lookup"><span data-stu-id="a2f38-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="a2f38-123">Texto `highlighted as code` dentro de una \` oración mediante comillas\`</span><span class="sxs-lookup"><span data-stu-id="a2f38-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="a2f38-124">Vínculos a páginas de documentos [Directrices de documentación de MRTK](documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="a2f38-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="a2f38-125">Vínculos [a delimitadores dentro de una página](#style); Los delimitadores se forman reemplazando espacios por guiones y convirtiendo a minúsculas</span><span class="sxs-lookup"><span data-stu-id="a2f38-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="a2f38-126">En el caso de los ejemplos de código, usamos los bloques con tres signos de subrayado y especificamos csharp como lenguaje para el resaltado \` \` \` de sintaxis: </span><span class="sxs-lookup"><span data-stu-id="a2f38-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="a2f38-127">Al mencionar código dentro de una oración `use a single backtick` .</span><span class="sxs-lookup"><span data-stu-id="a2f38-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="a2f38-128">TODOs</span><span class="sxs-lookup"><span data-stu-id="a2f38-128">TODOs</span></span>

<span data-ttu-id="a2f38-129">Evite el uso de TODOs en documentos, ya que con el tiempo estos TODOs (como los TTO de código) tienden a acumular información sobre cómo se deben actualizar y por qué se pierden.</span><span class="sxs-lookup"><span data-stu-id="a2f38-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="a2f38-130">Si es absolutamente necesario agregar una lista de tareas pendientes, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="a2f38-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="a2f38-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span><span class="sxs-lookup"><span data-stu-id="a2f38-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="a2f38-132">Haga referencia a la dirección URL del problema en la lista de tareas de los documentos.</span><span class="sxs-lookup"><span data-stu-id="a2f38-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="a2f38-133">Secciones resaltadas</span><span class="sxs-lookup"><span data-stu-id="a2f38-133">Highlighted sections</span></span>

<span data-ttu-id="a2f38-134">Para resaltar puntos específicos al lector, use *> [!NOTE]* , y para generar los estilos *> [!WARNING]* *> [!IMPORTANT]* siguientes.</span><span class="sxs-lookup"><span data-stu-id="a2f38-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="a2f38-135">Se recomienda usar notas para puntos generales y puntos de advertencia o importantes solo para casos relevantes especiales.</span><span class="sxs-lookup"><span data-stu-id="a2f38-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="a2f38-136">Ejemplo de una nota</span><span class="sxs-lookup"><span data-stu-id="a2f38-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="a2f38-137">Ejemplo de una advertencia</span><span class="sxs-lookup"><span data-stu-id="a2f38-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2f38-138">Ejemplo de un comentario importante</span><span class="sxs-lookup"><span data-stu-id="a2f38-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="a2f38-139">Diseño de página</span><span class="sxs-lookup"><span data-stu-id="a2f38-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="a2f38-140">Introducción</span><span class="sxs-lookup"><span data-stu-id="a2f38-140">Introduction</span></span>

<span data-ttu-id="a2f38-141">La parte inmediatamente posterior al título del capítulo principal debe servir como breve introducción de la que trata el capítulo.</span><span class="sxs-lookup"><span data-stu-id="a2f38-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="a2f38-142">No lo haga demasiado largo; en su lugar, agregue sub titulares.</span><span class="sxs-lookup"><span data-stu-id="a2f38-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="a2f38-143">Permiten vincular a secciones y se pueden guardar como marcadores.</span><span class="sxs-lookup"><span data-stu-id="a2f38-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="a2f38-144">Cuerpo principal</span><span class="sxs-lookup"><span data-stu-id="a2f38-144">Main body</span></span>

<span data-ttu-id="a2f38-145">Use titulares de dos y tres niveles para estructurar el resto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="a2f38-146">**Minisecciones**</span><span class="sxs-lookup"><span data-stu-id="a2f38-146">**Mini Sections**</span></span>

<span data-ttu-id="a2f38-147">Use una línea de texto en negrita para los bloques que deben destacar. Esto se podría reemplazar por titulares de cuatro niveles en algún momento.</span><span class="sxs-lookup"><span data-stu-id="a2f38-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="a2f38-148">Sección "Ver también"</span><span class="sxs-lookup"><span data-stu-id="a2f38-148">'See also' section</span></span>

<span data-ttu-id="a2f38-149">La mayoría de las páginas deben terminar con un capítulo denominado *Vea también*.</span><span class="sxs-lookup"><span data-stu-id="a2f38-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="a2f38-150">Este capítulo es simplemente una lista con viñetas de vínculos a páginas relacionadas con este tema.</span><span class="sxs-lookup"><span data-stu-id="a2f38-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="a2f38-151">Estos vínculos también pueden aparecer en el texto de la página cuando corresponda, pero esto no es necesario.</span><span class="sxs-lookup"><span data-stu-id="a2f38-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="a2f38-152">De forma similar, el texto de la página puede contener vínculos a páginas que no están relacionadas con el tema principal; no deben incluirse en la *lista Ver* también.</span><span class="sxs-lookup"><span data-stu-id="a2f38-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="a2f38-153">Vea [el capítulo "Ver también"](#see-also) de esta página como ejemplo para la elección de vínculos.</span><span class="sxs-lookup"><span data-stu-id="a2f38-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="a2f38-154">Tabla de contenido (TOC)</span><span class="sxs-lookup"><span data-stu-id="a2f38-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="a2f38-155">Los archivos toc se usan para generar las barras de navegación en la documentación de github.io MRTK.</span><span class="sxs-lookup"><span data-stu-id="a2f38-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="a2f38-156">Cada vez que se agrega un nuevo archivo de documentación, asegúrese de que haya una entrada para ese archivo en uno de los archivos toc.yml de la carpeta de documentación.</span><span class="sxs-lookup"><span data-stu-id="a2f38-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="a2f38-157">Solo los artículos enumerados en los archivos toc se mostrarán en la navegación de los documentos para desarrolladores. Puede haber un archivo toc para cada subcarpeta de la carpeta de documentación que se puede vincular a cualquier archivo toc existente para agregarlo como una subsección a la parte correspondiente de la navegación.</span><span class="sxs-lookup"><span data-stu-id="a2f38-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="a2f38-158">Estilo</span><span class="sxs-lookup"><span data-stu-id="a2f38-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="a2f38-159">Estilo de escritura</span><span class="sxs-lookup"><span data-stu-id="a2f38-159">Writing style</span></span>

<span data-ttu-id="a2f38-160">Regla general: intente parecer **profesional.**</span><span class="sxs-lookup"><span data-stu-id="a2f38-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="a2f38-161">Esto suele significar evitar un "tono de conversación".</span><span class="sxs-lookup"><span data-stu-id="a2f38-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="a2f38-162">Intente también evitar el hiperbole y el desenlazismo.</span><span class="sxs-lookup"><span data-stu-id="a2f38-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="a2f38-163">No intente ser (en exceso) desastoso.</span><span class="sxs-lookup"><span data-stu-id="a2f38-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="a2f38-164">No escribir nunca "I"</span><span class="sxs-lookup"><span data-stu-id="a2f38-164">Never write 'I'</span></span>
3. <span data-ttu-id="a2f38-165">Evite "we".</span><span class="sxs-lookup"><span data-stu-id="a2f38-165">Avoid 'we'.</span></span> <span data-ttu-id="a2f38-166">Normalmente, esto se puede volver a cambiar fácilmente mediante "MRTK".</span><span class="sxs-lookup"><span data-stu-id="a2f38-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="a2f38-167">Ejemplo: "se admite esta característica" -> "MRTK admite esta característica" o "se admiten las siguientes características...".</span><span class="sxs-lookup"><span data-stu-id="a2f38-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="a2f38-168">De forma similar, intente evitar "usted".</span><span class="sxs-lookup"><span data-stu-id="a2f38-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="a2f38-169">Ejemplo: "Con este simple cambio, el sombreador se vuelve configurable"</span><span class="sxs-lookup"><span data-stu-id="a2f38-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="a2f38-170">-> "Los sombreadores se pueden configurar con poco esfuerzo".</span><span class="sxs-lookup"><span data-stu-id="a2f38-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="a2f38-171">No use "frases desasechas".</span><span class="sxs-lookup"><span data-stu-id="a2f38-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="a2f38-172">Evite parecer demasiado entusiasmado, no es necesario vender nada.</span><span class="sxs-lookup"><span data-stu-id="a2f38-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="a2f38-173">Del mismo modo, evite ser muy drástico.</span><span class="sxs-lookup"><span data-stu-id="a2f38-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="a2f38-174">Rara vez se necesitan signos de exclamación.</span><span class="sxs-lookup"><span data-stu-id="a2f38-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="a2f38-175">Uso de mayúsculas</span><span class="sxs-lookup"><span data-stu-id="a2f38-175">Capitalization</span></span>

- <span data-ttu-id="a2f38-176">Use **El caso de oración para los titulares**.</span><span class="sxs-lookup"><span data-stu-id="a2f38-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="a2f38-177">Por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="a2f38-177">Ie.</span></span> <span data-ttu-id="a2f38-178">capitalice la primera letra y los nombres, pero nada más.</span><span class="sxs-lookup"><span data-stu-id="a2f38-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="a2f38-179">Use el inglés normal para todo lo demás.</span><span class="sxs-lookup"><span data-stu-id="a2f38-179">Use regular English for everything else.</span></span> <span data-ttu-id="a2f38-180">Esto significa **que no se capitalizan palabras arbitrarias,** incluso si tienen un significado especial en ese contexto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="a2f38-181">Prefiere *texto en cursiva* para resaltar ciertas palabras; vea [a continuación](#emphasis-and-highlighting).</span><span class="sxs-lookup"><span data-stu-id="a2f38-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="a2f38-182">Cuando un vínculo se inserta en una oración (que es el método preferido), el nombre del capítulo estándar siempre usa letras mayúsculas, lo que rompe la regla de que no haya mayúsculas arbitrarias dentro del texto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="a2f38-183">Por lo tanto, use un nombre de vínculo personalizado para corregir el uso de mayúsculas y mayúsculas.</span><span class="sxs-lookup"><span data-stu-id="a2f38-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="a2f38-184">Por ejemplo, este es un vínculo a la documentación [del control de límites.](../features/ux-building-blocks/bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="a2f38-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="a2f38-185">Haga mayúsculas en los nombres, como *Unity.*</span><span class="sxs-lookup"><span data-stu-id="a2f38-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="a2f38-186">NO escriba "editor" en mayúsculas al escribir el *editor de Unity.*</span><span class="sxs-lookup"><span data-stu-id="a2f38-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="a2f38-187">Énfasis y resaltado</span><span class="sxs-lookup"><span data-stu-id="a2f38-187">Emphasis and highlighting</span></span>

<span data-ttu-id="a2f38-188">Hay dos maneras de resaltar las palabras, ponerlas en negrita o ponerlas en cursiva.</span><span class="sxs-lookup"><span data-stu-id="a2f38-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="a2f38-189">El efecto del texto  en negrita es que el texto en negrita se mantiene y, por tanto, se puede observar fácilmente mientras se desliza un fragmento de texto o incluso simplemente se desplaza por una página.</span><span class="sxs-lookup"><span data-stu-id="a2f38-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="a2f38-190">Negrita es excelente para resaltar frases que los usuarios deben recordar.</span><span class="sxs-lookup"><span data-stu-id="a2f38-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="a2f38-191">Sin embargo, **use texto en negrita rara vez**, porque suele distraer.</span><span class="sxs-lookup"><span data-stu-id="a2f38-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="a2f38-192">A menudo, se quiere "agrupar" algo que pertenezca de forma lógica o resaltar un término específico, ya que tiene un significado especial.</span><span class="sxs-lookup"><span data-stu-id="a2f38-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="a2f38-193">Estas cosas no necesitan destacarse del texto general.</span><span class="sxs-lookup"><span data-stu-id="a2f38-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="a2f38-194">Use texto cursiva como *método ligero para* resaltar algo.</span><span class="sxs-lookup"><span data-stu-id="a2f38-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="a2f38-195">De forma similar, cuando un nombre de archivo, una ruta de acceso o una entrada de menú se mencionan en texto, prefiere que sea cursiva para agruparlo lógicamente, sin distraer.</span><span class="sxs-lookup"><span data-stu-id="a2f38-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="a2f38-196">En general, intente evitar **el resaltado de texto innecesario.**</span><span class="sxs-lookup"><span data-stu-id="a2f38-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="a2f38-197">Los términos especiales se pueden resaltar una vez para que el lector tenga en cuenta, no repita este resaltado en todo el texto, cuando ya no sirve para nada y solo distrae.</span><span class="sxs-lookup"><span data-stu-id="a2f38-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="a2f38-198">Mencione las entradas del menú</span><span class="sxs-lookup"><span data-stu-id="a2f38-198">Mentioning menu entries</span></span>

<span data-ttu-id="a2f38-199">Al mencionar una entrada de menú en la que un usuario debe hacer clic, la convención actual es: Project > Files > Create > Leaf (Crear *> hoja).*</span><span class="sxs-lookup"><span data-stu-id="a2f38-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="a2f38-200">Vínculos</span><span class="sxs-lookup"><span data-stu-id="a2f38-200">Links</span></span>

<span data-ttu-id="a2f38-201">Inserte tantos vínculos útiles a otras páginas como sea posible, pero cada vínculo solo una vez.</span><span class="sxs-lookup"><span data-stu-id="a2f38-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="a2f38-202">Supongamos que un lector hace clic en cada vínculo de la página y piensa en lo molesto que sería, si la misma página se abre 20 veces.</span><span class="sxs-lookup"><span data-stu-id="a2f38-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="a2f38-203">Prefiere los vínculos insertados en una oración:</span><span class="sxs-lookup"><span data-stu-id="a2f38-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="a2f38-204">BAD: las directrices son útiles.</span><span class="sxs-lookup"><span data-stu-id="a2f38-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="a2f38-205">Consulte [este capítulo para](../contributing/documentation-guide.md) obtener más información.</span><span class="sxs-lookup"><span data-stu-id="a2f38-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="a2f38-206">BUENO: [Las directrices](documentation-guide.md) son útiles.</span><span class="sxs-lookup"><span data-stu-id="a2f38-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="a2f38-207">Evite los vínculos externos, ya que pueden quedar obsoletos o contener contenido con derechos de autor.</span><span class="sxs-lookup"><span data-stu-id="a2f38-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="a2f38-208">Al agregar un vínculo, considere si también debe aparecer en la [sección Ver](#see-also) también.</span><span class="sxs-lookup"><span data-stu-id="a2f38-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="a2f38-209">De forma similar, compruebe si se debe agregar un vínculo a la nueva página a la página vinculada.</span><span class="sxs-lookup"><span data-stu-id="a2f38-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="a2f38-210">Imágenes o capturas de pantalla</span><span class="sxs-lookup"><span data-stu-id="a2f38-210">Images / screenshots</span></span>

<span data-ttu-id="a2f38-211">**Use las capturas de pantalla con moderación.**</span><span class="sxs-lookup"><span data-stu-id="a2f38-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="a2f38-212">Mantener imágenes en la documentación es mucho trabajo, los pequeños cambios en la interfaz de usuario pueden hacer que muchas capturas de pantalla no funcionen.</span><span class="sxs-lookup"><span data-stu-id="a2f38-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="a2f38-213">Las reglas siguientes reducirán el esfuerzo de mantenimiento:</span><span class="sxs-lookup"><span data-stu-id="a2f38-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="a2f38-214">No use capturas de pantalla para las cosas que se pueden describir en texto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="a2f38-215">En especial, **nunca captura de pantalla una cuadrícula de propiedades** con el único fin de mostrar los nombres de propiedad y los valores.</span><span class="sxs-lookup"><span data-stu-id="a2f38-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="a2f38-216">No incluya cosas en una captura de pantalla que sean irrelevantes para lo que se muestra.</span><span class="sxs-lookup"><span data-stu-id="a2f38-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="a2f38-217">Por ejemplo, cuando se muestra un efecto de representación, realice una captura de pantalla de la ventanilla, pero excluya cualquier interfaz de usuario que la rodea.</span><span class="sxs-lookup"><span data-stu-id="a2f38-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="a2f38-218">Al mostrar alguna interfaz de usuario, intente mover las ventanas de forma que solo esa parte importante esté en la imagen.</span><span class="sxs-lookup"><span data-stu-id="a2f38-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="a2f38-219">Al incluir la interfaz de usuario de captura de pantalla, solo se muestran las partes importantes.</span><span class="sxs-lookup"><span data-stu-id="a2f38-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="a2f38-220">Por ejemplo, al hablar de botones en una barra de herramientas, realice una imagen pequeña que muestre los botones importantes de la barra de herramientas, pero excluya todo lo que le rodea.</span><span class="sxs-lookup"><span data-stu-id="a2f38-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="a2f38-221">Use solo imágenes que sean fáciles de reproducir.</span><span class="sxs-lookup"><span data-stu-id="a2f38-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="a2f38-222">Esto significa que no pinte marcadores ni resaltados en capturas de pantalla.</span><span class="sxs-lookup"><span data-stu-id="a2f38-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="a2f38-223">En primer lugar, no hay reglas coherentes en cuanto a su aspecto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="a2f38-224">En segundo lugar, reproducir este tipo de captura de pantalla es un esfuerzo adicional.</span><span class="sxs-lookup"><span data-stu-id="a2f38-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="a2f38-225">En su lugar, describa las partes importantes del texto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="a2f38-226">Hay excepciones a esta regla, pero son poco frecuentes.</span><span class="sxs-lookup"><span data-stu-id="a2f38-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="a2f38-227">Obviamente, es mucho más esfuerzo volver a crear un GIF animado.</span><span class="sxs-lookup"><span data-stu-id="a2f38-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="a2f38-228">Espere ser responsable de volver a crearla hasta el final del tiempo o espere que los usuarios lo lancen, si no quieren dedicar ese tiempo.</span><span class="sxs-lookup"><span data-stu-id="a2f38-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="a2f38-229">Mantenga bajo el número de imágenes de un artículo.</span><span class="sxs-lookup"><span data-stu-id="a2f38-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="a2f38-230">A menudo, un buen método consiste en realizar una captura de pantalla general de alguna herramienta, que muestra todo y, a continuación, describir el resto en texto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="a2f38-231">Esto facilita la sustitución de la captura de pantalla cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="a2f38-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="a2f38-232">Otros aspectos:</span><span class="sxs-lookup"><span data-stu-id="a2f38-232">Some other aspects:</span></span>

- <span data-ttu-id="a2f38-233">La interfaz de usuario del editor para las capturas de pantalla debe usar el editor de temas de color gris claro, ya que no todos los usuarios tienen acceso al tema oscuro y nos gustaría mantener las cosas lo más coherentes posible.</span><span class="sxs-lookup"><span data-stu-id="a2f38-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="a2f38-234">El ancho de imagen predeterminado es de 500 píxeles, ya que se muestra bien en la mayoría de los monitores.</span><span class="sxs-lookup"><span data-stu-id="a2f38-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="a2f38-235">Intente no desviarse demasiado de él.</span><span class="sxs-lookup"><span data-stu-id="a2f38-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="a2f38-236">El ancho de 800 píxeles debe ser el máximo.</span><span class="sxs-lookup"><span data-stu-id="a2f38-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="a2f38-237">Use PNG para capturas de pantalla de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="a2f38-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="a2f38-238">Use PNG o JPG para capturas de pantalla de ventanilla 3D.</span><span class="sxs-lookup"><span data-stu-id="a2f38-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="a2f38-239">Prefiere la calidad sobre la relación de compresión.</span><span class="sxs-lookup"><span data-stu-id="a2f38-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="a2f38-240">Lista de propiedades de componente</span><span class="sxs-lookup"><span data-stu-id="a2f38-240">List of component properties</span></span>

<span data-ttu-id="a2f38-241">Al documentar una lista de propiedades, use texto en negrita para resaltar el nombre de propiedad y, a continuación, saltos de línea y texto normal para describirlos.</span><span class="sxs-lookup"><span data-stu-id="a2f38-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="a2f38-242">No use sub capítulos ni listas de puntos de viñeta.</span><span class="sxs-lookup"><span data-stu-id="a2f38-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="a2f38-243">Además, no olvide finalizar todas las oraciones con un punto.</span><span class="sxs-lookup"><span data-stu-id="a2f38-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="a2f38-244">Lista de comprobación de finalización de página</span><span class="sxs-lookup"><span data-stu-id="a2f38-244">Page completion checklist</span></span>

1. <span data-ttu-id="a2f38-245">Asegúrese de que se han seguido las directrices de este documento.</span><span class="sxs-lookup"><span data-stu-id="a2f38-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="a2f38-246">Examine la estructura del documento y vea si el nuevo documento se puede mencionar en la [sección Ver](#see-also) también de otras páginas.</span><span class="sxs-lookup"><span data-stu-id="a2f38-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="a2f38-247">Si está disponible, haga que alguien con conocimientos del tema lea la página para conocer la corrección técnica.</span><span class="sxs-lookup"><span data-stu-id="a2f38-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="a2f38-248">Haga que alguien lea a prueba la página para el estilo y el formato.</span><span class="sxs-lookup"><span data-stu-id="a2f38-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="a2f38-249">Puede ser alguien que no esté familiarizado con el tema, lo que también es una buena idea para obtener comentarios sobre lo comprensible que es la documentación.</span><span class="sxs-lookup"><span data-stu-id="a2f38-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="a2f38-250">Documentación de origen</span><span class="sxs-lookup"><span data-stu-id="a2f38-250">Source documentation</span></span>

<span data-ttu-id="a2f38-251">La documentación de la API se generará automáticamente a partir de los archivos de origen de MRTK.</span><span class="sxs-lookup"><span data-stu-id="a2f38-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="a2f38-252">Para facilitar esto, los archivos de código fuente deben contener lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a2f38-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="a2f38-253">Bloques de resumen de clase, estructura y enumeración</span><span class="sxs-lookup"><span data-stu-id="a2f38-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="a2f38-254">Bloques de resumen de propiedades, métodos y eventos</span><span class="sxs-lookup"><span data-stu-id="a2f38-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="a2f38-255">Versión de introducción de características y dependencias</span><span class="sxs-lookup"><span data-stu-id="a2f38-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="a2f38-256">Campos serializados</span><span class="sxs-lookup"><span data-stu-id="a2f38-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="a2f38-257">Valores de enumeración</span><span class="sxs-lookup"><span data-stu-id="a2f38-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="a2f38-258">Además de lo anterior, el código debe estar bien comentado para permitir el mantenimiento, las correcciones de errores y la facilidad de personalización.</span><span class="sxs-lookup"><span data-stu-id="a2f38-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="a2f38-259">Bloques de resumen de clase, estructura y enumeración</span><span class="sxs-lookup"><span data-stu-id="a2f38-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="a2f38-260">Si se agrega una clase, estructura o enumeración a MRTK, se debe describir su propósito.</span><span class="sxs-lookup"><span data-stu-id="a2f38-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="a2f38-261">Esto es para tomar la forma de un bloque de resumen encima de la clase .</span><span class="sxs-lookup"><span data-stu-id="a2f38-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="a2f38-262">Si hay dependencias de nivel de clase, deben documentarse en un bloque de comentarios, inmediatamente debajo del resumen.</span><span class="sxs-lookup"><span data-stu-id="a2f38-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="a2f38-263">No se aprobarán las solicitudes de extracción enviadas sin resúmenes para clases, estructuras o enumeraciones.</span><span class="sxs-lookup"><span data-stu-id="a2f38-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="a2f38-264">Bloques de resumen de propiedades, métodos y eventos</span><span class="sxs-lookup"><span data-stu-id="a2f38-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="a2f38-265">Las propiedades, los métodos y los eventos (PME), así como los campos, se documentan con bloques de resumen, independientemente de la visibilidad del código (pública, privada, protegida e interna).</span><span class="sxs-lookup"><span data-stu-id="a2f38-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="a2f38-266">La herramienta de generación de documentación es responsable de filtrar y publicar solo las características públicas y protegidas.</span><span class="sxs-lookup"><span data-stu-id="a2f38-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="a2f38-267">NOTA: No se requiere un bloque **de** resumen para los métodos de Unity (por ejemplo: Activo, Iniciar, Actualizar).</span><span class="sxs-lookup"><span data-stu-id="a2f38-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="a2f38-268">La documentación de PME **es necesaria** para que se apruebe una solicitud de extracción.</span><span class="sxs-lookup"><span data-stu-id="a2f38-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="a2f38-269">Como parte de un bloque de resumen de PME, se requiere el significado y el propósito de los parámetros y los datos devueltos.</span><span class="sxs-lookup"><span data-stu-id="a2f38-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="a2f38-270">Versión de introducción de características y dependencias</span><span class="sxs-lookup"><span data-stu-id="a2f38-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="a2f38-271">Como parte de la documentación de resumen de la API, la información sobre la versión de MRTK en la que se introdujo la característica y las dependencias deben documentarse en un bloque de comentarios.</span><span class="sxs-lookup"><span data-stu-id="a2f38-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="a2f38-272">Las dependencias deben incluir dependencias de extensión o plataforma.</span><span class="sxs-lookup"><span data-stu-id="a2f38-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="a2f38-273">Campos serializados</span><span class="sxs-lookup"><span data-stu-id="a2f38-273">Serialized fields</span></span>

<span data-ttu-id="a2f38-274">Es una buena práctica usar el atributo de información sobre herramientas de Unity para proporcionar documentación en tiempo de ejecución para los campos de un script en el inspector.</span><span class="sxs-lookup"><span data-stu-id="a2f38-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="a2f38-275">Para que las opciones de configuración se incluyan  en la documentación de la API, los scripts deben incluir al menos el contenido de la información sobre herramientas en un bloque de resumen.</span><span class="sxs-lookup"><span data-stu-id="a2f38-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="a2f38-276">Valores de enumeración</span><span class="sxs-lookup"><span data-stu-id="a2f38-276">Enumeration values</span></span>

<span data-ttu-id="a2f38-277">Al definir y enumerar, el código también debe documentar el significado de los valores de enumeración mediante un bloque de resumen.</span><span class="sxs-lookup"><span data-stu-id="a2f38-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="a2f38-278">Opcionalmente, los bloques de comentarios se pueden usar para proporcionar detalles adicionales para mejorar la comprensión.</span><span class="sxs-lookup"><span data-stu-id="a2f38-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="a2f38-279">Documentación de procedimientos</span><span class="sxs-lookup"><span data-stu-id="a2f38-279">How-to documentation</span></span>

<span data-ttu-id="a2f38-280">Es posible que muchos Mixed Reality Toolkit no necesiten usar la documentación de la API.</span><span class="sxs-lookup"><span data-stu-id="a2f38-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="a2f38-281">Estos usuarios aprovecharán nuestros prefabs y scripts reutilizables y creados previamente para crear sus experiencias.</span><span class="sxs-lookup"><span data-stu-id="a2f38-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="a2f38-282">Cada área de características contendrá uno o varios archivos markdown (.md) que describen en un nivel bastante alto, lo que se proporciona.</span><span class="sxs-lookup"><span data-stu-id="a2f38-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="a2f38-283">Según el tamaño o la complejidad de un área de características determinada, puede que sea necesario tener archivos adicionales, hasta uno por cada característica proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a2f38-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="a2f38-284">Cuando se agrega una característica (o se cambia el uso), se debe proporcionar documentación general.</span><span class="sxs-lookup"><span data-stu-id="a2f38-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="a2f38-285">Como parte de esta documentación, se deben proporcionar secciones de pasos, incluidas las ilustraciones, para ayudar a los clientes nuevos en una característica o concepto en la introducción.</span><span class="sxs-lookup"><span data-stu-id="a2f38-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="a2f38-286">Documentación de diseño</span><span class="sxs-lookup"><span data-stu-id="a2f38-286">Design documentation</span></span>

<span data-ttu-id="a2f38-287">Mixed Reality ofrece la oportunidad de crear mundos completamente nuevos.</span><span class="sxs-lookup"><span data-stu-id="a2f38-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="a2f38-288">Es probable que parte de esto implique la creación de recursos personalizados para su uso con MRTK.</span><span class="sxs-lookup"><span data-stu-id="a2f38-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="a2f38-289">Para que esto sea lo más libre posible para los clientes, los componentes deben proporcionar documentación de diseño que describa cualquier formato u otros requisitos para los recursos de arte.</span><span class="sxs-lookup"><span data-stu-id="a2f38-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="a2f38-290">Algunos ejemplos en los que la documentación de diseño puede ser útil:</span><span class="sxs-lookup"><span data-stu-id="a2f38-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="a2f38-291">Modelos de cursor</span><span class="sxs-lookup"><span data-stu-id="a2f38-291">Cursor models</span></span>
- <span data-ttu-id="a2f38-292">Visualizaciones de asignaciones espaciales</span><span class="sxs-lookup"><span data-stu-id="a2f38-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="a2f38-293">Archivos de efecto de sonido</span><span class="sxs-lookup"><span data-stu-id="a2f38-293">Sound effect files</span></span>

<span data-ttu-id="a2f38-294">Este tipo de documentación es **muy** recomendable y **se puede** solicitar como parte de una revisión de solicitud de extracción.</span><span class="sxs-lookup"><span data-stu-id="a2f38-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="a2f38-295">Esto puede ser o no diferente de la recomendación de diseño en el sitio [de MS Developer](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="a2f38-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="a2f38-296">Notas de rendimiento</span><span class="sxs-lookup"><span data-stu-id="a2f38-296">Performance notes</span></span>

<span data-ttu-id="a2f38-297">Algunas características importantes tienen un costo de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="a2f38-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="a2f38-298">A menudo, este código dependerá mucho de cómo se configuren.</span><span class="sxs-lookup"><span data-stu-id="a2f38-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="a2f38-299">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a2f38-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="a2f38-300">Se recomiendan notas de rendimiento para los componentes pesados de CPU o GPU y **se** pueden solicitar como parte de una revisión de la solicitud de extracción.</span><span class="sxs-lookup"><span data-stu-id="a2f38-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="a2f38-301">Las notas de rendimiento aplicables se incluirán en la documentación de api **y** de información general.</span><span class="sxs-lookup"><span data-stu-id="a2f38-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="a2f38-302">Últimos cambios</span><span class="sxs-lookup"><span data-stu-id="a2f38-302">Breaking changes</span></span>

<span data-ttu-id="a2f38-303">La documentación de cambios importantes consiste en un archivo de [nivel](../contributing/breaking-changes.md) superior que se vincula a los datos individuales de cada área breaking-changes.md.</span><span class="sxs-lookup"><span data-stu-id="a2f38-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="a2f38-304">El área de características breaking-changes.md archivos deben contener la lista de  todos los cambios importantes conocidos de una versión determinada, así como el historial de cambios importantes de versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="a2f38-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="a2f38-305">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a2f38-305">For example:</span></span>

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

<span data-ttu-id="a2f38-306">La información contenida en el nivel de característica breaking-changes.md archivos se agregará a las notas de la versión de cada nueva versión de MRTK.</span><span class="sxs-lookup"><span data-stu-id="a2f38-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="a2f38-307">Los cambios importantes que forman parte de un cambio **deben** documentarse como parte de una solicitud de extracción.</span><span class="sxs-lookup"><span data-stu-id="a2f38-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="a2f38-308">Herramientas para editar MarkDown</span><span class="sxs-lookup"><span data-stu-id="a2f38-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="a2f38-309">[Visual Studio Code](https://code.visualstudio.com/) es una excelente herramienta para editar archivos Markdown que forman parte de la documentación de MRTK.</span><span class="sxs-lookup"><span data-stu-id="a2f38-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="a2f38-310">Al escribir documentación, también se recomienda encarecidamente instalar las dos extensiones siguientes:</span><span class="sxs-lookup"><span data-stu-id="a2f38-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="a2f38-311">Extensión Markdown de Docs Visual Studio Code: use Alt+M para abrir un menú de opciones de creación de documentos.</span><span class="sxs-lookup"><span data-stu-id="a2f38-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="a2f38-312">Corrector ortográfico de código: las palabras mal escritas se subrayan; Haga clic con el botón derecho en una palabra mal escrita para cambiarla o guardarla en el diccionario.</span><span class="sxs-lookup"><span data-stu-id="a2f38-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="a2f38-313">Ambos vienen empaquetados en el paquete de creación de Docs publicado por Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a2f38-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2f38-314">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a2f38-314">See also</span></span>

- [<span data-ttu-id="a2f38-315">Vínculo de ejemplo "ver también" para la documentación</span><span class="sxs-lookup"><span data-stu-id="a2f38-315">Example "see also" link for documentation</span></span>](https://www.microsoft.com)
