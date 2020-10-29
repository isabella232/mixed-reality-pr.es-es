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
# <a name="openxr-performance"></a><span data-ttu-id="36ec4-104">Rendimiento de OpenXR</span><span class="sxs-lookup"><span data-stu-id="36ec4-104">OpenXR performance</span></span>

<span data-ttu-id="36ec4-105">En HoloLens 2, hay varias formas de enviar datos de composición a través de los cuales se producirá un `xrEndFrame` procesamiento posterior que tendrá una penalización notable en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="36ec4-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="36ec4-106">Para evitar penalizaciones de rendimiento, [envíe un `XrCompositionProjectionLayer` solo](openxr-best-practices.md#use-a-single-projection-layer) con las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="36ec4-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="36ec4-107">Usar una matriz de textura intercambio</span><span class="sxs-lookup"><span data-stu-id="36ec4-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="36ec4-108">Usar el formato intercambio de color principal</span><span class="sxs-lookup"><span data-stu-id="36ec4-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="36ec4-109">Usar las dimensiones de vista recomendadas</span><span class="sxs-lookup"><span data-stu-id="36ec4-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="36ec4-110">No establecer la `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` marca</span><span class="sxs-lookup"><span data-stu-id="36ec4-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="36ec4-111">Establezca `XrCompositionLayerDepthInfoKHR` `minDepth` en 0.0 f y `maxDepth` en 1,0 f.</span><span class="sxs-lookup"><span data-stu-id="36ec4-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="36ec4-112">Otras consideraciones darán lugar a un mejor rendimiento:</span><span class="sxs-lookup"><span data-stu-id="36ec4-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="36ec4-113">Usar el formato de profundidad de 16 bits</span><span class="sxs-lookup"><span data-stu-id="36ec4-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="36ec4-114">Realizar llamadas a Draw con instancias</span><span class="sxs-lookup"><span data-stu-id="36ec4-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
