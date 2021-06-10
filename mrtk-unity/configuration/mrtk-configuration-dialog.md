---
title: Cuadro de diálogo de configuración de MRTK
description: Configuración de MRTK en el proyecto de Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345098"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="daad7-104">Cuadro de diálogo de configuración del proyecto de MRTK</span><span class="sxs-lookup"><span data-stu-id="daad7-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="daad7-105">El cuadro de diálogo de configuración de MRTK se muestra cuando Unity carga un proyecto y se determina que una o varias opciones de configuración necesitan la atención del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="daad7-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Aplicar ignore posterior](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="daad7-107">Para aplicar los cambios, haga clic en **el botón** Aplicar.</span><span class="sxs-lookup"><span data-stu-id="daad7-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="daad7-108">El **botón** Más adelante aplazará los cambios hasta que el proyecto se vuelva a cargar en un momento futuro.</span><span class="sxs-lookup"><span data-stu-id="daad7-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="daad7-109">El cuadro de diálogo de configuración volverá a aparecer si se deja desactivada una o varias de las opciones recomendadas.</span><span class="sxs-lookup"><span data-stu-id="daad7-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="daad7-110">Para evitar que esto ocurra, aplique las opciones deseadas y, a continuación, vuelva a iniciar el cuadro de diálogo a través de utilidades de **Mixed Reality Toolkit** Configure Unity Project (Configurar proyecto de  >    >  **Unity)** y haga clic **en Omitir**.</span><span class="sxs-lookup"><span data-stu-id="daad7-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="daad7-111">Esto impedirá que el cuadro de diálogo de configuración vuelva a aparecer automáticamente.</span><span class="sxs-lookup"><span data-stu-id="daad7-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="daad7-112">Configuración común</span><span class="sxs-lookup"><span data-stu-id="daad7-112">Common settings</span></span>

<span data-ttu-id="daad7-113">Todos los destinos de compilación comparten una colección de opciones comunes.</span><span class="sxs-lookup"><span data-stu-id="daad7-113">All build targets share a collection of common options.</span></span>

![Configuración común](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="daad7-115">Forzar la serialización de recursos de texto y Habilitar metadatos visibles</span><span class="sxs-lookup"><span data-stu-id="daad7-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="daad7-116">Esta configuración ayuda a simplificar el trabajo con proyectos de Unity y sistemas de control de código fuente (por ejemplo, Git).</span><span class="sxs-lookup"><span data-stu-id="daad7-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="daad7-117">Habilitación de VR compatible</span><span class="sxs-lookup"><span data-stu-id="daad7-117">Enable VR supported</span></span>

<span data-ttu-id="daad7-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="daad7-118">**Unity 2018**</span></span>

<span data-ttu-id="daad7-119">Configura las opciones Del SDK de Virtual Reality Compatible y Virtual Reality en **Configuración del** reproductor Configuración  >  **de XR.**</span><span class="sxs-lookup"><span data-stu-id="daad7-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="daad7-120">Establecer la ruta de acceso de representación de instancia de paso único</span><span class="sxs-lookup"><span data-stu-id="daad7-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="daad7-121">Configura la configuración del **reproductor XR** Settings Stereo Rendering Mode (Modo de representación estéreo de configuración de  >  **XR)**  >   en Single **Pass Instanced (Instancia de paso único).**</span><span class="sxs-lookup"><span data-stu-id="daad7-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="daad7-122">Establecer la capa de reconocimiento espacial predeterminada</span><span class="sxs-lookup"><span data-stu-id="daad7-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="daad7-123">Registra el reconocimiento espacial como nivel 31 para permitir una configuración sencilla y coherente de las opciones de difusión por rayos y física.</span><span class="sxs-lookup"><span data-stu-id="daad7-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="daad7-124">Espacializador de audio</span><span class="sxs-lookup"><span data-stu-id="daad7-124">Audio spatializer</span></span>

<span data-ttu-id="daad7-125">Los espacializadores de audio son los componentes que desbloquean la potencia del sonido espacial y el audio posicional para que las experiencias de realidad mixta sean realmente envolventes.</span><span class="sxs-lookup"><span data-stu-id="daad7-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="daad7-126">Si establece el espacializador de audio en Ninguno, se deshabilitarán las características de audio posicionales.</span><span class="sxs-lookup"><span data-stu-id="daad7-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="daad7-127">Espacializadores comunes</span><span class="sxs-lookup"><span data-stu-id="daad7-127">Common spatializers</span></span>

- <span data-ttu-id="daad7-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="daad7-128">Microsoft Spatializer</span></span>

<span data-ttu-id="daad7-129">Espacializador proporcionado por Microsoft que admite el uso de la aceleración de hardware en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="daad7-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="daad7-130">Este espacializador está disponible a través [de NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) y [GitHub.](https://github.com/microsoft/spatialaudio-unity)</span><span class="sxs-lookup"><span data-stu-id="daad7-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="daad7-131">Puede encontrar más detalles sobre Microsoft Spatializer en la documentación [de sonido espacial](/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="daad7-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="daad7-132">Espacializador HRTF de MS</span><span class="sxs-lookup"><span data-stu-id="daad7-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="daad7-133">Espacializador de Microsoft Windows proporcionado por Unity como parte de los paquetes Windows Mixed Reality y windows XR Platform.</span><span class="sxs-lookup"><span data-stu-id="daad7-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="daad7-134">Audio desaía</span><span class="sxs-lookup"><span data-stu-id="daad7-134">Resonance Audio</span></span>

<span data-ttu-id="daad7-135">Espacializador multiplataforma de Google proporcionado por Unity.</span><span class="sxs-lookup"><span data-stu-id="daad7-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="daad7-136">Puede encontrar más información en el sitio de documentación [de Audio de resalte.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)</span><span class="sxs-lookup"><span data-stu-id="daad7-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="daad7-137">Plataforma universal de Windows configuración</span><span class="sxs-lookup"><span data-stu-id="daad7-137">Universal Windows Platform settings</span></span>

![Configuración de UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="daad7-139">Funcionalidades de UWP</span><span class="sxs-lookup"><span data-stu-id="daad7-139">UWP Capabilities</span></span>

<span data-ttu-id="daad7-140">Habilita funcionalidades de aplicación específicas para Plataforma universal de Windows aplicación.</span><span class="sxs-lookup"><span data-stu-id="daad7-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="daad7-141">Estas funcionalidades permiten a la plataforma informar y solicitar permiso para habilitar una funcionalidad específica.</span><span class="sxs-lookup"><span data-stu-id="daad7-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="daad7-142">Micrófono</span><span class="sxs-lookup"><span data-stu-id="daad7-142">Microphone</span></span>

  <span data-ttu-id="daad7-143">Habilita la captura de sonido a través del micrófono.</span><span class="sxs-lookup"><span data-stu-id="daad7-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="daad7-144">Cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="daad7-144">Internet Client</span></span>

  <span data-ttu-id="daad7-145">Habilita la compatibilidad con el acceso a los recursos en Internet.</span><span class="sxs-lookup"><span data-stu-id="daad7-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="daad7-146">Percepción espacial</span><span class="sxs-lookup"><span data-stu-id="daad7-146">Spatial Perception</span></span>

  <span data-ttu-id="daad7-147">Habilita la compatibilidad con el uso del entorno real.</span><span class="sxs-lookup"><span data-stu-id="daad7-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="daad7-148">Mirada con los ojos</span><span class="sxs-lookup"><span data-stu-id="daad7-148">Eye Gaze</span></span>

  <span data-ttu-id="daad7-149">**Unity 2019.3 y versiones más recientes**</span><span class="sxs-lookup"><span data-stu-id="daad7-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="daad7-150">Habilita la compatibilidad para realizar el seguimiento de la mirada con los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="daad7-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="daad7-151">Evitar el bloqueo "PlayerSettings.graphicsJob" de Unity</span><span class="sxs-lookup"><span data-stu-id="daad7-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="daad7-152">**Unity 2019.3 y versiones más recientes**</span><span class="sxs-lookup"><span data-stu-id="daad7-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="daad7-153">En la versión más reciente de Unity 2019, cuando se habilita "Trabajos de gráficos", la aplicación se bloqueará cuando se implemente en un HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="daad7-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="daad7-154">Esta configuración está habilitada de forma predeterminada en Unity: aunque este error existe (consulte Error de [Unity),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)el configurador establecerá de forma predeterminada trabajos de gráficos en "false" (lo que permite que las aplicaciones implementadas en HoloLens 2 no se bloquean).</span><span class="sxs-lookup"><span data-stu-id="daad7-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="daad7-155">Configuración de Android</span><span class="sxs-lookup"><span data-stu-id="daad7-155">Android settings</span></span>

<span data-ttu-id="daad7-156">Opciones de configuración para admitir aplicaciones de AR en dispositivos con tecnología Android.</span><span class="sxs-lookup"><span data-stu-id="daad7-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Configuración de Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="daad7-158">Deshabilitar la representación multiproceso</span><span class="sxs-lookup"><span data-stu-id="daad7-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="daad7-159">Deshabilita la **configuración del reproductor Otra**  >  **configuración**  >  **Representación multiproceso** según sea necesario para la compatibilidad con AR de Android.</span><span class="sxs-lookup"><span data-stu-id="daad7-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="daad7-160">Establecer el nivel mínimo de API</span><span class="sxs-lookup"><span data-stu-id="daad7-160">Set Minimum API Level</span></span>

<span data-ttu-id="daad7-161">Establece el valor de Configuración del **reproductor** Otro  >  **nivel** mínimo  >  **de API para** aplicar los requisitos del sistema operativo para las aplicaciones de AR.</span><span class="sxs-lookup"><span data-stu-id="daad7-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="daad7-162">Configuración de iOS</span><span class="sxs-lookup"><span data-stu-id="daad7-162">iOS settings</span></span>

<span data-ttu-id="daad7-163">Opciones de configuración para admitir aplicaciones ar en dispositivos con tecnología iOS.</span><span class="sxs-lookup"><span data-stu-id="daad7-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Configuración de iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="daad7-165">Establecer la versión necesaria del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="daad7-165">Set Required OS Version</span></span>

<span data-ttu-id="daad7-166">Establece el valor de Configuración del **reproductor**  >  **Otras configuraciones** Versión mínima de  >  **iOS para** aplicar los requisitos del sistema operativo para las aplicaciones de AR.</span><span class="sxs-lookup"><span data-stu-id="daad7-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="daad7-167">Establecer la arquitectura necesaria</span><span class="sxs-lookup"><span data-stu-id="daad7-167">Set Required Architecture</span></span>

<span data-ttu-id="daad7-168">Establece el valor de Configuración del **reproductor** Otra  >  **arquitectura de configuración**  >  **para** aplicar los requisitos de plataforma para las aplicaciones de AR.</span><span class="sxs-lookup"><span data-stu-id="daad7-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="daad7-169">Establecer descripciones de uso de la cámara</span><span class="sxs-lookup"><span data-stu-id="daad7-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="daad7-170">Establece el valor de Player **Settings** Other Settings Camera Usage Description (Configuración del reproductor Descripción del uso de la cámara de configuración que se usa para solicitar  >    >   permiso para usar la cámara del dispositivo).</span><span class="sxs-lookup"><span data-stu-id="daad7-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>