---
title: Transferencias de delimitadores locales en Unity
description: Aprenda a transferir delimitadores entre varios dispositivos HoloLens en una aplicación de realidad mixta de Unity.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, transfer, local anchor transfer, anchor export, anchor import
ms.openlocfilehash: eaf25edbae39aab628277aa29f975f3d4d9d7374c796fd1b7b159053d4a46b95
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189133"
---
# <a name="local-anchor-transfers-in-unity"></a>Transferencias de delimitadores locales en Unity

En situaciones en las que no se puede usar <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, las transferencias de delimitadores locales permiten que un dispositivo HoloLens exporte un delimitador para que lo importe un segundo HoloLens dispositivo.

>[!NOTE]
>Las transferencias de anclaje local proporcionan una recuperación de anclaje menos sólida que <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, y este enfoque no admite dispositivos iOS y Android.

### <a name="setting-the-spatialperception-capability"></a>Establecimiento de la funcionalidad SpatialPerception

Para que una aplicación transfiera anclajes espaciales, se debe habilitar la funcionalidad *SpatialPerception.*

Habilitación de *la funcionalidad SpatialPerception:*
1. En el Editor de Unity, abra **el panel "Player Configuración"** (Editar > Project Configuración > Player)
2. Haga clic en la **pestaña "Windows Store".**
3. Expanda **"Publicación Configuración"** y compruebe la **funcionalidad "SpatialPerception"** en la **lista "Funcionalidades".**

>[!NOTE]
>Si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o establecer manualmente esta funcionalidad en [AppxManifest](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)en Visual Studio .

### <a name="anchor-transfer"></a>Transferencia de delimitadores

**Espacio de nombres:** *UnityEngine.XR.WSA.Sharing*<br>
**Tipo**: *WorldAnchorTransferBatch*

Para transferir un [Objeto WorldAnchor,](../develop/unity/coordinate-systems-in-unity.md)se debe establecer el delimitador que se va a transferir. El usuario de un HoloLens examina su entorno y elige manualmente o mediante programación un punto en el espacio para que sea el delimitador de la experiencia compartida. Los datos que representan este punto se pueden serializar y transmitir a los demás dispositivos que comparten la experiencia. A continuación, cada dispositivo deseriala los datos delimitadores e intenta localizar ese punto en el espacio. Para que la transferencia de delimitadores funcione, cada dispositivo debe haber examinado suficientemente el entorno para que se pueda identificar el punto representado por el delimitador.

### <a name="setup"></a>Configurar

El código de ejemplo de esta página tiene algunos campos que se deben inicializar:
1. *RootGameObject de GameObject* es *un GameObject* de Unity que tiene un *componente WorldAnchor.* Un usuario de la experiencia compartida colocará *este GameObject* y exportará los datos a los demás usuarios.
2. *WorldAnchor gameRootAnchor* es *UnityEngine.XR.WSA.WorldAnchor* que se encuentra en *rootGameObject*.
3. *byte[] importedData es* una matriz de bytes para el delimitador serializado que cada cliente recibe a través de la red.

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>Exportación

Para exportar, solo necesitamos un *WorldAnchor* y saber cómo lo llamaremos de modo que tenga sentido para la aplicación receptora. Un cliente de la experiencia compartida realizará estos pasos para exportar el delimitador compartido:
1. Creación de *un WorldAnchorTransferBatch*
2. Adición de *WorldAnchors para* transferir
3. Inicio de la exportación
4. Controlar el *evento OnExportDataAvailable* a medida que los datos están disponibles
5. Controlar el *evento OnExportComplete*

Creamos un *Objeto WorldAnchorTransferBatch* para encapsular lo que se va a transferir y, a continuación, exportarlo en bytes:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

A medida que los datos estén disponibles, envíe los bytes al cliente o búfer a medida que los segmentos de datos estén disponibles y envíe a través de los medios deseados:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Una vez completada la exportación, si hemos estado transfiriendo datos y se ha generado un error de serialización, indórmele al cliente que descarte los datos. Si la serialización se ha realizado correctamente, informe al cliente de que se han transferido todos los datos y se puede iniciar la importación:

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>Importación

Después de recibir todos los bytes del remitente, podemos volver a importar los datos en *worldanchorTransferBatch* y bloquear el objeto raíz del juego en la misma ubicación física. Nota: La importación a veces producirá un error transitorio y debe reinterse:

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

Después de bloquear *un GameObject* mediante la llamada *LockObject,* tendrá un *Elemento WorldAnchor* que lo mantendrá en la misma posición física del mundo, pero puede estar en una ubicación diferente en el espacio de coordenadas de Unity que otros usuarios.