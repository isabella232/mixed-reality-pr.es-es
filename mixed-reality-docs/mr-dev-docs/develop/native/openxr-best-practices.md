---
title: Procedimientos recomendados de OpenXR
description: Conozca los procedimientos recomendados para la calidad, la estabilidad y el rendimiento visual de las aplicaciones de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, procedimientos recomendados, rendimiento, calidad, estabilidad
ms.openlocfilehash: ee600cfc22ab1fb7ee43c5727d8e19cf3a1b1463
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612989"
---
# <a name="openxr-app-best-practices"></a>Prácticas recomendadas de aplicaciones de OpenXR

Puede ver un ejemplo de los procedimientos recomendados que se indican a continuación en el archivo OpenXRProgram. cpp de <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>. La función Run () al principio captura un flujo de código de la aplicación OpenXR típico desde la inicialización hasta el bucle de representación y evento.

## <a name="best-practices-for-visual-quality-and-stability"></a>Prácticas recomendadas para la calidad y estabilidad visual

En los procedimientos recomendados de esta sección se describe cómo obtener la mejor calidad y estabilidad visual de cualquier aplicación de OpenXR.

Para obtener más recomendaciones sobre el rendimiento específicas de HoloLens 2, consulte la sección [procedimientos recomendados para el rendimiento en hololens 2](#best-practices-for-performance-on-hololens-2) a continuación.

### <a name="gamma-correct-rendering"></a>Representación gamma-correcta

Se debe tener cuidado para asegurarse de que la canalización de representación sea correcta. Al representar en un intercambio, el formato de vista de destino de representación debe coincidir con el formato de intercambio. Por ejemplo, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` para el formato intercambio y la vista representación-destino.
Existe una excepción si la canalización de representación de la aplicación realiza una conversión sRGB manual en el código del sombreador. La aplicación debe solicitar un formato sRGB intercambio, pero usar el formato lineal para la vista Render-Target. Por ejemplo, solicite `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` como el formato intercambio, pero use `DXGI_FORMAT_B8G8R8A8_UNORM` como vista de destino de representación para evitar que el contenido se corrija con doble gamma.

### <a name="submit-depth-buffer-for-projection-layers"></a>Enviar búfer de profundidad para capas de proyección

Use siempre `XR_KHR_composition_layer_depth` Extension y envíe el búfer de profundidad junto con la capa de proyección al enviar un fotograma a `xrEndFrame` .
La habilitación de la reproyección de profundidad de hardware en HoloLens 2 mejora la estabilidad del holograma.

### <a name="choose-a-reasonable-depth-range"></a>Elegir un intervalo de profundidad razonable

Prefiera un intervalo de profundidad más estrecho para definir el ámbito del contenido virtual para ayudar a la estabilidad del holograma en HoloLens.
Por ejemplo, el ejemplo OpenXrProgram. cpp usa 0,1 metros en 20 metros.
Use [invertida-Z](https://developer.nvidia.com/content/depth-precision-visualized) para una resolución de profundidad más uniforme.
En HoloLens 2, el uso del `DXGI_FORMAT_D16_UNORM` formato de profundidad preferido le ayudará a lograr una mayor velocidad de fotogramas y rendimiento, aunque los búferes de profundidad de 16 bits proporcionan una resolución menos profunda que los búferes de profundidad de 24 bits.
Seguir estas prácticas recomendadas para hacer el mejor uso de la resolución de profundidad es más importante.

### <a name="prepare-for-different-environment-blend-modes"></a>Preparación para diferentes modos de fusión de entornos

Si la aplicación también se va a ejecutar en auriculares envolventes que bloqueen completamente el mundo, asegúrese de enumerar los modos de Blend de entorno admitidos con `xrEnumerateEnvironmentBlendModes` la API y preparar el contenido de representación correctamente.
Por ejemplo, para un sistema con, `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` como HoloLens, la aplicación debe usar transparente como color sin cifrar, mientras que en el caso de un sistema con `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` , la aplicación debe representar algún color opaco o alguna sala virtual en segundo plano.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Elegir espacio de referencia sin enlazar como espacio de la raíz de la aplicación

Normalmente, las aplicaciones establecen algún espacio de coordenadas del mundo raíz para conectar las vistas, las acciones y los hologramas juntos.
Use `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` cuando se admita la extensión para establecer un [sistema de coordenadas de escala mundial](../../design/coordinate-systems.md#building-a-world-scale-experience), lo que permite a la aplicación evitar el desplazamiento de hologramas no deseado cuando el usuario se desplaza lejos (por ejemplo, 5 metros de distancia) desde donde se inicia la aplicación.
Use `XR_REFERENCE_SPACE_TYPE_LOCAL` como reserva si la extensión de espacio sin enlazar no existe.

### <a name="associate-hologram-with-spatial-anchor"></a>Asociar holograma con delimitador espacial

Cuando se usa un espacio de referencia sin enlazar, los hologramas colocados directamente en ese espacio de referencia pueden desplazarse [a medida que el usuario dirige a habitaciones lejanas y, a continuación,](../../design/coordinate-systems.md#building-a-world-scale-experience)vuelve.
En el caso de los usuarios de hologramas colocan en una ubicación discreta del mundo, [crean un delimitador espacial](../../design/spatial-anchors.md#best-practices) con la `xrCreateSpatialAnchorSpaceMSFT` función de extensión y colocan el holograma en su origen. De este modo, el holograma será estable de manera independiente con el tiempo.

### <a name="support-mixed-reality-capture"></a>Compatibilidad con la captura de realidad mixta

Aunque la pantalla principal de HoloLens 2 usa la combinación de entornos aditivos, cuando el usuario inicia una [captura de realidad mixta](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md), el contenido de representación de la aplicación se combinará alfa con el flujo de vídeo del entorno.
Para lograr la mejor calidad visual en vídeos de captura de realidad mixta, es mejor establecer en la de la `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` capa de proyección `layerFlags` .

## <a name="best-practices-for-performance-on-hololens-2"></a>Prácticas recomendadas para el rendimiento en HoloLens 2

Como dispositivo móvil con compatibilidad con la reproyección de hardware, HoloLens 2 tiene requisitos más estrictos para un rendimiento óptimo.  Hay varias maneras de enviar datos de composición a través de, lo que produce un procesamiento posterior con una penalización de rendimiento notable.

### <a name="select-a-swapchain-format"></a>Seleccionar un formato de intercambio

Enumere siempre los formatos de píxel admitidos mediante `xrEnumerateSwapchainFormats` y elija el primer formato de píxeles de color y profundidad del tiempo de ejecución que admita la aplicación, ya que es lo que el tiempo de ejecución prefiere para un rendimiento óptimo. Tenga en cuenta que, en HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` y `DXGI_FORMAT_D16_UNORM` suele ser la primera opción para lograr un mejor rendimiento de la representación. Esta preferencia puede ser diferente en los auriculares de VR que se ejecutan en un equipo de escritorio, donde los búferes de profundidad de 24 bits tienen menos impacto en el rendimiento.
  
**Advertencia de rendimiento:** El uso de un formato distinto del formato de color intercambio principal dará como resultado un procesamiento posterior en tiempo de ejecución, lo que supone una penalización significativa del rendimiento.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Representar con los parámetros de representación recomendados y los intervalos de fotogramas

Siempre se representa con el ancho y alto de la configuración de vista recomendada ( `recommendedImageRectWidth` y `recommendedImageRectHeight` desde `XrViewConfigurationView` ) y use siempre la `xrLocateViews` API para consultar la representación de vista recomendada, el subproceso y otros parámetros de representación antes de la representación.
Use siempre el `XrFrameEndInfo.predictedDisplayTime` de la llamada más reciente `xrWaitFrame` al consultar las vistas y las vistas.
Esto permite a HoloLens ajustar la representación y optimizar la calidad visual de la persona que posee HoloLens.

### <a name="use-a-single-projection-layer"></a>Usar una sola capa de proyección

HoloLens 2 tiene una potencia de GPU limitada para la representación de contenido y un compositor de hardware optimizado para una sola capa de proyección.
El uso de una sola capa de proyección puede ayudar a la velocidad de fotogramas de la aplicación, la estabilidad del holograma y la calidad visual.  
  
**Advertencia de rendimiento:** El envío de cualquier elemento, pero con un nivel de protección único, dará lugar a un procesamiento posterior en tiempo de ejecución, lo que supone una penalización significativa del rendimiento.

### <a name="render-with-texture-array-and-vprt"></a>Representar con la matriz de textura y VPRT

Cree uno `xrSwapchain` para el ojo izquierdo y derecho con el `arraySize=2` fin de intercambio de color y otro para la profundidad.
Representar el ojo izquierdo en el segmento 0 y el ojo derecho en el segmento 1.
Use un sombreador con VPRT y llamadas de dibujo con instancias para la representación de Stereoscopic a fin de minimizar la carga de la GPU.
Esto también permite la optimización del tiempo de ejecución para lograr el mejor rendimiento en HoloLens 2.
Las alternativas al uso de una matriz de textura, como la representación de doble ancho o una intercambio independiente por ojo, darán lugar a un procesamiento posterior en tiempo de ejecución, lo que supone una penalización significativa del rendimiento.

### <a name="avoid-quad-layers"></a>Evite las cuatro capas

En lugar de enviar cuatro capas como capas de composición con `XrCompositionLayerQuad` , represente el contenido cuádruple directamente en la proyección intercambio.

**Advertencia de rendimiento:** Proporcionar capas adicionales más allá de una sola capa de proyección, como las capas cuádruples, dará como resultado un procesamiento posterior en tiempo de ejecución, lo que supone una penalización significativa del rendimiento.