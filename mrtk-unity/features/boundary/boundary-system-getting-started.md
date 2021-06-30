---
title: Información general del sistema de límites
description: Página de aterrizaje del sistema de límites en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema de límites,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121363"
---
# <a name="boundary-system"></a><span data-ttu-id="2103d-104">Sistema de límites</span><span class="sxs-lookup"><span data-stu-id="2103d-104">Boundary system</span></span>

<span data-ttu-id="2103d-105">El sistema de límites proporciona compatibilidad para visualizar componentes de límite de realidad virtual en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2103d-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="2103d-106">Los límites definen el área en la que los usuarios pueden moverse de forma segura mientras llevan un casco de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="2103d-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="2103d-107">Los límites son un componente importante de una experiencia de realidad mixta para ayudar a los usuarios a evitar obstáculos desconocidos al usar un casco de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="2103d-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="2103d-108">Muchas plataformas de realidad virtual proporcionan una pantalla automática, por ejemplo, un contorno blanco superpuesto en el mundo virtual cuando el usuario o su controlador se acerca al límite.</span><span class="sxs-lookup"><span data-stu-id="2103d-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="2103d-109">El sistema de límites del kit de herramientas de Mixed Reality amplía esta característica para habilitar la presentación de un esquema del área con seguimiento, un plano de la planta y otras características que se pueden usar para proporcionar información adicional a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="2103d-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2103d-110">Introducción</span><span class="sxs-lookup"><span data-stu-id="2103d-110">Getting started</span></span>

<span data-ttu-id="2103d-111">La adición de compatibilidad con límites requiere dos componentes clave de Mixed Reality Toolkit: el sistema de límites y una plataforma de realidad virtual configurada con un límite.</span><span class="sxs-lookup"><span data-stu-id="2103d-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="2103d-112">[Habilitación](#enable-boundary-system) del sistema de límites</span><span class="sxs-lookup"><span data-stu-id="2103d-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="2103d-113">[Configuración de](#configure-boundary-visualization) la visualización de límites</span><span class="sxs-lookup"><span data-stu-id="2103d-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="2103d-114">[Compilación e implementación](#build-and-deploy) en una plataforma de realidad virtual con un límite configurado</span><span class="sxs-lookup"><span data-stu-id="2103d-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="2103d-115">Habilitación del sistema de límites</span><span class="sxs-lookup"><span data-stu-id="2103d-115">Enable boundary system</span></span>

<span data-ttu-id="2103d-116">El sistema de límites se administra mediante el objeto MixedRealityToolkit (u otro componente [registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) servicios).</span><span class="sxs-lookup"><span data-stu-id="2103d-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="2103d-117">En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="2103d-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="2103d-118">Los pasos necesarios para otros registradores de servicios pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="2103d-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="2103d-119">Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="2103d-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="2103d-121">Vaya al panel Inspector a la sección Sistema de límites y active Habilitar.</span><span class="sxs-lookup"><span data-stu-id="2103d-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Habilitar el sistema de límites](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="2103d-123">Seleccione la implementación del sistema de límites.</span><span class="sxs-lookup"><span data-stu-id="2103d-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="2103d-124">La implementación de clase predeterminada proporcionada por MRTK es la [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="2103d-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Selección de la implementación del sistema de límites](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="2103d-126">Toda la implementación del sistema de límites debe extender el [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="2103d-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="2103d-127">Configuración de la visualización de límites</span><span class="sxs-lookup"><span data-stu-id="2103d-127">Configure boundary visualization</span></span>

<span data-ttu-id="2103d-128">El [sistema de límites usa un perfil de configuración](configuring-boundary-visualization.md) para especificar qué componentes de límite se van a mostrar y para configurar su apariencia.</span><span class="sxs-lookup"><span data-stu-id="2103d-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Opciones de visualización de límites](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="2103d-130">Los usuarios del perfil predeterminado `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) tendrán el sistema de límites preconfigurado para mostrar un plano de planta, el área de juego y el área de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="2103d-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="2103d-131">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="2103d-131">Build and deploy</span></span>

<span data-ttu-id="2103d-132">Una vez configurado el sistema de límites con las opciones de visualización deseadas, el proyecto se puede crear implementado en la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="2103d-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="2103d-133">El modo de reproducción de Unity habilita la visualización en el editor del límite configurado.</span><span class="sxs-lookup"><span data-stu-id="2103d-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="2103d-134">Esta característica permite un desarrollo y pruebas rápidos sin necesidad del paso de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="2103d-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="2103d-135">Asegúrese de realizar pruebas de aceptación finales mediante una versión integrada e implementada de la aplicación, que se ejecuta en el hardware y la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="2103d-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="2103d-136">Acceso al sistema de límites mediante código</span><span class="sxs-lookup"><span data-stu-id="2103d-136">Accessing boundary system via code</span></span>

<span data-ttu-id="2103d-137">Si está habilitado y configurado, se puede acceder al sistema de límites a través de la clase auxiliar estática CoreServices.</span><span class="sxs-lookup"><span data-stu-id="2103d-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="2103d-138">A continuación, la referencia se puede usar para cambiar dinámicamente los parámetros boundary y acceder a los GameObjects relacionados administrados por el sistema.</span><span class="sxs-lookup"><span data-stu-id="2103d-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="2103d-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2103d-139">See also</span></span>

- [<span data-ttu-id="2103d-140">Documentación de la API de límites</span><span class="sxs-lookup"><span data-stu-id="2103d-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="2103d-141">Configuración de la visualización de límites</span><span class="sxs-lookup"><span data-stu-id="2103d-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
