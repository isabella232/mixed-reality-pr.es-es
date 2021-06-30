---
title: Introducción a la portabilidad
description: Información general de las distintas opciones de porte para llevar las aplicaciones existentes a Mixed Reality para HoloLens y VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042276"
---
# <a name="porting-overview"></a><span data-ttu-id="e531c-104">Introducción a la portabilidad</span><span class="sxs-lookup"><span data-stu-id="e531c-104">Porting overview</span></span>

<span data-ttu-id="e531c-105">Cuando se trata de portear o actualizar los proyectos existentes para Mixed Reality, el recorrido de porte depende de si la aplicación se ha creado con Unity o Unreal Engine, y tiene como destino HoloLens (1.ª generación) o HoloLens 2, o SteamVR.</span><span class="sxs-lookup"><span data-stu-id="e531c-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="e531c-106">Esta página de información general contiene nuestras recomendaciones actuales para cada plataforma y dispositivo; asegúrese de volver a comprobarlo, ya que estos procesos siempre cambian.</span><span class="sxs-lookup"><span data-stu-id="e531c-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="e531c-107">En primer lugar, configure el destino del proyecto en función de nuestras recomendaciones de [Unity](#unity) y [Unreal](#unreal) y, a continuación, siga uno o varios de nuestros escenarios de porte:</span><span class="sxs-lookup"><span data-stu-id="e531c-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="e531c-108">HoloLens (1.ª generación) para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e531c-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="e531c-109">Cascos envolventes de VR</span><span class="sxs-lookup"><span data-stu-id="e531c-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="e531c-110">Aplicaciones para UWP 2D</span><span class="sxs-lookup"><span data-stu-id="e531c-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="e531c-111">Destinos de proyecto recomendados</span><span class="sxs-lookup"><span data-stu-id="e531c-111">Recommended project targets</span></span>

<span data-ttu-id="e531c-112">Es importante mantener los proyectos actualizados, tanto si se porte una aplicación a otro dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="e531c-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="e531c-113">Consulte los recursos basados en motor que se enumeran a continuación para ver nuestras recomendaciones actuales.</span><span class="sxs-lookup"><span data-stu-id="e531c-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="e531c-114">Unity</span><span class="sxs-lookup"><span data-stu-id="e531c-114">Unity</span></span>

<span data-ttu-id="e531c-115">Consulte la [página Elegir una versión de Unity](../unity/choosing-unity-version.md) para obtener instrucciones actualizadas sobre las versiones recomendadas de Unity y MRTK.</span><span class="sxs-lookup"><span data-stu-id="e531c-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="e531c-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="e531c-116">Unreal</span></span>

<span data-ttu-id="e531c-117">Consulte la página Configuración del proyecto [de Unreal](../unreal/unreal-project-setup.md) para obtener instrucciones actualizadas sobre las versiones recomendadas de Unreal y MRTK.</span><span class="sxs-lookup"><span data-stu-id="e531c-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="e531c-118">Escenarios de porte</span><span class="sxs-lookup"><span data-stu-id="e531c-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="e531c-119">Aplicaciones de Unity de HoloLens (1.ª generación) para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e531c-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="e531c-120">Si tiene una aplicación de Unity holoLens (1.ª generación) existente que le gustaría portabilidad a un HoloLens 2, siga las instrucciones de nuestro artículo de portabilidad de [HoloLens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="e531c-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="e531c-121">Cascos envolventes de VR</span><span class="sxs-lookup"><span data-stu-id="e531c-121">Immersive VR headsets</span></span>

<span data-ttu-id="e531c-122">Si ha creado contenido para otros dispositivos vr, deberá redestinar los SDK de REALIDAD virtual específicos del proveedor y las API de asignación de entrada potenciales.</span><span class="sxs-lookup"><span data-stu-id="e531c-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="e531c-123">Puede encontrar información sobre los escenarios de porte de Unity y Unreal en nuestra guía de [porte de aplicaciones inmersivas.](porting-guides.md)</span><span class="sxs-lookup"><span data-stu-id="e531c-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="e531c-124">Para conocer las experiencias de SteamVR que desea actualizar para Windows Mixed Reality cascos, consulte nuestra guía [de actualización de SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="e531c-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="e531c-125">Aplicaciones universales de Windows 2D</span><span class="sxs-lookup"><span data-stu-id="e531c-125">2D Universal Windows applications</span></span>

<span data-ttu-id="e531c-126">Si tienes una aplicación 2D para UWP existente que te gustaría portabilidad a un casco envolvente de Windows Mixed Reality o HoloLens, sigue nuestras instrucciones de portabilidad de aplicaciones [2D para UWP Windows Mixed Reality](building-2d-apps.md) usuario.</span><span class="sxs-lookup"><span data-stu-id="e531c-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>