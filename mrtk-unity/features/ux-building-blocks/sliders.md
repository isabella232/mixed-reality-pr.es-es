---
title: Controles deslizantes
description: Información general de MRTK de controles deslizantes
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, controles deslizantes,
ms.openlocfilehash: c8a2b6c377762918bfff79008ab34d3dfe4e20bb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177501"
---
# <a name="sliders"></a><span data-ttu-id="b0bbf-104">Controles deslizantes</span><span class="sxs-lookup"><span data-stu-id="b0bbf-104">Sliders</span></span>

![Ejemplo de control deslizante](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="b0bbf-106">Los controles deslizantes son componentes de la interfaz de usuario que permiten cambiar continuamente un valor moviendo un control deslizante en una pista. Actualmente, el control deslizante Desenlazador se puede mover agarrándose directamente al control deslizante, ya sea directamente o a una distancia.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="b0bbf-107">Los controles deslizantes funcionan en AR y VR, mediante controladores de movimiento, manos o Gesto + voz.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="b0bbf-108">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="b0bbf-108">Example scene</span></span>

<span data-ttu-id="b0bbf-109">Puede encontrar ejemplos en la escena **SliderExample** en `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="b0bbf-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="b0bbf-110">Uso de controles deslizantes</span><span class="sxs-lookup"><span data-stu-id="b0bbf-110">How to use sliders</span></span>

<span data-ttu-id="b0bbf-111">Arrastre y coloque el prefab **PinchSlider** en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="b0bbf-112">Si desea modificar o crear su propio control deslizante, recuerde hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b0bbf-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="b0bbf-113">Asegúrese de que el objeto de control tiene un colisionador.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="b0bbf-114">En el prefab de PinchSlider, el colisionador está en `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="b0bbf-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="b0bbf-115">Asegúrese de que el objeto que contiene el colisionador también tiene un componente Near Interaction Grabbable (Interacción cercana que se puede capturar) si desea poder acercar el control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="b0bbf-116">También se recomienda usar la siguiente jerarquía</span><span class="sxs-lookup"><span data-stu-id="b0bbf-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="b0bbf-117">PinchSlider: contiene el control deslizanteComponent.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="b0bbf-118">TouchCollider: colisionador que contiene todo el área seleccionable del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="b0bbf-119">Habilita el comportamiento Ajustar a posición.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="b0bbf-120">SliderThumb: contiene el control de posición móvil</span><span class="sxs-lookup"><span data-stu-id="b0bbf-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="b0bbf-121">TrackVisuals: contiene la pista y cualquier otro objeto visual.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="b0bbf-122">OtherVisuals: que contiene cualquier otro objeto visual</span><span class="sxs-lookup"><span data-stu-id="b0bbf-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="b0bbf-123">Eventos de control deslizante</span><span class="sxs-lookup"><span data-stu-id="b0bbf-123">Slider events</span></span>

<span data-ttu-id="b0bbf-124">Los controles deslizantes exponen los siguientes eventos:</span><span class="sxs-lookup"><span data-stu-id="b0bbf-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="b0bbf-125">OnValueUpdated: se llama cada vez que cambia el valor del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="b0bbf-126">OnInteractionStarted: se llama cuando el usuario toma el control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="b0bbf-127">OnInteractionEnded: se llama cuando el usuario suelta el control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="b0bbf-128">OnHoverEntered: se llama cuando la mano o el controlador del usuario mantiene el puntero sobre el control deslizante, mediante una interacción cercana o lejana.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="b0bbf-129">OnHoverExited: se llama cuando la mano o el controlador del usuario ya no está cerca del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="b0bbf-130">Configuración del límite del control deslizante y el eje</span><span class="sxs-lookup"><span data-stu-id="b0bbf-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="b0bbf-131">Puede mover directamente los puntos inicial y final del control deslizante moviendo los identificadores de la escena:</span><span class="sxs-lookup"><span data-stu-id="b0bbf-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![Configuración de controles deslizantes](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="b0bbf-133">También puede especificar el eje (en el espacio local) del control deslizante a través del _campo Eje deslizante._</span><span class="sxs-lookup"><span data-stu-id="b0bbf-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="b0bbf-134">Si no puede usar los identificadores, en su lugar puede especificar los puntos inicial y final del control deslizante a través de los campos _Slider Start Distance_ (Distancia de inicio del control deslizante) y Slider End Distance _(Distancia final del_ control deslizante).</span><span class="sxs-lookup"><span data-stu-id="b0bbf-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="b0bbf-135">Estos especifican la posición inicial y final del control deslizante como una distancia desde el centro del control deslizante, en coordenadas locales.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="b0bbf-136">Esto significa que, una vez establecidas las distancias de inicio y finalización del control deslizante como quiera, puede escalar el control deslizante para que sea menor o mayor sin necesidad de actualizar las distancias inicial y final.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="b0bbf-137">Propiedades del inspector</span><span class="sxs-lookup"><span data-stu-id="b0bbf-137">Inspector properties</span></span>

<span data-ttu-id="b0bbf-138">**Raíz de thumb** Objeto gameobject que contiene el control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="b0bbf-139">**Ajustar a la posición** Si este control deslizante se ajusta o no a la posición designada en el control deslizante</span><span class="sxs-lookup"><span data-stu-id="b0bbf-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="b0bbf-140">**Es táctil** Si este control deslizante se puede controlar o no a través de eventos táctiles</span><span class="sxs-lookup"><span data-stu-id="b0bbf-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="b0bbf-141">**Colisionador de thumb** Colisionador que controla el control deslizante</span><span class="sxs-lookup"><span data-stu-id="b0bbf-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="b0bbf-142">**Colisionador táctil** Área del control deslizante que se puede tocar o seleccionar cuando Ajustar a la posición es true.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="b0bbf-143">**Valor del control deslizante** Valor del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="b0bbf-144">**Usar divisiones de pasos de control deslizante** Controla si este control deslizante se incrementa en pasos o continuamente.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="b0bbf-145">**Divisiones de pasos de control deslizante** Número de subdivisiones en las que se divide el control deslizante cuando se habilita Usar divisiones de pasos deslizantes.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="b0bbf-146">**Seguimiento de objetos visuales** Objeto gameobject que contiene los objetos visuales de seguimiento deseados que van a lo largo del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="b0bbf-147">**Marcas de graduación** Objeto gameobject que contiene las marcas de graduación deseadas que van a lo largo del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="b0bbf-148">**Objetos visuales thumb** El objeto gameobject que contiene el objeto visual de posición deseado que va a lo largo del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="b0bbf-149">**Eje deslizante** Eje a lo largo del que se mueve el control deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="b0bbf-150">**Distancia de inicio del control deslizante** Donde se inicia la pista del control deslizante, como distancia desde el centro a lo largo del eje deslizante, en unidades de espacio local.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="b0bbf-151">**Distancia final del control deslizante** Donde finaliza la pista del control deslizante, como distancia desde el centro a lo largo del eje deslizante, en unidades de espacio local.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="b0bbf-152">Cuando el usuario actualiza el valor del eje deslizante en el editor, si se especifica Track Visuals o Tick Visuals, se actualiza su transformación.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="b0bbf-153">En concreto, se restablece su posición local y su rotación local se establece para que coincida con la orientación del eje deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="b0bbf-154">Su escala no se modifica.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-154">Their scale isn't modified.</span></span>
<span data-ttu-id="b0bbf-155">Si las marcas de graduación tienen un componente Colección de objetos de cuadrícula, layout y CellWidth o CellHeight se actualizan en consecuencia para que coincidan con el eje deslizante.</span><span class="sxs-lookup"><span data-stu-id="b0bbf-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="b0bbf-156">Configuraciones de control deslizante de ejemplo</span><span class="sxs-lookup"><span data-stu-id="b0bbf-156">Example Slider Configurations</span></span>

<span data-ttu-id="b0bbf-157">Controles deslizantes continuos con controles deslizantes continuos ajustar ![ a la posición](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="b0bbf-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="b0bbf-158">Controles deslizantes de paso con ajustar a la posición</span><span class="sxs-lookup"><span data-stu-id="b0bbf-158">Step Sliders with Snap To Position</span></span>

![Controles deslizantes de pasos](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="b0bbf-160">Controles deslizantes táctiles</span><span class="sxs-lookup"><span data-stu-id="b0bbf-160">Touch Sliders</span></span>

![Controles deslizantes táctiles](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
