---
title: Modo de reproducción de Unity
description: Aprenda a usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios de la aplicación en un dispositivo sin necesidad de implementar una aplicación.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor de comunicación remota holográfica, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, modo de reproducción de Unity
ms.openlocfilehash: 9f6c2cafd08fca8a5d60f3fcf5832ee74762e173
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009845"
---
# <a name="unity-play-mode"></a>Modo de reproducción de Unity

Una manera rápida de trabajar en el proyecto de Unity es usar "modo de reproducción", que ejecuta la aplicación localmente en el editor de Unity en el equipo. Unity usa la comunicación remota holográfica para proporcionar una manera rápida de obtener una vista previa del contenido en un dispositivo HoloLens real. El modo de reproducción también puede usarse con un casco de realidad mixta de Windows conectado al equipo de desarrollo.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reproducción de Unity con la comunicación remota holográfica

Con la comunicación remota de Holographic, puedes experimentar tu aplicación en HoloLens mientras se ejecuta en el editor de Unity en tu equipo. La entrada de la asignación de miras, gestos, voz y espaciales se envía desde HoloLens al equipo. Los fotogramas representados se envían a su HoloLens. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.
1. En HoloLens, vaya al **Microsoft Store** e instale la aplicación **[holográfica Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
2. En HoloLens, inicie la aplicación de **reproductor de comunicación remota holográfica** .
3. En Unity, vaya al menú **ventana** , expanda el submenú **XR** y seleccione **emulación holográfica**.
4. Establezca el **modo de emulación** en **remoto en dispositivo**.
5. En **equipo remoto**, escriba la dirección IP de su HoloLens.
6. Seleccione **Conectar**. Debería ver el cambio de estado de la **conexión** a **conectado** y ver que la pantalla aparece en blanco en HoloLens.
7. Seleccione el botón **reproducir** para iniciar el modo de reproducción y experimente la aplicación en su HoloLens.

Holographic Remoting requiere una conexión rápida de PC y Wi-Fi. Puede encontrar más detalles en la documentación de [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Para obtener los mejores resultados, asegúrese de que la aplicación establece correctamente el [punto de enfoque](focus-point-in-unity.md). Esto ayuda a Holographic Remoting a adaptar mejor su escena a la latencia de la conexión inalámbrica.

## <a name="see-also"></a>Consulte también
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
