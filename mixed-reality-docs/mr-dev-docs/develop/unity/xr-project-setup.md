---
title: Establecimiento de la configuración de XR
description: Manténgase al día de las recomendaciones de configuración más recientes de Unity XR para HoloLens desarrollo de aplicaciones.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603731"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="51653-104">Establecimiento de la configuración de XR</span><span class="sxs-lookup"><span data-stu-id="51653-104">Setting up your XR configuration</span></span>

<span data-ttu-id="51653-105">Una vez que haya elegido una versión de [Unity,](choosing-unity-version.md)el siguiente paso es seleccionar la configuración de XR que usará para compilar la aplicación de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="51653-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="51653-106">Elección de una configuración de XR</span><span class="sxs-lookup"><span data-stu-id="51653-106">Choosing an XR configuration</span></span>

<span data-ttu-id="51653-107">Al iniciar un nuevo proyecto de Unity, tiene varias configuraciones de XR entre las que puede seleccionar: el complemento **Mixed Reality OpenXR**, el complemento **XR** de Windows y **XR integrado heredado.**</span><span class="sxs-lookup"><span data-stu-id="51653-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="51653-108">Configuración del proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="51653-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="51653-109">La manera más fácil de configurar el proyecto de Unity para la realidad mixta es con Mixed Reality Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="51653-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="51653-110">MRTK para Unity es un kit de desarrollo multiplataforma de código abierto diseñado para facilitar la creación de aplicaciones de realidad mixta increíbles.</span><span class="sxs-lookup"><span data-stu-id="51653-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="51653-112">MRTK proporciona un sistema de entrada multiplataforma, componentes fundamentales y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="51653-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="51653-113">Con la versión 2 de MRTK, puede acelerar el desarrollo de aplicaciones para Microsoft HoloLens Windows Mixed Reality, cascos envolventes (VR) y muchos otros dispositivos VR/AR.</span><span class="sxs-lookup"><span data-stu-id="51653-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="51653-114">El proyecto está destinado a reducir las barreras de entrada, lo que permite a todos crear aplicaciones de realidad mixta y contribuir a la comunidad a medida que crecemos.</span><span class="sxs-lookup"><span data-stu-id="51653-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="51653-115">Para obtener más información sobre la Mixed Reality Toolkit, consulte la [documentación de MRTK](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="51653-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="51653-116">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="51653-116">Manual setup without MRTK</span></span>

<span data-ttu-id="51653-117">Aunque Microsoft y la comunidad han creado herramientas de código abierto como [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) que configurarán automáticamente el entorno para la realidad mixta, es posible que algunos desarrolladores quieran crear sus experiencias desde cero.</span><span class="sxs-lookup"><span data-stu-id="51653-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]