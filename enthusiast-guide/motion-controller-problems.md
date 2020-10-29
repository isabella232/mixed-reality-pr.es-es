---
title: Preguntas más frecuentes sobre el controlador de movimiento
description: Solución avanzada de problemas de realidad mixta de Windows que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, controladores de movimiento
appliesto:
- Windows 10
ms.openlocfilehash: 2a45f16cfbe62cb1263fcb1a1e7f5c76ea0b9268
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692495"
---
# <a name="motion-controller-faqs"></a>Preguntas más frecuentes sobre el controlador de movimiento

## <a name="general-questions"></a>Preguntas generales

### <a name="what-do-the-vibrations-and-lights-mean"></a>¿Qué significan las vibraciones y las luces?

El LED constelación ring y hápticos indican el estado del controlador de movimiento.

| State    | Comportamiento asociado al estado | Cómo obtener o salir del estado | 
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Encendido**               | Los LED se encienden y el controlador vibra una vez. | Mantenga presionado el botón de Windows en el controlador durante dos segundos para activar el controlador.  | 
| **Apagado**              |  Los LED se apagan y el controlador vibra dos veces. | Mantenga presionado el botón de Windows en el controlador durante cuatro segundos para desactivar el controlador.   |
| **En espera**               |  Los LED se apagan y parpadean cada tres segundos mientras están en estado de suspensión. | El controlador entra en el estado de inactividad automáticamente cuando se motionless durante 30 segundos. El controlador se activa cuando detecta movimiento, excepto si el dispositivo no está emparejado con el equipo host. Presione el botón para reactivarlo en ese caso. |
| **Emparejamiento**                |  Los LED se pulsan lentamente en el modo de emparejamiento y van sólidos al salir del modo de emparejamiento. El controlador vibra una vez si el emparejamiento fue correcto o tres veces si el emparejamiento no se realiza correctamente y, a continuación, se agota el tiempo de espera. | Mantenga presionado el botón de emparejamiento dentro de la batería durante tres segundos.     |
| **El controlador se conecta/desconecta del equipo** |  El controlador vibra una vez en la conexión o desconexión del equipo. | Esto sucede cuando el controlador se conecta correctamente al equipo después de encenderlo, o si el controlador se desconecta del equipo durante el uso.|
| **Nivel de batería baja**      | Los hápticos se deshabilitan cuando la batería es baja (no hay ninguna indicación LED). El icono del indicador de la batería del controlador de la controladora en auriculares mostrará 1/4 lleno cuando la batería esté baja. | Reemplace las baterías. | 
| **Nivel crítico de batería** |  El controlador vibra tres veces cuando se activa y se desactiva automáticamente. El icono del indicador de la batería se activará en rojo. | Reemplace las baterías. Si el problema persiste, [restaure el dispositivo a su configuración de fábrica](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) .|

### <a name="my-motion-controllers-arent-working-properly"></a>Mis controladores de movimiento no funcionan correctamente.

Si los [controladores de movimiento](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) no funcionan, no se está conectando o si no ve una imagen de los controladores cuando tiene el casco, intente lo siguiente:
1. Asegúrese de que los controladores estén encendidos. Para activarlas, mantenga presionado el botón de Windows durante dos segundos.
2. Asegúrese de que los controladores estén totalmente cargados y reemplace las baterías si no lo están.
3. Apague y encienda los controladores mientras los mantiene delante. Mantenga presionado el botón de Windows durante cuatro segundos para desactivar un controlador y, a continuación, mantenga presionado el botón en dos segundos para activarlo. 
4. Si los controladores se emparejan al equipo, vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** , o bien, si los controladores se emparejan con el casco, vaya a **Device Manager > dispositivos de interfaz de usuario > controlador de movimiento** . Asegúrese de que los controladores aparecen como emparejados. Si no es así, [empareje](motion-controller-problems.md#how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc). 
5. Asegúrese de que los controladores de movimiento aparecen como "conectados". "Emparejado" no significa necesariamente que los controladores estén conectados al equipo. Los controladores deben aparecer en la categoría "Mouse, teclado & el lápiz". Los controladores de movimiento en "otros dispositivos" no han superado el proceso de emparejamiento y no son funcionales. Comprobar los LED de los controladores de movimiento: los controladores iluminados brillantes están emparejados y conectados, los controladores dimly Lit no están conectados.
6. Vaya a **inicio > portal de realidad mixta** en su PC y seleccione "menú". Debería ver los controladores de movimiento enumerados, junto con un mensaje de estado:
    * Listo: todos los controladores están establecidos.
    * Seguimiento perdido: el portal de realidad mixta no puede encontrar los controladores. Manténgalos delante del casco y reinícielos presionando el botón Windows durante cuatro segundos y, luego, de nuevo durante dos segundos.
    * Batería baja: Reemplace las baterías del controlador.
7. Si utiliza un adaptador de Bluetooth USB externo, asegúrese de que está conectado a un puerto USB 2,0 (a menudo, pero no siempre es negro). También debe estar enchufado en la medida de lo posible desde cualquier otro transmisor inalámbrico o unidad flash USB, incluido el conector USB del casco. 
8. Para comprobar que solo hay un radio Bluetooth en el equipo, vaya a **Device Manager > Bluetooth** y busque un adaptador. Si usa la configuración de PC de escritorio con radio integrada, compruebe si hay una antena externa conectada. Si no hay ninguna antena externa conectada, puede causar problemas de seguimiento. O bien, use una llave de Bluetooth (USB) externa, deshabilite la funcionalidad de Bluetooth interna y reintente el emparejamiento y la conexión.
9. Si la ventana Configuración de Bluetooth está abierta en segundo plano, se realizan muchas llamadas adicionales al protocolo Bluetooth. Ciérrelo.
10. Compruebe el nivel de batería virtual en el controlador de movimiento. para ello, desactive los controladores en la realidad mixta para ver el icono de la batería. Espere unos 15 segundos antes de leer el nivel, ya que el nivel indicado es mayor que el nivel real inmediatamente después de conectar un controlador. Reemplace las baterías si el icono está en rojo. 
11. Quite los altavoces y auriculares Bluetooth de la **configuración > dispositivos > Bluetooth & otros dispositivos** y apague los dispositivos. Use el conector de auriculares o los altavoces integrados en los auriculares de la realidad mixta para disfrutar de la mejor experiencia de audio.
12. Quite otros dispositivos Bluetooth que se pueden emparejar con su PC, como los auriculares o los controladores de juegos. Vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** , seleccione los dispositivos y, a continuación, "quitar dispositivo".
13. Desconecte el cable USB del casco y conéctelo de nuevo al equipo para reiniciar Windows Mixed Reality.
14. Las luces del controlador parpadean cuando se están llevando a cabo una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en la realidad mixta.
15. Asegúrese de que su equipo está conectado a una red Wi-Fi de 5 GHz. Si el portátil está conectado a una red Wi-Fi de 2,4 GHz, normalmente comparte la conexión Bluetooth. Esto puede afectar negativamente al rendimiento de la red Wi-Fi o Bluetooth, en función del diseño del producto. Cambie la banda preferida a 5 GHz en la configuración del adaptador de red. Si la red no admite 5 GHz, se puede usar una llave Bluetooth en lugar de la capacidad interna de Bluetooth.
16. Si la configuración de Bluetooth tiene controladores de movimiento que ya están emparejados, Windows no detectará los nuevos dispositivos hasta que se quiten (si se han agregado con un dispositivo de protección específico, solo se pueden quitar con ese adaptador).
17. Si su equipo tiene Bluetooth integrado y tiene problemas de conexión, pruebe a usar un adaptador de Bluetooth USB. Para ello, desactive la radio Bluetooth integrada en Device Manager y, a continuación, empareje los demás dispositivos Bluetooth con el nuevo adaptador.

### <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Mis controladores vibran, se bloquean o parpadean y desaparecen en realidad mixta. 

* Si el equipo se ejecuta en una red Wi-Fi de 2,4 GHz, cambie a una red Wi-Fi de 5 GHz. 
* Si usa un adaptador Bluetooth externo, asegúrese de que está conectado a un puerto USB 2,0 (que suele ser, aunque no siempre, negro), de otros transmisores inalámbricos o de unidades flash USB. 
* Ejecute el solucionador de problemas de Bluetooth en **configuración > actualizar & seguridad > solucionar problemas de > Bluetooth** . 

### <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Mi controlador está atascado en un reinicio infinito.

Se trata de un indicador crítico de la batería. Coloque pilas nuevas en el dispositivo y, si el problema persiste, [restablezca la configuración de fábrica del controlador](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).

### <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>El portal de realidad mixta funciona, pero el seguimiento de los controladores es deficiente (volando, agitando, etc.).

1. Las condiciones de iluminación pueden afectar al seguimiento. Asegúrese de que no está expuesto a la luz solar directa y que no tiene una gran cantidad de fuentes de luz de punto visibles para su HMD (por ejemplo, cadenas de luces como un árbol de Navidad). 
2. Estos síntomas suelen deberse a errores de comunicación entre el controlador y el equipo host, e indican una calidad de vínculo de Bluetooth deficiente. Consulte [preguntas sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Los LED del controlador de movimiento no están encendidos, pero los botones y el stick analógico siguen funcionando en el portal de realidad mixta.

La memoria caché de calibración del controlador de movimiento puede estar dañada. Para eliminar la memoria caché, ejecute el siguiente comando en un símbolo del sistema de administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Esta carpeta no es accesible en el explorador de Windows y solo se puede modificar desde un símbolo del sistema de administrador. Después de eliminar la carpeta, reinicie el equipo y vuelva a conectar los controladores de movimiento para restaurar los archivos de calibración.

### <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Mi controlador es similar a un Naopak/Oculus, tiene una orientación extraña o los botones están asignados incorrectamente.

Es probable que el sitio web no tenga compatibilidad total con el controlador de movimiento.

### <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Mis controladores de movimiento no aparecen en aplicaciones y juegos de SteamVR.

En primer lugar, asegúrese de que se cobran las baterías del controlador. Los controladores no funcionarán si las baterías están muertas o Dying. 

Si puede ver los controladores en la casa de acantilado, pero no en SteamVR apps and Games, es posible que el controlador del modelo de controlador de movimiento no esté instalado correctamente. Para comprobar que el controlador del modelo de controlador de movimiento está instalado correctamente:
1. Active ambos controladores de movimiento. Si los controladores se emparejan al equipo, vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** , o bien, si los controladores se emparejan con el casco, vaya a **Device Manager > dispositivos de interfaz de usuario > controlador de movimiento** . Asegúrese de que se muestran como "conectados". Si no aparecen o no aparecen como "emparejadas", [empareje](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Vaya a **Device Manager > Bluetooth** y busque "controlador de movimiento".
3. Seleccione el dispositivo y, a continuación, vaya a **ver > dispositivos por conexión** .
4. Vaya a **configuración del sistema > dispositivos > Bluetooth & otros dispositivos > otros dispositivos** para ver si están visibles. Habrá dos dispositivos "dispositivo HID Bluetooth" y, en cada dispositivo HID Bluetooth, deben ser dispositivos denominados "controlador de movimiento" (con iconos grises) en el mismo nodo que el controlador de movimiento.
5. Haga doble clic en cada dispositivo de "controlador de movimiento" y vaya a la pestaña "controlador". Confirme que la versión de controlador indicada corresponde a una de [estas versiones](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history).
6. Si no es así, ejecute Windows Update, que descargará e instalará automáticamente el controlador. Si está en un equipo que tiene directivas de empresa o si Windows Update está restringido de otro modo, es posible que tenga que instalar manualmente el controlador del modelo de controlador de movimiento. Para ello, visite [esta página](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) y busque la versión del controlador correspondiente a su versión de Windows 10. Las instrucciones de instalación están disponibles en la página de descarga.

### <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>La actualización del firmware del controlador tarda bastante más de dos minutos.

Consulte la [sección preguntas sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Una calidad de vínculo Bluetooth deficiente suele provocar estos problemas.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Acabo de insertar baterías nuevas, pero el nivel de batería virtual del controlador no indica el nivel completo.

El nivel de batería del controlador de movimiento está optimizado para baterías AA. Es posible que algunas baterías recargables de baja tensión no informen como llenas, aunque estén totalmente cargadas.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>El panel táctil del controlador de movimiento de Samsung está fuera del centro o tiene una zona muerta.

Probablemente se trate de un defecto de hardware y debe volver al fabricante del distribuidor o equipo para reemplazarlo o cambiarlo.

### <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>¿Cómo puedo restaurar los controladores a la configuración de fábrica?

Restáurela en las condiciones de fábrica (necesitará baterías nuevas):
1. Desconecte y apague los controladores.
2. Abra la cubierta de la batería.
3. Inserte las nuevas baterías.
4. Mantenga presionado el botón de emparejamiento (la pestaña en la parte inferior de las baterías).
5. Mientras mantiene presionado el botón de emparejamiento, encienda el controlador presionando y manteniendo presionado el botón de Windows durante cinco segundos (mantenga presionados ambos botones).
6. Suelte los botones y espere a que el controlador se encienda. Esto tarda hasta 15 segundos y no hay ningún indicador cuando se está produciendo la recuperación del dispositivo. Si el dispositivo se enciende inmediatamente en el lanzamiento del botón, la secuencia del botón de recuperación no se registró y tendrá que intentarlo de nuevo.
7. Si los controladores se emparejaron al equipo, vaya a **configuración > Bluetooth > otros dispositivos** y seleccione "controlador de movimiento" y "quitar dispositivo" para quitar las asociaciones de controlador de la configuración de Bluetooth. 
8. [Empareje los controladores](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc) con el casco o el PC de nuevo.
9. Después de conectarse con el host y el casco, el dispositivo se actualizará al firmware disponible más reciente.

### <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>¿Puedo emparejar mi controlador Xbox a mi PC para poder usarlo con auriculares?

Puede emparejar un controlador Xbox de Bluetooth para usarlo con el casco siguiendo [estas instrucciones](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues). 

Si tiene un controlador Xbox con cable, conéctelo a su PC.

Algunos juegos y aplicaciones usan el controlador Xbox de forma distinta a como se usa en la realidad mixta. Para usar el controlador para un juego o una aplicación, selecciona "usar como controlador de juegos" en la barra de la aplicación o "usar como controlador de juegos". Para volver a activar el controlador a la realidad mixta, vuelva a seleccionar "usar como controlador de juegos" o "use con mirarme". 



## <a name="if-your-motion-controllers-are-paired-to-your-headset"></a>Si los controladores de movimiento se emparejan con los auriculares:

### <a name="should-i-pair-my-controllers-to-a-windows-mixed-reality-headset-that-has-built-in-bluetooth-radio"></a>¿Debo emparejar mis controladores a un casco de realidad mixta de Windows con radio Bluetooth integrado?

Algunos auriculares Windows Mixed Reality, incluidos Acer OJO 500 y Samsung Odyssey +, tienen radios Bluetooth integrados para su uso con controladores de movimiento. Los controladores de movimiento que se incluyen con estos auriculares se emparejan previamente con los auriculares de la fábrica y no requieren que el equipo tenga una radio Bluetooth independiente. Estos controladores de movimiento se _pueden_ emparejar manualmente con la radio Bluetooth de su equipo, por ejemplo, para su uso con auriculares de realidad mixta de Windows que no tienen radios Bluetooth integrados. 

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Cómo emparejar controladores nuevos si Windows Mixed Reality ya está configurado en mi PC
Si va a emparejar los controladores con el casco, use la aplicación complementaria (el [portal de realidad mixta](install-windows-mixed-reality.md#launch-mixed-reality-portal) puede ayudarle a encontrar una aplicación complementaria que se inicia o le proporciona una lista de aplicaciones complementarias que puede seleccionar).

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mis controladores emparejados no aparecen en el portal de realidad mixta. 

* Mantenga los controladores delante del casco y reinícielos; para ello, presione el botón Windows durante cuatro segundos y, luego, de nuevo durante dos segundos. 
* Si ve el "controlador de movimiento" en **Device Manager > dispositivos de interfaz humana** , vuelva a realizar el proceso de emparejamiento. 
* Si los LED del controlador son cíclicas, la activación de un cuadrante de las luces a la vez y su desactivación se están llevando a cabo una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en la realidad mixta. 
* Si se usa un adaptador Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2,0 (que suele ser, aunque no siempre, negro), de otros transmisores inalámbricos o de dispositivos USB 3,0. 
* Si el equipo se acaba de bloquear y se usa un adaptador Qualcomm, es posible que no funcione el restablecimiento. Para solucionarlo, desconecte la alimentación de la parte posterior del equipo (o, si está en un portátil, mantenga presionado el botón de encendido durante 10 segundos) y reinicie el equipo. 
* Ejecute el solucionador de problemas de Bluetooth en **configuración > actualizar & seguridad > solucionar problemas de > Bluetooth** .  

### <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>¿Cómo puedo devolver los controladores a su emparejamiento de fábrica?

Para devolver los controladores de movimiento a su emparejamiento de fábrica, o bien, para emparejarlos con un casco de realidad mixta de Windows con radio Bluetooth integrado, ejecute la aplicación complementaria de dispositivo del auricular (por ejemplo, la aplicación "Acer OJO 500" o la aplicación "Samsung HMD Odyssey + Setup", que se instala automáticamente la primera vez que el casco está enchufado) y siga las instrucciones para emparejar controladores de movimiento.



## <a name="if-your-motion-controllers-are-paired-to-your-pc"></a>**Si los controladores de movimiento están emparejados al equipo:**

### <a name="my-motion-controllers-are-not-pairing"></a>Mis controladores de movimiento no están emparejados. 

* Si los controladores no se activan, Inserte pilas nuevas. Si esto no lo corrige, restaure el dispositivo a su configuración de fábrica. para ello, encienda el dispositivo mientras mantiene presionados los botones de emparejamiento. Consulte los [pasos de recuperación del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) para obtener más detalles. 
* Si los controladores se activan y usa un adaptador de Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2,0 (que suele ser, pero no siempre, negro), lejos de otros transmisores inalámbricos o unidades flash USB. Si sigue sin funcionar, ejecute el solucionador de problemas de Bluetooth en configuración > actualizar & seguridad > solucionar problemas de > Bluetooth. 
* Si usa un adaptador Qualcomm y el equipo acaba de bloquearse, reinicie el equipo. 
* Intente reiniciar los controladores de movimiento que no están emparejados, de uno en uno, y, a continuación, reinicie el equipo. 
* La memoria caché del controlador de movimiento puede estar dañada. Para solucionar este problema, consulte estos [pasos](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal). 
* Si ninguno de estos pasos soluciona el problema, debe ponerse en contacto con el fabricante. 

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Mis controladores emparejados no aparecen en el portal de realidad mixta. 

* Mantenga los controladores delante del casco y reinícielos; para ello, presione el botón Windows durante cuatro segundos y, luego, de nuevo durante dos segundos. 
* Si los controladores aparecen como conectados en la **configuración > Bluetooth & otros dispositivos** , desemparejarlos y volver a realizar el proceso de emparejamiento. 
* Si los LED del controlador son cíclicas, la activación de un cuadrante de las luces a la vez y su desactivación se están llevando a cabo una actualización de firmware. Espere a que se complete la actualización y los controladores deben aparecer en la realidad mixta. 
* Si se usa un adaptador Bluetooth externo, asegúrese de que el adaptador está conectado a un puerto USB 2,0 (que suele ser negro), fuera de otros transmisores inalámbricos o dispositivos USB 3,0. 
* Si el equipo se acaba de bloquear y se usa un adaptador Qualcomm, es posible que no funcione el restablecimiento. Para solucionarlo, desconecte la alimentación de la parte posterior del equipo (o, si está en un portátil, mantenga presionado el botón de encendido durante 10 segundos) y reinicie el equipo. 
* Ejecute el solucionador de problemas de Bluetooth en **configuración > actualizar & seguridad > solucionar problemas de > Bluetooth** .  

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Estoy intentando emparejar mis controladores, pero nunca aparecen en el menú "agregar un nuevo dispositivo" en la configuración de Bluetooth.

Compruebe que ya no tiene controladores emparejados. Si lo hace, quítelos e inténtelo de nuevo. Reinicie el equipo si el problema persiste. Si se produce un error, consulte más [información sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Cómo emparejar controladores nuevos si Windows Mixed Reality ya está configurado en mi PC

1. Inserte dos baterías AA en cada controlador. No vuelva a poner la batería en la cubierta.
2. Mantenga presionado el botón Windows durante dos segundos para activar cada controlador. Hablaremos cuando se activen.
3. Ponga los controladores en modo de emparejamiento. El botón de emparejamiento está dentro del compartimiento de la batería (consulte esta [imagen](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc)). Manténgala presionada hasta que las luces del controlador empiecen a parpadear.
4. Vaya a **configuración > dispositivos > bluetooth & otros dispositivos** y, a continuación, **agregue Bluetooth u otro dispositivo > Bluetooth** . Cuando aparezcan los controladores, selecciónelos para emparejarlos.

Nota: si hay otro conjunto de controladores de movimiento emparejados con el equipo, deberá desemparejar los controladores antes de emparejarlos. Si empareja un conjunto de controladores de movimiento con el equipo actual y luego los empareja con un segundo equipo, deberá desemparejarlos y volver a emparejarlos con el equipo actual antes de volver a usarlos.

### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>¿Cómo se puede saber si utilizo tecnología Bluetooth?

Los controladores de movimiento usan la misma tecnología Bluetooth que se encuentra en muchos dispositivos de consumo y están diseñados para funcionar con la capacidad de Bluetooth incluida en cualquier equipo reciente. El equipo debe tener radio Bluetooth Si ha superado la comprobación de compatibilidad de realidad mixta. Para comprobarlo: 
* Abra "Device Manager". 
* Expanda la sección Bluetooth y busque un adaptador. 

![Captura de pantalla de un Device Manager de ejemplo. El adaptador es el radio Bluetooth.](images/devicemanagerbtadapterpic.png) 

Si su equipo no tiene Bluetooth, un dispositivo de protección recomendado es el [adaptador USB Bluetooth 4,0 de baja energía](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom).

### <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi se ralentiza en mi cuaderno cuando se activan los controladores de movimiento.

El cuaderno puede compartir su antena Wi-Fi con Bluetooth cuando se conecta a un punto de acceso de 2,4 GHz. Proteja Device Manager si puede cambiar la preferencia de banda a 5 GHz. Si una red de 5 GHz no está disponible y el rendimiento se ve afectado gravemente, considere la posibilidad de usar una llave de Bluetooth.

![La configuración de selección de banda wifi se puede encontrar a través del administrador de dispositivos](images/wifi5ghz.png)

### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>Mi PC tiene tecnología Bluetooth, pero tengo problemas con los controladores.

Los controladores de movimiento deben funcionar con otros teclados, ratones y controladores de juegos Bluetooth, pero la experiencia variará en función del modelo de teclado, mouse o dispositivo de juego que use. Estas son algunas de las cosas que puede hacer para mejorar el rendimiento:
* Si el equipo tiene Bluetooth pero sigue teniendo problemas con los controladores de movimiento, considere la posibilidad de reemplazar la radio Bluetooth por un adaptador Bluetooth externo que se puede conectar a USB. Solo puede tener un adaptador de radio Bluetooth activo a la vez. Si conecta una radio externa además de una radio existente, deberá deshabilitar la radio Bluetooth existente en Device Manager (haga clic con el botón derecho en el adaptador y seleccione "deshabilitar dispositivo") y elimine el emparejamiento de todos los dispositivos Bluetooth anteriores.
* Si utiliza un adaptador Bluetooth USB, conéctelo a un puerto USB 2,0 (los puertos 2,0 suelen ser negros y no tienen la etiqueta "SS"), si están disponibles. El puerto debe estar separado físicamente de:
    - el conector USB de HMD
    - unidades flash
    - unidades de disco duro
    - los receptores USB inalámbricos como los de teclados o ratones ideales, conectan el adaptador de Bluetooth USB en el lado opuesto del equipo lo más lejos posible de estos otros conectores.
* Cierre la ventana de configuración de Bluetooth Si está abierta. Dejándolo abierto en segundo plano significa que se realizan muchas llamadas adicionales al protocolo Bluetooth.
* Si el casco está emparejado con el equipo, use la pila del controlador de Bluetooth de Windows y no instale ninguna pila de controladores Bluetooth de terceros. Es posible que el software de terceros no funcione correctamente.
* Deshabilite la opción "Mostrar notificación para conectarse con el par SWIFT" en "Bluetooth & otros dispositivos" para reducir la actividad de detección de radio de host.
* Si usa una tarjeta Bluetooth interna, asegúrese de que está usando una antena Bluetooth externa o puede experimentar problemas de seguimiento. Si esto no funciona, use una llave Bluetooth (USB) externa después de deshabilitar el Bluetooth interno.
* El dispositivo debe aparecer en la categoría "Mouse, teclado & el lápiz" en la configuración de Bluetooth. Si se encuentra en "otros dispositivos", desemparejar y emparejar el dispositivo.
* Quitar, desemparejar y desconectar auriculares y altavoces Bluetooth. No se admiten con Windows Mixed Reality. Use el conector de auriculares o los altavoces integrados en los auriculares de la realidad mixta para disfrutar de la mejor experiencia de audio.

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>El segundo controlador tarda mucho tiempo en volver a conectarse.

Algunos dispositivos de radio Intel anteriores experimentan este problema si los controladores de movimiento se encienden al mismo tiempo. Evite el encendido de controladores al mismo tiempo.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Mi radio Bluetooth de Qualcomm no puede emparejar controladores después de un bloqueo del equipo.

Los controladores de radio de Bluetooth de Qualcomm (QCA) anteriores a 10.0.0.448 pueden acabar en mal estado después de un bloqueo de Windows. Apague el equipo completamente para solucionar este problema. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Tengo un seguimiento deficiente del controlador con radio Marvell.

Vaya a **Device Manager > adaptador de radio bluetooth > Marvell AVASTAR > de propiedades de > controlador** y asegúrese de que está usando el controlador 15.68.9210.47 o posterior.
