---
title: Paquetes UDP en aplicaciones de Unity para UWP
description: Aprenda a configurar una aplicación de Unity para UWP para enviar y recibir paquetes UDP a través de una red segura.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, paquetes UDP, Socket, servidor cliente, punto de conexión, redes, equipo remoto, datagramsocket, ejemplo, .net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566986"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Paquetes UDP en aplicaciones de Unity para UWP

Puede configurar las aplicaciones de Unity de Plataforma universal de Windows (UWP) para recibir paquetes UDP con la ayuda de un servidor y un cliente de socket UDP. Los sockets UDP no mantienen la conexión en ambos extremos, por lo que son una solución rápida y sencilla para redes entre equipos remotos. Sin embargo, será responsable de comprobar si los paquetes obtienen acceso a su destino, ya que los sockets UDP no lo hacen automáticamente.

## <a name="setup"></a>Configuración

Abra los proyectos HoloLens manifest.jsen el archivo y asegúrese de que ha habilitado:
* **Internet (servidor de & de cliente)** 
* **Redes privadas (cliente & servidor)**.

## <a name="build-your-socket-client-and-server"></a>Compilar el cliente y el servidor de sockets 

Siga las instrucciones para [crear un cliente de socket UDP básico y un servidor](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server). Usará la clase [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) para enviar y recibir datos a través de UDP y formar un cliente y un servidor de eco. También se recomienda leer las secciones de otros recursos de este artículo, ya que se aplican a casos de uso más personalizados y complejos. 

> [!IMPORTANT]
> Si tiene problemas para enviar paquetes UDP del equipo al equipo, compruebe que la red permite estas operaciones. Si la red bloquea los paquetes UDP de algún modo, el dispositivo HoloLens no podrá escucharlos.

Puede descargar una aplicación de ejemplo de un UDP de DatagramSocket completa en el vínculo siguiente:

> [!div class="nextstepaction"]
> [Instalación de las herramientas](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Consulta también 
* [Experimentos con hologramas compartidos y multidifusión de Azure Blob Storage/UDP](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)