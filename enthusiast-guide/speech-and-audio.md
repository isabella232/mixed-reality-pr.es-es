---
title: Preguntas más frecuentes sobre voz y audio
description: Solución de problemas de Windows mixed reality de voz y audio que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, problemas de audio, problemas de voz
ms.openlocfilehash: 811c58196073a2a55af58978a4248033a1c4aef2
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131849"
---
# <a name="speech-and-audio-faqs"></a>Preguntas más frecuentes sobre voz y audio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>No puedo oír ningún sonido en el casco o el sonido se está reproduciendo en el equipo en lugar de en el casco

* Si el casco envolvente no incluye auriculares integrados, conecte auriculares al conector de audio del casco. El conector suele encontrarse detrás o debajo del visor o los lentes con auriculares. Si no puede encontrarlo, consulte con el fabricante del casco.
* Algunos auriculares de audio tienen botones físicos para controlar el volumen. Si el audio no funciona, compruebe si el volumen está desactivado o silenciado.
* Si saca el casco, gira el parasol, cierra la aplicación del portal de realidad mixta o, cuando esa aplicación no se ha usado durante 15 minutos, el audio cambiará al dispositivo de reproducción de Windows predeterminado. Puede cambiar esta configuración en **configuración > realidad mixta > audio y voz.**
* Asegúrese de que el casco de audio esté completamente enchufado en el conector de audio. El casco de Acer en concreto puede requerir más atención para asegurarse de que el casco de audio está enchufado.
* Compruebe que el micrófono y los auriculares de audio están enchufados en el casco y no en el PC.
* En el panel de control de sonido de **configuración > sistema > sonido** solo se muestran los puntos de conexión de audio habilitados, no deshabilitados. El dispositivo de audio con auriculares se deshabilitará cuando no disponga de los auriculares. Para verlo, haga clic con el botón derecho en el panel de control de sonido y elija "Mostrar dispositivos deshabilitados". El nombre del dispositivo es "Realtek USB 2.0 audio" (se puede cambiar el nombre en la página "propiedades"). Puede hacerlo para las pestañas reproducción y grabación.
* Si el audio no funciona en aplicaciones de realidad mixta (por ejemplo, Netflix), puede deberse a un problema conocido en el que Windows Mixed Reality no se actualice automáticamente para que coincida con la versión del sistema operativo. Para corregir este problema y obtener la mejor experiencia mixta, vaya a **configuración > actualizar & seguridad > Windows Update > comprobar si hay actualizaciones** .

> [!NOTE]
> * El audio espacial de realidad mixta de Windows funciona mejor con los auriculares incorporados o conectados directamente a los auriculares más inmersivo. Es posible que los altavoces o auriculares conectados al equipo no funcionen bien para el audio espacial.
> * Windows Mixed Reality no es compatible con los auriculares de audio Bluetooth.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Estoy experimentando cambios repentinos en el volumen, audio perdido o zumbidos

* Algunas aplicaciones, incluidas muchas de las que se inician a través de SteamVR, pueden perder audio o bloquearse cuando el dispositivo de audio cambia cuando se inicia o se detiene el portal de realidad mixta. Para corregir esto, vuelva a abrir el portal de realidad mixta y reinicie la aplicación.
* Si otro dispositivo USB multimedia (por ejemplo, una cámara web) comparte el mismo concentrador USB interno o externo con el casco de realidad mixta de Windows, es posible que, en ocasiones, el Jack o los auriculares de audio de los auriculares tengan un sonido de zumbido o que no haya audio. Conecte el casco a un puerto USB que use un concentrador diferente o desconecte o deshabilite el otro dispositivo multimedia USB.
* Si observa una ráfaga de ruido de los auriculares conectados al casco, es posible que el concentrador USB del equipo no pueda proporcionar suficiente energía para los auriculares de la realidad mixta de Windows. Si esto ocurre, archivo un error de [centro de comentarios](https://docs.microsoft.com/hololens/hololens-feedback) y pruebe lo siguiente:
    * quitar cables de extensión
    * uso de un CONCENTRADOr USB 3,0 dedicado y externo
    * un puerto USB diferente en el equipo

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mis auriculares de audio Bluetooth no funcionan como se esperaba

Microsoft no recomienda el uso de auriculares de audio Bluetooth con Windows Mixed Reality. Los periféricos de audio Bluetooth no funcionan bien con las experiencias de sonido espacial y de voz de Windows Mixed Reality, y los auriculares de audio Bluetooth no admiten la entrada de micrófono y la salida estéreo al mismo tiempo, por lo que no oirá sonido estéreo o espacial al usarlo para gamechat u otra entrada de voz. Los auriculares de audio Bluetooth también pueden afectar negativamente a la experiencia del controlador de movimiento.

## <a name="sound-isnt-coming-from-expected-directions"></a>El sonido no proviene de las direcciones esperadas

La Página principal de Windows Mixed Reality incluye sonido espacial (audio similar al de las aplicaciones que se encuentran en su hogar). A medida que se acerque y se aleje de cada aplicación, la dirección y el nivel sonoros cambiarán a la sensación de realismo. Estas son algunas razones posibles para las direcciones de sonido inesperadas:

* Si abre y reproduce música desde una aplicación de música compatible con el fondo (como Groove Music) en su hogar y, a continuación, abre una experiencia de VR envolvente como un juego, el sonido de la aplicación de música sonará a través del sonido espacial. Puede parecer más alto porque ya no existe ninguna distancia entre el usuario y el sonido.
* Si tiene Cortana habilitada en el equipo antes de usar el casco de la realidad mixta de Windows, puede perder el sonido espacial que se aplica a las aplicaciones en la Página principal de Windows Mixed Reality. Para solucionarlo, desactive "permitir que Cortana responda a Hola Cortana" en **configuración > Cortana** en el escritorio antes de iniciar Windows Mixed Reality, o bien habilite "Sonic de Windows para auriculares":
    1. Vaya a la ventana de la aplicación de escritorio en la Página principal de Windows Mixed Reality.
    2. Haga clic con el botón izquierdo en el icono de altavoz de la barra de tareas del escritorio y selecciónelo en la lista de dispositivos de audio.
    3. Haga clic con el botón secundario en el icono de altavoz de la barra de tareas del escritorio y seleccione "Windows Sonic para auriculares" en el menú "configuración del altavoz".
    4. Repita estos pasos para todos los dispositivos de audio (puntos de conexión).

## <a name="speech-commands-are-not-working-as-expected"></a>Los comandos de voz no funcionan como se esperaba

* Para usar comandos de voz, la configuración de voz y idioma del equipo debe estar establecida en un [idioma compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Para comprobar la configuración de la voz y el idioma de Windows, seleccione **configuración > tiempo & idioma > región & idioma** y **configuración > hora & lenguaje > voz** .
* Si el casco no tiene un micrófono integrado, deberá adjuntar auriculares con un micrófono al casco o a su PC. Para que la entrada de micrófono cambie automáticamente al casco cuando lo haga, vaya a **configuración > realidad mixta > audio y voz** , y Active "cuando me gaste el casco, cambie a micrófono de auriculares".
* Algunos auriculares de audio tienen un botón físico para silenciar y dessilenciar el micrófono. Si los comandos de voz no funcionan, compruebe si el micrófono está silenciado.
* Los auriculares de audio con un micrófono que se encuentra en el cable earbud no funcionan bien para los comandos de voz en entornos con ruido ambiente.
* Cortana puede ser lento la primera vez que se invoca en una sesión de portal de realidad mixta. Vaya a **configuración > cortana > hable con Cortana** y asegúrese de que esté habilitada la opción "permitir que Cortana responda a Hola Cortana".
* En algunos equipos, es posible que la ganancia predeterminada de la captura de voz para el micrófono conectado con auriculares sea demasiado baja. Si experimenta comandos de voz no confiables o dictado, ejecute el solucionador de problemas de instalación del micrófono:
    1. Vaya a la aplicación de escritorio en la Página principal de Windows Mixed Reality mientras usa el casco (para que afecte al micrófono que usa para Windows Mixed Reality).
    2. Vaya a **configuración > tiempo & idioma > Speech** .
    3. Seleccione "introducción" en la sección "micrófono".
    4. Seleccione el extremo adecuado en el Asistente para solucionar problemas.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Solo tengo un auricular de audio y quiero usarlo para el escritorio y para el casco

Si solo tiene un casco de audio y no tiene un casco con auriculares integrados, conecte los auriculares de audio al equipo en lugar de a los auriculares. A continuación, desactive "cambiar a audio con auriculares" en la configuración del portal de realidad mixta.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Quiero cambiar a Dolby Atmos para auriculares

Los entornos de realidad mixta de Windows y sus aplicaciones usan la tecnología de audio espacial de Windows Sonic para auriculares, que está personalizada para experiencias de realidad mixta. Otras tecnologías de audio espacial, como Dolby Atmos para auriculares, pueden aplicarse a aplicaciones de pantalla completa como SteamVR Games, pero no a los entornos y aplicaciones de Shell de realidad mixta de Windows (por ejemplo, la colocación de un explorador Web en la pared de la casa del acantilado o el cielo Loft) que se han diseñado con Windows Sonic para auriculares de sonido espacial y acústicos.
