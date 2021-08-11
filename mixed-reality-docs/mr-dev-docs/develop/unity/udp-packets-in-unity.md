---
title: Paquetes UDP en aplicaciones para UWP de Unity
description: Aprenda a configurar una aplicación para UWP de Unity para enviar y recibir paquetes UDP a través de una red segura.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, paquetes UDP, socket, servidor cliente, punto de conexión, redes, máquina remota, datagramasocket, ejemplo, .net
ms.openlocfilehash: a24498384ccb2018f62f00523bf33764d2ef7c019dec0cfd8fc70d86b55a81bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192561"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Paquetes UDP en aplicaciones para UWP de Unity

Puede configurar las aplicaciones de Unity Windows Platform Universal (UWP) para recibir paquetes UDP con la ayuda de un cliente y un servidor de socket UDP. Los sockets UDP no mantienen la conexión en ambos puntos de conexión, por lo que son una solución rápida y sencilla para las redes entre máquinas remotas. Sin embargo, será responsable de comprobar si los paquetes lleguen a su destino, ya que los sockets UDP no lo hacen automáticamente.

## <a name="setup"></a>Configurar

Abra los proyectos HoloLens manifest.jsen el archivo y asegúrese de que ha habilitado:
* **Internet (cliente & Server)** 
* **Redes privadas (servidor & cliente).**

## <a name="build-your-socket-client-and-server"></a>Compilación del cliente de socket y el servidor 

Siga las instrucciones para [crear un cliente de socket UDP básico y un servidor](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server). Va a usar la clase [DatagramSocket para](/uwp/api/Windows.Networking.Sockets.DatagramSocket) enviar y recibir datos a través de UDP y formar un servidor y un cliente de eco. También se recomienda leer las demás secciones de recursos de este artículo, ya que se aplican a casos de uso más personalizados y complejos. 

> [!IMPORTANT]
> Si tiene problemas para enviar paquetes UDP desde pc a PC, compruebe que la red permite estas operaciones. Si la red bloquea los paquetes UDP de alguna manera, HoloLens dispositivo no podrá escucharlos.

Puede descargar una aplicación de ejemplo UDP DatagramSocket completa desde el vínculo siguiente:

> [!div class="nextstepaction"]
> [Instalación de las herramientas](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Consulta también 
* [Experimentos con la multidifusión Hologramas y UDP de Azure Blob Storage/UDP](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)