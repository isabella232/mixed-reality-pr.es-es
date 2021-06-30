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
# <a name="creating-a-camera-settings-provider"></a>Creación de un proveedor de configuración de cámara

El sistema de cámara es un sistema extensible para proporcionar compatibilidad con configuraciones de cámara específicas de la plataforma. Para agregar compatibilidad con una nueva configuración de cámara, es posible que se requiera un proveedor de configuración personalizado.

> [!NOTE]
> El código fuente completo usado en este ejemplo se puede encontrar en la **carpeta MRTK/Providers/UnityAR.**

## <a name="namespace-and-folder-structure"></a>Espacio de nombres y estructura de carpetas

Los proveedores de datos se pueden distribuir de una de estas dos maneras:

1. Complementos de terceros
1. Parte de Microsoft Mixed Reality Toolkit

El proceso de aprobación de envíos de nuevos proveedores de datos a MRTK variará caso por caso y se comunicará en el momento de la propuesta inicial. Las propuestas se pueden enviar mediante la creación de un nuevo problema [ *de tipo de solicitud* de características](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-ons"></a>Complementos de terceros

**Espacio de nombres**

Los proveedores de datos deben tener un espacio de nombres para mitigar posibles conflictos de nombres. Se recomienda que el espacio de nombres incluya los siguientes componentes.

- Nombre de la empresa que genera el complemento
- Área de función

Por ejemplo, un proveedor de configuración de cámara creado y enviado por la empresa Contoso puede ser *"Contoso.MixedReality.Toolkit.Camera".*

**Estructura de carpetas**

Se recomienda retrasar el código fuente de los proveedores de datos en una jerarquía de carpetas, como se muestra en la imagen siguiente.

![Ejemplo de estructura de carpetas](../images/camera-system/ExampleProviderFolderStructure.png)

Cuando la *carpeta ContosoCamera* contiene la implementación del proveedor de datos, la carpeta *Editor* contiene el inspector (y cualquier otro código específico del editor de Unity) y la carpeta Perfiles contiene uno o varios objetos pre-creados que pueden incluirse en scripts de perfil. 

### <a name="mrtk-submission"></a>Envío de MRTK

**Espacio de nombres**

Si se envía un proveedor de configuración de cámara al repositorio  [de Mixed Reality Toolkit,](https://github.com/Microsoft/MixedRealityToolkit-Unity)el espacio de nombres debe comenzar por Microsoft.MixedReality.Toolkit (por ejemplo: *Microsoft.MixedReality.Toolkit.CameraSystem).*

**Estructura de carpetas**

Todo el código debe encontrarse en una carpeta debajo de MRTK/Providers (por ejemplo, MRTK/Providers/UnityAR).

## <a name="define-the-camera-settings-object"></a>Definición del objeto de configuración de la cámara

El primer paso para crear un proveedor de configuración de cámara es determinar el tipo de datos (por ejemplo, mallas o planos) que proporcionará a las aplicaciones.

Todos los objetos de datos espaciales deben implementar la [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interfaz .

## <a name="implement-the-settings-provider"></a>Implementación del proveedor de configuración

### <a name="specify-interface-andor-base-class-inheritance"></a>Especificación de la herencia de interfaz o clase base

Todos los proveedores de configuración de cámara deben [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) implementar la interfaz , que especifica la funcionalidad mínima requerida por el sistema de cámara. La base de MRTK incluye la [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) clase que proporciona una implementación predeterminada de la funcionalidad necesaria.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Aplicación del atributo MixedRealityDataProvider

Un paso clave para crear un proveedor de configuración de cámara es aplicar el [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo a la clase . Este paso permite establecer el perfil y las plataformas predeterminados para el proveedor de datos, cuando se seleccionan en el perfil sistema de cámara, así como el nombre, la ruta de acceso de la carpeta y mucho más.

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementación de los métodos IMixedRealityDataProvider

Una vez definida la clase , el siguiente paso es proporcionar la implementación de la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .

> [!NOTE]
> La [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) clase, a través de [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) la clase , proporciona implementaciones vacías para los [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos. Los detalles de estos métodos suelen ser específicos del proveedor de datos.

Los métodos que debe implementar el proveedor de datos son:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> No todos los proveedores de configuración requerirán implementaciones para todos estos métodos. Se recomienda encarecidamente que `Destroy()` y `Initialize()` se implementen como mínimo.

### <a name="implement-the-data-provider-logic"></a>Implementación de la lógica del proveedor de datos

El siguiente paso consiste en agregar la lógica del proveedor de configuración mediante la implementación de [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) . Esta parte del proveedor de datos normalmente será específica de la configuración de la cámara.

## <a name="create-the-profile-and-inspector"></a>Creación del perfil y el inspector

En Mixed Reality Toolkit, los proveedores de datos se configuran mediante [perfiles](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definición del perfil

El contenido del perfil debe reflejar las opciones de configuración seleccionables para el desarrollador. Las propiedades configurables por el usuario definidas en cada interfaz también deben incluirse con el perfil.

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

El atributo se puede aplicar a la clase de perfil para permitir que los clientes creen una instancia de perfil mediante el menú `CreateAssetMenu`   >    >  **Crear recursos Mixed Reality perfiles** del kit  >  **de** herramientas.

### <a name="implement-the-inspector"></a>Implementación del inspector

Los inspectores de perfil son la interfaz de usuario para configurar y ver el contenido del perfil. Cada inspector de perfil debe extender la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) clase .

El `CustomEditor` atributo informa a Unity del tipo de recurso al que se aplica el inspector.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>Creación de definiciones de ensamblado

El Mixed Reality Toolkit usa archivos de definición de ensamblado[(.asmdef)](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)para especificar las dependencias entre componentes, así como para ayudar a Unity a reducir el tiempo de compilación.

Se recomienda crear archivos de definición de ensamblado para todos los proveedores de datos y sus componentes del editor.

Con la [estructura de carpetas](#namespace-and-folder-structure) del ejemplo anterior, habría dos archivos .asmdef para el proveedor de datos ContosoCamera.

La primera definición de ensamblado es para el proveedor de datos. En este ejemplo, se llamará ContosoCamera y se ubicará en la *carpeta ContosoCamera del* ejemplo. Esta definición de ensamblado debe especificar una dependencia en Microsoft.MixedReality.Toolkit y en cualquier otro ensamblado del que dependa.

La definición del ensamblado ContosoCameraEditor especificará el inspector de perfil y cualquier código específico del editor. Este archivo debe encontrarse en la carpeta raíz del código del editor. En este ejemplo, el archivo se ubicará en la *carpeta ContosoCamera\Editor.* Esta definición de ensamblado contendrá una referencia al ensamblado ContosoCamera, así como:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

## <a name="register-the-data-provider"></a>Registro del proveedor de datos

Una vez creado, el proveedor de datos se puede registrar con el sistema Camera para su uso en la aplicación.

![Selección del proveedor de configuración de la cámara](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Empaquetado y distribución

Los proveedores de datos que se distribuyen como componentes de terceros tienen los detalles específicos del empaquetado y la distribución de acuerdo con las preferencias del desarrollador. Probablemente, la solución más común será generar un .unitypackage y distribuirlo a través del Almacén de recursos de Unity.

Si se envía y acepta un proveedor de datos como parte del paquete microsoft Mixed Reality Toolkit, el equipo de Microsoft MRTK lo empaquetará y distribuirá como parte de las ofertas de MRTK.

## <a name="see-also"></a>Consulte también

- [Información general del sistema de cámara](camera-system-overview.md)
- [Clase `BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` Interfaz](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` Interfaz](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
