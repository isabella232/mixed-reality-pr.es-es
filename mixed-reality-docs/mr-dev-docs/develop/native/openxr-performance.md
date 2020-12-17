---
title: Rendimiento de OpenXR
description: Depure el rendimiento de la GPU de las aplicaciones de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, rendimiento, optimización, depuración de GPU, RenderDoc, PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613179"
---
# <a name="openxr-performance"></a><span data-ttu-id="d1a29-104">Rendimiento de OpenXR</span><span class="sxs-lookup"><span data-stu-id="d1a29-104">OpenXR performance</span></span>

<span data-ttu-id="d1a29-105">En HoloLens 2, hay varias formas de enviar datos de composición a través de `xrEndFrame` , lo que puede dar lugar a un procesamiento posterior y a penalizaciones de rendimiento perceptibles.</span><span class="sxs-lookup"><span data-stu-id="d1a29-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>
<span data-ttu-id="d1a29-106">Para evitar un rendimiento deficiente, [envíe una `XrCompositionProjectionLayer` única](openxr-best-practices.md#use-a-single-projection-layer) con las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="d1a29-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="d1a29-107">Usar una matriz de textura intercambio</span><span class="sxs-lookup"><span data-stu-id="d1a29-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="d1a29-108">Usar el formato intercambio de color principal</span><span class="sxs-lookup"><span data-stu-id="d1a29-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="d1a29-109">Usar las dimensiones de vista recomendadas</span><span class="sxs-lookup"><span data-stu-id="d1a29-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="d1a29-110">No establezca la `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` marca</span><span class="sxs-lookup"><span data-stu-id="d1a29-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="d1a29-111">Establezca `XrCompositionLayerDepthInfoKHR` `minDepth` en 0.0 f y `maxDepth` en 1,0 f.</span><span class="sxs-lookup"><span data-stu-id="d1a29-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="d1a29-112">Para mejorar el rendimiento, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d1a29-112">For better performance, consider:</span></span>
* [<span data-ttu-id="d1a29-113">Usar el formato de profundidad de 16 bits</span><span class="sxs-lookup"><span data-stu-id="d1a29-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="d1a29-114">Realización de llamadas a Draw con instancias</span><span class="sxs-lookup"><span data-stu-id="d1a29-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
