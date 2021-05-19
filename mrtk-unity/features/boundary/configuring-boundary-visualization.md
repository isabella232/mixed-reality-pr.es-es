---
title: Configuración de la visualización de límites
description: Detalles para configurar el sistema de límites en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema de límites,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144495"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="deee5-104">Configuración de la visualización de límites</span><span class="sxs-lookup"><span data-stu-id="deee5-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="deee5-105">El *perfil de visualización de límites* proporciona opciones para configurar la apariencia visual y otros parámetros relacionados para el sistema de límites.</span><span class="sxs-lookup"><span data-stu-id="deee5-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="deee5-106">Las visualizaciones de límites se adjuntan al Mixed Reality objeto Playspace de la escena y se teletransporta con el usuario.</span><span class="sxs-lookup"><span data-stu-id="deee5-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="deee5-107">Configuración general</span><span class="sxs-lookup"><span data-stu-id="deee5-107">General settings</span></span>

![Configuración general de visualización de límites](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="deee5-109">Alto del límite</span><span class="sxs-lookup"><span data-stu-id="deee5-109">Boundary height</span></span>

<span data-ttu-id="deee5-110">El alto del límite indica la distancia por encima del plano de suelo en el que se debe representar el límite superior.</span><span class="sxs-lookup"><span data-stu-id="deee5-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="deee5-111">El valor predeterminado es 3 metros.</span><span class="sxs-lookup"><span data-stu-id="deee5-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="deee5-112">Configuración de la planta</span><span class="sxs-lookup"><span data-stu-id="deee5-112">Floor settings</span></span>

![Configuración de la planta de visualización de límites](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="deee5-114">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="deee5-114">**Show**</span></span>

<span data-ttu-id="deee5-115">Indica si se va a crear o no un plano de suelo y agregarlo a la escena.</span><span class="sxs-lookup"><span data-stu-id="deee5-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="deee5-116">El valor predeterminado es true.</span><span class="sxs-lookup"><span data-stu-id="deee5-116">The default value is true.</span></span>

<span data-ttu-id="deee5-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="deee5-117">**Material**</span></span>

<span data-ttu-id="deee5-118">Indica el material que se debe usar al crear el plano de suelo.</span><span class="sxs-lookup"><span data-stu-id="deee5-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="deee5-119">**Escala**</span><span class="sxs-lookup"><span data-stu-id="deee5-119">**Scale**</span></span>

<span data-ttu-id="deee5-120">Indica el tamaño, en metros, del plano de suelo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="deee5-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="deee5-121">La escala predeterminada es un cuadrado de 3 x 3 metros.</span><span class="sxs-lookup"><span data-stu-id="deee5-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="deee5-122">**Capa física**</span><span class="sxs-lookup"><span data-stu-id="deee5-122">**Physics Layer**</span></span>

<span data-ttu-id="deee5-123">Capa en la que se debe establecer el plano de suelo.</span><span class="sxs-lookup"><span data-stu-id="deee5-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="deee5-124">El valor predeterminado es la *capa* Predeterminada.</span><span class="sxs-lookup"><span data-stu-id="deee5-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="deee5-125">Configuración del área de reproducción</span><span class="sxs-lookup"><span data-stu-id="deee5-125">Play area settings</span></span>

![Configuración del área de reproducción de visualización de límites](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="deee5-127">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="deee5-127">**Show**</span></span>

<span data-ttu-id="deee5-128">Indica si se crea o no un rectángulo de área de reproducción y se agrega a la escena.</span><span class="sxs-lookup"><span data-stu-id="deee5-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="deee5-129">El valor predeterminado es true.</span><span class="sxs-lookup"><span data-stu-id="deee5-129">The default value is true.</span></span>

<span data-ttu-id="deee5-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="deee5-130">**Material**</span></span>

<span data-ttu-id="deee5-131">Indica el material que se debe usar al crear el objeto de área de reproducción.</span><span class="sxs-lookup"><span data-stu-id="deee5-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="deee5-132">**Capa de física**</span><span class="sxs-lookup"><span data-stu-id="deee5-132">**Physics Layer**</span></span>

<span data-ttu-id="deee5-133">Capa en la que se debe establecer el área de juego.</span><span class="sxs-lookup"><span data-stu-id="deee5-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="deee5-134">El valor predeterminado es la *capa Omitir raycast.*</span><span class="sxs-lookup"><span data-stu-id="deee5-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="deee5-135">Configuración del área de seguimiento</span><span class="sxs-lookup"><span data-stu-id="deee5-135">Tracked area settings</span></span>

![Configuración del área de seguimiento de visualización de límites](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="deee5-137">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="deee5-137">**Show**</span></span>

<span data-ttu-id="deee5-138">Indica si se crea o no el contorno del área de seguimiento y se agrega a la escena.</span><span class="sxs-lookup"><span data-stu-id="deee5-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="deee5-139">El valor predeterminado es true.</span><span class="sxs-lookup"><span data-stu-id="deee5-139">The default value is true.</span></span>

<span data-ttu-id="deee5-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="deee5-140">**Material**</span></span>

<span data-ttu-id="deee5-141">Indica el material que se debe usar al crear el contorno del área de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="deee5-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="deee5-142">**Capa de física**</span><span class="sxs-lookup"><span data-stu-id="deee5-142">**Physics Layer**</span></span>

<span data-ttu-id="deee5-143">Capa en la que se debe establecer el área de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="deee5-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="deee5-144">El valor predeterminado es la *capa Omitir raycast.*</span><span class="sxs-lookup"><span data-stu-id="deee5-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="deee5-145">Configuración de la pared de límites</span><span class="sxs-lookup"><span data-stu-id="deee5-145">Boundary wall settings</span></span>

![Configuración de la pared de límites de visualización de límites](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="deee5-147">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="deee5-147">**Show**</span></span>

<span data-ttu-id="deee5-148">Indica si los planos de la pared de límites se van a crear y agregar a la escena.</span><span class="sxs-lookup"><span data-stu-id="deee5-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="deee5-149">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="deee5-149">The default value is false.</span></span>

<span data-ttu-id="deee5-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="deee5-150">**Material**</span></span>

<span data-ttu-id="deee5-151">Indica el material que se debe usar al crear los planos de la pared de límites.</span><span class="sxs-lookup"><span data-stu-id="deee5-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="deee5-152">**Capa de física**</span><span class="sxs-lookup"><span data-stu-id="deee5-152">**Physics Layer**</span></span>

<span data-ttu-id="deee5-153">Capa en la que se deben establecer las paredes de límite.</span><span class="sxs-lookup"><span data-stu-id="deee5-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="deee5-154">El valor predeterminado es la *capa Omitir Raycast.*</span><span class="sxs-lookup"><span data-stu-id="deee5-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="deee5-155">Establecer el componente de la pared de límites en una capa física que no sea *Omitir Raycast* puede impedir que los usuarios interactúen con objetos dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="deee5-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="deee5-156">Configuración del límite superior</span><span class="sxs-lookup"><span data-stu-id="deee5-156">Boundary ceiling settings</span></span>

![Configuración del límite de límites de visualización de límites](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="deee5-158">**Mostrar**</span><span class="sxs-lookup"><span data-stu-id="deee5-158">**Show**</span></span>

<span data-ttu-id="deee5-159">Indica si se va a crear o no un plano de límite superior y agregarlo a la escena.</span><span class="sxs-lookup"><span data-stu-id="deee5-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="deee5-160">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="deee5-160">The default value is false.</span></span>

<span data-ttu-id="deee5-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="deee5-161">**Material**</span></span>

<span data-ttu-id="deee5-162">Indica el material que se debe usar al crear el plano de límite superior.</span><span class="sxs-lookup"><span data-stu-id="deee5-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="deee5-163">**Capa de física**</span><span class="sxs-lookup"><span data-stu-id="deee5-163">**Physics Layer**</span></span>

<span data-ttu-id="deee5-164">Capa en la que se deben establecer las paredes de límite.</span><span class="sxs-lookup"><span data-stu-id="deee5-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="deee5-165">El valor predeterminado es la *capa Omitir raycast.*</span><span class="sxs-lookup"><span data-stu-id="deee5-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="deee5-166">Establecer el componente de límite superior en una capa física que no sea *Omitir Raycast* puede impedir que los usuarios interactúen con objetos dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="deee5-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="deee5-167">Consulte también</span><span class="sxs-lookup"><span data-stu-id="deee5-167">See also</span></span>

- [<span data-ttu-id="deee5-168">Documentación de la API de límites</span><span class="sxs-lookup"><span data-stu-id="deee5-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="deee5-169">Sistema  de límites</span><span class="sxs-lookup"><span data-stu-id="deee5-169">Boundary System</span></span>](boundary-system-getting-started.md)
