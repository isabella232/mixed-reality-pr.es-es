---
title: Preguntas más frecuentes sobre la conectividad de cascos
description: La conectividad del casco Windows Mixed Reality solución de problemas de conectividad de cascos que va más allá de la documentación de soporte técnico al consumidor estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Headset
appliesto:
- Windows 10
ms.openlocfilehash: ed8708d39953e79d445f3794d335d9a9451c9bf9fe8c2fca1feb792ee3f9b2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189227"
---
# <a name="headset-connectivity-faqs"></a>Preguntas más frecuentes sobre la conectividad de cascos

## <a name="my-headset-will-not-wake-up"></a>El casco no se reactivará

Si el casco está en modo de somnquete y hacer clic en el botón reactivar no funciona, reinicie el equipo.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Mi equipo no tiene hdmi ni puerto de presentación

Es posible que tenga que usar un adaptador. Vaya [aquí](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para obtener una lista de adaptadores admitidos.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>¿Puedo usar cables de extensión USB o HDMI o DisplayPort con Windows Mixed Reality cascos?

Windows Mixed Reality cascos no admiten oficialmente el uso de cables de extensión USB, HDMI o DisplayPort. Si usa estos cables, la experiencia de Mixed Reality puede verse afectada debido a las variaciones en la integridad de la señal y la potencia del bus entre el controlador USB del equipo y el casco Mixed Reality dispositivo. Pruebe a usar el casco sin cables de extensión si:

* La pantalla del casco muestra brevemente una pantalla azul y, a continuación, se vuelve Portal de realidad mixta se reinicia o se desenumeró completamente durante el uso.
* El audio del casco se corta o se convierte en un problema
* El casco parpadea entre el negro y la pantalla correcta

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Aparece el error "Comprobar el cable de pantalla"

* Si usa adaptadores para conectar el casco al equipo, asegúrese de que admiten Windows Mixed Reality y que son compatibles con 4K. Pruebe también a conectar el adaptador al equipo antes de conectar el casco al adaptador.
* Pruebe a usar otro puerto HDMI o DisplayPort.
* Conectar el casco a DisplayPort 1.2 o posterior, o HDMI 1.4 o posterior. Asegúrese de que el puerto se corresponde con la tarjeta gráfica más avanzada del equipo.
* Si el equipo tiene gráficos integrados y discretos, asegúrese de que usa el puerto HDMI o DisplayPort en la tarjeta gráfica activa. Esto puede significar que tendrá que conectar la pantalla del equipo a un puerto que no sea HDMI.
* Si el equipo tiene gráficos integrados y discretos, y los gráficos integrados son antiguos y no admiten Windows Mixed Reality, intente deshabilitar la GPU integrada.
* Conectar monitor de equipo al puerto HDMI o DisplayPort del equipo. Asegúrese de que los controladores de gráficos están actualizados. Descargue e instale los controladores directamente desde AMD, Nvidia o Intel, ya que probablemente serán más recientes de lo que se publica en Windows Update.
* Si tiene un monitor externo conectado a un puerto HDMI, intente conectarlo a displayPort en su lugar y use el puerto HDMI para el casco.
* Asegúrese de conectar el cable HDMI del casco a un puerto "HDMI out" del equipo, no a un puerto "HDMI in".
* Windows que no pueda detectar la conexión del cable de pantalla. Abra el Administrador de dispositivos y vea si el casco aparece en "Monitores". Si no es así, seleccione Action > Scan for hardware changes (Buscar **cambios de hardware).**

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Aparece un mensaje que dice "Put on your headset" (Poner el casco), pero tengo el casco puesto

Al colocar el casco, es Windows Mixed Reality unos segundos para volver a cargar el espacio. Si este mensaje no desaparece, asegúrese de que se ha quitado el protector del sensor de proximidad del interior del casco entre las lentes. Póngase en contacto con el fabricante del casco si el problema persiste.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Un mensaje dice "Conectar casco" pero he conectado el casco

- Asegúrese de que los cables USB y HDMI o DisplayPort del casco están conectados a los puertos correctos del equipo. Aquí se muestra cómo identificar los puertos correctos:

    - Los puertos USB 3.0 tienen un logotipo especial con una marca "SS" (que indica "SuperSpeed"). La parte interna del puerto es normalmente azul, pero los puertos USB 2.0 más antiguos suelen ser en blanco o negro en el interior.
    - Si el equipo tiene dos puertos HDMI o DisplayPort, use el que se conecta a la tarjeta gráfica, no a la placa base del equipo. No siempre es obvio, que es lo que, aunque los puertos discretos suelen estar ubicados en una ranura de expansión en el equipo. Si prueba un puerto y no funciona, pruebe el otro.

- Desconecte y conecte los cables USB y HDMI o DisplayPort del casco para asegurarse de que están conectados de forma segura. Al conectar el cable USB, intente no pausar durante la inserción del cable USB.
- Pruebe un concentrador USB 3.0 con tecnología externa si ve una enumeración parcial del casco, por ejemplo, una serie de dispositivos USB, pero no hay nada en "cascos Mixed Reality" en Administrador de dispositivos.
- Vaya al sitio web del fabricante del casco y actualice los controladores y el firmware del casco.
- Conectar el casco a otro equipo y abra Administrador de dispositivos. Incluso si ese equipo no es totalmente compatible con Windows Mixed Reality, puede comprobar si el casco se enumera. Si el casco no se enumera en varios equipos, podría tener un problema de hardware.

> [!NOTE]
> Para los usuarios de Surface: las versiones anteriores del software de actualización de firmware de Surface Dock Surface Book USB Hub no son compatibles con Mixed Reality cascos. Si recibe un mensaje "Conectar el casco" en un equipo Surface, compruebe si algún dispositivo informa de un error "Código 10: el dispositivo no se puede iniciar" en Administrador de dispositivos. Si es así, [quite el controlador en conflicto](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Solo debe hacerlo una vez.

Nota para los usuarios de Windows 10-N: si el equipo ejecuta Windows 10 N, verá un error "Código 28: la clase de instalación no está presente o no es válida" en Administrador de dispositivos después de conectar el casco de Mixed Reality. N ediciones de Windows 10 no son compatibles con Windows Mixed Reality. Siga estas [instrucciones](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) para obtener más información.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un mensaje indica "Compruebe el cable USB" o "Velocidad USB insuficiente"

* Asegúrese de que usa un puerto USB 3.0 compatible en el equipo:

    * Asegúrese de que el cable USB del casco está conectado en todo momento.
    * Ejecute el [Windows Mixed Reality Portal para](install-windows-mixed-reality.md#launch-mixed-reality-portal) asegurarse de que se admite el controlador USB 3.0 del equipo.
    * Conectar el casco a los demás puertos USB 3.0 del equipo. Algunos equipos tienen más de un controlador USB 3.0.
    * Desconecte temporalmente todos los dispositivos USB conectados al equipo y conecte solo los cascos.
    * En equipos creados de forma personalizada, aunque un puerto se pueda marcar como puerto USB 3.0, puede estar conectado a un controlador USB 2.0. Con el casco conectado, abra Administrador de dispositivos, busque y haga clic en cualquiera de los dispositivos enumerados en el casco y, a continuación, vaya a Ver **> dispositivos por conexión.**
* Pruebe el casco en otro equipo. Si ese otro equipo no es totalmente compatible con Windows Mixed Reality, Administrador de dispositivos para ver si ve el mensaje de "velocidad USB insuficiente". Si no se enumera correctamente en varios equipos, el casco podría ser defectuoso.
* Quite los extensores o concentradores entre el casco y el equipo.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>La Portal de realidad mixta no se hizo después de conectar el casco

Es posible que el casco no se haya detectado correctamente debido a un problema subyacente. Inicie el Portal de realidad mixta manualmente y busque los mensajes de error que aparezcan.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>El casco dejó de funcionar cuando mi PC entra en modo de suspensión o hibernación, o al reiniciar el equipo con el casco conectado

1. Abra Administrador de dispositivos y confirme que el casco aparece en "Mixed Reality dispositivos".
2. Seleccione el casco en "Mixed Reality dispositivos" y confirme que el estado del dispositivo indica "Este dispositivo funciona correctamente".
3. Si ve un error de "Código 43" que indica que el dispositivo ha dejado de funcionar, o si no ve el casco en "dispositivos Mixed Reality", desconecte y vuelva a conectarlo en el cable USB del casco. Microsoft está investigando un posible problema de interoperabilidad entre software y controlador, lo que puede dar lugar a este error. Este problema afecta a un pequeño número de equipos y se espera que se resuelva en una futura actualización del controlador Mixed Reality casco.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>El casco hace que mi PC genere una comprobación de errores (pantalla azul) cuando se pone el equipo en suspensión o cuando está en modo de hibernación

Asegúrese de que está en el controlador 10.0.19041.2034 o posterior.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>El controlador de casco no se instaló automáticamente al conectar el casco

En equipos nuevos o equipos con una copia recién instalada de Windows 10, el controlador de casco podría poner en cola detrás de otras actualizaciones de Windows y es posible que no se instale inmediatamente.

1. Vaya a **Inicio > Administrador de dispositivos** y busque en "Mixed Reality dispositivos" para el casco. El estado del dispositivo debe indicar que "El dispositivo funciona correctamente".
2. Haga clic con el botón derecho en el dispositivo y seleccione "Actualizar controlador".

Si eso no funciona, intente desinstalar el controlador:

1. Vaya a **Inicio > Administrador de dispositivos** y busque en "Mixed Reality dispositivos" para el casco. El estado del dispositivo debe indicar que "El dispositivo funciona correctamente".
2. Haga clic con el botón derecho en el dispositivo y seleccione "Desinstalar dispositivo".
3. En el nuevo elemento emergente que aparece, active la casilla "Eliminar el software del controlador para este dispositivo" y, a continuación, seleccione "Desinstalar".
4. Cuando se complete, desconecte el casco del equipo y vuelva a conectarlo. Windows La actualización ahora descargará e instalará un nuevo controlador.

Nota: Si tiene una edición N de Windows, deberá cambiar a una edición normal de Windows 10 para usar Windows Mixed Reality.