---
title: SceneContent
description: Documentación sobre el componente de Mixed Reality scene content
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647917"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="a6004-104">Mixed Reality de escena</span><span class="sxs-lookup"><span data-stu-id="a6004-104">Mixed Reality Scene Content</span></span>

<span data-ttu-id="a6004-105">Al agregar MRTK a una escena, se `MixedRealitySceneContent` crea un objeto gameobject.</span><span class="sxs-lookup"><span data-stu-id="a6004-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="a6004-106">Este objeto sirve como un lugar dedicado para colocar y crear instancias Mixed Reality contenido para asegurarse de que se escala correctamente en muchas experiencias diferentes.</span><span class="sxs-lookup"><span data-stu-id="a6004-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="a6004-107">El objeto gameobject tiene un monobehavior **MixedRealitySceneContent** equivalente, que se puede configurar mediante el **parámetro Alignment Type.**</span><span class="sxs-lookup"><span data-stu-id="a6004-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="a6004-108">Este parámetro puede tomar los siguientes valores.</span><span class="sxs-lookup"><span data-stu-id="a6004-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="a6004-109">*AlignWithExperienceScale:* alinea el contenido  en función  de la escala de la experiencia de destino y el ajuste de contenido establecidos en la configuración de la experiencia del perfil [de configuración.](experience-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a6004-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="a6004-110">*AlignWithHeadHeight:* alinea el contenido con la posición y de la cabeza del usuario, que es la ubicación de la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="a6004-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![Mixed Reality objeto de contenido de escena creado en el editor](../images/experience-settings/MixedRealitySceneContent.png)