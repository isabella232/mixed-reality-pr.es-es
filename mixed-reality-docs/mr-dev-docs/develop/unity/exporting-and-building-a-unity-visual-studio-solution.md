---
title: Exportación y creación de una solución de Visual Studio para Unity
description: En este artículo se describe la exportación de un proyecto de realidad mixta desde Unity para que pueda compilar e implementar en Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, exportación, compilación, implementación, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, UWP, implementación
ms.openlocfilehash: 29415fa7d561cab1aec5f0c2c9344fa24b0e8293
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677564"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportación y creación de una solución de Visual Studio para Unity

Si no tiene previsto usar el teclado del sistema en su aplicación, nuestra recomendación es usar *D3D* , ya que la aplicación usará un poco menos de memoria y tendrá un tiempo de inicio ligeramente más rápido. Si usa la API de TouchScreenKeyboard en el proyecto para usar el teclado del sistema, debe exportarlo como *XAML*.

## <a name="how-to-export-from-unity"></a>Cómo exportar desde Unity

![Configuración de compilación de Unity](images/unitybuildsettings-300px.png)<br>
*Configuración de compilación de Unity*

1. Cuando esté listo para exportar el proyecto desde Unity, abra el menú **archivo** y seleccione **configuración de compilación..** .
2. Haga clic en **Agregar escenas abiertas** para agregar la escena a la compilación.
3. En el cuadro de diálogo **configuración de compilación** , elija las opciones siguientes para la exportación de HoloLens:
   * **Plataforma:** *plataforma universal de Windows* y asegúrese de seleccionar **cambiar plataforma** para que la selección surta efecto.
   * **SDK:** *universal 10*.
   * **Tipo de compilación de UWP:** *D3D*.
4. **Opcional**: **proyectos de C# de Unity:** activado.

>[!NOTE]
>La activación de esta casilla le permite:
>* Depure la aplicación en el depurador remoto de Visual Studio.
>* Edite scripts en el proyecto de C# de Unity mientras usa IntelliSense para las API de WinRT.

5. En la ventana **configuración de compilación...** , Abra **configuración del reproductor...**
6. Seleccione la **configuración de plataforma universal de Windows** pestaña.
7. Expanda el grupo **XR Settings** (Configuración de XR).
8. En la **sección configuración de XR** , active la casilla compatibilidad con **realidad virtual** para agregar una nueva lista de dispositivos de **realidad virtual** y confirme que **"Windows Mixed Reality"** aparece como un dispositivo compatible.
9. Vuelva al cuadro de diálogo **configuración de compilación** .
10. Seleccione **Build** (Compilar).
11. En el cuadro de diálogo del explorador de Windows que aparece, cree una nueva carpeta para almacenar la salida de la compilación de Unity. Por lo general, el nombre de la carpeta es "app".
12. Seleccione la carpeta que acaba de crear y haga clic en **Seleccionar carpeta**.
13. Una vez que Unity termine de crearse, se abrirá una ventana del explorador de Windows en el directorio raíz del proyecto. Navegue a la carpeta recién creada.
14. Abra el archivo de solución de Visual Studio generado que se encuentra dentro de esta carpeta.

## <a name="when-to-re-export-from-unity"></a>Cuándo volver a exportar desde Unity

Al activar la casilla "proyectos de C#" al exportar la aplicación desde Unity, se crea una solución de Visual Studio que incluye todos los archivos de script de Unity. Esto le permite iterar en los scripts sin volver a exportar desde Unity. Sin embargo, si desea realizar cambios en el proyecto que no solo cambian el contenido de los scripts, deberá volver a exportar desde Unity. A continuación se indican algunos ejemplos de veces que es necesario volver a exportar desde Unity:
* Los recursos se agregan o quitan en la pestaña proyecto.
* Puede cambiar cualquier valor en la pestaña inspector.
* Los objetos se agregan o se quitan de la pestaña jerarquía.
* Puede cambiar cualquier configuración de proyecto de Unity.

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Compilar e implementar una solución de Visual Studio para Unity

El resto de compilar e implementar aplicaciones tiene lugar en [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Tendrá que especificar una configuración de compilación de Unity. Las convenciones de nomenclatura de Unity pueden diferir de lo que se suele usar en Visual Studio:

|  Configuración  |  Explicación | 
|----------|----------|
|  Depurar  |  Todas las optimizaciones están desactivadas y el generador de perfiles está habilitado. Se usa para depurar scripts. | 
|  Master  |  Todas las optimizaciones están activadas y el generador de perfiles está deshabilitado. Se usa para enviar aplicaciones a la tienda. | 
|  Release  |  Todas las optimizaciones están activadas y el generador de perfiles está habilitado. Se usa para evaluar el rendimiento de la aplicación. | 

Tenga en cuenta que la lista anterior es un subconjunto de los desencadenadores comunes que harán que se genere el proyecto de Visual Studio. En general, la edición de archivos. CS desde Visual Studio no requerirá que se vuelva a generar el proyecto desde Unity.

## <a name="troubleshooting"></a>Solución de problemas

Si observa que las modificaciones en los archivos. CS no se reconocen en el proyecto de Visual Studio, asegúrese de que la opción "proyectos de C# de Unity" esté activada al generar el proyecto de VS desde el menú de compilación de Unity.
