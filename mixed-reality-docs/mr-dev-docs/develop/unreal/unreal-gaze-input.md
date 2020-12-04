---
title: Mira fijamente inrealmente
description: Tutorial sobre la configuración de la entrada de fijamente para HoloLens y el motor no real
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578894"
---
# <a name="gaze-input"></a><span data-ttu-id="746f1-104">Entrada de mira</span><span class="sxs-lookup"><span data-stu-id="746f1-104">Gaze Input</span></span>

<span data-ttu-id="746f1-105">Fijamente se usa para indicar lo que el usuario está examinando.</span><span class="sxs-lookup"><span data-stu-id="746f1-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="746f1-106">Esto usa las cámaras de seguimiento de ojo en el dispositivo para buscar un rayo en un espacio de mundo poco real que coincida con lo que está viendo actualmente el usuario.</span><span class="sxs-lookup"><span data-stu-id="746f1-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="746f1-107">Habilitación del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="746f1-107">Enabling eye tracking</span></span>

- <span data-ttu-id="746f1-108">En **configuración del proyecto > HoloLens**, habilite la función de **entrada de mirada** :</span><span class="sxs-lookup"><span data-stu-id="746f1-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Captura de pantalla de las capacidades de configuración de proyecto de HoloLens con entrada de pág resaltada](images/unreal-gaze-img-01.png)

- <span data-ttu-id="746f1-110">Cree un nuevo actor y agréguelo a su escena</span><span class="sxs-lookup"><span data-stu-id="746f1-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="746f1-111">El seguimiento ocular de HoloLens en inreal solo tiene un único rayo de miración para ambos ojos en lugar de los dos rayos necesarios para el seguimiento de Stereoscopic, que no se admite.</span><span class="sxs-lookup"><span data-stu-id="746f1-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="746f1-112">Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="746f1-112">Using eye tracking</span></span>

<span data-ttu-id="746f1-113">En primer lugar, compruebe que el dispositivo admite el seguimiento ocular con la función IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="746f1-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="746f1-114">Si devuelve true, llame a GetGazeData para buscar el lugar en el que el usuario mira en el fotograma actual:</span><span class="sxs-lookup"><span data-stu-id="746f1-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![Blueprint de la función Connected Tracking](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="746f1-116">El punto de fijación y el valor de confianza no están disponibles en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="746f1-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="746f1-117">Para encontrar lo que está buscando el usuario, use el origen y la dirección de mira en un seguimiento de línea.</span><span class="sxs-lookup"><span data-stu-id="746f1-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="746f1-118">El inicio de este vector es el origen de la mirada y el final es el origen más la dirección de miración multiplicada por la distancia deseada:</span><span class="sxs-lookup"><span data-stu-id="746f1-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Blueprint de la función de datos de miras](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="746f1-120">Obtener orientación del encabezado</span><span class="sxs-lookup"><span data-stu-id="746f1-120">Getting head orientation</span></span>

<span data-ttu-id="746f1-121">Como alternativa, se puede utilizar la rotación HMD para representar la dirección del encabezado del usuario.</span><span class="sxs-lookup"><span data-stu-id="746f1-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="746f1-122">Esto no requiere la función de entrada fijamente, pero no le proporcionará información de seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="746f1-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="746f1-123">Se debe agregar una referencia a Blueprint como contexto del mundo para obtener los datos de salida correctos:</span><span class="sxs-lookup"><span data-stu-id="746f1-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="746f1-124">La obtención de datos de HMD solo está disponible en 4,26 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="746f1-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Plano de la función get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="746f1-126">Usar C++</span><span class="sxs-lookup"><span data-stu-id="746f1-126">Using C++</span></span> 

- <span data-ttu-id="746f1-127">En el archivo build.cs del juego, agregue "EyeTracker" a la lista de PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="746f1-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="746f1-128">En "archivo/nueva clase de C++", cree un nuevo actor de C++ llamado "EyeTracker".</span><span class="sxs-lookup"><span data-stu-id="746f1-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="746f1-129">Se abrirá una solución de Visual Studio en la nueva clase EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="746f1-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="746f1-130">Compile y ejecute para abrir el juego inreal con el nuevo actor EyeTracker.</span><span class="sxs-lookup"><span data-stu-id="746f1-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="746f1-131">Busque "EyeTracker" en la ventana "colocar actores".</span><span class="sxs-lookup"><span data-stu-id="746f1-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="746f1-132">Arrastre y coloque esta clase en la ventana del juego para agregarla al proyecto:</span><span class="sxs-lookup"><span data-stu-id="746f1-132">Drag and drop this class into the game window to add it to the project:</span></span>

![Captura de pantalla de un actor con la ventana colocar actor abierta](images/unreal-gaze-img-06.png)

- <span data-ttu-id="746f1-134">En EyeTracker. cpp, agregue includes para EyeTrackerFunctionLibrary y DrawDebugHelpers:</span><span class="sxs-lookup"><span data-stu-id="746f1-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="746f1-135">En marca, compruebe que el dispositivo admite el seguimiento ocular con UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected.</span><span class="sxs-lookup"><span data-stu-id="746f1-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="746f1-136">A continuación, busque el inicio y el final de un rayo para un seguimiento de línea de UEyeTrackerFunctionLibrary:: GetGazeData:</span><span class="sxs-lookup"><span data-stu-id="746f1-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="746f1-137">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="746f1-137">Next Development Checkpoint</span></span>

<span data-ttu-id="746f1-138">Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="746f1-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="746f1-139">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="746f1-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="746f1-140">Seguimiento de las manos</span><span class="sxs-lookup"><span data-stu-id="746f1-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="746f1-141">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="746f1-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="746f1-142">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="746f1-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="746f1-143">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="746f1-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="746f1-144">Consulta también</span><span class="sxs-lookup"><span data-stu-id="746f1-144">See also</span></span>
* [<span data-ttu-id="746f1-145">Calibración</span><span class="sxs-lookup"><span data-stu-id="746f1-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="746f1-146">Comodidad</span><span class="sxs-lookup"><span data-stu-id="746f1-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="746f1-147">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="746f1-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="746f1-148">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="746f1-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
