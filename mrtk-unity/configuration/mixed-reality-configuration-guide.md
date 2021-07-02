---
title: Guía de configuración de perfiles de MRTK
description: Documentación para configurar MRTK en Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK,
ms.openlocfilehash: b7ec8d9ca2213ff998f94a6a2d029900ff886a2f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176413"
---
# <a name="mrtk-profile-configuration-guide"></a><span data-ttu-id="d0461-104">Guía de configuración de perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="d0461-104">MRTK profile configuration guide</span></span>

<span data-ttu-id="d0461-105">El Mixed Reality Toolkit centraliza la mayor parte de la configuración necesaria para administrar el kit de herramientas lo más posible (excepto para las verdaderas "cosas" en tiempo de ejecución).</span><span class="sxs-lookup"><span data-stu-id="d0461-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="d0461-106">Esta guía es un tutorial sencillo para cada una de las pantallas de perfil de configuración disponibles actualmente para el kit de herramientas.</span><span class="sxs-lookup"><span data-stu-id="d0461-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="d0461-107">El perfil de configuración Mixed Reality Toolkit principal</span><span class="sxs-lookup"><span data-stu-id="d0461-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="d0461-108">El perfil de configuración principal, que está asociado a *MixedRealityToolkit* GameObject en la escena, proporciona el punto de entrada principal para la Toolkit en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d0461-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="d0461-109">El Mixed Reality Toolkit "bloquea" las pantallas de configuración predeterminadas para asegurarse de que siempre tiene un punto de inicio común para el proyecto y se recomienda empezar a definir su propia configuración a medida que evoluciona el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d0461-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="d0461-110">La configuración de MRTK no se puede editar durante el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="d0461-110">The MRTK configuration is not editable during play-mode.</span></span>

![Perfil de configuración de MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="d0461-112">Todos los perfiles "predeterminados" de la Mixed Reality Toolkit pueden encontrarse en el proyecto del SDK en la carpeta Assets/MRTK/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="d0461-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0461-113">DefaultHoloLens2ConfigurationProfile está optimizado para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d0461-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="d0461-114">Consulte [Perfiles para](../features/profiles/profiles.md) obtener más información.</span><span class="sxs-lookup"><span data-stu-id="d0461-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="d0461-115">Al abrir el perfil Mixed Reality Toolkit configuración principal, verá la siguiente pantalla en el inspector:</span><span class="sxs-lookup"><span data-stu-id="d0461-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="d0461-116">Si selecciona un recurso MixedRealityToolkitConfigurationProfile sin MixedRealityToolkit en la escena, se le preguntará si desea que MRTK configure automáticamente la escena.</span><span class="sxs-lookup"><span data-stu-id="d0461-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="d0461-117">Sin embargo, esto es opcional, debe haber un objeto MixedRealityToolkit activo en la escena para acceder a todas las pantallas de configuración.</span><span class="sxs-lookup"><span data-stu-id="d0461-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="d0461-118">Esto aloja la configuración actual del entorno de ejecución activo para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d0461-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="d0461-119">Desde aquí puede navegar a todos los perfiles de configuración de MRTK, incluidos:</span><span class="sxs-lookup"><span data-stu-id="d0461-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="d0461-120">Mixed Reality Toolkit de configuración de perfiles</span><span class="sxs-lookup"><span data-stu-id="d0461-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mrtk-profile-configuration-guide)
  - [<span data-ttu-id="d0461-121">El perfil de configuración Mixed Reality Toolkit principal</span><span class="sxs-lookup"><span data-stu-id="d0461-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="d0461-122">Configuración de la experiencia</span><span class="sxs-lookup"><span data-stu-id="d0461-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="d0461-123">Configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="d0461-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="d0461-124">Configuración del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="d0461-125">Configuración de visualización de límites</span><span class="sxs-lookup"><span data-stu-id="d0461-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="d0461-126">Selección del sistema de teleportación</span><span class="sxs-lookup"><span data-stu-id="d0461-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="d0461-127">Configuración de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="d0461-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="d0461-128">Configuración de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d0461-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="d0461-129">Configuración del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="d0461-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="d0461-130">Configuración de servicios adicionales</span><span class="sxs-lookup"><span data-stu-id="d0461-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="d0461-131">Configuración de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="d0461-132">Reglas de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="d0461-133">Configuración del puntero</span><span class="sxs-lookup"><span data-stu-id="d0461-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="d0461-134">Configuración de gestos</span><span class="sxs-lookup"><span data-stu-id="d0461-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="d0461-135">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="d0461-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="d0461-136">Configuración de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="d0461-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="d0461-137">Configuración de visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="d0461-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="d0461-138">Utilidades del editor</span><span class="sxs-lookup"><span data-stu-id="d0461-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="d0461-139">Inspectores de servicio</span><span class="sxs-lookup"><span data-stu-id="d0461-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="d0461-140">Representador de búfer de profundidad</span><span class="sxs-lookup"><span data-stu-id="d0461-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="d0461-141">Cambio de perfiles en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="d0461-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="d0461-142">Modificador de perfil de inicialización de MRTK anterior</span><span class="sxs-lookup"><span data-stu-id="d0461-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="d0461-143">Conmutador de perfil activo</span><span class="sxs-lookup"><span data-stu-id="d0461-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="d0461-144">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d0461-144">See also</span></span>](#see-also)

<span data-ttu-id="d0461-145">Estos perfiles de configuración se detallan a continuación en sus secciones pertinentes:</span><span class="sxs-lookup"><span data-stu-id="d0461-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="d0461-146">Configuración de la experiencia</span><span class="sxs-lookup"><span data-stu-id="d0461-146">Experience settings</span></span>

<span data-ttu-id="d0461-147">Ubicado en la página Mixed Reality Toolkit configuración principal, esta configuración define la operación predeterminada de la escala de Mixed Reality [de entorno](/windows/mixed-reality/coordinate-systems-in-unity) para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d0461-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="d0461-148">Configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="d0461-148">Camera settings</span></span>

<span data-ttu-id="d0461-149">La configuración de la cámara define cómo se configurará la cámara para el proyecto de Mixed Reality, definiendo la configuración genérica de recorte, calidad y transparencia.</span><span class="sxs-lookup"><span data-stu-id="d0461-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="d0461-150">Configuración del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-150">Input system settings</span></span>

<span data-ttu-id="d0461-151">El Mixed Reality Project proporciona un sistema de entrada sólido y bien entrenado para enrutar todos los eventos de entrada alrededor del proyecto que está seleccionado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="d0461-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="d0461-152">Detrás del sistema de entrada proporcionado por MRTK hay otros sistemas, que ayudan a impulsar y administrar las complejas intercalaciones necesarias para abstraer las complejidades de un marco de trabajo de realidad mixta o multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="d0461-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="d0461-153">Cada uno de los perfiles individuales se detalla a continuación:</span><span class="sxs-lookup"><span data-stu-id="d0461-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="d0461-154">Enfoque Configuración</span><span class="sxs-lookup"><span data-stu-id="d0461-154">Focus Settings</span></span>
- [<span data-ttu-id="d0461-155">Configuración de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="d0461-156">Reglas de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="d0461-157">Configuración del puntero</span><span class="sxs-lookup"><span data-stu-id="d0461-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="d0461-158">Configuración de gestos</span><span class="sxs-lookup"><span data-stu-id="d0461-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="d0461-159">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="d0461-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="d0461-160">Configuración de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="d0461-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="d0461-161">Configuración de visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="d0461-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="d0461-162">Configuración de visualización de límites</span><span class="sxs-lookup"><span data-stu-id="d0461-162">Boundary visualization settings</span></span>

<span data-ttu-id="d0461-163">El sistema de límites traduce el límite percibido notificado por el sistema de protección o límite de las plataformas subyacentes.</span><span class="sxs-lookup"><span data-stu-id="d0461-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="d0461-164">La configuración del visualizador de límites le ofrece la capacidad de mostrar automáticamente el límite registrado dentro de la escena con respecto a la posición del usuario. El límite también reaccionará o actualizará en función de dónde se teleporte el usuario dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="d0461-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="d0461-165">Selección del sistema de teleportación</span><span class="sxs-lookup"><span data-stu-id="d0461-165">Teleportation system selection</span></span>

<span data-ttu-id="d0461-166">El Mixed Reality Project proporciona un sistema de teleportación completo para administrar eventos de teleportación en el proyecto que está seleccionado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="d0461-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="d0461-167">Configuración de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="d0461-167">Spatial awareness settings</span></span>

<span data-ttu-id="d0461-168">El Mixed Reality Project proporciona un sistema de reconocimiento espacial creado para trabajar con sistemas de análisis espacial en el proyecto que está seleccionado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="d0461-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="d0461-169">La Mixed Reality Toolkit de reconocimiento espacial permite adaptar cómo se inicia el sistema, ya sea automáticamente cuando se inicia la aplicación o posterior mediante programación, así como establecer las extensiones para el campo de vista.</span><span class="sxs-lookup"><span data-stu-id="d0461-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="d0461-170">También le permite configurar la malla y la superficie, personalizando aún más cómo el proyecto entiende el entorno que le rodea.</span><span class="sxs-lookup"><span data-stu-id="d0461-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="d0461-171">Esto solo es aplicable a los dispositivos que pueden proporcionar un entorno analizado.</span><span class="sxs-lookup"><span data-stu-id="d0461-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="d0461-172">Configuración de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d0461-172">Diagnostics settings</span></span>

<span data-ttu-id="d0461-173">Una característica opcional pero muy útil de MRTK es la funcionalidad de diagnóstico del complemento.</span><span class="sxs-lookup"><span data-stu-id="d0461-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="d0461-174">El perfil de diagnóstico proporciona varios sistemas sencillos para supervisar mientras se ejecuta el proyecto, incluido un práctico conmutador de encendido y apagado para habilitar o deshabilitar el panel de visualización en la escena.</span><span class="sxs-lookup"><span data-stu-id="d0461-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="d0461-175">Configuración del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="d0461-175">Scene system settings</span></span>

<span data-ttu-id="d0461-176">MRTK proporciona este servicio opcional para ayudarle a administrar la carga y descarga complejas de la escena aditiva.</span><span class="sxs-lookup"><span data-stu-id="d0461-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="d0461-177">Para decidir si scene system sería una buena opción para el proyecto, lea scene system Tareas iniciales Guide (Guía de configuración [del sistema de escena).](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="d0461-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="d0461-178">Configuración de servicios adicionales</span><span class="sxs-lookup"><span data-stu-id="d0461-178">Additional services settings</span></span>

<span data-ttu-id="d0461-179">Una de las áreas más avanzadas de [](https://en.wikipedia.org/wiki/Service_locator_pattern) la Mixed Reality Toolkit es su implementación del patrón de localizador de servicios, que permite el registro de cualquier "servicio" con el marco.</span><span class="sxs-lookup"><span data-stu-id="d0461-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="d0461-180">Esto permite ampliar el marco con nuevas características o sistemas fácilmente, pero también permite que los proyectos aprovechen estas funcionalidades para registrar sus propios componentes en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="d0461-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="d0461-181">Cualquier servicio registrado sigue aprovechando al máximo todos los eventos de Unity, sin la sobrecarga y el costo de implementar patrones monobehaviour o singleton desordenados.</span><span class="sxs-lookup"><span data-stu-id="d0461-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="d0461-182">Esto permite componentes de C# puros sin sobrecarga de escena para ejecutar procesos en primer plano y en segundo plano, por ejemplo, sistemas de generación, lógica de juego en tiempo de ejecución o prácticamente cualquier otra cosa.</span><span class="sxs-lookup"><span data-stu-id="d0461-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="d0461-183">Configuración de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-183">Input actions settings</span></span>

<span data-ttu-id="d0461-184">Las acciones de entrada proporcionan una manera de abstraer las interacciones físicas y las entradas de un proyecto en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="d0461-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="d0461-185">Toda la entrada física (de controladores, manos, mouse, etc.) se traduce en una acción de entrada lógica para su uso en el proyecto en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="d0461-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="d0461-186">Esto garantiza que, independientemente de dónde procede la entrada, el proyecto simplemente implementa estas acciones como "Cosas que hacer" o "Interactuar con" en las escenas.</span><span class="sxs-lookup"><span data-stu-id="d0461-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="d0461-187">Para crear una nueva acción de entrada, simplemente haga clic en el botón "Agregar una nueva acción" y escriba un nombre de texto descriptivo para lo que representa.</span><span class="sxs-lookup"><span data-stu-id="d0461-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="d0461-188">A continuación, solo necesita seleccionar un eje (el tipo de datos) que la acción está pensada para transmitir, o en el caso de los controladores físicos, el tipo de entrada física al que se puede adjuntar, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d0461-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="d0461-189">Restricción de eje</span><span class="sxs-lookup"><span data-stu-id="d0461-189">Axis Constraint</span></span> | <span data-ttu-id="d0461-190">Tipo de datos</span><span class="sxs-lookup"><span data-stu-id="d0461-190">Data Type</span></span> | <span data-ttu-id="d0461-191">Descripción</span><span class="sxs-lookup"><span data-stu-id="d0461-191">Description</span></span> | <span data-ttu-id="d0461-192">Ejemplo de uso</span><span class="sxs-lookup"><span data-stu-id="d0461-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="d0461-193">Ninguno</span><span class="sxs-lookup"><span data-stu-id="d0461-193">None</span></span> | <span data-ttu-id="d0461-194">Sin datos</span><span class="sxs-lookup"><span data-stu-id="d0461-194">No data</span></span> | <span data-ttu-id="d0461-195">Se usa para una acción o un evento vacíos</span><span class="sxs-lookup"><span data-stu-id="d0461-195">Used for an empty action or event</span></span> | <span data-ttu-id="d0461-196">Desencadenador de eventos</span><span class="sxs-lookup"><span data-stu-id="d0461-196">Event Trigger</span></span> |
| <span data-ttu-id="d0461-197">Sin procesar (reservado)</span><span class="sxs-lookup"><span data-stu-id="d0461-197">Raw (reserved)</span></span> | <span data-ttu-id="d0461-198">object</span><span class="sxs-lookup"><span data-stu-id="d0461-198">object</span></span> | <span data-ttu-id="d0461-199">Reservado para uso futuro</span><span class="sxs-lookup"><span data-stu-id="d0461-199">Reserved for future use</span></span> | <span data-ttu-id="d0461-200">N/D</span><span class="sxs-lookup"><span data-stu-id="d0461-200">N/A</span></span> |
| <span data-ttu-id="d0461-201">Digital</span><span class="sxs-lookup"><span data-stu-id="d0461-201">Digital</span></span> | <span data-ttu-id="d0461-202">bool</span><span class="sxs-lookup"><span data-stu-id="d0461-202">bool</span></span> | <span data-ttu-id="d0461-203">Datos de tipo booleanos on o off</span><span class="sxs-lookup"><span data-stu-id="d0461-203">A boolean on or off type data</span></span> | <span data-ttu-id="d0461-204">Un botón de controlador</span><span class="sxs-lookup"><span data-stu-id="d0461-204">A controller button</span></span> |
| <span data-ttu-id="d0461-205">Eje único</span><span class="sxs-lookup"><span data-stu-id="d0461-205">Single Axis</span></span> | <span data-ttu-id="d0461-206">FLOAT</span><span class="sxs-lookup"><span data-stu-id="d0461-206">float</span></span> | <span data-ttu-id="d0461-207">Un valor de datos de precisión única</span><span class="sxs-lookup"><span data-stu-id="d0461-207">A single precision data value</span></span> | <span data-ttu-id="d0461-208">Una entrada de intervalo, por ejemplo, un desencadenador</span><span class="sxs-lookup"><span data-stu-id="d0461-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="d0461-209">Eje dual</span><span class="sxs-lookup"><span data-stu-id="d0461-209">Dual Axis</span></span> | <span data-ttu-id="d0461-210">Vector2</span><span class="sxs-lookup"><span data-stu-id="d0461-210">Vector2</span></span> | <span data-ttu-id="d0461-211">Una fecha de tipo float dual para varios ejes</span><span class="sxs-lookup"><span data-stu-id="d0461-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="d0461-212">Un Dpad o thumbstick</span><span class="sxs-lookup"><span data-stu-id="d0461-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="d0461-213">Posición de tres dof</span><span class="sxs-lookup"><span data-stu-id="d0461-213">Three Dof Position</span></span> | <span data-ttu-id="d0461-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="d0461-214">Vector3</span></span> | <span data-ttu-id="d0461-215">Datos de tipo posicional de con 3 ejes flotantes</span><span class="sxs-lookup"><span data-stu-id="d0461-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="d0461-216">Controlador solo de estilo de posición 3D</span><span class="sxs-lookup"><span data-stu-id="d0461-216">3D position style only controller</span></span> |
| <span data-ttu-id="d0461-217">Rotación de tres dof</span><span class="sxs-lookup"><span data-stu-id="d0461-217">Three Dof Rotation</span></span> | <span data-ttu-id="d0461-218">Quaternion</span><span class="sxs-lookup"><span data-stu-id="d0461-218">Quaternion</span></span> | <span data-ttu-id="d0461-219">Entrada de solo rotación con 4 ejes flotantes</span><span class="sxs-lookup"><span data-stu-id="d0461-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="d0461-220">Un controlador de estilo de tres grados, por ejemplo, el controlador Oculus Go</span><span class="sxs-lookup"><span data-stu-id="d0461-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="d0461-221">Seis dof</span><span class="sxs-lookup"><span data-stu-id="d0461-221">Six Dof</span></span> | <span data-ttu-id="d0461-222">Mixed Reality Pose (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="d0461-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="d0461-223">Entrada de estilo de posición y rotación con los componentes Vector3 y Quaternion</span><span class="sxs-lookup"><span data-stu-id="d0461-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="d0461-224">Un controlador de movimiento o un puntero</span><span class="sxs-lookup"><span data-stu-id="d0461-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="d0461-225">Los eventos que usan acciones de entrada no se limitan a los controladores físicos y todavía se pueden usar en el proyecto para que los efectos en tiempo de ejecución generen nuevas acciones.</span><span class="sxs-lookup"><span data-stu-id="d0461-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="d0461-226">Las acciones de entrada son uno de los pocos componentes que no se pueden editar en tiempo de ejecución, son solo una configuración en tiempo de diseño.</span><span class="sxs-lookup"><span data-stu-id="d0461-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="d0461-227">Este perfil no se debe intercambiar mientras el proyecto se ejecuta debido a la dependencia del marco (y los proyectos) en los identificadores generados para cada acción.</span><span class="sxs-lookup"><span data-stu-id="d0461-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="d0461-228">Reglas de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="d0461-228">Input actions rules</span></span>

<span data-ttu-id="d0461-229">Las reglas de acción de entrada proporcionan una manera de traducir automáticamente un evento que se genera para una acción de entrada en a acciones diferentes en función de su valor de datos.</span><span class="sxs-lookup"><span data-stu-id="d0461-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="d0461-230">Estos se administran sin problemas dentro del marco de trabajo y no incurren en ningún costo de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="d0461-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="d0461-231">Por ejemplo, convertir el evento de entrada de eje dual único de un DPad en las 4 acciones "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" correspondientes (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="d0461-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="d0461-232">Esto también se puede hacer en su propio código.</span><span class="sxs-lookup"><span data-stu-id="d0461-232">This could also be done in your own code.</span></span> <span data-ttu-id="d0461-233">Sin embargo, al ver que se trata de un patrón muy común, el marco proporciona un mecanismo para hacerlo de forma "lista para usar".</span><span class="sxs-lookup"><span data-stu-id="d0461-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="d0461-234">Las reglas de acción de entrada se pueden configurar para cualquiera de los ejes de entrada disponibles.</span><span class="sxs-lookup"><span data-stu-id="d0461-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="d0461-235">Sin embargo, las acciones de entrada de un tipo de eje se pueden traducir a otra acción de entrada del mismo tipo de eje.</span><span class="sxs-lookup"><span data-stu-id="d0461-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="d0461-236">Puede asignar una acción de eje dual a otra acción de eje dual, pero no a una acción digital o ninguna.</span><span class="sxs-lookup"><span data-stu-id="d0461-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Perfil de reglas de acción de entrada](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="d0461-238">Configuración del puntero</span><span class="sxs-lookup"><span data-stu-id="d0461-238">Pointer configuration</span></span>

<span data-ttu-id="d0461-239">Los punteros se usan para impulsar la interactividad en la escena desde cualquier dispositivo de entrada, lo que da una dirección y una prueba de acceso con cualquier objeto de una escena (que tiene un colisionador asociado o es un componente de la interfaz de usuario).</span><span class="sxs-lookup"><span data-stu-id="d0461-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="d0461-240">De forma predeterminada, los punteros se configuran automáticamente para controladores, cascos (mirada/foco) y entrada táctil o de mouse.</span><span class="sxs-lookup"><span data-stu-id="d0461-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="d0461-241">Los punteros también se pueden visualizar dentro de la escena activa mediante uno de los muchos componentes de línea proporcionados por el Mixed Reality Toolkit o cualquiera de los suyos propios si implementan la interfaz IMixedRealityPointer de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d0461-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="d0461-242">Extensión de apuntar: determina la extensión de apuntar global para todos los punteros, incluida la mirada.</span><span class="sxs-lookup"><span data-stu-id="d0461-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="d0461-243">Máscaras de capa de Raycast que apuntan: determina con qué capas se van a convertir los punteros.</span><span class="sxs-lookup"><span data-stu-id="d0461-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="d0461-244">Debug Draw Pointing Ray: asistente de depuración para visualizar los rayos usados para la difusión de rayos.</span><span class="sxs-lookup"><span data-stu-id="d0461-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="d0461-245">Depurar los colores de los rayos de dibujo que apuntan: un conjunto de colores que se usarán para visualizar.</span><span class="sxs-lookup"><span data-stu-id="d0461-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="d0461-246">Prefab de cursor de mirada: facilita la especificación de un cursor de mirada global para cualquier escena.</span><span class="sxs-lookup"><span data-stu-id="d0461-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="d0461-247">Hay un botón auxiliar adicional para saltar rápidamente al proveedor de miradas para invalidar algunos valores específicos de Gaze si es necesario.</span><span class="sxs-lookup"><span data-stu-id="d0461-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="d0461-248">Configuración de gestos</span><span class="sxs-lookup"><span data-stu-id="d0461-248">Gestures configuration</span></span>

<span data-ttu-id="d0461-249">Los gestos son una implementación específica del sistema que permite asignar acciones de entrada a los distintos métodos de entrada "Gesto" proporcionados por varios SDK (por ejemplo, HoloLens).</span><span class="sxs-lookup"><span data-stu-id="d0461-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="d0461-250">La implementación actual de Gestos es solo para el HoloLens y se mejorará para otros sistemas a medida que se agregan al Toolkit en el futuro (aún no hay fechas).</span><span class="sxs-lookup"><span data-stu-id="d0461-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="d0461-251">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="d0461-251">Speech commands</span></span>

<span data-ttu-id="d0461-252">Al igual que los gestos, algunas plataformas en tiempo de ejecución también proporcionan funcionalidad "Speech to Text" inteligente con la capacidad de generar comandos que un proyecto de Unity puede recibir.</span><span class="sxs-lookup"><span data-stu-id="d0461-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="d0461-253">Este perfil de configuración permite configurar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d0461-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="d0461-254">El Configuración general: "Comportamiento de inicio" establecido en Inicio automático o Inicio manual determina si inicializar KeywordRecognizer al iniciar el sistema de entrada o dejar que el proyecto decida cuándo inicializar KeywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="d0461-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="d0461-255">"Nivel de confianza de reconocimiento" se usa para inicializar la [API KeywordRecognizer de](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity</span><span class="sxs-lookup"><span data-stu-id="d0461-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="d0461-256">Comandos de voz: registra "palabras" y las traduce en a acciones de entrada que el proyecto puede recibir.</span><span class="sxs-lookup"><span data-stu-id="d0461-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="d0461-257">También se pueden adjuntar a las acciones del teclado si es necesario.</span><span class="sxs-lookup"><span data-stu-id="d0461-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0461-258">Actualmente, el sistema solo admite voz cuando se ejecuta en plataformas de Windows 10, por ejemplo, un escritorio de HoloLens y Windows 10, y se mejorará para otros sistemas a medida que se agregan a MRTK en el futuro (aún no hay fechas).</span><span class="sxs-lookup"><span data-stu-id="d0461-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="d0461-259">Configuración de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="d0461-259">Controller mapping configuration</span></span>

<span data-ttu-id="d0461-260">Una de las pantallas de configuración principales de la Mixed Reality Toolkit es la capacidad de configurar y asignar los distintos tipos de controladores que puede usar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d0461-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="d0461-261">La pantalla de configuración siguiente permite configurar cualquiera de los controladores reconocidos actualmente por el kit de herramientas.</span><span class="sxs-lookup"><span data-stu-id="d0461-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="d0461-262">MRTK proporciona una configuración predeterminada para los siguientes controladores o sistemas:</span><span class="sxs-lookup"><span data-stu-id="d0461-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="d0461-263">Mouse (incluida la compatibilidad con el mouse espacial 3D)</span><span class="sxs-lookup"><span data-stu-id="d0461-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="d0461-264">Pantalla táctil</span><span class="sxs-lookup"><span data-stu-id="d0461-264">Touch Screen</span></span>
- <span data-ttu-id="d0461-265">Mandos de Xbox</span><span class="sxs-lookup"><span data-stu-id="d0461-265">Xbox controllers</span></span>
- <span data-ttu-id="d0461-266">Windows Mixed Reality controladores</span><span class="sxs-lookup"><span data-stu-id="d0461-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="d0461-267">HoloLens Gestos</span><span class="sxs-lookup"><span data-stu-id="d0461-267">HoloLens Gestures</span></span>
- <span data-ttu-id="d0461-268">CONTROLADORES DE WAND DE LA WAND DE SES VIVE</span><span class="sxs-lookup"><span data-stu-id="d0461-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="d0461-269">Controladores táctiles de Oculus</span><span class="sxs-lookup"><span data-stu-id="d0461-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="d0461-270">Controlador remoto de Oculus</span><span class="sxs-lookup"><span data-stu-id="d0461-270">Oculus Remote controller</span></span>
- <span data-ttu-id="d0461-271">Dispositivos OpenVR genéricos (solo usuarios avanzados)</span><span class="sxs-lookup"><span data-stu-id="d0461-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="d0461-272">Al hacer clic en la imagen de cualquiera de los sistemas de controlador pre built, puede configurar una sola acción de entrada para todas sus entradas correspondientes; por ejemplo, consulte la pantalla de configuración del controlador táctil de Oculus a continuación:</span><span class="sxs-lookup"><span data-stu-id="d0461-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="d0461-273">También hay una pantalla avanzada para configurar otros controladores de entrada de OpenVR o Unity que no se han identificado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d0461-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="d0461-274">Configuración de visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="d0461-274">Controller visualization settings</span></span>

<span data-ttu-id="d0461-275">Además de la asignación del controlador, se proporciona un perfil de configuración independiente para personalizar cómo se presentan los controladores en sus escenas.</span><span class="sxs-lookup"><span data-stu-id="d0461-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="d0461-276">Esto se puede configurar en un "Global" (todas las instancias de un controlador para una mano específica) o específico de un tipo de controlador o mano individual.</span><span class="sxs-lookup"><span data-stu-id="d0461-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="d0461-277">MRTK también admite modelos de controlador de SDK nativos para Windows Mixed Reality y OpenVR.</span><span class="sxs-lookup"><span data-stu-id="d0461-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="d0461-278">Se cargan como GameObjects en la escena y se posicionan mediante el seguimiento del controlador de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="d0461-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="d0461-279">Si la representación del controlador en la escena debe desplazarse desde la posición del controlador físico, simplemente establezca ese desplazamiento con respecto al elemento prefab del modelo del controlador (por ejemplo, establecer la posición de transformación del prefab del controlador con una posición de desplazamiento).</span><span class="sxs-lookup"><span data-stu-id="d0461-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="d0461-280">Utilidades del editor</span><span class="sxs-lookup"><span data-stu-id="d0461-280">Editor utilities</span></span>

<span data-ttu-id="d0461-281">Las utilidades siguientes solo funcionan en el editor y son útiles para mejorar la productividad del desarrollo.</span><span class="sxs-lookup"><span data-stu-id="d0461-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilidades de configuración del editor de MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="d0461-283">Inspectores de servicio</span><span class="sxs-lookup"><span data-stu-id="d0461-283">Service inspectors</span></span>

<span data-ttu-id="d0461-284">Los inspectores de servicio son una característica solo del editor que genera objetos en escena que representan servicios activos.</span><span class="sxs-lookup"><span data-stu-id="d0461-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="d0461-285">Al seleccionar estos objetos se muestran inspectores que ofrecen vínculos de documentación, control sobre las visualizaciones del editor e información sobre el estado del servicio.</span><span class="sxs-lookup"><span data-stu-id="d0461-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="d0461-286">Para habilitar los inspectores de servicio, *active Usar inspectores* de servicio en *Editor Configuración* el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="d0461-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="d0461-287">Representador de búfer de profundidad</span><span class="sxs-lookup"><span data-stu-id="d0461-287">Depth buffer renderer</span></span>

<span data-ttu-id="d0461-288">Compartir el búfer de profundidad con algunas plataformas de realidad mixta puede mejorar la [estabilización del holograma.](../performance/hologram-stabilization.md)</span><span class="sxs-lookup"><span data-stu-id="d0461-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="d0461-289">Por ejemplo, la plataforma de Windows Mixed Reality puede modificar la escena representada por píxel para tener en cuenta los movimientos sutiles de la cabeza durante el tiempo que se tardó en representar un fotograma.</span><span class="sxs-lookup"><span data-stu-id="d0461-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="d0461-290">Sin embargo, estas técnicas requieren búferes de profundidad con datos precisos para saber dónde y a qué distancia está la geometría del usuario.</span><span class="sxs-lookup"><span data-stu-id="d0461-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="d0461-291">Para asegurarse de que una escena representa todos los  datos necesarios en el búfer de profundidad, los desarrolladores pueden alternar la característica Búfer de profundidad de *representación en* Editor Configuración en el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="d0461-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="d0461-292">Esto tomará el búfer de profundidad actual y lo representará como color en la vista de escena aplicando un efecto posterior al procesamiento, , a [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="d0461-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="d0461-293">![Utilidad de búfer de profundidad de representación El cilindro azul de la escena tiene un ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>material con ZWrite</sup> desactivado para que no se escriban datos de profundidad</span><span class="sxs-lookup"><span data-stu-id="d0461-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="d0461-294">Cambio de perfiles en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="d0461-294">Changing profiles at runtime</span></span>

<span data-ttu-id="d0461-295">Es posible actualizar perfiles en tiempo de ejecución y, por lo general, hay dos escenarios y horas diferentes en los que esto resulta útil:</span><span class="sxs-lookup"><span data-stu-id="d0461-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="d0461-296">Modificador de perfil de inicialización de **MRTK** anterior: en el inicio, antes de inicializar MRTK y de que el perfil se active, reemplazando el perfil que aún no está en uso para habilitar o deshabilitar diferentes características en función de las funcionalidades del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d0461-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="d0461-297">Por ejemplo, si la experiencia se ejecuta en REALIDAD virtual que no tiene hardware de asignación espacial, probablemente no tenga sentido tener habilitado el componente de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="d0461-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="d0461-298">**Conmutador de perfil** activo: después del inicio, después de inicializar MRTK y de que se haya activado un perfil, cambie el perfil actualmente en uso para cambiar la forma en que se comportan determinadas características.</span><span class="sxs-lookup"><span data-stu-id="d0461-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="d0461-299">Por ejemplo, puede haber una sub experiencia específica en la aplicación que quiera quitar completamente los punteros de mano lejanos.</span><span class="sxs-lookup"><span data-stu-id="d0461-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="d0461-300">Modificador de perfil de inicialización de MRTK anterior</span><span class="sxs-lookup"><span data-stu-id="d0461-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="d0461-301">Esto se puede lograr adjuntando un monobehaviour (ejemplo siguiente) que se ejecuta antes de la inicialización de MRTK (es decir, con el estado Activo()).</span><span class="sxs-lookup"><span data-stu-id="d0461-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="d0461-302">Tenga en cuenta que el script (es decir, llamar a ) debe ejecutarse antes que el script, lo que se puede lograr estableciendo la configuración del orden `SetProfileBeforeInitialization` `MixedRealityToolkit` de ejecución del [script.](https://docs.unity3d.com/Manual/class-MonoManager.html)</span><span class="sxs-lookup"><span data-stu-id="d0461-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="d0461-303">En lugar de "profileToUse", es posible tener un conjunto arbitrario de perfiles que se aplican a plataformas específicas (por ejemplo, uno para HoloLens 1, otro para VR, otro para HoloLens 2, etc.).</span><span class="sxs-lookup"><span data-stu-id="d0461-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="d0461-304">Es posible usar otros indicadores (por ejemplo, , o si la cámara es opaca o transparente), para averiguar qué perfil https://docs.unity3d.com/ScriptReference/SystemInfo.html cargar.</span><span class="sxs-lookup"><span data-stu-id="d0461-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="d0461-305">Conmutador de perfil activo</span><span class="sxs-lookup"><span data-stu-id="d0461-305">Active profile switch</span></span>

<span data-ttu-id="d0461-306">Esto se puede lograr estableciendo la `MixedRealityToolkit.Instance.ActiveProfile` propiedad en un nuevo perfil reemplazando el perfil activo.</span><span class="sxs-lookup"><span data-stu-id="d0461-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="d0461-307">Tenga en cuenta que, al establecer durante el tiempo de ejecución, la destrucción de los servicios en ejecución se realizará después de la última lateupdate() de todos los servicios y la creación de instancias e inicialización de los servicios asociados con el nuevo perfil se realizará antes de la primera update() de todos los `ActiveProfile` servicios.</span><span class="sxs-lookup"><span data-stu-id="d0461-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="d0461-308">Durante este proceso puede producirse una indeseación apreciable en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d0461-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="d0461-309">Además, cualquier script con mayor prioridad que el script puede escribir su actualización antes de `MixedRealityToolkit` que el nuevo perfil se configure correctamente.</span><span class="sxs-lookup"><span data-stu-id="d0461-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="d0461-310">Consulte [Configuración del orden de ejecución del script](https://docs.unity3d.com/Manual/class-MonoManager.html) para obtener más información sobre la prioridad del script.</span><span class="sxs-lookup"><span data-stu-id="d0461-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="d0461-311">En el proceso de cambio de perfil, la cámara de interfaz de usuario existente permanecerá sin cambios, lo que garantiza que los componentes de la interfaz de usuario de Unity que requieren lienzo sigan funcionando después del cambio.</span><span class="sxs-lookup"><span data-stu-id="d0461-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0461-312">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d0461-312">See also</span></span>

- [<span data-ttu-id="d0461-313">Estabilización de hologramas</span><span class="sxs-lookup"><span data-stu-id="d0461-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)
