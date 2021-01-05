---
title: Preguntas más frecuentes sobre el controlador de movimiento
description: Controladores solución de problemas de realidad mixta de Windows que van más allá de nuestra documentación de soporte técnico estándar para el consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, controladores de movimiento
appliesto:
- Windows 10
ms.openlocfilehash: 372e9ca294e7b65d3450e76b1dbd826a7b5b736b
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726036"
---
# <a name="motion-controller-faqs"></a>Preguntas más frecuentes sobre el controlador de movimiento

## <a name="what-do-the-vibrations-and-lights-mean"></a>¿Qué significan las vibraciones y las luces?

El LED constelación ring y hápticos indican el estado del controlador de movimiento.

| State    | Comportamiento asociado al estado | Cómo obtener o salir del estado |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Encendido**               | Los LED se encienden y el controlador vibra una vez. | Mantenga presionado el botón de Windows en el controlador durante dos segundos para activar el controlador.  |
| **Apagado**              |  Los LED se apagan y el controlador vibra dos veces. | Mantenga presionado el botón de Windows en el controlador durante cuatro segundos para desactivar el controlador.   |
| **En espera**               |  Los LED se apagan y parpadean cada tres segundos mientras están en estado de suspensión. | El controlador entra en el estado de inactividad automáticamente cuando se motionless durante 30 segundos. El controlador se activa cuando detecta movimiento, excepto si el dispositivo no está emparejado con el equipo host. Presione el botón para reactivarlo en ese caso. |
| **Emparejamiento**                |  Los LED se pulsan lentamente en el modo de emparejamiento y van sólidos al salir del modo de emparejamiento. El controlador vibra una vez si el emparejamiento fue correcto o tres veces si el emparejamiento no se realiza correctamente y, a continuación, se agota el tiempo de espera. | Mantenga presionado el botón de emparejamiento dentro de la batería durante tres segundos.     |
| **El controlador se conecta/desconecta del equipo** |  El controlador vibra una vez en la conexión o desconexión del equipo. | Se produce cuando el controlador se conecta correctamente al equipo después de encenderlo, o si el controlador se desconecta del equipo durante el uso.|
| **Nivel de batería baja**      | Los hápticos están deshabilitados cuando la batería es baja (no hay ninguna indicación LED). El icono del indicador de la batería del controlador de la controladora en auriculares mostrará 1/4 lleno cuando la batería esté baja. | Reemplace las baterías. | 
| **Nivel crítico de batería** |  El controlador vibra tres veces cuando se activa y se desactiva automáticamente. El icono del indicador de la batería se activará en rojo. | Reemplace las baterías. Si el problema persiste, [restaure el dispositivo a su configuración de fábrica](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) .|

## <a name="my-motion-controllers-arent-working-properly"></a>Mis controladores de movimiento no funcionan correctamente

Si los [controladores de movimiento](controllers-in-wmr.md) no funcionan, se conectan o muestran una imagen de los controladores cuando se usa el casco:

1. Asegúrese de que los controladores estén encendidos. Para activarlas, mantenga presionado el botón de Windows durante dos segundos.
2. Asegúrese de que los controladores estén totalmente cargados y reemplace las baterías si no lo están.
3. Apague y encienda los controladores mientras los mantiene delante. Mantenga presionado el botón Windows durante cuatro segundos para desactivar un controlador. Mantenlo de nuevo durante dos segundos para activarlo.
4. Compruebe si los controladores de movimiento están [emparejados correctamente](controllers-in-wmr.md#pair-motion-controllers).
5. Comprobar los LED de los controladores de movimiento: los controladores iluminados brillantes están emparejados y conectados, los controladores dimly Lit no están conectados.
6. Vaya a **inicio > portal de realidad mixta** en su PC y seleccione "menú". Debería ver los controladores de movimiento enumerados, junto con un mensaje de estado:
    * Listo: todos los controladores están establecidos.
    * Seguimiento perdido: el portal de realidad mixta no puede encontrar los controladores. Manténgalos delante del casco y reinícielos presionando el botón Windows durante cuatro segundos y, luego, de nuevo durante dos segundos.
    * Batería baja: Reemplace las baterías del controlador.
7. Si utiliza un adaptador de Bluetooth USB externo, asegúrese de que está conectado a un puerto USB 2,0 (a menudo, pero no siempre es negro). También debe estar enchufado en la medida de lo posible desde cualquier otro transmisor inalámbrico o unidad flash USB, incluido el conector USB del casco. 
8. Vaya a **Device Manager > Bluetooth** y busque un adaptador para comprobar que solo hay un radio Bluetooth en el equipo. Si usa la configuración de PC de escritorio con radio integrada, compruebe si hay una antena externa conectada. Si no hay ninguna antena externa conectada, puede causar problemas de seguimiento. O bien, use una llave de Bluetooth (USB) externa, deshabilite la funcionalidad de Bluetooth interna y reintente el emparejamiento y la conexión.
9. Si la ventana Configuración de Bluetooth está abierta en segundo plano, se realizan muchas llamadas adicionales al protocolo Bluetooth. Ciérrelo.
10. Compruebe el nivel de batería virtual en el controlador de movimiento. para ello, desactive los controladores en la realidad mixta para ver el icono de la batería. Espere unos 15 segundos antes de leer el nivel, ya que el nivel indicado es mayor que el nivel real inmediatamente después de conectar un controlador. Reemplace las baterías si el icono está en rojo.
11. Quite los altavoces y auriculares Bluetooth de la **configuración > dispositivos > Bluetooth & otros dispositivos** y apague los dispositivos. Use el conector de auriculares o los altavoces integrados en los auriculares de la realidad mixta para disfrutar de la mejor experiencia de audio.
12. Quite otros dispositivos Bluetooth que se pueden emparejar con su PC, como los auriculares o los controladores de juegos. Vaya a **configuración > dispositivos > Bluetooth & otros dispositivos**, seleccione los dispositivos y, a continuación, "quitar dispositivo".
13. Desconecte el cable USB del casco y conéctelo de nuevo al equipo para reiniciar Windows Mixed Reality.
14. Las luces del controlador parpadean cuando se están llevando a cabo una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en la realidad mixta.
15. Asegúrese de que el equipo está conectado a una red Wi-Fi de 5 GHz. Si el equipo portátil está conectado a una red Wi-Fi de 2,4 GHz, normalmente comparte la conexión Bluetooth. Esto puede afectar negativamente al rendimiento de Wi-Fi o Bluetooth, en función del diseño del producto. Cambie la banda preferida a 5 GHz en la configuración del adaptador de red. Si la red no admite 5 GHz, se puede usar una llave Bluetooth en lugar de la capacidad interna de Bluetooth.
16. Si la configuración de Bluetooth tiene controladores de movimiento ya emparejados, Windows no detectará los nuevos dispositivos hasta que se quiten. Si se han agregado con un adaptador de dispositivo específico, solo se pueden quitar con esa llave.
17. Si su equipo tiene Bluetooth integrado y tiene problemas de conexión, pruebe a usar un adaptador de Bluetooth USB. Para ello, desactive la radio Bluetooth integrada en Device Manager y, a continuación, empareje los demás dispositivos Bluetooth con el nuevo adaptador.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Mis controladores vibran, se bloquean o parpadean y desaparecen en realidad mixta

* Si el equipo se ejecuta en una red Wi-Fi de 2,4 GHz, cambie a la red Wi-Fi de 5 GHz. 
* Si usa un adaptador Bluetooth externo, asegúrese de que está conectado a un puerto USB 2,0 (que suele ser, aunque no siempre, negro), de otros transmisores inalámbricos o de unidades flash USB.
* Ejecute el solucionador de problemas de Bluetooth en **configuración > actualizar & seguridad > solucionar problemas de > Bluetooth**.

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Mi controlador está atascado en un reinicio infinito

Se trata de un indicador crítico de la batería. Coloque pilas nuevas en el dispositivo y, si el problema persiste, [restablezca la configuración de fábrica del controlador](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>El portal de realidad mixta funciona, pero el seguimiento de los controladores es deficiente (volando, agitando, etc.).

1. Las condiciones de iluminación pueden afectar al seguimiento. Asegúrese de que no está expuesto a la luz solar directa y de que tiene fuentes de luz de punto mínimas visibles para su HMD (por ejemplo, cadenas de luces como un árbol de Navidad).
2. Estos síntomas se deben a errores de comunicación entre el controlador y el equipo host, e indican una calidad de vínculo de Bluetooth deficiente. Consulte [preguntas sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Los LED del controlador de movimiento no están encendidos, pero los botones y el stick analógico siguen funcionando en el portal de realidad mixta.

La memoria caché de calibración del controlador de movimiento puede estar dañada. Para eliminar la memoria caché, ejecute el siguiente comando en un símbolo del sistema de administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Esta carpeta no es accesible en el explorador de Windows y solo se puede modificar desde un símbolo del sistema de administrador. Después de eliminar la carpeta, reinicie el equipo y vuelva a conectar los controladores de movimiento para restaurar los archivos de calibración.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Mi controlador es similar a un Naopak/Oculus, tiene una orientación extraña o los botones están asignados incorrectamente

Es probable que el sitio web no tenga compatibilidad total con el controlador de movimiento.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Mis controladores de movimiento no aparecen en aplicaciones y juegos de SteamVR

En primer lugar, asegúrese de que se cobran las baterías del controlador. Los controladores no funcionarán si las baterías están muertas o Dying

Si puede ver los controladores en la casa de acantilado, pero no en SteamVR apps and Games, es posible que el controlador del modelo de controlador de movimiento no esté instalado correctamente. Para comprobar que el controlador del modelo de controlador de movimiento está instalado correctamente:

1. Active ambos controladores de movimiento. Compruebe si los controladores de movimiento están [emparejados correctamente](controllers-in-wmr.md#pair-motion-controllers).
2. Vaya a **Device Manager > Bluetooth** y busque "controlador de movimiento".
3. Seleccione el dispositivo y, a continuación, vaya a **ver > dispositivos por conexión**.
4. Vaya a **configuración del sistema > dispositivos > Bluetooth & otros dispositivos > otros dispositivos** para ver si están visibles. Habrá dos dispositivos "dispositivo HID Bluetooth" y, en cada dispositivo HID Bluetooth, deben ser dispositivos denominados "controlador de movimiento" (con iconos grises) en el mismo nodo que el controlador de movimiento.
5. Haga doble clic en cada dispositivo de "controlador de movimiento" y vaya a la pestaña "controlador". Confirme que la versión de controlador indicada corresponde a una de [estas versiones](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history).
6. Si no es así, ejecute Windows Update, que descargará e instalará automáticamente el controlador. Si está en un equipo que tiene directivas de empresa o si Windows Update está restringido de otro modo, es posible que tenga que instalar manualmente el controlador del modelo de controlador de movimiento. Para ello, visite [esta página](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) y busque la versión del controlador correspondiente a su versión de Windows 10. Las instrucciones de instalación están disponibles en la página de descarga.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>La actualización del firmware del controlador tarda más de dos minutos

Consulte la [sección preguntas sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Una calidad de vínculo Bluetooth deficiente suele provocar estos problemas.

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Insertó baterías nuevas, pero el nivel de batería virtual del controlador no indica el nivel completo

El nivel de batería del controlador de movimiento está optimizado para baterías AA. Es posible que algunas baterías recargables de baja tensión no informen como llenas, aunque estén totalmente cargadas.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>El panel táctil del controlador de movimiento de Samsung está fuera del centro o tiene una zona muerta

Probablemente se trate de un defecto de hardware y debe volver al fabricante del distribuidor o equipo para reemplazarlo o cambiarlo.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Cómo restaurar los controladores a la configuración de fábrica

Restáurela en las condiciones de fábrica (necesitará baterías nuevas):

1. Desconecte y apague los controladores.
2. Abra la cubierta de la batería.
3. Inserte las nuevas baterías.
4. Mantenga presionado el botón de emparejamiento (la pestaña en la parte inferior de las baterías).
5. Mientras mantiene presionado el botón de emparejamiento, encienda el controlador presionando y manteniendo presionado el botón de Windows durante cinco segundos (mantenga presionados ambos botones).
6. Suelte los botones y espere a que el controlador se encienda. Esto tarda hasta 15 segundos y no hay ningún indicador cuando se está produciendo la recuperación del dispositivo. Si el dispositivo se enciende inmediatamente en el lanzamiento del botón, la secuencia del botón de recuperación no se registró y tendrá que intentarlo de nuevo.
7. Si los controladores se emparejaron al equipo, vaya a **configuración > Bluetooth > otros dispositivos** y seleccione "controlador de movimiento" y "quitar dispositivo" para quitar las asociaciones de controlador de la configuración de Bluetooth.
8. [Empareje los controladores](controllers-in-wmr.md#pair-motion-controllers) con el casco o el PC de nuevo.
9. Después de conectarse con el host y el casco, el dispositivo se actualizará al firmware disponible más reciente.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>¿Puedo emparejar mi controlador Xbox a mi PC para poder usarlo con auriculares

Puede emparejar un controlador Xbox de Bluetooth para usarlo con el casco siguiendo [estas instrucciones](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues).

Si tiene un controlador Xbox con cable, conéctelo a su PC.

Algunos juegos y aplicaciones usan el controlador Xbox de forma distinta a como se usa en la realidad mixta. Para usar el controlador para un juego o una aplicación, selecciona "usar como controlador de juegos" en la barra de la aplicación o "usar como controlador de juegos". Para volver a activar el controlador a la realidad mixta, vuelva a seleccionar "usar como controlador de juegos" o "use con mirarme". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Cómo emparejar controladores nuevos si Windows Mixed Reality ya está configurado en mi PC

Si va a emparejar los controladores con el casco, use la aplicación complementaria (el [portal de realidad mixta](install-windows-mixed-reality.md#launch-mixed-reality-portal) puede ayudarle a encontrar una aplicación complementaria que se inicia o le proporciona una lista de aplicaciones complementarias que puede seleccionar).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>¿Cómo puedo devolver mis controladores a su emparejamiento de fábrica?

Para devolver los controladores de movimiento a su emparejamiento de fábrica, o para emparejarlos con un casco de realidad mixta de Windows con radio Bluetooth integrado, ejecute la aplicación complementaria de dispositivo del casco y siga las instrucciones para el emparejamiento del controlador de movimiento. Por ejemplo, la aplicación "Acer OJO 500" o la aplicación "Samsung HMD Odyssey + Setup" se instalan automáticamente la primera vez que el casco está enchufado.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>Mis controladores de movimiento no se emparejan con mi PC

* Si los controladores no se activan, Inserte pilas nuevas. Si esto no lo corrige, restaure el dispositivo a su configuración de fábrica. para ello, encienda el dispositivo mientras mantiene presionados los botones de emparejamiento. Para obtener más información, consulte los [pasos de recuperación del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).
* Si los controladores se activan mientras usa un adaptador Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2,0 (que suele ser, aunque no siempre, negro), de otros transmisores inalámbricos o de unidades flash USB. Si sigue sin funcionar, ejecute el solucionador de problemas de Bluetooth en configuración > actualizar & seguridad > solucionar problemas de > Bluetooth.
* Si usa un adaptador Qualcomm y el equipo acaba de bloquearse, reinicie el equipo.
* Intente reiniciar los controladores de movimiento que no están emparejados, de uno en uno, y, a continuación, reinicie el equipo.
* La memoria caché del controlador de movimiento puede estar dañada. Para solucionar este problema, consulte estos [pasos](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal).
* Si los pasos corrigen el problema, póngase en contacto con el fabricante.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mis controladores emparejados no aparecen en el portal de realidad mixta

* Mantenga los controladores delante del casco y reinícielos; para ello, presione el botón Windows durante cuatro segundos y, luego, de nuevo durante dos segundos.
* Si los controladores se muestran como conectados, desemparejarlos y volver a realizar el [proceso de emparejamiento](controllers-in-wmr.md#pair-motion-controllers) .
* Si los LED del controlador se están reciclando con un cuadrante de encendido y apagado a la vez, se están llevando a cabo una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en la realidad mixta.
* Si se usa un adaptador Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2,0 (que es negro), fuera de otros transmisores inalámbricos o dispositivos USB 3,0.
* Si el equipo se acaba de bloquear y se usa un adaptador Qualcomm, es posible que no funcione el restablecimiento. Para solucionarlo, desconecte la alimentación de la parte posterior del equipo (o, si está en un portátil, mantenga presionado el botón de encendido durante 10 segundos) y reinicie el equipo.
* Ejecute el solucionador de problemas de Bluetooth en **configuración > actualizar & seguridad > solucionar problemas de > Bluetooth**.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Estoy intentando emparejar mis controladores, pero nunca aparecen en el menú "agregar un nuevo dispositivo" en la configuración de Bluetooth

Compruebe que ya no tiene controladores emparejados. Si lo hace, quítelos e inténtelo de nuevo. Reinicie el equipo si el problema persiste. Si se produce un error, consulte más [información sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Nota: si hay otro conjunto de controladores de movimiento emparejados con el equipo, deberá desemparejar los controladores antes de emparejarlos. Si empareja un conjunto de controladores de movimiento con el equipo actual y luego los empareja con un segundo equipo, deberá desemparejarlos y volver a emparejarlos con el equipo actual antes de volver a usarlos.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>¿Cómo se puede saber si utilizo tecnología Bluetooth?

Los controladores de movimiento usan la misma tecnología Bluetooth que se encuentra en muchos dispositivos de consumo y están diseñados para funcionar con la capacidad de Bluetooth incluida en cualquier equipo reciente. El equipo debe tener radio Bluetooth Si ha superado la comprobación de compatibilidad de realidad mixta. Para comprobarlo:

* Abra "Device Manager".
* Expanda la sección Bluetooth y busque un adaptador.

![Captura de pantalla de un Device Manager de ejemplo. El adaptador es el radio Bluetooth.](images/devicemanagerbtadapterpic.png)

Si su equipo no tiene Bluetooth, use el adaptador USB Bluetooth 4,0 Low Energy micro.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi se ralentiza en mi cuaderno cuando se activan los controladores de movimiento

El Bloc de notas puede compartir su Wi-Fi antena con Bluetooth cuando se conecta a un punto de acceso de 2,4 GHz. Proteja Device Manager si puede cambiar la preferencia de banda a 5 GHz. Si una red de 5 GHz no está disponible y el rendimiento se ve afectado gravemente, considere la posibilidad de usar una llave de Bluetooth.

![La configuración de selección de banda wifi se puede encontrar a través del administrador de dispositivos](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>Mi PC tiene tecnología Bluetooth, pero tengo problemas con mis controladores

Los controladores de movimiento deben funcionar con otros teclados, ratones y controladores de juegos Bluetooth. La experiencia variará en función del modelo de teclado, mouse o controlador de juego que use. Estas son algunas de las cosas que puede hacer para mejorar el rendimiento:

* Si el equipo tiene Bluetooth pero todavía tiene problemas con los controladores de movimiento, considere la posibilidad de reemplazar la radio Bluetooth por un adaptador Bluetooth externo acoplable conectado a USB. Solo puede tener un adaptador de radio Bluetooth activo a la vez. Si conecta una radio externa junto con una radio existente, deberá deshabilitar la radio Bluetooth existente en Device Manager. Haga clic con el botón derecho en el adaptador y seleccione "deshabilitar dispositivo" y desemparejar o volver a emparejar todos los dispositivos Bluetooth anteriores.
* Si utiliza un adaptador Bluetooth USB, conéctelo a un puerto USB 2,0 (los puertos 2,0 suelen ser negros y no tienen la etiqueta "SS"), si están disponibles. El puerto debe estar separado físicamente de:
    - el conector USB de HMD
    - unidades flash
    - unidades de disco duro
    - los receptores USB inalámbricos como los de teclados o ratones ideales, conectan el adaptador de Bluetooth USB en el lado opuesto del equipo lo más lejos posible de estos otros conectores.
* Cierre la ventana de configuración de Bluetooth Si está abierta. Dejándolo abierto en segundo plano significa que se realizan muchas llamadas adicionales al protocolo Bluetooth.
* Si el casco está emparejado con el equipo, use la pila del controlador de Bluetooth de Windows y no instale ninguna pila de controladores Bluetooth de terceros. Es posible que el software de terceros no funcione correctamente.
* Deshabilite la opción "Mostrar notificación para conectarse con el par SWIFT" en "Bluetooth & otros dispositivos" para reducir la actividad de detección de radio de host.
* Si utiliza una tarjeta Bluetooth interna, asegúrese de que está usando una antena Bluetooth externa o puede experimentar problemas de seguimiento. Si esto no funciona, use una llave Bluetooth (USB) externa después de deshabilitar el Bluetooth interno.
* El dispositivo debe aparecer en la categoría "Mouse, teclado & el lápiz" en la configuración de Bluetooth. Si se encuentra en "otros dispositivos", desemparejar y emparejar el dispositivo.
* Quitar, desemparejar y desconectar auriculares y altavoces Bluetooth. No se admiten con Windows Mixed Reality. Use el conector de auriculares o los altavoces integrados en los auriculares de la realidad mixta para disfrutar de la mejor experiencia de audio.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>El segundo controlador tarda mucho tiempo en volver a conectarse

Algunos dispositivos de radio Intel anteriores experimentan este problema si los controladores de movimiento se encienden al mismo tiempo. Evite el encendido de controladores al mismo tiempo.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Mi radio Bluetooth de Qualcomm no puede emparejar controladores después de un bloqueo del equipo

Los controladores de radio de Bluetooth Qualcomm (QCA) antes de 10.0.0.448 pueden acabar en mal estado después de un bloqueo de Windows. Apague el equipo completamente para solucionar este problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Tengo un seguimiento deficiente del controlador con radio Marvell

Vaya a **Device Manager > adaptador de radio bluetooth > de Marvell AVASTAR > propiedades del controlador >** y asegúrese de que está usando el controlador 15.68.9210.47 o posterior.
