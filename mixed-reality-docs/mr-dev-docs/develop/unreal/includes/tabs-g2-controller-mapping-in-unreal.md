---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638741"
---
# <a name="all-platforms"></a>[<span data-ttu-id="b35b8-101">Todas las plataformas</span><span class="sxs-lookup"><span data-stu-id="b35b8-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="b35b8-102">Se pueden usar las mismas asignaciones de acción y eje en la configuración del proyecto de entrada del juego desde C++.</span><span class="sxs-lookup"><span data-stu-id="b35b8-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="b35b8-103">Cree una nueva clase de C++ con una clase de C++ de archivo o nueva...</span><span class="sxs-lookup"><span data-stu-id="b35b8-103">Create a new C++ Class with File/New C++ Class...</span></span>

![Crear una nueva clase de C++](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="b35b8-105">Creación de un peón</span><span class="sxs-lookup"><span data-stu-id="b35b8-105">Create a pawn</span></span>

![Creación de un peón](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="b35b8-107">En la solución de Visual Studio del proyecto, busque la nueva clase peón y configúrela como entrada.</span><span class="sxs-lookup"><span data-stu-id="b35b8-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="b35b8-108">En primer lugar, en el constructor, establezca AutoPossessPlayer en el primer reproductor para enrutar la entrada al peón.</span><span class="sxs-lookup"><span data-stu-id="b35b8-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="b35b8-109">A continuación, en SetupPlayerInputComponent, enlace acciones y eventos de eje a los nombres de acción de la configuración de entrada del proyecto.</span><span class="sxs-lookup"><span data-stu-id="b35b8-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="b35b8-110">Agregue las funciones de devolución de llamada a la clase:</span><span class="sxs-lookup"><span data-stu-id="b35b8-110">Add the callback functions to the class:</span></span>

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

* <span data-ttu-id="b35b8-111">Actualice el encabezado del peón con las definiciones de la función de devolución de llamada:</span><span class="sxs-lookup"><span data-stu-id="b35b8-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="b35b8-112">Compile desde Visual Studio para iniciar el editor con el nuevo peón.</span><span class="sxs-lookup"><span data-stu-id="b35b8-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="b35b8-113">Arrastre y coloque el peón del explorador de contenido en el juego y el peón ejecutará las devoluciones de llamada cuando se presione la entrada.</span><span class="sxs-lookup"><span data-stu-id="b35b8-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="b35b8-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="b35b8-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="b35b8-115">Cuando se usan eventos del eje de stick analógico, el nombre del evento de eje debe terminar en "_X" o "_Y" correspondiente a la clave utilizada.</span><span class="sxs-lookup"><span data-stu-id="b35b8-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![Usar eventos de stick analógico](../images/reverb-g2-img-09.png)

<span data-ttu-id="b35b8-117">Por último, registre las acciones en el juego con SteamVR mediante los botones **regenerar manifiesto de acción** y **volver a generar enlaces de controlador** de configuración del proyecto > entrada de vapor de la salida.</span><span class="sxs-lookup"><span data-stu-id="b35b8-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![Registrar acciones en la configuración del proyecto](../images/reverb-g2-img-10.png)

