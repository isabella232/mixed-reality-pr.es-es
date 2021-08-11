---
title: Información general sobre la comunicación remota holográfica
description: Obtenga información sobre la comunicación remota holográfica y cómo puede beneficiar al proceso de desarrollo.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidad mixta, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción, comunicación remota holográfica, escritorio, versión preliminar
ms.openlocfilehash: 1b20590429b7df209e805ed8e94de5a6010bdbb609edc10fc5854cd4df86f64c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217121"
---
# <a name="holographic-remoting-overview"></a>Información general sobre la comunicación remota holográfica

Al agregar compatibilidad con Holographic Rendering a la aplicación de PC o al juego, permite que la aplicación transmita contenido holográfico a HoloLens 2 en tiempo real. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo. La entrada de mirada, gesto, voz y asignación espacial se envía desde el HoloLens 2 al equipo, el contenido se representa en una vista inmersiva virtual mediante los mayores recursos del sistema del equipo y, a continuación, los fotogramas representados se envían de vuelta a la HoloLens 2. La comunicación remota holográfica también está disponible Windows Mixed Reality cascos envolventes.

Agregas comunicación remota holográfica a tu aplicación de escritorio o UWP a través de un paquete NuGet y la conexión se realiza mediante Wi-Fi estándar. Se requiere código adicional que controla la conexión y se representa en una vista inmersiva. Una conexión remota típica tendrá una latencia de hasta 50 ms. El dispositivo muestra el contenido transmitido mediante una aplicación de "reproductor" que puede notificar la latencia en tiempo real.

Si es desarrollador de Unity, también puede usar la comunicación remota holográfica ejecutando la aplicación en el editor de Unity en modo de reproducción.

## <a name="see-also"></a>Consulte también
* [Holographic Remoting Player](holographic-remoting-player.md)
* [Escritura de una aplicación remota de comunicación remota holográfica mediante Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de comunicación remota holográfica mediante las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Tutorial: Introducción a la comunicación remota holográfica de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Creación de una aplicación de pc de comunicación remota holográfica](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
