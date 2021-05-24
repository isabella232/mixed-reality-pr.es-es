---
title: Modo de reproducción de Unity
description: Obtenga información sobre cómo usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios de la aplicación en un dispositivo sin implementar una aplicación.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor de comunicación remota holográfica, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, modo de juego de Unity
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333426"
---
# <a name="unity-play-mode"></a>Modo de reproducción de Unity

Una manera rápida de trabajar en el proyecto de Unity es usar el "Modo de reproducción", que ejecuta la aplicación localmente en el editor de Unity en el equipo. Unity usa Holographic Remoting para proporcionar una forma rápida de obtener una vista previa del contenido en un dispositivo HoloLens real. El modo de reproducción también se puede usar con un Windows Mixed Reality casco conectado al equipo de desarrollo.

## <a name="holographic-remoting-setup"></a>Configuración de comunicación remota holográfica

1. En primer lugar, debe [instalar la aplicación Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde el Microsoft Store en el HoloLens 2
2. Ejecute la aplicación Holographic Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a los que conectarse.
    * Necesitará la versión 2.4 o posterior para trabajar con el complemento OpenXR.

    ![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Comunicación remota holográfica en el modo de reproducción del Editor de Unity

Compilar un proyecto de Unity para UWP en Visual Studio proyecto y, a continuación, empaquetar e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo. Una solución es habilitar la característica de comunicación remota del editor holográfico, que le permite depurar el script de C# mediante el modo "Reproducir" directamente en un dispositivo HoloLens 2 a través de la red. Este escenario evita la sobrecarga de compilar e implementar un paquete de UWP en un dispositivo remoto.

1. Siga los pasos descritos en [Configuración de Holographic Remoting.](#holographic-remoting-setup)
2. Abra **Windows > XR > comunicación remota del editor de OpenXR:**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la administración del complemento XR resaltada](images/openxr-features-img-02.png)

3. Introduzca la dirección IP que obtiene de la aplicación Holographic Remoting y seleccione **Habilitar comunicación remota del editor.**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con características resaltadas](images/openxr-features-img-03.png)

Ahora puede hacer clic en el botón "Play" (Reproducir) para reproducir la aplicación unity en la aplicación Holographic Remoting en HoloLens. También puede adjuntar [Visual Studio a Unity para](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) depurar scripts de C# en el modo de reproducción.

> [!NOTE]
> A partir de la versión 0.1.0, el entorno de ejecución de comunicación remota holográfica no admite anclajes y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica se va a publicar en futuras versiones.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reproducción de Unity con comunicación remota holográfica

Con Holographic Remoting, puede experimentar la aplicación en HoloLens mientras se ejecuta en el editor de Unity en el equipo. La entrada de mirada, gesto, voz y asignación espacial se envía desde HoloLens al equipo. Los fotogramas representados se envían de vuelta a HoloLens. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.
1. En HoloLens, vaya al Microsoft Store **e** instale la **[aplicación Holographic Remoting Player.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
2. En HoloLens, inicie la **aplicación Holographic Remoting Player.**
3. En Unity, vaya al menú **Ventana,** expanda el submenú **XR** y seleccione **Emulación holográfica.**
4. Establezca **Modo de emulación** **en Remoto en Dispositivo.**
5. En **Equipo remoto,** escriba la dirección IP de HoloLens.
6. Seleccione **Conectar**. Debería ver el cambio **de Estado de** conexión a Conectado **y** ver que la pantalla se deja en blanco en HoloLens.
7. Seleccione el **botón Reproducir** para iniciar el modo de reproducción y experimentar la aplicación en HoloLens.

La comunicación remota holográfica requiere un equipo rápido Wi-Fi conexión. Puede encontrar más detalles en la documentación [de Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Para obtener mejores resultados, asegúrese de que la aplicación establece correctamente el punto [de enfoque](focus-point-in-unity.md). Esto ayuda a Holographic Remoting a adaptar mejor la escena a la latencia de la conexión inalámbrica.

## <a name="see-also"></a>Consulte también
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
