---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636375"
---
# <a name="mrtk"></a>[<span data-ttu-id="589a0-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="589a0-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="589a0-102">MRTK proporciona un [sistema de teletransportar](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) que funciona automáticamente a través de manos y controladores articulados.</span><span class="sxs-lookup"><span data-stu-id="589a0-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="589a0-103">SDK DE XR</span><span class="sxs-lookup"><span data-stu-id="589a0-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="589a0-104">Se recomienda usar la implementación de teleportabilidad de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589a0-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="589a0-105">Si decide no usar MRTK, Unity proporciona una implementación de teletraslado en el kit de [herramientas de interacción de XR](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span><span class="sxs-lookup"><span data-stu-id="589a0-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="589a0-106">Si decide implementar el suyo propio, es conveniente tener en cuenta que no puede trasladar la cámara directamente.</span><span class="sxs-lookup"><span data-stu-id="589a0-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="589a0-107">Debido al control de Unity de la cámara para el seguimiento de los cabezales, deberá asignar a la cámara un elemento primario en la jerarquía y, en su lugar, pasarlo a GameObject.</span><span class="sxs-lookup"><span data-stu-id="589a0-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="589a0-108">Es el equivalente de Playspace de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589a0-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="589a0-109">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="589a0-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="589a0-110">Se recomienda usar la implementación de teleportabilidad de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589a0-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="589a0-111">Si decide implementar el suyo propio, es conveniente tener en cuenta que no puede trasladar la cámara directamente.</span><span class="sxs-lookup"><span data-stu-id="589a0-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="589a0-112">Debido al control de Unity de la cámara para el seguimiento de los cabezales, deberá asignar a la cámara un elemento primario en la jerarquía y, en su lugar, pasarlo a GameObject.</span><span class="sxs-lookup"><span data-stu-id="589a0-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="589a0-113">Es el equivalente de Playspace de MRTK.</span><span class="sxs-lookup"><span data-stu-id="589a0-113">This is the equivalent of MRTK's Playspace.</span></span>