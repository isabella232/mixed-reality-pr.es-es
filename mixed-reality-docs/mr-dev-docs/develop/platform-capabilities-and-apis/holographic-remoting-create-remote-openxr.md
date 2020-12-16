---
title: Escritura de una aplicación remota holográfica Remoting (OpenXR)
description: Al crear una aplicación remota Holographic Remoting, el contenido remoto, que se representa en un equipo remoto, se puede transmitir a HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, NuGet
ms.openlocfilehash: 202f2108ade9998d25d87dee20d4bd456da0a118
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530421"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Escritura de una aplicación remota de Holographic Remoting mediante la API de OpenXR

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación remota para los auriculares HoloLens 2 y Windows Mixed Reality mediante la [API de OpenXR](../native/openxr.md). Las aplicaciones remotas para **HoloLens (1ª generación)** deben usar el paquete NuGet versión **1. x. x**. Esto implica que las aplicaciones remotas escritas para HoloLens 2 no son compatibles con HoloLens 1 y viceversa. La documentación de HoloLens 1 se puede encontrar [aquí](add-holographic-remoting.md).

Las aplicaciones de acceso remoto holográfica pueden transmitir contenido representado de forma remota a los auriculares HoloLens 2 y Windows Mixed Reality. También puede tener acceso a más recursos del sistema e integrar [vistas de envolvente](../../design/app-views.md) remotas en el software de PC de escritorio existente. Una aplicación remota recibe un flujo de datos de entrada de HoloLens 2, representa el contenido en una vista envolvente virtual y vuelve a transmitir los fotogramas de contenido a HoloLens 2. La conexión se realiza mediante Wi-Fi estándar. Holographic Remoting se agrega a una aplicación de escritorio o UWP a través de un paquete NuGet. Se requiere código adicional que controla la conexión y se representa en una vista envolvente. Una conexión remota típica tendrá un mínimo de 50 ms de latencia. La aplicación de reproducción puede informar de la latencia en tiempo real.

Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Requisitos previos

Un buen punto de partida es una aplicación de escritorio o UWP basada en OpenXR en funcionamiento. Para obtener más información, consulte [Introducción a OpenXR](../native/openxr-getting-started.md).

>[!IMPORTANT]
>Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments). Se admite el uso de un apartamento de un [solo subproceso](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) , pero se producirá un rendimiento poco óptimo y posiblemente se produzca una intermitencia durante la reproducción. Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartamento multiproceso es el valor predeterminado.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obtención del paquete NuGet de Holographic Remoting

Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.
1. Abra el proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**
3. En el panel que aparece, seleccione **examinar** y busque "Holographic Remoting".
4. Seleccione **Microsoft. Holographic. Remoting. OpenXr**, asegúrese de elegir la versión **2. x. x** más reciente y seleccione **instalar**.
5. Si aparece el cuadro de diálogo **vista previa** , seleccione **Aceptar**.
6. Seleccione **acepto** cuando aparezca el cuadro de diálogo contrato de licencia.
7. Repita los pasos 3 a 6 para los siguientes paquetes NuGet: OpenXR. Headers, OpenXR. Loader

>[!NOTE]
>La versión **1. x.** x del paquete NuGet sigue estando disponible para los desarrolladores que quieran tener como destino HoloLens 1. Para obtener más información, consulte incorporación de la [comunicación remota holográfica (HoloLens (1º generación))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Seleccione el tiempo de ejecución de OpenXR de Holographic Remoting

El primer paso que debe hacer en la aplicación remota es seleccionar el tiempo de ejecución de Holographic Remoting OpenXR, que forma parte del paquete NuGet Microsoft. Holographic. Remoting. OpenXr. Para ello, establezca la variable de ```XR_RUNTIME_JSON``` entorno en la ruta de acceso del RemotingXR.jsen el archivo dentro de la aplicación. El cargador de OpenXR usa esta variable de entorno para no usar el tiempo de ejecución de OpenXR predeterminado del sistema, sino que se redirigirá al tiempo de ejecución de Holographic Remoting OpenXR. Al usar el paquete de NuGet Microsoft. Holographic. Remoting. OpenXr, el RemotingXR.jsen el archivo se copia automáticamente durante la compilación en la carpeta de salida, la selección del tiempo de ejecución de OpenXR suele tener el siguiente aspecto.

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Creación de XrInstance con la extensión Holographic Remoting

Se supone que es el primer paso que debe hacer una aplicación OpenXR típica para seleccionar las extensiones OpenXR y crear un XrInstance. La especificación de OpenXR Core no proporciona ninguna API específica de comunicación remota. Por ese motivo, Holographic Remoting introduce su propia extensión OpenXR denominada ```XR_MSFT_holographic_remoting``` . Asegúrese de que, al llamar a xrCreateInstance, ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` está incluido en XrInstanceCreateInfo.

>[!TIP]
>De forma predeterminada, el contenido representado de la aplicación solo se transmite al reproductor de comunicación remota holográfica que se ejecuta en una HoloLens 2 o en un casco de realidad mixta de Windows. Para mostrar también el contenido representado en el equipo remoto, a través de una cadena de intercambio de una ventana, por ejemplo, Holographic Remoting proporciona una segunda extensión OpenXR denominada ```XR_MSFT_holographic_remoting_frame_mirroring``` . Asegúrese de habilitar también esta extensión mediante ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` en caso de que desee usar esa funcionalidad.

>[!IMPORTANT]
>Para obtener información acerca de la API de extensión OpenXR de Holographic Remoting, consulte la [especificación](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) que se encuentra en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="connect-to-the-device"></a>Conexión al dispositivo

Después de que la aplicación remota haya creado el XrInstance y consultado el XrSystemId a través de xrGetSystem se puede establecer una conexión con el dispositivo de reproducción.

>[!WARNING]
> El tiempo de ejecución de OpenXR de Holographic Remoting solo puede proporcionar datos específicos del dispositivo, como configuraciones de vista o modos de fusión de entorno, una vez establecida una conexión. ```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` y le ```xrGetSystemProperties``` proporcionará los valores predeterminados, que coinciden con lo que normalmente obtendría si se conecta a un reproductor que se ejecuta en una HoloLens 2, antes de estar totalmente conectado.
Se recomienda no llamar a estos métodos antes de que se haya establecido una conexión. La sugerencia se usa en estos métodos una vez que se ha creado correctamente XrSession y el estado de la sesión es al menos XR_SESSION_STATE_READY.

Las propiedades generales como velocidad de bits máxima, audio habilitado, códec de vídeo o resolución de flujo de búfer de profundidad se pueden configurar a través ```xrRemotingSetContextPropertiesMSFT``` de la siguiente manera.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

La conexión puede realizarse de una de estas dos maneras.
1) La aplicación remota se conecta al reproductor que se ejecuta en el dispositivo.
2) El reproductor que se ejecuta en el dispositivo se conecta a la aplicación remota.

Para establecer una conexión desde la aplicación remota al dispositivo del reproductor, llame al ```xrRemotingConnectMSFT``` método especificando el nombre de host y el puerto a través de la  ```XrRemotingConnectInfoMSFT``` estructura. El puerto que usa el reproductor de comunicación remota holográfica es **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

La escucha de conexiones entrantes en la aplicación remota se puede realizar mediante una llamada al ```xrRemotingListenMSFT``` método. Tanto el puerto de enlace como el puerto de transporte se pueden especificar a través de la ```XrRemotingListenInfoMSFT``` estructura. El puerto de enlace se usa para el protocolo de enlace inicial. A continuación, los datos se envían a través del puerto de transporte. De forma predeterminada, se usan **8265** y **8266** .

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

El estado de conexión debe desconectarse cuando se llama a ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` . Puede obtener el estado de conexión en cualquier momento después de haber creado un XrInstance y de consultar el XrSystemId a través de ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Los Estados de conexión disponibles son:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``````xrRemotingListenMSFT```se debe llamar a o antes de intentar crear un XrSession a través de xrCreateSession. Si intenta crear un XrSession mientras el estado de conexión es ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` la creación de la sesión se realizará correctamente, pero el estado de la sesión pasará inmediatamente a XR_SESSION_STATE_LOSS_PENDING.

La implementación de Holographic Remoting de ```xrCreateSession``` admite la espera de que se establezca una conexión. Puede llamar a ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` inmediatamente después de una llamada a, que se bloqueará y esperará a que se establezca una conexión. El tiempo de espera se ha fijado en 10 segundos. Si se puede establecer una conexión en este momento, la creación de XrSession se realizará correctamente y el estado de la sesión pasará a XR_SESSION_STATE_READY. En caso de que no se pueda establecer una conexión, la creación de la sesión también se realiza correctamente, pero pasa inmediatamente a XR_SESSION_STATE_LOSS_PENDING.

En general, el estado de la conexión es par con el estado XrSession. Cualquier cambio en el estado de conexión también afecta al estado de la sesión. Por ejemplo, si el estado de conexión cambia de `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` a, ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` el estado de la sesión cambiará también a XR_SESSION_STATE_LOSS_PENDING.

## <a name="handling-remoting-specific-events"></a>Controlar eventos específicos de la comunicación remota

El tiempo de ejecución de OpenXR de Holographic Remoting expone tres eventos, que son importantes para supervisar el estado de una conexión.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Se desencadena cuando se ha establecido correctamente una conexión con el dispositivo.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Se desencadena si se cierra una conexión establecida o no se pudo establecer una conexión.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Cuando se inicia la escucha de conexiones entrantes.

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

Para mostrar el mismo contenido en la aplicación remota que se envía al dispositivo, ```XR_MSFT_holographic_remoting_frame_mirroring``` se puede usar la extensión. Con esta extensión, puede enviar una textura a xrEndFrame mediante el ```XrRemotingFrameMirrorImageInfoMSFT``` que no está encadenado a XrFrameEndInfo como se indica a continuación.

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

En el ejemplo anterior se usa una textura de cadena de intercambio de DX11 y se presenta la ventana inmediatamente después de la llamada a xrEndFrame. El uso no está restringido a las texturas de la cadena de intercambio y no se requiere ninguna sincronización de GPU adicional. Para obtener más información sobre el uso y las restricciones, consulte la especificación de la [extensión](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Si la aplicación remota usa DX12, use XrRemotingFrameMirrorImageD3D12MSFT en lugar de XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Consulte también
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Establecimiento de una conexión segura con Control remoto de holografías](holographic-remoting-secure-connection.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
