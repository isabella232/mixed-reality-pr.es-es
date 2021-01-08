---
title: Mira fijamente inrealmente
description: Obtenga información sobre cómo configurar y usar la entrada de fijamente con el seguimiento ocular y la orientación del encabezado de las aplicaciones de HoloLens en el caso de que no sea real.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens 2, seguimiento ocular, entrada de mirada, pantalla montada de cabeza, motor no real, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: e546867fe02acd5e72ee76b4108a369ec25fd32f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010145"
---
# <a name="gaze-input"></a>Entrada de mira

La entrada de miras en las aplicaciones de realidad mixta consiste en averiguar qué miran los usuarios. Cuando las cámaras de seguimiento ocular de su dispositivo coinciden con los rayos en el espacio mundial del usuario, la línea de datos de la vista del usuario está disponible. Fijamente se puede usar tanto en Blueprints como en C++, y es una característica principal para los mecanismos como interacción de objetos, búsqueda y controles de cámara.

## <a name="enabling-eye-tracking"></a>Habilitación del seguimiento ocular

- En **configuración del proyecto > HoloLens**, habilite la función de **entrada de mirada** :

![Captura de pantalla de las capacidades de configuración de proyecto de HoloLens con entrada de pág resaltada](images/unreal-gaze-img-01.png)

- Cree un nuevo actor y agréguelo a su escena

> [!NOTE]
> El seguimiento ocular de HoloLens en inreal solo tiene un único rayo de miración para ambos ojos. No se admite el seguimiento de Stereoscopic, que requiere dos rayos.

## <a name="using-eye-tracking"></a>Uso del seguimiento ocular

En primer lugar, compruebe que el dispositivo admite el seguimiento ocular con la función **IsEyeTrackerConnected** .  Si la función devuelve true, llame a **GetGazeData** para buscar el lugar en el que el usuario mira en el fotograma actual:

![Blueprint de la función Connected Tracking](images/unreal-gaze-img-02.png)

> [!NOTE]
> El punto de fijación y el valor de confianza no están disponibles en HoloLens.

Use el origen y la dirección de mira en un seguimiento de línea para averiguar exactamente dónde están buscando los usuarios.  El valor de mirar es un vector, comenzando en el origen de miras y terminando en el origen más la dirección de miración multiplicada por la distancia del seguimiento de línea:

![Blueprint de la función de datos de miras](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Obtener orientación del encabezado

También puede usar el giro de la pantalla montada del cabezal (HMD) para representar la dirección del encabezado del usuario. Puede obtener la dirección del encabezado de los usuarios sin habilitar la función de entrada fijamente, pero no recibirá ninguna información de seguimiento ocular.  Agregue una referencia al plano como el contexto del mundo para obtener los datos de salida correctos:

> [!NOTE]
> La obtención de datos de HMD solo está disponible en 4,26 y versiones posteriores.

![Plano de la función get HMDData](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Usar C++

- En el archivo **Build.CS** del juego, agregue **EyeTracker** a la lista de **PublicDependencyModuleNames** :

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

- En **archivo/nueva clase de c++**, cree un nuevo actor de C++ denominado **EyeTracker**
    - Una solución de Visual Studio abrirá la nueva clase EyeTracker. Compile y ejecute para abrir el juego inreal con el nuevo actor EyeTracker.  Busque "EyeTracker" en la ventana **colocar actores** y arrastre y coloque la clase en la ventana del juego para agregarla al proyecto:

![Captura de pantalla de un actor con la ventana colocar actor abierta](images/unreal-gaze-img-06.png)

- En **EyeTracker. cpp**, agregue includes para **EyeTrackerFunctionLibrary** y **DrawDebugHelpers**:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Compruebe que el dispositivo admite el seguimiento ocular con **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** antes de intentar obtener los datos de miras.  Si se admite el seguimiento ocular, busque el inicio y el final de un rayo para un seguimiento de línea de **UEyeTrackerFunctionLibrary:: GetGazeData**. A partir de ahí, puede crear un vector de miración y pasar su contenido a **LineTraceSingleByChannel** para depurar los resultados de los aciertos de rayo:

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
* [Calibración](../../calibration.md)
* [Comodidad](../../design/comfort.md)
* [Mirada y confirmación](../../design/gaze-and-commit.md)
* [Entrada de voz](../../out-of-scope/voice-design.md)
