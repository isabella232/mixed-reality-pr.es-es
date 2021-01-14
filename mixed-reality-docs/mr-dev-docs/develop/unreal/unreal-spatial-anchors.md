---
title: Anclajes espaciales locales en Unreal
description: Aprenda a usar, guardar y administrar delimitadores espaciales en aplicaciones de realidad mixta de Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: d44610ea0632dbc93941096007e60e4ae7be53e1
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009985"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="38461-104">Anclajes espaciales locales en Unreal</span><span class="sxs-lookup"><span data-stu-id="38461-104">Local Spatial Anchors in Unreal</span></span>

<span data-ttu-id="38461-105">Los anclajes espaciales sirven para guardar los hologramas en el espacio del mundo real entre sesiones de aplicación como **ARPin**.</span><span class="sxs-lookup"><span data-stu-id="38461-105">Spatial anchors save holograms in real-world space between application sessions as **ARPin** s.</span></span> <span data-ttu-id="38461-106">Una vez guardados en el almacén de anclajes de HoloLens,los ARPin se pueden cargar en futuras sesiones y es una opción de reserva ideal cuando no hay conectividad a Internet.</span><span class="sxs-lookup"><span data-stu-id="38461-106">Once saved in the HoloLens' anchor store, ARPin's can be loaded in future sessions and are an ideal fallback option when there's no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="38461-107">Las funciones de anclaje de UE 4.25 han quedado obsoletas en la versión 4.26 y deben reemplazarse por otras más recientes.</span><span class="sxs-lookup"><span data-stu-id="38461-107">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="38461-108">Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube.</span><span class="sxs-lookup"><span data-stu-id="38461-108">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="38461-109">Si desea usar servicios en la nube de Azure para almacenar los anclajes, existe un documento que le guiará por la integración de [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="38461-109">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="38461-110">Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.</span><span class="sxs-lookup"><span data-stu-id="38461-110">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="38461-111">Comprobación del almacén de anclajes</span><span class="sxs-lookup"><span data-stu-id="38461-111">Checking the anchor store</span></span>

<span data-ttu-id="38461-112">Antes de guardar o cargar anclajes, debe comprobar si el almacén de anclajes está listo.</span><span class="sxs-lookup"><span data-stu-id="38461-112">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="38461-113">Si se llama a cualquiera de las funciones de anclaje de HoloLens antes de que el almacén de anclajes esté listo, la llamada no se completará correctamente.</span><span class="sxs-lookup"><span data-stu-id="38461-113">Calling any of the HoloLens anchor functions before the anchor store is ready won't succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="38461-114">Guardar anclajes</span><span class="sxs-lookup"><span data-stu-id="38461-114">Saving anchors</span></span>

<span data-ttu-id="38461-115">Cuando la aplicación tenga un componente que se necesite anclar en el mundo, se puede guardar en el almacén de anclajes con la siguiente secuencia:</span><span class="sxs-lookup"><span data-stu-id="38461-115">Once the application has a component you need to pin to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="38461-116">Desglose:</span><span class="sxs-lookup"><span data-stu-id="38461-116">Breaking this down:</span></span>
1. <span data-ttu-id="38461-117">Genere un actor en una ubicación conocida.</span><span class="sxs-lookup"><span data-stu-id="38461-117">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="38461-118">Cree un elemento **ARPin** con esa ubicación y un nombre basado en la clase del actor.</span><span class="sxs-lookup"><span data-stu-id="38461-118">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="38461-119">Agregue el actor al elemento **ARPin** y guarde el marcador en el almacén de anclajes de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38461-119">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="38461-120">El nombre del anclaje que elija debe ser único, en este ejemplo, es la marca de tiempo actual.</span><span class="sxs-lookup"><span data-stu-id="38461-120">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="38461-121">Si el anclaje se guarda correctamente en el almacén de anclajes, se puede establecer en el portal de dispositivos de HoloLens en **Sistema > Administrador de mapas > Archivos de anclajes guardados en el dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="38461-121">If the anchor is successfully saved to the anchor store, you can see it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="38461-122">Carga de anclajes</span><span class="sxs-lookup"><span data-stu-id="38461-122">Loading anchors</span></span>

<span data-ttu-id="38461-123">Cuando se inicia una aplicación, se puede usar el siguiente plano técnico para restaurar los componentes en sus ubicaciones de anclaje:</span><span class="sxs-lookup"><span data-stu-id="38461-123">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="38461-124">Desglose:</span><span class="sxs-lookup"><span data-stu-id="38461-124">Breaking this down:</span></span>
1. <span data-ttu-id="38461-125">Recorra en iteración todos los anclajes del almacén de anclajes.</span><span class="sxs-lookup"><span data-stu-id="38461-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="38461-126">Genere un actor en la identidad.</span><span class="sxs-lookup"><span data-stu-id="38461-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="38461-127">Marque ese actor en **ARPin** en el almacén de anclajes.</span><span class="sxs-lookup"><span data-stu-id="38461-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="38461-128">Es importante generar el actor en la identidad, ya que el anclaje es responsable de cambiar la posición del holograma en el mundo en función de dónde se guardó.</span><span class="sxs-lookup"><span data-stu-id="38461-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="38461-129">Cualquier transformación que se proporcione aquí agregará un desplazamiento al anclaje.</span><span class="sxs-lookup"><span data-stu-id="38461-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="38461-130">También se consulta el identificador del anclaje para que se puedan generar diferentes actores en función del nombre guardado del anclaje.</span><span class="sxs-lookup"><span data-stu-id="38461-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="38461-131">Eliminación de anclajes</span><span class="sxs-lookup"><span data-stu-id="38461-131">Removing anchors</span></span> 

<span data-ttu-id="38461-132">Cuando haya terminado con un anclaje, puede borrar anclajes individuales o todo el almacén de anclajes con los componentes **Quitar ARPin del almacén WMRAnchor** y **Quitar todos los ARPin del almacén WMRAnchor**.</span><span class="sxs-lookup"><span data-stu-id="38461-132">When you're done with an anchor, you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="38461-133">Tenga en cuenta que Spatial Anchors todavía están en versión beta, por lo que debe asegurarse de consultar la información y las características actualizadas.</span><span class="sxs-lookup"><span data-stu-id="38461-133">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="38461-134">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="38461-134">Next Development Checkpoint</span></span>

<span data-ttu-id="38461-135">Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="38461-135">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="38461-136">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="38461-136">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="38461-137">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="38461-137">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="38461-138">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="38461-138">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="38461-139">Cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="38461-139">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="38461-140">Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="38461-140">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="38461-141">Consulta también</span><span class="sxs-lookup"><span data-stu-id="38461-141">See also</span></span>

* [<span data-ttu-id="38461-142">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="38461-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="38461-143">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="38461-143">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="38461-144">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="38461-144">Coordinate systems</span></span>](../../design/coordinate-systems.md)
