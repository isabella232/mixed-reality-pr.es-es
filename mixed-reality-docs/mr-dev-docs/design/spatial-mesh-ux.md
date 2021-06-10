---
title: Visualización de malla espacial
description: Obtenga información sobre las directrices de diseño y la comprensión del entorno físico con la visualización de malla espacial en MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality, HoloLens, controles de interfaz de usuario, interacción, ui, ux, UX Design, spatial UI, spatial interaction, 3D UI, 3D UX, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600634"
---
# <a name="spatial-mesh"></a><span data-ttu-id="66b35-104">Malla espacial</span><span class="sxs-lookup"><span data-stu-id="66b35-104">Spatial mesh</span></span>

![Malla espacial](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="66b35-106">Los usuarios aprenden cómo un dispositivo percibe y entiende el entorno físico a través de la visualización de malla espacial.</span><span class="sxs-lookup"><span data-stu-id="66b35-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="66b35-107">La visualización adecuada de la malla espacial puede crear una experiencia atractiva y mágica a la vez que proporciona contexto espacial.</span><span class="sxs-lookup"><span data-stu-id="66b35-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="66b35-108">Guía de diseño</span><span class="sxs-lookup"><span data-stu-id="66b35-108">Design guideline</span></span>

<span data-ttu-id="66b35-109">Es importante permitir que el usuario se centre e interactúe con el contenido.</span><span class="sxs-lookup"><span data-stu-id="66b35-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="66b35-110">La visualización continua de la malla espacial en segundo plano puede distraer.</span><span class="sxs-lookup"><span data-stu-id="66b35-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="66b35-111">Se recomienda visualizar el entorno con moderación, ya sea solo una vez en el lanzamiento inicial o cuando el usuario muestre claramente que quiere ver la malla ambiental mediante el destino y el espacio de pulsación en el aire.</span><span class="sxs-lookup"><span data-stu-id="66b35-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="66b35-112">Puede observar este comportamiento en el Portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="66b35-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="66b35-113">Visualización de malla espacial en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="66b35-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="66b35-114">MRTK proporciona varios materiales para la visualización de malla espacial.</span><span class="sxs-lookup"><span data-stu-id="66b35-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="66b35-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat:** material de malla espacial estático predeterminado, que muestra los contornos de la malla sin animación.</span><span class="sxs-lookup"><span data-stu-id="66b35-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="66b35-116">Este material es útil para la depuración, ya que muestra todas las geometrías de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="66b35-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="66b35-117">Sin embargo, no se recomienda para producción.</span><span class="sxs-lookup"><span data-stu-id="66b35-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="66b35-118">**MRTK_SurfaceReconstruction.mat:** este material proporciona un efecto de pulso animado en la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="66b35-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="66b35-119">Puede usar este material para visualizar el entorno en un momento específico o en la entrada de pulsación en el aire del usuario.</span><span class="sxs-lookup"><span data-stu-id="66b35-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="66b35-120">Consulte **la escena pulseShaderExamples.unity** para ver los ejemplos.</span><span class="sxs-lookup"><span data-stu-id="66b35-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* <span data-ttu-id="66b35-121">Para obtener más información, [vea MRTK - Spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) y [MRTK - Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span><span class="sxs-lookup"><span data-stu-id="66b35-121">For more information, see [MRTK - Spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) and [MRTK - Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="66b35-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="66b35-122">See also</span></span>

* [<span data-ttu-id="66b35-123">Cursores</span><span class="sxs-lookup"><span data-stu-id="66b35-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="66b35-124">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="66b35-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="66b35-125">Botón</span><span class="sxs-lookup"><span data-stu-id="66b35-125">Button</span></span>](button.md)
* [<span data-ttu-id="66b35-126">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="66b35-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="66b35-127">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="66b35-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="66b35-128">Manipulación</span><span class="sxs-lookup"><span data-stu-id="66b35-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="66b35-129">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="66b35-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="66b35-130">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="66b35-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="66b35-131">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="66b35-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="66b35-132">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="66b35-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="66b35-133">Teclado</span><span class="sxs-lookup"><span data-stu-id="66b35-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="66b35-134">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="66b35-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="66b35-135">Claqueta</span><span class="sxs-lookup"><span data-stu-id="66b35-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="66b35-136">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="66b35-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="66b35-137">Sombreador</span><span class="sxs-lookup"><span data-stu-id="66b35-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="66b35-138">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="66b35-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="66b35-139">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="66b35-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="66b35-140">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="66b35-140">Surface magnetism</span></span>](surface-magnetism.md)