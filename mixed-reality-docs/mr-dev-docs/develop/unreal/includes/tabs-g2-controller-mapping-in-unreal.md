---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638741"
---
# <a name="all-platforms"></a>[Todas las plataformas](#tab/all)

Se pueden usar las mismas asignaciones de acción y eje en la configuración del proyecto de entrada del juego desde C++.

1. Cree una nueva clase de C++ con una clase de C++ de archivo o nueva...

![Crear una nueva clase de C++](../images/reverb-g2-img-11.png)

2. Creación de un peón

![Creación de un peón](../images/reverb-g2-img-12.png)

3. En la solución de Visual Studio del proyecto, busque la nueva clase peón y configúrela como entrada.
* En primer lugar, en el constructor, establezca AutoPossessPlayer en el primer reproductor para enrutar la entrada al peón.

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* A continuación, en SetupPlayerInputComponent, enlace acciones y eventos de eje a los nombres de acción de la configuración de entrada del proyecto.

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* Agregue las funciones de devolución de llamada a la clase:

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

* Actualice el encabezado del peón con las definiciones de la función de devolución de llamada:

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. Compile desde Visual Studio para iniciar el editor con el nuevo peón. Arrastre y coloque el peón del explorador de contenido en el juego y el peón ejecutará las devoluciones de llamada cuando se presione la entrada.

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

Cuando se usan eventos del eje de stick analógico, el nombre del evento de eje debe terminar en "_X" o "_Y" correspondiente a la clave utilizada.

![Usar eventos de stick analógico](../images/reverb-g2-img-09.png)

Por último, registre las acciones en el juego con SteamVR mediante los botones **regenerar manifiesto de acción** y **volver a generar enlaces de controlador** de configuración del proyecto > entrada de vapor de la salida.

![Registrar acciones en la configuración del proyecto](../images/reverb-g2-img-10.png)

