---
title: Modo de reproducción de Unity
description: Obtenga información sobre cómo usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios de la aplicación en un dispositivo sin implementar una aplicación.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor de comunicación remota holográfica, HoloLens, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, modo de juego de Unity
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547104"
---
# <a name="unity-play-mode"></a>Modo de reproducción de Unity

Una manera rápida de trabajar en el proyecto de Unity es usar el "Modo de reproducción", que ejecuta la aplicación localmente en el editor de Unity en el equipo. Unity usa Holographic Remoting para proporcionar una forma rápida de obtener una vista previa del contenido en un dispositivo HoloLens real. El modo de reproducción también se puede usar con un Windows Mixed Reality casco conectado al equipo de desarrollo.

## <a name="holographic-remoting-setup"></a>Configuración de la comunicación remota holográfica

1. En primer lugar, debe [instalar la aplicación Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la Microsoft Store en el HoloLens 2
2. Ejecute la aplicación Holographic Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a los que conectarse.
    * Necesitará la versión 2.4 o posterior para trabajar con el complemento OpenXR.

    ![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Comunicación remota holográfica en el modo de reproducción del Editor de Unity

Compilar un proyecto de Unity para UWP Visual Studio proyecto y, a continuación, empaquetar e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo. Una solución es habilitar la característica de comunicación remota del editor holográfico, que le permite depurar el script de C# mediante el modo "Reproducir" directamente en un dispositivo HoloLens 2 a través de la red. Este escenario evita la sobrecarga de compilar e implementar un paquete de UWP en un dispositivo remoto.

1. Siga los pasos descritos en [Configuración de Holographic Remoting.](#holographic-remoting-setup)
2. Abra **Windows > XR > comunicación remota del editor de OpenXR:**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la administración del complemento XR resaltada](images/openxr-features-img-02.png)

3. Introduzca la dirección IP que obtiene de la aplicación Holographic Remoting y seleccione **Habilitar comunicación remota del editor.**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con características resaltadas](images/openxr-features-img-03.png)

Ahora puede hacer clic en el botón "Play" (Reproducir) para reproducir la aplicación unity en la aplicación Holographic Remoting en HoloLens. También puede adjuntar [Visual Studio a Unity para](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) depurar scripts de C# en el modo de reproducción.

> [!NOTE]
> A partir de la versión 0.1.0, el entorno de ejecución de comunicación remota holográfica no admite delimitadores y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica se va a publicar en futuras versiones.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reproducción de Unity con comunicación remota holográfica

Con Holographic Remoting, puede experimentar la aplicación en HoloLens mientras se ejecuta en el editor de Unity en el equipo. La entrada de mirada, gesto, voz y asignación espacial se envía desde HoloLens al equipo. A continuación, los fotogramas representados se envían de vuelta a HoloLens. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.

[!INCLUDE[](includes/unity-play-mode.md)]

La comunicación remota holográfica requiere un equipo rápido y Wi-Fi conexión. Puede encontrar más detalles en la documentación [de Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Para obtener mejores resultados, asegúrese de que la aplicación establece correctamente el punto [de enfoque](focus-point-in-unity.md). Esto ayuda a Holographic Remoting a adaptar mejor la escena a la latencia de la conexión inalámbrica.

## <a name="see-also"></a>Consulte también

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
