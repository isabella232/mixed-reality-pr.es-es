---
title: Introducción al reconocimiento espacial
description: describe el reconocimiento espacial en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176713"
---
# <a name="spatial-awareness-getting-started"></a><span data-ttu-id="f859c-104">Introducción al reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="f859c-104">Spatial awareness getting started</span></span>

![Reconocimiento espacial](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="f859c-106">El sistema de reconocimiento espacial proporciona reconocimiento ambiental del mundo real en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f859c-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="f859c-107">Cuando se introdujo en Microsoft HoloLens, Spatial Awareness proporcionó una colección de mallas, que representan la geometría del entorno, lo que permitía interacciones atractivas entre hologramas y el mundo real.</span><span class="sxs-lookup"><span data-stu-id="f859c-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="f859c-108">En este momento, el Mixed Reality Toolkit no se incluye con algoritmos de Spatial Understanding como se empaquetaron originalmente en HoloToolkit.</span><span class="sxs-lookup"><span data-stu-id="f859c-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="f859c-109">La comprensión espacial suele implicar la transformación de los datos de la malla espacial para crear datos de malla simplificados o agrupados, como planos, paredes, plantas, plantas, plantas, etc.</span><span class="sxs-lookup"><span data-stu-id="f859c-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="f859c-110">Introducción</span><span class="sxs-lookup"><span data-stu-id="f859c-110">Getting started</span></span>

<span data-ttu-id="f859c-111">La adición de compatibilidad con el reconocimiento espacial requiere dos componentes clave de la Mixed Reality Toolkit: el sistema de reconocimiento espacial y un proveedor de plataforma compatible.</span><span class="sxs-lookup"><span data-stu-id="f859c-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="f859c-112">[Habilitación](#enable-the-spatial-awareness-system) del sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="f859c-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="f859c-113">[Registro](#register-observers) y [configuración de](configuring-spatial-awareness-mesh-observer.md) uno o varios observadores espaciales para proporcionar datos de malla</span><span class="sxs-lookup"><span data-stu-id="f859c-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="f859c-114">[Compilación e implementación](#build-and-deploy) en una plataforma que admita el reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="f859c-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="f859c-115">Habilitación del sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="f859c-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="f859c-116">El sistema de reconocimiento espacial se administra mediante el objeto MixedRealityToolkit (u otro componente [del registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) servicios).</span><span class="sxs-lookup"><span data-stu-id="f859c-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="f859c-117">Siga estos pasos para habilitar o deshabilitar el sistema *de reconocimiento espacial* en el perfil de *MixedRealityToolkit.*</span><span class="sxs-lookup"><span data-stu-id="f859c-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="f859c-118">El Mixed Reality Toolkit se incluye con algunos perfiles preconfigurados predeterminados.</span><span class="sxs-lookup"><span data-stu-id="f859c-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="f859c-119">Algunos de ellos tienen el sistema de reconocimiento espacial habilitado o deshabilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="f859c-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="f859c-120">La intención de esta configuración previa, especialmente para cuando está deshabilitada, es evitar la sobrecarga visual de calcular y representar las mallas.</span><span class="sxs-lookup"><span data-stu-id="f859c-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="f859c-121">Perfil</span><span class="sxs-lookup"><span data-stu-id="f859c-121">Profile</span></span> | <span data-ttu-id="f859c-122">Sistema habilitado de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="f859c-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="f859c-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="f859c-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="f859c-124">Falso</span><span class="sxs-lookup"><span data-stu-id="f859c-124">False</span></span> |
| <span data-ttu-id="f859c-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="f859c-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="f859c-126">Falso</span><span class="sxs-lookup"><span data-stu-id="f859c-126">False</span></span> |
| <span data-ttu-id="f859c-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span><span class="sxs-lookup"><span data-stu-id="f859c-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="f859c-128">Verdadero</span><span class="sxs-lookup"><span data-stu-id="f859c-128">True</span></span> |

1. <span data-ttu-id="f859c-129">Seleccione el objeto MixedRealityToolkit en la jerarquía de escena para abrirlo en el panel inspector.</span><span class="sxs-lookup"><span data-stu-id="f859c-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="f859c-131">Vaya a la sección *Spatial Awareness System (Sistema de reconocimiento espacial)* y active *Enable Spatial Awareness System (Habilitar el sistema de reconocimiento espacial).*</span><span class="sxs-lookup"><span data-stu-id="f859c-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Habilitación del reconocimiento espacial](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="f859c-133">Seleccione el tipo de implementación del sistema de reconocimiento espacial deseado.</span><span class="sxs-lookup"><span data-stu-id="f859c-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="f859c-134">es [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) el valor predeterminado proporcionado.</span><span class="sxs-lookup"><span data-stu-id="f859c-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Selección de la implementación del sistema de reconocimiento espacial](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="f859c-136">Registro de observadores</span><span class="sxs-lookup"><span data-stu-id="f859c-136">Register observers</span></span>

<span data-ttu-id="f859c-137">Los servicios de la Mixed Reality Toolkit pueden tener [servicios de](../../architecture/systems-extensions-providers.md) proveedor de datos que complementan el servicio principal con controles de implementación y datos específicos de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="f859c-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="f859c-138">Un ejemplo de esto es el sistema [](../input/input-providers.md) de entrada Mixed Reality que tiene varios proveedores de datos para obtener el controlador y otra información de entrada relacionada de varias API específicas de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="f859c-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="f859c-139">El sistema de reconocimiento espacial es similar en que los proveedores de datos suministran al sistema datos de malla sobre el mundo real.</span><span class="sxs-lookup"><span data-stu-id="f859c-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="f859c-140">El perfil de reconocimiento espacial debe tener al menos un observador espacial registrado.</span><span class="sxs-lookup"><span data-stu-id="f859c-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="f859c-141">Los observadores espaciales suelen ser componentes específicos de la plataforma que actúan como proveedor para mostrar varios tipos de datos de malla desde un punto de conexión específico de la plataforma (es decir,</span><span class="sxs-lookup"><span data-stu-id="f859c-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="f859c-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="f859c-142">HoloLens).</span></span>

1. <span data-ttu-id="f859c-143">Abrir o expandir el perfil *del sistema de reconocimiento espacial*</span><span class="sxs-lookup"><span data-stu-id="f859c-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Perfil del sistema de reconocimiento espacial](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="f859c-145">Haga clic en *el botón "Agregar observador espacial".*</span><span class="sxs-lookup"><span data-stu-id="f859c-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="f859c-146">Selección del tipo de *implementación de Observador espacial deseado*</span><span class="sxs-lookup"><span data-stu-id="f859c-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Selección de la implementación del observador espacial](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="f859c-148">[Modificar las propiedades de configuración en el observador según](configuring-spatial-awareness-mesh-observer.md) sea necesario</span><span class="sxs-lookup"><span data-stu-id="f859c-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="f859c-149">Los usuarios `DefaultMixedRealityToolkitConfigurationProfile` de (Assets/MRTK/SDK/Profiles) tendrán preconfigurado el sistema de reconocimiento espacial para la plataforma Windows Mixed Reality que usa la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) clase .</span><span class="sxs-lookup"><span data-stu-id="f859c-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="f859c-150">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="f859c-150">Build and deploy</span></span>

<span data-ttu-id="f859c-151">Una vez configurado el sistema de reconocimiento espacial con los observadores deseados, el proyecto se puede crear e implementar en la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="f859c-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f859c-152">Si el destino es Windows Mixed Reality plataforma (por ejemplo, HoloLens), es [](/windows/mixed-reality/spatial-mapping-in-unity) importante asegurarse de que la funcionalidad percepción espacial está habilitada para usar el sistema de reconocimiento espacial en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f859c-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="f859c-153">Algunas plataformas, Microsoft HoloLens, proporcionan compatibilidad para la ejecución remota desde Unity.</span><span class="sxs-lookup"><span data-stu-id="f859c-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="f859c-154">Esta característica permite un desarrollo y pruebas rápidos sin necesidad del paso de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="f859c-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="f859c-155">Asegúrese de realizar pruebas de aceptación finales mediante una versión integrada e implementada de la aplicación, que se ejecuta en el hardware y la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="f859c-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f859c-156">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="f859c-156">Next steps</span></span>

<span data-ttu-id="f859c-157">Después de seguir los procedimientos anteriores para habilitar el sistema de reconocimiento espacial, el sistema se puede configurar y controlar con más detalle.</span><span class="sxs-lookup"><span data-stu-id="f859c-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="f859c-158">Información para configurar observadores en inspector:</span><span class="sxs-lookup"><span data-stu-id="f859c-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="f859c-159">Configuración de observadores para en el uso de dispositivos</span><span class="sxs-lookup"><span data-stu-id="f859c-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="f859c-160">Configuración de observadores para el uso en el editor</span><span class="sxs-lookup"><span data-stu-id="f859c-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="f859c-161">Información para controlar y extender observadores a través del código:</span><span class="sxs-lookup"><span data-stu-id="f859c-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="f859c-162">Configuración de observadores mediante código</span><span class="sxs-lookup"><span data-stu-id="f859c-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="f859c-163">Creación de un observador personalizado</span><span class="sxs-lookup"><span data-stu-id="f859c-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="f859c-164">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f859c-164">See also</span></span>

- [<span data-ttu-id="f859c-165">Documentación de Spatial Awareness API</span><span class="sxs-lookup"><span data-stu-id="f859c-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="f859c-166">Información general sobre la asignación espacial WMR</span><span class="sxs-lookup"><span data-stu-id="f859c-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="f859c-167">Asignación espacial en WMR de Unity</span><span class="sxs-lookup"><span data-stu-id="f859c-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)
