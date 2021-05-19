---
title: Creación de proveedores de datos de entrada
description: documentación para crear el sistema de entrada y el proveedor de datos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: c164fa406ae6822f4d889aff3bf615cf7fa76337
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144078"
---
# <a name="creating-an-input-system-data-provider"></a>Creación de un proveedor de datos del sistema de entrada

El sistema Mixed Reality Toolkit es un sistema extensible para habilitar la compatibilidad con dispositivos de entrada. Para agregar compatibilidad con una nueva plataforma de hardware, puede ser necesario un proveedor de datos de entrada personalizado.

En este artículo se describe cómo crear proveedores de datos personalizados, también denominados administradores de dispositivos, para el sistema de entrada. El código de ejemplo que se muestra aquí es de [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> El código completo usado en este ejemplo se puede encontrar en la carpeta MRTK/Providers/WindowsMixedReality.

## <a name="namespace-and-folder-structure"></a>Espacio de nombres y estructura de carpetas

Los proveedores de datos se pueden distribuir como un complemento de terceros o como parte de Microsoft Mixed Reality Toolkit. El proceso de aprobación de envíos de nuevos proveedores de datos a MRTK variará caso por caso y se comunicará en el momento de la propuesta inicial.

> [!Important]
> Si se envía un proveedor de datos del sistema de entrada  al repositorio [de Mixed Reality Toolkit,](https://github.com/Microsoft/MixedRealityToolkit-Unity)el espacio de nombres debe comenzar por Microsoft.MixedReality.Toolkit (por ejemplo: Microsoft.MixedReality.Toolkit.WindowsMixedReality) y el código debe encontrarse en una carpeta debajo de MRTK/Providers (por ejemplo, MRTK/Providers/WindowsMixedReality).

### <a name="namespace"></a>Espacio de nombres

Los proveedores de datos deben tener un espacio de nombres para mitigar posibles conflictos de nombres. Se recomienda que el espacio de nombres incluya los siguientes componentes.

- Nombre de la compañía
- Área de función

Por ejemplo, un proveedor de datos de entrada creado por la empresa Contoso puede ser "Contoso.MixedReality.Toolkit.Input".

### <a name="recommended-folder-structure"></a>Estructura de carpetas recomendada

Se recomienda retrasar el código fuente de los proveedores de datos en una jerarquía de carpetas, como se muestra en la imagen siguiente.

![Ejemplo de estructura de carpetas](../images/input/ExampleProviderFolderStructure.png)

Donde ContosoInput contiene la implementación del proveedor de datos, la carpeta Editor contiene el inspector (y cualquier otro código específico del editor de Unity), la carpeta Textures contiene imágenes de los controladores admitidos y Profiles contiene uno o varios perfiles pre-made.

> [!Note]
> Algunas imágenes de controlador comunes se pueden encontrar en la carpeta MixedRealityToolkit\StandardAssets\Textures.

## <a name="implement-the-data-provider"></a>Implementación del proveedor de datos

### <a name="specify-interface-andor-base-class-inheritance"></a>Especificación de la herencia de interfaz o clase base

Todos los proveedores de datos del sistema de entrada deben [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) implementar la interfaz , que especifica la funcionalidad mínima requerida por el sistema de entrada. La base de MRTK incluye la [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) clase que proporciona una implementación predeterminada de esta funcionalidad necesaria. En el caso de los dispositivos que se basan en la clase UInput de Unity, la [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) clase se puede usar como una clase base.

> [!Note]
> Las `BaseInputDeviceManager` clases y proporcionan la implementación `UnityJoystickManager` `IMixedRealityInputDeviceManager` necesaria.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` lo usa para indicar que proporciona compatibilidad con un conjunto de funcionalidades de entrada, en concreto, manos articuladas, manos de voz con gesto de mirada y controladores `WindowsMixedRealityDeviceManager` de movimiento.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Aplicación del atributo MixedRealityDataProvider

Un paso clave para crear un proveedor de datos del sistema de entrada es aplicar el [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo a la clase . Este paso permite establecer los perfiles y plataformas predeterminados para el proveedor, cuando se seleccionan en el perfil del sistema de entrada.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementación de los métodos IMixedRealityDataProvider

Una vez definida la clase , el siguiente paso es proporcionar la implementación de la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .

> [!Note]
> La `BaseInputDeviceManager` clase, a través de `BaseService` la clase , proporciona solo implementaciones vacías para los `IMixedRealityDataProvider` métodos. Los detalles de estos métodos suelen ser específicos del proveedor de datos.

Los métodos que debe implementar el proveedor de datos son:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementación de la lógica del proveedor de datos

El siguiente paso consiste en agregar la lógica para administrar los dispositivos de entrada, incluidos los controladores que se admiten.

### <a name="implement-the-controller-classes"></a>Implementación de las clases de controlador

 El ejemplo de define `WindowsMixedRealityDeviceManager` e implementa las siguientes clases de controlador.

> El código fuente de cada una de estas clases se puede encontrar en la carpeta MRTK/Providers/WindowsMixedReality.

- WindowsMixedRealityArticulatedHand.cs
- WindowsMixedRealityController.cs
- WindowsMixedRealityGGVHand.cs

> [!Note]
> No todos los administradores de dispositivos admitirán varios tipos de controlador.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>Aplicación del atributo MixedRealityController

A continuación, [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) aplique el atributo a la clase . Este atributo especifica el tipo de controlador (por ejemplo, la mano articulada), la entrega (por ejemplo, izquierda o derecha) y una imagen de controlador opcional.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>Configuración de las asignaciones de interacción

El siguiente paso consiste en definir el conjunto de asignaciones de interacción compatibles con el controlador. En el caso de los dispositivos que [](../tools/controller-mapping-tool.md) reciben sus datos a través de la clase Input de Unity, la herramienta de asignación de controladores es un recurso útil para confirmar las asignaciones de eje y botón correctas que se asignarán a las interacciones.

El ejemplo siguiente se abrevia desde la `GenericOpenVRController` clase , ubicada en la carpeta MRTK/Providers/OpenVR.

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
>La [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) clase proporciona constantes simbólicas para las definiciones de botón y eje de entrada de Unity.

### <a name="raise-notification-events"></a>Generar eventos de notificación

Para permitir que las aplicaciones respondan a la entrada del usuario, el proveedor de datos genera eventos de notificación correspondientes a los cambios de estado del controlador, tal como se define en las [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces y .

Para los controles de tipo digital (botón), genera los eventos OnInputDown y OnInputUp.

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

En el caso de los controles análogos (por ejemplo, la posición del panel táctil), se debe generar el evento InputChanged.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Adición de instrumentación de Unity Profiler

El rendimiento es fundamental en las aplicaciones de realidad mixta. Cada componente agrega cierta sobrecarga para la que las aplicaciones deben tener en cuenta. Para ello, es importante que todos los proveedores de datos de entrada contengan instrumentación de Unity Profiler en bucle interno y rutas de acceso de código que se usan con frecuencia.

Se recomienda implementar el patrón utilizado por MRTK al instrumentar proveedores personalizados.

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> El nombre usado para identificar el marcador del profiler es arbitrario. MRTK usa el siguiente patrón.
>
> "[product] className.methodName - optional note"
>
> Se recomienda que los proveedores de datos personalizados sigan un patrón similar para ayudar a simplificar la identificación de componentes y métodos específicos al analizar seguimientos.

## <a name="create-the-profile-and-inspector"></a>Creación del perfil y el inspector

En Mixed Reality Toolkit, los proveedores de datos se configuran mediante [perfiles](../profiles/profiles.md).

Los proveedores de datos con opciones de configuración adicionales (por ejemplo, [InputSimulationService)](../input-simulation/input-simulation-service.md)deben crear un perfil y un inspector para permitir que los clientes modifiquen el comportamiento para que se adapte mejor a las necesidades de la aplicación.

> El código completo del ejemplo de esta sección se puede encontrar en MRTK. Carpeta Services/InputSimulation.

### <a name="define-the-profile"></a>Definición del perfil

El contenido del perfil debe reflejar las propiedades accesibles del observador (por ejemplo, intervalo de actualización). Todas las propiedades configurables por el usuario definidas en cada interfaz deben incluirse con el perfil.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

El atributo se puede aplicar a la clase de perfil para permitir que los clientes creen una instancia de perfil mediante el menú Crear `CreateAssetMenu` > Assets > Mixed Reality Toolkit > **Profiles.**

### <a name="implement-the-inspector"></a>Implementación del inspector

Los inspectores de perfil son la interfaz de usuario para configurar y ver el contenido del perfil. Cada inspector de perfil debe extender la [clase 'BaseMixedRealityToolkitConfigurationProfileInspector.](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector)

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

El `CustomEditor` atributo informa a Unity del tipo de recurso al que se aplica el inspector.

## <a name="create-assembly-definitions"></a>Creación de definiciones de ensamblado

El Mixed Reality Toolkit usa archivos de definición de ensamblado[(.asmdef)](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)para especificar dependencias entre componentes, así como para ayudar a Unity a reducir el tiempo de compilación.

Se recomienda crear archivos de definición de ensamblado para todos los proveedores de datos y sus componentes del editor.

Con la [estructura de carpetas](#recommended-folder-structure) del ejemplo anterior, habría dos archivos .asmdef para el proveedor de datos ContosoInput.

La primera definición de ensamblado es para el proveedor de datos. En este ejemplo, se llamará ContosoInput y se ubicará en la carpeta ContosoInput del ejemplo.
Esta definición de ensamblado debe especificar una dependencia en Microsoft.MixedReality.Toolkit y en cualquier otro ensamblado del que dependa.

La definición del ensamblado ContosoInputEditor especificará el inspector de perfil y cualquier código específico del editor. Este archivo debe encontrarse en la carpeta raíz del código del editor. En este ejemplo, el archivo se ubicará en la carpeta ContosoInput\Editor. Esta definición de ensamblado contendrá una referencia al ensamblado ContosoInput, así como:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

## <a name="register-the-data-provider"></a>Registro del proveedor de datos

Una vez creado, el proveedor de datos se puede registrar con el sistema de entrada y usarse en la aplicación.

![Proveedores de datos del sistema de entrada registrados](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>Empaquetado y distribución

Los proveedores de datos que se distribuyen como componentes de terceros tienen los detalles específicos del empaquetado y la distribución de acuerdo con las preferencias del desarrollador. Probablemente, la solución más común será generar un .unitypackage y distribuirlo a través del Almacén de recursos de Unity.

Si se envía y acepta un proveedor de datos como parte del paquete microsoft Mixed Reality Toolkit, el equipo de Microsoft MRTK lo empaquetará y distribuirá como parte de las ofertas de MRTK.

## <a name="see-also"></a>Consulte también

- [Sistema de entrada](overview.md)
- [Clase `BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` Interfaz](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` Interfaz](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` Interfaz](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` Interfaz](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Interfaz](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Herramienta de asignación de controladores](../tools/controller-mapping-tool.md)
