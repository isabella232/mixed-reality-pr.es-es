---
title: Controladores
description: Uso de controladores en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, controladores,
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176919"
---
# <a name="controllers"></a><span data-ttu-id="06a7e-104">Controladores</span><span class="sxs-lookup"><span data-stu-id="06a7e-104">Controllers</span></span>

<span data-ttu-id="06a7e-105">Los proveedores de entrada crean y destruyen automáticamente los [**controladores.**](input-providers.md)</span><span class="sxs-lookup"><span data-stu-id="06a7e-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="06a7e-106">Cada tipo de controlador tiene una serie de entradas físicas *definidas* por un tipo de eje *,* que nos dice el tipo de datos del valor de entrada (Digital, Eje único, Eje dual, Six Dof, ...), y un tipo de entrada *(Button* Press, Trigger, Thumb Stick, Spatial Pointer, ...) que describe el origen de la entrada.</span><span class="sxs-lookup"><span data-stu-id="06a7e-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="06a7e-107">Las entradas físicas se  asignan a las acciones de entrada  a través de en el perfil de asignación de entrada del controlador **,** en el perfil del sistema de entrada del Mixed Reality Toolkit entrada.</span><span class="sxs-lookup"><span data-stu-id="06a7e-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

![Asignación de entrada del controlador](../images/input/ControllerInputMapping.png)
