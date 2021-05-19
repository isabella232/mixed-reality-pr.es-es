---
title: Tareas iniciales con MRTK y XRSDK
description: Página de aterrizaje de MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, XRSDK,
ms.openlocfilehash: ef6d8c9205a9d801e8cb0ec2690d77b74c72b5fb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143528"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="3bf0a-104">Introducción al SDK de MRTK y XR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="3bf0a-105">El SDK de XR es la nueva canalización de XR de [Unity en Unity 2019.3 y posteriores.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="3bf0a-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="3bf0a-106">En Unity 2019, proporciona una alternativa a la canalización XR existente.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="3bf0a-107">En Unity 2020, se convertirá en la única canalización XR en Unity.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3bf0a-108">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="3bf0a-108">Prerequisites</span></span>

<span data-ttu-id="3bf0a-109">Para empezar a trabajar con Mixed Reality Toolkit, siga [los](../install-the-tools.md#importing-the-mixed-reality-toolkit) pasos proporcionados para agregar MRTK a un proyecto.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="3bf0a-110">Configuración de Unity para la canalización del SDK de XR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="3bf0a-111">La canalización del SDK de XR admite actualmente 3 plataformas: Windows Mixed Reality, Oculus y OpenXR.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="3bf0a-112">En las secciones siguientes se detendrán los pasos necesarios para configurar el SDK de XR para cada plataforma.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="3bf0a-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3bf0a-113">Windows Mixed Reality</span></span>

<span data-ttu-id="3bf0a-114">Vaya a **unity's Administrador de paquetes** e instale el paquete del complemento XR de Windows, que agrega compatibilidad con Windows Mixed Reality sdk de XR.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="3bf0a-115">Esto también extraerá algunos paquetes de dependencias.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="3bf0a-116">Asegúrese de que todo lo siguiente se ha instalado correctamente:</span><span class="sxs-lookup"><span data-stu-id="3bf0a-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="3bf0a-117">Administración de complementos XR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-117">XR Plugin Management</span></span>
   * <span data-ttu-id="3bf0a-118">Complemento XR de Windows</span><span class="sxs-lookup"><span data-stu-id="3bf0a-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="3bf0a-119">Asistentes de entrada heredados de XR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="3bf0a-120">Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="3bf0a-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="3bf0a-121">Haga clic en la pestaña XR Plug-in Management (Administración de complementos XR) en la ventana Project Settings (Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="3bf0a-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="3bf0a-122">Vaya a la configuración Plataforma universal de Windows y asegúrese de Windows Mixed Reality esté activada en Proveedores de complementos.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="3bf0a-123">Asegúrese de que initialize XR on Startup (Inicializar XR al iniciar) está activado.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="3bf0a-124">(Obligatorio **_para la comunicación remota de HoloLens en el editor; de lo contrario, opcional)_** Vaya a la configuración independiente y asegúrese de que Windows Mixed Reality en Proveedores de complementos.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="3bf0a-125">Asegúrese también de que la opción Inicializar XR al iniciar está activada.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Administración de complementos XR con la pestaña Independiente seleccionada](images/xr-management-img-02.png)

7. <span data-ttu-id="3bf0a-127">(**_Opcional_**) Haga clic en la Windows Mixed Reality en Administración de complementos XR y cree un perfil de configuración personalizado para cambiar los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="3bf0a-128">Si la lista de configuraciones ya está ahí, no es necesario crear ningún perfil.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-128">If the list of settings are already there, no profile needs to be created.</span></span>

![Administración de complementos XR con la pestaña Windows seleccionada](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="3bf0a-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="3bf0a-130">Oculus</span></span>

1. <span data-ttu-id="3bf0a-131">Siga la [guía How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end (Cómo configurar Oculus Quest en MRTK mediante la canalización del SDK de XR hasta el final).</span><span class="sxs-lookup"><span data-stu-id="3bf0a-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="3bf0a-132">En la guía se describen los pasos necesarios para configurar Unity y MRTK para usar la canalización del SDK de XR para Oculus Unity.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="3bf0a-133">OpenXR (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3bf0a-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bf0a-134">OpenXR en Unity solo se admite en Unity 2020.2 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="3bf0a-135">Actualmente, solo admite compilaciones x64 y ARM64.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="3bf0a-136">Siga la guía Using [the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) (Uso del complemento OpenXR para Unity), incluidos los pasos para configurar la administración y optimización de complementos XR para instalar el complemento OpenXR en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="3bf0a-137">Asegúrese de que lo siguiente se ha instalado correctamente:</span><span class="sxs-lookup"><span data-stu-id="3bf0a-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="3bf0a-138">Administración de complementos XR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="3bf0a-139">Complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="3bf0a-140">Mixed Reality complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="3bf0a-141">Vaya a Editar > configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="3bf0a-142">Haga clic en la pestaña Administración de complementos XR en la ventana Configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="3bf0a-143">Asegúrese de que la opción Inicializar XR al iniciar está activada.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="3bf0a-144">(**_Opcional)_** Si el destino HoloLens 2, asegúrese de que está en la plataforma para UWP y seleccione Microsoft HoloLens conjunto de características.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Administración de complementos Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="3bf0a-146">Si tiene un proyecto preexistente que usa MRTK de UPM, asegúrese de que la línea siguiente se encuentra en el archivo **link.xml** ubicado en la carpeta MixedRealityToolkit.Generated.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="3bf0a-147">Para la versión inicial de MRTK y OpenXR, solo se admiten de forma nativa las HoloLens 2 y Windows Mixed Reality de movimiento.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="3bf0a-148">En las próximas versiones se agregará compatibilidad con hardware adicional.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="3bf0a-149">Configuración de MRTK para la canalización del SDK de XR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="3bf0a-150">Si usa OpenXR, elija "DefaultOpenXRConfigurationProfile" como perfil activo o clone para realizar personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="3bf0a-151">Si usa otros entornos de ejecución de XR en la configuración de administración de complementos de XR, como Windows Mixed Reality u Oculus, elija "DefaultXRSDKConfigurationProfile" como perfil activo o clone para realizar personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="3bf0a-152">Estos perfiles se establecen con los sistemas y proveedores correctos, cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="3bf0a-153">Consulte [los documentos de perfiles para](../features/profiles/profiles.md#xr-sdk) obtener más información sobre el perfil y la compatibilidad de ejemplo con el SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="3bf0a-154">Para migrar un perfil existente al SDK de XR, se deben actualizar los siguientes servicios y proveedores de datos:</span><span class="sxs-lookup"><span data-stu-id="3bf0a-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="3bf0a-155">Cámara</span><span class="sxs-lookup"><span data-stu-id="3bf0a-155">Camera</span></span>

<span data-ttu-id="3bf0a-156">De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="3bf0a-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Configuración de la cámara heredada](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="3bf0a-158">to</span><span class="sxs-lookup"><span data-stu-id="3bf0a-158">to</span></span>

| <span data-ttu-id="3bf0a-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-159">OpenXR</span></span> | <span data-ttu-id="3bf0a-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3bf0a-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="3bf0a-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**y**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="3bf0a-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![Configuración de la cámara del SDK de XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="3bf0a-163">Entrada</span><span class="sxs-lookup"><span data-stu-id="3bf0a-163">Input</span></span>

<span data-ttu-id="3bf0a-164">De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="3bf0a-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Configuración de entrada heredada](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="3bf0a-166">to</span><span class="sxs-lookup"><span data-stu-id="3bf0a-166">to</span></span>

| <span data-ttu-id="3bf0a-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-167">OpenXR</span></span> | <span data-ttu-id="3bf0a-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3bf0a-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="3bf0a-169">__OpenXR:__</span><span class="sxs-lookup"><span data-stu-id="3bf0a-169">__OpenXR__:</span></span>

![Configuración de entrada de OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="3bf0a-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="3bf0a-171">__Windows Mixed Reality__:</span></span>

![Configuración de entrada del SDK de XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="3bf0a-173">Límite</span><span class="sxs-lookup"><span data-stu-id="3bf0a-173">Boundary</span></span>

<span data-ttu-id="3bf0a-174">De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="3bf0a-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Configuración de límites heredada](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="3bf0a-176">to</span><span class="sxs-lookup"><span data-stu-id="3bf0a-176">to</span></span>

| <span data-ttu-id="3bf0a-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-177">OpenXR</span></span> | <span data-ttu-id="3bf0a-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3bf0a-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configuración de límites del SDK de XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="3bf0a-180">Reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="3bf0a-180">Spatial awareness</span></span>

<span data-ttu-id="3bf0a-181">De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="3bf0a-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Configuración de reconocimiento espacial heredado](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="3bf0a-183">to</span><span class="sxs-lookup"><span data-stu-id="3bf0a-183">to</span></span>

| <span data-ttu-id="3bf0a-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="3bf0a-184">OpenXR</span></span> | <span data-ttu-id="3bf0a-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3bf0a-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="3bf0a-186">En curso</span><span class="sxs-lookup"><span data-stu-id="3bf0a-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configuración de reconocimiento espacial del SDK de XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="3bf0a-188">Asignaciones de controladores</span><span class="sxs-lookup"><span data-stu-id="3bf0a-188">Controller mappings</span></span>

<span data-ttu-id="3bf0a-189">Si usa perfiles de asignación de controladores personalizados, abra uno de ellos y ejecute el elemento de menú Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles para asegurarse de que se definen los nuevos tipos de controlador del SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="3bf0a-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bf0a-190">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3bf0a-190">See also</span></span>

* [<span data-ttu-id="3bf0a-191">Introducción al desarrollo de AR en Unity</span><span class="sxs-lookup"><span data-stu-id="3bf0a-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="3bf0a-192">Introducción al desarrollo de realidad virtual en Unity</span><span class="sxs-lookup"><span data-stu-id="3bf0a-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)