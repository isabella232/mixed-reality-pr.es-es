---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748527"
---
# <a name="mrtk"></a>[<span data-ttu-id="6c73c-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="6c73c-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="6c73c-102">MRTK proporciona un sistema de [teleportador](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) integrado que funciona automáticamente entre manos y controladores articulados.</span><span class="sxs-lookup"><span data-stu-id="6c73c-102">MRTK provides an in-box [teleport system](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="6c73c-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="6c73c-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="6c73c-104">Se recomienda usar la implementación de teleportación de MRTK.</span><span class="sxs-lookup"><span data-stu-id="6c73c-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="6c73c-105">Si decide no usar MRTK, Unity proporciona una implementación de teleportación en [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span><span class="sxs-lookup"><span data-stu-id="6c73c-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="6c73c-106">Si decide implementar la suya propia, es bueno tener en cuenta que no puede mover la cámara directamente.</span><span class="sxs-lookup"><span data-stu-id="6c73c-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="6c73c-107">Debido al control de Unity de la cámara para el seguimiento de la cabeza, deberá dar a la cámara un elemento primario en la jerarquía y mover ese GameObject en su lugar.</span><span class="sxs-lookup"><span data-stu-id="6c73c-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="6c73c-108">Este es el equivalente del espacio de juego de MRTK.</span><span class="sxs-lookup"><span data-stu-id="6c73c-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="6c73c-109">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="6c73c-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="6c73c-110">Se recomienda usar la implementación de teleportación de MRTK.</span><span class="sxs-lookup"><span data-stu-id="6c73c-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="6c73c-111">Si decide implementar la suya propia, es bueno tener en cuenta que no puede mover la cámara directamente.</span><span class="sxs-lookup"><span data-stu-id="6c73c-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="6c73c-112">Debido al control de Unity de la cámara para el seguimiento de la cabeza, deberá dar a la cámara un elemento primario en la jerarquía y mover ese GameObject en su lugar.</span><span class="sxs-lookup"><span data-stu-id="6c73c-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="6c73c-113">Este es el equivalente del espacio de juego de MRTK.</span><span class="sxs-lookup"><span data-stu-id="6c73c-113">This is the equivalent of MRTK's Playspace.</span></span>