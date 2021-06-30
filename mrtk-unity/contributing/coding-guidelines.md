---
title: Instrucciones de codificación
description: Principios y convenciones de codificación que se deben seguir al contribuir a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, C#,
ms.openlocfilehash: 122c51962c55796c037302c7b79cc4df643a47b7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121443"
---
# <a name="coding-guidelines"></a><span data-ttu-id="9961c-104">Instrucciones de codificación</span><span class="sxs-lookup"><span data-stu-id="9961c-104">Coding guidelines</span></span>

<span data-ttu-id="9961c-105">En este documento se describen los principios y convenciones de codificación que se deben seguir al contribuir a MRTK.</span><span class="sxs-lookup"><span data-stu-id="9961c-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="9961c-106">Filosofía</span><span class="sxs-lookup"><span data-stu-id="9961c-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="9961c-107">Ser conciso y procurar la simplicidad</span><span class="sxs-lookup"><span data-stu-id="9961c-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="9961c-108">La solución más sencilla suele ser la mejor.</span><span class="sxs-lookup"><span data-stu-id="9961c-108">The simplest solution is often the best.</span></span> <span data-ttu-id="9961c-109">Este es un objetivo reemplazable de estas directrices y debe ser el objetivo de toda la actividad de codificación.</span><span class="sxs-lookup"><span data-stu-id="9961c-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="9961c-110">Parte de ser sencillo es ser conciso y coherente con el código existente.</span><span class="sxs-lookup"><span data-stu-id="9961c-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="9961c-111">Intente que el código sea sencillo.</span><span class="sxs-lookup"><span data-stu-id="9961c-111">Try to keep your code simple.</span></span>

<span data-ttu-id="9961c-112">Los lectores solo deben encontrar artefactos que proporcionen información útil.</span><span class="sxs-lookup"><span data-stu-id="9961c-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="9961c-113">Por ejemplo, los comentarios que restablecen lo que es obvio no proporcionan ninguna información adicional y aumentan la proporción de ruido y señal.</span><span class="sxs-lookup"><span data-stu-id="9961c-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="9961c-114">Mantenga la lógica de código simple.</span><span class="sxs-lookup"><span data-stu-id="9961c-114">Keep code logic simple.</span></span> <span data-ttu-id="9961c-115">Tenga en cuenta que no se trata de una instrucción sobre cómo usar el menor número de líneas, minimizar el tamaño de los nombres de identificador o el estilo de llave, sino reducir el número de conceptos y maximizar la visibilidad de las líneas a través de patrones conocidos.</span><span class="sxs-lookup"><span data-stu-id="9961c-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="9961c-116">Generación de código coherente y legible</span><span class="sxs-lookup"><span data-stu-id="9961c-116">Produce consistent, readable code</span></span>

<span data-ttu-id="9961c-117">La legibilidad del código está correlacionada con tasas de defectos bajas.</span><span class="sxs-lookup"><span data-stu-id="9961c-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="9961c-118">Esfuérzse por crear código fácil de leer.</span><span class="sxs-lookup"><span data-stu-id="9961c-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="9961c-119">Esfuérzate por crear código que tenga lógica simple y vuelva a usar los componentes existentes, ya que también ayudará a garantizar la corrección.</span><span class="sxs-lookup"><span data-stu-id="9961c-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="9961c-120">Todos los detalles del código que se genera son importantes, desde los detalles más básicos de corrección hasta el estilo y el formato coherentes.</span><span class="sxs-lookup"><span data-stu-id="9961c-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="9961c-121">Mantenga el estilo de codificación coherente con lo que ya existe, aunque no coincida con sus preferencias.</span><span class="sxs-lookup"><span data-stu-id="9961c-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="9961c-122">Esto aumenta la legibilidad del código base general.</span><span class="sxs-lookup"><span data-stu-id="9961c-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="9961c-123">Compatibilidad con la configuración de componentes en el editor y en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="9961c-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="9961c-124">MRTK admite un conjunto diverso de usuarios: personas que prefieren configurar componentes en el editor de Unity y cargar objetos prefabs, y personas que necesitan crear instancias y configurar objetos en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9961c-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="9961c-125">Todo el código debe funcionar agregando un componente a un GameObject en una escena guardada y mediante la creación de instancias de ese componente en el código.</span><span class="sxs-lookup"><span data-stu-id="9961c-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="9961c-126">Las pruebas deben incluir un caso de prueba para crear instancias de los elementos prefab y crear instancias, y configurar el componente en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9961c-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="9961c-127">Play-in-editor es la primera plataforma de destino principal</span><span class="sxs-lookup"><span data-stu-id="9961c-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="9961c-128">Play-In-Editor es la manera más rápida de iterar en Unity.</span><span class="sxs-lookup"><span data-stu-id="9961c-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="9961c-129">Proporcionar maneras a nuestros clientes de iterar rápidamente les permite desarrollar soluciones más rápidamente y probar más ideas.</span><span class="sxs-lookup"><span data-stu-id="9961c-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="9961c-130">En otras palabras, maximizar la velocidad de iteración permite a nuestros clientes lograr más.</span><span class="sxs-lookup"><span data-stu-id="9961c-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="9961c-131">Haga que todo funcione en el editor y, a continuación, haga que funcione en cualquier otra plataforma.</span><span class="sxs-lookup"><span data-stu-id="9961c-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="9961c-132">Siga funcionando en el editor.</span><span class="sxs-lookup"><span data-stu-id="9961c-132">Keep it working in the editor.</span></span> <span data-ttu-id="9961c-133">Es fácil agregar una nueva plataforma a Play-In-Editor.</span><span class="sxs-lookup"><span data-stu-id="9961c-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="9961c-134">Es muy difícil hacer que Play-In-Editor funcione si la aplicación solo funciona en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9961c-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="9961c-135">Agregar nuevos campos públicos, propiedades, métodos y campos privados serializados con cuidado</span><span class="sxs-lookup"><span data-stu-id="9961c-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="9961c-136">Cada vez que se agrega un método público, un campo y una propiedad, se convierte en parte de la superficie de LA API pública de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9961c-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="9961c-137">Los campos privados marcados con `[SerializeField]` también exponen campos al editor y forman parte de la superficie de la API pública.</span><span class="sxs-lookup"><span data-stu-id="9961c-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="9961c-138">Otras personas pueden usar ese método público, configurar objetos prefab personalizados con el campo público y tomar una dependencia de él.</span><span class="sxs-lookup"><span data-stu-id="9961c-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="9961c-139">Los nuevos miembros públicos deben examinarse cuidadosamente.</span><span class="sxs-lookup"><span data-stu-id="9961c-139">New public members should be carefully examined.</span></span> <span data-ttu-id="9961c-140">Cualquier campo público deberá mantenerse en el futuro.</span><span class="sxs-lookup"><span data-stu-id="9961c-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="9961c-141">Recuerde que si el tipo de un campo público (o campo privado serializado) cambia o se quita de un MonoBehaviour, podría interrumpir a otras personas.</span><span class="sxs-lookup"><span data-stu-id="9961c-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="9961c-142">En primer lugar, el campo debe estar en desuso para una versión y es necesario proporcionar código para migrar los cambios de las personas que han tomado dependencias.</span><span class="sxs-lookup"><span data-stu-id="9961c-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="9961c-143">Priorizar la escritura de pruebas</span><span class="sxs-lookup"><span data-stu-id="9961c-143">Prioritize writing tests</span></span>

<span data-ttu-id="9961c-144">MRTK es un proyecto de la comunidad, modificado por una amplia gama de colaboradores.</span><span class="sxs-lookup"><span data-stu-id="9961c-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="9961c-145">Es posible que estos colaboradores no conozcan los detalles de la corrección o característica de errores y que la característica se rompa accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="9961c-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="9961c-146">[MRTK ejecuta pruebas de integración continuas](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) antes de completar cada solicitud de incorporación de extracción.</span><span class="sxs-lookup"><span data-stu-id="9961c-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="9961c-147">Los cambios que rompen las pruebas no se pueden comprobar.</span><span class="sxs-lookup"><span data-stu-id="9961c-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="9961c-148">Por lo tanto, las pruebas son la mejor manera de asegurarse de que otras personas no interrumpirán la característica.</span><span class="sxs-lookup"><span data-stu-id="9961c-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="9961c-149">Cuando corrija un error, escriba una prueba para asegurarse de que no se revierte en el futuro.</span><span class="sxs-lookup"><span data-stu-id="9961c-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="9961c-150">Si agrega una característica, escriba pruebas que comprueben que la característica funciona.</span><span class="sxs-lookup"><span data-stu-id="9961c-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="9961c-151">Esto es necesario para todas las características de la experiencia de usuario, excepto las características experimentales.</span><span class="sxs-lookup"><span data-stu-id="9961c-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="9961c-152">Convenciones de codificación de C#</span><span class="sxs-lookup"><span data-stu-id="9961c-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="9961c-153">Encabezados de información de licencia de script</span><span class="sxs-lookup"><span data-stu-id="9961c-153">Script license information headers</span></span>

<span data-ttu-id="9961c-154">Todos los empleados de Microsoft que contribuyen a nuevos archivos deben agregar el siguiente encabezado de licencia estándar en la parte superior de los archivos nuevos, exactamente como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="9961c-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="9961c-155">Encabezados de resumen de función/método</span><span class="sxs-lookup"><span data-stu-id="9961c-155">Function / method summary headers</span></span>

<span data-ttu-id="9961c-156">Todas las clases públicas, structs, enumeraciones, funciones, propiedades, campos publicados en MRTK deben describirse como su propósito y uso, exactamente como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="9961c-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

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

<span data-ttu-id="9961c-157">Esto garantiza que la documentación se genera y se propaga correctamente para todas las clases, métodos y propiedades.</span><span class="sxs-lookup"><span data-stu-id="9961c-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="9961c-158">Se rechazarán los archivos de script enviados sin las etiquetas de resumen adecuadas.</span><span class="sxs-lookup"><span data-stu-id="9961c-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="9961c-159">Reglas de espacio de nombres de MRTK</span><span class="sxs-lookup"><span data-stu-id="9961c-159">MRTK namespace rules</span></span>

<span data-ttu-id="9961c-160">El Mixed Reality Toolkit usa un modelo de espacio de nombres basado en características, donde todos los espacios de nombres fundamentales comienzan por "Microsoft.MixedReality.Toolkit".</span><span class="sxs-lookup"><span data-stu-id="9961c-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="9961c-161">En general, no es necesario especificar la capa del kit de herramientas (por ejemplo, Core, Providers, Services) en los espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="9961c-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="9961c-162">Los espacios de nombres definidos actualmente son:</span><span class="sxs-lookup"><span data-stu-id="9961c-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="9961c-163">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="9961c-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="9961c-164">Microsoft.MixedReality.Toolkit.Boundary</span><span class="sxs-lookup"><span data-stu-id="9961c-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="9961c-165">Microsoft.MixedReality.Toolkit.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="9961c-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="9961c-166">Microsoft.MixedReality.Toolkit.Editor</span><span class="sxs-lookup"><span data-stu-id="9961c-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="9961c-167">Microsoft.MixedReality.Toolkit.Input</span><span class="sxs-lookup"><span data-stu-id="9961c-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="9961c-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span><span class="sxs-lookup"><span data-stu-id="9961c-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="9961c-169">Microsoft.MixedReality.Toolkit.Teleport</span><span class="sxs-lookup"><span data-stu-id="9961c-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="9961c-170">Microsoft.MixedReality.Toolkit.Utilities</span><span class="sxs-lookup"><span data-stu-id="9961c-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="9961c-171">En el caso de los espacios de nombres con una gran cantidad de tipos, es aceptable crear un número limitado de subparátipos de espacio de nombres para ayudar a limitar el uso.</span><span class="sxs-lookup"><span data-stu-id="9961c-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="9961c-172">Si se omite el espacio de nombres de una interfaz, clase o tipo de datos, se bloqueará el cambio.</span><span class="sxs-lookup"><span data-stu-id="9961c-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="9961c-173">Adición de nuevos scripts de MonoBehaviour</span><span class="sxs-lookup"><span data-stu-id="9961c-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="9961c-174">Al agregar nuevos scripts de MonoBehaviour con una solicitud de incorporación de cambios, asegúrese de que el atributo se aplica a [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) todos los archivos aplicables.</span><span class="sxs-lookup"><span data-stu-id="9961c-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="9961c-175">Esto garantiza que el componente se pueda detectar fácilmente en el editor en el *botón Agregar* componente.</span><span class="sxs-lookup"><span data-stu-id="9961c-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="9961c-176">La marca de atributo no es necesaria si el componente no se puede mostrar en el editor, como una clase abstracta.</span><span class="sxs-lookup"><span data-stu-id="9961c-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="9961c-177">En el ejemplo siguiente, el *paquete debe* rellenarse con la ubicación del paquete del componente.</span><span class="sxs-lookup"><span data-stu-id="9961c-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="9961c-178">Si coloca un elemento en *la carpeta MRTK/SDK,* el paquete será *SDK*.</span><span class="sxs-lookup"><span data-stu-id="9961c-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="9961c-179">Adición de nuevos scripts de inspector de Unity</span><span class="sxs-lookup"><span data-stu-id="9961c-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="9961c-180">En general, intente evitar la creación de scripts de inspector personalizados para los componentes de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9961c-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="9961c-181">Agrega sobrecarga adicional y administración del código base que podría controlar el motor de Unity.</span><span class="sxs-lookup"><span data-stu-id="9961c-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="9961c-182">Si se necesita una clase inspectora, intente usar el de [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) Unity.</span><span class="sxs-lookup"><span data-stu-id="9961c-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="9961c-183">Esto simplifica de nuevo la clase inspector y deja gran parte del trabajo a Unity.</span><span class="sxs-lookup"><span data-stu-id="9961c-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="9961c-184">Si se requiere una representación personalizada en la clase inspector, intente utilizar [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) y [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) .</span><span class="sxs-lookup"><span data-stu-id="9961c-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="9961c-185">Esto garantizará que Unity controla correctamente la representación de objetos prefab anidados y valores modificados.</span><span class="sxs-lookup"><span data-stu-id="9961c-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="9961c-186">Si no se puede usar debido a un requisito en la lógica personalizada, asegúrese de que todo [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) el uso se ajusta alrededor de [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) .</span><span class="sxs-lookup"><span data-stu-id="9961c-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="9961c-187">Esto garantizará que Unity represente el inspector correctamente para los elementos prefab anidados y los valores modificados con la propiedad dada.</span><span class="sxs-lookup"><span data-stu-id="9961c-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="9961c-188">Además, intente decorar la clase de inspector personalizado con [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) un .</span><span class="sxs-lookup"><span data-stu-id="9961c-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="9961c-189">Esta etiqueta garantiza que se pueden seleccionar y modificar juntos varios objetos con este componente en la escena.</span><span class="sxs-lookup"><span data-stu-id="9961c-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="9961c-190">Las nuevas clases de inspector deben probar que su código funciona en esta situación en la escena.</span><span class="sxs-lookup"><span data-stu-id="9961c-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

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

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="9961c-191">Adición de nuevos objetos ScriptableObjects</span><span class="sxs-lookup"><span data-stu-id="9961c-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="9961c-192">Al agregar nuevos scripts ScriptableObject, asegúrese de [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) que el atributo se aplica a todos los archivos aplicables.</span><span class="sxs-lookup"><span data-stu-id="9961c-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="9961c-193">Esto garantiza que el componente se pueda detectar fácilmente en el editor a través de los menús de creación de recursos.</span><span class="sxs-lookup"><span data-stu-id="9961c-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="9961c-194">La marca de atributo no es necesaria si el componente no se puede mostrar en el editor, como una clase abstracta.</span><span class="sxs-lookup"><span data-stu-id="9961c-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="9961c-195">En el ejemplo siguiente, la *subcarpeta* debe rellenarse con la subcarpeta MRTK, si procede.</span><span class="sxs-lookup"><span data-stu-id="9961c-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="9961c-196">Si coloca un elemento en *la carpeta MRTK/Providers,* el paquete será *Providers*.</span><span class="sxs-lookup"><span data-stu-id="9961c-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="9961c-197">Si coloca un elemento en la *carpeta MRTK/Core,* establezca esta opción en "Perfiles".</span><span class="sxs-lookup"><span data-stu-id="9961c-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="9961c-198">En el ejemplo siguiente, el archivo *MyNewService | MyNewProvider* debe rellenarse con el nombre de la nueva clase, si procede.</span><span class="sxs-lookup"><span data-stu-id="9961c-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="9961c-199">Si coloca un elemento en la *carpeta MixedRealityToolkit,* deje esta cadena fuera.</span><span class="sxs-lookup"><span data-stu-id="9961c-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a><span data-ttu-id="9961c-200">Registro</span><span class="sxs-lookup"><span data-stu-id="9961c-200">Logging</span></span>

<span data-ttu-id="9961c-201">Al agregar nuevas características o actualizar las características existentes, considere la posibilidad de agregar registros DebugUtilities.LogVerbose a código interesante que puede ser útil para la depuración futura.</span><span class="sxs-lookup"><span data-stu-id="9961c-201">When adding new features or updating existing features, consider adding DebugUtilities.LogVerbose logs to interesting code that may be useful for future debugging.</span></span> <span data-ttu-id="9961c-202">Aquí hay un equilibrio entre agregar registro y el ruido agregado y no hay suficiente registro (lo que dificulta el diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="9961c-202">There's a tradeoff here between adding logging and the added noise and not enough logging (which makes diagnosis difficult).</span></span>

<span data-ttu-id="9961c-203">Un ejemplo interesante en el que el registro es útil (junto con una carga útil interesante):</span><span class="sxs-lookup"><span data-stu-id="9961c-203">An interesting example where having logging is useful (along with interesting payload):</span></span>

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

<span data-ttu-id="9961c-204">Este tipo de registro puede ayudar a detectar problemas como , causados por eventos de origen no [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) coincidentes detectados y de pérdida de origen.</span><span class="sxs-lookup"><span data-stu-id="9961c-204">This type of logging can help catch issues like [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016), which were caused by mismatched source detected and source lost events.</span></span>

<span data-ttu-id="9961c-205">Evite agregar registros para los datos y eventos que se producen en cada fotograma; idealmente, el registro debe cubrir eventos "interesantes" controlados por distintas entradas de usuario (es decir, un "clic" por parte de un usuario y el conjunto de cambios y eventos que proceden de que son interesantes de registrar).</span><span class="sxs-lookup"><span data-stu-id="9961c-205">Avoid adding logs for data and events that are occurring on every frame - ideally logging should cover "interesting" events driven by distinct user inputs (i.e. a "click" by a user and the set of changes and events that come from that are interesting to log).</span></span> <span data-ttu-id="9961c-206">El estado continuo de "el usuario sigue manteniendo un gesto" registrado en cada fotograma no es interesante y sobrecargará los registros.</span><span class="sxs-lookup"><span data-stu-id="9961c-206">The ongoing state of "user is still holding a gesture" logged every frame is not interesting and will overwhelm the logs.</span></span>

<span data-ttu-id="9961c-207">Tenga en cuenta que este registro detallado no está activado de forma predeterminada (debe estar habilitado en la configuración [del sistema de diagnóstico).](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)</span><span class="sxs-lookup"><span data-stu-id="9961c-207">Note that this verbose logging is not turned on by default (it must be enabled in the [Diagnostic System settings](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span></span>

### <a name="spaces-vs-tabs"></a><span data-ttu-id="9961c-208">Espacios frente a pestañas</span><span class="sxs-lookup"><span data-stu-id="9961c-208">Spaces vs tabs</span></span>

<span data-ttu-id="9961c-209">Asegúrese de usar 4 espacios en lugar de pestañas al contribuir a este proyecto.</span><span class="sxs-lookup"><span data-stu-id="9961c-209">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="9961c-210">Espaciado</span><span class="sxs-lookup"><span data-stu-id="9961c-210">Spacing</span></span>

<span data-ttu-id="9961c-211">No agregue espacios adicionales entre corchetes y paréntesis:</span><span class="sxs-lookup"><span data-stu-id="9961c-211">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-212">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-212">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="9961c-213">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-213">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="9961c-214">Convenciones de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="9961c-214">Naming conventions</span></span>

<span data-ttu-id="9961c-215">Use siempre `PascalCase` para las propiedades.</span><span class="sxs-lookup"><span data-stu-id="9961c-215">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="9961c-216">Se `camelCase` usa para la mayoría de los campos, excepto para los campos y `PascalCase` `static readonly` `const` .</span><span class="sxs-lookup"><span data-stu-id="9961c-216">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="9961c-217">La única excepción a esto es para las estructuras de datos que requieren que los campos sean serializados por `JsonUtility` .</span><span class="sxs-lookup"><span data-stu-id="9961c-217">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-218">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-218">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="9961c-219">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-219">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="9961c-220">Modificadores de acceso</span><span class="sxs-lookup"><span data-stu-id="9961c-220">Access modifiers</span></span>

<span data-ttu-id="9961c-221">Declare siempre un modificador de acceso para todos los campos, propiedades y métodos.</span><span class="sxs-lookup"><span data-stu-id="9961c-221">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="9961c-222">Todos los métodos de LA API de Unity deben ser de forma predeterminada, a menos que `private` tenga que invalidarlos en una clase derivada.</span><span class="sxs-lookup"><span data-stu-id="9961c-222">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="9961c-223">En este `protected` caso, se debe usar .</span><span class="sxs-lookup"><span data-stu-id="9961c-223">In this case `protected` should be used.</span></span>

- <span data-ttu-id="9961c-224">Los campos siempre deben ser `private` , con `public` los `protected` accessors de propiedad o .</span><span class="sxs-lookup"><span data-stu-id="9961c-224">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="9961c-225">Usar [miembros con forma de expresión y](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) propiedades [automáticas siempre](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) que sea posible</span><span class="sxs-lookup"><span data-stu-id="9961c-225">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-226">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-226">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="9961c-227">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-227">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="9961c-228">Usar llaves</span><span class="sxs-lookup"><span data-stu-id="9961c-228">Use braces</span></span>

<span data-ttu-id="9961c-229">Use siempre llaves después de cada bloque de instrucciones y colóctelas en la línea siguiente.</span><span class="sxs-lookup"><span data-stu-id="9961c-229">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-230">Cosas que evitar</span><span class="sxs-lookup"><span data-stu-id="9961c-230">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="9961c-231">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-231">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="9961c-232">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-232">Do</span></span>

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="9961c-233">Las clases públicas, las estructuras y las enumeraciones deben ir en sus propios archivos.</span><span class="sxs-lookup"><span data-stu-id="9961c-233">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="9961c-234">Si la clase, la estructura o la enumeración se pueden convertir en privadas, es correcto que se incluyan en el mismo archivo.</span><span class="sxs-lookup"><span data-stu-id="9961c-234">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="9961c-235">Esto evita problemas de compilación con Unity y garantiza que se produce la abstracción de código adecuada, también reduce los conflictos y los cambios importantes cuando el código necesita cambiar.</span><span class="sxs-lookup"><span data-stu-id="9961c-235">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-236">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-236">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="9961c-237">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-237">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="9961c-238">Cosas que hacer</span><span class="sxs-lookup"><span data-stu-id="9961c-238">Do</span></span>

<span data-ttu-id="9961c-239">MyStruct.cs</span><span class="sxs-lookup"><span data-stu-id="9961c-239">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="9961c-240">MyEnumType.cs</span><span class="sxs-lookup"><span data-stu-id="9961c-240">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="9961c-241">MyClass.cs</span><span class="sxs-lookup"><span data-stu-id="9961c-241">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="9961c-242">Inicialización de enumeraciones</span><span class="sxs-lookup"><span data-stu-id="9961c-242">Initialize enums</span></span>

<span data-ttu-id="9961c-243">Para asegurarse de que todas las enumeraciones se inicializan correctamente a partir de 0, .NET proporciona un acceso directo ordenado para inicializar automáticamente la enumeración agregando simplemente el primer valor (inicio).</span><span class="sxs-lookup"><span data-stu-id="9961c-243">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="9961c-244">(Por ejemplo, valor 1 = 0 No se requieren valores restantes)</span><span class="sxs-lookup"><span data-stu-id="9961c-244">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-245">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-245">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="9961c-246">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-246">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="9961c-247">Ordenación de enumeraciones para la extensión adecuada</span><span class="sxs-lookup"><span data-stu-id="9961c-247">Order enums for appropriate extension</span></span>

<span data-ttu-id="9961c-248">Es fundamental que, si es probable que una enumeración se pueda extender en el futuro, para ordenar los valores predeterminados en la parte superior de la enumeración, esto garantiza que los índices de enumeración no se ven afectados con nuevas adiciones.</span><span class="sxs-lookup"><span data-stu-id="9961c-248">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-249">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-249">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="9961c-250">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-250">Do</span></span>

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

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="9961c-251">Revisión del uso de enumeración para campos de bits</span><span class="sxs-lookup"><span data-stu-id="9961c-251">Review enum use for bitfields</span></span>

<span data-ttu-id="9961c-252">Si existe la posibilidad de que una enumeración requiera varios estados como valor, por ejemplo, Handedness = Left & Right.</span><span class="sxs-lookup"><span data-stu-id="9961c-252">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="9961c-253">A continuación, la enumeración debe decorarse correctamente con BitFlags para que se pueda usar correctamente.</span><span class="sxs-lookup"><span data-stu-id="9961c-253">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="9961c-254">El archivo Handedness.cs tiene una implementación concreta para esto.</span><span class="sxs-lookup"><span data-stu-id="9961c-254">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="9961c-255">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-255">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="9961c-256">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-256">Do</span></span>

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

### <a name="hard-coded-file-paths"></a><span data-ttu-id="9961c-257">Rutas de acceso de archivo codificadas de forma fuerte</span><span class="sxs-lookup"><span data-stu-id="9961c-257">Hard-coded file paths</span></span>

<span data-ttu-id="9961c-258">Al generar rutas de acceso de archivo de cadena y, en particular, escribir rutas de acceso de cadena codificadas de forma fuerte, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9961c-258">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="9961c-259">Use las API de C# [ `Path` siempre](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) que sea posible, como `Path.Combine` o `Path.GetFullPath` .</span><span class="sxs-lookup"><span data-stu-id="9961c-259">Use C#'s [`Path` APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="9961c-260">Use / o [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) en lugar de \ o \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="9961c-260">Use / or [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) instead of \ or \\\\.</span></span>

<span data-ttu-id="9961c-261">Estos pasos garantizan que MRTK funciona en sistemas basados en Windows y Unix.</span><span class="sxs-lookup"><span data-stu-id="9961c-261">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="9961c-262">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-262">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="9961c-263">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-263">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="9961c-264">Procedimientos recomendados, incluidas las recomendaciones de Unity</span><span class="sxs-lookup"><span data-stu-id="9961c-264">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="9961c-265">Algunas de las plataformas de destino de este proyecto requieren tener en cuenta el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="9961c-265">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="9961c-266">Con esto en mente, tenga siempre cuidado al asignar memoria en código con frecuencia llamado en bucles de actualización o algoritmos estrictos.</span><span class="sxs-lookup"><span data-stu-id="9961c-266">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="9961c-267">Encapsulación</span><span class="sxs-lookup"><span data-stu-id="9961c-267">Encapsulation</span></span>

<span data-ttu-id="9961c-268">Use siempre campos privados y propiedades públicas si se necesita acceso al campo desde fuera de la clase o struct.</span><span class="sxs-lookup"><span data-stu-id="9961c-268">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="9961c-269">Asegúrese de colocar el campo privado y la propiedad pública.</span><span class="sxs-lookup"><span data-stu-id="9961c-269">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="9961c-270">Esto facilita ver, de un vistazo, lo que hace detrás de la propiedad y que el campo se puede modifica mediante script.</span><span class="sxs-lookup"><span data-stu-id="9961c-270">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="9961c-271">La única excepción a esto es para las estructuras de datos que requieren que los campos sean serializados por , donde se requiere que una clase de datos tenga todos los campos públicos para que funcione `JsonUtility` la serialización.</span><span class="sxs-lookup"><span data-stu-id="9961c-271">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-272">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-272">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="9961c-273">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-273">Do</span></span>

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

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="9961c-274">Almacenar en caché valores y serializarlos en la escena o prefab siempre que sea posible</span><span class="sxs-lookup"><span data-stu-id="9961c-274">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="9961c-275">Con HoloLens en mente, es mejor optimizar el rendimiento y almacenar en caché las referencias en la escena o prefab para limitar las asignaciones de memoria en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9961c-275">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-276">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-276">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="9961c-277">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-277">Do</span></span>

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

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="9961c-278">Almacenar en caché referencias a materiales, no llamar a ".material" cada vez</span><span class="sxs-lookup"><span data-stu-id="9961c-278">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="9961c-279">Unity creará un nuevo material cada vez que use ".material", lo que provocará una pérdida de memoria si no se limpia correctamente.</span><span class="sxs-lookup"><span data-stu-id="9961c-279">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="9961c-280">Lo que debe evitar:</span><span class="sxs-lookup"><span data-stu-id="9961c-280">Don't</span></span>

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

#### <a name="do"></a><span data-ttu-id="9961c-281">Lo que es necesario hacer:</span><span class="sxs-lookup"><span data-stu-id="9961c-281">Do</span></span>

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
> <span data-ttu-id="9961c-282">Como alternativa, use la propiedad "SharedMaterial" de Unity, que no crea un nuevo material cada vez que se hace referencia a él.</span><span class="sxs-lookup"><span data-stu-id="9961c-282">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="9961c-283">Uso [de la compilación dependiente de](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) la plataforma para asegurarse de que el kit de herramientas no interrumpirá la compilación en otra plataforma</span><span class="sxs-lookup"><span data-stu-id="9961c-283">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="9961c-284">Use `WINDOWS_UWP` para usar API específicas de UWP que no son de Unity.</span><span class="sxs-lookup"><span data-stu-id="9961c-284">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="9961c-285">Esto impedirá que intenten ejecutarse en el editor o en plataformas no admitidas.</span><span class="sxs-lookup"><span data-stu-id="9961c-285">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="9961c-286">Esto es equivalente a `UNITY_WSA && !UNITY_EDITOR` y debe usarse en favor de .</span><span class="sxs-lookup"><span data-stu-id="9961c-286">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="9961c-287">Use `UNITY_WSA` para usar LAS API de Unity específicas de UWP, como el espacio de nombres `UnityEngine.XR.WSA` .</span><span class="sxs-lookup"><span data-stu-id="9961c-287">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="9961c-288">Esto se ejecutará en el Editor cuando la plataforma esté establecida en UWP, así como en aplicaciones para UWP integradas.</span><span class="sxs-lookup"><span data-stu-id="9961c-288">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="9961c-289">Este gráfico puede ayudarle a decidir qué usar, en función de los casos `#if` de uso y la configuración de compilación que espera.</span><span class="sxs-lookup"><span data-stu-id="9961c-289">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

|<span data-ttu-id="9961c-290">Plataforma</span><span class="sxs-lookup"><span data-stu-id="9961c-290">Platform</span></span> | <span data-ttu-id="9961c-291">UWP IL2CPP</span><span class="sxs-lookup"><span data-stu-id="9961c-291">UWP IL2CPP</span></span> | <span data-ttu-id="9961c-292">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="9961c-292">UWP .NET</span></span> | <span data-ttu-id="9961c-293">Editor</span><span class="sxs-lookup"><span data-stu-id="9961c-293">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="9961c-294">Falso</span><span class="sxs-lookup"><span data-stu-id="9961c-294">False</span></span> | <span data-ttu-id="9961c-295">False</span><span class="sxs-lookup"><span data-stu-id="9961c-295">False</span></span> | <span data-ttu-id="9961c-296">True</span><span class="sxs-lookup"><span data-stu-id="9961c-296">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="9961c-297">True</span><span class="sxs-lookup"><span data-stu-id="9961c-297">True</span></span> | <span data-ttu-id="9961c-298">True</span><span class="sxs-lookup"><span data-stu-id="9961c-298">True</span></span> | <span data-ttu-id="9961c-299">True</span><span class="sxs-lookup"><span data-stu-id="9961c-299">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="9961c-300">True</span><span class="sxs-lookup"><span data-stu-id="9961c-300">True</span></span> | <span data-ttu-id="9961c-301">True</span><span class="sxs-lookup"><span data-stu-id="9961c-301">True</span></span> | <span data-ttu-id="9961c-302">False</span><span class="sxs-lookup"><span data-stu-id="9961c-302">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="9961c-303">True</span><span class="sxs-lookup"><span data-stu-id="9961c-303">True</span></span> | <span data-ttu-id="9961c-304">True</span><span class="sxs-lookup"><span data-stu-id="9961c-304">True</span></span> | <span data-ttu-id="9961c-305">False</span><span class="sxs-lookup"><span data-stu-id="9961c-305">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="9961c-306">True</span><span class="sxs-lookup"><span data-stu-id="9961c-306">True</span></span> | <span data-ttu-id="9961c-307">True</span><span class="sxs-lookup"><span data-stu-id="9961c-307">True</span></span> | <span data-ttu-id="9961c-308">Falso</span><span class="sxs-lookup"><span data-stu-id="9961c-308">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="9961c-309">False</span><span class="sxs-lookup"><span data-stu-id="9961c-309">False</span></span> | <span data-ttu-id="9961c-310">True</span><span class="sxs-lookup"><span data-stu-id="9961c-310">True</span></span> | <span data-ttu-id="9961c-311">Falso</span><span class="sxs-lookup"><span data-stu-id="9961c-311">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="9961c-312">Preferir DateTime.UtcNow en lugar de DateTime.Now</span><span class="sxs-lookup"><span data-stu-id="9961c-312">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="9961c-313">DateTime.UtcNow es más rápido que DateTime.Now.</span><span class="sxs-lookup"><span data-stu-id="9961c-313">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="9961c-314">En investigaciones de rendimiento anteriores, hemos descubierto que el uso de DateTime.Now agrega una sobrecarga significativa especialmente cuando se usa en el bucle Update().</span><span class="sxs-lookup"><span data-stu-id="9961c-314">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="9961c-315">[Otros han tenido el mismo problema.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)</span><span class="sxs-lookup"><span data-stu-id="9961c-315">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="9961c-316">Prefiere usar DateTime.UtcNow a menos que realmente necesite las horas localizadas (un motivo legítimo puede ser que quiera mostrar la hora actual en la zona horaria del usuario).</span><span class="sxs-lookup"><span data-stu-id="9961c-316">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="9961c-317">Si está trabajando con horas relativas (es decir, la diferencia entre alguna última actualización y ahora), es mejor usar DateTime.UtcNow para evitar la sobrecarga de realizar conversiones de zona horaria.</span><span class="sxs-lookup"><span data-stu-id="9961c-317">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="9961c-318">Convenciones de codificación de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9961c-318">PowerShell coding conventions</span></span>

<span data-ttu-id="9961c-319">Un subconjunto del código base de MRTK usa PowerShell para la infraestructura de canalización y varios scripts y utilidades.</span><span class="sxs-lookup"><span data-stu-id="9961c-319">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="9961c-320">El nuevo código de PowerShell debe seguir [el estilo PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span><span class="sxs-lookup"><span data-stu-id="9961c-320">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="9961c-321">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9961c-321">See also</span></span>

 [<span data-ttu-id="9961c-322">Convenciones de codificación de C# de MSDN</span><span class="sxs-lookup"><span data-stu-id="9961c-322">C# coding conventions from MSDN</span></span>](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)