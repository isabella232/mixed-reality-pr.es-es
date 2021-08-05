---
title: Rendimiento de OpenXR
description: Obtenga información sobre cómo depurar el rendimiento de GPU de las aplicaciones de realidad mixta de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, aplicación nativa, nativa, motor personalizado, middleware, rendimiento, optimización, depuración de GPU, RenderDoc, MIDDLEWARE
ms.openlocfilehash: f4462da954a3b6093e47f03e75b460671e7638f406b761ad6e05689ab97b3ddc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213181"
---
# <a name="openxr-performance"></a>Rendimiento de OpenXR

En HoloLens 2, hay varias maneras de enviar datos de composición a través de , lo que puede dar lugar a un procesamiento posterior y a una notable disminución `xrEndFrame` del rendimiento.

Para evitar un rendimiento deficiente, [envíe un único con `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) las siguientes características:

* [Uso de una cadena de intercambio de matriz de texturas](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usar el formato de cadena de intercambio de color principal](openxr-best-practices.md#select-a-swapchain-format)
* [Uso de las dimensiones de vista recomendadas](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* No establecer la `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` marca
* Establezca en `XrCompositionLayerDepthInfoKHR` `minDepth` 0,0f y `maxDepth` en 1,0f.

Para mejorar el rendimiento, tenga en cuenta lo siguiente:

* [Uso del formato de profundidad de 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Realización de llamadas a draw con instancias](openxr-best-practices.md#render-with-texture-array-and-vprt)
