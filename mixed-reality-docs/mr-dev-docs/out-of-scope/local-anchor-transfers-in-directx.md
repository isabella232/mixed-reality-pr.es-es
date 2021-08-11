---
title: Transferencias de anclaje local en DirectX
description: Aprenda a sincronizar dos dispositivos HoloLens mediante la transferencia, exportación y serialización de anclajes espaciales.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, synchronize, spatial anchor, transfer, multiplayer, view, scenario, walkthrough, sample code, transfer, local anchor transfer, anchor export, anchor import
ms.openlocfilehash: df00e323267aa398ba45cfd7a7234c04ce8eca85f2ff3be9b6c9ddee67264085
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195672"
---
# <a name="local-anchor-transfers-in-directx"></a>Transferencias de anclaje local en DirectX

En situaciones en las que no se puede usar <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, las transferencias de anclaje local permiten que un dispositivo HoloLens exporte un delimitador para que lo importe un segundo HoloLens dispositivo.

>[!NOTE]
>Las transferencias de anclaje local proporcionan una recuperación de anclaje menos sólida que <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>y este enfoque no admite dispositivos iOS y Android.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso de C++/CX en lugar de C++17 compatible con C++17, como se usa en la plantilla de proyecto holográfico de [C++.](../develop/native/creating-a-holographic-directx-project.md)  Los conceptos son equivalentes para un proyecto de C++/WinRT, aunque deberás traducir el código.

## <a name="transferring-spatial-anchors"></a>Transferencia de anclajes espaciales

Puede transferir delimitadores espaciales entre Windows Mixed Reality dispositivos mediante [SpatialAnchorTransferManager](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager). Esta API le permite agrupar un anclaje con todos los datos del sensor de soporte necesarios para encontrar ese lugar exacto en el mundo y, a continuación, importar ese paquete en otro dispositivo. Una vez que la aplicación del segundo dispositivo ha importado ese delimitador, cada aplicación puede representar hologramas mediante el sistema de coordenadas de ese delimitador espacial compartido, que aparecerá en el mismo lugar del mundo real.

Tenga en cuenta que los anclajes espaciales no pueden transferirse entre diferentes tipos de dispositivos, por ejemplo, un delimitador espacial HoloLens no se puede localizar mediante un casco envolvente.  Los anclajes transferidos tampoco son compatibles con dispositivos iOS o Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configuración de la aplicación para usar la funcionalidad spatialPerception

La aplicación debe tener permiso para usar la funcionalidad SpatialPerception para poder usar [SpatialAnchorTransferManager.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) Esto es necesario porque la transferencia de un delimitador espacial implica compartir imágenes de sensor recopiladas a lo largo del tiempo en proximidad de ese anclaje, lo que podría incluir información confidencial.

Declare esta funcionalidad en el archivo package.appxmanifest de la aplicación. Este es un ejemplo:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funcionalidad procede del espacio de **nombres uap2.** Para obtener acceso a este espacio de nombres en el manifiesto, inscluyéndolo como atributo *xlmns* en el elemento &lt; Package>. Este es un ejemplo:

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**NOTA:** La aplicación tendrá que solicitar la funcionalidad en tiempo de ejecución para poder acceder a las API de exportación e importación de SpatialAnchor. Consulte [RequestAccessAsync en](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) los ejemplos siguientes.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serializar los datos de delimitador exportandolos con SpatialAnchorTransferManager

En el ejemplo de código se incluye una función auxiliar para exportar (serializar) [datos spatialAnchor.](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) Esta API de exportación serializa todos los delimitadores de una colección de pares clave-valor que asocian cadenas a delimitadores.

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

En primer lugar, es necesario configurar el flujo de datos. Esto nos permitirá 1). use TryExportAnchorsAsync para colocar los datos en un búfer propiedad de la aplicación, y 2). lee datos del flujo de búfer de bytes exportado , que es un flujo de datos winRT, en nuestro propio búfer de memoria, que es un byte std::vector &lt;>.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Es necesario solicitar permiso para acceder a los datos espaciales, incluidos los delimitadores exportados por el sistema.

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

Si se obtiene el permiso y se exportan los delimitadores, se puede leer el flujo de datos. Aquí también se muestra cómo crear DataReader y InputStream que usaremos para leer los datos.

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

Después de leer bytes de la secuencia, podemos guardarlos en nuestro propio búfer de datos de este modo.

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserializar los datos de delimitador importing it into the system using the SpatialAnchorTransferManager

En el ejemplo de código se incluye una función auxiliar para cargar los datos exportados previamente. Esta función de deserialización proporciona una colección de pares clave-valor, similar a lo que proporciona SpatialAnchorStore, salvo que hemos recibido estos datos de otro origen, como un socket de red. Puede procesar y razonar sobre estos datos antes de almacenarlos sin conexión, mediante la memoria en la aplicación o (si procede) spatialAnchorStore de la aplicación.

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

En primer lugar, es necesario crear objetos de flujo para acceder a los datos delimitadores. Escribiremos los datos del búfer en un búfer del sistema, por lo que crearemos un objeto DataWriter que escriba en un flujo de datos en memoria para lograr nuestro objetivo de obtener anclajes de un búfer de bytes en el sistema como SpatialAnchors.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Una vez más, es necesario asegurarse de que la aplicación tiene permiso para exportar datos de anclaje espacial, lo que podría incluir información privada sobre el entorno del usuario.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Si se permite el acceso, podemos escribir bytes desde el búfer en un flujo de datos del sistema.

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

Si almacenamos correctamente bytes en el flujo de datos, podemos intentar importarlos mediante SpatialAnchorTransferManager.

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

Si los datos se pueden importar, se obtiene una vista de mapa de pares clave-valor que asocian cadenas con delimitadores. Podemos cargarlo en nuestra propia recopilación de datos en memoria y usar esa colección para buscar delimitadores que nos interesen usar.

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**NOTA:** El hecho de que pueda importar un delimitador no significa necesariamente que pueda usarlo de inmediato. El delimitador puede estar en una sala diferente o en otra ubicación física por completo; el delimitador no se podrá localizar hasta que el dispositivo que lo recibió tenga suficiente información visual sobre el entorno en el que se creó el delimitador para restaurar la posición del delimitador con respecto al entorno actual conocido. La implementación del cliente debe intentar localizar el delimitador en relación con el sistema de coordenadas local o el marco de referencia antes de continuar intentando usarlo para el contenido en directo. Por ejemplo, intente localizar el delimitador con respecto a un sistema de coordenadas actual periódicamente hasta que el delimitador empiece a ser localizable.

## <a name="special-considerations"></a>Consideraciones especiales

La API [TryExportAnchorsAsync](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) permite exportar varios [SpatialAnchors](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) al mismo blob binario opaco. Sin embargo, hay una diferencia sutil en los datos que incluirá el blob, en función de si un único SpatialAnchor o varios SpatialAnchors se exportan en una sola llamada.

### <a name="export-of-a-single-spatialanchor"></a>Exportación de un único SpatialAnchor

El blob contiene una representación del entorno en las proximidades de SpatialAnchor para que el entorno se pueda reconocer en el dispositivo que importa SpatialAnchor. Una vez completada la importación, el nuevo SpatialAnchor estará disponible para el dispositivo. Suponiendo que el usuario haya estado recientemente cerca del delimitador, será localizable y se podrán representar los hologramas conectados a SpatialAnchor. Estos hologramas se mostrarán en la misma ubicación física que en el dispositivo original que exportó SpatialAnchor.

![Exportación de un único SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Exportación de varios spatialanchors

Al igual que la exportación de un único SpatialAnchor, el blob contiene una representación del entorno en la proximidad de todos los SpatialAnchors especificados. Además, el blob contiene información sobre las conexiones entre los SpatialAnchors incluidos, si se encuentran en el mismo espacio físico. Esto significa que si se importan dos spatialanchors cercanos, un holograma asociado al segundo  SpatialAnchor sería localizable incluso si el dispositivo solo reconoce el entorno alrededor del primer  SpatialAnchor, porque se incluyeron suficientes datos para calcular la transformación entre los dos SpatialAnchors en el blob. Si los dos SpatialAnchors se exportaron individualmente (dos llamadas independientes a TryExportSpatialAnchors), es posible que no haya suficientes datos incluidos en el blob para los hologramas asociados al segundo SpatialAnchor que se puedan localizar cuando se encuentra el primero.

![Varios anclajes exportados mediante una única llamada TryExportAnchorsAsync](images/multipleanchors.png) ![Varios anclajes exportados mediante una llamada TryExportAnchorsAsync independiente para cada delimitador](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Ejemplo: Envío de datos delimitadores mediante un Windows::Networking::StreamSocket

Aquí se proporciona un ejemplo de cómo usar los datos delimitadores exportados mediante el envío a través de una red TCP. Esto es de HolographicSpatialAnchorTransferSample.

La clase StreamSocket de WinRT usa la biblioteca de tareas de PPL. En el caso de errores de red, el error se devuelve a la siguiente tarea de la cadena mediante una excepción que se vuelve a lanzar. La excepción contiene un HRESULT que indica el estado del error.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Usar un Windows::Networking::StreamSocketListener con TCP para enviar datos delimitadores exportados

Cree una instancia de servidor que escuche una conexión.

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

Cuando se recibe una conexión, use la conexión de socket de cliente para enviar datos delimitadores.

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

Ahora, podemos empezar a enviar un flujo de datos que contenga los datos delimitadores exportados.

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

Para poder enviar la propia secuencia, primero debemos enviar un paquete de encabezado. Este paquete de encabezado debe ser de longitud fija y también debe indicar la longitud de la matriz variable de bytes que es el flujo de datos delimitadores; En el caso de este ejemplo no tenemos ningún otro dato de encabezado para enviar, por lo que nuestro encabezado tiene 4 bytes de longitud y contiene un entero de 32 bits sin signo.

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

Una vez que la longitud del flujo, en bytes, se ha enviado al cliente, podemos continuar para escribir el propio flujo de datos en el flujo de socket. Esto hará que los bytes del almacén delimitador se envíen al cliente.

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

Como se indicó anteriormente en este tema, debemos estar preparados para controlar las excepciones que contienen mensajes de estado de error de red. Para los errores que no se esperan, podemos escribir la información de excepción en la consola de depuración de este modo. Esto nos dará una pista sobre lo que ha ocurrido si el ejemplo de código no puede completar la conexión o si no puede terminar de enviar los datos delimitadores.

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Use un Windows::Networking::StreamSocket con TCP para recibir datos delimitadores exportados

En primer lugar, tenemos que conectarnos al servidor. En este ejemplo de código se muestra cómo crear y configurar streamSocket y cómo crear un objeto DataReader que puede usar para adquirir datos de red mediante la conexión de socket.

**NOTA:** Si ejecuta este código de ejemplo, asegúrese de configurar e iniciar el servidor antes de iniciar el cliente.

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

Una vez que tenemos una conexión, podemos esperar a que el servidor envíe datos. Para ello, llamamos a LoadAsync en el lector de datos de flujo.

El primer conjunto de bytes que recibimos siempre debe ser el paquete de encabezado, que indica la longitud de bytes del flujo de datos delimitador tal y como se describe en la sección anterior.

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

Una vez que hemos recibido el paquete de encabezado, sabemos cuántos bytes de datos delimitadores debemos esperar. Podemos continuar con la lectura de esos bytes de la secuencia.

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

Este es nuestro código para recibir el flujo de datos delimitadores. De nuevo, primero cargaremos los bytes de la secuencia; Esta operación puede tardar algún tiempo en completarse, ya que StreamSocket espera recibir esa cantidad de bytes de la red.

Una vez completada la operación de carga, podemos leer ese número de bytes. Si recibimos el número de bytes que esperamos para el flujo de datos de anclaje, podemos continuar e importar los datos del delimitador. Si no es así, debe haber algún tipo de error. Por ejemplo, esto puede ocurrir cuando la instancia del servidor finaliza antes de que pueda terminar de enviar el flujo de datos o la red se queda sin servicio antes de que el cliente pueda recibir todo el flujo de datos.

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

De nuevo, debemos estar preparados para controlar los errores de red desconocidos.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Eso es todo. Ahora, debería tener suficiente información para intentar localizar los anclajes recibidos a través de la red. De nuevo, tenga en cuenta que el cliente debe tener suficientes datos de seguimiento visual para que el espacio localice correctamente el delimitador. Si no funciona de inmediato, pruebe a recorrerlo durante un tiempo. Si sigue sin funcionar, haga que el servidor envíe más anclajes y use las comunicaciones de red para ponerse de acuerdo en una que funcione para el cliente. Para probar esto, descargue HolographicSpatialAnchorTransferSample, configure las IP de cliente y de servidor, e implemente en dispositivos cliente HoloLens servidor.

## <a name="see-also"></a>Consulte también
* [Biblioteca de modelos de procesamiento paralelo (PPL)](/cpp/parallel/concrt/parallel-patterns-library-ppl)
* [Windows. Networking.StreamSocket](/uwp/api/Windows.Networking.Sockets.StreamSocket)
* [Windows. Networking.StreamSocketListener](/uwp/api/Windows.Networking.Sockets.StreamSocketListener)