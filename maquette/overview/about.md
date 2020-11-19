---
title: Acerca de Maquette
description: Introducción a Maquette y sus características.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipo, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935622"
---
# <a name="about-maquette"></a><span data-ttu-id="04d1a-104">Acerca de Maquette</span><span class="sxs-lookup"><span data-stu-id="04d1a-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="04d1a-105">![Logotipo ](../images/MaquetteIcon.png) MaquetteScript introducción</span><span class="sxs-lookup"><span data-stu-id="04d1a-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="04d1a-106">Maquette integra ECMA 5,1 JavaScript estándar para permitir la inversión de interactividad en escenas de Maquette y objetos que se pueden editar y ejecutar desde VSCode.</span><span class="sxs-lookup"><span data-stu-id="04d1a-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="04d1a-107">Las propiedades de los objetos se exponen para leer y establecer desde el script, los métodos de objeto denominados y los eventos del objeto y del sistema.</span><span class="sxs-lookup"><span data-stu-id="04d1a-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="04d1a-108">El script también puede interactuar con Maquette a través de objetos del sistema accesibles a través de un script.</span><span class="sxs-lookup"><span data-stu-id="04d1a-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="04d1a-109">Varios controles de interfaz de usuario con los que el usuario puede interactuar son parte del sistema.</span><span class="sxs-lookup"><span data-stu-id="04d1a-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="04d1a-110">Se pueden agregar al crear en Maquette o crearse y administrarse desde el script.</span><span class="sxs-lookup"><span data-stu-id="04d1a-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="04d1a-111">Los eventos de interacción del usuario con estos elementos (entrada de datos, clics, etc.) también se exponen al script como eventos.</span><span class="sxs-lookup"><span data-stu-id="04d1a-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="04d1a-112">Con estas adiciones, se pueden crear escenas simples y complejas, desde experimentos hasta la visualización de datos hasta exploraciones de escenarios de usuarios de realidad mixta hasta experiencias totalmente realizadas en AR o VR.</span><span class="sxs-lookup"><span data-stu-id="04d1a-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="04d1a-113">vídeo de 60 second'ish</span><span class="sxs-lookup"><span data-stu-id="04d1a-113">60 second'ish video</span></span>
* <span data-ttu-id="04d1a-114">Tarjeta de título de entrada</span><span class="sxs-lookup"><span data-stu-id="04d1a-114">Entry Title Card</span></span>
  * <span data-ttu-id="04d1a-115">Creación de contenido de realidad mixta interactiva en Maquette</span><span class="sxs-lookup"><span data-stu-id="04d1a-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="04d1a-116">Scripting e interactividad/sistema de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="04d1a-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="04d1a-117">¿Le agradecen los subtítulos de equipo o vídeo?</span><span class="sxs-lookup"><span data-stu-id="04d1a-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="04d1a-118">explicación</span><span class="sxs-lookup"><span data-stu-id="04d1a-118">explaining:</span></span>
  * <span data-ttu-id="04d1a-119">razonamiento detrás del scripting para habilitar la creación de contenido de MR interactivo</span><span class="sxs-lookup"><span data-stu-id="04d1a-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="04d1a-120">toque cómo se puede usar en trazos de pincel muy amplios</span><span class="sxs-lookup"><span data-stu-id="04d1a-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="04d1a-121">Scripting de vingette en acción</span><span class="sxs-lookup"><span data-stu-id="04d1a-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="04d1a-122">Cuadro de diálogo composición</span><span class="sxs-lookup"><span data-stu-id="04d1a-122">Composing dialog box</span></span>
  * <span data-ttu-id="04d1a-123">Creación de una aplicación a partir del esquema (demostración de la aplicación de cocina)</span><span class="sxs-lookup"><span data-stu-id="04d1a-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="04d1a-124">Redactar en el modelo Photogrammetry</span><span class="sxs-lookup"><span data-stu-id="04d1a-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="04d1a-125">Interactuar con la guía de solución de problemas</span><span class="sxs-lookup"><span data-stu-id="04d1a-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="04d1a-126">Vista de pantalla de la depuración de scripting en VSCode</span><span class="sxs-lookup"><span data-stu-id="04d1a-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="04d1a-127">Obtener acceso a un script desde un objeto de la escena</span><span class="sxs-lookup"><span data-stu-id="04d1a-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="04d1a-128">Etc...</span><span class="sxs-lookup"><span data-stu-id="04d1a-128">Etc...</span></span>
* <span data-ttu-id="04d1a-129">Tarjeta de título de resumen al final</span><span class="sxs-lookup"><span data-stu-id="04d1a-129">Summary Title card at end</span></span>
  * <span data-ttu-id="04d1a-130">Vínculo a Maquette</span><span class="sxs-lookup"><span data-stu-id="04d1a-130">Link to Maquette</span></span>
  * <span data-ttu-id="04d1a-131">Dónde ir a introducción al scripting</span><span class="sxs-lookup"><span data-stu-id="04d1a-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="04d1a-132">Anuncios/estado/comunidad</span><span class="sxs-lookup"><span data-stu-id="04d1a-132">Announcements/status/community</span></span>
  * <span data-ttu-id="04d1a-133">Esperamos ver lo que puede hacer o enviar (?)</span><span class="sxs-lookup"><span data-stu-id="04d1a-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="04d1a-134">Comentarios y cómo podemos ofrecerle un mejor servicio</span><span class="sxs-lookup"><span data-stu-id="04d1a-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="04d1a-135">Introducción</span><span class="sxs-lookup"><span data-stu-id="04d1a-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="04d1a-136">Ejemplos y aplicaciones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="04d1a-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="04d1a-137">Soporte técnico</span><span class="sxs-lookup"><span data-stu-id="04d1a-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="04d1a-138">Envíenos comentarios</span><span class="sxs-lookup"><span data-stu-id="04d1a-138">Send us feedback</span></span>

<span data-ttu-id="04d1a-139">Esperamos tener noticias sobre sus experiencias y resultados.</span><span class="sxs-lookup"><span data-stu-id="04d1a-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="04d1a-140">Comentarios, sugerencias e informes de errores siempre.</span><span class="sxs-lookup"><span data-stu-id="04d1a-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="04d1a-141"><Link? ></span><span class="sxs-lookup"><span data-stu-id="04d1a-141"><Link?></span></span>