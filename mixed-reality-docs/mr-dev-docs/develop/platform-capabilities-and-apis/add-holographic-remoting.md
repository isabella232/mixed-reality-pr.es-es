---
title: Agregar comunicación remota holográfica
description: Aprenda a instalar, configurar y usar Holographic Remoting para representar hologramas en un dispositivo HoloLens a través de la red.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, comunicación remota holográfica, representación remota, representación en red, HoloLens, hologramas remotos, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual
ms.openlocfilehash: ecfc49477e202b08303160e54ce986577a9d79eb387dc1edb1bc33c63644615f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198861"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>Agregar comunicación remota holográfica (HoloLens (primera generación))

>[!IMPORTANT]
> En este documento se describe la creación de una aplicación host para HoloLens 1. La aplicación host **HoloLens (1.ª generación)** debe usar NuGet versión **1.x.x del paquete**. Esto implica que las aplicaciones host escritas para HoloLens 1 no son compatibles con HoloLens 2 y viceversa.

## <a name="hololens-2"></a>HoloLens 2

HoloLens desarrolladores que usan Holographic Remoting tendrán que actualizar sus aplicaciones para que sean compatibles con HoloLens 2. Esto requiere una nueva versión del paquete NuGet comunicación remota holográfica. Asegúrese de usar la versión 2.0.0.0 o posterior del paquete holographic remoting NuGet al conectarse al reproductor de comunicación remota holográfica en HoloLens 2 o se producirá un error en la conexión.

>[!NOTE]
> Puede encontrar instrucciones específicas de HoloLens 2 [aquí.](holographic-remoting-create-remote-wmr.md)


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Adición de comunicación remota holográfica al escritorio o a la aplicación para UWP

En esta página se describe cómo agregar Holographic Remoting a una aplicación de escritorio o UWP.

La comunicación remota holográfica permite a la aplicación dirigirse a HoloLens con contenido holográfico hospedado en un equipo de escritorio o en un dispositivo para UWP, como el Xbox One. También tiene acceso a más recursos del sistema, lo que permite integrar vistas inmersivas [remotas](../../design/app-views.md) en el software de pc de escritorio existente. Una aplicación host de comunicación remota recibe un flujo de datos de entrada de un HoloLens, representa el contenido en una vista inmersiva virtual y transmite los fotogramas de contenido a HoloLens. La conexión se realiza mediante Wi-Fi estándar. Para usar la comunicación remota, use un paquete NuGet para agregar comunicación remota holográfica a la aplicación de escritorio o UWP y, a continuación, escriba código para controlar la conexión y representar una vista inmersiva. Las bibliotecas auxiliares se incluyen en el ejemplo de código que simplifican la tarea de controlar la conexión del dispositivo.

Una conexión remota típica tendrá una latencia de hasta 50 ms. La aplicación player puede notificar la latencia en tiempo real.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de C++17 compatible con C++/WinRT, como se usa en la plantilla de proyecto holográfico de [C++.](../native/creating-a-holographic-directx-project.md)  Los conceptos son equivalentes para un proyecto de C++/WinRT, aunque deberá traducir el código.

### <a name="get-the-remoting-nuget-packages"></a>Obtener la comunicación remota NuGet paquetes

Siga estos pasos para obtener el paquete NuGet para la comunicación remota holográfica y agregue una referencia del proyecto:
1. Vaya al proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y seleccione **Administrar NuGet paquetes...**
3. En el panel que aparece, seleccione **Examinar** y busque "Comunicación remota holográfica".
4. Seleccione **Microsoft.Holographic.Remoting** e instale **.**
5. Si aparece **el cuadro de** diálogo Vista previa, seleccione **Aceptar.**
6. Seleccione **Acepto cuando aparezca el** cuadro de diálogo del contrato de licencia.

### <a name="create-the-holographicstreamerhelpers"></a>Creación de HolographicStreamerHelpers

En primer lugar, es necesario agregar una instancia de HolographicStreamerHelpers a la clase que controlará la comunicación remota.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

También tendrá que realizar un seguimiento del estado de conexión. Si desea representar la vista previa, debe tener una textura en la que copiarla. También necesita algunas cosas como un bloqueo de estado de conexión, alguna manera de almacenar la dirección IP de HoloLens, y así sucesivamente.

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inicialice HolographicStreamerHelpers y conéctese a HoloLens

Para conectarse a un HoloLens, cree una instancia de HolographicStreamerHelpers y conéctese a la dirección IP de destino. Deberá establecer el tamaño del fotograma de vídeo para que coincida con el ancho y el alto de la pantalla HoloLens, ya que la biblioteca de comunicación remota holográfica espera que las resoluciones del codificador y el descodificador coincidan exactamente.

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

La conexión del dispositivo es asincrónica. La aplicación debe proporcionar controladores de eventos para los eventos de conexión, desconexión y envío de fotogramas.

El evento OnConnected puede actualizar la interfaz de usuario, iniciar la representación, y así sucesivamente. En nuestro ejemplo de código de escritorio, actualizamos el título de la ventana con un mensaje "conectado".

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

El evento OnDisconnected puede controlar la reconexión, las actualizaciones de la interfaz de usuario, y así sucesivamente. En este ejemplo, se vuelve a conectar si hay un error transitorio.

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Cuando el componente de comunicación remota está listo para enviar un fotograma, la aplicación tiene la oportunidad de realizar una copia de él en SendFrameEvent. Aquí, copiamos el marco en una cadena de intercambio para que podamos mostrarlo en una ventana de vista previa.

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>Representación de contenido holográfico

Para representar contenido mediante comunicación remota, configuras un IFrameworkView virtual en tu aplicación de escritorio o UWP y procesas fotogramas holográficos desde la comunicación remota. Todas las Windows holographic API se usan de la misma manera en esta vista, pero se configura de forma ligeramente diferente.

En lugar de crearlos usted mismo, el espacio holográfico y los componentes de voz proceden de la clase HolographicRemotingHelpers:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

En lugar de usar un bucle de actualización en un método Run, se proporcionan actualizaciones de tics desde el bucle principal de la aplicación de escritorio o UWP. Esto permite que la aplicación de escritorio o UWP permanezca en el control del procesamiento de mensajes.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

El método Tick() de la vista holográfica de la aplicación completa una iteración del bucle update, draw, present.

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

El bucle de actualización, representación y presentación de la vista de la aplicación holográfica es exactamente igual que cuando se ejecuta en HoloLens, salvo que tiene acceso a una cantidad mucho mayor de recursos del sistema en el equipo de escritorio. Puede representar muchos más triángulos, tener más pases de dibujo, hacer más física y usar procesos x64 para cargar contenido que requiere más de 2 GB de RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Desconectar y finalizar la sesión remota

Para desconectarse, por ejemplo, cuando el usuario hace clic en un botón de interfaz de usuario para desconectarse, llame a Disconnect() en HolographicStreamerHelpers y, a continuación, suelte el objeto.

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>Obtener el reproductor de comunicación remota

El Windows de comunicación remota holográfica se ofrece en la tienda de aplicaciones Windows como punto de conexión para conectarse a las aplicaciones host de comunicación remota. Para obtener el Windows de comunicación remota holográfica, visite la tienda de aplicaciones Windows desde su HoloLens, busque Comunicación remota y descargue la aplicación. El reproductor de comunicación remota incluye una característica para mostrar estadísticas en pantalla, que puede ser útil al depurar aplicaciones host de comunicación remota.

## <a name="notes-and-resources"></a>Notas y recursos

La vista de la aplicación holográfica necesitará una manera de proporcionar a la aplicación el dispositivo Direct3D, que debe usarse para inicializar el espacio holográfico. La aplicación debe usar este dispositivo Direct3D para copiar y mostrar el marco de vista previa.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Ejemplo de código:** Hay [](https://github.com/Microsoft/HoloLensCompanionKit) disponible un ejemplo completo de código de Comunicación remota holográfica, que incluye una vista de aplicación holográfica que es compatible con los proyectos de host de comunicación remota y comunicación remota para el escritorio Win32, DirectX para UWP y UWP con XAML. 

**Nota de depuración:** La biblioteca de comunicación remota holográfica puede producir excepciones de primera oportunidad. Estas excepciones pueden estar visibles en las sesiones de depuración, dependiendo de la Visual Studio de excepciones que están activas en ese momento. La biblioteca de comunicación remota holográfica detecta internamente estas excepciones y se pueden omitir.
