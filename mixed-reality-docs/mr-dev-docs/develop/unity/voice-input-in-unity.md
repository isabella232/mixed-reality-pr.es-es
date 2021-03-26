---
title: Entrada de voz en Unity
description: Obtenga información sobre cómo Unity expone tres maneras de agregar entrada de voz, reconocimiento de voz y dictado a su aplicación Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, micrófono, dictado, voz, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: c062289a1a26365528a86761b6b68a9a24041f7c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550385"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="954df-104">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="954df-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="954df-105">Antes de comenzar, considere la posibilidad de usar el complemento Unity para el SDK de servicios de voz cognitivo.</span><span class="sxs-lookup"><span data-stu-id="954df-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="954df-106">El complemento tiene mejores resultados de precisión de voz y acceso sencillo a la descodificación de voz a texto, así como características avanzadas de voz como cuadro de diálogo, interacción basada en intención, traducción, síntesis de texto a voz y reconocimiento de voz en lenguaje natural.</span><span class="sxs-lookup"><span data-stu-id="954df-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="954df-107">Para empezar, consulte la [documentación y el ejemplo](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span><span class="sxs-lookup"><span data-stu-id="954df-107">To get started, check out the [sample and documentation](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="954df-108">Unity expone tres maneras de agregar una [entrada de voz](../../design/voice-input.md) a la aplicación de Unity, los dos primeros son tipos de PhraseRecognizer:</span><span class="sxs-lookup"><span data-stu-id="954df-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="954df-109">`KeywordRecognizer`Proporciona la aplicación con una matriz de comandos de cadena para realizar escuchas.</span><span class="sxs-lookup"><span data-stu-id="954df-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="954df-110">`GrammarRecognizer`Proporciona a la aplicación un archivo SRGS que define una gramática específica para escuchar</span><span class="sxs-lookup"><span data-stu-id="954df-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="954df-111">`DictationRecognizer`Permite que la aplicación escuche cualquier palabra y proporcione al usuario una nota u otra presentación de la voz.</span><span class="sxs-lookup"><span data-stu-id="954df-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="954df-112">No se puede controlar el reconocimiento de dictado y frase al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="954df-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="954df-113">Si GrammarRecognizer o KeywordRecognizer está activo, un DictationRecognizer no puede estar activo y viceversa.</span><span class="sxs-lookup"><span data-stu-id="954df-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="954df-114">Habilitación de la funcionalidad de Voice</span><span class="sxs-lookup"><span data-stu-id="954df-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="954df-115">La capacidad del **micrófono** se debe declarar para que una aplicación use la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="954df-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="954df-116">En el editor de Unity, vaya a **editar > configuración del proyecto > Player** .</span><span class="sxs-lookup"><span data-stu-id="954df-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="954df-117">Seleccione la pestaña de la **tienda Windows**</span><span class="sxs-lookup"><span data-stu-id="954df-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="954df-118">En la sección **funciones de configuración de publicación >** , Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="954df-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="954df-119">Concesión de permisos a la aplicación para el acceso al micrófono en el dispositivo HoloLens</span><span class="sxs-lookup"><span data-stu-id="954df-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="954df-120">Se le pedirá que lo haga en el inicio del dispositivo, pero si hizo clic accidentalmente en "no", puede cambiar los permisos en la configuración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="954df-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="954df-121">Reconocimiento de frases</span><span class="sxs-lookup"><span data-stu-id="954df-121">Phrase Recognition</span></span>

<span data-ttu-id="954df-122">Para permitir que la aplicación escuche frases específicas que habla el usuario, realice alguna acción; debe:</span><span class="sxs-lookup"><span data-stu-id="954df-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="954df-123">Especificar las frases que se van a escuchar con `KeywordRecognizer` o `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="954df-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="954df-124">Controlar el `OnPhraseRecognized` evento y tomar las medidas correspondientes a la frase reconocida</span><span class="sxs-lookup"><span data-stu-id="954df-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="954df-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="954df-125">KeywordRecognizer</span></span>

<span data-ttu-id="954df-126">**Espacio de nombres:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="954df-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="954df-127">**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="954df-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="954df-128">Necesitamos algunas instrucciones Using para guardar algunas pulsaciones de teclas:</span><span class="sxs-lookup"><span data-stu-id="954df-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="954df-129">A continuación, vamos a agregar algunos campos a la clase para almacenar el reconocedor y la palabra clave >Diccionario de acciones:</span><span class="sxs-lookup"><span data-stu-id="954df-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="954df-130">Ahora, agregue una palabra clave al diccionario, por ejemplo, en de un `Start()` método.</span><span class="sxs-lookup"><span data-stu-id="954df-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="954df-131">Estamos agregando la palabra clave "activar" en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="954df-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="954df-132">Cree el reconocedor de palabras clave e indíquele lo que desea reconocer:</span><span class="sxs-lookup"><span data-stu-id="954df-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="954df-133">Regístrese ahora para el `OnPhraseRecognized` evento</span><span class="sxs-lookup"><span data-stu-id="954df-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="954df-134">Un controlador de ejemplo es:</span><span class="sxs-lookup"><span data-stu-id="954df-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="954df-135">Por último, empiece a reconocer.</span><span class="sxs-lookup"><span data-stu-id="954df-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="954df-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="954df-136">GrammarRecognizer</span></span>

<span data-ttu-id="954df-137">**Espacio de nombres:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="954df-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="954df-138">**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="954df-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="954df-139">El GrammarRecognizer se usa si se especifica la gramática de reconocimiento mediante SRGS.</span><span class="sxs-lookup"><span data-stu-id="954df-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="954df-140">Esto puede ser útil si la aplicación tiene más de unas pocas palabras clave, si desea reconocer frases más complejas o si desea activar o desactivar fácilmente conjuntos de comandos.</span><span class="sxs-lookup"><span data-stu-id="954df-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="954df-141">Vea: [crear gramáticas con XML de SRGS](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) para obtener información sobre el formato de archivo.</span><span class="sxs-lookup"><span data-stu-id="954df-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="954df-142">Una vez que tenga la gramática de SRGS y esté en el proyecto en una [carpeta StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="954df-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="954df-143">Cree un `GrammarRecognizer` y pásele la ruta de acceso al archivo SRGS:</span><span class="sxs-lookup"><span data-stu-id="954df-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="954df-144">Regístrese ahora para el `OnPhraseRecognized` evento</span><span class="sxs-lookup"><span data-stu-id="954df-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="954df-145">Obtendrá una devolución de llamada que contiene la información especificada en la gramática de SRGS, que puede controlar de forma adecuada.</span><span class="sxs-lookup"><span data-stu-id="954df-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="954df-146">La mayoría de la información importante se proporcionará en la `semanticMeanings` matriz.</span><span class="sxs-lookup"><span data-stu-id="954df-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="954df-147">Por último, empiece a reconocer.</span><span class="sxs-lookup"><span data-stu-id="954df-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="954df-148">Dictado</span><span class="sxs-lookup"><span data-stu-id="954df-148">Dictation</span></span>

<span data-ttu-id="954df-149">**Espacio de nombres:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="954df-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="954df-150">**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="954df-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="954df-151">Use `DictationRecognizer` para convertir la voz del usuario en texto.</span><span class="sxs-lookup"><span data-stu-id="954df-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="954df-152">DictationRecognizer expone la funcionalidad de [dictado](../../design/voice-input.md#dictation) y admite el registro y la escucha de eventos de hipótesis y frases completadas, de forma que puede enviar comentarios al usuario mientras hablan y después.</span><span class="sxs-lookup"><span data-stu-id="954df-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="954df-153">`Start()``Stop()`los métodos y, respectivamente, habilitan y deshabilitan el reconocimiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="954df-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="954df-154">Una vez que se ha realizado con el reconocedor, se debe eliminar usando `Dispose()` para liberar los recursos que utiliza.</span><span class="sxs-lookup"><span data-stu-id="954df-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="954df-155">Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se liberan antes.</span><span class="sxs-lookup"><span data-stu-id="954df-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="954df-156">Solo se necesitan algunos pasos para empezar a trabajar con el dictado:</span><span class="sxs-lookup"><span data-stu-id="954df-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="954df-157">Crear un nuevo `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="954df-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="954df-158">Controlar los eventos de dictado</span><span class="sxs-lookup"><span data-stu-id="954df-158">Handle Dictation events</span></span>
3. <span data-ttu-id="954df-159">Inicio de DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="954df-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="954df-160">Habilitar la funcionalidad para el dictado</span><span class="sxs-lookup"><span data-stu-id="954df-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="954df-161">Las capacidades de cliente y **micrófono** de **Internet** se deben declarar para que una aplicación use dictado:</span><span class="sxs-lookup"><span data-stu-id="954df-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="954df-162">En el editor de Unity, vaya a **editar > configuración del proyecto > Player** .</span><span class="sxs-lookup"><span data-stu-id="954df-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="954df-163">Seleccionar en la pestaña de la **tienda Windows**</span><span class="sxs-lookup"><span data-stu-id="954df-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="954df-164">En la sección **capacidades de publicación de configuración de >** , Compruebe la funcionalidad de **InternetClient** .</span><span class="sxs-lookup"><span data-stu-id="954df-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="954df-165">Opcionalmente, si aún no ha habilitado el micrófono, Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="954df-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="954df-166">Conceda permisos a la aplicación para acceder al micrófono en el dispositivo HoloLens, si no lo ha hecho ya</span><span class="sxs-lookup"><span data-stu-id="954df-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="954df-167">Se le pedirá que lo haga en el inicio del dispositivo, pero si hizo clic accidentalmente en "no", puede cambiar los permisos en la configuración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="954df-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="954df-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="954df-168">DictationRecognizer</span></span>

<span data-ttu-id="954df-169">Cree un DictationRecognizer como el siguiente:</span><span class="sxs-lookup"><span data-stu-id="954df-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="954df-170">Hay cuatro eventos de dictado a los que se puede suscribir y controlar para implementar el comportamiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="954df-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="954df-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="954df-171">**DictationResult**</span></span>

<span data-ttu-id="954df-172">Este evento se desencadena después de que el usuario se pausa, normalmente al final de una frase.</span><span class="sxs-lookup"><span data-stu-id="954df-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="954df-173">Aquí se devuelve la cadena completa reconocida.</span><span class="sxs-lookup"><span data-stu-id="954df-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="954df-174">En primer lugar, suscríbase al `DictationResult` evento:</span><span class="sxs-lookup"><span data-stu-id="954df-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="954df-175">A continuación, controle la devolución de llamada DictationResult:</span><span class="sxs-lookup"><span data-stu-id="954df-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="954df-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="954df-176">**DictationHypothesis**</span></span>

<span data-ttu-id="954df-177">Este evento se desencadena continuamente mientras el usuario está hablando.</span><span class="sxs-lookup"><span data-stu-id="954df-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="954df-178">A medida que el reconocedor realiza escuchas, proporciona texto de lo que se oye hasta ahora.</span><span class="sxs-lookup"><span data-stu-id="954df-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="954df-179">En primer lugar, suscríbase al `DictationHypothesis` evento:</span><span class="sxs-lookup"><span data-stu-id="954df-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="954df-180">A continuación, controle la devolución de llamada DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="954df-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="954df-181">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="954df-181">**DictationComplete**</span></span>

<span data-ttu-id="954df-182">Este evento se desencadena cuando se detiene el reconocedor, ya sea de detención (), se ha producido un tiempo de espera o de algún otro error.</span><span class="sxs-lookup"><span data-stu-id="954df-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="954df-183">En primer lugar, suscríbase al `DictationComplete` evento:</span><span class="sxs-lookup"><span data-stu-id="954df-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="954df-184">A continuación, controle la devolución de llamada DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="954df-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="954df-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="954df-185">**DictationError**</span></span>

<span data-ttu-id="954df-186">Este evento se desencadena cuando se produce un error.</span><span class="sxs-lookup"><span data-stu-id="954df-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="954df-187">En primer lugar, suscríbase al `DictationError` evento:</span><span class="sxs-lookup"><span data-stu-id="954df-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="954df-188">A continuación, controle la devolución de llamada DictationError:</span><span class="sxs-lookup"><span data-stu-id="954df-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="954df-189">Una vez que haya suscrito y controlado los eventos de dictado que le interesan, inicie el reconocedor de dictado para comenzar a recibir eventos.</span><span class="sxs-lookup"><span data-stu-id="954df-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="954df-190">Si ya no desea mantener el DictationRecognizer en torno, debe cancelar la suscripción a los eventos y eliminar el DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="954df-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="954df-191">**Sugerencias**</span><span class="sxs-lookup"><span data-stu-id="954df-191">**Tips**</span></span>
* <span data-ttu-id="954df-192">`Start()``Stop()`los métodos y, respectivamente, habilitan y deshabilitan el reconocimiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="954df-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="954df-193">Una vez que se realiza con el reconocedor, se debe desechar usando `Dispose()` para liberar los recursos que utiliza.</span><span class="sxs-lookup"><span data-stu-id="954df-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="954df-194">Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se liberan antes.</span><span class="sxs-lookup"><span data-stu-id="954df-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="954df-195">Los tiempos de espera se producen después de un período de tiempo establecido.</span><span class="sxs-lookup"><span data-stu-id="954df-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="954df-196">Puede buscar estos tiempos de espera en el `DictationComplete` evento.</span><span class="sxs-lookup"><span data-stu-id="954df-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="954df-197">Hay dos tiempos de espera que se deben tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="954df-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="954df-198">Si el reconocedor se inicia y no oye ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="954df-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="954df-199">Si el reconocedor ha dado un resultado, pero oye el silencio durante 20 segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="954df-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="954df-200">Usar el reconocimiento de frases y el dictado</span><span class="sxs-lookup"><span data-stu-id="954df-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="954df-201">Si desea usar tanto el reconocimiento de frases como el dictado en la aplicación, deberá apagarlo completamente antes de poder iniciar el otro.</span><span class="sxs-lookup"><span data-stu-id="954df-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="954df-202">Si tiene varios KeywordRecognizers en ejecución, puede cerrarlos todos a la vez con:</span><span class="sxs-lookup"><span data-stu-id="954df-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="954df-203">Puede llamar `Restart()` a para restaurar todos los reconocedores a su estado anterior después de que DictationRecognizer se haya detenido:</span><span class="sxs-lookup"><span data-stu-id="954df-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="954df-204">También puede iniciar una KeywordRecognizer, lo que reiniciará el PhraseRecognitionSystem también.</span><span class="sxs-lookup"><span data-stu-id="954df-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="954df-205">Entrada de voz en el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="954df-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="954df-206">Puede encontrar ejemplos de MRTK para la entrada de voz en las siguientes escenas de demostración:</span><span class="sxs-lookup"><span data-stu-id="954df-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="954df-207">Dictado</span><span class="sxs-lookup"><span data-stu-id="954df-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="954df-208">Voz</span><span class="sxs-lookup"><span data-stu-id="954df-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="954df-209">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="954df-209">Next Development Checkpoint</span></span>

<span data-ttu-id="954df-210">Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, la tarea siguiente está explorando las funcionalidades y API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="954df-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="954df-211">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="954df-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="954df-212">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="954df-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>