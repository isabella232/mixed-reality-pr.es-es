---
title: Modo de reproducción de Unity
description: Aprenda a usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios de la aplicación en un dispositivo sin implementar una aplicación.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor de comunicación remota holográfica, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, modo de juego de Unity
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392301"
---
# <a name="unity-play-mode"></a>Modo de reproducción de Unity

Una manera rápida de trabajar en el proyecto de Unity es usar el "Modo de reproducción", que ejecuta la aplicación localmente en el editor de Unity en el equipo. Unity usa Holographic Remoting para proporcionar una manera rápida de obtener una vista previa del contenido en un dispositivo HoloLens real. El modo de reproducción también se puede usar con un Windows Mixed Reality casco conectado al equipo de desarrollo.

## <a name="holographic-remoting-setup"></a>Configuración de Holographic Remoting

1. En primer lugar, debe [instalar la aplicación Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la Microsoft Store en el HoloLens 2
2. Ejecute la aplicación Holographic Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a los que conectarse.
    * Necesitará la versión 2.4 o posterior para trabajar con el complemento OpenXR.

    ![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reproducción de Unity con comunicación remota holográfica

Con Holographic Remoting, puede experimentar la aplicación en HoloLens mientras se ejecuta en el editor de Unity en el equipo. La entrada de mirada, gesto, voz y asignación espacial se envía desde HoloLens al equipo. Los fotogramas representados se envían de vuelta a HoloLens. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.

[!INCLUDE[](includes/unity-play-mode.md)]

La comunicación remota holográfica requiere un equipo rápido Wi-Fi conexión. Puede encontrar más detalles en la documentación [de Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Para obtener mejores resultados, asegúrese de que la aplicación establece correctamente el punto [de enfoque](focus-point-in-unity.md). Esto ayuda a Holographic Remoting a adaptar mejor la escena a la latencia de la conexión inalámbrica.

## <a name="see-also"></a>Consulte también

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
