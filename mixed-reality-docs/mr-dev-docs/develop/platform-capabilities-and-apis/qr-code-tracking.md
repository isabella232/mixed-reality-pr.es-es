---
title: Seguimiento de códigos QR
description: Obtenga información sobre cómo detectar códigos QR en HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, entretenimiento basado en ubicación, VR Arcade, Arcade, inmersivo, QR, código QR, hololens2
ms.openlocfilehash: 023da7a98d1559d9dd0387a7efbaf26ad577df50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530011"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="e3fcc-104">Seguimiento de códigos QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-104">QR code tracking</span></span>

<span data-ttu-id="e3fcc-105">HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="e3fcc-106">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="e3fcc-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e3fcc-107">Característica</span><span class="sxs-lookup"><span data-stu-id="e3fcc-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e3fcc-108"><a href="../../hololens-hardware-details.md">HoloLens (primera generación)</a></span><span class="sxs-lookup"><span data-stu-id="e3fcc-108"><a href="../../hololens-hardware-details.md">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="e3fcc-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e3fcc-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="e3fcc-110"><a href="../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="e3fcc-110"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e3fcc-111">Detección del código QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="e3fcc-112">️</span><span class="sxs-lookup"><span data-stu-id="e3fcc-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e3fcc-113">✔️</span><span class="sxs-lookup"><span data-stu-id="e3fcc-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="e3fcc-114">✔️</span><span class="sxs-lookup"><span data-stu-id="e3fcc-114">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="e3fcc-115">El seguimiento del código QR con auriculares con ventanas de gran nivel en equipos de escritorio es compatible con la versión 2004 y posteriores de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-115">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="e3fcc-116">Use la API Microsoft. MixedReality. QRCodeWatcher. IsSupported () para determinar si la característica es compatible con el dispositivo actual.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-116">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="e3fcc-117">Obtención del paquete QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-117">Getting the QR package</span></span>

<span data-ttu-id="e3fcc-118">Puede descargar el paquete NuGet para la detección del código QR [aquí](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span><span class="sxs-lookup"><span data-stu-id="e3fcc-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="e3fcc-119">Detección de códigos QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="e3fcc-120">Agregar la funcionalidad de cámara web</span><span class="sxs-lookup"><span data-stu-id="e3fcc-120">Adding the webcam capability</span></span>

<span data-ttu-id="e3fcc-121">Deberá agregar la funcionalidad `webcam` al manifiesto para detectar códigos QR.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-121">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="e3fcc-122">Esta capacidad es necesaria, ya que los datos de los códigos detectados en el entorno del usuario pueden contener información confidencial.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="e3fcc-123">El permiso se puede solicitar mediante una llamada a `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="e3fcc-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="e3fcc-124">_C#_</span><span class="sxs-lookup"><span data-stu-id="e3fcc-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="e3fcc-125">_C_</span><span class="sxs-lookup"><span data-stu-id="e3fcc-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="e3fcc-126">Se debe solicitar permiso antes de construir un objeto QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="e3fcc-127">Aunque la detección del código QR requiere la `webcam` capacidad, la detección se produce mediante las cámaras de seguimiento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="e3fcc-128">Esto proporciona un hipergráfico de detección más amplio y una mayor duración de la batería en comparación con la detección con la cámara foto/vídeo (PV) del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="e3fcc-129">Detección de códigos QR en Unity</span><span class="sxs-lookup"><span data-stu-id="e3fcc-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="e3fcc-130">Puede usar la API de detección de código QR en Unity sin importar MRTK mediante la instalación del paquete de NuGet con [Nuget para Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="e3fcc-130">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="e3fcc-131">Si quiere saber cómo funciona, descargue la [aplicación de ejemplo de Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span><span class="sxs-lookup"><span data-stu-id="e3fcc-131">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="e3fcc-132">La aplicación de ejemplo tiene ejemplos para mostrar un cuadrado holográfica sobre códigos QR y datos asociados, como GUID, tamaño físico, marca de tiempo y datos descodificados.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-132">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="e3fcc-133">Detectar códigos QR en C++</span><span class="sxs-lookup"><span data-stu-id="e3fcc-133">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="e3fcc-134">Obtención del sistema de coordenadas para un código QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-134">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="e3fcc-135">Cada código QR detectado expone un [sistema de coordenadas espaciales](../../design/coordinate-systems.md) alineado con el código QR en la esquina superior izquierda del cuadrado de detección rápida en la parte superior izquierda:</span><span class="sxs-lookup"><span data-stu-id="e3fcc-135">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![Sistema de coordenadas del código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="e3fcc-137">Cuando se usa directamente el SDK QR, el eje Z apunta al papel (no se muestra) cuando se convierte en coordenadas de Unity, el eje Z apunta fuera del papel y se entrega a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="e3fcc-138">El SpatialCoordinateSystem de un código QR se alinea como se muestra.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="e3fcc-139">Puede obtener el sistema de coordenadas de la plataforma llamando a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> y pasando el SpatialGraphNodeId del código.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-139">You can get the coordinate system from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="e3fcc-140">En el código de C++ siguiente se muestra cómo crear un rectángulo y colocarlo mediante el sistema de coordenadas del código QR:</span><span class="sxs-lookup"><span data-stu-id="e3fcc-140">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="e3fcc-141">Puede usar el tamaño físico para crear el rectángulo QR:</span><span class="sxs-lookup"><span data-stu-id="e3fcc-141">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="e3fcc-142">El sistema de coordenadas se puede usar para dibujar el código QR o adjuntar hologramas a la ubicación:</span><span class="sxs-lookup"><span data-stu-id="e3fcc-142">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="e3fcc-143">Por completo, su *QRCodeAddedHandler* puede tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="e3fcc-143">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="e3fcc-144">Prácticas recomendadas para la detección del código QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-144">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="e3fcc-145">Zonas tranquilas alrededor de códigos QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-145">Quiet zones around QR Codes</span></span>

<span data-ttu-id="e3fcc-146">Para que se puedan leer correctamente, los códigos QR requieren un margen alrededor de todos los lados del código.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-146">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="e3fcc-147">Este margen no debe contener contenido impreso y debe ser de cuatro módulos (un solo cuadrado negro en el código).</span><span class="sxs-lookup"><span data-stu-id="e3fcc-147">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="e3fcc-148">La [especificación QR](https://www.qrcode.com/en/howto/code.html) contiene más información acerca de las zonas tranquilas.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-148">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="e3fcc-149">Iluminación y fondo</span><span class="sxs-lookup"><span data-stu-id="e3fcc-149">Lighting and backdrop</span></span>
<span data-ttu-id="e3fcc-150">La calidad de detección del código QR es susceptible a la iluminación y el telón de fondo variables.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-150">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="e3fcc-151">En una escena con iluminación brillante, imprima un código negro sobre un fondo gris.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-151">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="e3fcc-152">De lo contrario, imprima un código QR negro sobre un fondo blanco.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-152">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="e3fcc-153">Si el telón de fondo del código es oscuro, pruebe con un color negro en el código gris si la tasa de detección es baja.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-153">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="e3fcc-154">Si el telón de fondo es relativamente claro, un código normal debería funcionar correctamente.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-154">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="e3fcc-155">Tamaño de los códigos QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-155">Size of QR codes</span></span>
<span data-ttu-id="e3fcc-156">Los dispositivos de Windows Mixed Reality no funcionan con códigos QR con lados inferiores a 5 cm cada uno.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-156">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="e3fcc-157">En el caso de los códigos QR entre 5 cm y 10 cm de longitud, debe estar bastante cerca de detectar el código.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-157">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="e3fcc-158">También se tardará más tiempo en detectar códigos en este tamaño.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-158">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="e3fcc-159">El tiempo exacto para detectar códigos depende no solo del tamaño de los códigos QR, sino de la distancia del código.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-159">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="e3fcc-160">Si se desplaza más cerca del código, se le ayudará a desplazar los problemas con el tamaño.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-160">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="e3fcc-161">Distancia y posición angular del código QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-161">Distance and angular position from the QR code</span></span>
<span data-ttu-id="e3fcc-162">Las cámaras de seguimiento solo pueden detectar un cierto nivel de detalle.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-162">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="e3fcc-163">En el caso de códigos pequeños (< 10 cm a lo largo de los lados) debe estar bastante cerca.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-163">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="e3fcc-164">En el caso de un código QR de la versión 1 que varía de 10 cm a 25 cm de ancho, la distancia mínima de detección oscila entre 0,15 y 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-164">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="e3fcc-165">La distancia de detección para el tamaño aumenta linealmente.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-165">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="e3fcc-166">La detección de QR funciona con un rango de ángulos + = 45 grados para garantizar que tenemos una solución adecuada para detectar el código.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-166">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="e3fcc-167">Códigos QR con logotipos</span><span class="sxs-lookup"><span data-stu-id="e3fcc-167">QR codes with logos</span></span>
<span data-ttu-id="e3fcc-168">Los códigos QR con logotipos no se han probado y actualmente no se admiten.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-168">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="e3fcc-169">Administración de datos de código QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-169">Managing QR code data</span></span>
<span data-ttu-id="e3fcc-170">Los dispositivos de Windows Mixed Reality detectan códigos QR en el nivel de sistema del controlador.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-170">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="e3fcc-171">Cuando se reinicia el dispositivo, los códigos QR detectados desaparecen y se volverán a detectar como nuevos objetos la próxima vez.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-171">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="e3fcc-172">Se recomienda configurar la aplicación para omitir los códigos QR anteriores a una marca de tiempo específica.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-172">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="e3fcc-173">Actualmente, la API no permite borrar el historial del código QR.</span><span class="sxs-lookup"><span data-stu-id="e3fcc-173">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="e3fcc-174">Colocación del código QR en un espacio</span><span class="sxs-lookup"><span data-stu-id="e3fcc-174">QR code placement in a space</span></span>
<span data-ttu-id="e3fcc-175">Para obtener recomendaciones sobre dónde y cómo colocar códigos QR, consulte [consideraciones de entorno para HoloLens](../../environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="e3fcc-175">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](../../environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="e3fcc-176">Referencia de la API QR</span><span class="sxs-lookup"><span data-stu-id="e3fcc-176">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e3fcc-177">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e3fcc-177">See also</span></span>
* [<span data-ttu-id="e3fcc-178">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="e3fcc-178">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="e3fcc-179"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="e3fcc-179"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>
