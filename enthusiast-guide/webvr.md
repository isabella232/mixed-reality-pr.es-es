---
title: Uso de WebVR con Windows Mixed Reality
description: Describe WebVR y cómo usarlo con Microsoft Edge en auriculares Windows Mixed Reality.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, WebVR, Edge, Microsoft Edge, exploración Web
ms.openlocfilehash: 92f1d00c7f635c88a727732fb743996a654ba775
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725606"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="5177b-104">Uso de WebVR con Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5177b-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT]
><span data-ttu-id="5177b-105">La mayoría de los exploradores Web modernos tienen compatibilidad en desuso de WebVR en favor de WebXR, el nuevo estándar para crear experiencias Web envolventes para auriculares VR.</span><span class="sxs-lookup"><span data-stu-id="5177b-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="5177b-106">Instale [el nuevo Microsoft Edge para la](using-microsoft-edge.md) compatibilidad con WebXR.</span><span class="sxs-lookup"><span data-stu-id="5177b-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="5177b-107">Qué es WebVR</span><span class="sxs-lookup"><span data-stu-id="5177b-107">What is WebVR</span></span>

<span data-ttu-id="5177b-108">[WebVR](https://webvr.info) es una especificación abierta que le permite experimentar el funcionamiento de VR desde un explorador.</span><span class="sxs-lookup"><span data-stu-id="5177b-108">[WebVR](https://webvr.info) is an open specification that lets you experience VR right from a browser.</span></span> <span data-ttu-id="5177b-109">Si un sitio web implementa la compatibilidad con WebVR y proporciona contenido 3D, puede mostrar el contenido envolvente del casco con el consentimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="5177b-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="5177b-110">¿Cuál es la diferencia entre WebVR y explorar la web en VR?</span><span class="sxs-lookup"><span data-stu-id="5177b-110">What is the difference between WebVR and browsing the web in VR</span></span>

<span data-ttu-id="5177b-111">WebVR es una tecnología que permite al autor de un sitio web agregar la funcionalidad de VR a una página.</span><span class="sxs-lookup"><span data-stu-id="5177b-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="5177b-112">La API de WebVR se usa en una página para mostrar contenido 3D (por ejemplo, un vídeo de 360 grados, un modelo 3D o un juego 3D) para todo el casco.</span><span class="sxs-lookup"><span data-stu-id="5177b-112">The WebVR API is used by a page to display 3D content (such as 360-degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="5177b-113">**Ejemplo:** Visualización de un vídeo de 360 en [CNN.com/VR](http://cnn.com/vr).</span><span class="sxs-lookup"><span data-stu-id="5177b-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="5177b-114">Si una página admite WebVR, agregará un botón u otro elemento de la interfaz de usuario que puede seleccionar para especificar VR.</span><span class="sxs-lookup"><span data-stu-id="5177b-114">If a page supports WebVR, it will add a button or other UI element that you can select to enter VR.</span></span>

<span data-ttu-id="5177b-115">Explorar la web en VR significa usar el explorador Edge mientras usa el casco, como una pizarra de aplicación 2D dentro de Cliffhouse.</span><span class="sxs-lookup"><span data-stu-id="5177b-115">Browsing the web in VR means using the Edge browser while you're wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="5177b-116">Hacer que todos los sitios web admitan WebVR</span><span class="sxs-lookup"><span data-stu-id="5177b-116">Do all websites support WebVR</span></span>

<span data-ttu-id="5177b-117">No.</span><span class="sxs-lookup"><span data-stu-id="5177b-117">No.</span></span> <span data-ttu-id="5177b-118">Los autores de sitios web deben participar en el uso de WebVR y pueden crear sitios optimizados para exploradores, auriculares y controladores específicos.</span><span class="sxs-lookup"><span data-stu-id="5177b-118">Website authors must opt in to use WebVR and they may create optimized sites for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="5177b-119">Algunos contenidos de WebVR están optimizados solo para dispositivos móviles de VR.</span><span class="sxs-lookup"><span data-stu-id="5177b-119">Some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="5177b-120">Además, tenga en cuenta que los sitios web deben crear y proporcionar contenido de WebVR de forma explícita.</span><span class="sxs-lookup"><span data-stu-id="5177b-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="5177b-121">El número de sitios que tienen algún contenido compatible con WebVR está creciendo cada día.</span><span class="sxs-lookup"><span data-stu-id="5177b-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="5177b-122">¿Puedo usar mi Naopak/Oculus, etc., para ver el contenido de WebVR en Microsoft Edge?</span><span class="sxs-lookup"><span data-stu-id="5177b-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge</span></span>

<span data-ttu-id="5177b-123">No.</span><span class="sxs-lookup"><span data-stu-id="5177b-123">No.</span></span> <span data-ttu-id="5177b-124">Se requiere un casco de Windows Mixed Reality para usar WebVR en Edge.</span><span class="sxs-lookup"><span data-stu-id="5177b-124">A Windows Mixed Reality headset is required to use WebVR in Edge.</span></span> <span data-ttu-id="5177b-125">Sin embargo, puede tener acceso al contenido de WebVR en otro explorador. Consulte la lista completa de dispositivos y exploradores compatibles en: [WebVR. Rocks](http://webvr.rocks/).</span><span class="sxs-lookup"><span data-stu-id="5177b-125">However, you can access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="5177b-126">¿Dónde puedo encontrar la documentación para desarrolladores de WebVR</span><span class="sxs-lookup"><span data-stu-id="5177b-126">Where can I find the WebVR developer documentation</span></span>

<span data-ttu-id="5177b-127">La documentación para desarrolladores se encuentra aquí: [documentación para desarrolladores de WebVR](https://docs.microsoft.com/microsoft-edge/webvr/).</span><span class="sxs-lookup"><span data-stu-id="5177b-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="5177b-128">He encontrado un sitio web con WebVR que no funciona en Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5177b-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="5177b-129">¿Qué hago?</span><span class="sxs-lookup"><span data-stu-id="5177b-129">What do I do</span></span>

<span data-ttu-id="5177b-130">Puede notificar sitios rotos directamente al equipo del explorador Microsoft Edge en el [rastreador de problemas](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)o a través de twitter con [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span><span class="sxs-lookup"><span data-stu-id="5177b-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="5177b-131">También puede registrar errores mediante la aplicación centro de comentarios de Windows en categoría:</span><span class="sxs-lookup"><span data-stu-id="5177b-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="5177b-132">Problemas con el sitio web de Microsoft Edge-></span><span class="sxs-lookup"><span data-stu-id="5177b-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="5177b-133">¿Qué es una buena página para probar si WebVR está funcionando?</span><span class="sxs-lookup"><span data-stu-id="5177b-133">What is a good page to test if WebVR is working</span></span>

<span data-ttu-id="5177b-134">Vea los [ejemplos de webvr.info](http://webvr.info/samples/XX-vr-controllers.html).</span><span class="sxs-lookup"><span data-stu-id="5177b-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="5177b-135">Cómo configurar WebVR</span><span class="sxs-lookup"><span data-stu-id="5177b-135">How do I set up WebVR</span></span>

<span data-ttu-id="5177b-136">Para experimentar el contenido de WebVR en un casco de realidad mixta de Windows (con hardware o simulación), debe:</span><span class="sxs-lookup"><span data-stu-id="5177b-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation), you must:</span></span>

1. <span data-ttu-id="5177b-137">Asegúrese de que el casco está conectado.</span><span class="sxs-lookup"><span data-stu-id="5177b-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="5177b-138">Inicie Microsoft Edge, ya sea en el escritorio o en una realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5177b-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="5177b-139">Navegue a una página habilitada para WebVR.</span><span class="sxs-lookup"><span data-stu-id="5177b-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="5177b-140">Seleccione el botón escribir VR dentro de la página (la ubicación y la representación visual de este botón pueden variar en función del sitio web).</span><span class="sxs-lookup"><span data-stu-id="5177b-140">Select the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="5177b-141">Puede tener un aspecto similar a: </span><span class="sxs-lookup"><span data-stu-id="5177b-141">It may look similar to:</span></span>\
   ![Imagen de la VR](images/75px-enter-vr.png)
5. <span data-ttu-id="5177b-143">La primera vez que intente especificar VR en un dominio específico, el explorador solicitará consentimiento para usar la vista envolvente, seleccione Sí:</span><span class="sxs-lookup"><span data-stu-id="5177b-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, select yes:</span></span> ![Interfaz de usuario de consentimiento que se muestra en el primer intento de especificar VR en un dominio determinado](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="5177b-145">Los auriculares deben empezar a mostrar el contenido de WebVR.</span><span class="sxs-lookup"><span data-stu-id="5177b-145">Your headset should begin displaying the WebVR content.</span></span>

## <a name="see-also"></a><span data-ttu-id="5177b-146">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5177b-146">See also</span></span>

* [<span data-ttu-id="5177b-147">Solución de problemas de > WebVR</span><span class="sxs-lookup"><span data-stu-id="5177b-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="5177b-148">Cómo llegar a su primera experiencia de WebVR</span><span class="sxs-lookup"><span data-stu-id="5177b-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="5177b-149">Uso de juegos y aplicaciones en Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5177b-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="5177b-150">Su página principal de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5177b-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="5177b-151">Sistema de seguimiento</span><span class="sxs-lookup"><span data-stu-id="5177b-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="5177b-152">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="5177b-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="5177b-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="5177b-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="5177b-154">Enviar comentarios</span><span class="sxs-lookup"><span data-stu-id="5177b-154">Filing feedback</span></span>](filing-feedback.md)
