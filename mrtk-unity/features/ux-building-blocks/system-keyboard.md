---
title: Teclado del sistema
description: Información general del panel de claves del sistema en MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, teclado del sistema,
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176495"
---
# <a name="system-keyboard"></a>Teclado del sistema

![Teclado del sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Una aplicación de Unity puede invocar el teclado del sistema en cualquier momento. Tenga en cuenta que el teclado del sistema se comportará según las funcionalidades de la plataforma de destino, por ejemplo, el teclado de HoloLens 2 admitiría interacciones de manos directas, mientras que el teclado de HoloLens (1ª generación) admitiría GGV (mirada, gesto y voz)<sup>[1.](/windows/mixed-reality/gaze)</sup> Además, el teclado del sistema no se mostrará al realizar la comunicación remota [de Unity](../tools/holographic-remoting.md) desde el editor a un HoloLens.

## <a name="how-to-invoke-the-system-keyboard"></a>Cómo invocar el teclado del sistema

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a>Cómo leer la entrada

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a>Ejemplo de teclado del sistema

Puede ver un ejemplo sencillo de cómo abrir el teclado del sistema `MixedRealityKeyboard.cs` en (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)

## <a name="see-also"></a>Consulte también

- [Mixed Reality del asistente de teclado](../experimental/mixed-reality-keyboard.md)
