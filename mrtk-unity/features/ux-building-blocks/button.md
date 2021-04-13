---
title: Botones
description: Información general sobre los botones de MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Los botones Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK y MRTK
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003124"
---
# <a name="button"></a><span data-ttu-id="f0099-104">Botón</span><span class="sxs-lookup"><span data-stu-id="f0099-104">Button</span></span>

![Botón principal](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="f0099-106">Un botón ofrece al usuario una forma de desencadenar una acción inmediata.</span><span class="sxs-lookup"><span data-stu-id="f0099-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="f0099-107">Es uno de los componentes fundamentales de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f0099-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="f0099-108">MRTK proporciona varios tipos de Prefabs de botón.</span><span class="sxs-lookup"><span data-stu-id="f0099-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="f0099-109">Botón Prefabs en MRTK</span><span class="sxs-lookup"><span data-stu-id="f0099-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="f0099-110">Ejemplos del botón Prefabs en la ``MRTK/SDK/Features/UX/Interactable/Prefabs`` carpeta</span><span class="sxs-lookup"><span data-stu-id="f0099-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="f0099-111">Botones basados en imagen/gráfico de interfaz de usuario de Unity</span><span class="sxs-lookup"><span data-stu-id="f0099-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="f0099-112">Botones basados en Colisionador</span><span class="sxs-lookup"><span data-stu-id="f0099-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="f0099-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="f0099-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="f0099-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="f0099-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="f0099-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="f0099-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="f0099-119">Botón de estilo de Shell de HoloLens 2 con placa posterior que admite diversos comentarios visuales como la luz de borde, la luz de proximidad y la placa frontal comprimida</span><span class="sxs-lookup"><span data-stu-id="f0099-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-120">Botón de estilo de Shell de HoloLens 2 sin fondo</span><span class="sxs-lookup"><span data-stu-id="f0099-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-121">Botón de estilo de Shell de HoloLens 2 con forma circular</span><span class="sxs-lookup"><span data-stu-id="f0099-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="f0099-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="f0099-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="f0099-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="f0099-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="f0099-125">Botón de estilo de Shell de 32x96mm Wide HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f0099-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-126">Barra de botones de HoloLens 2 horizontal con planchas compartidas</span><span class="sxs-lookup"><span data-stu-id="f0099-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-127">Barra de botones de HoloLens 2 vertical con planchas compartidas</span><span class="sxs-lookup"><span data-stu-id="f0099-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="f0099-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="f0099-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="f0099-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="f0099-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="f0099-131">Casilla de estilo de Shell de HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="f0099-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-132">Modificador de estilo de Shell de HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="f0099-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-133">32x32mm de radio de estilo de Shell de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f0099-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="f0099-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="f0099-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="f0099-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="f0099-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f0099-137">Casilla de estilo de Shell de HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="f0099-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-138">Modificador de estilo de Shell de HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="f0099-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-139">32x96mm de radio de estilo de Shell de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f0099-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f0099-140">![](../images/button/MRTK_Button_Radial.png) **Radial** radial</span><span class="sxs-lookup"><span data-stu-id="f0099-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-141">![Casilla](../images/button/MRTK_Button_Checkbox.png) **Casilla**</span><span class="sxs-lookup"><span data-stu-id="f0099-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="f0099-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f0099-143">Botón radial</span><span class="sxs-lookup"><span data-stu-id="f0099-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-144">Casilla de verificación</span><span class="sxs-lookup"><span data-stu-id="f0099-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-145">Modificador para alternar</span><span class="sxs-lookup"><span data-stu-id="f0099-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f0099-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="f0099-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="f0099-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-148">![](../images/button/MRTK_Button_Base.png)  Botón base del botón</span><span class="sxs-lookup"><span data-stu-id="f0099-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="f0099-149">Botón de estilo de Shell de la 1ª de HoloLens</span><span class="sxs-lookup"><span data-stu-id="f0099-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-150">Botón de redondear forma redondeada</span><span class="sxs-lookup"><span data-stu-id="f0099-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="f0099-151">Botón Básica</span><span class="sxs-lookup"><span data-stu-id="f0099-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="f0099-152">`Button`(Assets/MRTK/SDK/Features/UX/interactuable/Prefabs/Button. recurso prefabricado) se basa en el concepto [interactuable](interactable.md) para proporcionar controles de interfaz de usuario sencillos para botones u otros tipos de superficies interactivas.</span><span class="sxs-lookup"><span data-stu-id="f0099-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="f0099-153">El botón de línea de base admite todos los métodos de entrada disponibles, incluida la entrada de mano articulada para las interacciones cercanas, así como la pulsación + aérea para las interacciones lejanas.</span><span class="sxs-lookup"><span data-stu-id="f0099-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="f0099-154">También puede usar el comando Voice para desencadenar el botón.</span><span class="sxs-lookup"><span data-stu-id="f0099-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="f0099-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2. recurso prefabricado) es el botón de Shell de HoloLens 2 que admite el movimiento preciso del botón para la entrada de seguimiento de la mano directa.</span><span class="sxs-lookup"><span data-stu-id="f0099-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="f0099-156">Combina `Interactable` script con `PressableButton` script.</span><span class="sxs-lookup"><span data-stu-id="f0099-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="f0099-157">En el caso de HoloLens 2, se recomienda usar botones con una placa posterior opaca.</span><span class="sxs-lookup"><span data-stu-id="f0099-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="f0099-158">No se recomienda usar botones transparentes debido a estos problemas de facilidad de uso y estabilidad:</span><span class="sxs-lookup"><span data-stu-id="f0099-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="f0099-159">El icono y el texto son difíciles de leer con el entorno físico</span><span class="sxs-lookup"><span data-stu-id="f0099-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="f0099-160">Es difícil comprender cuándo se desencadena el evento.</span><span class="sxs-lookup"><span data-stu-id="f0099-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="f0099-161">Los hologramas que se muestran a través de un plano transparente pueden ser inestables con la estabilización LSR de la profundidad de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0099-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Botón revestido](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="f0099-163">Cómo usar los botones que se van a presionar</span><span class="sxs-lookup"><span data-stu-id="f0099-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="f0099-164">Botones basados en la interfaz de usuario de Unity</span><span class="sxs-lookup"><span data-stu-id="f0099-164">Unity UI based buttons</span></span>

<span data-ttu-id="f0099-165">Cree un lienzo en la escena (GameObject-> lienzo de > de interfaz de usuario).</span><span class="sxs-lookup"><span data-stu-id="f0099-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="f0099-166">En el panel Inspector del lienzo:</span><span class="sxs-lookup"><span data-stu-id="f0099-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="f0099-167">Haga clic en "convertir en lienzo MRTK"</span><span class="sxs-lookup"><span data-stu-id="f0099-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="f0099-168">Haga clic en "agregar NearInteractionTouchableUnityUI".</span><span class="sxs-lookup"><span data-stu-id="f0099-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="f0099-169">Establezca la escala X, y y Z del componente de transformación Rect en 0,001</span><span class="sxs-lookup"><span data-stu-id="f0099-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="f0099-170">A continuación, arrastre `PressableButtonUnityUI` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonUnityUI. recurso prefabricado), `PressableButtonUnityUICircular` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonUnityUICircular. recurso prefabricado) o `PressableButtonHoloLens2UnityUI` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2UnityUI. recurso prefabricado) en el lienzo.</span><span class="sxs-lookup"><span data-stu-id="f0099-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="f0099-171">Botones basados en Colisionador</span><span class="sxs-lookup"><span data-stu-id="f0099-171">Collider based buttons</span></span>

<span data-ttu-id="f0099-172">Simplemente arrastre `PressableButtonHoloLens2` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2. recurso prefabricado) o `PressableButtonHoloLens2Unplated` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2Unplated. recurso prefabricado) en la escena.</span><span class="sxs-lookup"><span data-stu-id="f0099-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="f0099-173">Estos Prefabs de botón ya están configurados para tener comentarios visuales de audio para los distintos tipos de entradas, incluida la entrada de mano articulada y la mirada.</span><span class="sxs-lookup"><span data-stu-id="f0099-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="f0099-174">Los eventos que se exponen en el propio recurso prefabricado, así como el componente [interactuable](interactable.md) , se pueden usar para desencadenar acciones adicionales.</span><span class="sxs-lookup"><span data-stu-id="f0099-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="f0099-175">Los botones que se van a presionar en la [escena HandInteractionExample](../example-scenes/hand-interaction-examples.md) usan el evento *onclick* del que se pueda interactuar para desencadenar un cambio en el color de un cubo.</span><span class="sxs-lookup"><span data-stu-id="f0099-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="f0099-176">Este evento se desencadena para los diferentes tipos de métodos de entrada, como, por ejemplo, la tecla de mira, el toque de aire, la mano y las pulsaciones de botones físicos mediante el script de botón que se admite.</span><span class="sxs-lookup"><span data-stu-id="f0099-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="f0099-177">Puede configurar el momento en el que el botón presionado activa el evento *onclick* a través de `PhysicalPressEventRouter` en el botón.</span><span class="sxs-lookup"><span data-stu-id="f0099-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="f0099-178">Por ejemplo, puede establecer *onclick* para que se desencadene cuando se presiona el botón por primera vez, en lugar de presionarlo y soltarlo, estableciendo *interactuable en click* to *Event on press*.</span><span class="sxs-lookup"><span data-stu-id="f0099-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="f0099-179">Para aprovechar la información específica sobre el estado de entrada articulado, puede utilizar los botones que se pueden presionar: Inicio de la *interacción táctil*, *extremo táctil*, *botón presionado*, *botón liberado*.</span><span class="sxs-lookup"><span data-stu-id="f0099-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="f0099-180">No obstante, estos eventos no se activarán en respuesta a las entradas de punteo de aire, de mano o de ojo.</span><span class="sxs-lookup"><span data-stu-id="f0099-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="f0099-181">**Para admitir interacciones Near y Far, se recomienda el uso del evento *onclick* del que se pueda interactuar.**</span><span class="sxs-lookup"><span data-stu-id="f0099-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="f0099-182">Estados de interacción</span><span class="sxs-lookup"><span data-stu-id="f0099-182">Interaction states</span></span>

<span data-ttu-id="f0099-183">En el estado inactivo, la placa frontal del botón no está visible.</span><span class="sxs-lookup"><span data-stu-id="f0099-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="f0099-184">A medida que se aproxima a un dedo o un cursor de una entrada de mira hacia la superficie, el borde de resplandor de la placa frontal se vuelve visible.</span><span class="sxs-lookup"><span data-stu-id="f0099-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="f0099-185">Hay un resaltado adicional de la posición del dedo en la superficie de la placa frontal.</span><span class="sxs-lookup"><span data-stu-id="f0099-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="f0099-186">Cuando se inserta con un dedo, la placa frontal se mueve con el dedo.</span><span class="sxs-lookup"><span data-stu-id="f0099-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="f0099-187">Cuando el dedo toca la superficie de la placa frontal, muestra un efecto de impulso sutil para proporcionar comentarios visuales del punto táctil.</span><span class="sxs-lookup"><span data-stu-id="f0099-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="f0099-188">En el botón de estilo Shell de HoloLens 2, hay muchas indicaciones visuales y prestaciones para aumentar la confianza del usuario en la interacción.</span><span class="sxs-lookup"><span data-stu-id="f0099-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Luz de proximidad](../images/button/ux_button_affordance_proximitylight.jpg) | ![Resaltado de foco](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Comprimiendo el Cage](../images/button/ux_button_affordance_compression.jpg) | ![Pulso en desencadenador](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="f0099-193">Luz de proximidad</span><span class="sxs-lookup"><span data-stu-id="f0099-193">Proximity light</span></span> | <span data-ttu-id="f0099-194">Resaltado de foco</span><span class="sxs-lookup"><span data-stu-id="f0099-194">Focus highlight</span></span> | <span data-ttu-id="f0099-195">Comprimiendo el Cage</span><span class="sxs-lookup"><span data-stu-id="f0099-195">Compressing cage</span></span> | <span data-ttu-id="f0099-196">Pulso en desencadenador</span><span class="sxs-lookup"><span data-stu-id="f0099-196">Pulse on trigger</span></span> |

<span data-ttu-id="f0099-197">El efecto de impulso sutil se desencadena mediante el botón que se presiona, que busca *ProximityLight (s)* que se encuentren en el puntero que está interactuando actualmente.</span><span class="sxs-lookup"><span data-stu-id="f0099-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="f0099-198">Si se encuentran luces de proximidad, `ProximityLight.Pulse` se llama al método, que anima automáticamente los parámetros del sombreador para mostrar un pulso.</span><span class="sxs-lookup"><span data-stu-id="f0099-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="f0099-199">Propiedades del inspector</span><span class="sxs-lookup"><span data-stu-id="f0099-199">Inspector properties</span></span>

![Estructura del botón](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="f0099-201">Colisionador de caja  
 `Box Collider` para la placa frontal del botón.</span><span class="sxs-lookup"><span data-stu-id="f0099-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="f0099-202">**Botón Presionable** La lógica para el movimiento del botón con interacción de prensa de mano.</span><span class="sxs-lookup"><span data-stu-id="f0099-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="f0099-203">**Enrutador de eventos de prensa física** Este script envía eventos de interacción de [prensa de mano a](interactable.md)interactivos.</span><span class="sxs-lookup"><span data-stu-id="f0099-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="f0099-204">**Interactuable** 
 [Interactúable](interactable.md) controla varios tipos de eventos y Estados de interacción.</span><span class="sxs-lookup"><span data-stu-id="f0099-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="f0099-205">Este script controla directamente la entrada de voz y el gestos de HoloLens, así como la entrada del controlador de movimiento de auriculares envolvente.</span><span class="sxs-lookup"><span data-stu-id="f0099-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="f0099-206">**Origen de audio** Origen de audio de Unity para los clips de comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="f0099-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="f0099-207">*NearInteractionTouchable. CS* necesario para que cualquier objeto pueda tocarse con la entrada de mano articulada.</span><span class="sxs-lookup"><span data-stu-id="f0099-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="f0099-208">Diseño de recurso prefabricado</span><span class="sxs-lookup"><span data-stu-id="f0099-208">Prefab layout</span></span>

<span data-ttu-id="f0099-209">El objeto *ButtonContent* contiene la placa frontal, la etiqueta de texto y el icono.</span><span class="sxs-lookup"><span data-stu-id="f0099-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="f0099-210">El *FrontPlate* responde a la proximidad del alcance del índice mediante el sombreador de *Button_Box* .</span><span class="sxs-lookup"><span data-stu-id="f0099-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="f0099-211">Muestra bordes iluminados, luz de proximidad y un efecto de impulso en el tacto.</span><span class="sxs-lookup"><span data-stu-id="f0099-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="f0099-212">La etiqueta de texto se realiza con TextMesh Pro.</span><span class="sxs-lookup"><span data-stu-id="f0099-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="f0099-213">La visibilidad de *SeeItSayItLabel* se controla mediante el tema del que se pueda [interactuar](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="f0099-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Diseño del botón](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="f0099-215">Cómo cambiar el icono y el texto</span><span class="sxs-lookup"><span data-stu-id="f0099-215">How to change the icon and text</span></span>

<span data-ttu-id="f0099-216">Los botones de MRTK usan un `ButtonConfigHelper` componente para ayudarle a cambiar el icono, el texto y la etiqueta del botón.</span><span class="sxs-lookup"><span data-stu-id="f0099-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="f0099-217">(Tenga en cuenta que algunos campos pueden estar ausentes si los elementos no están presentes en el botón seleccionado).</span><span class="sxs-lookup"><span data-stu-id="f0099-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Aplicación auxiliar de configuración de botones](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="f0099-219">Crear y modificar conjuntos de iconos</span><span class="sxs-lookup"><span data-stu-id="f0099-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="f0099-220">Un **conjunto de iconos** es un conjunto compartido de activos de iconos utilizados por el `ButtonConfigHelper` componente.</span><span class="sxs-lookup"><span data-stu-id="f0099-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="f0099-221">Se admiten tres *estilos* de icono.</span><span class="sxs-lookup"><span data-stu-id="f0099-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="f0099-222">Los iconos **cuádruples** se representan en un cuádruple mediante `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="f0099-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="f0099-223">Este es el estilo de icono predeterminado.</span><span class="sxs-lookup"><span data-stu-id="f0099-223">This is the default icon style.</span></span>
* <span data-ttu-id="f0099-224">Los iconos de **Sprite** se representan mediante `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="f0099-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="f0099-225">Esto resulta útil si prefiere importar los iconos como una hoja de Sprite o si desea que los recursos de icono se compartan con los componentes de la interfaz de usuario de Unity.</span><span class="sxs-lookup"><span data-stu-id="f0099-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="f0099-226">Para usar este estilo, deberá instalar el paquete de editor de Sprite **(Windows-> administrador de paquetes-> Sprite 2D)** .</span><span class="sxs-lookup"><span data-stu-id="f0099-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="f0099-227">Los iconos **Char** se representan mediante un `TextMeshPro` componente.</span><span class="sxs-lookup"><span data-stu-id="f0099-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="f0099-228">Esto resulta útil si prefiere usar una fuente de icono.</span><span class="sxs-lookup"><span data-stu-id="f0099-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="f0099-229">Para usar la fuente del icono de HoloLens, tendrá que crear un `TextMeshPro` recurso de fuente.</span><span class="sxs-lookup"><span data-stu-id="f0099-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="f0099-230">Para cambiar el estilo que utiliza el botón, expanda la lista desplegable *iconos* en el ButtonConfigHelper y seleccione en el menú desplegable *estilo de icono* .</span><span class="sxs-lookup"><span data-stu-id="f0099-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="f0099-231">Puede crear un nuevo icono de botón con el menú activo: **crear > kit de herramientas de realidad mixta > conjunto de iconos.**</span><span class="sxs-lookup"><span data-stu-id="f0099-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="f0099-232">Para agregar iconos de cuatro y Sprite, simplemente arrástrelos a sus respectivas matrices.</span><span class="sxs-lookup"><span data-stu-id="f0099-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="f0099-233">Para agregar iconos de carácter, primero debe crear y asignar un recurso de fuente.</span><span class="sxs-lookup"><span data-stu-id="f0099-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="f0099-234">En MRTK 2,4 y versiones posteriores, se recomienda que las texturas de iconos personalizados se muevan a un IconSet.</span><span class="sxs-lookup"><span data-stu-id="f0099-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="f0099-235">Para actualizar los recursos de todos los botones de un proyecto al nuevo formato recomendado, use ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="f0099-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="f0099-236">(Kit de herramientas de realidad mixta-> Utilities-> ventana de migración-> selección de controlador de migración > Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="f0099-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="f0099-237">Importar el paquete Microsoft. MixedRealityToolkit. Unity. Tools necesario para actualizar los botones.</span><span class="sxs-lookup"><span data-stu-id="f0099-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Cuadro de diálogo Actualizar ventana](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="f0099-239">Si no se encuentra un icono en el conjunto de iconos predeterminado durante la migración, se creará un conjunto de iconos personalizado en MixedRealityToolkit. generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="f0099-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="f0099-240">Un cuadro de diálogo indicará que se ha producido.</span><span class="sxs-lookup"><span data-stu-id="f0099-240">A dialog will indicate that this has taken place.</span></span>

![Notificación de icono personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="f0099-242">Creación de un recurso de fuente de icono de HoloLens</span><span class="sxs-lookup"><span data-stu-id="f0099-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="f0099-243">En primer lugar, importe la fuente del icono en Unity.</span><span class="sxs-lookup"><span data-stu-id="f0099-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="f0099-244">En máquinas Windows, puede encontrar la fuente HoloLens predeterminada en *Windows/Fonts/holomdl2. ttf.*</span><span class="sxs-lookup"><span data-stu-id="f0099-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="f0099-245">Copie y pegue este archivo en la carpeta assets.</span><span class="sxs-lookup"><span data-stu-id="f0099-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="f0099-246">A continuación, abra el creador del recurso TextMeshPro Font a través de la **ventana > TextMeshPro > Font Asset Creator.**</span><span class="sxs-lookup"><span data-stu-id="f0099-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="f0099-247">Esta es la configuración recomendada para generar un Atlas de fuentes HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0099-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="f0099-248">Para incluir todos los iconos, pegue el siguiente intervalo Unicode en el campo *secuencia de caracteres* :</span><span class="sxs-lookup"><span data-stu-id="f0099-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Creación de botón 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="f0099-250">Una vez generado el recurso de fuente, guárdelo en el proyecto y asígnelo al campo de *fuente del icono de char* del conjunto de iconos.</span><span class="sxs-lookup"><span data-stu-id="f0099-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="f0099-251">Ahora se rellenará la lista desplegable de *iconos disponibles* .</span><span class="sxs-lookup"><span data-stu-id="f0099-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="f0099-252">Para hacer que un icono esté disponible para que lo use un botón, haga clic en él.</span><span class="sxs-lookup"><span data-stu-id="f0099-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="f0099-253">Se agregará a la lista desplegable de *iconos seleccionados* y ahora se mostrará en el `ButtonConfigHelper.` , de manera opcional, puede asignarle el icono a una etiqueta.</span><span class="sxs-lookup"><span data-stu-id="f0099-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="f0099-254">Esto permite establecer el icono en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="f0099-254">This enables setting the icon at runtime.</span></span>

![Creación de botón 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Creación de botón 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="f0099-257">Para usar el conjunto de iconos, seleccione un botón, expanda la lista desplegable iconos en el `ButtonConfigHelper` y asígnelo al campo *conjunto de iconos* .</span><span class="sxs-lookup"><span data-stu-id="f0099-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Conjunto de iconos de botón](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="f0099-259">Cómo cambiar el tamaño de un botón</span><span class="sxs-lookup"><span data-stu-id="f0099-259">How to change the size of a button</span></span>

<span data-ttu-id="f0099-260">El tamaño del botón de estilo de Shell de HoloLens 2 es 32x32mm.</span><span class="sxs-lookup"><span data-stu-id="f0099-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="f0099-261">Para personalizar la dimensión, cambie el tamaño de estos objetos en el botón recurso prefabricado:</span><span class="sxs-lookup"><span data-stu-id="f0099-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="f0099-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="f0099-262">**FrontPlate**</span></span>
2. <span data-ttu-id="f0099-263">**Cuádruple** debajo del fondo</span><span class="sxs-lookup"><span data-stu-id="f0099-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="f0099-264">**Colisionador de Box** en la raíz</span><span class="sxs-lookup"><span data-stu-id="f0099-264">**Box Collider** on the root</span></span>

<span data-ttu-id="f0099-265">A continuación, haga clic en el botón **corregir límites** del script NearInteractionTouchable que se encuentra en la raíz del botón.</span><span class="sxs-lookup"><span data-stu-id="f0099-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="f0099-266">Actualiza el tamaño de la ![ Personalización del tamaño del botón de FrontPlate 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="f0099-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="f0099-267">Actualizar el tamaño de la ![ Personalización de tamaño de botón cuádruple 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="f0099-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="f0099-268">Actualiza el tamaño de la personalización del tamaño del botón del Colisionador de caja ![ 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="f0099-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="f0099-269">Haga clic en el botón "corregir límites" ![ Personalización de tamaño 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="f0099-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it&quot;></a><span data-ttu-id=&quot;f0099-270&quot;>Comando de voz (&quot;ver, por ejemplo, ti")</span><span class="sxs-lookup"><span data-stu-id="f0099-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="f0099-271">**Controlador de entrada de voz** El script [interactuable](interactable.md) en el botón Presionable ya implementa `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="f0099-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="f0099-272">Aquí puede establecerse una palabra clave de comando de voz.</span><span class="sxs-lookup"><span data-stu-id="f0099-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="f0099-273">**Perfil de entrada de voz** Además, debe registrar la palabra clave de comando de voz en el *perfil* global de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="f0099-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="f0099-274">**Ver, por ejemplo, etiqueta de ti** El botón pressable recurso prefabricado tiene una etiqueta de marcador de posición TextMesh Pro en el objeto *SeeItSayItLabel* .</span><span class="sxs-lookup"><span data-stu-id="f0099-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="f0099-275">Puede usar esta etiqueta para comunicar la palabra clave de comando de voz del botón al usuario.</span><span class="sxs-lookup"><span data-stu-id="f0099-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="f0099-276">Cómo crear un botón desde cero</span><span class="sxs-lookup"><span data-stu-id="f0099-276">How to make a button from scratch</span></span>

<span data-ttu-id="f0099-277">Puede encontrar ejemplos de estos botones en la escena de **PressableButtonExample** .</span><span class="sxs-lookup"><span data-stu-id="f0099-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="f0099-278">1. crear un botón que se presione con Cube (solo interacción cercana)</span><span class="sxs-lookup"><span data-stu-id="f0099-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="f0099-279">Crear un cubo de Unity (GameObject > objeto 3D > cubo)</span><span class="sxs-lookup"><span data-stu-id="f0099-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="f0099-280">Agregar `PressableButton.cs` script</span><span class="sxs-lookup"><span data-stu-id="f0099-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="f0099-281">Agregar `NearInteractionTouchable.cs` script</span><span class="sxs-lookup"><span data-stu-id="f0099-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="f0099-282">En el `PressableButton` panel Inspector del, asigne el objeto de cubo a los objetos **visuales del botón de movimiento**.</span><span class="sxs-lookup"><span data-stu-id="f0099-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="f0099-283">Al seleccionar el cubo, verá varias capas de color en el objeto.</span><span class="sxs-lookup"><span data-stu-id="f0099-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="f0099-284">Esto visualiza los valores de distancia en la **configuración de Press**.</span><span class="sxs-lookup"><span data-stu-id="f0099-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="f0099-285">Mediante el uso de los identificadores, puede configurar Cuándo se debe iniciar la pulsación (movimiento del objeto) y cuándo se desencadenará el evento.</span><span class="sxs-lookup"><span data-stu-id="f0099-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="f0099-286">Cuando se presiona el botón, se mueven y generan los eventos adecuados que se exponen en el script, como `PressableButton.cs` TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().</span><span class="sxs-lookup"><span data-stu-id="f0099-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="f0099-287">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="f0099-287">Troubleshooting</span></span>

<span data-ttu-id="f0099-288">Si el botón está ejecutando una doble presión, asegúrese de que la propiedad aplicar la entrada **delantera** está activa y de que el plano de **distancia de inicio** se coloca delante del plano táctil de la **interacción cercana** .</span><span class="sxs-lookup"><span data-stu-id="f0099-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="f0099-289">El plano **táctil cercano** a la interacción se indica mediante el plano azul colocado delante del origen de la flecha blanca en el GIF siguiente:</span><span class="sxs-lookup"><span data-stu-id="f0099-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Componente de script de botón que se admite con la propiedad aplicar Front-out resaltada](../images/button/MRTK_Button_Enforce_Push.png)

![Ejemplo animado de movimiento de la distancia de la pulsación inicial delante del plano táctil de la interacción cercana](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="f0099-292">2. agregar comentarios visuales al botón básico del cubo</span><span class="sxs-lookup"><span data-stu-id="f0099-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="f0099-293">El sombreador estándar de MRTK proporciona varias características que facilitan la adición de comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="f0099-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="f0099-294">Cree un material y seleccione Shader `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="f0099-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="f0099-295">O bien, puede usar o duplicar uno de los materiales existentes en `/SDK/StandardAssets/Materials/` que usa el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="f0099-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="f0099-296">Active `Hover Light` y `Proximity Light` en **Opciones fluidas**.</span><span class="sxs-lookup"><span data-stu-id="f0099-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="f0099-297">Esto permite que los comentarios visuales se intermuevan a la mano (luz de proximidad) y a las interacciones de puntero lejano (luz de desplazamiento).</span><span class="sxs-lookup"><span data-stu-id="f0099-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="f0099-298">3. agregar comentarios de audio al botón básico del cubo</span><span class="sxs-lookup"><span data-stu-id="f0099-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="f0099-299">Puesto que el `PressableButton.cs` script expone eventos como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), se pueden asignar fácilmente comentarios de audio.</span><span class="sxs-lookup"><span data-stu-id="f0099-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="f0099-300">Simplemente agregue Unity `Audio Source` al objeto de cubo y, a continuación, asigne los clips de audio seleccionando AudioSource. PlayOneShot ().</span><span class="sxs-lookup"><span data-stu-id="f0099-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="f0099-301">Puede usar MRTK_Select_Main y MRTK_Select_Secondary clips de audio en `/SDK/StandardAssets/Audio/` carpeta.</span><span class="sxs-lookup"><span data-stu-id="f0099-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="f0099-302">4. agregar Estados visuales y controlar eventos de interacción lejana</span><span class="sxs-lookup"><span data-stu-id="f0099-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="f0099-303">[Interactúable](interactable.md) es un script que facilita la creación de un estado visual para los distintos tipos de interacciones de entrada.</span><span class="sxs-lookup"><span data-stu-id="f0099-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="f0099-304">También controla los eventos de interacción Far.</span><span class="sxs-lookup"><span data-stu-id="f0099-304">It also handles far interaction events.</span></span> <span data-ttu-id="f0099-305">Agregue `Interactable.cs` y arrastre y coloque el objeto de cubo en el campo de **destino** en **perfiles**.</span><span class="sxs-lookup"><span data-stu-id="f0099-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="f0099-306">A continuación, cree un nuevo tema con un tipo **ScaleOffsetColorTheme**.</span><span class="sxs-lookup"><span data-stu-id="f0099-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="f0099-307">En este tema, puede especificar el color del objeto para los Estados de interacción específicos, como el **foco** y **presionado**.</span><span class="sxs-lookup"><span data-stu-id="f0099-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="f0099-308">También puede controlar la escala y el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="f0099-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="f0099-309">Compruebe la **aceleración** y establezca la duración para que la transición visual sea fluida.</span><span class="sxs-lookup"><span data-stu-id="f0099-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Seleccionar tema de perfil](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="f0099-311">Verá que el objeto responde a interacciones lejanas (cursor de mano o hacia abajo) y Near (mano).</span><span class="sxs-lookup"><span data-stu-id="f0099-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="f0099-312">Ejemplos de botones personalizados</span><span class="sxs-lookup"><span data-stu-id="f0099-312">Custom button examples</span></span>

<span data-ttu-id="f0099-313">En la [escena de HandInteractionExample](../example-scenes/hand-interaction-examples.md), vea los ejemplos de los botones de piano y redondo que usan `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="f0099-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="f0099-314">Cada clave de piano tiene un `PressableButton` y un `NearInteractionTouchable` script asignado.</span><span class="sxs-lookup"><span data-stu-id="f0099-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="f0099-315">Es importante comprobar que la dirección de *avance local* de `NearInteractionTouchable` es correcta.</span><span class="sxs-lookup"><span data-stu-id="f0099-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="f0099-316">Se representa mediante una flecha blanca en el editor.</span><span class="sxs-lookup"><span data-stu-id="f0099-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="f0099-317">Asegúrese de que la flecha apunta fuera de la cara frontal del botón:</span><span class="sxs-lookup"><span data-stu-id="f0099-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="f0099-318">Vea también</span><span class="sxs-lookup"><span data-stu-id="f0099-318">See also</span></span>

* [<span data-ttu-id="f0099-319">Interactuable</span><span class="sxs-lookup"><span data-stu-id="f0099-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="f0099-320">Temas visuales</span><span class="sxs-lookup"><span data-stu-id="f0099-320">Visual Themes</span></span>](visual-themes.md)
