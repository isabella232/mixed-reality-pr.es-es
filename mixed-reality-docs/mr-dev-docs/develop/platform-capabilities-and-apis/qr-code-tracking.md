---
title: Seguimiento de códigos QR
description: Obtenga información sobre cómo detectar códigos QR, agregar funcionalidades de cámara web y administrar sistemas de coordenadas en aplicaciones de realidad mixta en HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: VR, LBE, entretenimiento basado en ubicación, VR Arcade, Arcade, inmersivo, QR, código QR, hololens2
ms.openlocfilehash: 2617d5f811b9d437ece0d5ba2e7dbc909eb16988
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103574951"
---
# <a name="qr-code-tracking"></a>Seguimiento de códigos QR

HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código. Una vez que habilite la cámara web del dispositivo, podrá reconocer códigos QR en las versiones más recientes de los proyectos no reales o de Unity. Antes de pasar a producción, se recomienda seguir los procedimientos [recomendados](#best-practices-for-qr-code-detection) que hemos establecido al final del artículo.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (primera generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Detección del código QR</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>El seguimiento del código QR con auriculares con ventanas de gran nivel en equipos de escritorio es compatible con la versión 2004 y posteriores de Windows 10. Use la API Microsoft. MixedReality. QRCodeWatcher. IsSupported () para determinar si la característica es compatible con el dispositivo actual.

## <a name="getting-the-qr-package"></a>Obtención del paquete QR

Puede descargar el paquete NuGet para la detección del código QR [aquí](https://nuget.org/Packages/Microsoft.MixedReality.QR).

## <a name="detecting-qr-codes"></a>Detección de códigos QR

### <a name="adding-the-webcam-capability"></a>Agregar la funcionalidad de cámara web

Deberá agregar la funcionalidad `webcam` al manifiesto para detectar códigos QR. Esta capacidad es necesaria, ya que los datos de los códigos detectados en el entorno del usuario pueden contener información confidencial.

El permiso se puede solicitar mediante una llamada a `QRCodeWatcher.RequestAccessAsync()` :

_C#_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

Se debe solicitar permiso antes de construir un objeto QRCodeWatcher.

Aunque la detección del código QR requiere la `webcam` capacidad, la detección se produce mediante las cámaras de seguimiento del dispositivo. Esto proporciona un hipergráfico de detección más amplio y una mayor duración de la batería en comparación con la detección con la cámara foto/vídeo (PV) del dispositivo.

### <a name="detecting-qr-codes-in-unity"></a>Detección de códigos QR en Unity

Puede usar la API de detección de código QR en Unity sin importar MRTK mediante la instalación del paquete de NuGet con [Nuget para Unity](https://github.com/GlitchEnzo/NuGetForUnity). Si quiere saber cómo funciona, descargue la [aplicación de ejemplo de Unity](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes). La aplicación de ejemplo tiene ejemplos para mostrar un cuadrado holográfica sobre códigos QR y datos asociados, como GUID, tamaño físico, marca de tiempo y datos descodificados.

### <a name="detecting-qr-codes-in-c"></a>Detectar códigos QR en C++

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

Cada código QR detectado expone un [sistema de coordenadas espaciales](../../design/coordinate-systems.md) alineado con el código QR en la esquina superior izquierda del cuadrado de detección rápida en la parte superior izquierda:  

![Sistema de coordenadas del código QR](images/Qr-coordinatesystem.png) 

Cuando se usa directamente el SDK QR, el eje Z apunta al papel (no se muestra) cuando se convierte en coordenadas de Unity, el eje Z apunta fuera del papel y se entrega a la izquierda.

El SpatialCoordinateSystem de un código QR se alinea como se muestra. Puede obtener el sistema de coordenadas de la plataforma llamando a <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> y pasando el SpatialGraphNodeId del código.

En el código de C++ siguiente se muestra cómo crear un rectángulo y colocarlo mediante el sistema de coordenadas del código QR:

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

Por completo, su *QRCodeAddedHandler* puede tener un aspecto similar al siguiente:

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

## <a name="best-practices-for-qr-code-detection"></a>Prácticas recomendadas para la detección del código QR

### <a name="quiet-zones-around-qr-codes"></a>Zonas tranquilas alrededor de códigos QR

Para que se puedan leer correctamente, los códigos QR requieren un margen alrededor de todos los lados del código. Este margen no debe contener contenido impreso y debe ser de cuatro módulos (un solo cuadrado negro en el código). 

La [especificación QR](https://www.qrcode.com/en/howto/code.html) contiene más información acerca de las zonas tranquilas.

### <a name="lighting-and-backdrop"></a>Iluminación y fondo
La calidad de detección del código QR es susceptible a la iluminación y el telón de fondo variables. 

En una escena con iluminación brillante, imprima un código negro sobre un fondo gris. De lo contrario, imprima un código QR negro sobre un fondo blanco.

Si el telón de fondo del código es oscuro, pruebe con un color negro en el código gris si la tasa de detección es baja. Si el telón de fondo es relativamente claro, un código normal debería funcionar correctamente.

### <a name="size-of-qr-codes"></a>Tamaño de los códigos QR
Los dispositivos de Windows Mixed Reality no funcionan con códigos QR con lados inferiores a 5 cm cada uno.

En el caso de los códigos QR entre 5 cm y 10 cm de longitud, debe estar bastante cerca de detectar el código. También se tardará más tiempo en detectar códigos en este tamaño. 

El tiempo exacto para detectar códigos depende no solo del tamaño de los códigos QR, sino de la distancia del código. Si se desplaza más cerca del código, se le ayudará a desplazar los problemas con el tamaño.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Distancia y posición angular del código QR
Las cámaras de seguimiento solo pueden detectar un cierto nivel de detalle. En el caso de códigos pequeños (< 10 cm a lo largo de los lados) debe estar bastante cerca. En el caso de un código QR de la versión 1 que varía de 10 cm a 25 cm de ancho, la distancia mínima de detección oscila entre 0,15 y 0,5 metros. 

La distancia de detección para el tamaño aumenta linealmente, pero también depende de la versión QR o del tamaño del módulo. Cuanto mayor sea la versión, más pequeños serán los módulos, que solo se pueden detectar desde una posición más cercana. También puede probar códigos micro QR si desea que la distancia de detección sea más larga. La detección de QR funciona con un rango de ángulos + = 45 grados para garantizar que tenemos una solución adecuada para detectar el código.

> [!IMPORTANT]
> Asegúrese siempre de que tiene un contraste suficiente y un borde adecuado.

### <a name="qr-codes-with-logos"></a>Códigos QR con logotipos
Los códigos QR con logotipos no se han probado y actualmente no se admiten.

### <a name="managing-qr-code-data"></a>Administración de datos de código QR
Los dispositivos de Windows Mixed Reality detectan códigos QR en el nivel de sistema del controlador. Cuando se reinicia el dispositivo, los códigos QR detectados desaparecen y se volverán a detectar como nuevos objetos la próxima vez.

Se recomienda configurar la aplicación para omitir los códigos QR anteriores a una marca de tiempo específica. Actualmente, la API no permite borrar el historial del código QR.

### <a name="qr-code-placement-in-a-space"></a>Colocación del código QR en un espacio
Para obtener recomendaciones sobre dónde y cómo colocar códigos QR, consulte [consideraciones de entorno para HoloLens](/hololens/hololens-environment-considerations).

## <a name="qr-api-reference"></a>Referencia de la API QR

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

## <a name="see-also"></a>Consulte también
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>