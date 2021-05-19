---
title: Introducción al servicio de física de manos
description: documentación para usar el servicio de extensión física hand en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145088"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="cfb2e-104">Servicio de extensión física de mano</span><span class="sxs-lookup"><span data-stu-id="cfb2e-104">Hand physics extension service</span></span>

![Hand Physics Extension Service](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="cfb2e-106">El servicio de física de manos permite eventos de colisión corporal rígida e interacciones con las manos articuladas.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="cfb2e-107">Habilitación de la extensión</span><span class="sxs-lookup"><span data-stu-id="cfb2e-107">Enabling the extension</span></span>

<span data-ttu-id="cfb2e-108">Para habilitar la extensión, abra el perfil RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="cfb2e-109">Haga `Register a new Service Provider` clic para agregar una nueva configuración.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="cfb2e-110">En el campo tipo de componente, seleccione HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="cfb2e-111">En el campo Perfil de configuración, seleccione el perfil físico de mano predeterminado incluido con la extensión.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="cfb2e-112">Opciones de perfil</span><span class="sxs-lookup"><span data-stu-id="cfb2e-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="cfb2e-113">Capa de física de manos</span><span class="sxs-lookup"><span data-stu-id="cfb2e-113">Hand physics layer</span></span>

<span data-ttu-id="cfb2e-114">Controla la capa a la que irán las uniones de mano con instancias.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="cfb2e-115">Aunque el servicio tiene como valor predeterminado la capa "predeterminada" (0), se recomienda usar una capa independiente para los objetos físicos de mano.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="cfb2e-116">De lo contrario, puede haber colisiones no deseadas o raycasts inexactos.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="cfb2e-117">Prefab del cuerpo kinémático de la punta de los dedos</span><span class="sxs-lookup"><span data-stu-id="cfb2e-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="cfb2e-118">Controla qué prefab se crea una instancia al alcance de la mano.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="cfb2e-119">Para que el servicio funcione según lo previsto, el requisito previo requiere:</span><span class="sxs-lookup"><span data-stu-id="cfb2e-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="cfb2e-120">Un componente rigidbody, con isKinematic habilitado</span><span class="sxs-lookup"><span data-stu-id="cfb2e-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="cfb2e-121">Colisionador</span><span class="sxs-lookup"><span data-stu-id="cfb2e-121">A collider</span></span>
- <span data-ttu-id="cfb2e-122">Componente de `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="cfb2e-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="cfb2e-123">Uso del cuerpo kinemático de la mano</span><span class="sxs-lookup"><span data-stu-id="cfb2e-123">Use palm kinematic body</span></span>

<span data-ttu-id="cfb2e-124">Controla si el servicio intentará crear una instancia de un prefab en la unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="cfb2e-125">Prefab del cuerpo kinémático de la mano</span><span class="sxs-lookup"><span data-stu-id="cfb2e-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="cfb2e-126">Cuando `UsePalmKinematicBody` está habilitado, este es el prefab al que se va a crear una instancia.</span><span class="sxs-lookup"><span data-stu-id="cfb2e-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="cfb2e-127">Al igual `FingerTipKinematicBodyPrefab` que , este prefab requiere:</span><span class="sxs-lookup"><span data-stu-id="cfb2e-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="cfb2e-128">Un componente rigidbody, con isKinematic habilitado</span><span class="sxs-lookup"><span data-stu-id="cfb2e-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="cfb2e-129">Colisionador</span><span class="sxs-lookup"><span data-stu-id="cfb2e-129">A collider</span></span>
- <span data-ttu-id="cfb2e-130">Componente de `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="cfb2e-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="cfb2e-131">Uso del servicio</span><span class="sxs-lookup"><span data-stu-id="cfb2e-131">How to use the service</span></span>

<span data-ttu-id="cfb2e-132">Una vez habilitada, use la propiedad de cualquier colisionador para recibir eventos de colisión de los 10 dígitos (y descime si `IsTrigger` están habilitados).</span><span class="sxs-lookup"><span data-stu-id="cfb2e-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
