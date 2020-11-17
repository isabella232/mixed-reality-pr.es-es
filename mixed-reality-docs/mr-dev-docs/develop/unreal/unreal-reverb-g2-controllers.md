---
title: Controladores de HP reverberación G2 en la realidad
description: Instrucciones sobre el uso de los controladores de HP reverberación G2 en OpenXR y SteamVR
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, nonreal Engine 4, UE4, reverberation, reverberación G2, HP reverberación G2, realidad mixta, desarrollo, controladores de movimiento, entrada de usuario, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 6a56b11e6738dd6359508d0cdfc1560bddfaff2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678934"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="45886-104">Controladores de HP reverberación G2 en la realidad</span><span class="sxs-lookup"><span data-stu-id="45886-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="45886-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="45886-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45886-106">Se necesita el motor 4,26 y OpenXR o SteamVR inreal para tener acceso al complemento de controlador de movimiento de HP. tendrá que trabajar con los controladores de la reverberación de HP G2.</span><span class="sxs-lookup"><span data-stu-id="45886-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="45886-107">Portabilidad de una aplicación existente de OpenXR</span><span class="sxs-lookup"><span data-stu-id="45886-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="45886-108">Si no existe ningún enlace de controlador en el juego para el controlador de la realidad de HP Mixed, el tiempo de ejecución de OpenXR intentará reasignar los enlaces existentes al controlador activo.</span><span class="sxs-lookup"><span data-stu-id="45886-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="45886-109">En este caso, el juego tiene enlaces de toque Oculus y ningún enlace de controlador de realidad de HP Mixed.</span><span class="sxs-lookup"><span data-stu-id="45886-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![Volver a asignar los enlaces existentes cuando no existe ningún enlace de controlador](images/reverb-g2-img-04.png)

<span data-ttu-id="45886-111">Los eventos se seguirán activando, pero si el juego necesita hacer uso de enlaces específicos del controlador, como el botón derecho del menú, se debe usar el perfil de interacción de la realidad de HP Mixed.</span><span class="sxs-lookup"><span data-stu-id="45886-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="45886-112">Se pueden especificar varios enlaces de controlador por acción para admitir mejor los distintos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="45886-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![Usar varios enlaces de controlador](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="45886-114">Agregar asignaciones de acción de entrada</span><span class="sxs-lookup"><span data-stu-id="45886-114">Adding input action mappings</span></span> 

<span data-ttu-id="45886-115">Definir una nueva acción y asignarla a una de las pulsaciones de teclas de la sección controlador HP Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="45886-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![Definir nuevas acciones y asignaciones](images/reverb-g2-img-02.png)

<span data-ttu-id="45886-117">El controlador de HP reverberación G2 también tiene un control analógico, que se puede usar en las asignaciones de eje con el enlace "apriete de eje".</span><span class="sxs-lookup"><span data-stu-id="45886-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="45886-118">Hay un enlace de ajuste independiente que se debe usar para las asignaciones de acciones cuando el botón de control se presiona por completo.</span><span class="sxs-lookup"><span data-stu-id="45886-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![Usar los enlaces de eje de apriete](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="45886-120">Agregar eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="45886-120">Adding input events</span></span>

<span data-ttu-id="45886-121">Haga clic con el botón derecho en un plano y busque los nuevos nombres de acción del sistema de entrada para agregar eventos para estas acciones.</span><span class="sxs-lookup"><span data-stu-id="45886-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="45886-122">Aquí el Blueprint responde a los eventos con una cadena de impresión que genera el estado actual del eje y el botón.</span><span class="sxs-lookup"><span data-stu-id="45886-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![Blueprint responder a eventos y salida del botón actual y el estado del eje](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="45886-124">Usar entrada</span><span class="sxs-lookup"><span data-stu-id="45886-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="45886-125">Consulte también</span><span class="sxs-lookup"><span data-stu-id="45886-125">See also</span></span>
* [<span data-ttu-id="45886-126">Entrada SteamVR</span><span class="sxs-lookup"><span data-stu-id="45886-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="45886-127">Uso de SteamVR con Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="45886-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="45886-128">Cámara del reproductor inreal</span><span class="sxs-lookup"><span data-stu-id="45886-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)