---
title: Teclado de Mixed Reality
description: descripción en Uso del teclado de realidad mixta
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 6a33ed5b021e90cba56344f32a9c9a33e8fcc476
ms.sourcegitcommit: c260aed8a37855faf9575d968e615959a56a13fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2021
ms.locfileid: "113466235"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="bf378-104">Mixed Reality y HoloLens auxiliares de teclado</span><span class="sxs-lookup"><span data-stu-id="bf378-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="bf378-105">MRTK proporciona varios componentes auxiliares experimentales para ayudar a iniciar y leer texto desde [el teclado del sistema](../ux-building-blocks/system-keyboard.md).</span><span class="sxs-lookup"><span data-stu-id="bf378-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="bf378-106">Tenga en cuenta que el teclado del sistema se comportará según las funcionalidades de la plataforma de destino; por ejemplo, el teclado de HoloLens 2 admitiría interacciones de manos directas, mientras que el teclado de HoloLens (1.ª generación) admitiría GGV<sup>[1.](/windows/mixed-reality/gaze)</sup></span><span class="sxs-lookup"><span data-stu-id="bf378-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="bf378-107">Además, el teclado del sistema no se mostrará al realizar la comunicación remota de [Unity](../tools/holographic-remoting.md) desde el editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bf378-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="bf378-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="bf378-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="bf378-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) es un componente que proporciona métodos para iniciar y cerrar un teclado del sistema, así como interactuar con el texto escrito por el teclado.</span><span class="sxs-lookup"><span data-stu-id="bf378-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="bf378-110">Cómo se usa</span><span class="sxs-lookup"><span data-stu-id="bf378-110">How to Use</span></span>

1. <span data-ttu-id="bf378-111">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard)Adjunte el componente a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="bf378-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="bf378-112">Llame a para mostrar y ocultar el teclado y controle los eventos , y que se controlarán cuando se muestre, oculte y cuando se presione `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` la tecla `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` Entrar.</span><span class="sxs-lookup"><span data-stu-id="bf378-112">Call `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="bf378-113">Campos de TMP_KeyboardInputField y UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="bf378-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="bf378-114">Las clases y son componentes que se pueden agregar a los campos de entrada de texto para invocar automáticamente el teclado del sistema cuando se hace clic en él y actualizar el contenido del campo de entrada de texto a medida que el usuario escribe [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) texto.</span><span class="sxs-lookup"><span data-stu-id="bf378-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="bf378-115">Cómo se usa</span><span class="sxs-lookup"><span data-stu-id="bf378-115">How to use</span></span>

1. <span data-ttu-id="bf378-116">Cree un campo de entrada para UnityUI o TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="bf378-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="bf378-117">Agregue el componente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) o correspondiente al objeto de juego de campo de [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) entrada.</span><span class="sxs-lookup"><span data-stu-id="bf378-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="bf378-118">Los elementos prefabs para los campos de entrada UnityUI y TextMeshPro (TMPro) están disponibles en "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" (Activos\MRTK\Experimental\MixedRealityKeyboard\Prefabs)</span><span class="sxs-lookup"><span data-stu-id="bf378-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="bf378-119">Un ejemplo de cómo usar TMP_KeyboardInputField y UI_KeyboardInputField en "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span><span class="sxs-lookup"><span data-stu-id="bf378-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>