---
title: estabilización de hologramas
description: Rendimiento de hologramas en diferentes condiciones de entorno y velocidad de fotogramas.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, seguimiento del entorno, TMP,
ms.openlocfilehash: 4ea3f62153676154188584221c83ac97b5589e05
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528724"
---
# <a name="hologram-stabilization"></a>Estabilización del holograma

## <a name="performance"></a>Rendimiento

Para que la plataforma y el dispositivo de realidad mixta subyacentes produzcan los mejores resultados, es importante lograr velocidades de fotogramas. La velocidad de fotogramas de destino (por ejemplo, 60 FPS o 90 FPS) variará entre plataformas y dispositivos. Sin embargo, las aplicaciones de realidad mixta que se reúnen con la velocidad de fotogramas tendrán hologramas estables, así como un seguimiento eficaz de la cabeza, el seguimiento de manos y mucho más.  

## <a name="environment-tracking"></a>Seguimiento del entorno

La representación holográfica estable se basa en gran medida en el seguimiento de la posición de la cabeza por parte de la plataforma & dispositivo. Unity representará la escena en cada fotograma de la posición de la cámara estimada y proporcionada por la plataforma subyacente. Si este seguimiento no sigue correctamente el movimiento real de la cabeza, los hologramas aparecerán visualmente inexactos. Esto es especialmente evidente e importante para dispositivos de AR como HoloLens, donde los usuarios pueden relacionar hologramas virtuales con el mundo real. El rendimiento es significativo para el seguimiento de la cabeza confiable, pero también puede haber [otras características](/windows/mixed-reality/environment-considerations-for-hololens)importantes. Los tipos de elementos de entorno que afectan a la experiencia del usuario dependerán de los detalles específicos de la plataforma de destino.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

La Windows Mixed Reality proporciona algún [material de referencia para](/windows/mixed-reality/hologram-stability) estabilizar hologramas en la plataforma. Sin embargo, hay una serie de herramientas clave que los desarrolladores pueden usar para mejorar la experiencia visual del holograma para los usuarios.

### <a name="depth-buffer-sharing"></a>Uso compartido del búfer de profundidad

Los desarrolladores de Unity tienen la opción de compartir el búfer de profundidad de la aplicación con la plataforma. Esto proporciona información, donde existen hologramas para un marco actual, que la plataforma puede usar para estabilizar hologramas a través de un proceso asistido por hardware conocido como Late-Stage proyecto.

#### <a name="late-stage-reprojection"></a>Reproducción en fase tardía

Al final de la representación de un fotograma, la plataforma Windows Mixed Reality toma los destinos de representación de profundidad de color & generados por la aplicación y transforma la salida final de la pantalla para tener en cuenta cualquier movimiento ligero de la cabeza desde la última predicción de posición de la cabeza. El bucle de juego de una aplicación tarda tiempo en ejecutarse. Por ejemplo, a 60 FPS, esto significa que la aplicación está tardando ~16,667 ms en representar un fotograma. Aunque esto pueda parecer una cantidad mínima de tiempo, la posición y la orientación de la cabeza del usuario cambiarán, lo que dará lugar a nuevas matrices de proyección para la cámara en la representación. La reproducción en fase avanzada transforma los píxeles de la imagen final para tener en cuenta esta nueva perspectiva.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>LSR de plano por píxel frente a estabilización

Según el punto de conexión del dispositivo y la versión del sistema operativo que se ejecute en un dispositivo Windows Mixed Reality, el algoritmo de reproducción de Late-Stage se realizará por píxel o a través de un plano de [estabilización](/windows/mixed-reality/hologram-stability#stabilization-plane).

##### <a name="per-pixel-depth-based"></a>Basado en profundidad por píxel

La reproducción basada en profundidad por píxel implica el uso del búfer de profundidad para modificar la salida de la imagen por píxel y, por tanto, estabilizar hologramas a varias distancias. Por ejemplo, una esfera de 1 m de distancia puede estar delante de un pilar que está a 10 m de distancia. Los píxeles que representan la esfera tendrán una transformación diferente de los píxeles lejanos que representan el pilar si el usuario ha inclinado ligeramente la cabeza. La reproducción por píxel tendrá en cuenta esta diferencia de distancia en cada píxel para una reproducción más precisa.

##### <a name="stabilization-plane"></a>Plano de estabilización

Si no es posible crear un búfer de profundidad preciso para compartirlo con la plataforma, otra forma de LSR utiliza un plano de estabilización. Todos los hologramas de una escena recibirán alguna estabilización, pero los hologramas situados en el plano deseado recibirán la estabilización máxima del hardware. El punto y la normalidad del plano se pueden proporcionar a la plataforma a través de la API *HolographicSettings.SetFocusPointForFrame* [proporcionada por Unity](/windows/mixed-reality/focus-point-in-unity).

#### <a name="depth-buffer-format"></a>Formato de búfer de profundidad

Si el destino es HoloLens para el desarrollo, se recomienda encarecidamente usar el formato de búfer de profundidad de 16 bits en comparación con 24 bits. Esto puede ahorrar enormemente en el rendimiento, aunque los valores de profundidad tendrán menos precisión. Para compensar la precisión inferior y evitar [z-fighting,](https://en.wikipedia.org/wiki/Z-fighting)se recomienda reducir el plano de recorte lejano del valor predeterminado de 1000 m establecido por Unity. [](https://docs.unity3d.com/Manual/class-Camera.html)

> [!NOTE]
> Si usa el formato de profundidad de *16* bits , los efectos necesarios del búfer de galería de símbolos no funcionarán porque [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) no crea un búfer de galería de símbolos en esta configuración. Al seleccionar el formato de profundidad de *24* bits por el contrario, normalmente se creará un búfer de galería de símbolos de [8](https://docs.unity3d.com/Manual/SL-Stencil.html)bits, si procede en la plataforma de gráficos de punto de conexión.

#### <a name="depth-buffer-sharing-in-unity"></a>Uso compartido del búfer de profundidad en Unity

Para usar LSR basado en profundidad, hay dos pasos importantes que los desarrolladores deben seguir.

1. En **Edit**  >  **Project Settings**  >  **Player**  >  **XR Settings**  >  **Virtual Reality SDKs** (Editar  configuración del proyecto) los SDK de realidad virtual > uso compartido del búfer de profundidad
    1. Si el destino es HoloLens, se recomienda seleccionar también el formato de profundidad de **16** bits.
1. Al representar el color en pantalla, la profundidad de representación también

[Los objetos GameObject opacos](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) de Unity generalmente escribirán en profundidad automáticamente. Sin embargo, los & de texto transparentes generalmente no escribirán en profundidad de forma predeterminada. Si se utiliza el sombreador estándar de MRTK o Text Mesh Pro, esto se puede corregir fácilmente.

> [!NOTE]
> Para determinar rápidamente qué objetos de una escena no escriben visualmente en el búfer de profundidad, se puede usar la utilidad Render [ *Depth Buffer*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) en La configuración del *editor* del perfil de configuración de MRTK.

##### <a name="transparent-mrtk-standard-shader"></a>Sombreador estándar de MRTK transparente

En el caso de los materiales transparentes que usan el sombreador ESTÁNDAR DE [MRTK,](../features/rendering/MRTK-standard-shader.md)seleccione el material para verlo en la *ventana Inspector.* A continuación, haga clic *en el* botón Corregir ahora para convertir el material para escribir en profundidad (es decir, Z-Write On).

Antes

![Búfer de profundidad antes de corregir el sombreador estándar de MRTK](../features/images/performance/DepthBufferFixNow_Before.PNG)

Después

![Búfer de profundidad corregido sombreador estándar de MRTK](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Text Mesh Pro

En Objetos de Text Mesh Pro, seleccione el objeto GameObject de TMP para verlo en el inspector. En el componente de material, cambie el sombreador del material asignado para usar el sombreador TextMeshPro de MRTK.

![Corrección del búfer de profundidad de Text Mesh Pro](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>Sombreador personalizado

Si escribe un sombreador personalizado, agregue la marca [ZWrite](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) a la parte superior de la definición del bloque *Pass* para configurar el sombreador para escribir en el búfer de profundidad.

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>Respaldos opacos

Si los métodos anteriores no funcionan para un escenario determinado (es decir, mediante la interfaz de usuario de Unity), es posible que otro objeto escriba en el búfer de profundidad. Un ejemplo común es el uso de texto de interfaz de usuario de Unity en un panel flotante de una escena. Al hacer que el panel sea opaco o al menos escribir en profundidad, la plataforma estabilizará el texto & el panel, ya que sus valores z están tan cerca unos de otros.

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens)

Además de garantizar que se cumplen las configuraciones correctas para garantizar la estabilidad visual, es importante asegurarse de que los hologramas permanecen estables en sus ubicaciones físicas correctas. Para informar a la plataforma sobre ubicaciones importantes en un espacio físico, los desarrolladores pueden aprovechar [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) en GameObjects que necesitan permanecer en un solo lugar. [WorldAnchor es](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) un componente agregado a un GameObject que toma el control absoluto sobre la transformación de ese objeto.

Los dispositivos como HoloLens analizan y aprenden constantemente sobre el entorno. Por lo tanto, a medida que HoloLens realiza un seguimiento del movimiento & posición en el espacio, se actualizarán sus estimaciones y se ajustará el sistema de [coordenadas de Unity.](/windows/mixed-reality/coordinate-systems-in-unity) Por ejemplo, si un GameObject se coloca a 1 m de la cámara al principio, ya que HoloLens realiza un seguimiento del entorno, puede darse cuenta de que el punto físico donde se encuentra el GameObject está a 1,1 m de distancia. Esto daría lugar a que el holograma se desviase. La aplicación de WorldAnchor a un GameObject permitirá que el delimitador controle la transformación del objeto para que el objeto permanezca en la ubicación física correcta (es decir, actualizar a 1,1 m de distancia en lugar de 1 m en tiempo de ejecución). Para conservar [WorldAnchors entre](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) sesiones de aplicación, los desarrolladores pueden emplear [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) para guardar y [cargar WorldAnchors.](/windows/mixed-reality/persistence-in-unity)

> [!NOTE]
> Una vez que se ha agregado un componente WorldAnchor a un GameObject, no es posible modificar la transformación de ese GameObject (es decir, transform.position = x). Un desarrollador debe quitar WorldAnchor para editar la transformación.

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

Si desea una alternativa a trabajar manualmente con anclajes, consulte Microsoft World Locking Tools. 

> [!div class="nextstepaction"]
> [Instalar con la herramienta de características de MR](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>Consulta también

- [Rendimiento](../performance/perf-getting-started.md)
- [Consideraciones sobre el entorno para HoloLens](/windows/mixed-reality/environment-considerations-for-hololens)
- [Estabilidad del holograma Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Punto de enfoque en Unity](/windows/mixed-reality/focus-point-in-unity)
- [Sistemas de coordenadas de Unity](/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistencia en Unity](/windows/mixed-reality/persistence-in-unity)
- [Descripción del rendimiento de Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Recomendaciones de rendimiento para Unity](/windows/mixed-reality/performance-recommendations-for-unity)