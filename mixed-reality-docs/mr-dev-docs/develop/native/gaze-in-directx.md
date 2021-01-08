---
title: Control con la cabeza y los ojos de DirectX
description: Obtenga información acerca de cómo solicitar, usar y desempaquetar datos de raycasting del seguimiento de la mirada y del ojo en aplicaciones DirectX nativas.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: miras hacia abajo, hacia abajo, seguimiento del cabezal, seguimiento ocular, DirectX, entrada, hologramas, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: a518e5e4153da9c58295abb257a8ed2d69145211
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009555"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="696b5-104">Entrada de ojo y mira fijamente en DirectX</span><span class="sxs-lookup"><span data-stu-id="696b5-104">Head-gaze and eye-gaze input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="696b5-105">Este artículo está relacionado con las API nativas de WinRT heredadas.</span><span class="sxs-lookup"><span data-stu-id="696b5-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="696b5-106">En el caso de los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="696b5-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="696b5-107">En Windows Mixed Reality, se usa la entrada de ojo y mirarnos para determinar lo que el usuario está examinando.</span><span class="sxs-lookup"><span data-stu-id="696b5-107">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="696b5-108">Puede usar los datos para controlar los modelos de entrada principales, como [el encabezado de la mirada y la confirmación](../../design/gaze-and-commit.md), y proporcionar contexto para los distintos tipos de interacción.</span><span class="sxs-lookup"><span data-stu-id="696b5-108">You can use the data to drive primary input models like [head-gaze and commit](../../design/gaze-and-commit.md), and provide context for different interaction types.</span></span> <span data-ttu-id="696b5-109">Hay dos tipos de vectores de miración disponibles a través de la API: encabezado y ojo.</span><span class="sxs-lookup"><span data-stu-id="696b5-109">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="696b5-110">Ambos se proporcionan como un rayo tridimensional con un origen y una dirección.</span><span class="sxs-lookup"><span data-stu-id="696b5-110">Both are provided as a three-dimensional ray with an origin and direction.</span></span> <span data-ttu-id="696b5-111">A continuación, las aplicaciones pueden Raycast en sus escenas, o en el mundo real, y determinar el destino del usuario.</span><span class="sxs-lookup"><span data-stu-id="696b5-111">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="696b5-112">**Head-fijamente** representa la dirección en la que apunta el encabezado del usuario.</span><span class="sxs-lookup"><span data-stu-id="696b5-112">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="696b5-113">Piense en el encabezado y en la dirección hacia delante del propio dispositivo, con la posición como el punto central entre las dos pantallas.</span><span class="sxs-lookup"><span data-stu-id="696b5-113">Think of head-gaze as the position and forward direction of the device itself, with the position as the center point between the two displays.</span></span> <span data-ttu-id="696b5-114">La mirada está disponible en todos los dispositivos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="696b5-114">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="696b5-115">**Ojo:** representa la dirección que miran los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="696b5-115">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="696b5-116">El origen se encuentra entre los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="696b5-116">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="696b5-117">Está disponible en dispositivos de realidad mixta que incluyen un sistema de seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="696b5-117">It's available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="696b5-118">Se puede acceder a los rayos de mira y hacia la vista a través de la API de  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="696b5-118">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="696b5-119">Llame a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose en la marca de tiempo y el [sistema de coordenadas](coordinate-systems-in-directx.md)especificados.</span><span class="sxs-lookup"><span data-stu-id="696b5-119">Call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="696b5-120">Este SpatialPointerPose contiene el origen y la dirección del encabezado.</span><span class="sxs-lookup"><span data-stu-id="696b5-120">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="696b5-121">También contiene un origen y una dirección de mirada si el seguimiento ocular está disponible.</span><span class="sxs-lookup"><span data-stu-id="696b5-121">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="696b5-122">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="696b5-122">Device support</span></span>

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="696b5-123"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="696b5-123"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="696b5-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="696b5-124"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="696b5-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="696b5-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="696b5-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="696b5-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="696b5-127">Mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="696b5-127">Head-gaze</span></span></td>
     <td><span data-ttu-id="696b5-128">✔️</span><span class="sxs-lookup"><span data-stu-id="696b5-128">✔️</span></span></td>
     <td><span data-ttu-id="696b5-129">✔️</span><span class="sxs-lookup"><span data-stu-id="696b5-129">✔️</span></span></td>
     <td><span data-ttu-id="696b5-130">✔️</span><span class="sxs-lookup"><span data-stu-id="696b5-130">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="696b5-131">Miras hacia abajo</span><span class="sxs-lookup"><span data-stu-id="696b5-131">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="696b5-132">✔️</span><span class="sxs-lookup"><span data-stu-id="696b5-132">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="696b5-133">Uso del encabezado de mira</span><span class="sxs-lookup"><span data-stu-id="696b5-133">Using head-gaze</span></span>

<span data-ttu-id="696b5-134">Para obtener acceso al encabezado de la mirada, empiece llamando a  [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="696b5-134">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="696b5-135">Pase los parámetros siguientes.</span><span class="sxs-lookup"><span data-stu-id="696b5-135">Pass the following parameters.</span></span>
 - <span data-ttu-id="696b5-136">[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa el sistema de coordenadas que se desea para el encabezado.</span><span class="sxs-lookup"><span data-stu-id="696b5-136">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the coordinate system you want for the head-gaze.</span></span> <span data-ttu-id="696b5-137">Se representa mediante la variable *coordenadas* en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="696b5-137">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="696b5-138">Para obtener más información, visite nuestra guía para desarrolladores de [sistemas de coordenadas](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="696b5-138">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="696b5-139">[Marca](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) de tiempo que representa la hora exacta de la solicitud de encabezado.</span><span class="sxs-lookup"><span data-stu-id="696b5-139">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="696b5-140">Normalmente, usará una marca de tiempo que se corresponda con la hora a la que se mostrará el fotograma actual.</span><span class="sxs-lookup"><span data-stu-id="696b5-140">Typically, you'll use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="696b5-141">Puede obtener esta marca de tiempo de visualización de predicción de un objeto  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que es accesible a través de la [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)actual.</span><span class="sxs-lookup"><span data-stu-id="696b5-141">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="696b5-142">Este objeto HolographicFramePrediction se representa mediante la variable de *predicción* en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="696b5-142">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="696b5-143">Una vez que tenga un SpatialPointerPose válido, la posición del encabezado y la dirección hacia delante se pueden obtener como propiedades.</span><span class="sxs-lookup"><span data-stu-id="696b5-143">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="696b5-144">En el código siguiente se muestra cómo obtener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="696b5-144">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="696b5-145">Uso de la mirada</span><span class="sxs-lookup"><span data-stu-id="696b5-145">Using eye-gaze</span></span>

<span data-ttu-id="696b5-146">Para que los usuarios usen la entrada ocular, cada usuario tiene que pasar por una [calibración de usuario de seguimiento de ojos](../../calibration.md) la primera vez que usa el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="696b5-146">For your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](../../calibration.md) the first time they use the device.</span></span> <span data-ttu-id="696b5-147">La API ocular es similar a la de la mirada.</span><span class="sxs-lookup"><span data-stu-id="696b5-147">The eye-gaze API is similar to head-gaze.</span></span>
<span data-ttu-id="696b5-148">Usa la misma API de [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que proporciona un origen y una dirección de rayo que puede Raycast en la escena.</span><span class="sxs-lookup"><span data-stu-id="696b5-148">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="696b5-149">La única diferencia es que debe habilitar explícitamente el seguimiento ocular antes de usarlo:</span><span class="sxs-lookup"><span data-stu-id="696b5-149">The only difference is that you need to explicitly enable eye tracking before using it:</span></span>
1. <span data-ttu-id="696b5-150">Solicitar permiso de usuario para usar el seguimiento ocular en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="696b5-150">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="696b5-151">Habilite la funcionalidad de "entrada de Miración" en el manifiesto del paquete.</span><span class="sxs-lookup"><span data-stu-id="696b5-151">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="696b5-152">Solicitud de acceso a la entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="696b5-152">Requesting access to eye-gaze input</span></span>

<span data-ttu-id="696b5-153">Cuando se inicia la aplicación, llame a [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acceso al seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="696b5-153">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="696b5-154">El sistema solicitará al usuario si es necesario y devolverá [GazeInputAccessStatus:: allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) una vez que se haya concedido el acceso.</span><span class="sxs-lookup"><span data-stu-id="696b5-154">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="696b5-155">Se trata de una llamada asincrónica, por lo que requiere un poco de administración adicional.</span><span class="sxs-lookup"><span data-stu-id="696b5-155">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="696b5-156">En el ejemplo siguiente se pone en marcha un método STD:: Thread separado para esperar el resultado, que almacena en una variable miembro denominada *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="696b5-156">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="696b5-157">Iniciar un subproceso desasociado es solo una opción para controlar las llamadas asincrónicas.</span><span class="sxs-lookup"><span data-stu-id="696b5-157">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="696b5-158">También puede usar la nueva funcionalidad de [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) compatible con C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="696b5-158">You could also use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="696b5-159">Este es otro ejemplo para pedir permiso de usuario:</span><span class="sxs-lookup"><span data-stu-id="696b5-159">Here's another example for asking for user permission:</span></span>
-   <span data-ttu-id="696b5-160">EyesPose:: IsSupported () permite que la aplicación desencadene el cuadro de diálogo de permiso solo si hay un seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="696b5-160">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there's an eye tracker.</span></span>
-   <span data-ttu-id="696b5-161">M_gazeInputAccessStatus GazeInputAccessStatus; Esto es para evitar la acumulación de la solicitud de permiso una y otra vez.</span><span class="sxs-lookup"><span data-stu-id="696b5-161">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="696b5-162">Declarar la capacidad de *entrada de mira*</span><span class="sxs-lookup"><span data-stu-id="696b5-162">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="696b5-163">Haga doble clic en el archivo appxmanifest en *Explorador de soluciones*.</span><span class="sxs-lookup"><span data-stu-id="696b5-163">Double-click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="696b5-164">A continuación, vaya a la sección *funcionalidades* y Compruebe la capacidad de *entrada de mira* .</span><span class="sxs-lookup"><span data-stu-id="696b5-164">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Función de entrada de mirada](images/gaze-input-capability.png)

<span data-ttu-id="696b5-166">Esto agrega las líneas siguientes a la sección *Package* del archivo appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="696b5-166">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="696b5-167">Obtención del rayo ojo</span><span class="sxs-lookup"><span data-stu-id="696b5-167">Getting the eye-gaze ray</span></span>

<span data-ttu-id="696b5-168">Una vez que haya recibido el acceso a ET, tendrá la libertad de captar el rayo cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="696b5-168">Once you have received access to ET, you're free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="696b5-169">Como con el encabezado de la mirada, obtenga el [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) llamando a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con una marca de tiempo y un sistema de coordenadas deseados.</span><span class="sxs-lookup"><span data-stu-id="696b5-169">As with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="696b5-170">SpatialPointerPose contiene un objeto [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) a través de la propiedad [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="696b5-170">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="696b5-171">No es null solo si está habilitado el seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="696b5-171">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="696b5-172">Desde allí, puede comprobar si el usuario del dispositivo tiene una calibración de seguimiento de ojo llamando a [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="696b5-172">From there, you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="696b5-173">A continuación, use la propiedad [fijamente](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obtener el [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) que contiene la posición y la dirección de la mirada.</span><span class="sxs-lookup"><span data-stu-id="696b5-173">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="696b5-174">A veces, la propiedad fijamente puede ser null, por lo que debe asegurarse de comprobarlo.</span><span class="sxs-lookup"><span data-stu-id="696b5-174">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="696b5-175">Esto puede ocurrir si un usuario calibrado cierra temporalmente sus ojos.</span><span class="sxs-lookup"><span data-stu-id="696b5-175">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="696b5-176">En el código siguiente se muestra cómo tener acceso al rayo ojo.</span><span class="sxs-lookup"><span data-stu-id="696b5-176">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a><span data-ttu-id="696b5-177">Reserva cuando el seguimiento ocular no está disponible</span><span class="sxs-lookup"><span data-stu-id="696b5-177">Fallback when eye tracking isn't available</span></span>

<span data-ttu-id="696b5-178">Como se mencionó en nuestros [documentos de diseño de seguimiento ocular](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), los diseñadores y desarrolladores deben tener en cuenta las instancias en las que es posible que los datos de seguimiento ocular no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="696b5-178">As mentioned in our [eye tracking design docs](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), both designers and developers should be aware of instances where eye tracking data may not be available.</span></span>

<span data-ttu-id="696b5-179">Hay varios motivos por los que los datos no están disponibles:</span><span class="sxs-lookup"><span data-stu-id="696b5-179">There are various reasons for data being unavailable:</span></span>
* <span data-ttu-id="696b5-180">Un usuario que no se está calibrando</span><span class="sxs-lookup"><span data-stu-id="696b5-180">A user not being calibrated</span></span>
* <span data-ttu-id="696b5-181">Un usuario ha denegado el acceso de la aplicación a sus datos de seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="696b5-181">A user has denied the app access to his/her eye tracking data</span></span>
* <span data-ttu-id="696b5-182">Interferencias temporales, como las manchas en el parasol o el pelo de HoloLens, occluding los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="696b5-182">Temporary interferences, such as smudges on the HoloLens visor or hair occluding the user's eyes.</span></span> 

<span data-ttu-id="696b5-183">Aunque algunas de las API ya se han mencionado en este documento, en el siguiente se proporciona un resumen de cómo detectar que el seguimiento ocular está disponible como referencia rápida:</span><span class="sxs-lookup"><span data-stu-id="696b5-183">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="696b5-184">Compruebe que el sistema admite el seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="696b5-184">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="696b5-185">Llame al *método* siguiente: [Windows. percepción. people. EyesPose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="696b5-185">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="696b5-186">Compruebe que el usuario está calibrado.</span><span class="sxs-lookup"><span data-stu-id="696b5-186">Check that the user is calibrated.</span></span> <span data-ttu-id="696b5-187">Llame a la *propiedad* siguiente: [Windows. imception. people. EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="696b5-187">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="696b5-188">Compruebe que el usuario ha dado permiso a la aplicación para usar los datos de seguimiento ocular: recupere el _' GazeInputAccessStatus '_ actual.</span><span class="sxs-lookup"><span data-stu-id="696b5-188">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="696b5-189">Un ejemplo de cómo hacerlo se explica cómo solicitar el [acceso a la entrada de mirada](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span><span class="sxs-lookup"><span data-stu-id="696b5-189">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="696b5-190">También puede que desee comprobar que los datos de seguimiento ocular no están obsoletos agregando un tiempo de espera entre las actualizaciones de datos de seguimiento de ojos recibidos y, de lo contrario, reserva a Head-mira como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="696b5-190">You may also want to check that your eye tracking data isn't stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>   
<span data-ttu-id="696b5-191">Para obtener más información, consulte nuestras [consideraciones de diseño de reserva](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) .</span><span class="sxs-lookup"><span data-stu-id="696b5-191">Visit our [fallback design considerations](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="696b5-192">Correlacionar miradamente con otras entradas</span><span class="sxs-lookup"><span data-stu-id="696b5-192">Correlating gaze with other inputs</span></span>

<span data-ttu-id="696b5-193">En ocasiones, es posible que necesite un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) que se corresponda con un evento en el pasado.</span><span class="sxs-lookup"><span data-stu-id="696b5-193">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="696b5-194">Por ejemplo, si el usuario realiza una pulsación aérea, es posible que la aplicación desee saber lo que estaba viendo.</span><span class="sxs-lookup"><span data-stu-id="696b5-194">For example, if the user does an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="696b5-195">Con este propósito, simplemente el uso de [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con el tiempo de fotograma previsto sería incorrecto debido a la latencia entre el procesamiento de la entrada del sistema y el tiempo de presentación.</span><span class="sxs-lookup"><span data-stu-id="696b5-195">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="696b5-196">Además, si se usa la mirada ocular para el destino, nuestros ojos tienden a moverse incluso antes de finalizar una acción de confirmación.</span><span class="sxs-lookup"><span data-stu-id="696b5-196">Also, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="696b5-197">Se trata de un problema menos importante en el caso de una simple pulsación del aire, pero es más crítico cuando se combinan comandos de voz largos con movimientos oculares rápidos.</span><span class="sxs-lookup"><span data-stu-id="696b5-197">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="696b5-198">Una manera de controlar este escenario consiste en realizar una llamada adicional a  [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mediante una marca de tiempo histórica que se corresponda con el evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="696b5-198">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="696b5-199">Sin embargo, para la entrada que enruta a través de SpatialInteractionManager, hay un método más sencillo.</span><span class="sxs-lookup"><span data-stu-id="696b5-199">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="696b5-200">[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tiene su propia función [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="696b5-200">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="696b5-201">Llamar a que proporcionará un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) perfectamente correlacionado sin las conjeturas.</span><span class="sxs-lookup"><span data-stu-id="696b5-201">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="696b5-202">Para obtener más información sobre cómo trabajar con SpatialInteractionSourceStates, eche un vistazo a los [controladores de manos y de movimiento de la documentación de DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="696b5-202">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="696b5-203">Calibración</span><span class="sxs-lookup"><span data-stu-id="696b5-203">Calibration</span></span>

<span data-ttu-id="696b5-204">Para que el seguimiento de los ojos funcione con precisión, cada usuario debe realizar un [seguimiento ocular](../../calibration.md)de la calibración del usuario.</span><span class="sxs-lookup"><span data-stu-id="696b5-204">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](../../calibration.md).</span></span> <span data-ttu-id="696b5-205">Esto permite que el dispositivo ajuste el sistema para una experiencia de visualización más cómoda y de mayor calidad para el usuario y para garantizar un seguimiento de ojo preciso al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="696b5-205">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="696b5-206">Los desarrolladores no tienen que hacer nada en su extremo para administrar la calibración del usuario.</span><span class="sxs-lookup"><span data-stu-id="696b5-206">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="696b5-207">El sistema garantizará que se solicite al usuario que calibre el dispositivo en las siguientes circunstancias:</span><span class="sxs-lookup"><span data-stu-id="696b5-207">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="696b5-208">El usuario está usando el dispositivo por primera vez</span><span class="sxs-lookup"><span data-stu-id="696b5-208">The user is using the device for the first time</span></span>
* <span data-ttu-id="696b5-209">El usuario previamente decidió salir del proceso de calibración</span><span class="sxs-lookup"><span data-stu-id="696b5-209">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="696b5-210">El proceso de calibración no se realizó correctamente la última vez que el usuario usaba el dispositivo</span><span class="sxs-lookup"><span data-stu-id="696b5-210">The calibration process didn't succeed the last time the user used the device</span></span>

<span data-ttu-id="696b5-211">Los desarrolladores deben asegurarse de proporcionar la compatibilidad adecuada para los usuarios en los que es posible que los datos de seguimiento ocular no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="696b5-211">Developers should make sure to provide adequate support for users where eye tracking data may not be available.</span></span> <span data-ttu-id="696b5-212">Más información sobre las consideraciones sobre las soluciones de reserva en el [seguimiento de HoloLens 2](../../design/eye-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="696b5-212">Learn more about considerations for fallback solutions at [Eye tracking on HoloLens 2](../../design/eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="696b5-213">Consulte también</span><span class="sxs-lookup"><span data-stu-id="696b5-213">See also</span></span>

* [<span data-ttu-id="696b5-214">Calibración</span><span class="sxs-lookup"><span data-stu-id="696b5-214">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="696b5-215">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="696b5-215">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="696b5-216">Miras a la vista de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="696b5-216">Eye-gaze on HoloLens 2</span></span>](../../design/eye-tracking.md)
* [<span data-ttu-id="696b5-217">Miran y confirman el modelo de entrada</span><span class="sxs-lookup"><span data-stu-id="696b5-217">Gaze and commit input model</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="696b5-218">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="696b5-218">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="696b5-219">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="696b5-219">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
