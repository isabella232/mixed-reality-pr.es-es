---
title: 'Entrada de HoloLens de primera generación (212): voz'
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para aprender los detalles de los conceptos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, voice, HoloLens, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset, Windows 10
ms.openlocfilehash: 75a1d32ae72a07b68fc65c40035109c468adb1080070240827eeb253eb4a03f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207371"
---
# <a name="hololens-1st-gen-input-212-voice"></a>HoloLens (1ª generación) Entrada 212: Voz

>[!IMPORTANT]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (1ª generación), Unity 2017 y Mixed Reality cascos envolventes en mente.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos. Estos tutoriales no **_se actualizarán_** con los conjuntos de herramientas o interacciones más recientes que se usan para HoloLens 2 y es posible que no sean compatibles con las versiones más recientes de Unity.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

[La entrada de](../../../design/voice-input.md) voz nos ofrece otra manera de interactuar con nuestros hologramas. Los comandos de voz funcionan de una manera muy natural y sencilla. Diseñe los comandos de voz para que sean:

* Natural
* Fácil de recordar
* Contexto adecuado
* Suficientemente distintas de otras opciones dentro del mismo contexto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

En [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md), se usa KeywordRecognizer para compilar dos comandos de voz simples. En mr input 212, profundizaremos y aprenderemos a:

* Diseñe comandos de voz optimizados para el motor HoloLens voz.
* Haga que el usuario sepa qué comandos de voz están disponibles.
* Confirme que hemos oído el comando de voz del usuario.
* Comprenda lo que dice el usuario mediante un reconocedor de dictado.
* Use grammar recognizer para escuchar comandos basados en un archivo SRGS o especificación de gramática de reconocimiento de voz.

En este curso, volveremos a visitar el Explorador de modelos, que hemos creado en mr [input 210](holograms-210.md) y [mr input 211](holograms-211.md).

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el Mixed Reality Toolkit. Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para la pósteridad y porque los conceptos tratados siguen siendo aplicables.


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Entrada de realidad mixta (212): Voz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 configurado con las [herramientas correctas instaladas.](../../../develop/install-the-tools.md)
* Alguna capacidad básica de programación de C#.
* Debe haber completado [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Debe haber completado la [entrada mr 210](holograms-210.md).
* Debería haber completado la [entrada mr 211](holograms-211.md).
* Un HoloLens configurado [para el desarrollo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) requeridos por el proyecto. Requiere Unity 2017.2 o posterior.
* Des archive los archivos en el escritorio u otra ubicación de fácil acceso.

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errata y Notes

* "Habilitar Solo mi código" debe deshabilitarse *(desactivado)* en Visual Studio en Herramientas->Opciones->Depuración para alcanzar puntos de interrupción en el código.

## <a name="unity-setup"></a>Configuración de Unity

### <a name="instructions"></a>Instrucciones

1. Inicie Unity.
2. Seleccione **Open** (Abrir).
3. Vaya a la **carpeta HolographicAcademy-Hologramas-212-Voice** que anteriormente des archivó.
4. Busque y seleccione la carpeta **Starting** / **Model Explorer (Iniciar explorador de** modelos).
5. Haga clic en **el botón Seleccionar** carpeta.
6. En el **panel Project,** expanda la **carpeta Escenas.**
7. Haga doble clic **en ModeloExplorador** de la escena para cargarla en Unity.

### <a name="building"></a>Compilación

1. En Unity, seleccione **File > Build Configuración**.
2. Si **Scenes/ModelExplorer no** aparece en **Scenes In Build (Escenas** en la compilación), haga clic en **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena.
3. Si va a desarrollar específicamente para HoloLens, establezca **Dispositivo de destino** en **HoloLens**. De lo contrario, déjelo en **Cualquier dispositivo.**
4. Asegúrese **de que Tipo** de compilación está establecido en **D3D** y **sdk** está establecido en Instalado más reciente **(que** debe ser SDK 16299 o posterior).
5. Haga clic en **Generar**.
6. Cree una **carpeta denominada** "App".
7. Haga clic en la **carpeta** Aplicación.
8. Presione **Seleccionar carpeta y** Unity comenzará a compilar el proyecto para Visual Studio.

Cuando Unity haya terminado, aparecerá Explorador de archivos ventana.

1. Abra la **carpeta** Aplicación.
2. Abra la **solución ModelExplorer Visual Studio**.

Si se implementa en HoloLens:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x86.**
2. Haga clic en la flecha desplegable situada junto al botón Máquina local y seleccione **Equipo remoto.**
3. Escriba **la HoloLens IP del dispositivo y** establezca Modo de autenticación en Universal **(protocolo sin cifrar).** Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en Configuración > **Network & Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar** sin depurar o **presione Ctrl + F5**. Si es la primera vez que se implementa en el dispositivo, deberá emparejar con [Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. Cuando se haya implementado la aplicación, descarte **fitbox** con un **gesto de selección.**

Si se implementa en un casco envolvente:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x64.**
2. Asegúrese de que el destino de implementación está establecido en **Máquina local.**
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar** sin depurar o **presione Ctrl + F5**.
4. Cuando la aplicación se haya implementado, descarte **fitbox** mediante la extracción del desencadenador en un controlador de movimiento.

>[!NOTE]
>Es posible que observe algunos errores rojos en el panel Visual Studio errores. Es seguro omitirlos. Cambie al panel Salida para ver el progreso real de la compilación. Los errores del panel Salida requerirán que realice una corrección (la mayoría de las veces se deben a un error en un script).

## <a name="chapter-1---awareness"></a>Capítulo 1: Reconocimiento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre el diseño de los comandos Dos y **Don'ts** de voz.
* Use **KeywordRecognizer para** agregar comandos de voz basados en mirada.
* Haga que los usuarios conozcan los comandos de voz mediante los comentarios **del cursor**.

### <a name="voice-command-design"></a>Diseño de comandos de voz

En este capítulo, aprenderá a diseñar comandos de voz. Al crear comandos de voz:

#### <a name="do"></a>DO

* Cree comandos concisos. No quiere usar "Reproducir el vídeo seleccionado *actualmente",* ya que ese comando no es conciso y el usuario lo olvidaría fácilmente. En su lugar, debe usar: *"Reproducir vídeo",* porque es conciso y tiene varias sílabas.
* Use un vocabulario simple. Intente usar siempre palabras y frases comunes que sean fáciles de detectar y recordar para el usuario. Por ejemplo, si la aplicación tuviera un objeto de nota que se pudiera mostrar u ocultar de la vista, no usaría el comando *"Show Placard",* ya que "placard" es un término que se usa poco. En su lugar, usaría el comando" *"Mostrar nota"* para mostrar la nota en la aplicación.
* Ser coherente. Los comandos de voz deben ser coherentes en toda la aplicación. Imagine que tiene dos escenas en la aplicación y ambas escenas contienen un botón para cerrar la aplicación. Si la primera escena usó el comando *"Exit"* para desencadenar el botón, pero la segunda escena usó el comando *"Cerrar aplicación",* el usuario se va a confundir mucho. Si la misma funcionalidad persiste en varias escenas, se debe usar el mismo comando de voz para desencadenarla.

#### <a name="dont"></a>No

* Use comandos de sílabas únicas. Por ejemplo, si estaba creando un comando de voz para reproducir un vídeo, debe evitar el uso del comando simple *"Play",* ya que es solo una sílaba y el sistema podría perderse fácilmente. En su lugar, debe usar: *"Reproducir vídeo",* porque es conciso y tiene varias sílabas.
* Use comandos del sistema. El sistema reserva el comando *"Seleccionar"* para desencadenar un evento Tap para el objeto actualmente centrado. No vuelva a usar el comando *"Select"* en una palabra clave o frase, ya que es posible que no funcione como se espera. Por ejemplo, si el comando de voz para seleccionar un cubo en la aplicación era *"Seleccionar cubo",* pero el usuario miraba una esfera cuando pronunciaba el comando, la esfera se seleccionaría en su lugar. De forma similar, los comandos de la barra de la aplicación están habilitados para voz. No use los siguientes comandos de voz en la vista CoreWindow:
    1. Hacia atrás
    2. Herramienta de desplazamiento
    3. Herramienta zoom
    4. Herramienta de arrastre
    5. Ajustar
    6. Quitar
* Use sonidos similares. Intente evitar el uso de comandos de voz que riman. Si tuviera una aplicación de compra que admite *"Mostrar tienda"* y *"Mostrar más"* como comandos de voz, le gustaría deshabilitar uno de los comandos mientras el otro estaba en uso. Por ejemplo, podría usar el botón *"Mostrar tienda"* para abrir el almacén y, a continuación, deshabilitar ese comando cuando se mostrara el almacén para que el comando *"Mostrar más"* se pudiera usar para examinar.

### <a name="instructions"></a>Instrucciones

* En el panel **Hierarchy (Jerarquía) de** Unity, use la herramienta de búsqueda para buscar **el holoComm_screen_mesh** objeto.
* Haga doble clic en el **holoComm_screen_mesh** objeto para verlo en la **escena**. Este es el reloj del astronauta, que responderá a nuestros comandos de voz.
* En el **panel Inspector,** busque el componente Origen de entrada de voz **(script).**
* Expanda la **sección Palabras clave** para ver el comando de voz admitido: Abra **Communicator**.
* Haga clic en el engranaje del lado derecho y seleccione **Editar script.**
* Explore **SpeechInputSource.cs para** comprender cómo usa **KeywordRecognizer** para agregar comandos de voz.

### <a name="build-and-deploy"></a>Compilación e implementación

* En Unity, use **File > Build Configuración** para recompilar la aplicación.
* Abra la **carpeta** Aplicación.
* Abra la **solución ModelExplorer Visual Studio**.

(Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "Recargar todo" cuando se le solicite).

* En Visual Studio, haga clic **en Depurar -> Iniciar** sin depurar o presione Ctrl + **F5**.
* Una vez que la aplicación se implemente en HoloLens, descarte el cuadro de ajuste mediante el gesto [de pulsar el](../../../design/gaze-and-commit.md#composite-gestures) aire.
* Mire el reloj del astronauta.
* Cuando el reloj tenga el foco, compruebe que el cursor cambia a un micrófono. Esto proporciona comentarios sobre que la aplicación escucha comandos de voz.
* Compruebe que aparece información sobre herramientas en el reloj. Esto ayuda a los usuarios *a detectar el comando "Abrir Communicator".*
* Mientras mira el reloj, diga *"Abrir Communicator"* para abrir el panel de la comunicadora.

## <a name="chapter-2---acknowledgement"></a>Capítulo 2: Confirmación

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Objetivos

* Registre un mensaje mediante la entrada Micrófono.
* Enviar comentarios al usuario de que la aplicación está escuchando su voz.

>[!NOTE]
>La **funcionalidad** Micrófono debe declararse para que una aplicación grabe desde el micrófono. Esto ya se hace en mr input 212, pero tenga esto en cuenta para sus propios proyectos.
>
>1. En el Editor de Unity, vaya a la configuración del reproductor; para ello, vaya a "Editar > Project Configuración > Player".
>2. Haga clic en la pestaña "Plataforma Windows universal".
>3. En la sección "Funcionalidades de Configuración > publicación", compruebe la **funcionalidad Micrófono.**

### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía de** Unity, compruebe que el **holoComm_screen_mesh** está seleccionado.
* En el **panel Inspector,** busque el componente **Astronaut Watch (Script).**
* Haga clic en el pequeño cubo azul que se establece como el valor de la Communicator **propiedad Prefab.**
* En el **panel Project,** el **Communicator** anterior debe tener ahora el foco.
* Haga clic en **Communicator** en el panel **de** Project para ver sus componentes en **el inspector**.
* Mire el componente **Microphone Manager (Script) (Administrador** de micrófonos [script]), lo que nos permitirá grabar la voz del usuario.
* Tenga en cuenta **que Communicator** objeto tiene un componente controlador de entrada de voz **(script)** para responder al **comando Enviar** mensaje.
* Mire el componente **Communicator (script)** y haga doble clic en el script para abrirlo Visual Studio.

Communicator.cs es responsable de establecer los estados de botón adecuados en el dispositivo de resalte. Esto permitirá a nuestros usuarios grabar un mensaje, reproducirlo y enviarlo al astronauta. También se iniciará y detendrá una forma de onda animada para confirmar al usuario que se ha oído su voz.

* En **Communicator.cs**, elimine las líneas siguientes (81 y 82) del **método** Start. Esto habilitará el botón "Grabar" en el resalte.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilación e implementación

* En Visual Studio, recompile la aplicación e impleméntese en el dispositivo.
* Mire el reloj del astronauta y diga *"Abrir Communicator"* para mostrar la mirada.
* Presione el **botón Grabar** (micrófono) para empezar a grabar un mensaje verbal para el astronauta.
* Comience a hablar y compruebe que la animación de onda se reproduce en el resalte, lo que proporciona comentarios al usuario de que se escucha su voz.
* Presione el **botón Detener** (cuadrado izquierdo) y compruebe que la animación de onda deja de ejecutarse.
* Presione el **botón Reproducir** (triángulo derecho) para reproducir el mensaje grabado y escucharlo en el dispositivo.
* Presione el **botón Detener** (cuadrado derecho) para detener la reproducción del mensaje grabado.
* Diga *"Enviar mensaje"* para cerrar el mensaje y recibir una respuesta "Mensaje recibido" del astronauta.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capítulo 3: Descripción y el reconocedor de dictado

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Objetivos

* Use dictation Recognizer para convertir la voz del usuario en texto.
* Mostrar los resultados hipotéticos y finales del reconocedor de dictado en el resatorio.

En este capítulo, usaremos el reconocedor de dictado para crear un mensaje para el astronauta. Al usar el reconocedor de dictado, tenga en cuenta lo siguiente:

* Debe estar conectado a Wi-Fi para que el reconocedor de dictado funcione.
* Los tiempos de espera se producen después de un período de tiempo establecido. Hay dos tiempos de espera que se deben tener en cuenta:
  * Si el reconocedor se inicia y no escucha ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.
  * Si el reconocedor ha dado un resultado pero, a continuación, escucha el silencio durante veinte segundos, se agotará el tiempo de espera.
* Solo se puede ejecutar un tipo de reconocedor (palabra clave o dictado) a la vez.

>[!NOTE]
>La **funcionalidad** Micrófono debe declararse para que una aplicación grabe desde el micrófono. Esto ya se hace en mr input 212, pero tenga esto en cuenta para sus propios proyectos.
>
>1. En el Editor de Unity, vaya a la configuración del reproductor; para ello, vaya a "Editar > Project Configuración > Player".
>2. Haga clic en la pestaña "Plataforma Windows universal".
>3. En la sección "Funcionalidades de Configuración > publicación", compruebe la **funcionalidad Micrófono.**

### <a name="instructions"></a>Instrucciones

Vamos a editar **MicrophoneManager.cs** para usar el reconocedor de dictado. Esto es lo que agregaremos:

1. Cuando **se presiona el** botón Grabar, iniciaremos **dictationRecognizer**.
2. Mostrar la **hipótesis** de lo que el dictadoRecognizer entiende.
3. Bloquear los **resultados** de lo que el dictadoRecognizer entiende.
4. Compruebe los tiempos de espera del dictadoRecognizer.
5. Cuando se **presione el botón** Detener o se haya finalizado el tiempo de espera de la sesión de micrófono, detenga **dictationRecognizer**.
6. Reinicie **keywordRecognizer**, que escuchará el **comando Enviar** mensaje.

Comencemos. Complete todos los ejercicios de codificación para 3.a en **MicrophoneManager.cs,** o copie y pegue el código terminado que se encuentra a continuación:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Compilación e implementación

* Vuelva a generar Visual Studio e impleméntese en el dispositivo.
* Descarte el cuadro de ajuste con un gesto de pulsar el aire.
* Mire el reloj del astronauta y diga *"Abrir Communicator".*
* Seleccione el **botón** Grabar (micrófono) para registrar el mensaje.
* Empiece a hablar. El **reconocedor de dictado** interpretará su voz y mostrará el texto hipotético en el comunicador.
* Intente decir *"Enviar mensaje"* mientras está grabando un mensaje. Observe que **el reconocedor de palabras** clave no responde porque el **reconocedor de dictado** sigue activo.
* Deje de hablar durante unos segundos. Observe cómo el reconocedor de dictado completa su hipótesis y muestra el resultado final.
* Comience a hablar y, a continuación, haga una pausa de 20 segundos. Esto hará que el **reconocedor de dictado agote** el tiempo de espera.
* Observe que el **reconocedor de palabras** clave se vuelve a habilitar después del tiempo de espera anterior. El comunicador responderá ahora a los comandos de voz.
* Diga *"Enviar mensaje"* para enviar el mensaje al astronauta.

## <a name="chapter-4---grammar-recognizer"></a>Capítulo 4: Grammar Recognizer

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Objetivos

* Use Grammar Recognizer para reconocer la voz del usuario según un archivo SRGS o especificación de gramática de reconocimiento de voz.

>[!NOTE]
>La **funcionalidad** Micrófono debe declararse para que una aplicación grabe desde el micrófono. Esto ya se hace en la entrada 212 de MR, pero tenga esto en cuenta para sus propios proyectos.
>
>1. En el Editor de Unity, vaya a la configuración del reproductor; para ello, vaya a "Editar > Project Configuración > Player".
>2. Haga clic en la pestaña "Plataforma Windows universal"
>3. En la sección "Publishing Configuración > Capabilities" (Funcionalidades de Configuración > publicación), compruebe la **funcionalidad Microphone** (Micrófono).

### <a name="instructions"></a>Instrucciones

1. En el panel **Jerarquía,** busque **Jetpack_Center** y selecciónelo.
2. Busque el script **Acción tagalong** en el **panel** Inspector.
3. Haga clic en el círculo pequeño a la derecha del campo Objeto para **etiquetar junto.**
4. En la ventana que aparece, busque **SRGSToolbox** y selecciónelo en la lista.
5. Echa un vistazo al archivo **SRGSColor.xml** en la **carpeta StreamingAssets.**
    1. La especificación de diseño de SRGS se puede encontrar en el sitio web de W3C [aquí.](https://www.w3.org/TR/speech-grammar/)

En nuestro archivo SRGS, tenemos tres tipos de reglas:

* Una regla que le permite decir un color de una lista de doce colores.
* Tres reglas que escuchan una combinación de la regla de color y una de las tres formas.
* La regla raíz, colorChooser, que escucha cualquier combinación de las tres reglas de "color y forma". Las formas se pueden decir en cualquier orden y en cualquier cantidad, de una a las tres. Esta es la única regla que se escucha, ya que se especifica como la regla raíz en la parte superior del archivo en la etiqueta &lt; de gramática &gt; inicial.

### <a name="build-and-deploy"></a>Compilación e implementación

* Recompile la aplicación en Unity y, a continuación, compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.
* Descarte el cuadro de ajuste con un gesto de pulsar el aire.
* Mire el jetpack del astronauta y realice un gesto de pulsación en el aire.
* Empiece a hablar. **Grammar Recognizer interpretará** la voz y cambiará los colores de las formas en función del reconocimiento. Un comando de ejemplo es "círculo azul, cuadrado amarillo".
* Realice otro gesto de pulsar el aire para descartar el cuadro de herramientas.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ahora ha completado mr **input 212: voice**.

* Conoce los comandos de voz Dos y No.
* Ha visto cómo se empleó la información sobre herramientas para que los usuarios conozcan los comandos de voz.
* Ha visto varios tipos de comentarios usados para confirmar que se ha oído la voz del usuario.
* Sabe cómo cambiar entre el reconocedor de palabras clave y el reconocedor de dictado, y cómo estas dos características entienden e interpretan la voz.
* Ha aprendido a usar un archivo SRGS y Grammar Recognizer para el reconocimiento de voz en la aplicación.