---
title: Guía de configuración de Mixed Reality
description: Documentación para configurar MRTK en Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: fc97a2d7c6182b4836d644d91be237e2aef01feb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143578"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="bebff-104">guía de configuración de perfiles de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="bebff-104">Mixed Reality Toolkit profile configuration guide</span></span>

![Logotipo de MRTK](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="bebff-106">El Mixed Reality toolkit centraliza la mayor parte de la configuración necesaria para administrar el kit de herramientas lo más posible (excepto para las verdaderas "cosas" en tiempo de ejecución).</span><span class="sxs-lookup"><span data-stu-id="bebff-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="bebff-107">Esta guía es un tutorial sencillo para cada una de las pantallas de perfil de configuración disponibles actualmente para el kit de herramientas.</span><span class="sxs-lookup"><span data-stu-id="bebff-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="bebff-108">El perfil de configuración Mixed Reality Toolkit principal</span><span class="sxs-lookup"><span data-stu-id="bebff-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="bebff-109">El perfil de configuración principal, que se adjunta a *MixedRealityToolkit* GameObject en la escena, proporciona el punto de entrada principal para el kit de herramientas en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="bebff-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="bebff-110">El kit de herramientas de Mixed Reality "bloquea" las pantallas de configuración predeterminadas para asegurarse de que siempre tiene un punto de inicio común para el proyecto y se recomienda empezar a definir su propia configuración a medida que evoluciona el proyecto.</span><span class="sxs-lookup"><span data-stu-id="bebff-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="bebff-111">La configuración de MRTK no se puede editar durante el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="bebff-111">The MRTK configuration is not editable during play-mode.</span></span>

![Perfil de configuración de MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="bebff-113">Todos los perfiles "predeterminados" de Mixed Reality Toolkit se pueden encontrar en el proyecto sdk en la carpeta Assets/MRTK/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="bebff-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bebff-114">DefaultHoloLens2ConfigurationProfile está optimizado para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bebff-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="bebff-115">Consulte [Perfiles para](../features/profiles/profiles.md) obtener más información.</span><span class="sxs-lookup"><span data-stu-id="bebff-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="bebff-116">Al abrir el perfil de configuración Mixed Reality Toolkit, verá la siguiente pantalla en el inspector:</span><span class="sxs-lookup"><span data-stu-id="bebff-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="bebff-117">Si selecciona un recurso MixedRealityToolkitConfigurationProfile sin MixedRealityToolkit en la escena, se le preguntará si desea que MRTK configure automáticamente la escena.</span><span class="sxs-lookup"><span data-stu-id="bebff-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="bebff-118">Sin embargo, esto es opcional, debe haber un objeto MixedRealityToolkit activo en la escena para acceder a todas las pantallas de configuración.</span><span class="sxs-lookup"><span data-stu-id="bebff-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="bebff-119">Esto aloja la configuración actual del entorno de ejecución activo para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="bebff-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="bebff-120">Desde aquí puede navegar a todos los perfiles de configuración de MRTK, incluidos:</span><span class="sxs-lookup"><span data-stu-id="bebff-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="bebff-121">guía de configuración de perfiles de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="bebff-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="bebff-122">El perfil de configuración Mixed Reality Toolkit principal</span><span class="sxs-lookup"><span data-stu-id="bebff-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="bebff-123">Configuración de la experiencia</span><span class="sxs-lookup"><span data-stu-id="bebff-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="bebff-124">Configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="bebff-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="bebff-125">Configuración del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="bebff-126">Configuración de visualización de límites</span><span class="sxs-lookup"><span data-stu-id="bebff-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="bebff-127">Selección del sistema de teleportación</span><span class="sxs-lookup"><span data-stu-id="bebff-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="bebff-128">Configuración de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="bebff-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="bebff-129">Configuración de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="bebff-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="bebff-130">Configuración del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="bebff-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="bebff-131">Configuración de servicios adicionales</span><span class="sxs-lookup"><span data-stu-id="bebff-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="bebff-132">Configuración de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="bebff-133">Reglas de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="bebff-134">Configuración del puntero</span><span class="sxs-lookup"><span data-stu-id="bebff-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="bebff-135">Configuración de gestos</span><span class="sxs-lookup"><span data-stu-id="bebff-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="bebff-136">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="bebff-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="bebff-137">Configuración de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="bebff-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="bebff-138">Configuración de visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="bebff-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="bebff-139">Utilidades del editor</span><span class="sxs-lookup"><span data-stu-id="bebff-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="bebff-140">Inspectores de servicio</span><span class="sxs-lookup"><span data-stu-id="bebff-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="bebff-141">Representador de búfer de profundidad</span><span class="sxs-lookup"><span data-stu-id="bebff-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="bebff-142">Cambio de perfiles en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="bebff-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="bebff-143">Modificador de perfil de inicialización de MRTK anterior</span><span class="sxs-lookup"><span data-stu-id="bebff-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="bebff-144">Conmutador de perfil activo</span><span class="sxs-lookup"><span data-stu-id="bebff-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="bebff-145">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bebff-145">See also</span></span>](#see-also)

<span data-ttu-id="bebff-146">Estos perfiles de configuración se detallan a continuación en sus secciones pertinentes:</span><span class="sxs-lookup"><span data-stu-id="bebff-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="bebff-147">Configuración de la experiencia</span><span class="sxs-lookup"><span data-stu-id="bebff-147">Experience settings</span></span>

<span data-ttu-id="bebff-148">En la página principal de Mixed Reality Toolkit, esta configuración define el funcionamiento predeterminado de la escala de Mixed Reality [del](/windows/mixed-reality/coordinate-systems-in-unity) proyecto.</span><span class="sxs-lookup"><span data-stu-id="bebff-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="bebff-149">Configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="bebff-149">Camera settings</span></span>

<span data-ttu-id="bebff-150">La configuración de la cámara define cómo se configurará la cámara para el proyecto de Mixed Reality, definiendo la configuración genérica de recorte, calidad y transparencia.</span><span class="sxs-lookup"><span data-stu-id="bebff-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="bebff-151">Configuración del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-151">Input system settings</span></span>

<span data-ttu-id="bebff-152">El Mixed Reality proyecto proporciona un sistema de entrada sólido y bien entrenado para enrutar todos los eventos de entrada alrededor del proyecto que está seleccionado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bebff-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="bebff-153">Detrás del sistema de entrada proporcionado por MRTK hay otros sistemas, que ayudan a impulsar y administrar las complejas intercalaciones necesarias para abstraer las complejidades de un marco de trabajo multiplataforma o de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="bebff-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="bebff-154">Cada uno de los perfiles individuales se detalla a continuación:</span><span class="sxs-lookup"><span data-stu-id="bebff-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="bebff-155">Configuración del foco</span><span class="sxs-lookup"><span data-stu-id="bebff-155">Focus Settings</span></span>
- [<span data-ttu-id="bebff-156">Configuración de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="bebff-157">Reglas de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="bebff-158">Configuración del puntero</span><span class="sxs-lookup"><span data-stu-id="bebff-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="bebff-159">Configuración de gestos</span><span class="sxs-lookup"><span data-stu-id="bebff-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="bebff-160">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="bebff-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="bebff-161">Configuración de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="bebff-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="bebff-162">Configuración de visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="bebff-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="bebff-163">Configuración de visualización de límites</span><span class="sxs-lookup"><span data-stu-id="bebff-163">Boundary visualization settings</span></span>

<span data-ttu-id="bebff-164">El sistema de límites traduce el límite percibido notificado por el sistema de protección o límite de las plataformas subyacentes.</span><span class="sxs-lookup"><span data-stu-id="bebff-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="bebff-165">La configuración del visualizador de límites le ofrece la capacidad de mostrar automáticamente el límite registrado dentro de la escena con respecto a la posición del usuario. El límite también reaccionará o actualizará en función de dónde se teleporte el usuario dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="bebff-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="bebff-166">Selección del sistema de teleportación</span><span class="sxs-lookup"><span data-stu-id="bebff-166">Teleportation system selection</span></span>

<span data-ttu-id="bebff-167">El Mixed Reality project proporciona un sistema de teleportación completo para administrar eventos de teleportación en el proyecto que está seleccionado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bebff-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="bebff-168">Configuración de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="bebff-168">Spatial awareness settings</span></span>

<span data-ttu-id="bebff-169">El Mixed Reality project proporciona un sistema de reconocimiento espacial creado para trabajar con sistemas de examen espacial en el proyecto que está seleccionado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bebff-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="bebff-170">La configuración de reconocimiento espacial del kit de herramientas de Mixed Reality le permite adaptar cómo se inicia el sistema, tanto si se inicia automáticamente cuando se inicia la aplicación o posterior mediante programación, como al establecer las extensiones del campo de vista.</span><span class="sxs-lookup"><span data-stu-id="bebff-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="bebff-171">También le permite configurar la malla y la superficie, personalizando aún más cómo el proyecto entiende el entorno que le rodea.</span><span class="sxs-lookup"><span data-stu-id="bebff-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="bebff-172">Esto solo es aplicable a los dispositivos que pueden proporcionar un entorno analizado.</span><span class="sxs-lookup"><span data-stu-id="bebff-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="bebff-173">Configuración de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="bebff-173">Diagnostics settings</span></span>

<span data-ttu-id="bebff-174">Una característica opcional pero muy útil de MRTK es la funcionalidad de diagnóstico del complemento.</span><span class="sxs-lookup"><span data-stu-id="bebff-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="bebff-175">El perfil de diagnóstico proporciona varios sistemas sencillos para supervisar mientras se ejecuta el proyecto, incluido un práctico conmutador de encendido y apagado para habilitar o deshabilitar el panel de visualización en la escena.</span><span class="sxs-lookup"><span data-stu-id="bebff-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="bebff-176">Configuración del sistema de escena</span><span class="sxs-lookup"><span data-stu-id="bebff-176">Scene system settings</span></span>

<span data-ttu-id="bebff-177">MRTK proporciona este servicio opcional para ayudarle a administrar la carga y descarga complejas de la escena de adición.</span><span class="sxs-lookup"><span data-stu-id="bebff-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="bebff-178">Para decidir si scene system sería una buena opción para el proyecto, lea scene system Tareas iniciales Guide (Guía de configuración [del sistema de Tareas iniciales escena).](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="bebff-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="bebff-179">Configuración de servicios adicionales</span><span class="sxs-lookup"><span data-stu-id="bebff-179">Additional services settings</span></span>

<span data-ttu-id="bebff-180">Una de las áreas más avanzadas de Mixed Reality [](https://en.wikipedia.org/wiki/Service_locator_pattern) Toolkit es su implementación de patrón de localizador de servicios que permite el registro de cualquier "servicio" con el marco.</span><span class="sxs-lookup"><span data-stu-id="bebff-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="bebff-181">Esto permite ampliar el marco con nuevas características o sistemas fácilmente, pero también permite que los proyectos aprovechen estas funcionalidades para registrar sus propios componentes en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bebff-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="bebff-182">Cualquier servicio registrado sigue aprovechando al máximo todos los eventos de Unity, sin la sobrecarga y el costo de implementar patrones monobehaviour o singleton desordenados.</span><span class="sxs-lookup"><span data-stu-id="bebff-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="bebff-183">Esto permite componentes de C# puros sin sobrecarga de escena para ejecutar procesos en primer plano y en segundo plano, por ejemplo, generación de sistemas, lógica de juego en tiempo de ejecución o prácticamente cualquier otra cosa.</span><span class="sxs-lookup"><span data-stu-id="bebff-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="bebff-184">Configuración de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-184">Input actions settings</span></span>

<span data-ttu-id="bebff-185">Las acciones de entrada proporcionan una manera de abstraer las interacciones físicas y las entradas de un proyecto en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bebff-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="bebff-186">Toda la entrada física (de controladores, manos, mouse, etc.) se traduce en una acción de entrada lógica para su uso en el proyecto en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bebff-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="bebff-187">Esto garantiza que, independientemente de dónde procede la entrada, el proyecto simplemente implementa estas acciones como "Cosas que hacer" o "Interactuar con" en sus escenas.</span><span class="sxs-lookup"><span data-stu-id="bebff-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="bebff-188">Para crear una nueva acción de entrada, simplemente haga clic en el botón "Agregar una nueva acción" y escriba un nombre de texto descriptivo para lo que representa.</span><span class="sxs-lookup"><span data-stu-id="bebff-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="bebff-189">A continuación, solo necesita seleccionar un eje (el tipo de datos) que la acción está pensada para transmitir, o en el caso de los controladores físicos, el tipo de entrada física al que se puede adjuntar, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bebff-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="bebff-190">Restricción de eje</span><span class="sxs-lookup"><span data-stu-id="bebff-190">Axis Constraint</span></span> | <span data-ttu-id="bebff-191">Tipo de datos</span><span class="sxs-lookup"><span data-stu-id="bebff-191">Data Type</span></span> | <span data-ttu-id="bebff-192">Descripción</span><span class="sxs-lookup"><span data-stu-id="bebff-192">Description</span></span> | <span data-ttu-id="bebff-193">Ejemplo de uso</span><span class="sxs-lookup"><span data-stu-id="bebff-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="bebff-194">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bebff-194">None</span></span> | <span data-ttu-id="bebff-195">Sin datos</span><span class="sxs-lookup"><span data-stu-id="bebff-195">No data</span></span> | <span data-ttu-id="bebff-196">Se usa para una acción o un evento vacíos.</span><span class="sxs-lookup"><span data-stu-id="bebff-196">Used for an empty action or event</span></span> | <span data-ttu-id="bebff-197">Desencadenador de eventos</span><span class="sxs-lookup"><span data-stu-id="bebff-197">Event Trigger</span></span> |
| <span data-ttu-id="bebff-198">Sin formato (reservado)</span><span class="sxs-lookup"><span data-stu-id="bebff-198">Raw (reserved)</span></span> | <span data-ttu-id="bebff-199">object</span><span class="sxs-lookup"><span data-stu-id="bebff-199">object</span></span> | <span data-ttu-id="bebff-200">Reservado para uso futuro</span><span class="sxs-lookup"><span data-stu-id="bebff-200">Reserved for future use</span></span> | <span data-ttu-id="bebff-201">N/D</span><span class="sxs-lookup"><span data-stu-id="bebff-201">N/A</span></span> |
| <span data-ttu-id="bebff-202">Digital</span><span class="sxs-lookup"><span data-stu-id="bebff-202">Digital</span></span> | <span data-ttu-id="bebff-203">bool</span><span class="sxs-lookup"><span data-stu-id="bebff-203">bool</span></span> | <span data-ttu-id="bebff-204">Datos de tipo booleanos de entrada o de salida</span><span class="sxs-lookup"><span data-stu-id="bebff-204">A boolean on or off type data</span></span> | <span data-ttu-id="bebff-205">Un botón de controlador</span><span class="sxs-lookup"><span data-stu-id="bebff-205">A controller button</span></span> |
| <span data-ttu-id="bebff-206">Eje único</span><span class="sxs-lookup"><span data-stu-id="bebff-206">Single Axis</span></span> | <span data-ttu-id="bebff-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="bebff-207">float</span></span> | <span data-ttu-id="bebff-208">Un valor de datos de precisión única</span><span class="sxs-lookup"><span data-stu-id="bebff-208">A single precision data value</span></span> | <span data-ttu-id="bebff-209">Una entrada de intervalo, por ejemplo, un desencadenador</span><span class="sxs-lookup"><span data-stu-id="bebff-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="bebff-210">Eje dual</span><span class="sxs-lookup"><span data-stu-id="bebff-210">Dual Axis</span></span> | <span data-ttu-id="bebff-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="bebff-211">Vector2</span></span> | <span data-ttu-id="bebff-212">Una fecha de tipo float dual para varios ejes</span><span class="sxs-lookup"><span data-stu-id="bebff-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="bebff-213">Un Dpad o thumbstick</span><span class="sxs-lookup"><span data-stu-id="bebff-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="bebff-214">Posición de tres dof</span><span class="sxs-lookup"><span data-stu-id="bebff-214">Three Dof Position</span></span> | <span data-ttu-id="bebff-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="bebff-215">Vector3</span></span> | <span data-ttu-id="bebff-216">Datos de tipo posicional de con 3 ejes flotantes</span><span class="sxs-lookup"><span data-stu-id="bebff-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="bebff-217">Controlador solo de estilo de posición 3D</span><span class="sxs-lookup"><span data-stu-id="bebff-217">3D position style only controller</span></span> |
| <span data-ttu-id="bebff-218">Rotación de tres dof</span><span class="sxs-lookup"><span data-stu-id="bebff-218">Three Dof Rotation</span></span> | <span data-ttu-id="bebff-219">Quaternion</span><span class="sxs-lookup"><span data-stu-id="bebff-219">Quaternion</span></span> | <span data-ttu-id="bebff-220">Entrada de solo rotación con 4 ejes flotantes</span><span class="sxs-lookup"><span data-stu-id="bebff-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="bebff-221">Un controlador de estilo de tres grados, por ejemplo, el controlador Oculus Go</span><span class="sxs-lookup"><span data-stu-id="bebff-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="bebff-222">Seis dof</span><span class="sxs-lookup"><span data-stu-id="bebff-222">Six Dof</span></span> | <span data-ttu-id="bebff-223">Mixed Reality Pose (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="bebff-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="bebff-224">Entrada de estilo de posición y rotación con los componentes Vector3 y Quaternion</span><span class="sxs-lookup"><span data-stu-id="bebff-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="bebff-225">Un controlador de movimiento o un puntero</span><span class="sxs-lookup"><span data-stu-id="bebff-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="bebff-226">Los eventos que usan acciones de entrada no se limitan a los controladores físicos y todavía se pueden usar en el proyecto para que los efectos en tiempo de ejecución generen nuevas acciones.</span><span class="sxs-lookup"><span data-stu-id="bebff-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="bebff-227">Las acciones de entrada son uno de los pocos componentes que no se pueden editar en tiempo de ejecución, son solo una configuración en tiempo de diseño.</span><span class="sxs-lookup"><span data-stu-id="bebff-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="bebff-228">Este perfil no se debe intercambiar mientras el proyecto se ejecuta debido a la dependencia del marco (y los proyectos) en los identificadores generados para cada acción.</span><span class="sxs-lookup"><span data-stu-id="bebff-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="bebff-229">Reglas de acciones de entrada</span><span class="sxs-lookup"><span data-stu-id="bebff-229">Input actions rules</span></span>

<span data-ttu-id="bebff-230">Las reglas de acción de entrada proporcionan una manera de traducir automáticamente un evento que se genera para una acción de entrada en a acciones diferentes en función de su valor de datos.</span><span class="sxs-lookup"><span data-stu-id="bebff-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="bebff-231">Estos se administran sin problemas dentro del marco de trabajo y no incurren en ningún costo de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bebff-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="bebff-232">Por ejemplo, convertir el evento de entrada de eje dual único de un DPad en las 4 acciones "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" correspondientes (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="bebff-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="bebff-233">Esto también se puede hacer en su propio código.</span><span class="sxs-lookup"><span data-stu-id="bebff-233">This could also be done in your own code.</span></span> <span data-ttu-id="bebff-234">Sin embargo, al ver que se trata de un patrón muy común, el marco proporciona un mecanismo para hacerlo "de forma lista".</span><span class="sxs-lookup"><span data-stu-id="bebff-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="bebff-235">Las reglas de acción de entrada se pueden configurar para cualquiera de los ejes de entrada disponibles.</span><span class="sxs-lookup"><span data-stu-id="bebff-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="bebff-236">Sin embargo, las acciones de entrada de un tipo de eje se pueden traducir a otra acción de entrada del mismo tipo de eje.</span><span class="sxs-lookup"><span data-stu-id="bebff-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="bebff-237">Puede asignar una acción de eje dual a otra acción de eje dual, pero no a una acción digital o ninguna.</span><span class="sxs-lookup"><span data-stu-id="bebff-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Perfil de reglas de acción de entrada](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="bebff-239">Configuración de puntero</span><span class="sxs-lookup"><span data-stu-id="bebff-239">Pointer configuration</span></span>

<span data-ttu-id="bebff-240">Los punteros se usan para impulsar la interactividad en la escena desde cualquier dispositivo de entrada, lo que da una dirección y una prueba de posición con cualquier objeto de una escena (que tiene un colisionador asociado o es un componente de la interfaz de usuario).</span><span class="sxs-lookup"><span data-stu-id="bebff-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="bebff-241">De forma predeterminada, los punteros se configuran automáticamente para controladores, cascos (mirada/foco) y entrada táctil o de mouse.</span><span class="sxs-lookup"><span data-stu-id="bebff-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="bebff-242">Los punteros también se pueden visualizar dentro de la escena activa mediante uno de los muchos componentes de línea proporcionados por el kit de herramientas de Mixed Reality, o cualquiera de los suyos propios si implementan la interfaz de MRTK IMixedRealityPointer.</span><span class="sxs-lookup"><span data-stu-id="bebff-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="bebff-243">Pointing Extent (Extensión de apuntar): determina la extensión global que apunta a todos los punteros, incluida la mirada.</span><span class="sxs-lookup"><span data-stu-id="bebff-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="bebff-244">Apuntar máscaras de capa de rayas: determina las capas con las que se van a convertir los punteros.</span><span class="sxs-lookup"><span data-stu-id="bebff-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="bebff-245">Debug Draw Pointing Ray: un asistente de depuración para visualizar los rayos usados para la difusión de rayos.</span><span class="sxs-lookup"><span data-stu-id="bebff-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="bebff-246">Depurar colores de rayos de dibujo que apuntan: un conjunto de colores que se usarán para la visualización.</span><span class="sxs-lookup"><span data-stu-id="bebff-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="bebff-247">Prefab de cursor de mirada: facilita la especificación de un cursor de mirada global para cualquier escena.</span><span class="sxs-lookup"><span data-stu-id="bebff-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="bebff-248">Hay un botón auxiliar adicional para saltar rápidamente al proveedor de miradas para invalidar algunos valores específicos de Mirada si es necesario.</span><span class="sxs-lookup"><span data-stu-id="bebff-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="bebff-249">Configuración de gestos</span><span class="sxs-lookup"><span data-stu-id="bebff-249">Gestures configuration</span></span>

<span data-ttu-id="bebff-250">Los gestos son una implementación específica del sistema que permite asignar acciones de entrada a los distintos métodos de entrada "Gesto" proporcionados por varios SDK (por ejemplo, HoloLens).</span><span class="sxs-lookup"><span data-stu-id="bebff-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="bebff-251">La implementación actual de Gestos es solo para HoloLens y se mejorará para otros sistemas a medida que se agregan al kit de herramientas en el futuro (todavía no hay fechas).</span><span class="sxs-lookup"><span data-stu-id="bebff-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="bebff-252">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="bebff-252">Speech commands</span></span>

<span data-ttu-id="bebff-253">Al igual que los gestos, algunas plataformas en tiempo de ejecución también proporcionan funcionalidad "Speech to Text" inteligente con la capacidad de generar comandos que un proyecto de Unity puede recibir.</span><span class="sxs-lookup"><span data-stu-id="bebff-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="bebff-254">Este perfil de configuración le permite configurar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="bebff-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="bebff-255">Configuración general: "Comportamiento de inicio" establecido en Inicio automático o Inicio manual determina si inicializar KeywordRecognizer al iniciar el sistema de entrada o dejar que el proyecto decida cuándo inicializar keywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="bebff-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="bebff-256">"Nivel de confianza de reconocimiento" se usa para inicializar la [API KeywordRecognizer de](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity</span><span class="sxs-lookup"><span data-stu-id="bebff-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="bebff-257">Comandos de voz: registra "palabras" y las traduce en a acciones de entrada que el proyecto puede recibir.</span><span class="sxs-lookup"><span data-stu-id="bebff-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="bebff-258">También se pueden adjuntar a las acciones de teclado si es necesario.</span><span class="sxs-lookup"><span data-stu-id="bebff-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bebff-259">Actualmente, el sistema solo admite voz cuando se ejecuta en plataformas de Windows 10, por ejemplo, HoloLens y Windows 10 Desktop, y se mejorará para otros sistemas a medida que se agregan a MRTK en el futuro (aún no hay fechas).</span><span class="sxs-lookup"><span data-stu-id="bebff-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="bebff-260">Configuración de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="bebff-260">Controller mapping configuration</span></span>

<span data-ttu-id="bebff-261">Una de las pantallas de configuración principales de Mixed Reality Toolkit es la capacidad de configurar y asignar los distintos tipos de controladores que puede usar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="bebff-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="bebff-262">La pantalla de configuración siguiente permite configurar cualquiera de los controladores reconocidos actualmente por el kit de herramientas.</span><span class="sxs-lookup"><span data-stu-id="bebff-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="bebff-263">MRTK proporciona una configuración predeterminada para los siguientes controladores o sistemas:</span><span class="sxs-lookup"><span data-stu-id="bebff-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="bebff-264">Mouse (incluida la compatibilidad con el mouse espacial 3D)</span><span class="sxs-lookup"><span data-stu-id="bebff-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="bebff-265">Pantalla táctil</span><span class="sxs-lookup"><span data-stu-id="bebff-265">Touch Screen</span></span>
- <span data-ttu-id="bebff-266">Mandos de Xbox</span><span class="sxs-lookup"><span data-stu-id="bebff-266">Xbox controllers</span></span>
- <span data-ttu-id="bebff-267">Windows Mixed Reality controladores</span><span class="sxs-lookup"><span data-stu-id="bebff-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="bebff-268">Gestos de HoloLens</span><span class="sxs-lookup"><span data-stu-id="bebff-268">HoloLens Gestures</span></span>
- <span data-ttu-id="bebff-269">CONTROLADORES DE WAND DE LA WAND DE LA PROGRAMACIÓN</span><span class="sxs-lookup"><span data-stu-id="bebff-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="bebff-270">Controladores táctiles de Oculus</span><span class="sxs-lookup"><span data-stu-id="bebff-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="bebff-271">Controlador remoto de Oculus</span><span class="sxs-lookup"><span data-stu-id="bebff-271">Oculus Remote controller</span></span>
- <span data-ttu-id="bebff-272">Dispositivos OpenVR genéricos (solo usuarios avanzados)</span><span class="sxs-lookup"><span data-stu-id="bebff-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="bebff-273">Al hacer clic en la imagen de cualquiera de los sistemas de controlador pre built, puede configurar una sola acción de entrada para todas sus entradas correspondientes; por ejemplo, consulte la pantalla de configuración del controlador táctil de Oculus a continuación:</span><span class="sxs-lookup"><span data-stu-id="bebff-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="bebff-274">También hay una pantalla avanzada para configurar otros controladores de entrada de OpenVR o Unity que no se han identificado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="bebff-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="bebff-275">Configuración de visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="bebff-275">Controller visualization settings</span></span>

<span data-ttu-id="bebff-276">Además de la asignación del controlador, se proporciona un perfil de configuración independiente para personalizar cómo se presentan los controladores en sus escenas.</span><span class="sxs-lookup"><span data-stu-id="bebff-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="bebff-277">Esto se puede configurar en un "Global" (todas las instancias de un controlador para una mano específica) o específico de un tipo de controlador individual o mano.</span><span class="sxs-lookup"><span data-stu-id="bebff-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="bebff-278">MRTK también admite modelos de controlador de SDK nativos para Windows Mixed Reality y OpenVR.</span><span class="sxs-lookup"><span data-stu-id="bebff-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="bebff-279">Se cargan como GameObjects en la escena y se posicionan mediante el seguimiento del controlador de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="bebff-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="bebff-280">Si es necesario desplazar la representación del controlador en la escena de la posición del controlador físico, basta con establecer ese desplazamiento con respecto al objeto prefab del modelo del controlador (por ejemplo, establecer la posición de transformación del objeto prefab del controlador con una posición de desplazamiento).</span><span class="sxs-lookup"><span data-stu-id="bebff-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="bebff-281">Utilidades del editor</span><span class="sxs-lookup"><span data-stu-id="bebff-281">Editor utilities</span></span>

<span data-ttu-id="bebff-282">Las utilidades siguientes solo funcionan en el editor y son útiles para mejorar la productividad del desarrollo.</span><span class="sxs-lookup"><span data-stu-id="bebff-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilidades de configuración del editor de MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="bebff-284">Inspectores de servicio</span><span class="sxs-lookup"><span data-stu-id="bebff-284">Service inspectors</span></span>

<span data-ttu-id="bebff-285">Los inspectores de servicio son una característica solo de editor que genera objetos en escena que representan servicios activos.</span><span class="sxs-lookup"><span data-stu-id="bebff-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="bebff-286">Al seleccionar estos objetos se muestran inspectores que ofrecen vínculos de documentación, control sobre las visualizaciones del editor e información sobre el estado del servicio.</span><span class="sxs-lookup"><span data-stu-id="bebff-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="bebff-287">Para habilitar los inspectores de servicio, *active Usar inspectores de servicio* en Configuración del *editor* en el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="bebff-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="bebff-288">Representador de búfer de profundidad</span><span class="sxs-lookup"><span data-stu-id="bebff-288">Depth buffer renderer</span></span>

<span data-ttu-id="bebff-289">Compartir el búfer de profundidad con algunas plataformas de realidad mixta puede mejorar la [estabilización del holograma.](../performance/hologram-stabilization.md)</span><span class="sxs-lookup"><span data-stu-id="bebff-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="bebff-290">Por ejemplo, la plataforma Windows Mixed Reality puede modificar la escena representado por píxel para tener en cuenta los movimientos sutiles de la cabeza durante el tiempo que se tardó en representar un fotograma.</span><span class="sxs-lookup"><span data-stu-id="bebff-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="bebff-291">Sin embargo, estas técnicas requieren búferes de profundidad con datos precisos para saber dónde y qué distancia está la geometría del usuario.</span><span class="sxs-lookup"><span data-stu-id="bebff-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="bebff-292">Para asegurarse de que una escena representa todos los datos necesarios en el búfer de profundidad, los desarrolladores pueden alternar la característica Búfer de profundidad de *representación* en Configuración del *editor* en el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="bebff-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="bebff-293">Esto tomará el búfer de profundidad actual y lo representará como color en la vista de escena aplicando un efecto posterior al procesamiento, , a [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="bebff-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="bebff-294">![Utilidad de búfer de profundidad de representación El cilindro azul de la escena tiene un material con ZWrite desactivado para que no se escriban ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>datos de profundidad.</sup></span><span class="sxs-lookup"><span data-stu-id="bebff-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="bebff-295">Cambio de perfiles en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="bebff-295">Changing profiles at runtime</span></span>

<span data-ttu-id="bebff-296">Es posible actualizar perfiles en tiempo de ejecución y, por lo general, hay dos escenarios y horas diferentes en los que esto resulta útil:</span><span class="sxs-lookup"><span data-stu-id="bebff-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="bebff-297">Modificador de perfil de inicialización de **MRTK** anterior: en el inicio, antes de inicializar MRTK y de que el perfil se active, reemplazando el perfil que aún no está en uso para habilitar o deshabilitar diferentes características en función de las funcionalidades del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bebff-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="bebff-298">Por ejemplo, si la experiencia se ejecuta en REALIDAD virtual que no tiene hardware de asignación espacial, probablemente no tenga sentido tener habilitado el componente de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="bebff-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="bebff-299">**Conmutador de perfil** activo: después del inicio, después de inicializar MRTK y de que un perfil se haya activado, cambie el perfil actualmente en uso para cambiar la forma en que se comportan determinadas características.</span><span class="sxs-lookup"><span data-stu-id="bebff-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="bebff-300">Por ejemplo, puede haber una sub experiencia específica en la aplicación que quiera quitar completamente los punteros de mano lejanos.</span><span class="sxs-lookup"><span data-stu-id="bebff-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="bebff-301">Modificador de perfil de inicialización de MRTK anterior</span><span class="sxs-lookup"><span data-stu-id="bebff-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="bebff-302">Esto se puede lograr asociando un monobehaviour (ejemplo siguiente) que se ejecuta antes de la inicialización de MRTK (es decir, con El activo()).</span><span class="sxs-lookup"><span data-stu-id="bebff-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="bebff-303">Tenga en cuenta que el script (es decir, llamar a ) debe ejecutarse antes que el script, lo que se puede lograr estableciendo la configuración del orden `SetProfileBeforeInitialization` `MixedRealityToolkit` de ejecución del [script.](https://docs.unity3d.com/Manual/class-MonoManager.html)</span><span class="sxs-lookup"><span data-stu-id="bebff-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="bebff-304">En lugar de "profileToUse", es posible tener un conjunto arbitrario de perfiles que se aplican a plataformas específicas (por ejemplo, uno para HoloLens 1, otro para VR, otro para HoloLens 2, etc.).</span><span class="sxs-lookup"><span data-stu-id="bebff-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="bebff-305">Es posible usar otros indicadores (por ejemplo, , o si la cámara es opaca o transparente), para averiguar qué perfil se va https://docs.unity3d.com/ScriptReference/SystemInfo.html a cargar.</span><span class="sxs-lookup"><span data-stu-id="bebff-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="bebff-306">Conmutador de perfil activo</span><span class="sxs-lookup"><span data-stu-id="bebff-306">Active profile switch</span></span>

<span data-ttu-id="bebff-307">Esto se puede lograr estableciendo la `MixedRealityToolkit.Instance.ActiveProfile` propiedad en un nuevo perfil reemplazando el perfil activo.</span><span class="sxs-lookup"><span data-stu-id="bebff-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="bebff-308">Tenga en cuenta que al establecer durante el tiempo de ejecución, la destrucción de los servicios actualmente en ejecución se realizará después de la última LateUpdate() de todos los servicios, y la creación de instancias e inicialización de los servicios asociados con el nuevo perfil se realizará antes de la primera Update() de todos los `ActiveProfile` servicios.</span><span class="sxs-lookup"><span data-stu-id="bebff-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="bebff-309">Durante este proceso puede producirse un evidente duda de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bebff-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="bebff-310">Además, cualquier script con mayor prioridad que el script puede escribir su actualización antes de `MixedRealityToolkit` que el nuevo perfil se configure correctamente.</span><span class="sxs-lookup"><span data-stu-id="bebff-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="bebff-311">Consulte Configuración [del orden de ejecución del script](https://docs.unity3d.com/Manual/class-MonoManager.html) para obtener más información sobre la prioridad del script.</span><span class="sxs-lookup"><span data-stu-id="bebff-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="bebff-312">En el proceso de cambio de perfil, la cámara de interfaz de usuario existente permanecerá sin cambios, lo que garantiza que los componentes de la interfaz de usuario de Unity que requieren lienzo siguen funcionando después del cambio.</span><span class="sxs-lookup"><span data-stu-id="bebff-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="bebff-313">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bebff-313">See also</span></span>

- [<span data-ttu-id="bebff-314">Estabilización de hologramas</span><span class="sxs-lookup"><span data-stu-id="bebff-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)