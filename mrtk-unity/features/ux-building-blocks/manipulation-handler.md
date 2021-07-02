---
title: Controlador de manipulación
description: Documentación sobre el controlador de manipulación en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, manipulación,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176630"
---
# <a name="manipulation-handler"></a><span data-ttu-id="5aee7-104">Controlador de manipulación</span><span class="sxs-lookup"><span data-stu-id="5aee7-104">Manipulation handler</span></span>

![Controlador de manipulación](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="5aee7-106">El script *ManipulationHandler* permite que un objeto se pueda mover, escalable y girar con una o dos manos.</span><span class="sxs-lookup"><span data-stu-id="5aee7-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="5aee7-107">La manipulación se puede restringir para que solo permita determinados tipos de transformación.</span><span class="sxs-lookup"><span data-stu-id="5aee7-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="5aee7-108">El script funciona con varios tipos de entradas, como una entrada de mano articulada, rayo HoloLens 2 s de mano, entrada de gesto de HoloLens (1.ª generación) y entrada de controlador de movimiento de casco envolvente.</span><span class="sxs-lookup"><span data-stu-id="5aee7-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="5aee7-109">Uso del controlador de manipulación</span><span class="sxs-lookup"><span data-stu-id="5aee7-109">How to use the manipulation handler</span></span>

<span data-ttu-id="5aee7-110">Agregue el `ManipulationHandler` componente de script a un Objeto GameObject.</span><span class="sxs-lookup"><span data-stu-id="5aee7-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="5aee7-111">Asegúrese de agregar también un colisionador al objeto, que coincida con sus límites que se pueden agarrar.</span><span class="sxs-lookup"><span data-stu-id="5aee7-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="5aee7-112">Para que el objeto responda a una entrada de mano casi articulada, agregue también `NearInteractionGrabbable` el script.</span><span class="sxs-lookup"><span data-stu-id="5aee7-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![Uso del controlador de manipulación en el editor de Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="5aee7-114">Propiedades del inspector</span><span class="sxs-lookup"><span data-stu-id="5aee7-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="5aee7-115">**Transformación de host** Transformación que se arrastrará.</span><span class="sxs-lookup"><span data-stu-id="5aee7-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="5aee7-116">El valor predeterminado es el objeto del componente.</span><span class="sxs-lookup"><span data-stu-id="5aee7-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="5aee7-117">**Tipo de manipulación** Especifica si el objeto se puede manipular con una mano, dos manos o ambas.</span><span class="sxs-lookup"><span data-stu-id="5aee7-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="5aee7-118">*Solo una mano*</span><span class="sxs-lookup"><span data-stu-id="5aee7-118">*One handed only*</span></span>
* <span data-ttu-id="5aee7-119">*Solo dos manos*</span><span class="sxs-lookup"><span data-stu-id="5aee7-119">*Two handed only*</span></span>
* <span data-ttu-id="5aee7-120">*Una y dos manos*</span><span class="sxs-lookup"><span data-stu-id="5aee7-120">*One and Two handed*</span></span>

<span data-ttu-id="5aee7-121">**Tipo de manipulación con dos manos**</span><span class="sxs-lookup"><span data-stu-id="5aee7-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="5aee7-122">*Escala:* solo se permite el escalado.</span><span class="sxs-lookup"><span data-stu-id="5aee7-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="5aee7-123">*Girar:* solo se permite la rotación.</span><span class="sxs-lookup"><span data-stu-id="5aee7-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="5aee7-124">*Mover escala:* se permite el movimiento y el escalado.</span><span class="sxs-lookup"><span data-stu-id="5aee7-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="5aee7-125">*Mover rotación:* se permite mover y girar.</span><span class="sxs-lookup"><span data-stu-id="5aee7-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="5aee7-126">*Girar escala:* se permite la rotación y el escalado.</span><span class="sxs-lookup"><span data-stu-id="5aee7-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="5aee7-127">*Mover escala de rotación:* se permite mover, girar y escalar.</span><span class="sxs-lookup"><span data-stu-id="5aee7-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![Controlador de manipulación](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="5aee7-129">**Permitir manipulación lejana** Especifica si se puede realizar la manipulación mediante la interacción lejana con punteros.</span><span class="sxs-lookup"><span data-stu-id="5aee7-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="5aee7-130">**Modo de rotación de una mano cerca** Especifica cómo se comportará el objeto cuando se esté capturando con una mano o un controlador cerca.</span><span class="sxs-lookup"><span data-stu-id="5aee7-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="5aee7-131">**Modo de rotación de una mano lejos** Especifica cómo se comportará el objeto cuando se esté capturando con una mano o un controlador a distancia.</span><span class="sxs-lookup"><span data-stu-id="5aee7-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="5aee7-132">**Opciones del modo de rotación de una mano** Especifica cómo girará el objeto cuando se le agarró con una mano.</span><span class="sxs-lookup"><span data-stu-id="5aee7-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="5aee7-133">*Mantener la rotación original:* no gira el objeto mientras se mueve.</span><span class="sxs-lookup"><span data-stu-id="5aee7-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="5aee7-134">*Mantener la rotación al usuario:* mantiene al usuario la rotación original del objeto para el eje X/Y.</span><span class="sxs-lookup"><span data-stu-id="5aee7-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="5aee7-135">*La gravedad alineada mantiene la rotación al* usuario: mantiene la rotación original del objeto al usuario, pero hace que el objeto sea vertical.</span><span class="sxs-lookup"><span data-stu-id="5aee7-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="5aee7-136">Útil para objetos con un control de límites.</span><span class="sxs-lookup"><span data-stu-id="5aee7-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="5aee7-137">*Usuario de face:* garantiza que el objeto siempre se enfrenta al usuario.</span><span class="sxs-lookup"><span data-stu-id="5aee7-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="5aee7-138">Útil para paneles o pizarras.</span><span class="sxs-lookup"><span data-stu-id="5aee7-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="5aee7-139">*Cara lejos del usuario:* garantiza que el objeto siempre se aleje del usuario.</span><span class="sxs-lookup"><span data-stu-id="5aee7-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="5aee7-140">Resulta útil para las pizarras o paneles configurados con versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="5aee7-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="5aee7-141">*Girar sobre el centro de objetos:* solo funciona para manos o controladores articulados.</span><span class="sxs-lookup"><span data-stu-id="5aee7-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="5aee7-142">Girar el objeto mediante la rotación de la mano o el controlador, pero sobre el punto central del objeto.</span><span class="sxs-lookup"><span data-stu-id="5aee7-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="5aee7-143">Útil para inspeccionar a distancia.</span><span class="sxs-lookup"><span data-stu-id="5aee7-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="5aee7-144">*Girar sobre el punto de agarre:* solo funciona para manos o controladores articulados.</span><span class="sxs-lookup"><span data-stu-id="5aee7-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="5aee7-145">Gira el objeto como si lo hubiera mantenido la mano o el controlador.</span><span class="sxs-lookup"><span data-stu-id="5aee7-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="5aee7-146">Útil para la inspección.</span><span class="sxs-lookup"><span data-stu-id="5aee7-146">Useful for inspection.</span></span>

<span data-ttu-id="5aee7-147">**Comportamiento de la versión** Cuando se libera un objeto, especifique su comportamiento de movimiento físico.</span><span class="sxs-lookup"><span data-stu-id="5aee7-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="5aee7-148">Requiere que un componente de rigidbody esté en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="5aee7-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="5aee7-149">*Nothing*</span><span class="sxs-lookup"><span data-stu-id="5aee7-149">*Nothing*</span></span>
* <span data-ttu-id="5aee7-150">*Everything (Todo)*</span><span class="sxs-lookup"><span data-stu-id="5aee7-150">*Everything*</span></span>
* <span data-ttu-id="5aee7-151">*Mantener velocidad*</span><span class="sxs-lookup"><span data-stu-id="5aee7-151">*Keep Velocity*</span></span>
* <span data-ttu-id="5aee7-152">*Mantener Angular velocidad*</span><span class="sxs-lookup"><span data-stu-id="5aee7-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="5aee7-153">**Restricciones de rotación** Especifica en qué eje girará el objeto cuando se interactúe con él.</span><span class="sxs-lookup"><span data-stu-id="5aee7-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="5aee7-154">*None*</span><span class="sxs-lookup"><span data-stu-id="5aee7-154">*None*</span></span>
* <span data-ttu-id="5aee7-155">*Solo eje X*</span><span class="sxs-lookup"><span data-stu-id="5aee7-155">*X-Axis Only*</span></span>
* <span data-ttu-id="5aee7-156">*Solo eje Y*</span><span class="sxs-lookup"><span data-stu-id="5aee7-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="5aee7-157">*Solo eje Z*</span><span class="sxs-lookup"><span data-stu-id="5aee7-157">*Z-Axis Only*</span></span>

<span data-ttu-id="5aee7-158">**Usar espacio local para la restricción** Un botón de alternancia para cambiar entre aplicar restricciones con respecto al eje del espacio mundial o al eje de espacio local.</span><span class="sxs-lookup"><span data-stu-id="5aee7-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="5aee7-159">**Restricciones en el movimiento**</span><span class="sxs-lookup"><span data-stu-id="5aee7-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="5aee7-160">*None*</span><span class="sxs-lookup"><span data-stu-id="5aee7-160">*None*</span></span>
* <span data-ttu-id="5aee7-161">*Corrección de la distancia desde la cabeza*</span><span class="sxs-lookup"><span data-stu-id="5aee7-161">*Fix distance from head*</span></span>

<span data-ttu-id="5aee7-162">**Suavizado activo** Especifica si el suavizado está activo.</span><span class="sxs-lookup"><span data-stu-id="5aee7-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="5aee7-163">**Smoothing Amount One Hand** Cantidad de suavizado que se aplicará al movimiento, la escala y la rotación.</span><span class="sxs-lookup"><span data-stu-id="5aee7-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="5aee7-164">Suavizado de 0 significa que no hay suavizado.</span><span class="sxs-lookup"><span data-stu-id="5aee7-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="5aee7-165">El valor máximo significa que no hay ningún cambio en el valor.</span><span class="sxs-lookup"><span data-stu-id="5aee7-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="5aee7-166">Events</span><span class="sxs-lookup"><span data-stu-id="5aee7-166">Events</span></span>

<span data-ttu-id="5aee7-167">El controlador de manipulación proporciona los siguientes eventos:</span><span class="sxs-lookup"><span data-stu-id="5aee7-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="5aee7-168">*OnManipulationStarted:* se desencadena cuando se inicia la manipulación.</span><span class="sxs-lookup"><span data-stu-id="5aee7-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="5aee7-169">*OnManipulationEnded:* se ejecuta cuando finaliza la manipulación.</span><span class="sxs-lookup"><span data-stu-id="5aee7-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="5aee7-170">*OnHoverStarted:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.</span><span class="sxs-lookup"><span data-stu-id="5aee7-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="5aee7-171">*OnHoverEnded:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.</span><span class="sxs-lookup"><span data-stu-id="5aee7-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
