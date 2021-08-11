---
title: Temas visuales
description: 'Información general: Control flexible de los recursos de la experiencia de usuario en MRTK'
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, temas de MRTK,
ms.openlocfilehash: f7e0b10f51947884c4d23191fd147315084c5295e9b48953bb5de10b7cbc0d22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223978"
---
# <a name="visual-themes"></a>Temas visuales

Los temas permiten un control flexible de los recursos de la experiencia de usuario en respuesta a diversas transiciones de estados. Esto puede implicar cambiar el color de un botón, cambiar el tamaño de un elemento en respuesta al foco, etc. El marco de visual themes se integra en dos partes clave: 1) configuración y 2) motores en tiempo de ejecución.

[Las configuraciones de tema](#theme-configuration) son [](#theme-engines) definiciones de propiedades y tipos, mientras que los motores de temas son clases que consumen las configuraciones e implementan la lógica para actualizar transformaciones, materiales y mucho más en tiempo de ejecución.

## <a name="theme-configuration"></a>Configuración del tema

Las configuraciones de tema [son ScriptableObjects que](https://docs.unity3d.com/Manual/class-ScriptableObject.html) definen cómo se inicializarán los motores de temas en tiempo de ejecución. Definen qué propiedades y valores usar en respuesta a los cambios de entrada u otros cambios de estado cuando se ejecuta la aplicación. Como [recursos de ScriptableObjects,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) las configuraciones de tema se pueden definir una vez y, a continuación, volver a usarse en distintos componentes de la experiencia de usuario.

Para crear un nuevo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) recurso:

1) Haga clic con el botón derecho *en Project ventana.*
1) Seleccione **Create** Mixed Reality Toolkit Theme  >  **(Crear Mixed Reality Toolkit**  >  **tema).**

Los recursos de configuración de tema de ejemplo se pueden encontrar en `MRTK/SDK/Features/UX/Interactable/Themes` .

![Ejemplo de ScriptableObject de tema en inspector](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>States

Al crear un nuevo [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , lo primero que hay que establecer es qué estados están disponibles. La *propiedad States* indica cuántos valores debe definir una configuración de tema, ya que habrá un valor por estado. En la imagen de ejemplo anterior, los estados predeterminados definidos para el componente [Interactable](interactable.md#general-input-settings) son *Default*, *Focus*, *Pressed* y *Disabled*. Se definen en el archivo de recursos `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States).

Para crear un nuevo [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) recurso:

1) Haga clic con el botón derecho *en Project ventana.*
1) Seleccione **Create** Mixed Reality Toolkit State  >  **(Crear Mixed Reality Toolkit**  >  **estado).**

![Ejemplo de ScriptableObject de estados en inspector](../images/interactable/DefaultInteractableStates.png)

ScriptableObject define tanto la lista de estados como el [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) tipo de *StateModel* que se creará para estos estados. *StateModel* es una clase que extiende e implementa la lógica de la máquina de estado para generar el estado actual en tiempo de [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) ejecución. Los motores de temas en tiempo de ejecución suelen usar el estado actual de esta clase para determinar qué valores se establecerán en las propiedades de material, las transformaciones de GameObject y mucho más.

### <a name="theme-engine-properties"></a>Propiedades del motor de temas

Fuera de *Estados*, un recurso también define una lista de motores de [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) temas y las propiedades asociadas para estos motores. Un [motor de tema](#theme-engines) define de nuevo la lógica para establecer los valores correctos en un GameObject en tiempo de ejecución.

Un recurso puede definir varios motores de temas para lograr transiciones sofisticadas de estados visuales [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) destinadas a varias propiedades gameObject.

**Tiempo de ejecución de temas**

Define el tipo de clase del motor de tema que se creará.

**Facilitar**

Algunos *motores de temas*, si definen su propiedad [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) como true, admiten la aceleración entre estados. Por ejemplo, la lerping entre dos colores cuando se produce un cambio de estado. La *duración* define en segundos cuánto tiempo se  va a facilitar desde el valor inicial hasta el valor final y la curva de animación define la tasa de cambio durante ese período de tiempo.

**Propiedades del sombreador**

Algunos motores de temas , si definen su propiedad [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) como true, modificarán propiedades de sombreador *concretas* en tiempo de ejecución. Los *campos Sombreador* *y Propiedad* definen la propiedad del sombreador de destino.

### <a name="create-a-theme-configuration-via-code"></a>Creación de una configuración de tema mediante código

En general, es más fácil diseñar configuraciones de tema a través del inspector de Unity, pero hay casos en los que los temas se deben generar dinámicamente en tiempo de ejecución a través del código. El fragmento de código siguiente proporciona un ejemplo de cómo realizar esta tarea.

Para ayudar a acelerar el desarrollo, los siguientes métodos auxiliares son útiles para simplificar la configuración.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable): crea un nuevo objeto States ScriptableObject con los cuatro valores de estado predeterminados utilizados en el [componente Interactable.](interactable.md)

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Cada motor de temas define una configuración predeterminada con las propiedades correctas necesarias para ese tipo de tiempo de ejecución de tema. Este asistente crea una definición para el tipo de motor de tema especificado.

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

## <a name="theme-engines"></a>Motores de temas

Un [motor de](#theme-engines) temas es una clase que se extiende desde la clase [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) . Se crea una instancia de estas clases en tiempo de ejecución y se configuran con [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) un objeto como se ha descrito anteriormente.

### <a name="default-theme-engines"></a>Motores de temas predeterminados

MRTK se incluye con un conjunto predeterminado de motores de temas que se enumeran a continuación:

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

Los motores de temas predeterminados se pueden encontrar en `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Motores de temas personalizados

Como se ha indicado, un motor de temas se define como una clase que se extiende desde la [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) clase . Por lo tanto, el nuevo motor de temas solo necesita extender esta clase e implementar lo siguiente:

#### <a name="mandatory-implementations"></a>Implementaciones obligatorias

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.SetValue)

Para la propiedad determinada, que se puede identificar mediante , establezca su valor de estado actual en el host gameObject de destino `ThemeStateProperty.Name` (es decir, establecer el color del material, etc.). El *índice* indica el valor de estado actual al que se va a obtener acceso y el porcentaje *,* un valor float entre 0 y 1, se usa para la aceleración o el equilibrio entre valores.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetProperty)

Para la propiedad determinada, que se puede identificar mediante , devuelve el valor actual establecido en el objeto GameObject host `ThemeStateProperty.Name` de destino (es decir, el color del material actual, el desplazamiento de la posición local actual, etc.). Esto se usa principalmente para almacenar en caché el valor de inicio cuando se acelera entre estados.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality. Toolkit. Ui. InteractableThemeBase.GetDefaultThemeDefinition)

Devuelve un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objeto que define las propiedades y la configuración predeterminadas necesarias para el tema personalizado.

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Variante protegida de la definición pública, excepto el valor ThemePropertyValue proporcionado para establecer en lugar de dirigir para usar la `SetValue()` configuración de índice o porcentaje.

#### <a name="recommended-overrides"></a>Invalidaciones recomendadas

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Realice los pasos de inicialización aquí dirigidos al parámetro *GameObject* proporcionado y use las propiedades y configuraciones definidas en el *parámetro ThemeDefinition.* Se recomienda llamar al `base.Init(host, settings)` principio de una invalidación.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Si el motor de temas personalizado puede admitir la aceleración entre los valores que se configuran a través de la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) propiedad .

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Si el motor de temas personalizado puede admitir propiedades de sombreador de destino. Se recomienda ampliar desde para beneficiarse de la infraestructura existente para establecer o obtener eficazmente las propiedades del [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) sombreador a través [de MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html). La información de la propiedad del sombreador se almacena en cada [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) a través de y [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .

> [!NOTE]
> Si extiende [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) , también puede ser útil invalidar [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) mediante *el nuevo*.
>
> Código de ejemplo: `protected new const string DefaultShaderProperty = "_Color";`
>
> Además, las siguientes clases amplían la clase que usa de nuevo [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) para modificar los valores de propiedad del sombreador. Este enfoque [ayuda al rendimiento](https://docs.unity3d.com/Manual/DrawCallBatching.html) porque *MaterialPropertyBlocks* no crea nuevos materiales con instancias cuando cambian los valores. Sin embargo, el acceso a las [propiedades de clase Material](https://docs.unity3d.com/ScriptReference/Material.html) típicas no devolverá los valores esperados. Use *MaterialPropertyBlocks para* obtener y validar los valores de propiedad de material actuales (es decir, *_Color* o *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Dirige al tema para restablecer las propiedades modificadas a sus valores originales establecidos en el gameObject del host cuando se inicializó este motor de tema.  

### <a name="custom-theme-engine-example"></a>Ejemplo de motor de tema personalizado

La clase siguiente es un ejemplo de un nuevo motor de temas personalizado. Esta implementación buscará un componente [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) en el objeto host inicializado y controlará su visibilidad en función del estado actual.

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

## <a name="end-to-end-example"></a>Ejemplo de un extremo a otro

Al extenderse fuera del motor de temas personalizado definido en la sección anterior, el ejemplo de código siguiente muestra cómo controlar este tema en tiempo de ejecución. En concreto, cómo establecer el estado actual en el tema para que la visibilidad de MeshRenderer se actualice correctamente.

> [!NOTE]
> `theme.OnUpdate(state,force)` Por lo general, se debe llamar a en el método Update() para admitir los motores de temas que usan la aceleración o el equilibrio entre valores.

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

## <a name="see-also"></a>Consulte también

- [Interactuable](interactable.md)
