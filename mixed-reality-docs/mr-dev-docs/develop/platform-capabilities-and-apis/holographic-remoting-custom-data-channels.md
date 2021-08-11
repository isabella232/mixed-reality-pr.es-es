---
title: Canales de datos personalizados de control remoto de holografías
description: Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota holográfica ya establecida.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, canales de datos
ms.openlocfilehash: 09fea161f9042d7afc59c16d3b5e8a6c69892e84b1de5e9ab4a4808733b4f171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217091"
---
# <a name="custom-holographic-remoting-data-channels"></a>Canales de datos personalizados de control remoto de holografías

>[!NOTE]
>Esta guía es específica de la comunicación remota holográfica en HoloLens 2.

Use canales de datos personalizados para enviar datos personalizados a través de una conexión remota establecida.

>[!IMPORTANT]
>Los canales de datos personalizados requieren una aplicación remota personalizada y una aplicación de reproductor personalizado, ya que permite la comunicación entre las dos aplicaciones personalizadas.

>[!TIP]
>Puede encontrar un ejemplo sencillo de ping-ping-ping en los ejemplos remotos y de reproductor dentro del repositorio de GitHub de ejemplos de [Holographic Remoting.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) Descomprima ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` los archivos SampleRemoteMain.h / SamplePlayerMain.h para habilitar el código de ejemplo.


## <a name="create-a-custom-data-channel"></a>Creación de un canal de datos personalizado


Para crear un canal de datos personalizado, se requieren los siguientes campos:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Una vez establecida correctamente una conexión, puede crear nuevos canales de datos desde el lado remoto, el lado del reproductor o ambos. Tanto RemoteContext como PlayerContext proporcionan un ```CreateDataChannel()``` método para crear canales de datos. El primer parámetro es el identificador del canal, que se usa para identificar el canal de datos en las operaciones posteriores. El segundo parámetro es la prioridad, que especifica la prioridad con la que los datos de este canal se transfieren al otro lado. Los identificadores de canal válidos en el lado remoto van de 0 a 63, incluidos 63, y 64 hasta 127, incluidos 127 para el lado del jugador. Las prioridades válidas ```Low``` ```Medium``` son , o ```High``` (en ambos lados).

Para iniciar la creación de un canal de datos en **el lado** remoto:
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Para iniciar la creación de un canal de datos en el **lado del** reproductor:
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Para crear un nuevo canal de datos personalizado, solo un lado (ya sea remoto o reproductor) necesita llamar al ```CreateDataChannel``` método .

## <a name="handling-custom-data-channel-events"></a>Control de eventos de canal de datos personalizados

Para establecer un canal de datos personalizado, el evento debe controlarse (tanto en el ```OnDataChannelCreated``` reproductor como en el lado remoto). Se desencadena cuando un canal de datos de usuario se ha creado por cualquiera de los lados y proporciona un objeto , que se puede usar para enviar y recibir ```IDataChannel``` datos a través de este canal.

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

Para recibir una notificación cuando se reciben datos, regístrese en el ```OnDataReceived``` evento en el objeto proporcionado por el ```IDataChannel``` ```OnDataChannelCreated``` controlador. Regístrese en el evento para recibir una notificación cuando se haya ```OnClosed``` cerrado el canal de datos.

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

Para enviar datos a través de un canal de datos personalizado, use el ```IDataChannel::SendData()``` método . El primer parámetro es a ```winrt::array_view<const uint8_t>``` los datos que se deben enviar. El segundo parámetro especifica dónde se deben reenviar los datos, hasta que el otro lado confirme la recepción. 

>[!IMPORTANT]
>En caso de condiciones de red no adecuadas, el mismo paquete de datos podría llegar más de una vez. El código receptor debe ser capaz de controlar esta situación.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Cierre de un canal de datos personalizado

Para cerrar un canal de datos personalizado, use el ```IDataChannel::Close()``` método . El evento notificará a ambos lados una vez que se haya cerrado ```OnClosed``` el canal de datos personalizado.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Consulte también
* [Escritura de una aplicación remota de comunicación remota holográfica mediante Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de comunicación remota holográfica mediante las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)