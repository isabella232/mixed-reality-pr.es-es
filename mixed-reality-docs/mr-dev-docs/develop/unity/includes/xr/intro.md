---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603721"
---
# <a name="openxr"></a>[<span data-ttu-id="88cac-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="88cac-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="88cac-102">El Mixed Reality complemento OpenXR es la recomendación de **Microsoft** para **Unity 2020 LTS** o posterior.</span><span class="sxs-lookup"><span data-stu-id="88cac-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="88cac-103">A medida que se desarrollan nuevas características en el futuro, solo se incluirán en el Mixed Reality complemento OpenXR en el futuro.</span><span class="sxs-lookup"><span data-stu-id="88cac-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="88cac-104">El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="88cac-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="88cac-105">Esto le permite escribir código de difusión por rayos una vez que, a continuación, HoloLens 2 teléfonos y tabletas ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="88cac-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="88cac-106">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="88cac-106">Prerequisites</span></span> 

* <span data-ttu-id="88cac-107">Herramientas [más recientes para HoloLens 2 desarrollo](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="88cac-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="88cac-108">Versión más reciente de Unity 2020.3 LTS: versión 2020.3.8f1 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="88cac-109">Versiones de paquete recomendadas</span><span class="sxs-lookup"><span data-stu-id="88cac-109">Recommended package versions</span></span>

<span data-ttu-id="88cac-110">Las instrucciones de esta página le configurarán con los paquetes principales de Unity OpenXR necesarios para implementar HoloLens 2 o Windows Mixed Reality aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="88cac-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="88cac-111">Complemento OpenXR de Unity: versión 1.2 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="88cac-112">Mixed Reality complemento OpenXR: versión 1.0.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="88cac-113">Si usa los siguientes paquetes en el proyecto, deberá asegurarse de usar al menos las versiones mínimas enumeradas a continuación:</span><span class="sxs-lookup"><span data-stu-id="88cac-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="88cac-114">MRTK: versión 2.7.2 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="88cac-115">AR Foundation: versión 4.1.1 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="88cac-116">Canalización de representación universal (URP): versión 10.5.1 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="88cac-117">Azure Spatial Anchors: versión 2.10 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="88cac-118">Azure Remote Rendering: versión 1.0.15 o posterior</span><span class="sxs-lookup"><span data-stu-id="88cac-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="88cac-119">Si va a compilar aplicaciones vr en Windows pc, Mixed Reality complemento OpenXR no es estrictamente necesario.</span><span class="sxs-lookup"><span data-stu-id="88cac-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="88cac-120">Sin embargo, querrá instalar el complemento si va a configurar enlaces de entrada para controladores HP Reverb G2 o crear aplicaciones que funcionen en cascos de HoloLens 2 y VR.</span><span class="sxs-lookup"><span data-stu-id="88cac-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="88cac-121">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="88cac-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="88cac-122">Microsoft no recomienda usar el complemento Windows XR para proyectos nuevos en Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="88cac-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="88cac-123">En su lugar, debe usar Mixed Reality complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="88cac-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="88cac-124">Sin embargo, si usa Unity 2019 y necesita AR Foundation 2.0 para la compatibilidad con dispositivos ARCore/ARKit, este complemento habilita esa compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="88cac-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88cac-125">El uso de este complemento en Unity 2019 no es compatible con Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="88cac-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="88cac-126">XR heredado</span><span class="sxs-lookup"><span data-stu-id="88cac-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="88cac-127">Si todavía está en **Unity 2019** o versiones anteriores, Microsoft recomienda usar la compatibilidad con **XR integrada heredada.**</span><span class="sxs-lookup"><span data-stu-id="88cac-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="88cac-128">Aunque el Windows XR es funcional en Unity 2019, no se recomienda porque este complemento no es compatible con Azure Spatial Anchors en Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="88cac-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="88cac-129">Si va a iniciar un nuevo proyecto, se recomienda instalar [Unity 2020](../../choosing-unity-version.md) en su lugar y usar Mixed Reality complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="88cac-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>