---
title: Configuración de la configuración de XR
description: Manténgase al día con las recomendaciones de configuración XR de Unity más recientes para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906949"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="e70e1-104">Configuración de la configuración de XR</span><span class="sxs-lookup"><span data-stu-id="e70e1-104">Setting up your XR configuration</span></span>

<span data-ttu-id="e70e1-105">Al iniciar un nuevo proyecto de Unity, tiene tres opciones diferentes para controlar sus necesidades de XR:</span><span class="sxs-lookup"><span data-stu-id="e70e1-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="e70e1-106">Complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="e70e1-106">OpenXR plugin</span></span>
* <span data-ttu-id="e70e1-107">Complemento XR de Windows</span><span class="sxs-lookup"><span data-stu-id="e70e1-107">Windows XR plugin</span></span>
* <span data-ttu-id="e70e1-108">Complemento XR heredado</span><span class="sxs-lookup"><span data-stu-id="e70e1-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="e70e1-109">Configuración del proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="e70e1-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="e70e1-110">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="e70e1-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="e70e1-111">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="e70e1-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="e70e1-112">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="e70e1-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e70e1-113">Pruebe nuestros tutoriales de MRTK</span><span class="sxs-lookup"><span data-stu-id="e70e1-113">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="e70e1-114">Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="e70e1-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="e70e1-115">Uso de MRTK con compatibilidad con OpenXR</span><span class="sxs-lookup"><span data-stu-id="e70e1-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="e70e1-116">MRTK-Unity versión 2.7 proporciona mejores compatibilidades para el complemento Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="e70e1-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="e70e1-117">Abra de [nuevo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) para instalar Mixed Reality Toolkit, si aún no lo ha hecho.</span><span class="sxs-lookup"><span data-stu-id="e70e1-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="e70e1-118">La compatibilidad con OpenXR está en el **paquete de Foundation.**</span><span class="sxs-lookup"><span data-stu-id="e70e1-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="e70e1-119">Consulte la documentación de MRTK para obtener información más [detallada sobre la migración a OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="e70e1-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="e70e1-120">Al actualizar desde una versión anterior de MRTK anterior a **la 2.5.3,** asegúrese de que la línea siguiente está en el archivo **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="e70e1-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="e70e1-121">Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o posterior.</span><span class="sxs-lookup"><span data-stu-id="e70e1-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="e70e1-122">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="e70e1-122">Manual setup without MRTK</span></span>

<span data-ttu-id="e70e1-123">Aunque Microsoft y la comunidad han creado herramientas de código abierto como [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) que configurarán automáticamente el entorno WMR, muchos desarrolladores desean crear sus experiencias desde cero.</span><span class="sxs-lookup"><span data-stu-id="e70e1-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]