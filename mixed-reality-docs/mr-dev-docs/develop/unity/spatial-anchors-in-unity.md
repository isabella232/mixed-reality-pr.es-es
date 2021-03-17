---
title: Anclajes espaciales en Unity
description: Obtenga información sobre cómo crear, almacenar y obtener delimitadores espaciales en aplicaciones de realidad mixta de Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, anclajes espaciales, almacenamiento delimitado, HoloLens, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623625"
---
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="947a9-104">Anclajes espaciales en Unity</span><span class="sxs-lookup"><span data-stu-id="947a9-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="947a9-105">Los delimitadores espaciales guardan los hologramas en el espacio real entre las sesiones de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="947a9-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="947a9-106">Una vez guardada en el almacén de delimitadores de HoloLens, se pueden encontrar y cargar en sesiones diferentes y es una alternativa ideal cuando no hay conectividad a Internet.</span><span class="sxs-lookup"><span data-stu-id="947a9-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="947a9-107">Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube.</span><span class="sxs-lookup"><span data-stu-id="947a9-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="947a9-108">Si desea usar servicios en la nube de Azure para almacenar los anclajes, existe un documento que le guiará por la integración de [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span><span class="sxs-lookup"><span data-stu-id="947a9-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="947a9-109">Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.</span><span class="sxs-lookup"><span data-stu-id="947a9-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="947a9-110">Descripción de los delimitadores</span><span class="sxs-lookup"><span data-stu-id="947a9-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="947a9-111">Usar AnchorStore</span><span class="sxs-lookup"><span data-stu-id="947a9-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="947a9-112">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="947a9-112">Next Development Checkpoint</span></span>

<span data-ttu-id="947a9-113">Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="947a9-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="947a9-114">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="947a9-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="947a9-115">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="947a9-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="947a9-116">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="947a9-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="947a9-117">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="947a9-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="947a9-118">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="947a9-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="947a9-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="947a9-119">See Also</span></span>
* [<span data-ttu-id="947a9-120">Persistencia del delimitador espacial</span><span class="sxs-lookup"><span data-stu-id="947a9-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="947a9-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="947a9-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="947a9-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="947a9-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="947a9-123">Escalas de experiencia</span><span class="sxs-lookup"><span data-stu-id="947a9-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="947a9-124">Fase espacial</span><span class="sxs-lookup"><span data-stu-id="947a9-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="947a9-125">Pérdida de seguimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="947a9-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="947a9-126">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="947a9-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="947a9-127">Experiencias compartidas en Unity</span><span class="sxs-lookup"><span data-stu-id="947a9-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)