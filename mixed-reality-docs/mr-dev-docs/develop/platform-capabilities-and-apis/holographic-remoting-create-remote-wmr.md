---
title: Escritura de una aplicación remota holográfica Remoting (WMR)
description: Al crear un contenido remoto de aplicaciones remotas holográficas, que se representa en un equipo remoto, se puede transmitir a HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, NuGet
ms.openlocfilehash: 5eddcc117008ebc54eac11965592099601880d3e
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530215"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a><span data-ttu-id="b2121-104">Escritura de una aplicación remota de Holographic Remoting mediante la API de HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="b2121-104">Writing a Holographic Remoting remote app using the HolographicSpace API</span></span>

>[!IMPORTANT]
><span data-ttu-id="b2121-105">En este documento se describe la creación de una aplicación remota para HoloLens 2 mediante la [API de HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="b2121-105">This document describes the creation of a remote application for HoloLens 2 using the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="b2121-106">Las aplicaciones remotas para **HoloLens (1ª generación)** deben usar el paquete NuGet versión **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="b2121-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="b2121-107">Esto implica que las aplicaciones remotas escritas para HoloLens 2 no son compatibles con HoloLens 1 y viceversa.</span><span class="sxs-lookup"><span data-stu-id="b2121-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="b2121-108">La documentación de HoloLens 1 se puede encontrar [aquí](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="b2121-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="b2121-109">Las aplicaciones de acceso remoto holográfica pueden transmitir contenido representado de forma remota a los auriculares HoloLens 2 y Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b2121-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="b2121-110">También puede tener acceso a más recursos del sistema e integrar [vistas de envolvente](../../design/app-views.md) remotas en el software de PC de escritorio existente.</span><span class="sxs-lookup"><span data-stu-id="b2121-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="b2121-111">Una aplicación remota recibe un flujo de datos de entrada de HoloLens 2, representa el contenido en una vista envolvente virtual y vuelve a transmitir los fotogramas de contenido a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b2121-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="b2121-112">La conexión se realiza mediante Wi-Fi estándar.</span><span class="sxs-lookup"><span data-stu-id="b2121-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="b2121-113">Holographic Remoting se agrega a una aplicación de escritorio o UWP a través de un paquete NuGet.</span><span class="sxs-lookup"><span data-stu-id="b2121-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="b2121-114">Se requiere código adicional que controla la conexión y se representa en una vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="b2121-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="b2121-115">Una conexión remota típica tendrá un mínimo de 50 ms de latencia.</span><span class="sxs-lookup"><span data-stu-id="b2121-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="b2121-116">La aplicación de reproducción puede informar de la latencia en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="b2121-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="b2121-117">Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="b2121-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2121-118">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b2121-118">Prerequisites</span></span>

<span data-ttu-id="b2121-119">Un buen punto de partida es una aplicación de escritorio o UWP basada en DirectX que funciona como destino de la [API de HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="b2121-119">A good starting point is a working DirectX based Desktop or UWP app, which targets the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="b2121-120">Para obtener más información, vea [Introducción al desarrollo de DirectX](../native/directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2121-120">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="b2121-121">La [plantilla de proyecto Holographic de C++](../native/creating-a-holographic-directx-project.md) es un buen punto de partida.</span><span class="sxs-lookup"><span data-stu-id="b2121-121">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b2121-122">Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="b2121-122">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="b2121-123">Se admite el uso de un apartamento de un [solo subproceso](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) , pero se producirá un rendimiento poco óptimo y posiblemente se produzca una intermitencia durante la reproducción.</span><span class="sxs-lookup"><span data-stu-id="b2121-123">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="b2121-124">Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartamento multiproceso es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="b2121-124">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="b2121-125">Obtención del paquete NuGet de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b2121-125">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="b2121-126">Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2121-126">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="b2121-127">Abra el proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2121-127">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="b2121-128">Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="b2121-128">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="b2121-129">En el panel que aparece, seleccione **examinar** y busque "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="b2121-129">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="b2121-130">Seleccione **Microsoft. Holographic. Remoting**, asegúrese de elegir la versión **2. x. x** más reciente y seleccione **instalar**.</span><span class="sxs-lookup"><span data-stu-id="b2121-130">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="b2121-131">Si aparece el cuadro de diálogo **vista previa** , seleccione **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="b2121-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="b2121-132">Seleccione **acepto** cuando aparezca el cuadro de diálogo contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="b2121-132">Select **I Accept** when the license agreement dialog pops up.</span></span>

>[!NOTE]
><span data-ttu-id="b2121-133">La versión **1. x.** x del paquete NuGet sigue estando disponible para los desarrolladores que quieran tener como destino HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="b2121-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="b2121-134">Para obtener más información, consulte incorporación de la [comunicación remota holográfica (HoloLens (1º generación))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="b2121-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="b2121-135">Crear el contexto remoto</span><span class="sxs-lookup"><span data-stu-id="b2121-135">Create the remote context</span></span>

<span data-ttu-id="b2121-136">Como primer paso, la aplicación debe crear un contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="b2121-136">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="b2121-137">Holographic Remoting funciona reemplazando el tiempo de ejecución de Windows Mixed Reality, que forma parte de Windows con un tiempo de ejecución específico de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="b2121-137">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="b2121-138">Esto se realiza durante la creación del contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="b2121-138">This is done during the creation of the remote context.</span></span> <span data-ttu-id="b2121-139">Por ese motivo, cualquier llamada en cualquier API de Windows Mixed Reality antes de crear el contexto remoto puede producir un comportamiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="b2121-139">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="b2121-140">El enfoque recomendado es crear el contexto remoto tan pronto como sea posible antes de la interacción con cualquier API de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b2121-140">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="b2121-141">Nunca mezcle objetos creados o recuperados a través de cualquier API de realidad mixta de Windows antes de la llamada a CreateRemoteContext con objetos creados o recuperados después.</span><span class="sxs-lookup"><span data-stu-id="b2121-141">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="b2121-142">A continuación, es necesario crear el espacio holográfica.</span><span class="sxs-lookup"><span data-stu-id="b2121-142">Next the holographic space needs to be created.</span></span> <span data-ttu-id="b2121-143">No es necesario especificar CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="b2121-143">Specifying a CoreWindow isn't required.</span></span> <span data-ttu-id="b2121-144">Las aplicaciones de escritorio que no tienen un CoreWindow solo pueden pasar un ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="b2121-144">Desktop apps that don't have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="b2121-145">Conexión al dispositivo</span><span class="sxs-lookup"><span data-stu-id="b2121-145">Connect to the device</span></span>

<span data-ttu-id="b2121-146">Cuando la aplicación remota está lista para la representación de contenido, se puede establecer una conexión con el dispositivo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="b2121-146">When the remote app is ready for rendering content a connection to the player device can be established.</span></span>

<span data-ttu-id="b2121-147">La conexión puede realizarse de una de estas dos maneras.</span><span class="sxs-lookup"><span data-stu-id="b2121-147">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="b2121-148">La aplicación remota se conecta al reproductor que se ejecuta en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b2121-148">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="b2121-149">El reproductor que se ejecuta en el dispositivo se conecta a la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="b2121-149">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="b2121-150">Para establecer una conexión desde la aplicación remota al dispositivo del reproductor, llame al ```Connect``` método en el contexto remoto y especifique el nombre de host y el puerto.</span><span class="sxs-lookup"><span data-stu-id="b2121-150">To establish a connection from the remote app to the player device call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="b2121-151">El puerto que usa el reproductor de comunicación remota holográfica es **8265**.</span><span class="sxs-lookup"><span data-stu-id="b2121-151">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="b2121-152">Como con cualquier API de C++/WinRT, ```Connect``` puede producir una excepción WinRT:: hresult_error que debe controlarse.</span><span class="sxs-lookup"><span data-stu-id="b2121-152">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="b2121-153">Para evitar el uso de la proyección de lenguaje [/WinRT de C++](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) , se puede incluir el archivo que ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` se encuentra dentro del paquete NuGet de Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="b2121-153">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="b2121-154">Contiene declaraciones de las interfaces COM subyacentes.</span><span class="sxs-lookup"><span data-stu-id="b2121-154">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="b2121-155">No obstante, se recomienda el uso de/WinRT de C++.</span><span class="sxs-lookup"><span data-stu-id="b2121-155">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="b2121-156">La escucha de conexiones entrantes en la aplicación remota se puede realizar mediante una llamada al ```Listen``` método.</span><span class="sxs-lookup"><span data-stu-id="b2121-156">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="b2121-157">El puerto de enlace y el puerto de transporte se pueden especificar durante esta llamada.</span><span class="sxs-lookup"><span data-stu-id="b2121-157">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="b2121-158">El puerto de enlace se usa para el protocolo de enlace inicial.</span><span class="sxs-lookup"><span data-stu-id="b2121-158">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="b2121-159">A continuación, los datos se envían a través del puerto de transporte.</span><span class="sxs-lookup"><span data-stu-id="b2121-159">The data is then sent over the transport port.</span></span> <span data-ttu-id="b2121-160">De forma predeterminada, se usan **8265** y **8266** .</span><span class="sxs-lookup"><span data-stu-id="b2121-160">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="b2121-161">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```En el paquete NuGet se incluye documentación detallada para la API expuesta por la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="b2121-161">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="b2121-162">Controlar eventos específicos de la comunicación remota</span><span class="sxs-lookup"><span data-stu-id="b2121-162">Handling Remoting specific events</span></span>

<span data-ttu-id="b2121-163">El contexto remoto expone tres eventos, que son importantes para supervisar el estado de una conexión.</span><span class="sxs-lookup"><span data-stu-id="b2121-163">The remote context exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="b2121-164">OnConnection: se desencadena cuando se ha establecido correctamente una conexión con el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b2121-164">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="b2121-165">OnDisconnection: se desencadena si se cierra una conexión establecida o no se pudo establecer una conexión.</span><span class="sxs-lookup"><span data-stu-id="b2121-165">OnDisconnected: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="b2121-166">MyListener: cuando se inicia la escucha de conexiones entrantes.</span><span class="sxs-lookup"><span data-stu-id="b2121-166">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="b2121-167">Además, se puede consultar el estado de la conexión utilizando la ```ConnectionState``` propiedad en el contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="b2121-167">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="b2121-168">Control de eventos de voz</span><span class="sxs-lookup"><span data-stu-id="b2121-168">Handling speech events</span></span>

<span data-ttu-id="b2121-169">El uso de la interfaz de voz remota es posible registrar los desencadenadores de voz con HoloLens 2 y hacerlos remotos en la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="b2121-169">Using the remote speech interface it's possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="b2121-170">Este miembro adicional es necesario para realizar el seguimiento del estado de la voz remota.</span><span class="sxs-lookup"><span data-stu-id="b2121-170">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="b2121-171">En primer lugar, es necesario recuperar la interfaz de voz remota.</span><span class="sxs-lookup"><span data-stu-id="b2121-171">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="b2121-172">Con un método auxiliar asincrónico, puede inicializar la voz remota.</span><span class="sxs-lookup"><span data-stu-id="b2121-172">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="b2121-173">Esto debe hacerse de forma asincrónica, ya que la inicialización puede tardar un tiempo considerable.</span><span class="sxs-lookup"><span data-stu-id="b2121-173">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="b2121-174">[Operaciones de simultaneidad y asincrónicas con c++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explica cómo crear funciones asincrónicas con c++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="b2121-174">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="b2121-175">Hay dos maneras de especificar frases que se reconocerán.</span><span class="sxs-lookup"><span data-stu-id="b2121-175">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="b2121-176">Especificación dentro de un archivo XML de gramática de voz.</span><span class="sxs-lookup"><span data-stu-id="b2121-176">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="b2121-177">Vea [Cómo crear una gramática XML básica](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="b2121-177">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="b2121-178">Especifique pasándolos dentro del vector del diccionario a ```ApplyParameters``` .</span><span class="sxs-lookup"><span data-stu-id="b2121-178">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="b2121-179">Dentro de la devolución de llamada OnRecognizedSpeech, se pueden procesar los eventos de voz:</span><span class="sxs-lookup"><span data-stu-id="b2121-179">Inside the OnRecognizedSpeech callback, the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="b2121-180">Vista previa del contenido transmitido localmente</span><span class="sxs-lookup"><span data-stu-id="b2121-180">Preview streamed content locally</span></span>

<span data-ttu-id="b2121-181">Para mostrar el mismo contenido en la aplicación remota que se envía al dispositivo, ```OnSendFrame``` se puede usar el evento del contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="b2121-181">To display the same content in the remote app that is sent to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="b2121-182">El ```OnSendFrame``` evento se desencadena cada vez que la biblioteca de acceso remoto holográfica envía el marco actual al dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="b2121-182">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="b2121-183">Este es el momento ideal para tomar el contenido y también dividirlo en la ventana de escritorio o UWP.</span><span class="sxs-lookup"><span data-stu-id="b2121-183">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="b2121-184">Reproyección de profundidad</span><span class="sxs-lookup"><span data-stu-id="b2121-184">Depth Reprojection</span></span>

<span data-ttu-id="b2121-185">A partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting admite la [reproyección de profundidad](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="b2121-185">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="b2121-186">Esto requiere que el búfer de color y el búfer de profundidad se transmitan desde la aplicación remota a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b2121-186">This requires both the color buffer and depth buffer to be streamed from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="b2121-187">De forma predeterminada, el streaming de búfer de profundidad está habilitado y configurado para usar la mitad de la resolución del búfer de color.</span><span class="sxs-lookup"><span data-stu-id="b2121-187">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="b2121-188">Esto puede cambiarse de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="b2121-188">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="b2121-189">Tenga en cuenta que, si no se deben usar los valores predeterminados, ```ConfigureDepthVideoStream``` se debe llamar a antes de establecer una conexión con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b2121-189">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="b2121-190">El mejor lugar es justo después de haber creado el contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="b2121-190">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="b2121-191">Los valores posibles para DepthBufferStreamResolution son:</span><span class="sxs-lookup"><span data-stu-id="b2121-191">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="b2121-192">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="b2121-192">Full_Resolution</span></span>
* <span data-ttu-id="b2121-193">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="b2121-193">Half_Resolution</span></span>
* <span data-ttu-id="b2121-194">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="b2121-194">Quarter_Resolution</span></span>
* <span data-ttu-id="b2121-195">Deshabilitado (agregado con la versión [2.1.3](holographic-remoting-version-history.md#v2.1.3) y, si no se usa, no se crea ninguna secuencia de vídeo de profundidad adicional)</span><span class="sxs-lookup"><span data-stu-id="b2121-195">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="b2121-196">Tenga en cuenta que el uso de un búfer de profundidad de resolución completa también afecta a los requisitos de ancho de banda y se debe tener en cuenta en el valor de ancho de banda máximo que se proporciona a ```CreateRemoteContext``` .</span><span class="sxs-lookup"><span data-stu-id="b2121-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="b2121-197">Junto a la configuración de la resolución, también tiene que confirmar un búfer de profundidad a través de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="b2121-197">Beside configuring the resolution, you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="b2121-198">Para comprobar si la reproyección de profundidad funciona correctamente en HoloLens 2, puede habilitar un visualizador de profundidad a través del portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2121-198">To verify if depth reprojection is correctly working on HoloLens 2, you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="b2121-199">Consulte [comprobar profundidad está configurado correctamente](hologram-stability.md#verifying-depth-is-set-correctly) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="b2121-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="b2121-200">Opcional: canales de datos personalizados</span><span class="sxs-lookup"><span data-stu-id="b2121-200">Optional: Custom data channels</span></span>

<span data-ttu-id="b2121-201">Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida.</span><span class="sxs-lookup"><span data-stu-id="b2121-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="b2121-202">Vea [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="b2121-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2121-203">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b2121-203">See Also</span></span>
* [<span data-ttu-id="b2121-204">Escritura de una aplicación de reproductor de control remoto de holografías personalizada</span><span class="sxs-lookup"><span data-stu-id="b2121-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="b2121-205">Canales de datos personalizados de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="b2121-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="b2121-206">Establecimiento de una conexión segura con Control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="b2121-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="b2121-207">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="b2121-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="b2121-208">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="b2121-208">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="b2121-209">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="b2121-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
