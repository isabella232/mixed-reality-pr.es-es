---
title: Acciones de entrada
description: Documentación para crear acciones de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144150"
---
# <a name="input-actions"></a><span data-ttu-id="e263d-104">Acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="e263d-104">Input actions</span></span>

<span data-ttu-id="e263d-105">[**Las acciones de**](input-actions.md) entrada son abstracciones sobre entradas sin procesar diseñadas para ayudar a aislar la lógica de la aplicación de los orígenes de entrada específicos que producen una entrada.</span><span class="sxs-lookup"><span data-stu-id="e263d-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="e263d-106">Puede ser útil, por ejemplo,  definir una acción Seleccionar y asignarla al botón izquierdo del mouse, un botón en un controlador gamepad y un desencadenador en un controlador de 6 DOF.</span><span class="sxs-lookup"><span data-stu-id="e263d-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="e263d-107">A continuación, puede hacer que la lógica de la aplicación escuche los eventos select *input* action en lugar de tener que tener en cuenta todas las distintas entradas que pueden producirla.</span><span class="sxs-lookup"><span data-stu-id="e263d-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="e263d-108">Creación de una acción de entrada</span><span class="sxs-lookup"><span data-stu-id="e263d-108">Creating an input action</span></span>

<span data-ttu-id="e263d-109">Las acciones de entrada se configuran  en el perfil de acciones de entrada **,** dentro del perfil del sistema de entrada del componente del kit de herramientas de Mixed Reality, especificando un nombre para la acción y el tipo de entradas *(restricción* del eje ) al que se puede asignar:</span><span class="sxs-lookup"><span data-stu-id="e263d-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="e263d-110">Estos son los valores que se usan con más frecuencia para **la restricción de eje:**</span><span class="sxs-lookup"><span data-stu-id="e263d-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="e263d-111">Restricción de eje</span><span class="sxs-lookup"><span data-stu-id="e263d-111">Axis Constraint</span></span> | <span data-ttu-id="e263d-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="e263d-112">Description</span></span>
--- | ---
<span data-ttu-id="e263d-113">Digital</span><span class="sxs-lookup"><span data-stu-id="e263d-113">Digital</span></span> | <span data-ttu-id="e263d-114">Entrada de encendido y apagado como un botón binario en un gamepad o mouse.</span><span class="sxs-lookup"><span data-stu-id="e263d-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="e263d-115">Eje único</span><span class="sxs-lookup"><span data-stu-id="e263d-115">Single Axis</span></span> | <span data-ttu-id="e263d-116">Entrada de eje único, como un desencadenador análogo en un gamepad.</span><span class="sxs-lookup"><span data-stu-id="e263d-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="e263d-117">Eje dual</span><span class="sxs-lookup"><span data-stu-id="e263d-117">Dual Axis</span></span> | <span data-ttu-id="e263d-118">Entrada de eje dual, como una huella digital.</span><span class="sxs-lookup"><span data-stu-id="e263d-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="e263d-119">Seis dof</span><span class="sxs-lookup"><span data-stu-id="e263d-119">Six Dof</span></span> | <span data-ttu-id="e263d-120">Posición 3D con traducción y rotación como la producida por 6 controladores DOF.</span><span class="sxs-lookup"><span data-stu-id="e263d-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="e263d-121">Puede encontrar la lista completa en [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .</span><span class="sxs-lookup"><span data-stu-id="e263d-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="e263d-122">Asignación de entrada a acciones</span><span class="sxs-lookup"><span data-stu-id="e263d-122">Mapping input to actions</span></span>

<span data-ttu-id="e263d-123">La forma de asignar una entrada a una acción y depende del tipo de origen de entrada:</span><span class="sxs-lookup"><span data-stu-id="e263d-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="e263d-124">Entrada del controlador</span><span class="sxs-lookup"><span data-stu-id="e263d-124">Controller input</span></span>

<span data-ttu-id="e263d-125">Vaya al perfil de **asignación de entrada del controlador**, en el perfil del sistema de *entrada*.</span><span class="sxs-lookup"><span data-stu-id="e263d-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="e263d-126">Allí encontrará una lista de todos los controladores admitidos:</span><span class="sxs-lookup"><span data-stu-id="e263d-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="e263d-127">Seleccione la que desea configurar y aparecerá una ventana de diálogo con todas las entradas del controlador, lo que le permite establecer una acción para cada una de ellas:</span><span class="sxs-lookup"><span data-stu-id="e263d-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="e263d-128">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="e263d-128">Speech input</span></span>

<span data-ttu-id="e263d-129">En Perfil **de comando de voz**, en El perfil del sistema *de* entrada , encontrará la lista de comandos de voz definidos actualmente.</span><span class="sxs-lookup"><span data-stu-id="e263d-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="e263d-130">Para asignar uno de ellos a una acción, selecciónelo en la *lista desplegable* Acción.</span><span class="sxs-lookup"><span data-stu-id="e263d-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="e263d-131">Entrada de gesto</span><span class="sxs-lookup"><span data-stu-id="e263d-131">Gesture input</span></span>

<span data-ttu-id="e263d-132">El **perfil de gestos**, en el *perfil del sistema de entrada*, contiene todos los gestos definidos.</span><span class="sxs-lookup"><span data-stu-id="e263d-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="e263d-133">Puede asignar cada una de ellas a una acción seleccionándolo en la *lista desplegable* Acción.</span><span class="sxs-lookup"><span data-stu-id="e263d-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="e263d-134">Control de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="e263d-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="e263d-135">Actualmente solo se pueden controlar las *acciones de* entrada de tipo Digital mediante los métodos descritos en esta sección.</span><span class="sxs-lookup"><span data-stu-id="e263d-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="e263d-136">Para otros tipos de acción, tendrá que controlar directamente los eventos de las entradas correspondientes en su lugar.</span><span class="sxs-lookup"><span data-stu-id="e263d-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="e263d-137">Por ejemplo, para controlar una acción de 6 DOF asignada a las entradas del controlador, tendrá que usar [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) con T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="e263d-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="e263d-138">La manera más fácil de controlar las acciones de entrada es usar el [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span><span class="sxs-lookup"><span data-stu-id="e263d-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="e263d-139">Esto le permite definir la acción que quiere escuchar y reaccionar a los eventos iniciados y finalizados de la acción mediante eventos de Unity.</span><span class="sxs-lookup"><span data-stu-id="e263d-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="e263d-140">Si desea más control, puede implementar la [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interfaz directamente en el script.</span><span class="sxs-lookup"><span data-stu-id="e263d-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="e263d-141">Consulte la sección [**Eventos de entrada**](input-events.md) para obtener más detalles sobre el control de eventos a través de interfaces de controlador.</span><span class="sxs-lookup"><span data-stu-id="e263d-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="e263d-142">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="e263d-142">Examples</span></span>

<span data-ttu-id="e263d-143">Vea una escena de ejemplo en la que se muestra cómo crear una acción, asignarla a entradas de controlador, voz y gestos y usarla para girar un `MRTK/Examples/Demos/Input/Scenes/InputActions` objeto en el comando.</span><span class="sxs-lookup"><span data-stu-id="e263d-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
