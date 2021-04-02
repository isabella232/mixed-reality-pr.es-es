---
title: Entrada desde teclado en Unity
description: Unity proporciona la clase TouchScreenKeyboard para aceptar la entrada de teclado cuando no hay ningún teclado físico disponible.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: teclado, entrada, Unity, touchscreenkeyboard, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098277"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="d34bd-104">Entrada desde teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="d34bd-104">Keyboard input in Unity</span></span>

<span data-ttu-id="d34bd-105">**Espacio de nombres:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="d34bd-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="d34bd-106">**Tipo**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="d34bd-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="d34bd-107">Aunque HoloLens admite muchas formas de entrada, incluidos los teclados Bluetooth, la mayoría de las aplicaciones no puede suponer que todos los usuarios tendrán un teclado físico disponible.</span><span class="sxs-lookup"><span data-stu-id="d34bd-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="d34bd-108">Si la aplicación requiere una entrada de texto, se debe proporcionar alguna forma de teclado en pantalla.</span><span class="sxs-lookup"><span data-stu-id="d34bd-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="d34bd-109">Unity proporciona la clase *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceptar la entrada de teclado cuando no hay ningún teclado físico disponible.</span><span class="sxs-lookup"><span data-stu-id="d34bd-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="d34bd-110">Comportamiento del teclado del sistema HoloLens en Unity</span><span class="sxs-lookup"><span data-stu-id="d34bd-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="d34bd-111">En HoloLens, el *TouchScreenKeyboard* aprovecha el teclado en pantalla del sistema y las superposiciones directamente sobre la vista volumétrica de la aplicación Mr.</span><span class="sxs-lookup"><span data-stu-id="d34bd-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="d34bd-112">La experiencia es similar a usar el teclado en las aplicaciones integradas de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d34bd-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="d34bd-113">Tenga en cuenta que el teclado del sistema se comportará de acuerdo con las capacidades de la plataforma de destino; por ejemplo, el teclado de HoloLens 2 admitiría interacciones de manos directas, mientras que el teclado de HoloLens (1º gen) admitiría GGV (con miras, gestos y voz).</span><span class="sxs-lookup"><span data-stu-id="d34bd-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="d34bd-114">Además, el teclado del sistema no se mostrará al realizar la comunicación remota de Unity desde el editor a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d34bd-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="d34bd-115">Uso del teclado del sistema en la aplicación de Unity</span><span class="sxs-lookup"><span data-stu-id="d34bd-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="d34bd-116">Declarar el teclado</span><span class="sxs-lookup"><span data-stu-id="d34bd-116">Declare the keyboard</span></span>

<span data-ttu-id="d34bd-117">En la clase, declare una variable para almacenar el *TouchScreenKeyboard* y una variable que contenga la cadena que devuelve el teclado.</span><span class="sxs-lookup"><span data-stu-id="d34bd-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="d34bd-118">Invocar el teclado</span><span class="sxs-lookup"><span data-stu-id="d34bd-118">Invoke the keyboard</span></span>

<span data-ttu-id="d34bd-119">Cuando se produzca un evento que solicite la entrada del teclado, use lo siguiente para mostrar el teclado.</span><span class="sxs-lookup"><span data-stu-id="d34bd-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="d34bd-120">Puede usar parámetros adicionales que se pasan a la `TouchScreenKeyboard.Open` función para controlar el comportamiento del teclado (por ejemplo, establecer el texto del marcador de posición o admitir la corrección automáticamente).</span><span class="sxs-lookup"><span data-stu-id="d34bd-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="d34bd-121">Para obtener la lista completa de parámetros, consulte la [documentación de Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span><span class="sxs-lookup"><span data-stu-id="d34bd-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="d34bd-122">Recuperar contenido con tipo</span><span class="sxs-lookup"><span data-stu-id="d34bd-122">Retrieve typed contents</span></span>

<span data-ttu-id="d34bd-123">El contenido solo se puede recuperar llamando a `keyboard.text` .</span><span class="sxs-lookup"><span data-stu-id="d34bd-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="d34bd-124">Puede que desee recuperar el contenido por fotograma o solo cuando el teclado esté cerrado.</span><span class="sxs-lookup"><span data-stu-id="d34bd-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="d34bd-125">Opciones de teclado alternativas</span><span class="sxs-lookup"><span data-stu-id="d34bd-125">Alternative keyboard options</span></span>

<span data-ttu-id="d34bd-126">Además de usar directamente la clase *TouchScreenKeyboard* , también puede obtener datos proporcionados por el usuario mediante el campo de *entrada* de la interfaz de usuario de Unity o el *campo de entrada TextMeshPro*.</span><span class="sxs-lookup"><span data-stu-id="d34bd-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="d34bd-127">Además, hay una implementación basada en *TouchScreenKeyboard* en la [escena HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) de [MRTK](/windows/mixed-reality/mrtk-unity) (hay un ejemplo de interacción de teclado en el lado izquierdo).</span><span class="sxs-lookup"><span data-stu-id="d34bd-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d34bd-128">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="d34bd-128">Next Development Checkpoint</span></span>

<span data-ttu-id="d34bd-129">Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d34bd-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="d34bd-130">Desde aquí, puede continuar con cualquier [tema](unity-development-overview.md#3-advanced-features) o ir directamente a la implementación de la aplicación en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="d34bd-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d34bd-131">Implementación en HoloLens o con auriculares de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d34bd-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
