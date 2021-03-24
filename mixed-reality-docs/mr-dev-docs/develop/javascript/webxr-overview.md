---
title: Uso de WebXR con Windows Mixed Reality
description: Conozca los aspectos básicos del uso y desarrollo de aplicaciones de WebXR que se ejecutan en auriculares Windows Mixed Reality.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, ar website, 360, 360 video, 360 videos, 360 Photo, 360 photos, 360 Content, Web inmersivo, immersiveweb, IW
ms.openlocfilehash: 99cf5cf151c41252e43c6051c0d6281d33fe695a
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909132"
---
# <a name="webxr-overview"></a><span data-ttu-id="44435-104">Información general de WebXR</span><span class="sxs-lookup"><span data-stu-id="44435-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="44435-105">Qué es WebXR</span><span class="sxs-lookup"><span data-stu-id="44435-105">What is WebXR</span></span>

<span data-ttu-id="44435-106">La **API de dispositivo WebXR** es para tener acceso a dispositivos de **realidad virtual (VR)** y de **realidad aumentada (ar)** , incluidos los **sensores** y las **pantallas montadas** por el cabezal en la **Web**.</span><span class="sxs-lookup"><span data-stu-id="44435-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="44435-107">WebXR API de dispositivo está disponible actualmente en Microsoft Edge y Chrome versión 79 y versiones posteriores admite WebXR como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="44435-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="44435-108">Puede comprobar el estado de compatibilidad más reciente del explorador para WebXR en [Caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="44435-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="44435-109">Obtenga más información sobre [Windows Mixed Reality y la nueva Microsoft Edge en la](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)sección [novedades](/windows/mixed-reality/mrtk-porting-guide) .</span><span class="sxs-lookup"><span data-stu-id="44435-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="44435-110">Ver WebXR</span><span class="sxs-lookup"><span data-stu-id="44435-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44435-111">Microsoft Edge (heredado) solo admite WebVR, una API desusada que no está disponible en los exploradores actuales.</span><span class="sxs-lookup"><span data-stu-id="44435-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="44435-112">Sin embargo, el nuevo **[Explorador Edge basado en cromo](../../whats-new/new-microsoft-edge.md)** es compatible con WebXR y está disponible para el prototipo de VR en Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="44435-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="44435-113">WebVR no estará disponible en el nuevo explorador Edge basado en cromo.</span><span class="sxs-lookup"><span data-stu-id="44435-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="44435-114">Si está buscando una forma de prototipo de WebXR en HoloLens 2 en la actualidad, consulte la [realidad de Firefox](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="44435-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="44435-115">Para probar si el explorador admite WebXR, puede ir a los [ejemplos de WebXR](https://immersive-web.github.io/webxr-samples/) en el explorador.</span><span class="sxs-lookup"><span data-stu-id="44435-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="44435-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="44435-116">See Also</span></span>

* [<span data-ttu-id="44435-117">Especificación de la API de dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="44435-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="44435-118">Documentación de la API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="44435-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="44435-119">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="44435-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="44435-120">Ejemplos de WebXR</span><span class="sxs-lookup"><span data-stu-id="44435-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="44435-121">Windows Mixed Reality y el nuevo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="44435-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="44435-122">GitHub Web de W3C envolvente</span><span class="sxs-lookup"><span data-stu-id="44435-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="44435-123">[API de WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="44435-123">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="44435-124">[API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) y [extensiones de controlador](https://w3c.github.io/gamepad/extensions.html) para juegos</span><span class="sxs-lookup"><span data-stu-id="44435-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="44435-125">Controlar el contexto perdido en WebGL</span><span class="sxs-lookup"><span data-stu-id="44435-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="44435-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="44435-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="44435-127">glTF</span><span class="sxs-lookup"><span data-stu-id="44435-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="44435-128">Uso de Babylon.js para crear experiencias de WebXR</span><span class="sxs-lookup"><span data-stu-id="44435-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="44435-129">Grupo de la comunidad web envolvente</span><span class="sxs-lookup"><span data-stu-id="44435-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)