---
title: Configuración recomendada para Unity
description: Obtenga información sobre los comportamientos de rendimiento y publicación de Unity específicos de las aplicaciones de realidad mixta que se pueden alternar a través de la configuración del proyecto.
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: unity, settings, mixed reality, HoloLens, mixed reality headset, windows mixed reality headset, virtual reality headset, performance, quality settings, lighting settings, depth buffer, xr, tracking loss
ms.openlocfilehash: 736ec4c1cc967eaae1ff53728d6e912c4f03a1f17ef75450c93e58b1a1f0064d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211843"
---
# <a name="recommended-settings-for-unity"></a>Configuración recomendada para Unity

Unity proporciona un conjunto de opciones predeterminadas que suelen ser el caso medio de todas las plataformas. Sin embargo, Unity ofrece algunos comportamientos específicos de la realidad mixta que se pueden alternar a través de la configuración del proyecto.

## <a name="performant-environment-set-up"></a>Configuración del entorno de rendimiento

### <a name="low-quality-settings"></a>Configuración de baja calidad

Es importante modificar la configuración de  calidad de **Unity** a Muy bajo para que la aplicación se ejecute y funcione correctamente con la velocidad de fotogramas adecuada, especialmente para HoloLens desarrollo. Para el desarrollo en cascos envolventes, en función de las especificaciones del escritorio que potencia la experiencia de realidad virtual, todavía se puede lograr la velocidad de fotogramas sin los parámetros de calidad más baja.

En Unity 2019 LTS+, puede establecer el nivel de calidad del proyecto; para ello, vaya a **Edit** Project Configuración Quality (Editar calidad de Project Configuración) y establezca default (Predeterminado) haciendo clic en la flecha hacia abajo en el nivel  >    >   **Very Low-quality level  (Muy baja calidad).

### <a name="lighting-settings"></a>Configuración de iluminación

De forma similar a la configuración de la escena de calidad, es importante establecer la configuración de iluminación óptima para Mixed Reality aplicación. En Unity, la configuración de iluminación que normalmente tendrá el mayor impacto en el rendimiento en la escena es **Iluminación global en tiempo real.** Para desactivar la iluminación global, vaya a **Window**  >  **Rendering**  >  **Lighting Configuración**  >  Realtime Global Lighting (Iluminación de representación de ventanas Configuración **iluminación global en tiempo real).**

Hay otra configuración de iluminación, **La iluminación global al aire.** Esta configuración puede proporcionar resultados de rendimiento y visualmente sorprendentes en los cascos envolventes, pero no es aplicable para HoloLens desarrollo. **La iluminación global recién** hecho solo se calcula para objetos GameObject estáticos, que no se encuentran en escenas HoloLens debido a la naturaleza de un entorno desconocido y cambiante.

Lea [Iluminación global de Unity](https://docs.unity3d.com/Manual/GIIntro.html) para obtener más información. 

>[!NOTE]
> **La iluminación global en tiempo** real se establece por **escena** y, por tanto, los desarrolladores deben guardar esta propiedad para cada escena de Unity en su proyecto.

### <a name="single-pass-instancing-rendering-path"></a>Ruta de acceso de representación de creación de instancias de paso único

En Mixed Reality aplicaciones, la escena se representa dos veces, una por cada ojo para el usuario. En comparación con el desarrollo 3D tradicional, esto duplica eficazmente la cantidad de trabajo que se debe calcular. Es importante seleccionar la ruta de acceso de representación más eficaz en Unity para ahorrar en tiempo de CPU y GPU. La representación con instancia de paso único optimiza la canalización de representación de Unity para Mixed Reality aplicaciones y se recomienda habilitar esta configuración de forma predeterminada para cada proyecto.

Para habilitar esta característica en el proyecto de Unity

1)  Abre **Player XR Settings** (Configuración del reproductor XR) (ve a **Editar** > **Configuración del proyecto** > **Reproductor** > **XR Settings** [Configuración de XR]).
2) Selecciona **Single Pass Instanced** (Con instancia de un solo paso) en el menú desplegable **Stereo Rendering Method** (Método de representación en estéreo) (la casilla **Virtual Reality Supported** [Compatibilidad con realidad virtual] debe estar marcada)

Lea los siguientes artículos de Unity para obtener más detalles con este enfoque de representación.

- [Cómo maximizar el rendimiento de AR y VR con la representación en estéreo avanzada](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creación de instancias de un solo paso](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> Un problema común con la representación con instancia de un solo paso se produce si los desarrolladores ya tienen sombreadores personalizados no escritos para la creación de instancias. Después de habilitar esta característica, los desarrolladores pueden observar que algunos objetos GameObjects solo se representan en un ojo. Esto se debe a que los sombreadores personalizados asociados no tienen las propiedades adecuadas para la creación de instancias.
>
> Consulta [Representación en estéreo de un solo paso para HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) de Unity para solucionar este problema.

### <a name="enable-depth-buffer-sharing"></a>Habilitación del uso compartido del búfer de profundidad

Para lograr una mejor estabilidad del holograma desde la percepción del usuario, se recomienda habilitar la propiedad **Uso** compartido del búfer de profundidad en Unity. Al activar esta opción, Unity compartirá el mapa de profundidad generado por la aplicación con Windows Mixed Reality plataforma. A continuación, la plataforma puede optimizar mejor la estabilidad del holograma específicamente para la escena para cualquier fotograma determinado que represente la aplicación.

Para habilitar esta característica en el proyecto de Unity

1) Abre **Player XR Settings** (Configuración del reproductor XR) (ve a **Editar** > **Configuración del proyecto** > **Reproductor** > **XR Settings** [Configuración de XR]).
2) Active la casilla Enable **Depth Buffer Sharing** (Habilitar el uso compartido de búfer de profundidad) en Virtual **Reality SDKs**  >  **Windows Mixed Reality** expansion (la casilla Virtual **Reality Supported (Compatible con Virtual Reality)** debe estar activada).

Además, se recomienda seleccionar la profundidad de **16** bits en la opción **Formato** de profundidad de este panel, especialmente para HoloLens Desarrollo. La selección de 16 bits en comparación con 24 bits reducirá significativamente los requisitos de ancho de banda, ya que se tendrán que mover o procesar menos datos.

Para que la plataforma Windows Mixed Reality optimizar la estabilidad del holograma, se basa en que el búfer de profundidad sea preciso y coincida con los hologramas representados en la pantalla. Por lo tanto, con el uso compartido del búfer de profundidad en , es importante al representar el color, para representar también la profundidad. En Unity, la mayoría de los materiales Opacos o TransparenteCutout representarán la profundidad de forma predeterminada, pero los objetos de texto y transparentes no representarán la profundidad, aunque esto depende del sombreador, etc.

Si usa el [sombreador Mixed Reality Toolkit estándar](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader), para representar la profundidad de los objetos transparentes:

1) Seleccione el material transparente que usa el sombreador ESTÁNDAR DE MRTK y abra la ventana del editor inspector.
2) Seleccione el botón **Corregir ahora en** la advertencia de uso compartido del búfer de profundidad. Esto también se puede realizar manualmente estableciendo el modo **de representación** en **Personalizado**; a continuación, **establezca Modo** **en Transparente** y, por **último, establezca Escritura en** profundidad en **On**

> [!IMPORTANT]
> Los desarrolladores deben tener cuidado con la Z-fighting al cambiar estos valores junto con la configuración del plano cercano o lejano de la cámara. Z-Fighting se produce cuando dos objetos gameobject intentan representarse en el mismo píxel y debido a limitaciones en la fidelidad del búfer de profundidad (es decir, profundidad z), Unity no puede distinguir qué objeto está delante del otro. Los desarrolladores tendrán en cuenta un parpadeo entre dos objetos de juego *mientras* buscan el mismo valor de profundidad z. Esto se puede resolver cambiando al formato de profundidad de 24 bits, ya que habrá un intervalo mayor de valores para cada objeto en el que calcular su profundidad z desde la cámara.
>
> Sin embargo, se recomienda, especialmente para el desarrollo HoloLens, modificar los planos cercanos y lejanos de la cámara a un intervalo más pequeño en su lugar y conservar el formato de profundidad de 16 bits. La profundidad z no se asigna linealmente al intervalo de valores a lo largo de los planos de cámara cercanos y lejanos. Para modificarlo, seleccione  la cámara principal de la escena y, en **Inspector,** cambie los valores de Plano de recorte lejano de Near **&** para reducir su intervalo (es decir, de 1000 m a 100 m u otro valor x, etc.)

>[!IMPORTANT]
> [Unity no crea un búfer de galería de símbolos](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) cuando se usa el formato de profundidad de 16 bits. Por lo tanto, algunos efectos de la interfaz de usuario de Unity y otros efectos necesarios para la galería de símbolos no funcionarán a menos que se seleccione el formato de profundidad de 24 bits, lo que creará un búfer de galería de símbolos de [8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html).

### <a name="building-for-il2cpp"></a>Creación para IL2CPP

Unity ha dejado de ser compatible con el back-end de scripting de .NET y, por tanto, recomienda que los desarrolladores usen **IL2CPP** para sus compilaciones de Visual Studio para UWP. Aunque esto aporta varias ventajas, la creación de la solución de Visual Studio desde Unity **para IL2CPP** puede ser más lenta que el método antiguo de .NET. Por lo tanto, se recomienda encarecidamente seguir los procedimientos recomendados para compilar **IL2CPP** para ahorrar en el tiempo de iteración de desarrollo.

1) Aproveche la compilación incremental mediante la compilación del proyecto en el mismo directorio cada vez, y vuelva a usar allí los archivos pre compilados.
2) Deshabilitación de los exámenes de software antimalware para las carpetas de compilación & proyecto
   - Abra **Virus & threat protection en** la aplicación de Windows 10 configuración de aplicaciones
   - Seleccione **Administrar Configuración** en Configuración de protección contra amenazas & **virus**
   - Seleccione **Agregar o quitar exclusiones en** la sección **Exclusiones.**
   - Seleccione **Agregar una exclusión** y seleccione la carpeta que contiene el código del proyecto de Unity y las salidas de compilación.
3) Uso de un SSD para la creación

Lea [Optimización de los tiempos de compilación para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obtener más información.

> [!NOTE]
> Además, puede resultar útil configurar un [servidor de caché](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para los proyectos de Unity con una gran cantidad de activos (sin contar con los archivos de script), o que cambien constantemente de escenas o activos. Al abrir un proyecto, Unity almacena los activos aplicables en un formato de la memoria caché interna en la máquina del desarrollador. Los elementos se tienen que volver a importar y, por tanto, volver a procesar cuando se modifican. Este proceso se puede realizar una vez y guardar en un servidor de caché, de esta forma se comparte con otros desarrolladores, lo que ahorra tiempo al evitar que cada desarrollador tenga que procesar localmente los nuevos cambios que reimporte.

## <a name="publishing-properties"></a>Propiedades de publicación

### <a name="holographic-splash-screen"></a>Pantalla de presentación holográfica

HoloLens una CPU y GPU de clase móvil, lo que significa que las aplicaciones pueden tardar un poco más en cargarse. Mientras se carga la aplicación, los usuarios solo verán negro, por lo que es posible que se pregunten qué está ocurrindo. Para garantizarlos durante la carga, puede agregar una pantalla de presentación holográfica.

Para alternar la pantalla de presentación holográfica:

1) Vaya a **la página Editar**  >  **Project Configuración**  >  **Player.**
2) Seleccione la **Windows Store y** abra la sección Imagen de **presentación.**
3) Aplique la imagen en la Windows **holographic > propiedad Holographic Splash Image** ( Imagen de presentación holográfica).
    - Al alternar la opción **Mostrar pantalla de presentación de Unity,** se habilitará o deshabilitará la pantalla de presentación con marca de Unity. Si no tiene una licencia de Pro Unity, siempre se mostrará la pantalla de presentación de marca de Unity.
    - Si se **aplica una imagen de presentación** holográfica, siempre se mostrará si la casilla Mostrar pantalla de presentación de Unity está habilitada o deshabilitada. La especificación de una imagen de presentación holográfica personalizada solo está disponible para los desarrolladores con una licencia Pro Unity.

|  Mostrar pantalla de presentación de Unity  |  Imagen de presentación holográfica  |  Comportamiento |
|----------|----------|----------|
|  Activado  |  Ninguno  |  Mostrar la pantalla de presentación predeterminada de Unity durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. |
|  Activado  |  Personalizado  |  Mostrar pantalla de presentación personalizada durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. |
|  Desactivado  |  Ninguno  |  Mostrar negro transparente (nada) hasta que se cargue la aplicación. |
|  Desactivado  |  Personalizado  |  Mostrar pantalla de presentación personalizada durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. |

Lea [la documentación de pantalla de presentación de Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) para obtener más información.

### <a name="tracking-loss"></a>Pérdida de seguimiento

Un casco de realidad mixta depende de ver el entorno que lo rodea para construir sistemas de coordenadas bloqueados por el [mundo,](coordinate-systems-in-unity.md)que permiten que los hologramas permanezcan en su posición. Cuando el casco no se encuentra en el mundo, se dice que ha perdido *el seguimiento.* En estos casos, la funcionalidad dependiente de los sistemas de coordenadas bloqueados por el mundo, como las fases espaciales, los anclajes espaciales y la asignación espacial, no funcionan.

Si se produce una pérdida de seguimiento, el comportamiento predeterminado de Unity [](https://docs.unity3d.com/Manual/ExecutionOrder.html)es detener la representación de hologramas, pausar el bucle del juego y mostrar una notificación de pérdida de seguimiento que sigue cómodamente la mirada de los usuarios. También se pueden proporcionar notificaciones personalizadas en forma de imagen de pérdida de seguimiento. En el caso de las aplicaciones que dependen del seguimiento durante toda su experiencia, es suficiente dejar que Unity lo controle completamente hasta que se recupere el seguimiento. Los desarrolladores pueden proporcionar una imagen personalizada que se mostrará durante el seguimiento de la pérdida.

Para personalizar la imagen perdida de seguimiento:

1) Vaya a **la página Editar**  >  **Project Configuración**  >  **Player.**
2) Seleccione la pestaña **Windows store y** abra la sección Imagen de **presentación.**
3) Aplique la imagen en la Windows **holographic > Tracking Loss Image** (Imagen de pérdida de seguimiento).

#### <a name="opt-out-of-automatic-pause"></a>No participar en la pausa automática

Es posible que algunas aplicaciones no requieran seguimiento (por [ejemplo,](coordinate-systems-in-unity.md) aplicaciones de solo orientación, como visores de vídeo de 360 grados) o que necesiten seguir procesando sin interrupciones mientras se pierde el seguimiento. Puede rechazar la pérdida predeterminada del comportamiento de seguimiento, pero es responsable de ocultar o deshabilitar los objetos, que no se representaría correctamente en un escenario de pérdida de seguimiento. En la mayoría de los casos, el único contenido que se recomienda representar en ese caso es el contenido bloqueado por el cuerpo, centrado alrededor de la cámara principal.

Para rechazar el comportamiento de pausa automática:

1) Vaya a la **página**  >  **Editar Project Configuración**  >  **Player**
2) Seleccione la **pestaña Windows Store y** abra la sección Imagen de **presentación.**
3) Modifique la casilla **Windows holographic > On Tracking Loss Pause and Show Image** (Pausar y mostrar imagen al realizar el seguimiento de la pérdida).

#### <a name="tracking-loss-events"></a>Seguimiento de eventos de pérdida

Para definir el comportamiento personalizado cuando se pierde el seguimiento, controle los eventos [de pérdida de seguimiento globales](tracking-loss-in-unity.md).

### <a name="capabilities"></a>Funcionalidades

Para que una aplicación aproveche ciertas funcionalidades, debe declarar las funcionalidades adecuadas en su manifiesto. Las declaraciones de manifiesto se pueden realizar en Unity para que se incluyan en todas las futuras exportaciones de proyectos.

Las funcionalidades se pueden habilitar para Mixed Reality aplicación mediante:

1) Vaya a **la página Editar**  >  **Project Configuración**  >  **Player.**
2) Seleccione la **Windows Store,** abra la **sección Publishing Configuración** y busque la lista Capabilities **(Funcionalidades).**

Las funcionalidades aplicables para habilitar las API más usadas para aplicaciones holográficas son:
<br>

|  Capacidad  |  API que requieren funcionalidad |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  Webcam  |  PhotoCapture y VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture o VideoCapture, respectivamente (al almacenar el contenido capturado) |
|  Micrófono  |  VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (y para usar Unity Profiler) |

## <a name="see-also"></a>Consulte también

* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Análisis de rendimiento de la realidad mixta](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)