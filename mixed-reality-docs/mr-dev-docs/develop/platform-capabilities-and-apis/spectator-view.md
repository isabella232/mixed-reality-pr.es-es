---
title: Vista del espectador
description: Visualice los hologramas de un dispositivo externo para mostrar o grabar una experiencia de realidad mixta en una pantalla externa.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Vista del espectador, iPhone, iOS, iPad, OpenCV, cámara, ARKit, HoloLens, realidad mixta, MixedRealityToolkit, demo, grabar
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530107"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="e1634-104">Vista del espectador para HoloLens y HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e1634-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marcador](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="e1634-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="e1634-106">Overview</span></span>

<span data-ttu-id="e1634-107">Cuando tiene un dispositivo HoloLens, es fácil olvidarse de que aquellos que no tienen ninguno no pueden ver las mismas maravillas de las que está disfrutando.</span><span class="sxs-lookup"><span data-stu-id="e1634-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="e1634-108">Gracias a la vista de espectador, otros usuarios pueden ver lo que ve un usuario de HoloLens en una pantalla 2D.</span><span class="sxs-lookup"><span data-stu-id="e1634-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="e1634-109">También es un enfoque rápido y asequible para grabar hologramas en HD con dispositivos móviles y obtener grabaciones de los hologramas de gran calidad con cámaras de vídeo.</span><span class="sxs-lookup"><span data-stu-id="e1634-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="e1634-110">Recursos clave</span><span class="sxs-lookup"><span data-stu-id="e1634-110">Key Resources</span></span>

* [<span data-ttu-id="e1634-111">**Vista del espectador en GitHub**</span><span class="sxs-lookup"><span data-stu-id="e1634-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="e1634-112">**Documentación de la vista del espectador**</span><span class="sxs-lookup"><span data-stu-id="e1634-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="e1634-113">**Ejemplos de la vista del espectador**</span><span class="sxs-lookup"><span data-stu-id="e1634-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="e1634-114">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="e1634-114">Use Cases</span></span>

* <span data-ttu-id="e1634-115">Puedes grabar una experiencia de realidad mixta mediante un dispositivo iPhone o Android.</span><span class="sxs-lookup"><span data-stu-id="e1634-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="e1634-116">Grabe en Full HD y aplique el suavizado de contornos y un sombreado a los hologramas para conseguir una forma rentable y rápida de grabar vídeos de los mismos.</span><span class="sxs-lookup"><span data-stu-id="e1634-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="e1634-117">Haz streaming de experiencias de realidad mixta en directo a Apple TV directamente desde tu iPhone o iPad y sin retrasos.</span><span class="sxs-lookup"><span data-stu-id="e1634-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="e1634-118">Comparte la experiencia con los invitados: permite que los usuarios sin HoloLens experimenten los hologramas directamente desde sus teléfonos o tabletas.</span><span class="sxs-lookup"><span data-stu-id="e1634-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="e1634-119">Características actuales</span><span class="sxs-lookup"><span data-stu-id="e1634-119">Current Features</span></span>

* <span data-ttu-id="e1634-120">Sincronización espacial de los hologramas, para que todos los usuarios vean los hologramas exactamente en el mismo lugar.</span><span class="sxs-lookup"><span data-stu-id="e1634-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="e1634-121">Compatibilidad con iOS (dispositivos habilitados para ARKit) y Android (dispositivos habilitados para ARCore).</span><span class="sxs-lookup"><span data-stu-id="e1634-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="e1634-122">Varios invitados de iOS.</span><span class="sxs-lookup"><span data-stu-id="e1634-122">Multiple iOS guests.</span></span>
<span data-ttu-id="e1634-123">Grabación de vídeo + hologramas + sonido de ambiente + sonido del holograma.</span><span class="sxs-lookup"><span data-stu-id="e1634-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="e1634-124">Hoja compartida para que puedas guardar un vídeo, enviarlo por correo electrónico o compartirlo con otras aplicaciones compatibles.</span><span class="sxs-lookup"><span data-stu-id="e1634-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="e1634-125">![Marcador](images/SpecViewPhoneDemo.jpg)
![Marcador](images/hololensspectatorview-500px.jpg) ![Marcador](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="e1634-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="e1634-126">En la tabla siguiente se muestran varias funcionalidades de la vista de espectador y sus características.</span><span class="sxs-lookup"><span data-stu-id="e1634-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="e1634-127">Elige la opción que mejor se adapte a tus necesidades de grabación de vídeo:</span><span class="sxs-lookup"><span data-stu-id="e1634-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="e1634-128">Funcionalidad</span><span class="sxs-lookup"><span data-stu-id="e1634-128">Functionality</span></span>                                | <span data-ttu-id="e1634-129">Móvil</span><span class="sxs-lookup"><span data-stu-id="e1634-129">Mobile</span></span>                  |                    <span data-ttu-id="e1634-130">Cámara de vídeo</span><span class="sxs-lookup"><span data-stu-id="e1634-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="e1634-131">Calidad HD</span><span class="sxs-lookup"><span data-stu-id="e1634-131">HD quality</span></span>                           |         <span data-ttu-id="e1634-132">Full HD</span><span class="sxs-lookup"><span data-stu-id="e1634-132">Full HD</span></span>         |        <span data-ttu-id="e1634-133">Filmación de calidad profesional (determinada por la cámara de vídeo)</span><span class="sxs-lookup"><span data-stu-id="e1634-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="e1634-134">Movimiento de la cámara simplificado</span><span class="sxs-lookup"><span data-stu-id="e1634-134">Easy camera movement</span></span>                 |            <span data-ttu-id="e1634-135">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-135">✔</span></span>            |                      <span data-ttu-id="e1634-136">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-136">✔</span></span>                      |
| <span data-ttu-id="e1634-137">Vista en tercera persona</span><span class="sxs-lookup"><span data-stu-id="e1634-137">Third-person view</span></span>                    |            <span data-ttu-id="e1634-138">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-138">✔</span></span>            |                      <span data-ttu-id="e1634-139">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-139">✔</span></span>                      |
| <span data-ttu-id="e1634-140">Se puede hacer streaming a pantallas</span><span class="sxs-lookup"><span data-stu-id="e1634-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="e1634-141">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-141">✔</span></span>            |                      <span data-ttu-id="e1634-142">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-142">✔</span></span>                      |
| <span data-ttu-id="e1634-143">Portátil</span><span class="sxs-lookup"><span data-stu-id="e1634-143">Portable</span></span>                             |            <span data-ttu-id="e1634-144">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-144">✔</span></span>            |                                             |
| <span data-ttu-id="e1634-145">Inalámbrico</span><span class="sxs-lookup"><span data-stu-id="e1634-145">Wireless</span></span>                             |            <span data-ttu-id="e1634-146">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-146">✔</span></span>            |                                             |
| <span data-ttu-id="e1634-147">Hardware adicional necesario</span><span class="sxs-lookup"><span data-stu-id="e1634-147">Additional required hardware</span></span>         |     <span data-ttu-id="e1634-148">Teléfono Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="e1634-148">Android phone, iPhone</span></span>    | <span data-ttu-id="e1634-149">HoloLens + plataforma + trípode + cámara de vídeo + equipo + Unity</span><span class="sxs-lookup"><span data-stu-id="e1634-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="e1634-150">Inversión en hardware</span><span class="sxs-lookup"><span data-stu-id="e1634-150">Hardware investment</span></span>                  |           <span data-ttu-id="e1634-151">Bajo</span><span class="sxs-lookup"><span data-stu-id="e1634-151">Low</span></span>            |                     <span data-ttu-id="e1634-152">Alto</span><span class="sxs-lookup"><span data-stu-id="e1634-152">High</span></span>                    |
| <span data-ttu-id="e1634-153">Multiplataforma</span><span class="sxs-lookup"><span data-stu-id="e1634-153">Cross-platform</span></span>                       |           <span data-ttu-id="e1634-154">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="e1634-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="e1634-155">Contenido sincronizado</span><span class="sxs-lookup"><span data-stu-id="e1634-155">Synchronized content</span></span>                 |            <span data-ttu-id="e1634-156">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-156">✔</span></span>            |                      <span data-ttu-id="e1634-157">✔</span><span class="sxs-lookup"><span data-stu-id="e1634-157">✔</span></span>                      |
| <span data-ttu-id="e1634-158">Duración de la instalación en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="e1634-158">Runtime setup duration</span></span>               |         <span data-ttu-id="e1634-159">Instantánea</span><span class="sxs-lookup"><span data-stu-id="e1634-159">Instant</span></span>          |                     <span data-ttu-id="e1634-160">Lenta</span><span class="sxs-lookup"><span data-stu-id="e1634-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="e1634-161">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e1634-161">See also</span></span>

* [<span data-ttu-id="e1634-162">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="e1634-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="e1634-163">Captura de realidad mixta para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="e1634-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="e1634-164">Experiencias compartidas en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="e1634-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
