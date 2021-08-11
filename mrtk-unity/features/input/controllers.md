---
title: Controladores
description: Uso de controladores en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, controladores,
ms.openlocfilehash: bc6aea1abda85567ab1b0db2616b529a92b4165e9b9cbcbc4b8b3cecd8a34c9f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224778"
---
# <a name="controllers"></a>Controladores

Los proveedores de entrada crean y destruyen automáticamente los [**controladores.**](input-providers.md) Cada tipo de controlador tiene una serie de entradas físicas *definidas* por un tipo de eje *,* que nos dice el tipo de datos del valor de entrada (Digital, Eje único, Eje dual, Seis Dof, ...), y un tipo de entrada *(Button* Press, Trigger, Thumb Stick, Spatial Pointer, ...) que describe el origen de la entrada. Las entradas físicas se  asignan a acciones de entrada a  través de en el perfil de asignación de entrada del controlador **,** en el perfil del sistema de entrada en el Mixed Reality Toolkit de entrada.

![Asignación de entrada del controlador](../images/input/ControllerInputMapping.png)
