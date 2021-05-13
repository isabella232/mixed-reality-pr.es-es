---
title: Controladores
description: Uso de controladores en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, controladores,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850341"
---
# <a name="controllers"></a><span data-ttu-id="1cc5d-104">Controladores</span><span class="sxs-lookup"><span data-stu-id="1cc5d-104">Controllers</span></span>

<span data-ttu-id="1cc5d-105">Los proveedores de entrada crean y destruyen automáticamente los [**controladores.**](input-providers.md)</span><span class="sxs-lookup"><span data-stu-id="1cc5d-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="1cc5d-106">Cada tipo de controlador tiene una serie de entradas físicas *definidas* por un tipo de eje *,* que nos dice el tipo de datos del valor de entrada (Digital, Eje único, Eje dual, Six Dof, ...), y un tipo de entrada *(Button* Press, Trigger, Thumb Stick, Spatial Pointer, ...) que describe el origen de la entrada.</span><span class="sxs-lookup"><span data-stu-id="1cc5d-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="1cc5d-107">Las entradas físicas se  asignan a las acciones de entrada  a través de en el perfil de asignación de entrada del controlador **,** en el perfil del sistema de entrada del componente Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="1cc5d-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<span data-ttu-id="1cc5d-108">MRTK detectará automáticamente los controladores WMR y los mostrará cuando se instale el paquete [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="1cc5d-108">MRTK will automatically detect WMR controllers and display them when the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package is installed.</span></span> <span data-ttu-id="1cc5d-109">Los modelos de controladores solo se mostrarán en el editor cuando se use la canalización de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="1cc5d-109">Controllers models will only show up in the editor when using the OpenXR pipeline.</span></span> <span data-ttu-id="1cc5d-110">Para visualizar los modelos de controlador de Oculus, siga las instrucciones [de implementación de Oculus Raid.](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="1cc5d-110">To visualize Oculus controller models, follow the [Oculus Quest deployment instructions](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span></span>

![Asignación de entrada del controlador](../images/input/ControllerInputMapping.png)