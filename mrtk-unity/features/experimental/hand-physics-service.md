---
title: Hand Physics Extension Service
description: descripción Servicios de extensión física de mano.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143434"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="648e6-104">Servicios de extensión de física de mano</span><span class="sxs-lookup"><span data-stu-id="648e6-104">Hand physics extension services</span></span>

<span data-ttu-id="648e6-105">El servicio de física de manos permite eventos de colisión corporal rígida e interacciones con manos articuladas.</span><span class="sxs-lookup"><span data-stu-id="648e6-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="648e6-106">Introducción al servicio de extensión física manual</span><span class="sxs-lookup"><span data-stu-id="648e6-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="648e6-107">Agregue el servicio físico de mano a la lista de servicios de extensión y use el perfil predeterminado.</span><span class="sxs-lookup"><span data-stu-id="648e6-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="648e6-108">Una vez habilitada, use la propiedad IsTrigger de cualquier colisionador para recibir eventos de colisión de los 10 dígitos (y desconcertar si están habilitados).</span><span class="sxs-lookup"><span data-stu-id="648e6-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="648e6-109">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="648e6-109">Prerequisites</span></span>

- <span data-ttu-id="648e6-110">Se ha habilitado el servicio de extensión.</span><span class="sxs-lookup"><span data-stu-id="648e6-110">Enabled the extension service</span></span>
- <span data-ttu-id="648e6-111">Asigne un objeto prefab adecuado a la unión de dedo/mano.</span><span class="sxs-lookup"><span data-stu-id="648e6-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="648e6-112">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="648e6-112">Recommendations</span></span>

<span data-ttu-id="648e6-113">Aunque el servicio tiene como valor predeterminado la capa "predeterminada", se recomienda usar una capa independiente para los objetos HandPhysics.</span><span class="sxs-lookup"><span data-stu-id="648e6-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="648e6-114">De lo contrario, puede haber colisiones no deseadas o raycasts inexactos.</span><span class="sxs-lookup"><span data-stu-id="648e6-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
