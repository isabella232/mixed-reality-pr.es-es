---
title: Procedimientos recomendados para trabajar con Unity y Visual Studio
description: Sugerencias y trucos para simplificar el flujo de trabajo de creación de una aplicación de realidad mixta con Unity y Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: implementación, Unity, Visual Studio, HoloLens, HoloLens 2, auriculares envolvente, procedimientos recomendados, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, UWP, Visual Studio Tools, Windows SDK
ms.openlocfilehash: 9e80cad3e7154ae5548514297343db8efcdcb49e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010266"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Procedimientos recomendados para trabajar con Unity y Visual Studio

Al crear una aplicación de realidad mixta con Unity, debe cambiar entre Unity y Visual Studio para compilar e implementar el paquete de la aplicación en HoloLens o en un casco envolvente. De forma predeterminada, se requieren dos instancias de Visual Studio: una instancia para modificar los scripts de Unity y otra para la implementación en el dispositivo y la depuración. Las instrucciones siguientes le permiten desarrollar mediante una única instancia de Visual Studio, lo que reduce la frecuencia de exportación de proyectos de Unity y mejora la experiencia de depuración.

## <a name="improving-iteration-time"></a>Mejorar el tiempo de iteración

La compatibilidad con el back-end de scripting de .NET en Unity está en desuso en Unity 2018 y se quitó en Unity 2019 +. por lo tanto, se recomienda cambiar a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). Sin embargo, es posible que se produzcan tiempos de compilación más prolongados de Unity a Visual Studio. Para mejorar la iteración más rápida, configure el entorno para obtener los mejores resultados de la compilación:

1) Use la compilación incremental compilando el proyecto en el mismo directorio cada vez, reutilizando los archivos generados previamente.
2) Deshabilitar exámenes de software antimalware para el proyecto & carpetas de compilación
   - Abrir **protección contra amenazas de Virus &** en la aplicación de configuración de Windows 10
   - Seleccione **Administrar configuración** en **configuración de protección contra amenazas de virus &**
   - Seleccione **Agregar o quitar exclusiones** en la sección **exclusiones** .
   - Seleccione **Agregar una exclusión** y seleccione la carpeta que contiene el código del proyecto de Unity y las salidas de compilación.
3) Uso de SSD para compilar

Revise la [optimización de los tiempos de compilación de IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obtener más información. Además, revise [la depuración en el back-end de scripting de IL2CPP](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Considere la posibilidad de instalar la [extensión de Visual Studio *UnityScriptAnalyzer*](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Esta herramienta analiza los scripts de C# de Unity para código que se puede escribir de forma más optimizada.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools para Unity

Descargar [Visual Studio Tools para Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Ventajas de Visual Studio Tools para Unity**
* Depure el modo de reproducción en el editor de Unity desde Visual Studio colocando puntos de interrupción, evaluando variables y expresiones complejas.
* Use el explorador de proyectos de Unity para buscar el script con la misma jerarquía que se muestra en Unity.
* Obtenga la consola de Unity directamente en Visual Studio.
* Use los asistentes para crear o navegar rápidamente por scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Exponer variables de clase de C# para facilitar la optimización

Hay dos maneras de exponer variables de clase. La manera recomendada es agregar el atributo [SerializeField] a las variables privadas. Se puede tener acceso a los campos serializados desde el editor pero no se pueden exponer mediante programación.  La otra opción es hacer que las variables de clase de C# sean públicas para exponerlas en la interfaz de usuario del editor. 

Ambos enfoques permiten ajustar fácilmente las variables mientras se reproducen en el editor, lo que es especialmente útil para ajustar las propiedades del mecánico de interacción.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Volver a generar soluciones de Visual Studio para UWP después de la actualización de Windows SDK o Unity

Las soluciones de Visual Studio de UWP protegidas en el control de código fuente pueden no estar actualizadas después de actualizar a un nuevo motor de Windows SDK o Unity. Puede resolver soluciones no actualizadas después de compilar una nueva solución de UWP desde Unity y combinar las diferencias en la solución protegida.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usar recursos en formato de texto para facilitar la comparación de los cambios de contenido

El almacenamiento de recursos en formato de texto permite revisar más fácilmente las diferencias de cambio de contenido en Visual Studio. Puede almacenar recursos en formato de texto seleccionando **editar > configuración del proyecto > editor** y cambiar el modo de **serialización de activos** para **forzar el texto**. Sin embargo, la combinación de cambios en el archivo de recursos de texto es propensa a errores y no se recomienda, por lo que considere habilitar desprotecciones binarias exclusivas en el control de código fuente.

## <a name="see-also"></a>Consulte también
- [Visual Studio Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimizar los tiempos de compilación para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Extensión de Visual Studio](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
