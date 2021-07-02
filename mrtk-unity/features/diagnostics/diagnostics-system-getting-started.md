---
title: Introducción al sistema de diagnósticos
description: Documentación para habilitar y deshabilitar diagnósticos en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: a31b88f661c141941cae2d0b01668b26c0bed7d7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177243"
---
# <a name="diagnostics-system-overview"></a><span data-ttu-id="33eb5-104">Introducción al sistema de diagnósticos</span><span class="sxs-lookup"><span data-stu-id="33eb5-104">Diagnostics system overview</span></span>

<span data-ttu-id="33eb5-105">El Mixed Reality Toolkit diagnostics proporciona herramientas de diagnóstico que se ejecutan dentro de la aplicación para habilitar el análisis de problemas de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="33eb5-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="33eb5-106">La primera versión del sistema de diagnóstico contiene [Visual Profiler](using-visual-profiler.md) para permitir el análisis de problemas de rendimiento mientras se usa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="33eb5-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="33eb5-107">Introducción</span><span class="sxs-lookup"><span data-stu-id="33eb5-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33eb5-108">Se recomienda **_encarecidamente_** habilitar el sistema de diagnóstico durante todo el ciclo de desarrollo del producto y deshabilitarlo como último cambio antes de compilar y publicar la versión final.</span><span class="sxs-lookup"><span data-stu-id="33eb5-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="33eb5-109">Hay dos pasos clave para empezar a usar el sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="33eb5-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="33eb5-110">[Habilitar](#enable-diagnostics) el sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33eb5-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="33eb5-111">[Configuración de](#configure-diagnostic-options) opciones de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33eb5-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="33eb5-112">Habilitación de diagnósticos</span><span class="sxs-lookup"><span data-stu-id="33eb5-112">Enable diagnostics</span></span>

<span data-ttu-id="33eb5-113">El sistema de diagnóstico se administra mediante el objeto MixedRealityToolkit (u otro componente [de registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) servicios).</span><span class="sxs-lookup"><span data-stu-id="33eb5-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="33eb5-114">En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="33eb5-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="33eb5-115">Los pasos necesarios para otros registradores de servicios pueden ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="33eb5-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="33eb5-116">Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="33eb5-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="33eb5-118">Vaya al panel Inspector a la sección Sistema de diagnóstico y active Habilitar.</span><span class="sxs-lookup"><span data-stu-id="33eb5-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="33eb5-119">Selección de la implementación del sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33eb5-119">Select the Diagnostics System implementation</span></span>

    ![Selección de la implementación del sistema de diagnósticos](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="33eb5-121">Los usuarios del perfil predeterminado `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) tendrán el sistema de diagnóstico preconfigurado para usar el [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) objeto .</span><span class="sxs-lookup"><span data-stu-id="33eb5-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="33eb5-122">Configuración de opciones de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33eb5-122">Configure diagnostic options</span></span>

<span data-ttu-id="33eb5-123">El sistema de diagnóstico usa un perfil de configuración para especificar qué componentes se van a mostrar y para configurar sus valores.</span><span class="sxs-lookup"><span data-stu-id="33eb5-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="33eb5-124">Consulte [Configuring the Diagnostics System (Configuración](configuring-diagnostics.md) del sistema de diagnóstico) para obtener más información relacionada con la configuración de componentes disponible.</span><span class="sxs-lookup"><span data-stu-id="33eb5-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33eb5-125">Aunque es posible usar el modo de reproducción de Unity al desarrollar aplicaciones sin necesidad de los pasos de compilación e implementación, es importante evaluar los resultados del sistema de diagnóstico mediante una aplicación compilada que se ejecuta en el hardware y la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="33eb5-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="33eb5-126">Es posible que los diagnósticos de rendimiento, como [Visual Profiler,](using-visual-profiler.md)no reflejen con precisión el rendimiento real de la aplicación cuando se ejecutan desde el editor.</span><span class="sxs-lookup"><span data-stu-id="33eb5-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="33eb5-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="33eb5-127">See also</span></span>

- [<span data-ttu-id="33eb5-128">Documentación de la API de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33eb5-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="33eb5-129">Configuración del sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="33eb5-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="33eb5-130">Uso de Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="33eb5-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
