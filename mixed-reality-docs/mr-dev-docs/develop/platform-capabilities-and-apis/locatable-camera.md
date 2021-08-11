---
title: Cámara localizable
description: Información general sobre la HoloLens frontal, cómo funciona y los perfiles y resoluciones disponibles para los desarrolladores.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: camera, hololens, color camera, front facing, hololens 2, cv, computer vision, fiducial, markers, qr code, qr, photo, video
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217101"
---
# <a name="locatable-camera"></a>Cámara localizable

HoloLens incluye una cámara de visión general montada en la parte frontal del dispositivo, lo que permite a las aplicaciones ver lo que ve el usuario. Los desarrolladores tienen acceso y control de la cámara, como lo harían con las cámaras de color en smartphones, portátiles o escritorios. Las mismas API universales de windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture) y Windows Media Foundation que funcionan en dispositivos móviles y de escritorio en HoloLens. Unity [ha ajustado estas API de Windows para](../unity/locatable-camera-in-unity.md) abstraer las características de uso de la cámara HoloLens. Las tareas de características incluyen tomar fotos y vídeos normales (con o sin hologramas) y localizar la posición de la cámara en la escena y su perspectiva.

## <a name="device-camera-information"></a>Información de la cámara del dispositivo

### <a name="hololens-first-generation"></a>HoloLens (primera generación)

* Se ha corregido el enfoque de la cámara de foto/vídeo (PV) con equilibrio de blanco automático, exposición automática y canalización de procesamiento de imágenes completa.
* El LED de privacidad blanca orientado al mundo se enciende cada vez que la cámara esté activa.
* La cámara admite los modos siguientes (todos los modos tienen una relación de aspecto de 16:9) a 30, 24, 20, 15 y 5 fps:

  |  Vídeo  |  Vista previa  |  Todavía  |  Campo de vista horizontal (H-FOV) |  Uso sugerido | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45 deg  |  (modo predeterminado con estabilización de vídeo) | 
  |  N/D |  N/D |  2048x1152 |  67 deg |  Imagen de la resolución más alta | 
  |  1408x792 |  1408x792 |  1408x792 |  48 deg |  Resolución de sobreexploración (relleno) antes de la estabilización del vídeo | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  Modo de vídeo fov grande con sobreexploración | 
  |  896x504 |  896x504 |  896x504 |  48 deg |  Modo de baja potencia/baja resolución para tareas de procesamiento de imágenes | 

### <a name="hololens-2"></a>HoloLens 2

* Cámara de foto/vídeo (PV) de enfoque automático con equilibrio de blanco automático, exposición automática y canalización de procesamiento de imágenes completa.
* El LED de privacidad blanca orientado al mundo se encenderá cada vez que la cámara esté activa.
* HoloLens 2 admite diferentes perfiles de cámara. Obtenga información sobre cómo [detectar y seleccionar las funcionalidades de la cámara.](/windows/uwp/audio-video-camera/camera-profiles)
* La cámara admite los siguientes perfiles y resoluciones (todos los modos de vídeo son relación de aspecto 16:9):
  
  | Perfil                                         | Vídeo     | Vista previa   | Todavía     | Velocidades de fotogramas | Campo de vista horizontal (H-FOV) | Uso sugerido                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0 BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | Grabación de vídeo de alta calidad                |
  | Legacy,0 BalancedVideoAndPhoto,100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | Secuencia de vista previa para la captura de fotos de alta calidad |
  | Legacy,0 BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | Captura de fotos de alta calidad                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | Escenarios de larga duración                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15.30       | 64.69                            | Escenarios de larga duración                     |
  | Videoconferencia,100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 1128x636  |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 960 x 540   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 760x428   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 640 x 360   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 500 x 282   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |
  | Videoconferencia,100 BalancedVideoAndPhoto,120 | 424 x 240   |           |           | 15,30       | 64.69                            | Videoconferencia, escenarios de larga duración |

> [!NOTE]
> Los clientes pueden [aprovechar la captura de realidad](/hololens/holographic-photos-and-videos) mixta para tomar vídeos o fotos de la aplicación, que incluyen hologramas y estabilización de vídeo.
>
>Como desarrollador, hay consideraciones que debe tener en cuenta al crear la aplicación si desea que tenga el aspecto más bueno posible cuando un cliente capture contenido. También puede habilitar (y personalizar) la captura de realidad mixta desde directamente dentro de la aplicación. Obtenga más información en [mixed reality capture for developers (Captura de realidad mixta para desarrolladores).](mixed-reality-capture-for-developers.md)

## <a name="locating-the-device-camera-in-the-world"></a>Buscar la cámara del dispositivo en el mundo

Cuando HoloLens fotos y vídeos, los fotogramas capturados incluyen la ubicación de la cámara en el mundo y el modelo de lente de la cámara. Esto permite a las aplicaciones razonar sobre la posición de la cámara en el mundo real para escenarios de creación de imágenes aumentadas. Los desarrolladores pueden crear sus propios escenarios con sus bibliotecas personalizadas de computer vision o procesamiento de imágenes favoritas.

"Cámara" en otro lugar de HoloLens documentación puede hacer referencia a la "cámara de juego virtual" (el frustum en el que se representa la aplicación). A menos que se indique lo contrario, la "cámara" de esta página hace referencia a la cámara de color RGB real.

### <a name="using-unity"></a>Con Unity

Para pasar de "CameraIntrinsics" y "CameraCoordinateSystem" al sistema de coordenadas de la aplicación o el mundo, siga las instrucciones del artículo Cámara localizable en [Unity.](../unity/locatable-camera-in-unity.md)  La clase PhotoCaptureFrame proporciona CameraToWorldMatrix automáticamente, por lo que no es necesario preocuparse por las transformaciones CameraCoordinateSystem que se deban tratar a continuación.

### <a name="using-mediaframereference"></a>Uso de MediaFrameReference

Estas instrucciones se aplican si usa la clase [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) para leer fotogramas de imagen de la cámara.

Cada fotograma de imagen (ya sea una foto o un vídeo) incluye un [elemento SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) basado en la cámara en el momento de la captura, al que se puede acceder mediante la propiedad [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) de [MediaFrameReference.](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference) Cada fotograma contiene una descripción del modelo de lente de la cámara, que se puede encontrar en la [propiedad CameraIntrinsics.](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) Juntas, estas transformaciones definen para cada píxel un rayo en el espacio 3D que representa la ruta de acceso tomada por los fotones que generaron el píxel. Estos rayos pueden estar relacionados con otro contenido de la aplicación mediante la obtención de la transformación [](../../design/coordinate-systems.md#stationary-frame-of-reference)del sistema de coordenadas del marco a algún otro sistema de coordenadas (por ejemplo, de un marco de referencia estacionado). 

Cada marco de imagen proporciona lo siguiente:
* Datos de píxeles (en formato RGB/NV12/JPEG/etc.)
* [SpatialCoordinateSystem desde](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) la ubicación de la captura
* Una [clase CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) que contiene el modo de lente de la cámara

El [ejemplo HolographicFaceTracking](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) muestra la manera bastante sencilla de consultar la transformación entre el sistema de coordenadas de la cámara y sus propios sistemas de coordenadas de aplicación.

### <a name="using-media-foundation"></a>Uso de Media Foundation

Si usa Media Foundation directamente para leer fotogramas de imagen de la cámara, puede usar el atributo MFSampleExtension_CameraExtrinsics y el atributo [MFSampleExtension_PinholeCameraIntrinsics](/windows/win32/medfound/mfsampleextension-cameraextrinsics) de cada fotograma para buscar fotogramas de cámara en relación [con](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) otros sistemas de coordenadas de la aplicación, como se muestra en este código de ejemplo:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>Error de distorsión

En HoloLens, los flujos de vídeo y de imagen todavía no sedistorgen en la canalización de procesamiento de imágenes del sistema antes de que los fotogramas estén disponibles para la aplicación (la secuencia de vista previa contiene los fotogramas distorsionados originales). Dado que solo están disponibles los elementos CameraIntrinsics, las aplicaciones deben asumir que los fotogramas de imagen representan una cámara perfecta.

En HoloLens (primera generación), la función de desdistorsión en el procesador de imágenes puede dejar un error de hasta 10 píxeles al usar CameraIntrinsics en los metadatos del fotograma. En muchos casos de uso, este error no importa, pero si alinea hologramas con pósteres o marcadores reales, por ejemplo, y observa un desplazamiento de <10 px (aproximadamente 11 mm para hologramas situados a 2 metros de distancia), este error de distorsión podría ser la causa. 

## <a name="locatable-camera-usage-scenarios"></a>Escenarios de uso de cámara localizables

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostrar una foto o un vídeo en el mundo donde se capturó

Los fotogramas de la cámara del dispositivo incluyen una transformación "Cámara a mundo", que se puede usar para mostrar exactamente dónde estaba el dispositivo cuando se tomó la imagen. Por ejemplo, podría colocar un pequeño icono holográfico en esta ubicación (CameraToWorld.MultiplyPoint(Vector3.zero)) e incluso dibujar una pequeña flecha en la dirección a la que estaba orientada la cámara (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Tag/Pattern/Poster/Object Tracking

Muchas aplicaciones de realidad mixta usan una imagen o un patrón visual reconocibles para crear un punto de seguimiento en el espacio. A continuación, se usa para representar objetos relativos a ese punto o crear una ubicación conocida. Algunos usos de HoloLens incluyen la búsqueda de un objeto real etiquetado con fiduciales (por ejemplo, un monitor de televisión con un código QR), la colocación de hologramas sobre fiduciales y el emparejamiento visual con dispositivos que no son de HoloLens, como tabletas que se han configurado para comunicarse con HoloLens a través de Wi-Fi.

Necesitará algunas cosas para reconocer un patrón visual y colocar un objeto en el espacio del mundo de las aplicaciones:
1. Un kit de herramientas de reconocimiento de patrones de imagen, como código QR, etiquetas AR, buscador de caras, seguimientos de círculos, OCR, etc.
2. Recopilar fotogramas de imagen en tiempo de ejecución y pasarlos a la capa de reconocimiento
3. Desproyecte sus ubicaciones de imagen de nuevo en posiciones del mundo o probablemente rayos del mundo. 
4. Colocación de los modelos virtuales en estas ubicaciones del mundo

Algunos vínculos importantes de procesamiento de imágenes:
* [OpenCV](https://opencv.org/)
* [Etiquetas QR](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Mantener una velocidad de fotogramas de aplicación interactiva es fundamental, especialmente cuando se trabaja con algoritmos de reconocimiento de imágenes de ejecución larga. Por esta razón, normalmente usamos el siguiente patrón:
1. Subproceso principal: administra el objeto de cámara
2. Subproceso principal: solicita nuevos fotogramas (asincrónicos)
3. Subproceso principal: pasar nuevos fotogramas al subproceso de seguimiento
4. Subproceso de seguimiento: procesa la imagen para recopilar puntos clave
5. Subproceso principal: mueve el modelo virtual para que coincida con los puntos clave encontrados
6. Subproceso principal: repita el paso 2

Algunos sistemas de marcadores de imagen solo proporcionan una ubicación de un solo píxel (otros proporcionan la transformación completa en cuyo caso esta sección no será necesaria), lo que equivale a un rayo de ubicaciones posibles. Para llegar a una única ubicación 3d, podemos aprovechar varios rayos y encontrar el resultado final por su intersección aproximada. Para ello, necesitará lo siguiente:
1. Obtener un bucle que va a recopilar varias imágenes de cámara
2. Buscar los puntos de características asociados y sus rayos del mundo
3. Cuando tenga un diccionario de características, cada una con varios rayos del mundo, puede usar el código siguiente para resolver la intersección de esos rayos:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Dadas dos o más ubicaciones de etiquetas con seguimiento, puede colocar una escena modelada para adaptarla al escenario actual del usuario. Si no puede asumir la gravedad, necesitará tres ubicaciones de etiquetas. En muchos casos, usamos una combinación de colores donde las esferas blancas representan ubicaciones de etiquetas con seguimiento en tiempo real y las esferas azules representan ubicaciones de etiquetas modeladas. Esto permite al usuario medir visualmente la calidad de la alineación. Se supone que la siguiente configuración se encuentra en todas nuestras aplicaciones:
* Dos o más ubicaciones de etiquetas modeladas
* Un "espacio de calibración", que en la escena es el elemento primario de las etiquetas
* Identificador de característica de cámara
* Comportamiento, que mueve el espacio de calibración para alinear las etiquetas modeladas con las etiquetas en tiempo real (tenemos cuidado de mover el espacio primario, no los propios marcadores modelados, porque otras conectaciones son posiciones relativas a ellos).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Seguimiento o identificación de objetos o caras del mundo real etiquetados como estacionados o en movimiento mediante LED u otras bibliotecas de reconocedores

Ejemplos:
* Robots industriales con LED (o códigos QR para objetos de movimiento más lentos)
* Identificación y reconocimiento de objetos en la sala
* Identificar y reconocer personas en la sala, por ejemplo, colocar tarjetas de contacto holográficas sobre caras

## <a name="see-also"></a>Consulte también
* [Ejemplo de cámara localizable](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Cámara localizable en Unity](../unity/locatable-camera-in-unity.md)
* [Captura de realidad mixta](/hololens/holographic-photos-and-videos)
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Introducción a la captura de medios](/windows/uwp/audio-video-camera/)
* [Ejemplo de seguimiento de caras holográficas](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)