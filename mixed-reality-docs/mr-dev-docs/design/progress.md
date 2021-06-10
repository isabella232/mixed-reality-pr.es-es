---
title: Indicación del progreso
description: Obtenga información sobre cómo los controles de progreso proporcionan comentarios al usuario sobre la ejecución de una operación de larga duración en las aplicaciones de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, interfaz de usuario, experiencia de usuario, indicador de progreso, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600554"
---
# <a name="progress-indicator"></a><span data-ttu-id="68552-104">Indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="68552-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="68552-105">Un control de progreso proporciona comentarios sobre una operación de ejecución larga en curso.</span><span class="sxs-lookup"><span data-stu-id="68552-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="68552-106">Cuando un indicador de progreso está visible, los usuarios pueden ver el tiempo de espera y no pueden interactuar con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="68552-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="68552-107">Tipos de progreso</span><span class="sxs-lookup"><span data-stu-id="68552-107">Types of progress</span></span>

<span data-ttu-id="68552-108">Es importante proporcionar al usuario información sobre lo que sucede.</span><span class="sxs-lookup"><span data-stu-id="68552-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="68552-109">En realidad mixta, el entorno físico u los objetos pueden distraer fácilmente a los usuarios si la aplicación no tiene buenos comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="68552-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="68552-110">Para situaciones que tarden unos segundos, como cuando se cargan datos o se actualiza una escena, es una buena idea mostrar un indicador visual.</span><span class="sxs-lookup"><span data-stu-id="68552-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="68552-111">Hay dos opciones para mostrar al usuario que hay una operación en curso: una **barra de progreso** o un anillo de **progreso**.</span><span class="sxs-lookup"><span data-stu-id="68552-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="68552-112">Barra de progreso</span><span class="sxs-lookup"><span data-stu-id="68552-112">Progress bar</span></span><br>
        <span data-ttu-id="68552-113">Una barra progreso muestra el porcentaje completado de una tarea.</span><span class="sxs-lookup"><span data-stu-id="68552-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="68552-114">Debe usarse durante una operación cuya duración se conoce (determinada), pero su progreso no debe bloquear la interacción del usuario con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="68552-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="68552-115">*Imagen: Ejemplo de barra de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="68552-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68552-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68552-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68552-117">![Ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="68552-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="68552-118">Círculo de progreso</span><span class="sxs-lookup"><span data-stu-id="68552-118">Progress ring</span></span><br>
        <span data-ttu-id="68552-119">Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea la interacción del usuario hasta que se complete la operación.</span><span class="sxs-lookup"><span data-stu-id="68552-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="68552-120">*Imagen: Ejemplo de anillo de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="68552-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68552-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68552-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68552-122">![Ejemplo de anillo de progreso en un dispositivo HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="68552-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="68552-123">Progreso con un objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="68552-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="68552-124">Puede agregar a la personalidad y la identidad de marca de la aplicación personalizando el control Progreso con sus propios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="68552-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="68552-125">*Imagen: Ejemplo de progreso con malla personalizada en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="68552-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68552-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68552-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68552-127">![Ejemplo de progreso con malla personalizada en HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="68552-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="68552-128">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="68552-128">Best practices</span></span>

* <span data-ttu-id="68552-129">Ajuste estrechamente [el formato o](billboarding-and-tag-along.md) la etiqueta junto a la presentación de Progreso, ya que el usuario puede mover fácilmente la cabeza a un espacio vacío y perder el contexto.</span><span class="sxs-lookup"><span data-stu-id="68552-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="68552-130">Es posible que la aplicación parezca que se ha bloqueado si el usuario no puede ver nada.</span><span class="sxs-lookup"><span data-stu-id="68552-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="68552-131">La marcación y la etiqueta se han integrado en el prefab Progreso.</span><span class="sxs-lookup"><span data-stu-id="68552-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="68552-132">Siempre es bueno proporcionar información de estado sobre lo que sucede al usuario.</span><span class="sxs-lookup"><span data-stu-id="68552-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="68552-133">El objeto prefab Progreso proporciona varios estilos visuales, incluido el progreso de tipo de anillo estándar de Windows para proporcionar el estado.</span><span class="sxs-lookup"><span data-stu-id="68552-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="68552-134">También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="68552-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="68552-135">Indicador de progreso en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="68552-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="68552-136">MRTK: prefabs del indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="68552-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="68552-137">MRTK: servicio de transición de escena</span><span class="sxs-lookup"><span data-stu-id="68552-137">MRTK - Scene transition service</span></span>](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a><span data-ttu-id="68552-138">Vea también</span><span class="sxs-lookup"><span data-stu-id="68552-138">See also</span></span>

* [<span data-ttu-id="68552-139">Cursores</span><span class="sxs-lookup"><span data-stu-id="68552-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="68552-140">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="68552-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="68552-141">Botón</span><span class="sxs-lookup"><span data-stu-id="68552-141">Button</span></span>](button.md)
* [<span data-ttu-id="68552-142">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="68552-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="68552-143">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="68552-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="68552-144">Manipulación</span><span class="sxs-lookup"><span data-stu-id="68552-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="68552-145">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="68552-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="68552-146">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="68552-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="68552-147">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="68552-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="68552-148">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="68552-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="68552-149">Teclado</span><span class="sxs-lookup"><span data-stu-id="68552-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="68552-150">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="68552-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="68552-151">Claqueta</span><span class="sxs-lookup"><span data-stu-id="68552-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="68552-152">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="68552-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="68552-153">Sombreador</span><span class="sxs-lookup"><span data-stu-id="68552-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="68552-154">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="68552-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="68552-155">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="68552-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="68552-156">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="68552-156">Surface magnetism</span></span>](surface-magnetism.md)