---
title: Cuadro de límite y barra de la aplicación
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 0f94aa3842afbfbd544716b801c7cb88d7be3abc
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847653"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="41c25-104">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="41c25-104">Bounding box and App bar</span></span>
<span data-ttu-id="41c25-105">![El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="41c25-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="41c25-106">¿Cuál es el cuadro de límite?</span><span class="sxs-lookup"><span data-stu-id="41c25-106">What is the Bounding box?</span></span>

<span data-ttu-id="41c25-107">El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="41c25-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="41c25-108">Esta característica proporciona al usuario una indicación visual de que el objeto es ajustable actualmente.</span><span class="sxs-lookup"><span data-stu-id="41c25-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="41c25-109">En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario.</span><span class="sxs-lookup"><span data-stu-id="41c25-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="41c25-110">Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.</span><span class="sxs-lookup"><span data-stu-id="41c25-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="41c25-111">Escalado de un objeto</span><span class="sxs-lookup"><span data-stu-id="41c25-111">Scaling an object</span></span><br>
        <span data-ttu-id="41c25-112">Las esquinas del cuadro de límite indican al usuario que el objeto se puede escalar.</span><span class="sxs-lookup"><span data-stu-id="41c25-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="41c25-113">Los identificadores siguen un patrón muy entendido para ajustar la escala.</span><span class="sxs-lookup"><span data-stu-id="41c25-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="41c25-114">Esta indicación visual muestra a los usuarios el área total del objeto, aunque no sea visible fuera de un modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="41c25-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="41c25-115">Sin esta característica, es posible que un objeto ajustado a otro objeto o superficie parezca que se comporte como si hubiera espacio alrededor que no debiera estar ahí.</span><span class="sxs-lookup"><span data-stu-id="41c25-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="41c25-116">*Bucle de vídeo: escalado de un objeto a través del cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="41c25-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="41c25-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="41c25-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="41c25-118">![Punto de vista de HoloLens de escalado de un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="41c25-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="41c25-119">Girar un objeto</span><span class="sxs-lookup"><span data-stu-id="41c25-119">Rotating an object</span></span><br>
        <span data-ttu-id="41c25-120">Las prestaciones rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación.</span><span class="sxs-lookup"><span data-stu-id="41c25-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="41c25-121">Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados.</span><span class="sxs-lookup"><span data-stu-id="41c25-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="41c25-122">No solo se pueden ajustar y escalar, sino que ahora giran.</span><span class="sxs-lookup"><span data-stu-id="41c25-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="41c25-123">*Bucle de vídeo: girar un objeto a través del cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="41c25-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="41c25-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="41c25-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="41c25-125">![Punto de vista de HoloLens de girar un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="41c25-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="41c25-126">Comentarios visuales sobre la proximidad en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="41c25-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="41c25-127">En HoloLens 2, hay una indicación visual adicional, que puede ayudar a la percepción del usuario de la profundidad.</span><span class="sxs-lookup"><span data-stu-id="41c25-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="41c25-128">Se muestra un anillo cerca de su dedo y se reduce verticalmente a medida que la mano se acerca al objeto.</span><span class="sxs-lookup"><span data-stu-id="41c25-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="41c25-129">El anillo finalmente converge en un punto cuando se alcanza el estado presionado.</span><span class="sxs-lookup"><span data-stu-id="41c25-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="41c25-130">Esta prestación visual ayuda al usuario a comprender hasta qué punto proceden del objeto.</span><span class="sxs-lookup"><span data-stu-id="41c25-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="41c25-131">*Bucle de vídeo: ejemplo de comentarios visuales basados en proximidad a un cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="41c25-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="41c25-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="41c25-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="41c25-133">![Comentarios visuales en proximidad](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="41c25-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="41c25-134">**Para el desarrollo de aplicaciones de Unity, consulte [cuadro de límite en el kit de herramientas de realidad mixta (Unity).](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="41c25-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="41c25-135">¿Qué es la barra de la aplicación?</span><span class="sxs-lookup"><span data-stu-id="41c25-135">What is the App bar?</span></span>

<span data-ttu-id="41c25-136">La barra de la aplicación es un menú de nivel de objeto, que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.</span><span class="sxs-lookup"><span data-stu-id="41c25-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="41c25-137">Este patrón se usa normalmente para permitir que los usuarios quiten y ajusten los hologramas.</span><span class="sxs-lookup"><span data-stu-id="41c25-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="41c25-138">La barra de la aplicación se diseñó principalmente como una manera de administrar objetos colocados en el entorno de un usuario.</span><span class="sxs-lookup"><span data-stu-id="41c25-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="41c25-139">Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="41c25-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="41c25-140">La barra de la aplicación sigue al usuario</span><span class="sxs-lookup"><span data-stu-id="41c25-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="41c25-141">Puesto que este patrón se usa con objetos que están bloqueados por todo el mundo, a medida que un usuario se desplaza por el objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario.</span><span class="sxs-lookup"><span data-stu-id="41c25-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="41c25-142">Aunque técnicamente no se trata de una característica, esta característica consigue el mismo resultado.</span><span class="sxs-lookup"><span data-stu-id="41c25-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="41c25-143">Impedir que la posición de un usuario tapaba o bloquee la funcionalidad que, de otro modo, estará disponible desde una ubicación diferente en su entorno.</span><span class="sxs-lookup"><span data-stu-id="41c25-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="41c25-144">*Bucle de vídeo: desplazarse por un holograma, la barra de la aplicación sigue*</span><span class="sxs-lookup"><span data-stu-id="41c25-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="41c25-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="41c25-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="41c25-146">![Recorrer un holograma.</span><span class="sxs-lookup"><span data-stu-id="41c25-146">![Walking around a hologram.</span></span> <span data-ttu-id="41c25-147">A continuación se muestra la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="41c25-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="41c25-148">Cuadro de límite en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="41c25-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="41c25-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts y Prefabs para el cuadro de límite y la barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="41c25-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="41c25-150">Puede Agregar un cuadro de límite mediante la asignación del script BoundingBox.cs en cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="41c25-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="41c25-151">MRTK: cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="41c25-151">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="41c25-152">Consulte también</span><span class="sxs-lookup"><span data-stu-id="41c25-152">See also</span></span>

* [<span data-ttu-id="41c25-153">Cursores</span><span class="sxs-lookup"><span data-stu-id="41c25-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="41c25-154">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="41c25-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="41c25-155">Botón</span><span class="sxs-lookup"><span data-stu-id="41c25-155">Button</span></span>](button.md)
* [<span data-ttu-id="41c25-156">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="41c25-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="41c25-157">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="41c25-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="41c25-158">Manipulación</span><span class="sxs-lookup"><span data-stu-id="41c25-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="41c25-159">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="41c25-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="41c25-160">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="41c25-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="41c25-161">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="41c25-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="41c25-162">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="41c25-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="41c25-163">Teclado</span><span class="sxs-lookup"><span data-stu-id="41c25-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="41c25-164">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="41c25-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="41c25-165">Claqueta</span><span class="sxs-lookup"><span data-stu-id="41c25-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="41c25-166">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="41c25-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="41c25-167">Sombreador</span><span class="sxs-lookup"><span data-stu-id="41c25-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="41c25-168">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="41c25-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="41c25-169">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="41c25-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="41c25-170">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="41c25-170">Surface magnetism</span></span>](surface-magnetism.md)
