---
title: Menú Cerca
description: Introducción a los tipos de menús cercanos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, menú cercano,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175656"
---
# <a name="near-menu"></a><span data-ttu-id="3a9f2-104">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="3a9f2-104">Near menu</span></span>

![Menú Cerca](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="3a9f2-106">Near Menu es un control de experiencia de usuario que proporciona una colección de botones u otros componentes de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="3a9f2-107">Está flotante alrededor del cuerpo del usuario y es fácilmente accesible en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="3a9f2-108">Dado que se acopla de forma flexible con el usuario, no afecta a la interacción del usuario con el contenido de destino.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="3a9f2-109">El usuario puede usar el botón "Anclar" para bloquear o desbloquear el menú.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="3a9f2-110">El menú se puede agarrar y colocar en una posición específica.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="3a9f2-111">Comportamiento de interacción</span><span class="sxs-lookup"><span data-stu-id="3a9f2-111">Interaction behavior</span></span>

- <span data-ttu-id="3a9f2-112">**Etiqueta: el** menú le sigue y permanece dentro del intervalo de 30-60 cm desde el usuario para las interacciones cercanas.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="3a9f2-113">**Anclar:** con el botón "Anclar", el menú se puede bloquear y liberar.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="3a9f2-114">**Agarrar y mover:** el menú siempre se puede agarrar y mover.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="3a9f2-115">Independientemente del estado anterior, el menú se anclará (bloqueado por el mundo) cuando se agarrá y se liberará.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="3a9f2-116">Hay indicaciones visuales para el área que se puede agarrar.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="3a9f2-117">Se revelan por proximidad.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="3a9f2-118">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="3a9f2-118">Prefabs</span></span>

<span data-ttu-id="3a9f2-119">Los elementos prefabs de menú cercano están diseñados para mostrar cómo usar los distintos componentes de MRTK para crear menús para interacciones cercanas.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="3a9f2-120">**NearMenu2x4.prefab**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="3a9f2-121">**NearMenu3x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="3a9f2-122">**NearMenu3x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="3a9f2-123">**NearMenu3x3.prefab**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="3a9f2-124">**NearMenu4x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="3a9f2-125">**NearMenu4x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="3a9f2-126">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="3a9f2-126">Example scene</span></span>

<span data-ttu-id="3a9f2-127">Puede encontrar ejemplos de elementos prefabs de menú cercano en la `NearMenuExamples` escena.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="3a9f2-128">Estructura</span><span class="sxs-lookup"><span data-stu-id="3a9f2-128">Structure</span></span>

<span data-ttu-id="3a9f2-129">Los elementos prefabs del menú cercano se realizan con los siguientes componentes de MRTK.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="3a9f2-130">[**Prefab PressableButtonHoloLens2**](button.md)</span><span class="sxs-lookup"><span data-stu-id="3a9f2-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="3a9f2-131">[**Colección de objetos grid:**](object-collection.md)diseño de varios botones en la cuadrícula</span><span class="sxs-lookup"><span data-stu-id="3a9f2-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="3a9f2-132">[**Controlador de manipulación:**](manipulation-handler.md)agarrar y mover el menú</span><span class="sxs-lookup"><span data-stu-id="3a9f2-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="3a9f2-133">[**Solucionador radialView:**](solvers/solver.md)seguir el comportamiento de me (etiqueta)</span><span class="sxs-lookup"><span data-stu-id="3a9f2-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![Menú cercano prefab](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="3a9f2-135">Cómo realizar la personalización</span><span class="sxs-lookup"><span data-stu-id="3a9f2-135">How to customize</span></span>

<span data-ttu-id="3a9f2-136">**1. Agregar o quitar botones**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="3a9f2-137">En `ButtonCollection` objeto , agregue o quite botones.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="3a9f2-138">**2. Actualización de la colección de objetos Grid**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="3a9f2-139">Haga `Update Collection` clic en el botón del inspector del `ButtonCollection` objeto.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="3a9f2-140">Actualizará el diseño de la cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="3a9f2-141">Puede configurar el número de filas mediante la `Rows` propiedad de la colección de objetos Grid.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="3a9f2-142">**3. Ajuste del tamaño de la placa trasera**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="3a9f2-143">Ajuste el tamaño del objeto `Quad` `Backplate` debajo de .</span><span class="sxs-lookup"><span data-stu-id="3a9f2-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="3a9f2-144">El ancho y alto de la placa trasera deben ser `0.032 * [Number of the buttons + 1]` .</span><span class="sxs-lookup"><span data-stu-id="3a9f2-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="3a9f2-145">Por ejemplo, si tiene 3 x 2 botones, el ancho de la placa trasera es `0.032 * 4` y el alto es `0.032 * 3` .</span><span class="sxs-lookup"><span data-stu-id="3a9f2-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="3a9f2-146">Puede colocar directamente esta expresión en el campo de Unity.</span><span class="sxs-lookup"><span data-stu-id="3a9f2-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="3a9f2-147">El tamaño predeterminado del botón HoloLens 2 es 3,2 x 3,2 cm (0,032 m)</span><span class="sxs-lookup"><span data-stu-id="3a9f2-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="3a9f2-148">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3a9f2-148">See also</span></span>

- [<span data-ttu-id="3a9f2-149">**Botones**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="3a9f2-150">**Control de límites**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="3a9f2-151">**Slider**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="3a9f2-152">**Colección de objetos Grid**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="3a9f2-153">**Controlador de manipulación**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="3a9f2-154">**RadialView Solver**</span><span class="sxs-lookup"><span data-stu-id="3a9f2-154">**RadialView Solver**</span></span>](solvers/solver.md)
