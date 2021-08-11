---
title: Voz
description: configuración de la entrada de voz en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Voz,
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228420"
---
# <a name="speech"></a>Voz

![Menú Cerca](../images/input/MRTK_Input_Speech.png)

Los proveedores de entrada de voz, como *Windows entrada* de voz, no crean ningún controlador, sino que permiten definir palabras clave que generarán eventos de entrada de voz cuando se reconozcan. El **perfil de comandos de voz** del perfil del sistema de *entrada* es donde se configuran las palabras clave que se reconocerán. Para cada comando también puede:

- Seleccione una **acción de entrada a** la que asignarla. De este modo, por ejemplo, puede usar la palabra clave *Select* para tener el mismo efecto que un clic izquierdo del mouse, asignando ambos a la misma acción.
- Especifique un **código de clave** que producirá el mismo evento de voz cuando se presione.
- Agregue una **clave de localización** que se usará en las aplicaciones para UWP para obtener la palabra clave localizada de los recursos de la aplicación.

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>Control de la entrada de voz

El [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script se puede agregar a un GameObject para controlar los comandos de voz mediante [**UnityEvents.**](https://docs.unity3d.com/Manual/UnityEvents.html) Muestra automáticamente la lista de las palabras clave definidas del perfil **de comandos de voz**.

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

Asigne **speechConfirmationTooltip.prefab opcional** para mostrar la etiqueta de información sobre herramientas de confirmación animada en el reconocimiento.

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

Como alternativa, los desarrolladores pueden implementar la [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interfaz en un componente de script personalizado para controlar los eventos de entrada de [voz.](input-events.md#input-event-interface-example)

## <a name="example-scene"></a>Escena de ejemplo

La **escena SpeechInputExample,** en `MRTK/Examples/Demos/Input/Scenes/Speech` , muestra cómo usar voz. También puede escuchar eventos de comandos de voz directamente en su propio script implementando (consulte la [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) tabla de controladores de [eventos](input-events.md)).

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
