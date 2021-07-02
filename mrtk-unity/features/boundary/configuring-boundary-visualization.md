---
title: Configuración de la visualización de límites
description: Detalles para configurar el sistema de límites en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema de límites,
ms.openlocfilehash: 77bdaedb60700bac27643ae718c795c02e5ee7e7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177094"
---
# <a name="configuring-boundary-visualization"></a><span data-ttu-id="97c29-104">Configuración de la visualización de límites</span><span class="sxs-lookup"><span data-stu-id="97c29-104">Configuring boundary visualization</span></span>

<span data-ttu-id="97c29-105">El *perfil de visualización de límites* proporciona opciones para configurar la apariencia visual y otros parámetros relacionados para el sistema de límites.</span><span class="sxs-lookup"><span data-stu-id="97c29-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="97c29-106">Las visualizaciones de límites se adjuntan al Mixed Reality objeto Playspace de la escena y se teletransporta con el usuario.</span><span class="sxs-lookup"><span data-stu-id="97c29-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="97c29-107">Configuración general</span><span class="sxs-lookup"><span data-stu-id="97c29-107">General settings</span></span>

![Visualización general de límites Configuración](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="97c29-109">Alto del límite</span><span class="sxs-lookup"><span data-stu-id="97c29-109">Boundary height</span></span>

<span data-ttu-id="97c29-110">El alto del límite indica la distancia por encima del plano de suelo en el que se debe representar el límite superior.</span><span class="sxs-lookup"><span data-stu-id="97c29-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="97c29-111">El valor predeterminado es 3 metros.</span><span class="sxs-lookup"><span data-stu-id="97c29-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="97c29-112">Configuración de la planta</span><span class="sxs-lookup"><span data-stu-id="97c29-112">Floor settings</span></span>

![Zona de visualización de límites Configuración](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="97c29-114">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="97c29-114">**Show**</span></span>

<span data-ttu-id="97c29-115">Indica si se va a crear o no un plano de suelo y agregarlo a la escena.</span><span class="sxs-lookup"><span data-stu-id="97c29-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="97c29-116">El valor predeterminado es true.</span><span class="sxs-lookup"><span data-stu-id="97c29-116">The default value is true.</span></span>

<span data-ttu-id="97c29-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="97c29-117">**Material**</span></span>

<span data-ttu-id="97c29-118">Indica el material que se debe usar al crear el plano de suelo.</span><span class="sxs-lookup"><span data-stu-id="97c29-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="97c29-119">**Escala**</span><span class="sxs-lookup"><span data-stu-id="97c29-119">**Scale**</span></span>

<span data-ttu-id="97c29-120">Indica el tamaño, en metros, del plano de suelo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="97c29-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="97c29-121">La escala predeterminada es un cuadrado de 3 x 3 metros.</span><span class="sxs-lookup"><span data-stu-id="97c29-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="97c29-122">**Capa física**</span><span class="sxs-lookup"><span data-stu-id="97c29-122">**Physics Layer**</span></span>

<span data-ttu-id="97c29-123">Capa en la que se debe establecer el plano de suelo.</span><span class="sxs-lookup"><span data-stu-id="97c29-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="97c29-124">El valor predeterminado es la *capa* Predeterminada.</span><span class="sxs-lookup"><span data-stu-id="97c29-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="97c29-125">Configuración del área de reproducción</span><span class="sxs-lookup"><span data-stu-id="97c29-125">Play area settings</span></span>

![Área de reproducción de visualización de límites Configuración](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="97c29-127">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="97c29-127">**Show**</span></span>

<span data-ttu-id="97c29-128">Indica si se crea o no un rectángulo de área de reproducción y se agrega a la escena.</span><span class="sxs-lookup"><span data-stu-id="97c29-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="97c29-129">El valor predeterminado es true.</span><span class="sxs-lookup"><span data-stu-id="97c29-129">The default value is true.</span></span>

<span data-ttu-id="97c29-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="97c29-130">**Material**</span></span>

<span data-ttu-id="97c29-131">Indica el material que se debe usar al crear el objeto de área de reproducción.</span><span class="sxs-lookup"><span data-stu-id="97c29-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="97c29-132">**Capa física**</span><span class="sxs-lookup"><span data-stu-id="97c29-132">**Physics Layer**</span></span>

<span data-ttu-id="97c29-133">Capa en la que se debe establecer el área de juego.</span><span class="sxs-lookup"><span data-stu-id="97c29-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="97c29-134">El valor predeterminado es la *capa Omitir raycast.*</span><span class="sxs-lookup"><span data-stu-id="97c29-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="97c29-135">Configuración del área de seguimiento</span><span class="sxs-lookup"><span data-stu-id="97c29-135">Tracked area settings</span></span>

![Área de seguimiento de visualización de límites Configuración](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="97c29-137">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="97c29-137">**Show**</span></span>

<span data-ttu-id="97c29-138">Indica si se crea o no el contorno del área de seguimiento y se agrega a la escena.</span><span class="sxs-lookup"><span data-stu-id="97c29-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="97c29-139">El valor predeterminado es true.</span><span class="sxs-lookup"><span data-stu-id="97c29-139">The default value is true.</span></span>

<span data-ttu-id="97c29-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="97c29-140">**Material**</span></span>

<span data-ttu-id="97c29-141">Indica el material que se debe usar al crear el contorno del área de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="97c29-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="97c29-142">**Capa física**</span><span class="sxs-lookup"><span data-stu-id="97c29-142">**Physics Layer**</span></span>

<span data-ttu-id="97c29-143">Capa en la que se debe establecer el área de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="97c29-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="97c29-144">El valor predeterminado es la *capa Omitir raycast.*</span><span class="sxs-lookup"><span data-stu-id="97c29-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="97c29-145">Configuración de la pared de límites</span><span class="sxs-lookup"><span data-stu-id="97c29-145">Boundary wall settings</span></span>

![Límites de la visualización de límites Configuración](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="97c29-147">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="97c29-147">**Show**</span></span>

<span data-ttu-id="97c29-148">Indica si los planos de la pared de límites se van a crear y agregar a la escena.</span><span class="sxs-lookup"><span data-stu-id="97c29-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="97c29-149">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="97c29-149">The default value is false.</span></span>

<span data-ttu-id="97c29-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="97c29-150">**Material**</span></span>

<span data-ttu-id="97c29-151">Indica el material que se debe usar al crear los planos de la pared de límites.</span><span class="sxs-lookup"><span data-stu-id="97c29-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="97c29-152">**Capa física**</span><span class="sxs-lookup"><span data-stu-id="97c29-152">**Physics Layer**</span></span>

<span data-ttu-id="97c29-153">Capa en la que se deben establecer las paredes de límite.</span><span class="sxs-lookup"><span data-stu-id="97c29-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="97c29-154">El valor predeterminado es la *capa Omitir raycast.*</span><span class="sxs-lookup"><span data-stu-id="97c29-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="97c29-155">Establecer el componente de la pared de límites en una capa física que no sea *Ignore Raycast* puede impedir que los usuarios interactúen con objetos dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="97c29-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="97c29-156">Configuración del límite superior</span><span class="sxs-lookup"><span data-stu-id="97c29-156">Boundary ceiling settings</span></span>

![Límite de límites de visualización de límites Configuración](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="97c29-158">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="97c29-158">**Show**</span></span>

<span data-ttu-id="97c29-159">Indica si se va a crear o no un plano de límite superior y agregarlo a la escena.</span><span class="sxs-lookup"><span data-stu-id="97c29-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="97c29-160">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="97c29-160">The default value is false.</span></span>

<span data-ttu-id="97c29-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="97c29-161">**Material**</span></span>

<span data-ttu-id="97c29-162">Indica el material que se debe usar al crear el plano de límite superior.</span><span class="sxs-lookup"><span data-stu-id="97c29-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="97c29-163">**Capa física**</span><span class="sxs-lookup"><span data-stu-id="97c29-163">**Physics Layer**</span></span>

<span data-ttu-id="97c29-164">Capa en la que se deben establecer las paredes de límite.</span><span class="sxs-lookup"><span data-stu-id="97c29-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="97c29-165">El valor predeterminado es la *capa Omitir raycast.*</span><span class="sxs-lookup"><span data-stu-id="97c29-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="97c29-166">Establecer el componente de límite superior en una capa física que no sea *Ignore Raycast* puede impedir que los usuarios interactúen con objetos dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="97c29-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="97c29-167">Consulte también</span><span class="sxs-lookup"><span data-stu-id="97c29-167">See also</span></span>

- [<span data-ttu-id="97c29-168">Documentación de la API de límites</span><span class="sxs-lookup"><span data-stu-id="97c29-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="97c29-169">Sistema  de límites</span><span class="sxs-lookup"><span data-stu-id="97c29-169">Boundary System</span></span>](boundary-system-getting-started.md)
