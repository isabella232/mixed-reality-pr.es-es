---
title: Seguimiento de códigos QR
description: Obtenga información sobre cómo detectar códigos QR, agregar funcionalidades de cámara web y administrar sistemas de coordenadas en aplicaciones de realidad mixta HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr, lbe, entretenimiento basado en la ubicación, vr vr, vr vr, inmersivo, qr, código qr, hololens2
ms.openlocfilehash: 9d3a5d9696fbf875b2e6a890ed837efc055a9e6e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394339"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="7b8f5-104">Seguimiento de códigos QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-104">QR code tracking</span></span>

<span data-ttu-id="7b8f5-105">HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="7b8f5-106">Una vez que habilite la cámara web del dispositivo, podrá reconocer códigos QR en las versiones más recientes de los proyectos de Unreal o Unity.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="7b8f5-107">Antes de pasar a producción, se recomienda seguir los [procedimientos](#best-practices-for-qr-code-detection) recomendados que hemos establecido al final del artículo.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="7b8f5-108">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="7b8f5-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7b8f5-109">Característica</span><span class="sxs-lookup"><span data-stu-id="7b8f5-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="7b8f5-110"><a href="/hololens/hololens1-hardware">HoloLens (primera generación)</a></span><span class="sxs-lookup"><span data-stu-id="7b8f5-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="7b8f5-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7b8f5-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="7b8f5-112"><a href="../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="7b8f5-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7b8f5-113">Detección de código QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="7b8f5-114">️</span><span class="sxs-lookup"><span data-stu-id="7b8f5-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7b8f5-115">✔️</span><span class="sxs-lookup"><span data-stu-id="7b8f5-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="7b8f5-116">✔️</span><span class="sxs-lookup"><span data-stu-id="7b8f5-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="7b8f5-117">El seguimiento de código QR con cascos Windows Mixed Reality envolventes en equipos de escritorio se admite en Windows 10 versión 2004 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="7b8f5-118">Use la API Microsoft.MixedReality.QRCodeWatcher.IsSupported() para determinar si la característica se admite en el dispositivo actual.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="7b8f5-119">Obtención del paquete QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-119">Getting the QR package</span></span>

<span data-ttu-id="7b8f5-120">Puede descargar el paquete NuGet para la detección de código QR [aquí.](https://nuget.org/Packages/Microsoft.MixedReality.QR)</span><span class="sxs-lookup"><span data-stu-id="7b8f5-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="using-openxr"></a><span data-ttu-id="7b8f5-121">Uso de OpenXR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-121">Using OpenXR</span></span>

<span data-ttu-id="7b8f5-122">Cuando use el complemento OpenXR, tome el de [ `SpatialGraphNodeId` la API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) y use la API para buscar el código `Microsoft.MixedReality.OpenXR.SpatialGraphNode` QR.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-122">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="7b8f5-123">Como referencia, tenemos un proyecto [de ejemplo de seguimiento QR en GitHub](https://github.com/yl-msft/QRTracking) con una explicación de uso más detallada para la [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span><span class="sxs-lookup"><span data-stu-id="7b8f5-123">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="7b8f5-124">Detección de códigos QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-124">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="7b8f5-125">Adición de la funcionalidad de cámara web</span><span class="sxs-lookup"><span data-stu-id="7b8f5-125">Adding the webcam capability</span></span>

<span data-ttu-id="7b8f5-126">Deberá agregar la funcionalidad al manifiesto para detectar `webcam` códigos QR.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-126">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="7b8f5-127">Esta funcionalidad es necesaria, ya que los datos incluidos en los códigos detectados en el entorno del usuario pueden contener información confidencial.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-127">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="7b8f5-128">El permiso se puede solicitar llamando a `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="7b8f5-128">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="7b8f5-129">_C #:_</span><span class="sxs-lookup"><span data-stu-id="7b8f5-129">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="7b8f5-130">_C++:_</span><span class="sxs-lookup"><span data-stu-id="7b8f5-130">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="7b8f5-131">El permiso debe solicitarse antes de construir un objeto QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-131">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="7b8f5-132">Aunque la detección de código QR requiere la funcionalidad , la detección se produce `webcam` mediante las cámaras de seguimiento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-132">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="7b8f5-133">Esto proporciona un FOV de detección más amplio y una mejor duración de la batería en comparación con la detección con la cámara de foto/vídeo (PV) del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-133">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="7b8f5-134">Detección de códigos QR en Unity</span><span class="sxs-lookup"><span data-stu-id="7b8f5-134">Detecting QR codes in Unity</span></span>

<span data-ttu-id="7b8f5-135">Puede usar la API de detección de código QR en Unity sin importar MRTK instalando el paquete NuGet mediante [NuGet para Unity.](https://github.com/GlitchEnzo/NuGetForUnity)</span><span class="sxs-lookup"><span data-stu-id="7b8f5-135">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="7b8f5-136">Si quiere obtener una sensación de cómo funciona, descargue la [aplicación de Unity de ejemplo](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span><span class="sxs-lookup"><span data-stu-id="7b8f5-136">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="7b8f5-137">La aplicación de ejemplo tiene ejemplos para mostrar un cuadrado holográfico sobre códigos QR y datos asociados, como GUID, tamaño físico, marca de tiempo y datos descodificados.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-137">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="7b8f5-138">Detección de códigos QR en C++</span><span class="sxs-lookup"><span data-stu-id="7b8f5-138">Detecting QR codes in C++</span></span>

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="7b8f5-139">Obtención del sistema de coordenadas para un código QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-139">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="7b8f5-140">Cada código QR detectado [](../../design/coordinate-systems.md) expone un sistema de coordenadas espaciales alineado con el código QR en la esquina superior izquierda del cuadrado de detección rápida de la parte superior izquierda:</span><span class="sxs-lookup"><span data-stu-id="7b8f5-140">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="7b8f5-142">Cuando se usa directamente el SDK de QR, el eje Z apunta al papel (no se muestra): cuando se convierte en coordenadas de Unity, el eje Z apunta fuera del papel y es a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="7b8f5-143">SpatialCoordinateSystem de un código QR se alinea como se muestra.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-143">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="7b8f5-144">Para obtener el sistema de coordenadas de la plataforma, llame a <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> y pase spatialGraphNodeId del código.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-144">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="7b8f5-145">El código de C++ siguiente muestra cómo crear un rectángulo y colocarlo mediante el sistema de coordenadas del código QR:</span><span class="sxs-lookup"><span data-stu-id="7b8f5-145">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="7b8f5-146">Puede usar el tamaño físico para crear el rectángulo QR:</span><span class="sxs-lookup"><span data-stu-id="7b8f5-146">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="7b8f5-147">El sistema de coordenadas se puede usar para dibujar el código QR o adjuntar hologramas a la ubicación:</span><span class="sxs-lookup"><span data-stu-id="7b8f5-147">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="7b8f5-148">En conjunto, *qrcodeaddedHandler* puede tener un aspecto parecido al siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b8f5-148">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="7b8f5-149">Procedimientos recomendados para la detección de código QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-149">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="7b8f5-150">Zonas silenciosas alrededor de códigos QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-150">Quiet zones around QR Codes</span></span>

<span data-ttu-id="7b8f5-151">Para leerse correctamente, los códigos QR requieren un margen alrededor de todos los lados del código.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-151">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="7b8f5-152">Este margen no debe contener ningún contenido impreso y debe tener cuatro módulos (un único cuadrado negro en el código) de ancho.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-152">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="7b8f5-153">La [especificación QR](https://www.qrcode.com/en/howto/code.html) contiene más información sobre las zonas silenciosas.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-153">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="7b8f5-154">Iluminación y fondo</span><span class="sxs-lookup"><span data-stu-id="7b8f5-154">Lighting and backdrop</span></span>
<span data-ttu-id="7b8f5-155">La calidad de la detección de código QR es susceptible a diferentes iluminación y fondo.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-155">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="7b8f5-156">En una escena con iluminación brillante, imprima un código que sea negro sobre un fondo gris.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-156">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="7b8f5-157">De lo contrario, imprima un código QR negro en un fondo blanco.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-157">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="7b8f5-158">Si el fondo del código es oscuro, pruebe un código negro sobre gris si la tasa de detección es baja.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-158">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="7b8f5-159">Si el fondo es relativamente claro, un código normal debería funcionar bien.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-159">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="7b8f5-160">Tamaño de códigos QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-160">Size of QR codes</span></span>
<span data-ttu-id="7b8f5-161">Windows Mixed Reality dispositivos no funcionan con códigos QR con lados de menos de 5 cm cada uno.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-161">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="7b8f5-162">En el caso de los códigos QR de entre 5 cm y 10 cm de longitud, debe estar bastante cerca de detectar el código.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-162">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="7b8f5-163">También se tarda más tiempo en detectar códigos con este tamaño.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-163">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="7b8f5-164">El tiempo exacto para detectar códigos depende no solo del tamaño de los códigos QR, sino de la distancia que se encuentra del código.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-164">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="7b8f5-165">Acercarse al código le ayudará a compensar los problemas con el tamaño.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-165">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="7b8f5-166">Distancia y posición angular desde el código QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-166">Distance and angular position from the QR code</span></span>
<span data-ttu-id="7b8f5-167">Las cámaras de seguimiento solo pueden detectar un cierto nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-167">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="7b8f5-168">Para los códigos pequeños < 10 cm a lo largo de los lados, debe estar bastante cerca.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-168">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="7b8f5-169">Para un código QR de la versión 1 que va de 10 cm a 25 cm de ancho, la distancia de detección mínima oscila entre 0,15 y 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-169">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="7b8f5-170">La distancia de detección del tamaño aumenta linealmente, pero también depende de la versión de QR o del tamaño del módulo.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-170">The detection distance for size increases linearly, but also depends on QR version or module size.</span></span> <span data-ttu-id="7b8f5-171">Cuanto mayor sea la versión, más pequeños serán los módulos, que solo se pueden detectar desde una posición más cercana.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-171">The higher the version, the smaller the modules, which can only be detected from a closer position.</span></span> <span data-ttu-id="7b8f5-172">También puede probar códigos QR micro si desea que la distancia de detección sea mayor.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-172">You can also try micro QR codes if you want the distance of detection to be longer.</span></span> <span data-ttu-id="7b8f5-173">La detección de QR funciona con un intervalo de ángulos += 45 deg para garantizar que tenemos una resolución adecuada para detectar el código.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-173">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b8f5-174">Asegúrese siempre de que tiene suficiente contraste y un borde adecuado.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-174">Always make sure you have enough contrast and a proper border.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="7b8f5-175">Códigos QR con logotipos</span><span class="sxs-lookup"><span data-stu-id="7b8f5-175">QR codes with logos</span></span>
<span data-ttu-id="7b8f5-176">Los códigos QR con logotipos no se han probado y actualmente no se admiten.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-176">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="7b8f5-177">Administración de datos de código QR</span><span class="sxs-lookup"><span data-stu-id="7b8f5-177">Managing QR code data</span></span>
<span data-ttu-id="7b8f5-178">Windows Mixed Reality dispositivos detectan códigos QR en el nivel del sistema en el controlador.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-178">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="7b8f5-179">Cuando se reinicia el dispositivo, los códigos QR detectados desaparecen y se volverán a detectar como nuevos objetos la próxima vez.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-179">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="7b8f5-180">Se recomienda configurar la aplicación para omitir los códigos QR anteriores a una marca de tiempo específica.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-180">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="7b8f5-181">Actualmente, la API no admite borrar el historial de códigos QR.</span><span class="sxs-lookup"><span data-stu-id="7b8f5-181">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="7b8f5-182">Colocación de código QR en un espacio</span><span class="sxs-lookup"><span data-stu-id="7b8f5-182">QR code placement in a space</span></span>
<span data-ttu-id="7b8f5-183">Para obtener recomendaciones sobre dónde y cómo colocar códigos QR, consulte [Consideraciones de entorno para HoloLens.](/hololens/hololens-environment-considerations)</span><span class="sxs-lookup"><span data-stu-id="7b8f5-183">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="7b8f5-184">Referencia de QR API</span><span class="sxs-lookup"><span data-stu-id="7b8f5-184">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="7b8f5-185">Vea también</span><span class="sxs-lookup"><span data-stu-id="7b8f5-185">See also</span></span>
* [<span data-ttu-id="7b8f5-186">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="7b8f5-186">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="7b8f5-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="7b8f5-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>