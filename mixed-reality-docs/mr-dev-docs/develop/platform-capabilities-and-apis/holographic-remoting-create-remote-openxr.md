---
title: Escritura de una aplicación remota de comunicación remota holográfica (OpenXR)
description: Obtenga información sobre cómo transmitir contenido remoto representado en un equipo remoto para HoloLens 2 aplicaciones de comunicación remota holográfica con OpenXR.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, NuGet
ms.openlocfilehash: 3fd210db1b179cbceff057e25bf451be0e7ca843
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184596"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Escritura de una aplicación remota de comunicación remota holográfica mediante la API openXR

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación remota para HoloLens 2 y Windows Mixed Reality con la [API de OpenXR.](../native/openxr.md) Las aplicaciones remotas **HoloLens (1.ª generación)** deben usar NuGet paquete **1.x.x**. Esto implica que las aplicaciones remotas escritas HoloLens 2 no son compatibles con HoloLens 1 y viceversa. La documentación de HoloLens 1 se puede encontrar [aquí.](add-holographic-remoting.md)

Las aplicaciones de comunicación remota holográfica pueden transmitir contenido representado de forma remota HoloLens 2 y Windows Mixed Reality cascos envolventes. También puede acceder a más recursos del sistema e integrar vistas inmersivas [remotas en](../../design/app-views.md) el software de pc de escritorio existente. Una aplicación remota recibe un flujo de datos de entrada de HoloLens 2, representa el contenido en una vista inmersiva virtual y transmite los fotogramas de contenido a HoloLens 2. La conexión se realiza mediante Wi-Fi estándar. La comunicación remota holográfica se agrega a una aplicación de escritorio o UWP a través de un NuGet paquete. Se requiere código adicional que controla la conexión y se representa en una vista inmersiva. Una conexión remota típica tendrá una latencia de hasta 50 ms. La aplicación player puede notificar la latencia en tiempo real.

Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de GitHub de ejemplos [de Holographic Remoting](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Requisitos previos

Un buen punto de partida es una aplicación de escritorio o UWP basada en OpenXR en funcionamiento. Para más información, [consulte Introducción a OpenXR.](../native/openxr-getting-started.md)

>[!IMPORTANT]
>Cualquier aplicación que use Holographic Remoting debe crearse para usar un apartamento [multiproceso.](/windows/win32/com/multithreaded-apartments) Se admite el [uso](/windows/win32/com/single-threaded-apartments) de un apartamento de un solo subproceso, pero dará lugar a un rendimiento poco óptimo y posiblemente a un entrecortado durante la reproducción. Cuando se usa [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) C++/WinRT, el valor predeterminado es un apartamento multiproceso.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obtener el paquete de NuGet holographic remoting

Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.
1. Abra el proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y **seleccione Administrar NuGet paquetes...**
3. En el panel que aparece, seleccione **Examinar y** busque "Comunicación remota holográfica".
4. Seleccione **Microsoft.Holographic.Remoting.OpenXr,** asegúrese de elegir la versión **2.x.x** más reciente y seleccione **Instalar.**
5. Si aparece **el cuadro de** diálogo Vista previa, seleccione **Aceptar.**
6. Seleccione **Acepto cuando** se abre el cuadro de diálogo del contrato de licencia.
7. Repita los pasos del 3 al 6 para los siguientes paquetes NuGet: OpenXR.Headers, OpenXR.Loader

>[!NOTE]
>La **versión 1.x.x** del paquete NuGet todavía está disponible para los desarrolladores que desean tener como destino HoloLens 1. Para obtener más información, vea Agregar comunicación remota holográfica [(HoloLens (1.ª generación)).](add-holographic-remoting.md)

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Selección del entorno de ejecución de OpenXR de Holographic Remoting

El primer paso que debe realizar en la aplicación remota es seleccionar el entorno de ejecución de OpenXR holographic remoting, que forma parte del paquete de NuGet Microsoft.Holographic.Remoting.OpenXr. Para ello, puede establecer la variable de entorno en la ruta de ```XR_RUNTIME_JSON``` acceso del RemotingXR.jsarchivo dentro de la aplicación. El cargador de OpenXR usa esta variable de entorno para no usar el entorno de ejecución de OpenXR predeterminado del sistema, sino redirigirlo al entorno de ejecución de OpenXR de comunicación remota holográfica. Cuando se usa el paquete de NuGet Microsoft.Holographic.Remoting.OpenXr, el RemotingXR.jsdel archivo se copia automáticamente durante la compilación en la carpeta de salida, la selección en tiempo de ejecución de OpenXR suele ser la siguiente.

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Creación de XrInstance con la extensión de comunicación remota holográfica

El primer paso que debe realizar una aplicación típica de OpenXR es seleccionar extensiones OpenXR y crear una instancia de XrInstance. La especificación principal de OpenXR no proporciona ninguna API específica de comunicación remota. Por ese motivo, Holographic Remoting presenta su propia extensión OpenXR denominada ```XR_MSFT_holographic_remoting``` . Asegúrese de que, al llamar a xrCreateInstance, ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` se incluye en XrInstanceCreateInfo.

>[!TIP]
>De forma predeterminada, el contenido representado de la aplicación solo se transmite al reproductor de Holographic Remoting que se ejecuta en un HoloLens 2 o en un Windows Mixed Reality cascos. Para mostrar también el contenido representado en el equipo remoto, a través de una cadena de intercambio de una ventana, por ejemplo, Holographic Remoting proporciona una segunda extensión OpenXR denominada ```XR_MSFT_holographic_remoting_frame_mirroring``` . Asegúrese de habilitar también esta extensión mediante ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` en caso de que desee usar esa funcionalidad.

>[!IMPORTANT]
>Para obtener información sobre la API de extensión OpenXR de holographic Remoting, consulte la especificación que se puede encontrar en el repositorio de GitHub de ejemplos de [Holographic Remoting](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). [](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)

## <a name="connect-to-the-device"></a>Conectar al dispositivo

Una vez que la aplicación remota ha creado XrInstance y ha consultado XrSystemId a través de xrGetSystem, se puede establecer una conexión con el dispositivo del reproductor.

>[!WARNING]
> El entorno de ejecución de OpenXR de comunicación remota holográfica solo puede proporcionar datos específicos del dispositivo, como configuraciones de vista o modos de combinación de entorno una vez establecida una conexión. ```xrEnumerateViewConfigurations```, , , y le darán valores predeterminados, que coinciden con lo que normalmente se obtiene si se conecta a un reproductor que se ejecuta en un HoloLens 2, antes de estar totalmente ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` ```xrEnumerateEnvironmentBlendModes``` ```xrGetSystemProperties``` conectado.
Se recomienda encarecidamente no llamar a estos métodos antes de establecer una conexión. La sugerencia se usa estos métodos después de que la XrSession se haya creado correctamente y el estado de sesión sea al menos XR_SESSION_STATE_READY.

Las propiedades generales, como la velocidad de bits máxima, el audio habilitado, el códec de vídeo o la resolución de secuencias de búfer de profundidad se pueden configurar a través ```xrRemotingSetContextPropertiesMSFT``` de como se muestra a continuación.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

La conexión se puede realizar de una de estas dos maneras.
1) La aplicación remota se conecta al reproductor que se ejecuta en el dispositivo.
2) El reproductor que se ejecuta en el dispositivo se conecta a la aplicación remota.

Para establecer una conexión desde la aplicación remota al dispositivo del reproductor, llame al método especificando el nombre de host y ```xrRemotingConnectMSFT``` el puerto a través de la estructura  ```XrRemotingConnectInfoMSFT``` . El puerto que usa holographic remoting Player es **8265.**

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

La escucha de conexiones entrantes en la aplicación remota se puede realizar llamando al ```xrRemotingListenMSFT``` método . Tanto el puerto de protocolo de enlace como el puerto de transporte se pueden especificar a través de la ```XrRemotingListenInfoMSFT``` estructura . El puerto de protocolo de enlace se usa para el protocolo de enlace inicial. A continuación, los datos se envían a través del puerto de transporte. De forma predeterminada, se usan **8265** y **8266.**

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

El estado de conexión debe desconectarse al llamar a ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` . Puede obtener el estado de conexión en cualquier momento después de crear una instancia de XrInstance y consultar el XrSystemId a través de ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Los estados de conexión disponibles son:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` Se ```xrRemotingListenMSFT``` debe llamar a o antes de intentar crear una XrSession a través de xrCreateSession. Si intenta crear una XrSession mientras el estado de conexión es , la creación de la sesión se realizará correctamente, pero el estado de sesión pasará inmediatamente a ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` XR_SESSION_STATE_LOSS_PENDING.

La implementación de Holographic Remoting ```xrCreateSession``` admite la espera a que se establezca una conexión. Puede llamar a ```xrRemotingConnectMSFT``` o inmediatamente seguido de una llamada a , que bloqueará y ```xrRemotingListenMSFT``` esperará a que se establezca una conexión. El tiempo de espera se fija en 10 segundos. Si se puede establecer una conexión dentro de este tiempo, la creación de XrSession se realizará correctamente y el estado de sesión pasará a XR_SESSION_STATE_READY. En caso de que no se pueda establecer ninguna conexión, la creación de la sesión también se realiza correctamente, pero pasa inmediatamente a XR_SESSION_STATE_LOSS_PENDING.

En general, el estado de conexión es pareja con el estado XrSession. Cualquier cambio en el estado de conexión también afecta al estado de sesión. Por ejemplo, si el estado de conexión cambia de al estado de sesión, también pasará a `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` XR_SESSION_STATE_LOSS_PENDING.

## <a name="handling-remoting-specific-events"></a>Control de eventos específicos de comunicación remota

El entorno de ejecución de OpenXR de comunicación remota holográfica expone tres eventos, que son importantes para supervisar el estado de una conexión.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: se desencadena cuando se ha establecido correctamente una conexión al dispositivo.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: se desencadena si se cierra una conexión establecida o no se pudo establecer una conexión.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: cuando se inicia la escucha de las conexiones entrantes.

Estos eventos se colocan en una cola y la aplicación remota debe leer de la cola con regularidad a través de ```xrPollEvent``` .

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a>Vista previa del contenido transmitido localmente

Para mostrar el mismo contenido en la aplicación remota que se envía al dispositivo, se ```XR_MSFT_holographic_remoting_frame_mirroring``` puede usar la extensión. Con esta extensión, puede enviar una textura a xrEndFrame mediante el que no está encadenado a ```XrRemotingFrameMirrorImageInfoMSFT``` XrFrameEndInfo como se muestra a continuación.

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

En el ejemplo anterior se usa una textura de cadena de intercambio DX11 y se presenta la ventana inmediatamente después de la llamada a xrEndFrame. El uso no está restringido a las texturas de la cadena de intercambio y no se requiere ninguna sincronización de GPU adicional. Para más información sobre el uso y las restricciones, consulte la [especificación de extensión](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Si la aplicación remota usa DX12, use XrRemotingFrameMirrorImageD3D12MSFT en lugar de XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Consulte también
* [Información general sobre la comunicación remota holográfica](holographic-remoting-overview.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Establecimiento de una conexión segura con Control remoto de holografías](holographic-remoting-secure-connection.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)