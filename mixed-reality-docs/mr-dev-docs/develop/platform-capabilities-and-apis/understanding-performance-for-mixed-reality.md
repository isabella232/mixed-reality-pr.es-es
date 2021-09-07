---
title: Descripción del rendimiento de Mixed Reality
description: Obtenga información avanzada y detalles para analizar y optimizar Windows Mixed Reality rendimiento de la aplicación.
author: hferrone
ms.author: v-vtieto
ms.date: 08/16/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Performance, Optimization, CPU, GPU
ms.openlocfilehash: 9304e4cd80f0929b87a29873ad07329700ec463f
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244207"
---
# <a name="understanding-performance-for-mixed-reality"></a>Descripción del rendimiento de la realidad mixta

Este artículo es una introducción para comprender la importancia del rendimiento para la Mixed Reality aplicación.  La experiencia del usuario puede degradarse enormemente si la aplicación no se ejecuta a una velocidad de fotogramas óptima. Hologramas parecerá inestable y el seguimiento de la cabeza del entorno será inexacto, lo que dará lugar a una mala experiencia para el usuario. El rendimiento debe considerarse una característica de primera clase para el desarrollo de realidad mixta y no una tarea pulida.

Recientemente hemos publicado una aplicación denominada Fundamentos de calidad que cubre problemas comunes de rendimiento, diseño y entorno y soluciones para HoloLens 2 aplicaciones. Esta aplicación es una excelente demostración visual para el contenido que se muestra a continuación.

> [!div class="nextstepaction"]
> [Descarga de la aplicación Aspectos básicos de calidad](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

A continuación se enumeran los valores de velocidad de fotogramas de rendimiento para cada plataforma de destino.

| Plataforma | Velocidad de fotogramas de destino |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality Ultra Pc](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pc](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

En el marco siguiente se describen los procedimientos recomendados para alcanzar las velocidades de fotogramas objetivo. Para obtener sugerencias sobre cómo medir y mejorar la velocidad de fotogramas en el entorno de Unity, se recomienda leer las recomendaciones [de rendimiento para Unity.](../unity/performance-recommendations-for-unity.md) 

## <a name="understanding-performance-bottlenecks"></a>Descripción de los cuellos de botella de rendimiento

Si la aplicación tiene una velocidad de fotogramas de bajo rendimiento, el primer paso es analizar y comprender dónde la aplicación consume muchos cálculos. Hay dos procesadores principales responsables del trabajo para representar la escena: la CPU y la GPU, cada uno de los que administra distintos aspectos de la Mixed Reality aplicación. Los tres lugares clave donde pueden producirse cuellos de botella son: 

1. **Subproceso de aplicación: CPU** -
    Responsable de la lógica de la aplicación, incluido el procesamiento de entradas, animaciones, física y otra lógica de aplicación.
2. **Render Thread - CPU to GPU** (Subproceso de representación: CPU a GPU) - Responsable de enviar las llamadas de dibujo a la GPU. Cuando la aplicación quiere representar un objeto como un cubo o un modelo, este subproceso envía una solicitud a la GPU para realizar las operaciones.
3. **GPU:** normalmente controla la canalización de gráficos de la aplicación para transformar datos 3D (modelos, texturas, entre otros) en píxeles. En última instancia, genera una imagen 2D para enviarla a la pantalla del dispositivo.

![Duración de un fotograma](images/lifetime-of-a-frame.png)

Por lo general, HoloLens aplicaciones estarán enlazadas a GPU, pero no siempre. Use las herramientas y técnicas siguientes para comprender dónde se producen cuellos de botella en la aplicación en particular.

## <a name="how-to-analyze-your-application"></a>Análisis de la aplicación

Hay muchas herramientas que le permiten comprender el perfil de rendimiento y los posibles cuellos de botella en la aplicación de realidad mixta. 

A continuación se muestran algunas herramientas comunes que le ayudarán a recopilar información de generación de perfiles detallada para la aplicación:
- [Analizadores de rendimiento de gráficos Intel](https://software.intel.com/gpa)
- [Visual Studio Depuradores de gráficos](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador de fotogramas de Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Ideas](../unreal/unreal-insights.md)
- [PIX](https://devblogs.microsoft.com/pix/)
- [Pofiling de GPU en Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>Cómo crear perfiles en cualquier entorno

Una manera de determinar si la aplicación está enlazada a GPU o CPU es reducir la resolución de la salida del destino de representación. Al reducir el número de píxeles que se va a calcular, reducirá la carga de GPU. El dispositivo se representará en una textura más pequeña y, a continuación, se mostrará la imagen final.

Después de reducir la resolución de representación, si:
1) La velocidad de **fotogramas de la** aplicación aumenta y es probable que esté enlazado **a GPU.**
1) Velocidad de fotogramas **de la aplicación sin** cambios y, a continuación, es probable que esté enlazado a la **CPU**

>[!NOTE]
>Unity proporciona la capacidad de modificar fácilmente la resolución de destino de representación de la aplicación en tiempo de ejecución a través de la *[propiedad XRSettings.renderViewportScale.](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* La imagen final presentada en el dispositivo tiene una resolución fija. La plataforma muestrea la salida de resolución inferior para crear una imagen de resolución más alta para representarla en las pantallas. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Cómo mejorar la aplicación

### <a name="cpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU

Por lo general, la mayoría del trabajo en una aplicación de realidad mixta en la CPU implica realizar la "simulación" de la escena y procesar la lógica de la aplicación. Las siguientes áreas están destinadas a la optimización:

- Animaciones
- Física
- Asignaciones de memoria
- Algoritmos complejos (es decir, kinética inversa, búsqueda de rutas de acceso)

### <a name="gpu-performance-recommendations"></a>Recomendaciones de rendimiento de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Descripción del ancho de banda frente a la tasa de relleno
Al representar un fotograma en la GPU, una aplicación está enlazada por ancho de banda de memoria o velocidad de relleno.

- **El ancho de** banda de memoria es la velocidad de lecturas y escrituras que la GPU puede hacer desde la memoria.
    - Para identificar las limitaciones de ancho de banda, reduzca la calidad de la textura y compruebe si la velocidad de fotogramas ha mejorado.
    - En Unity, cambie **Calidad de textura en** **Editar**  >  **Project Configuración**  >  **[Calidad Configuración](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **La velocidad de** relleno hace referencia a los píxeles que la GPU puede dibujar por segundo.
    - Para identificar las limitaciones de la velocidad de relleno, reduzca la resolución de la pantalla y compruebe si se ha mejorado la velocidad de fotogramas. 
    - En Unity, use la *[propiedad XRSettings.renderViewportScale.](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

El ancho de banda de memoria suele implicar optimizaciones para:
1) Resoluciones de textura inferiores
2) Usar menos texturas (normales, especulares, entre otras)

La tasa de relleno se centra en reducir el número de operaciones que deben calcularse para un píxel representado final, incluidos:
1) Número de objetos que se representan o procesan
2) Número de operaciones por sombreador
3) Número de fases de GPU hasta el resultado final (sombreadores de geometría, efectos posteriores al procesamiento, entre otros)
4) Número de píxeles que se representará (resolución de pantalla)

#### <a name="reduce-polygon-count"></a>Reducción del recuento de polígonos

Los recuentos de polígonos más altos tienen como resultado más operaciones para la GPU, por lo que reducir el número de [polígonos](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) de la escena reduce el tiempo de representación. Hay otros factores que hacen que el sombreado de la geometría sea costoso, pero el recuento de polígonos es la métrica más sencilla para determinar cuánto trabajo se necesita para representar una escena.

#### <a name="limit-overdraw"></a>Sobredibujo del límite

El sobredes dibujo alto se produce cuando se representan varios objetos, pero no se muestran en la pantalla, ya que están ocultos por un objeto ocluido. Imagine una pared que tiene objetos detrás. Toda la geometría se procesaría para su representación, pero solo es necesario representar la pared opaca, lo que da lugar a operaciones innecesarias.

#### <a name="shaders"></a>Sombreadores

Los sombreadores son pequeños programas que se ejecutan en la GPU y hacen dos pasos importantes en la representación:
1) Determinar qué vértices se deben dibujar y dónde se encuentran en el espacio de la pantalla (sombreador de vértices)
    - El sombreador de vértices se ejecuta por vértice para cada malla.
2) Determinar el color de cada píxel (sombreador de píxeles)
    - El sombreador de píxeles se ejecuta por píxel y se representa mediante la geometría en la textura de representación de destino.

Normalmente, los sombreadores hacen muchas transformaciones y cálculos de iluminación. Aunque los modelos de iluminación complejos, las sombras y otras operaciones pueden generar resultados fantásticos, también tienen un precio. Reducir el número de operaciones calculadas en sombreadores puede reducir en gran medida el trabajo necesario para la GPU por fotograma.

##### <a name="shader-coding-recommendations"></a>Recomendaciones de codificación de sombreadores

- Uso del filtrado bilineal, siempre que sea posible
- Reorganizar expresiones para usar intrínsecos DE RIESGO para realizar una multiplicación y una adición al mismo tiempo
- Precalcular tanto como sea posible en la CPU y pasar como constantes al material
- **Favor de mover las operaciones del sombreador de píxeles al sombreador de vértices**
    - Por lo general, el número de vértices es mucho menor que el número de píxeles (720p es 921 600 píxeles, 1080p es 2 073 600 píxeles, y así sucesivamente)

#### <a name="remove-gpu-stages"></a>Eliminación de fases de GPU

Los efectos posteriores al procesamiento pueden ser costosos y aumentar la tasa de relleno de la aplicación, incluidas técnicas de suavizado de alias como MSAA. En HoloLens, se recomienda evitar estas técnicas y fases adicionales del sombreador, como la geometría, el casco y los sombreadores de proceso.

## <a name="memory-recommendations"></a>Recomendaciones de memoria

Las operaciones excesivas de asignación y desasignación de memoria pueden dar lugar a un rendimiento incoherente, fotogramas inmovilizados y otro comportamiento perjudicial. Es especialmente importante comprender las consideraciones de memoria al desarrollar en Unity, ya que el recolector de elementos no utilizados controla la administración de memoria.

#### <a name="object-pooling"></a>Agrupación de objetos

La agrupación de objetos es una técnica popular para reducir el costo de asignaciones continuas y desasignaciones de objetos. Para ello, se asigna un grupo grande de objetos idénticos y se reutilizan instancias disponibles inactivas de este grupo en lugar de generar y destruir objetos constantemente a lo largo del tiempo. Los grupos de objetos son excelentes para los componentes reutilizables que tienen una duración variable en una aplicación.

## <a name="see-also"></a>Consulte también
- [Recomendaciones de rendimiento para Unity](../unity/performance-recommendations-for-unity.md)
- [Configuración recomendada para Unity](../unity/recommended-settings-for-unity.md)
- [Recomendaciones de rendimiento para Unreal](../unreal/performance-recommendations-for-unreal.md)
- [Recomendaciones de material en Unreal](../unreal/unreal-materials.md)
- [Optimización de modelos 3D](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Procedimientos recomendados para convertir y optimizar modelos 3D en tiempo real](/dynamics365/mixed-reality/import-tool/best-practices)
- [Directrices de rendimiento para creadores y diseñadores de Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Procedimientos recomendados de realidad virtual para Unreal](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)