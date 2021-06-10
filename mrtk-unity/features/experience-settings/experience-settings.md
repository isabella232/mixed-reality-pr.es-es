---
title: ExperienceSettings
description: Documentación sobre las distintas configuraciones de experiencia para MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647895"
---
# <a name="experience-settings"></a><span data-ttu-id="f3c39-104">Configuración de la experiencia</span><span class="sxs-lookup"><span data-stu-id="f3c39-104">Experience Settings</span></span>

<span data-ttu-id="f3c39-105">Uno de los desafíos de la creación de la interfaz de usuario Mixed Reality es la alineación entre distintas experiencias.</span><span class="sxs-lookup"><span data-stu-id="f3c39-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="f3c39-106">Con MRTK, puede establecer y para la escena, configurará lo siguiente para que se comporte correctamente `Target Experience Scale` para la escala de `Content Offset` destino.</span><span class="sxs-lookup"><span data-stu-id="f3c39-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="f3c39-107">Mixed Reality de escena</span><span class="sxs-lookup"><span data-stu-id="f3c39-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="f3c39-108">Sistema de límites</span><span class="sxs-lookup"><span data-stu-id="f3c39-108">Boundary System</span></span>

  ![Configuración de la experiencia en el perfil de configuración de MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="f3c39-110">Escala de experiencia de destino</span><span class="sxs-lookup"><span data-stu-id="f3c39-110">Target Experience Scale</span></span>

<span data-ttu-id="f3c39-111">La **escala de experiencia** de destino especifica el entorno para el que se ha diseñado la experiencia.</span><span class="sxs-lookup"><span data-stu-id="f3c39-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="f3c39-112">Puede tomar los siguientes valores.</span><span class="sxs-lookup"><span data-stu-id="f3c39-112">It can take on the following values.</span></span>

* <span data-ttu-id="f3c39-113">*OrientationOnly:* una experiencia que utiliza solo la orientación del casco y está alineada con la gravedad.</span><span class="sxs-lookup"><span data-stu-id="f3c39-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="f3c39-114">El origen del sistema de coordenadas está en el nivel principal.</span><span class="sxs-lookup"><span data-stu-id="f3c39-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="f3c39-115">*Sentado:* una experiencia diseñada para su uso sentado.</span><span class="sxs-lookup"><span data-stu-id="f3c39-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="f3c39-116">El origen del sistema de coordenadas está en el nivel de planta.</span><span class="sxs-lookup"><span data-stu-id="f3c39-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="f3c39-117">*De* pie: una experiencia diseñada para un uso estacionario.</span><span class="sxs-lookup"><span data-stu-id="f3c39-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="f3c39-118">El origen del sistema de coordenadas está en el nivel de planta.</span><span class="sxs-lookup"><span data-stu-id="f3c39-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="f3c39-119">*Room:* una experiencia diseñada para admitir el movimiento por una sala.</span><span class="sxs-lookup"><span data-stu-id="f3c39-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="f3c39-120">El origen del sistema de coordenadas está en el nivel de planta.</span><span class="sxs-lookup"><span data-stu-id="f3c39-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="f3c39-121">*Mundo:* una experiencia diseñada para usar y desplazarse por el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="f3c39-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="f3c39-122">El origen del sistema de coordenadas está en el nivel principal.</span><span class="sxs-lookup"><span data-stu-id="f3c39-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="f3c39-123">Desplazamiento de contenido</span><span class="sxs-lookup"><span data-stu-id="f3c39-123">Content Offset</span></span>

<span data-ttu-id="f3c39-124">Este parámetro especifica el alto por encima del suelo para desplazarse por el [Mixed Reality de](scene-content.md) la escena cuando **tipo** de alineación se establece en Alinear con escala **de experiencia**</span><span class="sxs-lookup"><span data-stu-id="f3c39-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>