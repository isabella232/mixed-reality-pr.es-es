---
title: Solución de problemas de Windows Mixed Reality
description: Solución avanzada de problemas de realidad mixta de Windows que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692415"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>Solución de problemas de Windows Mixed Reality (p + f)

## <a name="understanding-common-installation-error-messages"></a>Descripción de los mensajes de error de instalación comunes

### <a name="your-pc-cant-run-windows-mixed-reality"></a>"El equipo no puede ejecutar Windows Mixed Reality"

Su equipo no cumple los [requisitos mínimos](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necesarios para ejecutar Windows Mixed Reality. Esto podría deberse a que la configuración de hardware del equipo no es compatible con Windows Mixed Reality, o a que es necesario [actualizar a la versión más reciente de Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq). 

Tenga en cuenta que Windows Mixed Reality requiere un controlador de tarjeta de gráficos que admita al menos WDDM 2,2, por lo que debe asegurarse de que tiene la última actualización del controlador del fabricante. Si la instalación de Windows Mixed Reality indica que la tarjeta gráfica no cumple los requisitos y cree que lo hace, asegúrese de que el casco esté conectado a la tarjeta correcta.

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Ya está casi ahí: este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality"

Su equipo no cumple los [requisitos mínimos](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necesarios para la mejor experiencia en Windows Mixed Reality. Es posible que el equipo pueda ejecutar un casco envolvente, pero es posible que no pueda ejecutar ciertas aplicaciones o que tenga problemas de rendimiento.

Tenga en cuenta que Windows Mixed Reality requiere un controlador de tarjeta de gráficos que admita al menos WDDM 2,2, por lo que debe asegurarse de que tiene la última actualización del controlador del fabricante. Si la instalación de Windows Mixed Reality indica que la tarjeta gráfica no cumple los requisitos y cree que lo hace, asegúrese de que el casco esté conectado a la tarjeta correcta.

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Antes de poder configurar Windows Mixed Reality, el administrador deberá habilitarlo para su organización. Más información "

Probablemente se encuentre en una red administrada por la empresa y su organización use Windows Server Update Services (WSUS) o tiene otras directivas que pueden bloquear la descarga. Póngase en contacto con el administrador del sistema o el Departamento de TI de su organización para [habilitar Windows Mixed Reality](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"No pudimos descargar el software de realidad mixta" ni "colgar mientras hacemos una descarga"

* A veces, una actualización pendiente puede bloquear la descarga de software de realidad mixta. Vaya a **configuración > actualizar & seguridad > Windows Update** y asegúrese de que Windows Update está activado. A continuación, descargue e instale las actualizaciones que estén esperando para ser instaladas. Si recibe un error con Windows Update al intentar estos pasos, vaya [aquí](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors).
* Asegúrese de que el equipo está conectado a Internet y tiene al menos 2 GB de espacio de almacenamiento libre. Compruebe el estado de la red en: **configuración > red & estado de > de Internet** . Si no puede conectarse a Internet, vaya [aquí](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) para obtener ayuda.  
* Reinicie el equipo e inténtelo de nuevo. 

Si las soluciones anteriores no funcionan, pruebe lo siguiente:
* Si la conexión de red Wi-Fi está establecida en [medido](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq), cámbiela a desmedido. Para desactivar una conexión de uso medido, vaya a: **configuración > red & Internet > estado > cambiar las propiedades de conexión > establecer como conexión de uso medido** y seleccione "desactivado".  
* Si ha instalado recientemente una actualización, puede causar problemas. No se recomienda quitar las actualizaciones instaladas, especialmente las actualizaciones de seguridad que mantienen el equipo seguro, pero a veces quitar la actualización más reciente puede ayudar a determinar el origen del problema. Para ello, siga estos pasos: 
    * Vaya a **configuración > actualizar & seguridad > ver el historial de actualizaciones instaladas > desinstalar actualizaciones**
    * Seleccione la última actualización instalada y "desinstalar".
    * Cuando se le pregunte ¿está seguro de que desea desinstalar esta actualización? " responda "sí". Si recibe un error al intentar realizar estos pasos, vaya [aquí](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors). 
    * Reinicie el equipo e inténtelo de nuevo. 
    * Si Windows Mixed Reality se instala correctamente, vuelva a instalar las actualizaciones más recientes en **configuración > Windows Update > comprobar si hay actualizaciones** y ver si Windows Mixed Reality continúa funcionando. Si no se instala correctamente, vuelva a instalar las actualizaciones más recientes y póngase en contacto con el soporte técnico de Windows. 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Se produjo un error y no se pudo iniciar Windows Mixed Reality"
* Desconecte ambos cables de los auriculares del equipo.
* Reinicia el equipo.
* Vaya a **configuración > actualizar & seguridad > Windows Update** y asegúrese de que Windows Update está activado. A continuación, descargue e instale las actualizaciones en espera.
* Vuelva a conectar los auriculares al equipo y, a continuación, intente realizar de nuevo la instalación.

Si los pasos anteriores no funcionan, intente desinstalar y reinstalar Windows Mixed Reality:
* Vaya a **configuración > realidad mixta > desinstalar** y seleccione "desinstalar". 
* Reinicia tu equipo. 
* Para volver a iniciar el proceso de instalación, simplemente conecte el casco a su PC.
    

## <a name="troubleshooting-setup-questions"></a>Solucionar problemas de configuración 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>El controlador Xbox no funciona con Windows Mixed Reality.

* Asegúrese de que el controlador esté encendido, totalmente cargado y conectado al equipo.
* Reemplace las baterías del controlador.
* Si usa un controlador de Bluetooth, vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo y asegúrese de que esté emparejado (debe aparecer en la página).

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>No puedo dirigir la entrada (controladores, controlador de juegos, Mouse/teclado) a Windows Mixed Reality.

Al colocar el casco, la entrada se debe cambiar automáticamente a la experiencia de realidad mixta a través del sensor de presencia del casco. En el escritorio debe aparecer una barra azul:

![Escritorio de Windows con entrada que se dirige al casco](images/1050px-windowsy.png)

Si la entrada no se activa automáticamente, debe alternar manualmente la entrada al casco. Para ello, escriba **tecla Windows + y** en el teclado (y el mismo para alternar la entrada de vuelta al escritorio).

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>Al conectar los auriculares, no sucede nada. El portal de realidad mixta no se abre.
Portal de realidad mixta, la aplicación que le guía a través de la configuración de Windows Mixed Reality, está diseñada para abrirse automáticamente cuando conecta un casco compatible. Si no se abre, vaya a Inicio y escriba "portal de realidad mixta" en el cuadro de búsqueda para abrir la aplicación desde allí. Si no encuentra el portal de realidad mixta, es posible que deba [actualizar a la versión más reciente de Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Cómo elegir entre "sentado y permanente" y "todas las experiencias"

Si elige "sentado y permanente", ya sea durante la configuración del auricular o más adelante, utilizará los auriculares sin límite. Puede ponerse al día, pero tendrá que permanecer en un solo lugar, ya que no tendrá ningún límite que le ayude a evitar obstáculos físicos. Algunas aplicaciones pueden estar diseñadas para trabajar con un límite, por lo que es posible que no pueda usarlas o que no tenga la misma experiencia si las usa sin límite. Consulte "¿Qué es un límite y por qué debo crear uno?". a continuación encontrará más información.

Si elige "todas las experiencias", configurará un límite y podrá usar aplicaciones y experiencias que funcionen con un límite, así como los que no lo necesiten. 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>Obtenga información sobre la realidad mixta no se ejecutó en el primer inicio y me encontré en la Página principal de Windows Mixed Reality.

Puede volver a ejecutar la experiencia de aprendizaje siguiendo los [pasos de volver a ejecutar](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 


## <a name="boundary-setup-and-other-questions"></a>Configuración de límites y otras preguntas

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>¿Qué es un límite y por qué debo crear uno?

Un límite define el área en la que se puede desplazar mientras se utiliza el casco de la realidad mixta de Windows. Como no puede ver su entorno mientras usa el casco, es importante crear un límite que le ayude a evitar obstáculos. El límite es similar a un contorno blanco dentro de la realidad mixta y aparece cuando está cerca de él. Cuando lo vea, ralentice los movimientos y Evite cruzar el límite o extender sus extremidades más allá de él.

El área dentro del límite debe ser libre de mobiliario, accesorios de luz de baja francesa, ventiladores de techo, etc., por lo que no se saltará ni se desplazará sobre nada. [Obtenga información sobre el estado y la seguridad en Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

### <a name="how-do-i-create-a-boundary"></a>¿Cómo crear un límite?

La primera vez que configure los auriculares, la aplicación de instalación (portal de realidad mixta) le guiará por los pasos necesarios para crear un límite. Sin embargo, puede crear una en cualquier momento. Para ello, siga estos pasos:
1. Seleccione **inicio > portal de realidad mixta** en el escritorio. 
2. Abra "menú".
3. Seleccione "ejecutar el programa de instalación" para crear un nuevo límite.

Si otra persona usa el casco, asegúrese de que comprenden el límite y cómo usarlo. Si mueve los auriculares a una nueva ubicación, deberá configurar un nuevo límite que funcione para ese espacio.

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Obtengo un mensaje de error al intentar crear un límite.

* No se acerque demasiado a una pared u otro obstáculo al crear un límite.
* Asegúrese de mantener el casco en el alto de waist y enfrente el equipo mientras realiza el seguimiento del límite.
* Asegúrese de que el sensor no esté bloqueado y de que haya suficiente luz.
* El espacio en el que se realiza el seguimiento debe ser superior a tres metros cuadrados.
* El espacio no debe ser demasiado grande o demasiado complicado. Adhiere a una forma geométrica simple sin muchos giros y vueltas.
* No vuelva a cruzar su propia ruta de acceso mientras realiza el seguimiento.
* Si se queda atascado en una esquina, empiece de nuevo.

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante el inicio de la realidad mixta, estoy atascado en el paso "gire el cabezal hacia el lateral y, a continuación, en el suelo".

Este paso permite que los auriculares reconozcan su espacio y restauren el suelo y el límite virtual existentes. Al colocar el casco, este proceso de análisis puede tardar hasta 10 segundos. Una vez finalizado, estará en la Página principal de la realidad mixta o se le pedirá que configure de nuevo el límite.

Si el proceso de análisis tarda más de 10 segundos, podría haber un problema con el sensor de proximidad en el casco:
1. Compruebe que la etiqueta se ha quitado del sensor de proximidad. El sensor de proximidad se encuentra dentro del casco aproximadamente donde sería el centro del Forehead.
2. Compruebe que el sensor de proximidad está alternando la entrada al casco: con el dedo, cubra y descubra el sensor de proximidad varias veces para comprobar que la entrada está cambiando al casco. Debería ver el banner **clave de Windows + Y** en la parte superior de su PC. Puede cambiar manualmente la entrada al casco en cualquier momento escribiendo **tecla Windows + Y** en el teclado.

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>Aparece un mensaje que indica que no se puede encontrar el límite.   ¿Qué debo hacer?

Windows Mixed Reality podría tener problemas para identificar el límite existente. Puede crear un nuevo límite o usar el dispositivo en modo "sentado y permanente". 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Veo un mensaje que indica "pérdida de seguimiento" o "no tenemos límite para este espacio".

Debe crear un nuevo límite. Para ello, siga estos pasos:
* Seleccione **inicio > portal de realidad mixta** .
* Seleccione "Ejecutar instalación".

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>El límite siempre es visible. ¿Cómo puedo hacer que salga?

El límite aparece cuando está cerca de él. Si el límite incluye alguna sección que tiene una forma estrecha o irregular, puede acabar cerca de ella y hacer que aparezca, con más frecuencia de lo que desea. Para solucionarlo, intente crear de nuevo el límite usando una forma más grande y más normal. Para ello, siga estos pasos:
* Seleccione **inicio > portal de realidad mixta** .
* Seleccione "Ejecutar instalación".

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>¿Cómo se puede desactivar el límite temporalmente?

* Seleccione **inicio > portal de realidad mixta** .
* Abra "menú". 
* Active "límite" en "desactivado". Asegúrese de permanecer en un lugar mientras el límite esté desactivado.


## <a name="problems-in-windows-mixed-reality-home"></a>Problemas en la Página principal de Windows Mixed Reality

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>Mis controladores no se muestran en la Página principal de Windows Mixed Reality.

Asegúrese de que los controladores tienen baterías completas y que se emparejan correctamente con Bluetooth. Pruebe a desconectar y apagar los controladores con el botón Windows. Si todavía no puede ver los controladores, pruebe a emparejar y volver a emparejar cada controlador en el menú configuración, en **dispositivos > Bluetooth** .

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>El nivel inferior de la Página principal de Windows Mixed Reality no parece estar en el alto correcto o está inclinado.

Seleccione **inicio > ajuste de sala** que se iniciará una vez que coloque la aplicación en el mundo para realizar cambios mientras se contiene el casco. En esta aplicación, se le indicará que use el teclado táctil (controlador de movimiento) o el panel de control (controlador de vídeo) para ajustar el alto del piso. Cuando el piso sea correcto, use el botón de Windows para salir de nuevo a su hogar.

### <a name="my-headset-has-stopped-tracking"></a>El micrófono ha dejado de realizar el seguimiento.

Asegúrese de que las luces están encendidas y de que no hay nada que obstruya las cámaras de seguimiento interior de la parte delantera del casco. Si se pierde el seguimiento, puede tardar unos segundos en reanudarse. Si el seguimiento no se reanuda, intente reiniciar el portal de Windows Mixed Reality. Consulte [solución de problemas de seguimiento](tracking.md) para obtener más detalles.

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>No se puede mostrar una vista previa de lo que veo en el casco en la pantalla de escritorio.

El portal de realidad mixta tiene un botón **reproducir** en la parte inferior de la pantalla que le permite mostrar una vista previa de lo que está viendo en el casco en la pantalla del escritorio. Sin embargo, por motivos de rendimiento, esta característica solo está disponible en equipos que ejecutan Windows Mixed Reality ultra (90Hz).

## <a name="headset-connectivity-issues"></a>Problemas de conectividad con auriculares

### <a name="my-computer-does-not-have-an-hdmi-port"></a>El equipo no tiene un puerto HDMI.
Si el equipo no tiene un puerto HDMI pero tiene un puerto DisplayPort (DP), mini DisplayPort (miniDP) o de tipo USB (USB-C) para la salida de vídeo, es posible que deba usar un [adaptador compatible](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>¿Puedo usar cables de extensión USB o HDMI con auriculares de realidad mixta de Windows?
Los auriculares de realidad mixta de Windows no admiten oficialmente el uso de cables de extensión USB o HDMI. El uso de estos cables puede afectar de forma significativa a la experiencia de realidad mixta debido a las variaciones en la integridad de la señal resultante y la potencia de bus entre el controlador USB del equipo y el casco de realidad mixta. Si la pantalla de los auriculares muestra brevemente una pantalla azul y, a continuación, se reinicia el portal de realidad mixta y el negro y se vuelve a enumerar por completo durante el uso, o si el audio de los auriculares se recorta o se convierte en un problema, o si el casco parpadea entre el negro y la pantalla correcta, pruebe a usar el casco sin cables de extensión.

### <a name="i-am-getting-a-check-your-display-cable-error"></a>Obtengo un error "comprobar el cable de pantalla".

* Si usa adaptadores para conectar los auriculares a su equipo, asegúrese de que admiten Windows Mixed Reality. Intente también conectar el adaptador al equipo antes de conectar el HMD al adaptador.
* Si su equipo tiene gráficos integrados y discretos, asegúrese de que está usando el puerto HDMI en la tarjeta gráfica activa. En algunos casos, esto puede significar que necesita conectar la pantalla de su PC a un puerto no HDMI.
* Si su equipo tiene gráficos integrados y discretos, y los gráficos integrados son más antiguos y no admiten Windows Mixed Reality, intente deshabilitar la GPU integrada.
* Conecte un monitor de PC al puerto HDMI de su PC. Asegúrese de que los controladores de gráficos están actualizados. Descargue e instale los que se encuentran desde AMD, NVIDIA o Intel directamente, ya que probablemente sean más recientes que las que se publican en Windows Update.
* Asegúrese de enchufar el cable HDMI del casco en un puerto de **salida de HDMI** en el equipo, no en un puerto HDMI.
* Es posible que Windows no pueda detectar la conexión del cable de la pantalla. Abra el Device Manager y compruebe si el casco aparece en "monitores". Si no es así, seleccione **acción > buscar cambios de hardware** . 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Aparece un mensaje que indica "poner en el casco" aunque tengo el casco encendido.

Al colocar el casco, Windows Mixed Reality puede necesitar unos segundos para recargar el espacio. Si este mensaje no desaparece, asegúrese de que se ha quitado el adhesivo protector del sensor de proximidad, que se encuentra en el interior del casco entre las lentes. Si esto no resuelve el problema, póngase en contacto con el fabricante del casco.

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Un mensaje dice "conectar los auriculares" aunque he enchufado los auriculares.

1. Asegúrese de que los cables USB y HDMI del casco están conectados a los puertos correctos del equipo. Aquí se describe cómo identificar los puertos correctos:
    * Los puertos USB 3,0 tienen un logotipo especial con una marca "SS" (que indica "SuperSpeed"). La pieza interior del puerto suele ser azul, mientras que los puertos USB 2,0 más antiguos suelen estar en blanco o negro en el interior.
    * Si el equipo tiene dos puertos HDMI, use el que se conecta a la tarjeta gráfica, no la placa base del equipo. No siempre es obvio qué es, aunque los puertos discretos se encuentran a menudo en una ranura de expansión del equipo. Si intenta un puerto y no funciona, pruebe el otro.
2. Desconecte y conecte los cables USB y HDMI desde los auriculares para asegurarse de que están conectados de forma segura. Al conectar el cable USB, intente no pausarse durante la inserción del cable USB.
3. Abra Device Manager y confirme que el casco aparece en "dispositivos de realidad mixta". Haga doble clic en el casco en "dispositivos de realidad mixta" y confirme que el estado del dispositivo indica que el dispositivo funciona correctamente. Los signos de exclamación amarillo en los dispositivos que aparecen en Device Manager indican los errores notificados por los dispositivos conectados a su equipo.
    * Si aparece "sensores de Hololens" con un signo de exclamación amarillo en Device Manager, haga doble clic en el dispositivo. Si ve un **"código 10: los controladores de este dispositivo no están instalados. No hay controladores compatibles para este dispositivo** : siga las [instrucciones](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) para instalar manualmente el controlador de auriculares.
    * Si usa varios auriculares de realidad mixta en su PC y ha instalado manualmente el controlador de auriculares de realidad mixta, en algunas circunstancias la actualización manual del controlador solo se puede aplicar a los auriculares conectados en el momento y no a los demás auriculares. En este caso, verá **"código 31: este dispositivo no funciona correctamente porque Windows no puede cargar los controladores necesarios para este dispositivo. (Código 31). El mensaje ALPC solicitado ya no está disponible** en Device Manager. En Device Manager, haga clic con el botón derecho en el casco en "dispositivos de realidad mixta" y seleccione "desinstalar dispositivo". Seleccione "Aceptar" para confirmar y, a continuación, desconectar y volver a enchufar los auriculares.
4. Si ve una enumeración parcial de los auriculares (una serie de dispositivos USB enumeración, pero no hay nada en "auriculares de realidad mixta" en Device Manager), pruebe un concentrador USB 3,0 de alimentación externa.
5. Vaya al sitio web del fabricante del casco y actualice los controladores y el firmware del casco.
6. Conecte los auriculares a otro equipo y abra Device Manager. Incluso si ese equipo no es totalmente compatible con Windows Mixed Reality, puede comprobar si se enumeran los auriculares. Si el casco no se enumera en varios equipos, podría tener un problema de hardware.

**Nota para usuarios de Surface:** Las versiones anteriores de la superficie de Dock y el software de actualización de firmware del concentrador USB del libro de Surface son incompatibles con los auriculares de realidad mixta. Si recibe un mensaje de "conectar el casco" en un equipo Surface, compruebe si algún dispositivo está informando de un **error "código 10: el dispositivo no se puede iniciar"** en Device Manager. En ese caso, [Quite el controlador en conflicto](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Solo debe hacerlo una vez.

**Nota para usuarios de Windows 10 N:** Si el equipo ejecuta Windows 10 N, verá **el error "Code 28: la clase de instalación no está presente o no es válido"** en Device Manager después de conectar el casco de realidad mixta. Las ediciones N de Windows 10 no son compatibles con Windows Mixed Reality. Siga estas [instrucciones](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) para obtener más información.

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un mensaje indica "comprobar el cable USB" o "velocidad de USB insuficiente".

* Asegúrese de que está usando un puerto USB 3,0 compatible en su PC:
    * Asegúrese de que el cable USB del auricular está enchufado.
    * Ejecute la aplicación de [comprobación de PC de realidad mixta de Windows](https://aka.ms/pccheckapp) para asegurarse de que se admite el controlador USB 3,0 de su PC.
    * Pruebe cada uno de los demás puertos USB 3,0 del equipo. Algunos equipos tienen más de un controlador USB 3,0.
    * Desconecte temporalmente todos los dispositivos USB conectados al equipo y conecte solo los auriculares.
    * En los equipos personalizados, aunque un puerto se puede marcar como un puerto USB 3,0, puede estar conectado a un controlador USB 2,0. Con el casco conectado, abra Device Manager, busque y haga clic en cualquiera de los dispositivos enumerados desde el casco y, a continuación, vaya a **ver > dispositivos por conexión** .
* Pruebe el casco en otro equipo. Si ese equipo no es totalmente compatible con Windows Mixed Reality, proteja Device Manager para ver si ve el mensaje "velocidad de USB insuficiente". Si el casco no se enumera correctamente en varios equipos, el casco podría estar defectuoso.

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>El portal de realidad mixta no se inició automáticamente después de haber enchufado los auriculares.

Es posible que el casco no se haya detectado correctamente debido a un problema subyacente. Intente iniciar el portal de realidad mixta manualmente y busque los mensajes de error que aparecen. 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>El casco dejó de funcionar después de poner el equipo en suspensión, en modo de hibernación o al reiniciar el equipo con el casco conectado.

1. Abra Device Manager y confirme que el casco aparece en "dispositivos de realidad mixta".
2. Haga doble clic en el casco en "dispositivos de realidad mixta" y confirme que el estado del dispositivo indica que el dispositivo funciona correctamente.
3. Si ve un error "código 43" que indica que el dispositivo ha dejado de funcionar o si no ve los auriculares en la lista "dispositivos de realidad mixta", desconecte y reenchufe el cable USB del casco. Microsoft está investigando un posible problema de interoperabilidad entre software y controlador que puede producir este error. Este problema afecta a un número pequeño de equipos y se espera que se resuelva en una futura actualización del controlador de auriculares de realidad mixta.

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>El casco hace que el equipo genere una comprobación de errores (pantalla azul) al poner el equipo en suspensión o en modo de hibernación.

Microsoft está investigando un posible problema de interoperabilidad entre software y controlador que puede dar lugar a un pequeño número de equipos que pueden generar una comprobación de errores de "9F" (pantalla azul) cuando el equipo se pone en suspensión o en modo de hibernación con los auriculares conectados. Se espera que este problema se resuelva en una actualización futura del controlador de auriculares de realidad mixta.

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>El controlador de casco no se instaló automáticamente al enchufar el casco.

En los equipos nuevos o equipos con una copia recién instalada de Windows 10, el controlador de auriculares puede ponerse en cola detrás de otras actualizaciones de Windows y es posible que no se instale inmediatamente. Si tiene una edición "N" de Windows, tendrá que cambiar a una edición normal de Windows 10 para usar Windows Mixed Reality. Para instalarlo manualmente:

1. Vaya a **inicio > Device Manager** y busque en "otros dispositivos" un dispositivo de "sensores de hololens" con un signo de exclamación amarillo: ![ vista de Device Manager sensores de hololens](images/hololenssensors.png)
2. Haga clic con el botón derecho en el dispositivo y seleccione Propiedades. Si las propiedades del dispositivo leen **los controladores de este dispositivo no están instalados (código 28)** , cierre la ventana y continúe. Si hay otro mensaje, siga los pasos de solución de problemas en el resto de esta página.
![Código 28 de sensores de HoloLens en Device Manager](images/code28.png)
3. Vuelva a hacer clic con el botón derecho en el dispositivo y seleccione "actualizar controladores..." y, a continuación, "Buscar software de controlador actualizado" después de las actualizaciones del dispositivo, debería ver los auriculares que aparecen en "dispositivos de realidad mixta" en Device Manager: el ![ dispositivo de realidad mixta aparece en Device Manager](images/mixedrealitydevices.png)

Si la instalación manual no funciona o no encuentra el controlador en otros dispositivos, es probable que tenga que desinstalar el controlador existente y volver a instalarlo. Para ello:
1. Vaya a **inicio > Device Manager** y mire en "dispositivos de realidad mixta" para el casco. El estado del dispositivo debe indicar que "el dispositivo funciona correctamente".
2. Haga clic con el botón derecho en el dispositivo y seleccione "desinstalar dispositivo".
3. En el menú emergente nuevo que aparece, active la casilla "eliminar el software de controlador para este dispositivo" y, a continuación, seleccione "desinstalar".
4. Cuando termine, desconecte el casco del equipo y conéctelo de nuevo. Windows Update ahora descargará e instalará un nuevo controlador.

### <a name="troubleshooting-flowchart"></a>Diagrama de flujo de solución de problemas

![Conecte el casco y compruebe el cable USB.](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>Problemas de pantalla de realidad mixta con auriculares ##

### <a name="my-headset-displays-are-black"></a>Los auriculares aparecen en negro.

* Compruebe el rendimiento y la estabilidad del equipo:
    * Use el administrador de tareas para ver si se agotan los procesos de la CPU, la GPU o las unidades de disco del equipo.
    * Examine las aplicaciones y los registros de eventos del sistema de Windows (con Visor de eventos) para ver si tiene una aplicación que se bloquea con frecuencia y genera informes Informe de errores de Windows (WER).
    * Compruebe Windows Update para asegurarse de que la versión de Windows sea la actual. Es posible que tenga que seleccionar varias veces "buscar actualizaciones".
* Comprobar la estabilidad de la aplicación y el juego:
    * Asegúrese de que su equipo cumple los requisitos mínimos del sistema para ejecutar cualquier aplicación o juego que no funcione correctamente.    
    * Asegúrese de que la versión del controlador de GPU es reciente y compruebe si hay nuevos problemas de rendimiento y compatibilidad y regresiones en los controladores nuevos.
    * Si usa aplicaciones y juegos de SteamVR, asegúrese de que los componentes de SteamVR y Windows Mixed Reality para SteamVR están actualizados.
* Comprobar la compatibilidad del adaptador de HDMI:
    * Asegúrese de que el cable HDMI está enchufado.
    * Si usa un adaptador HDMI (por ejemplo, un adaptador de DisplayPort a HDMI), asegúrese de que es compatible con Windows Mixed Reality. El adaptador debe ser compatible con HDMI 2,0 y hay muchos adaptadores más antiguos que solo admiten 1080p. Consulte [adaptadores recomendados para Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
    * El orden de los conectores puede ser importante. Conecte el adaptador de HDMI al equipo antes de conectar los auriculares al adaptador, especialmente si usa un adaptador de USB a HDMI. 
    * Intente quitar los cables de extensión si los usa.
* Comprobar la compatibilidad de tarjetas y controladores de gráficos:
    * Pruebe el puerto HDMI de su PC con un monitor de PC. Algunos equipos pueden tener más de un puerto HDMI y no todos pueden estar activos.
    * Si el equipo tiene una unidad de procesamiento de gráficos (iGPU) integrada y una unidad de procesamiento de gráficos discretos (dGPU), asegúrese de que está conectado al puerto HDMI de su dGPU.<br> ![Puertos HDMI](images/HP_HDMI_Ports_s.png)
    * Compruebe la versión del controlador de GPU. Asegúrese de que es reciente, pero también preste atención a los nuevos problemas de rendimiento y compatibilidad y a las regresiones en los nuevos controladores.
    * Si usa la realidad mixta en un equipo portátil y ha instalado un controlador de gráficos más reciente desde el sitio web del fabricante de la tarjeta gráfica, intente cambiar al controlador de la tarjeta gráfica más reciente que se proporciona en el sitio web del fabricante del equipo o en Windows Update.
    * Si tiene varios monitores de PC conectados al equipo, intente desconectar temporalmente todos los equipos, excepto uno.
    * Si ha establecido una frecuencia de actualización personalizada para el monitor de PC, intente revertir temporalmente a una frecuencia de actualización estándar, como 60 Hz.
    * Si ha cambiado recientemente la tarjeta gráfica sin reinstalar Windows, compruebe que el monitor de auriculares todavía tiene instalado el controlador correcto. Con el casco enchufado, confirme que aparece "auricular de realidad mixta" en el nodo monitores de Device Manager.
    * Si el equipo tiene una tarjeta gráfica NVIDIA, asegúrese de que el software 3D Vision de NVIDIA esté deshabilitado.
    * En algunas tarjetas de gráficos (especialmente tarjetas gráficas más antiguas), es posible que el puerto HDMI no admita HDMI 2,0 o que no sea totalmente compatible con Windows Mixed Reality. Pruebe el puerto de DisplayPort de la tarjeta gráfica mediante un [adaptador de displayport 1,2 a HDMI 2,0 activo](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) .
    * Los equipos HP Omen con el número de producto de HP 1RJ99EA # ABU tienen puertos HDMI que no son compatibles con Windows Mixed Reality. Para ver esto, abra el "Asistente de soporte técnico de HP" y el número de producto se mostrará en la parte inferior de la aplicación.
    * Si el equipo tiene una tarjeta gráfica de la serie de AMD R9 y usa un casco de la realidad mixta de Samsung, deberá actualizar el firmware del casco a la versión 1.0.8 o posterior o posterior para poder usar el puerto HDMI de la tarjeta gráfica con los auriculares.
    * Si usa un libro de superficie 2, asegúrese de que está usando el [adaptador de USB-C de Surface-C para HDMI](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
* Busque un problema de hardware con auriculares de realidad mixta:
    * Para confirmar o descartar problemas de hardware con el casco de realidad mixta, intente conectar los auriculares de realidad mixta a otro equipo. 
    * Compruebe los problemas de configuración y compatibilidad de PC primero, ya que los síntomas son muy similares.
* Asegúrese de que el cable USB esté conectado a un puerto USB 3,0 o superior. Los puertos USB 3,0 tienen SS (súper velocidad) escrito junto a ellos. Con frecuencia (pero no siempre) se colorean de azul.        

Si es útil, consulte el diagrama de flujo de solución de problemas de pantalla negra de auriculares siguiente.

![Pantalla negra/no se puede ver nada](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>La pantalla de los auriculares se vuelve de color negro después de algún uso.

* Intente deshabilitar las características de suspensión o ahorro de energía USB que pueda tener su PC. Por ejemplo, [suspensión selectiva de USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) en opciones de energía de Windows, la opción "permitir que el equipo apague este dispositivo para ahorrar energía" en Device Manager y cualquier configuración de ahorro de energía USB en el firmware del equipo.
* Desconecte temporalmente cualquier otro dispositivo USB y periféricos conectados al equipo.
* Compruebe la versión del controlador de GPU. Asegúrese de que es reciente, pero también preste atención a los nuevos problemas de rendimiento y compatibilidad y a las regresiones en los nuevos controladores.

### <a name="one-of-the-displays-on-my-headset-is-black"></a>Una de las pantallas en el casco es negro.

* Si usa un adaptador HDMI, asegúrese de que es compatible con HDMI 2,0.
* Quite los cables de extensión USB y HDMI que esté usando.
* Asegúrese de que el controlador de gráficos esté actualizado.
* Pruebe el casco de realidad mixta en otro equipo.

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>El casco muestra el azul por un momento y, a continuación, se reinicializa el portal de realidad mixta.

Esto suele indicar un problema ocasional de confiabilidad de controlador USB en el equipo:
* Pruebe con otro puerto USB. El equipo puede tener varios controladores USB 3,0.
* Quite los cables de extensión (si procede).
* Intente desconectar todos los demás dispositivos USB del equipo.
* Intente conectar un concentrador USB 3,0 con tecnología externa a su PC y conecte los auriculares a la central.
* Si utiliza un equipo de escritorio, considere la posibilidad de comprar una tarjeta PCIe USB 3,0 para agregar otra controladora USB a su PC.

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>El casco hace que el equipo se bloquee o muestre una pantalla negra al iniciarse.

En algunos equipos, al mantener el casco conectado antes de encender o reiniciar el equipo puede interferir con el proceso de inicio. El equipo podría seleccionar los auriculares que aparecen como "monitor principal" para mostrar el progreso de inicio del equipo o se podría impedir que se iniciara correctamente y podría "bloquearse" o generar un código de error de pitido. El comportamiento depende en gran medida de la marca y el modelo de PC, y/o la marca y el modelo de la tarjeta gráfica. Para solucionar este error:
* Conecte los auriculares a un puerto diferente de la tarjeta gráfica (puede que tenga que usar un adaptador para usar los demás puertos).
* Asegúrese de que el firmware de BIOS/UEFI del equipo está actualizado (pero actualice el firmware de BIOS/UEFI del equipo si está familiarizado con esto).

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>El equipo o el casco muestran parpadeo, Flash o permanecen negros cuando se usa un equipo Surface.

* Asegúrese de que está usando un adaptador HDMI compatible con HDMI 2,0. Muchos adaptadores de HDMI anteriores solo admiten la resolución de 1080p, lo que no es suficiente para auriculares de realidad mixta.
* Asegúrese de que el controlador de gráficos esté actualizado. Además de comprobar Windows Update, puede que desee consultar el sitio web del fabricante del equipo para obtener un controlador de gráficos actualizado.
* Algunos dispositivos Surface son incompatibles con Windows Mixed Reality. Más información sobre la [compatibilidad y los requisitos](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)de las superficies.

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La pantalla del casco no funciona después de apagar y realizar un inicio rápido.

Desconecte el cable HDMI y el cable USB del casco y, a continuación, vuelva a conectarlos.

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Los auriculares se muestran muy entrecortado, pero la ventana de vista previa del portal de realidad mixta aparece bien.

* Asegúrese de que los recursos del sistema (CPU, memoria y unidad de disco duro) del equipo están disponibles y no se han fijado ni agotado por otra aplicación o proceso.
* Actualice el controlador de gráficos.

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Obtengo un error "la clase de instalación no está presente o no es válida" en Device Manager.

Si ve "sensores de HoloLens" con un signo de exclamación amarillo en Device Manager, haga doble clic en el dispositivo para obtener más detalles. Si ve un mensaje que dice "los controladores de este dispositivo no están instalados. (Código 28): la clase de instalación no está presente o no es válida. Esto suele deberse a que el equipo está ejecutando [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Tenga en cuenta que las ediciones N de Windows 10 no admiten Windows Mixed Reality, por lo que deberá instalar una versión que no sea de N de Windows 10.

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Mi entorno WMR es vibrar o se repite cuando se mueve el cabezal y muestra Double Vision.

En un equipo portátil con gráficos integrados y una GPU de NVIDIA, se produce un error después de un período de tiempo que parece hacer que un fotograma anterior se muestre después del fotograma siguiente, lo que da lugar a una doble visión cuanto más rápido mueve el cabezal en una guiñada, un tono o un desplazamiento. El problema parece estar en controladores después del controlador de gráficos Nvidia 436,48.  La instalación de este controlador corregirá el problema hasta que NVIDIA resuelva el problema en los controladores actualizados. Para obtener una instalación directa del controlador de gráficos de NVIDIA 436,48, visite [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Tengo la molestia cuando uso mis auriculares.
Para obtener información general acerca de la comodidad en Windows Mixed Reality, vea [Windows mixed reality sobre el estado de los auriculares, la seguridad y la comodidad](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort). Para obtener más información sobre el casco específico, consulte con el fabricante del casco.

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>¿Cómo puedo obtener una vista más clara en el casco?
Intente ajustar el ajuste del casco. Ajuste su posición en su superficie moviéndola hacia arriba, hacia abajo o hacia la izquierda y a la derecha, y ajuste las correas para que se sientan perfectamente.

Si el casco lo admite, también puede ajustar la configuración de la calibración. Si el casco tiene un botón para ajustar la calibración, úselo. Si no es así, vaya a **configuración > realidad mixta > calidad visual** y ajuste la calibración allí. Para obtener más información sobre la calibración de un dispositivo específico, consulte con el fabricante del casco.

## <a name="mixed-reality-portal-error-messages-and-problems"></a>Problemas y mensajes de error del portal de realidad mixta

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Obtengo un mensaje de error "algo salió mal" o tengo problemas en el portal de realidad mixta.

Reiniciar Windows Mixed Reality:
1. Desconecte ambos cables de auriculares del equipo.
2. Reinicia tu equipo.
3. Vuelva a conectar los auriculares.

Si eso no funciona, asegúrese de que el equipo reconoce los auriculares:
1. Seleccione Inicio.
2. Escriba "Administrador de dispositivos" en el cuadro de búsqueda y selecciónelo en la lista. 
3. Expanda "dispositivos de realidad mixta" y compruebe si aparece el casco. 

Si no aparece, intente lo siguiente:
1. Conecte los auriculares a puertos diferentes en el equipo, si está disponible.
2. Busque las actualizaciones de software más recientes desde Windows Update.
3. Desinstalar y reinstalar Windows Mixed Reality:
    1. Desconecte ambos cables de auriculares del equipo.
    2. Seleccione **configuración > realidad mixta > desinstalar** .
    3. Seleccione **configuración > dispositivos > Bluetooth & otros dispositivos** para desemparejar los controladores de movimiento. Seleccione cada controlador y, a continuación, seleccione "quitar dispositivo".
    4. Vuelva a conectar el casco al equipo para volver a instalar Windows Mixed Reality.
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>Obtengo un mensaje de error "comprobar el cable USB".

Conecte los auriculares a otro puerto USB (y asegúrese de que es un SuperSpeed USB 3,0). Además, pruebe a quitar cualquier dispositivo extender o concentrador entre los auriculares y el equipo.

### <a name="im-getting-a-check-your-display-cable-error-message"></a>Obtengo un mensaje de error "comprobar el cable de pantalla".

Pruebe lo siguiente:
* Conecte los auriculares a un DisplayPort 1,2 o posterior, o HDMI 1,4 o posterior. Asegúrese de que el puerto corresponde a la tarjeta de gráficos más avanzada del equipo.
* Si utiliza un adaptador, asegúrese de que sea compatible con 4K.
* Pruebe a usar un puerto HDMI diferente.
* Si tiene un monitor externo conectado a un puerto HDMI, intente conectarlo a un DisplayPort en su lugar y use el puerto HDMI para sus auriculares.


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>Códigos de error de "algo salió mal" y cómo resolverlos

| **Códigos de error de Windows 10** (versión 1809/versiones 1709, 1803) | **Sugerencias de solución de problemas y mensajes de error**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **Compruebe el cable para mostrar: Asegúrese de que el cable de la pantalla del casco esté conectado correctamente.** <br/><br/><ol start="1"><li>Desenchufe los cables USB y HDMI del casco y vuelva a conectarlos.</li><li>Compruebe Device Manager y confirme que en "monitores", el monitor "auriculares de realidad mixta" está presente.</li><li>Asegúrese de que los controladores de gráficos están actualizados (desde el sitio web del fabricante de la tarjeta gráfica).</li><li>Si usa un adaptador para conectar el casco, asegúrese de que [es compatible con Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Si la tarjeta gráfica tiene puertos de DisplayPort y HDMI, pruebe a usar el puerto de DisplayPort en la tarjeta gráfica y use un adaptador de DisplayPort-to-HDMI de realidad mixta compatible.</li><li>Pruebe otro puerto USB 3,0 en su PC</li></ol> |
|   1-5 / 2197815297-5  | **Compruebe el cable para mostrar: el casco que muestra no se pudo inicializar correctamente. Intente reiniciar el equipo y volver a conectar los auriculares.**<br/><br/>Windows Ve el monitor de auriculares, pero Windows Mixed Reality está teniendo problemas para comunicarse con las pantallas en el casco de realidad mixta. Para solucionar este error:<br/><ol start="1"><li>Asegúrese de que los controladores de gráficos están actualizados (desde el sitio web del fabricante de la tarjeta gráfica).</li><li>Si usa un adaptador para conectar el casco, asegúrese de que [es compatible con Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Si la tarjeta gráfica tiene puertos de DisplayPort y HDMI, pruebe a usar el puerto de DisplayPort en la tarjeta gráfica y use un adaptador de DisplayPort-to-HDMI de realidad mixta compatible.</li><li>Intente reiniciar el equipo.</li></ol> |
|   7-1, 7-2, 7-3/2181038087-1, 2181038087-2, 2181038087-3  | **Windows Mixed Reality tiene problemas para conectarse al casco. Pruebe a desconectar el casco y volver a conectarlo.**<br/><br/>No se pudo inicializar completamente el casco de realidad mixta. Lo más probable es que sea un error transitorio. Desconecte el casco y vuelva a conectarlo para resolver este problema.
|   7-4 / 2181038087-4  | **Windows Mixed Reality tiene problemas para conectarse al casco. Pruebe a desconectar el casco y volver a conectarlo.**<br/><br/>El controlador de casco de realidad mixta no pudo inicializar las cámaras de seguimiento en el casco. Lo más probable es que sea un error transitorio. Desconecte el casco y conéctelo de nuevo para resolver este problema.
|   7-5 / 2181038087-5  | **Windows Mixed Reality tiene problemas para conectarse al casco. Intente conectar el casco a otro puerto USB y desconecte temporalmente cualquier otro dispositivo USB conectado al equipo.**<br/><br/>Windows Mixed Reality perdió la sincronización entre las marcas de tiempo de fotogramas de la cámara de realidad mixta y las marcas de tiempo del equipo. Puede tratarse de un error transitorio o una indicación de problemas de integridad de la señal USB. Para solucionar este error:</li><li>Desconecte temporalmente todos los dispositivos y periféricos USB, quite todos los cables de extensión y conecte el casco.</li><li>Deshabilite las características de suspensión y ahorro de energía USB en el equipo, como la suspensión selectiva en las opciones de energía de Windows, la opción "permitir que el equipo apague este dispositivo para ahorrar energía" en Device Manager y cualquier configuración de ahorro de energía USB en el firmware del equipo.</li></ul>
|   7-6 / 2181038087-6  | **Hay un problema con el firmware del auricular. Pruebe a desconectar el casco y volver a conectarlo.** <br/><br/>Puede ser un error transitorio. Intente desconectar y volver a enchufar el casco. Si eso no funciona:</li><li>Compruebe las actualizaciones de Windows para asegurarse de que está ejecutando el controlador de auriculares más reciente disponible.</li><li>Pruebe el casco en otro equipo. Si ve el mismo mensaje de error, será necesario que se representen los auriculares.</li></ul>
|   7-7 / 2181038087-7  | **Windows Mixed Reality tiene problemas para conectarse al casco. Intente conectar el casco a otro puerto USB y desconecte temporalmente cualquier otro dispositivo USB conectado al equipo.**<br/><br/>El controlador de casco de realidad mixta no pudo inicializar el firmware en el casco. Puede ser un error transitorio. Intente desconectar y volver a enchufar el casco. Si eso no funciona:<li>Desconecte temporalmente dispositivos USB y periféricos que no necesite para ejecutar Windows Mixed Reality.</li><li>Compruebe las actualizaciones de Windows para asegurarse de que está ejecutando el controlador de auriculares más reciente disponible.</li></ul>
|   7-11 / 2181038087-11 | **La CPU es demasiado antigua para ser compatible con Windows Mixed Reality.**<br/><br/>El equipo no puede realizar la comprobación de compatibilidad porque la CPU no tiene el conjunto de instrucciones AVX requerido por los controladores de movimiento de realidad mixta. Necesitará un [equipo compatible con Windows Mixed Reality](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons).
|   7-12 / 2181038087-12 | **Los auriculares están conectados a una controladora USB incompatible. Intente conectar los auriculares a otro puerto USB, si está disponible. O bien, intente instalar un controlador USB de Microsoft en lugar de los controladores no compatibles.**<br/><br/>Los auriculares pueden estar conectados a un puerto USB conectado a un controlador de controlador USB que no sea de Microsoft. A menudo, estos controladores de controladora USB 3,0 no tienen la capacidad de leer y controlar el [descriptor de ContainerID](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows), que agrega las partes dispares del casco de realidad mixta en una unidad unida (para reproducir audio de los auriculares correctos, extraer el vídeo de las pantallas correctas y extraer los datos de seguimiento de los sensores correctos). Para cambiar el controlador de la controladora USB: <ol start="1"><li>Inicie Device Manager.</li><li>Expanda la categoría de controladoras de bus serie universal y haga clic con el botón secundario para desinstalar el controlador de cada elemento que incluya el texto "controlador de host extensible" **y** no tenga "Microsoft" en el nombre.</li><li>Seleccione "eliminar el software de controlador para este dispositivo" para asegurarse de que se quitan los controladores antiguos.</li><li>Compruebe que cada elemento que incluye el texto "controlador de host extensible" tiene "Microsoft" al final.</li><li>Conecte el HMD.</li></ol>Como alternativa, si el problema es intermitente, es posible que el HMD no responda correctamente a los comandos del controlador HMD. Para corregirlo, desconecte el HMD durante 30 segundos o más, y vuelva a conectarlo. | 
|   7-13 / 2181038087-13 | **Los auriculares están conectados a una controladora USB incompatible. Intente conectar los auriculares a otro puerto USB, si está disponible. Si no es así, deberá instalar un nuevo controlador USB 3,0.**<br/><br/>Windows Mixed Reality no puede sincronizar las marcas de tiempo de fotogramas de la cámara de realidad mixta con las marcas de tiempo del equipo. Lo más probable es que se deba a un controlador de host USB 3,0 no compatible que no admita ITP (paquetes de marca de tiempo isocrónicos). Póngase en contacto con el fabricante del equipo para ver si se puede habilitar ITP o cambiar a otro controlador de host USB con soporte de ITP. |
|   7-14 / 2181038087-14 | **Windows Mixed Reality tiene problemas para conectarse al casco. Pruebe a desconectar el casco y volver a conectarlo.**<br/><br/>Windows Mixed Reality tiene problemas para inicializar el sensor de presencia en el casco de realidad mixta. En Device Manager, el casco mostrará el mensaje de error "PoseThread no se pudo inicializar el sensor de presencia". Para solucionar este error:<br/><ol start="1"><li>Desconecte el casco y vuelva a conectarlo. Asegúrese de que el cable USB está enchufado.</li><li>Pruebe otro puerto USB en su PC.</li><li>Pruebe el casco en otro equipo para ver si el casco se enumera completamente en Device Manager de ese equipo.</li><li>Compruebe si hay algún otro controlador HID en conflicto instalado en el equipo, por ejemplo, desde el teclado o el mouse. (Busque cualquier dispositivo HID en Device Manager con un logotipo de signo de interrogación en ellos).</li><li>Si usa un auricular de la realidad mixta de Samsung con la versión 1709 o 1803 de Windows 10, siga las instrucciones del código de error 2181038087-12 para comprobar si el controlador USB 3,0 está ejecutando un controlador de controlador USB que no sea de Microsoft.</li></ol> |
|   7-15 / 2181038087-15 | **Windows Mixed Reality ha detectado un controlador WinUSB incompatible instalado.**<br/><br/><ol start="1"><li>Asegúrese de que el controlador WinUSB del equipo es el que viene con Windows y que los controladores USB de terceros no han sobrescrito la copia de WinUSB en el equipo.</li><li>Si el problema persiste, es posible que necesite recuperar o volver a instalar la instalación de Windows.</li></ol> |
|   13-11/-            | El portal de realidad mixta ha detectado un problema de registro de aplicaciones con Windows. Compruebe el registro de eventos de la aplicación (mediante Visor de eventos) para ver si hay más detalles. |
|   14-1/-            | El portal de realidad mixta tiene problemas al inicializar la pila de gráficos y composición. Para solucionar este error:<ul><li>Administrador de ventanas de escritorio (DWM, un componente clave de la pila de gráficos de Windows) puede estar bloqueado. Compruebe el registro de eventos de la aplicación (mediante Visor de eventos) para ver si se está produciendo.</li><li>Pruebe a realizar una desinstalación limpia del controlador de gráficos y, a continuación, instale el controlador de gráficos más reciente desde el sitio web del fabricante de la tarjeta gráfica.</li></ul> |
|   14-2/C0001160-101  | **Se produjo un problema al conectar con el casco. Intente quitar los cables de extensión que esté usando y asegúrese de que ha conectado los auriculares al puerto correcto para la tarjeta gráfica. Si utiliza adaptadores, asegúrese de que son compatibles con la realidad mixta. Si sigue teniendo problemas, intente actualizar el controlador de gráficos.**<br/><br/>No se pudo inicializar la pantalla de la realidad mixta y la pila de composición. Es posible que el controlador de tarjeta de gráficos o tarjeta gráfica de su PC no sea compatible con Windows Mixed Reality. Para comprobarlo: <ul><li>Compruebe que el equipo cumple los requisitos mínimos del sistema para Windows Mixed Reality.</li><li>Si usa equipos Dell Inspiron 5577 en Windows 10, versión 1809 o posterior, es posible que vea este error debido a un conflicto con la funcionalidad de postprocesamiento de gráficos TrueColor de Dell. Para solucionar este problema, use la aplicación TrueColor de Dell para desactivar la funcionalidad TrueColor y luego vuelva a ejecutar el portal de realidad mixta.</li><li>En un equipo de escritorio, instale el controlador de gráficos más reciente desde el sitio web del fabricante de la tarjeta gráfica. En un equipo portátil, instale el controlador de gráficos más reciente para su marca y modelo desde el sitio web del fabricante del equipo portátil.</li><li>Si tiene gráficos de terceros o muestra software o accesorios, desinstale temporalmente estas aplicaciones y controladores.</li><li>Seleccione "intentarlo de nuevo" para ver si se trata de un problema transitorio.</li></ul> |
|   14-3/-             | **Se produjo un problema al conectar con el casco. Intente quitar los cables de extensión que esté usando y asegúrese de que ha conectado los auriculares al puerto correcto para la tarjeta gráfica. Si utiliza adaptadores, asegúrese de que son compatibles con la realidad mixta. Si sigue teniendo problemas, intente actualizar el controlador de gráficos.** <br/><br/><ul><li>Si usa modos personalizados o frecuencias de actualización en el monitor de su PC, pruebe a establecer sus frecuencias de actualización en 60 Hz.</li><li>Asegúrese de que los adaptadores que usa son compatibles con Windows Mixed Reality.</li><li>Intente instalar el controlador de gráficos más reciente desde el sitio web del fabricante de la tarjeta gráfica.</li><li>Haga clic en "intentar de nuevo" para ver si se trata de un problema transitorio.</li></ul> |
| 14-4/-             | **Se produjo un problema al conectar con el casco. Intente quitar los cables de extensión que esté usando y asegúrese de que ha conectado los auriculares al puerto correcto para la tarjeta gráfica. Si utiliza adaptadores, asegúrese de que son compatibles con la realidad mixta. Si sigue teniendo problemas, intente actualizar el controlador de gráficos.** <br/><br/><ul><li>Es posible que el equipo tenga más monitores de PC conectados de los que pueda admitir el adaptador de gráficos. Desconecte todo menos el monitor de su equipo principal.</li><li>Asegúrese de que los adaptadores que usa son compatibles con Windows Mixed Reality.</li><li>Instale el controlador de gráficos más reciente desde el sitio web del fabricante de la tarjeta gráfica.</li><li>Haga clic en "intentar de nuevo" para ver si se trata de un problema transitorio.</li></ul> |
|   15-5/-             | **El portal de realidad mixta ha perdido la sincronización con la realidad mixta principal y los componentes de Windows de los que depende.**<br/><br/><ul><li>Esto puede deberse a un problema de rendimiento del equipo. Asegúrese de que la CPU, la GPU y la unidad de disco duro no estén fijas en el administrador de tareas.</li><li>Desconecte temporalmente el resto de dispositivos USB del equipo.</li><li>Reinicia tu equipo.</li></ul> |
|   -/H0002000-0    | **El sistema operativo de su equipo ha llegado a un estado no coincidente para Windows Mixed Reality**<br/><br/>Compruebe si hay actualizaciones en Windows Update. |
|   -/S0002261-101, S0002361-101 | **Un problema con un componente de Shell de realidad mixta impide que el portal de realidad mixta se inicie correctamente.**<br/><br/><ul><li>Abra el registro de la aplicación mediante Visor de eventos en su equipo para comprobar si hay bloqueos de la aplicación en torno a la hora a la que intentó iniciar Windows Mixed Reality.</li><li>Asegúrese de que el controlador de gráficos esté actualizado.</li><li>El adaptador de HDMI que está usando es incompatible con Windows Mixed Reality. Vea el adaptador de HDMI to mini display Port (DP) compatible y recomendado [aquí](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).</li></ul> |


## <a name="motion-controller-problems"></a>Problemas del controlador de movimiento

### <a name="my-motion-controllers-arent-working-properly"></a>Mis controladores de movimiento no funcionan correctamente.

Si los [controladores de movimiento](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) no funcionan, no se está conectando o si no ve una imagen de los controladores cuando tiene el casco, intente lo siguiente:
1. Asegúrese de que los controladores estén encendidos. Para activarlas, mantenga presionado el botón de Windows durante dos segundos.
2. Asegúrese de que los controladores estén totalmente cargados y reemplace las baterías si no lo están.
3. Apague y encienda los controladores mientras los mantiene delante. Mantenga presionado el botón de Windows durante cuatro segundos para desactivar un controlador y, a continuación, mantenga presionado el botón en dos segundos para activarlo. 
4. Seleccione **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo y asegúrese de que los controladores aparecen como emparejados. Si no es así, deberá [emparejarlos](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality). 
5. Asegúrese de que los controladores de movimiento aparecen como "conectados". "Emparejado" no significa necesariamente que los controladores estén conectados al equipo. Los controladores deben aparecer en la categoría "Mouse, teclado & el lápiz". Los controladores de movimiento en "otros dispositivos" no han superado el proceso de emparejamiento y no son funcionales. Comprobar los LED de los controladores de movimiento: los controladores iluminados brillantes están emparejados y conectados, los controladores dimly Lit no están conectados.
6. Vaya a **inicio > portal de realidad mixta** en su PC y seleccione "menú". Debería ver los controladores de movimiento enumerados, junto con un mensaje de estado:
    * Listo: todos los controladores están establecidos.
    * Seguimiento perdido: el portal de realidad mixta no puede encontrar los controladores. Manténgalos delante del casco y reinícielos presionando el botón Windows durante 4 segundos y, luego, de nuevo durante 2 segundos.
    * Batería baja: Reemplace las baterías del controlador.
7. Si usa un adaptador de Bluetooth USB externo, asegúrese de que está conectado a un puerto USB 2,0 negro. También debe estar enchufado en la medida de lo posible desde cualquier otro transmisor inalámbrico o unidad flash USB, incluido el conector USB de los auriculares. 
8. Compruebe que solo haya un radio Bluetooth en el equipo; para ello, haga clic con el botón derecho en el menú Inicio de Windows y seleccione Device Manager. Expanda la sección Bluetooth y busque un adaptador. Si usa la configuración de PC de escritorio con radio integrada, compruebe si hay una antena externa conectada. Si no hay ninguna antena externa conectada, puede causar problemas de seguimiento. O bien, use una llave de Bluetooth (USB) externa, deshabilite la funcionalidad de Bluetooth interna y reintente el emparejamiento y la conexión.
9. Cierre la ventana de configuración de Bluetooth Si está abierta. Si está abierto en segundo plano, se realizan muchas llamadas adicionales al protocolo Bluetooth.
10. Compruebe el nivel de batería virtual en el controlador de movimiento. En realidad mixta, encienda los controladores y podrá ver un icono de la batería. Si está en rojo, reemplace las baterías. Los informes de batería suelen ser más altos que el nivel real inmediatamente después de conectar un controlador. Espere unos 15 segundos para que el nivel de batería se estabilice y, a continuación, lea el nivel.
11. Quite los altavoces y auriculares Bluetooth de la **configuración > dispositivos > Bluetooth & otros dispositivos** y apague los dispositivos. Use el conector de auriculares o los altavoces integrados en los auriculares de la realidad mixta para disfrutar de la mejor experiencia de audio.
12. Si tiene otros dispositivos Bluetooth emparejados con su PC, como los auriculares o los controladores de juegos, quite algunos de ellos. Seleccione **configuración > dispositivos > Bluetooth & otros dispositivos del equipo** , seleccione los dispositivos y, a continuación, seleccione "quitar dispositivo".
13. Desconecte el cable USB del casco y conéctelo de nuevo al equipo para reiniciar la funcionalidad del controlador en el equipo.
14. Las luces del controlador parpadean cuando se están llevando a cabo una actualización de firmware. Espere a que se complete la actualización de firmware y los controladores deben aparecer en la realidad mixta.
15. Asegúrese de que su equipo está conectado a una red Wi-Fi de 5 GHz. Si el portátil está conectado a una red Wi-Fi de 2,4 GHz, normalmente comparte la conexión Bluetooth. Esto puede afectar negativamente al rendimiento de la red Wi-Fi o Bluetooth, en función del diseño del producto. Cambie la banda preferida a 5 GHz en la configuración del adaptador de red. Si la red no admite 5 GHz, se puede usar una llave Bluetooth en lugar de la capacidad interna de Bluetooth.
16. Si la configuración de Bluetooth tiene controladores de movimiento que ya están emparejados, Windows no detectará los nuevos dispositivos hasta que se quiten (si se han agregado con un dispositivo de protección específico, solo se pueden quitar con ese adaptador).
17. Si su equipo tiene Bluetooth integrado y tiene problemas de conexión, pruebe a usar un adaptador de Bluetooth USB en su lugar. Para ello, deberá desactivar la radio Bluetooth integrada en Device Manager y, a continuación, emparejar los demás dispositivos Bluetooth con el nuevo adaptador.

### <a name="motion-controller-troubleshooting-flowchart"></a>Diagrama de flujo de solución de problemas del controlador de movimiento

![Diagrama de flujo de solución de problemas para controladores de movimiento](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>Mi controlador está atascado en un reinicio infinito (timbre después del ciclo de LED).

Se trata de un indicador crítico de la batería, por lo que debe asegurarse de que tiene baterías nuevas en el dispositivo. Si el problema persiste, realice la [recuperación del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) para restablecer el controlador a la configuración de fábrica.

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Estoy intentando emparejar mis controladores, pero nunca aparecen en el menú "agregar un nuevo dispositivo" en la configuración de Bluetooth.

Compruebe que ya no tiene controladores emparejados, quítelos e inténtelo de nuevo. Si el problema persiste, reinicie el equipo e inténtelo de nuevo. Si se produce un error, consulte las [preguntas más frecuentes sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>Las velocidades de Wi-Fi se vuelven lentas en mi cuaderno cuando se activan los controladores de movimiento.

El cuaderno puede compartir su antena Wi-Fi con Bluetooth cuando se conecta a un punto de acceso de 2,4 GHz. Compruebe desde el administrador de dispositivos si puede cambiar la preferencia de banda a 5 GHz. Si la red de 5 GHz no está disponible y el rendimiento se ve afectado gravemente, considere la posibilidad de usar una llave de Bluetooth.

![La configuración de selección de banda wifi se puede encontrar a través del administrador de dispositivos](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>El segundo controlador tarda mucho tiempo en volver a conectarse.

Algunos dispositivos de radio Intel anteriores experimentan este problema si los controladores de movimiento se encienden al mismo tiempo. Evite el encendido de controladores al mismo tiempo.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Mi radio Bluetooth de Qualcomm no puede emparejar controladores después de un bloqueo del equipo.

Los controladores de radio de Bluetooth de Qualcomm (QCA) anteriores a 10.0.0.448 pueden acabar en mal estado después de un bloqueo de Windows. Apague el equipo completamente para solucionar este problema. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Tengo un seguimiento deficiente del controlador con radio Marvell.

Vaya a **Device Manager > adaptador de radio bluetooth > Marvell AVASTAR > de propiedades de > controlador** y asegúrese de que está usando el controlador 15.68.9210.47 o posterior.

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>El portal de realidad mixta funciona, pero los controladores de movimiento están realizando un seguimiento deficiente (los controladores siguen desplazando, etc.).

1. Algunas condiciones de iluminación pueden afectar al seguimiento. Asegúrese de que no está expuesto a la luz solar directa y que no tiene una gran cantidad de fuentes de luz de punto visibles para su HMD (por ejemplo, cadenas de luces como un árbol de Navidad). 
2. Consulte las [preguntas más frecuentes sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Estos síntomas suelen deberse a errores de comunicación entre el controlador y el equipo host, e indican una calidad de vínculo de Bluetooth deficiente.

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Los LED del controlador de movimiento no están encendidos, pero los botones y el stick analógico siguen funcionando en el portal de realidad mixta.

La memoria caché de calibración del controlador de movimiento puede estar dañada. Para eliminar la memoria caché, ejecute el siguiente comando en un símbolo del sistema de administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Esta carpeta no es accesible en el explorador de Windows y solo se puede modificar desde un símbolo del sistema de administrador. Después de eliminar la carpeta, reinicie el equipo y vuelva a conectar los controladores de movimiento para restaurar los archivos de calibración.

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Los controladores de movimiento no aparecen en aplicaciones y juegos de SteamVR.

Si puede ver sus controladores de movimiento en la casa de acantilado, pero no en aplicaciones y juegos de SteamVR, es posible que el controlador del modelo de controlador de movimiento no esté instalado correctamente. Este controlador se descarga e instala automáticamente a través de Windows Update, pero si se encuentra en un equipo que tiene directivas empresariales o si Windows Update está restringido de otra forma, es posible que deba instalarlo manualmente. Para comprobar que el controlador del modelo de controlador de movimiento está instalado correctamente:
1. Active ambos controladores de movimiento y asegúrese de que se muestran como "conectados" en la aplicación de configuración en **dispositivos > Bluetooth & otros dispositivos** . Si no aparecen o no aparecen como "emparejadas", [empareje](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Abra Device Manager y busque "Motion Controller-left" y "Motion Controller-Right" en "Bluetooth".
3. Seleccione un dispositivo y, a continuación, vaya a **ver > dispositivos por conexión** .
4. Ahora verá una vista de los dispositivos Bluetooth del controlador de movimiento que se acumulan en el radio Bluetooth. En el mismo nodo, los dos controladores de movimiento deben ser dos dispositivos "dispositivo HID Bluetooth" y, en cada dispositivo HID Bluetooth, deben ser dispositivos denominados "controlador de movimiento" (con iconos grises).
5. Haga doble clic en cada uno de los dispositivos de "controlador de movimiento" y vaya a la pestaña **controlador** . Confirme que la versión de controlador indicada corresponde a una de [estas versiones del controlador del modelo de controlador de movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history).

Para descargar e instalar manualmente el controlador del modelo de controlador de movimiento, visite [esta página](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) y busque la versión del controlador correspondiente a su versión de Windows 10. Las instrucciones de instalación están disponibles en la página de descarga.

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>La actualización de firmware de los controladores de movimiento tarda mucho más de dos minutos.

Consulte las [preguntas más frecuentes sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Una calidad de vínculo Bluetooth deficiente suele ser la causa de estos problemas.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Acabo de insertar baterías nuevas, pero el nivel de batería virtual del controlador no indica el nivel completo.

El nivel de batería del controlador de movimiento está optimizado para baterías AA. Es posible que algunas baterías recargables de baja tensión no informen como completas, aunque estén totalmente cargadas.

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>El controlador no vibra cuando la batería es baja.

Los hápticos se deshabilitan cuando el nivel de batería es bajo. Reemplace las baterías.

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>El dispositivo vibra tres veces y después se apaga.

Las baterías se están agotando y alcanzan el umbral de reducción. Reemplace las baterías.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>El panel táctil del controlador de movimiento de Samsung está fuera del centro o tiene una zona muerta.

Probablemente se trate de un defecto de hardware y debe volver al fabricante del distribuidor o equipo para reemplazarlo o cambiarlo.

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>El controlador no funciona correctamente y no puedo actualizar el dispositivo.

Restáurela en las condiciones de fábrica (necesitará baterías nuevas):
1. Desconecte y apague los controladores.
2. Abra la cubierta de la batería.
3. Inserte las nuevas baterías.
4. Mantenga presionado el botón de emparejamiento (la pestaña en la parte inferior de las baterías).
5. Mientras mantiene presionado el botón de emparejamiento, encienda el controlador presionando y manteniendo presionado el botón de Windows durante cinco segundos (mantenga presionados ambos botones).
6. Suelte los botones y espere a que el controlador se encienda. Esto tarda hasta 15 segundos y no hay ningún indicador cuando se está produciendo la recuperación del dispositivo. Si el dispositivo se enciende inmediatamente en el lanzamiento del botón, la secuencia del botón de recuperación no se registró y tendrá que intentarlo de nuevo.
7. Vaya a **configuración > Bluetooth > otros dispositivos** y seleccione "controlador de movimiento-izquierda" o "controlador de movimiento-derecha" y "quitar dispositivo") para quitar las asociaciones de controlador antiguas de la configuración de Bluetooth. 
8. Vuelva a emparejar el controlador con el equipo.
9. Después de conectarse con el host y HMD, el dispositivo se actualizará al firmware disponible más reciente.

### <a name="lights-and-indicators"></a>Luces e indicadores

El LED constelación ring y hápticos indican el estado del controlador de movimiento.

| State    | Qué hace que el estado | Comportamiento de luz y vibración asociado al estado |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Encendido**               | Mantenga presionado el botón de Windows en el controlador durante dos segundos para activar el controlador.       | Los LED se encienden y el controlador vibra una vez. |
| **Apagado**              | Mantenga presionado el botón de Windows en el controlador durante cuatro segundos para desactivar el controlador.      | Los LED se apagan y el controlador vibra dos veces. |
| **En espera**               | El controlador entra en estado de inactividad automáticamente cuando se motionless durante 30 segundos. El controlador se activa automáticamente cuando detecta movimiento excepto cuando el dispositivo no está emparejado con el equipo host. En ese caso, será necesario presionar un botón para activarlo. | Los LED se apagan y parpadean cada tres segundos mientras están en estado de suspensión. |
| **Emparejamiento**                | Mantenga presionado el botón de emparejamiento en la batería durante tres segundos.     | Los LED se pulsan lentamente en el modo de emparejamiento y van sólidos al salir del modo de emparejamiento. El controlador vibra una vez si el emparejamiento fue correcto o vibra tres veces si el emparejamiento no se realiza correctamente y se agota el tiempo de espera. |
| **El controlador se conecta/desconecta del equipo** | El controlador se conecta correctamente al equipo después de encenderlo o el controlador se desconecta del equipo durante el uso por algún motivo.| El controlador vibra una vez en la conexión o desconexión del equipo. |
| **Nivel de batería baja**      | El nivel de batería es bajo.| No hay ninguna indicación de vibración o LED cuando la batería es baja. Hay un icono de indicador de la batería en el controlador de la representación del controlador en el casco. Cuando la batería es baja, el icono de indicador mostrará 1/4 lleno. |
| **Nivel crítico de batería** | Durante el encendido cuando el nivel de batería es "crítico". El nivel de batería "crítico" significa que no hay suficiente energía y el controlador se desactivará automáticamente.| El controlador vibra tres veces cuando se activa y se desactiva automáticamente. A medida que se aproxima a este estado, el icono de indicador de la batería se mostrará en rojo. |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>¿Cómo se puede saber si utilizo tecnología Bluetooth?

Los controladores de movimiento usan la misma tecnología Bluetooth que se encuentra en muchos dispositivos de consumo y están diseñados para funcionar con la capacidad de Bluetooth incluida en cualquier equipo reciente. Para comprobar que el equipo tiene una radio Bluetooth (si el dispositivo pasa el comprobador de compatibilidad de realidad mixta): 
* Haga clic con el botón derecho en el menú Inicio de Windows y seleccione "Device Manager". 
* Expanda la sección Bluetooth y busque un adaptador. 
* Si su equipo no tiene Bluetooth, un dispositivo de protección recomendado es el [adaptador USB Bluetooth 4,0 de baja energía](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom). \
![Captura de pantalla de un Device Manager de ejemplo. El adaptador es el radio Bluetooth.](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>Mi PC tiene tecnología Bluetooth, pero tengo problemas con los controladores de movimiento.

Los controladores de movimiento deben funcionar con otros teclados, ratones y controladores de juegos Bluetooth, pero la experiencia variará en función del modelo de teclado, mouse o dispositivo de juego que use. Estas son algunas de las cosas que puede hacer para mejorar el rendimiento:
* Si el equipo tiene Bluetooth pero sigue teniendo problemas con los controladores de movimiento, considere la posibilidad de reemplazar la radio Bluetooth con el adaptador Bluetooth externo que se puede conectar a USB. Tenga en cuenta que solo puede tener un adaptador de radio Bluetooth activo a la vez. Si conecta una radio externa además de una radio existente, deberá deshabilitar la radio Bluetooth existente en Device Manager (haga clic con el botón derecho en el adaptador y seleccione "deshabilitar dispositivo") y elimine el emparejamiento de todos los dispositivos Bluetooth anteriores.
* Si utiliza un adaptador de Bluetooth USB, conéctelo a un puerto USB 2,0 (los puertos 2,0 son negros y no tienen la etiqueta "SS"), si están disponibles. El puerto debe estar separado físicamente de:
    - el conector USB de HMD
    - unidades flash
    - unidades de disco duro
    - los receptores USB inalámbricos como los de teclados o ratones ideales, conectan el adaptador de Bluetooth USB en el lado opuesto del equipo lo más lejos posible de estos otros conectores.
* No instale ningún software de terceros.
* Cierre la ventana de configuración de Bluetooth Si está abierta. Dejándolo abierto en segundo plano significa que se realizan muchas llamadas adicionales al protocolo Bluetooth.
* Deshabilite la opción "Mostrar notificación para conectarse con el par SWIFT" en Bluetooth & otros dispositivos para reducir la actividad de detección de radio de host.
* Si usa una tarjeta Bluetooth interna, asegúrese de que está usando una antena Bluetooth externa. 
  * La falta de una antena Bluetooth externa en este caso se sabe que causa problemas de seguimiento. 
  * Si esto no funciona, use una llave de Bluetooth (USB) externa después de deshabilitar el Bluetooth interno.
* Es importante que el dispositivo aparezca en la categoría "Mouse, teclado & el lápiz" en la configuración de Bluetooth. Si se trata de "otros dispositivos", desemparejar y emparejar el dispositivo.
* Quite, elimine el emparejamiento y apague auriculares y altavoces Bluetooth. No se admiten con Windows Mixed Reality. Puede usar el conector para auriculares o los altavoces integrados en el casco de la realidad mixta para disfrutar de la mejor experiencia de audio.

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>¿Cómo puedo emparejar mis controladores de movimiento a un casco de realidad mixta de Windows con radio Bluetooth integrado o devolverlos a su emparejamiento de fábrica?

Algunos auriculares Windows Mixed Reality, incluidos Acer OJO 500 y Samsung Odyssey +, tienen radios Bluetooth integrados para su uso con controladores de movimiento. Los controladores de movimiento que se incluyen con estos auriculares se emparejan previamente con los auriculares de la fábrica y no requieren que el equipo tenga una radio Bluetooth independiente. Estos controladores de movimiento se _pueden_ emparejar manualmente con la radio Bluetooth de su equipo, por ejemplo, para su uso con auriculares de realidad mixta de Windows que no tienen radios Bluetooth integrados. Para devolver los controladores de movimiento a su emparejamiento de fábrica, o bien, para emparejarlos con un casco de realidad mixta de Windows con radio Bluetooth integrado, ejecute la aplicación complementaria de dispositivo del auricular (por ejemplo, la aplicación "Acer OJO 500" o la aplicación "Samsung HMD Odyssey + Setup", que se instala automáticamente la primera vez que el casco está enchufado) y siga las instrucciones para emparejar controladores de movimiento.


## <a name="performance-questions"></a>Preguntas sobre rendimiento

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>¿Cómo se puede saber si el casco de la realidad mixta de Windows se representa con una velocidad de fotogramas de 60 Hz o 90Hz?

Consulte la pestaña **rendimiento del portal de dispositivos >** . 

**Nota** : Si tiene una GPU discreta con puertos HDMI 2,0 y una CPU con cuatro o más núcleos físicos, debe obtener 90 Hz. Si la GPU solo tiene una salida HDMI 1,4, puede usar un adaptador de DisplayPort a [hdmi 2,0](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) como solución alternativa. 

**Nota** : los **auriculares que se muestran > configuración de calidad visual** solo afectan a la representación de la experiencia principal de Windows Mixed Reality.

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>¿Qué hago si el equipo parece estar ejecutándose lentamente?

El sistema puede ser lento por muchas razones y, en la mayoría de los casos, esto se producirá después de unos segundos. Si experimenta este problema durante largos períodos de tiempo:
1. Cierre todas las aplicaciones sin usar en el escritorio.
2. Asegúrese de que el portátil esté conectado a una fuente de alimentación.
3. Asegúrese de que el equipo no se está preparando.
4. Reduzca la calidad visual en la Página principal de Windows Mixed Reality.
5. Asegúrese de que dispone de los controladores de gráficos más recientes para su PC (consulte la sección Controladores de gráficos).

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Mi PC se está preparando mientras ejecuto las experiencias de realidad mixta. Cómo mantenerla en frío?

1. Asegúrese de que la batería esté cargada y de que la fuente de alimentación esté conectada.
2. Asegúrese de que los ventiladores que impidan o salgan del equipo no estén bloqueados.
3. Use el equipo en un entorno relativamente frío.
4. Asegúrese de que no haya fuentes de calor (por ejemplo, el sol o los orificios de ventilación) señalados al equipo.

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Los objetos visuales son entrecortado, se cargan lentamente o no tienen un aspecto correcto.
* Asegúrese de que el casco está enchufado en la tarjeta gráfica correcta del equipo. Algunos equipos tienen tarjetas de gráficos integradas y discretas. Por lo general, la tarjeta discreta proporcionará el mejor rendimiento. [Más información sobre el hardware de PC](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* Cierre las aplicaciones no utilizadas en el escritorio.
* Asegúrese de que el casco se ajusta perfectamente (muévalo hacia abajo y hacia arriba o hacia la izquierda y derecha para ajustar).
* Ajusta la configuración visual de los auriculares en **configuración > realidad mixta > pantalla de auriculares** . Cuando "calidad visual" esté establecido en "automático", elegiremos la mejor experiencia de realidad mixta para tu equipo. Para obtener una experiencia con más detalles visuales, establezca "calidad visual" en "alto". Si los objetos visuales son entrecortado, puede que desee seleccionar un valor inferior.
* Intente ajustar la calibración del casco. Las lentes deben ajustarse para que coincidan con la distancia de Interpupillary (IPD), la distancia entre los alumnos. Si no conoce el IPD, un Optometrist debe ser capaz de medirlo. También hay sitios web diseñados para medir IPD. Una vez que conozca el IPD, use el botón de calibración del casco para realizar ajustes. Si el casco no tiene un botón de calibración, seleccione la **configuración > realidad mixta > auriculares para mostrar** y ajustar el "control de calibración".


## <a name="tracking-system-problems"></a>Seguimiento de problemas del sistema

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>El sistema no puede encontrar el límite y se está presentando la interfaz de usuario del programa de instalación.

Esto significa que el sistema de seguimiento no pudo reconocer el entorno. Si está en un entorno nuevo, debe configurar el [límite](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary). Si ha usado anteriormente el dispositivo en este entorno y ha configurado un límite:
* Asegúrese de que el salón tenga suficiente luz.
* Asegúrese de que ha desgastado el dispositivo y ha examinado el salón. El dispositivo debe observar su entorno para saber dónde está. No encontrará los límites si está sentado en un escritorio o una tabla.
* Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectar el dispositivo.
* Es posible que haya cambiado en su entorno y que el dispositivo ya no lo reconozca. Intente configurar un nuevo límite.

Si estos pasos no resuelven el problema, elimine los datos del entorno y vuelva a configurar el límite.

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>El sistema se presenta con una interfaz de usuario que me pide que elija el programa de instalación de todas las experiencias o que se encuentren o se hayan colocado, y veo mis límites.

El dispositivo está tardando demasiado tiempo en encontrar los límites. Puede omitir este mensaje eligiendo la opción para usar un límite y se le dirigirá a la Página principal de Windows Mixed Reality con los límites presentes.

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>A menudo veo un mensaje que dice "he perdido mis límites".

El sistema de seguimiento está realizando un seguimiento e identificación del entorno. En este estado, el dispositivo ya no puede mostrar los límites y el casco cambia a 3DOF para evitar que se produzcan problemas en el mundo real hasta que vuelva a ubicar los límites. Para solucionar este error:
1. Asegúrese de que el salón tenga suficiente luz.
2. Vuelva a ejecutar el programa de instalación si ha redecorado o remodelado recientemente el salón.
3. Desconecte el dispositivo, cierre Windows Mixed Reality y conéctelo de nuevo.
4. Borre los datos del entorno y vuelva a configurar el dispositivo.
5. Si el mensaje persiste, póngase en contacto con el servicio de soporte al cliente.

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Me puedo buscar, pero no puedo traducir (Estoy atascado en 3DOF).

Esto significa que el sistema de seguimiento no puede generar una suposición o la aplicación se ha detenido con los nuevos datos de pose que se van a representar. Compruebe lo siguiente:
* Asegúrese de que el salón tenga suficiente luz.
* Asegúrese de que el salón tenga suficientes detalles para realizar el seguimiento.
* Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectar el dispositivo.
* Si el mensaje persiste, póngase en contacto con el servicio de soporte al cliente.

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>La vista del HMD está completamente inmovilizada.

Normalmente, esto significa que se ha producido un error en la aplicación o en un componente de nivel de sistema. Intente:
1. Presione el botón "Inicio" para salir de la aplicación.
2. Desconecte el dispositivo, cierre PRM y vuelva a conectar el dispositivo.
3. Reinicie el equipo.

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>A menudo veo un borde negro alrededor de los bordes de la vista en el HMD. A veces parece que busco un túnel.

Esto significa que la aplicación no puede alcanzar la velocidad de fotogramas en el equipo y el sistema usa fotogramas anteriores para presentar la vista en el HMD. Puesto que las aplicaciones solo representan la parte del mundo que se está viendo, si no alcanzan sistemáticamente sus velocidades de fotogramas, el sistema intentará seguir representando el mundo desde un punto de vista anterior y rellenará los detalles que faltan con negro. Si esto sucede con frecuencia:
1. Cierre o finalice todos los programas innecesarios para liberar memoria y CPU.
2. Reduzca los valores de configuración de la aplicación.
3. Reduzca los valores de configuración en la configuración de Windows Mixed Reality.

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>La vista de HMD está vibrando y repite mucho.

Hay varias razones por las que esto puede ocurrir. Las causas principales son que el sistema no puede representar el contenido en los auriculares o que el sistema de seguimiento está experimentando problemas. Compruebe lo siguiente:
1. Asegúrese de que el equipo no está en la contención de recursos. Abra el administrador de tareas y asegúrese de que los recursos de proceso son gratis (por ejemplo, 80% de CPU libres, 400 MB de RAM y e/s de disco es inferior a 80%).
2. Asegúrese de que dispone de los controladores de gráficos más recientes para su hardware. Consulte la sección controlador de gráficos para obtener más información.
3. Asegúrese de que el salón tenga suficiente luz.
4. Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectar el dispositivo.
5. Reinicie el PC.
6. Si el problema persiste, póngase en contacto con el servicio de soporte al cliente.

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>El mundo se inmovilizó brevemente y quizás se inclina o voltea hacia arriba antes de volver a la normalidad.

Esto puede deberse a que una aplicación o un componente de nivel de sistema ha provocado un error irrecuperable o una falta temporal de memoria o de recursos de CPU. Compruebe lo siguiente:
1. Abra "Administrador de tareas" y asegúrese de que tiene al menos un 20% de CPU libre y 400 MB de memoria libre (por ejemplo, 80% de CPU libres, 400 MB de RAM y e/s de disco es inferior a 80%).
2. Abra "Visor de eventos" y vaya a **registros de Windows > la aplicación y** las entradas de eventos de error aproximadamente en el momento de la inmovilización. Compruebe si se ha bloqueado algún proceso.
3. Intente reiniciar el equipo si el problema persiste.

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>El mundo se ha volteado hacia arriba y se ha vuelto a la normalidad.

Esto se debe normalmente a errores en la obtención de datos de sensor desde los auriculares para informar sobre los algoritmos de seguimiento. Si esto sucede con frecuencia:
1. Conecte los auriculares a otro puerto USB 3,0.
2. Conecte los auriculares directamente al equipo en lugar de a un concentrador USB 3,0.
3. Si el problema persiste, póngase en contacto con el servicio de soporte al cliente.

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>El mundo está inclinado, pero puedo navegar y desplazarse por Windows Mixed Reality.

Esto suele deberse a que los errores de datos del sensor se registran en los datos del entorno que se almacenan en el equipo. Esto puede hacer que la realidad mixta de Windows parezca inclinada, a veces permanentemente. Pruebe lo siguiente:
1. Desenchufe el HMD, cierre Windows Mixed Reality y vuelva a conectar el casco.
2. Reinicie el equipo.
3. Borre los datos del entorno.

## <a name="webvr-questions"></a>Preguntas sobre WebVR

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>¿Por qué no veo mis controladores al ver el contenido de VR desde Edge?

No todo el contenido de WebVR se crea para admitir controladores de movimiento. WebVR permite a los desarrolladores de contenido admitir distintos tipos de entrada, como controladores de juegos o controladores de movimiento. Si no ve los controladores en un sitio, es probable que no tenga compatibilidad con el controlador de movimiento.

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>¿Por qué no puedo usar el mouse en una vista WebVR envolvente?

Esta es una característica opcional de la especificación WebVR. No todos los exploradores admiten esta característica y no se crea todo el contenido de WebVR para admitir la entrada del mouse. WebVR permite a los desarrolladores de contenido admitir distintos tipos de entrada, como el mouse, el teclado, los controladores de juegos o los controladores de movimiento. El comportamiento de la entrada del mouse varía según el explorador. Dentro de Microsoft Edge, los autores de sitios web deben asegurarse de que usan "pointerlock" cuando se presentan al casco para que la entrada del mouse funcione.

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>¿Por qué el controlador se parece a un Naopak/Oculus, tiene una orientación extraña o los botones están asignados incorrectamente?

Es probable que el sitio web no tenga compatibilidad total con el controlador de movimiento.

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>¿Por qué no puedo ver vídeos de 360 Degrees de YouTube/Facebook/Vimeo/The Guardian/New York Times, etc. desde Edge en VR?

Al igual que cualquier otra especificación web o estándar, el autor tiene la opción de implementarlo o no. Existe una especificación de WebVR que permite que los sitios web inicien experiencias de VR directamente desde el explorador y que los autores de estos sitios web no hayan implementado esta especificación en este momento. Puede haber aplicaciones descargables en algunas plataformas que permitan ver el contenido de VR de estos proveedores.

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>¿Por qué no puedo especificar VR desde Firefox o Chrome?

WebVR solo es compatible con dispositivos de Windows Mixed Reality en Edge en este momento.

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Cuando se especifica VR desde un sitio web, ¿por qué veo una pantalla en blanco en el casco?

Es posible que el sitio web no haya implementado compatibilidad con máquinas con varias GPU (incluidos los equipos portátiles de GPU híbrida). Intente:
* Recargue la página.
* En equipos de escritorio, conecte los auriculares al mismo adaptador de gráficos que el monitor que muestra Microsoft Edge. Conecte ambos en la tarjeta de gráficos de mayor potencia, no en el adaptador de gráficos integrado.

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Al salir de VR al ver un vídeo desde la periferia, el sonido continúa jugando, pero la ventana del borde está atenuada.

Se trata de un problema conocido al ejecutar WebVR desde Edge en el cliffhouse de realidad mixta. Para resolverlo, presione ESC en el teclado en lugar de presionar el botón Windows para salir de la experiencia WebVR, o bien Active la ventana de borde atenuado seleccionándola y, a continuación, detenga el vídeo.

### <a name="can-i-use-webvr-on-the-hololens"></a>¿Puedo usar WebVR en HoloLens?

En este momento, Microsoft no ha anunciado nada sobre WebVR en HoloLens.

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>¿Por qué mi vista está en el nivel inferior al ver el contenido de WebVR desde el perímetro?

El sitio web no admite correctamente auriculares con Windows Mixed Reality. Para solucionar este problema:
1. Coloque los auriculares en el suelo del espacio.
2. Vaya a la página WebVR con Microsoft Edge en el escritorio (no en la realidad mixta).
3. Haga clic en el botón de la página web para especificar VR.
4. Espere 5-10 segundos para que la experiencia entre en el modo inmersivo completo.
5. Seleccione el casco y colóquelo en la cabeza.

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>La pantalla tiene una resolución muy baja en algunas experiencias de WebVR.

Los sitios web no admiten correctamente auriculares de alta resolución. Para solucionar este problema:
* Si va a iniciar WebVR desde el escritorio (en lugar de desde el cliffhouse de realidad mixta), asegúrese de que la ventana está maximizada antes de escribir VR.
* Evite cambiar el tamaño de la ventana de Microsoft Edge después de haber escrito VR.

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>¿Por qué se sale de la vista envolvente WebVR al cambiar las pestañas del explorador?

Este es el comportamiento esperado. Por motivos de seguridad, solo la pestaña del explorador activo puede acceder a los auriculares conectados.

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>¿Por qué no puedo oír audio en una experiencia de WebVR determinada?

Es posible que el sitio web use el formato de archivo de audio OGG, que Microsoft Edge no admite actualmente.

Puede notificar sitios rotos directamente al equipo del explorador Microsoft Edge en el [rastreador de problemas](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)o a través de twitter con [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>¿Por qué los comentarios hápticos no funcionan en WebVR con los controladores de movimiento?

Microsoft Edge no es compatible actualmente con hápticos en las extensiones de la API del controlador de juegos de WebVR.


## <a name="steamvr-questions"></a>Preguntas sobre SteamVR

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>¿Cómo puedo jugar a SteamVR Games en mi micrófono con Windows Mixed Reality?

Debe instalar Windows Mixed Reality para SteamVR en su PC y configurar SteamVR:
* [Descargue e instale SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe).
* Inicie SteamVR. El tutorial de SteamVR debe iniciarse automáticamente.
* Conecte los auriculares al equipo y encienda los controladores de movimiento.
* Una vez que se haya cargado la Página principal de Windows Mixed Reality y que los controladores estén visibles, abra la aplicación de vapor en el escritorio.
* Use la aplicación de vapor para iniciar un juego de SteamVR desde la biblioteca de vapor. Para iniciar juegos de SteamVR sin sacar el casco, puede buscarlos e iniciarlos en el inicio de Windows Mixed Reality **> todas las aplicaciones** . 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Aparece un mensaje que dice "para usar SteamVR con Windows Mixed Reality, debe instalar la Windows Update más reciente" o "modo de desarrollador de Windows necesario".

1. Asegúrese de que el equipo está ejecutando la versión más reciente de Windows 10. Para comprobarlo, vaya a **configuración > sistema > acerca de** . En "Especificaciones de Windows", asegúrese de que "compilación de SO" sea 16299,64 o superior.
2. Asegúrese de que no tiene ninguna actualización en espera para descargar o instalar. Vaya a **configuración > actualizar & seguridad > Windows Update** y seleccione "buscar actualizaciones". Es posible que tenga que buscar actualizaciones varias veces, de modo que siga comprobando las actualizaciones hasta que no haya más actualizaciones disponibles y, a continuación, reinicie el equipo.

### <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR se bloquea después de actualizar Windows.

Algunas versiones anteriores de Windows Mixed Reality para SteamVR ya no son compatibles con Windows. Es posible que tenga una versión anterior de Windows Mixed Reality para SteamVR. Para asegurarse de que está actualizado:
1. En la biblioteca de vapor, vaya a **Software > Windows Mixed Reality para SteamVR** .
2. Haga clic con el botón derecho en él y vaya a "propiedades".
3. Seleccione la pestaña "actualizar" y seleccione "mantener siempre actualizada esta aplicación".
4. Fuerce la actualización; para ello, vaya a la pestaña "archivos locales" y seleccione "comprobar la integridad de los archivos de aplicación".
5. Reinicie vapor y SteamVR.

Si SteamVR todavía se bloquea después de la actualización, es posible que tenga dos instalaciones de Windows Mixed Reality para SteamVR en el equipo. Para confirmar si este es el caso:
1. Busque%LocalAppData%\openvr\openvrpaths.VrPath y ábralo en el Bloc de notas.
2. En las secciones "controladores externos", busque varias entradas para "MixedRealityVRDriver" 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Si ve varias entradas, quite las dos entradas más antiguas. Tenga en cuenta que una vez que solo tiene una entrada, ya no debe haber una coma al final de la línea, por ejemplo:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Guarde el archivo y ciérrelo.
5. Reinicie vapor y SteamVR.

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Mis controladores no funcionan como se esperaba en SteamVR.

1. Cierre SteamVR.
2. Vuelva a la Página principal de la realidad mixta y confirme que los controladores funcionan según lo previsto.
3. Vuelva a iniciar la experiencia de SteamVR y los controladores deben volver a la normalidad.
4. Si los problemas persisten, envíe comentarios mediante el [centro de comentarios de Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) en la categoría realidad mixta e incluya SteamVR en el resumen.

Tenga en cuenta que usará los controladores de movimiento de forma diferente en distintos juegos. Estos son algunos aspectos básicos que le ayudarán a empezar:
* Para abrir el panel de vapor, presione hacia abajo en el stick analógico izquierdo.
* Para salir de un juego de SteamVR y volver a la Página principal de Windows Mixed Reality, presione el botón Windows. A continuación, seleccione el botón Inicio de realidad mixta que aparece en la pantalla.

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Los controladores izquierdo y derecho se invierten en SteamVR.

Inicie el juego con las controladoras desactivadas y, a continuación, desactive la izquierda, seguida de la derecha.

### <a name="my-games-are-running-slowly"></a>Mis juegos se ejecutan lentamente.

1. Confirmar que el equipo cumple con las especificaciones de SteamVR en Windows Mixed Reality
2. Confirme que el equipo cumple con las especificaciones del juego SteamVR que está reproduciendo.
2. En el portal de realidad mixta del escritorio, seleccione "pausar" para detener la vista previa del escritorio.
3. Siga las instrucciones anteriores para asegurarse de que está ejecutando Windows 10 Build 16299,64 o posterior.
4. Asegúrese de que el equipo tiene los controladores de gráficos más recientes.
5. Compruebe el administrador de tareas para ver qué otros procesos pueden estar en ejecución en el equipo y consumir recursos.
6. Compruebe si la secuencia está descargando un juego en segundo plano. Esto puede consumir recursos y hacer que los juegos se ejecuten de forma deficiente.
7. Hay un problema de rendimiento conocido que afecta a una pequeña clase de aplicaciones que no tienen una ventana visible, por ejemplo, SteamVR Home. La gran mayoría de las aplicaciones no entran en esta categoría y una corrección estará disponible en una futura actualización.

Si sigue teniendo problemas de rendimiento inesperados, envíenos sus comentarios mediante el centro de comentarios de Windows. Asegúrese de seguir las instrucciones para [incluir un seguimiento de rendimiento de SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr). 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR muestra un error del compositor (por ejemplo, "error al conectar el compositor de IPC compartido (400)").

Existe un problema conocido en el que esto puede suceder si el micrófono y el monitor principal están en dos adaptadores de vídeo diferentes. Conecte el monitor al mismo adaptador que el casco y configúrelo para que sea el monitor principal de configuración de la **aplicación > sistema > pantalla** .

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>El contenido de SteamVR aparece en el lugar equivocado, como debajo del piso o por encima de mi cabeza.

Restablezca su posición: 
1. Haga clic en el stick de la izquierda del controlador para abrir el "panel de SteamVR".
2. Seleccione el botón "configuración".
3. Seleccione "restablecer posición asentada".

### <a name="my-steam-app-closed-unexpectedly"></a>La aplicación de vapor se cerró de forma inesperada.

La aplicación de vapor se cerrará si bloquea la pantalla del equipo, quita el casco, cambia de usuario o si el equipo entra en suspensión.


## <a name="speech-and-audio-problems"></a>Problemas de voz y audio

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>No puedo oír ningún sonido en el casco o el sonido se está reproduciendo en el equipo en lugar de en el casco.

* Si el casco envolvente no incluye auriculares integrados, deberá conectar los auriculares con el conector de audio del casco. El conector suele encontrarse detrás o debajo del visor o los lentes con auriculares. Si no puede encontrarlo, consulte con el fabricante del casco.
* Algunos auriculares de audio tienen botones físicos para controlar el volumen. Si el audio no funciona, compruebe si el volumen está desactivado o silenciado.
* Windows Mixed Reality está diseñado para reproducir sonido a través de los auriculares más inmersivo cuando se ejecuta el portal de realidad mixta y tiene auriculares conectados a él. Al desplazarse por los auriculares o voltear el parasol, cerrar la aplicación del portal de realidad mixta o, cuando esa aplicación no se ha usado durante 15 minutos, el audio cambiará al dispositivo de reproducción de Windows predeterminado. Puede cambiar esta configuración en **configuración > realidad mixta > audio y voz.**
* Asegúrese de que el casco de audio está enchufado completamente en el conector de audio. El casco de Acer en concreto puede requerir más atención para asegurarse de que el casco de audio está enchufado.
* Compruebe que el micrófono y los auriculares de audio están enchufados en el casco y no en el PC.
* En el panel de control de sonido de Windows solo se muestran los puntos de conexión de audio habilitados, no deshabilitados. El dispositivo de audio con auriculares se deshabilitará cuando no disponga de los auriculares, por lo que tiene que hacer clic con el botón derecho en el panel de control de sonido y elegir "Mostrar dispositivos deshabilitados" para verlo; el nombre del dispositivo es "Realtek USB 2.0 audio". Una vez hecho esto, puede cambiar el nombre en la página "propiedades" por algo que se reconocerá más fácilmente. Puede hacerlo para las pestañas reproducción y grabación.
* Si el audio no funciona en aplicaciones de realidad mixta (por ejemplo, Netflix), puede deberse a un problema conocido en el que Windows Mixed Reality no se actualice automáticamente para que coincida con la versión del sistema operativo. Para corregir este problema y obtener la mejor experiencia mixta, vaya a **configuración > actualizar & seguridad > Windows Update > comprobar si hay actualizaciones** .

**Nota:** El audio espacial de realidad mixta de Windows funciona mejor con los auriculares incorporados o conectados directamente a los auriculares más inmersivo. Es posible que los altavoces o auriculares conectados al equipo no funcionen bien para el audio espacial.

**Nota:** Windows Mixed Reality no es compatible con los auriculares de audio Bluetooth.

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Estoy experimentando cambios repentinos en el volumen, audio perdido o zumbidos.

* Algunas aplicaciones, incluidas muchas de las que se inician a través de SteamVR, pueden perder audio o bloquearse cuando el dispositivo de audio cambia cuando se inicia o se detiene el portal de realidad mixta. Reinicie la aplicación después de abrir la aplicación del portal de realidad mixta para corregir este comportamiento.
* Si otro dispositivo USB multimedia (como una cámara web) comparte el mismo concentrador USB interno o externo con el casco de realidad mixta de Windows, es posible que, en ocasiones, el Jack y los auriculares de audio del casco tengan un sonido sonoro o que no haya audio. Conecte el casco a un puerto USB que use un concentrador diferente o desconecte o deshabilite el otro dispositivo multimedia USB.
* Si observa una ráfaga de ruido de los auriculares conectados al casco, es posible que el concentrador USB del equipo no pueda proporcionar suficiente energía para los auriculares de la realidad mixta de Windows. Si esto ocurre, envíe un error al [centro de comentarios](https://docs.microsoft.com/hololens/hololens-feedback) de forma inmediata. Soluciones alternativas que pueden ayudar a incluir la no utilización de cables de extensión, el uso de un CONCENTRADOr USB 3,0 dedicado y externo, o la prueba de un puerto USB diferente en el equipo.

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mis auriculares de audio Bluetooth no funcionan según lo esperado.

Microsoft no recomienda el uso de auriculares de audio Bluetooth con Windows Mixed Reality. Los periféricos de audio Bluetooth no funcionan bien con las experiencias de sonido espacial y de voz de Windows Mixed Reality, y los auriculares de audio Bluetooth no admiten la entrada de micrófono y la salida estéreo al mismo tiempo, por lo que no oirá sonido estéreo o espacial al usarlo para gamechat u otra entrada de voz. Los auriculares de audio Bluetooth también pueden afectar negativamente a la experiencia del controlador de movimiento. 

### <a name="sound-isnt-coming-from-expected-directions"></a>El sonido no proviene de las direcciones esperadas.

La Página principal de Windows Mixed Reality incluye sonido espacial (audio similar al de las aplicaciones que se encuentran en su hogar). A medida que se acerque y se aleje de cada aplicación, la dirección y el nivel sonoros cambiarán a la sensación de realismo. Estas son algunas razones para las direcciones de sonido inesperadas: 
* Cuando abra y reproduzca música desde una aplicación de música compatible con el fondo (como Groove Music) en su hogar y, a continuación, abra una experiencia de VR envolvente (como un juego), el sonido de la aplicación de música pasará a través de un sonido espacial a estéreo. Puede parecer más alto que antes porque ya no existe ninguna distancia entre el usuario y el sonido.
* Si tiene Cortana habilitada en el equipo host antes de usar el casco de realidad mixta de Windows, puede perder el sonido espacial que se aplica a las aplicaciones en la Página principal de Windows Mixed Reality. Para solucionarlo, desactive la opción "permitir que Cortana responda a Hola Cortana" en **configuración > Cortana** en el escritorio antes de iniciar Windows Mixed Reality, o bien habilite "Windows Sonic para auriculares" en la ventana de la aplicación de escritorio en la Página principal de Windows Mixed Reality:
    1. Haga clic con el botón izquierdo en el icono de altavoz de la barra de tareas del escritorio y selecciónelo en la lista de dispositivos de audio.
    2. Haga clic con el botón secundario en el icono de altavoz de la barra de tareas del escritorio y seleccione "Windows Sonic para auriculares" en el menú "configuración del altavoz".
    3. Repita estos pasos para todos los dispositivos de audio (puntos de conexión).

### <a name="speech-commands-are-not-working-as-expected"></a>Los comandos de voz no funcionan según lo esperado.

* Para usar comandos de voz, la configuración de voz y idioma del equipo debe estar establecida en un [idioma compatible con Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Para comprobar la configuración de la voz y el idioma de Windows, seleccione **configuración > tiempo & idioma > región & idioma** y **configuración > hora & lenguaje > voz** .
* Si el casco no tiene un micrófono integrado, deberá adjuntar auriculares con un micrófono al casco o a su PC. Para que la entrada de micrófono cambie automáticamente al casco cuando lo haga, vaya a **configuración > realidad mixta > audio y voz** , y Active "cuando me gaste el casco, cambie a micrófono de auriculares".
* Algunos auriculares de audio tienen un botón físico para silenciar y dessilenciar el micrófono. Si los comandos de voz no funcionan, compruebe si el micrófono está silenciado.
* Los auriculares de audio con un micrófono que se encuentra en el cable earbud no funcionan bien para los comandos de voz en entornos con ruido ambiente.
* Cortana puede ser lento la primera vez que se invoca en una sesión de portal de realidad mixta. Vaya a **configuración > cortana > hable con Cortana** y asegúrese de que esté habilitada la opción "permitir que Cortana responda a Hola Cortana".
* En algunos equipos, es posible que la ganancia predeterminada de la captura de voz para el micrófono conectado con auriculares sea demasiado baja. Si experimenta comandos de voz no confiables o dictado, puede intentar ejecutar el solucionador de problemas de instalación del micrófono. Puede llegar a este solucionador de problemas a través de la **configuración > tiempo & idioma > voz** y, a continuación, seleccione "introducción" en la sección "micrófono". Hágalo a través de la aplicación de escritorio en la Página principal de Windows Mixed Reality mientras usa los auriculares para afectar al micrófono que usa para Windows Mixed Reality. Seleccione el extremo adecuado en el Asistente para solucionar problemas.

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Solo tengo un auricular de audio y quiero usarlo para el escritorio y para el casco.

Si solo tiene un casco de audio y no tiene un casco con auriculares integrados, conecte los auriculares de audio al equipo host en lugar de los auriculares. A continuación, desactive "cambiar a audio con auriculares" en la configuración de PRM.

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Quiero cambiar a Dolby Atmos para auriculares.

Los entornos de realidad mixta de Windows y sus aplicaciones usan la tecnología de audio espacial de Windows Sonic para auriculares, que está personalizada para experiencias de realidad mixta. Otras tecnologías de audio espacial, como Dolby Atmos para auriculares, pueden aplicarse a aplicaciones de pantalla completa como SteamVR Games, pero no a los entornos y aplicaciones de Shell de realidad mixta de Windows (por ejemplo, la colocación de un explorador Web en la pared de la casa del acantilado o el cielo Loft) que se han diseñado con Windows Sonic para auriculares de sonido espacial y acústicos.


## <a name="questions-about-desktop-in-mixed-reality"></a>Preguntas sobre el escritorio en realidad mixta

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Cómo tener acceso al escritorio de mi PC en la realidad mixta
Puede tener acceso al escritorio de su PC en la realidad mixta mediante la aplicación de escritorio. Inícielo en el botón auriculares de **Windows > todas las aplicaciones > Desktop** . 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>¿Cómo puedo ver varios monitores en realidad mixta?
De forma predeterminada, la aplicación de escritorio cambia automáticamente para mostrar el monitor con el foco. Si desea ver todos los monitores en realidad mixta: 
* Haga clic en el icono de monitor en la esquina superior izquierda de la aplicación.
* Deshabilitar "cambiar automáticamente el monitor"
* Elija el monitor que desea ver
* Iniciar otra instancia de la aplicación de escritorio
* Elija el monitor que desea ver en esa instancia 
* Repita el procedimiento con todos los monitores físicos. tenga en cuenta que tendrá que volver a seleccionar el monitor para que se muestre en cada aplicación de escritorio cada vez que reinicie la realidad mixta. 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>La aplicación de escritorio solo muestra una pantalla en negro.
Si su equipo tiene una GPU híbrida de NVIDIA, el problema puede deberse al dispositivo NVIDIA que ejecuta el runtimebroker.exe en la GPU discreta en lugar de la integrada. Para corregir este problema, siga estas instrucciones en "[Cómo crear la configuración de Optimus para un nuevo programa?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)". para agregar C:\windows\system32\runtimebroker.exe y forzarlo a que se ejecute en el procesador de "gráficos integrados". 


## <a name="other-questions"></a>Otras preguntas

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>Se está bloqueando la actualización de firmware de Samsung Odyssey o Odyssey +.

Samsung posee y publica las actualizaciones de firmware de los auriculares que se entregan a través de las aplicaciones complementarias "Samsung HMD Odyssey Setup" y "Samsung HMD Odyssey + Setup". Para obtener más detalles y obtener ayuda con los problemas de actualización de firmware de Samsung, póngase en contacto con el servicio de atención al cliente de Samsung.

Si el proceso de actualización de firmware se está bloqueando y no ha habido ningún progreso durante más de cinco minutos:
* Desconecte temporalmente todos los demás dispositivos USB y vuelva a intentar la actualización del firmware.
* Conecte sus auriculares Samsung a otro puerto USB 3,0 en su PC.
* Deshabilitar o desinstalar cualquier software instalado que puede interferir con las actualizaciones de firmware, como la App Center de Gigabyte AORUS.
* Use otro equipo para realizar la actualización de firmware de auriculares de Samsung.

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mi Wi-Fi se ralentiza cuando utilizo Windows Mixed Reality.

Si usa una conexión Wi-Fi de 2,4 GHz, los controladores de movimiento pueden ralentizar la red Wi-Fi. Pruebe una de las siguientes opciones:
* Cambie a una conexión Wi-Fi de 5 GHz, si hay alguna disponible. [Más información](https://support.microsoft.com/en-us/help/4000461).
* Use un adaptador Bluetooth independiente para conectar sus controladores de movimiento al equipo. Consulte [adaptadores recomendados](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Aparece un mensaje que indica que se ha incorporado el equipo. ¿Por qué?

Si usa un equipo portátil, Windows Mixed Reality funciona mejor cuando el equipo está totalmente cargado y conectado. 

### <a name="what-is-the-experience-options-setting"></a>¿Cuál es la configuración de opciones de experiencia?

La configuración de las opciones de experiencia ( **configuración > la realidad mixta > las opciones de experiencia > experiencia** ) le permite cambiar la configuración de rendimiento de Windows Mixed Reality. Esto le permite elegir la mejor experiencia posible para la configuración de hardware en una variedad de contenido. La experiencia de 90Hz está disponible para todos los sistemas, pero es posible que desee probar de forma automática la configuración que prefiera. Estas son las opciones:
* Automático: Windows Mixed Reality determinará la mejor experiencia para la configuración de hardware. Para la mayoría de los usuarios, esta es la mejor opción para empezar.
* 60Hz: establece la frecuencia de actualización en 60 Hz y desactiva ciertas características, como captura de vídeo y vista previa en el portal de realidad mixta.
* 90Hz: establece la frecuencia de actualización en 90Hz.

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>¿Qué idiomas se admiten en Windows Mixed Reality?

Windows Mixed Reality está disponible en los idiomas siguientes. Si el equipo está configurado en un idioma diferente, puede seguir usando Windows Mixed Reality, pero la interfaz aparecerá en inglés (Estados Unidos), y los comandos de voz y el dictado no estarán disponibles.

* Chino simplificado (China)
* Inglés (Australia)
* Inglés (Canadá)
* Inglés (Gran Bretaña)
* Spanish (Traditional Sort) - Spain
* Francés (Canadá)
* Francés (Francia)
* Alemán (Alemania)
* Italiano (Italia)
* Japonés (Japón)
* Español (México)
* Español (España)

El teclado Windows Mixed Reality en pantalla solo es inglés (Estados Unidos). Para escribir texto en otro idioma, use un teclado físico conectado a su PC. También puede usar dictado en uno de los idiomas admitidos de Windows Mixed Reality enumerados anteriormente, simplemente seleccionar micrófono en el teclado en pantalla.

Windows Mixed Reality también está disponible en los siguientes idiomas sin comandos de voz ni características de dictado:

* Chino tradicional (Taiwán y Hong Kong)
* Neerlandés (Países Bajos)
* Coreano (Corea)
* Ruso (Rusia)

### <a name="i-have-questions-about-my-headset-hardware"></a>Tengo preguntas sobre el hardware de auriculares.

Para obtener más información sobre el casco, consulte con el fabricante. Puede haber una guía de producto en el cuadro o puede probar el sitio web del fabricante.


## <a name="how-to-uninstall-windows-mixed-reality"></a>Desinstalación de Windows Mixed Reality

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>Cómo desinstalar Windows Mixed Reality

1. Desconecte el casco del equipo.
2. Cierre el portal de realidad mixta.
2. Vaya a  **inicio > configuración > realidad mixta** y seleccione "desinstalar".

Cuando esté listo para empezar a usar el casco de nuevo, conéctelo y el portal de realidad mixta le guiará a través del programa de instalación.

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Aparece el mensaje "no se pudo finalizar la desinstalación de Windows Mixed Reality".

Esto significa que algunos archivos, incluida la información sobre su entorno, pueden seguir estando en el equipo. Esto puede causar problemas si decide volver a instalar Windows Mixed Reality más tarde. Puede quitar manualmente cualquier información restante de Windows Mixed Reality del equipo modificando el registro y usando Windows PowerShell para ejecutar comandos. _Si modifica el registro de forma incorrecta, pueden producirse problemas graves. Asegúrese de seguir estos pasos con cuidado. Para una mayor protección, haga una copia de seguridad del registro antes de modificarlo para poder restaurarlo en caso de que se produzcan problemas._ Para obtener más información, vea [Cómo realizar una copia de seguridad del registro y volver a narrarlo en Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Para desinstalar Windows Mixed Reality con estos comandos:
1. Reinicia tu equipo.
2. En el cuadro de **búsqueda** , escriba "regedit" y, a continuación, seleccione **sí** .
3. Quite los siguientes valores del registro:
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>y, a continuación, elimine <b>FirstRunSucceeded</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>, elimine <b>PreferDesktopSpeaker</b> y <b>PreferDesktopMic</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>y, a continuación, elimine <b>DisableSpeechInput</b>. Nota: los elementos del registro en HHKEY_CURRENT_USER deben eliminarse para cada cuenta de usuario del equipo que haya usado Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>, elimine el <b>DeviceID</b> y el <b>modo</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>y, a continuación, elimine <b>OnDeviceLearningCompleted</b>.</li> 
   </ul>
4. Quite las claves del registro siguientes: <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. Cierre el editor del registro.
6. Vaya a **C:\Users\nombre name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** y, a continuación, elimine **RoomBounds.jsde** . Repita este paso para cada usuario que haya usado Windows Mixed Reality.
7. Abra el símbolo del sistema de administrador y vaya a **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . A continuación, elimine el contenido de la carpeta de **datos HeadTracking** (pero no la propia carpeta).
8. Escriba "PowerShell" en el **cuadro de búsqueda** , haga clic con el botón derecho en **Windows PowerShell** y, a continuación, seleccione **Ejecutar como administrador** .
9. En Windows PowerShell, haga lo siguiente: <ul>
   <li>Copie y pegue lo siguiente en el símbolo del sistema y, a continuación, presione ENTRAR: <b>DISM/online/Get-Capabilities</b></li> 
   <li>Copie la identidad de capacidad que comienza con el método analógico. Holographic. Desktop (si no lo&#39;, eso significa que este elemento no está&#39;t instalado. En ese caso, vaya al paso 10).</li> 
   <li>Copie y pegue el siguiente símbolo del sistema y, a continuación, presione ENTRAR: <b>DISM/online/Remove-Capability/CapabilityName: la identidad de la capacidad copiada en el último paso</b></li>
   </ul>
10. Reinicie el equipo.




