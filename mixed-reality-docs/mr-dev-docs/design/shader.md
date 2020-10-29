---
title: Sombreador
description: El sombreador estándar de MRTK proporciona varios tipos de efectos visuales que se pueden usar con hologramas.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, IU, experiencia de usuario
ms.openlocfilehash: 86e56de93736c90f3b28467a0ecd6e18a1ba0146
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691554"
---
# <a name="shader"></a><span data-ttu-id="afbe5-104">Sombreador</span><span class="sxs-lookup"><span data-stu-id="afbe5-104">Shader</span></span>

![Sombreador](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="afbe5-106">Dado que los objetos holográficas se mezclan con los físicos en el entorno real, es importante proporcionar indicaciones visuales al usuario.</span><span class="sxs-lookup"><span data-stu-id="afbe5-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="afbe5-107">El sombreador estándar de MRTK proporciona varios tipos de efectos visuales que se pueden usar con hologramas.</span><span class="sxs-lookup"><span data-stu-id="afbe5-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="afbe5-108">El sistema de sombreado estándar de MRTK emplea un sombreador único y flexible que puede lograr objetos visuales similares al sombreador estándar de Unity, implementa [principios del sistema de diseño fluida](https://www.microsoft.com/design/fluent/#/)y sigue teniendo el rendimiento de los dispositivos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="afbe5-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="afbe5-109">Ejemplos de efectos visuales con el sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="afbe5-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="afbe5-110">![Mover](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="afbe5-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="afbe5-111">**Luz de proximidad**</span><span class="sxs-lookup"><span data-stu-id="afbe5-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="afbe5-112">![Girar](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="afbe5-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="afbe5-113">**Borde claro**</span><span class="sxs-lookup"><span data-stu-id="afbe5-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="afbe5-114">Sombreador estándar de MRTK en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="afbe5-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="afbe5-115">MRTK: sombreador estándar</span><span class="sxs-lookup"><span data-stu-id="afbe5-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="afbe5-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="afbe5-116">See also</span></span>

* [<span data-ttu-id="afbe5-117">Cursores</span><span class="sxs-lookup"><span data-stu-id="afbe5-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="afbe5-118">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="afbe5-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="afbe5-119">Botón</span><span class="sxs-lookup"><span data-stu-id="afbe5-119">Button</span></span>](button.md)
* [<span data-ttu-id="afbe5-120">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="afbe5-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="afbe5-121">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="afbe5-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="afbe5-122">Manipulación</span><span class="sxs-lookup"><span data-stu-id="afbe5-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="afbe5-123">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="afbe5-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="afbe5-124">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="afbe5-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="afbe5-125">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="afbe5-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="afbe5-126">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="afbe5-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="afbe5-127">Teclado</span><span class="sxs-lookup"><span data-stu-id="afbe5-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="afbe5-128">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="afbe5-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="afbe5-129">Claqueta</span><span class="sxs-lookup"><span data-stu-id="afbe5-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="afbe5-130">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="afbe5-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="afbe5-131">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="afbe5-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="afbe5-132">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="afbe5-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="afbe5-133">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="afbe5-133">Surface magnetism</span></span>](surface-magnetism.md)
