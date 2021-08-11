---
title: Entrada de mirada en Unreal
description: Aprenda a configurar y usar la entrada de mirada con seguimiento ocular y orientación de la cabeza para HoloLens aplicaciones en Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento de los ojos, entrada de mirada, pantalla montada en la cabeza, motor de Unreal, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: e423086e293629e3dfadb49b52a376c0b93f5e465328b93f47c2f1e3e0790b63
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200681"
---
# <a name="gaze-input"></a>Entrada de mirada

La entrada de mirada en las aplicaciones de realidad mixta se trata de averiguar lo que miran los usuarios. Cuando las cámaras de seguimiento de los ojos del dispositivo coinciden con los rayos del espacio mundial de Unreal, los datos de la línea de visión del usuario están disponibles. La mirada se puede usar en planos planos y C++, y es una característica fundamental para mecanismos como la interacción de objetos, la búsqueda de maneras y los controles de cámara.

## <a name="enabling-eye-tracking"></a>Habilitación del seguimiento de los ojos

- En **Project Configuración > HoloLens**, habilite la **funcionalidad Entrada de** mirada:

![Captura de pantalla de HoloLens de configuración del proyecto con la entrada de mirada resaltada](images/unreal-gaze-img-01.png)

- Creación de un actor y adición a la escena

> [!NOTE]
> HoloLens seguimiento de los ojos en Unreal solo tiene un solo rayo de mirada para ambos ojos. No se admite el seguimiento estereocopia, que requiere dos rayos.

## <a name="using-eye-tracking"></a>Uso del seguimiento ocular

En primer lugar, compruebe que el dispositivo admite el seguimiento de los ojos con **la función IsEyeTrackerConnected.**  Si la función devuelve true, llame a **GetGazeData** para buscar dónde se miran los ojos del usuario en el marco actual:

![Plano técnico de la función Is Eye Tracking Connected](images/unreal-gaze-img-02.png)

> [!NOTE]
> El punto de corrección y el valor de confianza no están disponibles en HoloLens.

Use el origen y la dirección de la mirada en un seguimiento de línea para averiguar exactamente dónde buscan los usuarios.  El valor de mirada es un vector, empezando por el origen de la mirada y finalizando en el origen más la dirección de mirada multiplicada por la distancia de seguimiento de línea:

![Plano técnico de la función Get Gaze Data](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Obtener orientación de la cabeza

También puede usar la rotación de head mounted Display (HMD) para representar la dirección de la cabeza del usuario. Puede obtener la dirección principal de los usuarios sin habilitar la funcionalidad Entrada de mirada, pero no le permitirá obtener información de seguimiento de los ojos.  Agregue una referencia al plano técnico como contexto mundial para obtener los datos de salida correctos:

> [!NOTE]
> La obtención de datos HMD solo está disponible en Unreal 4.26 y en adelante.

![Plano técnico de la función Get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Usar C++

- En el archivo **build.cs del** juego, agregue **EyeTracker** a la **lista PublicDependencyModuleNames:**

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

- En **File/New C++ Class (Archivo/Nueva clase de C++),** cree un nuevo actor de C++ llamado **EyeTracker.**
    - Una Visual Studio solución abrirá la nueva clase EyeTracker. Compile y ejecute para abrir el juego de Unreal con el nuevo actor EyeTracker.  Busque "EyeTracker" en la ventana **Colocar** actores y arrastre y coloque la clase en la ventana del juego para agregarla al proyecto:

![Captura de pantalla de un actor con la ventana de actor de lugar abierta](images/unreal-gaze-img-06.png)

- En **EyeTracker.cpp,** agregue includes para **EyeTrackerFunctionLibrary** y **DrawDebugHelpers**:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Compruebe que el dispositivo admite el seguimiento de los ojos **con UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** antes de intentar obtener los datos de mirada.  Si se admite el seguimiento de los ojos, busque el inicio y el final de un rayo para un seguimiento de línea **desde UEyeTrackerFunctionLibrary::GetGazeData**. Desde allí, puede construir un vector de mirada y pasar su contenido a **LineTraceSingleByChannel** para depurar los resultados de cualquier impacto de rayo:

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

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Seguimiento de las manos](unreal-hand-tracking.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Calibración](/hololens/hololens-calibration)
* [Comodidad](../../design/comfort.md)
* [Mirada y confirmación](../../design/gaze-and-commit.md)
* [Entrada de voz](../../out-of-scope/voice-design.md)