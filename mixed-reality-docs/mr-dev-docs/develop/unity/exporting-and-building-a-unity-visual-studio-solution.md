---
title: Exportación y creación de una solución de Visual Studio para Unity
description: En este artículo se describe la exportación del proyecto de realidad mixta desde Unity para que pueda compilar e implementar en Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, export, build, deploy, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset, UWP, deploying
ms.openlocfilehash: 78410da352b1cce1377b35737376437608f3017c00334c1a489ede26d5170d2d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203627"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportación y creación de una solución de Visual Studio para Unity

Si la aplicación no necesita el teclado del sistema, nuestra recomendación es usar *D3D* para que la aplicación use un poco menos memoria y un tiempo de inicio más rápido. Sin embargo, si usa el teclado del sistema a través de la API TouchScreenKeyboard, debe exportar el proyecto como *XAML.*

## <a name="how-to-export-from-unity"></a>Cómo exportar desde Unity

![Configuración de compilación de Unity](images/unitybuildsettings-300px.png)<br>
*Configuración de compilación en el editor de Unity*

1. Cuando esté listo para exportar el proyecto desde Unity, abra el **menú** Archivo y seleccione **Compilar Configuración...**
2. Seleccione **Agregar escenas abiertas** para agregar la escena a la compilación.
3. En el **cuadro de diálogo Configuración** compilación, elija las siguientes opciones para exportar HoloLens:
   * **Plataforma:** *plataforma Windows universal y* asegúrese de seleccionar Cambiar **plataforma** para que la selección suba.
   * **SDK:** *Universal 10.*
   * **Tipo de compilación de UWP:** *D3D*.
4. **Opcional:** **Proyectos de C# de Unity:** activado.

>[!NOTE]
>Si se marca esta casilla, podrá:
>* Depure la aplicación en el Visual Studio remoto.
>* Edite scripts en el proyecto de C# de Unity mientras usa IntelliSense para las API de WinRT.

5. En la **ventana Build Configuración... (Compilar Configuración...),** abra **Player Configuración...**
6. Seleccione la **Configuración la pestaña Plataforma Windows** universal.
7. Expanda el grupo **XR Settings** (Configuración de XR).
8. En la **sección XR Configuración,** active la casilla Virtual Reality Supported (Compatible con Virtual **Reality)** para agregar una nueva lista de dispositivos de realidad **virtual** y confirme que **"Windows Mixed Reality"** aparece como un dispositivo compatible.
9. Vuelva al cuadro **de diálogo Configuración** compilación.
10. Seleccione **Build** (Compilar).
11. En el Windows explorer que aparece, cree una carpeta para contener la salida de compilación de Unity. Por lo general, la carpeta se llama "App".
12. Seleccione la carpeta recién creada y seleccione **Seleccionar carpeta.**
13. Una vez que Unity haya terminado de compilarse, se abrirá Windows explorador en el directorio raíz del proyecto. Vaya a la carpeta recién creada.
14. Abra el archivo Visual Studio solución que se encuentra dentro de esta carpeta.

## <a name="when-to-re-export-from-unity"></a>Cuándo volver a exportar desde Unity

Al activar la casilla Proyectos de **C#** al exportar la aplicación desde Unity, se crea Visual Studio solución que incluye todos los archivos de script de Unity. Tener todos los scripts en un solo lugar le permite iterar sin volver a exportar desde Unity. Sin embargo, si realiza cambios en el proyecto que no solo cambian el contenido de los scripts, deberá volver a exportar desde Unity. Algunos ejemplos de veces que necesita volver a exportar desde Unity son:
* Puede agregar o quitar recursos en la pestaña Project datos.
* Puede cambiar cualquier valor en la pestaña Inspector.
* Puede agregar o quitar objetos de la pestaña Jerarquía.
* Se cambia cualquier configuración de proyecto de Unity.

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Creación e implementación de una solución de Visual Studio Unity

El resto de la creación e implementación de aplicaciones se produce en [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Deberá especificar una configuración de compilación de Unity. Las convenciones de nomenclatura de Unity pueden diferir de lo que está acostumbrado en Visual Studio:

|  Configuración  |  Explicación | 
|----------|----------|
|  Depurar  |  Todas las optimizaciones desactivadas y el profiler está habilitado. Se usa para depurar scripts. | 
|  Master  |  Todas las optimizaciones están activadas y el profiler está deshabilitado. Se usa para enviar aplicaciones a la Tienda. | 
|  Release  |  Todas las optimizaciones están activadas y el profiler está habilitado. Se usa para evaluar el rendimiento de la aplicación. | 

Tenga en cuenta que la lista anterior es un subconjunto de los desencadenadores comunes que harán que el Visual Studio proyecto tenga que generarse. En general, la edición de archivos .cs Visual Studio no requerirá que el proyecto se vuelva a generar desde Unity.

## <a name="troubleshooting"></a>Solución de problemas

Si ve que las ediciones de los archivos .cs no se reconocen en el proyecto de Visual Studio, asegúrese de que proyectos de C# de Unity se comprueban al generar el proyecto de VS desde el menú Compilar de **Unity.**
