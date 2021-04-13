---
title: Indicación del progreso
description: Obtenga información sobre cómo los controles de progreso proporcionan comentarios al usuario de que se está llevando a cabo una operación de ejecución prolongada en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, IU, experiencia de usuario, indicador de progreso, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: e949d8805446429d3853a3fedb1b776c50c710dd
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299740"
---
# <a name="progress-indicator"></a><span data-ttu-id="bb43e-104">Indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="bb43e-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="bb43e-105">Un control de progreso proporciona comentarios de que se está llevando a cabo una operación de ejecución prolongada.</span><span class="sxs-lookup"><span data-stu-id="bb43e-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="bb43e-106">Cuando un indicador de progreso está visible, los usuarios pueden ver el tiempo de espera y no pueden interactuar con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bb43e-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="bb43e-107">Tipos de progreso</span><span class="sxs-lookup"><span data-stu-id="bb43e-107">Types of progress</span></span>

<span data-ttu-id="bb43e-108">Es importante proporcionar información de usuario sobre lo que está ocurriendo.</span><span class="sxs-lookup"><span data-stu-id="bb43e-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="bb43e-109">En realidad mixta, los usuarios pueden distraerse fácilmente por el entorno físico u objetos si la aplicación no tiene buenos comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="bb43e-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="bb43e-110">En situaciones en las que se tardan unos segundos, como cuando se cargan los datos o se actualiza una escena, es una buena idea mostrar un indicador visual.</span><span class="sxs-lookup"><span data-stu-id="bb43e-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="bb43e-111">Hay dos opciones para mostrar el usuario que está realizando una operación: una **barra de progreso** o un **anillo de progreso**.</span><span class="sxs-lookup"><span data-stu-id="bb43e-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="bb43e-112">Barra de progreso</span><span class="sxs-lookup"><span data-stu-id="bb43e-112">Progress bar</span></span><br>
        <span data-ttu-id="bb43e-113">Una barra de progreso muestra el porcentaje completado de una tarea.</span><span class="sxs-lookup"><span data-stu-id="bb43e-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="bb43e-114">Se debe usar durante una operación cuya duración se conoce (determinan), pero su progreso no debe bloquear la interacción del usuario con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bb43e-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="bb43e-115">*Imagen: ejemplo de barra de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="bb43e-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="bb43e-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="bb43e-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="bb43e-117">![Ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="bb43e-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="bb43e-118">Círculo de progreso</span><span class="sxs-lookup"><span data-stu-id="bb43e-118">Progress ring</span></span><br>
        <span data-ttu-id="bb43e-119">Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea la interacción del usuario hasta que se haya completado la operación.</span><span class="sxs-lookup"><span data-stu-id="bb43e-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="bb43e-120">*Imagen: ejemplo de anillo de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="bb43e-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="bb43e-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="bb43e-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="bb43e-122">![Ejemplo de anillo de progreso en el dispositivo HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="bb43e-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="bb43e-123">Progreso con un objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="bb43e-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="bb43e-124">Puede Agregar a la identidad de personalidad y marca de la aplicación personalizando el control de progreso con sus propios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="bb43e-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="bb43e-125">*Imagen: progreso con el ejemplo de malla personalizada en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="bb43e-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="bb43e-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="bb43e-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="bb43e-127">![Progreso con el ejemplo de malla personalizada en HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="bb43e-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="bb43e-128">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="bb43e-128">Best practices</span></span>

* <span data-ttu-id="bb43e-129">Encadenar estrechamente la [cartelera o etiqueta, junto](billboarding-and-tag-along.md) con la presentación de progreso, ya que el usuario puede trasladar fácilmente el encabezado a un espacio vacío y perder el contexto.</span><span class="sxs-lookup"><span data-stu-id="bb43e-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="bb43e-130">La aplicación podría parecerse a que se ha bloqueado si el usuario no puede ver nada.</span><span class="sxs-lookup"><span data-stu-id="bb43e-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="bb43e-131">La cartelera y el etiquetado están integrados en el recurso prefabricado de progreso.</span><span class="sxs-lookup"><span data-stu-id="bb43e-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="bb43e-132">Siempre es conveniente proporcionar información de estado sobre lo que está ocurriendo al usuario.</span><span class="sxs-lookup"><span data-stu-id="bb43e-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="bb43e-133">El recurso prefabricado de progreso proporciona varios estilos visuales, incluido el progreso de tipo anillo estándar de Windows para proporcionar el estado.</span><span class="sxs-lookup"><span data-stu-id="bb43e-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="bb43e-134">También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bb43e-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="bb43e-135">Indicador de progreso en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="bb43e-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="bb43e-136">MRTK: indicador de progreso Prefabs</span><span class="sxs-lookup"><span data-stu-id="bb43e-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="bb43e-137">MRTK: servicio de transición de escenas</span><span class="sxs-lookup"><span data-stu-id="bb43e-137">MRTK - Scene transition service</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a><span data-ttu-id="bb43e-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bb43e-138">See also</span></span>

* [<span data-ttu-id="bb43e-139">Cursores</span><span class="sxs-lookup"><span data-stu-id="bb43e-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="bb43e-140">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="bb43e-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="bb43e-141">Botón</span><span class="sxs-lookup"><span data-stu-id="bb43e-141">Button</span></span>](button.md)
* [<span data-ttu-id="bb43e-142">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="bb43e-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bb43e-143">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="bb43e-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="bb43e-144">Manipulación</span><span class="sxs-lookup"><span data-stu-id="bb43e-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bb43e-145">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="bb43e-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="bb43e-146">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="bb43e-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="bb43e-147">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="bb43e-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="bb43e-148">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="bb43e-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="bb43e-149">Teclado</span><span class="sxs-lookup"><span data-stu-id="bb43e-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="bb43e-150">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="bb43e-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="bb43e-151">Claqueta</span><span class="sxs-lookup"><span data-stu-id="bb43e-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="bb43e-152">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="bb43e-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="bb43e-153">Sombreador</span><span class="sxs-lookup"><span data-stu-id="bb43e-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="bb43e-154">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="bb43e-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="bb43e-155">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="bb43e-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="bb43e-156">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="bb43e-156">Surface magnetism</span></span>](surface-magnetism.md)
