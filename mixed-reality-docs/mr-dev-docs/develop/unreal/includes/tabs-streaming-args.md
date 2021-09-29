---
ms.openlocfilehash: 12634c1fc18366e28a51688b19fc739ea69d37ec
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184639"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Opción | Descripción |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Tome la dirección IP (y el puerto opcional) del dispositivo HoloLens 2 al que se va a conectar. Si no se proporciona ningún puerto, el valor predeterminado es 8265. |
| `-RemotingBitrate=<bitrate>` | (opcional) Valor predeterminado de 8000. Velocidad de transferencia de red máxima (KB/s). |
| `-HoloLensRemotingListen` | (opcional) Inicio de un servidor de escucha. |
| `-HoloLensRemotingListenPort=<port>` | (opcional) Toma el puerto en el que realizar la escucha. Se usa para conectarse a un equipo o una máquina virtual desde un dispositivo HoloLens. |
| `-HoloLens1Remoting=<IP address>` | (en desuso en la versión 4.26) Toma la dirección IP del dispositivo HoloLens 1 al que se va a conectar. |
| `-eyetracking=WindowsMixedRealityEyeTracker` | (opcional) Uso del seguimiento ocular de Windows Mixed Reality |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Opción | Descripción |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Toma la dirección IP (y el puerto opcional, el valor predeterminado 8265) del dispositivo HoloLens 2 al que se va a conectar, o el puerto en el que la aplicación debe escuchar las conexiones. |
| `-EnableAudio` | (opcional) Uso del audio del equipo cuando se usa la comunicación remota.  |
| `-Listen` | (opcional) Inicio de un servidor de escucha. |
| `-RemotingBitrate=<bitrate>` | (opcional) Valor predeterminado de 8000. Velocidad de transferencia de red máxima (KB/s). |
| `-RemotingCodec=<codec>` | (opcional) Códec de conexión.  |
| `-eyetracking=OpenXREyeTracker` | (opcional) Uso del seguimiento ocular con OpenXR |