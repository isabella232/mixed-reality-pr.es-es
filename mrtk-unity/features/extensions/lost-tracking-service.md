---
title: Servicio de seguimientos perdidos
description: Introducción al servicio LostTracking en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144523"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="35e9d-104">Visualización de seguimiento perdido</span><span class="sxs-lookup"><span data-stu-id="35e9d-104">Lost tracking visualization</span></span>

![Seguimiento perdido](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="35e9d-106">El servicio de extensión de seguimiento perdido proporciona un objeto visual animado de estilo shell de HoloLens para el estado de seguimiento perdido.</span><span class="sxs-lookup"><span data-stu-id="35e9d-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="35e9d-107">Uso de extensiones de seguimiento perdidas</span><span class="sxs-lookup"><span data-stu-id="35e9d-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="35e9d-108">En Perfil de MRTK, agregue **Lost Tracking Service** a las extensiones.</span><span class="sxs-lookup"><span data-stu-id="35e9d-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="35e9d-109">Asigne **DefaultLostTrackingServiceProfile,** que incluye **LostTrackingVisualPrefab.**</span><span class="sxs-lookup"><span data-stu-id="35e9d-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
