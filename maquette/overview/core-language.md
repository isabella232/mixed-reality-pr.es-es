---
title: Lenguaje básico
description: Obtenga información sobre los detalles principales del lenguaje de Maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipo, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935628"
---
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="5342a-104">Detalles de idioma de MaquetteScript Core</span><span class="sxs-lookup"><span data-stu-id="5342a-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="5342a-105">![Maquette logo ](../images/MaquetteIcon.png) MaquetteScript Core Language details</span><span class="sxs-lookup"><span data-stu-id="5342a-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="5342a-106">Obtener acceso a `Maquette` objetos y espacios de nombres</span><span class="sxs-lookup"><span data-stu-id="5342a-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="5342a-107">Maquette expone objetos e interfaces internos en JavaScript a través del `Maquette` objeto y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="5342a-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="5342a-108">Esta funcionalidad se describe en el [objeto Maquette y](https://www.maquette.ms/doc_staging/objects/Maquette.html) en la documentación del espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="5342a-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="5342a-109">El `Maquette` objeto tiene funciones de nivel superior para facilitar la interacción con el propio Maquette y facilitar la resolución de problemas repetitivos.</span><span class="sxs-lookup"><span data-stu-id="5342a-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="5342a-110">Esto se describe en la documentación de [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span><span class="sxs-lookup"><span data-stu-id="5342a-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="5342a-111">Inicio y carga de Maquette</span><span class="sxs-lookup"><span data-stu-id="5342a-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="5342a-112">Maquette cargará y evaluará determinados archivos JavaScript para habilitar la configuración, la instalación y la inicialización en las siguientes ocasiones:</span><span class="sxs-lookup"><span data-stu-id="5342a-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="5342a-113">Durante el inicio de Maquette:</span><span class="sxs-lookup"><span data-stu-id="5342a-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="5342a-114">Cada vez que se carga algún proyecto:</span><span class="sxs-lookup"><span data-stu-id="5342a-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="5342a-115">Los proyectos cargan sus scripts de proyecto respectivos:</span><span class="sxs-lookup"><span data-stu-id="5342a-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="5342a-116">Implementación de JavaScript</span><span class="sxs-lookup"><span data-stu-id="5342a-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="5342a-117">El intérprete de JavaScript usado en Maquette se basa en [Jint](https://github.com/sebastienros/jint).</span><span class="sxs-lookup"><span data-stu-id="5342a-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="5342a-118">Jint es compatible con ECMAScript 5,1 y admite [extensiones adicionales de ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span><span class="sxs-lookup"><span data-stu-id="5342a-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="5342a-119">La extensión `.mqjs` se usa para distinguir los archivos de JavaScript de Maquette de JavaScript normal.</span><span class="sxs-lookup"><span data-stu-id="5342a-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="5342a-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="5342a-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->