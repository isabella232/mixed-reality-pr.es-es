---
title: Obtención de HolographicSpace
description: Aprenda a usar HolographicSpace API para la representación holográfica y la entrada espacial en las aplicaciones de realidad mixta.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrada espacial, representación, cadena de intercambio, marco holográfico, bucle de actualización, bucle de juego, marco de referencia, locatability, código de ejemplo, tutorial, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 986ccdc6e81d1ac7c7b401a427da548218a68eb0352a0057bf7d7aba3c1d6d6a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212173"
---
# <a name="getting-a-holographicspace"></a>Obtención de HolographicSpace

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.

La <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">clase HolographicSpace</a> es el portal en el mundo holográfico. Controla la representación inmersiva, proporciona datos de la cámara y proporciona acceso a las API de razonamiento espacial. Creará uno para <a href="/api/windows.ui.core.corewindow" target="_blank">corewindow</a> de la aplicación para UWP o para el HWND de la aplicación Win32.

## <a name="set-up-the-holographic-space"></a>Configuración del espacio holográfico

La creación del objeto de espacio holográfico es el primer paso para crear Windows Mixed Reality aplicación. Las Windows tradicionales se representan en una cadena de intercambio de Direct3D creada para la ventana principal de su vista de aplicación. Esta cadena de intercambio se muestra en una pizarra en la interfaz de usuario holográfica. Para que la aplicación vea holográfica en lugar de una pizarra 2D, cree un espacio holográfico para su ventana principal en lugar de una cadena de intercambio. La presentación de fotogramas holográficos creados por este espacio holográfico pone la aplicación en modo de representación a pantalla completa.

Para una aplicación **para UWP** a partir de la plantilla [ *Holographic DirectX 11 App (Universal Windows),*](creating-a-holographic-directx-project.md)busque este código en el método **SetWindow** en AppView.cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Si va a compilar una aplicación **Win32** a partir del ejemplo [ *BasicHologram* Win32,](creating-a-holographic-directx-project.md#creating-a-win32-project)consulte **App::CreateWindowAndHolographicSpace** para ver un ejemplo de HWND. A continuación, puede convertirlo en un HWND inmersivo mediante la creación de un <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicSpace asociado:</a>

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

Una vez que haya obtenido un holographicSpace para UWP CoreWindow o Win32 HWND, HolographicSpace puede controlar cámaras holográficas, crear sistemas de coordenadas y realizar la representación holográfica. El espacio holográfico actual se usa en varios lugares de la plantilla de DirectX:
* La **clase DeviceResources** debe obtener información del objeto HolographicSpace para crear el dispositivo Direct3D. Este es el identificador del adaptador DXGI asociado a la pantalla holográfica. La <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">clase HolographicSpace</a> usa el dispositivo Direct3D 11 de la aplicación para crear y administrar recursos basados en dispositivos, como los búferes de reserva para cada cámara holográfica. Si está interesado en ver lo que hace esta función en primer lugar, la encontrará en DeviceResources.cpp.
* La función **DeviceResources::InitializeUsingHolographicSpace** muestra cómo obtener el adaptador mediante la búsqueda del LUID y cómo elegir un adaptador predeterminado cuando no se especifica ningún adaptador preferido.
* La clase principal de la aplicación usa el espacio holográfico de **AppView::SetWindow** o **App::CreateWindowAndHolographicSpace** para las actualizaciones y la representación.

>[!NOTE]
>Aunque en las secciones siguientes se mencionan los nombres de función de la plantilla, como **AppView::SetWindow,** que suponen que se inició desde la plantilla de aplicación holográfica para UWP, los fragmentos de código que vea se aplicarán por igual en las aplicaciones de UWP y Win32.

A continuación, profundizaremos en el proceso de configuración del que Es responsable **SetHolographicSpace** en la clase AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Suscripción a eventos de cámara, creación y eliminación de recursos de cámara

El contenido holográfico de la aplicación reside en su espacio holográfico y se ve a través de una o varias cámaras holográficas, que representan distintas perspectivas de la escena. Ahora que tiene el espacio holográfico, puede recibir datos para las cámaras holográficas.

La aplicación debe responder a eventos **CameraAdded** mediante la creación de recursos específicos de esa cámara. Un ejemplo de este tipo de recurso es la vista de destino de representación del búfer de reserva. Puede ver este código en la función **DeviceResources::SetHolographicSpace,** a la que llama **AppView::SetWindow antes** de que la aplicación cree fotogramas holográficos:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

La aplicación también debe responder a los eventos **CameraRemoved** mediante la liberación de los recursos creados para esa cámara.

Desde **DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Los controladores de eventos deben completar algún trabajo para que la representación holográfica fluya sin problemas y la representación de la aplicación. Lea el código y los comentarios para obtener más información: puede buscar **OnCameraAdded** y **OnCameraRemoved** en la clase principal para comprender cómo **DeviceResources** controla el mapa de **m_cameraResources.**

En este momento, nos centraremos en AppMain y en la configuración que realiza para permitir que la aplicación conozca las cámaras holográficas. Con esto en mente, es importante tener en cuenta los dos requisitos siguientes:

1. Para el **controlador de eventos CameraAdded,** la aplicación puede funcionar de forma asincrónica para terminar de crear recursos y cargar recursos para la nueva cámara holográfica. Las aplicaciones que toman más de un fotograma para completar este trabajo deben solicitar un aplazamiento y completar el aplazamiento después de la carga asincrónica. Se puede usar una tarea de [PPL](/cpp/parallel/concrt/parallel-patterns-library-ppl) para realizar un trabajo asincrónico. La aplicación debe asegurarse de que está lista para representarse en esa cámara inmediatamente cuando sale del controlador de eventos o cuando completa el aplazamiento. Salir del controlador de eventos o completar el aplazamiento indica al sistema que la aplicación ya está lista para recibir fotogramas holográficos con esa cámara incluida.

2. Cuando la aplicación recibe un **evento CameraRemoved,** debe liberar todas las referencias al búfer de reserva y salir de la función de inmediato. Esto incluye las vistas de destino de representación y cualquier otro recurso que pueda contener una referencia a [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). La aplicación también debe asegurarse de que el búfer de reserva no está asociado como destino de representación, como se muestra en **CameraResources::ReleaseResourcesForBackBuffer**. Para ayudar a acelerar las cosas, la aplicación puede liberar el búfer de reserva y, a continuación, iniciar una tarea para completar de forma asincrónica cualquier otro trabajo de desmontado de la cámara. La plantilla de aplicación holográfica incluye una tarea de PPL que puede usar para este propósito.

>[!NOTE]
>Si quiere determinar cuándo aparece una cámara agregada o quitada en el fotograma, use las propiedades **HolographicFrame** [AddedCamgrafía](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) y [RemovedCamntes.](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Creación de un marco de referencia para el contenido holográfico

El contenido de la aplicación debe colocarse en un sistema de [coordenadas](coordinate-systems-in-directx.md) espaciales para representarlo en HolographicSpace. El sistema proporciona dos fotogramas principales de referencia, que puede usar para establecer un sistema de coordenadas para los hologramas.

Hay dos tipos de fotogramas de referencia en Windows Holographic: fotogramas de referencia conectados al dispositivo y fotogramas de referencia que permanecen estacionados a medida que el dispositivo se mueve por el entorno del usuario. La plantilla de aplicación holográfica usa un marco de referencia estacionado de forma predeterminada; esta es una de las formas más sencillas de representar hologramas bloqueados por el mundo.

Los marcos de referencia estacionados están diseñados para estabilizar posiciones cerca de la ubicación actual del dispositivo. Esto significa que las coordenadas lejos del dispositivo pueden desplazarse ligeramente en relación con el entorno del usuario a medida que el dispositivo aprende más sobre el espacio que lo rodea. Hay dos maneras de crear un marco de referencia estacionado: adquirir el sistema de coordenadas de la fase [espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)o usar el <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">spatialLocator predeterminado.</a> Si va a crear una aplicación Windows Mixed Reality para cascos envolventes, el punto de partida recomendado es la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage). La fase espacial también proporciona información sobre las funcionalidades del casco envolvente que el jugador lleva a la cabeza. Aquí se muestra cómo usar el <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">objeto SpatialLocator predeterminado.</a>

El localizador espacial representa Windows Mixed Reality dispositivo, realiza un seguimiento del movimiento del dispositivo y proporciona sistemas de coordenadas que se pueden entender en relación con su ubicación.

Desde **AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Cree el marco de referencia estacionado una vez cuando se inicia la aplicación. Esto es análogo a la definición de un sistema de coordenadas universal, con el origen situado en la posición del dispositivo cuando se inicia la aplicación. Este marco de referencia no se mueve con el dispositivo.

Desde **AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Todos los fotogramas de referencia están alineados por gravedad, lo que significa que el eje Y apunta "hacia arriba" en relación con el entorno del usuario. Puesto Windows sistemas de coordenadas "con la mano derecha", la dirección del eje –z coincide con la dirección "hacia delante" a la que se enfrenta el dispositivo cuando se crea el marco de referencia.

>[!NOTE]
>Cuando la aplicación requiera una ubicación precisa de hologramas individuales, use <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">spatialAnchor</a> para delimitar el holograma individual a una posición en el mundo real. Por ejemplo, use un delimitador espacial cuando el usuario indique que un punto tiene un interés especial. Las posiciones de anclaje no se desplazan, pero se pueden ajustar. De forma predeterminada, cuando se ajusta un delimitador, facilita su posición en los siguientes fotogramas después de que se haya producido la corrección. Dependiendo de la aplicación, cuando esto ocurra, es posible que desee controlar el ajuste de una manera diferente (por ejemplo, aplazando hasta que el holograma esté fuera de la vista). La <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">propiedad RawCoordinateSystem</a> y <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">los eventos RawCoordinateSystemAdjusted</a> habilitan estas personalizaciones.

## <a name="respond-to-locatability-changed-events"></a>Respuesta a eventos modificados de locatability

La representación de hologramas bloqueados en el mundo requiere que el dispositivo se encuentre en el mundo. Esto puede no ser siempre posible debido a condiciones ambientales y, si es así, el usuario puede esperar una indicación visual de la interrupción del seguimiento. Esta indicación visual debe representarse mediante marcos de referencia conectados al dispositivo, en lugar de de forma fija al mundo.

La aplicación puede solicitar que se le notifique si se interrumpe el seguimiento por cualquier motivo. Regístrese en el evento LocatabilityChanged para detectar cuándo cambia la capacidad del dispositivo para ubicarse en el mundo. Desde **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

A continuación, use este evento para determinar cuándo no se pueden representar hologramas de forma fija en el mundo.

## <a name="see-also"></a>Consulte también
* [Representación en DirectX](rendering-in-directx.md)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)