---
title: Temas visuales
description: 'Información general: Control flexible de los recursos de la experiencia de usuario en MRTK'
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, temas de MRTK,
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177177"
---
# <a name="visual-themes"></a><span data-ttu-id="bf497-104">Temas visuales</span><span class="sxs-lookup"><span data-stu-id="bf497-104">Visual themes</span></span>

<span data-ttu-id="bf497-105">Los temas permiten un control flexible de los recursos de la experiencia de usuario en respuesta a diversas transiciones de estados.</span><span class="sxs-lookup"><span data-stu-id="bf497-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="bf497-106">Esto puede implicar cambiar el color de un botón, cambiar el tamaño de un elemento en respuesta al foco, etc. El marco de visual themes se integra en dos partes clave: 1) configuración y 2) motores en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bf497-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="bf497-107">[Las configuraciones de tema](#theme-configuration) son [](#theme-engines) definiciones de propiedades y tipos, mientras que los motores de temas son clases que consumen las configuraciones e implementan la lógica para actualizar transformaciones, materiales y mucho más en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bf497-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="bf497-108">Configuración del tema</span><span class="sxs-lookup"><span data-stu-id="bf497-108">Theme configuration</span></span>

<span data-ttu-id="bf497-109">Las configuraciones de tema [son ScriptableObjects que](https://docs.unity3d.com/Manual/class-ScriptableObject.html) definen cómo se inicializarán los motores de temas en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bf497-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="bf497-110">Definen qué propiedades y valores usar en respuesta a los cambios de entrada u otros cambios de estado cuando se ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bf497-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="bf497-111">Como [recursos de ScriptableObjects,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) las configuraciones de tema se pueden definir una vez y, a continuación, volver a usarse en distintos componentes de la experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="bf497-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="bf497-112">Para crear un nuevo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) recurso:</span><span class="sxs-lookup"><span data-stu-id="bf497-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="bf497-113">Haga clic con el botón derecho *en Project ventana.*</span><span class="sxs-lookup"><span data-stu-id="bf497-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="bf497-114">Seleccione **Create** Mixed Reality Toolkit Theme  >  **(Crear Mixed Reality Toolkit**  >  **tema).**</span><span class="sxs-lookup"><span data-stu-id="bf497-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="bf497-115">Los recursos de configuración de tema de ejemplo se pueden encontrar en `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="bf497-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Ejemplo de ScriptableObject de tema en inspector](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="bf497-117">States</span><span class="sxs-lookup"><span data-stu-id="bf497-117">States</span></span>

<span data-ttu-id="bf497-118">Al crear un nuevo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , lo primero que hay que establecer es qué estados están disponibles.</span><span class="sxs-lookup"><span data-stu-id="bf497-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="bf497-119">La *propiedad States* indica cuántos valores debe definir una configuración de tema, ya que habrá un valor por estado.</span><span class="sxs-lookup"><span data-stu-id="bf497-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="bf497-120">En la imagen de ejemplo anterior, los estados predeterminados definidos para el componente [Interactable](interactable.md#general-input-settings) son *Default*, *Focus*, *Pressed* y *Disabled*.</span><span class="sxs-lookup"><span data-stu-id="bf497-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="bf497-121">Se definen en el archivo de recursos `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States).</span><span class="sxs-lookup"><span data-stu-id="bf497-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="bf497-122">Para crear un nuevo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) recurso:</span><span class="sxs-lookup"><span data-stu-id="bf497-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="bf497-123">Haga clic con el botón derecho *en Project ventana.*</span><span class="sxs-lookup"><span data-stu-id="bf497-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="bf497-124">Seleccione **Create** Mixed Reality Toolkit State  >  **(Crear Mixed Reality Toolkit**  >  **estado).**</span><span class="sxs-lookup"><span data-stu-id="bf497-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![Ejemplo de ScriptableObject de estados en inspector](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="bf497-126">ScriptableObject define tanto la lista de estados como el [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) tipo de *StateModel* que se creará para estos estados.</span><span class="sxs-lookup"><span data-stu-id="bf497-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="bf497-127">*StateModel* es una clase que extiende e implementa la lógica de la máquina de estado para generar el estado actual en tiempo de [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) ejecución.</span><span class="sxs-lookup"><span data-stu-id="bf497-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="bf497-128">Los motores de temas en tiempo de ejecución suelen usar el estado actual de esta clase para determinar qué valores se establecerán en las propiedades de material, las transformaciones de GameObject y mucho más.</span><span class="sxs-lookup"><span data-stu-id="bf497-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="bf497-129">Propiedades del motor de temas</span><span class="sxs-lookup"><span data-stu-id="bf497-129">Theme engine properties</span></span>

<span data-ttu-id="bf497-130">Fuera de *Estados*, un recurso también define una lista de motores de [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) temas y las propiedades asociadas para estos motores.</span><span class="sxs-lookup"><span data-stu-id="bf497-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="bf497-131">Un [motor de tema](#theme-engines) define de nuevo la lógica para establecer los valores correctos en un GameObject en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bf497-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="bf497-132">Un recurso puede definir varios motores de temas para lograr transiciones sofisticadas de estados visuales [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) destinadas a varias propiedades gameObject.</span><span class="sxs-lookup"><span data-stu-id="bf497-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="bf497-133">**Tiempo de ejecución de temas**</span><span class="sxs-lookup"><span data-stu-id="bf497-133">**Theme Runtime**</span></span>

<span data-ttu-id="bf497-134">Define el tipo de clase del motor de tema que se creará.</span><span class="sxs-lookup"><span data-stu-id="bf497-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="bf497-135">**Facilitar**</span><span class="sxs-lookup"><span data-stu-id="bf497-135">**Easing**</span></span>

<span data-ttu-id="bf497-136">Algunos *motores de temas*, si definen su propiedad [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) como true, admiten la aceleración entre estados.</span><span class="sxs-lookup"><span data-stu-id="bf497-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="bf497-137">Por ejemplo, la lerping entre dos colores cuando se produce un cambio de estado.</span><span class="sxs-lookup"><span data-stu-id="bf497-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="bf497-138">La *duración* define en segundos cuánto tiempo se  va a facilitar desde el valor inicial hasta el valor final y la curva de animación define la tasa de cambio durante ese período de tiempo.</span><span class="sxs-lookup"><span data-stu-id="bf497-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="bf497-139">**Propiedades del sombreador**</span><span class="sxs-lookup"><span data-stu-id="bf497-139">**Shader properties**</span></span>

<span data-ttu-id="bf497-140">Algunos motores de temas , si definen su propiedad [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) como true, modificarán propiedades de sombreador *concretas* en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bf497-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="bf497-141">Los *campos Sombreador* *y Propiedad* definen la propiedad del sombreador de destino.</span><span class="sxs-lookup"><span data-stu-id="bf497-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="bf497-142">Creación de una configuración de tema mediante código</span><span class="sxs-lookup"><span data-stu-id="bf497-142">Create a theme configuration via code</span></span>

<span data-ttu-id="bf497-143">En general, es más fácil diseñar configuraciones de tema a través del inspector de Unity, pero hay casos en los que los temas se deben generar dinámicamente en tiempo de ejecución a través del código.</span><span class="sxs-lookup"><span data-stu-id="bf497-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="bf497-144">El fragmento de código siguiente proporciona un ejemplo de cómo realizar esta tarea.</span><span class="sxs-lookup"><span data-stu-id="bf497-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="bf497-145">Para ayudar a acelerar el desarrollo, los siguientes métodos auxiliares son útiles para simplificar la configuración.</span><span class="sxs-lookup"><span data-stu-id="bf497-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="bf497-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable): crea un nuevo objeto States ScriptableObject con los cuatro valores de estado predeterminados utilizados en el [componente Interactable.](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="bf497-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="bf497-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Cada motor de temas define una configuración predeterminada con las propiedades correctas necesarias para ese tipo de tiempo de ejecución de tema.</span><span class="sxs-lookup"><span data-stu-id="bf497-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="bf497-148">Este asistente crea una definición para el tipo de motor de tema especificado.</span><span class="sxs-lookup"><span data-stu-id="bf497-148">This helper creates a definition for the given Theme Engine type.</span></span>

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a><span data-ttu-id="bf497-149">Motores de temas</span><span class="sxs-lookup"><span data-stu-id="bf497-149">Theme engines</span></span>

<span data-ttu-id="bf497-150">Un [motor de](#theme-engines) temas es una clase que se extiende desde la clase [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) .</span><span class="sxs-lookup"><span data-stu-id="bf497-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="bf497-151">Se crea una instancia de estas clases en tiempo de ejecución y se configuran con [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) un objeto como se ha descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="bf497-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="bf497-152">Motores de temas predeterminados</span><span class="sxs-lookup"><span data-stu-id="bf497-152">Default theme engines</span></span>

<span data-ttu-id="bf497-153">MRTK se distribuye con un conjunto predeterminado de motores de temas que se enumeran a continuación:</span><span class="sxs-lookup"><span data-stu-id="bf497-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

<span data-ttu-id="bf497-154">Los motores de temas predeterminados se pueden encontrar en `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="bf497-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="bf497-155">Motores de temas personalizados</span><span class="sxs-lookup"><span data-stu-id="bf497-155">Custom theme engines</span></span>

<span data-ttu-id="bf497-156">Como se ha indicado, un motor de temas se define como una clase que se extiende desde la [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) clase .</span><span class="sxs-lookup"><span data-stu-id="bf497-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="bf497-157">Por lo tanto, el nuevo motor de temas solo necesita extender esta clase e implementar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="bf497-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="bf497-158">Implementaciones obligatorias</span><span class="sxs-lookup"><span data-stu-id="bf497-158">Mandatory implementations</span></span>

<span data-ttu-id="bf497-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.SetValue)</span><span class="sxs-lookup"><span data-stu-id="bf497-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="bf497-160">Para la propiedad determinada, que se puede identificar mediante , establezca su valor de estado actual en el host gameObject de destino `ThemeStateProperty.Name` (es decir,</span><span class="sxs-lookup"><span data-stu-id="bf497-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="bf497-161">establecer el color del material, etc.).</span><span class="sxs-lookup"><span data-stu-id="bf497-161">set the material color, etc).</span></span> <span data-ttu-id="bf497-162">El *índice* indica el valor de estado actual al que se va a obtener acceso y el porcentaje *,* un valor float entre 0 y 1, se usa para la aceleración o el equilibrio entre valores.</span><span class="sxs-lookup"><span data-stu-id="bf497-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="bf497-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetProperty)</span><span class="sxs-lookup"><span data-stu-id="bf497-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="bf497-164">Para la propiedad determinada, que se puede identificar mediante , devuelve el valor actual establecido en el objeto GameObject host `ThemeStateProperty.Name` de destino (es decir,</span><span class="sxs-lookup"><span data-stu-id="bf497-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="bf497-165">el color del material actual, el desplazamiento de la posición local actual, etc.).</span><span class="sxs-lookup"><span data-stu-id="bf497-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="bf497-166">Esto se usa principalmente para almacenar en caché el valor de inicio cuando se acelera entre estados.</span><span class="sxs-lookup"><span data-stu-id="bf497-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="bf497-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetDefaultThemeDefinition)</span><span class="sxs-lookup"><span data-stu-id="bf497-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="bf497-168">Devuelve un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objeto que define las propiedades y la configuración predeterminadas necesarias para el tema personalizado.</span><span class="sxs-lookup"><span data-stu-id="bf497-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="bf497-169">Variante protegida de la definición pública, excepto el valor ThemePropertyValue proporcionado para establecer en lugar de dirigir para usar la `SetValue()` configuración de índice o porcentaje.</span><span class="sxs-lookup"><span data-stu-id="bf497-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="bf497-170">Invalidaciones recomendadas</span><span class="sxs-lookup"><span data-stu-id="bf497-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="bf497-171">Realice los pasos de inicialización aquí dirigidos al parámetro *GameObject* proporcionado y use las propiedades y configuraciones definidas en el *parámetro ThemeDefinition.*</span><span class="sxs-lookup"><span data-stu-id="bf497-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="bf497-172">Se recomienda llamar a `base.Init(host, settings)` al principio de una invalidación.</span><span class="sxs-lookup"><span data-stu-id="bf497-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="bf497-173">Si el motor de temas personalizado puede admitir la aceleración entre los valores que se configuran a través de la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) propiedad .</span><span class="sxs-lookup"><span data-stu-id="bf497-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="bf497-174">Si el motor de temas personalizado puede admitir propiedades de sombreador de destino.</span><span class="sxs-lookup"><span data-stu-id="bf497-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="bf497-175">Se recomienda ampliar desde para beneficiarse de la infraestructura existente para establecer o obtener eficazmente las propiedades del [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) sombreador a través [de MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span><span class="sxs-lookup"><span data-stu-id="bf497-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="bf497-176">La información de la propiedad del sombreador se almacena en cada [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) a través de y [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .</span><span class="sxs-lookup"><span data-stu-id="bf497-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="bf497-177">Si extiende [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) , también puede ser útil invalidar [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) mediante *el nuevo*.</span><span class="sxs-lookup"><span data-stu-id="bf497-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="bf497-178">Código de ejemplo: `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="bf497-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="bf497-179">Además, las siguientes clases amplían la clase que usa de nuevo [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) para modificar los valores de propiedad del sombreador.</span><span class="sxs-lookup"><span data-stu-id="bf497-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="bf497-180">Este enfoque [ayuda al rendimiento](https://docs.unity3d.com/Manual/DrawCallBatching.html) porque *MaterialPropertyBlocks* no crea nuevos materiales con instancias cuando cambian los valores.</span><span class="sxs-lookup"><span data-stu-id="bf497-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="bf497-181">Sin embargo, el acceso a las [propiedades de clase Material](https://docs.unity3d.com/ScriptReference/Material.html) típicas no devolverá los valores esperados.</span><span class="sxs-lookup"><span data-stu-id="bf497-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="bf497-182">Use *MaterialPropertyBlocks para* obtener y validar los valores de propiedad de material actuales (es decir,</span><span class="sxs-lookup"><span data-stu-id="bf497-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="bf497-183">*_Color* o *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="bf497-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="bf497-184">Dirige al tema para restablecer las propiedades modificadas a sus valores originales establecidos en el gameObject del host cuando se inicializó este motor de tema.</span><span class="sxs-lookup"><span data-stu-id="bf497-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="bf497-185">Ejemplo de motor de tema personalizado</span><span class="sxs-lookup"><span data-stu-id="bf497-185">Custom theme engine example</span></span>

<span data-ttu-id="bf497-186">La clase siguiente es un ejemplo de un nuevo motor de temas personalizado.</span><span class="sxs-lookup"><span data-stu-id="bf497-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="bf497-187">Esta implementación buscará un componente [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) en el objeto host inicializado y controlará su visibilidad en función del estado actual.</span><span class="sxs-lookup"><span data-stu-id="bf497-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a><span data-ttu-id="bf497-188">Ejemplo de un extremo a otro</span><span class="sxs-lookup"><span data-stu-id="bf497-188">End-to-end example</span></span>

<span data-ttu-id="bf497-189">Al extenderse fuera del motor de temas personalizado definido en la sección anterior, el ejemplo de código siguiente muestra cómo controlar este tema en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="bf497-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="bf497-190">En concreto, cómo establecer el estado actual en el tema para que la visibilidad de MeshRenderer se actualice correctamente.</span><span class="sxs-lookup"><span data-stu-id="bf497-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="bf497-191">`theme.OnUpdate(state,force)` Por lo general, se debe llamar a en el método Update() para admitir los motores de temas que usan la aceleración o el equilibrio entre valores.</span><span class="sxs-lookup"><span data-stu-id="bf497-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="bf497-192">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bf497-192">See also</span></span>

- [<span data-ttu-id="bf497-193">Interactuable</span><span class="sxs-lookup"><span data-stu-id="bf497-193">Interactable</span></span>](interactable.md)
