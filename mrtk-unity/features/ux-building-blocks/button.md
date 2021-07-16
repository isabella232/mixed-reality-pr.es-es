---
title: Botones
description: Información general sobre botones en MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, botones de MRTK
ms.openlocfilehash: 16baeede2c63437e933eb1367f01af7f372cd62f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281852"
---
# <a name="buttons"></a><span data-ttu-id="65f34-104">Botones</span><span class="sxs-lookup"><span data-stu-id="65f34-104">Buttons</span></span>

![Button Main](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="65f34-106">Un botón ofrece al usuario una forma de desencadenar una acción inmediata.</span><span class="sxs-lookup"><span data-stu-id="65f34-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="65f34-107">Es uno de los componentes más fundamentales de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="65f34-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="65f34-108">MRTK proporciona varios tipos de elementos prefabs de botón.</span><span class="sxs-lookup"><span data-stu-id="65f34-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="65f34-109">Prefabs de botón en MRTK</span><span class="sxs-lookup"><span data-stu-id="65f34-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="65f34-110">Ejemplos de los requisitos previos del botón en la ``MRTK/SDK/Features/UX/Interactable/Prefabs`` carpeta</span><span class="sxs-lookup"><span data-stu-id="65f34-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="65f34-111">Botones basados en gráficos o imágenes de la interfaz de usuario de Unity</span><span class="sxs-lookup"><span data-stu-id="65f34-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="65f34-112">Botones basados en colisionador</span><span class="sxs-lookup"><span data-stu-id="65f34-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="65f34-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="65f34-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="65f34-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="65f34-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="65f34-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="65f34-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="65f34-119">HoloLens 2 botón de estilo shell con placa trasera que admite varios comentarios visuales, como luz de borde, luz de proximidad y placa frontal comprimida</span><span class="sxs-lookup"><span data-stu-id="65f34-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-120">HoloLens 2 botón de estilo shell sin placa trasera</span><span class="sxs-lookup"><span data-stu-id="65f34-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-121">HoloLens 2 botón de estilo shell con forma circular</span><span class="sxs-lookup"><span data-stu-id="65f34-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="65f34-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="65f34-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="65f34-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="65f34-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="65f34-125">Botón de HoloLens 2 estilo shell de Wide HoloLens 2 32 x 96 mm</span><span class="sxs-lookup"><span data-stu-id="65f34-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-126">Barra de HoloLens 2 horizontal con placa trasera compartida</span><span class="sxs-lookup"><span data-stu-id="65f34-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-127">Barra de HoloLens 2 vertical con placa trasera compartida</span><span class="sxs-lookup"><span data-stu-id="65f34-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="65f34-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="65f34-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="65f34-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="65f34-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="65f34-131">casilla de HoloLens 2 estilo de shell de 32 x 32 mm</span><span class="sxs-lookup"><span data-stu-id="65f34-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-132">HoloLens 2 conmutador de estilo shell de 32 x 32 mm</span><span class="sxs-lookup"><span data-stu-id="65f34-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-133">radio de estilo shell de HoloLens 2 32 x 32 mm</span><span class="sxs-lookup"><span data-stu-id="65f34-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="65f34-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="65f34-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="65f34-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="65f34-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="65f34-137">HoloLens 2 de la casilla de estilo shell de 32 x 96 mm</span><span class="sxs-lookup"><span data-stu-id="65f34-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-138">HoloLens 2 de estilo shell de 32 x 96 mm</span><span class="sxs-lookup"><span data-stu-id="65f34-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-139">radio de estilo shell de HoloLens 2 32 x 96 mm</span><span class="sxs-lookup"><span data-stu-id="65f34-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="65f34-140">![Radial ](../images/button/MRTK_Button_Radial.png) **radial**</span><span class="sxs-lookup"><span data-stu-id="65f34-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-141">![Casilla de ](../images/button/MRTK_Button_Checkbox.png) **verificación**</span><span class="sxs-lookup"><span data-stu-id="65f34-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="65f34-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="65f34-143">Botón radial</span><span class="sxs-lookup"><span data-stu-id="65f34-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-144">Casilla de verificación</span><span class="sxs-lookup"><span data-stu-id="65f34-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-145">Modificador para alternar</span><span class="sxs-lookup"><span data-stu-id="65f34-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="65f34-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="65f34-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="65f34-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-148">![Botón Base del ](../images/button/MRTK_Button_Base.png) **botón**</span><span class="sxs-lookup"><span data-stu-id="65f34-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="65f34-149">HoloLens botón de estilo de shell de 1.ª generación</span><span class="sxs-lookup"><span data-stu-id="65f34-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-150">Botón de inserción de forma redondeada</span><span class="sxs-lookup"><span data-stu-id="65f34-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="65f34-151">Botón Básica</span><span class="sxs-lookup"><span data-stu-id="65f34-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="65f34-152">`Button`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) se basa en el concepto [Interactable](interactable.md) para proporcionar controles de interfaz de usuario sencillos para botones u otros tipos de superficies interactivas.</span><span class="sxs-lookup"><span data-stu-id="65f34-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="65f34-153">El botón de línea base admite todos los métodos de entrada disponibles, incluida la entrada de mano articulada para las interacciones cercanas, así como la mirada y la pulsación en el aire para las interacciones lejanas.</span><span class="sxs-lookup"><span data-stu-id="65f34-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="65f34-154">También puede usar el comando de voz para desencadenar el botón.</span><span class="sxs-lookup"><span data-stu-id="65f34-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="65f34-155">`PressableButtonHoloLens2`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) es el botón de estilo de shell de HoloLens 2 que admite el movimiento preciso del botón para la entrada de seguimiento directo de la mano.</span><span class="sxs-lookup"><span data-stu-id="65f34-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="65f34-156">Combina el `Interactable` script con el `PressableButton` script.</span><span class="sxs-lookup"><span data-stu-id="65f34-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="65f34-157">Por HoloLens 2, se recomienda usar botones con una placa trasera opaca.</span><span class="sxs-lookup"><span data-stu-id="65f34-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="65f34-158">Los botones transparentes no se recomiendan debido a estos problemas de facilidad de uso y estabilidad:</span><span class="sxs-lookup"><span data-stu-id="65f34-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="65f34-159">El icono y el texto son difíciles de leer con el entorno físico</span><span class="sxs-lookup"><span data-stu-id="65f34-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="65f34-160">Es difícil entender cuándo se desencadena el evento</span><span class="sxs-lookup"><span data-stu-id="65f34-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="65f34-161">Hologramas que se muestran a través de un plano transparente puede ser inestable con la estabilización LSR de profundidad de HoloLens 2 de datos</span><span class="sxs-lookup"><span data-stu-id="65f34-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Botón adosado](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="65f34-163">Uso de botones presionables</span><span class="sxs-lookup"><span data-stu-id="65f34-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="65f34-164">Botones basados en la interfaz de usuario de Unity</span><span class="sxs-lookup"><span data-stu-id="65f34-164">Unity UI based buttons</span></span>

<span data-ttu-id="65f34-165">Cree un lienzo en la escena (GameObject -> UI -> Canvas).</span><span class="sxs-lookup"><span data-stu-id="65f34-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="65f34-166">En el panel Inspector del lienzo:</span><span class="sxs-lookup"><span data-stu-id="65f34-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="65f34-167">Haga clic en "Convertir al lienzo de MRTK".</span><span class="sxs-lookup"><span data-stu-id="65f34-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="65f34-168">Haga clic en "Add NearInteractionTouchableUnityUI" (Agregar NearInteractionTouchableUnityUI).</span><span class="sxs-lookup"><span data-stu-id="65f34-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="65f34-169">Establezca la escala X, Y y Z del componente Transformación de rect en 0,001.</span><span class="sxs-lookup"><span data-stu-id="65f34-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="65f34-170">A continuación, arrastre `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/. PressableButtonUnityUICircular.prefab) o `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) en el lienzo.</span><span class="sxs-lookup"><span data-stu-id="65f34-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="65f34-171">Botones basados en colisionador</span><span class="sxs-lookup"><span data-stu-id="65f34-171">Collider based buttons</span></span>

<span data-ttu-id="65f34-172">Simplemente arrastre `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) o `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) a la escena.</span><span class="sxs-lookup"><span data-stu-id="65f34-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="65f34-173">Estos elementos prefabs de botón ya están configurados para tener comentarios visuales de audio para los distintos tipos de entradas, incluida la entrada y la mirada con la mano articuladas.</span><span class="sxs-lookup"><span data-stu-id="65f34-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="65f34-174">Los eventos expuestos en el propio elemento prefab, así como el [componente Interactable,](interactable.md) se pueden usar para desencadenar acciones adicionales.</span><span class="sxs-lookup"><span data-stu-id="65f34-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="65f34-175">Los botones presionables de la [escena HandInteractionExample](../example-scenes/hand-interaction-examples.md) usan el evento *OnClick* de Interactable para desencadenar un cambio en el color de un cubo.</span><span class="sxs-lookup"><span data-stu-id="65f34-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="65f34-176">Este evento se desencadena para diferentes tipos de métodos de entrada, como la mirada, el toque de aire, el rayo de la mano, así como las pulsaciones de botón físicos a través del script de botón que se puede presionar.</span><span class="sxs-lookup"><span data-stu-id="65f34-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="65f34-177">Puede configurar cuando el botón presionable desan el evento *OnClick* a través `PhysicalPressEventRouter` de en el botón.</span><span class="sxs-lookup"><span data-stu-id="65f34-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="65f34-178">Por ejemplo, puede establecer *OnClick* para que se desenlome cuando se presione el botón por primera vez, en lugar de presionarlo y liberarlo, estableciendo *Interactable On Click (Interactable* al hacer clic) en Event On Press (Evento al *presionar).*</span><span class="sxs-lookup"><span data-stu-id="65f34-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="65f34-179">Para aprovechar la información específica del estado de entrada de la mano articulada, puede usar eventos de botones presionables: *Touch Begin*, *Touch End*, Button *Pressed*, *Button Released*.</span><span class="sxs-lookup"><span data-stu-id="65f34-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="65f34-180">Sin embargo, estos eventos no se mostrarán en respuesta a las entradas de pulsación del aire, de rayos de mano o de los ojos.</span><span class="sxs-lookup"><span data-stu-id="65f34-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="65f34-181">**Para admitir interacciones cercanas y lejanas, se recomienda usar el evento *OnClick de Interactable.***</span><span class="sxs-lookup"><span data-stu-id="65f34-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="65f34-182">Estados de interacción</span><span class="sxs-lookup"><span data-stu-id="65f34-182">Interaction states</span></span>

<span data-ttu-id="65f34-183">En el estado de inactividad, la placa frontal del botón no está visible.</span><span class="sxs-lookup"><span data-stu-id="65f34-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="65f34-184">A medida que un dedo se acerca o un cursor de la entrada de mirada apunta a la superficie, el borde brillante de la placa frontal se vuelve visible.</span><span class="sxs-lookup"><span data-stu-id="65f34-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="65f34-185">Hay un resaltado adicional de la posición del dedo en la superficie de la placa frontal.</span><span class="sxs-lookup"><span data-stu-id="65f34-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="65f34-186">Cuando se inserta con un dedo, la placa frontal se mueve con el dedo.</span><span class="sxs-lookup"><span data-stu-id="65f34-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="65f34-187">Cuando el dedo toca la superficie de la placa frontal, muestra un efecto de pulso sutil para proporcionar comentarios visuales del punto táctil.</span><span class="sxs-lookup"><span data-stu-id="65f34-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="65f34-188">En HoloLens 2 de estilo shell, hay muchas indicaciones visuales y asequiciones para aumentar la confianza del usuario en la interacción.</span><span class="sxs-lookup"><span data-stu-id="65f34-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Luz de proximidad](../images/button/ux_button_affordance_proximitylight.jpg) | ![Resaltado del foco](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compresión de la caja de seguridad](../images/button/ux_button_affordance_compression.jpg) | ![Pulse on trigger (Pulse on trigger)](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="65f34-193">Luz de proximidad</span><span class="sxs-lookup"><span data-stu-id="65f34-193">Proximity light</span></span> | <span data-ttu-id="65f34-194">Resaltado del foco</span><span class="sxs-lookup"><span data-stu-id="65f34-194">Focus highlight</span></span> | <span data-ttu-id="65f34-195">Compresión de la caja de seguridad</span><span class="sxs-lookup"><span data-stu-id="65f34-195">Compressing cage</span></span> | <span data-ttu-id="65f34-196">Pulse on trigger (Pulse on trigger)</span><span class="sxs-lookup"><span data-stu-id="65f34-196">Pulse on trigger</span></span> |

<span data-ttu-id="65f34-197">El efecto de pulso sutil se desencadena mediante el botón que se puede presionar, que busca *proximityLight(s)* que se encuentran en el puntero que interactúa actualmente.</span><span class="sxs-lookup"><span data-stu-id="65f34-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="65f34-198">Si se encuentra alguna luz de proximidad, se llama al método , que anima automáticamente los parámetros del `ProximityLight.Pulse` sombreador para mostrar un pulso.</span><span class="sxs-lookup"><span data-stu-id="65f34-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="65f34-199">Propiedades del inspector</span><span class="sxs-lookup"><span data-stu-id="65f34-199">Inspector properties</span></span>

![Estructura de botones](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="65f34-201">**Box Collider** 
 `Box Collider` para la placa frontal del botón.</span><span class="sxs-lookup"><span data-stu-id="65f34-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="65f34-202">**Botón que se puede presionar** Lógica para el movimiento del botón con la interacción de la pulsación con la mano.</span><span class="sxs-lookup"><span data-stu-id="65f34-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="65f34-203">**Enrutador de eventos de presión física** Este script envía eventos desde la interacción de la pulsación a mano [a Interactable.](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="65f34-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="65f34-204">**Interactuable** 
 [Interactable controla](interactable.md) varios tipos de estados y eventos de interacción.</span><span class="sxs-lookup"><span data-stu-id="65f34-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="65f34-205">HoloLens la mirada, el gesto y la entrada de voz y la entrada del controlador de movimiento del casco envolvente se controlan directamente mediante este script.</span><span class="sxs-lookup"><span data-stu-id="65f34-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="65f34-206">**Origen de audio** Origen de audio de Unity para los clips de comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="65f34-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="65f34-207">*NearInteractionTouchable.cs* Obligatorio para que cualquier objeto sea táctil con entrada de mano articulada.</span><span class="sxs-lookup"><span data-stu-id="65f34-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="65f34-208">Diseño prefab</span><span class="sxs-lookup"><span data-stu-id="65f34-208">Prefab layout</span></span>

<span data-ttu-id="65f34-209">El *objeto ButtonContent* contiene la placa frontal, la etiqueta de texto y el icono.</span><span class="sxs-lookup"><span data-stu-id="65f34-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="65f34-210">FrontPlate *responde a* la proximidad del dedo del índice mediante el *sombreador Button_Box* índice.</span><span class="sxs-lookup"><span data-stu-id="65f34-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="65f34-211">Muestra bordes brillantes, luz de proximidad y un efecto de pulso en el toque.</span><span class="sxs-lookup"><span data-stu-id="65f34-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="65f34-212">La etiqueta de texto se realiza con TextMesh Pro.</span><span class="sxs-lookup"><span data-stu-id="65f34-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="65f34-213">*La visibilidad de SeeItSayItLabel* se controla mediante el tema de [Interactable.](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="65f34-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Diseño de botón](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="65f34-215">Cómo cambiar el icono y el texto</span><span class="sxs-lookup"><span data-stu-id="65f34-215">How to change the icon and text</span></span>

<span data-ttu-id="65f34-216">Los botones de MRTK usan un componente para ayudarle a cambiar el icono, el `ButtonConfigHelper` texto y la etiqueta del botón.</span><span class="sxs-lookup"><span data-stu-id="65f34-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="65f34-217">(Tenga en cuenta que algunos campos pueden estar ausentes si los elementos no están presentes en el botón seleccionado).</span><span class="sxs-lookup"><span data-stu-id="65f34-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Asistente de configuración de botón](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="65f34-219">Crear y modificar conjuntos de iconos</span><span class="sxs-lookup"><span data-stu-id="65f34-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="65f34-220">Un **conjunto de iconos** es un conjunto compartido de recursos de icono usados por el `ButtonConfigHelper` componente.</span><span class="sxs-lookup"><span data-stu-id="65f34-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="65f34-221">Se admiten *estilos de* tres iconos.</span><span class="sxs-lookup"><span data-stu-id="65f34-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="65f34-222">**Los** iconos de cuatro se representan en un cuadrándido mediante `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="65f34-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="65f34-223">Este es el estilo de icono predeterminado.</span><span class="sxs-lookup"><span data-stu-id="65f34-223">This is the default icon style.</span></span>
* <span data-ttu-id="65f34-224">**Los** iconos de sprite se representan mediante `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="65f34-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="65f34-225">Esto resulta útil si prefiere importar los iconos como una hoja de sprites, o si quiere que los recursos de icono se compartan con los componentes de la interfaz de usuario de Unity.</span><span class="sxs-lookup"><span data-stu-id="65f34-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="65f34-226">Para usar este estilo, deberá instalar el paquete Sprite Editor **(Windows -> Administrador de paquetes -> sprite 2D)**</span><span class="sxs-lookup"><span data-stu-id="65f34-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="65f34-227">**Los** iconos char se representan mediante un `TextMeshPro` componente.</span><span class="sxs-lookup"><span data-stu-id="65f34-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="65f34-228">Esto resulta útil si prefiere usar una fuente de icono.</span><span class="sxs-lookup"><span data-stu-id="65f34-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="65f34-229">Para usar la HoloLens de icono de fuente, deberá crear un recurso `TextMeshPro` de fuente.</span><span class="sxs-lookup"><span data-stu-id="65f34-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="65f34-230">Para cambiar el estilo que usa el botón, expanda la lista desplegable *Iconos* de ButtonConfigHelper y seleccione en la lista desplegable *Estilo de* icono.</span><span class="sxs-lookup"><span data-stu-id="65f34-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="65f34-231">Puede crear un nuevo conjunto de iconos de botón con el menú de recursos: **Crear > Mixed Reality Toolkit > conjunto de iconos.**</span><span class="sxs-lookup"><span data-stu-id="65f34-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="65f34-232">Para agregar iconos de cuatro y sprites, simplemente arrástrelos a sus respectivas matrices.</span><span class="sxs-lookup"><span data-stu-id="65f34-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="65f34-233">Para agregar iconos char, primero debe crear y asignar un recurso de fuente.</span><span class="sxs-lookup"><span data-stu-id="65f34-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="65f34-234">En MRTK 2.4 y posteriores, se recomienda mover texturas de icono personalizadas a iconSet.</span><span class="sxs-lookup"><span data-stu-id="65f34-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="65f34-235">Para actualizar los recursos de todos los botones de un proyecto al nuevo formato recomendado, use ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="65f34-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="65f34-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="65f34-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="65f34-237">Importar el paquete Microsoft.MixedRealityToolkit.Unity.Tools necesario para actualizar los botones.</span><span class="sxs-lookup"><span data-stu-id="65f34-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Cuadro de diálogo actualizar ventana](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="65f34-239">Si no se encuentra un icono en el conjunto de iconos predeterminado durante la migración, se creará un conjunto de iconos personalizado en MixedRealityToolkit.Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="65f34-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="65f34-240">Un cuadro de diálogo indicará que esto ha tenido lugar.</span><span class="sxs-lookup"><span data-stu-id="65f34-240">A dialog will indicate that this has taken place.</span></span>

![Notificación de icono personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="65f34-242">Crear un recurso de fuente HoloLens icono de archivo</span><span class="sxs-lookup"><span data-stu-id="65f34-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="65f34-243">En primer lugar, importe la fuente del icono en Unity.</span><span class="sxs-lookup"><span data-stu-id="65f34-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="65f34-244">En Windows máquinas virtuales, puede encontrar la fuente HoloLens predeterminada *en Windows/Fonts/holomdl2.ttf.*</span><span class="sxs-lookup"><span data-stu-id="65f34-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="65f34-245">Copie y pegue este archivo en la carpeta Recursos.</span><span class="sxs-lookup"><span data-stu-id="65f34-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="65f34-246">A continuación, abra TextMeshPro Font Asset Creator a través de **Window > TextMeshPro > Font Asset Creator.**</span><span class="sxs-lookup"><span data-stu-id="65f34-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="65f34-247">Esta es la configuración recomendada para generar un atlas HoloLens fuente.</span><span class="sxs-lookup"><span data-stu-id="65f34-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="65f34-248">Para incluir todos los iconos, pegue el siguiente intervalo Unicode en el *campo Secuencia de* caracteres:</span><span class="sxs-lookup"><span data-stu-id="65f34-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Creación de botones 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="65f34-250">Una vez generado el recurso de fuente, guárdelo en el proyecto y asígnelo al campo Fuente de *icono de char* del conjunto de iconos.</span><span class="sxs-lookup"><span data-stu-id="65f34-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="65f34-251">Ahora *se rellenará la* lista desplegable Iconos disponibles.</span><span class="sxs-lookup"><span data-stu-id="65f34-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="65f34-252">Para que un icono esté disponible para que lo use un botón, haga clic en él.</span><span class="sxs-lookup"><span data-stu-id="65f34-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="65f34-253">Se agregará a la lista desplegable *Iconos* seleccionados y ahora se mostrará en La opción Puede dar al `ButtonConfigHelper.` icono una etiqueta.</span><span class="sxs-lookup"><span data-stu-id="65f34-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="65f34-254">Esto permite establecer el icono en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="65f34-254">This enables setting the icon at runtime.</span></span>

![Creación de botones 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Creación de botones 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="65f34-257">Para usar el conjunto de iconos, seleccione un botón, expanda la lista desplegable Iconos de y `ButtonConfigHelper` asígnelo al campo *Conjunto de* iconos.</span><span class="sxs-lookup"><span data-stu-id="65f34-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Conjunto de iconos de botón](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="65f34-259">Cómo cambiar el tamaño de un botón</span><span class="sxs-lookup"><span data-stu-id="65f34-259">How to change the size of a button</span></span>

<span data-ttu-id="65f34-260">HoloLens 2 el tamaño del botón de estilo shell es de 32 x 32 mm.</span><span class="sxs-lookup"><span data-stu-id="65f34-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="65f34-261">Para personalizar la dimensión, cambie el tamaño de estos objetos en el botón prefab:</span><span class="sxs-lookup"><span data-stu-id="65f34-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="65f34-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="65f34-262">**FrontPlate**</span></span>
2. <span data-ttu-id="65f34-263">**Quad** en BackPlate</span><span class="sxs-lookup"><span data-stu-id="65f34-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="65f34-264">**Box Collider** en la raíz</span><span class="sxs-lookup"><span data-stu-id="65f34-264">**Box Collider** on the root</span></span>

<span data-ttu-id="65f34-265">A continuación, haga clic en el botón Corregir **límites** del script NearInteractionTouchable que se encuentra en la raíz del botón.</span><span class="sxs-lookup"><span data-stu-id="65f34-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="65f34-266">Actualización del tamaño de la personalización de tamaño de botón FrontPlate ![ 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="65f34-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="65f34-267">Actualización del tamaño de la personalización de ![ tamaño de botón cuadránitrido 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="65f34-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="65f34-268">Actualizar el tamaño de la personalización del tamaño del botón ![ colisionador de cuadro 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="65f34-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="65f34-269">Haga clic en la personalización del tamaño del botón "Corregir ![ límites" 4.](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="65f34-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="65f34-270">Comando de voz ('see-it, say-it')</span><span class="sxs-lookup"><span data-stu-id="65f34-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="65f34-271">**Controlador de entrada de voz** El [script Interactable](interactable.md) de Pressable Button ya implementa `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="65f34-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="65f34-272">Aquí se puede establecer una palabra clave de comando de voz.</span><span class="sxs-lookup"><span data-stu-id="65f34-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="65f34-273">**Perfil de entrada de voz** Además, debe registrar la palabra clave de comando de voz en el perfil global *de comandos de voz*.</span><span class="sxs-lookup"><span data-stu-id="65f34-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="65f34-274">**See-it, Say-it label** El botón prefab presionable tiene un marcador de posición TextMesh Pro etiqueta en el *objeto SeeItSayItLabel.*</span><span class="sxs-lookup"><span data-stu-id="65f34-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="65f34-275">Puede usar esta etiqueta para comunicar al usuario la palabra clave del comando de voz para el botón.</span><span class="sxs-lookup"><span data-stu-id="65f34-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="65f34-276">Cómo crear un botón desde cero</span><span class="sxs-lookup"><span data-stu-id="65f34-276">How to make a button from scratch</span></span>

<span data-ttu-id="65f34-277">Puede encontrar los ejemplos de estos botones en la **escena PressableButtonExample.**</span><span class="sxs-lookup"><span data-stu-id="65f34-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="65f34-278">1. Creación de un botón presionable con cubo (solo interacción cercana)</span><span class="sxs-lookup"><span data-stu-id="65f34-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="65f34-279">Crear un cubo de Unity (GameObject > 3D Object > Cube)</span><span class="sxs-lookup"><span data-stu-id="65f34-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="65f34-280">Agregar `PressableButton.cs` script</span><span class="sxs-lookup"><span data-stu-id="65f34-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="65f34-281">Agregar `NearInteractionTouchable.cs` script</span><span class="sxs-lookup"><span data-stu-id="65f34-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="65f34-282">En el `PressableButton` panel Inspector del , asigne el objeto de cubo a los objetos visuales de botón de **movimiento**.</span><span class="sxs-lookup"><span data-stu-id="65f34-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="65f34-283">Al seleccionar el cubo, verá varias capas de color en el objeto.</span><span class="sxs-lookup"><span data-stu-id="65f34-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="65f34-284">Esto visualiza los valores de distancia en **Presione Configuración**.</span><span class="sxs-lookup"><span data-stu-id="65f34-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="65f34-285">Con los identificadores, puede configurar cuándo iniciar la pulsación (mover el objeto) y cuándo desencadenar el evento.</span><span class="sxs-lookup"><span data-stu-id="65f34-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="65f34-286">Al presionar el botón, se moverá y generará los eventos adecuados expuestos en el script, como `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span><span class="sxs-lookup"><span data-stu-id="65f34-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="65f34-287">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="65f34-287">Troubleshooting</span></span>

<span data-ttu-id="65f34-288">Si el botón está ejecutando una doble  pulsación, asegúrese de  que la propiedad Aplicar inserción frontal está activa y de que el plano Iniciar distancia de inserción se coloca delante del plano táctil Interacción **cercana.**</span><span class="sxs-lookup"><span data-stu-id="65f34-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="65f34-289">El **plano táctil Interacción** cercana se indica mediante el plano azul situado delante del origen de la flecha blanca en el gif siguiente:</span><span class="sxs-lookup"><span data-stu-id="65f34-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Componente de script de botón presionable con la propiedad Aplicar inserción front-push resaltada](../images/button/MRTK_Button_Enforce_Push.png)

![Ejemplo animado de mover la distancia de inserción inicial delante del plano táctil de interacción cercana](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="65f34-292">2. Adición de comentarios visuales al botón de cubo básico</span><span class="sxs-lookup"><span data-stu-id="65f34-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="65f34-293">MrTK Standard Shader proporciona varias características que facilita la adición de comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="65f34-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="65f34-294">Cree un material y seleccione el sombreador `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="65f34-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="65f34-295">O bien, puede usar o duplicar uno de los materiales existentes en `/SDK/StandardAssets/Materials/` que usa el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="65f34-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="65f34-296">Active `Hover Light` y en Fluent `Proximity Light` **opciones**.</span><span class="sxs-lookup"><span data-stu-id="65f34-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="65f34-297">Esto habilita los comentarios visuales para las interacciones de mano cercana (luz de proximidad) y puntero lejano (mantener el puntero sobre la luz).</span><span class="sxs-lookup"><span data-stu-id="65f34-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="65f34-298">3. Adición de comentarios de audio al botón básico del cubo</span><span class="sxs-lookup"><span data-stu-id="65f34-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="65f34-299">Dado que el script expone eventos como `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), podemos asignar fácilmente comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="65f34-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="65f34-300">Simplemente agregue unity al objeto de cubo y, a `Audio Source` continuación, asigne clips de audio seleccionando AudioSource.PlayOneShot().</span><span class="sxs-lookup"><span data-stu-id="65f34-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="65f34-301">Puede usar los clips MRTK_Select_Main y MRTK_Select_Secondary audio en la `/SDK/StandardAssets/Audio/` carpeta .</span><span class="sxs-lookup"><span data-stu-id="65f34-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="65f34-302">4. Adición de estados visuales y control de eventos de interacción lejana</span><span class="sxs-lookup"><span data-stu-id="65f34-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="65f34-303">[Interactable](interactable.md) es un script que facilita la creación de un estado visual para los distintos tipos de interacciones de entrada.</span><span class="sxs-lookup"><span data-stu-id="65f34-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="65f34-304">También controla eventos de interacción lejana.</span><span class="sxs-lookup"><span data-stu-id="65f34-304">It also handles far interaction events.</span></span> <span data-ttu-id="65f34-305">Agregue `Interactable.cs` y arrastre y coloque el objeto de cubo en el campo **Destino** en **Perfiles**.</span><span class="sxs-lookup"><span data-stu-id="65f34-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="65f34-306">A continuación, cree un tema con un tipo **ScaleOffsetColorTheme**.</span><span class="sxs-lookup"><span data-stu-id="65f34-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="65f34-307">En este tema, puede especificar el color del objeto para los estados de interacción específicos, como **Foco** **y Presionado.**</span><span class="sxs-lookup"><span data-stu-id="65f34-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="65f34-308">También puede controlar la escala y el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="65f34-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="65f34-309">Compruebe **Easing (Aceleración)** y establezca la duración para que la transición visual sea fluida.</span><span class="sxs-lookup"><span data-stu-id="65f34-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Selección del tema del perfil](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="65f34-311">Verá que el objeto responde a interacciones lejanas (de rayo de mano o de mirada) y cercanas (mano).</span><span class="sxs-lookup"><span data-stu-id="65f34-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="65f34-312">Ejemplos de botones personalizados</span><span class="sxs-lookup"><span data-stu-id="65f34-312">Custom button examples</span></span>

<span data-ttu-id="65f34-313">En la [escena HandInteractionExample,](../example-scenes/hand-interaction-examples.md)vea los ejemplos de botones de redondeo y de teclado que usan `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="65f34-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="65f34-314">Cada clave tiene un `PressableButton` y un `NearInteractionTouchable` script asignados.</span><span class="sxs-lookup"><span data-stu-id="65f34-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="65f34-315">Es importante comprobar que la dirección de *reenvío local* de `NearInteractionTouchable` es correcta.</span><span class="sxs-lookup"><span data-stu-id="65f34-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="65f34-316">Se representa mediante una flecha blanca en el editor.</span><span class="sxs-lookup"><span data-stu-id="65f34-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="65f34-317">Asegúrese de que la flecha apunta lejos de la cara frontal del botón:</span><span class="sxs-lookup"><span data-stu-id="65f34-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="65f34-318">Vea también</span><span class="sxs-lookup"><span data-stu-id="65f34-318">See also</span></span>

* [<span data-ttu-id="65f34-319">Interactuable</span><span class="sxs-lookup"><span data-stu-id="65f34-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="65f34-320">Temas visuales</span><span class="sxs-lookup"><span data-stu-id="65f34-320">Visual Themes</span></span>](visual-themes.md)
