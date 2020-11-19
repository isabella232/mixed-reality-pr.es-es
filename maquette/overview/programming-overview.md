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
# <a name="programming-overview"></a>Información general sobre programación

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logotipo](../images/MaquetteIcon.png) Información general sobre programación

Microsoft Maquette usa JavaScript (ECMAScript 5,1 con extensiones) basado en el intérprete de [Jint](https://github.com/sebastienros/jint) . La extensión `.mqjs` se usa para distinguir los archivos de JavaScript de Maquette de JavaScript normal.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Se puede acceder a los objetos e interfaces Maquette mediante el `Maquette` objeto. La documentación sobre objetos e interfaces de Maquette se proporciona en referencia de la API de Maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript es una nueva adición y en flujo, por lo que se deberían esperar cambios. Pronto encontrará documentación y actualizaciones más detalladas.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Spotlight en scripting

* TBD: scripting de Spotlight centrados en ejemplos o tutoriales
  * 2x imágenes/título: vínculo a la página Spotlight

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Introducción a MaquetteScript

* Mqjs frente a JS
* Modelo de programación
  * Edición frente a ejecución
* Vínculo a flujo de trabajo de programación
* Vínculo a los resultados de uso compartido

## <a name="programming-workflow"></a>Flujo de trabajo de programación

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Operación de scripting
* Operación del depurador
* Bucle de depuración
* ¿Copiar y pegar código?

## <a name="running-mqjs-scripts"></a>Ejecutar scripts. mqjs

<!-- TODO(Stefan): Need screenshot -->
Para ejecutar un archivo MaquetteScript. mqjs, vaya a las ventanas complementarias de Maquette y abra la pestaña scripting para buscar scripts.

> [!NOTE] 
> Algunas opciones no funcionarán todavía porque no se han enviado los scripts.

## <a name="vscode-editor-workflow"></a>Flujo de trabajo del editor de VSCode

Para evaluar el script en Maquette desde VSCode, el usuario debe conocer dos comandos:

   `CTRL-5` evalúa el texto seleccionado o la línea completa donde se encuentra el cursor. 

   `CTRL-SHIFT-5` evalúa el archivo completo.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
El texto se envía a Maquette, se evalúa en el entorno de JavaScript y el resultado se devuelve a la consola de salida de VSCode. Se puede usar como REPL (Read-eval-Print-Loop).

## <a name="example-first-step"></a>Primer paso de ejemplo

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Copie el código siguiente en un archivo en VSCode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Seleccione el código o simplemente secciones y presione `CTRL-5` Ejecutar. Esto debe crear un cubo, colocarlo delante de usted y cambiar su color.

Hay más ejemplos para buscar a través de la extensión.

## <a name="sharing-results"></a>Resultados de uso compartido

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Cómo compartir entre usuarios y equipos
* Proyecto zip en el directorio de documentos
* Copiar proyecto en recurso compartido de archivos
* Adición de la ubicación del archivo de envío del recurso compartido de equipo al equipo de Maquette

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Incluye, referencia a código en otro lugar con rutas de acceso relativas/absolutas, módulos
* Libre?
* Compatibilidad con el tiempo de ejecución
* Externos sin resolver: comportamiento cuando faltan entradas o se bloquean
* ¿Se puede Agregar, editar y observar el script asociado a objetos específicos?
  * ¿Se puede copiar y pegar este script en otro lugar?
  * ¿Qué ocurre con las propiedades de objeto?
  * ¿Asignar nombres a objetos en mi escena? (cambiar el nombre del script con él)
  * Esta palabra clave SELF para el script asociado a un objeto
  * Si hago clic con el botón secundario en un objeto, ¿puedo ver el código asociado a él (y toda su jerarquía)?
  * ¿Puedo seleccionar en la interfaz de usuario para que se ponga en el código de VSCode?
  * ¿Mantener el código asociado a un objeto "juntos" en el archivo de código fuente del script?
  * Traer la ventana de propiedades de un objeto al hacer clic en él En la pestaña de VR y en la principal?
* Problemas de seguridad
* Pruebas: podría ser TBD, pero podríamos sugerir vídeo o captación de fotogramas por script
* Si tenemos un mecanismo de notificación de errores, podríamos hacer que sea accesible a través de script para otros (?)... después
* Implementación: Cómo "compartir" el resultado, paquete como EXE
* Ejecución o control de una demostración o spectating/supervisión
* Modo de reproductor
* Podríamos tener un segmento sobre cómo crear "componentes" para compartir? (puede que sea TBD)
  * ¿Hay #include? Esto controla el JS puro que supongo, pero puede tener conflictos de espacio de nombres.
  * ¿Hay algo que podríamos hacer para que un Maquette incorpore algún otro Maquette con objetos con nombre para que coincida con el código JS?
