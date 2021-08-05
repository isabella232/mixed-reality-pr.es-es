---
title: Creación de un proveedor de datos de reconocimiento espacial
description: describe cómo crear proveedores de datos personalizados en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 05186c418a7b0b7b143abc58be6a6afb64cb69f5a1c90c73ed516d51c2a5d8ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188866"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>Creación de un proveedor de datos del sistema de reconocimiento espacial

El sistema de reconocimiento espacial es un sistema extensible para proporcionar a las aplicaciones datos sobre entornos del mundo real. Para agregar compatibilidad con una nueva plataforma de hardware o una nueva forma de datos de reconocimiento espacial, es posible que se requiera un proveedor de datos personalizado.

En este artículo se describe cómo crear proveedores de [datos](../../architecture/systems-extensions-providers.md)personalizados, también denominados observadores espaciales, para el sistema de reconocimiento espacial. El código de ejemplo que se muestra aquí es de la implementación de clase , que es útil para cargar datos [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [de malla 3D en el editor](spatial-object-mesh-observer.md).

> [!NOTE]
> El código fuente completo usado en este ejemplo se puede encontrar en la `Assets/MRTK/Providers/ObjectMeshObserver` carpeta .

## <a name="namespace-and-folder-structure"></a>Espacio de nombres y estructura de carpetas

Los proveedores de datos se pueden distribuir de una de estas dos maneras:

1. Complementos de terceros
1. Parte de microsoft Mixed Reality Toolkit

El proceso de aprobación de envíos de nuevos proveedores de datos a MRTK variará caso por caso y se comunicará en el momento de la propuesta inicial. Las propuestas se pueden enviar mediante la creación de un nuevo problema [ *de tipo de solicitud* de características](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-on"></a>Complemento de terceros

**Espacio de nombres**

Los proveedores de datos deben tener un espacio de nombres para mitigar posibles conflictos de nombres. Se recomienda que el espacio de nombres incluya los siguientes componentes.

- Nombre de la empresa que genera el complemento
- Área de función

Por ejemplo, un proveedor de datos de reconocimiento espacial creado y enviado por la empresa Contoso puede ser *"Contoso.MixedReality.Toolkit. SpatialAwareness".*

**Estructura de carpetas**

Se recomienda retrasar el código fuente de los proveedores de datos en una jerarquía de carpetas, como se muestra en la imagen siguiente.

![Ejemplo de estructura de carpetas](../images/spatial-awareness/ExampleProviderFolderStructure.png)

Donde la *carpeta ContosoSpatialAwareness* contiene la implementación del proveedor de datos, la carpeta *Editor* contiene el inspector (y cualquier otro código específico del editor de Unity) y la carpeta Perfiles contiene uno o varios objetos pre-creados que pueden incluirse en scripts de perfil. 

### <a name="mrtk-submission"></a>Envío de MRTK

**Espacio de nombres**

Si se envía un proveedor de datos del sistema de reconocimiento espacial al repositorio [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity), el espacio de nombres debe **comenzar** por Microsoft.MixedReality. Toolkit (p. *ej.: Microsoft.MixedReality.Toolkit. SpatialObjectMeshObserver*)

 y el código debe estar ubicado en una carpeta debajo de MRTK/Providers (por ejemplo: *MRTK/Providers/ObjectMeshObserver*).

**Estructura de carpetas**

Todo el código debe estar ubicado en una carpeta debajo de MRTK/Providers (por ejemplo: MRTK/Providers/ObjectMeshObserver).

## <a name="define-the-spatial-data-object"></a>Definición del objeto de datos espaciales

El primer paso para crear un proveedor de datos de reconocimiento espacial es determinar el tipo de datos (por ejemplo, mallas o planos) que proporcionará a las aplicaciones.

Todos los objetos de datos espaciales deben implementar la [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interfaz .

La Mixed Reality Toolkit proporciona los siguientes objetos espaciales que se pueden usar o extender en nuevos proveedores de datos.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>Implementación del proveedor de datos

### <a name="specify-interface-andor-base-class-inheritance"></a>Especificación de la herencia de interfaz o clase base

Todos los proveedores de datos de reconocimiento espacial deben implementar la [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interfaz , que especifica la funcionalidad mínima requerida por el sistema de reconocimiento espacial. La base de MRTK incluye la [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) clase que proporciona una implementación predeterminada de esta funcionalidad necesaria.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> La [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) clase usa la interfaz para indicar que proporciona compatibilidad con la funcionalidad [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) SpatialAwarenessMesh.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Aplicación del atributo MixedRealityDataProvider

Un paso clave para crear un proveedor de datos de reconocimiento espacial es aplicar el [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo a la clase . Este paso permite establecer el perfil y las plataformas predeterminados para el proveedor de datos, cuando se seleccionan en el perfil de reconocimiento espacial, así como el nombre, la ruta de acceso de la carpeta, etc.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementación de los métodos IMixedRealityDataProvider

Una vez definida la clase , el siguiente paso es proporcionar la implementación de la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .

> [!NOTE]
> La [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) clase, a través de [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) la clase , proporciona solo implementaciones vacías para los [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) métodos. Los detalles de estos métodos suelen ser específicos del proveedor de datos.

Los métodos que debe implementar el proveedor de datos son:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementación de la lógica del proveedor de datos

El siguiente paso consiste en agregar la lógica del proveedor de datos mediante la implementación de la interfaz del proveedor de datos específica, por ejemplo [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) . Esta parte del proveedor de datos normalmente será específica de la plataforma.

### <a name="observation-change-notifications"></a>Notificaciones de cambio de observación

Para permitir que las aplicaciones respondan a los cambios en la comprensión del entorno del dispositivo, el proveedor de datos genera eventos de notificación como se define en la [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interfaz .

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 El código siguiente de los [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) ejemplos muestra la generación y el evento cuando se agregan datos de malla.

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> La [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) clase no genera `OnObservationUpdated` eventos, ya que el modelo 3D solo se carga una vez. La implementación de la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) clase proporciona un ejemplo de cómo generar un evento para una malla `OnObservationUpdated` observada.

### <a name="add-unity-profiler-instrumentation"></a>Adición de instrumentación de Unity Profiler

El rendimiento es fundamental en las aplicaciones de realidad mixta. Cada componente agrega cierta sobrecarga para la que las aplicaciones deben tener en cuenta. Para ello, es importante que todos los proveedores de datos de reconocimiento espacial contengan instrumentación de Unity Profiler en bucle interno y rutas de acceso de código que se usan con frecuencia.

Se recomienda implementar el patrón utilizado por MRTK al instrumentar proveedores personalizados.

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> El nombre utilizado para identificar el marcador del profiler es arbitrario. MrTK usa el siguiente patrón.
>
> "[product] className.methodName - optional note"
>
> Se recomienda que los proveedores de datos personalizados sigan un patrón similar para ayudar a simplificar la identificación de componentes y métodos específicos al analizar seguimientos.

## <a name="create-the-profile-and-inspector"></a>Creación del perfil y el inspector

En la Mixed Reality Toolkit, los proveedores de datos se configuran mediante [perfiles](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definición del perfil

El contenido del perfil debe reflejar las propiedades accesibles del proveedor de datos (por ejemplo, intervalo de actualización). Todas las propiedades configurables por el usuario definidas en cada interfaz deben incluirse con el perfil.

Se recomiendan las clases base si un nuevo proveedor de datos extiende un proveedor existente. Por ejemplo, extiende para permitir que los clientes proporcionen un modelo 3D que se [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) usará como datos del [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) entorno.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

El atributo se puede aplicar a la clase de perfil para permitir que los clientes creen una instancia de perfil mediante el `CreateAssetMenu`   >    >  **menú Crear recursos Mixed Reality Toolkit**  >  **perfiles.**

### <a name="implement-the-inspector"></a>Implementación del inspector

Los inspectores de perfil son la interfaz de usuario para configurar y ver el contenido del perfil. Cada inspector de perfil debe extender la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) clase .

El `CustomEditor` atributo informa a Unity del tipo de recurso al que se aplica el inspector.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>Creación de definiciones de ensamblado

El Mixed Reality Toolkit archivos de definición de ensamblado ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar las dependencias entre componentes, así como para ayudar a Unity a reducir el tiempo de compilación.

Se recomienda crear archivos de definición de ensamblado para todos los proveedores de datos y sus componentes del editor.

Con la [estructura de carpetas](#namespace-and-folder-structure) del ejemplo anterior, habría dos archivos .asmdef para el proveedor de datos ContosoSpatialAwareness.

La primera definición de ensamblado es para el proveedor de datos. En este ejemplo, se llamará ContosoSpatialAwareness y se ubicará en la carpeta *ContosoSpatialAwareness del* ejemplo. Esta definición de ensamblado debe especificar una dependencia en Microsoft.MixedReality. Toolkit y cualquier otro ensamblado del que dependa.

La definición del ensamblado ContosoInputEditor especificará el inspector de perfil y cualquier código específico del editor. Este archivo debe encontrarse en la carpeta raíz del código del editor. En este ejemplo, el archivo se ubicará en la *carpeta ContosoSpatialAwareness\Editor.* Esta definición de ensamblado contendrá una referencia al ensamblado ContosoSpatialAwareness, así como:

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Editor.Inspectors
- Microsoft.MixedReality. Toolkit. Editor.Utilities

## <a name="register-the-data-provider"></a>Registro del proveedor de datos

Una vez creado, el proveedor de datos se puede registrar con el sistema de reconocimiento espacial que se usará en la aplicación.

![Selección del observador de malla de objetos espaciales](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>Empaquetado y distribución

Los proveedores de datos que se distribuyen como componentes de terceros tienen los detalles específicos del empaquetado y la distribución a la preferencia del desarrollador. Probablemente, la solución más común será generar un .unitypackage y distribuirlo a través del Almacén de recursos de Unity.

Si se envía y acepta un proveedor de datos como parte del paquete microsoft Mixed Reality Toolkit, el equipo de Microsoft MRTK lo empaquetará y distribuirá como parte de las ofertas de MRTK.

## <a name="see-also"></a>Vea también

- [Sistema de reconocimiento espacial](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` Interfaz](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [Clase `BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [Clase `SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [Clase `SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` Interfaz](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [Clase `BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` Interfaz](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` Interfaz](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Interfaz](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
