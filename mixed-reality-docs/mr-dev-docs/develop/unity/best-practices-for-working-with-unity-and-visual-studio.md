---
title: Procedimientos recomendados Visual Studio Unity y Visual Studio
description: Sugerencias y trucos para simplificar el flujo de trabajo de creación de una aplicación de realidad mixta con Unity y Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy, unity, visual studio, HoloLens, HoloLens 2, casco envolvente, procedimientos recomendados, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, UWP, Visual Studio Tools, sdk de Windows
ms.openlocfilehash: cc1ef6448ebabd1729dbe056cdccc40ab7444466701094cc942f2a20fbe81a65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186885"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Procedimientos recomendados para trabajar con Unity y Visual Studio

Al crear una aplicación de realidad mixta con Unity, debe cambiar entre Unity y Visual Studio para compilar e implementar el paquete de aplicación en HoloLens o en un casco envolvente. De forma predeterminada, se requieren dos instancias de Visual Studio : una instancia para modificar scripts de Unity y otra para implementar en el dispositivo y depurar. Las instrucciones siguientes le permiten desarrollar con una única instancia de Visual Studio, lo que reduce la frecuencia de exportación de proyectos de Unity y mejora la experiencia de depuración.

## <a name="improving-iteration-time"></a>Mejora del tiempo de iteración

La compatibilidad con el back-end de scripting de .NET en Unity quedó en desuso en Unity 2018 y se quitó a partir de Unity 2019+, por lo que se recomienda cambiar a [IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP.html) Sin embargo, puede experimentar tiempos de compilación más largos de Unity a Visual Studio. Para mejorar la iteración más rápida, configure el entorno para obtener los mejores resultados de compilación:

1) Use la compilación incremental compilando el proyecto en el mismo directorio cada vez, y vuelva a usar allí los archivos pre compilados.
2) Deshabilitación de los exámenes de software antimalware para las carpetas de compilación & proyecto
   - Abra **Virus & threat protection en** la aplicación de Windows 10 configuración de aplicaciones
   - Seleccione **Administrar Configuración** en Configuración de protección contra amenazas & **virus**
   - Seleccione **Agregar o quitar exclusiones en** la sección **Exclusiones.**
   - Seleccione **Agregar una exclusión** y seleccione la carpeta que contiene el código del proyecto de Unity y las salidas de compilación.
3) Uso de un SSD para la creación

Consulte [Optimización de los tiempos de compilación para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obtener más información. Además, revise [Depuración en il2CPP scripting back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Considere la posibilidad de [ *instalar la extensión de Visual Studio UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Esta herramienta analiza los scripts de C# de Unity en busca de código que se pueda escribir de una manera más optimizada.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools para Unity

Descargar [Visual Studio Tools para Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Ventajas de Visual Studio Tools para Unity**
* Depure el modo de reproducción en el editor de Unity desde Visual Studio puntos de interrupción, evaluando variables y expresiones complejas.
* Use unity Project Explorer para buscar el script con la misma jerarquía que muestra Unity.
* Obtenga la consola de Unity directamente dentro de Visual Studio.
* Use asistentes para crear o navegar rápidamente a scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Exposición de variables de clase de C# para facilitar el ajuste

Hay dos maneras de exponer variables de clase. La manera recomendada es agregar el atributo [SerializeField] a las variables privadas. Se puede acceder a los campos serializados desde el editor, pero no se pueden exponer mediante programación.  La otra opción es hacer públicas las variables de clase de C# para exponerlas en la interfaz de usuario del editor. 

Ambos enfoques hacen posible ajustar fácilmente las variables mientras se reproducen en el editor, lo que resulta especialmente útil para ajustar las propiedades mecánicas de interacción.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Regeneración de soluciones de Visual Studio UWP después de Windows SDK o actualización de Unity

Las soluciones Visual Studio UWP que se han registrado en el control de código fuente pueden estar des actualizadas después de actualizar a un nuevo SDK de Windows o motor de Unity. Puede resolver soluciones no actualizadas después de crear una nueva solución para UWP desde Unity y combinar las diferencias en la solución integrada.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Uso de recursos de formato de texto para una comparación sencilla de los cambios de contenido

El almacenamiento de recursos en formato de texto facilita la revisión de las diferencias de cambio de contenido en Visual Studio. Puede almacenar recursos en formato de texto seleccionando Editar **> Project Configuración > Editor** y cambiar el modo **de** serialización de recursos a **Forzar texto.** Sin embargo, la combinación de cambios en el archivo de recursos de texto es propensa a errores y no se recomienda, por lo que considere la posibilidad de habilitar las desprotecciones binarias exclusivas en el control de código fuente.

## <a name="see-also"></a>Vea también
- [Visual Studio Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimización de los tiempos de compilación para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Extensión de Visual Studio UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)