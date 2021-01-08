---
title: Escritura de un reproductor de control remoto de holografías personalizado
description: Cree una aplicación de comunicación remota de hologaphic personalizada para mostrar el contenido representado en una máquina remota a HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, Holographic Remoting, NuGet, manifiesto de la aplicación, contexto del reproductor, aplicación remota, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 23449749e709075e6530730e596bfcc9cd088c1e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006555"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Escritura de una aplicación de reproductor de control remoto de holografías personalizada

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación de reproductor personalizada para HoloLens 2. Los reproductores personalizados escritos para HoloLens 2 no son compatibles con las aplicaciones remotas escritas para HoloLens 1. Esto implica que ambas aplicaciones deben usar el paquete NuGet versión **2. x. x**.

Mediante la creación de una aplicación de reproductor de comunicación remota holográfica personalizada, puede crear una aplicación personalizada capaz de mostrar [vistas envolventes](../../design/app-views.md) desde en una máquina remota de HoloLens 2. Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Un reproductor remoto holográfica permite que la aplicación muestre el contenido holográfica [representado](rendering.md) en un equipo de escritorio o un dispositivo UWP como la Xbox One con acceso a más recursos del sistema. Una aplicación de reproductor de comunicación remota holográfica transmite datos de entrada a una aplicación remota de Holographic Remoting y recibe una vista envolvente como flujo de audio y vídeo. La conexión se realiza mediante Wi-Fi estándar. Para crear una aplicación de reproductor, use un paquete NuGet para agregar la comunicación remota holográfica a la aplicación de UWP. A continuación, escriba el código para controlar la conexión y mostrar una vista envolvente. 

## <a name="prerequisites"></a>Requisitos previos

Un buen punto de partida es una aplicación UWP basada en DirectX que ya tiene como destino la API de Windows Mixed Reality. Para obtener más información, vea [Introducción al desarrollo de DirectX](../native/directx-development-overview.md). Si no tiene una aplicación existente y desea comenzar desde el principio, la [plantilla de proyecto de C++ Holographic](../native/creating-a-holographic-directx-project.md) es un buen punto de partida.

>[!IMPORTANT]
>Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments). Se admite el uso de un apartamento de un [solo subproceso](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) , pero se producirá un rendimiento poco óptimo y posiblemente se produzca una intermitencia durante la reproducción. Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartamento multiproceso es el valor predeterminado.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obtención del paquete NuGet de Holographic Remoting

Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.
1. Abra el proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**
3. En el panel que aparece, seleccione **examinar** y busque "Holographic Remoting".
4. Seleccione **Microsoft. Holographic. Remoting**, asegúrese de elegir la versión **2. x. x** más reciente y seleccione **instalar**.
5. Si aparece el cuadro de diálogo **vista previa** , seleccione **Aceptar**.
6. Seleccione **acepto** cuando aparezca el cuadro de diálogo contrato de licencia.

>[!IMPORTANT]
><a name="idl"></a>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```En el paquete NuGet se incluye documentación detallada para la API expuesta por la comunicación remota holográfica.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificar el paquete. appxmanifest de la aplicación

Para que la aplicación tenga en cuenta los Microsoft.Holographic.AppRemoting.dll agregados por el paquete de NuGet, es necesario realizar los siguientes pasos en el proyecto:

1. En el Explorador de soluciones haga clic con el botón derecho en el archivo **Package. appxmanifest** y seleccione **abrir con.** ..
2. Seleccione **Editor XML (texto)** y haga clic en **Aceptar** .
3. Agregue las líneas siguientes al archivo y guárdela
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
## <a name="create-the-player-context"></a>Crear el contexto del reproductor

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
>Holographic Remoting funciona reemplazando el tiempo de ejecución de Windows Mixed Reality, que forma parte de Windows con un tiempo de ejecución específico de comunicación remota. Esto se realiza durante la creación del contexto del reproductor. Por ese motivo, cualquier llamada en cualquier API de Windows Mixed Reality antes de crear el contexto del reproductor puede producir un comportamiento inesperado. El enfoque recomendado es crear el contexto del reproductor tan pronto como sea posible antes de la interacción con cualquier API de realidad mixta. Nunca mezcle objetos creados o recuperados a través de cualquier API de realidad mixta de Windows antes de la llamada a ```PlayerContext::Create``` con objetos creados o recuperados después.

A continuación, se puede crear el HolographicSpace llamando a [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Conexión a la aplicación remota

Una vez que la aplicación de reproducción está lista para la representación de contenido, se puede establecer una conexión con la aplicación remota.

La conexión se puede establecer de una de las siguientes maneras:
1) La aplicación de reproducción que se ejecuta en HoloLens 2 se conecta a la aplicación remota.
2) La aplicación remota se conecta a la aplicación de reproductor que se ejecuta en HoloLens 2.

Para conectarse desde la aplicación de reproducción a la aplicación remota, llame al ```Connect``` método en el contexto del reproductor y especifique el nombre de host y el puerto. El puerto predeterminado es **8265**.

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
>Como con cualquier API de C++/WinRT, ```Connect``` puede producir una excepción WinRT:: hresult_error que debe controlarse.

La escucha de conexiones entrantes en la aplicación del reproductor puede realizarse mediante una llamada al ```Listen``` método. El puerto de enlace y el puerto de transporte se pueden especificar durante esta llamada. El puerto de enlace se usa para el protocolo de enlace inicial. A continuación, los datos se envían a través del puerto de transporte. De forma predeterminada, se usan el número de puerto **8265** y **8266** .

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


## <a name="handling-connection-related-events"></a>Controlar eventos relacionados con la conexión

```PlayerContext```Expone tres eventos para supervisar el estado de la conexión.
1) OnConnection: se desencadena cuando se ha establecido correctamente una conexión con la aplicación remota.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnection: se desencadena si se termina una conexión establecida o no se pudo establecer una conexión.
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

3) MyListener: cuando se inicia la escucha de conexiones entrantes.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Además, se puede consultar el estado de la conexión utilizando la ```ConnectionState``` propiedad en el contexto del reproductor.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Mostrar el marco representado de forma remota

Para mostrar el contenido representado de forma remota, llame a ```PlayerContext::BlitRemoteFrame``` mientras representa un [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame``` requiere que el búfer de reserva del HolographicFrame actual esté enlazado como destino de representación. El búfer de reserva se puede recibir desde [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) a través de la propiedad [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

Cuando se llama, ```BlitRemoteFrame``` copia el último fotograma recibido de la aplicación remota en el búfer de reserva del HolographicFrame. Además, se establece el conjunto de puntos de enfoque si la aplicación remota ha especificado un punto de enfoque durante la representación del marco remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` potencialmente sobrescribe el punto de enfoque para el marco actual. 
>- Para especificar un punto de enfoque de reserva, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes de ```PlayerContext::BlitRemoteFrame``` . 
>- Para sobrescribir el punto de enfoque remoto, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  después de ```PlayerContext::BlitRemoteFrame``` .

Si se ejecuta correctamente, ```BlitRemoteFrame``` devuelve ```BlitResult::Success_Color``` . En caso contrario, devuelve el motivo del error:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: No se pudo ejecutar porque no hay ningún marco remoto disponible.
- ```BlitResult::Failed_NoCamera```: No se pudo realizar porque no hay ninguna cámara presente.
- ```BlitResult::Failed_RemoteFrameTooOld```: No se pudo completar porque el marco remoto es demasiado antiguo (consulte la propiedad PlayerContext:: BlitRemoteFrameTimeout).

>[!IMPORTANT]
> A partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0) , es posible que un reproductor personalizado use la reproyección de profundidad mediante la comunicación remota de Holographic.

```BlitResult``` también puede devolver ```BlitResult::Success_Color_Depth``` en las siguientes condiciones:

- La aplicación remota ha confirmado un búfer de profundidad a través de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).
- La aplicación de reproductor personalizada ha enlazado un búfer de profundidad válido antes de llamar a ```BlitRemoteFrame``` .

Si se cumplen estas condiciones ```BlitRemoteFrame``` , la profundidad remota se convertirá en el búfer de profundidad local actualmente enlazado. Después, puede representar contenido local adicional, que tendrá una intersección de profundidad con el contenido representado remoto. Además, puede confirmar el búfer de profundidad local a través de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) en el reproductor personalizado para tener una reproyección de profundidad para el contenido representado de forma local y remota. Consulte [reproyección de profundidad](hologram-stability.md#reprojection) para obtener más información.

### <a name="projection-transform-mode"></a>Modo de transformación de proyección

Un problema, que se muestra al usar la reproyección de profundidad a través de la comunicación remota de Holographic, es que el contenido remoto se puede representar con una transformación de proyección diferente que el contenido local que representa directamente la aplicación de reproductor personalizada. Un caso de uso común es especificar valores diferentes para el plano Near y Far (a través de [HolographicCamera:: SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) y [HolographicCamera:: SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) en el lado del reproductor y en el lado remoto. En este caso, no está claro si la transformación de proyección en el lado del reproductor debe reflejar las distancias de plano Near/Far remoto o las locales.

A partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0) , puede controlar el modo de transformación de proyección a través de ```PlayerContext::ProjectionTransformConfig``` . Los valores admitidos son:

- ```Local``` - [HolographicCameraPose::P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) devuelve una transformación de proyección, que refleja las distancias de plano Near/Far establecidas por la aplicación de reproductor personalizada en el HolographicCamera.
- ```Remote``` -La transformación de proyección refleja las distancias de plano Near y Far especificadas por la aplicación remota.
- ```Merged``` -Las distancias de plano Near y Far desde la aplicación remota y la aplicación de reproductor personalizada se combinan. De forma predeterminada, esto se realiza tomando el mínimo de las distancias de plano cercanos y el máximo de las distancias de plano lejano. En caso de que se invierta el lado remoto o el local, por ejemplo, < Near, se voltean las distancias de plano Near/Far remoto.

## <a name="optional-set-blitremoteframetimeout"></a>Opcional: establecer BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9). 

La ```PlayerContext::BlitRemoteFrameTimeout``` propiedad especifica la cantidad de tiempo que se reutiliza un marco remoto si no se recibe un nuevo marco remoto. 

Un caso de uso común es habilitar el tiempo de espera de BlitRemoteFrame para mostrar una pantalla en blanco si no se recibe ningún fotograma nuevo durante un período de tiempo determinado. Cuando está habilitado, el tipo de valor devuelto del ```BlitRemoteFrame``` método también se puede utilizar para cambiar a un contenido de reserva representado localmente. 

Para habilitar el tiempo de espera, establezca el valor de la propiedad en una duración igual o mayor que 100 ms. Para deshabilitar el tiempo de espera, establezca la propiedad en cero Duration. Si el tiempo de espera está habilitado y no se recibe ningún marco remoto durante el tiempo establecido, BlitRemoteFrame producirá un error y devolverá ```Failed_RemoteFrameTooOld``` hasta que se reciba un nuevo marco remoto.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Opcional: obtener estadísticas sobre el último marco remoto

Para diagnosticar problemas de rendimiento o de red, se pueden recuperar estadísticas sobre el último marco remoto a través de la ```PlayerContext::LastFrameStatistics``` propiedad. Las estadísticas se actualizan durante la llamada a [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Para obtener más información, consulte la ```PlayerFrameStatistics``` documentación del ```Microsoft.Holographic.AppRemoting.idl``` [archivo](#idl).

## <a name="optional-custom-data-channels"></a>Opcional: canales de datos personalizados

Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida. Vea [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.

## <a name="see-also"></a>Consulte también
* [Escritura de una aplicación remota Holographic Remoting con las API de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting con las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Canales de datos personalizados de control remoto de holografías](holographic-remoting-custom-data-channels.md)
* [Establecimiento de una conexión segura con Control remoto de holografías](holographic-remoting-secure-connection.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
