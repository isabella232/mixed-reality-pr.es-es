---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855891"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="4fd5b-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4fd5b-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="4fd5b-102">Opción</span><span class="sxs-lookup"><span data-stu-id="4fd5b-102">Option</span></span> | <span data-ttu-id="4fd5b-103">Descripción</span><span class="sxs-lookup"><span data-stu-id="4fd5b-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="4fd5b-104">Tome la dirección IP (y el puerto opcional) del dispositivo HoloLens 2 al que se va a conectar.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="4fd5b-105">Si no se proporciona ningún puerto, el valor predeterminado es 8265.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="4fd5b-106">(opcional) Valor predeterminado de 8000.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-106">(optional) Default 8000.</span></span> <span data-ttu-id="4fd5b-107">Velocidad de transferencia de red máxima (KB/s).</span><span class="sxs-lookup"><span data-stu-id="4fd5b-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="4fd5b-108">(opcional) Inicio de un servidor de escucha.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="4fd5b-109">(opcional) Toma el puerto en el que realizar la escucha.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="4fd5b-110">Se usa para conectarse a un equipo o una máquina virtual desde un dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="4fd5b-111">(en desuso en la versión 4.26) Toma la dirección IP del dispositivo HoloLens 1 al que se va a conectar.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="4fd5b-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4fd5b-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="4fd5b-113">Opción</span><span class="sxs-lookup"><span data-stu-id="4fd5b-113">Option</span></span> | <span data-ttu-id="4fd5b-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="4fd5b-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="4fd5b-115">Toma la dirección IP (y el puerto opcional, el valor predeterminado 8265) del dispositivo HoloLens 2 al que se va a conectar, o el puerto en el que la aplicación debe escuchar las conexiones.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="4fd5b-116">(opcional) Uso del audio del equipo cuando se usa la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="4fd5b-117">(opcional) Inicio de un servidor de escucha.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="4fd5b-118">(opcional) Valor predeterminado de 8000.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-118">(optional) Default 8000.</span></span> <span data-ttu-id="4fd5b-119">Velocidad de transferencia de red máxima (KB/s).</span><span class="sxs-lookup"><span data-stu-id="4fd5b-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="4fd5b-120">(opcional) Códec de conexión.</span><span class="sxs-lookup"><span data-stu-id="4fd5b-120">(optional) Connection codec</span></span>  |