---
title: Creación de un proveedor de datos del sistema de entrada
description: documentación para crear el sistema de entrada y el proveedor de datos en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 0b6012871a4d4988fdb70336a3c33455f479bcac
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281920"
---
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="bd46d-104">Creación de un proveedor de datos del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bd46d-104">Creating an input system data provider</span></span>

<span data-ttu-id="bd46d-105">El Mixed Reality Toolkit de entrada es un sistema extensible para habilitar la compatibilidad con dispositivos de entrada.</span><span class="sxs-lookup"><span data-stu-id="bd46d-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="bd46d-106">Para agregar compatibilidad con una nueva plataforma de hardware, puede ser necesario un proveedor de datos de entrada personalizado.</span><span class="sxs-lookup"><span data-stu-id="bd46d-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="bd46d-107">En este artículo se describe cómo crear proveedores de datos personalizados, también denominados administradores de dispositivos, para el sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="bd46d-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="bd46d-108">El código de ejemplo que se muestra aquí es de [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="bd46d-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="bd46d-109">El código completo usado en este ejemplo se puede encontrar en la carpeta MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="bd46d-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="bd46d-110">Espacio de nombres y estructura de carpetas</span><span class="sxs-lookup"><span data-stu-id="bd46d-110">Namespace and folder structure</span></span>

<span data-ttu-id="bd46d-111">Los proveedores de datos se pueden distribuir como complemento de terceros o como parte de microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="bd46d-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="bd46d-112">El proceso de aprobación de envíos de nuevos proveedores de datos a MRTK variará caso por caso y se comunicará en el momento de la propuesta inicial.</span><span class="sxs-lookup"><span data-stu-id="bd46d-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="bd46d-113">Si se envía un proveedor de datos del sistema de entrada [al](https://github.com/Microsoft/MixedRealityToolkit-Unity)repositorio Mixed Reality Toolkit , el espacio de nombres debe **comenzar** por Microsoft.MixedReality. Toolkit (por ejemplo: Microsoft.MixedReality.Toolkit. WindowsMixedReality) y el código deben estar ubicados en una carpeta debajo de MRTK/Providers (por ejemplo, MRTK/Providers/WindowsMixedReality).</span><span class="sxs-lookup"><span data-stu-id="bd46d-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="bd46d-114">Espacio de nombres</span><span class="sxs-lookup"><span data-stu-id="bd46d-114">Namespace</span></span>

<span data-ttu-id="bd46d-115">Los proveedores de datos deben tener un espacio de nombres para mitigar posibles conflictos de nombres.</span><span class="sxs-lookup"><span data-stu-id="bd46d-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="bd46d-116">Se recomienda que el espacio de nombres incluya los siguientes componentes.</span><span class="sxs-lookup"><span data-stu-id="bd46d-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="bd46d-117">Nombre de la compañía</span><span class="sxs-lookup"><span data-stu-id="bd46d-117">Company name</span></span>
- <span data-ttu-id="bd46d-118">Área de función</span><span class="sxs-lookup"><span data-stu-id="bd46d-118">Feature area</span></span>

<span data-ttu-id="bd46d-119">Por ejemplo, un proveedor de datos de entrada creado por la empresa Contoso puede ser "Contoso.MixedReality. Toolkit. Entrada".</span><span class="sxs-lookup"><span data-stu-id="bd46d-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="bd46d-120">Estructura de carpetas recomendada</span><span class="sxs-lookup"><span data-stu-id="bd46d-120">Recommended folder structure</span></span>

<span data-ttu-id="bd46d-121">Se recomienda retrasar el código fuente de los proveedores de datos en una jerarquía de carpetas, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="bd46d-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Ejemplo de estructura de carpetas](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="bd46d-123">Donde ContosoInput contiene la implementación del proveedor de datos, la carpeta Editor contiene el inspector (y cualquier otro código específico del editor de Unity), la carpeta Textures contiene imágenes de los controladores admitidos y Profiles contiene uno o varios perfiles pre-made.</span><span class="sxs-lookup"><span data-stu-id="bd46d-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="bd46d-124">Puede encontrar algunas imágenes de controlador comunes en la carpeta MixedRealityToolkit\StandardAssets\Textures.</span><span class="sxs-lookup"><span data-stu-id="bd46d-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="bd46d-125">Implementación del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="bd46d-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="bd46d-126">Especificación de la herencia de interfaz o clase base</span><span class="sxs-lookup"><span data-stu-id="bd46d-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="bd46d-127">Todos los proveedores de datos del sistema de entrada deben [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) implementar la interfaz , que especifica la funcionalidad mínima requerida por el sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="bd46d-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="bd46d-128">La base de MRTK incluye la [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) clase que proporciona una implementación predeterminada de esta funcionalidad necesaria.</span><span class="sxs-lookup"><span data-stu-id="bd46d-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="bd46d-129">En el caso de los dispositivos que se basan en la clase UInput de Unity, la [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) clase se puede usar como clase base.</span><span class="sxs-lookup"><span data-stu-id="bd46d-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="bd46d-130">Las `BaseInputDeviceManager` clases y proporcionan la implementación `UnityJoystickManager` `IMixedRealityInputDeviceManager` necesaria.</span><span class="sxs-lookup"><span data-stu-id="bd46d-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="bd46d-131">`IMixedRealityCapabilityCheck` lo usa para indicar que proporciona compatibilidad con un conjunto de funcionalidades de entrada, en concreto, manos articuladas, manos con gesto de mirada y controladores `WindowsMixedRealityDeviceManager` de movimiento.</span><span class="sxs-lookup"><span data-stu-id="bd46d-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="bd46d-132">Aplicación del atributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="bd46d-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="bd46d-133">Un paso clave para crear un proveedor de datos del sistema de entrada es aplicar el [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) atributo a la clase .</span><span class="sxs-lookup"><span data-stu-id="bd46d-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="bd46d-134">Este paso permite establecer los perfiles y plataformas predeterminados para el proveedor, cuando se seleccionan en el perfil del sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="bd46d-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="bd46d-135">Implementación de los métodos IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="bd46d-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="bd46d-136">Una vez definida la clase , el siguiente paso es proporcionar la implementación de la [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaz .</span><span class="sxs-lookup"><span data-stu-id="bd46d-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="bd46d-137">La `BaseInputDeviceManager` clase, a través de `BaseService` la clase , solo proporciona implementaciones vacías para los `IMixedRealityDataProvider` métodos.</span><span class="sxs-lookup"><span data-stu-id="bd46d-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="bd46d-138">Los detalles de estos métodos suelen ser específicos del proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="bd46d-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="bd46d-139">Los métodos que debe implementar el proveedor de datos son:</span><span class="sxs-lookup"><span data-stu-id="bd46d-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="bd46d-140">Implementación de la lógica del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="bd46d-140">Implement the data provider logic</span></span>

<span data-ttu-id="bd46d-141">El siguiente paso consiste en agregar la lógica para administrar los dispositivos de entrada, incluidos los controladores que se admiten.</span><span class="sxs-lookup"><span data-stu-id="bd46d-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="bd46d-142">Implementación de las clases de controlador</span><span class="sxs-lookup"><span data-stu-id="bd46d-142">Implement the controller classes</span></span>

 <span data-ttu-id="bd46d-143">El ejemplo de define `WindowsMixedRealityDeviceManager` e implementa las siguientes clases de controlador.</span><span class="sxs-lookup"><span data-stu-id="bd46d-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="bd46d-144">El código fuente de cada una de estas clases se puede encontrar en la carpeta MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="bd46d-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="bd46d-145">WindowsMixedRealityArticulatedHand.cs</span><span class="sxs-lookup"><span data-stu-id="bd46d-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="bd46d-146">WindowsMixedRealityController.cs</span><span class="sxs-lookup"><span data-stu-id="bd46d-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="bd46d-147">WindowsMixedRealityGGVHand.cs</span><span class="sxs-lookup"><span data-stu-id="bd46d-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="bd46d-148">No todos los administradores de dispositivos admitirán varios tipos de controlador.</span><span class="sxs-lookup"><span data-stu-id="bd46d-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="bd46d-149">Aplicación del atributo MixedRealityController</span><span class="sxs-lookup"><span data-stu-id="bd46d-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="bd46d-150">A continuación, [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) aplique el atributo a la clase .</span><span class="sxs-lookup"><span data-stu-id="bd46d-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="bd46d-151">Este atributo especifica el tipo de controlador (por ejemplo, la mano articulada), la entrega (por ejemplo, izquierda o derecha) y una imagen de controlador opcional.</span><span class="sxs-lookup"><span data-stu-id="bd46d-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="bd46d-152">Configuración de las asignaciones de interacción</span><span class="sxs-lookup"><span data-stu-id="bd46d-152">Configure the interaction mappings</span></span>

<span data-ttu-id="bd46d-153">El siguiente paso consiste en definir el conjunto de asignaciones de interacción compatibles con el controlador.</span><span class="sxs-lookup"><span data-stu-id="bd46d-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="bd46d-154">Para los dispositivos que reciben sus datos [](../tools/controller-mapping-tool.md) a través de la clase Input de Unity, la herramienta de asignación de controladores es un recurso útil para confirmar las asignaciones de eje y botón correctas que se asignarán a las interacciones.</span><span class="sxs-lookup"><span data-stu-id="bd46d-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="bd46d-155">El ejemplo siguiente se abrevia desde la `GenericOpenVRController` clase , ubicada en la carpeta MRTK/Providers/OpenVR.</span><span class="sxs-lookup"><span data-stu-id="bd46d-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

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
><span data-ttu-id="bd46d-156">La [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) clase proporciona constantes simbólicas para las definiciones de botón y eje de entrada de Unity.</span><span class="sxs-lookup"><span data-stu-id="bd46d-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="bd46d-157">Generar eventos de notificación</span><span class="sxs-lookup"><span data-stu-id="bd46d-157">Raise notification events</span></span>

<span data-ttu-id="bd46d-158">Para permitir que las aplicaciones respondan a la entrada del usuario, el proveedor de datos genera eventos de notificación correspondientes a los cambios de estado del controlador, tal como se define en las [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces y .</span><span class="sxs-lookup"><span data-stu-id="bd46d-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="bd46d-159">Para los controles de tipo digital (botón), genera los eventos OnInputDown y OnInputUp.</span><span class="sxs-lookup"><span data-stu-id="bd46d-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

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

<span data-ttu-id="bd46d-160">En el caso de los controles análogos (por ejemplo, la posición del panel táctil), se debe generar el evento InputChanged.</span><span class="sxs-lookup"><span data-stu-id="bd46d-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="bd46d-161">Adición de instrumentación de Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="bd46d-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="bd46d-162">El rendimiento es fundamental en las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="bd46d-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="bd46d-163">Cada componente agrega cierta sobrecarga para la que las aplicaciones deben tener en cuenta.</span><span class="sxs-lookup"><span data-stu-id="bd46d-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="bd46d-164">Para ello, es importante que todos los proveedores de datos de entrada contengan instrumentación de Unity Profiler en bucle interno y rutas de acceso de código que se usan con frecuencia.</span><span class="sxs-lookup"><span data-stu-id="bd46d-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="bd46d-165">Se recomienda implementar el patrón utilizado por MRTK al instrumentar proveedores personalizados.</span><span class="sxs-lookup"><span data-stu-id="bd46d-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

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
> <span data-ttu-id="bd46d-166">El nombre utilizado para identificar el marcador del profiler es arbitrario.</span><span class="sxs-lookup"><span data-stu-id="bd46d-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="bd46d-167">MrTK usa el siguiente patrón.</span><span class="sxs-lookup"><span data-stu-id="bd46d-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="bd46d-168">"[product] className.methodName - optional note"</span><span class="sxs-lookup"><span data-stu-id="bd46d-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="bd46d-169">Se recomienda que los proveedores de datos personalizados sigan un patrón similar para ayudar a simplificar la identificación de componentes y métodos específicos al analizar seguimientos.</span><span class="sxs-lookup"><span data-stu-id="bd46d-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="bd46d-170">Creación del perfil y el inspector</span><span class="sxs-lookup"><span data-stu-id="bd46d-170">Create the profile and inspector</span></span>

<span data-ttu-id="bd46d-171">En la Mixed Reality Toolkit, los proveedores de datos se configuran mediante [perfiles](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bd46d-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="bd46d-172">Los proveedores de datos con opciones de configuración adicionales (por ejemplo, [InputSimulationService)](../input-simulation/input-simulation-service.md)deben crear un perfil e inspector para permitir a los clientes modificar el comportamiento para que se adapte mejor a las necesidades de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bd46d-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="bd46d-173">El código completo del ejemplo de esta sección se puede encontrar en MRTK. Carpeta Services/InputSimulation.</span><span class="sxs-lookup"><span data-stu-id="bd46d-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="bd46d-174">Definición del perfil</span><span class="sxs-lookup"><span data-stu-id="bd46d-174">Define the profile</span></span>

<span data-ttu-id="bd46d-175">El contenido del perfil debe reflejar las propiedades accesibles del observador (por ejemplo, intervalo de actualización).</span><span class="sxs-lookup"><span data-stu-id="bd46d-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="bd46d-176">Todas las propiedades configurables por el usuario definidas en cada interfaz deben incluirse con el perfil.</span><span class="sxs-lookup"><span data-stu-id="bd46d-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="bd46d-177">El atributo se puede aplicar a la clase de perfil para permitir que los clientes creen una instancia de perfil mediante el menú `CreateAssetMenu` Crear > recursos > Mixed Reality Toolkit > **perfiles.**</span><span class="sxs-lookup"><span data-stu-id="bd46d-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="bd46d-178">Implementación del inspector</span><span class="sxs-lookup"><span data-stu-id="bd46d-178">Implement the inspector</span></span>

<span data-ttu-id="bd46d-179">Los inspectores de perfil son la interfaz de usuario para configurar y ver el contenido del perfil.</span><span class="sxs-lookup"><span data-stu-id="bd46d-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="bd46d-180">Cada inspector de perfil debe extender la [clase 'BaseMixedRealityToolkitConfigurationProfileInspector.](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector)</span><span class="sxs-lookup"><span data-stu-id="bd46d-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="bd46d-181">El `CustomEditor` atributo informa a Unity del tipo de recurso al que se aplica el inspector.</span><span class="sxs-lookup"><span data-stu-id="bd46d-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="bd46d-182">Creación de definiciones de ensamblado</span><span class="sxs-lookup"><span data-stu-id="bd46d-182">Create assembly definition(s)</span></span>

<span data-ttu-id="bd46d-183">El Mixed Reality Toolkit archivos de definición de ensamblado ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) para especificar dependencias entre componentes, así como para ayudar a Unity a reducir el tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="bd46d-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="bd46d-184">Se recomienda crear archivos de definición de ensamblado para todos los proveedores de datos y sus componentes del editor.</span><span class="sxs-lookup"><span data-stu-id="bd46d-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="bd46d-185">Con la [estructura de carpetas](#recommended-folder-structure) del ejemplo anterior, habría dos archivos .asmdef para el proveedor de datos ContosoInput.</span><span class="sxs-lookup"><span data-stu-id="bd46d-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="bd46d-186">La primera definición de ensamblado es para el proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="bd46d-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="bd46d-187">En este ejemplo, se llamará ContosoInput y se ubicará en la carpeta ContosoInput del ejemplo.</span><span class="sxs-lookup"><span data-stu-id="bd46d-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="bd46d-188">Esta definición de ensamblado debe especificar una dependencia en Microsoft.MixedReality. Toolkit y cualquier otro ensamblado del que dependa.</span><span class="sxs-lookup"><span data-stu-id="bd46d-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="bd46d-189">La definición del ensamblado ContosoInputEditor especificará el inspector de perfil y cualquier código específico del editor.</span><span class="sxs-lookup"><span data-stu-id="bd46d-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="bd46d-190">Este archivo debe encontrarse en la carpeta raíz del código del editor.</span><span class="sxs-lookup"><span data-stu-id="bd46d-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="bd46d-191">En este ejemplo, el archivo se ubicará en la carpeta ContosoInput\Editor.</span><span class="sxs-lookup"><span data-stu-id="bd46d-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="bd46d-192">Esta definición de ensamblado contendrá una referencia al ensamblado ContosoInput, así como:</span><span class="sxs-lookup"><span data-stu-id="bd46d-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="bd46d-193">Microsoft.MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="bd46d-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="bd46d-194">Microsoft.MixedReality. Toolkit. Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="bd46d-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="bd46d-195">Microsoft.MixedReality. Toolkit. Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="bd46d-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="bd46d-196">Registro del proveedor de datos</span><span class="sxs-lookup"><span data-stu-id="bd46d-196">Register the data provider</span></span>

<span data-ttu-id="bd46d-197">Una vez creado, el proveedor de datos se puede registrar con el sistema de entrada y usarse en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bd46d-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![Proveedores de datos del sistema de entrada registrados](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="bd46d-199">Empaquetado y distribución</span><span class="sxs-lookup"><span data-stu-id="bd46d-199">Packaging and distribution</span></span>

<span data-ttu-id="bd46d-200">Los proveedores de datos que se distribuyen como componentes de terceros tienen los detalles específicos del empaquetado y la distribución de acuerdo con las preferencias del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="bd46d-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="bd46d-201">Probablemente, la solución más común será generar un paquete .unitypackage y distribuirlo a través del almacén de recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="bd46d-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="bd46d-202">Si se envía y acepta un proveedor de datos como parte del paquete microsoft Mixed Reality Toolkit, el equipo de Microsoft MRTK lo empaquetará y distribuirá como parte de las ofertas de MRTK.</span><span class="sxs-lookup"><span data-stu-id="bd46d-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd46d-203">Vea también</span><span class="sxs-lookup"><span data-stu-id="bd46d-203">See also</span></span>

- [<span data-ttu-id="bd46d-204">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bd46d-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="bd46d-205">Clase `BaseInputDeviceManager`</span><span class="sxs-lookup"><span data-stu-id="bd46d-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="bd46d-206">`IMixedRealityInputDeviceManager` Interfaz</span><span class="sxs-lookup"><span data-stu-id="bd46d-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="bd46d-207">`IMixedRealityInputHandler` Interfaz</span><span class="sxs-lookup"><span data-stu-id="bd46d-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="bd46d-208">`IMixedRealityInputHandler<T>` Interfaz</span><span class="sxs-lookup"><span data-stu-id="bd46d-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="bd46d-209">`IMixedRealityDataProvider` Interfaz</span><span class="sxs-lookup"><span data-stu-id="bd46d-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="bd46d-210">`IMixedRealityCapabilityCheck` Interfaz</span><span class="sxs-lookup"><span data-stu-id="bd46d-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="bd46d-211">Herramienta de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="bd46d-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
