---
title: Implementación en cascos Hololens y WMR
description: Documentación para compilar e implementar aplicaciones en varios dispositivos.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Visual Studio
ms.openlocfilehash: 1547f0630d307e9e87505890adef4cad366d6c00
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441157"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="fe715-104">Implementación en cascos Hololens y WMR</span><span class="sxs-lookup"><span data-stu-id="fe715-104">Deploying to Hololens and WMR headsets</span></span>

<span data-ttu-id="fe715-105">Hay dos maneras de implementar aplicaciones compiladas con MRTK en el dispositivo Windows, la Plataforma univeral de Windows (UWP) y la Plataforma independiente.</span><span class="sxs-lookup"><span data-stu-id="fe715-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="fe715-106">Las aplicaciones compiladas para HoloLens 1 o HoloLens 2 deben tener como destino UWP, mientras que las aplicaciones creadas para cascos WMR pueden tener como destino UWP o independiente.</span><span class="sxs-lookup"><span data-stu-id="fe715-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="fe715-107">Compilación e implementación de MRTK en HoloLens 1, HoloLens 2 y cascos WMR (UWP)</span><span class="sxs-lookup"><span data-stu-id="fe715-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="fe715-108">Puede encontrar instrucciones sobre cómo compilar e implementar **para HoloLens 1** **y HoloLens 2** (UWP) en Compilación de la aplicación en [el dispositivo](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="fe715-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="fe715-109">Estos pasos también le permiten implementar en **cascos WMR.**</span><span class="sxs-lookup"><span data-stu-id="fe715-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="fe715-110">Al implementar la aplicación en el dispositivo en Visual Studio, debe configurar Visual Studio de forma ligeramente diferente en función del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fe715-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="fe715-111">Las configuraciones son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="fe715-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="fe715-112">Plataforma</span><span class="sxs-lookup"><span data-stu-id="fe715-112">Platform</span></span> | <span data-ttu-id="fe715-113">Configuración</span><span class="sxs-lookup"><span data-stu-id="fe715-113">Configuration</span></span> | <span data-ttu-id="fe715-114">Architecture</span><span class="sxs-lookup"><span data-stu-id="fe715-114">Architecture</span></span> | <span data-ttu-id="fe715-115">Destino</span><span class="sxs-lookup"><span data-stu-id="fe715-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="fe715-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fe715-116">HoloLens 2</span></span> | <span data-ttu-id="fe715-117">Versión o maestra</span><span class="sxs-lookup"><span data-stu-id="fe715-117">Release or Master</span></span> | <span data-ttu-id="fe715-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="fe715-118">ARM64</span></span> | <span data-ttu-id="fe715-119">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="fe715-119">Device</span></span> |
| <span data-ttu-id="fe715-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="fe715-120">HoloLens 1</span></span> | <span data-ttu-id="fe715-121">Versión o maestra</span><span class="sxs-lookup"><span data-stu-id="fe715-121">Release or Master</span></span> | <span data-ttu-id="fe715-122">x86</span><span class="sxs-lookup"><span data-stu-id="fe715-122">x86</span></span> | <span data-ttu-id="fe715-123">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="fe715-123">Device</span></span> |
| <span data-ttu-id="fe715-124">Cascos WMR</span><span class="sxs-lookup"><span data-stu-id="fe715-124">WMR Headsets</span></span> | <span data-ttu-id="fe715-125">Versión o maestra</span><span class="sxs-lookup"><span data-stu-id="fe715-125">Release or Master</span></span> | <span data-ttu-id="fe715-126">x64</span><span class="sxs-lookup"><span data-stu-id="fe715-126">x64</span></span> | <span data-ttu-id="fe715-127">Equipo local</span><span class="sxs-lookup"><span data-stu-id="fe715-127">Local Machine</span></span> |

<span data-ttu-id="fe715-128">**Sugerencia:** Al compilar para HoloLens 1, HoloLens 2 o WMR, se recomienda que los valores de compilación "Versión del SDK de destino" y "Versión mínima de la plataforma" se parezcan a los de la siguiente imagen:</span><span class="sxs-lookup"><span data-stu-id="fe715-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Ventana de compilación](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="fe715-130">El resto de opciones de configuración pueden ser diferentes (p. ej., Configuración de compilación/Arquitectura/Tipo de compilación y otras opciones se pueden cambiar dentro de la solución de Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="fe715-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="fe715-131">Asegúrese de que la lista desplegable de versión de SDK de destino incluya la opción "10.0.18362.0". En caso contrario, es necesario instalar el [Windows SDK más reciente](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="fe715-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="fe715-132">Unity 2019.3 y HoloLens</span><span class="sxs-lookup"><span data-stu-id="fe715-132">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="fe715-133">Si una aplicación de HoloLens aparece como un panel 2D en el dispositivo, asegúrese de que se han configurado las opciones siguientes en Unity 2019.3.x antes de implementar la aplicación para UWP:</span><span class="sxs-lookup"><span data-stu-id="fe715-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="fe715-134">Si usa una versión de XR heredada:</span><span class="sxs-lookup"><span data-stu-id="fe715-134">If using the legacy XR:</span></span>

1. <span data-ttu-id="fe715-135">Vaya a Edit > Project Settings, Player (Editar > Configuración del proyecto, Jugador)</span><span class="sxs-lookup"><span data-stu-id="fe715-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="fe715-136">En **XR Settings** (Configuración de XR) en la pestaña UWP, asegúrese de que la opción **Virtual Reality Supported** (Compatible con realidad virtual) está habilitada y de que el SDK de **Windows Mixed Reality** se ha agregado a los SDK.</span><span class="sxs-lookup"><span data-stu-id="fe715-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="fe715-137">Compilación e implementación en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fe715-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="fe715-138">Si usa el complemento XR:</span><span class="sxs-lookup"><span data-stu-id="fe715-138">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="fe715-139">Siga los pasos que encontrará en [Introducción a XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="fe715-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="fe715-140">Asegúrese de que el perfil de configuración sea **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="fe715-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="fe715-141">Vaya a **Edit > Project Settings, XR-Plugin Management** (Editar > Configuración del proyecto, Administración del complemento XR) y asegúrese de que **Windows Mixed Reality** está habilitado.</span><span class="sxs-lookup"><span data-stu-id="fe715-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="fe715-142">Compilación e implementación en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fe715-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="fe715-143">Si usa Unity 2019.3.x, seleccione **ARM64** y no **ARM** como arquitectura de compilación en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe715-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="fe715-144">Con la configuración predeterminada de Unity en Unity 2019.3.x, una aplicación de Unity no se implementará en HoloLens si se selecciona ARM debido a un error de Unity.</span><span class="sxs-lookup"><span data-stu-id="fe715-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="fe715-145">Se puede hacer un seguimiento de esto desde el [seguimiento de problemas de Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="fe715-145">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="fe715-146">Si se requiere la arquitectura de ARM, vaya a **Edit > Project Settings, Player** (Editar > Configuración del proyecto, Jugador) y, en el menú **Other Settings** (Otras opciones) , deshabilite **Graphics Jobs** (Trabajos de gráficos).</span><span class="sxs-lookup"><span data-stu-id="fe715-146">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="fe715-147">Al deshabilitar **Graphics Jobs** (Trabajos de gráficos) permitirá que la aplicación se implemente con la arquitectura de compilación de ARM para Unity 2019.3.x, pero se recomienda ARM64.</span><span class="sxs-lookup"><span data-stu-id="fe715-147">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="fe715-148">Creación e implementación de MRTK en cascos WMR (independiente)</span><span class="sxs-lookup"><span data-stu-id="fe715-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="fe715-149">Las compilaciones independientes de MRTK se pueden usar en cascos WMR.</span><span class="sxs-lookup"><span data-stu-id="fe715-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="fe715-150">Una compilación independiente para un casco de WMR requiere los siguientes pasos adicionales:</span><span class="sxs-lookup"><span data-stu-id="fe715-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="fe715-151">El SDK de XR de Unity también admite WMR nativo en compilaciones independientes, pero no requiere el complemento SteamVR o WMR.</span><span class="sxs-lookup"><span data-stu-id="fe715-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="fe715-152">Estos pasos son necesarios para la versión de XR heredada de Unity.</span><span class="sxs-lookup"><span data-stu-id="fe715-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="fe715-153">Instalación de [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="fe715-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="fe715-154">Instalación de [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="fe715-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="fe715-155">Instalación del [complemento de WMR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="fe715-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="fe715-156">Uso del complemento de MWR</span><span class="sxs-lookup"><span data-stu-id="fe715-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="fe715-157">Abra Steam y busque el complemento de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fe715-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="fe715-158">Compruebe que SteamVR esté cerrado antes de iniciar el complemento de WMR.</span><span class="sxs-lookup"><span data-stu-id="fe715-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="fe715-159">Al iniciar el complemento de WMR, también se inicia SteamVR.</span><span class="sxs-lookup"><span data-stu-id="fe715-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="fe715-160">Asegúrese de que el casco de WMR está conectado.</span><span class="sxs-lookup"><span data-stu-id="fe715-160">Make sure the WMR headset is plugged in.</span></span>

    ![Búsqueda de complementos de WMR](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="fe715-162">Seleccione **Launch** (Iniciar) para Windows Mixed Reality para el complemento SteamVR.</span><span class="sxs-lookup"><span data-stu-id="fe715-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![Complemento de WMR](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="fe715-164">Se iniciará SteamVR y el complemento de WMR y aparecerá una nueva ventana de estado de seguimiento para el casco de WMR.</span><span class="sxs-lookup"><span data-stu-id="fe715-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="fe715-165">Para obtener más información, visite la [documentación de Steam de Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="fe715-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Aspecto de inicio de WMR](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="fe715-167">En Unity, con la escena de MRTK abierta, vaya a **File > Build Settings** (Archivo > Configuración de la compilación).</span><span class="sxs-lookup"><span data-stu-id="fe715-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="fe715-168">Compilación de la escena</span><span class="sxs-lookup"><span data-stu-id="fe715-168">Build the scene</span></span>
    - <span data-ttu-id="fe715-169">Seleccione **Add Open Scene** (Agregar escena abierta).</span><span class="sxs-lookup"><span data-stu-id="fe715-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="fe715-170">Asegúrese de que la plataforma sea **Standalone** (Independiente).</span><span class="sxs-lookup"><span data-stu-id="fe715-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="fe715-171">Seleccione **Build** (Compilar).</span><span class="sxs-lookup"><span data-stu-id="fe715-171">Select **Build**</span></span>
    - <span data-ttu-id="fe715-172">Elija la ubicación de la nueva compilación en el Explorador de archivos</span><span class="sxs-lookup"><span data-stu-id="fe715-172">Choose the location for the new build in File Explorer</span></span>

    ![Configuración de compilación para plataformas independientes](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="fe715-174">Se creará un nuevo archivo ejecutable de Unity. Para iniciar la aplicación, selecciónelo en el Explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="fe715-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity en el Explorador de archivos](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="fe715-176">Vea también</span><span class="sxs-lookup"><span data-stu-id="fe715-176">See also</span></span>

- [<span data-ttu-id="fe715-177">Compatibilidad con Android y iOS</span><span class="sxs-lookup"><span data-stu-id="fe715-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="fe715-178">Compatibilidad con el movimiento Leap</span><span class="sxs-lookup"><span data-stu-id="fe715-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="fe715-179">Detección de las capacidades de la plataforma</span><span class="sxs-lookup"><span data-stu-id="fe715-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)