---
title: Holographic Remoting en la aplicación de escritorio
description: Descubra cómo usar Holographic Remoting en una aplicación de escritorio con OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción, comunicación remota de Holographic, escritorio
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624328"
---
# <a name="holographic-remoting-in-desktop-app"></a>Holographic Remoting en la aplicación de escritorio

> [!NOTE]
> La compatibilidad con la comunicación remota de aplicaciones independiente de Windows se agregó en la versión del paquete 0.1.3.
> A partir de la versión 0.1.3, esta característica no es compatible con las compilaciones de UWP.

1. Siga los pasos del [programa de instalación de Holographic Remoting](openxr-supported-features.md#holographic-remoting-setup)
2. Abra **configuración del proyecto de edición >**, vaya a **Administración de complementos de XR** y active la casilla **conjunto de características de Windows Mixed Reality** . Además, desactive **inicializar XR en el inicio**:

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con Initialize XR on Startup desactivada](images/openxr-features-img-02-app.png)

3. Expanda la sección **características** en **OpenXR** y seleccione **Mostrar todas**
4. Active la casilla de verificación remota de la **aplicación Holographic** :

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con la comunicación remota de la aplicación habilitada](images/openxr-features-img-03-app.png)

5. A continuación, escriba código para establecer la configuración de comunicación remota y desencadenar la inicialización de XR. La aplicación de ejemplo distribuida con el [complemento Mixed Reality OpenXR](openxr-getting-started.md#hololens-2-samples) contiene AppRemoting.CS, que muestra un escenario de ejemplo para conectarse a una dirección IP específica en tiempo de ejecución. La implementación de la aplicación de ejemplo en un equipo local en este momento mostrará un campo de entrada de dirección IP con un botón conectar. Al escribir una dirección IP y hacer clic en conectar se inicializará XR e intentará conectarse al dispositivo de destino:

    ![Captura de pantalla de la aplicación de ejemplo que muestra la interfaz de usuario de comunicación remota](images/openxr-sample-app-remoting.png)

6. Para escribir código de conexión personalizado, llame a `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` con un rellenado `RemotingConfiguration` . La aplicación de ejemplo expone esto en el inspector y muestra cómo rellenar la dirección IP desde un campo de texto. Al llamar a, `Connect` se establecerá la configuración y se inicializará automáticamente XR, motivo por el que debe llamarse como corrutina:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. Mientras se ejecuta, puede obtener el estado de conexión actual con la `AppRemoting.TryGetConnectionState` API y, opcionalmente, desconectar y desinicializar XR mediante `AppRemoting.Disconnect()` . Esto podría usarse para desconectarse y volver a conectarse a un dispositivo diferente dentro de la misma sesión de la aplicación. La aplicación de ejemplo proporciona un cubo de tappable que desconectará la sesión de comunicación remota si se puntea.

### <a name="migration-from-previous-apis"></a>Migración desde API anteriores

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR. WSA. HolographicRemoting

En el código de ejemplo de los [documentos de Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):

| XR. WSA. HolographicRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A: se produce automáticamente cuando se llama a `AppRemoting.Connect` ]  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. WindowsMR. WindowsMRRemoting

| XR. WindowsMR.WindowsMRRemoting | OpenXR. Remoting. AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` y `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | Se pasa a `AppRemoting.Connect` través del `RemotingConfiguration` struct |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`