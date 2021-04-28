---
title: Preguntas más frecuentes sobre el controlador de movimiento
description: Los Windows Mixed Reality solución de problemas que van más allá de nuestra documentación estándar de soporte técnico al consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Motion controllers
appliesto:
- Windows 10
ms.openlocfilehash: cf45794d5c5c6c790578e76be4b222d851b5a73c
ms.sourcegitcommit: 229c33afab7c70341982f48962028aad13956356
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2021
ms.locfileid: "108069199"
---
# <a name="motion-controller-faqs"></a>Preguntas más frecuentes sobre el controlador de movimiento

## <a name="what-do-the-vibrations-and-lights-mean"></a>¿Qué significan las vibración y las luces?

El anillo y los hápticos led indican el estado del controlador de movimiento.

| Estado    | Comportamiento asociado al estado | Cómo obtener o salir del estado |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Encendido**               | Los LED se encienden y el controlador se vibración una vez. | Mantenga presionado el botón de Windows en el controlador durante dos segundos para activar el controlador.  |
| **Apagado**              |  Los LED se apagan y el controlador se vibración dos veces. | Mantenga presionado el botón de Windows en el controlador durante cuatro segundos para desactivar el controlador.   |
| **Dormir**               |  Los LED se apagan y parpadean cada tres segundos mientras están en estado de apagado. | El controlador entra automáticamente en estado de inmoción durante 30 segundos. El controlador se reactiva cuando detecta movimiento, excepto si el dispositivo no está emparejado con el equipo host. Presione el botón para activarlo en ese caso. |
| **Emparejamiento**                |  Los LED pulsan lentamente mientras están en modo de emparejamiento y se mantienen sólidos al salir del modo de emparejamiento. El controlador se vibración una vez si el emparejamiento se ha realizado correctamente o tres veces si el emparejamiento no se realiza correctamente y, a continuación, se ha completado el tiempo de espera. | Mantenga presionado el botón de emparejamiento dentro de la caja de la batería durante tres segundos.     |
| **El controlador se conecta o se desconecta del equipo** |  El controlador se vibración una vez en la conexión o desconexión del equipo. | Se produce cuando el controlador se conecta correctamente al equipo después de activarlo, o si el controlador se desconecta del equipo durante el uso.|
| **Bajo nivel de batería**      | Los hápticos se deshabilitan cuando la batería está baja (no hay ninguna indicación de LED). El icono del indicador de batería en el controlador del casco mostrará 1/4 lleno cuando la batería esté baja. | Reemplace las baterías. | 
| **Nivel de batería crítico** |  El controlador se vibre tres veces cuando se activa y, a continuación, se desactiva automáticamente. El icono del indicador de batería se volverá rojo. | Reemplace las baterías. Si el problema persiste, [restaure el dispositivo a su configuración de fábrica.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>Mis controladores de movimiento no funcionan correctamente

Si los [controladores de](controllers-in-wmr.md) movimiento no funcionan, se conectan o muestran una imagen de los controladores cuando se lleva el casco:

1. Asegúrese de que los controladores están activados. Para activarlos, mantenga presionado el botón De Windows durante dos segundos.
2. Asegúrese de que los controladores están totalmente cargados y reemplace las baterías si no lo están.
3. Desactive y vuelva a activar los controladores mientras los mantiene delante de usted. Mantenga presionado el botón de Windows durante cuatro segundos para desactivar un controlador. Mantenga presionado de nuevo durante dos segundos para activarlo.
4. Compruebe si los controladores de movimiento [están emparejados correctamente.](controllers-in-wmr.md#pair-motion-controllers)
5. Compruebe los LED de los controladores de movimiento: los controladores con iluminación brillante están emparejados y conectados, los controladores con luz tenue no están conectados.
6. Vaya a **Inicio > Portal de realidad mixta** en el equipo y seleccione "Menú". Debería ver los controladores de movimiento en la lista, junto con un mensaje de estado:
    * Listo: todos los controladores están establecidos.
    * Seguimiento perdido: Portal de realidad mixta no puede encontrar los controladores. Manténlos delante del casco y reinícielos presionando el botón de Windows durante cuatro segundos y, después, de nuevo durante dos segundos.
    * Batería baja: reemplace las baterías del controlador.
7. Si usa un adaptador bluetooth USB externo, asegúrese de que está conectado a un puerto USB 2.0 (a menudo, pero no siempre es negro). También debe conectarse lo más posible desde cualquier otro transmisor inalámbrico o unidades flash USB, incluido el conector USB para el casco. 
8. Vaya a **Administrador de dispositivos > Bluetooth** y busque un adaptador para comprobar que solo hay una radio Bluetooth en el equipo. Si usa la configuración del equipo de escritorio con radio integrada, compruebe si hay una antena externa conectada. Si no hay ninguna antena externa conectada, puede causar problemas de seguimiento. O bien, use un dongle Bluetooth (USB) externo, deshabilite la funcionalidad bluetooth interna y vuelva a intentar el emparejamiento y la conexión.
9. Si la ventana de configuración de Bluetooth está abierta en segundo plano, se realizan muchas llamadas adicionales al protocolo Bluetooth. Ciérrelo.
10. Compruebe el nivel de batería virtual en el controlador de movimiento girando los controladores en realidad mixta para ver el icono de batería. Espere unos 15 segundos antes de leer el nivel, ya que el nivel notificado es mayor que el nivel real inmediatamente después de conectar un controlador. Reemplace las baterías si el icono está rojo.
11. Quite los altavoces y auriculares Bluetooth en Configuración **> dispositivos > Bluetooth &** otros dispositivos y apague los dispositivos. Use el conector o los altavoces integrados del casco de realidad mixta para obtener la mejor experiencia de audio.
12. Quite otros dispositivos Bluetooth que se puedan emparejar con el equipo, como cascos o mandos de juegos. Vaya a **Configuración > dispositivos > Bluetooth & otros** dispositivos, seleccione los dispositivos y, a continuación, "Quitar dispositivo".
13. Desconecte el cable USB del casco y vuelva a conectarlo al equipo para reiniciar Windows Mixed Reality.
14. Las luces del controlador parpadean cuando se someten a una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en Mixed Reality.
15. Asegúrese de que el equipo está conectado a una red de 5 GHz Wi-Fi red. Si el portátil está conectado a una red de 2,4 GHz Wi-Fi, normalmente comparte la conexión Bluetooth. Esto puede afectar negativamente al rendimiento Wi-Fi o Bluetooth, en función del diseño del producto. Cambie la banda preferida a 5 GHz en la configuración del adaptador de red. Si la red no admite 5 GHz, se puede usar un dongle Bluetooth en lugar de la funcionalidad bluetooth interna.
16. Si la configuración de Bluetooth tiene controladores de movimiento ya emparejados, Windows no detectará los nuevos dispositivos hasta que se quiten. Si se han agregado mediante un dongle específico, solo se pueden quitar con ese dongle.
17. Si el equipo tiene Bluetooth integrado y tiene problemas de conexión, pruebe a usar un adaptador Bluetooth USB. Para ello, desactive la radio Bluetooth integrada en Administrador de dispositivos y, a continuación, emparere los demás dispositivos Bluetooth con el nuevo adaptador.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Mis controladores parpadean, se atascan o parpadean y desaparecen en realidad mixta

* Si el equipo se ejecuta en Wi-Fi de 2,4 GHz, cambie a Wi-Fi de 5 GHz. 
* Si usa un adaptador Bluetooth externo, asegúrese de que está conectado a un puerto USB 2.0 (que a menudo es negro, pero no siempre), lejos de otros transmisores inalámbricos o unidades flash USB.
* Ejecute el solucionador de problemas de Bluetooth en **Configuración > actualización & seguridad > solución de problemas > Bluetooth.**

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Mi controlador está bloqueado en un reinicio infinito

Se trata de un indicador de batería crítico. Coloque baterías nuevas en el dispositivo y, si el problema persiste, [restablezca](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)el controlador a la configuración de fábrica .

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>La Portal de realidad mixta está funcionando, pero mis controladores están siguiendo un seguimiento deficiente (vuelo fuera, desfilando, etc.).

1. Las condiciones de iluminación pueden afectar al seguimiento. Asegúrese de que no está expuesto a la iluminación directa y que tiene fuentes de luz de punto mínimo visibles para el HMD (por ejemplo, cadenas de luces como un árbol de árbol).
2. Estos síntomas se deben a errores en la comunicación entre el controlador y el equipo host, e indican una calidad de vínculo Bluetooth deficiente. Consulte [las preguntas sobre Bluetooth.](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Los LED del controlador de movimiento no están encendidos, pero los botones y la chincheta siguen funcionando en Portal de realidad mixta

La memoria caché de calibración del controlador de movimiento puede estar dañada. Para eliminar la memoria caché, ejecute el siguiente comando en un símbolo del sistema del administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Esta carpeta no es accesible en Explorador de Windows solo se puede modificar desde un símbolo del sistema de administrador. Después de eliminar la carpeta, reinicie el equipo y vuelva a conectar los controladores de movimiento para restaurar los archivos de calibración.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Mi controlador parece un Vive/Oculus, tiene una orientación extraño o los botones están asignados incorrectamente.

Es probable que el sitio web no tenga compatibilidad completa con el controlador de movimiento.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Mis controladores de movimiento no aparecen en aplicaciones y juegos de SteamVR

En primer lugar, asegúrese de que se cobran las baterías del controlador. Los controladores no funcionarán si las baterías están agotadas o no funcionan

Si puede ver los controladores en el Casa sobre el acantilado pero no en aplicaciones y juegos de SteamVR, es posible que el controlador de modelo del controlador de movimiento no esté instalado correctamente. Para comprobar que el controlador de modelo del controlador de movimiento está instalado correctamente:

1. Active los dos controladores de movimiento. Compruebe si los controladores de movimiento [están emparejados correctamente.](controllers-in-wmr.md#pair-motion-controllers)
2. Vaya a **Administrador de dispositivos > dispositivos de interfaz humana** y busque "Controlador de movimiento".
3. Haga doble clic en cada dispositivo "Controlador de movimiento" y vaya a la pestaña "Controlador". Confirme que la versión del controlador enumerada corresponde a una de [estas versiones.](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)
4. Si la versión del controlador no coincide o no encuentra un dispositivo denominado "Controlador de movimiento", ejecute Windows Update.  Esto descargará e instalará automáticamente el controlador. Si está en un equipo que tiene directivas empresariales o si Windows Update está restringido de otro modo, es posible que tenga que instalar manualmente el controlador de modelo del controlador de movimiento. Para ello, visite [esta página y](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) busque la versión del controlador correspondiente al hardware del controlador. Las instrucciones de instalación están disponibles en la página de descarga.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>La actualización del firmware del controlador tarda más de dos minutos.

Consulte la [sección Preguntas de Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Una calidad de vínculo Bluetooth deficiente suele provocar estos problemas.

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
5. Mientras mantiene presionado el botón de emparejamiento, encienda el controlador presionando y manteniendo presionado el botón de Windows durante cinco segundos (mantenga ambos botones presionados).
6. Suelte los botones y espere a que el controlador se encienda. Esto tarda hasta 15 segundos y no hay indicadores de cuándo se produce la recuperación del dispositivo. Si el dispositivo se enciende inmediatamente al liberar el botón, la secuencia del botón de recuperación no se registró y debe intentarlo de nuevo.
7. Si los controladores se emparejaron con el equipo, vaya a Configuración **> Bluetooth >** otros dispositivos y seleccione "Controlador de movimiento" y "Quitar dispositivo" para quitar las asociaciones de controlador de la configuración de Bluetooth.
8. [Vuelva a emparejar los](controllers-in-wmr.md#pair-motion-controllers) controladores con el casco o el equipo.
9. Después de conectarse con el host y el casco, el dispositivo se actualizará al firmware más reciente disponible.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>¿Puedo emparejar mi controlador Xbox con mi PC para poder usarlo en el casco?

Puede emparejar un controlador Bluetooth de Xbox para usarlo con el casco siguiendo [estas instrucciones.](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)

Si tiene un controlador Xbox cableado, conéctelo al equipo.

Algunos juegos y aplicaciones usan el controlador de Xbox de forma diferente a como se usa en la realidad mixta. Para usar el controlador para un juego o una aplicación, seleccione "Usar como controlador para juegos" en la barra de la aplicación o diga "Usar como controlador para juegos". Para volver a cambiar el controlador a la realidad mixta, vuelva a seleccionar "Usar como controlador para juegos" o diga "Usar con mirada". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Cómo nuevos controladores si Windows Mixed Reality ya está configurado en mi PC

Si va a emparejar los controladores con el [](install-windows-mixed-reality.md#launch-mixed-reality-portal) casco, use la aplicación complementaria (el Portal de realidad mixta puede ayudarle a encontrar una aplicación complementaria para iniciarla o proporcionar una lista de aplicaciones complementarias entre las que puede seleccionar).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>¿Cómo puedo devolver mis controladores a su emparejamiento de fábrica?

Para devolver los controladores de movimiento a su emparejamiento de fábrica o emparejarlos con un casco Windows Mixed Reality con radio Bluetooth integrado, ejecute la aplicación complementaria de dispositivo del casco y siga las instrucciones para el emparejamiento del controlador de movimiento. Por ejemplo, la aplicación "Acer OJO 500" o la aplicación "Samsung HMD Ctrl+ Setup" se instalan automáticamente la primera vez que se conecta el casco.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>Mis controladores de movimiento no se emparejan con mi PC

* Si los controladores no se encienden, inserte baterías nuevas. Si esto no lo corrige, restaure el dispositivo a su configuración de fábrica; para ello, encienda el dispositivo mientras mantiene presionados los botones de emparejamiento. Para más información, consulte los pasos de [recuperación del dispositivo.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)
* Si los controladores se encienden mientras se usa un adaptador Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2.0 (que a menudo es negro, pero no siempre), lejos de otros transmisores inalámbricos o unidades flash USB. Si sigue sin funcionar, ejecute el Solucionador de problemas de Bluetooth en Configuración > Actualización de & seguridad > solución de problemas > Bluetooth.
* Si usa un adaptador qualcomm y el equipo se acaba de bloquear, reinicie el equipo.
* Intente reiniciar los controladores de movimiento que no están emparejando, de uno en uno, y reinicie el equipo.
* La memoria caché del controlador de movimiento puede estar dañada. Para corregir este problema, consulte estos [pasos.](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)
* Si los pasos corrigen el problema, debe ponerse en contacto con el fabricante.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mis controladores emparejados no se muestran en el Portal de realidad mixta

* Mantenga los controladores delante del casco y reinícielos presionando el botón de Windows durante cuatro segundos y, después, de nuevo durante dos segundos.
* Si los controladores se muestran como conectados, desenlazándolos y vuelva a pasar por el [proceso de](controllers-in-wmr.md#pair-motion-controllers) emparejamiento.
* Si los LED del controlador están en bicicleta con un cuadrante de luces que se encienden y apagan a la vez, se están sometiendo a una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en Mixed Reality.
* Si se usa un adaptador Bluetooth externo, asegúrese de que está conectado a un puerto USB 2.0 (que es negro), lejos de otros transmisores inalámbricos o dispositivos USB 3.0.
* Si el equipo simplemente se bloquea y se usa un adaptador Qualcomm, es posible que un restablecimiento no funcione. Para solucionar este problema, desconecte la alimentación de la parte posterior del equipo (o, si está en un equipo portátil, mantenga presionado el botón de encendido durante 10 segundos) y reinicie el equipo.
* Ejecute el solucionador de problemas de Bluetooth en **Configuración > actualización & seguridad > solución de > Bluetooth**.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Estoy intentando emparejar mis controladores, pero nunca se muestran en el menú "Agregar un nuevo dispositivo" en la configuración de Bluetooth.

Compruebe que aún no tiene controladores emparejados. Si lo hace, quítelos e inténtelo de nuevo. Reinicie el equipo si el problema persiste. Si se produce un error, vea más [información sobre Bluetooth.](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)

Nota: Si otro conjunto de controladores de movimiento está emparejado con el equipo, tendrá que desaparpare esos controladores antes de emparejar los nuevos. Si ha emparejado un conjunto de controladores de movimiento con el equipo actual y, a continuación, los ha emparejado con un segundo equipo, deberá desenlazarlos y volver a emparejarlos con el equipo actual antes de volver a usarlos.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>¿Cómo puedo saber si uso la tecnología Bluetooth?

Los controladores de movimiento usan la misma tecnología Bluetooth que se encuentra en muchos dispositivos de consumidor y están diseñados para funcionar con la funcionalidad Bluetooth incluida en cualquier equipo reciente. El equipo debe tener radio Bluetooth si ha superado la comprobación de compatibilidad de realidad mixta. Para comprobarlo:

* Abra "Administrador de dispositivos".
* Expanda la sección Bluetooth y busque un adaptador.

![Captura de pantalla de un ejemplo Administrador de dispositivos. El adaptador es la radio Bluetooth.](images/devicemanagerbtadapterpic.png)

Si el equipo no tiene Bluetooth, use El microaceptador Bluetooth 4.0 de bajo consumo usb conectable.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi se ralentiza en el cuaderno cuando los controladores de movimiento están activados

El cuaderno puede compartir su Wi-Fi antena con Bluetooth cuando se conecta a un punto de acceso de 2,4 GHz. Compruebe Administrador de dispositivos si puede cambiar la preferencia de banda a 5 GHz. Si una red de 5 GHz no está disponible y el rendimiento se ve gravemente afectado, considere la posibilidad de usar un dongle Bluetooth.

![La configuración de selección de banda Wifi se puede encontrar a través del administrador de dispositivos.](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers&quot;></a>Mi PC tiene tecnología Bluetooth, pero tengo problemas con los controladores

Los controladores de movimiento deben funcionar con otros teclados Bluetooth, mouse y controladores de juegos. La experiencia variará en función del modelo de teclado, mouse o controlador de juego que use. Estas son algunas de las cosas que puede hacer para mejorar el rendimiento:

* Si el equipo tiene Bluetooth pero sigue teniendo problemas con los controladores de movimiento, considere la posibilidad de reemplazar la radio Bluetooth por un adaptador Bluetooth externo conectable conectado a USB. Solo puede tener un adaptador de radio Bluetooth activo a la vez. Si conecta una radio externa junto con una radio existente, debe deshabilitar la radio Bluetooth existente en Administrador de dispositivos. Haga clic con el botón derecho en el adaptador y seleccione &quot;Deshabilitar dispositivo&quot; y desapareque o vuelva a emparejar todos los dispositivos Bluetooth anteriores.
* Si usa un adaptador Bluetooth USB, conéctelo a un puerto USB 2.0 (los puertos 2.0 suelen ser negros y no tienen la etiqueta &quot;SS"), si están disponibles. El puerto debe estar separado físicamente de:
    - conector USB HMD
    - unidades flash
    - unidades de disco duro
    - Receptores USB inalámbricos como los de teclados o mouse Idealmente, conecte el adaptador Bluetooth USB en el lado opuesto del equipo en la medida de lo posible desde estos otros conectores.
* Cierre la ventana de configuración de Bluetooth si está abierta. Dejarlo abierto en segundo plano significa que se realizan muchas llamadas adicionales al protocolo Bluetooth.
* Si el casco está emparejado con el equipo, use la pila de controladores Bluetooth de Windows y no instale pilas de controladores Bluetooth de terceros. Es posible que el software de terceros no funcione correctamente.
* Deshabilite la opción "Mostrar notificación para conectarse mediante el par Swift" en "Bluetooth & otros dispositivos" para reducir la actividad de examen de radio del host.
* Si usa una tarjeta Bluetooth interna, asegúrese de que usa una antena Bluetooth externa o que puede experimentar problemas de seguimiento. Si esto no funciona, use un dongle Bluetooth (USB) externo después de deshabilitar el Bluetooth interno.
* El dispositivo debe aparecer en la categoría "Mouse, Keyboard & Pen" en la configuración de Bluetooth. Si está en "Otros dispositivos", desapare y emparere el dispositivo.
* Quite, quite y apague los altavoces y los auriculares Bluetooth. No se admiten con Windows Mixed Reality. Use el conector de casco o los altavoces integrados en el casco Mixed Reality para obtener la mejor experiencia de audio.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Mi segundo controlador tarda mucho tiempo en volver a conectarse

Algunas radios intel anteriores experimentan este problema si los controladores de movimiento están encendidos al mismo tiempo. Evite encender los controladores al mismo tiempo.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>La radio Qualcomm Bluetooth no puede emparejar controladores después de un bloqueo del equipo

Los controladores de radio Bluetooth Qualcomm (QCA) anteriores a 10.0.0.448 pueden acabar en mal estado después de un bloqueo de Windows. Apague completamente el equipo para solucionar este problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Estoy experimentando un seguimiento deficiente del controlador con radio de Marvell

Vaya **a Administrador de dispositivos > Bluetooth > Vgal VGAAR Bluetooth Radio Adapter > Properties > Driver** (Propiedades del > Driver) de Bluetooth y asegúrese de que usa el controlador 15.68.9210.47 o posterior.
