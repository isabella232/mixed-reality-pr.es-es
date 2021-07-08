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
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Mixed Reality y HoloLens auxiliares de teclado

MRTK proporciona varios componentes auxiliares experimentales para ayudar a iniciar y leer texto desde [el teclado del sistema](../ux-building-blocks/system-keyboard.md).

Tenga en cuenta que el teclado del sistema se comportará según las funcionalidades de la plataforma de destino; por ejemplo, el teclado de HoloLens 2 admitiría interacciones de manos directas, mientras que el teclado de HoloLens (1.ª generación) admitiría GGV<sup>[1.](/windows/mixed-reality/gaze)</sup> Además, el teclado del sistema no se mostrará al realizar la comunicación remota de [Unity](../tools/holographic-remoting.md) desde el editor a un HoloLens.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) es un componente que proporciona métodos para iniciar y cerrar un teclado del sistema, así como interactuar con el texto escrito por el teclado.  

### <a name="how-to-use"></a>Cómo se usa

1. [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard)Adjunte el componente a cualquier objeto.
2. Llame a para mostrar y ocultar el teclado y controle los eventos , y que se controlarán cuando se muestre, oculte y cuando se presione `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` la tecla `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` Entrar.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Campos de TMP_KeyboardInputField y UI_KeyboardInputField

Las clases y son componentes que se pueden agregar a los campos de entrada de texto para invocar automáticamente el teclado del sistema cuando se hace clic en él y actualizar el contenido del campo de entrada de texto a medida que el usuario escribe [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) texto.

### <a name="how-to-use"></a>Cómo se usa

1. Cree un campo de entrada para UnityUI o TextMeshPro.
2. Agregue el componente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) o correspondiente al objeto de juego de campo de [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) entrada.

Los elementos prefabs para los campos de entrada UnityUI y TextMeshPro (TMPro) están disponibles en "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" (Activos\MRTK\Experimental\MixedRealityKeyboard\Prefabs)

Un ejemplo de cómo usar TMP_KeyboardInputField y UI_KeyboardInputField en "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"