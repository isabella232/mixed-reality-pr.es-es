---
title: Comandos de voz
description: Mirada, gesto y voz (GGV) son el medio principal de interacción en HoloLens. Este artículo proporciona información detallada sobre el diseño de voz.
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, design, interaction, voice
ms.openlocfilehash: 2a988ad50a8b20a256b0d7208187785778447cc08109fbf55d4ae83e820a76ba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225378"
---
# <a name="voice-commanding"></a>Comandos de voz

Cuando se usan comandos de voz, la mirada se usa normalmente como mecanismo de destino, ya sea como puntero ("seleccionar") o para dirigir el comando a una aplicación ("véalo, digalo"). Por supuesto, algunos comandos de voz no requieren un destino, como "Ir al comienzo" o "Hola, Cortana".


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
        <td>Comandos de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con casco adjunto)</td>
    </tr>
</table>



## <a name="how-to-use-voice"></a>Cómo se usa la voz

Considera la posibilidad de agregar comandos de voz a cualquier experiencia que compiles. La voz es una manera eficaz y cómoda de controlar el sistema y las aplicaciones. Dado que los usuarios hablan con variantes regionales y acentos diversos, la opción adecuada de palabras clave de voz asegurará que los comandos de los usuarios se interpretan de forma inequívoca.

### <a name="best-practices"></a>Procedimientos recomendados

A continuación se muestran algunas prácticas que te ayudarán a realizar sin problemas las tareas de reconocimiento de voz.
* **Usa comandos concisos**: cuando sea posible, elige palabras clave de dos o más sílabas. Las palabras de una sílaba tienden a tener diferentes pronunciaciones de las vocales dependiendo del acento de la persona. Ejemplo: "Reproducir vídeo" es mejor que "Reproducir el vídeo seleccionado actualmente"
* **Uso de vocabulario simple:** ejemplo: "Mostrar nota" es mejor que "Mostrar placa"
* **Asegúrate de que los comandos no sean destructivos**: haz que cualquier acción que se puede realizar mediante un comando de voz no sea destructiva, y se pueda deshacer fácilmente, en caso de que otra persona que esté hablando cerca del usuario pueda desencadenar accidentalmente un comando.
* **Evita los comandos que tengan un sonido similar**: evita registrar varios comandos de voz que suenen de forma parecida. Ejemplo: "Mostrar más" y "Mostrar tienda" pueden ser muy similares.
* **Anula el registro de la aplicación cuando no esté en uso**: cuando la aplicación no está en un estado en el que un comando de voz determinado es válido, considera la posibilidad de anular el registro de modo que otros comandos no se confundan con ese.
* **Prueba con diferentes acentos**: prueba la aplicación con usuarios con diferentes acentos.
* **Mantén la coherencia en los comandos de voz**: si "Volver" va a la página anterior, mantén este comportamiento en tus aplicaciones.
* **Evita el uso de comandos del sistema**: los siguientes comandos de voz están reservados para el sistema. Las aplicaciones no deben utilizar estos comandos.
   * "Hola Cortana"
   * "Seleccionar"

### <a name="select"></a>"Seleccionar"

Decir "seleccionar" en cualquier momento activará aquello a lo que está apuntando el cursor de mirada. 

>Nota: En HoloLens 2, el cursor de mirada debe invocarse primero con la palabra "select". Vuelva a decir "seleccionar" para activar. Para ocultar el cursor de mirada, basta con usar las manos para tocar o tocar un objeto. 

### <a name="see-it-say-it"></a>Verlo, decirlo

Windows Mixed Reality emplea un modelo de voz "verlo, decirlo" en el que **las etiquetas en los botones son idénticas a los comandos de voz asociados**. Como no hay ninguna diferencia entre la etiqueta y el comando de voz, los usuarios pueden saber mejor qué decir para controlar el sistema. Para servir de refuerzo, si el usuario se mantiene sobre un botón aparecerá una **"sugerencia de marca para voz"** para comunicar qué botones están habilitados para voz.


![Ejemplo 1 de verlo, decirlo](../design/images/voice-seeitsayit1-640px.jpg)

![Ejemplo 2 de verlo, decirlo](../design/images/voice-seeitsayit2-640px.jpg)<br>
*Ejemplos de "verlo, decirlo"*

### <a name="voices-strengths"></a>Puntos fuertes de los comandos de voz

Las entradas de voz son una manera natural de comunicar nuestras intenciones. La voz es especialmente buena en los **recorridos** de interfaz porque puede ayudar a los usuarios a recorrer varios pasos de una interfaz (un usuario podría decir "volver" mientras mira una página web, en lugar de tener que subir y hacer clic en el botón Atrás en la aplicación). Este pequeño ahorro de tiempo tiene **un** efecto emocional eficaz en la percepción del usuario de la experiencia y le proporciona una pequeña cantidad de superpoderes. El uso de la voz es también un método práctico de entrada cuando tenemos las manos ocupadas o estamos **realizando varias tareas a la vez**. En los dispositivos en los que escribir en un teclado es difícil, el **dictado** de voz puede ser una manera eficaz y alternativa de entrada. Por último, en algunos  casos, cuando el intervalo de precisión de la mirada y el gesto son limitados, la voz podría ser el único método de entrada de confianza del usuario.

**Cómo puede beneficiar al usuario la utilización de la voz**
* Reduce el tiempo: debe hacer que el objetivo final sea más eficaz.
* Minimiza el esfuerzo: debe hacer que las tareas se realicen de forma más fluida y sin esfuerzo.
* Reduce la carga cognitiva: es una forma intuitiva y fácil de aprender y recordar.
* Es aceptable socialmente: se adapta a las normas sociales en términos de comportamiento.
* Es fácil de convertir en rutina: puede convertirse fácilmente en un comportamiento habitual.

### <a name="voices-weaknesses"></a>Desventajas de los comandos de voz

La voz también tiene algunas desventajas. Uno de ellos es la falta de precisión en el control. (por ejemplo, un usuario podría decir "más alto", pero no puede decir cuánto. "Un poco" es algo difícil de cuantificar. El movimiento o el escalado de las cosas con la voz también es también difícil (la voz no ofrece granularidad en el control). Los comandos de voz también pueden ser imperfectos. A veces, un sistema de voz escucha de forma incorrectamente un comando o no lo escucha. Recuperarse de estos errores es un desafío en cualquier interfaz. Por último, el uso de la voz puede no ser socialmente aceptable en lugares públicos. Hay algunas cosas que los usuarios no pueden o no deben decir. Por estos motivos, el habla debe utilizarse para aquello para lo que mejor sirve.

### <a name="voice-feedback-states"></a>Estados de la respuesta a la voz

Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtiene una respuesta clara** de que el sistema **le ha oído correctamente**. Estas dos señales hacen que el usuario se sienta seguro utilizando la voz como entrada principal. A continuación se muestra un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y cómo se lo comunica al usuario.

![Estados de la respuesta a la voz del cursor](../design/images/voicefeedbackstates.png)<br>
*Estados de la respuesta a la voz del cursor*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Cosas principales que los usuarios deben saber sobre los comandos de voz en la realidad mixta
* Di **"Seleccionar"** mientras seleccionas como destino un botón (puedes usar esto en cualquier lugar para hacer clic en un botón).
* Puedes decir el **nombre de etiqueta de un botón de la barra de la aplicación** en algunas aplicaciones para realizar una acción. Por ejemplo, al examinar una aplicación, un usuario puede decir el comando "Quitar" para quitar la aplicación (esto te ahorra el tiempo de hacer clic con la mano).
* Puedes iniciar la escucha de Cortana diciendo **"Hola Cortana".** Puede hacer sus preguntas ("Hola Cortana, ¿qué alto es la torre de Tower?", pedirle que abra una aplicación ("Hola Cortana, abra Netflix") o pedirle que abra el menú Inicio ("Hola Cortana, lléveme a casa") y mucho más.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Preguntas y dudas comunes que tienen los usuarios acerca del uso de la voz
* What can I say? (¿Qué puedo decir?)
* ¿Cómo sé si el sistema me escuchó correctamente?
   * El sistema se equivoca todo el tiempo con mis comandos de voz.
   * No reacciona cuando digo un comando de voz.
* Reacciona de forma equivocada cuando digo un comando de voz.
* ¿Cómo dirijo mi voz a una aplicación o un comando de la aplicación específicos?
* ¿Puedo usar la voz para comandar cosas en el marco holográfico en HoloLens?

## <a name="see-also"></a>Consulte también
* [Gestos](../design/gaze-and-commit.md#composite-gestures)
* [Control con la cabeza y permanencia](../design/gaze-and-dwell.md)