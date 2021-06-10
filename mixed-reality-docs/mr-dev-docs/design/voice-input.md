---
title: Entrada de voz
description: La entrada de voz es una entrada básica para HoloLens Windows Mixed Reality cascos envolventes. La voz se puede usar para comandos, dictado, Cortana y mucho más.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voice, cortana, speech, input, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit, gaze
ms.openlocfilehash: 6773bb71da7d98b1dd00d2246084d469e5e7c6ba
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600584"
---
# <a name="voice-input"></a>Entrada de voz

![Entrada de voz](images/UX_Hero_VoiceCommand.jpg)

La voz es una de las formas clave de entrada en HoloLens. Permite controlar directamente un holograma sin tener que usar [gestos de mano.](gaze-and-commit.md#composite-gestures) La entrada de voz es una manera natural de comunicar tus intenciones. La voz es especialmente buena para atravesar interfaces complejas, ya que permite a los usuarios recorrer los menús anidados con un comando.

La entrada de voz funciona con el [mismo motor que](/windows/uwp/design/input/speech-recognition) admite voz en todas las aplicaciones _universales de Windows._ En HoloLens, el reconocimiento de voz siempre funcionará en el idioma de visualización de Windows configurado en la configuración del dispositivo. 

<br>

## <a name="voice-and-gaze&quot;></a>Voz y mirada

Cuando se usan comandos de voz, la mirada con la cabeza o los ojos es el mecanismo típico de selección de destino, ya sea con un cursor para &quot;seleccionar&quot; o para canalizar el comando a una aplicación que esté viendo. Es posible que ni siquiera sea necesario mostrar ningún cursor de mirada _(&quot;véalo, digalo")._ Algunos comandos de voz no requieren ningún destino, como "ir al principio" o "Hola Cortana".

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con micrófono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>El comando "select"

**HoloLens (1ª generación)**

Incluso sin agregar específicamente compatibilidad de voz a la aplicación, los usuarios pueden activar hologramas simplemente indicando el comando de voz del sistema "select". Esto se comporta igual [](gaze-and-commit.md#composite-gestures) que una pulsación en el aire en HoloLens, al presionar el botón de selección en el botón de clic de [HoloLens](/hololens/hololens1-clicker)o al presionar el desencadenador en un controlador de movimiento [Windows Mixed Reality](motion-controllers.md). Oirá un sonido y verá que aparece una información sobre herramientas con "seleccionar" como confirmación. La opción "Seleccionar" está habilitada por un algoritmo de detección de palabras clave de bajo consumo, lo que significa que se puede decir en cualquier momento con un impacto mínimo en la duración de la batería. Incluso puede decir "seleccionar" con las manos a su lado.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Para usar el comando de voz "seleccionar" en HoloLens 2, primero debe abrir el cursor de mirada para usarlo como puntero. El comando para mostrarlo es fácil de recordar, por ejemplo, "select".<br><br>
        Para salir del modo, vuelva a usar las manos pulsando el aire, acercando un botón con los dedos o usando el gesto del sistema.<br>
        <br> 
        *Imagen: diga "seleccionar" para usar el comando de voz para la selección.*
    :::column-end:::
        :::column:::
       ![Un usuario puede decir "seleccionar" para usar el comando de voz para una selección.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Hola Cortana

Puede decir "Hola Cortana" para mostrar Cortana en cualquier momento. No tiene que esperar a que parezca que sigue haciendo su pregunta o le ha dado una instrucción. Por ejemplo, pruebe a decir "Hola Cortana, ¿cuál es el tiempo?" como una sola oración. Para obtener más información sobre Cortana y lo que puede hacer, pregúntele. Diga "Hola Cortana, ¿qué puedo decir?" y extraerá una lista de comandos en funcionamiento y sugeridos. Si ya está en la aplicación Cortana, seleccione el botón **?** icono de la barra lateral para extraer este mismo menú.

**Comandos específicos de HoloLens**
* "¿Qué puedo decir?"
* "Ir a Inicio": en lugar de [bloom](system-gesture.md#bloom) para ir al [menú Inicio](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)
* <app>"Launch"
* "Mover <app> aquí"
* "Hacer una foto"
* "Iniciar grabación"
* "Detener grabación"
* "Mostrar rayo de mano"
* "Ocultar rayo de mano"
* "Aumentar el brillo"
* "Disminuir el brillo"
* "Aumentar el volumen"
* "Reducir el volumen"
* "Mute" o "Unmute"
* "Apagar el dispositivo"
* "Reiniciar el dispositivo"
* "Ir a suspensión"
* "¿Qué hora es?"
* "¿Cuánta batería me queda?"

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"See It, Say It"<br>
        HoloLens tiene un modelo "véalo, digalo" para la entrada de voz, donde las etiquetas de los botones le dicen a los usuarios qué comandos de voz también pueden decir. Por ejemplo, al mirar una ventana de aplicación en HoloLens (1ª generación), un usuario puede decir el comando "Ajustar" para ajustar la posición de la aplicación en el mundo.<br>
        <br>
        *Imagen: un usuario puede decir el comando "Ajustar", que ve en la barra de la aplicación para ajustar la posición de la aplicación.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Al mirar una ventana de aplicación o un holograma, un usuario puede decir el comando "Ajustar" que ve en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Cuando las aplicaciones siguen esta regla, los usuarios pueden entender fácilmente qué decir para controlar el sistema. Mientras mira un botón en HoloLens (1ª generación), verá una información sobre herramientas de "permanencia de voz" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para hablar para "presionar". Para mostrar información sobre herramientas de voz en HoloLens 2, muestre el cursor de voz con "select" o "What can I say" (¿Qué puedo decir?) (Vea la imagen). <br>
        <br>
        *Imagen: los comandos "See it, say it" aparecen debajo de los botones*
    :::column-end:::
        :::column:::
       ![Véalo, por ejemplo, los comandos aparecen debajo de los botones.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para la manipulación rápida de hologramas

Hay muchos comandos de voz que puede decir mientras mira un holograma para realizar rápidamente tareas de manipulación. Estos comandos de voz funcionan en ventanas de aplicaciones y objetos 3D que ha colocado en el mundo.

**Comandos de manipulación de hologramas**
* Orientar hacia mí
* Más | Mejorar
* Más pequeño

En HoloLens 2, también puede crear interacciones más naturales en combinación con la mirada con los ojos, que proporciona implícitamente información contextual sobre lo que se hace referencia. Por ejemplo, podría mirar un holograma y decir "put _this"_(poner esto) y, a continuación, buscar dónde quiere colocarlo y decir _"aquí"._
O bien, podría ver una parte holográfica en una máquina compleja y decir: "give me more information about _this"._

## <a name="discovering-voice-commands"></a>Detectar comandos de voz

Algunos comandos, como los comandos para la manipulación rápida anterior, se pueden ocultar. Para obtener información sobre los comandos que puede usar, mire un objeto y diga "¿qué puedo decir?". Aparece una lista de posibles comandos. También puede usar el cursor de mirada con la cabeza para mirar y mostrar la información sobre herramientas de voz de cada botón delante de usted. 

Si quiere una lista completa, simplemente diga "Mostrar todos los comandos" en cualquier momento. 

## <a name="dictation"></a>Dictado

En lugar de escribir [con pulsaciones de aire,](gaze-and-commit.md#composite-gestures)el dictado de voz puede ser más eficaz para escribir texto en una aplicación. Esto puede acelerar enormemente la entrada con menos esfuerzo para el usuario.

![El dictado de voz se inicia seleccionando el botón de micrófono](images/micbuttonfordictation.png)<br>
*El dictado de voz se inicia seleccionando el botón de micrófono en el teclado*

Siempre que el teclado holográfico esté activo, puede cambiar al modo de dictado en lugar de escribir. Seleccione el micrófono en el lado del cuadro de entrada de texto para empezar.

## <a name="adding-voice-commands-to-your-app"></a>Adición de comandos de voz a la aplicación

Considera la posibilidad de agregar comandos de voz a cualquier experiencia que compiles. La voz es una manera eficaz de controlar el sistema y las aplicaciones. Dado que los usuarios hablan con diferentes tipos de dialectos y acentos, la elección adecuada de las palabras clave de voz garantizará que los comandos de los usuarios se interpreten de forma inequívoca.

### <a name="best-practices"></a>Procedimientos recomendados

A continuación se muestran algunas prácticas que te ayudarán a realizar sin problemas las tareas de reconocimiento de voz.
* **Usa comandos concisos**: cuando sea posible, elige palabras clave de dos o más sílabas. Las palabras de una sílaba tienden a tener diferentes pronunciaciones de las vocales dependiendo del acento de la persona. Ejemplo: "Reproducir vídeo" es mejor que "Reproducir el vídeo seleccionado actualmente"
* **Uso de vocabulario simple:** ejemplo: "Mostrar nota" es mejor que "Mostrar placa"
* **Asegúrese de que** los comandos no son destructivos: asegúrese de que las acciones de comandos de voz no sean destructivas y que se puedan deshacer fácilmente en caso de que otra persona que habla cerca del usuario desencadene accidentalmente un comando.
* **Evitar comandos de sonido similares:** evite registrar varios comandos de voz que suenen de forma similar. Ejemplo: "Mostrar más" y "Mostrar almacén" pueden ser similares.
* **Anular el** registro de la aplicación cuando no se usa: si la aplicación no está en un estado en el que un comando de voz determinado es válido, considere la posibilidad de anular el registro para que otros comandos no se confundan con ese.
* **Prueba con diferentes acentos**: prueba la aplicación con usuarios con diferentes acentos.
* **Mantén la coherencia en los comandos de voz**: si "Volver" va a la página anterior, mantén este comportamiento en tus aplicaciones.
* **Evitar el uso de comandos del sistema:** los siguientes comandos de voz están reservados para el sistema, así que evite usarlos en las aplicaciones:
   * "Hola Cortana"
   * "Seleccionar"
   * "Ir al inicio"

### <a name="advantages-of-voice-input"></a>Ventajas de la entrada de voz

Las entradas de voz son una manera natural de comunicar nuestras intenciones. La voz es especialmente buena en los **recorridos de interfaz** porque puede ayudar a los usuarios a recorrer varios pasos de una interfaz. Un usuario podría decir "volver" mientras mira una página web, en lugar de tener que subir y hacer clic en el botón Atrás de la aplicación. Este pequeño ahorro de tiempo tiene un efecto emocional **eficaz** en la percepción del usuario de la experiencia y le proporciona una pequeña cantidad de superpoder. El uso de la voz es también un método práctico de entrada cuando tenemos las manos ocupadas o estamos **realizando varias tareas a la vez**. En los dispositivos en los que es difícil escribir en un teclado, el **dictado de** voz puede ser una manera alternativa eficaz de introducir texto. Por último, en algunos  casos, cuando el intervalo de precisión para la mirada y el gesto son limitados, la voz puede ayudar a eliminar la ambigüedad de la intención del usuario. 

**Cómo puede beneficiar al usuario la utilización de la voz**
* Reduce el tiempo: debe hacer que el objetivo final sea más eficaz.
* Minimiza el esfuerzo: debe hacer que las tareas se realicen de forma más fluida y sin esfuerzo.
* Reduce la carga cognitiva: es una forma intuitiva y fácil de aprender y recordar.
* Es socialmente aceptable; debe ajustarse a las normas sociales de comportamiento.
* Es fácil de convertir en rutina: puede convertirse fácilmente en un comportamiento habitual.

### <a name="challenges-for-voice-input"></a>Desafíos de la entrada de voz

Aunque la entrada de voz es excelente para muchas aplicaciones diferentes, también se enfrenta a varios desafíos. Comprender las ventajas y los desafíos de la entrada de voz permite a los desarrolladores de aplicaciones tomar decisiones más inteligentes sobre cómo y cuándo usar la entrada de voz y crear una experiencia excelente para sus usuarios.

**Entrada de voz para el control de entrada continua** El control más preciso es uno de ellos. Por ejemplo, es posible que un usuario quiera cambiar su volumen en su aplicación de música. Puede decir "más alto", pero no está claro cuánto más alto se supone que el sistema debe hacer el volumen. El usuario podría decir: "Make it a little louder", pero "un poco" es difícil de cuantificar. Mover o escalar hologramas con voz es igualmente difícil. 

**Confiabilidad de la detección de entrada de voz** Aunque los sistemas de entrada de voz son mejores y mejores, a veces pueden escuchar e interpretar incorrectamente un comando de voz.
La clave es abordar el desafío en la aplicación. Proporcionar comentarios a los usuarios cuando el sistema escucha y lo que el sistema entiende aclara posibles problemas para comprender la voz de los usuarios.  

**Entrada de voz en espacios compartidos** Es posible que la voz no sea socialmente aceptable en espacios que se comparten con otros usuarios.
Estos son algunos ejemplos:
* Es posible que el usuario no quiera molestar a otros usuarios (por ejemplo, en una biblioteca silenciosa o una oficina compartida).
* Los usuarios pueden sentirse extraños cuando se les ve hablando a sí mismos en público.
* Es posible que un usuario no esté cómodo dictando un mensaje personal o confidencial (incluidas las contraseñas) mientras otros escuchan

**Entrada de voz de palabras únicas o desconocidas** Las dificultades para la entrada de voz también se encuentran cuando los usuarios dictan palabras que pueden ser desconocidas para el sistema, como alias, determinadas palabras de jerga o abreviaturas. 

**Aprendizaje de comandos de voz** Aunque el objetivo final es dialogar de forma natural con el sistema, a menudo las aplicaciones todavía se basan en comandos de voz predefinidos específicos.
Un desafío asociado a un conjunto significativo de comandos de voz es cómo enseñarlos sin sobrecargar al usuario y cómo ayudar al usuario a conservarlos. 

<br>

---

### <a name="voice-feedback-states"></a>Estados de la respuesta a la voz

Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtiene una respuesta clara** de que el sistema **le ha oído correctamente**. Estas dos señales hacen que el usuario se sienta seguro utilizando la voz como entrada principal. A continuación se muestra un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y cómo se lo comunica al usuario.


:::row:::
    :::column:::
       ![1. Estado normal del cursor](images/voicefeedbackstates-regular.jpg)<br>
       **1. Estado normal del cursor**<br>
    :::column-end:::
    :::column:::
       ![2. Comunica los comentarios de voz y, a continuación, desaparece](images/voicefeedbackstates-voice.jpg)<br>
        **2. Comunica los comentarios de voz y, a continuación, desaparece**<br>
    :::column-end:::
    :::column:::
       ![*3. Estado normal del cursor](images/voicefeedbackstates-regular.jpg)<br>
       **3. Vuelve al estado normal del cursor**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Cosas principales que los usuarios deben saber sobre los comandos de voz en la realidad mixta

* Diga **"Seleccionar"** al dirigirse a un botón (puede usarlo en cualquier lugar para seleccionar un botón).
* Puedes decir el **nombre de etiqueta de un botón de la barra de la aplicación** en algunas aplicaciones para realizar una acción. Por ejemplo, al mirar una aplicación, un usuario puede decir el comando "Quitar" para quitar la aplicación del mundo (esto ahorra tiempo al tener que seleccionarla con la mano).
* Para empezar a escuchar a **Cortana, diga "Hola Cortana".** Puedes preguntarle cosas ("Hola Cortana, cuál es la altura de la torre Eiffel"), decirle que abra una aplicación ("Hola Cortana, abre Netflix") o que abra el menú Inicio ("Hola Cortana, llévame al principio") y mucho más.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Preguntas y dudas comunes que tienen los usuarios acerca del uso de la voz

* What can I say? (¿Qué puedo decir?)
* ¿Cómo sé si el sistema me escuchó correctamente?
   * El sistema se equivoca todo el tiempo con mis comandos de voz.
   * No reacciona cuando digo un comando de voz.
* Reacciona de forma equivocada cuando digo un comando de voz.
* ¿Cómo dirijo mi voz a una aplicación o un comando de la aplicación específicos?
* ¿Puedo usar la voz para comandar cosas en el marco holográfico en HoloLens?

## <a name="communication"></a>Comunicación

En el caso de las aplicaciones que desean aprovechar las opciones personalizadas de procesamiento de entrada de audio proporcionadas por HoloLens, es importante comprender las distintas categorías de secuencias de [audio](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) que puede consumir la aplicación. Windows 10 admite varias categorías de secuencias diferentes y HoloLens usa tres de estas para permitir el procesamiento personalizado para optimizar la calidad del audio del micrófono adaptada a la voz, la comunicación y otras, que se puede usar para escenarios de captura de audio del entorno ambiente (es decir, "cámara").
* La categoría AudioCategory_Communications stream se personaliza para escenarios de narración y calidad de llamadas y proporciona al cliente una secuencia de audio mono de 16 kHz de 24 bits de la voz del usuario.
* La categoría AudioCategory_Speech stream se personaliza para el motor de voz de HoloLens (Windows) y proporciona una secuencia mono de 24 bits de 16 kHz de la voz del usuario. Los motores de voz de terceros pueden usar esta categoría si es necesario.
* La AudioCategory_Other de streaming está personalizada para la grabación de audio del entorno ambiente y proporciona al cliente una secuencia de audio estéreo de 24 bits de 48 kHz.

Todo este procesamiento de audio se acelera por hardware, lo que significa que las características consumen mucha menos potencia que si se realizara el mismo procesamiento en la CPU de HoloLens. Evite ejecutar otro procesamiento de entrada de audio en la CPU para maximizar la duración de la batería del sistema y aprovechar el procesamiento de entrada de audio descargado integrado.

## <a name="languages"></a>Idiomas

HoloLens 2 admite [varios lenguajes](/hololens/hololens2-language-support). Tenga en cuenta que los comandos de voz siempre se ejecutarán en el idioma para mostrar del sistema, incluso si hay varios teclados instalados o si las aplicaciones intentan crear un reconocedor de voz en otro idioma.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene algún problema al usar "select" y "Hey Cortana", intente pasar a un espacio más silencioso, alejarse de la fuente de ruido o hablar más alto. En este momento, todo el reconocimiento de voz en HoloLens está optimizado específicamente para hablantes nativos Estados Unidos inglés.

Para la versión 2017 de Windows Mixed Reality Developer Edition, la lógica de administración de puntos de conexión de audio funcionará bien (indefinidamente) después de cerrar sesión y volver a iniciar sesión en el escritorio del equipo después de la conexión INICIAL DE HMD. Antes de ese primer evento de inicio de sesión después de pasar por WMR OOBE, el usuario podría experimentar varios problemas de funcionalidad de audio que van desde sin audio a sin conmutación de audio en función de cómo se haya configurado el sistema antes de conectar el HMD por primera vez.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Entrada de voz en MRTK (Mixed Reality Toolkit) para Unity
Con **[MRTK,](https://github.com/Microsoft/MixedRealityToolkit-Unity)** puede asignar fácilmente comandos de voz en cualquier objeto. Use el perfil de entrada de **voz de** MRTK para definir las palabras clave. Al asignar el script **SpeechInputHandler,** puede hacer que cualquier objeto responda a las palabras clave definidas en el perfil de entrada de voz. SpeechInputHandler también proporciona la etiqueta de confirmación de voz para mejorar la confianza del usuario.

* [MRTK: comando de voz](/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a>Vea también

* [Mirada y confirmación](gaze-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz en DirectX](../develop/native/voice-input-in-directx.md)
* [Entrada de voz en Unity](../develop/unity/voice-input-in-unity.md)