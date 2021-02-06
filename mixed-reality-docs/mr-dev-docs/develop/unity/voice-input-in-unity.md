---
title: Entrada de voz en Unity
description: Obtenga información sobre cómo Unity expone tres maneras de agregar entrada de voz, reconocimiento de voz y dictado a su aplicación Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, micrófono, dictado, voz, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 7268a4df9c7fce03029937c72540ed274574067d
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606120"
---
# <a name="voice-input-in-unity"></a>Entrada de voz en Unity

> [!CAUTION]
> Antes de comenzar, considere la posibilidad de usar el complemento Unity para el SDK de servicios de voz cognitivo. El complemento tiene mejores resultados de precisión de voz y acceso sencillo a la descodificación de voz a texto, así como características avanzadas de voz como cuadro de diálogo, interacción basada en intención, traducción, síntesis de texto a voz y reconocimiento de voz en lenguaje natural. Para empezar, consulte la [documentación y el ejemplo](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).

Unity expone tres maneras de agregar una [entrada de voz](../../design/voice-input.md) a la aplicación de Unity, los dos primeros son tipos de PhraseRecognizer:
* `KeywordRecognizer`Proporciona la aplicación con una matriz de comandos de cadena para realizar escuchas.
* `GrammarRecognizer`Proporciona a la aplicación un archivo SRGS que define una gramática específica para escuchar
* `DictationRecognizer`Permite que la aplicación escuche cualquier palabra y proporcione al usuario una nota u otra presentación de la voz.

> [!NOTE]
> No se puede controlar el reconocimiento de dictado y frase al mismo tiempo. Si GrammarRecognizer o KeywordRecognizer está activo, un DictationRecognizer no puede estar activo y viceversa.

## <a name="enabling-the-capability-for-voice"></a>Habilitación de la funcionalidad de Voice

La capacidad del **micrófono** se debe declarar para que una aplicación use la entrada de voz.
1. En el editor de Unity, vaya a **editar > configuración del proyecto > Player** .
2. Seleccione la pestaña de la **tienda Windows**
3. En la sección **funciones de configuración de publicación >** , Compruebe la capacidad del **micrófono** .
4. Concesión de permisos a la aplicación para el acceso al micrófono en el dispositivo HoloLens
    * Se le pedirá que lo haga en el inicio del dispositivo, pero si hizo clic accidentalmente en "no", puede cambiar los permisos en la configuración del dispositivo.

## <a name="phrase-recognition"></a>Reconocimiento de frases

Para permitir que la aplicación escuche frases específicas que habla el usuario, realice alguna acción; debe:
1. Especificar las frases que se van a escuchar con `KeywordRecognizer` o `GrammarRecognizer`
2. Controlar el `OnPhraseRecognized` evento y tomar las medidas correspondientes a la frase reconocida

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Espacio de nombres:** *UnityEngine. Windows. Speech*<br>
**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Necesitamos algunas instrucciones Using para guardar algunas pulsaciones de teclas:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

A continuación, vamos a agregar algunos campos a la clase para almacenar el reconocedor y la palabra clave >Diccionario de acciones:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Ahora, agregue una palabra clave al diccionario, por ejemplo, en de un `Start()` método. Estamos agregando la palabra clave "activar" en este ejemplo:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Cree el reconocedor de palabras clave e indíquele lo que desea reconocer:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Regístrese ahora para el `OnPhraseRecognized` evento

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

**Espacio de nombres:** *UnityEngine. Windows. Speech*<br>
**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

El GrammarRecognizer se usa si se especifica la gramática de reconocimiento mediante SRGS. Esto puede ser útil si la aplicación tiene más de unas pocas palabras clave, si desea reconocer frases más complejas o si desea activar o desactivar fácilmente conjuntos de comandos. Vea: [crear gramáticas con XML de SRGS](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) para obtener información sobre el formato de archivo.

Una vez que tenga la gramática de SRGS y esté en el proyecto en una [carpeta StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Cree un `GrammarRecognizer` y pásele la ruta de acceso al archivo SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Regístrese ahora para el `OnPhraseRecognized` evento

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Obtendrá una devolución de llamada que contiene la información especificada en la gramática de SRGS, que puede controlar de forma adecuada. La mayoría de la información importante se proporcionará en la `semanticMeanings` matriz.

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

**Espacio de nombres:** *UnityEngine. Windows. Speech*<br>
**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Use `DictationRecognizer` para convertir la voz del usuario en texto. DictationRecognizer expone la funcionalidad de [dictado](../../design/voice-input.md#dictation) y admite el registro y la escucha de eventos de hipótesis y frases completadas, de forma que puede enviar comentarios al usuario mientras hablan y después. `Start()``Stop()`los métodos y, respectivamente, habilitan y deshabilitan el reconocimiento de dictado. Una vez que se ha realizado con el reconocedor, se debe eliminar usando `Dispose()` para liberar los recursos que utiliza. Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se liberan antes.

Solo se necesitan algunos pasos para empezar a trabajar con el dictado:
1. Crear un nuevo `DictationRecognizer`
2. Controlar los eventos de dictado
3. Inicio de DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Habilitar la funcionalidad para el dictado

Las capacidades de cliente y **micrófono** de **Internet** se deben declarar para que una aplicación use dictado:
1. En el editor de Unity, vaya a **editar > configuración del proyecto > Player** .
2. Seleccionar en la pestaña de la **tienda Windows**
3. En la sección **capacidades de publicación de configuración de >** , Compruebe la funcionalidad de **InternetClient** .
    * Opcionalmente, si aún no ha habilitado el micrófono, Compruebe la capacidad del **micrófono** .
4. Conceda permisos a la aplicación para acceder al micrófono en el dispositivo HoloLens, si no lo ha hecho ya
    * Se le pedirá que lo haga en el inicio del dispositivo, pero si hizo clic accidentalmente en "no", puede cambiar los permisos en la configuración del dispositivo.

### <a name="dictationrecognizer"></a>DictationRecognizer

Cree un DictationRecognizer como el siguiente:

```
dictationRecognizer = new DictationRecognizer();
```

Hay cuatro eventos de dictado a los que se puede suscribir y controlar para implementar el comportamiento de dictado.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

Este evento se desencadena después de que el usuario se pausa, normalmente al final de una frase. Aquí se devuelve la cadena completa reconocida.

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

Este evento se desencadena continuamente mientras el usuario está hablando. A medida que el reconocedor realiza escuchas, proporciona texto de lo que se oye hasta ahora.

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

Este evento se desencadena cuando se detiene el reconocedor, ya sea de detención (), se ha producido un tiempo de espera o de algún otro error.

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

Una vez que haya suscrito y controlado los eventos de dictado que le interesan, inicie el reconocedor de dictado para comenzar a recibir eventos.

```
dictationRecognizer.Start();
```

Si ya no desea mantener el DictationRecognizer en torno, debe cancelar la suscripción a los eventos y eliminar el DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Sugerencias**
* `Start()``Stop()`los métodos y, respectivamente, habilitan y deshabilitan el reconocimiento de dictado.
* Una vez que se realiza con el reconocedor, se debe desechar usando `Dispose()` para liberar los recursos que utiliza. Estos recursos se liberan automáticamente durante la recolección de elementos no utilizados en un costo de rendimiento adicional si no se liberan antes.
* Los tiempos de espera se producen después de un período de tiempo establecido. Puede buscar estos tiempos de espera en el `DictationComplete` evento. Hay dos tiempos de espera que se deben tener en cuenta:
   1. Si el reconocedor se inicia y no oye ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.
   2. Si el reconocedor ha dado un resultado, pero oye el silencio durante 20 segundos, se agotará el tiempo de espera.

## <a name="using-both-phrase-recognition-and-dictation"></a>Usar el reconocimiento de frases y el dictado

Si desea usar tanto el reconocimiento de frases como el dictado en la aplicación, deberá apagarlo completamente antes de poder iniciar el otro. Si tiene varios KeywordRecognizers en ejecución, puede cerrarlos todos a la vez con:

```
PhraseRecognitionSystem.Shutdown();
```

Puede llamar `Restart()` a para restaurar todos los reconocedores a su estado anterior después de que DictationRecognizer se haya detenido:

```
PhraseRecognitionSystem.Restart();
```

También puede iniciar una KeywordRecognizer, lo que reiniciará el PhraseRecognitionSystem también.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrada de voz en el kit de herramientas de realidad mixta

Puede encontrar ejemplos de MRTK para la entrada de voz en las siguientes escenas de demostración:
* [Dictado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Voz](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, la tarea siguiente está explorando las funcionalidades y API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.