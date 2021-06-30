---
ms.openlocfilehash: 550ad2b9fa92894cdf4dad86def4cd3a9b450fb1
ms.sourcegitcommit: e9a1510984d00dc40ffd39239349e500f5737a0d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113103890"
---
# <a name="openxr"></a>[<span data-ttu-id="ef5b2-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ef5b2-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ef5b2-102">El Mixed Reality complemento OpenXR es la recomendación **de Microsoft** para Unity 2020 LTS o posterior.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="ef5b2-103">A medida que se desarrollan nuevas características en el futuro, solo se incluirán en el Mixed Reality complemento openXR a futuro.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="ef5b2-104">El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="ef5b2-105">Esto le permite escribir código de difusión por rayos una vez que abarque HoloLens 2 teléfonos y tabletas ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ef5b2-106">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="ef5b2-106">Prerequisites</span></span> 

* <span data-ttu-id="ef5b2-107">Herramientas [más recientes para HoloLens 2 desarrollo](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="ef5b2-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="ef5b2-108">La versión más reciente de Unity 2020.3 LTS(se recomienda 2020.3.8f1 o posterior)</span><span class="sxs-lookup"><span data-stu-id="ef5b2-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="ef5b2-109">Versiones mínimas</span><span class="sxs-lookup"><span data-stu-id="ef5b2-109">Minimum versions</span></span>

<span data-ttu-id="ef5b2-110">Las instrucciones de esta página le configurarán con los requisitos más recientes y más importantes de Unity y OpenXR que se enumeran a continuación:</span><span class="sxs-lookup"><span data-stu-id="ef5b2-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="ef5b2-111">Complemento OpenXR de Unity más reciente (se recomienda la versión 1.2 o posterior)</span><span class="sxs-lookup"><span data-stu-id="ef5b2-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="ef5b2-112">Versión Mixed Reality complemento OpenXR (se recomienda la versión 1.0.0 o posterior)</span><span class="sxs-lookup"><span data-stu-id="ef5b2-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="ef5b2-113">Si el proyecto usa MRTK, se recomienda la versión 2.7.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-113">If your project uses MRTK, we recommend version 2.7.2 or later</span></span>
* <span data-ttu-id="ef5b2-114">Si el proyecto usa el paquete de canalización de representación universal (URP), se recomienda la versión 10.5.1 o posterior.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-114">If your project uses Universal Render Pipeline (URP) package, we recommend version 10.5.1 or later</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="ef5b2-115">Si va a compilar aplicaciones de REALIDAD virtual en equipos Windows, Mixed Reality complemento OpenXR no es necesariamente necesario.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ef5b2-116">Sin embargo, querrá instalar el complemento si va a personalizar la asignación de controladores para controladores HP Reverb G2 o compilar aplicaciones que funcionen en cascos de realidad virtual HoloLens 2 y de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="ef5b2-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="ef5b2-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="ef5b2-118">Microsoft no recomienda usar el complemento XR de Windows para ningún proyecto nuevo de Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="ef5b2-119">Sin embargo, si usa Unity 2019 y necesita AR Foundation 2.0 para la compatibilidad con dispositivos ARCore/ARKit, este complemento habilita esa compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef5b2-120">El uso de este complemento en Unity 2019 no admite Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="ef5b2-121">XR heredado</span><span class="sxs-lookup"><span data-stu-id="ef5b2-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="ef5b2-122">Si todavía está en Unity 2019 o versiones anteriores, Microsoft recomienda usar la compatibilidad con XR integrada heredada.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="ef5b2-123">Aunque el complemento XR de Windows es funcional en Unity 2019, no se recomienda porque azure Spatial Anchors no se admite.</span><span class="sxs-lookup"><span data-stu-id="ef5b2-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>