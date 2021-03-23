---
title: 'MRTK 101: uso de interacciones espaciales comunes'
description: Uso de Unity con Mixed Reality Toolkit para interacciones básicas en HoloLens 2, HoloLens, Windows Mixed Reality y Open VR.
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, design, sample app, controls, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "98248151"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="3fc77-104">MRTK 101: Uso de Mixed Reality Toolkit Unity para interacciones espaciales comunes</span><span class="sxs-lookup"><span data-stu-id="3fc77-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="3fc77-106">Aprende a usar MRTK para lograr algunos de los patrones de interacción comunes más usados en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="3fc77-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="3fc77-107">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="3fc77-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="3fc77-108">¿Cómo agarrar y desplazar un objeto?</span><span class="sxs-lookup"><span data-stu-id="3fc77-108">How to grab and move an object?</span></span>
- <span data-ttu-id="3fc77-109">¿Cómo cambiar el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="3fc77-109">How to resize an object?</span></span>
- <span data-ttu-id="3fc77-110">¿Cómo mover o girar un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="3fc77-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="3fc77-111">¿Cómo conseguir que un objeto responda a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="3fc77-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="3fc77-112">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="3fc77-112">How to add visual feedback?</span></span>
- <span data-ttu-id="3fc77-113">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="3fc77-113">How to add audio feedback?</span></span>
- <span data-ttu-id="3fc77-114">¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="3fc77-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="3fc77-115">¿Cómo hacer que un objeto te siga?</span><span class="sxs-lookup"><span data-stu-id="3fc77-115">How to make an object follow you?</span></span>
- <span data-ttu-id="3fc77-116">¿Cómo hacer que un objeto se ponga delante de ti?</span><span class="sxs-lookup"><span data-stu-id="3fc77-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="3fc77-117">Este artículo se ha actualizado para reflejar los cambios en [MRTK, versión 2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).</span><span class="sxs-lookup"><span data-stu-id="3fc77-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="3fc77-118">Todo el contenido de esta página se puede probar en el editor de Unity con la simulación de entrada de MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fc77-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="3fc77-119">Si no lo ha hecho, siga la [Guía de instalación de MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) para instalar la versión más reciente de MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fc77-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="3fc77-120">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="3fc77-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="3fc77-121">MRTK admite la simulación de entrada en el editor.</span><span class="sxs-lookup"><span data-stu-id="3fc77-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="3fc77-122">Ejecute la escena haciendo clic en el botón Reproducir de Unity y, a continuación, use las claves siguientes para simular la entrada:</span><span class="sxs-lookup"><span data-stu-id="3fc77-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="3fc77-123">Presiona las teclas W, A, S y D para mover la cámara.</span><span class="sxs-lookup"><span data-stu-id="3fc77-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="3fc77-124">Mantén presionado el botón derecho del ratón y muévelo para mirar alrededor.</span><span class="sxs-lookup"><span data-stu-id="3fc77-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="3fc77-125">Presione la barra espaciadora (mano derecha) o la tecla Mayús izquierda (mano izquierda) para abrir las manos simuladas.</span><span class="sxs-lookup"><span data-stu-id="3fc77-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="3fc77-126">Presione las teclas T o Y para mantener las manos simuladas en la vista.</span><span class="sxs-lookup"><span data-stu-id="3fc77-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="3fc77-127">Presione Q o E (horizontal)/R o F (vertical) para girar las manos simuladas.</span><span class="sxs-lookup"><span data-stu-id="3fc77-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="3fc77-128">Puede obtener más información sobre la simulación de entrada en la [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span><span class="sxs-lookup"><span data-stu-id="3fc77-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="3fc77-129">¿Cómo agarrar y desplazar un objeto?</span><span class="sxs-lookup"><span data-stu-id="3fc77-129">How to grab and move an object?</span></span>

<span data-ttu-id="3fc77-130">Adjunte los scripts **ObjectManipulator.cs** y **NearInteractionGrabbable.cs** para que se pueda obtener un objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc77-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="3fc77-131">ObjectManipulator admite interacciones cercanas y lejanas.</span><span class="sxs-lookup"><span data-stu-id="3fc77-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="3fc77-132">Puede agarrar y mover un objeto con la entrada de seguimiento de manos articulada de HoloLens 2 (cercana), el haz de mano (lejano), el cursor del controlador de movimiento (lejano), el cursor de mirada de HoloLens y el toque en el aire (lejano).</span><span class="sxs-lookup"><span data-stu-id="3fc77-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="3fc77-133">¿Cómo cambiar el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="3fc77-133">How to resize an object?</span></span>
<span data-ttu-id="3fc77-134">**ObjectManipulator.cs** admite el escalado o la rotación con dos manos.</span><span class="sxs-lookup"><span data-stu-id="3fc77-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="3fc77-135">El script funciona con varios tipos de entrada, como la entrada de manos articulada de HoloLens 2, la entrada de mirada y gestos de HoloLens 1 y la entrada del controlador de movimiento del casco envolvente de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3fc77-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="3fc77-136">Más información sobre Object Manipulator en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="3fc77-137">¿Cómo mover o girar un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="3fc77-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="3fc77-138">Asigne **BoundsControl.cs** a un objeto para usar el cuadro de límite, que es la interfaz para escalar y girar un objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc77-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="3fc77-139">De forma predeterminada, se muestran los controladores y los cables de color azul del estilo de HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="3fc77-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="3fc77-140">Para usar controladores animados basados en proximidad del estilo de HoloLens 2, debes asignar objetos prefabricados y materiales.</span><span class="sxs-lookup"><span data-stu-id="3fc77-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="3fc77-141">Más información sobre Bounds Control en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="3fc77-142">¿Cómo conseguir que un objeto responda a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="3fc77-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="3fc77-143">Asigne **PointerHandler.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc77-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="3fc77-144">En el inspector, puede usar los eventos OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Para usarlos en un script, implemente **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="3fc77-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="3fc77-145">Más información sobre el sistema de entrada en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="3fc77-146">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="3fc77-146">How to add visual feedback?</span></span>
<span data-ttu-id="3fc77-147">Asigne **Interactable.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc77-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="3fc77-148">En el inspector, agregue el objeto de destino y cree un nuevo tema.</span><span class="sxs-lookup"><span data-stu-id="3fc77-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="3fc77-149">Mediante el uso de perfiles de tema interactuables, puedes agregar comentarios visuales a todos los estados de interacción de entrada disponibles.</span><span class="sxs-lookup"><span data-stu-id="3fc77-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="3fc77-150">Los elementos interactuables proporcionan varios tipos de temas, incluido el tema del sombreador, que permite controlar las propiedades del sombreador por estado de interacción.</span><span class="sxs-lookup"><span data-stu-id="3fc77-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="3fc77-151">Más información sobre los elementos interactuables en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="3fc77-152">Otro bloque de creación importante para los comentarios visuales es **MRTK Standard Shader**.</span><span class="sxs-lookup"><span data-stu-id="3fc77-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="3fc77-153">Con el sombreador estándar de MRTK, puedes agregar fácilmente efectos de comentarios visuales, como luz de desplazamiento y de proximidad.</span><span class="sxs-lookup"><span data-stu-id="3fc77-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="3fc77-154">Dado que el sombreador estándar de MRTK realiza un cálculo menor que el sombreador estándar de Unity, puede crear una experiencia de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="3fc77-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="3fc77-155">Crea un nuevo material y selecciona el sombreador "Mixed Reality Toolkit > Standard (Estándar)".</span><span class="sxs-lookup"><span data-stu-id="3fc77-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="3fc77-156">También puedes elegir uno de los materiales existentes que usan el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fc77-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="3fc77-157">Más información sobre el sombreador estándar de MRTK en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="3fc77-158">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="3fc77-158">How to add audio feedback?</span></span>
<span data-ttu-id="3fc77-159">Agregue **AudioSource** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc77-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="3fc77-160">A continuación, en los scripts que exponen eventos de entrada (p. ej., Interactable.cs o PointerHandler.cs), asigne el objeto con AudioSource al evento y seleccione **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="3fc77-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="3fc77-161">Puedes usar los clips de audio o elegir uno de los recursos de audio de MRTK.</span><span class="sxs-lookup"><span data-stu-id="3fc77-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="3fc77-162">¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="3fc77-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="3fc77-163">MRTK proporciona varios tipos de botones de estilo de shell (SO) de HoloLens 2, incluidos los comentarios visuales, como la luz de proximidad, el cuadro de compresión y un efecto de ondulación en la superficie del botón, que mejoran la confianza del usuario.</span><span class="sxs-lookup"><span data-stu-id="3fc77-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="3fc77-164">Arrastre y coloque uno de los **objetos prefabricados de botón presionable del estilo de HoloLens 2** a la escena.</span><span class="sxs-lookup"><span data-stu-id="3fc77-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="3fc77-165">El objeto prefabricado usa el Interactable.cs presentado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3fc77-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="3fc77-166">Puedes usar eventos expuestos como OnClick() en el objeto interactuable para desencadenar acciones.</span><span class="sxs-lookup"><span data-stu-id="3fc77-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="3fc77-167">Más información sobre los objetos prefabricados de botón en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="3fc77-168">¿Cómo hacer que un objeto te siga?</span><span class="sxs-lookup"><span data-stu-id="3fc77-168">How to make an object follow you?</span></span>
<span data-ttu-id="3fc77-169">Asigne el script **RadialView.cs** o **Follow.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc77-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="3fc77-170">Forma parte de la serie de scripts del solucionador que permite lograr distintos tipos de selección de ubicación de objetos en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="3fc77-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="3fc77-171">**SolverHandler.cs** se agregará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="3fc77-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="3fc77-172">A continuación se incluye un ejemplo de configuración de RadialView para lograr el comportamiento y la etiqueta "lazy follow" (seguimiento diferido), como el menú Inicio del shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3fc77-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="3fc77-173">Puedes especificar la distancia mínima/máxima y los grados de vista mínimos y máximos.</span><span class="sxs-lookup"><span data-stu-id="3fc77-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="3fc77-174">En el ejemplo siguiente se muestra cómo colocar el objeto en un intervalo entre 0,4 m y 0,8 m en 15°.</span><span class="sxs-lookup"><span data-stu-id="3fc77-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="3fc77-175">Ajusta los valores de tiempo de Lerp para que la actualización posicional sea más rápida o más lenta.</span><span class="sxs-lookup"><span data-stu-id="3fc77-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="3fc77-176">Más información sobre los solucionadores en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="3fc77-177">¿Cómo hacer que un objeto se ponga delante de ti?</span><span class="sxs-lookup"><span data-stu-id="3fc77-177">How to make an object face you?</span></span>
<span data-ttu-id="3fc77-178">Asigne el script **Billboard.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc77-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="3fc77-179">Siempre se situará delante de usted, independientemente de su posición.</span><span class="sxs-lookup"><span data-stu-id="3fc77-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="3fc77-180">Puedes especificar la opción del eje dinámico.</span><span class="sxs-lookup"><span data-stu-id="3fc77-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="3fc77-181">¿Estás listo para crear experiencias sorprendentes para la realidad mixta?</span><span class="sxs-lookup"><span data-stu-id="3fc77-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="3fc77-182">Visita las páginas siguientes y obtén más información sobre MRTK y Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3fc77-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="3fc77-183">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="3fc77-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="3fc77-184"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="3fc77-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="3fc77-185">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="3fc77-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="3fc77-186">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3fc77-186">See also</span></span>
* [<span data-ttu-id="3fc77-187">Guía de instalación de MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3fc77-187">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="3fc77-188">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="3fc77-188">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="3fc77-189">Portal de documentación de MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3fc77-189">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="3fc77-190">Guía de portabilidad de HoloToolkit a MRTK</span><span class="sxs-lookup"><span data-stu-id="3fc77-190">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
