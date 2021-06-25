---
title: Holographic Remoting en la aplicación de escritorio
description: Descubra cómo usar Holographic Remoting en una aplicación de escritorio con OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción, comunicación remota holográfica, escritorio
ms.openlocfilehash: b04f7e003cff41ae6970bef71c37231b2475ca75
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906731"
---
# <a name="holographic-remoting-in-desktop-app"></a>Holographic Remoting en la aplicación de escritorio

> [!NOTE]
> La compatibilidad con la comunicación remota de aplicaciones independientes de Windows se agregó en la versión del paquete 0.1.3.
> A partir de la versión 0.1.3, esta característica no admite compilaciones de UWP.

1. Siga los pasos descritos en [Configuración de Holographic Remoting.](unity-play-mode.md#holographic-remoting-setup)
2. Abra **Editar -> configuración** del proyecto, vaya a Administración del complemento **XR** y active la casilla **Windows Mixed Reality conjunto de características.** Además, desactive **Initialize XR on Startup (Inicializar XR al iniciar):**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con Inicializar XR al iniciar desactivada](images/openxr-features-img-02-app.png)

3. Expanda la **sección Características** en **OpenXR** y seleccione **Mostrar todo.**
4. Active la **casilla Holographic App Remoting (Comunicación remota de aplicaciones holográficas):**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la comunicación remota de aplicaciones habilitada](images/openxr-features-img-03-app.png)

5. A continuación, escriba código para establecer la configuración de comunicación remota y desencadenar la inicialización de XR. La aplicación de ejemplo distribuida con el complemento [Mixed Reality OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) contiene AppRemoting.cs, que muestra un escenario de ejemplo para conectarse a una dirección IP específica en tiempo de ejecución. La implementación de la aplicación de ejemplo en un equipo local en este momento mostrará un campo de entrada de dirección IP con un botón conectar. Si escribe una dirección IP y hace clic en Conectar, se inicializará XR e intentará conectarse al dispositivo de destino:

    ![Captura de pantalla de la aplicación de ejemplo que muestra la interfaz de usuario de comunicación remota de aplicaciones de ejemplo](images/openxr-sample-app-remoting.png)

6. Para escribir código de conexión personalizado, llame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` a con un rellenado `RemotingConfiguration` . La aplicación de ejemplo expone esto en el inspector y muestra cómo rellenar la dirección IP desde un campo de texto. Al `Connect` llamar a se establecerá la configuración y se inicializará automáticamente XR, por lo que se debe llamar a esta como corrotina:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Mientras se ejecuta, puede obtener el estado de conexión actual con la API y, opcionalmente, desconectar y `AppRemoting.TryGetConnectionState` des inicializar XR mediante `AppRemoting.Disconnect()` . Esto se podría usar para desconectarse y volver a conectarse a un dispositivo diferente dentro de la misma sesión de la aplicación. La aplicación de ejemplo proporciona un cubo que se puede aplicar y que desconectará la sesión de comunicación remota si se pulsa.

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