---
title: Experiencias compartidas en Unity
description: Comparta los mismos hologramas entre varios usuarios en una aplicación de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Uso compartido, delimitador, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, anclajes espaciales de Azure, ASA
ms.openlocfilehash: 324aecdc89b4996625ce93514616c32d2d064ffa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691963"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="c92b8-104">Experiencias compartidas en Unity</span><span class="sxs-lookup"><span data-stu-id="c92b8-104">Shared experiences in Unity</span></span>

<span data-ttu-id="c92b8-105">Una experiencia compartida es aquella en la que varios usuarios, cada uno con sus propios dispositivos HoloLens, iOS o Android, ven colectivamente e interactúan con el mismo holograma que se coloca en un punto fijo en el espacio.</span><span class="sxs-lookup"><span data-stu-id="c92b8-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="c92b8-106">Esto se logra mediante el uso compartido del delimitador espacial.</span><span class="sxs-lookup"><span data-stu-id="c92b8-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="c92b8-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c92b8-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="c92b8-108">Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para crear delimitadores espaciales con respaldo en la nube duraderos, que la aplicación puede encontrar en varios dispositivos HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="c92b8-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c92b8-109">Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="c92b8-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="c92b8-110">Esto permite compartir experiencias en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="c92b8-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="c92b8-111">También se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia de hologramas asincrónicos en dispositivos Android, iOS y HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c92b8-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c92b8-112">Al compartir un delimitador espacial en la nube duradera, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, aunque los dispositivos no estén presentes juntos simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="c92b8-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="c92b8-113">Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="c92b8-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c92b8-114">Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="c92b8-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="c92b8-115">Transferencias de delimitadores locales</span><span class="sxs-lookup"><span data-stu-id="c92b8-115">Local anchor transfers</span></span>

<span data-ttu-id="c92b8-116">En situaciones en las que no se pueden usar delimitadores espaciales de Azure, las [transferencias de delimitadores locales](../../out-of-scope/local-anchor-transfers-in-unity.md) permiten que un dispositivo hololens exporte un delimitador para que lo importe un segundo dispositivo hololens.</span><span class="sxs-lookup"><span data-stu-id="c92b8-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="c92b8-117">Tenga en cuenta que este enfoque proporciona una recuperación de delimitador menos sólida que los delimitadores espaciales de Azure, y los dispositivos iOS y Android no son compatibles con este enfoque.</span><span class="sxs-lookup"><span data-stu-id="c92b8-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c92b8-118">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="c92b8-118">Next Development Checkpoint</span></span>

<span data-ttu-id="c92b8-119">Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c92b8-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="c92b8-120">Desde aquí, puede continuar con el tema siguiente:</span><span class="sxs-lookup"><span data-stu-id="c92b8-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c92b8-121">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="c92b8-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="c92b8-122">O ir directamente a la implementación de la aplicación en un dispositivo o emulador:</span><span class="sxs-lookup"><span data-stu-id="c92b8-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c92b8-123">Implementación en HoloLens o con auriculares de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c92b8-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="c92b8-124">Siempre puede volver a los puntos de [control de desarrollo de Unity](unity-development-overview.md#3-platform-capabilities-and-apis) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="c92b8-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="c92b8-125">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c92b8-125">See also</span></span>
* [<span data-ttu-id="c92b8-126">Experiencias compartidas en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c92b8-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="c92b8-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="c92b8-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="c92b8-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="c92b8-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
