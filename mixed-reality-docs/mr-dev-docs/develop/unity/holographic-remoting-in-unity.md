---
title: Comunicación remota holográfica en Unity
description: Descubra cómo usar la comunicación remota holográfica en una aplicación de escritorio y el modo de reproducción de Unity con OpenXR.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, augmented reality, virtual reality, mixed reality headsets, learn, tutorial, getting started, holographic remoting, desktop
ms.openlocfilehash: 0b18bf4a187190da3ef9d17fd87f2c42feaa271210345330887ce618b49a0442
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192221"
---
# <a name="holographic-remoting-in-unity"></a>Comunicación remota holográfica en Unity

> [!NOTE]
> Windows La compatibilidad con la comunicación remota de aplicaciones independientes se agregó en la versión del paquete 0.1.3.
> A partir de la versión 0.1.3, esta característica no admite compilaciones de UWP.

[Aprenda los conceptos básicos de la comunicación remota holográfica.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Puede usar Holographic Remoting para transmitir contenido holográfico a su HoloLens 2 en tiempo real. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo. 

Antes de empezar, es importante comprender las dos opciones principales en Unity:
* **Holographic Remoting in Unity Play mode**(Comunicación remota holográfica en modo de reproducción de Unity): ejecute la aplicación localmente en el editor de Unity en el equipo en modo de reproducción para proporcionar una manera rápida de obtener una vista previa del contenido en un HoloLens 2. El modo de reproducción también se puede usar con un Windows Mixed Reality casco conectado al equipo de desarrollo.
* **Comunicación remota holográfica** desde un archivo de compilación de Unity: ejecute la aplicación desde una aplicación remota de Comunicación remota holográfica de Unity que haya exportado al escritorio a su HoloLens 2. Esto puede resultar útil si la aplicación tiene modelos o recursos de alta resolución. la GPU de escritorio controla la representación antes de llegar al HoloLens 2.

## <a name="holographic-remoting-setup"></a>Configuración de Holographic Remoting

Independientemente de la ruta que tome con Holographic Remoting, debe instalar la aplicación [Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la Microsoft Store en la HoloLens 2.

Una vez descargado, ejecute la aplicación Holographic Remoting Player en el HoloLens 2 y verá el número de versión y la dirección IP a los que conectarse. **Necesitará la versión 2.4** o posterior para trabajar con el complemento OpenXR .

![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reproducción de Unity con comunicación remota holográfica

[!INCLUDE[](includes/unity-play-mode.md)]

La comunicación remota holográfica requiere un equipo rápido Wi-Fi conexión. Puede encontrar más detalles en la documentación [de Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Para obtener mejores resultados, asegúrese de que la aplicación establece correctamente el punto [de enfoque](focus-point-in-unity.md). Esto ayuda a Holographic Remoting a adaptar la escena a la latencia de la conexión inalámbrica.

## <a name="holographic-remoting-from-a-remote-application"></a>Comunicación remota holográfica desde una aplicación remota

1. En la barra de menús, **seleccione Editar > Project Configuración**.
1. En la columna del lado izquierdo, seleccione **Administración del complemento XR.**
1. En la **sección XR Plug-in Management (Administración** de complementos XR), seleccione **Microsoft HoloLens grupo** de características y Holographic Remoting remote app feature group (Grupo de características de aplicaciones remotas **de Holographic Remoting).**
1. Anule la **selección de Initialize XR on Startup (Inicializar XR al iniciar):**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con Inicializar XR al iniciar desactivada](images/001-openxr-features.png)

1. Escriba código para establecer la configuración de comunicación remota y desencadenar la inicialización de XR. La aplicación de ejemplo distribuida con el complemento [Mixed Reality OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) contiene AppRemoting.cs, que muestra un escenario de ejemplo para conectarse a una dirección IP específica en tiempo de ejecución. La implementación de la aplicación de ejemplo en un equipo local en este momento mostrará un campo de entrada de dirección IP con un botón conectar. Al escribir una dirección IP y hacer clic Conectar inicializará XR e intentará conectarse al dispositivo de destino:

    ![Captura de pantalla de la aplicación de ejemplo que muestra la interfaz de usuario de comunicación remota de aplicaciones de ejemplo](images/openxr-sample-app-remoting.png)

1. Para escribir código de conexión personalizado, llame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` a con un rellenado `RemotingConfiguration` . La aplicación de ejemplo expone esto en el inspector y muestra cómo rellenar la dirección IP desde un campo de texto. Al `Connect` llamar a se establecerá la configuración y se inicializará automáticamente XR, por lo que se debe llamar a esta como corrotina:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Mientras se ejecuta, puede obtener el estado de conexión actual con la API y, opcionalmente, desconectar y `AppRemoting.TryGetConnectionState` des inicializar XR mediante `AppRemoting.Disconnect()` . Esto se podría usar para desconectarse y volver a conectarse a un dispositivo diferente dentro de la misma sesión de la aplicación. La aplicación de ejemplo proporciona un cubo que se puede aplicar y que desconectará la sesión de comunicación remota si se pulsa.

### <a name="migration-from-previous-apis"></a>Migración desde API anteriores

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine.XR.WSA.HolographicRemoting

En el código de ejemplo [de los documentos de Unity:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)

| Xr. Wsa. HolographicRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A: Se produce automáticamente al llamar a `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine.XR.WindowsMR.WindowsMRRemoting

| Xr. WindowsMR.WindowsMRRemoting | OpenXR.Remoting.AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` y `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Pasado a `AppRemoting.Connect` a través de la `RemotingConfiguration` estructura |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="see-also"></a>Consulte también

* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Tutorial: Introducción a la comunicación remota holográfica de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Creación de una aplicación de PC de comunicación remota holográfica](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
