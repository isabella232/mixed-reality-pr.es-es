---
title: Control con la cabeza y los ojos de DirectX
description: Obtenga información sobre cómo solicitar, usar y desempaquetar datos de difusión por rayos de la mirada con la cabeza y el seguimiento de los ojos en aplicaciones nativas de DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: mirada con los ojos, mirada con la cabeza, seguimiento de la cabeza, seguimiento de los ojos, directx, entrada, hologramas, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 0e32c9f24b56d938b5c6f9cbdf28e9959b190abc22591a26d1dfcfa0af2f5f4d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193216"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Entrada de mirada con la cabeza y mirada con los ojos en DirectX

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR.](openxr-getting-started.md)**

En Windows Mixed Reality, la entrada de mirada con los ojos y la cabeza se usa para determinar lo que el usuario está mirando. Puede usar los datos para impulsar los modelos de entrada principales, como la mirada con la cabeza y [la](../../design/gaze-and-commit.md)confirmación, y proporcionar contexto para los distintos tipos de interacción. Hay dos tipos de vectores de mirada disponibles a través de la API: la mirada con la cabeza y la mirada con los ojos.  Ambos se proporcionan como un rayo tridimensional con un origen y una dirección. A continuación, las aplicaciones se pueden convertir en sus escenas o en el mundo real y determinar a qué se dirigirá el usuario.

**La mirada con la** cabeza representa la dirección a la que apunta la cabeza del usuario. Piense en la mirada con la cabeza como la posición y la dirección hacia delante del propio dispositivo, con la posición como el punto central entre las dos pantallas. La mirada con la cabeza está disponible en todos Mixed Reality dispositivos.

**La mirada con los** ojos representa la dirección hacia la que miran los ojos del usuario. El origen se encuentra entre los ojos del usuario.  Está disponible en Mixed Reality dispositivos que incluyen un sistema de seguimiento ocular.

Los rayos de mirada con la cabeza y los ojos son accesibles a través de  [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API. Llame a [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose en la marca de tiempo y el sistema de [coordenadas especificados.](coordinate-systems-in-directx.md) SpatialPointerPose contiene un origen y una dirección de mirada con la cabeza. También contiene un origen y dirección de la mirada con los ojos si está disponible el seguimiento ocular.

### <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Característica</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Mirada con la cabeza</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Mirada con los ojos</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Uso de la mirada con la cabeza

Para acceder a la mirada con la cabeza, empiece por llamar a  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose. Pase los parámetros siguientes.
 - [SpatialCoordinateSystem que](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) representa el sistema de coordenadas que desea para la mirada con la cabeza. Esto se representa mediante la variable *coordinateSystem* en el código siguiente. Para más información, visite nuestra guía [para desarrolladores de sistemas](coordinate-systems-in-directx.md) de coordenadas.
 - Marca [de](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) tiempo que representa la hora exacta de la posición de la cabeza solicitada.  Normalmente, usará una marca de tiempo que corresponda a la hora en que se mostrará el marco actual. Puede obtener esta marca de tiempo de presentación predicho desde un objeto [HolographicFramePrediction,](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) al que se puede acceder a través del [elemento HolographicFrame actual.](/uwp/api/windows.graphics.holographic.holographicframe)  Este objeto HolographicFramePrediction se representa mediante la variable *de* predicción en el código siguiente.

 Una vez que tenga un SpatialPointerPose válido, la posición de la cabeza y la dirección hacia delante son accesibles como propiedades.  El código siguiente muestra cómo acceder a ellos.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Uso de la mirada con los ojos

Para que los usuarios usen la entrada de mirada con los ojos, cada usuario debe pasar por una calibración [de](/hololens/hololens-calibration) usuario de seguimiento ocular la primera vez que use el dispositivo. La API de mirada con los ojos es similar a la mirada con la cabeza.
Usa la misma API [SpatialPointerPose,](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) que proporciona un origen y una dirección de rayo que se pueden convertir en rayos en la escena.  La única diferencia es que debe habilitar explícitamente el seguimiento ocular antes de usarlo:
1. Solicite al usuario permiso para usar el seguimiento ocular en la aplicación.
2. Habilite la funcionalidad "Entrada de mirada" en el manifiesto del paquete.

### <a name="requesting-access-to-eye-gaze-input"></a>Solicitud de acceso a la entrada de mirada con los ojos

Cuando se inicie la aplicación, llame a [EyesPose::RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acceso al seguimiento ocular. El sistema preguntará al usuario si es necesario y devolverá [GazeInputAccessStatus::Allowed una](/uwp/api/windows.ui.input.gazeinputaccessstatus) vez que se haya concedido acceso. Se trata de una llamada asincrónica, por lo que requiere un poco de administración adicional. En el ejemplo siguiente se gira un std::thread desasociado para esperar el resultado, que almacena en una variable miembro denominada *m_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
Iniciar un subproceso desasociado es solo una opción para controlar las llamadas asincrónicas. También puedes usar la nueva funcionalidad [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) compatible con C++/WinRT.
Este es otro ejemplo para solicitar permiso de usuario:
-   EyesPose::IsSupported() permite que la aplicación desencadene el cuadro de diálogo de permisos solo si hay un seguimiento ocular.
-   GazeInputAccessStatus m_gazeInputAccessStatus; Esto es para evitar que se vuelva a abrir el símbolo del sistema de permisos una y otra vez.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>Declaración de la funcionalidad *Entrada de* mirada

Haga doble clic en el archivo appxmanifest *en Explorador de soluciones*.  A continuación, vaya a *la sección Funcionalidades* y compruebe la *funcionalidad Entrada de* mirada. 

![Funcionalidad de entrada de mirada](images/gaze-input-capability.png)

Esto agrega las siguientes líneas a la *sección Paquete* del archivo appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Obtención del rayo de la mirada con los ojos

Una vez que haya recibido acceso a ET, puede agarrar el rayo de la mirada con los ojos en cada fotograma.
Al igual que con la mirada con la cabeza, obtenga [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) llamando a [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con una marca de tiempo y un sistema de coordenadas deseados. SpatialPointerPose contiene un [objeto EyesPose](/uwp/api/windows.perception.people.eyespose) a través de la [propiedad Eyes.](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Esto no es null solo si está habilitado el seguimiento ocular. Desde allí, puede comprobar si el usuario del dispositivo tiene una calibración de seguimiento de los ojos mediante una llamada a [EyesPose::IsPlantbrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  A continuación, use [la propiedad Gaze](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obtener [spatialRay](/uwp/api/windows.perception.spatial.spatialray) que contiene la posición y la dirección de la mirada con los ojos. La propiedad Gaze a veces puede ser NULL, así que asegúrese de comprobarlo. Esto puede ocurrir si un usuario calibrado cierra temporalmente los ojos.

En el código siguiente se muestra cómo acceder al rayo de la mirada con los ojos.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>Reserva cuando el seguimiento de los ojos no está disponible

Como se mencionó en nuestros [documentos de](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)diseño de seguimiento ocular, tanto los diseñadores como los desarrolladores deben tener en cuenta las instancias en las que es posible que los datos de seguimiento ocular no estén disponibles.

Hay varias razones por las que los datos no están disponibles:
* Un usuario que no está calibrado
* Un usuario ha denegado a la aplicación el acceso a sus datos de seguimiento ocular.
* Interferencias temporales, como los sobresalimientos en la HoloLens visor o el vello que oculta los ojos del usuario. 

Aunque algunas de las API ya se han mencionado en este documento, en el siguiente se proporciona un resumen de cómo detectar que el seguimiento ocular está disponible como referencia rápida: 

* Compruebe que el sistema admite en absoluto el seguimiento ocular. Llame al método *siguiente:* [Windows. Perception.People.EyesPose.IsSupported()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Compruebe que el usuario está calibrado. Llame a la siguiente *propiedad*: [Windows. Perception.People.EyesPose.IsPlantbrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* Compruebe que el usuario ha dado permiso a la aplicación para usar sus datos de seguimiento ocular: Recupere el elemento _"GazeInputAccessStatus" actual._ Un ejemplo sobre cómo hacerlo se explica en Solicitud [de acceso a la entrada de mirada.](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input) 

También puede comprobar que los datos de seguimiento ocular no están obsoletos agregando un tiempo de espera entre las actualizaciones de datos de seguimiento ocular recibidas y, de lo contrario, la reserva a la mirada con la cabeza, como se describe a continuación.   
Visite nuestras [consideraciones de diseño de reserva](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) para obtener más información.

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Correlación de la mirada con otras entradas

En ocasiones, es posible que necesite un [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) que se corresponda con un evento en el pasado. Por ejemplo, si el usuario realiza una pulsación en el aire, es posible que la aplicación quiera saber lo que estaba mirando. Para ello, el uso de [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con el tiempo de fotograma previsto sería inexacto debido a la latencia entre el procesamiento de entrada del sistema y la hora de presentación. Además, si se usa la mirada con los ojos para la selección de destino, los ojos tienden a avanzar incluso antes de finalizar una acción de confirmación. Esto no es un problema para una simple pulsación en el aire, pero se vuelve más importante al combinar comandos de voz largos con movimientos rápidos de los ojos. Una manera de controlar este escenario es realizar una llamada adicional a  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)mediante una marca de tiempo histórica que se corresponde con el evento de entrada.  

Sin embargo, para la entrada que se enruta a través de SpatialInteractionManager, hay un método más sencillo. [SpatialInteractionSourceState tiene](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) su propia [función TryGetAtTimestamp.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) Llamar a que proporcionará un [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfectamente correlacionado sin la suposición. Para obtener más información sobre cómo trabajar con SpatialInteractionSourceStates, consulte la documentación De manos y controladores de movimiento [en DirectX.](hands-and-motion-controllers-in-directx.md)

<br>

## <a name="calibration"></a>Calibración

Para que el seguimiento de los ojos funcione con precisión, se requiere que cada usuario pase por una [calibración de usuario de seguimiento de los ojos.](/hololens/hololens-calibration) Esto permite al dispositivo ajustar el sistema para una experiencia de visualización más cómoda y de mayor calidad para el usuario y garantizar un seguimiento preciso de los ojos al mismo tiempo. Los desarrolladores no necesitan hacer nada por su parte para administrar la calibración del usuario. El sistema garantizará que se pida al usuario que calibra el dispositivo en las siguientes circunstancias:
* El usuario está usando el dispositivo por primera vez.
* El usuario ha optado previamente por no completar el proceso de calibración.
* El proceso de calibración no se realizó correctamente la última vez que el usuario usó el dispositivo.

Los desarrolladores deben asegurarse de proporcionar compatibilidad adecuada para los usuarios en los que es posible que los datos de seguimiento de los ojos no estén disponibles. Obtenga más información sobre las consideraciones para las soluciones de reserva en Seguimiento de los [ojos HoloLens 2](../../design/eye-tracking.md).

<br>

## <a name="see-also"></a>Consulte también

* [Calibración](/hololens/hololens-calibration)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
* [Mirada con los ojos en HoloLens 2](../../design/eye-tracking.md)
* [Modelo de entrada de mirada y confirmación](../../design/gaze-and-commit.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)