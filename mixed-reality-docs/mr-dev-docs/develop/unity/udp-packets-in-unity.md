---
title: Paquetes UDP en aplicaciones de Unity para UWP
description: Aprenda a configurar una aplicación de Unity para UWP para enviar y recibir paquetes UDP a través de una red segura.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, paquetes UDP, Socket, servidor cliente, punto de conexión, redes, equipo remoto, datagramsocket, ejemplo, .net
ms.openlocfilehash: b38897f228a62abeb63b7e2ffc0f2a98a840b781
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550525"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="84eae-104">Paquetes UDP en aplicaciones de Unity para UWP</span><span class="sxs-lookup"><span data-stu-id="84eae-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="84eae-105">Puede configurar las aplicaciones de Unity de Plataforma universal de Windows (UWP) para recibir paquetes UDP con la ayuda de un servidor y un cliente de socket UDP.</span><span class="sxs-lookup"><span data-stu-id="84eae-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="84eae-106">Los sockets UDP no mantienen la conexión en ambos extremos, por lo que son una solución rápida y sencilla para redes entre equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="84eae-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="84eae-107">Sin embargo, será responsable de comprobar si los paquetes obtienen acceso a su destino, ya que los sockets UDP no lo hacen automáticamente.</span><span class="sxs-lookup"><span data-stu-id="84eae-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="84eae-108">Configurar</span><span class="sxs-lookup"><span data-stu-id="84eae-108">Setup</span></span>

<span data-ttu-id="84eae-109">Abra los proyectos HoloLens manifest.jsen el archivo y asegúrese de que ha habilitado:</span><span class="sxs-lookup"><span data-stu-id="84eae-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="84eae-110">**Internet (servidor de & de cliente)**</span><span class="sxs-lookup"><span data-stu-id="84eae-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="84eae-111">**Redes privadas (cliente & servidor)**.</span><span class="sxs-lookup"><span data-stu-id="84eae-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="84eae-112">Compilar el cliente y el servidor de sockets</span><span class="sxs-lookup"><span data-stu-id="84eae-112">Build your socket client and server</span></span> 

<span data-ttu-id="84eae-113">Siga las instrucciones para [crear un cliente de socket UDP básico y un servidor](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="84eae-113">Follow the instructions for [building a basic UDP socket client and server](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="84eae-114">Usará la clase [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) para enviar y recibir datos a través de UDP y formar un cliente y un servidor de eco.</span><span class="sxs-lookup"><span data-stu-id="84eae-114">You'll be using the [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="84eae-115">También se recomienda leer las secciones de otros recursos de este artículo, ya que se aplican a casos de uso más personalizados y complejos.</span><span class="sxs-lookup"><span data-stu-id="84eae-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="84eae-116">Si tiene problemas para enviar paquetes UDP del equipo al equipo, compruebe que la red permite estas operaciones.</span><span class="sxs-lookup"><span data-stu-id="84eae-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="84eae-117">Si la red bloquea los paquetes UDP de algún modo, el dispositivo HoloLens no podrá escucharlos.</span><span class="sxs-lookup"><span data-stu-id="84eae-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="84eae-118">Puede descargar una aplicación de ejemplo de un UDP de DatagramSocket completa en el vínculo siguiente:</span><span class="sxs-lookup"><span data-stu-id="84eae-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84eae-119">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="84eae-119">Install the tools</span></span>](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="84eae-120">Consulta también</span><span class="sxs-lookup"><span data-stu-id="84eae-120">See also</span></span> 
* [<span data-ttu-id="84eae-121">Experimentos con hologramas compartidos y multidifusión de Azure Blob Storage/UDP</span><span class="sxs-lookup"><span data-stu-id="84eae-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)