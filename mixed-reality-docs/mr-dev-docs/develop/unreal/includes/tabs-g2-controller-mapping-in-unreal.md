---
ms.openlocfilehash: 4dde9dcb34553e1ad39d9c732f32f9d0ef174eaf2a6b6fbe7b59b8fdc9facf8d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204294"
---
# <a name="all-platforms"></a>[Todas las plataformas](#tab/all)

Se pueden usar las mismas asignaciones de ejes y acciones en la configuración del proyecto de entrada del juego desde C++.

1. Crear una nueva clase de C++ con archivo/nueva clase de C++...

![Creación de una nueva clase de C++](../images/reverb-g2-img-11.png)

2. Creación de un peón

![Creación de un peón](../images/reverb-g2-img-12.png)

3. En la solución de Visual Studio proyecto, busque la nueva clase Pawn y configúrela para la entrada.
* En primer lugar, en el constructor, establezca AutoPossessPlayer en el primer jugador para enrutar la entrada al peón.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* A continuación, en SetupPlayerInputComponent, enlace acciones y eventos de eje a los nombres de acción desde la configuración de entrada del proyecto.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Agregue las funciones de devolución de llamada a la clase :

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* Actualice el encabezado del peón con las definiciones de función de devolución de llamada:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Compile desde Visual Studio para iniciar el editor con el nuevo peón. Arrastre y coloque el peón desde el explorador de contenido en el juego y el peón ejecutará ahora las devoluciones de llamada cuando se presione la entrada.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Cuando se usan eventos de eje thumbstick, el nombre del evento de eje debe terminar en "_X" o "_Y" correspondiente a la clave utilizada.

![Uso de eventos thumbstick](../images/reverb-g2-img-09.png)

Por último, registre las acciones del juego con SteamVR mediante los botones **Regenerate Action Manifest (Regenerar** manifiesto de acción) y **Regenerate Controller Bindings (Regenerar** enlaces de controlador) Project Configuración > entrada vr de Steam.

![Registro de acciones en la configuración del proyecto](../images/reverb-g2-img-10.png)

