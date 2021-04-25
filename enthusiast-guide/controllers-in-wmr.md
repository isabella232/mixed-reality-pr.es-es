---
title: Controladores de Windows Mixed Reality
description: Aprenda a configurar, emparejar, usar y solucionar problemas comunes con controladores en Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Feedback, Centro de opiniones, bugs
appliesto:
- Windows 10
ms.openlocfilehash: 66b352696016577ab121520102dd766b030ccf0e
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944636"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Controladores de movimiento en Windows Mixed Reality

Los controladores de movimiento son accesorios de hardware que permiten a los usuarios interactuar en realidad mixta. Una ventaja de los controladores de movimiento frente a los gestos es que los controladores tienen una posición precisa en el espacio, lo que permite una interacción más precisa con objetos digitales. Para Windows Mixed Reality cascos envolventes, los controladores de movimiento son la forma principal de que los usuarios tomen medidas en su mundo.

Windows Mixed Reality de movimiento ofrecen un seguimiento preciso y dinámico del movimiento en el campo de visión a través de los sensores envolventes de los cascos. No es necesario instalar hardware en las paredes del espacio. Estos controladores de movimiento ofrecen la misma facilidad de configuración y portabilidad que Windows Mixed Reality cascos envolventes.

También puede usar un controlador de Xbox, un mouse y un teclado, o bien moverse usando [solo la voz](using-speech-in-wmr.md).

## <a name="motion-controller-setup"></a>Configuración del controlador de movimiento

La mayoría de los cascos vienen emparejados previamente directamente con los cascos, pero algunos cascos iniciales requieren que los controladores de movimiento se empareen con el equipo con Bluetooth 4.0. Al conectar el casco envolvente por primera vez, se le mostrará cómo activar los controladores de movimiento durante la instalación. Pero si necesita volver a emparejarlos más adelante, aquí se muestra cómo:

1. Inicie **Portal de realidad mixta** con el casco conectado.  
2. En la esquina inferior izquierda, seleccione **... > Configurar controladores**.
3. Inserte dos baterías AA en cada controlador y ponga el controlador en modo de emparejamiento (consulte las instrucciones de la sección Controladores [de movimiento de pares).](controllers-in-wmr.md#pair-motion-controllers)
4. Siga las instrucciones proporcionadas en pantalla.

> [!NOTE]
> * Para los controladores que se emparejan directamente con el equipo, deberá ponerlos en modo de emparejamiento encendiendolos y presionando el botón de emparejamiento dentro del compartimiento de la batería hasta que las luces empiecen a parpadear.
> * Los controladores de movimiento solo admiten emparejarse con un equipo a la vez. Si necesita usarlos con un casco diferente, deberá pasar por el proceso de emparejamiento. Consulte [Configuración de Windows Mixed Reality](set-up-windows-mixed-reality.md)

[Obtener ayuda para conectarse](wmr-setup-faq.yml#my-motion-controllers-aren-t-working)

> [!IMPORTANT]
> **¿Tiene un controlador de Xbox?**
> 
> Si tienes un controlador Bluetooth de Xbox, empareda con tu PC para usarlo con el casco.
> 
> Si tiene un controlador Xbox cableado, conéctelo al equipo.
> 
> Algunos juegos y aplicaciones usan el controlador de Xbox de forma diferente a como se usa en la realidad mixta. Para usar el controlador para un juego o una aplicación, seleccione Usar como controlador para juegos **en** la barra de la aplicación o diga "Usar como controlador para juegos". Para volver a cambiar el controlador a la realidad mixta, seleccione Usar como controlador para juegos **,** de nuevo o diga "Usar con mirada".  

## <a name="pair-motion-controllers"></a>Emparejar controladores de movimiento

Si usa un casco que incluye un controlador Bluetooth integrado, como Samsung Samsung Samsung+ o HP Reverb, los controladores ya deben estar emparejados. Sin embargo, puede emparejar los controladores mediante la aplicación de instalación (ya debería estar instalada durante la configuración de HMD. También puede obtenerlo de Microsoft Store).

### <a name="pair-motion-controllers-to-hmd"></a>Emparejar controladores de movimiento con HMD

Para encender los controladores, presione el botón de Windows durante 2 segundos hasta que se enciendan los LED.

Quite la cubierta de la batería de los controladores y busque el botón de emparejamiento pequeño en el borde del controlador. Mantenga presionado este botón para emparejar con el equipo.
    ![Emparejamiento del controlador de movimiento](images/connect_controller.png)

Inicie **Portal de realidad mixta** con el casco conectado.  
En la esquina inferior izquierda, seleccione **... > Configurar controladores.**
Siga las instrucciones de la pantalla.

### <a name="pair-motion-controllers-to-pc"></a>Emparejar controladores de movimiento con PC

Puede emparejar el controlador con un equipo agregando otro dispositivo Bluetooth.

Encienda los controladores y colómelos en modo de emparejamiento como se ha descrito anteriormente.

* Vaya a Configuración del equipo.
* Dispositivo/ Agregar Bluetooth u otro dispositivo.

Una vez completado el emparejamiento, los LED serán sólidos y brillantes.

### <a name="common-issues"></a>Problemas comunes

* Compruebe que solo tiene una radio Bluetooth activa en el equipo. Si tiene más de una radio Bluetooth, deberá deshabilitar las demás radios en Administrador de dispositivos.
* Coloque el dongle Bluetooth en un puerto que tenga una línea de visión clara a los controladores y lejos de estar conectado a dispositivos USB 3.0. Se sabe que USB 3.0 tiene interferencias de radiofrecuencia con Bluetooth (lea [este documento](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) de Intel para obtener más detalles). Los puertos USB 2.0 pueden funcionar mejor para el dongle Bluetooth.
* Asegúrese de que el dongle Bluetooth no está conectado a un puerto USB junto al cable USB del HMD. También se sabe que el cable del casco provoca interferencias con bluetooth. Conecte el dongle en el puerto USB frontal del equipo para obtener los mejores resultados.
* En el caso de los cuadernos, asegúrese de que wi-fi está conectado a la banda de 5 GHz para obtener la mejor experiencia. Seleccione la bandeja inferior derecha del icono de red inalámbrica y seleccione las propiedades de la red que está usando. Los cuadernos diseñados para compartir una antena de 2,4 GHz para la conectividad Bluetooth y Wi-Fi verán la congestión de datos debido a velocidades de red lentas o un rendimiento deficiente del seguimiento del controlador de movimiento.
* Los controladores de movimiento recibirán actualizaciones de software nuevas de Microsoft de forma periódica. Los controladores mostrarán un patrón alterno de luces intermitentes cuando reciban estas nuevas actualizaciones de software. Esto es normal. Espere hasta que se complete la actualización de software antes de usar los controladores. Los controladores parpadearán y una luz constante reemplazará el patrón de flash alternativo cuando haya terminado.
* Es posible que se le diga "Put on the headset and use the thumbstick to teleport" (Poner el casco y usar la herramienta para teleportar) antes de que los controladores finalicen el proceso de actualización. Los controladores no serán visibles ni se podrán usar hasta que se complete la actualización. La mayoría de las actualizaciones se producen en dos minutos, pero las actualizaciones pueden tardar unos 10 minutos. Espere a que se complete la actualización antes de continuar con el paso siguiente.

## <a name="using-controllers"></a>Uso de controladores

Aquí se muestra cómo moverse por la realidad mixta con controladores de movimiento, un controlador para juegos de Xbox o un mouse y un teclado.

> [!TIP]
> Para cambiar la entrada entre la realidad mixta y el escritorio, presione la tecla **del logotipo de Windows + Y en** el teclado del equipo.

![Asignación de botones de controlador de movimiento](images/get_to_know_controllers.png)

|  Para hacer esto  |  Controladores de movimiento  | Controlador para juegos | Mouse + teclado |
| --- | --- | --- | --- |
| Teleport | Presione el botón de posición hacia delante y, a continuación, apunte el controlador donde desea ir. Suelte la chincheta. | Presione el botón de control izquierdo hacia delante y, a continuación, busque dónde desea ir. Suelte la chincheta. | Seleccione y mantenga presionado el botón derecho y, a continuación, apunte el mouse donde quiera ir. Suelte el botón. |
| Seleccionar | Apunte el controlador y, a continuación, extraiga el desencadenador o use el panel táctil. | Mire el destino y, a continuación, presione A. | Apunte el mouse y, a continuación, haga clic con el botón izquierdo. |
| Abrir el menú Inicio | Presione el **botón Windows.** | Presione el **botón Xbox.** | Presione la tecla **del logotipo de Windows**. |
| Dejar una aplicación inmersiva | Presione el **botón Windows.** A continuación, **seleccione Mixed reality home (Inicio de realidad** mixta) en el menú de acciones rápidas. | Presione el **botón Xbox.** A continuación, **seleccione el botón Inicio de realidad** mixta en el menú acciones rápidas. | Presione la tecla **Logotipo de Windows. A continuación, **seleccione el botón Inicio de realidad** mixta en el menú Acciones rápidas que aparece. |
| Girar | Mueva el control de posición a la izquierda o a la derecha. | Mueva el stick derecho a la izquierda o derecha. | No disponible. |
| Copia de seguridad | Mueva el control de posición hacia atrás. | Mueva el stick izquierdo hacia atrás. | No disponible. |
| A pie | Presione el botón de posición hacia abajo y, a continuación, púlsallo en la dirección que desea recorrer. | Presione el stick izquierdo hacia abajo y, a continuación, púlsallo en la dirección que desea recorrer. | No disponible. |
| Mover una ventana de aplicación | Apunte a la barra de la aplicación. Extraiga y mantenga presionado el desencadenador para agarrar la ventana y, a continuación, use el controlador para moverlo en cualquier dirección. Suelte el desencadenador. | Mire la barra de la aplicación y, a continuación, mantenga presionada la tecla A para agarrar la ventana. Use el stick izquierdo para mover la ventana de lado a lado o hacia arriba y hacia abajo. Use los desencadenadores para acercarlos más y más lejos. A continuación, la versión A. | Apunte el mouse a la barra de la aplicación. Haga clic con el botón izquierdo y mantenga presionado para agarrar la ventana y, a continuación, use el mouse para moverla de lado a lado o hacia arriba y hacia abajo. Use la rueda de desplazamiento para acercar o alejar la ventana. Suelte el botón del mouse (ratón). |
| Mover un objeto 3D | Apunte al objeto y, a continuación, extraiga y mantenga presionado el desencadenador para agarrarlo. Muévelo en cualquier dirección con el controlador y, a continuación, suelte el desencadenador. | Mire el objeto y, a continuación, mantenga presionada la tecla A para agarrarlo. Use el stick izquierdo para mover la ventana de lado a lado o hacia arriba y hacia abajo. Use los desencadenadores para acercarlos más y más lejos. A continuación, la versión A. | Apunte el mouse al objeto . Haga clic con el botón izquierdo y mantenga presionado para agarrarlo y, a continuación, use el mouse para moverlo de lado a lado o hacia arriba y hacia abajo.  Para acercarlos más o más lejos, use la rueda de desplazamiento. Suelte el botón del mouse (ratón). |
| Girar o cambiar el tamaño de una ventana de la aplicación | Apunte un controlador a la barra de la aplicación y el otro controlador en cualquier parte de la ventana. Mantenga presionados ambos desencadenadores y, a continuación, mueva los controladores juntos o separados para cambiar el tamaño.  Para girar, mueva un controlador hacia usted y el otro fuera de usted. Libere los desencadenadores. | Seleccione **Ajustar en** la barra de la aplicación. Mire a una esquina del marco de ajuste y presione A para seleccionarlo. Use el stick izquierdo para cambiar el tamaño de la ventana.  | Seleccione **Ajustar en** la barra de la aplicación. Seleccione y mantenga presionada una esquina del marco de ajuste y, a continuación, use el mouse para cambiar el tamaño de la ventana. |
| Girar o cambiar el tamaño de un objeto 3D | Apunte ambos controladores al objeto . Mantenga presionados ambos desencadenadores y, a continuación, mueva los controladores juntos o separados para cambiar el tamaño.  Para girar, mueva un controlador hacia usted y el otro fuera de usted. | Seleccione **Ajustar** en la barra de la aplicación y, a continuación, mueva el objeto con el stick izquierdo. | Seleccione **Ajustar** en la barra de la aplicación y, a continuación, mantenga presionado el objeto y use el mouse para moverlo. |
| Desplazarse en una ventana de aplicación | Extraiga y mantenga presionado el desencadenador y, a continuación, mueva el controlador hacia arriba o hacia abajo.  | Use el panel D. | Use la rueda de desplazamiento del mouse. |
| Acercar o alejar en la ventana de la aplicación | Extraiga ambos desencadenadores y, a continuación, mueva los controladores más juntos o más separados. | Extraiga el desencadenador derecho para acercar y el desencadenador izquierdo para alejar. | Use la rueda de desplazamiento del mouse mientras mantiene presionada la tecla CTRL en el teclado. |
| Abrir un menú | Presione el **botón** Menú. | Presione el **botón** Menú. | Haga clic con el botón derecho. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>¿Qué significan las vibración y las luces?

El controlador le comunica lo que hace mediante la vibración y el parpadeo de sus luces LED.

|  Cuando el controlador lo hace  |  Esto significa que |
| --- | --- |
| Los LED se encienden y el controlador se vibración una vez | **Activación** |  
| Los LED se apagan y el controlador se vibración dos veces | **Desactivar** |
| Led parpadean cada 3 segundos | **Dormir** |
| Los LED pulsan lentamente y el controlador se vibración una vez | **Introducción al modo de emparejamiento** |
| El controlador se vibración una vez | **Conexión o desconexión del equipo** |
| Los LED están muy encendidos | **Controladores de los que se realiza un seguimiento mediante el casco** |
| Los LED están atenuados | **Controladores de los que no realiza un seguimiento el casco** |
| El controlador se vibración tres veces y, a continuación, se apaga. | **Nivel de batería crítico** |
| Los anillos exterior e interno de los LED parpadean en un patrón alternativo | **Actualizando** |

## <a name="updating-motion-controllers-firmware"></a>Actualización del firmware de los controladores de movimiento

* Si hay un casco envolvente conectado al equipo y hay disponible un nuevo firmware del controlador, el firmware se insertará automáticamente en los controladores de movimiento la próxima vez que estén activados.
* Las actualizaciones de firmware del controlador se muestran con un patrón de iluminación de cuadrantes LED en un movimiento circular y pueden tardar entre 1 y 2 minutos. En ocasiones, las actualizaciones de firmware pueden tardar más, hasta 10 minutos, lo que puede indicar una mala conectividad Bluetooth o interferencias de radio.
* En caso de que se interrumpa la actualización del firmware (se apaga el controlador o se agota la batería), se volverá a intentar en la siguiente encendido.
* Una vez completada la actualización del firmware, los controladores se reiniciarán y se volverán a conectar.
* Ambos controladores deben estar conectados ahora. Vaya a Portal de realidad mixta para comprobar el estado de los controladores.
* Compruebe que los controladores funcionan correctamente:
  * Inicie **Portal de realidad mixta** y escriba su Mixed Reality Inicio.
  * Mueva los controladores y compruebe que el seguimiento, los botones de prueba y comprueben que la teleportación funciona. Si no lo hacen, consulte la sección de solución de problemas [del controlador de movimiento.](motion-controller-problems.md)

## <a name="faq"></a>Preguntas más frecuentes

### <a name="how-can-i-check-battery-level"></a>¿Cómo puedo comprobar el nivel de batería?

*A. El nivel de batería está en el lado inverso del modelo virtual, no hay ningún indicador físico de nivel de batería. Después de encender el controlador, espere unos segundos para que la lectura se estabilice.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>¿Puede usar estos controladores sin casco? ¿Solo para la entrada del desencadenador, etc.?

*A: No para aplicaciones universales de Windows*

## <a name="filing-motion-controller-feedbackbugs"></a>Presentación de comentarios o errores del controlador de movimiento

Enviarnos comentarios en Centro de opiniones, mediante la categoría "Mixed Reality -> Entrada".

## <a name="see-also"></a>Vea también

- [Controladores de HP en Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
- [Controladores de HP en Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
- [Preguntar a la comunidad](https://answers.microsoft.com)
- [Póngase en contacto con nosotros para obtener soporte técnico.](https://support.microsoft.com/contactus/)
- [Solución de problemas](troubleshooting-windows-mixed-reality.md)

¿Tiene problemas con los controladores de movimiento? [Obtener ayuda](motion-controller-problems.md)