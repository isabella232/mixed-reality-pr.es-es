---
title: Información general sobre programación
description: Obtenga información sobre cómo acceder a objetos e interfaces de Maquette con scripting.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototipo, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935604"
---
# <a name="programming-overview"></a><span data-ttu-id="613d9-104">Información general sobre programación</span><span class="sxs-lookup"><span data-stu-id="613d9-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logotipo](../images/MaquetteIcon.png) <span data-ttu-id="613d9-106">Información general sobre programación</span><span class="sxs-lookup"><span data-stu-id="613d9-106">Programming Overview</span></span>

<span data-ttu-id="613d9-107">Microsoft Maquette usa JavaScript (ECMAScript 5,1 con extensiones) basado en el intérprete de [Jint](https://github.com/sebastienros/jint) .</span><span class="sxs-lookup"><span data-stu-id="613d9-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="613d9-108">La extensión `.mqjs` se usa para distinguir los archivos de JavaScript de Maquette de JavaScript normal.</span><span class="sxs-lookup"><span data-stu-id="613d9-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="613d9-109">Se puede acceder a los objetos e interfaces Maquette mediante el `Maquette` objeto.</span><span class="sxs-lookup"><span data-stu-id="613d9-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="613d9-110">La documentación sobre objetos e interfaces de Maquette se proporciona en referencia de la API de Maquette.</span><span class="sxs-lookup"><span data-stu-id="613d9-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="613d9-111">MaquetteScript es una nueva adición y en flujo, por lo que se deberían esperar cambios.</span><span class="sxs-lookup"><span data-stu-id="613d9-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="613d9-112">Pronto encontrará documentación y actualizaciones más detalladas.</span><span class="sxs-lookup"><span data-stu-id="613d9-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="613d9-113">Spotlight en scripting</span><span class="sxs-lookup"><span data-stu-id="613d9-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="613d9-114">TBD: scripting de Spotlight centrados en ejemplos o tutoriales</span><span class="sxs-lookup"><span data-stu-id="613d9-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="613d9-115">2x imágenes/título: vínculo a la página Spotlight</span><span class="sxs-lookup"><span data-stu-id="613d9-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="613d9-116">Introducción a MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="613d9-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="613d9-117">Mqjs frente a JS</span><span class="sxs-lookup"><span data-stu-id="613d9-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="613d9-118">Modelo de programación</span><span class="sxs-lookup"><span data-stu-id="613d9-118">Programming Model</span></span>
  * <span data-ttu-id="613d9-119">Edición frente a ejecución</span><span class="sxs-lookup"><span data-stu-id="613d9-119">Editing vs. Running</span></span>
* <span data-ttu-id="613d9-120">Vínculo a flujo de trabajo de programación</span><span class="sxs-lookup"><span data-stu-id="613d9-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="613d9-121">Vínculo a los resultados de uso compartido</span><span class="sxs-lookup"><span data-stu-id="613d9-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="613d9-122">Flujo de trabajo de programación</span><span class="sxs-lookup"><span data-stu-id="613d9-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="613d9-123">TBD</span><span class="sxs-lookup"><span data-stu-id="613d9-123">TBD</span></span>
* <span data-ttu-id="613d9-124">REPL</span><span class="sxs-lookup"><span data-stu-id="613d9-124">REPL</span></span>
* <span data-ttu-id="613d9-125">Operación de scripting</span><span class="sxs-lookup"><span data-stu-id="613d9-125">Scripting operation</span></span>
* <span data-ttu-id="613d9-126">Operación del depurador</span><span class="sxs-lookup"><span data-stu-id="613d9-126">Debugger operation</span></span>
* <span data-ttu-id="613d9-127">Bucle de depuración</span><span class="sxs-lookup"><span data-stu-id="613d9-127">Debugging loop</span></span>
* <span data-ttu-id="613d9-128">¿Copiar y pegar código?</span><span class="sxs-lookup"><span data-stu-id="613d9-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="613d9-129">Ejecutar scripts. mqjs</span><span class="sxs-lookup"><span data-stu-id="613d9-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="613d9-130">Para ejecutar un archivo MaquetteScript. mqjs, vaya a las ventanas complementarias de Maquette y abra la pestaña scripting para buscar scripts.</span><span class="sxs-lookup"><span data-stu-id="613d9-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="613d9-131">Algunas opciones no funcionarán todavía porque no se han enviado los scripts.</span><span class="sxs-lookup"><span data-stu-id="613d9-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="613d9-132">Flujo de trabajo del editor de VSCode</span><span class="sxs-lookup"><span data-stu-id="613d9-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="613d9-133">Para evaluar el script en Maquette desde VSCode, el usuario debe conocer dos comandos:</span><span class="sxs-lookup"><span data-stu-id="613d9-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="613d9-134">`CTRL-5` evalúa el texto seleccionado o la línea completa donde se encuentra el cursor.</span><span class="sxs-lookup"><span data-stu-id="613d9-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="613d9-135">`CTRL-SHIFT-5` evalúa el archivo completo.</span><span class="sxs-lookup"><span data-stu-id="613d9-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="613d9-136">El texto se envía a Maquette, se evalúa en el entorno de JavaScript y el resultado se devuelve a la consola de salida de VSCode.</span><span class="sxs-lookup"><span data-stu-id="613d9-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="613d9-137">Se puede usar como REPL (Read-eval-Print-Loop).</span><span class="sxs-lookup"><span data-stu-id="613d9-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="613d9-138">Primer paso de ejemplo</span><span class="sxs-lookup"><span data-stu-id="613d9-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="613d9-139">Copie el código siguiente en un archivo en VSCode:</span><span class="sxs-lookup"><span data-stu-id="613d9-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="613d9-140">Seleccione el código o simplemente secciones y presione `CTRL-5` Ejecutar.</span><span class="sxs-lookup"><span data-stu-id="613d9-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="613d9-141">Esto debe crear un cubo, colocarlo delante de usted y cambiar su color.</span><span class="sxs-lookup"><span data-stu-id="613d9-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="613d9-142">Hay más ejemplos para buscar a través de la extensión.</span><span class="sxs-lookup"><span data-stu-id="613d9-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="613d9-143">Resultados de uso compartido</span><span class="sxs-lookup"><span data-stu-id="613d9-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="613d9-144">Cómo compartir entre usuarios y equipos</span><span class="sxs-lookup"><span data-stu-id="613d9-144">How to share between users/teams</span></span>
* <span data-ttu-id="613d9-145">Proyecto zip en el directorio de documentos</span><span class="sxs-lookup"><span data-stu-id="613d9-145">Zip project in documents directory</span></span>
* <span data-ttu-id="613d9-146">Copiar proyecto en recurso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="613d9-146">Copy project to file share</span></span>
* <span data-ttu-id="613d9-147">Adición de la ubicación del archivo de envío del recurso compartido de equipo al equipo de Maquette</span><span class="sxs-lookup"><span data-stu-id="613d9-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="613d9-148">TBD</span><span class="sxs-lookup"><span data-stu-id="613d9-148">TBD</span></span>
* <span data-ttu-id="613d9-149">Incluye, referencia a código en otro lugar con rutas de acceso relativas/absolutas, módulos</span><span class="sxs-lookup"><span data-stu-id="613d9-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="613d9-150">Libre?</span><span class="sxs-lookup"><span data-stu-id="613d9-150">Libraries?</span></span>
* <span data-ttu-id="613d9-151">Compatibilidad con el tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="613d9-151">Runtime support</span></span>
* <span data-ttu-id="613d9-152">Externos sin resolver: comportamiento cuando faltan entradas o se bloquean</span><span class="sxs-lookup"><span data-stu-id="613d9-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="613d9-153">¿Se puede Agregar, editar y observar el script asociado a objetos específicos?</span><span class="sxs-lookup"><span data-stu-id="613d9-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="613d9-154">¿Se puede copiar y pegar este script en otro lugar?</span><span class="sxs-lookup"><span data-stu-id="613d9-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="613d9-155">¿Qué ocurre con las propiedades de objeto?</span><span class="sxs-lookup"><span data-stu-id="613d9-155">What about object properties?</span></span>
  * <span data-ttu-id="613d9-156">¿Asignar nombres a objetos en mi escena?</span><span class="sxs-lookup"><span data-stu-id="613d9-156">Naming objects in my scene?</span></span> <span data-ttu-id="613d9-157">(cambiar el nombre del script con él)</span><span class="sxs-lookup"><span data-stu-id="613d9-157">(renaming script with it)</span></span>
  * <span data-ttu-id="613d9-158">Esta palabra clave SELF para el script asociado a un objeto</span><span class="sxs-lookup"><span data-stu-id="613d9-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="613d9-159">Si hago clic con el botón secundario en un objeto, ¿puedo ver el código asociado a él (y toda su jerarquía)?</span><span class="sxs-lookup"><span data-stu-id="613d9-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="613d9-160">¿Puedo seleccionar en la interfaz de usuario para que se ponga en el código de VSCode?</span><span class="sxs-lookup"><span data-stu-id="613d9-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="613d9-161">¿Mantener el código asociado a un objeto "juntos" en el archivo de código fuente del script?</span><span class="sxs-lookup"><span data-stu-id="613d9-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="613d9-162">Traer la ventana de propiedades de un objeto al hacer clic en él</span><span class="sxs-lookup"><span data-stu-id="613d9-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="613d9-163">En la pestaña de VR y en la principal?</span><span class="sxs-lookup"><span data-stu-id="613d9-163">In VR and in main tab?</span></span>
* <span data-ttu-id="613d9-164">Problemas de seguridad</span><span class="sxs-lookup"><span data-stu-id="613d9-164">Security Issues</span></span>
* <span data-ttu-id="613d9-165">Pruebas: podría ser TBD, pero podríamos sugerir vídeo o captación de fotogramas por script</span><span class="sxs-lookup"><span data-stu-id="613d9-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="613d9-166">Si tenemos un mecanismo de notificación de errores, podríamos hacer que sea accesible a través de script para otros (?)... después</span><span class="sxs-lookup"><span data-stu-id="613d9-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="613d9-167">Implementación: Cómo "compartir" el resultado, paquete como EXE</span><span class="sxs-lookup"><span data-stu-id="613d9-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="613d9-168">Ejecución o control de una demostración o spectating/supervisión</span><span class="sxs-lookup"><span data-stu-id="613d9-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="613d9-169">Modo de reproductor</span><span class="sxs-lookup"><span data-stu-id="613d9-169">Player mode</span></span>
* <span data-ttu-id="613d9-170">Podríamos tener un segmento sobre cómo crear "componentes" para compartir?</span><span class="sxs-lookup"><span data-stu-id="613d9-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="613d9-171">(puede que sea TBD)</span><span class="sxs-lookup"><span data-stu-id="613d9-171">(might  be tbd)</span></span>
  * <span data-ttu-id="613d9-172">¿Hay #include?</span><span class="sxs-lookup"><span data-stu-id="613d9-172">Is there #include?</span></span> <span data-ttu-id="613d9-173">Esto controla el JS puro que supongo, pero puede tener conflictos de espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="613d9-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="613d9-174">¿Hay algo que podríamos hacer para que un Maquette incorpore algún otro Maquette con objetos con nombre para que coincida con el código JS?</span><span class="sxs-lookup"><span data-stu-id="613d9-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
