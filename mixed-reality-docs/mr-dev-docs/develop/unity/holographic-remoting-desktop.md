---
title: Holographic Remoting en la aplicación de escritorio
description: Descubra cómo usar Holographic Remoting en una aplicación de escritorio con OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción, comunicación remota holográfica, escritorio
ms.openlocfilehash: 18557af1f08ea05715b92b5072460871bb05a329
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333427"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="08605-104">Holographic Remoting en la aplicación de escritorio</span><span class="sxs-lookup"><span data-stu-id="08605-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="08605-105">La compatibilidad con la comunicación remota de aplicaciones independientes de Windows se agregó en la versión del paquete 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="08605-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="08605-106">A partir de la versión 0.1.3, esta característica no admite compilaciones de UWP.</span><span class="sxs-lookup"><span data-stu-id="08605-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="08605-107">Siga los pasos descritos en [Configuración de Holographic Remoting.](unity-play-mode.md#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="08605-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="08605-108">Abra **Editar -> configuración** del proyecto, vaya a Administración del complemento **XR** y active Windows Mixed Reality conjunto de **características.**</span><span class="sxs-lookup"><span data-stu-id="08605-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="08605-109">Además, desactive **Initialize XR on Startup (Inicializar XR al iniciar):**</span><span class="sxs-lookup"><span data-stu-id="08605-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con Inicializar XR al iniciar desactivada](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="08605-111">Expanda la **sección Características** en **OpenXR** y seleccione **Mostrar todo.**</span><span class="sxs-lookup"><span data-stu-id="08605-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="08605-112">Active la **casilla Holographic App Remoting (Comunicación remota de aplicaciones holográficas):**</span><span class="sxs-lookup"><span data-stu-id="08605-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la comunicación remota de aplicaciones habilitada](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="08605-114">A continuación, escriba código para establecer la configuración de comunicación remota y desencadenar la inicialización de XR.</span><span class="sxs-lookup"><span data-stu-id="08605-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="08605-115">La aplicación de ejemplo distribuida con [Mixed Reality complemento OpenXR](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contiene AppRemoting.cs, que muestra un escenario de ejemplo para conectarse a una dirección IP específica en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="08605-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="08605-116">La implementación de la aplicación de ejemplo en un equipo local en este momento mostrará un campo de entrada de dirección IP con un botón conectar.</span><span class="sxs-lookup"><span data-stu-id="08605-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="08605-117">Al escribir una dirección IP y hacer clic en Conectar, se inicializará XR e intentará conectarse al dispositivo de destino:</span><span class="sxs-lookup"><span data-stu-id="08605-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Captura de pantalla de la aplicación de ejemplo que muestra la interfaz de usuario de comunicación remota de aplicaciones de ejemplo](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="08605-119">Para escribir código de conexión personalizado, llame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` a con un elemento rellenado. `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="08605-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="08605-120">La aplicación de ejemplo expone esto en el inspector y muestra cómo rellenar la dirección IP desde un campo de texto.</span><span class="sxs-lookup"><span data-stu-id="08605-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="08605-121">Al `Connect` llamar a se establecerá la configuración y se inicializará automáticamente XR, por lo que se debe llamar a ella como una corrotina:</span><span class="sxs-lookup"><span data-stu-id="08605-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="08605-122">Mientras se ejecuta, puede obtener el estado de conexión actual con la API y, opcionalmente, desconectar y `AppRemoting.TryGetConnectionState` des inicializar XR mediante `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="08605-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="08605-123">Esto se podría usar para desconectarse y volver a conectarse a un dispositivo diferente dentro de la misma sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="08605-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="08605-124">La aplicación de ejemplo proporciona un cubo que se puede aplicar y que desconectará la sesión de comunicación remota si se pulsa.</span><span class="sxs-lookup"><span data-stu-id="08605-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="08605-125">Migración desde API anteriores</span><span class="sxs-lookup"><span data-stu-id="08605-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="08605-126">UnityEngine.XR.WSA.HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="08605-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="08605-127">En el código de ejemplo [de los documentos de Unity:](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)</span><span class="sxs-lookup"><span data-stu-id="08605-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="08605-128">Xr. Wsa. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="08605-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="08605-129">OpenXR.Remoting.AppRemoting</span><span class="sxs-lookup"><span data-stu-id="08605-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="08605-130">[N/A: Se produce automáticamente al llamar a `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="08605-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="08605-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="08605-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="08605-132">Xr. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="08605-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="08605-133">OpenXR.Remoting.AppRemoting</span><span class="sxs-lookup"><span data-stu-id="08605-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="08605-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` y `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="08605-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="08605-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="08605-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="08605-136">Pasado a `AppRemoting.Connect` a través de la `RemotingConfiguration` estructura</span><span class="sxs-lookup"><span data-stu-id="08605-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`