---
title: Escritura de una aplicación remota de comunicación remota holográfica (WMR)
description: Aprenda a transmitir contenido remoto representado en un equipo remoto para HoloLens 2 aplicaciones de comunicación remota holográfica con HolographicSpace.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, NuGet
ms.openlocfilehash: 0c5943ff92ce797e39ec0d2d98c129fa91eb3f14
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184726"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>Escritura de una aplicación remota de comunicación remota holográfica con HolographicSpace API

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación remota para HoloLens 2 mediante [holographicSpace API](../native/getting-a-holographicspace.md). Las aplicaciones remotas **HoloLens (1.ª generación)** deben usar NuGet versión **1.x.x del paquete**. Esto implica que las aplicaciones remotas escritas HoloLens 2 no son compatibles con HoloLens 1 y viceversa. La documentación de HoloLens 1 se puede encontrar [aquí.](add-holographic-remoting.md)

Las aplicaciones de comunicación remota holográfica pueden transmitir contenido representado de forma remota a HoloLens 2 y Windows Mixed Reality cascos envolventes. También puede acceder a más recursos del sistema e integrar vistas inmersivas [remotas en](../../design/app-views.md) el software de pc de escritorio existente. Una aplicación remota recibe un flujo de datos de entrada de HoloLens 2, representa el contenido en una vista inmersiva virtual y transmite los fotogramas de contenido a HoloLens 2. La conexión se realiza mediante Wi-Fi estándar. La comunicación remota holográfica se agrega a una aplicación de escritorio o para UWP a través de un NuGet paquete. Se requiere código adicional que controla la conexión y se representa en una vista inmersiva. Una conexión remota típica tendrá una latencia de hasta 50 ms. La aplicación player puede notificar la latencia en tiempo real.

Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de GitHub de ejemplos [de Holographic Remoting](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Requisitos previos

Un buen punto de partida es una aplicación de escritorio o UWP basada en DirectX en funcionamiento, que tiene como destino [holographicSpace API.](../native/getting-a-holographicspace.md) Para más información, [consulte Introducción al desarrollo de DirectX.](../native/directx-development-overview.md) La [plantilla de proyecto holográfico de C++](../native/creating-a-holographic-directx-project.md) es un buen punto de partida.

>[!IMPORTANT]
>Cualquier aplicación que use Holographic Remoting debe crearse para usar un apartamento [multiproceso.](/windows/win32/com/multithreaded-apartments) Se admite el [uso](/windows/win32/com/single-threaded-apartments) de un apartamento de un solo subproceso, pero dará lugar a un rendimiento poco óptimo y posiblemente a un entrecortado durante la reproducción. Cuando se usa [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) C++/WinRT, el valor predeterminado es un apartamento multiproceso.



## <a name="get-the-holographic-remoting-nuget-package"></a>Obtener el paquete de NuGet holographic remoting

Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.
1. Abra el proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y **seleccione Administrar NuGet paquetes...**
3. En el panel que aparece, seleccione **Examinar y** busque "Comunicación remota holográfica".
4. Seleccione **Microsoft.Holographic.Remoting,** asegúrese de elegir la versión **2.x.x** más reciente y seleccione **Instalar.**
5. Si aparece **el cuadro de** diálogo Vista previa, seleccione **Aceptar.**
6. Seleccione **Acepto cuando** se abre el cuadro de diálogo del contrato de licencia.

>[!NOTE]
>La **versión 1.x.x** del paquete NuGet está disponible para los desarrolladores que desean tener como destino HoloLens 1. Para obtener más información, vea Agregar comunicación remota holográfica [(HoloLens (1.ª generación)).](add-holographic-remoting.md)

## <a name="create-the-remote-context"></a>Creación del contexto remoto

Como primer paso, la aplicación debe crear un contexto remoto.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>La comunicación remota holográfica funciona reemplazando el runtime Windows Mixed Reality que forma parte de Windows por un tiempo de ejecución específico de comunicación remota. Esto se hace durante la creación del contexto remoto. Por ese motivo, cualquier llamada a cualquier API Windows Mixed Reality antes de crear el contexto remoto puede dar lugar a un comportamiento inesperado. El enfoque recomendado es crear el contexto remoto lo antes posible antes de la interacción con Mixed Reality API. Nunca mezcle objetos creados o recuperados a través de Windows Mixed Reality API antes de la llamada a CreateRemoteContext con objetos creados o recuperados posteriormente.

A continuación, debe crearse el espacio holográfico. No es necesario especificar coreWindow. Las aplicaciones de escritorio que no tienen coreWindow solo pueden pasar un ```nullptr``` .

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Conectar al dispositivo

Cuando la aplicación remota está lista para representar contenido, se puede establecer una conexión con el dispositivo del reproductor.

La conexión se puede realizar de una de estas dos maneras.
1) La aplicación remota se conecta al reproductor que se ejecuta en el dispositivo.
2) El reproductor que se ejecuta en el dispositivo se conecta a la aplicación remota.

Para establecer una conexión desde la aplicación remota al dispositivo del reproductor, llame al método en el contexto remoto ```Connect``` especificando el nombre de host y el puerto. El puerto que usa holographic remoting Player es **8265.**

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Al igual que con cualquier API de C++/WinRT, podría producirse una ```Connect``` excepción winrt::hresult_error que debe controlarse.

>[!TIP]
>Para evitar el uso de la proyección del lenguaje [C++/WinRT,](/windows/uwp/cpp-and-winrt-apis/) se puede incluir el archivo ubicado dentro de ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` holographic remoting NuGet paquete. Contiene declaraciones de las interfaces COM subyacentes. Sin embargo, se recomienda usar C++/WinRT.

La escucha de conexiones entrantes en la aplicación remota se puede realizar llamando al ```Listen``` método . Tanto el puerto de protocolo de enlace como el puerto de transporte se pueden especificar durante esta llamada. El puerto de protocolo de enlace se usa para el protocolo de enlace inicial. A continuación, los datos se envían a través del puerto de transporte. De forma predeterminada, se usan **8265** y **8266.**

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Dentro del paquete NuGet contiene documentación detallada de ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` la API expuesta por Holographic Remoting.

## <a name="handling-remoting-specific-events"></a>Control de eventos específicos de comunicación remota

El contexto remoto expone tres eventos, que son importantes para supervisar el estado de una conexión.
1) OnConnected: se desencadena cuando se ha establecido correctamente una conexión al dispositivo.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected: se desencadena si se cierra una conexión establecida o no se pudo establecer una conexión.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening: cuando se inicia la escucha de las conexiones entrantes.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Además, el estado de conexión se puede consultar mediante la ```ConnectionState``` propiedad en el contexto remoto.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Control de eventos de voz

Con la interfaz de voz remota es posible registrar desencadenadores de voz con HoloLens 2 y hacer que se desencadene de forma remota a la aplicación remota.

Este miembro adicional es necesario para realizar un seguimiento del estado de la voz remota.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

En primer lugar, es necesario recuperar la interfaz de voz remota.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

Con un método auxiliar asincrónico, puede inicializar la voz remota. Esto debe hacerse de forma asincrónica, ya que la inicialización puede tardar una cantidad considerable de tiempo. [Las operaciones de simultaneidad y asincrónicas con C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) explican cómo crear funciones asincrónicas con C++/WinRT.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

Hay dos maneras de especificar las frases que se van a reconocer.
1) Especificación dentro de un archivo xml de gramática de voz. Consulte [How to create a basic XML Grammar (Cómo](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) crear una gramática XML básica) para obtener más información.
2) Especifique pasándolos dentro del vector de diccionario a ```ApplyParameters``` .

Dentro de la devolución de llamada OnRecognizedSpeech, se pueden procesar los eventos de voz:

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>Vista previa del contenido transmitido localmente

Para mostrar el mismo contenido en la aplicación remota que se envía al dispositivo, se puede usar el evento ```OnSendFrame``` del contexto remoto. El evento se desencadena cada vez que la biblioteca de comunicación ```OnSendFrame``` remota holográfica envía el fotograma actual al dispositivo remoto. Este es el momento ideal para tomar el contenido y también para abrirlo en la ventana de escritorio o UWP.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>Reproducción de profundidad

A partir de la [versión 2.1.0,](holographic-remoting-version-history.md#v2.1.0)Holographic Remoting admite [la proyección de profundidad.](hologram-stability.md#reprojection) Esto requiere que tanto el búfer de color como el búfer de profundidad se transmita desde la aplicación remota al HoloLens 2. De forma predeterminada, el streaming de búfer de profundidad está habilitado y configurado para usar la mitad de la resolución del búfer de color. Esto se puede cambiar como se muestra a continuación:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Tenga en cuenta que, si no se deben usar los valores predeterminados, se ```ConfigureDepthVideoStream``` debe llamar a antes de establecer una conexión con el HoloLens 2. El mejor lugar es justo después de haber creado el contexto remoto. Los valores posibles para DepthBufferStreamResolution son:

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Deshabilitado (se agrega con la [versión 2.1.3](holographic-remoting-version-history.md#v2.1.3) y, si se usa, no se crea ninguna secuencia de vídeo de profundidad adicional)

Tenga en cuenta que el uso de un búfer de profundidad de resolución completa también afecta a los requisitos de ancho de banda y debe tenerse en cuenta en el valor de ancho de banda máximo que proporcione a ```CreateRemoteContext``` .

Además de configurar la resolución, también tiene que confirmar un búfer de profundidad a través de [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

Para comprobar si la reproducción de profundidad funciona correctamente HoloLens 2, puede habilitar un visualizador de profundidad a través del Portal de dispositivos. Consulte [Verifying Depth is Set Correctly (Comprobar que la profundidad está establecida correctamente)](hologram-stability.md#verifying-depth-is-set-correctly) para obtener más información.

## <a name="optional-custom-data-channels"></a>Opcional: canales de datos personalizados

Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida. Consulte [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.

## <a name="see-also"></a>Consulte también
* [Información general sobre la comunicación remota holográfica](holographic-remoting-overview.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Canales de datos personalizados de control remoto de holografías](holographic-remoting-custom-data-channels.md)
* [Establecimiento de una conexión segura con Control remoto de holografías](holographic-remoting-secure-connection.md)
* [Solución de problemas y limitaciones de Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)