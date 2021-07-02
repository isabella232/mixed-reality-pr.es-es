---
title: Dictado
description: Docummentation on how to record audio clips and obtain a transcription in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176469"
---
# <a name="dictation"></a>Dictado

El dictado permite a los usuarios grabar clips de audio y obtener una transcripción. Para usarlo, asegúrese de que un sistema de dictado está registrado en el perfil *del sistema de entrada*. **Windows de entrada de dictado** es el sistema de dictado proporcionado de forma estándar, pero se pueden crear sistemas de dictado alternativos que implementan [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Requisitos

El sistema de dictado usa [dictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) de Unity, que a su vez usa las API de voz Windows subyacentes para controlar el dictado. Tenga en cuenta que esto implica que esta característica solo está presente en Windows plataformas basadas en aplicaciones.

El uso del sistema de dictado requiere las funcionalidades de aplicación "Cliente de Internet" y "Micrófono" en la [sección PlayerSettings - Capabilities (PlayerSettings: funcionalidades).](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)
Consulte [Windows Mixed Reality documentación para](/windows/mixed-reality/voice-input-in-unity#dictation) obtener más detalles sobre la entrada de voz en Unity.

## <a name="configuration"></a>Configuración

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Una vez configurado un servicio de dictado, puede usar el script para iniciar y detener la grabación de sesiones y obtener los resultados de la transcripción [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) a través de UnityEvents.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **La hipótesis de** dictado se genera a medida que el usuario habla con transcripciones tempranas y aproximadas del audio capturado hasta ahora.
- **El resultado de dictado** se genera al final de cada frase (es decir, cuando el usuario se detiene) con la transcripción final del audio capturado hasta ahora.
- **Dictation Complete se** genera al final de la sesión de grabación con la transcripción completa y final del audio.
- **El error de** dictado se genera para informar de los errores en el servicio de dictado. La transcripción en este caso contiene una descripción del error.

## <a name="example-scene"></a>Escena de ejemplo

**La escena** de dictado `MRTK/Examples/Demos/Input/Scenes/Dictation` de muestra el script en `DictationHandler` uso. Si necesita más control, puede extender este script o crear su propia implementación [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) para recibir eventos de dictado directamente.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
