---
title: Introducción a la portabilidad
description: Información general de las distintas opciones de porteo para llevar las aplicaciones existentes a Mixed Reality para HoloLens y VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600504"
---
# <a name="porting-overview"></a><span data-ttu-id="4d218-104">Introducción a la portabilidad</span><span class="sxs-lookup"><span data-stu-id="4d218-104">Porting overview</span></span>

<span data-ttu-id="4d218-105">Cuando se trata de porte o actualización de los proyectos existentes para Mixed Reality, el recorrido de porte depende de si la aplicación se ha creado con Unity o Unreal Engine, y tiene como destino HoloLens (1ª generación) o HoloLens 2, o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="4d218-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="4d218-106">Esta página de información general contiene nuestras recomendaciones actuales para cada plataforma y dispositivo; asegúrese de comprobarlo, ya que estos procesos siempre cambian.</span><span class="sxs-lookup"><span data-stu-id="4d218-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="4d218-107">En primer lugar, configure el destino del proyecto en función de nuestras recomendaciones de [Unity](#unity) y [Unreal](#unreal) y, a continuación, siga uno o varios de nuestros escenarios de porte:</span><span class="sxs-lookup"><span data-stu-id="4d218-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="4d218-108">HoloLens (1ª generación) para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4d218-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="4d218-109">Cascos de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4d218-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="4d218-110">Aplicaciones de SteamVR</span><span class="sxs-lookup"><span data-stu-id="4d218-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="4d218-111">Aplicaciones para UWP 2D</span><span class="sxs-lookup"><span data-stu-id="4d218-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="4d218-112">Destinos de proyecto recomendados</span><span class="sxs-lookup"><span data-stu-id="4d218-112">Recommended project targets</span></span>

<span data-ttu-id="4d218-113">Es importante mantener actualizados los proyectos, independientemente de si se porte una aplicación a otro dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="4d218-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="4d218-114">Consulte los recursos basados en motor que se enumeran a continuación para ver nuestras recomendaciones actuales.</span><span class="sxs-lookup"><span data-stu-id="4d218-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="4d218-115">Unity</span><span class="sxs-lookup"><span data-stu-id="4d218-115">Unity</span></span>

<span data-ttu-id="4d218-116">Nuestra recomendación actual para el desarrollo de Unity con Mixed Reality es **Unity 2019 LTS** mediante el paquete XR heredado .</span><span class="sxs-lookup"><span data-stu-id="4d218-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="4d218-117">Si el proyecto usa Mixed Reality Toolkit, compruebe que se encuentra en la versión más reciente, que actualmente es **MRTK-Unity 2.5.**</span><span class="sxs-lookup"><span data-stu-id="4d218-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="4d218-118">Aunque el SDK de XR está disponible con esta versión de Unity, Azure Spatial Anchors no es compatible actualmente con esta configuración.</span><span class="sxs-lookup"><span data-stu-id="4d218-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="4d218-119">Esta recomendación se actualizará con una versión futura del paquete Spatial Anchors Azure para Unity.</span><span class="sxs-lookup"><span data-stu-id="4d218-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="4d218-120">Si no necesita Azure Spatial Anchors, puede configurar el proyecto de Unity para [XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) y empezar a trabajar con [MRTK y el SDK de XR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)</span><span class="sxs-lookup"><span data-stu-id="4d218-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="4d218-121">Si actualmente usa el SDK de XR en el proyecto y desea usar Azure Spatial Anchors, desinstale el SDK de XR y vuelva a instalar el paquete XR heredado para revertir la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="4d218-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="4d218-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="4d218-122">Unreal</span></span>

<span data-ttu-id="4d218-123">Nuestra recomendación actual para el desarrollo de Unreal Mixed Reality **es Unreal Engine 4.26**.</span><span class="sxs-lookup"><span data-stu-id="4d218-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="4d218-124">Si el proyecto usa Mixed Reality Toolkit UX Tools, asegúrese de que usa la versión más reciente, que actualmente es **UXT 0.10**.</span><span class="sxs-lookup"><span data-stu-id="4d218-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="4d218-125">Escenarios de porte</span><span class="sxs-lookup"><span data-stu-id="4d218-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="4d218-126">Aplicaciones de Unity de HoloLens (1ª generación) para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4d218-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="4d218-127">Si tiene una aplicación de Unity de HoloLens (1.ª generación) que le gustaría portabilidad a un HoloLens 2, siga las instrucciones de nuestro artículo de portabilidad de [HoloLens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="4d218-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="4d218-128">Cascos de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4d218-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="4d218-129">Si ha creado contenido para otros dispositivos, como Oculus Dimensional o HP Reverb G2, deberá redestinar los SDK de REALIDAD virtual específicos del proveedor y las API de asignación de entrada potenciales.</span><span class="sxs-lookup"><span data-stu-id="4d218-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="4d218-130">Puede encontrar información sobre los escenarios de porte de Unity y Unreal en nuestra guía de [porte de aplicaciones inmersivas](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="4d218-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="4d218-131">Aplicaciones de SteamVR</span><span class="sxs-lookup"><span data-stu-id="4d218-131">SteamVR applications</span></span>

<span data-ttu-id="4d218-132">Para conocer las experiencias de SteamVR que quiera actualizar para los cascos Windows Mixed Reality, consulte nuestra guía [de actualización de SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="4d218-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="4d218-133">Aplicaciones universales de Windows 2D</span><span class="sxs-lookup"><span data-stu-id="4d218-133">2D Universal Windows applications</span></span>

<span data-ttu-id="4d218-134">Si tienes una aplicación para UWP 2D existente que te gustaría portabilidad a un casco envolvente de Windows Mixed Reality o HoloLens, sigue nuestras instrucciones de portabilidad de aplicaciones [2D](building-2d-apps.md) para UWP Windows Mixed Reality aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="4d218-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>