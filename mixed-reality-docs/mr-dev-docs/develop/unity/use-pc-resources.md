---
title: Uso de recursos de PC para encender la aplicación con Holographic Remoting
description: Use recursos de PC, en lugar de depender de la capacidad de procesamiento de la HoloLens, para encender la aplicación con Holographic Remoting.
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, augmented reality, virtual reality, mixed reality headsets, learn, tutorial, getting started, holographic remoting, desktop, preview, debug
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203862"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>Uso de recursos de PC para encender la aplicación con Holographic Remoting

En este artículo se explica el siguiente caso de uso para la comunicación remota holográfica:

-  Quiere que los recursos de un equipo enciendan la aplicación en lugar de depender de los recursos de **HoloLens:** puede crear y compilar una aplicación que tenga la funcionalidad de comunicación remota holográfica. El usuario experimenta la aplicación en el HoloLens, pero la aplicación se ejecuta realmente en un equipo, lo que permite que la aplicación aproveche los recursos más eficaces del equipo. Esto puede resultar especialmente útil si la aplicación tiene modelos o activos de alta resolución y no desea que la velocidad de fotogramas sufra. Esto se llama aplicación _remota de_ comunicación remota holográfica . Las entradas del HoloLens (mirada, gesto, voz y asignación espacial) se envían al equipo, donde el contenido se representa en una vista inmersiva virtual. A continuación, los fotogramas representados se envían al HoloLens.

Este tipo de comunicación remota holográfica también está disponible para los cascos envolventes Windows Mixed Reality (WMR). Esto podría ser útil si, por ejemplo, el casco WMR está conectado a un equipo con experiencia y desea transmitir la aplicación desde un equipo más eficaz al pc.

Para más información sobre la comunicación remota holográfica, consulte [Información general sobre la comunicación remota holográfica.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Tenga en cuenta que también puede usar la comunicación remota holográfica si desea obtener una vista previa [y depurar la aplicación durante el proceso de desarrollo.](preview-and-debug-your-app.md)

## <a name="set-up-holographic-remoting"></a>Configuración de Holographic Remoting

Para usar Holographic Remoting, debe instalar la aplicación [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) desde el Microsoft Store en el HoloLens 2. Como se explica a continuación, después de descargar y ejecutar la aplicación, verá el número de versión y la dirección IP a los que conectarse. **Necesitará la versión 2.4** o posterior para trabajar con el complemento OpenXR.

La comunicación remota holográfica requiere un equipo rápido y Wi-Fi conexión. Puede encontrar más detalles en el artículo de Holographic Remoting Player vinculado anteriormente.

![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en el HoloLens](images/openxr-features-img-01.png)

1. En la barra de menús, **seleccione Editar > Project Configuración**.
1. En la columna del lado izquierdo, seleccione Administración del **complemento XR.**
1. En la **sección XR Plug-in Management** (Administración de complementos **XR), seleccione Microsoft HoloLens grupo** de características y Holographic Remoting remote app feature group (Grupo de características remotas de **holographic Remoting).**
1. Anule la **selección de Initialize XR on Startup (Inicializar XR al iniciar):**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con Inicializar XR al iniciar desactivada](images/001-openxr-features.png)

1. Escriba código para establecer la configuración de comunicación remota y desencadenar la inicialización de XR. La aplicación de ejemplo distribuida con [Mixed Reality complemento OpenXR](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) contiene AppRemoting.cs, que muestra un escenario de ejemplo para conectarse a una dirección IP específica en tiempo de ejecución. La implementación de la aplicación de ejemplo en un equipo local en este momento mostrará un campo de entrada de dirección IP con un botón conectar. Al escribir una dirección IP y hacer clic Conectar inicializará XR e intentará conectarse al dispositivo de destino:

    ![Captura de pantalla de la aplicación de ejemplo que muestra la interfaz de usuario de comunicación remota de aplicaciones de ejemplo](images/openxr-sample-app-remoting.png)

1. Para escribir código de conexión personalizado, llame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` a con un elemento rellenado. `RemotingConfiguration` La aplicación de ejemplo expone esto en el inspector y muestra cómo rellenar la dirección IP desde un campo de texto. Al `Connect` llamar a se establecerá la configuración y se inicializará automáticamente XR, por lo que se debe llamar a ella como una corrotina:

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. Mientras se ejecuta, puede obtener el estado de conexión actual con la API y, opcionalmente, desconectar y `AppRemoting.TryGetConnectionState` des inicializar XR mediante `AppRemoting.Disconnect()` . Esto podría usarse para desconectarse y volver a conectarse a un dispositivo diferente dentro de la misma sesión de la aplicación. La aplicación de ejemplo proporciona un cubo que se puede aplicar y que desconectará la sesión de comunicación remota si se pulsa.

## <a name="migrate-from-previous-holographic-remoting-apis"></a>Migración desde api de comunicación remota holográfica anteriores

Para más información sobre la comunicación remota holográfica, consulte [Información general sobre la comunicación remota holográfica.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine.XR.WSA.HolographicRemoting

En el código de ejemplo de [los documentos de Unity:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)

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
* [Vista previa y depuración de la aplicación con la comunicación remota holográfica y el modo de reproducción](preview-and-debug-your-app.md)
* [Tutorial: Introducción a la comunicación remota holográfica de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Creación de una aplicación de pc de comunicación remota holográfica](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
