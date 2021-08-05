---
title: Preguntas más frecuentes sobre voz y audio
description: Solución de problemas Windows Mixed Reality voz y audio que va más allá de nuestra documentación estándar de soporte técnico al consumidor.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Audio problems, Speech problems
ms.openlocfilehash: d1d30cebb40d54d579e978013b9abc60981fa943d43b95a96f358092631b4d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208985"
---
# <a name="speech-and-audio-faqs"></a>Preguntas más frecuentes sobre voz y audio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>No puedo escuchar ningún sonido en el casco o el sonido se reproduce a través de mi equipo en lugar del casco.

* Si el casco envolvente no incluye auriculares integrados, conecte los auriculares al conector de audio del casco. A menudo, el conector se encuentra justo detrás o debajo de la visor o las lentes del casco. Consulte con el fabricante del casco si no lo encuentra.
* Algunos cascos de audio tienen botones físicos para controlar el volumen. Si el audio no funciona, compruebe si el volumen está apagado o apagado.
* El audio cambia al dispositivo de reproducción Windows predeterminado: 
    * Si quita el casco
    * Voltear el visor hacia arriba
    * Cierre de la Portal de realidad mixta aplicación
    * Cuando una aplicación no se ha usado durante 15 minutos. 
    * Puede cambiar esta configuración en Configuración > **Mixed Reality > Audio y voz.**
* Asegúrese de que el casco de audio está conectado al conector de audio. En concreto, el casco de Acer puede requerir más atención para asegurarse de que el casco de audio está conectado.
* Compruebe que el micrófono o el casco de audio están conectados al casco y no al equipo.
* El cuadro de Panel de control en **Configuración > system > Sound** solo muestra los puntos de conexión de audio habilitados, no los puntos de conexión deshabilitados. El dispositivo de audio de los cascos se deshabilitará cuando no lleve el casco. Para verlo, haga clic con el botón derecho en el cuadro de Panel de control y elija "Mostrar dispositivos deshabilitados". El nombre del dispositivo es "Realtek USB2.0 Audio", cuyo nombre se puede cambiar en la página "Propiedades". Puede hacerlo para las pestañas de reproducción y grabación.
* Si el audio no funciona en Mixed Reality, por ejemplo, con la aplicación Netflix. Esto puede deberse a un problema conocido Windows Mixed Reality no se actualiza automáticamente para que coincida con la versión del sistema operativo. Para corregir este problema y obtener la mejor experiencia Mixed Reality, vaya a Configuración > **Update & Security > Windows Update > Buscar actualizaciones.**

> [!NOTE]
> * Windows Mixed Reality audio espacial funciona mejor con auriculares integrados o conectados directamente a los cascos envolventes. Es posible que los altavoces o auriculares de PC conectados al equipo no funcionen bien para el audio espacial.
> * Windows Mixed Reality no admite cascos Bluetooth audio.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Estoy experimentando cambios repentinos en el volumen, pérdida de audio o ruido

* Algunas aplicaciones, como las que se inician a través de SteamVR, pueden perder audio o detenerse cuando cambia el dispositivo de audio al iniciar o detener el Portal de realidad mixta. Para corregirlo, vuelva a abrir el Portal de realidad mixta y reinicie la aplicación.
* Si otro dispositivo USB multimedia (por ejemplo, un cámara web) comparte el mismo concentrador USB interno o externo con el casco Windows Mixed Reality, es posible que en ocasiones el conector de audio o los auriculares del casco tengan un sonido de timbre o ningún audio. Conecte el casco a un puerto USB que use un concentrador diferente o desconecte o deshabilite el otro dispositivo multimedia USB.
* Si observa una ráfaga de ruido fuerte de los auriculares conectados, es posible que el concentrador USB del equipo no pueda proporcionar suficiente energía al casco Windows Mixed Reality dispositivo. Si esto ocurre, presente un [error Centro de opiniones](/hololens/hololens-feedback) e intente lo siguiente:
    * quitar cables de extensión
    * uso de un concentrador USB 3.0 dedicado y externo
    * otro puerto USB en el equipo

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mi Bluetooth casco de audio no funciona según lo esperado

Microsoft no recomienda usar cascos Bluetooth audio con Windows Mixed Reality. Bluetooth periféricos de audio no funcionan bien con Windows Mixed Reality de voz y sonido espacial. Bluetooth cascos de audio no pueden admitir la entrada de micrófono y la salida estéreo al mismo tiempo, por lo que no escuchará sonido estéreo o espacializado al usarlo para gamechat u otra entrada de voz. Bluetooth cascos de audio también pueden afectar negativamente a la experiencia del controlador de movimiento.

## <a name="sound-isnt-coming-from-expected-directions"></a>El sonido no viene de las direcciones esperadas

El Windows Mixed Reality Inicio incluye sonido espacial (audio que parece procedente de las aplicaciones ubicadas en su hogar). A medida que se desenfoque y se acerque o se acerque más a cada aplicación, la dirección y el nivel del sonido cambiarán para aumentar la sensación de realismo. A continuación se muestran algunas posibles razones para direcciones de sonido inesperadas:

* Si abre y reproduce música desde una aplicación de música compatible con el fondo (como Groove Música) en su casa y, a continuación, abre una experiencia de realidad virtual inmersiva como un juego, el sonido de la aplicación de música se cruza desde el sonido espacial al estéreo. Puede parecer más alto porque ya no hay ninguna distancia entre usted y el sonido.
* Si había habilitado Cortana en el equipo antes de usar el casco de Windows Mixed Reality, puede perder el sonido espacial aplicado a las aplicaciones de su Windows Mixed Reality inicio. Para solucionar este problema, desactive "Let Cortana respond to Hey Cortana" (Permitir que Cortana responda a Hey Cortana) en **Configuración > Cortana** en el escritorio antes de iniciar Windows Mixed Reality, o habilite "Windows Sonic para auriculares":
    1. Vaya a la ventana Aplicación de escritorio en Windows Mixed Reality inicio.
    2. Haga clic con el botón izquierdo en el icono del altavoz en la barra de tareas Escritorio y selecciónelo en la lista de dispositivos de audio.
    3. Haga clic con el botón derecho en el icono del altavoz en la barra de tareas Escritorio y seleccione "Windows Sonic para auriculares" en el menú "Configuración del hablante".
    4. Repita estos pasos para todos los dispositivos de audio (puntos de conexión).

## <a name="speech-commands-are-not-working-as-expected"></a>Los comandos de voz no funcionan según lo previsto

* Para usar comandos de voz, la configuración de voz e idioma en el equipo debe establecerse en un [idioma compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Para comprobar la configuración Windows idioma y voz de Configuración >, seleccione idioma de idioma & hora **> región &** y idioma de Configuración > tiempo & idioma > **voz.**
* Si el casco no tiene un micrófono integrado, deberá conectar los auriculares con un micrófono al casco o al equipo. Para tener el conmutador de entrada de micrófono automáticamente en el casco al usarlo, vaya **Configuración > Mixed reality > Audio and speech**(Audio y voz de realidad mixta) y active "When I wear my headset, switch to headset mic".
* Algunos cascos de audio tienen un botón físico para silenciar y desactivar el micrófono. Si los comandos de voz no funcionan, compruebe si el micrófono está silenciado.
* Los cascos de audio con un micrófono que se desenreda desde el cable del auricular no son adecuados para los comandos de voz en entornos con ruido ambiental.
* Cortana puede ser lenta la primera vez que se invoca en una Portal de realidad mixta sesión. Vaya a **Configuración > Cortana > Hable con Cortana** asegúrese de que está habilitada la opción "Let Cortana respond to Hey Cortana" (Permitir que Cortana a Hey Cortana" esté habilitada.
* En algunos equipos, la ganancia de captura de voz predeterminada para el micrófono conectado al casco puede estar demasiado baja. Si experimenta comandos de voz no confiables o dictados, ejecute el solucionador de problemas de configuración del micrófono:
    1. Vaya a la aplicación de escritorio en la Windows Mixed Reality mientras lleva el casco (para afectar al micrófono que usa para Windows Mixed Reality).
    2. Vaya a **Configuración > Time & Language > Speech**.
    3. Seleccione "Introducción" en la sección "Micrófono".
    4. Seleccione el punto de conexión adecuado en el Asistente para el solucionador de problemas.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Solo tengo un casco de audio y quiero usarlo tanto para el escritorio como para el casco.

Si solo tiene un casco de audio y no tiene un casco con cascos integrados, conecte el casco de audio al equipo en lugar del casco. A continuación, desactive "Switch to headset audio" (Cambiar al audio del casco) en Portal de realidad mixta configuración.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Quiero cambiar a Dolby Atmos for Headphones

Windows Mixed Reality entornos y sus aplicaciones usan Windows Sonic para auriculares de audio espacial, que se personaliza para experiencias de realidad mixta. Otras tecnologías de audio espacial, como Dolby Atmos for Headphones, se pueden aplicar para aplicaciones de pantalla completa como juegos de SteamVR, pero no para entornos y aplicaciones de shell de Windows Mixed Reality (como la colocación de un explorador web en la pared del Casa sobre el acantilado o Sky Sky Sky) que se han diseñado con sonido espacial y acústica de Windows Sonic para auriculares.