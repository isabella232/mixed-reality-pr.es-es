---
title: Experiencias compartidas en Unity
description: Aprenda a compartir los mismos hologramas entre varios usuarios de una aplicación de Unity con los delimitadores espaciales de Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Uso compartido, delimitador, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, anclajes espaciales de Azure, ASA, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: a82439d5676bf4bcb7898a33aafc29b43e91a49f
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031961"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="76965-104">Experiencias compartidas en Unity</span><span class="sxs-lookup"><span data-stu-id="76965-104">Shared experiences in Unity</span></span>

<span data-ttu-id="76965-105">Una experiencia compartida permite que varios usuarios, cada uno con sus propios dispositivos HoloLens, iOS o Android, vean el mismo holograma e interactúen con él de forma colectiva.</span><span class="sxs-lookup"><span data-stu-id="76965-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="76965-106">Los hologramas se colocan en un punto fijo en el espacio a través del uso compartido del delimitador espacial.</span><span class="sxs-lookup"><span data-stu-id="76965-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="76965-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="76965-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="76965-108">Los <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> crean delimitadores espaciales con respaldo en la nube duraderos, que la aplicación puede ubicar en varios dispositivos HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="76965-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="76965-109">Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="76965-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="76965-110">También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para la persistencia asincrónica de hologramas en dispositivos de HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="76965-110">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="76965-111">Al compartir un delimitador espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="76965-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="76965-112">Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="76965-112">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="76965-113">Una vez configurados los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="76965-113">Once Azure Spatial Anchors is set up, you can <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="76965-114">Transferencias de delimitadores locales</span><span class="sxs-lookup"><span data-stu-id="76965-114">Local anchor transfers</span></span>

<span data-ttu-id="76965-115">En situaciones en las que no se pueden usar delimitadores espaciales de Azure, las [transferencias de delimitadores locales](../../out-of-scope/local-anchor-transfers-in-unity.md) permiten que un dispositivo hololens exporte un delimitador para que una segunda HoloLens pueda importarlo.</span><span class="sxs-lookup"><span data-stu-id="76965-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="76965-116">Este enfoque no se admite en dispositivos iOS y Android, y proporciona una recuperación de delimitador menos sólida que los delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="76965-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="76965-117">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="76965-117">Next Development Checkpoint</span></span>

<span data-ttu-id="76965-118">Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="76965-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="76965-119">Desde aquí, puede continuar con la siguiente sección:</span><span class="sxs-lookup"><span data-stu-id="76965-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="76965-120">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="76965-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="76965-121">O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:</span><span class="sxs-lookup"><span data-stu-id="76965-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="76965-122">Implementación en HoloLens o con auriculares de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="76965-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="76965-123">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#3-platform-capabilities-and-apis) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="76965-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="76965-124">Consulte también</span><span class="sxs-lookup"><span data-stu-id="76965-124">See also</span></span>
* [<span data-ttu-id="76965-125">Experiencias compartidas en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="76965-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="76965-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="76965-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="76965-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="76965-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
