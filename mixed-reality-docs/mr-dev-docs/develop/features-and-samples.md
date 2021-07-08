---
title: Aplicaciones de ejemplo y características
description: Manténgase al día con todos los ejemplos de Microsoft disponibles y las aplicaciones de características de realidad mixta para HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, learn, ejemplos, MRTK, modo de investigación, HoloLens 2, códigos qr, WebRTC, captura de realidad mixta, control remoto de holografías, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906901"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="c9e24-104">Aplicaciones de ejemplo y características</span><span class="sxs-lookup"><span data-stu-id="c9e24-104">Samples and feature apps</span></span>

![Imagen de un usuario con HoloLens manipulando un holograma con movimiento de mano](unreal/images/unreal-developer.jpg)

<span data-ttu-id="c9e24-106">Cada recorrido de desarrollo comienza con un vistazo a lo que otros desarrolladores han compilado correctamente. En el caso de la realidad mixta, no es diferente.</span><span class="sxs-lookup"><span data-stu-id="c9e24-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="c9e24-107">Actualmente, todos nuestros tutoriales y aplicaciones de ejemplo se basan en Unity o Unreal.</span><span class="sxs-lookup"><span data-stu-id="c9e24-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="c9e24-108">A medida que desarrollamos contenido para otros motores y plataformas, los encontrará en el encabezado correspondiente de la tabla de contenido.</span><span class="sxs-lookup"><span data-stu-id="c9e24-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="c9e24-109">Aplicaciones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="c9e24-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="c9e24-110">Ejemplos de características</span><span class="sxs-lookup"><span data-stu-id="c9e24-110">Feature samples</span></span>

<span data-ttu-id="c9e24-111">Los ejemplos de características que se enumeran a continuación corresponden a implementaciones específicas que se tratan en nuestra documentación y abarcan una variedad de plataformas de desarrollo y dispositivos de hardware.</span><span class="sxs-lookup"><span data-stu-id="c9e24-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="c9e24-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c9e24-112">OpenXR</span></span>

<span data-ttu-id="c9e24-113">Para los desarrolladores que usan Unity 2020 para compilar aplicaciones para HoloLens 2 o Mixed Reality, se puede usar el complemento de OpenXR en lugar del complemento de WindowsXR para mejorar las compatibilidades multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="c9e24-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="c9e24-114">Mixed Reality OpenXR Plugin también funciona bien con la versión Mixed Reality Toolkit 2.7 más reciente.</span><span class="sxs-lookup"><span data-stu-id="c9e24-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="c9e24-115">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="c9e24-115">Reference article</span></span> | <span data-ttu-id="c9e24-116">Muestra</span><span class="sxs-lookup"><span data-stu-id="c9e24-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="c9e24-117">Uso del complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="c9e24-117">Using the OpenXR plugin</span></span>](./unity/xr-project-setup.md) | [<span data-ttu-id="c9e24-118">Mixed Reality OpenXR con ejemplos de Unity</span><span class="sxs-lookup"><span data-stu-id="c9e24-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="c9e24-119">N/D</span><span class="sxs-lookup"><span data-stu-id="c9e24-119">N/A</span></span> | [<span data-ttu-id="c9e24-120">Proyecto OpenXR MRTK Base de Unity</span><span class="sxs-lookup"><span data-stu-id="c9e24-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="c9e24-121">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="c9e24-121">Research Mode</span></span>

<span data-ttu-id="c9e24-122">El modo de investigación se presentó en la primera generación de HoloLens para dar acceso a los sensores de claves en el dispositivo, específicamente para las aplicaciones de investigación que no están pensadas para la implementación.</span><span class="sxs-lookup"><span data-stu-id="c9e24-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="c9e24-123">Las aplicaciones de ejemplo siguientes son ejemplos de acceso y grabación de secuencias de modo de investigación y el uso de los atributos [intrinsics y extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="c9e24-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="c9e24-124">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="c9e24-124">Reference article</span></span> | <span data-ttu-id="c9e24-125">Aplicación de ejemplo</span><span class="sxs-lookup"><span data-stu-id="c9e24-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="c9e24-126">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="c9e24-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="c9e24-127">HoloLens (1ª generación)</span><span class="sxs-lookup"><span data-stu-id="c9e24-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="c9e24-128">Modo de investigación</span><span class="sxs-lookup"><span data-stu-id="c9e24-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="c9e24-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c9e24-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="c9e24-130">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="c9e24-130">QR codes</span></span>

<span data-ttu-id="c9e24-131">HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código.</span><span class="sxs-lookup"><span data-stu-id="c9e24-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="c9e24-132">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="c9e24-132">Reference article</span></span> | <span data-ttu-id="c9e24-133">Muestra</span><span class="sxs-lookup"><span data-stu-id="c9e24-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="c9e24-134">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="c9e24-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="c9e24-135">Seguimiento de códigos QR en Unity</span><span class="sxs-lookup"><span data-stu-id="c9e24-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="c9e24-136">Descripción de escenas</span><span class="sxs-lookup"><span data-stu-id="c9e24-136">Scene understanding</span></span>

<span data-ttu-id="c9e24-137">La descripción de escenas aporta a los desarrolladores de realidad mixta una representación estructurada y general del entorno, diseñada para que el desarrollo para aplicaciones con control del entorno sea intuitivo.</span><span class="sxs-lookup"><span data-stu-id="c9e24-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="c9e24-138">Para ello, la descripción de escenas combina la potencia de los entornos en tiempo de ejecución de realidad mixta existentes, como la asignación espacial altamente precisa, pero menos estructurada, y los nuevos entornos en tiempo de ejecución controlados por IA.</span><span class="sxs-lookup"><span data-stu-id="c9e24-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="c9e24-139">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="c9e24-139">Reference article</span></span> | <span data-ttu-id="c9e24-140">Muestra</span><span class="sxs-lookup"><span data-stu-id="c9e24-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="c9e24-141">Descripción de escenas</span><span class="sxs-lookup"><span data-stu-id="c9e24-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="c9e24-142">Ejemplos de descripción de escenas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c9e24-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="c9e24-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="c9e24-143">WebRTC</span></span>

<span data-ttu-id="c9e24-144">El proyecto MixedReality-WebRTC es una colección de componentes que ayudan a los desarrolladores de aplicaciones de realidad mixta a integrar la comunicación punto a punto en tiempo real de audio, vídeo y datos en los componentes de WebRTC de sus aplicaciones. Se basa en el protocolo de WebRTC para la comunicación en tiempo real (RTC), que es compatible con la mayoría de los exploradores web modernos.</span><span class="sxs-lookup"><span data-stu-id="c9e24-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="c9e24-145">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="c9e24-145">Reference article</span></span> | <span data-ttu-id="c9e24-146">Muestra</span><span class="sxs-lookup"><span data-stu-id="c9e24-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="c9e24-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="c9e24-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="c9e24-148">Aplicaciones de ejemplo de Unreal</span><span class="sxs-lookup"><span data-stu-id="c9e24-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="c9e24-149">Captura holográfica de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c9e24-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="c9e24-150">Captura de realidad mixta (MRC) captura la experiencia en primera persona de combinar mundos reales y digitales como una foto o un vídeo, compartiendo lo que se ve con otros usuarios en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="c9e24-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="c9e24-151">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="c9e24-151">Reference article</span></span> | <span data-ttu-id="c9e24-152">Muestra</span><span class="sxs-lookup"><span data-stu-id="c9e24-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="c9e24-153">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c9e24-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="c9e24-154">Ejemplos de Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c9e24-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="c9e24-155">Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="c9e24-155">Holographic Remoting</span></span>

<span data-ttu-id="c9e24-156">Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de PC que admiten el control remoto de holografías.</span><span class="sxs-lookup"><span data-stu-id="c9e24-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="c9e24-157">El control remoto de holografías transmite contenido holográfico desde un PC a su Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi y es compatible con HoloLens (1.ª generación) y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c9e24-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="c9e24-158">Artículo de referencia</span><span class="sxs-lookup"><span data-stu-id="c9e24-158">Reference article</span></span> | <span data-ttu-id="c9e24-159">Muestra</span><span class="sxs-lookup"><span data-stu-id="c9e24-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="c9e24-160">Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="c9e24-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="c9e24-161">Ejemplos de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="c9e24-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |