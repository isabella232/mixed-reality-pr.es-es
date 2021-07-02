---
title: Barra de la aplicación
description: Información general sobre la barra de aplicaciones en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, barra de aplicaciones,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175698"
---
# <a name="app-bar"></a><span data-ttu-id="dbbc9-104">Barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="dbbc9-104">App bar</span></span>

![Barra de la aplicación](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="dbbc9-106">La barra de aplicaciones es un componente de interfaz de usuario que se usa junto con el script [de control de límites.](bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="dbbc9-106">App bar is a UI component that is used together with the [bounds control](bounds-control.md) script.</span></span> <span data-ttu-id="dbbc9-107">Agrega controles de botón a un objeto con la intención de manipularlo.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="dbbc9-108">Con el botón "Ajustar", la interfaz de control de límites de un objeto se puede desajuste o activar.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="dbbc9-109">El botón "Quitar" debe quitar el objeto de la escena.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="dbbc9-110">Uso de la barra de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="dbbc9-110">How to use app bar</span></span>

<span data-ttu-id="dbbc9-111">Arrastre y coloque `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) en la jerarquía de escena.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="dbbc9-112">En el panel inspector del componente, asigne cualquier objeto  con un control de límites como cuadro de límite de destino para agregarle la barra de aplicación.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="dbbc9-113">**Importante:** La opción de activación del control de límites para el objeto de destino debe ser "Activar manualmente".</span><span class="sxs-lookup"><span data-stu-id="dbbc9-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
