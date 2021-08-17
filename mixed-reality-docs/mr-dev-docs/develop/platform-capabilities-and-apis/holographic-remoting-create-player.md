---
title: Escribir un reproductor personalizado de Holographic Remoting (C++)
description: Cree una aplicación de comunicación remota de Hologagalc personalizada para mostrar el contenido representado en un equipo remoto en el HoloLens 2.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 7/30/2021
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, NuGet, manifiesto de aplicación, contexto del reproductor, aplicación remota, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 37388dc9cbf70cb7fccd742fb45e1e29c0ceb971
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184736"
---
# <a name="writing-a-custom-holographic-remoting-player-app-c"></a>Escritura de una aplicación personalizada del reproductor de Holographic Remoting (C++)

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación de reproductor personalizado para HoloLens 2. Los reproductores personalizados escritos HoloLens 2 no son compatibles con las aplicaciones remotas escritas para HoloLens 1. Esto implica que ambas aplicaciones deben usar NuGet versión **2.x.x del paquete**.

Al crear una aplicación personalizada del reproductor de Holographic Remoting, puede crear una aplicación personalizada capaz de mostrar vistas inmersivas desde en un equipo remoto en el HoloLens 2. [](../../design/app-views.md) Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de [Holographic Remoting](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Un reproductor de Comunicación remota holográfica [](rendering.md) permite que la aplicación muestre contenido holográfico representado en un equipo de escritorio o dispositivo UWP, como Xbox One con acceso a más recursos del sistema. Una aplicación del reproductor de Holographic Remoting transmite los datos de entrada a una aplicación remota de Holographic Remoting y recibe una vista inmersiva como secuencia de audio y vídeo. La conexión se realiza mediante Wi-Fi estándar. Para crear una aplicación de reproductor, usa un NuGet para agregar La comunicación remota holográfica a la aplicación para UWP. A continuación, escriba código para controlar la conexión y mostrar una vista inmersiva. 

## <a name="prerequisites"></a>Requisitos previos

Un buen punto de partida es una aplicación para UWP basada en DirectX en funcionamiento que ya tiene como destino Windows Mixed Reality API. Para más información, [consulte Introducción al desarrollo de DirectX.](../native/directx-development-overview.md) Si no tiene una aplicación existente y desea empezar desde cero, la plantilla de proyecto holográfico de [C++](../native/creating-a-holographic-directx-project.md) es un buen punto de partida.

>[!IMPORTANT]
>Cualquier aplicación que use Holographic Remoting debe crearse para usar un apartamento [multiproceso.](/windows/win32/com/multithreaded-apartments) Se admite el uso de [un](/windows/win32/com/single-threaded-apartments) apartamento de un solo subproceso, pero dará lugar a un rendimiento poco óptimo y posiblemente a un desorden durante la reproducción. Cuando se usa [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) C++/WinRT, el valor predeterminado es un apartamento multiproceso.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obtener el paquete de NuGet holographic remoting

Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.
1. Abra el proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y seleccione **Administrar NuGet paquetes...**
3. En el panel que aparece, seleccione **Examinar y** busque "Holographic Remoting".
4. Seleccione **Microsoft.Holographic.Remoting,** asegúrese de elegir la versión **2.x.x** más reciente y seleccione **Instalar.**
5. Si aparece **el cuadro de** diálogo Vista previa, seleccione **Aceptar.**
6. Seleccione **Acepto cuando aparezca** el cuadro de diálogo del contrato de licencia.

>[!IMPORTANT]
><a name="idl"></a>Dentro del paquete NuGet contiene documentación detallada de ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` la API expuesta por Holographic Remoting.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificación del archivo Package.appxmanifest de la aplicación

Para que la aplicación tenga en cuenta los Microsoft.Holographic.AppRemoting.dll agregados por el paquete NuGet, es necesario realizar los pasos siguientes en el proyecto:

1. En la Explorador de soluciones haga clic con el botón derecho en el **archivo Package.appxmanifest** y **seleccione Abrir con...**
2. Seleccione **Editor XML (texto)** y seleccione **Aceptar.**
3. Agregue las siguientes líneas al archivo y guárdelo.
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Creación del contexto del reproductor

Como primer paso, la aplicación debe crear un contexto de reproductor.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>La comunicación remota holográfica funciona reemplazando el tiempo de ejecución Windows Mixed Reality que forma parte de Windows por un tiempo de ejecución específico de comunicación remota. Esto se hace durante la creación del contexto del reproductor. Por ese motivo, cualquier llamada a cualquier API Windows Mixed Reality antes de crear el contexto del reproductor puede dar lugar a un comportamiento inesperado. El enfoque recomendado es crear el contexto del reproductor lo antes posible antes de la interacción con cualquier API Mixed Reality aplicación. No mezcle nunca los objetos creados o recuperados a través de Windows Mixed Reality API antes de llamar a con objetos ```PlayerContext::Create``` creados o recuperados posteriormente.

A continuación, se puede crear holographicSpace mediante una [llamada a HolographicSpace.CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Conectar a la aplicación remota

Una vez que la aplicación de reproductor está lista para representar contenido, se puede establecer una conexión a la aplicación remota.

La conexión se puede establecer de una de las maneras siguientes:
1) La aplicación de reproductor que se HoloLens 2 se conecta a la aplicación remota.
2) La aplicación remota se conecta a la aplicación de reproductor que se ejecuta en HoloLens 2.

Para conectarse desde la aplicación de reproductor a la aplicación remota, llame al método en el contexto del reproductor ```Connect``` especificando el nombre de host y el puerto. El puerto predeterminado es **8265.**

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Al igual que con cualquier API de C++/WinRT, podría producirse una ```Connect``` excepción winrt::hresult_error que debe controlarse.

La escucha de las conexiones entrantes en la aplicación de reproductor se puede realizar mediante una llamada al ```Listen``` método . Tanto el puerto de protocolo de enlace como el puerto de transporte se pueden especificar durante esta llamada. El puerto de protocolo de enlace se usa para el protocolo de enlace inicial. A continuación, los datos se envían a través del puerto de transporte. De forma predeterminada se usan **los números de puerto 8265** y **8266.**

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Control de eventos relacionados con la conexión

expone ```PlayerContext``` tres eventos para supervisar el estado de la conexión.
1) OnConnected: se desencadena cuando se ha establecido correctamente una conexión a la aplicación remota.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: se desencadena si se termina una conexión establecida o no se pudo establecer una conexión.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>Los ```ConnectionFailureReason``` valores posibles se documentan en el ```Microsoft.Holographic.AppRemoting.idl``` [archivo](#idl).

3) OnListening: cuando se inicia la escucha de conexiones entrantes.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Además, se puede consultar el estado de conexión mediante la ```ConnectionState``` propiedad en el contexto del reproductor.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Mostrar el marco representado de forma remota

Para mostrar el contenido representado de forma remota, llame ```PlayerContext::BlitRemoteFrame``` a mientras representa un elemento [HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe) 

```BlitRemoteFrame``` requiere que el búfer de reserva para el holographicFrame actual esté enlazado como destino de representación. El búfer de reserva se puede recibir de [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) a través de la [propiedad Direct3D11BackBuffer.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)

Cuando se le ```BlitRemoteFrame``` llama, copia el fotograma recibido más reciente de la aplicación remota en el BackBuffer de HolographicFrame. Además, se establece el conjunto de puntos de enfoque, si la aplicación remota ha especificado un punto de enfoque durante la representación del marco remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` sobrescribe potencialmente el punto de enfoque del marco actual. 
>- Para especificar un punto de enfoque de reserva, llame a [HolographicCameraRenderingParameters::SetFocusPoint antes](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) de ```PlayerContext::BlitRemoteFrame``` . 
>- Para sobrescribir el punto de enfoque remoto, llame [a HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  después de ```PlayerContext::BlitRemoteFrame``` .

Si se ejecuta ```BlitRemoteFrame``` correctamente, devuelve ```BlitResult::Success_Color``` . De lo contrario, devuelve el motivo del error:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: error porque no hay ningún marco remoto disponible.
- ```BlitResult::Failed_NoCamera```: error porque no hay ninguna cámara presente.
- ```BlitResult::Failed_RemoteFrameTooOld```: error porque el marco remoto es demasiado antiguo (vea PlayerContext::BlitRemoteFrameTimeout property).

>[!IMPORTANT]
> A partir de [la versión 2.1.0,](holographic-remoting-version-history.md#v2.1.0) es posible con un reproductor personalizado usar la reproducción de profundidad a través de Holographic Remoting.

```BlitResult``` también puede devolver ```BlitResult::Success_Color_Depth``` en las siguientes condiciones:

- La aplicación remota ha confirmado un búfer de profundidad a [través de HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).
- La aplicación de reproductor personalizado ha enlazado un búfer de profundidad válido antes de llamar a ```BlitRemoteFrame``` .

Si se cumplen estas condiciones, la profundidad remota se divide en el búfer de profundidad ```BlitRemoteFrame``` local enlazado actualmente. A continuación, puede representar contenido local adicional, que tendrá una intersección de profundidad con el contenido representado de forma remota. Además, puede confirmar el búfer de profundidad local a través de [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) en el reproductor personalizado para que se vuelva a proyectar la profundidad del contenido representado local y remoto. Consulte [Depth Reprojection (Reproyecto de](hologram-stability.md#reprojection) profundidad) para obtener más información.

### <a name="projection-transform-mode"></a>Modo de transformación de proyección

Un problema, que se produce al usar la reproducción de profundidad a través de la comunicación remota holográfica, es que el contenido remoto se puede representar con una transformación de proyección diferente al contenido local representado directamente por la aplicación de reproductor personalizada. Un caso de uso común es especificar valores diferentes para el plano cercano y lejano (a través de [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) y [HolographicCamera::SetFarPlaneDistance)](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)en el lado del reproductor y en el lado remoto. En este caso, no está claro si la transformación de proyección en el lado del jugador debe reflejar las distancias remotas del plano cercano o lejano o las locales.

A partir de la [versión 2.1.0,](holographic-remoting-version-history.md#v2.1.0) puede controlar el modo de transformación de proyección a través de ```PlayerContext::ProjectionTransformConfig``` . Los valores admitidos son:

- ```Local``` - [HolographicCameraPose::P rojectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) devuelve una transformación de proyección, que refleja las distancias de plano cercanas o lejanas establecidas por la aplicación de reproductor personalizado en HolographicCamera.
- ```Remote``` - La transformación de proyección refleja las distancias de plano cercanas o lejanas especificadas por la aplicación remota.
- ```Merged``` - Se combinan las distancias de plano cercano o lejano desde la aplicación remota y la aplicación de reproductor personalizado. De forma predeterminada, esto se realiza tomando el mínimo de las distancias del plano cercano y el máximo de las distancias del plano lejano. En caso de que se invierta el lado remoto o local, por ejemplo, < cerca, se voltearán las distancias remotas del plano cercano o lejano.

## <a name="optional-set-blitremoteframetimeout"></a>Opcional: Establecer BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout```se admite a partir de la [versión 2.0.9.](holographic-remoting-version-history.md#v2.0.9) 

La propiedad especifica la cantidad de tiempo que se reutiliza un marco remoto ```PlayerContext::BlitRemoteFrameTimeout``` si no se recibe ningún fotograma remoto nuevo. 

Un caso de uso común es permitir que el tiempo de espera de BlitRemoteFrame muestre una pantalla en blanco si no se recibe ningún fotograma nuevo durante un período de tiempo determinado. Cuando se habilita, el tipo de valor devuelto del método también se puede usar para cambiar a un contenido de reserva ```BlitRemoteFrame``` representado localmente. 

Para habilitar el tiempo de espera, establezca el valor de propiedad en una duración igual o superior a 100 ms. Para deshabilitar el tiempo de espera, establezca la propiedad en duración cero. Si el tiempo de espera está habilitado y no se recibe ningún fotograma remoto durante el tiempo establecido, BlitRemoteFrame producirá un error y volverá hasta que se reciba ```Failed_RemoteFrameTooOld``` un nuevo fotograma remoto.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Opcional: Obtener estadísticas sobre el último fotograma remoto

Para diagnosticar problemas de rendimiento o de red, las estadísticas sobre el último fotograma remoto se pueden recuperar a través de la ```PlayerContext::LastFrameStatistics``` propiedad . Las estadísticas se actualizan durante la llamada a [HolographicFrame::P resentUsingCurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Para obtener más información, vea ```PlayerFrameStatistics``` la documentación del ```Microsoft.Holographic.AppRemoting.idl``` [archivo](#idl).

## <a name="optional-custom-data-channels"></a>Opcional: canales de datos personalizados

Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida. Consulte [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.

## <a name="see-also"></a>Consulte también
* [Información general sobre la comunicación remota holográfica](holographic-remoting-overview.md)
* [Escritura de una aplicación remota de Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting mediante las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Canales de datos personalizados de control remoto de holografías](holographic-remoting-custom-data-channels.md)
* [Establecimiento de una conexión segura con Control remoto de holografías](holographic-remoting-secure-connection.md)
* [Solución de problemas y limitaciones de Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)