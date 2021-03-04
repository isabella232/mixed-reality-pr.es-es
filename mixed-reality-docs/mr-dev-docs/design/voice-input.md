---
title: Entrada de voz
description: La entrada de voz es una entrada básica para los auriculares de la realidad de HoloLens y Windows Mixed Reality. Voice se puede usar para comandos, dictado, Cortana y mucho más.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, voz, Cortana, voz, entrada, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, mira fijamente
ms.openlocfilehash: cc1ecd7d236748c3c4de77678e6f67c69a2c1af1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759146"
---
# <a name="voice-input"></a>Entrada de voz

![Entrada de voz](images/UX_Hero_VoiceCommand.jpg)

La voz es una de las formas clave de entrada en HoloLens. Permite comandos directamente de un holograma sin tener que usar [gestos de mano](gaze-and-commit.md#composite-gestures). La entrada de voz es una manera natural de comunicar tus intenciones. La voz es especialmente adecuada en el recorrido de interfaces complejas, ya que permite a los usuarios cortar menús anidados con un comando.

La entrada de voz se basa en el [mismo motor](/windows/uwp/design/input/speech-recognition) que admite la voz en todas las _aplicaciones universales de Windows_. En HoloLens, el reconocimiento de voz siempre funcionará en el idioma de visualización de Windows configurado en la configuración del dispositivo. 

<br>

## <a name="voice-and-gaze"></a>Voz y miras

Cuando se usan comandos de voz, la punta o la vista rápida es el mecanismo de selección de destino típico, con un cursor para "seleccionar" o para canalizar el comando a una aplicación que se está viendo. Es posible que ni siquiera sea necesario mostrar un cursor de miración _("verlo, decirlo")_. Algunos comandos de voz no requieren un destino, como "ir a Inicio" o "Hola Cortana".

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con micrófono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Comando "seleccionar"

**HoloLens (1ª generación)**

Incluso sin agregar específicamente compatibilidad con voz a su aplicación, los usuarios pueden activar los hologramas simplemente diciendo el comando de voz del sistema "Select". Esto se comporta igual que una [pulsación aérea](gaze-and-commit.md#composite-gestures) en HoloLens, presionando el botón seleccionar en el [clic de hololens](/hololens/hololens1-clicker)o presionando el desencadenador en un controlador de [movimiento de Windows Mixed Reality](motion-controllers.md). Oirá un sonido y verá que aparece una información sobre herramientas con "seleccionar" como confirmación. "Select" está habilitado por un algoritmo de detección de palabras clave de bajo consumo, lo que significa que puede decirlo en cualquier momento con un impacto mínimo en la duración de la batería. Incluso puede decir "seleccionar" con sus manos en su lado.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Para usar el comando "seleccionar" de voz en HoloLens 2, primero debe abrir el cursor de miración para usarlo como puntero. El comando para ponerlo al día es fácil de recordar (simplemente, por ejemplo, "Select").<br><br>
        Para salir del modo, vuelva a usar las manos con el toque de aire, cerca de un botón con los dedos o mediante el gesto del sistema.<br>
        <br> 
        *Imagen: "seleccionar" para usar el comando de voz para la selección*
    :::column-end:::
        :::column:::
       ![Un usuario puede decir "seleccionar" para usar el comando de voz para una selección.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Hola Cortana

Puede decir "Hola Cortana" para abrir Cortana en cualquier momento. No tiene que esperar a que parezca que sigue preguntando su pregunta o le dé una instrucción. Por ejemplo, intente decir "Hola a Cortana, ¿cuál es el tiempo?". como una sola oración. Para obtener más información sobre Cortana y lo que puede hacer, pregúntele. Por ejemplo, "Hola Cortana, ¿qué puedo decir?" y desplegarán una lista de comandos de trabajo y sugeridos. Si ya está **en la aplicación** de Cortana, seleccione el en la barra lateral para desplegar el mismo menú.

**Comandos específicos de HoloLens**
* "¿Qué puedo decir?"
* "Ir a Inicio"-en lugar de a la [floración](system-gesture.md#bloom) para ir al [menú Inicio](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)
* "Launch <app> "
* "Moverse <app> aquí"
* "Tomar una imagen"
* "Iniciar grabación"
* "Detener grabación"
* "Mostrar rayo manos"
* "Ocultar rayo manos"
* "Aumentar el brillo"
* "Reducir el brillo"
* "Aumentar el volumen"
* "Reducir el volumen"
* "Silenciar" o "dessilenciar"
* "Apagar el dispositivo"
* "Reiniciar el dispositivo"
* "Ir a suspensión"
* "¿Qué hora es?"
* "¿Cuánta batería he dejado?"

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"Verlo, decirlo"<br>
        HoloLens tiene un modelo "ver ti" para la entrada de voz, donde las etiquetas de los botones indican a los usuarios los comandos de voz que también pueden decir. Por ejemplo, al examinar una ventana de la aplicación en HoloLens (1ª generación), un usuario puede decir el comando "ajustar" para ajustar la posición de la aplicación en el mundo.<br>
        <br>
        *Imagen: un usuario puede decir el comando "ajustar", que se ve en la barra de la aplicación para ajustar la posición de la aplicación.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Al mirar una ventana de la aplicación o un holograma, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Cuando las aplicaciones siguen esta regla, los usuarios pueden comprender fácilmente qué decir para controlar el sistema. Mientras Gazing en un botón de HoloLens (1ª generación), verá una información sobre herramientas de "permanencia de voz" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para hablar de ella. Para mostrar la información sobre herramientas de voz en HoloLens 2, muestre el cursor de voz indicando "seleccionar" o "Qué puedo decir" (vea la imagen). <br>
        <br>
        *Imagen: "ver, por ejemplo," los comandos aparecen debajo de los botones*
    :::column-end:::
        :::column:::
       ![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para la manipulación rápida de hologramas

Hay muchos comandos de voz que puede decir mientras Gazing en un holograma para realizar rápidamente tareas de manipulación. Estos comandos de voz funcionan en las ventanas de la aplicación y en los objetos 3D que ha colocado en el mundo.

**Comandos de manipulación de hologramas**
* Me encuentro
* Mayor | Enhance
* Disminuye

En HoloLens 2, también puede crear interacciones más naturales en combinación con la mirada, que proporciona implícitamente información contextual sobre lo que se está haciendo referencia. Por ejemplo, podría ver un holograma y decir "colocarlo" y, a continuación, buscar _el_ lugar en el que desea colocarlo y decir " _aquí_".
O bien, podría ver una pieza holográfica en una máquina compleja y decir: "proporcione más información acerca de _esto_".

## <a name="discovering-voice-commands"></a>Detección de comandos de voz

Algunos comandos, como los comandos para la manipulación rápida anterior, se pueden ocultar. Para obtener información sobre los comandos que puede usar, mira fijamente a un objeto y, por ejemplo, "¿Qué puedo decir?". Aparece una lista de posibles comandos. También puede usar el cursor de mirar hacia abajo para buscar y mostrar la información sobre herramientas de voz de cada botón delante. 

Si desea una lista completa, simplemente indique "Mostrar todos los comandos" en cualquier momento. 

## <a name="dictation"></a>Dictado

En lugar de escribir con [grifos de aire](gaze-and-commit.md#composite-gestures), el dictado de voz puede ser más eficaz para escribir texto en una aplicación. Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.

![El dictado de voz comienza seleccionando el botón micrófono](images/micbuttonfordictation.png)<br>
*El dictado de voz comienza seleccionando el botón micrófono del teclado.*

Siempre que el teclado Holographic esté activo, puede cambiar al modo de dictado en lugar de escribir. Seleccione el micrófono en el lateral del cuadro de entrada de texto para comenzar.

## <a name="adding-voice-commands-to-your-app"></a>Agregar comandos de voz a la aplicación

Considera la posibilidad de agregar comandos de voz a cualquier experiencia que compiles. Voice es un método eficaz para controlar el sistema y las aplicaciones. Dado que los usuarios hablan con distintos tipos de dialectos y acentos, la elección adecuada de palabras clave de voz garantizará que los comandos de los usuarios se interpreten sin ambigüedades.

### <a name="best-practices"></a>Procedimientos recomendados

A continuación se muestran algunas prácticas que te ayudarán a realizar sin problemas las tareas de reconocimiento de voz.
* **Usa comandos concisos**: cuando sea posible, elige palabras clave de dos o más sílabas. Las palabras de una sílaba tienden a tener diferentes pronunciaciones de las vocales dependiendo del acento de la persona. Ejemplo: "reproducir vídeo" es mejor que "reproducir el vídeo seleccionado actualmente"
* **Usar vocabulario simple** : por ejemplo, "show Note" es mejor que "show letrero"
* Asegúrese de que los **comandos no sean destructivos** : Asegúrese de que las acciones de comando de voz no sean destructivas y se puedan deshacer fácilmente en caso de que otra persona que hable cerca del usuario desencadene accidentalmente un comando.
* **Evite comandos de sonido similares** : Evite registrar varios comandos de voz que suenen de forma similar. Ejemplo: "Mostrar más" y "Mostrar tienda" puede ser similar.
* **Anular el registro de la aplicación cuando no se usa** : cuando la aplicación no se encuentra en un estado en el que un comando de voz determinado es válido, considere la posibilidad de anular el registro para que otros comandos no estén confundidos para ese.
* **Prueba con diferentes acentos**: prueba la aplicación con usuarios con diferentes acentos.
* **Mantén la coherencia en los comandos de voz**: si "Volver" va a la página anterior, mantén este comportamiento en tus aplicaciones.
* **Evitar el uso de comandos del sistema** : los siguientes comandos de voz están reservados para el sistema, por lo que no se deben usar en las aplicaciones:
   * "Hola Cortana"
   * "Seleccionar"
   * "Ir a Inicio"

### <a name="advantages-of-voice-input"></a>Ventajas de la entrada de voz

Las entradas de voz son una manera natural de comunicar nuestras intenciones. La voz es especialmente útil en los **recorridos** de la interfaz, ya que puede ayudar a los usuarios a recorrer varios pasos de una interfaz. Un usuario podría decir "volver atrás" mientras mira una página web, en lugar de tener que subir y presionar el botón atrás en la aplicación. Esta pequeña hora de guardar tiene un **efecto emocional** eficaz sobre la percepción del usuario de la experiencia y les da una pequeña cantidad de mejorar enormemente. El uso de la voz es también un método práctico de entrada cuando tenemos las manos ocupadas o estamos **realizando varias tareas a la vez**. En los dispositivos en los que es difícil escribir en un teclado, el **dictado de voz** puede ser una forma alternativa eficaz de escribir texto. Por último, en algunos casos en los que el **intervalo de precisión** de la mirada y el gesto es limitado, la voz puede ayudar a eliminar la ambigüedad de la intención del usuario. 

**Cómo puede beneficiar al usuario la utilización de la voz**
* Reduce el tiempo: debe hacer que el objetivo final sea más eficaz.
* Minimiza el esfuerzo: debe hacer que las tareas se realicen de forma más fluida y sin esfuerzo.
* Reduce la carga cognitiva: es una forma intuitiva y fácil de aprender y recordar.
* Es social aceptable: debe ajustarse a las normas de un comportamiento de la sociedad.
* Es fácil de convertir en rutina: puede convertirse fácilmente en un comportamiento habitual.

### <a name="challenges-for-voice-input"></a>Desafíos de la entrada de voz

Aunque la entrada de voz es excelente para muchas aplicaciones diferentes, también enfrenta varios desafíos. La comprensión de las ventajas y los desafíos de la entrada de voz permite a los desarrolladores de aplicaciones tomar decisiones más inteligentes sobre cómo y Cuándo usar la entrada de voz y crear una excelente experiencia para los usuarios.

**Entrada de voz para el control de entrada continuo** El control específico es uno de ellos. Por ejemplo, un usuario podría querer cambiar su volumen en su aplicación de música. Puede decir "más alto", pero no está claro cuánto debe ser el sistema para crear el volumen. El usuario podría decir: "hacer que sea un poco más alto", pero "un poco" es difícil de cuantificar. El movimiento o el escalado de los hologramas con la voz es igualmente difícil. 

**Confiabilidad de la detección de entrada de voz** Aunque los sistemas de entrada de voz son mejores y mejores, a veces pueden oír e interpretar de forma incorrecta un comando de voz.
La clave es abordar el desafío en la aplicación. Proporcione comentarios a los usuarios cuando el sistema esté escuchando y lo que el sistema entienda clarifica los posibles problemas que comprenden la voz de los usuarios.  

**Entrada de voz en espacios compartidos** Es posible que la voz no sea socialmente aceptable en espacios que comparta con otros usuarios.
Estos son algunos ejemplos:
* Es posible que el usuario no quiera molestar a otros (por ejemplo, en una biblioteca tranquila o en una oficina compartida).
* Es posible que los usuarios no se vean tan complicados como hablar en el público.
* Un usuario puede sentirse incómodo dictar un mensaje personal o confidencial (incluidas las contraseñas) mientras que otros están escuchando

**Entrada de voz de palabras únicas o desconocidas** Las dificultades para la entrada de voz también se muestran cuando los usuarios están dictando palabras que pueden ser desconocidas para el sistema, como sobrenombres, ciertas palabras jergas o abreviaturas. 

**Comandos de voz de aprendizaje** Aunque el objetivo final es conversar naturalmente con el sistema, a menudo las aplicaciones todavía dependen de comandos de voz específicos predefinidos.
Un desafío asociado a un conjunto importante de comandos de voz es cómo enseñarlas sin sobrecargar al usuario y cómo ayudar al usuario a mantenerlas. 

<br>

---

### <a name="voice-feedback-states"></a>Estados de la respuesta a la voz

Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtiene una respuesta clara** de que el sistema **le ha oído correctamente**. Estas dos señales hacen que el usuario se sienta seguro utilizando la voz como entrada principal. A continuación se muestra un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y cómo se lo comunica al usuario.


:::row:::
    :::column:::
       ![1. estado normal del cursor](images/voicefeedbackstates-regular.jpg)<br>
       **1. estado normal del cursor**<br>
    :::column-end:::
    :::column:::
       ![2. comunica comentarios de voz y luego desaparece](images/voicefeedbackstates-voice.jpg)<br>
        **2. comunica comentarios de voz y luego desaparece**<br>
    :::column-end:::
    :::column:::
       ![3. Estado normal del cursor](images/voicefeedbackstates-regular.jpg)<br>
       **3. vuelve al estado normal del cursor**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Cosas principales que los usuarios deben saber sobre los comandos de voz en la realidad mixta

* **Suseleccione "seleccionar"** mientras el destino es un botón (puede utilizarlo en cualquier lugar para seleccionar un botón).
* Puedes decir el **nombre de etiqueta de un botón de la barra de la aplicación** en algunas aplicaciones para realizar una acción. Por ejemplo, al mirar una aplicación, un usuario puede decir el comando "quitar" para quitar la aplicación del mundo (esto ahorra tiempo al tener que seleccionarla con la mano).
* Puede iniciar la escucha de Cortana diciendo **"Hola Cortana".** Puedes preguntarle cosas ("Hola Cortana, cuál es la altura de la torre Eiffel"), decirle que abra una aplicación ("Hola Cortana, abre Netflix") o que abra el menú Inicio ("Hola Cortana, llévame al principio") y mucho más.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Preguntas y dudas comunes que tienen los usuarios acerca del uso de la voz

* What can I say? (¿Qué puedo decir?)
* ¿Cómo sé si el sistema me escuchó correctamente?
   * El sistema se equivoca todo el tiempo con mis comandos de voz.
   * No reacciona cuando digo un comando de voz.
* Reacciona de forma equivocada cuando digo un comando de voz.
* ¿Cómo dirijo mi voz a una aplicación o un comando de la aplicación específicos?
* ¿Puedo usar la voz para comandar cosas en el marco holográfico en HoloLens?

## <a name="communication"></a>Comunicación

En el caso de las aplicaciones que desean aprovechar las opciones de procesamiento de entrada de audio personalizadas proporcionadas por HoloLens, es importante comprender las distintas [categorías de flujo de audio](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) que puede consumir la aplicación. Windows 10 admite varias categorías de secuencias diferentes y HoloLens usa tres de ellas para habilitar el procesamiento personalizado con el fin de optimizar la calidad de audio del micrófono adaptada a la voz, la comunicación y otros, que se pueden usar para los escenarios de captura de audio de entorno ambiente (es decir, "videocámara").
* La categoría AudioCategory_Communications Stream está personalizada para escenarios de calidad y narración de llamadas y proporciona al cliente una secuencia de audio mono de 16 bits de 16 kHz de la voz del usuario
* La categoría AudioCategory_Speech Stream está personalizada para el motor de voz de HoloLens (Windows) y le proporciona una secuencia mono de 16 kHz de 24 bits de la voz del usuario. Los motores de voz de terceros pueden usar esta categoría si es necesario.
* La categoría AudioCategory_Other Stream está personalizada para la grabación de audio del entorno ambiente y proporciona al cliente una secuencia de audio estéreo de 24 bits 48 kHz.

Todo este procesamiento de audio se acelera en hardware, lo que significa que las características agotan una gran cantidad de energía que si se realizara el mismo procesamiento en la CPU de HoloLens. Evite ejecutar otro procesamiento de entrada de audio en la CPU para maximizar la duración de la batería del sistema y aprovechar el procesamiento de entrada de audio descargado integrado.

## <a name="languages"></a>Lenguajes

HoloLens 2 [es compatible con varios idiomas](/hololens/hololens2-language-support). Tenga en cuenta que los comandos de voz siempre se ejecutarán en el idioma para mostrar del sistema aunque se instalen varios teclados o cuando las aplicaciones intenten crear un reconocedor de voz en otro idioma.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene algún problema con "Select" y "Hola Cortana", intente cambiar a un espacio más silencioso, desplazarse fuera del origen del ruido o hablar de más alto. En este momento, todo el reconocimiento de voz en HoloLens se ajusta y optimiza específicamente a los hablantes nativos de Estados Unidos inglés.

En el caso de la versión 2017 de Windows Mixed Reality Developer Edition, la lógica de administración de puntos de conexión de audio funcionará bien (siempre) después de cerrar la sesión y volver a iniciarla en el escritorio del equipo después de la conexión inicial de HMD. Antes de que el primer evento de cierre de sesión o de salida después de pasar a WMR OOBE, el usuario podría experimentar varios problemas de funcionalidad de audio que van desde sin audio hasta sin conmutación de audio, en función de cómo se haya configurado el sistema antes de conectarse a HMD por primera vez.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Entrada de voz en MRTK (kit de herramientas de realidad mixta) para Unity
Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, puede asignar fácilmente comandos de voz en cualquier objeto. Use el **Perfil de entrada de voz** de MRTK para definir sus palabras clave. Mediante la asignación del script **SpeechInputHandler** , puede hacer que cualquier objeto responda a las palabras clave definidas en el perfil de entrada de voz. SpeechInputHandler también proporciona una etiqueta de confirmación de voz para mejorar la confianza del usuario.

* [Comando MRTK-Voice](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/speech.md)

---

## <a name="see-also"></a>Consulte también

* [Mirada y confirmación](gaze-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz en DirectX](../develop/native/voice-input-in-directx.md)
* [Entrada de voz en Unity](../develop/unity/voice-input-in-unity.md)