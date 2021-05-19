---
title: Rendimiento Tareas iniciales
description: Documentación para comprender y ajustar el rendimiento previo en MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 1ddc057c7f3966375d512a5e4a714dce093412e6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144865"
---
# <a name="performance"></a>Rendimiento

## <a name="getting-started"></a>Introducción

La manera más fácil de racionalizar el rendimiento es a través de la velocidad de fotogramas o el número de veces que la aplicación puede representar una imagen por segundo. Es importante cumplir la velocidad de fotogramas de destino, como se describe en la plataforma de destino (es decir, [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus,](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)etc.). Por ejemplo, en HoloLens, la velocidad de fotogramas de destino es de 60 FPS. Las aplicaciones de velocidad de fotogramas baja [](../performance/hologram-stabilization.md)pueden dar lugar a experiencias de usuario degradadas, como la estabilización de hologramas, el seguimiento del mundo, el seguimiento de las manos, etc. Para ayudar a los desarrolladores a realizar un seguimiento y lograr una velocidad de fotogramas de calidad, Mixed Reality Toolkit proporciona una variedad de herramientas y scripts.

### <a name="visual-profiler"></a>Visualizador de perfiles

Para realizar un seguimiento continuo del rendimiento a lo largo de la duración del desarrollo, se recomienda mostrar siempre un objeto visual de velocidad de fotogramas mientras se ejecuta & depuración de una aplicación. El kit Mixed Reality herramientas proporciona la herramienta de diagnóstico [de Visual Profiler](../features/diagnostics/using-visual-profiler.md) que proporciona información en tiempo real sobre el fps actual y el uso de memoria en la vista de la aplicación. Visual Profiler se puede configurar a través de la configuración del sistema de [diagnósticos](../features/diagnostics/diagnostics-system-getting-started.md) en [el inspector de perfiles de MRTK](../configuration/mixed-reality-configuration-guide.md).

Además, es especialmente importante usar Visual Profiler para realizar un seguimiento de la velocidad de fotogramas cuando se ejecuta en el dispositivo en lugar de ejecutarse en el editor de Unity o en un emulador. Los resultados de rendimiento más precisos se representarán cuando se ejecute en el dispositivo con [compilaciones de configuración de versión](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019).

> [!NOTE]
> Si compila para Windows Mixed Reality, implemente con [compilaciones de configuración MASTER.](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Visual Profiler (Interfaz)](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>Ventana Optimizar

La ventana Optimización de [MRTK](../features/tools/optimize-window.md) ofrece herramientas de información y automatización para ayudar a los desarrolladores de realidad mixta a configurar su entorno para obtener los mejores resultados e identificar posibles cuellos de botella en sus recursos de & escena. Ciertas configuraciones clave de Unity pueden ayudar a ofrecer resultados considerablemente más optimizados para proyectos de realidad mixta.

Por lo general, estas opciones implican configuraciones de representación que son ideales para la realidad mixta. Las aplicaciones de realidad mixta son únicas en comparación con el desarrollo tradicional de gráficos 3D, ya que hay dos pantallas (es decir, dos ojos) para representar toda la escena.

La configuración recomendada a la que se hace referencia a continuación se puede configurar automáticamente en un proyecto de Unity aprovechando la ventana de optimización de MRTK.

![Optimización de la configuración de ventana de MRTK](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity Profiler

[Unity Profiler es](https://docs.unity3d.com/Manual/ProfilerWindow.html) una herramienta útil para investigar los detalles del rendimiento de la aplicación en un nivel fotograma a fotograma.

#### <a name="time-spent-on-the-cpu"></a>Tiempo dedicado a la CPU

![Gráfico de ejemplo de Unity Profiler](../features/images/performance/UnityProfilerGraph.png)

Para mantener velocidades de fotogramas cómodas (normalmente 60 fotogramas por segundo), las aplicaciones deben lograr un tiempo máximo de fotogramas de 16,6 milisegundos de tiempo de CPU. Para ayudar a identificar el costo de la funcionalidad de MRTK, Microsoft Mixed Reality Toolkit contiene marcadores para rutas de código de bucle interno (por fotograma). Estos marcadores usan el formato siguiente para ayudar a comprender la funcionalidad específica que se utiliza:

```
[MRTK] className.methodName
```

> [!Note]
> Puede haber datos adicionales después del nombre del método. Esto se usa para identificar funcionalidades potencialmente costosas y ejecutadas condicionalmente que pueden evitarse mediante pequeños cambios en el código de la aplicación.

![Ejemplo de jerarquía del profiler de Unity](../features/images/performance/UnityProfilerHierarchy.png)

En este ejemplo, la jerarquía se ha expandido para mostrar que el método UpdateHandData de la clase WindowsMixedRealityArticulatedHand consume 0,44 ms de tiempo de CPU durante el fotograma que se está analizando. Estos datos se pueden usar para ayudar a determinar si un problema de rendimiento está relacionado con el código de la aplicación o desde otra parte del sistema.

Se recomienda encarecidamente que los desarrolladores instrumente el código de la aplicación de forma similar. Las áreas principales de foco para la instrumentación de código de aplicación se encuentran dentro de los controladores de eventos, ya que estos métodos se cobran al bucle de actualización de MRTK a medida que se elevan los eventos. Los tiempos elevados de fotogramas dentro del bucle de actualización de MRTK pueden indicar código costoso en los métodos de controlador de eventos.

## <a name="recommended-settings-for-unity"></a>Configuración recomendada para Unity

### <a name="single-pass-instanced-rendering"></a>Single-Pass de instancias

La configuración de representación predeterminada para XR en Unity es [Multi-pass](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html). Esta configuración indica a Unity que ejecute toda la canalización de representación dos veces, una vez para cada ojo. Esto se puede optimizar seleccionando la [representación de instancia de paso único en](https://docs.unity3d.com/Manual/SinglePassInstancing.html) su lugar. Esta configuración aprovecha [las matrices](https://en.wikipedia.org/wiki/Multiple_Render_Targets) de destino de representación para poder realizar una sola llamada a draw que las instancias en el destino [de representación](https://en.wikipedia.org/wiki/Render_Target) adecuado para cada ojo. Además, este modo permite que toda la representación se haga en una sola ejecución de la canalización de representación. Por lo tanto, la selección de la representación con instancia de paso único como ruta de acceso de representación para una aplicación de realidad mixta puede ahorrar mucho tiempo en la GPU & [CPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) y es la configuración de representación recomendada.

Sin embargo, para emitir una sola llamada de dibujo para cada malla a cada ojo, la creación de instancias de [GPU](https://docs.unity3d.com/Manual/GPUInstancing.html) debe ser compatible con todos los sombreadores. La creación de instancias permite que la GPU dibuje llamadas a draw multiplex en ambos ojos. Los sombreadores integrados de Unity, así como el sombreador [estándar de MRTK](../features/rendering/mrtk-standard-shader.md) de forma predeterminada, contienen las instrucciones de creación de instancias necesarias en el código del sombreador. Sin embargo, si escribe sombreadores personalizados para Unity, es posible que deba actualizarse para admitir la representación de instancia de paso único.

#### <a name="example-code-for-custom-shader"></a>[Código de ejemplo para el sombreador personalizado](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a>Configuración de calidad

Unity proporciona valores [preestablecidos para controlar la calidad de](https://docs.unity3d.com/Manual/class-QualitySettings.html) la representación de cada punto de conexión de la plataforma. Estos valores preestablecidos controlan qué características gráficas se pueden habilitar, como sombras, suavizado de alias, iluminación global, etc. Se recomienda reducir esta configuración y optimizar el número de cálculos realizados durante la representación.

*Paso 1:* Actualización de proyectos de Unity de realidad mixta para usar la *configuración de nivel de* calidad baja  
**Editar**  >  **Configuración del** proyecto y, a continuación, seleccione **la** categoría Calidad > Seleccionar *baja calidad* para la plataforma UWP

*Paso 2:* Para cada archivo de escena de Unity, deshabilite [la iluminación global en tiempo real.](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**Ventana**  >  **Representación**  >  **Configuración de iluminación**  >  [Desactivación *de la iluminación global en tiempo real*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>Uso compartido del búfer de profundidad (HoloLens)

Si desarrolla para la plataforma Windows Mixed Reality y, en particular, HoloLens, habilitar el uso compartido del búfer de profundidad en la configuración *de XR* puede ayudar con la estabilización [del holograma](../performance/hologram-stabilization.md).  Sin embargo, el procesamiento del búfer de profundidad puede incurrir en un costo de rendimiento, especialmente si se usa el formato de [profundidad de 24 bits](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html). Por lo tanto, *se recomienda encarecidamente* configurar el búfer de profundidad con una precisión de 16 bits.

Si [se produce z-fighting](https://en.wikipedia.org/wiki/Z-fighting) debido al formato [](https://docs.unity3d.com/Manual/class-Camera.html) de bits inferior, confirme que el plano de recorte lejano de todas las cámaras está establecido en el valor más bajo posible para la aplicación. Unity establece de forma predeterminada un plano de recorte lejano de 1000 m. En HoloLens, un plano de recorte lejano de 50 m suele ser más que suficiente para la mayoría de los escenarios de aplicación.

> [!NOTE]
> Si usa el formato de profundidad de *16* bits , los efectos necesarios del búfer de galería de símbolos no funcionarán porque Unity no crea un búfer [de](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) galería de símbolos en esta configuración. Al seleccionar el formato de profundidad de *24* bits por el contrario, se suele crear un búfer de galería de símbolos de 8 bits, si procede en la plataforma de gráficos de punto de conexión.
>
> Si usa un componente [Mask](https://docs.unity3d.com/Manual/script-Mask.html) que requiere el búfer de galería de símbolos, considere la posibilidad de usar [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) en su lugar, que no requiere el búfer de galería de símbolos y, por tanto, se puede usar junto con un formato de profundidad de *16* bits .

> [!NOTE]
> Para determinar rápidamente qué objetos de una escena no escriben visualmente [](../configuration/mixed-reality-configuration-guide.md#editor-utilities) en el búfer de profundidad, se puede usar la utilidad Búfer de profundidad de representación en la configuración del *editor* en el perfil de configuración de MRTK.

### <a name="optimize-mesh-data"></a>Optimización de datos de malla

La [configuración Optimizar datos de](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) malla intenta quitar atributos de vértices no utilizados dentro de la aplicación. La configuración realiza esta operación mediante la ejecución de cada paso del sombreador en cada material que se encuentra en cada malla de la compilación. Esto es bueno para el tamaño de los datos del juego y el rendimiento en tiempo de ejecución, pero puede dificultar drásticamente los tiempos de compilación.

Se recomienda deshabilitar esta configuración durante el desarrollo y volver a habilitarla durante la creación de la compilación "Maestra". La configuración se puede encontrar en **Editar** configuración del proyecto Player Other Settings Optimize Mesh Data (Editar configuración del proyecto Reproductor  >    >    >  **de otras configuraciones**  >  **Optimizar datos de malla).**

## <a name="general-recommendations"></a>Recomendaciones generales

El rendimiento puede ser un desafío ambiguo y cambiante para los desarrolladores de realidad mixta y el espectro de conocimientos para racionalizar el rendimiento es amplio. Sin embargo, hay algunas recomendaciones generales para comprender cómo abordar el rendimiento de una aplicación.

Resulta útil simplificar la ejecución de una aplicación en las partes que se ejecutan en la *CPU* o la *GPU* y, por tanto, identificar si una aplicación está limitada por cualquiera de los componentes.  Puede haber cuellos de botella que abarquen las unidades de procesamiento y algunos escenarios únicos que deben investigarse cuidadosamente. Sin embargo, para empezar, es bueno comprender dónde se ejecuta una aplicación durante la mayor cantidad de tiempo.

### <a name="gpu-bounded"></a>Límite de GPU

Dado que la mayoría de las [](https://en.wikipedia.org/wiki/Stereoscopy)plataformas para aplicaciones de realidad mixta utilizan la representación estereomática, es muy común estar delimitada por GPU debido a la naturaleza de representar una pantalla de "doble ancho". Además, las plataformas de realidad mixta para dispositivos móviles, como HoloLens o OculusException, estarán limitadas por la CPU de clase móvil & potencia de procesamiento de GPU.

Al centrarse en la GPU, generalmente hay dos fases importantes en las que una aplicación debe completar cada fotograma.

1. Ejecución del [sombreador de vértices](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. Ejecutar el [sombreador de píxeles](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (también conocido como sombreador de fragmentos)

Sin entrar en profundidad en el complejo campo de [gráficos](https://en.wikipedia.org/wiki/Graphics_pipeline)de equipo & canalizaciones de representación, cada fase del sombreador es un programa que se ejecuta en la GPU para generar lo siguiente.

1. Los sombreadores de vértices transforman los vértices de malla en coordenadas en el espacio de pantalla (es decir, código ejecutado por vértice)
2. Los sombreadores de píxeles calculan el color que se dibujará para un fragmento de píxel y malla determinado (es decir, ejecución de código por píxel)

En lo que respecta al ajuste del rendimiento, normalmente es más fructífera centrarse en optimizar las operaciones en el sombreador de píxeles. Es posible que una aplicación solo necesite dibujar un cubo que solo será de 8 vértices. Sin embargo, el espacio de pantalla que ocupa el cubo es probable que esté en el orden de millones de píxeles. Por lo tanto, reducir el código del sombreador al decir 10 operaciones puede ahorrar mucho más trabajo si se reduce en el sombreador de píxeles que el sombreador de vértices.

Esta es una de las principales razones para aprovechar el sombreador ESTÁNDAR DE [MRTK,](../features/rendering/mrtk-standard-shader.md) ya que este sombreador suele ejecutar muchas instrucciones menos por píxel & vértice que el sombreador Estándar de Unity, a la vez que se logran resultados éticos comparables.

|    Optimizaciones de CPU      |             Optimizaciones de GPU              |
|---------------------------|--------------------------------------------|
| Lógica de simulación de aplicación      | Operaciones de representación |
| Simplificar la física          | Reducción de los cálculos de iluminación |
| Simplificar animaciones       | Reducir el número de & número de objetos dibujables |
| Administrar la recolección de elementos no utilizados | Reducir el número de objetos transparentes |
| Referencias de caché          | Evitar efectos posteriores al procesamiento o a pantalla completa  |

### <a name="draw-call-instancing"></a>Creación de instancias de llamada a Draw

Uno de los errores más comunes de Unity que reduce el rendimiento es la clonación de materiales en tiempo de ejecución. Si gameObjects comparte el mismo material o son la misma malla, se pueden optimizar en *[](https://docs.unity3d.com/Manual/DrawCallBatching.html)* llamadas de dibujo único a través de técnicas como el procesamiento por lotes *[estático,](https://docs.unity3d.com/Manual/DrawCallBatching.html)* el procesamiento por lotes dinámico y la creación de instancias de *[GPU.](https://docs.unity3d.com/Manual/GPUInstancing.html)* Sin embargo, si el desarrollador modifica las propiedades del [material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) de un representador en tiempo de ejecución, Unity creará una copia clonada del material asignado.

Por ejemplo, si hay 100 cubos en una escena, es posible que un desarrollador quiera asignar un color único a cada uno en tiempo de ejecución. El acceso de [*renderer.material.color*](https://docs.unity3d.com/ScriptReference/Material-color.html) en C# hará que Unity cree un nuevo material en memoria para este representador o GameObject en particular. Cada uno de los 100 cubos tendrá su propio material y, por tanto, no se pueden combinar en una llamada a draw, sino que se convertirán en 100 solicitudes de llamada de dibujo de la CPU a la GPU.

Para superar este obstáculo y seguir asignando un color único por cubo, los desarrolladores deben aprovechar [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a>Herramientas de rendimiento de Unity

Unity proporciona excelentes herramientas de rendimiento integradas en el editor.

- [Unity Profiler](https://docs.unity3d.com/Manual//Profiler.html)
- [Depurador de fotogramas de Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

Si calcula el equilibrio de rendimiento aproximado entre un sombreador y otro, resulta útil compilar cada sombreador y ver el número de operaciones por fase de sombreador. Para ello, seleccione un recurso de [sombreador](https://docs.unity3d.com/Manual/class-Shader.html) y haga clic en el botón *Compilar y mostrar* código. Esto compilará todas las variantes del sombreador y abrirá Visual Studio con los resultados. Nota: Los resultados estadísticos generados pueden variar en función de las características que se hayan habilitado en los materiales que utilizan el sombreador especificado. Unity solo compilará las variantes del sombreador que se usan directamente en el proyecto actual.

Ejemplo de estadísticas de sombreador estándar de Unity

![Estadísticas de sombreador estándar de Unity 1](../features/images/performance/UnityStandardShader-Stats.PNG)

Ejemplo de estadísticas de sombreador estándar de MRTK

![Estadísticas de sombreador estándar de MRTK 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>Consulte también

### <a name="unity"></a>Unity

- [Optimización del rendimiento de Unity para principiantes](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Tutoriales de optimización del rendimiento de Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Procedimientos recomendados de optimización de Unity](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [Optimización del rendimiento de gráficos](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [Guía práctica de optimización móvil](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Configuración recomendada para Unity](/windows/mixed-reality/recommended-settings-for-unity)
- [Descripción del rendimiento de Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recomendaciones de rendimiento para Unity](/windows/mixed-reality/performance-recommendations-for-unity)
- [guía Seguimiento de eventos para Windows Unity](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [Instrucciones de rendimiento](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [Herramientas de rendimiento](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>Optimización de malla

- [Optimización de modelos 3D](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Procedimientos recomendados para convertir y optimizar modelos 3D en tiempo real](/dynamics365/mixed-reality/import-tool/best-practices)