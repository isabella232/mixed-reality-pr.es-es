---
title: GettingStartedWithMRTKAndXRSDK
description: Página de aterrizaje de MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK, XRSDK,
ms.openlocfilehash: d5ab9bf51828c84759b72e87e1c41f885c7d6738
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300428"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="c43a8-104">Introducción al SDK de MRTK y XR</span><span class="sxs-lookup"><span data-stu-id="c43a8-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="c43a8-105">El SDK de XR es la [nueva canalización XR de Unity en unity 2019,3 y versiones posteriores](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span><span class="sxs-lookup"><span data-stu-id="c43a8-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="c43a8-106">En Unity 2019, proporciona una alternativa a la canalización XR existente.</span><span class="sxs-lookup"><span data-stu-id="c43a8-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="c43a8-107">En Unity 2020, se convertirá en la única canalización de XR en Unity.</span><span class="sxs-lookup"><span data-stu-id="c43a8-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c43a8-108">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="c43a8-108">Prerequisites</span></span>

<span data-ttu-id="c43a8-109">Para empezar a trabajar con el kit de herramientas de realidad mixta, siga [los pasos proporcionados](../install-the-tools.md#importing-the-mixed-reality-toolkit) para agregar MRTK a un proyecto.</span><span class="sxs-lookup"><span data-stu-id="c43a8-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="c43a8-110">Configuración de Unity para la canalización del SDK de XR</span><span class="sxs-lookup"><span data-stu-id="c43a8-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="c43a8-111">La canalización del SDK de XR actualmente admite 3 plataformas: Windows Mixed Reality, Oculus y OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c43a8-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="c43a8-112">En las secciones siguientes se explican los pasos necesarios para configurar el SDK de XR para cada plataforma.</span><span class="sxs-lookup"><span data-stu-id="c43a8-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="c43a8-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c43a8-113">Windows Mixed Reality</span></span>

<span data-ttu-id="c43a8-114">Vaya al **Administrador de paquetes de Unity** e instale el paquete del complemento de Windows XR, que agrega compatibilidad con Windows Mixed Reality en el SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="c43a8-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="c43a8-115">De este modo, se extraerán también algunos paquetes de dependencia.</span><span class="sxs-lookup"><span data-stu-id="c43a8-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="c43a8-116">Asegúrese de que los siguientes elementos se hayan instalado correctamente:</span><span class="sxs-lookup"><span data-stu-id="c43a8-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="c43a8-117">Administración de complementos de XR</span><span class="sxs-lookup"><span data-stu-id="c43a8-117">XR Plugin Management</span></span>
   * <span data-ttu-id="c43a8-118">Complemento de Windows XR</span><span class="sxs-lookup"><span data-stu-id="c43a8-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="c43a8-119">XR aplicaciones auxiliares de entrada heredadas</span><span class="sxs-lookup"><span data-stu-id="c43a8-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="c43a8-120">Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="c43a8-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="c43a8-121">Haga clic en la pestaña Administración de complementos de XR en la ventana Configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c43a8-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="c43a8-122">Vaya a la configuración de Plataforma universal de Windows y asegúrese de que Windows Mixed Reality está activado en proveedores de complementos.</span><span class="sxs-lookup"><span data-stu-id="c43a8-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="c43a8-123">Asegúrese de que está activada la opción inicializar XR al iniciar.</span><span class="sxs-lookup"><span data-stu-id="c43a8-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="c43a8-124">(**_Necesario para la comunicación remota de HoloLens en el editor; de lo contrario, opcional_**) Vaya a configuración independiente y asegúrese de que Windows Mixed Reality está activado en proveedores de complementos.</span><span class="sxs-lookup"><span data-stu-id="c43a8-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="c43a8-125">Asegúrese también de que la opción inicializar XR al iniciar está activada.</span><span class="sxs-lookup"><span data-stu-id="c43a8-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Administración de complementos de XR con pestaña independiente seleccionada](images/xr-management-img-02.png)

7. <span data-ttu-id="c43a8-127">(**_Opcional_**) Haga clic en la pestaña Windows Mixed Reality en administración de complementos de XR y cree un perfil de configuración personalizada para cambiar los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="c43a8-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="c43a8-128">Si la lista de valores de configuración ya existe, no es necesario crear ningún perfil.</span><span class="sxs-lookup"><span data-stu-id="c43a8-128">If the list of settings are already there, no profile needs to be created.</span></span>

![XR administración de complementos con la pestaña Windows seleccionada](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="c43a8-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="c43a8-130">Oculus</span></span>

1. <span data-ttu-id="c43a8-131">Siga las instrucciones para [configurar Oculus Quest in MRTK mediante la guía de canalización del SDK de XR](../features/cross-platform/oculus-quest-mrtk.md) al final.</span><span class="sxs-lookup"><span data-stu-id="c43a8-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../features/cross-platform/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="c43a8-132">En la guía se describen los pasos necesarios para configurar Unity y MRTK para usar la canalización del SDK de XR para Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="c43a8-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="c43a8-133">OpenXR (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="c43a8-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c43a8-134">OpenXR en Unity solo se admite en Unity 2020,2 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="c43a8-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="c43a8-135">Actualmente, también es compatible con las compilaciones x64 y ARM64.</span><span class="sxs-lookup"><span data-stu-id="c43a8-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="c43a8-136">Siga las instrucciones que se indican en la guía [usar el complemento Mixed Reality OpenXR plugin para Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , incluidos los pasos para configurar la administración y optimización del complemento de XR para instalar el complemento OpenXR en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c43a8-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="c43a8-137">Asegúrese de que se han instalado correctamente los siguientes:</span><span class="sxs-lookup"><span data-stu-id="c43a8-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="c43a8-138">Administración de complementos de XR</span><span class="sxs-lookup"><span data-stu-id="c43a8-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="c43a8-139">Complemento de OpenXR</span><span class="sxs-lookup"><span data-stu-id="c43a8-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="c43a8-140">Complemento OpenXR de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c43a8-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="c43a8-141">Vaya a editar > configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c43a8-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="c43a8-142">Haga clic en la pestaña Administración de complementos de XR en la ventana Configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c43a8-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="c43a8-143">Asegúrese de que está activada la opción inicializar XR al iniciar.</span><span class="sxs-lookup"><span data-stu-id="c43a8-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="c43a8-144">(**_Opcional_**) Si el destino es HoloLens 2, asegúrese de que está en la plataforma UWP y seleccione conjunto de características de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c43a8-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Administración de complementos abrir XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="c43a8-146">Si tiene un proyecto preexistente que usa MRTK de UPM, asegúrese de que la siguiente línea está en el archivo **link.xml** ubicado en la carpeta MixedRealityToolkit. generated.</span><span class="sxs-lookup"><span data-stu-id="c43a8-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="c43a8-147">Para la versión inicial de MRTK y OpenXR, solo se admiten de forma nativa las manos articuladas de HoloLens 2 y los controladores de movimiento de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c43a8-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="c43a8-148">En las próximas versiones se agregará compatibilidad con hardware adicional.</span><span class="sxs-lookup"><span data-stu-id="c43a8-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="c43a8-149">Configuración de MRTK para la canalización del SDK de XR</span><span class="sxs-lookup"><span data-stu-id="c43a8-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="c43a8-150">Si usa OpenXR, elija "DefaultOpenXRConfigurationProfile" como perfil activo o clonarlo para crear personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="c43a8-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="c43a8-151">Si usa otros tiempos de ejecución de XR en la configuración de administración de complementos de XR, como Windows Mixed Reality o Oculus, elija "DefaultXRSDKConfigurationProfile" como perfil activo o clonarlo para crear personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="c43a8-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="c43a8-152">Estos perfiles se configuran con los sistemas y proveedores correctos, cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="c43a8-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="c43a8-153">Vea [los documentos de perfiles](../features/profiles/profiles.md#xr-sdk) para obtener más información sobre el perfil y la compatibilidad de ejemplo con el SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="c43a8-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="c43a8-154">Para migrar un perfil existente a XR SDK, deben actualizarse los siguientes servicios y proveedores de datos:</span><span class="sxs-lookup"><span data-stu-id="c43a8-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="c43a8-155">Cámara</span><span class="sxs-lookup"><span data-stu-id="c43a8-155">Camera</span></span>

<span data-ttu-id="c43a8-156">De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="c43a8-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Configuración de cámara heredada](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="c43a8-158">en</span><span class="sxs-lookup"><span data-stu-id="c43a8-158">to</span></span>

| <span data-ttu-id="c43a8-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c43a8-159">OpenXR</span></span> | <span data-ttu-id="c43a8-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c43a8-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="c43a8-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**y**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="c43a8-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Configuración de cámara del SDK de XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="c43a8-163">Entrada</span><span class="sxs-lookup"><span data-stu-id="c43a8-163">Input</span></span>

<span data-ttu-id="c43a8-164">De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="c43a8-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Configuración de entrada heredada](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="c43a8-166">en</span><span class="sxs-lookup"><span data-stu-id="c43a8-166">to</span></span>

| <span data-ttu-id="c43a8-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c43a8-167">OpenXR</span></span> | <span data-ttu-id="c43a8-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c43a8-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="c43a8-169">__OpenXR__:</span><span class="sxs-lookup"><span data-stu-id="c43a8-169">__OpenXR__:</span></span>

![Configuración de entrada de OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="c43a8-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="c43a8-171">__Windows Mixed Reality__:</span></span>

![Configuración de entrada del SDK de XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="c43a8-173">Límite</span><span class="sxs-lookup"><span data-stu-id="c43a8-173">Boundary</span></span>

<span data-ttu-id="c43a8-174">De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="c43a8-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Configuración de límites heredados](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="c43a8-176">en</span><span class="sxs-lookup"><span data-stu-id="c43a8-176">to</span></span>

| <span data-ttu-id="c43a8-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c43a8-177">OpenXR</span></span> | <span data-ttu-id="c43a8-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c43a8-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configuración de límites del SDK de XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="c43a8-180">Reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="c43a8-180">Spatial awareness</span></span>

<span data-ttu-id="c43a8-181">De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="c43a8-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Configuración de reconocimiento espacial heredada](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="c43a8-183">en</span><span class="sxs-lookup"><span data-stu-id="c43a8-183">to</span></span>

| <span data-ttu-id="c43a8-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c43a8-184">OpenXR</span></span> | <span data-ttu-id="c43a8-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c43a8-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="c43a8-186">En curso</span><span class="sxs-lookup"><span data-stu-id="c43a8-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configuración de reconocimiento espacial del SDK de XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="c43a8-188">Asignaciones de controlador</span><span class="sxs-lookup"><span data-stu-id="c43a8-188">Controller mappings</span></span>

<span data-ttu-id="c43a8-189">Si usa perfiles de asignación de controlador personalizados, abra uno de ellos y ejecute el elemento de menú de los perfiles de asignación del kit de herramientas de realidad mixta-> Utilities-> Update-> Controller para asegurarse de que se han definido los nuevos tipos de controlador del SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="c43a8-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="c43a8-190">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c43a8-190">See also</span></span>

* [<span data-ttu-id="c43a8-191">Introducción al desarrollo de AR en Unity</span><span class="sxs-lookup"><span data-stu-id="c43a8-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="c43a8-192">Introducción al desarrollo de VR en Unity</span><span class="sxs-lookup"><span data-stu-id="c43a8-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)