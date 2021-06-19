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
# <a name="qr-code-tracking"></a>Seguimiento de códigos QR

HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código. Una vez que habilite la cámara web del dispositivo, podrá reconocer códigos QR en las versiones más recientes de los proyectos de Unreal o Unity. Antes de pasar a producción, se recomienda seguir los [procedimientos](#best-practices-for-qr-code-detection) recomendados que hemos establecido al final del artículo.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (primera generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Detección de código QR</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>El seguimiento de código QR con cascos Windows Mixed Reality envolventes en equipos de escritorio se admite en Windows 10 versión 2004 y posteriores. Use la API Microsoft.MixedReality.QRCodeWatcher.IsSupported() para determinar si la característica se admite en el dispositivo actual.

## <a name="getting-the-qr-package"></a>Obtención del paquete QR

Puede descargar el paquete NuGet para la detección de código QR [aquí.](https://nuget.org/Packages/Microsoft.MixedReality.QR)

## <a name="using-openxr"></a>Uso de OpenXR

Cuando use el complemento OpenXR, tome el de [ `SpatialGraphNodeId` la API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) y use la API para buscar el código `Microsoft.MixedReality.OpenXR.SpatialGraphNode` QR.

Como referencia, tenemos un proyecto [de ejemplo de seguimiento QR en GitHub](https://github.com/yl-msft/QRTracking) con una explicación de uso más detallada para la [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="detecting-qr-codes"></a>Detección de códigos QR

### <a name="adding-the-webcam-capability"></a>Adición de la funcionalidad de cámara web

Deberá agregar la funcionalidad al manifiesto para detectar `webcam` códigos QR. Esta funcionalidad es necesaria, ya que los datos incluidos en los códigos detectados en el entorno del usuario pueden contener información confidencial.

El permiso se puede solicitar llamando a `QRCodeWatcher.RequestAccessAsync()` :

_C #:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

El permiso debe solicitarse antes de construir un objeto QRCodeWatcher.

Aunque la detección de código QR requiere la funcionalidad , la detección se produce `webcam` mediante las cámaras de seguimiento del dispositivo. Esto proporciona un FOV de detección más amplio y una mejor duración de la batería en comparación con la detección con la cámara de foto/vídeo (PV) del dispositivo.

### <a name="detecting-qr-codes-in-unity"></a>Detección de códigos QR en Unity

Puede usar la API de detección de código QR en Unity sin importar MRTK instalando el paquete NuGet mediante [NuGet para Unity.](https://github.com/GlitchEnzo/NuGetForUnity) Si quiere obtener una sensación de cómo funciona, descargue la [aplicación de Unity de ejemplo](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes). La aplicación de ejemplo tiene ejemplos para mostrar un cuadrado holográfico sobre códigos QR y datos asociados, como GUID, tamaño físico, marca de tiempo y datos descodificados.

### <a name="detecting-qr-codes-in-c"></a>Detección de códigos QR en C++

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Obtención del sistema de coordenadas para un código QR

Cada código QR detectado [](../../design/coordinate-systems.md) expone un sistema de coordenadas espaciales alineado con el código QR en la esquina superior izquierda del cuadrado de detección rápida de la parte superior izquierda:  

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

Cuando se usa directamente el SDK de QR, el eje Z apunta al papel (no se muestra): cuando se convierte en coordenadas de Unity, el eje Z apunta fuera del papel y es a la izquierda.

SpatialCoordinateSystem de un código QR se alinea como se muestra. Para obtener el sistema de coordenadas de la plataforma, llame a <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> y pase spatialGraphNodeId del código.

El código de C++ siguiente muestra cómo crear un rectángulo y colocarlo mediante el sistema de coordenadas del código QR:

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

Puede usar el tamaño físico para crear el rectángulo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

El sistema de coordenadas se puede usar para dibujar el código QR o adjuntar hologramas a la ubicación:

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

En conjunto, *qrcodeaddedHandler* puede tener un aspecto parecido al siguiente:

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

## <a name="best-practices-for-qr-code-detection"></a>Procedimientos recomendados para la detección de código QR

### <a name="quiet-zones-around-qr-codes"></a>Zonas silenciosas alrededor de códigos QR

Para leerse correctamente, los códigos QR requieren un margen alrededor de todos los lados del código. Este margen no debe contener ningún contenido impreso y debe tener cuatro módulos (un único cuadrado negro en el código) de ancho. 

La [especificación QR](https://www.qrcode.com/en/howto/code.html) contiene más información sobre las zonas silenciosas.

### <a name="lighting-and-backdrop"></a>Iluminación y fondo
La calidad de la detección de código QR es susceptible a diferentes iluminación y fondo. 

En una escena con iluminación brillante, imprima un código que sea negro sobre un fondo gris. De lo contrario, imprima un código QR negro en un fondo blanco.

Si el fondo del código es oscuro, pruebe un código negro sobre gris si la tasa de detección es baja. Si el fondo es relativamente claro, un código normal debería funcionar bien.

### <a name="size-of-qr-codes"></a>Tamaño de códigos QR
Windows Mixed Reality dispositivos no funcionan con códigos QR con lados de menos de 5 cm cada uno.

En el caso de los códigos QR de entre 5 cm y 10 cm de longitud, debe estar bastante cerca de detectar el código. También se tarda más tiempo en detectar códigos con este tamaño. 

El tiempo exacto para detectar códigos depende no solo del tamaño de los códigos QR, sino de la distancia que se encuentra del código. Acercarse al código le ayudará a compensar los problemas con el tamaño.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Distancia y posición angular desde el código QR
Las cámaras de seguimiento solo pueden detectar un cierto nivel de detalle. Para los códigos pequeños < 10 cm a lo largo de los lados, debe estar bastante cerca. Para un código QR de la versión 1 que va de 10 cm a 25 cm de ancho, la distancia de detección mínima oscila entre 0,15 y 0,5 metros. 

La distancia de detección del tamaño aumenta linealmente, pero también depende de la versión de QR o del tamaño del módulo. Cuanto mayor sea la versión, más pequeños serán los módulos, que solo se pueden detectar desde una posición más cercana. También puede probar códigos QR micro si desea que la distancia de detección sea mayor. La detección de QR funciona con un intervalo de ángulos += 45 deg para garantizar que tenemos una resolución adecuada para detectar el código.

> [!IMPORTANT]
> Asegúrese siempre de que tiene suficiente contraste y un borde adecuado.

### <a name="qr-codes-with-logos"></a>Códigos QR con logotipos
Los códigos QR con logotipos no se han probado y actualmente no se admiten.

### <a name="managing-qr-code-data"></a>Administración de datos de código QR
Windows Mixed Reality dispositivos detectan códigos QR en el nivel del sistema en el controlador. Cuando se reinicia el dispositivo, los códigos QR detectados desaparecen y se volverán a detectar como nuevos objetos la próxima vez.

Se recomienda configurar la aplicación para omitir los códigos QR anteriores a una marca de tiempo específica. Actualmente, la API no admite borrar el historial de códigos QR.

### <a name="qr-code-placement-in-a-space"></a>Colocación de código QR en un espacio
Para obtener recomendaciones sobre dónde y cómo colocar códigos QR, consulte [Consideraciones de entorno para HoloLens.](/hololens/hololens-environment-considerations)

## <a name="qr-api-reference"></a>Referencia de QR API

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

## <a name="see-also"></a>Vea también
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>