---
title: Controladores de movimiento en Unity
description: Obtenga información sobre cómo realizar acciones en la mirada en Unity con la entrada del controlador de movimiento mediante XR y las API comunes de botón y eje.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: controladores de movimiento, unity, entrada, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: ff1eedcc337edd2d7edfe8d961bb88bcb859cd23
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743478"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="de3f5-104">Controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="de3f5-104">Motion controllers in Unity</span></span>

<span data-ttu-id="de3f5-105">Hay dos maneras clave de tomar medidas en [](../../design/motion-controllers.md) la mirada en [Unity,](gaze-in-unity.md) [gestos](../../design/gaze-and-commit.md#composite-gestures) de mano y controladores de movimiento en HoloLens y HMD inmersivo.</span><span class="sxs-lookup"><span data-stu-id="de3f5-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="de3f5-106">Puede acceder a los datos de ambos orígenes de entrada espacial a través de las mismas API en Unity.</span><span class="sxs-lookup"><span data-stu-id="de3f5-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="de3f5-107">Unity proporciona dos formas principales de acceder a los datos de entrada espacial para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="de3f5-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="de3f5-108">Las API *Input.GetButton/Input.GetAxis* comunes funcionan en varios SDK XR de Unity, mientras que la API *InteractionManager/GestureRecognizer* específica de Windows Mixed Reality expone el conjunto completo de datos de entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="de3f5-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="de3f5-109">API de entrada XR de Unity</span><span class="sxs-lookup"><span data-stu-id="de3f5-109">Unity XR input APIs</span></span>

<span data-ttu-id="de3f5-110">Para los proyectos nuevos, se recomienda usar las nuevas API de entrada XR desde el principio.</span><span class="sxs-lookup"><span data-stu-id="de3f5-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="de3f5-111">Puede encontrar más información sobre las [API de XR aquí.](https://docs.unity3d.com/Manual/xr_input.html)</span><span class="sxs-lookup"><span data-stu-id="de3f5-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="de3f5-112">Tabla de asignación de botones y ejes de Unity</span><span class="sxs-lookup"><span data-stu-id="de3f5-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="de3f5-113">El Administrador de entrada de Unity para Windows Mixed Reality de movimiento admite los valores de botón y de eje que se enumeran a continuación a través de las API *Input.GetButton/GetAxis.*</span><span class="sxs-lookup"><span data-stu-id="de3f5-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="de3f5-114">La columna "Específico de Mr. de Windows" hace referencia a las propiedades disponibles fuera del *tipo InteractionSourceState.*</span><span class="sxs-lookup"><span data-stu-id="de3f5-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="de3f5-115">Cada una de estas API se describe en detalle en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="de3f5-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="de3f5-116">Las asignaciones de identificadores de botón o eje Windows Mixed Reality suelen coincidir con los identificadores de botón o eje de Oculus.</span><span class="sxs-lookup"><span data-stu-id="de3f5-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="de3f5-117">Las asignaciones de identificadores de botón o eje Windows Mixed Reality de las asignaciones de OpenVR de dos maneras:</span><span class="sxs-lookup"><span data-stu-id="de3f5-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="de3f5-118">La asignación usa los IDs del panel táctil que son distintos de la huella digital, para admitir controladores con los controladores tanto con los controladores como con los controladores táctiles.</span><span class="sxs-lookup"><span data-stu-id="de3f5-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="de3f5-119">La asignación evita sobrecargar los ID de los botones A y X de los botones Menú para dejarlos disponibles para los botones FÍSICOS ABXY.</span><span class="sxs-lookup"><span data-stu-id="de3f5-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="de3f5-120">Entrada</span><span class="sxs-lookup"><span data-stu-id="de3f5-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="de3f5-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API comunes de Unity</a></span><span class="sxs-lookup"><span data-stu-id="de3f5-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="de3f5-122">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="de3f5-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="de3f5-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">API de entrada específica de MR de Windows</a></span><span class="sxs-lookup"><span data-stu-id="de3f5-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="de3f5-124">(XR. Wsa. Entrada)</span><span class="sxs-lookup"><span data-stu-id="de3f5-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="de3f5-125">Mano izquierda</span><span class="sxs-lookup"><span data-stu-id="de3f5-125">Left hand</span></span> </th><th> <span data-ttu-id="de3f5-126">Mano derecha</span><span class="sxs-lookup"><span data-stu-id="de3f5-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="de3f5-127">Selección del desencadenador presionado</span><span class="sxs-lookup"><span data-stu-id="de3f5-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="de3f5-128">Eje 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="de3f5-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="de3f5-129">Eje 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="de3f5-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="de3f5-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="de3f5-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-131">Selección del valor análogo del desencadenador</span><span class="sxs-lookup"><span data-stu-id="de3f5-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="de3f5-132">Eje 9</span><span class="sxs-lookup"><span data-stu-id="de3f5-132">Axis 9</span></span> </td><td> <span data-ttu-id="de3f5-133">Eje 10</span><span class="sxs-lookup"><span data-stu-id="de3f5-133">Axis 10</span></span> </td><td> <span data-ttu-id="de3f5-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="de3f5-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-135">Seleccionar desencadenador presionado parcialmente</span><span class="sxs-lookup"><span data-stu-id="de3f5-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="de3f5-136">Botón 14 <i>(compatibilidad con el gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="de3f5-137">Botón 15 <i>(compatibilidad con el gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="de3f5-138">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="de3f5-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-139">Botón menú presionado</span><span class="sxs-lookup"><span data-stu-id="de3f5-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="de3f5-140">Botón 6\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-140">Button 6\*</span></span> </td><td> <span data-ttu-id="de3f5-141">Botón 7\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-141">Button 7\*</span></span> </td><td> <span data-ttu-id="de3f5-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="de3f5-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-143">Botón De control presionado</span><span class="sxs-lookup"><span data-stu-id="de3f5-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="de3f5-144">Eje 11 = 1,0 (sin valores análogos)</span><span class="sxs-lookup"><span data-stu-id="de3f5-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="de3f5-145">Botón 4 <i>(compatibilidad con el gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="de3f5-146">Eje 12 = 1,0 (sin valores análogos)</span><span class="sxs-lookup"><span data-stu-id="de3f5-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="de3f5-147">Botón 5 <i>(compatibilidad con el gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="de3f5-148">Agarró</span><span class="sxs-lookup"><span data-stu-id="de3f5-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="de3f5-150">Eje 1</span><span class="sxs-lookup"><span data-stu-id="de3f5-150">Axis 1</span></span> </td><td> <span data-ttu-id="de3f5-151">Eje 4</span><span class="sxs-lookup"><span data-stu-id="de3f5-151">Axis 4</span></span> </td><td> <span data-ttu-id="de3f5-152">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="de3f5-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="de3f5-154">Eje 2</span><span class="sxs-lookup"><span data-stu-id="de3f5-154">Axis 2</span></span> </td><td> <span data-ttu-id="de3f5-155">Eje 5</span><span class="sxs-lookup"><span data-stu-id="de3f5-155">Axis 5</span></span> </td><td> <span data-ttu-id="de3f5-156">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="de3f5-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-157">Thumbstick pressed</span><span class="sxs-lookup"><span data-stu-id="de3f5-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="de3f5-158">Botón 8</span><span class="sxs-lookup"><span data-stu-id="de3f5-158">Button 8</span></span> </td><td> <span data-ttu-id="de3f5-159">Botón 9</span><span class="sxs-lookup"><span data-stu-id="de3f5-159">Button 9</span></span> </td><td> <span data-ttu-id="de3f5-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="de3f5-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-161">Touchpad X <i>(izquierda: -1.0, derecha: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="de3f5-162">Eje 17\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="de3f5-163">Eje 19\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="de3f5-164">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="de3f5-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-165">Touchpad Y <i>(superior: -1.0, inferior: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="de3f5-166">Eje 18\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="de3f5-167">Eje 20\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="de3f5-168">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="de3f5-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-169">Touchpad tocado</span><span class="sxs-lookup"><span data-stu-id="de3f5-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="de3f5-170">Botón 18\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-170">Button 18\*</span></span> </td><td> <span data-ttu-id="de3f5-171">Botón 19\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-171">Button 19\*</span></span> </td><td> <span data-ttu-id="de3f5-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="de3f5-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-173">Touchpad presionado</span><span class="sxs-lookup"><span data-stu-id="de3f5-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="de3f5-174">Botón 16\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-174">Button 16\*</span></span> </td><td> <span data-ttu-id="de3f5-175">Botón 17\*</span><span class="sxs-lookup"><span data-stu-id="de3f5-175">Button 17\*</span></span> </td><td> <span data-ttu-id="de3f5-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="de3f5-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-177">6 Posición de control o posición de puntero de DoF</span><span class="sxs-lookup"><span data-stu-id="de3f5-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="de3f5-178"><i>Solo</i> posición de control: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="de3f5-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="de3f5-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="de3f5-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="de3f5-180">Pasar <i>control</i> o <i>puntero</i> como argumento: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="de3f5-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="de3f5-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="de3f5-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-182">Estado de seguimiento</span><span class="sxs-lookup"><span data-stu-id="de3f5-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="de3f5-183"><i>La precisión de la posición y el riesgo de pérdida de origen solo están disponibles a través de la API específica de MR.</i> </span><span class="sxs-lookup"><span data-stu-id="de3f5-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="de3f5-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="de3f5-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="de3f5-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="de3f5-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="de3f5-186">Estos IDs de botón o eje difieren de los que usa Unity para OpenVR debido a colisiones en las asignaciones que usan los gamepads, Oculus Touch y OpenVR.</span><span class="sxs-lookup"><span data-stu-id="de3f5-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="de3f5-187">Posición de control frente a posición de apuntar</span><span class="sxs-lookup"><span data-stu-id="de3f5-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="de3f5-188">Windows Mixed Reality admite controladores de movimiento en una variedad de factores de forma.</span><span class="sxs-lookup"><span data-stu-id="de3f5-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="de3f5-189">El diseño de cada controlador difiere en su relación entre la posición de la mano del usuario y la dirección "hacia delante" natural que las aplicaciones deben usar para señalar al representar el controlador.</span><span class="sxs-lookup"><span data-stu-id="de3f5-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="de3f5-190">Para representar mejor estos controladores, hay dos tipos de poses que puede investigar para cada origen de interacción: la posición del **control** y la **posición del puntero.**</span><span class="sxs-lookup"><span data-stu-id="de3f5-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="de3f5-191">Tanto las coordenadas de posición de control como de posición de puntero se expresan mediante todas las API de Unity en coordenadas globales del mundo de Unity.</span><span class="sxs-lookup"><span data-stu-id="de3f5-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="de3f5-192">Posición de control</span><span class="sxs-lookup"><span data-stu-id="de3f5-192">Grip pose</span></span>

<span data-ttu-id="de3f5-193">La **posición del control** representa la ubicación de la mano de los usuarios, ya sea detectada por holoLens o que mantiene un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="de3f5-194">En los cascos envolventes, la  posición del control se usa mejor para representar la mano del usuario o un objeto que se **mantiene en la mano del usuario.**</span><span class="sxs-lookup"><span data-stu-id="de3f5-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="de3f5-195">La posición de control también se usa al visualizar un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="de3f5-196">El **modelo procesable proporcionado** por Windows para un controlador de movimiento usa la posición de control como su origen y centro de rotación.</span><span class="sxs-lookup"><span data-stu-id="de3f5-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="de3f5-197">La posición de control se define específicamente de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="de3f5-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="de3f5-198">Posición **del control:** centroide de mano al mantener el controlador de forma natural, ajustado a la izquierda o derecha para centrar la posición dentro del control.</span><span class="sxs-lookup"><span data-stu-id="de3f5-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="de3f5-199">En el Windows Mixed Reality de movimiento, esta posición se alinea generalmente con el botón Desajegar.</span><span class="sxs-lookup"><span data-stu-id="de3f5-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="de3f5-200">Eje **derecho** de la orientación del control: cuando se abre completamente la mano para formar una posición plana de 5 dedos, el rayo que es normal para la mano (hacia delante desde la mano izquierda, hacia atrás desde la mano derecha).</span><span class="sxs-lookup"><span data-stu-id="de3f5-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="de3f5-201">Eje **hacia** delante de la orientación del control: cuando cierra la mano parcialmente (como si sostendía el controlador), el rayo que señala "hacia delante" a través del metro formado por los dedos que no son de posición.</span><span class="sxs-lookup"><span data-stu-id="de3f5-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="de3f5-202">Eje **Up de la orientación del control:** eje Up implícito en las definiciones Right y Forward.</span><span class="sxs-lookup"><span data-stu-id="de3f5-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="de3f5-203">Puede acceder a la posición de control a través de la API de entrada entre proveedores de Unity *[(XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o a través de la API específica de MR de Windows *(sourceState.sourcePose.TryGetPosition/Rotation,* solicitando datos de posición para el **nodo Control).**</span><span class="sxs-lookup"><span data-stu-id="de3f5-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="de3f5-204">Posición de puntero</span><span class="sxs-lookup"><span data-stu-id="de3f5-204">Pointer pose</span></span>

<span data-ttu-id="de3f5-205">La **posición del puntero** representa la punta del controlador que apunta hacia delante.</span><span class="sxs-lookup"><span data-stu-id="de3f5-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="de3f5-206">La posición de puntero proporcionada por el sistema se usa mejor para la difusión por rayos cuando se representa **el propio modelo de controlador.**</span><span class="sxs-lookup"><span data-stu-id="de3f5-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="de3f5-207">Si va a representar algún otro objeto virtual en lugar del controlador, como un revólver virtual, debe apuntar con un rayo que sea más natural para ese objeto virtual, como un rayo que viaja a lo largo de la batería del modelo de revólver definido por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="de3f5-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="de3f5-208">Dado que los usuarios pueden ver el objeto virtual y no el controlador físico, es probable que apuntar con el objeto virtual sea más natural para aquellos que usan la aplicación.</span><span class="sxs-lookup"><span data-stu-id="de3f5-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="de3f5-209">Actualmente, la posición del puntero solo está disponible en Unity a través de la API específica de MR de Windows, *sourceState.sourcePose.TryGetPosition/Rotation,* pasando *InteractionSourceNode.Pointer* como argumento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="de3f5-210">Estado de seguimiento del controlador</span><span class="sxs-lookup"><span data-stu-id="de3f5-210">Controller tracking state</span></span>

<span data-ttu-id="de3f5-211">Al igual que los cascos, el Windows Mixed Reality de movimiento no requiere ninguna configuración de sensores de seguimiento externos.</span><span class="sxs-lookup"><span data-stu-id="de3f5-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="de3f5-212">En su lugar, los sensores del propio casco realiza el seguimiento de los controladores.</span><span class="sxs-lookup"><span data-stu-id="de3f5-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="de3f5-213">Si el usuario mueve los controladores fuera del campo de vista del casco, Windows sigue inferiendo las posiciones del controlador en la mayoría de los casos.</span><span class="sxs-lookup"><span data-stu-id="de3f5-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="de3f5-214">Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se colocarán en posiciones de precisión aproximada.</span><span class="sxs-lookup"><span data-stu-id="de3f5-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="de3f5-215">En este punto, el sistema bloqueará el controlador con el cuerpo del usuario, haciendo un seguimiento de la posición del usuario a medida que se mueve, mientras sigue exponiendo la verdadera orientación del controlador mediante sus sensores de orientación internos.</span><span class="sxs-lookup"><span data-stu-id="de3f5-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="de3f5-216">Muchas aplicaciones que usan controladores para apuntar y activar elementos de la interfaz de usuario pueden funcionar con normalidad mientras tienen una precisión aproximada sin que el usuario se de cuenta.</span><span class="sxs-lookup"><span data-stu-id="de3f5-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="de3f5-217">Razonamiento sobre el seguimiento del estado explícitamente</span><span class="sxs-lookup"><span data-stu-id="de3f5-217">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="de3f5-218">Las aplicaciones que desean tratar las posiciones de forma diferente en función del estado de seguimiento pueden ir más allá e inspeccionar las propiedades en el estado del controlador, como *SourceLossRisk* y *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="de3f5-218">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="de3f5-219">Estado de seguimiento</span><span class="sxs-lookup"><span data-stu-id="de3f5-219">Tracking state</span></span> </th><th> <span data-ttu-id="de3f5-220">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="de3f5-220">SourceLossRisk</span></span> </th><th> <span data-ttu-id="de3f5-221">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="de3f5-221">PositionAccuracy</span></span> </th><th> <span data-ttu-id="de3f5-222">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="de3f5-222">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="de3f5-223"><b>Alta precisión</b> </span><span class="sxs-lookup"><span data-stu-id="de3f5-223"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="de3f5-224">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="de3f5-224">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="de3f5-225">Alto</span><span class="sxs-lookup"><span data-stu-id="de3f5-225">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="de3f5-226">true</span><span class="sxs-lookup"><span data-stu-id="de3f5-226">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-227"><b>Alta precisión (en riesgo de pérdida)</b> </span><span class="sxs-lookup"><span data-stu-id="de3f5-227"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="de3f5-228">== 1,0</span><span class="sxs-lookup"><span data-stu-id="de3f5-228">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="de3f5-229">Alto</span><span class="sxs-lookup"><span data-stu-id="de3f5-229">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="de3f5-230">true</span><span class="sxs-lookup"><span data-stu-id="de3f5-230">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-231"><b>Precisión aproximada</b> </span><span class="sxs-lookup"><span data-stu-id="de3f5-231"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="de3f5-232">== 1,0</span><span class="sxs-lookup"><span data-stu-id="de3f5-232">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="de3f5-233">Aproximado</span><span class="sxs-lookup"><span data-stu-id="de3f5-233">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="de3f5-234">true</span><span class="sxs-lookup"><span data-stu-id="de3f5-234">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="de3f5-235"><b>Sin posición</b> </span><span class="sxs-lookup"><span data-stu-id="de3f5-235"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="de3f5-236">== 1,0</span><span class="sxs-lookup"><span data-stu-id="de3f5-236">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="de3f5-237">Aproximado</span><span class="sxs-lookup"><span data-stu-id="de3f5-237">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="de3f5-238">false</span><span class="sxs-lookup"><span data-stu-id="de3f5-238">false</span></span></td>
</tr>
</table>

<span data-ttu-id="de3f5-239">Estos estados de seguimiento del controlador de movimiento se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="de3f5-239">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="de3f5-240">**Alta precisión:** Aunque el controlador de movimiento está dentro del campo de vista del casco, generalmente proporcionará posiciones de alta precisión, en función del seguimiento visual.</span><span class="sxs-lookup"><span data-stu-id="de3f5-240">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="de3f5-241">Un controlador en movimiento que abandona momentáneamente el campo de visión o se oculta momentáneamente de los sensores de casco (por ejemplo, por la otra mano del usuario) seguirá devolviendo poses de alta precisión durante un breve período de tiempo, en función del seguimiento inerte del propio controlador.</span><span class="sxs-lookup"><span data-stu-id="de3f5-241">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="de3f5-242">**Alta precisión (en riesgo de perder):** Cuando el usuario mueve el controlador de movimiento más allá del borde del campo de vista del casco, el casco pronto no podrá realizar un seguimiento visual de la posición del controlador.</span><span class="sxs-lookup"><span data-stu-id="de3f5-242">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="de3f5-243">La aplicación sabe cuándo el controlador ha alcanzado este límite de FOV al ver que **SourceLossRisk** alcanza la versión 1.0.</span><span class="sxs-lookup"><span data-stu-id="de3f5-243">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="de3f5-244">En ese momento, la aplicación puede optar por pausar los gestos de controlador que requieren un flujo estable de poses de alta calidad.</span><span class="sxs-lookup"><span data-stu-id="de3f5-244">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="de3f5-245">**Precisión aproximada:** Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se colocarán en posiciones de precisión aproximada.</span><span class="sxs-lookup"><span data-stu-id="de3f5-245">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="de3f5-246">En este punto, el sistema bloqueará el controlador con el cuerpo del usuario, haciendo un seguimiento de la posición del usuario a medida que se mueve, mientras sigue exponiendo la verdadera orientación del controlador mediante sus sensores de orientación internos.</span><span class="sxs-lookup"><span data-stu-id="de3f5-246">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="de3f5-247">Muchas aplicaciones que usan controladores para apuntar y activar elementos de la interfaz de usuario pueden funcionar con normalidad mientras tienen una precisión aproximada sin que el usuario se de cuenta.</span><span class="sxs-lookup"><span data-stu-id="de3f5-247">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="de3f5-248">Las aplicaciones con requisitos de entrada  más elevados pueden optar por ver esta caída de Alta precisión a Precisión aproximada inspeccionando la propiedad **PositionAccuracy,** por ejemplo, para proporcionar al usuario un cuadro de acceso más práctico en los destinos fuera de la pantalla durante este tiempo. </span><span class="sxs-lookup"><span data-stu-id="de3f5-248">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="de3f5-249">**Sin posición:** Aunque el controlador puede funcionar con una precisión aproximada durante mucho tiempo, a veces el sistema sabe que incluso una posición bloqueada por el cuerpo no es significativa en este momento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-249">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="de3f5-250">Por ejemplo, es posible que un controlador que se ha activado nunca se haya observado visualmente o que un usuario pueda desactivar un controlador que otra persona haya seleccionado.</span><span class="sxs-lookup"><span data-stu-id="de3f5-250">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="de3f5-251">En ese momento, el sistema no proporcionará ninguna posición a la aplicación y *TryGetPosition* devolverá false.</span><span class="sxs-lookup"><span data-stu-id="de3f5-251">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="de3f5-252">API comunes de Unity (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="de3f5-252">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="de3f5-253">**Espacio de nombres:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="de3f5-253">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="de3f5-254">**Tipos:** *Entrada,* *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="de3f5-254">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="de3f5-255">Unity usa actualmente sus API *input.GetButton/Input.GetAxis* generales para exponer la entrada del SDK de [Oculus,](https://docs.unity3d.com/Manual/OculusControllers.html)el SDK de [OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) y Windows Mixed Reality, incluidos los controladores de movimiento y manos.</span><span class="sxs-lookup"><span data-stu-id="de3f5-255">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="de3f5-256">Si la aplicación usa estas API para la entrada, puede admitir fácilmente controladores de movimiento en varios SDK XR, incluidos Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="de3f5-256">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="de3f5-257">Obtención del estado presionado de un botón lógico</span><span class="sxs-lookup"><span data-stu-id="de3f5-257">Getting a logical button's pressed state</span></span>

<span data-ttu-id="de3f5-258">Para usar las API de entrada generales de Unity, normalmente empezaremos por conectar botones y ejes a nombres lógicos en el Administrador de entrada de [Unity,](https://docs.unity3d.com/Manual/ConventionalGameInput.html)enlazando un botón o los iD de eje a cada nombre.</span><span class="sxs-lookup"><span data-stu-id="de3f5-258">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="de3f5-259">A continuación, puede escribir código que haga referencia a ese nombre de botón o eje lógico.</span><span class="sxs-lookup"><span data-stu-id="de3f5-259">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="de3f5-260">Por ejemplo, para asignar el botón de desencadenador del controlador de movimiento izquierdo a la acción Enviar, vaya **a Edit > Project Settings > Input** within Unity (Editar configuración del proyecto > Entrada dentro de Unity) y expanda las propiedades de la sección Submit (Enviar) en Axes (Ejes).</span><span class="sxs-lookup"><span data-stu-id="de3f5-260">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="de3f5-261">Cambie la **propiedad Botón positivo o** Botón alt **positivo** para leer el **botón 14,** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="de3f5-261">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="de3f5-262">![InputManager de Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="de3f5-262">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="de3f5-263&quot;>*Unity InputManager*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;de3f5-263&quot;>*Unity InputManager*</span></span>

<span data-ttu-id=&quot;de3f5-264&quot;>A continuación, el script puede comprobar la acción Submit *mediante Input.GetButton*:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;de3f5-264&quot;>Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
<span data-ttu-id="de3f5-265">Puede agregar más botones lógicos cambiando la **propiedad Tamaño** en **Ejes**.</span><span class="sxs-lookup"><span data-stu-id="de3f5-265">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="de3f5-266">Obtener el estado presionado de un botón físico directamente</span><span class="sxs-lookup"><span data-stu-id="de3f5-266">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="de3f5-267">También puede acceder a los botones manualmente por su nombre completo, mediante *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="de3f5-267">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="de3f5-268">Obtención de la posición de una mano o un controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="de3f5-268">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="de3f5-269">Puede acceder a la posición y rotación del controlador mediante *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="de3f5-269">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="de3f5-270">El código anterior representa la posición de control del controlador (donde el usuario contiene el controlador), lo que resulta útil para representar un revólver o un revólver en la mano del usuario o un modelo del propio controlador.</span><span class="sxs-lookup"><span data-stu-id="de3f5-270">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="de3f5-271">La relación entre esta posición de control y la posición del puntero (donde apunta la punta del controlador) puede diferir entre los controladores.</span><span class="sxs-lookup"><span data-stu-id="de3f5-271">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="de3f5-272">En este momento, el acceso a la posición de puntero del controlador solo es posible a través de la API de entrada específica de MR, que se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="de3f5-272">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="de3f5-273">API específicas de Windows (XR. Wsa. Entrada)</span><span class="sxs-lookup"><span data-stu-id="de3f5-273">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="de3f5-274">Si el proyecto usa cualquiera de las XR. Las API de WSA se están eliminando gradualmente en favor del SDK de XR en futuras versiones de Unity.</span><span class="sxs-lookup"><span data-stu-id="de3f5-274">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="de3f5-275">Para los proyectos nuevos, se recomienda usar el SDK de XR desde el principio.</span><span class="sxs-lookup"><span data-stu-id="de3f5-275">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="de3f5-276">Puede encontrar más información sobre el sistema [de entrada XR y las API aquí.](https://docs.unity3d.com/Manual/xr_input.html)</span><span class="sxs-lookup"><span data-stu-id="de3f5-276">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="de3f5-277">**Espacio de nombres:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="de3f5-277">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="de3f5-278">**Tipos:** *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="de3f5-278">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="de3f5-279">Para obtener información más detallada sobre una entrada Windows Mixed Reality manual (para HoloLens) y controladores de movimiento, puede usar las API de entrada espacial específicas de Windows en el espacio de nombres *UnityEngine.XR.WSA.Input.*</span><span class="sxs-lookup"><span data-stu-id="de3f5-279">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="de3f5-280">Esto le permite acceder a información adicional, como la precisión de la posición o el tipo de origen, lo que le permite diferenciar las manos y los controladores.</span><span class="sxs-lookup"><span data-stu-id="de3f5-280">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="de3f5-281">Sondeo para el estado de las manos y los controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="de3f5-281">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="de3f5-282">Puede sondear el estado de este fotograma para cada origen de interacción (controlador de mano o movimiento) mediante el *método GetCurrentReading.*</span><span class="sxs-lookup"><span data-stu-id="de3f5-282">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="de3f5-283">Cada *InteractionSourceState que* se obtiene representa un origen de interacción en el momento actual en el tiempo.</span><span class="sxs-lookup"><span data-stu-id="de3f5-283">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="de3f5-284">*InteractionSourceState expone* información como:</span><span class="sxs-lookup"><span data-stu-id="de3f5-284">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="de3f5-285">Qué [tipos de presiones](../../design/motion-controllers.md) se están produciendo (Seleccionar/Menú/Comprender/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="de3f5-285">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="de3f5-286">Otros datos específicos de los controladores de movimiento, como las coordenadas XY del panel táctil o el control de posición y el estado tocado</span><span class="sxs-lookup"><span data-stu-id="de3f5-286">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="de3f5-287">InteractionSourceKind para saber si el origen es una mano o un controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="de3f5-287">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="de3f5-288">Sondeo de las representaciones predichos hacia delante</span><span class="sxs-lookup"><span data-stu-id="de3f5-288">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="de3f5-289">Al sondear los datos de origen de interacción de manos y controladores, las poses que obtiene son poses predichos hacia delante por el momento en que los fotones de este fotograma llegarán a los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="de3f5-289">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="de3f5-290">Las poses predichos hacia delante se usan mejor para **representar** el controlador o un objeto mantenido en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="de3f5-290">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="de3f5-291">Si tiene como destino una determinada presión o una versión con el controlador, será más preciso si usa las API de eventos históricos que se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="de3f5-291">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="de3f5-292">También puede obtener la posición de la cabeza predicho hacia delante para este fotograma actual.</span><span class="sxs-lookup"><span data-stu-id="de3f5-292">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="de3f5-293">Al igual que con la  posición de origen, esto resulta útil para representar un cursor, aunque el destino de una determinada presión o versión será más preciso si usa las API de eventos históricos que se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="de3f5-293">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="de3f5-294">Control de eventos de origen de interacción</span><span class="sxs-lookup"><span data-stu-id="de3f5-294">Handling interaction source events</span></span>

<span data-ttu-id="de3f5-295">Para controlar los eventos de entrada a medida que se suceden con sus datos de posición históricos precisos, puede controlar los eventos de origen de interacción en lugar de sondear.</span><span class="sxs-lookup"><span data-stu-id="de3f5-295">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="de3f5-296">Para controlar los eventos de origen de interacción:</span><span class="sxs-lookup"><span data-stu-id="de3f5-296">To handle interaction source events:</span></span>
* <span data-ttu-id="de3f5-297">Regístrese para un *evento de entrada de InteractionManager.*</span><span class="sxs-lookup"><span data-stu-id="de3f5-297">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="de3f5-298">Para cada tipo de evento de interacción que le interese, debe suscribirse a él.</span><span class="sxs-lookup"><span data-stu-id="de3f5-298">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="de3f5-299">Controle el evento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-299">Handle the event.</span></span> <span data-ttu-id="de3f5-300">Una vez que se haya suscrito a un evento de interacción, recibirá la devolución de llamada cuando corresponda.</span><span class="sxs-lookup"><span data-stu-id="de3f5-300">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="de3f5-301">En el *ejemplo SourcePressed,* será después de que se detecte el origen y antes de que se libera o se pierde.</span><span class="sxs-lookup"><span data-stu-id="de3f5-301">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="de3f5-302">Cómo detener el control de un evento</span><span class="sxs-lookup"><span data-stu-id="de3f5-302">How to stop handling an event</span></span>

<span data-ttu-id="de3f5-303">Debe dejar de controlar un evento cuando ya no esté interesado en el evento o esté destruyendo el objeto que se ha suscrito al evento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-303">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="de3f5-304">Para dejar de controlar el evento, cancele la suscripción al evento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-304">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="de3f5-305">Lista de eventos de origen de interacción</span><span class="sxs-lookup"><span data-stu-id="de3f5-305">List of interaction source events</span></span>

<span data-ttu-id="de3f5-306">Los eventos de origen de interacción disponibles son:</span><span class="sxs-lookup"><span data-stu-id="de3f5-306">The available interaction source events are:</span></span>
* <span data-ttu-id="de3f5-307">*InteractionSourceDetected* (el origen se activa)</span><span class="sxs-lookup"><span data-stu-id="de3f5-307">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="de3f5-308">*InteractionSourceLost* (queda inactivo)</span><span class="sxs-lookup"><span data-stu-id="de3f5-308">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="de3f5-309">*InteractionSourcePressed* (pulsar, presionar el botón o "Seleccionar" se ha dicho)</span><span class="sxs-lookup"><span data-stu-id="de3f5-309">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="de3f5-310">*InteractionSourceReleased* (final de una pulsación, un botón publicado o el final de la expresión "Select")</span><span class="sxs-lookup"><span data-stu-id="de3f5-310">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="de3f5-311">*InteractionSourceUpdated* (mueve o cambia algún estado)</span><span class="sxs-lookup"><span data-stu-id="de3f5-311">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="de3f5-312">Los eventos de destino históricos suponen que coinciden con mayor precisión con una publicación o una pulsación</span><span class="sxs-lookup"><span data-stu-id="de3f5-312">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="de3f5-313">Las API de sondeo descritas anteriormente dan a la aplicación poses predichos hacia delante.</span><span class="sxs-lookup"><span data-stu-id="de3f5-313">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="de3f5-314">Aunque las poses predichos son mejores para representar el controlador o un objeto de mano virtual, las poses futuras no son óptimas para el destino, por dos razones clave:</span><span class="sxs-lookup"><span data-stu-id="de3f5-314">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="de3f5-315">Cuando el usuario presiona un botón en un controlador, puede haber unos 20 ms de latencia inalámbrica a través de Bluetooth antes de que el sistema reciba la presión.</span><span class="sxs-lookup"><span data-stu-id="de3f5-315">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="de3f5-316">A continuación, si usa una posición predicho hacia delante, se aplicarían otros 10-20 ms de predicción hacia delante para dirigirse al momento en que los fotones del fotograma actual lleguen a los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="de3f5-316">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="de3f5-317">Esto significa que el sondeo proporciona una posición de origen o de cabeza que está entre 30 y 40 ms hacia delante desde donde la cabeza y las manos del usuario estaban realmente de vuelta cuando se produjo la presión o la liberación.</span><span class="sxs-lookup"><span data-stu-id="de3f5-317">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="de3f5-318">En el caso de la entrada de mano de HoloLens, aunque no hay ningún retraso de transmisión inalámbrica, hay un retraso de procesamiento similar para detectar la presión.</span><span class="sxs-lookup"><span data-stu-id="de3f5-318">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="de3f5-319">Para dirigirse con precisión en función de la intención original del usuario para una pulsación de mano o controlador, debe usar la posición histórica de origen o la posición de la cabeza de ese evento de entrada *InteractionSourcePressed* o *InteractionSourceReleased.*</span><span class="sxs-lookup"><span data-stu-id="de3f5-319">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="de3f5-320">Puede seleccionar como destino una presión o una versión con datos de posición históricos de la cabeza del usuario o su controlador:</span><span class="sxs-lookup"><span data-stu-id="de3f5-320">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="de3f5-321">La posición de la cabeza en el momento en que se  produjo un gesto o una pulsación del controlador, que se puede usar para establecer como destino para determinar a qué estaba mirando el [usuario:](../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="de3f5-321">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="de3f5-322">La posición de origen en el momento en que se  produjo una presión del controlador de movimiento, que se puede usar para establecer como destino para determinar a qué apuntaba el controlador el usuario.</span><span class="sxs-lookup"><span data-stu-id="de3f5-322">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="de3f5-323">Este será el estado del controlador que experimentó la presión.</span><span class="sxs-lookup"><span data-stu-id="de3f5-323">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="de3f5-324">Si va a representar el propio controlador, puede solicitar la posición del puntero en lugar de la posición de control para que el rayo de destino se base en lo que el usuario considerará la sugerencia natural de ese controlador representado:</span><span class="sxs-lookup"><span data-stu-id="de3f5-324">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="de3f5-325">Ejemplo de controladores de eventos</span><span class="sxs-lookup"><span data-stu-id="de3f5-325">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="de3f5-326">Controladores de movimiento en MRTK</span><span class="sxs-lookup"><span data-stu-id="de3f5-326">Motion Controllers in MRTK</span></span>

<span data-ttu-id="de3f5-327">Puede acceder al [gesto y al controlador de movimiento](/windows/mixed-reality/mrtk-unity/features/input/controllers) desde el Administrador de entrada.</span><span class="sxs-lookup"><span data-stu-id="de3f5-327">You can access [gesture and motion controller](/windows/mixed-reality/mrtk-unity/features/input/controllers) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="de3f5-328">Seguimiento de tutoriales</span><span class="sxs-lookup"><span data-stu-id="de3f5-328">Follow along with tutorials</span></span>

<span data-ttu-id="de3f5-329">Los tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en Mixed Reality Academy:</span><span class="sxs-lookup"><span data-stu-id="de3f5-329">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="de3f5-330">MR Input 211: gesto</span><span class="sxs-lookup"><span data-stu-id="de3f5-330">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="de3f5-331">MR Input 213: controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="de3f5-331">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="de3f5-332">[![Entrada de MR 213: controlador de movimiento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="de3f5-332">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="de3f5-333">*Entrada de MR 213: controlador de movimiento*</span><span class="sxs-lookup"><span data-stu-id="de3f5-333">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="de3f5-334">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="de3f5-334">Next Development Checkpoint</span></span>

<span data-ttu-id="de3f5-335">Si sigue el recorrido de desarrollo de Unity que hemos diseñado, está en medio de la exploración de los bloques de creación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="de3f5-335">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="de3f5-336">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="de3f5-336">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="de3f5-337">Seguimiento de manos y ocular</span><span class="sxs-lookup"><span data-stu-id="de3f5-337">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="de3f5-338">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="de3f5-338">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="de3f5-339">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="de3f5-339">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="de3f5-340">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="de3f5-340">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="de3f5-341">Consulta también</span><span class="sxs-lookup"><span data-stu-id="de3f5-341">See also</span></span>

* [<span data-ttu-id="de3f5-342">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="de3f5-342">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="de3f5-343">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="de3f5-343">Motion controllers</span></span>](../../design/motion-controllers.md)