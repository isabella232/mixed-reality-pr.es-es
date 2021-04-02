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
# <a name="keyboard-input-in-unity"></a>Entrada desde teclado en Unity

**Espacio de nombres:** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Aunque HoloLens admite muchas formas de entrada, incluidos los teclados Bluetooth, la mayoría de las aplicaciones no puede suponer que todos los usuarios tendrán un teclado físico disponible. Si la aplicación requiere una entrada de texto, se debe proporcionar alguna forma de teclado en pantalla.

Unity proporciona la clase *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceptar la entrada de teclado cuando no hay ningún teclado físico disponible.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamiento del teclado del sistema HoloLens en Unity

En HoloLens, el *TouchScreenKeyboard* aprovecha el teclado en pantalla del sistema y las superposiciones directamente sobre la vista volumétrica de la aplicación Mr. La experiencia es similar a usar el teclado en las aplicaciones integradas de HoloLens. Tenga en cuenta que el teclado del sistema se comportará de acuerdo con las capacidades de la plataforma de destino; por ejemplo, el teclado de HoloLens 2 admitiría interacciones de manos directas, mientras que el teclado de HoloLens (1º gen) admitiría GGV (con miras, gestos y voz). Además, el teclado del sistema no se mostrará al realizar la comunicación remota de Unity desde el editor a HoloLens.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Uso del teclado del sistema en la aplicación de Unity

### <a name="declare-the-keyboard"></a>Declarar el teclado

En la clase, declare una variable para almacenar el *TouchScreenKeyboard* y una variable que contenga la cadena que devuelve el teclado.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Invocar el teclado

Cuando se produzca un evento que solicite la entrada del teclado, use lo siguiente para mostrar el teclado.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

Puede usar parámetros adicionales que se pasan a la `TouchScreenKeyboard.Open` función para controlar el comportamiento del teclado (por ejemplo, establecer el texto del marcador de posición o admitir la corrección automáticamente). Para obtener la lista completa de parámetros, consulte la [documentación de Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).

### <a name="retrieve-typed-contents"></a>Recuperar contenido con tipo

El contenido solo se puede recuperar llamando a `keyboard.text` . Puede que desee recuperar el contenido por fotograma o solo cuando el teclado esté cerrado.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Opciones de teclado alternativas

Además de usar directamente la clase *TouchScreenKeyboard* , también puede obtener datos proporcionados por el usuario mediante el campo de *entrada* de la interfaz de usuario de Unity o el *campo de entrada TextMeshPro*. Además, hay una implementación basada en *TouchScreenKeyboard* en la [escena HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) de [MRTK](/windows/mixed-reality/mrtk-unity) (hay un ejemplo de interacción de teclado en el lado izquierdo).

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar las API y funcionalidades de la plataforma de realidad mixta. Desde aquí, puede continuar con cualquier [tema](unity-development-overview.md#3-advanced-features) o ir directamente a la implementación de la aplicación en un dispositivo o emulador.

> [!div class="nextstepaction"]
> [Implementación en HoloLens o con auriculares de Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
