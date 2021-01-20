---
title: Canales de datos personalizados de control remoto de holografías
description: Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión de Holographic Remoting ya establecida.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, canales de datos
ms.openlocfilehash: a11fe0bb023ae34692015585f6e1689db4330ac7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582616"
---
# <a name="custom-holographic-remoting-data-channels"></a>Canales de datos personalizados de control remoto de holografías

>[!NOTE]
>Esta guía es específica de Holographic Remoting en HoloLens 2.

Usar canales de datos personalizados para enviar datos personalizados a través de una conexión de comunicación remota establecida.

>[!IMPORTANT]
>Los canales de datos personalizados requieren una aplicación remota personalizada y una aplicación de reproductor personalizada, ya que permite la comunicación entre las dos aplicaciones personalizadas.

>[!TIP]
>Puede encontrar un ejemplo sencillo de ping-pong en los ejemplos de Remote y Player dentro del [repositorio de github de ejemplos](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)de la comunicación remota de Holographic. Quite los comentarios ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` dentro de los archivos SampleRemoteMain. h/SamplePlayerMain. h para habilitar el código de ejemplo.


## <a name="create-a-custom-data-channel"></a>Creación de un canal de datos personalizado


Para crear un canal de datos personalizado, se necesitan los siguientes campos:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Una vez establecida correctamente una conexión, puede crear canales de datos nuevos desde el lado remoto, el lado del reproductor o ambos. Tanto RemoteContext como PlayerContext proporcionan un ```CreateDataChannel()``` método para crear canales de datos. El primer parámetro es el identificador del canal, que se usa para identificar el canal de datos en operaciones posteriores. El segundo parámetro es la prioridad, que especifica la prioridad con la que se transfieren los datos de este canal al otro lado. Los identificadores de canal válidos en el lado remoto son desde 0 hasta 63 y 64, hasta el 127, inclusive. Las prioridades válidas son ```Low``` , ```Medium``` o ```High``` (en ambos lados).

Para iniciar la creación de un canal de datos en el lado **remoto** :
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Para iniciar la creación de un canal de datos en el lado del **reproductor** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Para crear un nuevo canal de datos personalizado, solo un lado (ya sea remoto o reproductor) debe llamar al ```CreateDataChannel``` método.

## <a name="handling-custom-data-channel-events"></a>Control de eventos de canal de datos personalizados

Para establecer un canal de datos personalizado, ```OnDataChannelCreated``` es necesario controlar el evento (tanto en el reproductor como en el lado remoto). Se desencadena cuando se crea un canal de datos de usuario en cualquier lado y proporciona un ```IDataChannel``` objeto, que se puede usar para enviar y recibir datos a través de este canal.

Para registrar un agente de escucha en el ```OnDataChannelCreated``` evento:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Para recibir una notificación cuando se reciban los datos, Regístrese en el ```OnDataReceived``` evento en el ```IDataChannel``` objeto proporcionado por el ```OnDataChannelCreated``` controlador. Regístrese en el ```OnClosed``` evento para recibir una notificación cuando se haya cerrado el canal de datos.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>Envío de datos

Para enviar datos a través de un canal de datos personalizado, use el ```IDataChannel::SendData()``` método. El primer parámetro es un ```winrt::array_view<const uint8_t>``` a los datos que se deben enviar. El segundo parámetro especifica dónde se deben volver a enviar los datos, hasta que el otro lado confirme la recepción. 

>[!IMPORTANT]
>En caso de condiciones de red erróneas, el mismo paquete de datos podría llegar más de una vez. El código receptor debe ser capaz de controlar esta situación.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Cerrar un canal de datos personalizado

Para cerrar un canal de datos personalizado, use el ```IDataChannel::Close()``` método. Los dos lados recibirán una notificación por el ```OnClosed``` evento una vez que se haya cerrado el canal de datos personalizado.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Consulte también
* [Escritura de una aplicación remota Holographic Remoting con las API de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting con las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)