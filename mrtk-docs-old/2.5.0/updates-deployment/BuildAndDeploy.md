---
title: BuildAndDeploy
description: Documentación para compilar e implementar aplicaciones en varios dispositivos.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: cbf17cfd463ee375d285a36aef1705b4d911107f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687435"
---
# <a name="building-and-deploying-mrtk"></a><span data-ttu-id="d8e16-104">Compilación e implementación de MRTK</span><span class="sxs-lookup"><span data-stu-id="d8e16-104">Building and deploying MRTK</span></span>

<span data-ttu-id="d8e16-105">Para ejecutar una aplicación en un dispositivo como aplicación independiente (para HoloLens, Android, iOS, etc.), el paso de compilación e implementación debe ejecutarse en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="d8e16-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="d8e16-106">Compilar e implementar una aplicación que usa MRTK es como compilar e implementar cualquier otra aplicación de Unity.</span><span class="sxs-lookup"><span data-stu-id="d8e16-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="d8e16-107">No hay instrucciones específicas para MRTK.</span><span class="sxs-lookup"><span data-stu-id="d8e16-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="d8e16-108">Siga leyendo para obtener información detallada sobre los pasos para compilar e implementar una aplicación de Unity para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d8e16-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span>  <span data-ttu-id="d8e16-109">Obtenga más información sobre la compilación para otras plataformas en [Publicación de compilaciones](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="d8e16-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a><span data-ttu-id="d8e16-110">Compilación e implementación de MRTK en HoloLens 1 y HoloLens 2 (UWP)</span><span class="sxs-lookup"><span data-stu-id="d8e16-110">Building and deploying MRTK to HoloLens 1 and HoloLens 2 (UWP)</span></span>

<span data-ttu-id="d8e16-111">Puede encontrar instrucciones sobre cómo compilar e implementar para HoloLens 1 y HoloLens 2 (UWP) en [Compilación de la aplicación en el dispositivo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="d8e16-111">Instructions on how to build and deploy for HoloLens 1 and HoloLens 2 (UWP) can be found at [building your application to device](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span>

<span data-ttu-id="d8e16-112">**Sugerencia:** Al compilar para WMR, HoloLens 1 o HoloLens 2, se recomienda que la configuración de la compilación en cuanto a versión del SDK de destino y versión mínima de la plataforma tenga un aspecto similar al de la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="d8e16-112">**Tip:** When building for WMR, HoloLens 1, or HoloLens 2, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Ventana de compilación](../features/Images/getting_started/BuildWindow.png)

<span data-ttu-id="d8e16-114">El resto de opciones de configuración pueden ser diferentes (p. ej., Configuración de compilación/Arquitectura/Tipo de compilación y otras opciones se pueden cambiar dentro de la solución de Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="d8e16-114">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="d8e16-115">Asegúrese de que la lista desplegable de versión de SDK de destino incluya la opción "10.0.18362.0". En caso contrario, es necesario instalar el [Windows SDK más reciente](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="d8e16-115">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="d8e16-116">Unity 2019.3 y HoloLens</span><span class="sxs-lookup"><span data-stu-id="d8e16-116">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="d8e16-117">Si una aplicación de HoloLens aparece como un panel 2D en el dispositivo, asegúrese de que se han configurado las opciones siguientes en Unity 2019.3.x antes de implementar la aplicación para UWP:</span><span class="sxs-lookup"><span data-stu-id="d8e16-117">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="d8e16-118">Si usa una versión de XR heredada:</span><span class="sxs-lookup"><span data-stu-id="d8e16-118">If using the legacy XR:</span></span>

1. <span data-ttu-id="d8e16-119">Vaya a Edit > Project Settings, Player (Editar > Configuración del proyecto, Jugador)</span><span class="sxs-lookup"><span data-stu-id="d8e16-119">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="d8e16-120">En **XR Settings** (Configuración de XR) en la pestaña UWP, asegúrese de que la opción **Virtual Reality Supported** (Compatible con realidad virtual) está habilitada y de que el SDK de **Windows Mixed Reality** se ha agregado a los SDK.</span><span class="sxs-lookup"><span data-stu-id="d8e16-120">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="d8e16-121">Compilación e implementación en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8e16-121">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="d8e16-122">Si usa el complemento XR:</span><span class="sxs-lookup"><span data-stu-id="d8e16-122">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="d8e16-123">Siga los pasos que encontrará en [Introducción a XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span><span class="sxs-lookup"><span data-stu-id="d8e16-123">Follow the steps found in [Getting Started with XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span></span>
1. <span data-ttu-id="d8e16-124">Asegúrese de que el perfil de configuración sea **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="d8e16-124">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="d8e16-125">Vaya a **Edit > Project Settings, XR-Plugin Management** (Editar > Configuración del proyecto, Administración del complemento XR) y asegúrese de que **Windows Mixed Reality** está habilitado.</span><span class="sxs-lookup"><span data-stu-id="d8e16-125">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="d8e16-126">Compilación e implementación en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8e16-126">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d8e16-127">Si usa Unity 2019.3.x, seleccione **ARM64** y no **ARM** como arquitectura de compilación en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8e16-127">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d8e16-128">Con la configuración predeterminada de Unity en Unity 2019.3.x, una aplicación de Unity no se implementará en HoloLens si se selecciona ARM debido a un error de Unity.</span><span class="sxs-lookup"><span data-stu-id="d8e16-128">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="d8e16-129">Se puede hacer un seguimiento de esto desde el [seguimiento de problemas de Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d8e16-129">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="d8e16-130">Si se requiere la arquitectura de ARM, vaya a **Edit > Project Settings, Player** (Editar > Configuración del proyecto, Jugador) y, en el menú **Other Settings** (Otras opciones) , deshabilite **Graphics Jobs** (Trabajos de gráficos).</span><span class="sxs-lookup"><span data-stu-id="d8e16-130">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="d8e16-131">Al deshabilitar **Graphics Jobs** (Trabajos de gráficos) permitirá que la aplicación se implemente con la arquitectura de compilación de ARM para Unity 2019.3.x, pero se recomienda ARM64.</span><span class="sxs-lookup"><span data-stu-id="d8e16-131">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a><span data-ttu-id="d8e16-132">Creación e implementación de MRTK en un casco de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d8e16-132">Building and deploying MRTK to a Windows Mixed Reality Headset</span></span>

<span data-ttu-id="d8e16-133">El casco de Windows Mixed Reality (WMR) se puede usar para la Plataforma universal de Windows (UWP) y en compilaciones independientes.</span><span class="sxs-lookup"><span data-stu-id="d8e16-133">The Windows Mixed Reality (WMR) headset can be used for Universal Windows Platform (UWP) and Standalone builds.</span></span>  <span data-ttu-id="d8e16-134">Una compilación independiente para un casco de WMR requiere los siguientes pasos adicionales:</span><span class="sxs-lookup"><span data-stu-id="d8e16-134">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="d8e16-135">El SDK de XR de Unity también admite WMR nativo en compilaciones independientes, pero no requiere el complemento SteamVR o WMR.</span><span class="sxs-lookup"><span data-stu-id="d8e16-135">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="d8e16-136">Estos pasos son necesarios para la versión de XR heredada de Unity.</span><span class="sxs-lookup"><span data-stu-id="d8e16-136">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="d8e16-137">Instalación de [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="d8e16-137">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="d8e16-138">Instalación de [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="d8e16-138">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="d8e16-139">Instalación del [complemento de WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="d8e16-139">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="d8e16-140">Uso del complemento de MWR</span><span class="sxs-lookup"><span data-stu-id="d8e16-140">How to use WMR plugin</span></span>

1. <span data-ttu-id="d8e16-141">Abra Steam y busque el complemento de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d8e16-141">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="d8e16-142">Compruebe que SteamVR esté cerrado antes de iniciar el complemento de WMR.</span><span class="sxs-lookup"><span data-stu-id="d8e16-142">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="d8e16-143">Al iniciar el complemento de WMR, también se inicia SteamVR.</span><span class="sxs-lookup"><span data-stu-id="d8e16-143">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="d8e16-144">Asegúrese de que el casco de WMR está conectado.</span><span class="sxs-lookup"><span data-stu-id="d8e16-144">Make sure the WMR headset is plugged in.</span></span>

    ![Búsqueda de complementos de WMR](../features/Images/BuildDeploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="d8e16-146">Seleccione **Launch** (Iniciar) para Windows Mixed Reality para el complemento SteamVR.</span><span class="sxs-lookup"><span data-stu-id="d8e16-146">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Complemento de WMR](../features/Images/BuildDeploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="d8e16-148">Se iniciará SteamVR y el complemento de WMR y aparecerá una nueva ventana de estado de seguimiento para el casco de WMR.</span><span class="sxs-lookup"><span data-stu-id="d8e16-148">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="d8e16-149">Para obtener más información, visite la [documentación de Steam de Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="d8e16-149">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Aspecto de inicio de WMR](../features/Images/BuildDeploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="d8e16-151">En Unity, con la escena de MRTK abierta, vaya a **File > Build Settings** (Archivo > Configuración de la compilación).</span><span class="sxs-lookup"><span data-stu-id="d8e16-151">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="d8e16-152">Compilación de la escena</span><span class="sxs-lookup"><span data-stu-id="d8e16-152">Build the scene</span></span>
    - <span data-ttu-id="d8e16-153">Seleccione **Add Open Scene** (Agregar escena abierta).</span><span class="sxs-lookup"><span data-stu-id="d8e16-153">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="d8e16-154">Asegúrese de que la plataforma sea **Standalone** (Independiente).</span><span class="sxs-lookup"><span data-stu-id="d8e16-154">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="d8e16-155">Seleccione **Build** (Compilar).</span><span class="sxs-lookup"><span data-stu-id="d8e16-155">Select **Build**</span></span>
    - <span data-ttu-id="d8e16-156">Elija la ubicación de la nueva compilación en el Explorador de archivos</span><span class="sxs-lookup"><span data-stu-id="d8e16-156">Choose the location for the new build in File Explorer</span></span>

    ![Configuración de compilación para plataformas independientes](../features/Images/BuildDeploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="d8e16-158">Se creará un nuevo archivo ejecutable de Unity. Para iniciar la aplicación, selecciónelo en el Explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="d8e16-158">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity en el Explorador de archivos](../features/Images/BuildDeploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="d8e16-160">Vea también</span><span class="sxs-lookup"><span data-stu-id="d8e16-160">See also</span></span>

- [<span data-ttu-id="d8e16-161">Compatibilidad con Android y iOS</span><span class="sxs-lookup"><span data-stu-id="d8e16-161">Android and iOS Support</span></span>](../features/CrossPlatform/UsingARFoundation.md)
- [<span data-ttu-id="d8e16-162">Compatibilidad con el movimiento Leap</span><span class="sxs-lookup"><span data-stu-id="d8e16-162">Leap Motion Support</span></span>](../features/CrossPlatform/LeapMotionMRTK.md)
- [<span data-ttu-id="d8e16-163">Detección de las capacidades de la plataforma</span><span class="sxs-lookup"><span data-stu-id="d8e16-163">Detecting Platform Capabilities</span></span>](../features/DetectingPlatformCapabilities.md)
