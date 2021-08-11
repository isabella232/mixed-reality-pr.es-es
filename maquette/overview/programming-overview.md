---
title: Información general sobre la programación
description: Obtenga información sobre cómo acceder a objetos e interfaces de Maquette con scripting.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototyping, Mixed Reality, Virtual Reality, VR, MR, Feedback, Centro de opiniones, bugs
ms.openlocfilehash: 969a4aedb60d947782acb41742b33f275e7c841c1989144b586b0329db3c3b57
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197879"
---
# <a name="programming-overview"></a>Información general sobre la programación

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logotipo](../images/MaquetteIcon.png) Introducción a la programación

Microsoft Maquette usa JavaScript (ECMAScript 5.1 con extensiones) basado en el [intérprete de Jint.](https://github.com/sebastienros/jint) La extensión `.mqjs` se usa para distinguir los archivos JavaScript de Maquette de JavaScript normal.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Los objetos e interfaces de Maquette son accesibles y se pueden incluir en scripts a través del `Maquette` objeto . La documentación sobre objetos e interfaces de Maquette se proporciona en la referencia de API de Maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript es una nueva adición y en flux, por lo que se deben esperar cambios. La documentación y las actualizaciones más detalladas estarán disponibles próximamente.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Destacados sobre scripting

* TBD: destacados de scripting centrados en ejemplos y tutoriales
  * 2x Images/Caption: vínculo a la página de contenido destacado

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Introducción a MaquetteScript

* Mqjs frente a JS
* Modelo de programación
  * Edición frente a ejecución
* Vínculo al flujo de trabajo de programación
* Vínculo a resultados de uso compartido

## <a name="programming-workflow"></a>Flujo de trabajo de programación

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Operación de scripting
* Operación del depurador
* Bucle de depuración
* ¿Copiar y pegar código?

## <a name="running-mqjs-scripts"></a>Ejecución de scripts .mqjs

<!-- TODO(Stefan): Need screenshot -->
Para ejecutar un archivo .mqjs de MaquetteScript, vaya a las ventanas complementarias de Maquette y abra la pestaña scripting para buscar scripts.

> [!NOTE] 
> Algunas opciones no funcionarán todavía porque no se han incluido los scripts.

## <a name="vscode-editor-workflow"></a>Flujo de trabajo del Editor de VSCode

Para evaluar el script en Maquette desde VSCode, el usuario debe conocer dos comandos:

   `CTRL-5` evalúa el texto seleccionado o toda la línea donde se encuentra el cursor. 

   `CTRL-SHIFT-5` evalúa todo el archivo.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
El texto se envía a Maquette, se evalúa en el entorno de JavaScript y el resultado se envía de vuelta a la consola de salida de VSCode. Se puede usar como REPL (read-eval-print-loop).

## <a name="example-first-step"></a>Primer paso de ejemplo

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Copie el código siguiente en un archivo de VSCode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Seleccione el código o solo las secciones y presione `CTRL-5` para ejecutar. Esto debería crear un cubo, colocarlo delante de usted y cambiar su color.

Hay más ejemplos para buscar a través de la extensión.

## <a name="sharing-results"></a>Compartir resultados

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Cómo compartir entre usuarios o equipos
* Proyecto ZIP en el directorio documents
* Copia de un proyecto en un recurso compartido de archivos
* Adición de la ubicación del archivo de envíos de recurso compartido de equipo al equipo de Maquette

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Incluye, referencia a código en otro lugar con rutas de acceso relativas o absolutas, módulos
* ¿Bibliotecas?
* Compatibilidad con el tiempo de ejecución
* Externos sin resolver: comportamiento cuando faltan entradas o se bloquean
* ¿Se puede agregar, editar o observar el script asociado a objetos específicos?
  * ¿Podemos copiar y pegar este script en otro lugar?
  * ¿Qué sucede con las propiedades del objeto?
  * ¿Asignar nombres a los objetos de mi escena? (cambiar el nombre del script por él)
  * Palabra clave THIS o SELF para el script asociado a un objeto
  * Si hago clic con el botón derecho en un objeto, puedo ver el código asociado a él (y toda su jerarquía).
  * ¿Puedo seleccionar en la interfaz de usuario y mostrarme en el código de VSCode?
  * ¿Mantener el código asociado a un objeto "junto" en el archivo de origen del script?
  * ¿Abre la ventana de propiedades de un objeto al hacer clic en él? ¿En VR y en la pestaña principal?
* Problemas de seguridad
* Pruebas: podría ser TBD, pero se podría sugerir la captura de vídeo o fotograma por script
* Si tenemos un mecanismo de informes de errores, podemos hacer que sea accesible a través del script para otros (?) ... Más tarde
* Implementación: cómo "compartir" el resultado, empaquetar como EXE
* Ejecución o control de una demostración o especificación/supervisión
* Modo de reproductor
* ¿Podemos tener un segmento sobre cómo crear "componentes" para compartir? (puede ser tbd)
  * ¿Hay #include? Esto controla JS puro, pero puede tener conflictos de espacio de nombres.
  * ¿Hay algo que podamos hacer para que un maquette incorpore algún otro maquette con objetos con nombre para que coincidan con el código JS?
