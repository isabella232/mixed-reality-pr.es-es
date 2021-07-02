---
title: Detección de funcionalidades de la plataforma
description: Detalles de las distintas funcionalidades que admite MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, funcionalidades,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175527"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="3fc98-104">Detección de funcionalidades de la plataforma</span><span class="sxs-lookup"><span data-stu-id="3fc98-104">Detecting platform capabilities</span></span>

<span data-ttu-id="3fc98-105">Una pregunta común que se hace de MRTK implica saber qué dispositivo específico (por ejemplo, Microsoft HoloLens 2) se usa para ejecutar una aplicación.</span><span class="sxs-lookup"><span data-stu-id="3fc98-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="3fc98-106">Identificar el hardware exacto puede ser complicado en distintas plataformas.</span><span class="sxs-lookup"><span data-stu-id="3fc98-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="3fc98-107">En su lugar, MRTK proporciona una manera de identificar funcionalidades específicas en tiempo de ejecución (por ejemplo, si el punto de conexión del dispositivo actual admite manos articuladas).</span><span class="sxs-lookup"><span data-stu-id="3fc98-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="3fc98-108">Funciones</span><span class="sxs-lookup"><span data-stu-id="3fc98-108">Capabilities</span></span>

<span data-ttu-id="3fc98-109">El Mixed Reality Toolkit proporciona la enumeración , que define un conjunto de funcionalidades para las que una aplicación [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) puede consultar en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="3fc98-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="3fc98-110">Funcionalidades del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="3fc98-110">Input system capabilities</span></span>

<span data-ttu-id="3fc98-111">El sistema de entrada DE MRTK predeterminado admite la consulta de las siguientes funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="3fc98-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="3fc98-112">Capacidad</span><span class="sxs-lookup"><span data-stu-id="3fc98-112">Capability</span></span> | <span data-ttu-id="3fc98-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="3fc98-113">Description</span></span> |
|---|---|
| <span data-ttu-id="3fc98-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="3fc98-114">ArticulatedHand</span></span> | <span data-ttu-id="3fc98-115">Entrada de mano articulada</span><span class="sxs-lookup"><span data-stu-id="3fc98-115">Articulated hand input</span></span> |
| <span data-ttu-id="3fc98-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="3fc98-116">EyeTracking</span></span> | <span data-ttu-id="3fc98-117">Objetivo de la mirada con los ojos</span><span class="sxs-lookup"><span data-stu-id="3fc98-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="3fc98-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="3fc98-118">GGVHand</span></span> | <span data-ttu-id="3fc98-119">Entrada de la mano Gesto de mirada y voz</span><span class="sxs-lookup"><span data-stu-id="3fc98-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="3fc98-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="3fc98-120">MotionController</span></span> | <span data-ttu-id="3fc98-121">Entrada del controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="3fc98-121">Motion controller input</span></span> |
| <span data-ttu-id="3fc98-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="3fc98-122">VoiceCommand</span></span> | <span data-ttu-id="3fc98-123">Comandos de voz mediante palabras clave definidas por la aplicación</span><span class="sxs-lookup"><span data-stu-id="3fc98-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="3fc98-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="3fc98-124">VoiceDictation</span></span> | <span data-ttu-id="3fc98-125">Dictado de voz a texto</span><span class="sxs-lookup"><span data-stu-id="3fc98-125">Voice to text dictation</span></span> |

<span data-ttu-id="3fc98-126">El código de ejemplo siguiente comprueba si el sistema de entrada ha cargado un proveedor de datos con compatibilidad con las manos articuladas.</span><span class="sxs-lookup"><span data-stu-id="3fc98-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="3fc98-127">Funcionalidades de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="3fc98-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="3fc98-128">El sistema de reconocimiento espacial de MRTK predeterminado admite la consulta de las siguientes funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="3fc98-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="3fc98-129">Capacidad</span><span class="sxs-lookup"><span data-stu-id="3fc98-129">Capability</span></span> | <span data-ttu-id="3fc98-130">Descripción</span><span class="sxs-lookup"><span data-stu-id="3fc98-130">Description</span></span> |
|---|---|
| <span data-ttu-id="3fc98-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="3fc98-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="3fc98-132">Mallas espaciales</span><span class="sxs-lookup"><span data-stu-id="3fc98-132">Spatial meshes</span></span> |
| <span data-ttu-id="3fc98-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="3fc98-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="3fc98-134">Planos espaciales</span><span class="sxs-lookup"><span data-stu-id="3fc98-134">Spatial planes</span></span> |
| <span data-ttu-id="3fc98-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="3fc98-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="3fc98-136">Puntos espaciales</span><span class="sxs-lookup"><span data-stu-id="3fc98-136">Spatial points</span></span> |

<span data-ttu-id="3fc98-137">En este ejemplo se comprueba si el sistema de reconocimiento espacial ha cargado un proveedor de datos con compatibilidad con mallas espaciales.</span><span class="sxs-lookup"><span data-stu-id="3fc98-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="3fc98-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3fc98-138">See also</span></span>

- [<span data-ttu-id="3fc98-139">Documentación de la API IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="3fc98-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="3fc98-140">Documentación de la enumeración MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="3fc98-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
