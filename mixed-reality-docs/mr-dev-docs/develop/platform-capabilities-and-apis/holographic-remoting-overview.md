---
title: Información general sobre la comunicación remota holográfica
description: Obtenga información sobre la comunicación remota holográfica y cómo puede beneficiar al proceso de desarrollo.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, augmented reality, virtual reality, mixed reality headsets, learn, tutorial, getting started, holographic remoting, desktop, preview
ms.openlocfilehash: 6eb3b9e9fe8811ab4666ef1beda0e48668bedbe6
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757440"
---
# <a name="holographic-remoting-overview"></a>Información general sobre la comunicación remota holográfica

Al agregar compatibilidad con Holographic Rendering a la aplicación o juego de PC, permite que la aplicación transmita contenido holográfico a su HoloLens 2 en tiempo real. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo. La entrada de mirada, gesto, voz y asignación espacial se envía desde el HoloLens 2 al equipo, el contenido se representa en una vista inmersiva virtual mediante los mayores recursos del sistema del equipo y, a continuación, los fotogramas representados se envían de vuelta a la HoloLens 2. La comunicación remota holográfica también está disponible Windows Mixed Reality cascos envolventes.

Agregas comunicación remota holográfica a tu aplicación de escritorio o UWP a través de un paquete NuGet y la conexión se realiza mediante Wi-Fi estándar. Se requiere código adicional que controle la conexión y se represente en una vista inmersiva. Una conexión remota típica tendrá tan solo 50 ms de latencia. El dispositivo muestra el contenido transmitido mediante una aplicación de "reproductor" que puede notificar la latencia en tiempo real.

Si es desarrollador de Unity, también puede usar la comunicación remota holográfica mediante la ejecución de la aplicación en el editor de Unity en modo de reproducción.

## <a name="see-also"></a>Consulte también
* [Holographic Remoting Player](holographic-remoting-player.md)
* [Escritura de una aplicación remota de Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting mediante las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Tutorial: Introducción a la comunicación remota holográfica de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Creación de una aplicación de PC de comunicación remota holográfica](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
