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
# <a name="dictation"></a><span data-ttu-id="cb267-104">Dictado</span><span class="sxs-lookup"><span data-stu-id="cb267-104">Dictation</span></span>

<span data-ttu-id="cb267-105">El dictado permite a los usuarios grabar clips de audio y obtener una transcripción.</span><span class="sxs-lookup"><span data-stu-id="cb267-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="cb267-106">Para usarlo, asegúrese de que un sistema de dictado está registrado en el perfil *del sistema de entrada*.</span><span class="sxs-lookup"><span data-stu-id="cb267-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="cb267-107">**Windows de entrada de dictado** es el sistema de dictado proporcionado de forma estándar, pero se pueden crear sistemas de dictado alternativos que implementan [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .</span><span class="sxs-lookup"><span data-stu-id="cb267-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="cb267-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb267-108">Requirements</span></span>

<span data-ttu-id="cb267-109">El sistema de dictado usa [dictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) de Unity, que a su vez usa las API de voz Windows subyacentes para controlar el dictado.</span><span class="sxs-lookup"><span data-stu-id="cb267-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="cb267-110">Tenga en cuenta que esto implica que esta característica solo está presente en Windows plataformas basadas en aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="cb267-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="cb267-111">El uso del sistema de dictado requiere las funcionalidades de aplicación "Cliente de Internet" y "Micrófono" en la [sección PlayerSettings - Capabilities (PlayerSettings: funcionalidades).](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)</span><span class="sxs-lookup"><span data-stu-id="cb267-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="cb267-112">Consulte [Windows Mixed Reality documentación para](/windows/mixed-reality/voice-input-in-unity#dictation) obtener más detalles sobre la entrada de voz en Unity.</span><span class="sxs-lookup"><span data-stu-id="cb267-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="cb267-113">Configuración</span><span class="sxs-lookup"><span data-stu-id="cb267-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="cb267-114">Una vez configurado un servicio de dictado, puede usar el script para iniciar y detener la grabación de sesiones y obtener los resultados de la transcripción [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) a través de UnityEvents.</span><span class="sxs-lookup"><span data-stu-id="cb267-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="cb267-115">**La hipótesis de** dictado se genera a medida que el usuario habla con transcripciones tempranas y aproximadas del audio capturado hasta ahora.</span><span class="sxs-lookup"><span data-stu-id="cb267-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="cb267-116">**El resultado de dictado** se genera al final de cada frase (es decir, cuando el usuario se detiene) con la transcripción final del audio capturado hasta ahora.</span><span class="sxs-lookup"><span data-stu-id="cb267-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="cb267-117">**Dictation Complete se** genera al final de la sesión de grabación con la transcripción completa y final del audio.</span><span class="sxs-lookup"><span data-stu-id="cb267-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="cb267-118">**El error de** dictado se genera para informar de los errores en el servicio de dictado.</span><span class="sxs-lookup"><span data-stu-id="cb267-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="cb267-119">La transcripción en este caso contiene una descripción del error.</span><span class="sxs-lookup"><span data-stu-id="cb267-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="cb267-120">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="cb267-120">Example scene</span></span>

<span data-ttu-id="cb267-121">**La escena** de dictado `MRTK/Examples/Demos/Input/Scenes/Dictation` de muestra el script en `DictationHandler` uso.</span><span class="sxs-lookup"><span data-stu-id="cb267-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="cb267-122">Si necesita más control, puede extender este script o crear su propia implementación [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) para recibir eventos de dictado directamente.</span><span class="sxs-lookup"><span data-stu-id="cb267-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
