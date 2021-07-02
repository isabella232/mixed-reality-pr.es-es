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
# <a name="system-keyboard"></a><span data-ttu-id="48cfb-104">Teclado del sistema</span><span class="sxs-lookup"><span data-stu-id="48cfb-104">System keyboard</span></span>

![Teclado del sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="48cfb-106">Una aplicación de Unity puede invocar el teclado del sistema en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="48cfb-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="48cfb-107">Tenga en cuenta que el teclado del sistema se comportará según las funcionalidades de la plataforma de destino, por ejemplo, el teclado de HoloLens 2 admitiría interacciones de manos directas, mientras que el teclado de HoloLens (1ª generación) admitiría GGV (mirada, gesto y voz)<sup>[1.](/windows/mixed-reality/gaze)</sup></span><span class="sxs-lookup"><span data-stu-id="48cfb-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="48cfb-108">Además, el teclado del sistema no se mostrará al realizar la comunicación remota [de Unity](../tools/holographic-remoting.md) desde el editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="48cfb-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="48cfb-109">Cómo invocar el teclado del sistema</span><span class="sxs-lookup"><span data-stu-id="48cfb-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="48cfb-110">Cómo leer la entrada</span><span class="sxs-lookup"><span data-stu-id="48cfb-110">How to read the input</span></span>

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

## <a name="system-keyboard-example"></a><span data-ttu-id="48cfb-111">Ejemplo de teclado del sistema</span><span class="sxs-lookup"><span data-stu-id="48cfb-111">System keyboard example</span></span>

<span data-ttu-id="48cfb-112">Puede ver un ejemplo sencillo de cómo abrir el teclado del sistema `MixedRealityKeyboard.cs` en (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span><span class="sxs-lookup"><span data-stu-id="48cfb-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="48cfb-113">Consulte también</span><span class="sxs-lookup"><span data-stu-id="48cfb-113">See Also</span></span>

- [<span data-ttu-id="48cfb-114">Mixed Reality del asistente de teclado</span><span class="sxs-lookup"><span data-stu-id="48cfb-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
