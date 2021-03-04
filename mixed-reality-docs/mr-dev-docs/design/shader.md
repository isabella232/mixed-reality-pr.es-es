---
title: Sombreador
description: Obtenga información sobre cómo el sombreador estándar del kit de herramientas de realidad mixta proporciona varios tipos de efectos visuales que se pueden usar con hologramas en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, interfaz de usuario, UX, sombreador, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, efectos visuales
ms.openlocfilehash: 046969d1d16c2bddcf5b0a392d721c291b945a94
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759126"
---
# <a name="shader"></a><span data-ttu-id="efb7a-104">Sombreador</span><span class="sxs-lookup"><span data-stu-id="efb7a-104">Shader</span></span>

![Sombreador](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="efb7a-106">Dado que los objetos holográficas se mezclan con los físicos en el entorno real, es importante proporcionar indicaciones visuales al usuario.</span><span class="sxs-lookup"><span data-stu-id="efb7a-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="efb7a-107">El sombreador estándar del kit de herramientas de realidad mixta proporciona varios tipos de efectos visuales para su uso con hologramas.</span><span class="sxs-lookup"><span data-stu-id="efb7a-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="efb7a-108">El sistema de sombreado usa un único sombreador flexible para lograr objetos visuales similares al sombreador estándar de Unity.</span><span class="sxs-lookup"><span data-stu-id="efb7a-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="efb7a-109">El sombreador implementa [principios del sistema de diseño fluida](https://www.microsoft.com/design/fluent/#/) y sigue teniendo un rendimiento en dispositivos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="efb7a-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="efb7a-110">Ejemplos de efectos visuales con el sombreador estándar de MRTK (kit de herramientas de realidad mixta)</span><span class="sxs-lookup"><span data-stu-id="efb7a-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="efb7a-111">![Mover](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="efb7a-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="efb7a-112">**Luz de proximidad**</span><span class="sxs-lookup"><span data-stu-id="efb7a-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="efb7a-113">![Girar](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="efb7a-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="efb7a-114">**Borde claro**</span><span class="sxs-lookup"><span data-stu-id="efb7a-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="efb7a-115">Sombreador estándar en MRTK para Unity</span><span class="sxs-lookup"><span data-stu-id="efb7a-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="efb7a-116">MRTK: sombreador estándar</span><span class="sxs-lookup"><span data-stu-id="efb7a-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shader.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="efb7a-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="efb7a-117">See also</span></span>

* [<span data-ttu-id="efb7a-118">Cursores</span><span class="sxs-lookup"><span data-stu-id="efb7a-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="efb7a-119">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="efb7a-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="efb7a-120">Botón</span><span class="sxs-lookup"><span data-stu-id="efb7a-120">Button</span></span>](button.md)
* [<span data-ttu-id="efb7a-121">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="efb7a-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="efb7a-122">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="efb7a-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="efb7a-123">Manipulación</span><span class="sxs-lookup"><span data-stu-id="efb7a-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="efb7a-124">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="efb7a-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="efb7a-125">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="efb7a-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="efb7a-126">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="efb7a-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="efb7a-127">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="efb7a-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="efb7a-128">Teclado</span><span class="sxs-lookup"><span data-stu-id="efb7a-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="efb7a-129">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="efb7a-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="efb7a-130">Claqueta</span><span class="sxs-lookup"><span data-stu-id="efb7a-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="efb7a-131">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="efb7a-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="efb7a-132">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="efb7a-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="efb7a-133">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="efb7a-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="efb7a-134">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="efb7a-134">Surface magnetism</span></span>](surface-magnetism.md)
