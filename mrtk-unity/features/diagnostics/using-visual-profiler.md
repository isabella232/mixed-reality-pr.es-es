---
title: Uso del profiler visual
description: documentación para usar Visual Profiler en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 018d6bf2087b73697a1e1f43e206c96ae25e1f21
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177221"
---
# <a name="using-the-visual-profiler"></a>Uso del profiler visual

VisualProfiler proporciona una vista en la aplicación fácil de usar del rendimiento de una aplicación de realidad mixta. El profiler se admite en todas las Mixed Reality Toolkit plataformas, incluidas:

- Microsoft HoloLens (1.ª generación)
- Microsoft HoloLens 2
- Cascos envolventes de Windows Mixed Reality
- OpenVR

Al desarrollar una aplicación, céntrate en varias partes de la escena, ya que Visual Profiler muestra datos relativos a la vista actual.

> [!IMPORTANT]
> Centre la atención en partes de la escena con objetos complejos, efectos de partícula o actividad. Estos y otros factores a menudo contribuyen a la reducción del rendimiento de la aplicación y a una experiencia de usuario menos que ideal.

## <a name="visual-profiler-interface"></a>Interfaz del profiler visual

![Interfaz de Visual Profiler](../images/diagnostics/VisualProfiler.png)

La interfaz de Visual Profiler incluye los siguientes componentes:

- [Velocidad de fotogramas](#frame-rate)
- [Tiempo de fotogramas](#frame-time)
- [Marco Graph](#frame-graph)
- [Uso de memoria](#memory-utilization)

### <a name="frame-rate"></a>Velocidad de fotogramas

En la esquina superior izquierda de la interfaz se encuentra la velocidad de fotogramas, medida en fotogramas por segundo. Para obtener la mejor experiencia y comodidad del usuario, este valor debe ser lo más alto posible.

La configuración específica de la plataforma y el hardware desempeñará un papel importante en la velocidad máxima de fotogramas factible. Algunos valores de destino comunes incluyen:

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> Debido a [la limitación](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)de velocidad de fotogramas en HoloLens cuando mrc predeterminado está activo, el profiler visual se oculta mientras se capturan vídeos y fotos. Esta configuración se puede invalidar en el perfil del sistema de diagnóstico.

### <a name="frame-time"></a>Tiempo entre fotogramas

A la derecha de la velocidad de fotogramas se encuentra el tiempo de fotograma, en milisegundos, empleado en la CPU. Para lograr las tasas de fotogramas de destino mencionadas anteriormente, una aplicación puede dedicar la siguiente cantidad de tiempo por fotograma:

- 60 fps: 16,6 ms
- 90 fps: 11,1 ms

Está previsto que el tiempo de GPU se agregó en una versión futura.

### <a name="frame-graph"></a>Gráfico de fotogramas

El gráfico de fotogramas proporciona una presentación gráfica del historial de velocidad de fotogramas de la aplicación.

![Visual Profiler Missed Frame Graph](../images/diagnostics/VisualProfilerMissedFrames.png)

Al usar la aplicación, busque fotogramas perdidos que indiquen que la aplicación no está alcanzando su velocidad de fotogramas objetivo y puede que necesite trabajo de optimización.

### <a name="memory-utilization"></a>Uso de memoria

La presentación de uso de memoria permite comprender fácilmente cómo afecta la vista actual al consumo de memoria de una aplicación.

![Memoria de Visual Profiler Graph](../images/diagnostics/VisualProfilerMemory.png)

Al usar la aplicación, busque el uso total de memoria. Entre los indicadores clave se incluyen la proximidad del límite de memoria y los cambios rápidos en el uso.

## <a name="customizing-the-visual-profiler"></a>Personalización del profiler visual

La apariencia y el comportamiento de Visual Profiler se pueden personalizar a través del perfil del sistema de diagnóstico. Consulte [Configuración del sistema de diagnóstico para](configuring-diagnostics.md) obtener más información.

## <a name="see-also"></a>Consulte también

- [Sistema de diagnóstico](diagnostics-system-getting-started.md)
- [Configuración del sistema de diagnóstico](configuring-diagnostics.md)
