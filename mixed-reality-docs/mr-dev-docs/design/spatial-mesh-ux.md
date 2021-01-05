---
title: Visualización de malla espacial
description: Obtenga información acerca de cómo los dispositivos entienden los entornos físicos mediante mallas espaciales.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidad mixta, HoloLens, controles de IU, interacción, IU, experiencia de usuario, diseño de la experiencia del usuario, interfaz de usuario espacial, interacción espacial, interfaz de usuario 3D, experiencia en 3D, auriculares
ms.openlocfilehash: ffa13da6762b803ba2a3f370308ac2af65164ecf
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848196"
---
# <a name="spatial-mesh"></a><span data-ttu-id="37b34-104">Malla espacial</span><span class="sxs-lookup"><span data-stu-id="37b34-104">Spatial mesh</span></span>

![Malla espacial](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="37b34-106">Los usuarios aprenden cómo un dispositivo percibe y comprenden el entorno físico a través de la visualización de malla espacial.</span><span class="sxs-lookup"><span data-stu-id="37b34-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="37b34-107">La visualización correcta de la malla espacial puede crear una experiencia agradables y mágica a la vez que proporciona un contexto espacial.</span><span class="sxs-lookup"><span data-stu-id="37b34-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="37b34-108">Directrices de diseño</span><span class="sxs-lookup"><span data-stu-id="37b34-108">Design guideline</span></span>

<span data-ttu-id="37b34-109">Es importante permitir que el usuario se Centre e interactúe con el contenido.</span><span class="sxs-lookup"><span data-stu-id="37b34-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="37b34-110">La visualización continua de la malla espacial en segundo plano puede distraerse.</span><span class="sxs-lookup"><span data-stu-id="37b34-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="37b34-111">Se recomienda visualizar el entorno de forma moderada, ya sea una sola vez en el inicio inicial o cuando el usuario muestra claramente que quieren ver la malla del entorno mediante el destino y el espacio de punteo aéreo.</span><span class="sxs-lookup"><span data-stu-id="37b34-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="37b34-112">Puede observar este comportamiento en el portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="37b34-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="37b34-113">Visualización de malla espacial en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="37b34-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="37b34-114">MRTK proporciona varios materiales para la visualización de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="37b34-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="37b34-115">**MRTK_Wireframe. MAT, MRTK_Wireframe. MAT**: material de malla espacial estático predeterminado, que muestra los contornos de la malla sin animación.</span><span class="sxs-lookup"><span data-stu-id="37b34-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="37b34-116">Este material es útil para la depuración, ya que muestra todas las geometrías espaciales de la malla.</span><span class="sxs-lookup"><span data-stu-id="37b34-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="37b34-117">Sin embargo, no se recomienda para la producción.</span><span class="sxs-lookup"><span data-stu-id="37b34-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="37b34-118">**MRTK_SurfaceReconstruction. MAT**: este material proporciona un efecto de pulso animado en la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="37b34-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="37b34-119">Puede usar este material para visualizar el entorno en un momento específico o en la entrada de punteo de aire del usuario.</span><span class="sxs-lookup"><span data-stu-id="37b34-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="37b34-120">Consulte **PulseShaderExamples. Unity** Scene para ver los ejemplos.</span><span class="sxs-lookup"><span data-stu-id="37b34-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="37b34-121">Para obtener más información, consulte [MRTK-Spatial awareing](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) y [MRTK-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span><span class="sxs-lookup"><span data-stu-id="37b34-121">For more information, see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="37b34-122">Consulte también</span><span class="sxs-lookup"><span data-stu-id="37b34-122">See also</span></span>

* [<span data-ttu-id="37b34-123">Cursores</span><span class="sxs-lookup"><span data-stu-id="37b34-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="37b34-124">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="37b34-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="37b34-125">Botón</span><span class="sxs-lookup"><span data-stu-id="37b34-125">Button</span></span>](button.md)
* [<span data-ttu-id="37b34-126">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="37b34-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="37b34-127">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="37b34-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="37b34-128">Manipulación</span><span class="sxs-lookup"><span data-stu-id="37b34-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="37b34-129">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="37b34-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="37b34-130">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="37b34-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="37b34-131">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="37b34-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="37b34-132">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="37b34-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="37b34-133">Teclado</span><span class="sxs-lookup"><span data-stu-id="37b34-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="37b34-134">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="37b34-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="37b34-135">Claqueta</span><span class="sxs-lookup"><span data-stu-id="37b34-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="37b34-136">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="37b34-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="37b34-137">Sombreador</span><span class="sxs-lookup"><span data-stu-id="37b34-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="37b34-138">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="37b34-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="37b34-139">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="37b34-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="37b34-140">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="37b34-140">Surface magnetism</span></span>](surface-magnetism.md)
