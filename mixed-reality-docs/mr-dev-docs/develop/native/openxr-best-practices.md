---
title: Procedimientos recomendados de OpenXR
description: Conozca los procedimientos recomendados para la calidad visual, la estabilidad y el rendimiento de las aplicaciones OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, aplicación nativa, nativa, motor personalizado, middleware, procedimientos recomendados, rendimiento, calidad, estabilidad
ms.openlocfilehash: 2cbd05417f62f7380b048f692295bbbe98ceba5bce69c4f1dae21aec812ec450
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207853"
---
# <a name="openxr-app-best-practices"></a>Procedimientos recomendados de la aplicación OpenXR

Puede ver un ejemplo de los procedimientos recomendados siguientes en el archivo OpenXRProgram.cpp de <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp.</a> La función Run() al principio captura un flujo de código de aplicación OpenXR típico desde la inicialización hasta el bucle de representación y eventos.

## <a name="best-practices-for-visual-quality-and-stability"></a>Procedimientos recomendados para la calidad visual y la estabilidad

Los procedimientos recomendados de esta sección describen cómo obtener la mejor calidad visual y estabilidad en cualquier aplicación OpenXR.

Para obtener más recomendaciones de rendimiento específicas de HoloLens 2, consulte la sección Procedimientos recomendados para el [HoloLens 2](#best-practices-for-performance-on-hololens-2) a continuación.

### <a name="gamma-correct-rendering"></a>Representación gamma correcta

Debe tener cuidado para asegurarse de que la canalización de representación es gamma correcta. Al representar en una cadena de intercambio, el formato de vista render-target debe coincidir con el formato de cadena de intercambio. Por ejemplo, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` para el formato de cadena de intercambio y la vista render-target.
Hay una excepción si la canalización de representación de la aplicación realiza una conversión manual de sRGB en el código del sombreador. La aplicación debe solicitar un formato de cadena de intercambio sRGB, pero usar el formato lineal para la vista render-target. Por ejemplo, solicite como formato de cadena de intercambio, pero use como vista render-target para evitar que se corrija el `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` `DXGI_FORMAT_B8G8R8A8_UNORM` contenido de doble gamma.

### <a name="submit-depth-buffer-for-projection-layers"></a>Enviar búfer de profundidad para capas de proyección

Use siempre `XR_KHR_composition_layer_depth` la extensión y envíe el búfer de profundidad junto con la capa de proyección al enviar un fotograma a `xrEndFrame` .
Habilitar la reproducción de profundidad de hardware HoloLens 2 mejora la estabilidad del holograma.

### <a name="choose-a-reasonable-depth-range"></a>Elección de un intervalo de profundidad razonable

Prefiere un intervalo de profundidad más reducido para limitar el ámbito del contenido virtual para ayudar a la estabilidad del holograma en HoloLens.
Por ejemplo, el ejemplo OpenXrProgram.cpp usa de 0,1 metros a 20 metros.
Use [reversed-Z para](https://developer.nvidia.com/content/depth-precision-visualized) una resolución de profundidad más uniforme.
En HoloLens 2, el uso del formato de profundidad preferido le ayudará a mejorar la velocidad de fotogramas y el rendimiento, aunque los búferes de profundidad de 16 bits proporcionan menos resolución de profundidad que los búferes de profundidad de `DXGI_FORMAT_D16_UNORM` 24 bits.
Seguir estos procedimientos recomendados para hacer un mejor uso de la resolución de profundidad es más importante.

### <a name="prepare-for-different-environment-blend-modes"></a>Preparación para distintos modos de combinación de entorno

Si la aplicación también se ejecutará en cascos envolventes que bloquean completamente el mundo, asegúrese de enumerar los modos de mezcla de entorno compatibles mediante la API y prepare el contenido de representación `xrEnumerateEnvironmentBlendModes` correctamente.
Por ejemplo, para un sistema con como el HoloLens, la aplicación debe usar transparente como color claro, mientras que para un sistema con , la aplicación debe representar algún color opaco o alguna sala virtual en segundo `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` plano.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Elección del espacio de referencia sin enlazar como espacio raíz de la aplicación

Las aplicaciones suelen establecer un espacio de coordenadas del mundo raíz para conectar vistas, acciones y hologramas.
Use cuando se admite la extensión para establecer un sistema de coordenadas a escala mundial, lo que permite a la aplicación evitar el desvío de hologramas no deseados cuando el usuario se mueve lejos `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` (por ejemplo, a 5 metros de distancia) desde donde se inicia la aplicación. [](../../design/coordinate-systems.md#building-a-world-scale-experience)
Use como reserva si la extensión de espacio sin `XR_REFERENCE_SPACE_TYPE_LOCAL` enlazar no existe.

### <a name="associate-hologram-with-spatial-anchor"></a>Asociación de hologramas con delimitador espacial

Cuando se usa un espacio de referencia sin enlazar, los hologramas que se coloquen directamente en ese espacio de referencia pueden desplazarse a medida que el usuario se desplaza a salas lejanas y, a continuación, [vuelve](../../design/coordinate-systems.md#building-a-world-scale-experience)a .
Para que los usuarios del holograma coloquen en una ubicación discreta del [mundo,](../../design/spatial-anchors.md#best-practices) cree un delimitador espacial mediante la función de extensión y coloque el `xrCreateSpatialAnchorSpaceMSFT` holograma en su origen. Esto mantendrá ese holograma independientemente estable con el tiempo.

### <a name="support-mixed-reality-capture"></a>Compatibilidad con la captura de realidad mixta

Aunque la pantalla principal de HoloLens 2 usa la combinación de entornos aditivos, cuando el usuario inicia la captura de realidad [mixta,](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)el contenido de representación de la aplicación se combinará alfa con la secuencia de vídeo del entorno.
Para lograr la mejor calidad visual en los vídeos de captura de realidad mixta, es mejor establecer en la capa `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` de `layerFlags` proyección.

## <a name="best-practices-for-performance-on-hololens-2"></a>Procedimientos recomendados para el rendimiento en HoloLens 2

Como dispositivo móvil con compatibilidad con la reproducción de hardware, HoloLens 2 requisitos más estrictos para obtener un rendimiento óptimo.  Hay varias maneras de enviar datos de composición, lo que da como resultado un procesamiento posterior con una disminución notable del rendimiento.

### <a name="select-a-swapchain-format"></a>Selección de un formato de cadena de intercambio

Enumere siempre los formatos de píxel admitidos mediante y elija el primer formato de píxel de color y profundidad del tiempo de ejecución que admite la aplicación, porque eso es lo que prefiere el tiempo de ejecución para obtener un `xrEnumerateSwapchainFormats` rendimiento óptimo. Tenga en cuenta que HoloLens 2 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` y suele ser la primera opción para lograr un mejor rendimiento de la `DXGI_FORMAT_D16_UNORM` representación. Esta preferencia puede ser diferente en los cascos vr que se ejecutan en un equipo de escritorio, donde los búferes de profundidad de 24 bits tienen menos impacto en el rendimiento.
  
**Advertencia de rendimiento:** El uso de un formato distinto del formato de color de cadena de intercambio principal dará lugar al procesamiento posterior del tiempo de ejecución, lo que produce una reducción significativa del rendimiento.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Representación con parámetros de representación recomendados y tiempo de fotogramas

Represente siempre con el ancho y alto recomendados de la configuración de la vista ( y desde ) y use siempre la API para consultar la posición de vista `recommendedImageRectWidth` `recommendedImageRectHeight` `XrViewConfigurationView` recomendada, fov y otros parámetros de representación antes de la `xrLocateViews` representación.
Use siempre de `XrFrameEndInfo.predictedDisplayTime` la llamada más reciente al consultar las poses y las `xrWaitFrame` vistas.
Esto permite HoloLens la representación y optimizar la calidad visual de la persona que lleva el HoloLens.

### <a name="use-a-single-projection-layer"></a>Uso de una sola capa de proyección

HoloLens 2 capacidad de GPU limitada para representar contenido y un compositor de hardware optimizado para una sola capa de proyección.
El uso siempre de una sola capa de proyección puede ayudar a la velocidad de fotogramas, la estabilidad del holograma y la calidad visual de la aplicación.  
  
**Advertencia de rendimiento:** El envío de cualquier cosa menos una sola capa de protección dará lugar al procesamiento posterior del tiempo de ejecución, lo que produce una reducción significativa del rendimiento.

### <a name="render-with-texture-array-and-vprt"></a>Representación con matriz de texturas y VPRT

Cree uno para los ojos izquierdo y derecho mediante para la cadena de intercambio de colores y otro `xrSwapchain` `arraySize=2` para la profundidad.
Represente el ojo izquierdo en el segmento 0 y el ojo derecho en el segmento 1.
Use un sombreador con VPRT y llamadas de dibujo con instancias para la representación estereomática para minimizar la carga de GPU.
Esto también permite que la optimización del entorno de ejecución alcance el mejor rendimiento en HoloLens 2.
Las alternativas al uso de una matriz de texturas, como la representación de doble ancho o una cadena de intercambio independiente por ojo, darán lugar al procesamiento posterior en tiempo de ejecución, lo que produce una reducción significativa del rendimiento.

### <a name="avoid-quad-layers"></a>Evitar las capas de cuatro niveles

En lugar de enviar capas de cuatro capas como capas de composición con `XrCompositionLayerQuad` , represente el contenido de cuatro elementos directamente en la cadena de intercambio de proyección.

**Advertencia de rendimiento:** Si se proporcionan capas adicionales más allá de una sola capa de proyección, como las de cuatro capas, se provocará un procesamiento posterior en tiempo de ejecución, lo que conlleva una reducción significativa del rendimiento.