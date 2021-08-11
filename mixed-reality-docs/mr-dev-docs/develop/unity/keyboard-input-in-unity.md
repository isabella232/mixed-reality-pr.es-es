---
title: Entrada desde teclado en Unity
description: Unity proporciona la clase TouchScreenKeyboard para aceptar entradas de teclado cuando no hay ningún teclado físico disponible.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: teclado, entrada, unity, pantalla táctilkeyboard, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, HoloLens, HoloLens 2
ms.openlocfilehash: a7bd392036ca548fdd1f25581c8fc1910308909253f9c8df763e2039a32d3e9a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203857"
---
# <a name="keyboard-input-in-unity"></a>Entrada desde teclado en Unity

**Espacio de nombres:** *UnityEngine*<br>
 **Tipo:** *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Aunque HoloLens admite muchas formas de entrada, incluidos Bluetooth teclados, la mayoría de las aplicaciones no pueden suponer que todos los usuarios tendrán un teclado físico disponible. Si la aplicación requiere entrada de texto, se debe proporcionar algún tipo de teclado en pantalla.

Unity proporciona la *[clase TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceptar entradas de teclado cuando no hay ningún teclado físico disponible.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>HoloLens de teclado del sistema en Unity

En HoloLens, *TouchScreenKeyboard* aprovecha el teclado en pantalla del sistema y se superpone directamente sobre la vista volumétrica de la aplicación de MR. La experiencia es similar al uso del teclado en las aplicaciones integradas de HoloLens. Tenga en cuenta que el teclado del sistema se comportará según las funcionalidades de la plataforma de destino; por ejemplo, el teclado de HoloLens 2 admitiría interacciones de manos directas, mientras que el teclado de HoloLens (1.ª generación) admitiría GGV (mirada, gesto y voz). Además, el teclado del sistema no se mostrará al realizar la comunicación remota de Unity desde el editor a un HoloLens.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Uso del teclado del sistema en la aplicación de Unity

### <a name="declare-the-keyboard"></a>Declarar el teclado

En la clase , declare una variable para almacenar *TouchScreenKeyboard* y una variable para contener la cadena que devuelve el teclado.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Invocación del teclado

Cuando se produzca un evento que solicite la entrada de teclado, use lo siguiente para mostrar el teclado.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

Puede usar parámetros adicionales pasados a la función para controlar el comportamiento del teclado (por ejemplo, establecer texto de marcador de posición o admitir la `TouchScreenKeyboard.Open` autocorrección). Para obtener la lista completa de parámetros, consulte la [documentación de Unity.](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)

### <a name="retrieve-typed-contents"></a>Recuperación del contenido con tipo

El contenido se puede recuperar simplemente llamando a `keyboard.text` . Es posible que quiera recuperar el contenido por fotograma o solo cuando se cierre el teclado.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Opciones alternativas de teclado

Además de usar la *clase TouchScreenKeyboard* directamente, también puede  obtener la entrada del usuario mediante el campo de entrada de la interfaz de usuario de Unity o el campo de *entrada TextMeshPro*. Además, hay una implementación basada en *TouchScreenKeyboard* en la escena [HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) de [MRTK](/windows/mixed-reality/mrtk-unity) (hay un ejemplo de interacción con el teclado en el lado izquierdo).

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra en medio de la exploración de las API y las funcionalidades de Mixed Reality plataforma. Desde aquí, puede continuar con [cualquier](unity-development-overview.md#3-advanced-features) tema o saltar directamente a la implementación de la aplicación en un dispositivo o emulador.

> [!div class="nextstepaction"]
> [Implementación en HoloLens o Windows Mixed Reality cascos envolventes](../platform-capabilities-and-apis/using-visual-studio.md)
