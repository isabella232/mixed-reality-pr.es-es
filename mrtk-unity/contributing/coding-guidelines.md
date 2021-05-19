---
title: Instrucciones de codificación
description: principios y convenciones de codificación que se deben seguir al contribuir a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, C#,
ms.openlocfilehash: 8887e248bd550bdd7a59f19c16df1ec3647ceff7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145243"
---
# <a name="coding-guidelines"></a>Instrucciones de codificación

En este documento se describen los principios y convenciones de codificación que se deben seguir al contribuir a MRTK.

---

## <a name="philosophy"></a>Filosofía

### <a name="be-concise-and-strive-for-simplicity"></a>Sea conciso y esfuérzate por la simplicidad

La solución más sencilla suele ser la mejor. Este es un objetivo reemplazable de estas directrices y debe ser el objetivo de toda la actividad de codificación. Parte de ser simple es ser conciso y coherente con el código existente. Intente que el código sea sencillo.

Los lectores solo deben encontrar artefactos que proporcionen información útil. Por ejemplo, los comentarios que restablecen lo obvio no proporcionan información adicional y aumentan la proporción de ruido y señal.

Mantenga la lógica de código simple. Tenga en cuenta que no se trata de una instrucción sobre el uso del menor número de líneas, lo que minimiza el tamaño de los nombres de identificador o el estilo de llaves, sino que reduce el número de conceptos y maximiza la visibilidad de las líneas a través de patrones conocidos.

### <a name="produce-consistent-readable-code"></a>Generación de código coherente y legible

La legibilidad del código se correlaciona con tasas de defectos bajas. Esfuérctese por crear código que sea fácil de leer. Esfuérzate por crear código que tenga una lógica simple y vuelva a usar los componentes existentes, ya que también ayudará a garantizar la corrección.

Todos los detalles del código que genera son importantes, desde los detalles más básicos de la corrección hasta el estilo y el formato coherentes. Mantenga el estilo de codificación coherente con lo que ya existe, incluso si no coincide con sus preferencias. Esto aumenta la legibilidad del código base general.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>Compatibilidad con la configuración de componentes en el editor y en tiempo de ejecución

MRTK admite un conjunto diverso de usuarios: personas que prefieren configurar componentes en el editor de Unity y cargar objetos prefabs, y personas que necesitan crear instancias y configurar objetos en tiempo de ejecución.

Todo el código debe funcionar agregando un componente a un GameObject en una escena guardada y mediante la creación de instancias de ese componente en el código. Las pruebas deben incluir un caso de prueba para crear instancias de los elementos prefab y crear instancias, y configurar el componente en tiempo de ejecución.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>Play-in-editor es la primera plataforma de destino principal

Play-In-Editor es la manera más rápida de iterar en Unity. Proporcionar maneras a nuestros clientes de iterar rápidamente les permite desarrollar soluciones más rápidamente y probar más ideas. En otras palabras, maximizar la velocidad de iteración permite a nuestros clientes lograr más.

Haga que todo funcione en el editor y, a continuación, haga que funcione en cualquier otra plataforma. Siga funcionando en el editor. Es fácil agregar una nueva plataforma a Play-In-Editor. Es muy difícil hacer que Play-In-Editor funcione si la aplicación solo funciona en un dispositivo.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>Agregar nuevos campos públicos, propiedades, métodos y campos privados serializados con cuidado

Cada vez que se agrega un método público, un campo y una propiedad, se convierte en parte de la superficie de LA API pública de MRTK. Los campos privados marcados con `[SerializeField]` también exponen campos al editor y forman parte de la superficie de la API pública. Otras personas pueden usar ese método público, configurar objetos prefab personalizados con el campo público y tomar una dependencia de él.

Los nuevos miembros públicos deben examinarse cuidadosamente. Cualquier campo público deberá mantenerse en el futuro. Recuerde que si el tipo de un campo público (o campo privado serializado) cambia o se quita de un MonoBehaviour, podría interrumpir a otras personas. En primer lugar, el campo debe estar en desuso para una versión y es necesario proporcionar código para migrar los cambios de las personas que han tomado dependencias.

### <a name="prioritize-writing-tests"></a>Priorizar la escritura de pruebas

MRTK es un proyecto de la comunidad, modificado por una amplia gama de colaboradores. Es posible que estos colaboradores no conozcan los detalles de la corrección o característica de errores y que la característica se rompa accidentalmente. [MRTK ejecuta pruebas de integración continuas](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) antes de completar cada solicitud de incorporación de extracción. Los cambios que interrumpirán las pruebas no se pueden comprobar. Por lo tanto, las pruebas son la mejor manera de asegurarse de que otras personas no interrumpirán la característica.

Cuando corrija un error, escriba una prueba para asegurarse de que no se revierte en el futuro. Si agrega una característica, escriba pruebas que comprueben que la característica funciona. Esto es necesario para todas las características de la experiencia de usuario, excepto las características experimentales.

## <a name="c-coding-conventions"></a>Convenciones de codificación de C#

### <a name="script-license-information-headers"></a>Script de encabezados de información de licencia

Todos los empleados de Microsoft que contribuyen a nuevos archivos deben agregar el siguiente encabezado de licencia estándar en la parte superior de los archivos nuevos, exactamente como se muestra a continuación:

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>Encabezados de resumen de función/método

Todas las clases públicas, structs, enumeraciones, funciones, propiedades, campos publicados en MRTK deben describirse como su propósito y uso, exactamente como se muestra a continuación:

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

Esto garantiza que la documentación se genera y se propaga correctamente para todas las clases, métodos y propiedades.

Se rechazarán los archivos de script enviados sin las etiquetas de resumen adecuadas.

### <a name="mrtk-namespace-rules"></a>Reglas de espacio de nombres de MRTK

El Mixed Reality toolkit usa un modelo de espacio de nombres basado en características, donde todos los espacios de nombres fundamentales comienzan por "Microsoft.MixedReality.Toolkit". En general, no es necesario especificar la capa del kit de herramientas (por ejemplo, Core, Providers, Services) en los espacios de nombres.

Los espacios de nombres definidos actualmente son:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Boundary
- Microsoft.MixedReality.Toolkit.Diagnostics
- Microsoft.MixedReality.Toolkit.Editor
- Microsoft.MixedReality.Toolkit.Input
- Microsoft.MixedReality.Toolkit.SpatialAwareness
- Microsoft.MixedReality.Toolkit.Teleport
- Microsoft.MixedReality.Toolkit.Utilities

En el caso de los espacios de nombres con una gran cantidad de tipos, es aceptable crear un número limitado de subparátipos de espacio de nombres para ayudar a limitar el uso.

Si se omite el espacio de nombres de una interfaz, clase o tipo de datos, se bloqueará el cambio.

### <a name="adding-new-monobehaviour-scripts"></a>Adición de nuevos scripts de MonoBehaviour

Al agregar nuevos scripts de MonoBehaviour con una solicitud de incorporación de cambios, asegúrese de que el atributo se aplica a [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) todos los archivos aplicables. Esto garantiza que el componente se pueda detectar fácilmente en el editor en el *botón Agregar* componente. La marca de atributo no es necesaria si el componente no se puede mostrar en el editor, como una clase abstracta.

En el ejemplo siguiente, el *paquete debe* rellenarse con la ubicación del paquete del componente. Si coloca un elemento en *la carpeta MRTK/SDK,* el paquete será *SDK*.

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>Adición de nuevos scripts de inspector de Unity

En general, intente evitar la creación de scripts de inspector personalizados para los componentes de MRTK. Agrega sobrecarga adicional y administración del código base que podría controlar el motor de Unity.

Si es necesaria una clase inspectora, intente usar el elemento de [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) Unity. Esto simplifica de nuevo la clase inspector y deja gran parte del trabajo a Unity.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Si se requiere una representación personalizada en la clase inspector, intente utilizar [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) y [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) . Esto garantizará que Unity controla correctamente la representación de elementos prefabs anidados y valores modificados.

Si no se puede usar debido a un requisito en la lógica personalizada, asegúrese de que todo [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) el uso se ajusta alrededor de [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) . Esto garantizará que Unity represente el inspector correctamente para los elementos prefab anidados y los valores modificados con la propiedad dada.

Además, intente decorar la clase inspectora personalizada con [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) un . Esta etiqueta garantiza que se pueden seleccionar y modificar juntos varios objetos con este componente en la escena. Las nuevas clases de inspector deben probar que su código funciona en esta situación en la escena.

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a>Adición de nuevos objetos ScriptableObjects

Al agregar nuevos scripts ScriptableObject, asegúrese de que [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) el atributo se aplica a todos los archivos aplicables. Esto garantiza que el componente se pueda detectar fácilmente en el editor a través de los menús de creación de recursos. La marca de atributo no es necesaria si el componente no se puede mostrar en el editor, como una clase abstracta.

En el ejemplo siguiente, la *subcarpeta* debe rellenarse con la subcarpeta MRTK, si procede. Si coloca un elemento en *la carpeta MRTK/Providers,* el paquete será *Providers*. Si coloca un elemento en la *carpeta MRTK/Core,* establezca esta opción en "Perfiles".

En el ejemplo siguiente, *el | MyNewProvider* debe rellenarse con el nombre de la nueva clase, si procede. Si coloca un elemento en la *carpeta MixedRealityToolkit,* deje esta cadena fuera.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Registro

Al agregar nuevas características o actualizar las características existentes, considere la posibilidad de agregar registros DebugUtilities.LogVerbose a código interesante que puede ser útil para la depuración futura. Aquí hay un equilibrio entre agregar el registro y el ruido agregado y no hay suficiente registro (lo que dificulta el diagnóstico).

Un ejemplo interesante en el que el registro es útil (junto con una carga útil interesante):

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

Este tipo de registro puede ayudar a detectar problemas como , causados por eventos de origen no [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) coincidentes detectados y pérdidas de origen.

Evite agregar registros para los datos y eventos que se producen en cada fotograma; idealmente, el registro debe cubrir eventos "interesantes" controlados por distintas entradas de usuario (es decir, un "clic" por parte de un usuario y el conjunto de cambios y eventos que proceden de que son interesantes de registrar). El estado continuo de "el usuario sigue manteniendo un gesto" registrado en cada fotograma no es interesante y sobrecargará los registros.

Tenga en cuenta que este registro detallado no está activado de forma predeterminada (debe estar habilitado en la configuración [del sistema de diagnóstico).](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)

### <a name="spaces-vs-tabs"></a>Espacios frente a pestañas

Asegúrese de usar 4 espacios en lugar de pestañas al contribuir a este proyecto.

### <a name="spacing"></a>Espaciado

No agregue espacios adicionales entre corchetes y paréntesis:

#### <a name="dont"></a>Lo que debe evitar:

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>Convenciones de nomenclatura

Use siempre `PascalCase` para las propiedades. Se `camelCase` usa para la mayoría de los campos, excepto para los campos y `PascalCase` `static readonly` `const` . La única excepción a esto es para las estructuras de datos que requieren que los campos sean serializados por `JsonUtility` .

#### <a name="dont"></a>Lo que debe evitar:

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>Modificadores de acceso

Declare siempre un modificador de acceso para todos los campos, propiedades y métodos.

- Todos los métodos de LA API de Unity deben ser de forma predeterminada, a menos que `private` tenga que invalidarlos en una clase derivada. En este `protected` caso, se debe usar .

- Los campos siempre deben ser `private` , con `public` los `protected` accessors de propiedad o .

- Usar [miembros con forma de expresión y](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) propiedades [automáticas siempre](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) que sea posible

#### <a name="dont"></a>Lo que debe evitar:

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>Usar llaves

Use siempre llaves después de cada bloque de instrucciones y colóctelas en la línea siguiente.

#### <a name="dont"></a>Cosas que evitar

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>Lo que debe evitar:

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Las clases públicas, las estructuras y las enumeraciones deben ir en sus propios archivos.

Si la clase, la estructura o la enumeración se pueden convertir en privadas, es correcto que se incluyan en el mismo archivo.  Esto evita problemas de compilación con Unity y garantiza que se produce la abstracción de código adecuada, también reduce los conflictos y los cambios importantes cuando es necesario cambiar el código.

#### <a name="dont"></a>Lo que debe evitar:

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>Cosas que hacer

MyStruct.cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType.cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass.cs

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>Inicialización de enumeraciones

Para asegurarse de que todas las enumeraciones se inicializan correctamente a partir de 0, .NET proporciona un acceso directo ordenado para inicializar automáticamente la enumeración simplemente agregando el primer valor (iniciador). (Por ejemplo, el valor 1 = 0 los valores restantes no son necesarios)

#### <a name="dont"></a>Lo que debe evitar:

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>Ordenar enumeraciones para la extensión adecuada

Es fundamental que si es probable que una enumeración se pueda extender en el futuro, para ordenar los valores predeterminados en la parte superior de la enumeración, esto garantiza que los índices de enumeración no se ven afectados con nuevas adiciones.

#### <a name="dont"></a>Lo que debe evitar:

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a>Revisión del uso de enumeración para campos de bits

Si existe la posibilidad de que una enumeración requiera varios estados como valor, por ejemplo, Handedness = Left & Right. A continuación, la enumeración debe decorarse correctamente con BitFlags para que se pueda usar correctamente.

El archivo Handedness.cs tiene una implementación concreta para esto.

### <a name="dont"></a>Lo que debe evitar:

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>Lo que es necesario hacer:

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a>Rutas de acceso de archivo codificadas de forma hard-coded

Al generar rutas de acceso de archivo de cadena y, en concreto, escribir rutas de acceso de cadena codificadas de forma fuerte, haga lo siguiente:

1. Use las API de C# [ `Path` siempre](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) que sea posible, como `Path.Combine` o `Path.GetFullPath` .
1. Use / o [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) en lugar de \ o \\ \\ .

Estos pasos garantizan que MRTK funciona en sistemas basados en Windows y Unix.

### <a name="dont"></a>Lo que debe evitar:

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>Lo que es necesario hacer:

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>Procedimientos recomendados, incluidas las recomendaciones de Unity

Algunas de las plataformas de destino de este proyecto requieren tener en cuenta el rendimiento. Con esto en mente, tenga siempre cuidado al asignar memoria en código que se llama con frecuencia en bucles de actualización o algoritmos estrictos.

### <a name="encapsulation"></a>Encapsulación

Use siempre campos privados y propiedades públicas si se necesita acceso al campo desde fuera de la clase o struct.  Asegúrese de colocar el campo privado y la propiedad pública. Esto facilita ver, de un vistazo, lo que hace detrás de la propiedad y que el campo se puede modifica mediante script.

> [!NOTE]
> La única excepción a esto es para las estructuras de datos que requieren que los campos sean serializados por , donde se requiere que una clase de datos tenga todos los campos públicos para que funcione `JsonUtility` la serialización.

#### <a name="dont"></a>Lo que debe evitar:

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>Almacenar en caché valores y serializarlos en la escena o prefab siempre que sea posible

Con HoloLens en mente, es mejor optimizar el rendimiento y almacenar en caché las referencias en la escena o prefab para limitar las asignaciones de memoria en tiempo de ejecución.

#### <a name="dont"></a>Lo que debe evitar:

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>Almacenar en caché referencias a materiales, no llamar a ".material" cada vez

Unity creará un nuevo material cada vez que use ".material", lo que provocará una pérdida de memoria si no se limpia correctamente.

#### <a name="dont"></a>Lo que debe evitar:

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a>Lo que es necesario hacer:

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> Como alternativa, use la propiedad "SharedMaterial" de Unity, que no crea un nuevo material cada vez que se hace referencia a él.

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>Uso [de la compilación dependiente de](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) la plataforma para asegurarse de que el kit de herramientas no interrumpirá la compilación en otra plataforma

- Use `WINDOWS_UWP` para usar API específicas de UWP que no son de Unity. Esto impedirá que intenten ejecutarse en el editor o en plataformas no admitidas. Esto es equivalente a `UNITY_WSA && !UNITY_EDITOR` y debe usarse en favor de .
- Use para usar LAS API de `UNITY_WSA` Unity específicas de UWP, como el espacio de `UnityEngine.XR.WSA` nombres . Esto se ejecutará en el Editor cuando la plataforma esté establecida en UWP, así como en aplicaciones para UWP integradas.

Este gráfico puede ayudarle a decidir qué usar, en función de los casos `#if` de uso y la configuración de compilación que espera.

|Plataforma | UWP IL2CPP | UWP .NET | Editor |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | Falso | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | Falso |
| `NETFX_CORE` | False | True | Falso |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>Preferir DateTime.UtcNow en lugar de DateTime.Now

DateTime.UtcNow es más rápido que DateTime.Now. En investigaciones de rendimiento anteriores, hemos descubierto que el uso de DateTime.Now agrega una sobrecarga significativa especialmente cuando se usa en el bucle Update(). [Otros han tenido el mismo problema.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)

Prefiere usar DateTime.UtcNow a menos que realmente necesite las horas localizadas (un motivo legítimo puede ser que quiera mostrar la hora actual en la zona horaria del usuario). Si está trabajando con horas relativas (es decir, la diferencia entre alguna última actualización y ahora), es mejor usar DateTime.UtcNow para evitar la sobrecarga de realizar conversiones de zona horaria.

## <a name="powershell-coding-conventions"></a>Convenciones de codificación de PowerShell

Un subconjunto del código base de MRTK usa PowerShell para la infraestructura de canalización y varios scripts y utilidades. El nuevo código de PowerShell debe seguir [el estilo PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).

## <a name="see-also"></a>Consulte también

 [Convenciones de codificación de C# de MSDN](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)