---
title: Servicio de física de manos
description: documentación para usar el servicio de extensión hand-physics en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176253"
---
# <a name="hand-physics-service"></a><span data-ttu-id="2c605-104">Servicio de física de manos</span><span class="sxs-lookup"><span data-stu-id="2c605-104">Hand physics service</span></span>

![Hand Physics Extension Service](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="2c605-106">El servicio de física de manos permite eventos de colisión corporal rígida e interacciones con manos articuladas.</span><span class="sxs-lookup"><span data-stu-id="2c605-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="2c605-107">Habilitación de la extensión</span><span class="sxs-lookup"><span data-stu-id="2c605-107">Enabling the extension</span></span>

<span data-ttu-id="2c605-108">Para habilitar la extensión, abra el perfil registeredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="2c605-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="2c605-109">Haga `Register a new Service Provider` clic para agregar una nueva configuración.</span><span class="sxs-lookup"><span data-stu-id="2c605-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="2c605-110">En el campo tipo de componente, seleccione HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="2c605-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="2c605-111">En el campo Perfil de configuración, seleccione el perfil físico de mano predeterminado incluido con la extensión.</span><span class="sxs-lookup"><span data-stu-id="2c605-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="2c605-112">Opciones de perfil</span><span class="sxs-lookup"><span data-stu-id="2c605-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="2c605-113">Capa de física de manos</span><span class="sxs-lookup"><span data-stu-id="2c605-113">Hand physics layer</span></span>

<span data-ttu-id="2c605-114">Controla la capa a la que irán las uniones de mano con instancias.</span><span class="sxs-lookup"><span data-stu-id="2c605-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="2c605-115">Aunque el servicio tiene como valor predeterminado la capa "predeterminada" (0), se recomienda usar una capa independiente para los objetos físicos de mano.</span><span class="sxs-lookup"><span data-stu-id="2c605-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="2c605-116">De lo contrario, puede haber colisiones no deseadas o raycasts inexactos.</span><span class="sxs-lookup"><span data-stu-id="2c605-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="2c605-117">Prefab del cuerpo kinemático de la punta de los dedos</span><span class="sxs-lookup"><span data-stu-id="2c605-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="2c605-118">Controla qué prefab se crea una instancia al dedo.</span><span class="sxs-lookup"><span data-stu-id="2c605-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="2c605-119">Para que el servicio funcione según lo previsto, el objeto prefab requiere:</span><span class="sxs-lookup"><span data-stu-id="2c605-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="2c605-120">Un componente rigidbody, con isKinematic habilitado</span><span class="sxs-lookup"><span data-stu-id="2c605-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="2c605-121">Colisionador</span><span class="sxs-lookup"><span data-stu-id="2c605-121">A collider</span></span>
- <span data-ttu-id="2c605-122">Componente de `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="2c605-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="2c605-123">Uso del cuerpo kinemático de la mano</span><span class="sxs-lookup"><span data-stu-id="2c605-123">Use palm kinematic body</span></span>

<span data-ttu-id="2c605-124">Controla si el servicio intentará crear una instancia de un prefab en la unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="2c605-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="2c605-125">Prefab del cuerpo kinémático de la mano</span><span class="sxs-lookup"><span data-stu-id="2c605-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="2c605-126">Cuando `UsePalmKinematicBody` está habilitado, este es el prefab al que se va a crear una instancia.</span><span class="sxs-lookup"><span data-stu-id="2c605-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="2c605-127">Al igual `FingerTipKinematicBodyPrefab` que , este prefab requiere:</span><span class="sxs-lookup"><span data-stu-id="2c605-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="2c605-128">Un componente rigidbody, con isKinematic habilitado</span><span class="sxs-lookup"><span data-stu-id="2c605-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="2c605-129">Colisionador</span><span class="sxs-lookup"><span data-stu-id="2c605-129">A collider</span></span>
- <span data-ttu-id="2c605-130">Componente de `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="2c605-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="2c605-131">Uso del servicio</span><span class="sxs-lookup"><span data-stu-id="2c605-131">How to use the service</span></span>

<span data-ttu-id="2c605-132">Una vez habilitada, use la propiedad de cualquier colisionador para recibir eventos de colisión de los 10 dígitos (y descime si `IsTrigger` están habilitados).</span><span class="sxs-lookup"><span data-stu-id="2c605-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
