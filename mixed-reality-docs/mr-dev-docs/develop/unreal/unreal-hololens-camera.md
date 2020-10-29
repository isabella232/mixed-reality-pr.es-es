---
title: Cámara de foto y vídeo HoloLens en Unreal
description: Guía para usar la cámara de foto y vídeo HoloLens en Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, PV camera, MRC
ms.openlocfilehash: e66583d46d64361621303e36a5fbcc209300f5d8
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699270"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="38a7a-104">Cámara de foto y vídeo HoloLens en Unreal</span><span class="sxs-lookup"><span data-stu-id="38a7a-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="38a7a-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="38a7a-105">Overview</span></span>

<span data-ttu-id="38a7a-106">HoloLens tiene una cámara de foto y vídeo (PV) que se usa para la Captura de realidad mixta (MRC) y que una aplicación puede usar para acceder a los objetos visuales del mundo real.</span><span class="sxs-lookup"><span data-stu-id="38a7a-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="38a7a-107">Representación de la cámara PV para MRC</span><span class="sxs-lookup"><span data-stu-id="38a7a-107">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="38a7a-108">Se requiere **Unreal Engine 4.25** o versión posterior.</span><span class="sxs-lookup"><span data-stu-id="38a7a-108">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="38a7a-109">El sistema y las grabadoras de MRC personalizadas crean capturas de realidad mixta mediante la combinación de la cámara PV con hologramas representados por la aplicación inmersiva.</span><span class="sxs-lookup"><span data-stu-id="38a7a-109">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="38a7a-110">De forma predeterminada, la captura de realidad mixta usa la salida holográfica del ojo derecho.</span><span class="sxs-lookup"><span data-stu-id="38a7a-110">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="38a7a-111">Si una aplicación inmersiva elige la [representación de la cámara PV](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), se usará en su lugar.</span><span class="sxs-lookup"><span data-stu-id="38a7a-111">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="38a7a-112">Esto mejora el mapeo entre el mundo real y los hologramas en el vídeo de MRC.</span><span class="sxs-lookup"><span data-stu-id="38a7a-112">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="38a7a-113">Para participar en la representación de la cámara PV:</span><span class="sxs-lookup"><span data-stu-id="38a7a-113">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="38a7a-114">Llame a **SetEnabledMixedRealityCamera** y **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="38a7a-114">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="38a7a-115">Use los valores **Tamaño X** y **Tamaño Y** para establecer las dimensiones del vídeo.</span><span class="sxs-lookup"><span data-stu-id="38a7a-115">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Tercera cámara](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="38a7a-117">Unreal controlará las solicitudes de MRC para representarlas desde la perspectiva de la cámara PV.</span><span class="sxs-lookup"><span data-stu-id="38a7a-117">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="38a7a-118">Solo cuando se desencadena la [Captura de realidad mixta](../../mixed-reality-capture.md), se pedirá a la aplicación que represente desde la perspectiva de la cámara de foto y vídeo.</span><span class="sxs-lookup"><span data-stu-id="38a7a-118">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="38a7a-119">Uso de la cámara PV</span><span class="sxs-lookup"><span data-stu-id="38a7a-119">Using the PV Camera</span></span>

<span data-ttu-id="38a7a-120">La textura de la cámara web se puede recuperar en el juego en tiempo de ejecución, pero debe habilitarse en la opción del editor **Editar > Configuración del proyecto** :</span><span class="sxs-lookup"><span data-stu-id="38a7a-120">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings** :</span></span>
1. <span data-ttu-id="38a7a-121">Vaya a **Plataformas > HoloLens > Capacidades** y marca **Cámara Web** .</span><span class="sxs-lookup"><span data-stu-id="38a7a-121">Go to **Platforms > HoloLens > Capabilities** and check **Webcam** .</span></span>
    * <span data-ttu-id="38a7a-122">Use la función **StartCameraCapture** para usar la cámara web en tiempo de ejecución y la función **StopCameraCapture** para detener la grabación.</span><span class="sxs-lookup"><span data-stu-id="38a7a-122">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Inicio y detención de la cámara](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="38a7a-124">Representación de una imagen</span><span class="sxs-lookup"><span data-stu-id="38a7a-124">Rendering an image</span></span>
<span data-ttu-id="38a7a-125">Para representar la imagen de la cámara:</span><span class="sxs-lookup"><span data-stu-id="38a7a-125">To render the camera image:</span></span>
1. <span data-ttu-id="38a7a-126">Cree una instancia de material dinámico basada en un material del proyecto, que se denomine **PVCamMat** en la siguiente captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="38a7a-126">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="38a7a-127">Establezca la instancia de material dinámico en una variable de **referencia de objeto dinámico de instancia de material** .</span><span class="sxs-lookup"><span data-stu-id="38a7a-127">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="38a7a-128">Establezca el material del objeto en la escena que representará la fuente de la cámara para esta nueva instancia de material dinámico.</span><span class="sxs-lookup"><span data-stu-id="38a7a-128">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="38a7a-129">Inicie un temporizador que se usará para enlazar la imagen de la cámara al material.</span><span class="sxs-lookup"><span data-stu-id="38a7a-129">Start a timer that will be used to bind the camera image to the material.</span></span>

![Representación de la cámara](images/unreal-camera-render.PNG)

4. <span data-ttu-id="38a7a-131">Cree una nueva función para este temporizador, en este caso **MaterialTimer** , y llame a **GetARCameraImage** para obtener la textura de la cámara web.</span><span class="sxs-lookup"><span data-stu-id="38a7a-131">Create a new function for this timer, in this case **MaterialTimer** , and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="38a7a-132">Si esta textura es válida, defina un parámetro de textura en el sombreador para esta imagen.</span><span class="sxs-lookup"><span data-stu-id="38a7a-132">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="38a7a-133">De lo contrario, vuelve a iniciar el temporizador de materiales.</span><span class="sxs-lookup"><span data-stu-id="38a7a-133">Otherwise, start the material timer again.</span></span>

![Textura de cámara desde la cámara web](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="38a7a-135">Asegúrese de que el material tiene un parámetro que coincide con el nombre de **SetTextureParameterValue** que está enlazado a una entrada de color.</span><span class="sxs-lookup"><span data-stu-id="38a7a-135">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="38a7a-136">Sin esto, la imagen de la cámara no puede mostrarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="38a7a-136">Without this, the camera image can't be properly displayed.</span></span>

![Textura de cámara](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="38a7a-138">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="38a7a-138">Next Development Checkpoint</span></span>

<span data-ttu-id="38a7a-139">Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="38a7a-139">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="38a7a-140">Desde aquí, puede continuar con el tema siguiente:</span><span class="sxs-lookup"><span data-stu-id="38a7a-140">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="38a7a-141">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="38a7a-141">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="38a7a-142">O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:</span><span class="sxs-lookup"><span data-stu-id="38a7a-142">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="38a7a-143">Implementación en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="38a7a-143">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="38a7a-144">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="38a7a-144">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="38a7a-145">Consulta también</span><span class="sxs-lookup"><span data-stu-id="38a7a-145">See also</span></span>
* [<span data-ttu-id="38a7a-146">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="38a7a-146">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="38a7a-147">Captura de realidad mixta para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="38a7a-147">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
