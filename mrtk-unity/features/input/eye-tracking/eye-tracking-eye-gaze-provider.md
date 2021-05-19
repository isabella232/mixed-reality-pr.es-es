---
title: Proveedor de ojo de seguimiento ocular
description: Documentación del proveedor de Mirada con los ojos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144028"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="6a9dc-104">Acceso a los datos de seguimiento de los ojos en el script de Unity</span><span class="sxs-lookup"><span data-stu-id="6a9dc-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="6a9dc-105">En este artículo se da por supuesto que uno tiene conocimientos para configurar el seguimiento de los ojos en una escena de MRTK (consulte Configuración básica de [MRTK para usar el seguimiento de los ojos).](eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="6a9dc-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="6a9dc-106">El acceso a los datos de seguimiento de los ojos en un script MonoBehaviour es fácil.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="6a9dc-107">Simplemente use *CoreServices.InputSystem.EyeGazeProvider.*</span><span class="sxs-lookup"><span data-stu-id="6a9dc-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="6a9dc-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="6a9dc-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="6a9dc-109">La configuración de seguimiento de los ojos en MRTK se configura a través de la [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaz .</span><span class="sxs-lookup"><span data-stu-id="6a9dc-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="6a9dc-110">El [uso de CoreServices.InputSystem.EyeGazeProvider proporciona](eye-tracking-eye-gaze-provider.md) la implementación predeterminada del proveedor de mirada registrada en el kit de herramientas en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="6a9dc-111">A continuación se `EyeGazeProvider` describen las propiedades útiles de .</span><span class="sxs-lookup"><span data-stu-id="6a9dc-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="6a9dc-112">**IsEyeTrackingEnabled:** true si el usuario ha seleccionado usar el seguimiento de los ojos para la mirada.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="6a9dc-113">**IsEyeEyebrationValid:** indica si la calibración del seguimiento de los ojos del usuario es válida o no.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="6a9dc-114">Devuelve "null", si el valor aún no ha recibido datos del sistema de seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="6a9dc-115">Puede no ser válido, porque el usuario omitió la calibración del seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="6a9dc-116">**IsEyeTrackingEnabledAndValid:** indica si los datos de seguimiento de los ojos actuales se usan actualmente para la mirada.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="6a9dc-117">**IsEyeTrackingDataValid:** true si hay datos de seguimiento de los ojos disponibles.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="6a9dc-118">Puede que no esté disponible debido a que se ha superado el tiempo de espera (debe ser sólido para que el usuario parpadee) o a la falta de hardware o permisos de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="6a9dc-119">Consulte nuestro ejemplo [de notificación falta de](eye-tracking-is-user-calibrated.md) calibración de los ojos que explica cómo detectar si un usuario está calibrado con los ojos y mostrar una notificación adecuada.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="6a9dc-120">**GazeOrigin:** origen del rayo de mirada.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="6a9dc-121">Tenga en cuenta que esto devolverá el origen *de* la mirada con la cabeza si "IsEyeGazeValid" es false.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="6a9dc-122">**GazeDirection:** dirección del rayo de mirada.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="6a9dc-123">Esto devolverá la dirección *de la* mirada con la cabeza si "IsEyeGazeValid" es false.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="6a9dc-124">**HitInfo,** **HitPosition,** **HitNormal,** etc.: información sobre el objetivo que se mira actualmente.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="6a9dc-125">De nuevo, si es false, esto se basará en la mirada con la `IsEyeGazeValid` *cabeza del* usuario.</span><span class="sxs-lookup"><span data-stu-id="6a9dc-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="6a9dc-126">Ejemplos de uso de CoreServices.InputSystem.EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="6a9dc-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="6a9dc-127">Este es un ejemplo de [FollowEyeGaze.cs:](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)</span><span class="sxs-lookup"><span data-stu-id="6a9dc-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="6a9dc-128">Obtenga el punto de un holograma que el usuario está observando:</span><span class="sxs-lookup"><span data-stu-id="6a9dc-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="6a9dc-129">Mostrar un recurso visual a una distancia fija desde donde el usuario está buscando actualmente:</span><span class="sxs-lookup"><span data-stu-id="6a9dc-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="6a9dc-130">Consulte también</span><span class="sxs-lookup"><span data-stu-id="6a9dc-130">See also</span></span>

- [<span data-ttu-id="6a9dc-131">Información general sobre el seguimiento de los ojos de MRTK</span><span class="sxs-lookup"><span data-stu-id="6a9dc-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="6a9dc-132">Configuración del seguimiento de los ojos de MRTK</span><span class="sxs-lookup"><span data-stu-id="6a9dc-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="6a9dc-133">Calibración del seguimiento ocular de MRTK</span><span class="sxs-lookup"><span data-stu-id="6a9dc-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="6a9dc-134">HoloLens 2 de seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="6a9dc-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)