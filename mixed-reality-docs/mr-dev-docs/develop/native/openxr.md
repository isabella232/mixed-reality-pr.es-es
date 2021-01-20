---
title: OpenXR
description: Cree un motor mediante el estándar portable OpenXR API e impleméntelo en Windows Mixed Reality y en auriculares de HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware
ms.openlocfilehash: 76193cdf3c790037474b66de9fbbbd1da8f31199
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583793"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR es un estándar abierto de API sin derechos de autor de <a href="https://www.khronos.org/" target="_blank">Khronos</a>, que proporciona a los motores acceso nativo a una variedad de dispositivos en el [espectro de realidad mixta](../../discover/mixed-reality.md).

Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="why-openxr"></a>¿Por qué OpenXR?

Con OpenXR, puede compilar motores que tengan como destino dispositivos holográficas, como HoloLens 2, y dispositivos envolventes, como los auriculares de realidad mixta de Windows para equipos de escritorio. OpenXR le permite escribir código una vez que es portable a una amplia gama de plataformas de hardware.

La API de OpenXR usa un cargador para conectar la aplicación directamente a la compatibilidad con la plataforma nativa del casco. Los usuarios finales obtienen el máximo rendimiento y la latencia mínima, tanto si usan una realidad mixta de Windows como cualquier otro casco.

## <a name="what-is-openxr"></a>¿Qué es OpenXR?

La API de OpenXR proporciona la predicción de supuestos principales, la temporización de fotogramas y la funcionalidad de entrada espacial que necesitará para crear un motor que pueda tener como destino dispositivos holográficas y envolventes.

Para obtener información sobre la API de OpenXR, consulte las <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificaciones</a>de OpenXR 1,0, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">referencia de API</a>y <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida</a>.  Para obtener más información, consulte la <a href="https://www.khronos.org/openxr/" target="_blank">Página de OpenXR de Khronos</a>.

Para tener como destino el conjunto completo de características de HoloLens 2, también usará extensiones de OpenXR específicas entre proveedores y proveedores que habilitan características adicionales más allá del OpenXR 1,0 núcleo, como el seguimiento de mano articulado, el seguimiento ocular, la asignación espacial y los delimitadores espaciales. Para obtener más información, consulte la sección sobre el [mapa de ruta](#roadmap) más adelante en las extensiones que entrarán más tarde este año.

OpenXR no es en sí mismo un motor de realidad mixta.  En su lugar, OpenXR habilita motores como Unity y nonreal para escribir código portable una vez que pueda acceder a las características de la plataforma nativa del dispositivo Holographic o inmersivo del usuario, independientemente del proveedor que haya creado esa plataforma.

## <a name="roadmap"></a>Plan de desarrollo

La especificación OpenXR define un mecanismo de extensión que permite a los implementadores de tiempo de ejecución exponer funcionalidad adicional más allá de las [características principales](#what-is-openxr) definidas en la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificación 1,0 base OpenXR</a>.

Hay tres tipos de extensiones de OpenXR:
* **Extensiones de proveedor (por ejemplo, `MSFT` ):** permite la innovación por proveedor en características de hardware o software.  Cualquier proveedor en tiempo de ejecución puede introducir y enviar una extensión de proveedor en cualquier momento.
  * **Extensiones de proveedor experimentales (por ejemplo, `MSFT_preview` ):** se muestra una vista previa de las extensiones de proveedor experimental para recopilar comentarios.  `MSFT_preview` las extensiones son solo para dispositivos de desarrollador y se quitarán cuando se distribuya la extensión real.  Para experimentar con ellos, puede [habilitar las extensiones de vista previa en el dispositivo del desarrollador](openxr-getting-started.md#using-preview-extensions).
* **Extensiones entre proveedores `EXT` :** extensiones entre proveedores que varias empresas definen e implementan.  Los grupos de compañías interesadas pueden introducir extensiones EXT en cualquier momento.
* **`KHR` Extensiones oficiales:** extensiones oficiales de Khronos ratificadas como parte de una versión de especificación básica.  Las extensiones KHR están contempladas por la misma licencia que la propia especificación principal.

A partir del 2020 de julio, el tiempo de ejecución de OpenXR mixed reality de Windows admite un conjunto de `MSFT` `EXT` extensiones y que proporciona el conjunto completo de características de HoloLens 2 a las aplicaciones de OpenXR:

| Área de función | Disponibilidad de la extensión |
|--------------|------------------------|
| Sistemas + sesiones | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Espacios de referencia (ver, local, fase)](../../design/coordinate-systems.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Configuraciones de vista (mono, estéreo) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Intercambio](../platform-capabilities-and-apis/rendering.md)  +  [temporización de fotogramas](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Capas de composición<br />(proyección, cuádruple) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Entrada y hápticos](../../design/interaction-fundamentals.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integración de Direct3D 11 | **`KHR`Extensión oficial publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Integración de Direct3D 12 | **`KHR`Extensión oficial publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Espacio de referencia sin enlazar <br /> (experiencias a escala mundial)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Delimitadores espaciales](../../design/spatial-anchors.md) | **`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Interacción con la mano <br /> (replanteamiento/objetivo, toque de aire, agarre)](../../design/hands-and-tools.md)<p>*Solo HoloLens 2*</p> | **`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Articulation de mano + malla de mano](../../design/hands-and-tools.md)<p>*Solo HoloLens 2*</p> | <p>**`EXT` extensión Publicada en tiempo de ejecución 102:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` extensión Publicada en tiempo de ejecución 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Mirada con ojo](../../design/eye-tracking.md)<p>*Solo HoloLens 2*</p> | **`EXT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| Interoperabilidad con otros SDK de HoloLens<br />(por ejemplo, [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*Solo HoloLens 2*</p> | <p>**`MSFT` extensión Publicada en tiempo de ejecución 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` extensión en [tiempo de ejecución de vista previa 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_perception_anchor_interop_preview">XR_MSFT_perception_anchor_interop_preview</a></code></p> |
| [Captura de realidad mixta <br /> (tercera representación de la cámara PV)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*Solo HoloLens 2*</p> | **`MSFT` extensiones publicadas en tiempo de ejecución 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interoperabilidad con la API de CoreWindow de UWP<br />(por ejemplo, para el teclado o el mouse) | **`MSFT` extensión Publicada en tiempo de ejecución 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Perfiles de interacción del controlador de movimiento (Samsung Odyssey y HP reverberación G2) | **`MSFT` extensiones publicadas en tiempo de ejecución 103:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Modelos de representación de controlador de movimiento](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` extensión en [tiempo de ejecución de vista previa 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Comprensión de escenas (planos, mallas)](../../design/scene-understanding.md)<p>*Solo HoloLens 2*</p> | <p>**En el [tiempo de ejecución de versión preliminar 102 o posterior](openxr-getting-started.md#using-preview-extensions):**<br />Usar <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> con el [SDK de comprensión de escenas](../platform-capabilities-and-apis/scene-understanding-sdk.md)</p><p>**`MSFT_preview` extensión en tiempo de ejecución de vista previa futura** *(planeada)*</p> |
| Otras extensiones entre proveedores | <p>**`KHR`Extensiones oficiales publicadas:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT` extensiones publicadas:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Aunque algunas de estas extensiones pueden comenzar como extensiones específicas del proveedor `MSFT` , Microsoft y otros proveedores de tiempo de ejecución de OpenXR trabajan juntos para diseñar `EXT` varios proveedores o `KHR` extensiones para muchas de estas áreas de características. Las extensiones entre proveedores harán que el código que escriba para esas características portable entre proveedores en tiempo de ejecución, como con la especificación básica.

## <a name="getting-started-with-openxr"></a>Introducción a OpenXR

![Captura de pantalla de Minecraft que está jugando un usuario con auriculares de realidad mixta](images/openxr-minecraft.jpg)

*El nuevo motor de RenderDragon de Minecraft está creando su compatibilidad con Desktop VR mediante OpenXR*

Microsoft ha estado trabajando con juegos de Unity y Epic para asegurarse de que el futuro de la realidad mixta está abierto, no solo para HoloLens 2, sino a lo largo de toda la gama de equipos con la [nueva reverberación G2 de HP](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).  Para obtener más información sobre el desarrollo de HoloLens (1ª generación), consulte las notas de la [versión](/hololens/hololens1-release-notes).

Para obtener información sobre cómo empezar a trabajar con OpenXR en Unity, en un motor no real o en su propio motor, siga leyendo.

### <a name="openxr-in-unity"></a>OpenXR en Unity

Hoy en día, la ruta de acceso de desarrollo de Unity admitida para los auriculares HoloLens 2, HoloLens (1º gen) y Windows Mixed Reality es **Unity 2019 lts** con el back-end de la API de WinRT existente.  Puede saltar a [OpenXR con Unity](../unity/openxr-getting-started.md). Si tiene como destino el nuevo controlador de HP reverberación G2 en una aplicación Unity 2019, consulte los [documentos de entrada de HP reverberación G2](../unity/unity-reverb-g2-controllers.md).

A partir de **unity 2020 lts**, Unity enviará [un back-end de OpenXR](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) que admite los auriculares de la realidad de HoloLens 2 y Windows Mixed Reality.  Esto incluye la compatibilidad con las extensiones de OpenXR que imponen [toda la funcionalidad de los auriculares de realidad de HoloLens 2 y Windows Mixed Reality](#roadmap), como el seguimiento manual o ocular, los anclajes espaciales y los controladores de la reverberación de HP G2.  MRTK-Unity compatibilidad con OpenXR está actualmente en desarrollo en la [rama de mrtk_development](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development) y estará disponible junto con ese paquete de vista previa de OpenXR.

A partir de **Unity 2021**, OpenXR se graduará para ser el único back-end de Unity admitido para el destino de los auriculares con HoloLens 2 y Windows Mixed Reality.

### <a name="openxr-in-unreal-engine"></a>OpenXR en un motor inreal

A partir de un **motor inreal 4,23**, la compatibilidad total con los auriculares HoloLens 2 y Windows Mixed Reality está disponible a través del complemento de Windows Mixed Reality (WinRT).

Unreal Engine 4,23 también era la primera versión principal del motor de juegos para el envío de compatibilidad con la versión preliminar de OpenXR 1,0.  Ahora, en el **motor inreal 4,26**, la compatibilidad con HoloLens 2, Windows Mixed Reality y otros auriculares de escritorio VR estarán disponibles a través [del complemento OpenXR integrado del motor](https://github.com/microsoft/Microsoft-OpenXR-Unreal).  No real Engine 4,26 también se incluirá con su primer conjunto de complementos de [extensión de OpenXR](#roadmap), lo que permite la interacción con la mano y la compatibilidad con el controlador de HP reverberación G2.  Inreal Engine 4,26 está disponible en versión preliminar hoy mismo en el [iniciador de juegos de Epic](https://www.unrealengine.com/download/creators), con la versión oficial que llegará después este año.  También estará disponible MRTK-Unreal compatibilidad con OpenXR junto con esa versión.


### <a name="openxr-for-native-development"></a>OpenXR para el desarrollo nativo

Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

Para empezar a desarrollar aplicaciones de OpenXR para los auriculares de la realidad de HoloLens 2 o Windows, consulte [Cómo empezar a usar OpenXR Development](openxr-getting-started.md).

Para ver un paseo por todos los componentes principales de la API de OpenXR, junto con ejemplos de las aplicaciones reales que usan OpenXR hoy, consulte este vídeo del tutorial de 60 minutos:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Consulte también

* <a href="https://www.khronos.org/openxr/" target="_blank">Más información sobre OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificación de OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referencia de la API de OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida de OpenXR 1,0</a>