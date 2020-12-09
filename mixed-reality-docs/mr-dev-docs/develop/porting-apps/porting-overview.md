---
title: Introducción a la portabilidad
description: Información general de las distintas opciones de portabilidad para incorporar aplicaciones existentes a la realidad mixta.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portabilidad, Unity, middleware, motor, UWP, Win32
ms.openlocfilehash: 1ec03610dd26e9f75162795cbdded77a8e0189ce
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925827"
---
# <a name="porting-overview"></a><span data-ttu-id="18073-104">Introducción a la portabilidad</span><span class="sxs-lookup"><span data-stu-id="18073-104">Porting overview</span></span>

<span data-ttu-id="18073-105">En lo que respecta a la migración o la actualización de los proyectos existentes para la realidad mixta, pueden aplicarse varios escenarios en función de si la aplicación se compiló con Unity o un motor no real, HoloLens (1º gen) o HoloLens 2 o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="18073-105">When it comes to porting or upgrading your existing projects for Mixed Reality, several scenarios may apply depending on whether your app was built with Unity or Unreal Engine, HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="18073-106">Esta página de información general contiene nuestras recomendaciones actuales para cada plataforma y dispositivo. Asegúrese de volver a comprobar que estos procesos siempre cambian.</span><span class="sxs-lookup"><span data-stu-id="18073-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="18073-107">En primer lugar, configure el destino del proyecto en función de las recomendaciones de [Unity](#unity) y de las no [reales](#unreal) y luego siga uno o varios de nuestros escenarios de migración:</span><span class="sxs-lookup"><span data-stu-id="18073-107">First, setup your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="18073-108">HoloLens (1ª generación) a HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="18073-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="18073-109">Cascos de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="18073-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="18073-110">Aplicaciones SteamVR</span><span class="sxs-lookup"><span data-stu-id="18073-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="18073-111">aplicaciones para UWP en 2D</span><span class="sxs-lookup"><span data-stu-id="18073-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="18073-112">Objetivos de proyecto recomendados</span><span class="sxs-lookup"><span data-stu-id="18073-112">Recommended project targets</span></span>

<span data-ttu-id="18073-113">Es importante mantener los proyectos actualizados, tanto si se traslada una aplicación a otro dispositivo de destino como si no.</span><span class="sxs-lookup"><span data-stu-id="18073-113">It's important to keep your projects up-to-date, whether or not your porting an app to another target device.</span></span> <span data-ttu-id="18073-114">Consulte los recursos basados en el motor que se enumeran a continuación para ver nuestras recomendaciones actuales.</span><span class="sxs-lookup"><span data-stu-id="18073-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="18073-115">Unity</span><span class="sxs-lookup"><span data-stu-id="18073-115">Unity</span></span>

<span data-ttu-id="18073-116">Nuestra recomendación actual para el desarrollo de Unity con realidad mixta es **Unity 2019 lts mediante el paquete de XR heredado**.</span><span class="sxs-lookup"><span data-stu-id="18073-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="18073-117">Si el proyecto usa el kit de herramientas de realidad mixta, compruebe que se encuentra en la versión más reciente, que actualmente es **MRTK-Unity 2,5**.</span><span class="sxs-lookup"><span data-stu-id="18073-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="18073-118">Aunque el SDK de XR está disponible con esta versión de Unity, los delimitadores espaciales de Azure no son compatibles actualmente con esta configuración.</span><span class="sxs-lookup"><span data-stu-id="18073-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="18073-119">Esta recomendación se actualizará con una versión futura del paquete de anclajes espaciales de Azure para Unity.</span><span class="sxs-lookup"><span data-stu-id="18073-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="18073-120">Si no necesita anclajes espaciales de Azure, puede [configurar el proyecto de Unity para XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) y comenzar a usar el [SDK de MRTK y XR](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span><span class="sxs-lookup"><span data-stu-id="18073-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span></span>
> 
> * <span data-ttu-id="18073-121">Si actualmente está usando el SDK de XR en el proyecto y quiere usar delimitadores espaciales de Azure, desinstale el SDK de XR y reinstale el paquete de XR heredado para revertir la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="18073-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="18073-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="18073-122">Unreal</span></span> 

<span data-ttu-id="18073-123">Nuestra recomendación actual para el desarrollo no real con realidad mixta es el **motor inreal 4,26**.</span><span class="sxs-lookup"><span data-stu-id="18073-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="18073-124">Si el proyecto usa las herramientas de la experiencia del kit de herramientas de realidad mixta, asegúrese de que está usando la versión más reciente, que actualmente es **UXT 0,10**.</span><span class="sxs-lookup"><span data-stu-id="18073-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="18073-125">Escenarios de migración</span><span class="sxs-lookup"><span data-stu-id="18073-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="18073-126">Aplicaciones de Unity de HoloLens (primera generación) a HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="18073-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="18073-127">Si ya tiene una aplicación de Unity de HoloLens (primera generación) que le gustaría migrar a un HoloLens 2, siga las instrucciones que aparecen en nuestro artículo sobre la [migración de hololens](../unity/mrtk-porting-guide.md).</span><span class="sxs-lookup"><span data-stu-id="18073-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](../unity/mrtk-porting-guide.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="18073-128">Cascos de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="18073-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="18073-129">Si ha creado contenido para otros dispositivos, como Oculus Rift o HP reverberación G2, deberá volver a dirigirse a los SDK de VR específicos del proveedor y a las API de asignación de entradas posibles.</span><span class="sxs-lookup"><span data-stu-id="18073-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to re-target vendor-specific VR SDKs and potentially input mapping APIs.</span></span> <span data-ttu-id="18073-130">Puede encontrar información sobre los escenarios de migración de Unity y no real en nuestra [Guía de migración de aplicaciones envolventes](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="18073-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="18073-131">Aplicaciones SteamVR</span><span class="sxs-lookup"><span data-stu-id="18073-131">SteamVR applications</span></span>

<span data-ttu-id="18073-132">En el caso de las experiencias de SteamVR que quiera actualizar para los auriculares con Windows Mixed Reality, consulte nuestra [Guía de actualización de SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="18073-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="18073-133">aplicaciones Windows universales en 2D</span><span class="sxs-lookup"><span data-stu-id="18073-133">2D Universal Windows applications</span></span>

<span data-ttu-id="18073-134">Si tiene una aplicación de UWP en 2D existente que le gustaría trasladar a un auricular o a HoloLens de realidad mixta de Windows, siga las instrucciones que aparecen en el artículo sobre cómo [migrar aplicaciones para UWP en 2D para Windows](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="18073-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow the instructions in our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) article.</span></span>

