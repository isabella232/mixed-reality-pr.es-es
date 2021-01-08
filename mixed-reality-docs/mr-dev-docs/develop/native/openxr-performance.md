---
title: Rendimiento de OpenXR
description: Obtenga información sobre cómo depurar el rendimiento de la GPU de las aplicaciones de OpenXR Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, rendimiento, optimización, depuración de GPU, RenderDoc, PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006765"
---
# <a name="openxr-performance"></a>Rendimiento de OpenXR

En HoloLens 2, hay varias formas de enviar datos de composición a través de `xrEndFrame` , lo que puede dar lugar a un procesamiento posterior y a penalizaciones de rendimiento perceptibles.

Para evitar un rendimiento deficiente, [envíe una `XrCompositionProjectionLayer` única](openxr-best-practices.md#use-a-single-projection-layer) con las siguientes características:

* [Usar una matriz de textura intercambio](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usar el formato intercambio de color principal](openxr-best-practices.md#select-a-swapchain-format)
* [Usar las dimensiones de vista recomendadas](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* No establezca la `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` marca
* Establezca `XrCompositionLayerDepthInfoKHR` `minDepth` en 0.0 f y `maxDepth` en 1,0 f.

Para mejorar el rendimiento, tenga en cuenta lo siguiente:

* [Usar el formato de profundidad de 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Realización de llamadas a Draw con instancias](openxr-best-practices.md#render-with-texture-array-and-vprt)
