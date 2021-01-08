---
title: Preguntas más frecuentes sobre la configuración de Windows Mixed Reality
description: Obtenga respuestas a preguntas de configuración comunes al trabajar con aplicaciones y dispositivos de Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
appliesto:
- Windows 10
ms.openlocfilehash: 2da2524ae09014b990ea4f0301a21d4aac963eb9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008635"
---
# <a name="windows-mixed-reality-setup-faq"></a>Preguntas más frecuentes sobre la configuración de Windows Mixed Reality

A continuación se muestra información para ayudar a solucionar los problemas que se pueden encontrar al configurar el casco envolvente de Windows Mixed Reality.

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>Aparece un mensaje que indica "no pudimos descargar el software de la realidad mixta de Windows" o el programa de instalación está atascado en la página "se bloqueó la carga mientras hacemos algunas descargas"

Realice estos pasos:

* Vaya a **configuración > actualizar & seguridad > Windows Update** y asegúrese de que Windows Update está activado. A continuación, descargue e instale las actualizaciones que estén esperando para ser instaladas.
* Asegúrese de que el equipo está conectado a Internet y tiene al menos 2 GB de espacio de almacenamiento libre.
* Reinicie el equipo e inténtelo de nuevo. Es posible que tenga que repetir varias veces o ejecutar el solucionador de problemas de Windows Update para borrar las actualizaciones pendientes.

> [!NOTE]
> * Si se encuentra en una red administrada por la empresa, consulte con el administrador. Es posible que necesiten habilitar Windows Mixed Reality. ¿Busca las instrucciones para profesionales de ti? Consulte **[este artículo](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)**.
> * Si la conexión de red Wi-Fi está establecida en medido, cámbiela a desmedido. **[Más información](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>Aparece un mensaje que indica "se produjo un error y no pudimos iniciar Windows Mixed Reality".

Realice estos pasos:

1. Desconecte el casco del equipo (ambos cables).
2. Reinicie el equipo.
3. Vaya a **configuración > Update & security > Windows Update** y asegúrese de que Windows Update está activado. A continuación, descargue e instale las actualizaciones que estén esperando para ser instaladas.
4. Vuelva a conectar los auriculares al equipo e intente realizar de nuevo la instalación.

Si los pasos anteriores no funcionan, intente desinstalar y reinstalar Windows Mixed Reality. Vaya a **configuración > realidad mixta > desinstalar** y seleccione **desinstalar**. Luego, reinicie el equipo. Para volver a iniciar el proceso de instalación, simplemente conecte el casco a su PC.

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>El portal de realidad mixta no se abre cuando se conectan los auriculares

Portal de realidad mixta, la aplicación que le guía a través de la configuración de Windows Mixed Reality, está diseñada para abrirse automáticamente cuando conecta un casco compatible. Si no se abre, vaya a Inicio y escriba "portal de realidad mixta" en el cuadro de búsqueda para abrir la aplicación. Es posible que tenga que [actualizar a la versión más reciente de Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq) si no encuentra el portal de realidad mixta.

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>Aparece un mensaje que indica que mi PC no puede ejecutar Windows Mixed Reality

Si recibe este mensaje, el equipo no cumple los [requisitos mínimos](https://support.microsoft.com/help/4039260) necesarios para ejecutar Windows Mixed Reality. Es posible que la configuración de hardware del equipo no sea compatible con Windows Mixed Reality, o que tenga que [actualizar a la versión más reciente de Windows](https://support.microsoft.com/help/12373).

Notas sobre tarjetas de gráficos:

* Si la instalación de Windows Mixed Reality indica que la tarjeta gráfica no cumple los requisitos y cree que lo hace, asegúrese de que el casco esté conectado a la tarjeta correcta.
* Consulte con el fabricante de la tarjeta gráfica para obtener la actualización del controlador más reciente. Windows Mixed Reality requiere un controlador de tarjeta de gráficos que admita al menos WDDM 2,2.

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>Aparece un mensaje que indica que "ya está casi ahí — este equipo no cumple los requisitos mínimos necesarios para ejecutar Windows Mixed Reality".

Si recibe este mensaje, el equipo no cumple los requisitos mínimos necesarios para la mejor experiencia en Windows Mixed Reality. El equipo puede ejecutar un casco envolvente, pero es posible que no pueda ejecutar ciertas aplicaciones o que tenga problemas de rendimiento.

## <a name="my-xbox-controller-isnt-working"></a>El controlador Xbox no funciona

Realice estos pasos:

* Asegúrese de que el controlador esté encendido, totalmente cargado y conectado al equipo.
* Reemplace las baterías del controlador.
* Si usa un controlador de Bluetooth, vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo y asegúrese de que están emparejados (debe verlos en la página).

[Más información acerca de los controladores de Xbox](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>Mis controladores de movimiento no funcionan

Realice estos pasos:

* Asegúrese de que los controladores están encendidos y totalmente cargados.
* Reemplace las baterías de los controladores.
* Apague y encienda los controladores mientras los mantiene delante. Mantenga presionado el botón de Windows durante 4 segundos para desactivar un controlador y, a continuación, mantenga presionado el botón en 2 segundos para activarlo.
* Vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo y asegúrese de que están emparejados (debe verlos en la página).

[Más información acerca de los controladores de movimiento](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Aparece un mensaje que dice "conectar los auriculares" aunque he enchufado los auriculares

Realice estos pasos:

- Asegúrese de que el casco esté conectado a los puertos correctos del equipo. Debe estar conectado a la tarjeta de gráficos discretos del equipo y a un puerto USB 3,0. Aquí se indica cómo identificar los puertos correctos:
    - Los puertos USB 3,0 tienen un logotipo especial con una marca "SS" (que indica "SuperSpeed"). Normalmente, la pieza interior del puerto es azul, pero los puertos USB 2,0 más antiguos suelen estar en blanco o negro en el interior.
    - Si el equipo tiene dos puertos HDMI, use el que se conecta a la tarjeta gráfica, no la placa base del equipo. No siempre es obvio, que es lo que, aunque los puertos discretos se encuentran a menudo en una ranura de expansión del equipo. Si intenta un puerto y no funciona, pruebe el otro.
- Vaya al sitio web del fabricante del casco y actualice los controladores y el firmware del casco.

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante el inicio de la realidad mixta, estoy atascado en "gire el cabezal hacia el lateral y, a continuación, en el suelo"

Este paso permite que los auriculares reconozcan su espacio y restauren el suelo y el límite virtual existentes. Al colocar el casco, este proceso de análisis puede tardar hasta 10 segundos. Una vez que haya finalizado, estará en la Página principal de Windows Mixed Reality o se le pedirá que configure de nuevo el límite.

Si el proceso de análisis tarda más de 10 segundos, podría haber un problema con el sensor de proximidad en el casco:

1. Compruebe que la etiqueta se ha quitado del sensor de proximidad. El sensor de proximidad se encuentra dentro del casco aproximadamente donde sería el centro del Forehead.
2. Compruebe que el sensor de proximidad está alternando la entrada al casco: con el dedo, cubra y descubra el sensor de proximidad varias veces para comprobar que la entrada está cambiando al casco. Debería ver el banner **clave de Windows + Y** en la parte superior de su PC. Puede cambiar manualmente la entrada al casco en cualquier momento escribiendo **tecla Windows + Y** en el teclado.

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>El nivel inferior de la Página principal de Windows Mixed Reality no parece estar en el alto correcto

Seleccione **inicio > ajuste del piso**, que se iniciará una vez que coloque la aplicación en el mundo, para realizar cambios mientras tiene el casco. En esta aplicación, se le indicará que use el teclado táctil (controlador de movimiento) o el panel de control (controlador de vídeo) para ajustar el alto del piso. Cuando el piso sea correcto, use el botón Windows para volver a la Página principal.

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>No se puede mostrar una vista previa de lo que veo en el micrófono

El portal de Windows Mixed Reality tiene un botón **reproducir** en la parte inferior de la pantalla que le permite obtener una vista previa de lo que está viendo en el casco en la pantalla del escritorio. Por motivos de rendimiento, esta característica solo está disponible en equipos que ejecutan Windows Mixed Reality ultra (90 Hz).

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>¿Cómo puedo obtener una vista más clara en el casco?

Intente ajustar el ajuste del casco. Ajuste su posición en su superficie moviéndola hacia arriba, hacia abajo o hacia la izquierda y a la derecha, y ajuste las correas para que se sientan perfectamente.

Si el casco lo admite, también puede ajustar la configuración de la calibración. Si el casco tiene un botón para ajustar la calibración, úselo. Si no es así, vaya a **configuración > realidad mixta > calidad visual** y ajuste la calibración allí. Para obtener más información sobre la calibración de un dispositivo específico, consulte con el fabricante del casco.

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>Al conectar los auriculares, no sucede nada: el portal de realidad mixta no se abre

Portal de realidad mixta, la aplicación que le guía a través de la configuración de Windows Mixed Reality, está diseñada para abrirse automáticamente cuando conecta un casco compatible. Si no se abre, vaya a **Inicio** y escriba **portal de realidad mixta** en el cuadro de **búsqueda**  para abrir la aplicación desde allí. Si no encuentra el portal de realidad mixta, es posible que deba [actualizar a la versión más reciente de Windows](https://support.microsoft.com/help/12373) o que el casco no esté correctamente conectado al equipo.

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La pantalla del montaje del cabezal no funciona después de apagar y realizar un inicio rápido

Pruebe esto:

* Desconecte el cable de la pantalla y el cable USB de la pantalla del montaje principal y vuelva a conectarlos.

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Mi Wi-Fi se ralentiza cuando utilizo Windows Mixed Reality

Si usa una conexión Wi-Fi a 2,4 GHz, los controladores de movimiento pueden ralentizar la red Wi-Fi. Realice uno de los pasos siguientes:

* Cambie a una conexión de Wi-Fi de 5 GHz, si hay alguna disponible. Saber más
* Use un adaptador Bluetooth independiente para conectar sus controladores de movimiento al equipo. [Consulte los adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> Los auriculares más recientes se emparejan directamente con los controladores a través de un chip Bluetooth integrado y no deben experimentar este problema.

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Obtengo un mensaje de error "algo salió mal" o tengo problemas en el portal de realidad mixta

Para obtener más información sobre un código de error específico, mire [aquí](error-codes.md). También puede intentar:

Reiniciar Windows Mixed Reality:

1. Desconecte ambos cables de auriculares del equipo.
2. Reinicia tu equipo.
3. Vuelva a conectar los auriculares.

Asegúrese de que el equipo reconoce los auriculares:

1. Seleccione Inicio.
2. Escriba "Device Manager" en el cuadro de búsqueda y selecciónelo en la lista.
3. Expanda "dispositivos de realidad mixta" y compruebe si aparece el casco.

Si no aparece en la lista:

1. Conecte los auriculares a puertos diferentes en el equipo, si está disponible.
2. Busque las actualizaciones de software más recientes desde Windows Update.
3. Desinstalar y reinstalar Windows Mixed Reality:
    1. Desconecte ambos cables de auriculares del equipo.
    2. Seleccione **configuración > realidad mixta > desinstalar**.
    3. Si los controladores de movimiento están emparejados al equipo, seleccione **configuración > dispositivos > Bluetooth & otros dispositivos** para desemparejarlos. Seleccione cada controlador y "quitar dispositivo". Si los controladores se emparejan con el casco, puede omitir este paso.
    4. Vuelva a conectar el casco al equipo para volver a instalar Windows Mixed Reality.

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)
* [Solución de problemas](troubleshooting-windows-mixed-reality.md)