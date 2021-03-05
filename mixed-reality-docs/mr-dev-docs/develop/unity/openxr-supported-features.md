---
title: Características compatibles con el complemento OpenXR en Unity
description: Descubra las características que OpenXR admite para el desarrollo de la realidad mixta en Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: 0501abe5a417c17283347455ccea8ec6f49a6a45
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230746"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="1c9e8-104">Características admitidas de OpenXR de realidad mixta en Unity</span><span class="sxs-lookup"><span data-stu-id="1c9e8-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="1c9e8-105">El paquete de **Complementos OpenXR de realidad mixta** es una extensión del **complemento OpenXR** de Unity y admite un conjunto de características para los auriculares HoloLens 2 y Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="1c9e8-106">Antes de continuar, asegúrese de que ha instalado **unity 2020,2** o posterior, **OpenXR plugin versión 0.1.3** o posterior y el proyecto de Unity está [configurado para OpenXR](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="1c9e8-107">Lo que se admite</span><span class="sxs-lookup"><span data-stu-id="1c9e8-107">What's supported</span></span>

<span data-ttu-id="1c9e8-108">Actualmente se admiten las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-108">The following features are currently supported:</span></span>

* <span data-ttu-id="1c9e8-109">Admite aplicaciones de UWP para HoloLens 2 y optimizar para el modelo de aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="1c9e8-110">Admite aplicaciones Win32 VR para auriculares con Windows Mixed Reality con los perfiles de controlador más recientes y la comunicación remota de la aplicación holográfica.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="1c9e8-111">Seguimiento de escala mundial con delimitadores y espacio sin enlazar.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="1c9e8-112">[Delimite la API de almacenamiento para conservar los delimitadores](#anchors-and-anchor-persistence) en el almacenamiento local de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="1c9e8-113">Control de [movimiento y interacciones de mano](#motion-controller-and-hand-interactions), incluido el nuevo controlador de HP reverberación G2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="1c9e8-114">Seguimiento de mano articulado mediante 26 uniones y entradas de radio uniones.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="1c9e8-115">Interacción de ojo mirada en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="1c9e8-116">Buscar la cámara de foto/vídeo (PV) en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="1c9e8-117">Captura de realidad mixta mediante la representación de la tercera vista a través de la cámara PV.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="1c9e8-118">Admite ["Play" en HoloLens 2 con la aplicación de comunicación remota holográfica](#holographic-remoting-in-unity-editor-play-mode), lo que permite a los desarrolladores depurar scripts sin compilar e implementar en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="1c9e8-119">Compatible con MRTK Unity 2.5.3 y versiones más recientes a través de la compatibilidad con el [proveedor de MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="1c9e8-120">Compatible con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o posterior.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="1c9e8-121">(Agregado en 0.1.3) Admite la [comunicación remota de la aplicación de escritorio holográfica](#holographic-remoting-in-desktop-app) desde una aplicación independiente de Windows compilada e implementada.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="1c9e8-122">(Agregado en 0.1.4) Admite el [seguimiento del código QR](#qr-codes) en HoloLens2 a través de SpatialGraphNode</span><span class="sxs-lookup"><span data-stu-id="1c9e8-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="1c9e8-123">Configuración de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1c9e8-123">Holographic Remoting setup</span></span>

1. <span data-ttu-id="1c9e8-124">En primer lugar, debe [instalar la aplicación de reproductor de comunicación remota holográfica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde el Microsoft Store en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-124">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="1c9e8-125">Ejecute la aplicación holográfica Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a la que se conectará.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-125">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="1c9e8-126">Necesitará v 2.4 o posterior para trabajar con el complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="1c9e8-126">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de pantalla del reproductor de acceso remoto holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="1c9e8-128">Holographic Remoting en el modo de reproducción del editor de Unity</span><span class="sxs-lookup"><span data-stu-id="1c9e8-128">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="1c9e8-129">Compilar un proyecto de Unity de UWP en un proyecto de Visual Studio y, luego, empaquetarlo e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-129">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="1c9e8-130">Una solución es habilitar la característica de comunicación remota del editor holográfica, que le permite depurar el script de C# mediante el modo "reproducir" directamente en un dispositivo HoloLens 2 a través de la red.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-130">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="1c9e8-131">En este escenario se evita la sobrecarga de crear e implementar un paquete de UWP en un dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-131">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="1c9e8-132">Siga los pasos del [programa de instalación de Holographic Remoting](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="1c9e8-132">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="1c9e8-133">Abra **configuración del proyecto de edición >**, vaya a **Administración de complementos de XR** y active la casilla **conjunto de características de Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="1c9e8-133">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abrir en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-features-img-02.png)

3. <span data-ttu-id="1c9e8-135">Expanda la sección **características** en **OpenXR** y seleccione **Mostrar todas**</span><span class="sxs-lookup"><span data-stu-id="1c9e8-135">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="1c9e8-136">Active la casilla de **comunicación remota del editor holográfica** y escriba la dirección IP que obtiene de la aplicación de acceso remoto holográfica:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-136">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con características resaltadas](images/openxr-features-img-03.png)

<span data-ttu-id="1c9e8-138">Ahora puede hacer clic en el botón "reproducir" para reproducir la aplicación de Unity en la aplicación de acceso remoto holográfica en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-138">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="1c9e8-139">También puede [adjuntar Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts de C# en el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-139">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="1c9e8-140">A partir de la versión 0.1.0, el tiempo de ejecución de la comunicación remota holográfica no admite delimitadores y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-140">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="1c9e8-141">Esta característica está disponible en futuras versiones.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-141">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="1c9e8-142">Holographic Remoting en la aplicación de escritorio</span><span class="sxs-lookup"><span data-stu-id="1c9e8-142">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="1c9e8-143">La compatibilidad con la comunicación remota de aplicaciones independiente de Windows se agregó en la versión del paquete 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-143">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="1c9e8-144">A partir de la versión 0.1.3, esta característica no es compatible con las compilaciones de UWP.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-144">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="1c9e8-145">Siga los pasos del [programa de instalación de Holographic Remoting](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="1c9e8-145">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="1c9e8-146">Abra **configuración del proyecto de edición >**, vaya a **Administración de complementos de XR** y active la casilla **conjunto de características de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-146">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="1c9e8-147">Además, desactive **inicializar XR en el inicio**:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-147">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con Initialize XR on Startup desactivada](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="1c9e8-149">Expanda la sección **características** en **OpenXR** y seleccione **Mostrar todas**</span><span class="sxs-lookup"><span data-stu-id="1c9e8-149">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="1c9e8-150">Active la casilla de verificación remota de la **aplicación Holographic** :</span><span class="sxs-lookup"><span data-stu-id="1c9e8-150">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con la comunicación remota de la aplicación habilitada](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="1c9e8-152">A continuación, escriba código para establecer la configuración de comunicación remota y desencadenar la inicialización de XR.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-152">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="1c9e8-153">La aplicación de ejemplo distribuida con el [complemento Mixed Reality OpenXR](openxr-getting-started.md#hololens-2-samples) contiene AppRemoting.CS, que muestra un escenario de ejemplo para conectarse a una dirección IP específica en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-153">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="1c9e8-154">La implementación de la aplicación de ejemplo en un equipo local en este momento mostrará un campo de entrada de dirección IP con un botón conectar.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-154">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="1c9e8-155">Al escribir una dirección IP y hacer clic en conectar se inicializará XR e intentará conectarse al dispositivo de destino:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-155">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Captura de pantalla de la aplicación de ejemplo que muestra la interfaz de usuario de comunicación remota](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="1c9e8-157">Para escribir código de conexión personalizado, llame a `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` con un rellenado `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-157">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="1c9e8-158">La aplicación de ejemplo expone esto en el inspector y muestra cómo rellenar la dirección IP desde un campo de texto.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-158">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="1c9e8-159">Al llamar a, `Connect` se establecerá la configuración y se inicializará automáticamente XR, motivo por el que debe llamarse como corrutina:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-159">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="1c9e8-160">Mientras se ejecuta, puede obtener el estado de conexión actual con la `AppRemoting.TryGetConnectionState` API y, opcionalmente, desconectar y desinicializar XR mediante `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-160">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="1c9e8-161">Esto podría usarse para desconectarse y volver a conectarse a un dispositivo diferente dentro de la misma sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-161">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="1c9e8-162">La aplicación de ejemplo proporciona un cubo de tappable que desconectará la sesión de comunicación remota si se puntea.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-162">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="1c9e8-163">Migración desde API anteriores</span><span class="sxs-lookup"><span data-stu-id="1c9e8-163">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="1c9e8-164">UnityEngine. XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="1c9e8-164">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="1c9e8-165">En el código de ejemplo de los [documentos de Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="1c9e8-165">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="1c9e8-166">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="1c9e8-166">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="1c9e8-167">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="1c9e8-167">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="1c9e8-168">[N/A: se produce automáticamente cuando se llama a `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="1c9e8-168">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="1c9e8-169">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="1c9e8-169">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="1c9e8-170">XR. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="1c9e8-170">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="1c9e8-171">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="1c9e8-171">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="1c9e8-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` y `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="1c9e8-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="1c9e8-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="1c9e8-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="1c9e8-174">Se pasa a `AppRemoting.Connect` través del `RemotingConfiguration` struct</span><span class="sxs-lookup"><span data-stu-id="1c9e8-174">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="1c9e8-175">Delimitadores y persistencia del delimitador</span><span class="sxs-lookup"><span data-stu-id="1c9e8-175">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="1c9e8-176">El complemento OpenXR de realidad mixta proporciona la funcionalidad básica de delimitador a través de una implementación de ARFoundation **ARAnchorManager** de Unity.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-176">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="1c9e8-177">Para obtener información sobre los conceptos básicos de **ARAnchor** s en ARFoundation, visite el [manual de ARFoundation para el administrador de delimitadores de ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-177">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="1c9e8-178">A partir de la versión 0.1.0, este complemento es compatible con toda la funcionalidad de ARAnchorManager, excepto la creación de delimitadores conectados a un plano, que se publica en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-178">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="1c9e8-179">Persistencia del delimitador y XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="1c9e8-179">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="1c9e8-180">Una API adicional denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-180">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="1c9e8-181">XRAnchorStore es una representación de los delimitadores guardados en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-181">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="1c9e8-182">Los delimitadores se pueden conservar de **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en nuevo **ARAnchors** o eliminarse del almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-182">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="1c9e8-183">Estos delimitadores se guardan y se cargan en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-183">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="1c9e8-184">El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-184">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="1c9e8-185">Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRAnchorSubsystem, el subsistema de ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-185">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="1c9e8-186">Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-186">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="1c9e8-187">Para ver un ejemplo completo de los delimitadores persistentes o no persistentes, consulte el script delimitadores-> delimitadores de ejemplo GameObject y AnchorsSample.cs en la [escena de ejemplo de complemento Mixed Reality OpenXR](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="1c9e8-187">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de pantalla del panel de jerarquías abierto en el editor de Unity con el ejemplo de anclajes resaltado](images/openxr-features-img-04.png)

![Captura de pantalla del panel de inspectores abierta en el editor de Unity con el script de ejemplo de delimitadores resaltado](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="1c9e8-190">Interacciones de controlador de movimiento y mano</span><span class="sxs-lookup"><span data-stu-id="1c9e8-190">Motion controller and hand interactions</span></span>

<span data-ttu-id="1c9e8-191">Para conocer los aspectos básicos sobre las interacciones de la realidad mixta en Unity, visite el [manual de Unity para la entrada de Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-191">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="1c9e8-192">Esta documentación de Unity cubre las asignaciones de entradas específicas del controlador a **InputFeatureUsage** s más generalizadas, cómo se pueden identificar y clasificar las entradas de XR disponibles, cómo leer datos de estas entradas, etc.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-192">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="1c9e8-193">El complemento OpenXR de realidad mixta proporciona perfiles de interacción de entrada adicionales, asignados a **InputFeatureUsage** s estándar, como se detalla a continuación:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-193">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="1c9e8-194">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="1c9e8-194">InputFeatureUsage</span></span> | <span data-ttu-id="1c9e8-195">Controlador de HP reverberación G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="1c9e8-195">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="1c9e8-196">Mano de HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="1c9e8-196">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="1c9e8-197">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="1c9e8-197">primary2DAxis</span></span> | <span data-ttu-id="1c9e8-198">Joystick</span><span class="sxs-lookup"><span data-stu-id="1c9e8-198">Joystick</span></span> | |
| <span data-ttu-id="1c9e8-199">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="1c9e8-199">primary2DAxisClick</span></span> | <span data-ttu-id="1c9e8-200">Joystick: haga clic</span><span class="sxs-lookup"><span data-stu-id="1c9e8-200">Joystick - Click</span></span> | |
| <span data-ttu-id="1c9e8-201">desencadenador</span><span class="sxs-lookup"><span data-stu-id="1c9e8-201">trigger</span></span> | <span data-ttu-id="1c9e8-202">Desencadenador</span><span class="sxs-lookup"><span data-stu-id="1c9e8-202">Trigger</span></span>  | |
| <span data-ttu-id="1c9e8-203">sujeta</span><span class="sxs-lookup"><span data-stu-id="1c9e8-203">grip</span></span> | <span data-ttu-id="1c9e8-204">Sujeta</span><span class="sxs-lookup"><span data-stu-id="1c9e8-204">Grip</span></span> | <span data-ttu-id="1c9e8-205">Puntear o comprimir el aire</span><span class="sxs-lookup"><span data-stu-id="1c9e8-205">Air tap or squeeze</span></span> |
| <span data-ttu-id="1c9e8-206">primaryButton</span><span class="sxs-lookup"><span data-stu-id="1c9e8-206">primaryButton</span></span> | <span data-ttu-id="1c9e8-207">[X/A]-presionar</span><span class="sxs-lookup"><span data-stu-id="1c9e8-207">[X/A] - Press</span></span> | <span data-ttu-id="1c9e8-208">Pulsar en el aire</span><span class="sxs-lookup"><span data-stu-id="1c9e8-208">Air tap</span></span> |
| <span data-ttu-id="1c9e8-209">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="1c9e8-209">secondaryButton</span></span> | <span data-ttu-id="1c9e8-210">[Y/B]-Presione</span><span class="sxs-lookup"><span data-stu-id="1c9e8-210">[Y/B] - Press</span></span> | |
| <span data-ttu-id="1c9e8-211">gripButton</span><span class="sxs-lookup"><span data-stu-id="1c9e8-211">gripButton</span></span> | <span data-ttu-id="1c9e8-212">Agarre: presionar</span><span class="sxs-lookup"><span data-stu-id="1c9e8-212">Grip - Press</span></span> | |
| <span data-ttu-id="1c9e8-213">triggerButton</span><span class="sxs-lookup"><span data-stu-id="1c9e8-213">triggerButton</span></span> | <span data-ttu-id="1c9e8-214">Desencadenador: Presione</span><span class="sxs-lookup"><span data-stu-id="1c9e8-214">Trigger - Press</span></span> | |
| <span data-ttu-id="1c9e8-215">menuButton</span><span class="sxs-lookup"><span data-stu-id="1c9e8-215">menuButton</span></span> | <span data-ttu-id="1c9e8-216">Menú</span><span class="sxs-lookup"><span data-stu-id="1c9e8-216">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="1c9e8-217">Objetivos y planteamiento</span><span class="sxs-lookup"><span data-stu-id="1c9e8-217">Aim and Grip Poses</span></span>

<span data-ttu-id="1c9e8-218">Tiene acceso a dos conjuntos de planteamientos a través de las interacciones de entrada de OpenXR:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-218">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="1c9e8-219">El control tiene que presentar los objetos a mano</span><span class="sxs-lookup"><span data-stu-id="1c9e8-219">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="1c9e8-220">El objetivo plantea la señal del mundo.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-220">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="1c9e8-221">Puede encontrar más información sobre este diseño y las diferencias entre las dos supuestos en la [especificación de OpenXR: subtrazados de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-221">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="1c9e8-222">Las supuestos suministradas por InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** y **DeviceAngularVelocity** representan la representación del **control** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-222">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="1c9e8-223">Los InputFeatureUsages relacionados con los planteamientos de agarre se definen en [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)de Unity.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-223">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="1c9e8-224">Las supuestos suministradas por InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** y **PointerAngularVelocity** representan la representación de **objetivo** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-224">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="1c9e8-225">Estos InputFeatureUsages no se definen en ningún archivo de C# incluido, por lo que deberá definir su propia InputFeatureUsages como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-225">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="1c9e8-226">Hápticos</span><span class="sxs-lookup"><span data-stu-id="1c9e8-226">Haptics</span></span>

<span data-ttu-id="1c9e8-227">Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el [manual de Unity para entrada-hápticos de Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-227">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="1c9e8-228">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="1c9e8-228">QR codes</span></span>

<span data-ttu-id="1c9e8-229">HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-229">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="1c9e8-230">Puede encontrar más detalles en nuestra documentación de [seguimiento de código QR](../platform-capabilities-and-apis/qr-code-tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-230">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="1c9e8-231">Al usar el complemento OpenXR, tome el [ `SpatialGraphNodeId` de la API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) y use la `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para buscar el código QR.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-231">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="1c9e8-232">Como referencia, tenemos un [proyecto de ejemplo de seguimiento de QR en github](https://github.com/yl-msft/QRTracking) con más información detallada sobre el uso de la [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-232">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="1c9e8-233">Novedades próximamente</span><span class="sxs-lookup"><span data-stu-id="1c9e8-233">What's coming soon</span></span>

<span data-ttu-id="1c9e8-234">Los siguientes problemas y las características que faltan se conocen con la **versión 0.1.0** del complemento OpenXR de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-234">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="1c9e8-235">Estamos trabajando en ellos y publicará correcciones y nuevas características en las próximas versiones.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-235">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="1c9e8-236">**ARPlaneSubsystem** todavía no se admite.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-236">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="1c9e8-237">**ARPlaneManager**, **ARRaycastManager** y API relacionada como **ARAnchorManager. AttachAnchor** tampoco se admiten en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-237">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="1c9e8-238">La **persistencia del delimitador** no es compatible aún con la comunicación remota de Holographic, pero está próximamente en un futuro.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-238">**Anchor persistence** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="1c9e8-239">Todavía no se admite el seguimiento de la **malla de mano** y **XRMeshSubsystem** .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-239">**Hand Mesh** tracking and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="1c9e8-240">La compatibilidad con los **anclajes espaciales de Azure** está disponible en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-240">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="1c9e8-241">**ARM64** es la única plataforma admitida para las aplicaciones de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-241">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="1c9e8-242">La plataforma **ARM** está próximamente en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-242">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="1c9e8-243">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="1c9e8-243">Troubleshooting</span></span>

<span data-ttu-id="1c9e8-244">Al suspender y reanudar una aplicación de Unity en HoloLens 2, la aplicación no se puede reanudar correctamente, lo que conduce a 4 puntos de giro en la vista de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-244">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="1c9e8-245">Establezca el **modo de envío de profundidad** en **ninguno** en la configuración del proyecto OpenXR como solución alternativa.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-245">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
