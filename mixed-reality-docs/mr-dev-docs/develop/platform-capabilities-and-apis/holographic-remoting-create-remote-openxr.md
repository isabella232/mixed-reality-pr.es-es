---
title: Escritura de una aplicación remota holográfica Remoting (OpenXR)
description: Al crear una aplicación remota Holographic Remoting, el contenido remoto, que se representa en un equipo remoto, se puede transmitir a HoloLens 2. En este artículo se describe cómo se puede lograr esto.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, NuGet
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469520"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="d4e19-105">Escritura de una aplicación remota de Holographic Remoting mediante la API de OpenXR</span><span class="sxs-lookup"><span data-stu-id="d4e19-105">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="d4e19-106">En este documento se describe la creación de una aplicación remota para los auriculares HoloLens 2 y Windows Mixed Reality mediante la [API de OpenXR](../native/openxr.md).</span><span class="sxs-lookup"><span data-stu-id="d4e19-106">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="d4e19-107">Las aplicaciones remotas para **HoloLens (1ª generación)** deben usar el paquete NuGet versión **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="d4e19-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="d4e19-108">Esto implica que las aplicaciones remotas escritas para HoloLens 2 no son compatibles con HoloLens 1 y viceversa.</span><span class="sxs-lookup"><span data-stu-id="d4e19-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="d4e19-109">La documentación de HoloLens 1 se puede encontrar [aquí](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="d4e19-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="d4e19-110">Mediante la creación de una aplicación remota de Holographic Remoting, el contenido remoto que se representa en un equipo remoto se puede transmitir a HoloLens 2 y a dispositivos envolventes, como los auriculares de realidad mixta de Windows.</span><span class="sxs-lookup"><span data-stu-id="d4e19-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2 and immersive devices like Windows Mixed Reality headsets.</span></span> <span data-ttu-id="d4e19-111">En este artículo se describe cómo se puede lograr esto.</span><span class="sxs-lookup"><span data-stu-id="d4e19-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="d4e19-112">Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="d4e19-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="d4e19-113">Holographic Remoting permite a una aplicación destinarse a HoloLens 2 y a auriculares de realidad mixta de Windows con contenido holográfica representada en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, lo que permite el acceso a más recursos del sistema y permite integrar [vistas envolventes](../../design/app-views.md) remotas en el software de PC de escritorio existente.</span><span class="sxs-lookup"><span data-stu-id="d4e19-113">Holographic remoting allows an app to target HoloLens 2 and Windows Mixed Reality headsets with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="d4e19-114">Una aplicación remota recibe un flujo de datos de entrada de HoloLens 2, representa el contenido en una vista envolvente virtual y vuelve a transmitir los fotogramas de contenido a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d4e19-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="d4e19-115">La conexión se realiza mediante Wi-Fi estándar.</span><span class="sxs-lookup"><span data-stu-id="d4e19-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="d4e19-116">Holographic Remoting se agrega a una aplicación de escritorio o UWP a través de un paquete NuGet.</span><span class="sxs-lookup"><span data-stu-id="d4e19-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="d4e19-117">Se requiere código adicional que controla la conexión y se representa en una vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="d4e19-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="d4e19-118">Una conexión remota típica tendrá un mínimo de 50 ms de latencia.</span><span class="sxs-lookup"><span data-stu-id="d4e19-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="d4e19-119">La aplicación de reproducción puede informar de la latencia en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="d4e19-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4e19-120">Prerrequisitos</span><span class="sxs-lookup"><span data-stu-id="d4e19-120">Prerequisites</span></span>

<span data-ttu-id="d4e19-121">Un buen punto de partida es una aplicación de escritorio o UWP basada en OpenXR en funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="d4e19-121">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="d4e19-122">Para obtener más información, consulte [Introducción a OpenXR](../native/openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="d4e19-122">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="d4e19-123">Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="d4e19-123">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="d4e19-124">Se admite el uso de un apartamento de un [solo subproceso](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) , pero se producirá un rendimiento poco óptimo y posiblemente se produzca una intermitencia durante la reproducción.</span><span class="sxs-lookup"><span data-stu-id="d4e19-124">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="d4e19-125">Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartamento multiproceso es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="d4e19-125">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="d4e19-126">Obtención del paquete NuGet de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="d4e19-126">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="d4e19-127">Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4e19-127">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="d4e19-128">Abra el proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4e19-128">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="d4e19-129">Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="d4e19-129">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="d4e19-130">En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="d4e19-130">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="d4e19-131">Seleccione **Microsoft. Holographic. Remoting. OpenXr**, asegúrese de elegir la versión **2. x. x** más reciente y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="d4e19-131">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="d4e19-132">Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="d4e19-132">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="d4e19-133">El siguiente cuadro de diálogo que aparece es el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="d4e19-133">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="d4e19-134">Haga clic en **acepto para aceptar el contrato de licencia** .</span><span class="sxs-lookup"><span data-stu-id="d4e19-134">Click on **I Accept** to accept the license agreement.</span></span>
7. <span data-ttu-id="d4e19-135">Repita los pasos 3 a 6 para los siguientes paquetes NuGet: OpenXR. Headers, OpenXR. Loader</span><span class="sxs-lookup"><span data-stu-id="d4e19-135">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="d4e19-136">La versión **1. x.** x del paquete NuGet sigue estando disponible para los desarrolladores que quieran tener como destino HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="d4e19-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="d4e19-137">Para obtener más información, consulte incorporación de la [comunicación remota holográfica (HoloLens (1º generación))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="d4e19-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="d4e19-138">Seleccione el tiempo de ejecución de OpenXR de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="d4e19-138">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="d4e19-139">El primer paso que debe hacer en la aplicación remota es seleccionar el entorno de ejecución de OpenXR de Holographic Remoting, que forma parte del paquete NuGet Microsoft. Holographic. Remoting. OpenXr.</span><span class="sxs-lookup"><span data-stu-id="d4e19-139">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="d4e19-140">Para ello, establezca la variable de ```XR_RUNTIME_JSON``` entorno en la ruta de acceso del RemotingXR.jsen el archivo dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d4e19-140">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="d4e19-141">El cargador de OpenXR usa esta variable de entorno para no usar el tiempo de ejecución de OpenXR predeterminado del sistema, sino que se redirigirá al tiempo de ejecución de Holographic Remoting OpenXR.</span><span class="sxs-lookup"><span data-stu-id="d4e19-141">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="d4e19-142">Al usar el paquete de NuGet Microsoft. Holographic. Remoting. OpenXr, el RemotingXR.jsen el archivo se copia automáticamente durante la compilación en la carpeta de salida, por lo que la selección del tiempo de ejecución de OpenXR suele tener el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="d4e19-142">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, thus the OpenXR runtime selection typically looks as follows.</span></span>

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="d4e19-143">Creación de XrInstance con la extensión Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="d4e19-143">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="d4e19-144">Se supone que es el primer paso que debe hacer una aplicación OpenXR típica para seleccionar las extensiones OpenXR y crear un XrInstance.</span><span class="sxs-lookup"><span data-stu-id="d4e19-144">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create a XrInstance.</span></span> <span data-ttu-id="d4e19-145">La especificación OpenXR Core no proporciona ninguna API específica de la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="d4e19-145">The OpenXR core specification does not provide any remoting specific API.</span></span> <span data-ttu-id="d4e19-146">Por ese motivo, Holographic Remoting incluye su propia extensión OpenXR denominada ```XR_MSFT_holographic_remoting``` .</span><span class="sxs-lookup"><span data-stu-id="d4e19-146">For that reason Holographic Remoting introduces it's own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="d4e19-147">Asegúrese de que, al llamar a xrCreateInstance, ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` está incluido en XrInstanceCreateInfo.</span><span class="sxs-lookup"><span data-stu-id="d4e19-147">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="d4e19-148">De forma predeterminada, el contenido representado de la aplicación solo se transmite al reproductor de comunicación remota holográfica que se ejecuta en una HoloLens 2 o en un casco de realidad mixta de Windows.</span><span class="sxs-lookup"><span data-stu-id="d4e19-148">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="d4e19-149">Para mostrar también el contenido representado en el equipo remoto, a través de una cadena de intercambio de una ventana, por ejemplo, Holographic Remoting proporciona una segunda extensión OpenXR denominada ```XR_MSFT_holographic_remoting_frame_mirroring``` .</span><span class="sxs-lookup"><span data-stu-id="d4e19-149">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="d4e19-150">Asegúrese de habilitar también esta extensión mediante ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` en caso de que desee usar esa funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="d4e19-150">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d4e19-151">Para obtener información acerca de la API de extensión OpenXR de Holographic Remoting, consulte la [especificación](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) que se encuentra en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="d4e19-151">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="d4e19-152">Conexión al dispositivo</span><span class="sxs-lookup"><span data-stu-id="d4e19-152">Connect to the device</span></span>

<span data-ttu-id="d4e19-153">Después de que la aplicación remota haya creado el XrInstance y consultado el XrSystemId a través de xrGetSystem se puede establecer una conexión con el dispositivo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="d4e19-153">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="d4e19-154">El tiempo de ejecución de OpenXR de Holographic Remoting solo puede proporcionar datos específicos del dispositivo, como configuraciones de vista o modos de fusión de entorno, una vez establecida una conexión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-154">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="d4e19-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` y le ```xrGetSystemProperties``` proporcionará los valores predeterminados, que coinciden con lo que normalmente obtendría si se conecta a un reproductor que se ejecuta en una HoloLens 2, antes de estar totalmente conectado.</span><span class="sxs-lookup"><span data-stu-id="d4e19-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="d4e19-156">Se recomienda no llamar a estos métodos antes de que se haya establecido una conexión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-156">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="d4e19-157">La sugerencia usa estos métodos después de que XrSession se haya creado correctamente y el estado de sesión sea al menos XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="d4e19-157">The suggestion is use these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="d4e19-158">Las propiedades generales como velocidad de bits máxima, audio habilitado, códec de vídeo o resolución de flujo de búfer de profundidad se pueden configurar a través ```xrRemotingSetContextPropertiesMSFT``` de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="d4e19-158">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="d4e19-159">La conexión puede realizarse de una de estas dos maneras.</span><span class="sxs-lookup"><span data-stu-id="d4e19-159">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="d4e19-160">La aplicación remota se conecta al reproductor que se ejecuta en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d4e19-160">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="d4e19-161">El reproductor que se ejecuta en el dispositivo se conecta a la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="d4e19-161">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="d4e19-162">Para establecer una conexión desde la aplicación remota al dispositivo del reproductor, llame al ```xrRemotingConnectMSFT``` método especificando el nombre de host y el puerto a través de la  ```XrRemotingConnectInfoMSFT``` estructura.</span><span class="sxs-lookup"><span data-stu-id="d4e19-162">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="d4e19-163">El puerto que usa el reproductor de comunicación remota holográfica es **8265**.</span><span class="sxs-lookup"><span data-stu-id="d4e19-163">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="d4e19-164">La escucha de conexiones entrantes en la aplicación remota se puede realizar mediante una llamada al ```xrRemotingListenMSFT``` método.</span><span class="sxs-lookup"><span data-stu-id="d4e19-164">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="d4e19-165">Tanto el puerto de enlace como el puerto de transporte se pueden especificar a través de la ```XrRemotingListenInfoMSFT``` estructura.</span><span class="sxs-lookup"><span data-stu-id="d4e19-165">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="d4e19-166">El puerto de enlace se usa para el protocolo de enlace inicial.</span><span class="sxs-lookup"><span data-stu-id="d4e19-166">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="d4e19-167">A continuación, los datos se envían a través del puerto de transporte.</span><span class="sxs-lookup"><span data-stu-id="d4e19-167">The data is then send over the transport port.</span></span> <span data-ttu-id="d4e19-168">De forma predeterminada, se usan **8265** y **8266** .</span><span class="sxs-lookup"><span data-stu-id="d4e19-168">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="d4e19-169">El estado de conexión debe desconectarse cuando se llama a ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="d4e19-169">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="d4e19-170">Puede obtener el estado de conexión en cualquier momento después de haber creado un XrInstance y de consultar el XrSystemId a través de ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="d4e19-170">You can get the connection state at any point after you have created a XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="d4e19-171">Los Estados de conexión disponibles son:</span><span class="sxs-lookup"><span data-stu-id="d4e19-171">Available connection states are:</span></span>
- <span data-ttu-id="d4e19-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="d4e19-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="d4e19-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="d4e19-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="d4e19-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="d4e19-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d4e19-175">```xrRemotingConnectMSFT``````xrRemotingListenMSFT```se debe llamar a o antes de intentar crear un XrSession a través de xrCreateSession.</span><span class="sxs-lookup"><span data-stu-id="d4e19-175">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="d4e19-176">Si intenta crear un XrSession mientras el estado de conexión es ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` la creación de la sesión se realizará correctamente, pero el estado de la sesión pasará inmediatamente a XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="d4e19-176">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="d4e19-177">La implementación de Holographic Remoting de ```xrCreateSession``` admite la espera de que se establezca una conexión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-177">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="d4e19-178">Puede llamar a ```xrRemotingConnectMSFT``` o ```xrRemotingListenMSFT``` inmediatamente después de una llamada a ```xrCreateSession``` que se bloqueará y esperará a que se establezca una conexión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-178">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to ```xrCreateSession``` which will block and wait for a connection to be established.</span></span> <span data-ttu-id="d4e19-179">El tiempo de espera se ha fijado en 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="d4e19-179">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="d4e19-180">Si se puede establecer una conexión en este momento, la creación de XrSession se realizará correctamente y el estado de la sesión pasará a XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="d4e19-180">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="d4e19-181">En caso de que no se pueda establecer una conexión, la creación de la sesión también se realiza correctamente, pero pasa inmediatamente a XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="d4e19-181">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="d4e19-182">En general, el estado de conexión es par con el estado XrSession.</span><span class="sxs-lookup"><span data-stu-id="d4e19-182">In general the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="d4e19-183">Cualquier cambio en el estado de conexión también afecta al estado de la sesión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-183">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="d4e19-184">Por ejemplo, si el estado de conexión cambia de `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` a, ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` el estado de la sesión cambiará también a XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="d4e19-184">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="d4e19-185">Controlar eventos específicos de la comunicación remota</span><span class="sxs-lookup"><span data-stu-id="d4e19-185">Handling Remoting specific events</span></span>

<span data-ttu-id="d4e19-186">El tiempo de ejecución de OpenXR de Holographic Remoting expone tres eventos que son importantes para supervisar el estado de una conexión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-186">The Holographic Remoting OpenXR runtime exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="d4e19-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Se desencadena cuando se ha establecido correctamente una conexión con el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d4e19-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="d4e19-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Se desencadena si se cierra una conexión establecida o no se pudo establecer una conexión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection could not be established.</span></span>
3) <span data-ttu-id="d4e19-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Cuando se inicia la escucha de conexiones entrantes.</span><span class="sxs-lookup"><span data-stu-id="d4e19-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="d4e19-190">Estos eventos se colocan en una cola y la aplicación remota debe leer de la cola con regularidad a través de ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="d4e19-190">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="d4e19-191">Vista previa del contenido transmitido localmente</span><span class="sxs-lookup"><span data-stu-id="d4e19-191">Preview streamed content locally</span></span>

<span data-ttu-id="d4e19-192">Para mostrar el mismo contenido en la aplicación remota que se envía al dispositivo, ```XR_MSFT_holographic_remoting_frame_mirroring``` se puede usar la extensión.</span><span class="sxs-lookup"><span data-stu-id="d4e19-192">To display the same content in the remote app that is send to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="d4e19-193">Con esta extensión puede enviar una textura a xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="d4e19-193">With this extension you can submit a texture to xrEndFrame.</span></span> <span data-ttu-id="d4e19-194">Esto se hace mediante la ```XrRemotingFrameMirrorImageInfoMSFT``` estructura que está encadenada a XrFrameEndInfo como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="d4e19-194">This is done by using the ```XrRemotingFrameMirrorImageInfoMSFT``` structure which is chained to the XrFrameEndInfo as follows.</span></span>

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

<span data-ttu-id="d4e19-195">En el ejemplo anterior se usa una textura de cadena de intercambio de DX11 y se presenta la ventana inmediatamente después de la llamada a xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="d4e19-195">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="d4e19-196">El uso no está restringido a las texturas de la cadena de intercambio y no se requiere ninguna sincronización de GPU adicional.</span><span class="sxs-lookup"><span data-stu-id="d4e19-196">The usage is not restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="d4e19-197">Para obtener más información sobre el uso y las restricciones, consulte la especificación de la [extensión](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span><span class="sxs-lookup"><span data-stu-id="d4e19-197">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="d4e19-198">Si la aplicación remota usa DX12, use XrRemotingFrameMirrorImageD3D12MSFT en lugar de XrRemotingFrameMirrorImageD3D11MSFT.</span><span class="sxs-lookup"><span data-stu-id="d4e19-198">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4e19-199">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d4e19-199">See Also</span></span>
* [<span data-ttu-id="d4e19-200">Escritura de una aplicación de reproductor de control remoto de holografías personalizada</span><span class="sxs-lookup"><span data-stu-id="d4e19-200">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="d4e19-201">Establecimiento de una conexión segura con Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="d4e19-201">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="d4e19-202">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="d4e19-202">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="d4e19-203">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="d4e19-203">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="d4e19-204">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4e19-204">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
