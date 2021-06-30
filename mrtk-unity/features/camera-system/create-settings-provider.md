---
title: Creación de un proveedor de configuración
description: Proveedor de datos para la configuración de la cámara en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: d07b84c3cf550f9a235e58286b4cd239ac43b649
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121193"
---
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="f3cf9-104">Creación de un proveedor de configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="f3cf9-104">Creating a camera settings provider</span></span>

<span data-ttu-id="f3cf9-105">El sistema de cámara es un sistema extensible para proporcionar compatibilidad con configuraciones de cámara específicas de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="f3cf9-106">Para agregar compatibilidad con una nueva configuración de cámara, es posible que se requiera un proveedor de configuración personalizado.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="f3cf9-107">El código fuente completo usado en este ejemplo se puede encontrar en la **carpeta MRTK/Providers/UnityAR.**</span><span class="sxs-lookup"><span data-stu-id="f3cf9-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="f3cf9-108">Espacio de nombres y estructura de carpetas</span><span class="sxs-lookup"><span data-stu-id="f3cf9-108">Namespace and folder structure</span></span>

<span data-ttu-id="f3cf9-109">Los proveedores de datos se pueden distribuir de una de estas dos maneras:</span><span class="sxs-lookup"><span data-stu-id="f3cf9-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="f3cf9-110">Complementos de terceros</span><span class="sxs-lookup"><span data-stu-id="f3cf9-110">Third party add-ons</span></span>
1. <span data-ttu-id="f3cf9-111">Parte de Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="f3cf9-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="f3cf9-112">El proceso de aprobación de envíos de nuevos proveedores de datos a MRTK variará caso por caso y se comunicará en el momento de la propuesta inicial.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="f3cf9-113">Las propuestas se pueden enviar mediante la creación de un nuevo problema [ *de tipo de solicitud* de características](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="f3cf9-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="f3cf9-114">Complementos de terceros</span><span class="sxs-lookup"><span data-stu-id="f3cf9-114">Third party add-ons</span></span>

<span data-ttu-id="f3cf9-115">**Espacio de nombres**</span><span class="sxs-lookup"><span data-stu-id="f3cf9-115">**Namespace**</span></span>

<span data-ttu-id="f3cf9-116">Los proveedores de datos deben tener un espacio de nombres para mitigar posibles conflictos de nombres.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="f3cf9-117">Se recomienda que el espacio de nombres incluya los siguientes componentes.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="f3cf9-118">Nombre de la empresa que genera el complemento</span><span class="sxs-lookup"><span data-stu-id="f3cf9-118">Company name producing the add-on</span></span>
- <span data-ttu-id="f3cf9-119">Área de función</span><span class="sxs-lookup"><span data-stu-id="f3cf9-119">Feature area</span></span>

<span data-ttu-id="f3cf9-120">Por ejemplo, un proveedor de configuración de cámara creado y enviado por la empresa Contoso puede ser *"Contoso.MixedReality.Toolkit.Camera".*</span><span class="sxs-lookup"><span data-stu-id="f3cf9-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="f3cf9-121">**Estructura de carpetas**</span><span class="sxs-lookup"><span data-stu-id="f3cf9-121">**Folder structure**</span></span>

<span data-ttu-id="f3cf9-122">Se recomienda retrasar el código fuente de los proveedores de datos en una jerarquía de carpetas, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Ejemplo de estructura de carpetas](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="f3cf9-124">Cuando la *carpeta ContosoCamera* contiene la implementación del proveedor de datos, la carpeta *Editor* contiene el inspector (y cualquier otro código específico del editor de Unity) y la carpeta Perfiles contiene uno o varios objetos pre-creados que pueden incluirse en scripts de perfil. </span><span class="sxs-lookup"><span data-stu-id="f3cf9-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="f3cf9-125">Envío de MRTK</span><span class="sxs-lookup"><span data-stu-id="f3cf9-125">MRTK submission</span></span>

<span data-ttu-id="f3cf9-126">**Espacio de nombres**</span><span class="sxs-lookup"><span data-stu-id="f3cf9-126">**Namespace**</span></span>

<span data-ttu-id="f3cf9-127">Si se envía un proveedor de configuración de cámara al repositorio  [de Mixed Reality Toolkit,](https://github.com/Microsoft/MixedRealityToolkit-Unity)el espacio de nombres debe comenzar por Microsoft.MixedReality.Toolkit (por ejemplo: *Microsoft.MixedReality.Toolkit.CameraSystem).*</span><span class="sxs-lookup"><span data-stu-id="f3cf9-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="f3cf9-128">**Estructura de carpetas**</span><span class="sxs-lookup"><span data-stu-id="f3cf9-128">**Folder structure**</span></span>

<span data-ttu-id="f3cf9-129">Todo el código debe encontrarse en una carpeta debajo de MRTK/Providers (por ejemplo, MRTK/Providers/UnityAR).</span><span class="sxs-lookup"><span data-stu-id="f3cf9-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="f3cf9-130">Definición del objeto de configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="f3cf9-130">Define the camera settings object</span></span>

<span data-ttu-id="f3cf9-131">El primer paso para crear un proveedor de configuración de cámara es determinar el tipo de datos (por ejemplo, mallas o planos) que proporcionará a las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="f3cf9-132">Todos los objetos de datos espaciales deben implementar la [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interfaz .</span><span class="sxs-lookup"><span data-stu-id="f3cf9-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="f3cf9-133">Implementación del proveedor de configuración</span><span class="sxs-lookup"><span data-stu-id="f3cf9-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="f3cf9-134">Especificación de la herencia de interfaz o clase base</span><span class="sxs-lookup"><span data-stu-id="f3cf9-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="f3cf9-135">Todos los proveedores de configuración de cámara deben [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) implementar la interfaz , que especifica la funcionalidad mínima requerida por el sistema de cámara.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="f3cf9-136">La base de MRTK incluye la [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) clase que proporciona una implementación predeterminada de la funcionalidad necesaria.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="f3cf9-137">Aplicación del atributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="f3cf9-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="f3cf9-138">Un paso clave para crear un proveedor de configuración de cámara es aplicar el [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo a la clase .</span><span class="sxs-lookup"><span data-stu-id="f3cf9-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="f3cf9-139">Este paso permite establecer el perfil y las plataformas predeterminados para el proveedor de datos, cuando se seleccionan en el perfil sistema de cámara, así como el nombre, la ruta de acceso de la carpeta y mucho más.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="f3cf9-140">Implementación de los métodos IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="f3cf9-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="f3cf9-141">Una vez definida la clase , el siguiente paso es proporcionar la implementación de la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .</span><span class="sxs-lookup"><span data-stu-id="f3cf9-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="f3cf9-142">La [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) clase, a través de [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) la clase , proporciona implementaciones vacías para los [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="f3cf9-143">Los detalles de estos métodos suelen ser específicos del proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="f3cf9-144">Los métodos que debe implementar el proveedor de datos son:</span><span class="sxs-lookup"><span data-stu-id="f3cf9-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="f3cf9-145">No todos los proveedores de configuración requerirán implementaciones para todos estos métodos.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="f3cf9-146">Se recomienda encarecidamente que `Destroy()` y `Initialize()` se implementen como mínimo.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="f3cf9-147">Implementación de la lógica del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="f3cf9-147">Implement the data provider logic</span></span>

<span data-ttu-id="f3cf9-148">El siguiente paso consiste en agregar la lógica del proveedor de configuración mediante la implementación de [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) .</span><span class="sxs-lookup"><span data-stu-id="f3cf9-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="f3cf9-149">Esta parte del proveedor de datos normalmente será específica de la configuración de la cámara.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="f3cf9-150">Creación del perfil y el inspector</span><span class="sxs-lookup"><span data-stu-id="f3cf9-150">Create the profile and inspector</span></span>

<span data-ttu-id="f3cf9-151">En Mixed Reality Toolkit, los proveedores de datos se configuran mediante [perfiles](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f3cf9-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="f3cf9-152">Definición del perfil</span><span class="sxs-lookup"><span data-stu-id="f3cf9-152">Define the profile</span></span>

<span data-ttu-id="f3cf9-153">El contenido del perfil debe reflejar las opciones de configuración seleccionables para el desarrollador.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="f3cf9-154">Las propiedades configurables por el usuario definidas en cada interfaz también deben incluirse con el perfil.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

<span data-ttu-id="f3cf9-155">El atributo se puede aplicar a la clase de perfil para permitir que los clientes creen una instancia de perfil mediante el menú `CreateAssetMenu`   >    >  **Crear recursos Mixed Reality perfiles** del kit  >  **de** herramientas.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="f3cf9-156">Implementación del inspector</span><span class="sxs-lookup"><span data-stu-id="f3cf9-156">Implement the inspector</span></span>

<span data-ttu-id="f3cf9-157">Los inspectores de perfil son la interfaz de usuario para configurar y ver el contenido del perfil.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="f3cf9-158">Cada inspector de perfil debe extender la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) clase .</span><span class="sxs-lookup"><span data-stu-id="f3cf9-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="f3cf9-159">El `CustomEditor` atributo informa a Unity del tipo de recurso al que se aplica el inspector.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="f3cf9-160">Creación de definiciones de ensamblado</span><span class="sxs-lookup"><span data-stu-id="f3cf9-160">Create assembly definition(s)</span></span>

<span data-ttu-id="f3cf9-161">El Mixed Reality Toolkit usa archivos de definición de ensamblado[(.asmdef)](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)para especificar las dependencias entre componentes, así como para ayudar a Unity a reducir el tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="f3cf9-162">Se recomienda crear archivos de definición de ensamblado para todos los proveedores de datos y sus componentes del editor.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="f3cf9-163">Con la [estructura de carpetas](#namespace-and-folder-structure) del ejemplo anterior, habría dos archivos .asmdef para el proveedor de datos ContosoCamera.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="f3cf9-164">La primera definición de ensamblado es para el proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="f3cf9-165">En este ejemplo, se llamará ContosoCamera y se ubicará en la *carpeta ContosoCamera del* ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="f3cf9-166">Esta definición de ensamblado debe especificar una dependencia en Microsoft.MixedReality.Toolkit y en cualquier otro ensamblado del que dependa.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="f3cf9-167">La definición del ensamblado ContosoCameraEditor especificará el inspector de perfil y cualquier código específico del editor.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="f3cf9-168">Este archivo debe encontrarse en la carpeta raíz del código del editor.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="f3cf9-169">En este ejemplo, el archivo se ubicará en la *carpeta ContosoCamera\Editor.*</span><span class="sxs-lookup"><span data-stu-id="f3cf9-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="f3cf9-170">Esta definición de ensamblado contendrá una referencia al ensamblado ContosoCamera, así como:</span><span class="sxs-lookup"><span data-stu-id="f3cf9-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="f3cf9-171">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="f3cf9-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="f3cf9-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="f3cf9-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="f3cf9-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="f3cf9-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="f3cf9-174">Registro del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="f3cf9-174">Register the data provider</span></span>

<span data-ttu-id="f3cf9-175">Una vez creado, el proveedor de datos se puede registrar con el sistema Camera para su uso en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![Selección del proveedor de configuración de la cámara](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="f3cf9-177">Empaquetado y distribución</span><span class="sxs-lookup"><span data-stu-id="f3cf9-177">Packaging and distribution</span></span>

<span data-ttu-id="f3cf9-178">Los proveedores de datos que se distribuyen como componentes de terceros tienen los detalles específicos del empaquetado y la distribución de acuerdo con las preferencias del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="f3cf9-179">Probablemente, la solución más común será generar un .unitypackage y distribuirlo a través del Almacén de recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="f3cf9-180">Si se envía y acepta un proveedor de datos como parte del paquete microsoft Mixed Reality Toolkit, el equipo de Microsoft MRTK lo empaquetará y distribuirá como parte de las ofertas de MRTK.</span><span class="sxs-lookup"><span data-stu-id="f3cf9-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3cf9-181">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f3cf9-181">See also</span></span>

- [<span data-ttu-id="f3cf9-182">Información general del sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="f3cf9-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="f3cf9-183">Clase `BaseCameraSettingsProvider`</span><span class="sxs-lookup"><span data-stu-id="f3cf9-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="f3cf9-184">`IMixedRealityCameraSettingsProvider` Interfaz</span><span class="sxs-lookup"><span data-stu-id="f3cf9-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="f3cf9-185">`IMixedRealityDataProvider` Interfaz</span><span class="sxs-lookup"><span data-stu-id="f3cf9-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
