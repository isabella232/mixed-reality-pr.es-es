---
title: Optimizar ventana
description: Ventana Optimización de documentación en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 7ffc2173cc55c83f126f66002d9240cb349d7f59
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144311"
---
# <a name="optimize-window"></a>Ventana Optimizar

La ventana optimización de MRTK es una utilidad que ayuda a automatizar e informar en el proceso de configuración de un proyecto de realidad mixta para obtener el [mejor](../../performance/perf-getting-started.md) rendimiento en Unity. Por lo general, esta herramienta se centra en las configuraciones de representación que, cuando se establecen en el valor preestablecido correcto, pueden ahorrar milisegundos de procesamiento.

El *destino de compilación activa* es la plataforma de [compilación](https://docs.unity3d.com/Manual/BuildSettings.html) destinada actualmente al proyecto para la compilación.

El *destino de rendimiento* indica a la herramienta de optimización qué tipo de puntos de conexión de dispositivo se debe tener como destino.

- *Los cascos AR* son dispositivos de clase móvil, como HoloLens
- *VR Independiente* son dispositivos de clase móvil, como Oculus Go o Vr
- *VR Tethered son* dispositivos con tecnología de PC, como Samsung Samsung Samsung, Oculus Dimensional o WM Vive, etc.

![Objetivo de rendimiento de ventana de optimización de MRTK](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Configuración de optimizaciones

En la pestaña de optimización de configuración se tratan algunas de las configuraciones de representación importantes para un proyecto de Unity. Esta sección puede ayudar a automatizar e informar sobre qué configuración se debe cambiar para obtener los mejores resultados.

Un icono de marca de verificación verde significa que se ha configurado un valor óptimo en el proyecto o la escena para esta configuración concreta. Un icono de advertencia amarillo indica que se puede mejorar la configuración actual. Al hacer clic en el botón asociado de una sección determinada, se configurará automáticamente esa configuración en el proyecto o escena de Unity en un valor más óptimo.

![Optimización de la configuración de ventana de MRTK](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Representación de instancia de un solo paso

[La representación con instancia de paso único](https://docs.unity3d.com/Manual/SinglePassInstancing.html) es la ruta de representación más eficaz para las aplicaciones de realidad mixta. Esta configuración garantiza que la canalización de representación se ejecuta solo una vez para ambos ojos y que las llamadas a draw se instancian entre ambos ojos.

### <a name="depth-buffer-sharing"></a>Uso compartido del búfer de profundidad

Para mejorar [la estabilización](../../performance/hologram-Stabilization.md)del holograma, los desarrolladores pueden compartir el búfer de profundidad de la aplicación, que proporciona a la plataforma información sobre dónde y qué hologramas estabilizar en la escena representado.

### <a name="depth-buffer-format"></a>Formato de búfer de profundidad

Además, en el caso de *los cascos* de AR, se recomienda usar un formato de profundidad de 16 bits al habilitar el uso compartido del búfer de profundidad en comparación con los de 24 bits. Esto significa una precisión más baja, pero ahorra rendimiento. Si [se produce z-fighting](https://en.wikipedia.org/wiki/Z-fighting) porque hay menos precisión al calcular la profundidad [](https://docs.unity3d.com/Manual/class-Camera.html) de los píxeles, se recomienda acercar el plano de recorte lejano a la cámara (por ejemplo: 50 m en lugar de 1000 m).

> [!NOTE]
> Si usa el formato de profundidad de *16* bits , los efectos necesarios del búfer de galería de símbolos no funcionarán porque Unity no crea un búfer [de](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) galería de símbolos en esta configuración. Al seleccionar el formato de profundidad de *24* bits por el contrario, normalmente se creará un búfer de galería de símbolos de [8](https://docs.unity3d.com/Manual/SL-Stencil.html)bits, si procede en la plataforma de gráficos de punto de conexión.
>
> Si usa un componente [Mask](https://docs.unity3d.com/Manual/script-Mask.html) que requiere el búfer de galería de símbolos, considere la posibilidad de usar [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) en su lugar, que no requiere el búfer de galería de símbolos y, por tanto, se puede usar junto con un formato de profundidad de *16* bits .

### <a name="real-time-global-illumination"></a>Iluminación global en tiempo real

[La iluminación global en tiempo real](https://docs.unity3d.com/Manual/GIIntro.html) en Unity puede proporcionar resultados éticos fantásticos, pero a un costo muy alto. La iluminación de iluminación global es muy costosa en la realidad mixta y, por tanto, se recomienda deshabilitar esta característica en el desarrollo.

> [!NOTE]
> La configuración de iluminación global en Unity se establece por escena y no una vez en todo el proyecto.

## <a name="scene-analysis"></a>Análisis de la escena

La *pestaña Análisis de* escena está diseñada para informar a los desarrolladores sobre qué elementos de la escena tendrán probablemente el mayor impacto en el rendimiento.

![Análisis de la escena de optimización de la configuración de ventana de MRTK](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Análisis de iluminación

En esta sección se examinará el número de luces que hay actualmente en la escena, así como las luces que deben deshabilitar las sombras. La conversión de sombras es una operación muy costosa.

### <a name="polygon-count-analysis"></a>Análisis de recuento de polígonos

La herramienta también proporciona estadísticas de recuento de polígonos. Puede ser muy útil identificar rápidamente qué objetos GameObject tienen la mayor complejidad de polígono en una escena determinada para dirigirse a las optimizaciones.

### <a name="unity-ui-raycast-analysis"></a>Análisis de difusión por rayos de la interfaz de usuario de Unity

Las operaciones de difusión de gráficos se realizan por puntero en MRTK para determinar si hay algún elemento de la interfaz de usuario de Unity en el foco. Estos raycasts pueden ser bastante caros y, para ayudar a mejorar el rendimiento, los elementos de la interfaz de usuario que no necesitan devolverse en los resultados deben deshabilitarse como destinos de difusión por rayos. Cada [elemento Graphic](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) tiene una propiedad [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) . Esta herramienta buscará elementos de interfaz de usuario de texto que tengan habilitada esta propiedad y, por tanto, probablemente sean candidatos para deshabilitarse.

## <a name="shader-analysis"></a>Análisis de sombreador

El [sombreador Estándar](https://docs.unity3d.com/Manual/shader-StandardShader.html) de Unity puede producir resultados visuales de muy alta calidad para juegos, pero generalmente no es más adecuado para las necesidades de rendimiento de las aplicaciones de realidad mixta, especialmente porque estas aplicaciones suelen estar limitadas por GPU. Por lo tanto, se recomienda a los desarrolladores usar el sombreador [ESTÁNDAR DE MRTK](../rendering/mrtk-standard-shader.md) para equilibrar la & características gráficas con el rendimiento.

La *pestaña Análisis de* sombreador examina la carpeta Asset del proyecto actual en busca de materiales mediante el sombreador Estándar de Unity o, si lo desea, todos los materiales que no usan los sombreadores proporcionados por Mixed Reality Toolkit. Una vez detectados, los desarrolladores pueden convertir todos los materiales o convertir individualmente con los botones adecuados.

![Análisis del sombreador optimización de la configuración de ventana de MRTK](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Consulta también

- [Rendimiento](../../performance/perf-getting-started.md)
- [Estabilización de hologramas](../../performance/hologram-stabilization.md)
