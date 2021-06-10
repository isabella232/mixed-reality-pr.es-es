---
title: Uso de WebXR con Windows Mixed Reality
description: Conozca los conceptos básicos del uso y el desarrollo de aplicaciones WebXR que se ejecutan Windows Mixed Reality cascos envolventes.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 video, 360 videos, 360 photo, 360 photos, 360 content, immersive web, immersiveweb, IW
ms.openlocfilehash: fa4d11fac59e25f43d9d55de16d3b0c35e8166b7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600114"
---
# <a name="webxr-overview"></a><span data-ttu-id="511cb-104">Introducción a WebXR</span><span class="sxs-lookup"><span data-stu-id="511cb-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="511cb-105">Qué es WebXR</span><span class="sxs-lookup"><span data-stu-id="511cb-105">What is WebXR</span></span>

<span data-ttu-id="511cb-106">[**WebXR Device API**](https://www.w3.org/TR/webxr/) sirve para acceder a dispositivos de realidad virtual **(VR)** y realidad aumentada **(AR),** incluidos sensores y pantallas montadas en la cabeza en **la web.**  </span><span class="sxs-lookup"><span data-stu-id="511cb-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="511cb-107">La API de dispositivo WebXR está disponible actualmente en Microsoft Edge y Chrome versión 79 y versiones posteriores admite WebXR de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="511cb-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="511cb-108">Puede comprobar el estado de compatibilidad del explorador más reciente para WebXR en [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="511cb-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="511cb-109">Visualización de WebXR</span><span class="sxs-lookup"><span data-stu-id="511cb-109">Viewing WebXR</span></span>

<span data-ttu-id="511cb-110">Puede ver las experiencias de WebXR en Windows Mixed Reality y los nuevos [Microsoft Edge](../../whats-new/new-microsoft-edge.md) [y Firefox Reality.](https://mixedreality.mozilla.org/firefox-reality/)</span><span class="sxs-lookup"><span data-stu-id="511cb-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](../../whats-new/new-microsoft-edge.md) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="511cb-111">Para probar si el explorador admite WebXR, puede ir a [Ejemplos de WebXR](https://immersive-web.github.io/webxr-samples/) en el explorador.</span><span class="sxs-lookup"><span data-stu-id="511cb-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="511cb-112">Consulte también</span><span class="sxs-lookup"><span data-stu-id="511cb-112">See Also</span></span>

* [<span data-ttu-id="511cb-113">Uso Babylon.js para crear experiencias de WebXR</span><span class="sxs-lookup"><span data-stu-id="511cb-113">Using Babylon.js to create WebXR experiences</span></span>](./tutorials/babylonjs-webxr-helloworld/introduction-01.md)
* [<span data-ttu-id="511cb-114">Especificación de Api de dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="511cb-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="511cb-115">Documentación de WebXR Device API</span><span class="sxs-lookup"><span data-stu-id="511cb-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="511cb-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="511cb-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="511cb-117">Ejemplos de WebXR</span><span class="sxs-lookup"><span data-stu-id="511cb-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="511cb-118">Windows Mixed Reality y la nueva Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="511cb-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](../../whats-new/new-microsoft-edge.md)
* [<span data-ttu-id="511cb-119">Github de W3C web inmersivo</span><span class="sxs-lookup"><span data-stu-id="511cb-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="511cb-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="511cb-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="511cb-121">[Extensiones de Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) [y Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="511cb-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="511cb-122">Control del contexto perdido en WebGL</span><span class="sxs-lookup"><span data-stu-id="511cb-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="511cb-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="511cb-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="511cb-124">glTF</span><span class="sxs-lookup"><span data-stu-id="511cb-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="511cb-125">Grupo de comunidad web envolvente</span><span class="sxs-lookup"><span data-stu-id="511cb-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)