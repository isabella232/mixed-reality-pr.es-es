---
title: Procedimientos recomendados Visual Studio Unity y Visual Studio
description: Sugerencias y trucos para simplificar el flujo de trabajo de creación de una aplicación de realidad mixta con Unity y Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy, unity, visual studio, HoloLens, HoloLens 2, casco envolvente, procedimientos recomendados, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, UWP, Visual Studio Tools, Windows SDK
ms.openlocfilehash: edd79b95d02cfeb1da4effc485fc57078e3d24a3
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042266"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Procedimientos recomendados para trabajar con Unity y Visual Studio

Al crear una aplicación de realidad mixta con Unity, debe cambiar entre Unity y Visual Studio para compilar e implementar el paquete de aplicación en HoloLens o un casco envolvente. De forma predeterminada, se requieren dos instancias de Visual Studio, una instancia para modificar scripts de Unity y otra para implementar en el dispositivo y depurar. Las instrucciones siguientes le permiten desarrollar con una única instancia de Visual Studio, lo que reduce la frecuencia de exportación de proyectos de Unity y mejora la experiencia de depuración.

## <a name="improving-iteration-time"></a>Mejora del tiempo de iteración

La compatibilidad con el back-end de scripting de .NET en Unity quedó en desuso en Unity 2018 y se quitó a partir de Unity 2019 y posteriores, por lo que se recomienda cambiar a [IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP.html) Sin embargo, puede experimentar tiempos de compilación más largos de Unity a Visual Studio. Para mejorar la iteración más rápida, configure el entorno para obtener los mejores resultados de compilación:

1) Use la compilación incremental mediante la compilación del proyecto en el mismo directorio cada vez, y vuelva a usar allí los archivos pre-creados.
2) Deshabilitación de exámenes de software antimalware para el proyecto & carpetas de compilación
   - Abra **Protección contra & virus en** la aplicación de Windows 10 protección contra amenazas
   - Seleccione **Manage Settings (Administrar configuración)** **en Virus & threat protection settings (Configuración de protección contra amenazas de virus).**
   - Seleccione **Agregar o quitar exclusiones en** la sección **Exclusiones.**
   - Seleccione **Agregar una exclusión** y seleccione la carpeta que contiene el código del proyecto de Unity y las salidas de compilación.
3) Uso de un SSD para la creación

Consulte [Optimizing Build Times for IL2CPP (Optimización](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) de los tiempos de compilación para IL2CPP) para obtener más información. Además, revise [Depuración en el back-end de scripting il2CPP](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Considere la posibilidad de [ *instalar la extensión de Visual Studio UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Esta herramienta analiza los scripts de C# de Unity en busca de código que se pueda escribir de una manera más optimizada.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools para Unity

Descargar [Visual Studio Tools para Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Ventajas de Visual Studio Tools para Unity**
* Depure el modo de reproducción en el editor de Unity Visual Studio colocando puntos de interrupción, evaluando variables y expresiones complejas.
* Use el Explorador de proyectos de Unity para buscar el script con la misma jerarquía exacta que muestra Unity.
* Obtenga la consola de Unity directamente dentro de Visual Studio.
* Use asistentes para crear o navegar rápidamente a scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Exposición de variables de clase de C# para facilitar el ajuste

Hay dos maneras de exponer variables de clase. La manera recomendada es agregar el atributo [SerializeField] a las variables privadas. Se puede acceder a los campos serializados desde el editor, pero no se pueden exponer mediante programación.  La otra opción es hacer públicas las variables de clase de C# para exponerlas en la interfaz de usuario del editor. 

Ambos enfoques hacen posible ajustar fácilmente las variables mientras se reproducen en el editor, lo que resulta especialmente útil para optimizar las propiedades de la mecánica de interacción.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Regeneración de soluciones de Visual Studio UWP después de Windows SDK o actualización de Unity

Las soluciones Visual Studio UWP que se han registrado en el control de código fuente pueden desaproterse después de actualizar a un nuevo motor Windows SDK o Unity. Puede resolver soluciones no actualizadas después de crear una nueva solución para UWP desde Unity y combinar las diferencias en la solución integrada.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Uso de recursos de formato de texto para facilitar la comparación de los cambios de contenido

Almacenar recursos en formato de texto facilita la revisión de las diferencias de cambios de contenido en Visual Studio. Puede almacenar recursos en formato de texto seleccionando Editar > configuración del  proyecto **> Editor** y cambiar el modo de serialización de recursos a **Forzar texto.** Sin embargo, la combinación de cambios en el archivo de recursos de texto es propensa a errores y no se recomienda, por lo que considere la posibilidad de habilitar las desprotecciones binarias exclusivas en el control de código fuente.

## <a name="see-also"></a>Consulte también
- [Visual Studio Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimización de los tiempos de compilación para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Visual Studio extensión](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)