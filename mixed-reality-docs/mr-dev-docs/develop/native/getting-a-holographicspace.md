---
title: Obtención de HolographicSpace
description: Explica la API de HolographicSpace, un concepto básico de representación de Holographic y entrada espacial.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrada espacial, representación, cadena de intercambio, fotograma holográfica, bucle de actualización, bucle de juego, fotograma de referencia, localización, código de ejemplo, tutorial, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: fa2c64901a7c4a09710a472509441d54a9e3a383
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679644"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="4901f-104">Obtención de HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="4901f-104">Getting a HolographicSpace</span></span>

> [!NOTE]
> <span data-ttu-id="4901f-105">Este artículo está relacionado con las API nativas de WinRT heredadas.</span><span class="sxs-lookup"><span data-stu-id="4901f-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="4901f-106">En el caso de los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="4901f-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="4901f-107">La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> es su portal en el mundo holográfica.</span><span class="sxs-lookup"><span data-stu-id="4901f-107">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="4901f-108">Controla la representación envolvente, proporciona datos de la cámara y proporciona acceso a las API de razonamiento espacial.</span><span class="sxs-lookup"><span data-stu-id="4901f-108">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="4901f-109">Creará una para el identificador de usuario de la <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">aplicación de UWP o la</a> aplicación Win32.</span><span class="sxs-lookup"><span data-stu-id="4901f-109">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="4901f-110">Configuración del espacio holográfica</span><span class="sxs-lookup"><span data-stu-id="4901f-110">Set up the holographic space</span></span>

<span data-ttu-id="4901f-111">La creación del objeto de espacio holográfica es el primer paso para crear una aplicación de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4901f-111">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="4901f-112">Las aplicaciones tradicionales de Windows se representan en una cadena de intercambio de Direct3D creada para la ventana principal de la vista de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4901f-112">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="4901f-113">Esta cadena de intercambio se muestra en una pizarra en la interfaz de usuario holográfica.</span><span class="sxs-lookup"><span data-stu-id="4901f-113">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="4901f-114">Para hacer que la vista de la aplicación sea holográfica en lugar de una pizarra 2D, cree un espacio holográfica para su ventana principal en lugar de una cadena de intercambio.</span><span class="sxs-lookup"><span data-stu-id="4901f-114">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="4901f-115">La presentación de tramas holográficas creadas por este espacio holográfica coloca la aplicación en el modo de representación de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="4901f-115">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="4901f-116">En el caso de una **aplicación para UWP** a partir [de la *plantilla holográfica DirectX 11 (Windows universal)*](creating-a-holographic-directx-project.md), busque este código en el método **SetWindow** en AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="4901f-116">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="4901f-117">En el caso de una **aplicación de Win32** que se [inicie en el ejemplo de Win32 *BasicHologram*](creating-a-holographic-directx-project.md#creating-a-win32-project), consulte **App:: CreateWindowAndHolographicSpace** para obtener un ejemplo de cómo crear un HWND y luego convertirlo en un HWND envolvente mediante la creación de un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>asociado:</span><span class="sxs-lookup"><span data-stu-id="4901f-117">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="4901f-118">Ahora que ha obtenido un HolographicSpace para su HWND de UWP o HWND de Win32, usará ese HolographicSpace para controlar las cámaras holográficas, crear sistemas de coordenadas y realizar la representación holográfica.</span><span class="sxs-lookup"><span data-stu-id="4901f-118">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="4901f-119">El espacio holográfica actual se usa en varios lugares de la plantilla de DirectX:</span><span class="sxs-lookup"><span data-stu-id="4901f-119">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="4901f-120">La clase **DeviceResources** debe obtener cierta información del objeto HolographicSpace para crear el dispositivo Direct3D.</span><span class="sxs-lookup"><span data-stu-id="4901f-120">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="4901f-121">Este es el identificador del adaptador de DXGI asociado a la pantalla holográfica.</span><span class="sxs-lookup"><span data-stu-id="4901f-121">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="4901f-122">La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> usa el dispositivo Direct3D 11 de la aplicación para crear y administrar recursos basados en dispositivos como, por ejemplo, los búferes de reserva de cada cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="4901f-122">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="4901f-123">Si le interesa ver lo que hace esta función en el capó, la encontrará en DeviceResources. cpp.</span><span class="sxs-lookup"><span data-stu-id="4901f-123">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="4901f-124">La función **DeviceResources:: InitializeUsingHolographicSpace** muestra cómo obtener el adaptador buscando el LUID y cómo elegir un adaptador predeterminado cuando no se especifica ningún adaptador preferido.</span><span class="sxs-lookup"><span data-stu-id="4901f-124">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="4901f-125">La clase principal de la aplicación usa el espacio holográfica de **AppView:: SetWindow** o **App:: CreateWindowAndHolographicSpace** para las actualizaciones y la representación.</span><span class="sxs-lookup"><span data-stu-id="4901f-125">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="4901f-126">Aunque en las secciones siguientes se mencionan los nombres de función de la plantilla como **AppView:: SetWindow** que suponen que se ha iniciado desde la plantilla de aplicación de UWP de Holographic, los fragmentos de código que se ven se aplicarán igualmente a través de aplicaciones de UWP y Win32.</span><span class="sxs-lookup"><span data-stu-id="4901f-126">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="4901f-127">A continuación, profundizaremos en el proceso de configuración que **SetHolographicSpace** es responsable de en la clase AppMain.</span><span class="sxs-lookup"><span data-stu-id="4901f-127">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="4901f-128">Suscripción a eventos de cámara, creación y eliminación de recursos de la cámara</span><span class="sxs-lookup"><span data-stu-id="4901f-128">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="4901f-129">El contenido holográfica de la aplicación vive en su espacio holográfica y se ve a través de una o varias cámaras holográfica que representan perspectivas diferentes en la escena.</span><span class="sxs-lookup"><span data-stu-id="4901f-129">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="4901f-130">Ahora que tiene el espacio holográfica, puede recibir datos para cámaras holográficas.</span><span class="sxs-lookup"><span data-stu-id="4901f-130">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="4901f-131">La aplicación debe responder a los eventos de **CameraAdded** mediante la creación de los recursos específicos de esa cámara, como la vista de destino de representación del búfer de reserva.</span><span class="sxs-lookup"><span data-stu-id="4901f-131">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="4901f-132">Puede ver este código en la función **DeviceResources:: SetHolographicSpace** , llamada por **AppView:: SetWindow** antes de que la aplicación cree cualquier trama holográfica:</span><span class="sxs-lookup"><span data-stu-id="4901f-132">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="4901f-133">La aplicación también debe responder a los eventos de **CameraRemoved** mediante la liberación de los recursos que se crearon para esa cámara.</span><span class="sxs-lookup"><span data-stu-id="4901f-133">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="4901f-134">De **DeviceResources:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="4901f-134">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="4901f-135">Los controladores de eventos deben completar algún trabajo para que la representación holográfica fluya sin problemas y para que la aplicación se pueda representar en absoluto.</span><span class="sxs-lookup"><span data-stu-id="4901f-135">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="4901f-136">Lea el código y los comentarios de los detalles: puede buscar **OnCameraAdded** y **OnCameraRemoved** en la clase principal para entender cómo controla la asignación de **m_cameraResources** mediante **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="4901f-136">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="4901f-137">En este momento, nos centramos en AppMain y en la configuración que permite que la aplicación Conozca las cámaras holográficas.</span><span class="sxs-lookup"><span data-stu-id="4901f-137">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="4901f-138">Teniendo esto en cuenta, es importante tener en cuenta los dos requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="4901f-138">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="4901f-139">En el caso del controlador de eventos **CameraAdded** , la aplicación puede trabajar de forma asincrónica para finalizar la creación de recursos y la carga de recursos para la nueva cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="4901f-139">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="4901f-140">Las aplicaciones que tardan más de un fotograma para completar este trabajo deben solicitar un aplazamiento y completar el aplazamiento después de cargarse de forma asincrónica. una [tarea PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) se puede usar para realizar el trabajo asincrónico.</span><span class="sxs-lookup"><span data-stu-id="4901f-140">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="4901f-141">La aplicación debe asegurarse de que esté lista para representarse en esa cámara inmediatamente cuando salga del controlador de eventos o cuando complete el aplazamiento.</span><span class="sxs-lookup"><span data-stu-id="4901f-141">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="4901f-142">Salir del controlador de eventos o completar el aplazamiento indica al sistema que la aplicación ya está lista para recibir tramas holográficas con esa cámara incluida.</span><span class="sxs-lookup"><span data-stu-id="4901f-142">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="4901f-143">Cuando la aplicación recibe un evento **CameraRemoved** , debe liberar todas las referencias al búfer de reserva y salir de la función inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="4901f-143">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="4901f-144">Esto incluye las vistas de destino de representación y cualquier otro recurso que pueda contener una referencia a [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="4901f-144">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="4901f-145">La aplicación también debe asegurarse de que el búfer de reserva no está asociado como destino de representación, como se muestra en **CameraResources:: ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="4901f-145">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="4901f-146">Para ayudar a acelerar las cosas, la aplicación puede liberar el búfer de reserva y, a continuación, iniciar una tarea para completar de forma asincrónica cualquier otro trabajo que sea necesario para anular la cámara.</span><span class="sxs-lookup"><span data-stu-id="4901f-146">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="4901f-147">La plantilla de aplicación holográfica incluye una tarea PPL que puede usar con este fin.</span><span class="sxs-lookup"><span data-stu-id="4901f-147">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="4901f-148">Si desea determinar cuándo se muestra una cámara agregada o quitada en el fotograma, use las propiedades **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) y [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="4901f-148">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="4901f-149">Creación de un marco de referencia para el contenido holográfica</span><span class="sxs-lookup"><span data-stu-id="4901f-149">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="4901f-150">El contenido de la aplicación debe colocarse en un [sistema de coordenadas espaciales](coordinate-systems-in-directx.md) que se va a representar en el HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="4901f-150">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="4901f-151">El sistema proporciona dos fotogramas principales de referencia que puede usar para establecer un sistema de coordenadas para los hologramas.</span><span class="sxs-lookup"><span data-stu-id="4901f-151">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="4901f-152">Hay dos tipos de fotogramas de referencia en Windows Holographic: los fotogramas de referencia conectados al dispositivo y hacen referencia a fotogramas que permanecen estacionarios a medida que el dispositivo se mueve por el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="4901f-152">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="4901f-153">De forma predeterminada, la plantilla de aplicación holográfica usa un marco de referencia estacional. Esta es una de las formas más sencillas de representar hologramas de bloque mundial.</span><span class="sxs-lookup"><span data-stu-id="4901f-153">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="4901f-154">Los fotogramas de referencia estacionarios están diseñados para estabilizar las posiciones cerca de la ubicación actual del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4901f-154">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="4901f-155">Esto significa que las coordenadas más allá del dispositivo pueden desplazarse ligeramente con respecto al entorno del usuario, ya que el dispositivo aprende más sobre el espacio que lo rodea.</span><span class="sxs-lookup"><span data-stu-id="4901f-155">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="4901f-156">Hay dos maneras de crear un marco estacionario de referencia: adquirir el sistema de coordenadas de la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)o usar el valor predeterminado <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="4901f-156">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="4901f-157">Si va a crear una aplicación de Windows Mixed Reality para auriculares envolventes, el punto de partida recomendado es la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que también proporciona información acerca de las capacidades del casco envolvente que gasta el jugador.</span><span class="sxs-lookup"><span data-stu-id="4901f-157">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="4901f-158">Aquí se muestra cómo usar el valor predeterminado de <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="4901f-158">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="4901f-159">El localizador espacial representa el dispositivo de Windows Mixed Reality y realiza un seguimiento del movimiento del dispositivo y proporciona sistemas de coordenadas que se pueden entender en relación con su ubicación.</span><span class="sxs-lookup"><span data-stu-id="4901f-159">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="4901f-160">Desde **AppMain:: OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="4901f-160">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="4901f-161">Cree el marco de referencia estacionario una vez cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4901f-161">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="4901f-162">Esto es análogo a definir un sistema de coordenadas universal, con el origen colocado en la posición del dispositivo cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4901f-162">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="4901f-163">Este fotograma de referencia no se mueve con el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4901f-163">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="4901f-164">Desde **AppMain:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="4901f-164">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="4901f-165">Todos los marcos de referencia están alineados con la gravedad, lo que significa que el eje y apunta "hacia arriba" con respecto al entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="4901f-165">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="4901f-166">Puesto que Windows usa sistemas de coordenadas "zurdos", la dirección del eje – z coincide con la dirección "hacia delante" a la que se enfrenta el dispositivo cuando se crea el fotograma de referencia.</span><span class="sxs-lookup"><span data-stu-id="4901f-166">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="4901f-167">Cuando la aplicación requiere una ubicación precisa de hologramas individuales, use un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> para anclar el holograma individual en una posición del mundo real.</span><span class="sxs-lookup"><span data-stu-id="4901f-167">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="4901f-168">Por ejemplo, use un delimitador espacial cuando el usuario indique que un punto debe ser de especial interés.</span><span class="sxs-lookup"><span data-stu-id="4901f-168">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="4901f-169">Las posiciones de anclaje no se desplazan, pero se pueden ajustar.</span><span class="sxs-lookup"><span data-stu-id="4901f-169">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="4901f-170">De forma predeterminada, cuando se ajusta un delimitador, facilita su posición en lugar de los próximos fotogramas después de que se haya realizado la corrección.</span><span class="sxs-lookup"><span data-stu-id="4901f-170">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="4901f-171">En función de la aplicación, cuando esto sucede, es posible que desee controlar el ajuste de manera diferente (por ejemplo, si lo aplaza hasta que el holograma esté fuera de la vista).</span><span class="sxs-lookup"><span data-stu-id="4901f-171">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="4901f-172">La propiedad <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> y los eventos <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> habilitan estas personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="4901f-172">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="4901f-173">Responder a los eventos de búsqueda modificada</span><span class="sxs-lookup"><span data-stu-id="4901f-173">Respond to locatability changed events</span></span>

<span data-ttu-id="4901f-174">La representación de hologramas con bloqueo mundial requiere que el dispositivo pueda localizarse en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="4901f-174">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="4901f-175">Esto puede no ser siempre posible debido a las condiciones del entorno, y si es así, el usuario puede esperar una indicación visual de la interrupción del seguimiento.</span><span class="sxs-lookup"><span data-stu-id="4901f-175">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="4901f-176">Esta indicación visual se debe representar mediante fotogramas de referencia conectados al dispositivo, en lugar de separarse del mundo.</span><span class="sxs-lookup"><span data-stu-id="4901f-176">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="4901f-177">La aplicación puede solicitar recibir una notificación si se interrumpe el seguimiento por cualquier motivo.</span><span class="sxs-lookup"><span data-stu-id="4901f-177">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="4901f-178">Regístrese en el evento LocatabilityChanged para detectar cuándo cambia la capacidad del dispositivo de localizarse en el mundo.</span><span class="sxs-lookup"><span data-stu-id="4901f-178">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="4901f-179">Desde **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="4901f-179">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="4901f-180">A continuación, use este evento para determinar cuándo no se pueden representar los hologramas estacionales en el mundo.</span><span class="sxs-lookup"><span data-stu-id="4901f-180">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="4901f-181">Vea también</span><span class="sxs-lookup"><span data-stu-id="4901f-181">See also</span></span>
* [<span data-ttu-id="4901f-182">Representación en DirectX</span><span class="sxs-lookup"><span data-stu-id="4901f-182">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="4901f-183">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="4901f-183">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
