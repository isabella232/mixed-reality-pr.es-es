---
title: Rendimiento de OpenXR
description: Depure el rendimiento de la GPU de las aplicaciones de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, rendimiento, optimización, depuración de GPU, RenderDoc, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691475"
---
# <a name="openxr-performance"></a>Rendimiento de OpenXR

En HoloLens 2, hay varias formas de enviar datos de composición a través de los cuales se producirá un `xrEndFrame` procesamiento posterior que tendrá una penalización notable en el rendimiento.
Para evitar penalizaciones de rendimiento, [envíe un `XrCompositionProjectionLayer` solo](openxr-best-practices.md#use-a-single-projection-layer) con las siguientes características:
* [Usar una matriz de textura intercambio](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usar el formato intercambio de color principal](openxr-best-practices.md#select-a-swapchain-format)
* [Usar las dimensiones de vista recomendadas](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* No establecer la `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` marca
* Establezca `XrCompositionLayerDepthInfoKHR` `minDepth` en 0.0 f y `maxDepth` en 1,0 f.

Otras consideraciones darán lugar a un mejor rendimiento:
* [Usar el formato de profundidad de 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Realizar llamadas a Draw con instancias](openxr-best-practices.md#render-with-texture-array-and-vprt)
