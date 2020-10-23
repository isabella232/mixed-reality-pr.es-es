---
title: Preguntas más frecuentes sobre la conectividad con auriculares
description: Configuración avanzada de Windows con auriculares con micrófonos, que va más allá de nuestra documentación de soporte técnico estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, auriculares
appliesto:
- Windows 10
ms.openlocfilehash: abdd0f04443e110f1eb19a31fb3d77e2f3bde929
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434553"
---
# <a name="headset-connectivity-faqs"></a>Preguntas más frecuentes sobre la conectividad con auriculares

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>El equipo no tiene un puerto HDMI o de pantalla

Es posible que tenga que usar un adaptador. Vaya [aquí](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para obtener una lista de adaptadores admitidos.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>¿Puedo usar cables de extensión USB o HDMI o DisplayPort con auriculares de realidad mixta de Windows?
Los auriculares de realidad mixta de Windows no admiten oficialmente los cables de extensión USB, HDMI o DisplayPort. El uso de estos cables puede afectar de forma significativa a la experiencia de realidad mixta debido a las variaciones en la integridad de la señal resultante y la potencia de bus entre el controlador USB del equipo y el casco de realidad mixta. Si la pantalla de los auriculares muestra brevemente una pantalla azul y, a continuación, se reinicia el portal de realidad mixta y el negro, o se anula la enumeración por completo durante el uso, o si el audio de los auriculares se reduce o se vuelve con problemas, o si el casco parpadea entre el negro y la pantalla correcta, pruebe a usar el casco sin cables de extensión.

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Obtengo un error "comprobar el cable de pantalla"

* Si usa adaptadores para conectar los auriculares a su equipo, asegúrese de que admiten Windows Mixed Reality (el adaptador debe ser compatible con 4K). Intente también conectar el adaptador al equipo antes de conectar los auriculares al adaptador.
* Pruebe a usar un puerto HDMI o DisplayPort diferente.
* Conecte los auriculares a un DisplayPort 1,2 o posterior, o HDMI 1,4 o posterior. Asegúrese de que el puerto corresponde a la tarjeta de gráficos más avanzada del equipo.
* Si su equipo tiene gráficos integrados y discretos, asegúrese de que está usando el puerto HDMI o DisplayPort en la tarjeta gráfica activa. Esto puede significar que tendrá que conectar la pantalla de su PC a un puerto que no sea HDMI.
* Si su equipo tiene gráficos integrados y discretos, y los gráficos integrados son más antiguos y no admiten Windows Mixed Reality, intente deshabilitar la GPU integrada.
* Conecte un monitor de PC al puerto HDMI o DisplayPort de su PC. Asegúrese de que los controladores de gráficos están actualizados. Descargue e instale los que se encuentran desde AMD, NVIDIA o Intel directamente, ya que probablemente sean más recientes que las que se publican en Windows Update.
* Si tiene un monitor externo conectado a un puerto HDMI, intente conectarlo a un DisplayPort en su lugar y use el puerto HDMI para sus auriculares.
* Asegúrese de conectar el cable HDMI del casco a un puerto "HDMI OUT" en el equipo, no un puerto "HDMI in".
* Es posible que Windows no pueda detectar la conexión del cable de la pantalla. Abra el Device Manager y compruebe si el casco aparece en "monitores". Si no es así, seleccione **acción > buscar cambios de hardware**. 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Un mensaje indica "poner en el casco", pero tengo el casco encendido

Al colocar el casco, Windows Mixed Reality puede necesitar unos segundos para recargar el espacio. Si este mensaje no desaparece, asegúrese de que se ha quitado el adhesivo protector del sensor de proximidad, que se encuentra en el interior del casco entre las lentes. Si esto no resuelve el problema, póngase en contacto con el fabricante del casco.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Un mensaje indica "conectar el casco", pero he enchufado en el casco

1. Asegúrese de que los cables USB y HDMI y/o DisplayPort del auricular están conectados a los puertos correctos del equipo. Aquí se describe cómo identificar los puertos correctos:
    * Los puertos USB 3,0 tienen un logotipo especial con una marca "SS" (que indica "SuperSpeed"). La pieza interior del puerto suele ser azul, mientras que los puertos USB 2,0 más antiguos suelen estar en blanco o negro en el interior.
    * Si el equipo tiene dos puertos HDMI o DisplayPort, use el que se conecta a la tarjeta gráfica, no la placa base del equipo. No siempre es obvio qué es, aunque los puertos discretos se encuentran a menudo en una ranura de expansión del equipo. Si intenta un puerto y no funciona, pruebe el otro.
2. Desconecte y conecte los cables USB y HDMI o DisplayPort desde los auriculares para asegurarse de que están conectados de forma segura. Al conectar el cable USB, intente no pausarse durante la inserción del cable USB.
3. Abra Device Manager y confirme que el casco aparece en "dispositivos de realidad mixta". Al seleccionar los auriculares, el estado del dispositivo debe indicar "este dispositivo funciona correctamente". Los signos de exclamación amarillo en los dispositivos de Device Manager indican errores.
    * Si "sensores de Hololens" aparece con un signo de exclamación amarillo en Device Manager, seleccione el dispositivo. Si ve un "código 10: los controladores de este dispositivo no están instalados. No hay controladores compatibles para este dispositivo ", [Instale manualmente el controlador de casco](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset).
    * Si usa varios auriculares de realidad mixta en su PC y ha instalado manualmente el controlador de auriculares de realidad mixta, la actualización manual del controlador solo se puede aplicar a los auriculares conectados en el momento y no a otros auriculares. En este caso, verá "código 31: este dispositivo no funciona correctamente porque Windows no puede cargar los controladores necesarios para este dispositivo. (Código 31). El mensaje ALPC solicitado ya no está disponible en Device Manager. En **Device Manager > dispositivos de realidad mixta**, haga clic con el botón derecho en el casco y seleccione "desinstalar dispositivo". Seleccione "Aceptar" para confirmar y, a continuación, desconectar y volver a enchufar los auriculares.
4. Si ve una enumeración parcial de los auriculares (una serie de dispositivos USB enumeración, pero no hay nada en "auriculares de realidad mixta" en Device Manager), pruebe un concentrador USB 3,0 de alimentación externa.
5. Vaya al sitio web del fabricante del casco y actualice los controladores y el firmware del casco.
6. Conecte los auriculares a otro equipo y abra Device Manager. Incluso si ese equipo no es totalmente compatible con Windows Mixed Reality, puede comprobar si se enumeran los auriculares. Si el casco no se enumera en varios equipos, podría tener un problema de hardware.

Nota para los usuarios de Surface: las versiones anteriores de los programas de actualización de firmware del concentrador USB de Surface Dock y Surface Si recibe un mensaje de "conectar el casco" en un equipo Surface, compruebe si algún dispositivo está informando de un error "código 10: el dispositivo no se puede iniciar" en Device Manager. En ese caso, [Quite el controlador en conflicto](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Solo debe hacerlo una vez.

Nota para los usuarios de Windows 10 N: Si el equipo está ejecutando Windows 10 N, verá el error "Code 28: la clase de instalación no está presente o no es válido" en Device Manager después de conectar el casco de realidad mixta. En Windows Mixed Reality no se admiten las ediciones N de Windows 10. Siga estas [instrucciones](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) para obtener más información.

Esta información también se muestra en un [Diagrama de flujo de solución de problemas](headset-connectivity-flowchart.md).

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un mensaje indica "comprobar el cable USB" o "velocidad de USB insuficiente".

* Asegúrese de que está usando un puerto USB 3,0 compatible en su PC:
    * Asegúrese de que el cable USB del auricular está enchufado.
    * Ejecute el [portal de Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) para asegurarse de que se admite el controlador USB 3,0 de su PC.
    * Conecte los auriculares a los demás puertos USB 3,0 del equipo. Algunos equipos tienen más de un controlador USB 3,0.
    * Desconecte temporalmente todos los dispositivos USB conectados al equipo y conecte solo los auriculares.
    * En los equipos personalizados, aunque un puerto se puede marcar como un puerto USB 3,0, puede estar conectado a un controlador USB 2,0. Con el casco conectado, abra Device Manager, busque y haga clic en cualquiera de los dispositivos enumerados desde el casco y, a continuación, vaya a **ver > dispositivos por conexión**.
* Pruebe el casco en otro equipo. Si ese equipo no es totalmente compatible con Windows Mixed Reality, proteja Device Manager para ver si ve el mensaje "velocidad de USB insuficiente". Si no se enumera correctamente en varios equipos, el casco podría estar defectuoso.
* Quite cualquier extensor o concentrador entre los auriculares y el equipo.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>El portal de realidad mixta no se inició después de haber enchufado los auriculares.

Es posible que el casco no se haya detectado correctamente debido a un problema subyacente. Inicie el portal de realidad mixta manualmente y busque los mensajes de error que aparecen. 

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>El casco dejó de funcionar cuando el equipo entra en modo de suspensión o hibernación, o bien al reiniciar el equipo con los auriculares conectados.

1. Abra Device Manager y confirme que el casco aparece en "dispositivos de realidad mixta".
2. Seleccione el casco en "dispositivos de realidad mixta" y confirme que el estado del dispositivo indica que el dispositivo funciona correctamente.
3. Si ve un error "código 43" que indica que el dispositivo ha dejado de funcionar o si no ve los auriculares en la lista "dispositivos de realidad mixta", desconecte y reenchufe el cable USB del casco. Microsoft está investigando un posible problema de interoperabilidad entre software y controlador que puede producir este error. Este problema afecta a un número pequeño de equipos y se espera que se resuelva en una futura actualización del controlador de auriculares de realidad mixta.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>El casco hace que el equipo genere una comprobación de errores (pantalla azul) al poner el equipo en suspensión o en modo de hibernación.
Asegúrese de que está en el controlador 10.0.18362.1062 o una versión más reciente.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>El controlador de casco no se instaló automáticamente al enchufar el casco.

En los equipos nuevos o equipos con una copia recién instalada de Windows 10, el controlador de auriculares puede ponerse en cola detrás de otras actualizaciones de Windows y es posible que no se instale inmediatamente. Para instalarlo manualmente:
1. Vaya a **inicio > Device Manager** y busque en "otros dispositivos" un dispositivo de "sensores de hololens" con un signo de exclamación amarillo: ![ vista de Device Manager sensores de hololens](images/hololenssensors.png)
2. Haga clic con el botón derecho en el dispositivo y seleccione Propiedades. Si las propiedades del dispositivo leen "los controladores de este dispositivo no están instalados (código 28)", cierre la ventana y continúe. Si hay otro mensaje, siga los pasos de solución de problemas en el resto de esta página.
![Código 28 de sensores de HoloLens en Device Manager](images/code28.png)
3. Vuelva a hacer clic con el botón derecho en el dispositivo y seleccione "actualizar controladores..." y, a continuación, "Buscar software de controlador actualizado" después de las actualizaciones del dispositivo, debería ver los auriculares que aparecen en "dispositivos de realidad mixta" en Device Manager: el ![ dispositivo de realidad mixta aparece en Device Manager](images/mixedrealitydevices.png)

Si la instalación manual no funciona o no encuentra el controlador en otros dispositivos, es probable que tenga que desinstalar el controlador existente y volver a instalarlo. Para ello:
1. Vaya a **inicio > Device Manager** y mire en "dispositivos de realidad mixta" para el casco. El estado del dispositivo debe indicar que "el dispositivo funciona correctamente".
2. Haga clic con el botón derecho en el dispositivo y seleccione "desinstalar dispositivo".
3. En el menú emergente nuevo que aparece, active la casilla "eliminar el software de controlador para este dispositivo" y, a continuación, seleccione "desinstalar".
4. Cuando termine, desconecte el casco del equipo y conéctelo de nuevo. Windows Update ahora descargará e instalará un nuevo controlador.

Nota: Si tiene una edición N de Windows, tendrá que cambiar a una edición normal de Windows 10 para usar Windows Mixed Reality.


