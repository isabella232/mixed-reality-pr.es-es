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
# <a name="controllers"></a>Controladores

Los proveedores de entrada crean y destruyen automáticamente los [**controladores.**](input-providers.md) Cada tipo de controlador tiene una serie de entradas físicas *definidas* por un tipo de eje *,* que nos dice el tipo de datos del valor de entrada (Digital, Eje único, Eje dual, Six Dof, ...), y un tipo de entrada *(Button* Press, Trigger, Thumb Stick, Spatial Pointer, ...) que describe el origen de la entrada. Las entradas físicas se  asignan a las acciones de entrada  a través de en el perfil de asignación de entrada del controlador **,** en el perfil del sistema de entrada del componente Mixed Reality Toolkit.

MRTK detectará automáticamente los controladores WMR y los mostrará cuando se instale el paquete [**Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) Los modelos de controladores solo se mostrarán en el editor cuando se use la canalización de OpenXR. Para visualizar los modelos de controlador de Oculus, siga las instrucciones [de implementación de Oculus Raid.](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)

![Asignación de entrada del controlador](../images/input/ControllerInputMapping.png)