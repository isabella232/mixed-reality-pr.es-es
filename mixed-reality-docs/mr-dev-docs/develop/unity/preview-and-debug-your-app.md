---
title: Vista previa y depuración de la aplicación con la comunicación remota holográfica y el modo de reproducción
description: Uso de la comunicación remota holográfica y el modo de reproducción para obtener una vista previa y depurar la aplicación
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, augmented reality, virtual reality, mixed reality headsets, learn, tutorial, getting started, holographic remoting, desktop, preview, debug
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203861"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>Vista previa y depuración de la aplicación mediante la comunicación remota holográfica y el modo de reproducción

En este artículo se explica el siguiente caso de uso para la comunicación remota holográfica: 

- **Quiere obtener una** vista previa y depurar la aplicación durante el proceso de desarrollo: puede ejecutar la aplicación localmente en el editor de Unity en el equipo en modo de reproducción y transmitir la experiencia a su HoloLens. Esto proporciona una manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo. A este tipo de aplicación se le llama aplicación _holographic remoting Play Mode Preview_. Las entradas del HoloLens (mirada, gesto, voz y asignación espacial) se envían al equipo, donde el contenido se representa en una vista inmersiva virtual. A continuación, los fotogramas representados se envían al HoloLens. 

Para más información sobre la comunicación remota holográfica, consulte [Información general sobre la comunicación remota holográfica.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Tenga en cuenta que también puede [](use-pc-resources.md) usar la comunicación remota holográfica si desea que los recursos de un equipo puedan encender la aplicación en lugar de confiar en los HoloLens recursos internos.

## <a name="set-up-holographic-remoting"></a>Configuración de Holographic Remoting

Para usar Holographic Remoting, debe instalar la aplicación [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) desde el Microsoft Store en el HoloLens. Como se explica a continuación, después de descargar y ejecutar la aplicación, verá el número de versión y la dirección IP a los que conectarse. **Necesitará la versión 2.4** o posterior para trabajar con el complemento OpenXR.

La comunicación remota holográfica requiere un equipo rápido y Wi-Fi conexión. Puede encontrar más detalles en el artículo de Holographic Remoting Player vinculado anteriormente.

![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en el HoloLens](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>Consulte también
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Tutorial: Introducción a la comunicación remota holográfica de PC](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Creación de una aplicación de pc de comunicación remota holográfica](tutorials/mr-learning-pc-holographic-remoting-02.md)
