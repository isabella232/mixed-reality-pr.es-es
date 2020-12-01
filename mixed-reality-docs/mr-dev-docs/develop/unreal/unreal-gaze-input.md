---
title: Mira fijamente inrealmente
description: Tutorial sobre la configuración de la entrada de fijamente para HoloLens y el motor no real
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: f89638cef6b90e004f097c701c3df13edaf74fac
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354357"
---
# <a name="gaze-input"></a>Entrada de mira

Fijamente se usa para indicar lo que el usuario está examinando.  Esto usa las cámaras de seguimiento de ojo en el dispositivo para buscar un rayo en un espacio de mundo poco real que coincida con lo que está viendo actualmente el usuario.

## <a name="enabling-eye-tracking"></a>Habilitación del seguimiento ocular

- En **configuración del proyecto > HoloLens**, habilite la función de **entrada de mirada** :

![Captura de pantalla de las capacidades de configuración de proyecto de HoloLens con entrada de pág resaltada](images/unreal-gaze-img-01.png)

- Cree un nuevo actor y agréguelo a su escena

> [!NOTE] 
> El seguimiento ocular de HoloLens en inreal solo tiene un único rayo de miración para ambos ojos en lugar de los dos rayos necesarios para el seguimiento de Stereoscopic, que no se admite.

## <a name="using-eye-tracking"></a>Uso del seguimiento ocular

En primer lugar, compruebe que el dispositivo admite el seguimiento ocular con la función IsEyeTrackerConnected.  Si devuelve true, llame a GetGazeData para buscar el lugar en el que el usuario mira en el fotograma actual:

![Blueprint de la función Connected Tracking](images/unreal-gaze-img-02.png)

> [!NOTE]
> El punto de fijación y el valor de confianza no están disponibles en HoloLens.

Para encontrar lo que está buscando el usuario, use el origen y la dirección de mira en un seguimiento de línea.  El inicio de este vector es el origen de la mirada y el final es el origen más la dirección de miración multiplicada por la distancia deseada:

![Blueprint de la función de datos de miras](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Obtener orientación del encabezado

Como alternativa, se puede utilizar la rotación HMD para representar la dirección del encabezado del usuario.  Esto no requiere la función de entrada fijamente, pero no le proporcionará información de seguimiento ocular.  Se debe agregar una referencia a Blueprint como contexto del mundo para obtener los datos de salida correctos:

> [!NOTE]
> La obtención de datos de HMD solo está disponible en 4,26 y versiones posteriores.

![Plano de la función get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Usar C++ 

- En el archivo build.cs del juego, agregue "EyeTracker" a la lista de PublicDependencyModuleNames:

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

- En "archivo/nueva clase de C++", cree un nuevo actor de C++ llamado "EyeTracker".
    - Se abrirá una solución de Visual Studio en la nueva clase EyeTracker. Compile y ejecute para abrir el juego inreal con el nuevo actor EyeTracker.  Busque "EyeTracker" en la ventana "colocar actores".  Arrastre y coloque esta clase en la ventana del juego para agregarla al proyecto:

![Captura de pantalla de un actor con la ventana colocar actor abierta](images/unreal-gaze-img-06.png)

- En EyeTracker. cpp, agregue includes para EyeTrackerFunctionLibrary y DrawDebugHelpers:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

En marca, compruebe que el dispositivo admite el seguimiento ocular con UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected.  A continuación, busque el inicio y el final de un rayo para un seguimiento de línea de UEyeTrackerFunctionLibrary:: GetGazeData:

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

Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación: 

> [!div class="nextstepaction"]
> [Seguimiento de las manos](unreal-hand-tracking.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Calibración](../../calibration.md)
* [Comodidad](../../design/comfort.md)
* [Mirada y confirmación](../../design/gaze-and-commit.md)
* [Entrada de voz](../../out-of-scope/voice-design.md)
