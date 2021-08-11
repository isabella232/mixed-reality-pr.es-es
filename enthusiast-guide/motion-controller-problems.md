---
title: Preguntas más frecuentes sobre el controlador de movimiento
description: Los Windows Mixed Reality solución de problemas que van más allá de la documentación de soporte técnico para consumidores estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Motion controllers
appliesto:
- Windows 10
ms.openlocfilehash: e477ed07e20fb06e270c9a6e13e20defecfc6328896983ed12c4b79ea2197e44
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219773"
---
# <a name="motion-controller-faqs"></a>Preguntas más frecuentes sobre el controlador de movimiento

## <a name="what-do-the-vibrations-and-lights-mean"></a>¿Qué significan las vibraciones y las luces?

El anillo y los hápticos led indican el estado del controlador de movimiento.

| Estado    | Comportamiento asociado al estado | Cómo obtener o salir del estado |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Encendido**               | Los LED se encienden y el controlador se activa una vez. | Mantenga presionado el botón Windows en el controlador durante dos segundos para activar el controlador.  |
| **Apagado**              |  Los LED se apagan y el controlador se vibración dos veces. | Mantenga presionado el botón Windows en el controlador durante cuatro segundos para desactivar el controlador.   |
| **Dormir**               |  Los LED se apagan y parpadean cada tres segundos mientras están en estado de apagado. | El controlador entra automáticamente en estado de inmóvil durante 30 segundos. El controlador se reactiva cuando detecta movimiento, excepto si el dispositivo no está emparejado con el equipo host. Presione el botón para reactivar en ese caso. |
| **Emparejamiento**                |  Los LED pulsan lentamente mientras están en modo de emparejamiento y se mantienen sólidos al salir del modo de emparejamiento. El controlador se vibración una vez si el emparejamiento se ha realizado correctamente o tres veces si el emparejamiento no se realiza correctamente y, a continuación, se ha completado el tiempo de espera. | Mantenga presionado el botón de emparejamiento dentro de la caja de la batería durante tres segundos.     |
| **El controlador se conecta o se desconecta del equipo** |  El controlador se vibración una vez en la conexión o desconexión del equipo. | Se produce cuando el controlador se conecta correctamente al equipo después de activarlo, o si el controlador se desconecta del equipo durante el uso.|
| **Bajo nivel de batería**      | Los hápticos se deshabilitan cuando la batería está baja (no hay ninguna indicación de LED). El icono del indicador de batería en el controlador del casco mostrará 1/4 lleno cuando la batería esté baja. | Reemplace las baterías. | 
| **Nivel de batería crítico** |  El controlador se vibración tres veces cuando se activa y, a continuación, se desactiva automáticamente. El icono del indicador de batería se volverá rojo. | Reemplace las baterías. Si el problema persiste, [restaure el dispositivo a su configuración de fábrica.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>Mis controladores de movimiento no funcionan correctamente

Si los [controladores de](controllers-in-wmr.md) movimiento no funcionan, se conectan o muestran una imagen de los controladores cuando se lleva el casco:

1. Asegúrese de que los controladores están activados. Para activarlos, mantenga presionado el botón de Windows durante dos segundos.
2. Asegúrese de que los controladores están totalmente cargados y reemplace las baterías si no lo están.
3. Desactive y vuelva a activar los controladores mientras los mantiene delante de usted. Mantenga presionado el botón Windows durante cuatro segundos para desactivar un controlador. Mantenga presionado de nuevo durante dos segundos para activarlo.
4. Compruebe si los controladores de movimiento [están emparejados correctamente.](controllers-in-wmr.md#pair-motion-controllers)
5. Compruebe los LED de los controladores de movimiento: los controladores con iluminación brillante están emparejados y conectados, los controladores con iluminación tenue no están conectados.
6. Vaya a **Inicio > Portal de realidad mixta** en el equipo y seleccione "Menú". Debería ver los controladores de movimiento en la lista, junto con un mensaje de estado:
    * Listo: todos los controladores están establecidos.
    * Seguimiento perdido: Portal de realidad mixta no puede encontrar los controladores. Sostejelos delante del casco y reinícielos presionando el botón de Windows durante cuatro segundos y, a continuación, de nuevo durante dos segundos.
    * Batería baja: reemplace las baterías del controlador.
7. Si usa un adaptador de Bluetooth USB externo, asegúrese de que está conectado a un puerto USB 2.0 (a menudo, pero no siempre es negro). También debe conectarse lo más lejos posible desde cualquier otro transmisor inalámbrico o unidades flash USB, incluido el conector USB para el casco. 
8. Vaya a **Administrador de dispositivos > Bluetooth** y busque un adaptador para comprobar que solo hay un Bluetooth radio en el equipo. Si usa la configuración del equipo de escritorio con radio integrada, compruebe si hay una antena externa conectada. Si no hay ninguna antena externa conectada, puede causar problemas de seguimiento. O bien, use un Bluetooth externo (USB), deshabilite la funcionalidad Bluetooth interna y vuelva a intentar el emparejamiento y la conexión.
9. Si la Bluetooth de configuración está abierta en segundo plano, se realizan muchas llamadas adicionales al Bluetooth protocolo. Ciérrelo.
10. Compruebe el nivel de batería virtual en el controlador de movimiento girando los controladores en realidad mixta para ver el icono de batería. Espere unos 15 segundos antes de leer el nivel, ya que el nivel notificado es superior al nivel real inmediatamente después de conectar un controlador. Reemplace las baterías si el icono es rojo.
11. Quite Bluetooth y altavoces de **Configuración > Dispositivos**> Bluetooth & otros dispositivos y desactive los dispositivos. Use el conector o los altavoces integrados del casco de realidad mixta para obtener la mejor experiencia de audio.
12. Quite otros Bluetooth dispositivos que se pueden emparejar con el equipo, como cascos o mandos de juegos. Vaya a **Configuración > Dispositivos > Bluetooth & otros** dispositivos, seleccione los dispositivos y, a continuación, "Quitar dispositivo".
13. Desconecte el cable USB del casco y vuelva a conectarlo al equipo para reiniciar Windows Mixed Reality.
14. Las luces del controlador parpadean cuando se someten a una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en Mixed Reality.
15. Asegúrese de que el equipo está conectado a una red de 5 GHz Wi-Fi red. Si el portátil está conectado a una red de Wi-Fi de 2,4 GHz, normalmente comparte la Bluetooth conexión. Esto puede afectar negativamente al rendimiento Wi-Fi o Bluetooth, en función del diseño del producto. Cambie la banda preferida a 5 GHz en la configuración del adaptador de red. Si la red no admite 5 GHz, se puede usar Bluetooth dongle en lugar de la funcionalidad de Bluetooth interna.
16. Si la Bluetooth de movimiento ya tiene controladores de movimiento emparejados, Windows detectará los nuevos dispositivos hasta que se quiten. Si se han agregado mediante un dongle específico, solo se pueden quitar con ese dongle.
17. Si el equipo tiene una conexión Bluetooth y tiene problemas de conexión, pruebe a usar un adaptador de Bluetooth USB. Para ello, desactive la radio integrada Bluetooth en Administrador de dispositivos y, a continuación, emparere los demás dispositivos Bluetooth con el nuevo adaptador.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Mis controladores parpadean, se atascan o parpadean y desaparecen en realidad mixta

* Si el equipo se ejecuta en Wi-Fi de 2,4 GHz, cambie a Wi-Fi de 5 GHz. 
* Si usa un adaptador Bluetooth externo, asegúrese de que está conectado a un puerto USB 2.0 (que a menudo es negro, pero no siempre), lejos de otros transmisores inalámbricos o unidades flash USB.
* Ejecute el solucionador Bluetooth solución de problemas **en Configuración > Update & Security > Solución de problemas > Bluetooth**.

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Mi controlador está bloqueado en un reinicio infinito

Se trata de un indicador de batería crítico. Coloque baterías nuevas en el dispositivo y, si el problema persiste, [restablezca el controlador a la configuración de fábrica.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>La Portal de realidad mixta está funcionando, pero mis controladores están siguiendo un seguimiento deficiente (vuelo fuera, saludando, etc.).

1. Las condiciones de iluminación pueden afectar al seguimiento. Asegúrese de que no está expuesto a luz directa y que tiene fuentes de luz de punto mínimo visibles para su HMD (por ejemplo, cadenas de luces como un árbol de noche).
2. Estos síntomas se deben a errores en la comunicación entre el controlador y el equipo host, e indican una calidad Bluetooth de vínculo. Vea [las preguntas sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Los LED del controlador de movimiento no están encendidos, pero los botones y la chincheta siguen funcionando en Portal de realidad mixta

La memoria caché de calibración del controlador de movimiento puede estar dañada. Para eliminar la memoria caché, ejecute el siguiente comando en un símbolo del sistema del administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Esta carpeta no es accesible en Windows Explorer y solo se puede modificar desde un símbolo del sistema del administrador. Después de eliminar la carpeta, reinicie el equipo y vuelva a conectar los controladores de movimiento para restaurar los archivos de calibración.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Mi controlador parece un Vive/Oculus, tiene una orientación extraña o los botones están asignados incorrectamente.

Es probable que el sitio web no tenga compatibilidad completa con el controlador de movimiento.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Mis controladores de movimiento no aparecen en aplicaciones y juegos de SteamVR

En primer lugar, asegúrese de que se cobran las baterías del controlador. Los controladores no funcionarán si las baterías están fallecidas o están agotadas.

Si puede ver los controladores en el Casa sobre el acantilado pero no en aplicaciones y juegos de SteamVR, es posible que el controlador de modelo del controlador de movimiento no esté instalado correctamente. Para comprobar que el controlador de modelo del controlador de movimiento está instalado correctamente:

1. Active ambos controladores de movimiento. Compruebe si los controladores de movimiento están [emparejados correctamente.](controllers-in-wmr.md#pair-motion-controllers)
2. Vaya a **Administrador de dispositivos > dispositivos de interfaz humana** y busque "Controlador de movimiento".
3. Haga doble clic en cada dispositivo "Controlador de movimiento" y vaya a la pestaña "Controlador". Confirme que la versión del controlador enumerada corresponde a una de [estas versiones.](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)
4. Si la versión del controlador no coincide o no encuentra un dispositivo denominado "Controlador de movimiento", ejecute Windows Actualización.  Esto descargará e instalará automáticamente el controlador. Si está en un equipo que tiene directivas empresariales o si la actualización de Windows está restringida de otro modo, es posible que tenga que instalar manualmente el controlador de modelo del controlador de movimiento. Para ello, visite [esta página y](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) busque la versión del controlador correspondiente al hardware del controlador. Las instrucciones de instalación están disponibles en la página de descarga.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>La actualización del firmware del controlador tarda más de dos minutos.

Consulte la [sección Bluetooth preguntas.](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) Normalmente, Bluetooth calidad de los vínculos deficientes provoca estos problemas.

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>He insertado baterías nuevas, pero el nivel de batería virtual del controlador no indica el nivel completo

El nivel de batería del controlador de movimiento está optimizado para baterías AA. Es posible que algunas baterías de baja tensión no se informen como llenas, aunque están totalmente cargadas.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>El panel táctil del controlador de movimiento de Samsung está fuera del centro o tiene un punto de inmóvil

Probablemente se trata de un defecto de hardware y debe volver a su distribuidor o fabricante de equipos para un reemplazo o intercambio.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Cómo se pueden restaurar los controladores a la configuración de fábrica

Restáurelo a las condiciones de fábrica (necesitará baterías nuevas):

1. Desconecte y apague los controladores.
2. Abra la cubierta de la batería.
3. Inserte las baterías nuevas.
4. Mantenga presionado el botón de emparejamiento (la pestaña de la parte inferior debajo de las baterías).
5. Mientras mantiene presionado el botón de emparejamiento, encienda el controlador presionando y manteniendo presionado el botón Windows durante cinco segundos (mantenga ambos botones presionados).
6. Suelte los botones y espere a que el controlador se encienda. Esto tarda hasta 15 segundos y no hay indicadores de cuándo se está produciendo la recuperación del dispositivo. Si el dispositivo se enciende inmediatamente en el lanzamiento del botón, la secuencia del botón de recuperación no se registró y debe intentarlo de nuevo.
7. Si los controladores se emparejaron con el equipo, vaya Configuración > Bluetooth > otros dispositivos **y** seleccione "Controlador de movimiento" y "Quitar dispositivo" para quitar las asociaciones de controlador de Bluetooth configuración.
8. [Vuelva a emparejar los controladores](controllers-in-wmr.md#pair-motion-controllers) con el casco o el equipo.
9. Después de conectarse con el host y el casco, el dispositivo se actualizará al firmware disponible más reciente.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>¿Puedo emparejar el controlador de Xbox con mi PC para poder usarlo en el casco?

Para emparejar un Bluetooth Xbox para usarlo con el casco, siga [estas instrucciones.](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)

Si tiene un controlador xbox cableado, conéctelo al equipo.

Algunos juegos y aplicaciones usan el controlador de Xbox de forma diferente a como se usa en la realidad mixta. Para usar el controlador para un juego o una aplicación, seleccione "Usar como controlador para juegos" en la barra de la aplicación o diga "Usar como controlador para juegos". Para volver a cambiar el controlador a la realidad mixta, vuelva a seleccionar "Usar como controlador para juegos" o diga "Usar con mirada". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Cómo emparejar nuevos controladores si Windows Mixed Reality ya está configurado en mi PC

Si va a emparejar los controladores con el [](install-windows-mixed-reality.md#launch-mixed-reality-portal) casco, use la aplicación complementaria (el Portal de realidad mixta puede ayudarle a encontrar una aplicación complementaria para iniciarla o proporcionar una lista de aplicaciones complementarias entre las que puede seleccionar).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>¿Cómo puedo devolver mis controladores a su emparejamiento de fábrica?

Para devolver los controladores de movimiento a su emparejamiento de fábrica o emparejarlos con un casco Windows Mixed Reality con radio Bluetooth integrada, ejecute la aplicación complementaria del dispositivo del casco y siga las instrucciones para el emparejamiento del controlador de movimiento. Por ejemplo, la aplicación "Acer OJO 500" o la aplicación "Samsung HMD Ctrl+ Setup" se instalan automáticamente la primera vez que se conecta el casco.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>Mis controladores de movimiento no se emparejan con mi PC

* Si los controladores no se encienden, inserte baterías nuevas. Si esto no lo corrige, restaure el dispositivo a su configuración de fábrica; para ello, encienda el dispositivo mientras mantiene presionados los botones de emparejamiento. Para más información, consulte los pasos de [recuperación del dispositivo.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)
* Si los controladores se encienden mientras se usa un adaptador Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2.0 (que a menudo es negro, pero no siempre), lejos de otros transmisores inalámbricos o unidades flash USB. Si sigue sin funcionar, ejecute el solucionador de problemas de Bluetooth en Configuración > Update & Security > Troubleshoot > Bluetooth.
* Si usa un adaptador qualcomm y el equipo se acaba de bloquear, reinicie el equipo.
* Intente reiniciar los controladores de movimiento que no están emparejando, de uno en uno, y reinicie el equipo.
* La memoria caché del controlador de movimiento puede estar dañada. Para corregir este problema, consulte estos [pasos.](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)
* Si los pasos corrigen el problema, debe ponerse en contacto con el fabricante.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mis controladores emparejados no se muestran en el Portal de realidad mixta

* Mantenga los controladores delante del casco y reinícielos presionando el botón de Windows durante cuatro segundos y, después, de nuevo durante dos segundos.
* Si los controladores se muestran como conectados, desenlazándolos y vuelva a pasar por el [proceso de](controllers-in-wmr.md#pair-motion-controllers) emparejamiento.
* Si los LED del controlador están en bicicleta con un cuadrante de luces que se encienden y apagan a la vez, se están sometiendo a una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en Mixed Reality.
* Si se usa un adaptador Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2.0 (que es negro), lejos de otros transmisores inalámbricos o dispositivos USB 3.0.
* Si el equipo se acaba de bloquear y se usa un adaptador Qualcomm, es posible que un restablecimiento no funcione. Para solucionar este problema, desconecte la alimentación de la parte posterior del equipo (o si está en un portátil, mantenga presionado el botón de encendido durante 10 segundos) y reinicie el equipo.
* Ejecute el solucionador Bluetooth solución de problemas en **Configuración > Update & Security > Troubleshoot > Bluetooth**.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Estoy intentando emparejar mis controladores, pero nunca se muestran en el menú "Agregar un nuevo dispositivo" en Bluetooth configuración.

Compruebe que aún no tiene controladores emparejados. Si lo hace, quítelos e inténtelo de nuevo. Reinicie el equipo si el problema persiste. Si se produce un error, vea más [información sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Nota: Si otro conjunto de controladores de movimiento está emparejado con el equipo, deberá desasocuir esos controladores antes de emparejar los nuevos. Si ha emparejado un conjunto de controladores de movimiento con el equipo actual y, a continuación, los ha emparejado con un segundo equipo, deberá desenlazarlos y volver a emparejarlos con el equipo actual antes de volver a usarlos.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>¿Cómo puedo saber si estoy usando Bluetooth tecnología?

Los controladores de movimiento usan la misma Bluetooth que se encuentra en muchos dispositivos de consumidor y están diseñados para funcionar con la funcionalidad Bluetooth incluida en cualquier equipo reciente. El equipo debe tener Bluetooth radio si ha superado la comprobación de compatibilidad de realidad mixta. Para comprobarlo:

* Abra "Administrador de dispositivos".
* Expanda la Bluetooth y busque un adaptador.

![Captura de pantalla de un ejemplo Administrador de dispositivos. El adaptador es la Bluetooth radio.](images/devicemanagerbtadapterpic.png)

Si el equipo no tiene conexión Bluetooth, use El microaceptador USB Bluetooth 4.0 de baja energía.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi se ralentiza en mi cuaderno cuando los controladores de movimiento están activados

El cuaderno puede compartir su Wi-Fi con Bluetooth cuando se conecta a un punto de acceso de 2,4 GHz. Compruebe Administrador de dispositivos si puede cambiar la preferencia de banda a 5 GHz. Si una red de 5 GHz no está disponible y el rendimiento se ve gravemente afectado, considere la posibilidad de usar un Bluetooth dongle.

![La configuración de selección de banda Wifi se puede encontrar a través del administrador de dispositivos.](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers&quot;></a>Mi PC tiene Bluetooth tecnología, pero tengo problemas con los controladores

Los controladores de movimiento deben funcionar con otros Bluetooth teclados, mouse y controladores de juegos. La experiencia variará en función del modelo de teclado, mouse o controlador de juego que use. Estas son algunas de las cosas que puede hacer para mejorar el rendimiento:

* Si el equipo tiene Bluetooth pero sigue teniendo problemas con los controladores de movimiento, considere la posibilidad de reemplazar la radio Bluetooth por un adaptador de Bluetooth externo conectable conectado a USB. Solo puede tener un adaptador Bluetooth radio activo a la vez. Si conecta una radio externa junto con una radio existente, debe deshabilitar la radio de Bluetooth existente en Administrador de dispositivos. Haga clic con el botón derecho en el adaptador y seleccione &quot;Deshabilitar dispositivo&quot; y desapareque o vuelva a emparejar todos los dispositivos Bluetooth anteriores.
* Si usa un adaptador usb Bluetooth, conéctelo a un puerto USB 2.0 (los puertos 2.0 suelen ser negros y no tienen la etiqueta &quot;SS"), si están disponibles. El puerto debe estar separado físicamente de:
    - conector USB HMD
    - unidades flash
    - unidades de disco duro
    - Receptores USB inalámbricos como los de teclados o mouse Idealmente, conecte el adaptador usb Bluetooth en el lado opuesto del equipo en la medida de lo posible desde estos otros conectores.
* Cierre la Bluetooth de configuración si está abierta. Dejarlo abierto en segundo plano significa que se realizan muchas llamadas adicionales al Bluetooth protocolo.
* Si el casco está emparejado con el equipo, use la pila de controladores Windows Bluetooth y no instale ninguna pila de controladores de Bluetooth de terceros. Es posible que el software de terceros no funcione correctamente.
* Deshabilite la opción "Mostrar notificación para conectarse mediante el par Swift" en "Bluetooth & otros dispositivos" para reducir la actividad de examen de radio del host.
* Si usa una tarjeta de Bluetooth interna, asegúrese de que usa una antena de Bluetooth externa o que puede experimentar problemas de seguimiento. Si esto no funciona, use una conexión externa Bluetooth (USB) después de deshabilitar el Bluetooth.
* El dispositivo debe aparecer en la categoría "Mouse, Keyboard & Pen" en la Bluetooth configuración. Si está en "Otros dispositivos", desenlaze y emparere el dispositivo.
* Quite, desasoyéctese y apague Bluetooth y altavoces. No se admiten con Windows Mixed Reality. Use el conector o los altavoces integrados del casco Mixed Reality para obtener la mejor experiencia de audio.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Mi segundo controlador tarda mucho tiempo en volver a conectarse

Algunas radios intel anteriores experimentan este problema si los controladores de movimiento están encendidos al mismo tiempo. Evite encender los controladores al mismo tiempo.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>My Qualcomm Bluetooth radio cannot pair controllers after a PC crash

Qualcomm (QCA) Bluetooth controladores de radio anteriores a 10.0.0.448 pueden acabar en mal estado después de un Windows bloqueo. Apague completamente el equipo para solucionar este problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Estoy experimentando un seguimiento deficiente del controlador con la radio de Marvell

Vaya Administrador de dispositivos > Bluetooth > controlador > properties > Del adaptador de > radio de **Marvell BLUETOOTH y** asegúrese de que usa el controlador 15.68.9210.47 o posterior.
