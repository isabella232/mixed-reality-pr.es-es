---
title: Escenas de iluminación del sistema de escenas
description: Documentación sobre la iluminación en la escena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144417"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="b2cf3-104">Operaciones de escena de iluminación</span><span class="sxs-lookup"><span data-stu-id="b2cf3-104">Lighting scene operations</span></span>

<span data-ttu-id="b2cf3-105">La escena de iluminación predeterminada definida en el perfil se carga al iniciarse.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="b2cf3-106">Esa escena de iluminación permanece cargada hasta `SetLightingScene` que se llama a .</span><span class="sxs-lookup"><span data-stu-id="b2cf3-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="b2cf3-107">Transiciones de configuración de iluminación</span><span class="sxs-lookup"><span data-stu-id="b2cf3-107">Lighting setting transitions</span></span>

<span data-ttu-id="b2cf3-108">`transitionType` controla el estilo de la transición a una nueva escena de iluminación.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="b2cf3-109">Los estilos disponibles son:</span><span class="sxs-lookup"><span data-stu-id="b2cf3-109">The available styles are:</span></span>

<span data-ttu-id="b2cf3-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="b2cf3-110">Type</span></span> | <span data-ttu-id="b2cf3-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="b2cf3-111">Description</span></span> | <span data-ttu-id="b2cf3-112">Duration</span><span class="sxs-lookup"><span data-stu-id="b2cf3-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="b2cf3-113">Ninguno</span><span class="sxs-lookup"><span data-stu-id="b2cf3-113">None</span></span> | <span data-ttu-id="b2cf3-114">Se descarga la escena de iluminación anterior, se carga una nueva escena de iluminación.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="b2cf3-115">Sin transición.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-115">No transition.</span></span> | <span data-ttu-id="b2cf3-116">Omitido</span><span class="sxs-lookup"><span data-stu-id="b2cf3-116">Ignored</span></span>
<span data-ttu-id="b2cf3-117">Fadetoblack</span><span class="sxs-lookup"><span data-stu-id="b2cf3-117">FadeToBlack</span></span> | <span data-ttu-id="b2cf3-118">La escena de iluminación anterior se atenua a negro.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="b2cf3-119">Se carga una nueva escena de iluminación y, a continuación, se desvanece de negro.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="b2cf3-120">Resulta útil para realizar transiciones fluidas entre ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="b2cf3-121">Utilizado</span><span class="sxs-lookup"><span data-stu-id="b2cf3-121">Used</span></span>
<span data-ttu-id="b2cf3-122">Crossfade</span><span class="sxs-lookup"><span data-stu-id="b2cf3-122">CrossFade</span></span> | <span data-ttu-id="b2cf3-123">La escena de iluminación anterior se desvanece a medida que se desvanece la nueva escena de iluminación.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="b2cf3-124">Resulta útil para realizar transiciones fluidas entre las configuraciones de iluminación en la misma ubicación.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="b2cf3-125">Utilizado</span><span class="sxs-lookup"><span data-stu-id="b2cf3-125">Used</span></span>

<span data-ttu-id="b2cf3-126">Tenga en cuenta que algunas configuraciones de iluminación no se pueden interpolar durante las transiciones.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="b2cf3-127">Si desea una transición visual fluida, esta configuración tendrá que mantener la coherencia entre escenas de iluminación.</span><span class="sxs-lookup"><span data-stu-id="b2cf3-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="b2cf3-128">Configuración</span><span class="sxs-lookup"><span data-stu-id="b2cf3-128">Setting</span></span> | <span data-ttu-id="b2cf3-129">Transición Smooth FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="b2cf3-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="b2cf3-130">Transición smooth crossfade</span><span class="sxs-lookup"><span data-stu-id="b2cf3-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="b2cf3-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="b2cf3-131">Skybox</span></span> | <span data-ttu-id="b2cf3-132">No</span><span class="sxs-lookup"><span data-stu-id="b2cf3-132">No</span></span> | <span data-ttu-id="b2cf3-133">No</span><span class="sxs-lookup"><span data-stu-id="b2cf3-133">No</span></span>
<span data-ttu-id="b2cf3-134">Reflexión personalizada</span><span class="sxs-lookup"><span data-stu-id="b2cf3-134">Custom Reflections</span></span> | <span data-ttu-id="b2cf3-135">No</span><span class="sxs-lookup"><span data-stu-id="b2cf3-135">No</span></span> | <span data-ttu-id="b2cf3-136">No</span><span class="sxs-lookup"><span data-stu-id="b2cf3-136">No</span></span>
<span data-ttu-id="b2cf3-137">Sombras en tiempo real de luz solar</span><span class="sxs-lookup"><span data-stu-id="b2cf3-137">Sun light realtime shadows</span></span> | <span data-ttu-id="b2cf3-138">Sí</span><span class="sxs-lookup"><span data-stu-id="b2cf3-138">Yes</span></span> | <span data-ttu-id="b2cf3-139">No</span><span class="sxs-lookup"><span data-stu-id="b2cf3-139">No</span></span>
