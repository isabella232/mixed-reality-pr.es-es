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
# <a name="dialog"></a><span data-ttu-id="98ce9-104">Diálogo</span><span class="sxs-lookup"><span data-stu-id="98ce9-104">Dialog</span></span>

![Diálogo](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="98ce9-106">Los controles de cuadro de diálogo son superposiciones de interfaz de usuario que proporcionan información contextual de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="98ce9-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="98ce9-107">A menudo solicitan algún tipo de acción por parte del usuario.</span><span class="sxs-lookup"><span data-stu-id="98ce9-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="98ce9-108">Use los cuadros de diálogo para notificar a los usuarios información importante o para solicitar información adicional o confirmación para completar una acción.</span><span class="sxs-lookup"><span data-stu-id="98ce9-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="98ce9-109">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="98ce9-109">Example scene</span></span>

<span data-ttu-id="98ce9-110">Puede encontrar ejemplos en la escena **DialogExample** en: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span><span class="sxs-lookup"><span data-stu-id="98ce9-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="98ce9-111">Cómo usar el control Dialog</span><span class="sxs-lookup"><span data-stu-id="98ce9-111">How to use Dialog control</span></span>

<span data-ttu-id="98ce9-112">MRTK proporciona tres prefabs de diálogo:</span><span class="sxs-lookup"><span data-stu-id="98ce9-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="98ce9-113">DialogSmall_192x96.prefab</span><span class="sxs-lookup"><span data-stu-id="98ce9-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="98ce9-114">DialogMedium_192x128.prefab</span><span class="sxs-lookup"><span data-stu-id="98ce9-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="98ce9-115">DialogLarge_192x192.prefab</span><span class="sxs-lookup"><span data-stu-id="98ce9-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="98ce9-116">Use Dialog.Open() para abrir un cuadro de diálogo nuevo.</span><span class="sxs-lookup"><span data-stu-id="98ce9-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="98ce9-117">Especifique el elemento prefab del cuadro de diálogo, el número de botones, el texto del título, el texto del mensaje, la distancia de colocación (cerca o lejos) y las variables adicionales.</span><span class="sxs-lookup"><span data-stu-id="98ce9-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="98ce9-118">Dialog proporciona las opciones de diálogo "Confirmation(single button)" y "Choice(two-buttons)".</span><span class="sxs-lookup"><span data-stu-id="98ce9-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="98ce9-119">Ejemplo de apertura de un cuadro de diálogo grande con un solo botón "Aceptar", colocado en un intervalo de interacción lejano (mirada, rayo de mano, controlador de movimiento)</span><span class="sxs-lookup"><span data-stu-id="98ce9-119">Example of opening a Large dialog with a single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="98ce9-120">Ejemplo de apertura de un cuadro de diálogo pequeño que contiene un mensaje de elección para el usuario, colocado en un intervalo de interacción cercano (interacción directa con la mano)</span><span class="sxs-lookup"><span data-stu-id="98ce9-120">Example of opening a Small dialog containing a choice message for the user, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="98ce9-121">Para obtener más información, vea `DialogExampleController.cs` en DialogExample.unity scene (Escena de DialogExample.unity).</span><span class="sxs-lookup"><span data-stu-id="98ce9-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>
