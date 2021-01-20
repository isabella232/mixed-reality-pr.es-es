---
title: Mira fijamente inrealmente
description: Obtenga información sobre cómo configurar y usar la entrada de fijamente con el seguimiento ocular y la orientación del encabezado de las aplicaciones de HoloLens en el caso de que no sea real.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 0c5191534313b94a5382d1065f5a5dd1a208bb49
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98579979"
---
# <a name="gaze-input"></a><span data-ttu-id="d56f5-104">Entrada de mira</span><span class="sxs-lookup"><span data-stu-id="d56f5-104">Gaze Input</span></span>

<span data-ttu-id="d56f5-105">La entrada de miras en las aplicaciones de realidad mixta consiste en averiguar qué miran los usuarios.</span><span class="sxs-lookup"><span data-stu-id="d56f5-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="d56f5-106">Cuando las cámaras de seguimiento ocular de su dispositivo coinciden con los rayos en el espacio mundial del usuario, la línea de datos de la vista del usuario está disponible.</span><span class="sxs-lookup"><span data-stu-id="d56f5-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="d56f5-107">Fijamente se puede usar tanto en Blueprints como en C++, y es una característica principal para los mecanismos como interacción de objetos, búsqueda y controles de cámara.</span><span class="sxs-lookup"><span data-stu-id="d56f5-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="d56f5-108">Habilitación del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="d56f5-108">Enabling eye tracking</span></span>

- <span data-ttu-id="d56f5-109">En **configuración del proyecto > HoloLens**, habilite la función de **entrada de mirada** :</span><span class="sxs-lookup"><span data-stu-id="d56f5-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Captura de pantalla de las capacidades de configuración de proyecto de HoloLens con entrada de pág resaltada](images/unreal-gaze-img-01.png)

- <span data-ttu-id="d56f5-111">Cree un nuevo actor y agréguelo a su escena</span><span class="sxs-lookup"><span data-stu-id="d56f5-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="d56f5-112">El seguimiento ocular de HoloLens en inreal solo tiene un único rayo de miración para ambos ojos.</span><span class="sxs-lookup"><span data-stu-id="d56f5-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="d56f5-113">No se admite el seguimiento de Stereoscopic, que requiere dos rayos.</span><span class="sxs-lookup"><span data-stu-id="d56f5-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="d56f5-114">Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="d56f5-114">Using eye tracking</span></span>

<span data-ttu-id="d56f5-115">En primer lugar, compruebe que el dispositivo admite el seguimiento ocular con la función **IsEyeTrackerConnected** .</span><span class="sxs-lookup"><span data-stu-id="d56f5-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="d56f5-116">Si la función devuelve true, llame a **GetGazeData** para buscar el lugar en el que el usuario mira en el fotograma actual:</span><span class="sxs-lookup"><span data-stu-id="d56f5-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![Blueprint de la función Connected Tracking](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="d56f5-118">El punto de fijación y el valor de confianza no están disponibles en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d56f5-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="d56f5-119">Use el origen y la dirección de mira en un seguimiento de línea para averiguar exactamente dónde están buscando los usuarios.</span><span class="sxs-lookup"><span data-stu-id="d56f5-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="d56f5-120">El valor de mirar es un vector, comenzando en el origen de miras y terminando en el origen más la dirección de miración multiplicada por la distancia del seguimiento de línea:</span><span class="sxs-lookup"><span data-stu-id="d56f5-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Blueprint de la función de datos de miras](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="d56f5-122">Obtener orientación del encabezado</span><span class="sxs-lookup"><span data-stu-id="d56f5-122">Getting head orientation</span></span>

<span data-ttu-id="d56f5-123">También puede usar el giro de la pantalla montada del cabezal (HMD) para representar la dirección del encabezado del usuario.</span><span class="sxs-lookup"><span data-stu-id="d56f5-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="d56f5-124">Puede obtener la dirección del encabezado de los usuarios sin habilitar la función de entrada fijamente, pero no recibirá ninguna información de seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="d56f5-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="d56f5-125">Agregue una referencia al plano como el contexto del mundo para obtener los datos de salida correctos:</span><span class="sxs-lookup"><span data-stu-id="d56f5-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="d56f5-126">La obtención de datos de HMD solo está disponible en 4,26 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="d56f5-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Plano de la función get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="d56f5-128">Usar C++</span><span class="sxs-lookup"><span data-stu-id="d56f5-128">Using C++</span></span>

- <span data-ttu-id="d56f5-129">En el archivo **Build.CS** del juego, agregue **EyeTracker** a la lista de **PublicDependencyModuleNames** :</span><span class="sxs-lookup"><span data-stu-id="d56f5-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- <span data-ttu-id="d56f5-130">En **archivo/nueva clase de c++**, cree un nuevo actor de C++ denominado **EyeTracker**</span><span class="sxs-lookup"><span data-stu-id="d56f5-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="d56f5-131">Una solución de Visual Studio abrirá la nueva clase EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="d56f5-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="d56f5-132">Compile y ejecute para abrir el juego inreal con el nuevo actor EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="d56f5-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="d56f5-133">Busque "EyeTracker" en la ventana **colocar actores** y arrastre y coloque la clase en la ventana del juego para agregarla al proyecto:</span><span class="sxs-lookup"><span data-stu-id="d56f5-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![Captura de pantalla de un actor con la ventana colocar actor abierta](images/unreal-gaze-img-06.png)

- <span data-ttu-id="d56f5-135">En **EyeTracker. cpp**, agregue includes para **EyeTrackerFunctionLibrary** y **DrawDebugHelpers**:</span><span class="sxs-lookup"><span data-stu-id="d56f5-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="d56f5-136">Compruebe que el dispositivo admite el seguimiento ocular con **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** antes de intentar obtener los datos de miras.</span><span class="sxs-lookup"><span data-stu-id="d56f5-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="d56f5-137">Si se admite el seguimiento ocular, busque el inicio y el final de un rayo para un seguimiento de línea de **UEyeTrackerFunctionLibrary:: GetGazeData**.</span><span class="sxs-lookup"><span data-stu-id="d56f5-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="d56f5-138">A partir de ahí, puede crear un vector de miración y pasar su contenido a **LineTraceSingleByChannel** para depurar los resultados de los aciertos de rayo:</span><span class="sxs-lookup"><span data-stu-id="d56f5-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="d56f5-139">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="d56f5-139">Next Development Checkpoint</span></span>

<span data-ttu-id="d56f5-140">Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d56f5-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="d56f5-141">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="d56f5-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d56f5-142">Seguimiento de las manos</span><span class="sxs-lookup"><span data-stu-id="d56f5-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="d56f5-143">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="d56f5-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d56f5-144">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="d56f5-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="d56f5-145">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="d56f5-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d56f5-146">Consulta también</span><span class="sxs-lookup"><span data-stu-id="d56f5-146">See also</span></span>
* [<span data-ttu-id="d56f5-147">Calibración</span><span class="sxs-lookup"><span data-stu-id="d56f5-147">Calibration</span></span>](/hololens/hololens-calibration)
* [<span data-ttu-id="d56f5-148">Comodidad</span><span class="sxs-lookup"><span data-stu-id="d56f5-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="d56f5-149">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="d56f5-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="d56f5-150">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="d56f5-150">Voice input</span></span>](../../out-of-scope/voice-design.md)