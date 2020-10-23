---
title: Controladores de Windows Mixed Reality
description: Obtenga información acerca de cómo configurar y usar controladores en Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
appliesto:
- Windows 10
ms.openlocfilehash: d1cf8e56d19ef9ae62d9f83811e843f34b1c2d8c
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434582"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Controladores de movimiento en Windows Mixed Reality

Los controladores de movimiento son accesorios de hardware que permiten a los usuarios tomar medidas en realidad mixta. Una ventaja de los controladores de movimiento a través de gestos es que los controladores tienen una posición precisa en el espacio, lo que permite una interacción específica con objetos digitales. En el caso de los auriculares de la realidad mixta de Windows, los controladores de movimiento son la manera principal en que los usuarios realizarán acciones en su mundo.

Los controladores de movimiento de Windows Mixed Reality ofrecen un seguimiento preciso y con capacidad de respuesta del movimiento en el campo de la vista con los sensores en el casco envolvente, lo que significa que no es necesario instalar hardware en las paredes del espacio. Estos controladores de movimiento ofrecen la misma facilidad de configuración y portabilidad que los auriculares de la realidad mixta de Windows.

También puede usar una controladora Xbox, un mouse y un teclado, o bien desplazarse por [el uso de la voz](using-speech-in-wmr.md).

## <a name="motion-controller-setup"></a>Configuración del controlador de movimiento

La mayoría de los auriculares se emparejan previamente directamente con los auriculares, pero algunos auriculares iniciales requieren que los controladores de movimiento se emparejen al equipo con Bluetooth 4,0. Cuando conecte el casco envolvente por primera vez, se le guiará a través de la activación de los controladores de movimiento durante la instalación. Pero si necesita volver a emparejarlos más adelante, aquí se muestra cómo:

1. Inicie el **portal de realidad mixta** con los auriculares conectados.  
2. En la esquina inferior izquierda, seleccione **... > configurar controladores**.
3. Inserte dos baterías AA en cada controlador y ponga el controlador en modo de emparejamiento (consulte las instrucciones en la [sección sobre controladores de movimiento en pares](controllers-in-wmr.md#Pair-motion-controllers) ).
4. Siga las instrucciones que aparecen en pantalla.

> [!NOTE]
> * En el caso de los controladores que se emparejan directamente con el equipo, tendrá que colocarlos en modo de emparejamiento, para lo que debe encenderlos y presionar el botón de emparejamiento dentro del compartimiento de la batería hasta que las luces empiecen a parpadear.
> * Los controladores de movimiento solo admiten emparejarse a un equipo a la vez. Si tiene que usarlos con un casco diferente, deberá pasar por el proceso de emparejamiento. Consulte [configurar Windows Mixed Reality](set-up-windows-mixed-reality.md)

[Obtener ayuda para conectarse](wmr-setup-faq.md#my-motion-controllers-arent-working)

> [!IMPORTANT]
> **¿Tiene un controlador Xbox?**
> 
> Si tiene un controlador Xbox de Bluetooth, empareje con su PC para usarlo con el casco.
> 
> Si tiene un controlador Xbox con cable, conéctelo a su PC.
> 
> Algunos juegos y aplicaciones usan el controlador Xbox de forma distinta a como se usa en la realidad mixta. Para usar el controlador para un juego o una aplicación, selecciona **usar como** controlador de juegos en la barra de la aplicación o decir "usar como controlador de juegos". Para volver a cambiar el controlador a la realidad mixta, seleccione **usar como controlador para juegos**, de nuevo o decir, "usar con mirarme".  

## <a name="pair-motion-controllers"></a>Controladores de movimiento de pares

Si usa un casco que incluye un controlador Bluetooth integrado, como la reverberación Samsung Odyssey + o HP, los controladores ya deben estar emparejados. Sin embargo, puede seguir emparejando los controladores mediante la aplicación de configuración (ya debe estar instalado durante la configuración de HMD. También puede obtenerlo en Microsoft Store).

### <a name="pair-motion-controllers-to-hmd"></a>Emparejar controladores de movimiento a HMD

Encienda los controladores presionando el botón de Windows durante 2 segundos hasta que se iluminen los LED.

Quite la tapa de la batería de los controladores y busque el pequeño botón de emparejamiento en el borde del controlador. Mantenga presionado este botón para emparejar con el equipo.
    ![Emparejamiento de controlador de movimiento](images/connect_controller.png)

Inicie el **portal de realidad mixta** con los auriculares conectados.  
En la esquina inferior izquierda, seleccione **... > configurar controladores**.
Siga las instrucciones de la pantalla.

### <a name="pair-motion-controllers-to-pc"></a>Emparejar controladores de movimiento al equipo

Puede emparejar el controlador a un equipo mediante la adición de otro dispositivo Bluetooth.

Encienda los controladores y colóquelos en el modo de emparejamiento como se describió anteriormente.

* Vaya a configuración del equipo
* Dispositivo/agregar Bluetooth u otro dispositivo.

Una vez completado el emparejamiento, los LED serán sólidos y brillantes.

### <a name="common-issues"></a>Problemas comunes

* Compruebe que solo tiene un radio Bluetooth activo en el equipo. Si tiene más de un radio Bluetooth, tendrá que deshabilitar las demás radios en Device Manager.
* Coloque la llave de Bluetooth en un puerto que tenga una visión clara de los controladores, y lejos del encendido en dispositivos USB 3,0. Se sabe que USB 3,0 tiene interferencias RF con Bluetooth (lea [este documento](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) de Intel para obtener más detalles). Los puertos USB 2,0 funcionan mejor para el dispositivo Bluetooth.
* Asegúrese de que la llave Bluetooth no esté conectada a un puerto USB adyacente al cable USB de su HMD. También se sabe que el cable de auriculares causa interferencias con los llaves Bluetooth. Conecte el dispositivo de protección en el puerto USB front-end del equipo para obtener los mejores resultados.
* En el caso de los cuadernos, asegúrese de que Wi-Fi está conectado a una banda de 5 GHz para obtener la mejor experiencia (seleccione el icono de red inalámbrica en la bandeja inferior derecha y seleccione Propiedades para la red que está usando). Los cuadernos que están diseñados para compartir una antena de 2,4 GHz para la conectividad Bluetooth y WiFi tienen más probabilidades de ver la congestión de los datos en forma de velocidades de red lentas o un rendimiento deficiente de seguimiento para los controladores de movimiento.
* Los controladores de movimiento recibirán nuevas actualizaciones de software de Microsoft de forma periódica. Los controladores mostrarán un patrón alterno de luces intermitentes cuando reciban estas nuevas actualizaciones de software. Esto es normal. Espere hasta que se complete la actualización del software antes de usar los controladores (los controladores vibrarán y una luz constante reemplazará el patrón de Flash alterno cuando haya terminado).
* Es posible que se le diga "poner en el casco y usar el stick analógico para teletransportar" antes de que los controladores finalicen el proceso de actualización. Los controladores no estarán visibles ni se podrán usar hasta que se complete la actualización. La mayoría de las actualizaciones se producen en dos minutos, pero las actualizaciones pueden tardar hasta 10 minutos. Espere a que se complete la actualización antes de continuar con el siguiente paso.

## <a name="using-controllers"></a>Uso de controladores

Aquí se muestra cómo desplazarse por la realidad mixta con controladores de movimiento, un controlador para juegos de Xbox o un mouse y un teclado.

> [!TIP]
> Para cambiar la entrada entre la realidad mixta y el escritorio, presione la **tecla del logotipo de Windows + Y** en el teclado de su PC.

![Asignación de botón de controlador de movimiento](images/get_to_know_controllers.png)

|  Para  |  Controladores de movimiento  | Controlador para juegos | Mouse + teclado |
| --- | --- | --- | --- |
| Te | Presione el stick analógico hacia delante y luego señale el controlador al que desea ir. Suelte el stick. | Presione el stick analógico izquierdo hacia delante y luego mire dónde quiere ir. Suelte el stick. | Haga clic y mantenga presionado el botón secundario y, a continuación, señale el mouse donde desea ir. Suelte el botón. |
| Seleccionar | Señale el controlador y, a continuación, extraiga el desencadenador o haga clic en el panel táctil. | Mira el destino y después presiona. | Señale el mouse y haga clic con el botón primario. |
| Abrir el menú Inicio | Presione el botón **Windows** . | Presione el botón **Xbox** . | Presione la **tecla del logotipo de Windows**. |
| Dejar una aplicación envolvente | Presione el botón **Windows** . A continuación, seleccione **Inicio de realidad mixta** en el menú acciones rápidas. | Presione el botón **Xbox** . A continuación, seleccione el botón **Inicio de realidad mixta** en el menú acciones rápidas. | Presione la **tecla del logotipo de Windows**. Después, seleccione el botón **Inicio de realidad mixta** en el menú acciones rápidas que aparece. |
| Girar | Mueve el Stick a la izquierda o a la derecha. | Mueve el stick derecho a la izquierda o a la derecha. | No está disponible. |
| Copia de seguridad | Mueve el stick hacia atrás. | Mueve el stick izquierdo hacia atrás. | No está disponible. |
| A pie | Inserte el stick analógico hacia abajo y luego presiónelo en la dirección que desea recorrer. | Inserte el stick izquierdo hacia abajo y, a continuación, haga clic en la dirección que desea recorrer. | No está disponible. |
| Movimiento de una ventana de aplicación | Apunte a la barra de la aplicación. Tire y mantenga presionado el desencadenador para capturar la ventana y, a continuación, use el controlador para moverla en cualquier dirección. Libere el desencadenador. | Mira fijamente en la barra de la aplicación y después presiona y mantiene presionada la ventana. Use el botón de la derecha para subir o bajar la ventana. Use los desencadenadores para desplazarlos más cerca y más lejos. A continuación, libere un. | Señale el mouse en la barra de la aplicación. Haga clic con el botón derecho y mantenga presionado el botón del mouse para seleccionarlo de lado a lado o hacia arriba y hacia abajo. Use la rueda de desplazamiento para bajar o alejar la ventana. Suelte el botón del mouse (ratón). |
| Mover un objeto 3D | Señale el objeto y, a continuación, extraiga y mantenga presionado el desencadenador para capturarlo. Muévalo en cualquier dirección con el controlador y, a continuación, libere el desencadenador. | Mira el objeto, presiona y mantiene presionado para obtenerlo. Use el botón de la derecha para subir o bajar la ventana. Use los desencadenadores para desplazarlos más cerca y más lejos. A continuación, libere un. | Señale el mouse en el objeto. Haga clic con el botón izquierdo y mantenga presionado el botón del mouse para moverlo de lado a lado o hacia arriba y hacia abajo.  Para moverla más cerca o más lejos, use la rueda de desplazamiento. Suelte el botón del mouse (ratón). |
| Girar o cambiar el tamaño de una ventana de la aplicación | Señale un controlador en la barra de la aplicación y el otro controlador en cualquier parte de la ventana. Mantenga presionados ambos desencadenadores y, a continuación, mueva los controladores o separe su tamaño.  Para rotar, mueva un controlador hacia usted y el otro a su alrededor. Libere los desencadenadores. | Seleccione **ajustar** en la barra de la aplicación. Mira una esquina del marco de ajuste y después presiona un para seleccionarlo. Use el stick izquierdo para cambiar el tamaño de la ventana.  | Seleccione **ajustar** en la barra de la aplicación. Seleccione y mantenga presionada una esquina del marco de ajuste y, a continuación, use el mouse para cambiar el tamaño de la ventana. |
| Girar o cambiar el tamaño de un objeto 3D | Señale ambos controladores en el objeto. Mantenga presionados ambos desencadenadores y, a continuación, mueva los controladores o separe su tamaño.  Para rotar, mueva un controlador hacia usted y el otro a su alrededor. | Seleccione **ajustar** en la barra de la aplicación y, a continuación, mueva el objeto con el stick izquierdo. | Seleccione **ajustar** en la barra de la aplicación y, a continuación, seleccione y mantenga presionado el objeto y use el mouse para moverlo. |
| Desplazarse en una ventana de la aplicación | Extraiga y mantenga presionado el desencadenador y, a continuación, mueva el controlador hacia arriba o hacia abajo.  | Use el panel D. | Use la rueda de desplazamiento del mouse. |
| Acercar o alejar en la ventana de la aplicación | Tire de ambos desencadenadores y, a continuación, mueva los controladores más juntos o más lejos. | Tire del desencadenador adecuado para acercarlo y el desencadenador izquierdo para alejar. | Use la rueda de desplazamiento del mouse mientras mantiene presionada la tecla CTRL del teclado. |
| Abrir un menú | Presione el botón de **menú** . | Presione el botón de **menú** . | Haga clic con el botón secundario. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>¿Qué significan las vibraciones y las luces?

El controlador se comunica con usted lo que está haciendo vibrando y parpadeando las luces LED.

|  Cuando el controlador lo hace  |  Esto significa que |
| --- | --- |
| Los LED se encienden y el controlador vibra una vez | **Activar** |  
| Los LEDs se apagan y el controlador vibra dos veces | **Desactivación** |
| Los LED parpadean cada tres segundos | **En espera** |
| LED lentamente pulso y el controlador vibra una vez | **Entrar en el modo de emparejamiento** |
| El controlador vibra una vez | **Conexión o desconexión del equipo** |
| Los LED están iluminados brillantemente | **Controladores controlados por auriculares** |
| Los LED están dimly iluminados | **Controladores no controlados por los auriculares** |
| El controlador vibra tres veces y después se apaga | **Nivel crítico de batería** |
| Los anillos externos e internos de los LED parpadean en un patrón alterno | **Actualizando** |

## <a name="updating-motion-controllers-firmware"></a>Actualización del firmware de los controladores de movimiento

* Si hay un auricular envolvente conectado al equipo y hay disponible un nuevo firmware de controlador, el firmware se insertará automáticamente en los controladores de movimiento la próxima vez que se activen.
* Las actualizaciones de firmware del controlador se indican mediante un patrón de cuadrantes LED de iluminación en un movimiento circular y tardan 1-2 minutos. En ocasiones, las actualizaciones de firmware pueden tardar más tiempo, hasta 10 minutos, lo que puede indicar una mala conectividad Bluetooth o interferencias de radio.
* En caso de que se interrumpa la actualización de firmware (controlador apagado o batería agotada), se volverá a intentar en el siguiente encendido.
* Una vez finalizada la actualización del firmware, los controladores se reinician y se vuelven a conectar.
* Ambos controladores deben estar conectados ahora. Vaya al portal de realidad mixta para comprobar el estado de los controladores.
* Compruebe que los controladores funcionan correctamente:
  * Inicie el **portal de realidad mixta** y escriba su hogar de realidad mixta.
  * Mueva los controladores y compruebe el seguimiento, los botones de prueba y la comprobación de la teleportabilidad. Si no es así, consulte [la sección solución de problemas del controlador de movimiento](motion-controller-problems.md) .

## <a name="faq"></a>Preguntas más frecuentes

### <a name="how-can-i-check-battery-level"></a>¿Cómo puedo comprobar el nivel de batería?

*R: el nivel de batería está en el lado inverso del modelo virtual, no hay ningún indicador de nivel de batería físico. Después de encender el controlador, espere unos segundos para que la lectura se estabilice.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>¿Puede usar estos controladores sin un casco? Solo para la entrada joystick/Trigger/etc?

*R: no para aplicaciones universales de Windows*

## <a name="filing-motion-controller-feedbackbugs"></a>Archivado de comentarios y errores del controlador de movimiento

Envíenos sus comentarios en la central de comentarios, usando la categoría de entrada de > de realidad mixta.

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)
* [Solución de problemas](troubleshooting-windows-mixed-reality.md)

¿Tiene problemas con los controladores de movimiento? [Obtener ayuda](motion-controller-problems.md)