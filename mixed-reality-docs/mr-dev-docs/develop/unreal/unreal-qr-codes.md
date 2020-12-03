---
title: Códigos QR en Unreal
description: Guía para el uso de códigos QR en Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: f2f06e9aa8d458d58dc8551ab6cd726622c30d4c
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354430"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="20f85-104">Códigos QR en Unreal</span><span class="sxs-lookup"><span data-stu-id="20f85-104">QR codes in Unreal</span></span>

<span data-ttu-id="20f85-105">HoloLens 2 puede ver los códigos QR en el espacio del mundo real a través de la cámara web, que los representa como hologramas empleando un sistema de coordenadas en la posición del mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="20f85-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="20f85-106">Además de los códigos QR únicos, HoloLens 2 también puede representar hologramas en la misma ubicación en varios dispositivos para crear una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="20f85-106">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="20f85-107">Asegúrese de seguir estos procedimientos recomendados para agregar códigos QR a las aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="20f85-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="20f85-108">Zonas tranquilas</span><span class="sxs-lookup"><span data-stu-id="20f85-108">Quiet zones</span></span>
- <span data-ttu-id="20f85-109">Iluminación y fondo</span><span class="sxs-lookup"><span data-stu-id="20f85-109">Lighting and backdrop</span></span>
- <span data-ttu-id="20f85-110">Tamaño, distancia y posición angular</span><span class="sxs-lookup"><span data-stu-id="20f85-110">Size, distance, and angular position</span></span>

<span data-ttu-id="20f85-111">Preste especial atención a las [consideraciones del ambiente](../../environment-considerations-for-hololens.md) al colocar códigos QR en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="20f85-111">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="20f85-112">Puede encontrar más información sobre cada uno de estos temas e instrucciones sobre cómo descargar el paquete de NuGet necesario en el documento principal de [seguimiento de código QR](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="20f85-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="20f85-113">Los códigos QR son el único tipo de imágenes de las que HoloLens puede realizar un seguimiento de forma predefinida. El módulo **UARTrackedImage** de Unreal no se admite en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="20f85-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="20f85-114">Si necesita realizar un seguimiento de las imágenes personalizadas, puede acceder a la [cámara web](unreal-hololens-camera.md) del dispositivo y procesar imágenes mediante una biblioteca de reconocimiento de imágenes de terceros.</span><span class="sxs-lookup"><span data-stu-id="20f85-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="20f85-115">Habilitación de la detección de QR</span><span class="sxs-lookup"><span data-stu-id="20f85-115">Enabling QR detection</span></span>
<span data-ttu-id="20f85-116">Como HoloLens 2 necesita usar la cámara web para ver los códigos QR, deberá habilitarla en la configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="20f85-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="20f85-117">Abra **Editar > Configuración del proyecto**, desplácese hasta la sección **Plataformas** y pulse en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="20f85-117">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="20f85-118">Expanda la sección **Funcionalidades** y marque **Cámara web**.</span><span class="sxs-lookup"><span data-stu-id="20f85-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="20f85-119">También deberá participar en el seguimiento del código QR mediante la [adición de un activo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="20f85-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="20f85-120">Configuración de un código QR con seguimiento</span><span class="sxs-lookup"><span data-stu-id="20f85-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="20f85-121">Los códigos QR aparecen en el sistema de geometría con seguimiento de AR de Unreal como una imagen con seguimiento.</span><span class="sxs-lookup"><span data-stu-id="20f85-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="20f85-122">Para que esto funcione, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="20f85-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="20f85-123">Cree un plano técnico de actor y agregue el componente **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="20f85-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![Notificación de seguimiento de AR de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="20f85-125">Seleccione **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**:</span><span class="sxs-lookup"><span data-stu-id="20f85-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![Eventos con QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="20f85-127">Haga clic en **+** junto a **On Add Tracked Geometry** (Al agregar geometría con seguimiento) para agregar el nodo al gráfico de eventos.</span><span class="sxs-lookup"><span data-stu-id="20f85-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="20f85-128">Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="20f85-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Adición de un nodo al evento On Add Tracked Geometry (Al agregar geometría con seguimiento)](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="20f85-130">Uso de un código QR con seguimiento</span><span class="sxs-lookup"><span data-stu-id="20f85-130">Using a tracked QR code</span></span>
<span data-ttu-id="20f85-131">El gráfico de eventos de la siguiente imagen muestra el evento **OnUpdateTrackedImage** que se usa para representar un punto en el centro de un código QR e imprimir sus datos.</span><span class="sxs-lookup"><span data-stu-id="20f85-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![Ejemplo de representación de QR](images/unreal-qr-render.PNG)

<span data-ttu-id="20f85-133">Esto es lo que sucede:</span><span class="sxs-lookup"><span data-stu-id="20f85-133">Here's what's going on:</span></span>
1. <span data-ttu-id="20f85-134">En primer lugar, convierte la imagen con seguimiento en un elemento **ARTrackedQRCode** para comprobar que la imagen actualizada actual es un código QR.</span><span class="sxs-lookup"><span data-stu-id="20f85-134">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="20f85-135">Los datos codificados se recuperan de la variable **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="20f85-135">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="20f85-136">Puede obtener la parte superior izquierda del código QR en la ubicación de **GetLocalToWorldTransform** y las dimensiones con **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="20f85-136">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="20f85-137">También puede [obtener el sistema de coordenadas para un código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) en el código.</span><span class="sxs-lookup"><span data-stu-id="20f85-137">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="20f85-138">Búsqueda del identificador único</span><span class="sxs-lookup"><span data-stu-id="20f85-138">Finding the unique ID</span></span>
<span data-ttu-id="20f85-139">Cada código QR tiene un id. de GUID único, que puede buscar:</span><span class="sxs-lookup"><span data-stu-id="20f85-139">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="20f85-140">Arrastrando y colocando el marcador **As ARTracked QRCode** (Como QRCode ARTracked) y buscando **Get Unique ID** (Obtener id. único).</span><span class="sxs-lookup"><span data-stu-id="20f85-140">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID de QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="20f85-142">Ocurren muchas cosas en segundo plano con los códigos QR, por lo que esto no es todo.</span><span class="sxs-lookup"><span data-stu-id="20f85-142">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="20f85-143">Asegúrese de consultar los siguientes vínculos para obtener más detalles sobre ellos.</span><span class="sxs-lookup"><span data-stu-id="20f85-143">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="20f85-144">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="20f85-144">Next Development Checkpoint</span></span>

<span data-ttu-id="20f85-145">Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="20f85-145">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="20f85-146">Desde aquí, puede continuar con el tema siguiente:</span><span class="sxs-lookup"><span data-stu-id="20f85-146">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20f85-147">WinRT</span><span class="sxs-lookup"><span data-stu-id="20f85-147">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="20f85-148">O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:</span><span class="sxs-lookup"><span data-stu-id="20f85-148">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20f85-149">Implementación en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="20f85-149">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="20f85-150">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="20f85-150">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="20f85-151">Consulta también</span><span class="sxs-lookup"><span data-stu-id="20f85-151">See also</span></span>
* [<span data-ttu-id="20f85-152">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="20f85-152">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="20f85-153">Hologramas</span><span class="sxs-lookup"><span data-stu-id="20f85-153">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="20f85-154">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="20f85-154">Coordinate systems</span></span>](../../design/coordinate-systems.md)
