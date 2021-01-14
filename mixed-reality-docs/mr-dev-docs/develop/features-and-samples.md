---
title: Aplicaciones de ejemplo y características
description: Manténgase al día con todos los ejemplos de Microsoft disponibles y las aplicaciones de características de realidad mixta para HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, learn, ejemplos, MRTK, modo de investigación, HoloLens 2, códigos qr, WebRTC, captura de realidad mixta, control remoto de holografías, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 3aa0e51a92b909689ff97a07b45900ab65579c59
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007615"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="87e2d-104">Aplicaciones de ejemplo y características</span><span class="sxs-lookup"><span data-stu-id="87e2d-104">Samples and feature apps</span></span>

![Imagen de un usuario con HoloLens manipulando un holograma con movimiento de mano](unreal/images/unreal-developer.jpg)

<span data-ttu-id="87e2d-106">Cada recorrido de desarrollo comienza con un vistazo a lo que otros desarrolladores han compilado correctamente. En el caso de la realidad mixta, no es diferente.</span><span class="sxs-lookup"><span data-stu-id="87e2d-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="87e2d-107">Actualmente, todos nuestros tutoriales y aplicaciones de ejemplo se basan en Unity o Unreal.</span><span class="sxs-lookup"><span data-stu-id="87e2d-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="87e2d-108">A medida que desarrollamos contenido para otros motores y plataformas, los encontrará en el encabezado correspondiente de la tabla de contenido.</span><span class="sxs-lookup"><span data-stu-id="87e2d-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="87e2d-109">Aplicaciones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="87e2d-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="87e2d-110">Ejemplos de características</span><span class="sxs-lookup"><span data-stu-id="87e2d-110">Feature samples</span></span>

<span data-ttu-id="87e2d-111">Los ejemplos de características que se enumeran a continuación corresponden a implementaciones específicas que se tratan en nuestra documentación y abarcan una variedad de plataformas de desarrollo y dispositivos de hardware.</span><span class="sxs-lookup"><span data-stu-id="87e2d-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="87e2d-112">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="87e2d-112">Research Mode</span></span>

<span data-ttu-id="87e2d-113">El modo de investigación se presentó en la primera generación de HoloLens para dar acceso a los sensores de claves en el dispositivo, específicamente para las aplicaciones de investigación que no están pensadas para la implementación.</span><span class="sxs-lookup"><span data-stu-id="87e2d-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="87e2d-114">Las aplicaciones de ejemplo siguientes son ejemplos de acceso y grabación de secuencias de modo de investigación y el uso de los atributos [intrinsics y extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="87e2d-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="87e2d-115">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="87e2d-115">Reference article</span></span> | <span data-ttu-id="87e2d-116">Aplicación de ejemplo</span><span class="sxs-lookup"><span data-stu-id="87e2d-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="87e2d-117">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="87e2d-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="87e2d-118">HoloLens (1ª generación)</span><span class="sxs-lookup"><span data-stu-id="87e2d-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="87e2d-119">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="87e2d-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="87e2d-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="87e2d-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="87e2d-121">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="87e2d-121">QR codes</span></span>

<span data-ttu-id="87e2d-122">HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código.</span><span class="sxs-lookup"><span data-stu-id="87e2d-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="87e2d-123">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="87e2d-123">Reference article</span></span> | <span data-ttu-id="87e2d-124">Muestra</span><span class="sxs-lookup"><span data-stu-id="87e2d-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="87e2d-125">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="87e2d-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="87e2d-126">Seguimiento de códigos QR en Unity</span><span class="sxs-lookup"><span data-stu-id="87e2d-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="87e2d-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="87e2d-127">WebRTC</span></span>

<span data-ttu-id="87e2d-128">El proyecto MixedReality-WebRTC es una colección de componentes que ayudan a los desarrolladores de aplicaciones de realidad mixta a integrar la comunicación punto a punto en tiempo real de audio, vídeo y datos en los componentes de WebRTC de sus aplicaciones. Se basa en el protocolo de WebRTC para la comunicación en tiempo real (RTC), que es compatible con la mayoría de los exploradores web modernos.</span><span class="sxs-lookup"><span data-stu-id="87e2d-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="87e2d-129">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="87e2d-129">Reference article</span></span> | <span data-ttu-id="87e2d-130">Muestra</span><span class="sxs-lookup"><span data-stu-id="87e2d-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="87e2d-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="87e2d-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="87e2d-132">Aplicaciones de ejemplo de Unreal</span><span class="sxs-lookup"><span data-stu-id="87e2d-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="87e2d-133">Captura holográfica de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="87e2d-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="87e2d-134">Captura de realidad mixta (MRC) captura la experiencia en primera persona de combinar mundos reales y digitales como una foto o un vídeo, compartiendo lo que se ve con otros usuarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="87e2d-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="87e2d-135">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="87e2d-135">Reference article</span></span> | <span data-ttu-id="87e2d-136">Muestra</span><span class="sxs-lookup"><span data-stu-id="87e2d-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="87e2d-137">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="87e2d-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="87e2d-138">Ejemplos de Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="87e2d-138">Mixed Reality Capture samples</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="87e2d-139">Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="87e2d-139">Holographic Remoting</span></span>

<span data-ttu-id="87e2d-140">Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de PC que admiten el control remoto de holografías.</span><span class="sxs-lookup"><span data-stu-id="87e2d-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="87e2d-141">El control remoto de holografías transmite contenido holográfico desde un PC a su Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi y es compatible con HoloLens (1.ª generación) y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="87e2d-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="87e2d-142">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="87e2d-142">Reference article</span></span> | <span data-ttu-id="87e2d-143">Muestra</span><span class="sxs-lookup"><span data-stu-id="87e2d-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="87e2d-144">Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="87e2d-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="87e2d-145">Ejemplos de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="87e2d-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |