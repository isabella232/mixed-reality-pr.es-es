---
title: Entrada de voz en Unity
description: Obtenga información sobre cómo Unity expone tres maneras de agregar entrada de voz, reconocimiento de voz y dictado a la aplicación Windows Mixed Reality voz.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, micrófono, dictado, voz, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: e436c320a2f4393eeae86a7a936a6afa8e8a15f91ba803e95e6a318b117ee81c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216411"
---
# <a name="voice-input-in-unity"></a>Entrada de voz en Unity

> [!CAUTION]
> Antes de empezar, considere la posibilidad de usar el complemento unity para el SDK de Cognitive Speech Services. El complemento tiene mejores resultados de precisión de voz y un acceso sencillo a la descodificación de voz a texto, así como características avanzadas de voz como diálogo, interacción basada en intenciones, traducción, síntesis de texto a voz y reconocimiento de voz en lenguaje natural. Para empezar, consulte el ejemplo [y la documentación](/azure/cognitive-services/speech-service/quickstart-csharp-unity).

Unity expone tres maneras de agregar [entrada](../../design/voice-input.md) de voz a la aplicación de Unity, las dos primeras de las cuales son tipos de PhraseRecognizer:
* proporciona `KeywordRecognizer` a la aplicación una matriz de comandos de cadena para escuchar.
* proporciona `GrammarRecognizer` a la aplicación un archivo SRGS que define una gramática específica para escuchar.
* permite que la aplicación escuche cualquier palabra y proporcione al usuario una nota u `DictationRecognizer` otra presentación de su voz.

> [!NOTE]
> El dictado y el reconocimiento de frases no se pueden controlar al mismo tiempo. Si GrammarRecognizer o KeywordRecognizer están activos, un dictationRecognizer no puede estar activo y viceversa.

## <a name="enabling-the-capability-for-voice"></a>Habilitación de la funcionalidad de Voz

La **funcionalidad** Micrófono debe declararse para que una aplicación use la entrada de voz.
1. En el Editor de Unity, vaya **a Editar > Project Configuración > Player.**
2. Seleccione la **pestaña Windows Store (Tienda de** aplicaciones).
3. En la **sección Publishing Configuración > Capabilities (Funcionalidades de Configuración > publicación),** compruebe la **funcionalidad Microphone** (Micrófono).
4. Concesión de permisos a la aplicación para el acceso al micrófono en HoloLens dispositivo
    * Se le pedirá que haga esto al iniciar el dispositivo, pero si ha hecho clic accidentalmente en "no", puede cambiar los permisos en la configuración del dispositivo.

## <a name="phrase-recognition"></a>Reconocimiento de frases

Para permitir que la aplicación escuche frases específicas habladas por el usuario, debe hacer lo siguiente:
1. Especificación de las frases que se escucharán mediante `KeywordRecognizer` o `GrammarRecognizer`
2. Controlar el `OnPhraseRecognized` evento y tomar medidas correspondientes a la frase reconocida

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Espacio de nombres:** *UnityEngine.Windows. Voz*<br>
**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Necesitamos algunas instrucciones using para guardar algunas pulsaciones de tecla:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

A continuación, vamos a agregar algunos campos a la clase para almacenar el reconocedor y el diccionario de >de palabras clave:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Ahora agregue una palabra clave al diccionario, por ejemplo en de un `Start()` método . Vamos a agregar la palabra clave "activate" en este ejemplo:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Cree el reconocedor de palabras clave e indórmele lo que queremos reconocer:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Regístrese ahora para el `OnPhraseRecognized` evento.

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Un controlador de ejemplo es:

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

Por último, empiece a reconocer.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Espacio de nombres:** *UnityEngine.Windows. Voz*<br>
**Tipos:** *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

GrammarRecognizer se usa si especifica la gramática de reconocimiento mediante SRGS. Esto puede ser útil si la aplicación tiene más de unas pocas palabras clave, si desea reconocer frases más complejas o si desea activar y desactivar fácilmente conjuntos de comandos. Vea: [Crear gramáticas mediante XML de SRGS para](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) obtener información sobre el formato de archivo.

Una vez que tenga la gramática de SRGS y esté en el proyecto en una [carpeta StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Cree un `GrammarRecognizer` y pase la ruta de acceso al archivo SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Regístrese ahora para el `OnPhraseRecognized` evento.

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Se obtiene una devolución de llamada que contiene información especificada en la gramática de SRGS, que puede controlar adecuadamente. La mayor parte de la información importante se proporciona en la `semanticMeanings` matriz.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Por último, empiece a reconocer.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Dictado

**Espacio de nombres:** *UnityEngine.Windows. Voz*<br>
**Tipos:** *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Use para `DictationRecognizer` convertir la voz del usuario en texto. DictationRecognizer expone la funcionalidad de dictado y admite el registro y la escucha de eventos [completados](../../design/voice-input.md#dictation) de hipótesis y frases, por lo que puede enviar comentarios al usuario mientras habla y después. `Start()` Los `Stop()` métodos y habilitan y deshabilitan respectivamente el reconocimiento de dictado. Una vez hecho con el reconocedor, se debe eliminar mediante `Dispose()` para liberar los recursos que usa. Liberará estos recursos automáticamente durante la recolección de elementos no utilizados con un costo de rendimiento adicional si no se liberan antes.

Solo hay unos pocos pasos necesarios para empezar a usar el dictado:
1. Creación de un nuevo `DictationRecognizer`
2. Controlar eventos de dictado
3. Iniciar dictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Habilitación de la funcionalidad de dictado

Las **funcionalidades Cliente** **de** Internet y Micrófono deben declararse para que una aplicación use el dictado:
1. En el Editor de Unity, vaya **a Editar > Project Configuración > Player.**
2. Seleccione en la **pestaña Windows Store (Tienda** de aplicaciones).
3. En la **sección Funcionalidades Configuración > publicación,** compruebe la **funcionalidad InternetClient.**
    * Opcionalmente, si no ha habilitado el micrófono, compruebe la **funcionalidad Micrófono.**
4. Conceda permisos a la aplicación para el acceso al micrófono en HoloLens dispositivo si aún no lo ha hecho.
    * Se le pedirá que haga esto al iniciar el dispositivo, pero si ha hecho clic accidentalmente en "no", puede cambiar los permisos en la configuración del dispositivo.

### <a name="dictationrecognizer"></a>DictationRecognizer

Cree un dictadoRecognizer de la siguiente manera:

```
dictationRecognizer = new DictationRecognizer();
```

Hay cuatro eventos de dictado a los que se puede suscribir y controlar para implementar el comportamiento de dictado.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

Este evento se desencadena después de que el usuario se detenga, normalmente al final de una frase. Aquí se devuelve la cadena reconocida completa.

En primer lugar, suscríbase al `DictationResult` evento:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

A continuación, controle la devolución de llamada DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Este evento se desencadena continuamente mientras el usuario está hablando. A medida que el reconocedor escucha, proporciona texto de lo que se ha oído hasta ahora.

En primer lugar, suscríbase al `DictationHypothesis` evento:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

A continuación, controle la devolución de llamada DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Este evento se desencadena cuando el reconocedor se detiene, ya sea desde stop() al que se llama, se produce un tiempo de espera o algún otro error.

En primer lugar, suscríbase al `DictationComplete` evento:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

A continuación, controle la devolución de llamada DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Este evento se desencadena cuando se produce un error.

En primer lugar, suscríbase al `DictationError` evento:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

A continuación, controle la devolución de llamada DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Una vez que se haya suscrito y controlado los eventos de dictado que le importan, inicie el reconocedor de dictado para empezar a recibir eventos.

```
dictationRecognizer.Start();
```

Si ya no quiere mantener el dictadoRecognizer, debe cancelar la suscripción a los eventos y eliminar el dictadoRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Sugerencias**
* `Start()` Los `Stop()` métodos y habilitan y deshabilitan respectivamente el reconocimiento de dictado.
* Una vez hecho con el reconocedor, se debe eliminar mediante `Dispose()` para liberar los recursos que usa. Liberará estos recursos automáticamente durante la recolección de elementos no utilizados con un costo de rendimiento adicional si no se liberan antes.
* Los tiempos de espera se producen después de un período de tiempo establecido. Puede comprobar si hay estos tiempos de espera en el `DictationComplete` evento. Hay dos tiempos de espera que se deben tener en cuenta:
   1. Si el reconocedor se inicia y no escucha ningún audio durante los primeros cinco segundos, se pasará el tiempo de espera.
   2. Si el reconocedor ha dado un resultado, pero después escucha el silencio durante 20 segundos, se pasará el tiempo de espera.

## <a name="using-both-phrase-recognition-and-dictation"></a>Usar tanto el reconocimiento de frases como el dictado

Si quiere usar el reconocimiento de frases y el dictado en la aplicación, deberá apagar completamente una para poder iniciar la otra. Si tiene varios keywordrecognizers en ejecución, puede apagarlos todos a la vez con:

```
PhraseRecognitionSystem.Shutdown();
```

Puede llamar a `Restart()` para restaurar todos los reconocedores a su estado anterior después de que se haya detenido dictationRecognizer:

```
PhraseRecognitionSystem.Restart();
```

También puede iniciar una palabra claveRecognizer, que también reiniciará PhraseRecognitionSystem.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrada de voz en Mixed Reality Toolkit

Puede encontrar ejemplos de MRTK para la entrada de voz en las siguientes escenas de demostración:
* [Dictado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Voz](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido del punto de control de desarrollo de Unity que hemos diseñado, la siguiente tarea consiste en explorar las funcionalidades y API de Mixed Reality plataforma:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.