---
title: Diálogo
description: Descripción de los controles de cuadro de diálogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489195"
---
# <a name="dialog"></a>Diálogo

![Diálogo](../images/dialog/MRTK_UX_Dialog_Main.png)

Los controles de cuadro de diálogo son superposiciones de interfaz de usuario que proporcionan información contextual de la aplicación. A menudo solicitan algún tipo de acción por parte del usuario. Use los cuadros de diálogo para notificar a los usuarios información importante o para solicitar información adicional o confirmación para completar una acción.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos en la escena **DialogExample** en: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Cómo usar el control Dialog

MRTK proporciona tres prefabs de diálogo:

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

Use Dialog.Open() para abrir un cuadro de diálogo nuevo. Especifique el elemento prefab del cuadro de diálogo, el número de botones, el texto del título, el texto del mensaje, la distancia de colocación (cerca o lejos) y las variables adicionales. Dialog proporciona las opciones de diálogo "Confirmation(single button)" y "Choice(two-buttons)".

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Ejemplo de apertura de un cuadro de diálogo grande con un solo botón "Aceptar", colocado en un intervalo de interacción lejano (mirada, rayo de mano, controlador de movimiento)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>Ejemplo de apertura de un cuadro de diálogo pequeño que contiene un mensaje de elección para el usuario, colocado en un intervalo de interacción cercano (interacción directa con la mano)

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Para obtener más información, vea `DialogExampleController.cs` en DialogExample.unity scene (Escena de DialogExample.unity).
