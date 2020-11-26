---
title: 'MRTK 101: Uso de Unity con Mixed Reality Toolkit para interacciones espaciales comunes (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)'
description: Uso de Unity con Mixed Reality Toolkit para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, design, sample app, controls, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.localizationpriority: high
ms.openlocfilehash: 95d8f8c52b226eda7ea1601feffc1464c2ea91c5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677535"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="85a4b-104">MRTK 101: Uso de Mixed Reality Toolkit Unity para interacciones espaciales comunes</span><span class="sxs-lookup"><span data-stu-id="85a4b-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>
![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="85a4b-106">Aprende a usar MRTK para lograr algunos de los patrones de interacción comunes más usados en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="85a4b-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="85a4b-107">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="85a4b-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="85a4b-108">¿Cómo agarrar y desplazar un objeto?</span><span class="sxs-lookup"><span data-stu-id="85a4b-108">How to grab and move an object?</span></span>
- <span data-ttu-id="85a4b-109">¿Cómo cambiar el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="85a4b-109">How to resize an object?</span></span>
- <span data-ttu-id="85a4b-110">¿Cómo mover o girar un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="85a4b-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="85a4b-111">¿Cómo conseguir que un objeto responda a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="85a4b-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="85a4b-112">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="85a4b-112">How to add visual feedback?</span></span>
- <span data-ttu-id="85a4b-113">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="85a4b-113">How to add audio feedback?</span></span>
- <span data-ttu-id="85a4b-114">¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="85a4b-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="85a4b-115">¿Cómo hacer que un objeto te siga?</span><span class="sxs-lookup"><span data-stu-id="85a4b-115">How to make an object follow you?</span></span>
- <span data-ttu-id="85a4b-116">¿Cómo hacer que un objeto se ponga delante de ti?</span><span class="sxs-lookup"><span data-stu-id="85a4b-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="85a4b-117">Este artículo se ha actualizado para reflejar los cambios en [MRTK, versión 2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).</span><span class="sxs-lookup"><span data-stu-id="85a4b-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="85a4b-118">Todo el contenido de esta página se puede probar en el editor de Unity con la simulación de entrada de MRTK.</span><span class="sxs-lookup"><span data-stu-id="85a4b-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="85a4b-119">Si no lo ha hecho, siga la [Guía de instalación de MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) para instalar la versión más reciente de MRTK.</span><span class="sxs-lookup"><span data-stu-id="85a4b-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="85a4b-120">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="85a4b-120">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="85a4b-121">MRTK admite la simulación de entrada en el editor.</span><span class="sxs-lookup"><span data-stu-id="85a4b-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="85a4b-122">Simplemente, ejecuta la escena haciendo clic en el botón de juego de Unity.</span><span class="sxs-lookup"><span data-stu-id="85a4b-122">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="85a4b-123">Usa estas claves para simular la entrada.</span><span class="sxs-lookup"><span data-stu-id="85a4b-123">Use these keys to simulate input.</span></span>
<span data-ttu-id="85a4b-124">Presiona las teclas W, A, S y D para mover la cámara.</span><span class="sxs-lookup"><span data-stu-id="85a4b-124">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="85a4b-125">Mantén presionado el botón derecho del ratón y muévelo para mirar alrededor.</span><span class="sxs-lookup"><span data-stu-id="85a4b-125">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="85a4b-126">Para mostrar las manos simuladas, presiona la barra espaciadora (mano derecha) o la tecla Mayús izquierda (mano izquierda). Para mantener las manos simuladas en la vista, presiona la tecla T o Y. Para girar las manos simuladas, presiona Q o E (horizontal)/R o F (vertical).</span><span class="sxs-lookup"><span data-stu-id="85a4b-126">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="85a4b-127">Más información sobre la simulación de entrada en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-127">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="85a4b-128">¿Cómo agarrar y desplazar un objeto?</span><span class="sxs-lookup"><span data-stu-id="85a4b-128">How to grab and move an object?</span></span>
<span data-ttu-id="85a4b-129">Para que un objeto se pueda agarrar, asigna estos dos scripts: **ObjectManipulator.cs** y **NearInteractionGrabbable.cs** (para captación directa con entrada de seguimiento de manos articulada). ObjectManipulator admite interacciones cercanas y lejanas.</span><span class="sxs-lookup"><span data-stu-id="85a4b-129">To make an object grabbable, assign these two scripts: **ObjectManipulator.cs** and **NearInteractionGrabbable.cs**(for direct grab with articulated hand tracking input) ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="85a4b-130">Puedes agarrar y mover un objeto con la entrada de seguimiento de manos articulada de HoloLens 2 (cercana), el haz de mano (lejana), el cursor del controlador de movimiento (lejano), el cursor de mirada de HoloLens y el toque en el aire (lejana).</span><span class="sxs-lookup"><span data-stu-id="85a4b-130">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="85a4b-131">¿Cómo cambiar el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="85a4b-131">How to resize an object?</span></span>
<span data-ttu-id="85a4b-132">**ObjectManipulator.cs** admite el escalado o la rotación con dos manos.</span><span class="sxs-lookup"><span data-stu-id="85a4b-132">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="85a4b-133">Esto funciona con varios tipos de entrada, como la entrada de manos articulada de HoloLens 2, la entrada de mirada y gestos de HoloLens 1 y la entrada del controlador de movimiento del casco envolvente de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="85a4b-133">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="85a4b-134">Más información sobre Object Manipulator en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-134">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="85a4b-135">¿Cómo mover o girar un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="85a4b-135">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="85a4b-136">Asigne **BoundsControl.cs** a un objeto para usar el cuadro de límite, que es la interfaz para escalar y girar un objeto.</span><span class="sxs-lookup"><span data-stu-id="85a4b-136">Assign **BoundsControl.cs** to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="85a4b-137">De forma predeterminada, se muestran los controladores y los cables de color azul del estilo de HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="85a4b-137">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="85a4b-138">Para usar controladores animados basados en proximidad del estilo de HoloLens 2, debes asignar objetos prefabricados y materiales.</span><span class="sxs-lookup"><span data-stu-id="85a4b-138">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="85a4b-139">Más información sobre Bounds Control en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-139">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="85a4b-140">¿Cómo conseguir que un objeto responda a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="85a4b-140">How to make an object respond to input events?</span></span>
<span data-ttu-id="85a4b-141">Asigne **PointerHandler.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="85a4b-141">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="85a4b-142">En el inspector, podrás usar los eventos OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Para usarlos en un script, implementa **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="85a4b-142">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="85a4b-143">Más información sobre el sistema de entrada en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-143">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="85a4b-144">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="85a4b-144">How to add visual feedback?</span></span>
<span data-ttu-id="85a4b-145">Asigne **Interactable.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="85a4b-145">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="85a4b-146">En el inspector, agregue el objeto de destino y cree un nuevo tema.</span><span class="sxs-lookup"><span data-stu-id="85a4b-146">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="85a4b-147">Mediante el uso de perfiles de tema interactuables, puedes agregar comentarios visuales a todos los estados de interacción de entrada disponibles.</span><span class="sxs-lookup"><span data-stu-id="85a4b-147">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="85a4b-148">Los elementos interactuables proporcionan varios tipos de temas, incluido el tema del sombreador, que permite controlar las propiedades del sombreador por estado de interacción.</span><span class="sxs-lookup"><span data-stu-id="85a4b-148">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="85a4b-149">Más información sobre los elementos interactuables en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-149">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="85a4b-150">Otro bloque de creación importante para los comentarios visuales es **MRTK Standard Shader**.</span><span class="sxs-lookup"><span data-stu-id="85a4b-150">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="85a4b-151">Con el sombreador estándar de MRTK, puedes agregar fácilmente efectos de comentarios visuales, como luz de desplazamiento y de proximidad.</span><span class="sxs-lookup"><span data-stu-id="85a4b-151">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="85a4b-152">Dado que el sombreador estándar de MRTK realiza un cálculo significativamente menor que el sombreador estándar de Unity, puedes crear una experiencia de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="85a4b-152">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="85a4b-153">Crea un nuevo material y selecciona el sombreador "Mixed Reality Toolkit > Standard (Estándar)".</span><span class="sxs-lookup"><span data-stu-id="85a4b-153">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="85a4b-154">También puedes elegir uno de los materiales existentes que usan el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="85a4b-154">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="85a4b-155">Más información sobre el sombreador estándar de MRTK en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-155">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="85a4b-156">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="85a4b-156">How to add audio feedback?</span></span>
<span data-ttu-id="85a4b-157">Agregue **AudioSource** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="85a4b-157">Add **AudioSource** to an object.</span></span> <span data-ttu-id="85a4b-158">A continuación, en los scripts que exponen eventos de entrada (p. ej., Interactable.cs o PointerHandler.cs), asigne el objeto con AudioSource al evento y seleccione **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="85a4b-158">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="85a4b-159">Puedes usar los clips de audio o elegir uno de los recursos de audio de MRTK.</span><span class="sxs-lookup"><span data-stu-id="85a4b-159">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="85a4b-160">¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="85a4b-160">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="85a4b-161">MRTK proporciona varios tipos de botones de estilo de Shell (SO) de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="85a4b-161">MRTK provides various types of HoloLens 2's shell (OS) style buttons.</span></span> <span data-ttu-id="85a4b-162">Proporciona comentarios visuales sofisticados, como la luz de proximidad, el cuadro de compresión y un efecto de rizado en la superficie del botón, que mejoran la confianza del usuario.</span><span class="sxs-lookup"><span data-stu-id="85a4b-162">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="85a4b-163">Basta con arrastrar y colocar uno de los **objetos prefabricados de botón presionable del estilo de HoloLens 2** a la escena.</span><span class="sxs-lookup"><span data-stu-id="85a4b-163">Simply drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="85a4b-164">El objeto prefabricado usa Interactable.cs, que se presentó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="85a4b-164">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="85a4b-165">Puedes usar eventos expuestos como OnClick() en el objeto interactuable para desencadenar acciones.</span><span class="sxs-lookup"><span data-stu-id="85a4b-165">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="85a4b-166">Más información sobre los objetos prefabricados de botón en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-166">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="85a4b-167">¿Cómo hacer que un objeto te siga?</span><span class="sxs-lookup"><span data-stu-id="85a4b-167">How to make an object follow you?</span></span>
<span data-ttu-id="85a4b-168">Asigne el script **RadialView.cs** o **Follow.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="85a4b-168">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="85a4b-169">Forma parte de la serie de scripts del solucionador que permite lograr distintos tipos de selección de ubicación de objetos en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="85a4b-169">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="85a4b-170">**SolverHandler.cs** se agregará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="85a4b-170">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="85a4b-171">A continuación se incluye un ejemplo de configuración de RadialView para lograr el comportamiento y la etiqueta "lazy follow" (seguimiento diferido), como el menú Inicio del shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85a4b-171">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="85a4b-172">Puedes especificar la distancia mínima/máxima y los grados de vista mínimos y máximos.</span><span class="sxs-lookup"><span data-stu-id="85a4b-172">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="85a4b-173">En el ejemplo siguiente se muestra cómo colocar el objeto en un intervalo entre 0,4 m y 0,8 m en 15°.</span><span class="sxs-lookup"><span data-stu-id="85a4b-173">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="85a4b-174">Ajusta los valores de tiempo de Lerp para que la actualización posicional sea más rápida o más lenta.</span><span class="sxs-lookup"><span data-stu-id="85a4b-174">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="85a4b-175">Más información sobre los solucionadores en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-175">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="85a4b-176">¿Cómo hacer que un objeto se ponga delante de ti?</span><span class="sxs-lookup"><span data-stu-id="85a4b-176">How to make an object face you?</span></span>
<span data-ttu-id="85a4b-177">Asigne el script **Billboard.cs** a un objeto.</span><span class="sxs-lookup"><span data-stu-id="85a4b-177">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="85a4b-178">Siempre se situará delante de ti, independientemente de tu posición.</span><span class="sxs-lookup"><span data-stu-id="85a4b-178">It will always face you, regardless of your position.</span></span> <span data-ttu-id="85a4b-179">Puedes especificar la opción del eje dinámico.</span><span class="sxs-lookup"><span data-stu-id="85a4b-179">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="85a4b-180">¿Estás listo para crear experiencias sorprendentes para la realidad mixta?</span><span class="sxs-lookup"><span data-stu-id="85a4b-180">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="85a4b-181">Visita las páginas siguientes y obtén más información sobre MRTK y Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="85a4b-181">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="85a4b-182">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="85a4b-182">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="85a4b-183"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="85a4b-183"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="85a4b-184">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="85a4b-184">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="85a4b-185">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="85a4b-185">Next Development Checkpoint</span></span>

<span data-ttu-id="85a4b-186">Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="85a4b-186">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="85a4b-187">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="85a4b-187">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="85a4b-188">Cámara</span><span class="sxs-lookup"><span data-stu-id="85a4b-188">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="85a4b-189">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="85a4b-189">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="85a4b-190">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="85a4b-190">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="85a4b-191">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="85a4b-191">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="85a4b-192">Consulte también</span><span class="sxs-lookup"><span data-stu-id="85a4b-192">See also</span></span>
* [<span data-ttu-id="85a4b-193">Guía de instalación de MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="85a4b-193">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="85a4b-194">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="85a4b-194">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="85a4b-195">Portal de documentación de MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="85a4b-195">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="85a4b-196">Guía de portabilidad de HoloToolkit a MRTK</span><span class="sxs-lookup"><span data-stu-id="85a4b-196">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
