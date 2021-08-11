---
title: Información general sobre acciones del usuario
description: Información general del sistema de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: b175b16e2004fb00cef430335751c3aabc8c59fdd4ae78a2fc78c959a92240fb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219770"
---
# <a name="input-overview"></a>Introducción a la entrada

El sistema de entrada de MRTK le permite:

- Consumir entradas de una variedad de orígenes de entrada, como 6 controladores DOF, manos o voz articuladas, a través de eventos de entrada.
- Defina acciones abstractas, *como Seleccionar* *o Menú,* y asócialas a distintas entradas.
- Configurar punteros asociados a controladores para impulsar los componentes de la interfaz de usuario a través de eventos de foco y puntero.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Información general del sistema de entrada de MRTK</sup>

Las entradas las generan los proveedores de datos [**de entrada (Administrador de dispositivos).**](input-providers.md) Cada proveedor corresponde a un origen de entrada determinado: Open VR, Windows Mixed Reality (WMR), Unity Unity Unity, Windows Speech, etc. Los proveedores se agregan al  proyecto a través del perfil de [](input-events.md) proveedores de servicios registrados en el componente *Mixed Reality Toolkit* y generan eventos de entrada automáticamente cuando están disponibles los orígenes de entrada correspondientes (por ejemplo, cuando se detecta un controlador WMR o se conecta un controlador de juego).

[**Las acciones de**](input-actions.md) entrada son abstracciones sobre entradas sin procesar diseñadas para ayudar a aislar la lógica de la aplicación de los orígenes de entrada específicos que producen una entrada. Puede ser útil, por ejemplo,  definir una acción Seleccionar y asignarla al botón izquierdo del mouse, un botón en un controlador de juegos y un desencadenador en un controlador de 6 DOF. A continuación, puede hacer que la lógica de la aplicación escuche los eventos select *input* action en lugar de tener que tener en cuenta todas las distintas entradas que pueden producirla. Las acciones de entrada se definen en el perfil **de acciones de entrada**, que se encuentra en el perfil del sistema de entrada del *Mixed Reality Toolkit* entrada. 

[**Los**](controllers.md) proveedores de entrada crean *controladores cuando* se detectan y destruyen dispositivos de entrada cuando se pierden o se desconectan. Por ejemplo, el proveedor de entrada WMR creará controladores *WMR* para 6 dispositivos DOF y controladores de mano articulados *WMR* para las manos articuladas. Las entradas del controlador se pueden asignar a las acciones de entrada a través del perfil de asignación **de controlador**, dentro del perfil del sistema *de entrada*. Los eventos de entrada producidos por los controladores incluirán la acción de entrada asociada, si la hubiera.

Los controladores pueden tener [**asociados punteros**](pointers.md) que consultan la escena para determinar el objeto de juego con el foco y generar eventos [**de puntero**](pointers.md#pointer-event-interfaces) en él. Por ejemplo, nuestro puntero *de* línea realiza un raycast en la escena mediante la posición del controlador para calcular el origen y la dirección del rayo. Los punteros creados para cada controlador se establecen en el perfil de **puntero**, en el perfil *del sistema de entrada*.

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Flujo de eventos.</sup>

Aunque puede controlar los eventos [de entrada directamente](input-events.md)en los componentes de la interfaz de usuario, se recomienda usar eventos de [puntero](pointers.md#pointer-event-interfaces) para mantener la implementación independiente del dispositivo.

MRTK también proporciona varios métodos prácticos para consultar el estado de entrada directamente de forma independiente del dispositivo. Consulte [Acceso al estado de entrada en MRTK](input-state.md) para obtener más detalles.
