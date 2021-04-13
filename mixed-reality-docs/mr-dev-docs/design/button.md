---
title: Botón
description: Aprenda a desencadenar una acción inmediata con botones, que es uno de los componentes fundamentales de la realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, interfaz de usuario, UX, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, botón
ms.openlocfilehash: 177ccfc1c07df9a9523c9ed6733d3da61bdb7921
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299760"
---
# <a name="button"></a><span data-ttu-id="8c03c-104">Button</span><span class="sxs-lookup"><span data-stu-id="8c03c-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="8c03c-106">Un botón permite a los usuarios desencadenar acciones inmediatas en una experiencia de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8c03c-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="8c03c-107">En HoloLens 2, los botones tienen indicaciones visuales y prestaciones que ayudan a aumentar la confianza de la interacción con los usuarios.</span><span class="sxs-lookup"><span data-stu-id="8c03c-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="8c03c-108">![Botón con el efecto de luz de proximidad mostrado](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c03c-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="8c03c-109">**Luz de proximidad**</span><span class="sxs-lookup"><span data-stu-id="8c03c-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8c03c-110">![Botón seleccionado con el efecto resaltado de foco mostrado](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c03c-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="8c03c-111">**Resaltado de foco**</span><span class="sxs-lookup"><span data-stu-id="8c03c-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8c03c-112">![Botón que se va a presionar con el efecto de la jaula de compresión mostrado](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c03c-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="8c03c-113">**Comprimiendo el Cage**</span><span class="sxs-lookup"><span data-stu-id="8c03c-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8c03c-114">![Botón que se está presionando con el efecto desencadenador mostrado](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c03c-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="8c03c-115">**Pulso en desencadenador**</span><span class="sxs-lookup"><span data-stu-id="8c03c-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="8c03c-116">Botón en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="8c03c-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="8c03c-117">**[MRTK para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona varios tipos de Prefabs de botón, incluidos los botones de estilo de Shell de hololens 2 y hololens (1ª generación).</span><span class="sxs-lookup"><span data-stu-id="8c03c-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="8c03c-118">El botón recurso prefabricado de HoloLens 2 contiene varias prestaciones detalladas que ayudan a mejorar la confianza del usuario:</span><span class="sxs-lookup"><span data-stu-id="8c03c-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="8c03c-119">Resaltado basado en proximidad</span><span class="sxs-lookup"><span data-stu-id="8c03c-119">Proximity-based highlight</span></span>
* <span data-ttu-id="8c03c-120">Comprimiendo el compartimento delantero</span><span class="sxs-lookup"><span data-stu-id="8c03c-120">Compressing front cage</span></span>
* <span data-ttu-id="8c03c-121">Efecto de impulso en el desencadenador.</span><span class="sxs-lookup"><span data-stu-id="8c03c-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="8c03c-122">Consulte el [botón MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) para obtener más instrucciones y ejemplos personalizados.</span><span class="sxs-lookup"><span data-stu-id="8c03c-122">Check out the [MRTK - Button](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="8c03c-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="8c03c-123">See also</span></span>

* [<span data-ttu-id="8c03c-124">Cursores</span><span class="sxs-lookup"><span data-stu-id="8c03c-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8c03c-125">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="8c03c-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8c03c-126">Botón</span><span class="sxs-lookup"><span data-stu-id="8c03c-126">Button</span></span>](button.md)
* [<span data-ttu-id="8c03c-127">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="8c03c-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8c03c-128">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="8c03c-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8c03c-129">Manipulación</span><span class="sxs-lookup"><span data-stu-id="8c03c-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8c03c-130">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="8c03c-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8c03c-131">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="8c03c-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8c03c-132">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="8c03c-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8c03c-133">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="8c03c-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8c03c-134">Teclado</span><span class="sxs-lookup"><span data-stu-id="8c03c-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8c03c-135">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="8c03c-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8c03c-136">Claqueta</span><span class="sxs-lookup"><span data-stu-id="8c03c-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="8c03c-137">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="8c03c-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="8c03c-138">Sombreador</span><span class="sxs-lookup"><span data-stu-id="8c03c-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="8c03c-139">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="8c03c-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8c03c-140">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="8c03c-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8c03c-141">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="8c03c-141">Surface magnetism</span></span>](surface-magnetism.md)
