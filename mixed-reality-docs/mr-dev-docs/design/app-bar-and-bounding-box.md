---
title: Cuadro de límite y barra de la aplicación
description: La barra aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de la aplicación, rectángulo de selección, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 750fb238e5b7f22998a86f71607498c8f6982076
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600524"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="99383-104">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="99383-104">Bounding box and App bar</span></span>
<span data-ttu-id="99383-105">![El límite es la interfaz estándar para la manipulación de objetos en Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="99383-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="99383-106">¿Qué es el rectángulo de selección?</span><span class="sxs-lookup"><span data-stu-id="99383-106">What is the Bounding box?</span></span>

<span data-ttu-id="99383-107">El límite es la interfaz estándar para la manipulación de objetos en Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="99383-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="99383-108">Esta característica proporciona al usuario una indicación visual de que el objeto es ajustable actualmente.</span><span class="sxs-lookup"><span data-stu-id="99383-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="99383-109">En HoloLens 2, el rectángulo de selección funciona con la manipulación directa de la mano y responde a la proximidad del dedo del usuario.</span><span class="sxs-lookup"><span data-stu-id="99383-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="99383-110">Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.</span><span class="sxs-lookup"><span data-stu-id="99383-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="99383-111">Escalado de un objeto</span><span class="sxs-lookup"><span data-stu-id="99383-111">Scaling an object</span></span><br>
        <span data-ttu-id="99383-112">Las esquinas del cuadro de límite le dicen al usuario que el objeto se puede escalar.</span><span class="sxs-lookup"><span data-stu-id="99383-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="99383-113">Los identificadores siguen un patrón ampliamente comprendido para ajustar la escala.</span><span class="sxs-lookup"><span data-stu-id="99383-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="99383-114">Esta indicación visual muestra a los usuarios el área total del objeto, incluso si no está visible fuera de un modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="99383-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="99383-115">Sin esta característica, un objeto ajustado a otro objeto o superficie puede parecer que se comporta como si hubiera espacio alrededor que no debería estar ahí.</span><span class="sxs-lookup"><span data-stu-id="99383-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="99383-116">*Bucle de vídeo: Escalado de un objeto mediante el rectángulo de selección*</span><span class="sxs-lookup"><span data-stu-id="99383-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="99383-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="99383-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="99383-118">![Punto de vista de HoloLens de escalado de un objeto a través del rectángulo de selección](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="99383-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="99383-119">Rotación de un objeto</span><span class="sxs-lookup"><span data-stu-id="99383-119">Rotating an object</span></span><br>
        <span data-ttu-id="99383-120">Las asequibilidades rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación.</span><span class="sxs-lookup"><span data-stu-id="99383-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="99383-121">Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados.</span><span class="sxs-lookup"><span data-stu-id="99383-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="99383-122">No solo se pueden ajustar y escalar, sino que ahora también se giran.</span><span class="sxs-lookup"><span data-stu-id="99383-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="99383-123">*Bucle de vídeo: Rotación de un objeto a través del rectángulo de selección*</span><span class="sxs-lookup"><span data-stu-id="99383-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="99383-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="99383-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="99383-125">![Punto de vista de HoloLens de rotación de un objeto a través del rectángulo de selección](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="99383-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="99383-126">Comentarios visuales sobre la proximidad a mano en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="99383-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="99383-127">En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción de profundidad del usuario.</span><span class="sxs-lookup"><span data-stu-id="99383-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="99383-128">Un anillo cerca de su dedo se muestra hacia arriba y se escala verticalmente a medida que el dedo se acerca al objeto.</span><span class="sxs-lookup"><span data-stu-id="99383-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="99383-129">El anillo finalmente converge en un punto cuando se alcanza el estado presionado.</span><span class="sxs-lookup"><span data-stu-id="99383-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="99383-130">Esta asequibilidad visual ayuda al usuario a comprender hasta qué punto está lejos del objeto.</span><span class="sxs-lookup"><span data-stu-id="99383-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="99383-131">*Bucle de vídeo: ejemplo de comentarios visuales basados en la proximidad a un cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="99383-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="99383-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="99383-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="99383-133">![Comentarios visuales sobre proximidad a mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="99383-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="99383-134">**Para el desarrollo de aplicaciones de Unity, consulte [Rectángulo de selección en Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="99383-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="99383-135">¿Qué es la barra de aplicaciones?</span><span class="sxs-lookup"><span data-stu-id="99383-135">What is the App bar?</span></span>

<span data-ttu-id="99383-136">La barra Aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.</span><span class="sxs-lookup"><span data-stu-id="99383-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="99383-137">Este patrón se usa normalmente para permitir que los usuarios quiten y ajusten hologramas.</span><span class="sxs-lookup"><span data-stu-id="99383-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="99383-138">La barra de la aplicación se diseñó principalmente como una manera de administrar los objetos colocados en el entorno de un usuario.</span><span class="sxs-lookup"><span data-stu-id="99383-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="99383-139">Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="99383-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="99383-140">La barra de la aplicación sigue al usuario</span><span class="sxs-lookup"><span data-stu-id="99383-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="99383-141">Puesto que este patrón se usa con objetos que están bloqueados por el mundo, a medida que un usuario se mueve alrededor del objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercanos al usuario.</span><span class="sxs-lookup"><span data-stu-id="99383-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="99383-142">Aunque técnicamente no se utiliza el diseño de paneles, esta característica logra eficazmente el mismo resultado.</span><span class="sxs-lookup"><span data-stu-id="99383-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="99383-143">Impedir que la posición de un usuario occlude o bloquee la funcionalidad que, de lo contrario, estaría disponible desde una ubicación diferente en su entorno.</span><span class="sxs-lookup"><span data-stu-id="99383-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="99383-144">*Bucle de vídeo: Recorrido alrededor de un holograma, la barra de la aplicación sigue*</span><span class="sxs-lookup"><span data-stu-id="99383-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="99383-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="99383-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="99383-146">![Recorrer un holograma.</span><span class="sxs-lookup"><span data-stu-id="99383-146">![Walking around a hologram.</span></span> <span data-ttu-id="99383-147">La barra De la aplicación sigue.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="99383-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="99383-148">Cuadro de límite en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="99383-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="99383-149">**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts y requisitos previos para el cuadro de límite y la barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="99383-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="99383-150">Puede agregar un cuadro de límite asignando el script BoundingBox.cs a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="99383-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="99383-151">MRTK: rectángulo de selección</span><span class="sxs-lookup"><span data-stu-id="99383-151">MRTK - Bounding Box</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="99383-152">Vea también</span><span class="sxs-lookup"><span data-stu-id="99383-152">See also</span></span>

* [<span data-ttu-id="99383-153">Cursores</span><span class="sxs-lookup"><span data-stu-id="99383-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="99383-154">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="99383-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="99383-155">Botón</span><span class="sxs-lookup"><span data-stu-id="99383-155">Button</span></span>](button.md)
* [<span data-ttu-id="99383-156">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="99383-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="99383-157">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="99383-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="99383-158">Manipulación</span><span class="sxs-lookup"><span data-stu-id="99383-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="99383-159">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="99383-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="99383-160">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="99383-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="99383-161">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="99383-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="99383-162">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="99383-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="99383-163">Teclado</span><span class="sxs-lookup"><span data-stu-id="99383-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="99383-164">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="99383-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="99383-165">Claqueta</span><span class="sxs-lookup"><span data-stu-id="99383-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="99383-166">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="99383-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="99383-167">Sombreador</span><span class="sxs-lookup"><span data-stu-id="99383-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="99383-168">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="99383-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="99383-169">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="99383-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="99383-170">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="99383-170">Surface magnetism</span></span>](surface-magnetism.md)