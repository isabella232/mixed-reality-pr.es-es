---
title: OpenXR
description: Compile un motor con el estándar de API de OpenXR portátil e impleméntelo en Windows Mixed Reality y HoloLens 2 cascos.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, hoja de ruta, extensiones, Khronos, BasicXRApp, DirectX, aplicación nativa, nativa, motor personalizado, middleware
ms.openlocfilehash: e9071f8b15f19be564b7c246244a5b7561aa5968
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042246"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR es un estándar de API abierto sin regalías de <a href="https://www.khronos.org/" target="_blank">Khronos,</a>que proporciona a los motores acceso nativo a una variedad de dispositivos en el espectro [de realidad mixta.](../../discover/mixed-reality.md)

Puede desarrollar mediante OpenXR en un HoloLens 2 o Windows Mixed Reality envolvente de REALIDAD virtual en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de Windows Mixed Reality en su lugar.

## <a name="why-openxr"></a>¿Por qué OpenXR?

Con OpenXR, puede crear motores destinados a dispositivos holográficos, como HoloLens 2, y dispositivos vr envolventes, como cascos de Windows Mixed Reality para equipos de escritorio. OpenXR le permite escribir código una vez que se pueda transportar a través de una amplia gama de plataformas de hardware.

La API de OpenXR usa un cargador para conectar la aplicación directamente a la compatibilidad nativa de la plataforma del casco. Los usuarios finales obtienen el máximo rendimiento y la latencia mínima, tanto si usan un Windows Mixed Reality como cualquier otro casco.

## <a name="what-is-openxr"></a>¿Qué es OpenXR?

La API de OpenXR proporciona la predicción de posición principal, el tiempo de fotogramas y la funcionalidad de entrada espacial que necesitará para crear un motor que pueda tener como destino dispositivos holográficos y envolventes.

Para obtener información sobre la API de OpenXR, consulte <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank"></a>la especificación de OpenXR 1.0, la referencia de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API</a>y la <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">guía de referencia rápida</a>.  Para obtener más información, vea la página <a href="https://www.khronos.org/openxr/" target="_blank">de OpenXR de Khronos</a>.

Para tener como destino el conjunto de características completo de HoloLens 2, también usará extensiones openXR específicas del proveedor y entre proveedores que permiten características adicionales más allá del núcleo de OpenXR 1.0, como el seguimiento de manos articulados, el seguimiento de los ojos, la asignación espacial y los anclajes espaciales. Para obtener más información, consulte la sección [Mapa de ruta a](#roadmap) continuación sobre las extensiones que se publicarán más adelante este año.

OpenXR no es en sí mismo un motor de realidad mixta.  En su lugar, OpenXR permite que motores como Unity y Unreal escriban código portátil una vez que puedan acceder a las características nativas de la plataforma del dispositivo holográfico o inmersivo del usuario, sea cual sea el proveedor que haya creado esa plataforma.

## <a name="roadmap"></a>Plan de desarrollo

La especificación openXR define un mecanismo de extensión que [](#what-is-openxr) permite a los implementadores en tiempo de ejecución exponer funcionalidades adicionales más allá de las características principales definidas en la especificación <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">base de OpenXR 1.0.</a>

Hay tres tipos de extensiones openXR:
* **Extensiones de proveedor (por ejemplo, `MSFT` ):** habilita la innovación por proveedor en características de hardware o software.  Cualquier proveedor en tiempo de ejecución puede introducir y enviar una extensión de proveedor en cualquier momento.
  * **Extensiones de proveedor experimentales (por ejemplo, `MSFT_preview` ):** las extensiones de proveedor experimentales se están visualizando para recopilar comentarios.  `MSFT_preview` Las extensiones son solo para dispositivos de desarrollador y se quitarán cuando se distribuye la extensión real.  Para experimentar con ellas, puede habilitar las extensiones en versión [preliminar en el dispositivo para desarrolladores.](openxr-getting-started.md#using-preview-extensions)
* **Extensiones entre `EXT` proveedores:** extensiones entre proveedores que varias empresas definen e implementan.  Los grupos de empresas interesadas pueden introducir extensiones EXT en cualquier momento.
* **Extensiones `KHR` oficiales: extensiones** oficiales de Khronos que se han publicado como parte de una versión de especificación principal.  Las extensiones DEER están cubiertas por la misma licencia que la propia especificación principal.

El Windows Mixed Reality openxr runtime admite un conjunto de extensiones y que aporta el conjunto completo de características HoloLens 2 a `MSFT` `EXT` las aplicaciones OpenXR:

| Área de función | Disponibilidad de extensiones |
|--------------|------------------------|
| Sistemas y sesiones | **Especificación de núcleo de OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Espacios de referencia (vista, local, fase)](../../design/coordinate-systems.md) | **Especificación de núcleo de OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Ver configuraciones (mono, estéreo) | **Especificación de núcleo de OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Cadenas de intercambio](../platform-capabilities-and-apis/rendering.md)  +  [tiempo de fotogramas](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **Especificación de núcleo de OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Capas de composición<br />(proyección, quad) | **Especificación de núcleo de OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Entrada y hápticos](../../design/interaction-fundamentals.md) | **Especificación de núcleo de OpenXR 1.0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integración de Direct3D 11 | **Extensión `KHR` oficial publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Integración de Direct3D 12 | **Extensión `KHR` oficial publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Espacio de referencia sin enlazar <br /> (experiencias de escala mundial)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Delimitadores espaciales](../../design/spatial-anchors.md) | <p>**`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code></p><p>**`MSFT_preview`Extensión en tiempo [de ejecución de versión preliminar 107:](openxr-getting-started.md#using-preview-extensions)**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_anchor_persistence_preview">XR_MSFT_spatial_anchor_persistence_preview</a></code></p> |
| [Interacción con la <br /> mano (posición de control/objetivo, pulsación en el aire, agarre)](../../design/hands-and-tools.md)<p>*HoloLens 2 solo*</p> | **`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Articulación de la mano + malla de mano](../../design/hands-and-tools.md)<p>*HoloLens 2 solo*</p> | <p>**`EXT` extensión publicada:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Mirada con ojo](../../design/eye-tracking.md)<p>*HoloLens 2 solo*</p> | **`EXT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| [Captura de realidad mixta <br /> (tercera representación desde la cámara PV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2 solo*</p> | **`MSFT` Extensiones publicadas:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interoperabilidad con otros SDK Mixed Reality de datos<br />(por ejemplo, [QR)](../platform-capabilities-and-apis/qr-code-tracking.md) | <p>**`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` Extensión publicada en tiempo de ejecución 105:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| Interoperabilidad con coreWindow API de UWP<br />(por ejemplo, para el teclado y el mouse) | **`MSFT` Extensión publicada en tiempo de ejecución 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Perfiles de interacción del controlador de movimiento<br />(Samsung Samsung Samsung y HP Reverb G2) | **`MSFT` Extensiones publicadas en tiempo de ejecución 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Modelos de representación del controlador de movimiento](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` Extensión publicada en tiempo de ejecución 104:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Descripción de la escena (planos, mallas)](../../design/scene-understanding.md)<p>*HoloLens 2 solo*</p> | <p>**`MSFT` Extensión publicada en tiempo de ejecución 106:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding">XR_MSFT_scene_understanding</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding_serialization">XR_MSFT_scene_understanding_serialization</a></code></p> |
| [Modos de reproducción de la capa de composición (reproducción plana automática o solo <br /> orientación)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` Extensión publicada en tiempo de ejecución 106:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_composition_layer_reprojection">XR_MSFT_composition_layer_reprojection</a></code> |
| Otras extensiones entre proveedores | <p>**Extensiones `KHR` oficiales publicadas:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code></p><p>**`EXT` Extensiones publicadas:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code></p> |

Aunque algunas de estas extensiones pueden empezar como extensiones específicas del proveedor, Microsoft y otros proveedores en tiempo de ejecución de OpenXR trabajan conjuntamente para diseñar extensiones o entre proveedores para muchas de estas áreas de `MSFT` `EXT` `KHR` características. Las extensiones entre proveedores harán que el código que escriba para esas características sea portátil entre proveedores en tiempo de ejecución, como con la especificación principal.

## <a name="getting-started-with-openxr"></a>Introducción a OpenXR

![Captura de pantalla de la interpretación de Quesada por un usuario con un casco de realidad mixta](images/openxr-minecraft.jpg)

*El nuevo motor Render Creative de Chips ha creado su compatibilidad de realidad virtual de escritorio con OpenXR.*

Microsoft ha estado trabajando con Unity y Epic Games para asegurarse de que el futuro de la realidad mixta está abierto, no solo para HoloLens 2, sino en toda la gama de PC VR, incluido el nuevo casco [Reverb G2](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)de HP.  OpenXR potencia la compatibilidad de realidad virtual entre proveedores para los títulos principales que se entregan hoy en día, como , Por ejemplo, y Simulador de vuelos de Microsoft.  Para obtener más información sobre el desarrollo para HoloLens (1.ª generación), vea las [notas de la versión](/hololens/hololens1-release-notes).

Para obtener información sobre cómo empezar a trabajar con OpenXR en Unity, Unreal Engine o su propio motor, siga leyendo.

### <a name="openxr-in-unity"></a>OpenXR en Unity

La configuración de Unity recomendada actualmente de Microsoft para el desarrollo de HoloLens 2 y Windows Mixed Reality es **Unity 2020.3 LTS** con el complemento openXR Mixed Reality más reciente.  Este complemento incluye compatibilidad con las extensiones OpenXR que encienden todas las funcionalidades de los [cascos HoloLens 2](#roadmap)y Windows Mixed Reality, incluido el seguimiento de manos y ojos, anclajes espaciales y controladores HP Reverb G2.  MRTK-Unity admite OpenXR a partir de [MRTK 2.7.](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)  Para obtener más información sobre cómo empezar a trabajar con Unity 2020 y OpenXR, consulte [Elección de una versión de Unity.](../unity/choosing-unity-version.md)

Si vas a desarrollar para HoloLens (1ª generación), tendrás que seguir usando **Unity 2019.4 LTS** con el back-end heredado de la API de WinRT.  Si tiene como destino el nuevo controlador HP Reverb G2 en una aplicación de Unity 2019, consulte nuestros documentos de entrada de [HP Reverb G2.](../unity/unity-reverb-g2-controllers.md)

A partir **de Unity 2021.2,** OpenXR será el único back-end de Unity compatible para dirigirse a HoloLens 2 y Windows Mixed Reality cascos.

### <a name="openxr-in-unreal-engine"></a>OpenXR en Unreal Engine

Unreal Engine 4.23 fue la primera versión principal del motor de juegos en enviar compatibilidad con la versión preliminar para OpenXR 1.0.  Ahora, en **Unreal Engine 4.26,** la compatibilidad con HoloLens 2, Windows Mixed Reality y otros cascos vr de escritorio está disponible a través de la compatibilidad integrada de OpenXR de Unreal Engine.  Unreal Engine 4.26 también admite el complemento de extensión [OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)de Microsoft, lo que permite la interacción con la mano y la compatibilidad con el controlador HP Reverb G2, lo que activa el conjunto completo de características de [HoloLens 2 y Windows Mixed Reality cascos](#roadmap).  Unreal Engine 4.26 está disponible hoy en el iniciador de [Epic Games,](https://www.unrealengine.com/download/creators)con MRTK-Unreal 0.12 compatible con proyectos de OpenXR.

### <a name="openxr-for-native-development"></a>OpenXR para desarrollo nativo

Puede desarrollar mediante OpenXR en un HoloLens 2 o Windows Mixed Reality casco de realidad virtual inmersivo en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de Windows Mixed Reality en su lugar.

Para empezar a desarrollar aplicaciones OpenXR para HoloLens 2 o Windows Mixed Reality cascos vr, consulte introducción al desarrollo [de OpenXR.](openxr-getting-started.md)

Para un paseo por todos los componentes principales de la API de OpenXR, junto con ejemplos de las aplicaciones reales que usan OpenXR hoy en día, consulte este vídeo de tutorial de 60 minutos:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Consulte también

* <a href="https://www.khronos.org/openxr/" target="_blank">Más información sobre OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificación de OpenXR 1.0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referencia de la API de OpenXR 1.0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida de OpenXR 1.0</a>